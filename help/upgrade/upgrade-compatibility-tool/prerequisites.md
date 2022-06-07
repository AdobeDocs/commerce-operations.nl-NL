---
title: '"[!DNL Upgrade Compatibility Tool] vereisten"'
description: 'Controleer of uw systeem voldoet aan de vereisten voor het uitvoeren van de [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface voor uw Adobe Commerce-project. '
source-git-commit: 7ec999f9122eb0707ac6c37b7b49f9c423945318
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---


# Adobe Commerce-toegangstoetsen

{{commerce-only}

U moet [Adobe Commerce-toegangstoetsen](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) om de [!DNL Upgrade Compatibility Tool]. Voeg je Adobe Commerce toegangstoetsen toe aan je `auth.json` bestand, dat zich bevindt op `~/.composer` standaard.

>[!NOTE]
>
>Controleer uw **COMPOSER_HOME** omgevingsvariabele om te zien waar de `auth.json` bestand is gevonden.

De **openbare sleutel** komt overeen met de _gebruikersnaam_ overwegende dat de **persoonlijke sleutel** is de _password_:

## Voorbeeld van Adobe Commerce-toegangstoetsen

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

>[!NOTE]
>
> Als u uw **Adobe Commerce-toegangstoetsen**, kunt u de [!DNL Upgrade Compatibility Tool] en de `composer create-project` de opdracht mislukt.

Uitvoeren `composer install` in uw terminal om gebiedsdelen te installeren.

## Systeemvereisten

De minimumeisen voor het gebruik van de [!DNL Upgrade Compatibility Tool] in een bevel-lijn interface zijn:

| **Vereisten** | **Restricties** |
|----------------|-----------------|
| PHP-versie | >= 7,3 |
| Composer | geen bekende eis. |
| Node.js | Node.js-versies `^12.22.0`, `^14.17.0`, of `>=16.0.0` (zie [Node.js installeren](https://nodejs.dev/learn/how-to-install-nodejs)) |
| Geheugenbeperkingen | minimaal 2 GB RAM. |

Adobe Commerce wordt alleen ondersteund op Linux-besturingssystemen. U kunt de [!DNL Upgrade Compatibility Tool] in een Linux-besturingssysteem. U hoeft de [!DNL Upgrade Compatibility Tool] waar uw Adobe Commerce-exemplaar zich bevindt.

Het is noodzakelijk [!DNL Upgrade Compatibility Tool] om toegang te hebben tot de broncode van de instantie Adobe Commerce. U kunt de toepassing bijvoorbeeld op de ene server installeren en deze op de Adobe Commerce-installatie op een andere server plaatsen.

Als u de [!DNL Upgrade Compatibility Tool] voor een Adobe Commerce-exemplaar met grote modules en bestanden kan het nodig zijn dat er veel RAM-geheugen beschikbaar is (ten minste 2 GB).
