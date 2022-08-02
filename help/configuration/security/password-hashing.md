---
title: Wachtwoordhashing
description: Lees voor wachtwoord het hakken strategieën en implementatie.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Wachtwoordhashing

Momenteel gebruikt de Handel zijn eigen strategie voor het hakken van wachtwoorden, gebaseerd op verschillende native PHP hashing algoritmen. De handel steunt veelvoudige algoritmen zoals `MD5`, `SHA256`, of `Argon 2ID13`. Als de natriumextensie is geïnstalleerd (standaard geïnstalleerd in PHP 7.3), dan `Argon 2ID13` wordt gekozen als het standaardhash-algoritme. Anders, `SHA256` is de standaardwaarde. Handel kan de native PHP gebruiken `password_hash` functie met ondersteuning voor het Argon 2i-algoritme.

Vermijd het compromitteren van oudere wachtwoorden die met verouderde algoritmen zoals zijn gehakt `MD5`, verstrekt de huidige implementatie een methode om de knoeiboel te bevorderen zonder het originele wachtwoord te veranderen. Over het algemeen heeft de wachtwoordhash de volgende indeling:

```text
password_hash:salt:version<n>:version<n>
```

Wanneer `version<n>`...`version<n>` vertegenwoordigt alle versies van hashalgoritmen die op het wachtwoord worden gebruikt. Bovendien wordt de salt altijd samen met de wachtwoordhash opgeslagen, zodat we de gehele keten van algoritmen kunnen herstellen. Een voorbeeld ziet er als volgt uit:

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

Het eerste deel vertegenwoordigt de wachtwoordhash. De tweede, `8qnyO4H1OYIfGCUb` is het zout. De laatste twee zijn de verschillende knoeiboelalgoritmen: 1 is `SHA256` en 2 `Argon 2ID13`. Dit betekent dat het wachtwoord van de klant oorspronkelijk is gehasht met `SHA256` en daarna werd het algoritme bijgewerkt met `Argon 2ID13` en de hash werd opgepakt met Argon.

## Hash-strategie bijwerken

Bedenk hoe het mechanisme van de hakupgrade eruitziet. Veronderstel dat oorspronkelijk, een wachtwoord werd gehakt met `MD5` en toen werd het algoritme bijgewerkt veelvoudige tijden met Argon 2ID13. Het volgende diagram toont de stroom van de knoeiboelverbetering.

![Workflow voor bijwerken van hash](../../assets/configuration/hash-upgrade-algorithm.png)

Elk knoeiboelalgoritme gebruikt het vorige wachtwoordknoeiboel om een nieuwe knoeiboel te produceren. De handel slaat niet het originele, ruwe wachtwoord op.

![Hash-upgradestrategie](../../assets/configuration/hash-upgrade-strategy.png)

Zoals hierboven beschreven, zou de wachtwoordknoeiboel veelvoudige knoeiboelversies kunnen hebben die op het originele wachtwoord worden toegepast.
Hier is hoe het mechanisme van de wachtwoordcontrole tijdens een klantenauthentificatie werkt.

```php
def verify(password, hash):
    restored = password

    hash_map = extract(hash)
    # iterate through all versions specified in the received hash [md5, sha256, argon2id13]
    for version in hash_map.get_versions():
        # generate new hash based on password/previous hash, salt and version
        restored = hash_func(salt . restored, version)

    # extract only password hash from the hash:salt:version chain
    hash = hash_map.get_hash()

    return compare(restored, hash)
```

Aangezien de Handel alle gebruikte versies van de wachtwoordknoeiboel samen met de wachtwoordknoeiboel opslaat, kunnen wij de volledige knoeiboel tijdens de wachtwoordcontrole herstellen. Het mechanisme van de knoeiboelcontrole is gelijkaardig aan de strategie van de knoeiboelverbetering: gebaseerd op versies die samen met de wachtwoordhash worden opgeslagen, produceert het algoritme hashes van het verstrekte wachtwoord en keert het vergelijkingsresultaat tussen hashed wachtwoord en het gegevensbestand-opgeslagen knoeiboel terug.

## Implementatie

De `\Magento\Framework\Encryption\Encryptor` De klasse is verantwoordelijk voor het genereren en verifiëren van wachtwoordhashes. De [`bin/magento customer:hash:upgrade`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) het bevel bevordert een knoeiboel van het klantenwachtwoord aan het recentste knoeiboelalgoritme.
