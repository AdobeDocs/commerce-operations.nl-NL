---
title: Installeer de [!DNL Upgrade Compatibility Tool]
description: Voer de volgende stappen uit om de [!DNL Upgrade Compatibility Tool] voor uw Adobe Commerce-project.
source-git-commit: 218b099caa883f66ddda48407fb789e51fedc203
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Installeer de [!DNL Upgrade Compatibility Tool]

{{commerce-only}

De [!DNL Upgrade Compatibility Tool] is een opdrachtregelprogramma dat een aangepaste Adobe Commerce-instantie controleert op een specifieke versie door alle daarin geïnstalleerde modules te analyseren. Er wordt een lijst met fouten en waarschuwingen geretourneerd die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

## Download de [!DNL Upgrade Compatibility Tool]

Als u het dialoogvenster [!DNL Upgrade Compatibility Tool], voert u de volgende opdracht uit:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installeren

Als u het dialoogvenster [!DNL Upgrade Compatibility Tool]dient u de vereiste voorwaarden te installeren:

* Adobe Commerce-toegangstoetsen
* Composer
* Node.js

## Vereisten

Zie [voorwaarden](../upgrade-compatibility-tool/prerequisites.md) voor meer informatie .

### Adobe Commerce-toegangstoetsen

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

### Composer

Klonen met [!DNL Upgrade Compatibility Tool] opbergen en uitvoeren `composer install` in uw terminal om gebiedsdelen te installeren.

>[!WARNING]
>
>Als de **Adobe Commerce-toegangstoetsen** zijn niet correct gevormd, [!DNL Upgrade Compatibility Tool] zal niet installeren en u zult fouten krijgen wanneer het runnen van `composer install` gebruiken.

### Node.js

Om Node.js te installeren, zie Node.js [documentatie](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensies van derden

Adobe raadt u aan contact op te nemen met uw leverancier van extensies om te bepalen of uw extensie volledig compatibel is met de nieuwste versie van Adobe Commerce.

Zie [Het gereedschap uitvoeren](../upgrade-compatibility-tool/run.md) voor informatie over de uitvoering van de [!DNL Upgrade Compatibility Tool].
