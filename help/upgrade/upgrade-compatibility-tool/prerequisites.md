---
title: '"[!DNL Upgrade Compatibility Tool] vereisten"'
description: 'Controleer of uw systeem voldoet aan de vereisten voor het uitvoeren van de [!DNL Upgrade Compatibility Tool] voor uw Adobe Commerce-project. '
source-git-commit: e539824b336978debd6e6adc538cd8bad367eff1
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 0%

---


# Systeemvereisten

{{commerce-only}

De minimumeisen voor het gebruik van de [!DNL Upgrade Compatibility Tool] zijn:

| **Vereisten** | **Restricties** |
|----------------|-----------------|
| PHP-versie | >= 7,3 |
| Composer | geen bekende vereiste |
| Node.js | [Node.js](https://nodejs.org/) (`^12.22.0`, `^14.17.0`, of `>=16.0.0`) |
| Geheugenbeperkingen | Minimaal 2 GB RAM |

U kunt de [!DNL Upgrade Compatibility Tool] in verschillende besturingssystemen (Windows wordt niet ondersteund). U hoeft de [!DNL Upgrade Compatibility Tool] waar uw Adobe Commerce-exemplaar zich bevindt.

Het is noodzakelijk [!DNL Upgrade Compatibility Tool] om toegang te hebben tot de broncode van de instantie Adobe Commerce. U kunt de toepassing bijvoorbeeld op de ene server installeren en deze op de Adobe Commerce-installatie op een andere server plaatsen.

Als u de [!DNL Upgrade Compatibility Tool] voor een Adobe Commerce-exemplaar met grote modules en bestanden kan het nodig zijn dat er veel RAM-geheugen beschikbaar is (ten minste 2 GB).

## Adobe Commerce-toegangstoetsen

U moet [Adobe Commerce-toegangstoetsen](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) om de [!DNL Upgrade Compatibility Tool]. Voeg je Adobe Commerce toegangstoetsen toe aan je `auth.json` bestand, dat zich bevindt op `~/.composer` standaard.

>[!WARNING]
>
>Controleer uw **COMPOSER_HOME** omgevingsvariabele om te zien waar de `auth.json` bestand is gevonden.

De **openbare sleutel** komt overeen met de _gebruikersnaam_ overwegende dat de **persoonlijke sleutel** is de _password_:

### Voorbeeld van Adobe Commerce-toegangstoetsen

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

## Composer

Download de [!DNL Upgrade Compatibility Tool] opbergen en uitvoeren `composer install` in uw terminal om gebiedsdelen te installeren.

>[!NOTE]
>
> Als u uw **Adobe Commerce-toegangstoetsen**, kunt u de [!DNL Upgrade Compatibility Tool]. De `composer create-project` de opdracht mislukt.

## Node.js

Om Node.js te installeren, zie Node.js [documentatie](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensies van derden

Adobe raadt u aan contact op te nemen met uw leverancier van extensies om te bepalen of uw extensie volledig compatibel is met de nieuwste versie van Adobe Commerce.
