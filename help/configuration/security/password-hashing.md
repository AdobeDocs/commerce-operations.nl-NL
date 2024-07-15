---
title: Wachtwoordhashing
description: Lees voor wachtwoord het hakken strategieën en implementatie.
feature: Configuration, Security
exl-id: 2865d041-950a-4d96-869c-b4b35f5c4120
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Wachtwoordhashing

Commerce gebruikt momenteel een eigen strategie voor wachtwoordhashing, gebaseerd op verschillende native PHP-hashingalgoritmen. Commerce ondersteunt meerdere algoritmen zoals `MD5` , `SHA256` of `Argon 2ID13` . Als de natriumextensie is geïnstalleerd (standaard geïnstalleerd in PHP 7.3), wordt `Argon 2ID13` gekozen als het standaardhashingalgoritme. Anders is `SHA256` de standaardwaarde. Commerce kan de native PHP `password_hash` functie gebruiken met ondersteuning voor het Argon 2i algoritme.

Als u wilt voorkomen dat oudere wachtwoorden die met verouderde algoritmen als `MD5` zijn gehasht, in het gedrang komen, biedt de huidige implementatie een methode om de hash bij te werken zonder het oorspronkelijke wachtwoord te wijzigen. Over het algemeen heeft de wachtwoordhash de volgende indeling:

```text
password_hash:salt:version<n>:version<n>
```

Waar `version<n>`... `version<n>` alle versies van hashalgoritmen vertegenwoordigt die op het wachtwoord worden gebruikt. Bovendien wordt de salt altijd samen met de wachtwoordhash opgeslagen, zodat we de gehele keten van algoritmen kunnen herstellen. Een voorbeeld ziet er als volgt uit:

```text
a853b06f077b686f8a3af80c98acfca763cf10c0e03597c67e756f1c782d1ab0:8qnyO4H1OYIfGCUb:1:2
```

Het eerste deel vertegenwoordigt de wachtwoordhash. De tweede, `8qnyO4H1OYIfGCUb` is de zout. De laatste twee zijn de verschillende hash-algoritmen: 1 is `SHA256` en 2 is `Argon 2ID13` . Dit betekent dat het wachtwoord van de klant oorspronkelijk is gehasht met `SHA256` en daarna is het algoritme bijgewerkt met `Argon 2ID13` en is de hash hervat met Argon.

## Hash-strategie bijwerken

Bedenk hoe het mechanisme van de hakupgrade eruitziet. Stel dat er oorspronkelijk een wachtwoord was opgeslagen met `MD5` en dat het algoritme vervolgens meerdere keren werd bijgewerkt met Argon 2ID13. Het volgende diagram toont de stroom van de knoeiboelverbetering.

![ de verbeteringswerkschema van de Hash {](../../assets/configuration/hash-upgrade-algorithm.png)

Elk knoeiboelalgoritme gebruikt het vorige wachtwoordknoeiboel om een nieuwe knoeiboel te produceren. Commerce slaat het oorspronkelijke, onbewerkte wachtwoord niet op.

![ de verbeteringsstrategie van de Hash ](../../assets/configuration/hash-upgrade-strategy.png)

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

Aangezien Commerce alle gebruikte versies van wachtwoordhashes samen met de wachtwoordhash opslaat, kunnen we de hele hashketen tijdens de wachtwoordverificatie herstellen. Het mechanisme van de knoeiboelverificatie is gelijkaardig aan de strategie van de knoeiboelverbetering: gebaseerd op versies die samen met de wachtwoordknoeiboel worden opgeslagen, produceert het algoritme hashes van het verstrekte wachtwoord en keert het vergelijkingsresultaat tussen hashed wachtwoord en de gegevensbestand-opgeslagen knoeiboel terug.

## Implementatie

De `\Magento\Framework\Encryption\Encryptor` -klasse is verantwoordelijk voor het genereren en verifiëren van wachtwoordhash. Het [`bin/magento customer:hash:upgrade` ](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#customerhashupgrade) bevel bevordert een knoeiboel van het klantenwachtwoord aan het recentste knoeiboelalgoritme.
