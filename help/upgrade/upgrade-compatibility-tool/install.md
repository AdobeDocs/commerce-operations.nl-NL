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

The [!DNL Upgrade Compatibility Tool] is a command-line tool that checks an Adobe Commerce customized instance against a specific version by analyzing all modules installed in it. Er wordt een lijst met fouten en waarschuwingen geretourneerd die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

## Download the [!DNL Upgrade Compatibility Tool]

Als u het dialoogvenster [!DNL Upgrade Compatibility Tool], voert u de volgende opdracht uit:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installeren

To install the [!DNL Upgrade Compatibility Tool], you must install the necessary prerequisites:

* Adobe Commerce access keys
* Composer
* Node.js

## Vereisten

Zie [voorwaarden](../upgrade-compatibility-tool/prerequisites.md) voor meer informatie .

### Adobe Commerce access keys

You must have [Adobe Commerce access keys](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) to download and use the [!DNL Upgrade Compatibility Tool]. Add your Adobe Commerce access keys to your `auth.json` file, which is located at `~/.composer` by default.

>[!WARNING]
>
>Check your **COMPOSER_HOME** environment variable to see where the `auth.json` file is located.

De **openbare sleutel** komt overeen met de _gebruikersnaam_ overwegende dat de **persoonlijke sleutel** is de _password_:

### Example of Adobe Commerce access keys

```json
    "http-basic": {
        "repo.magento.com": {
            "username": "YOUR_MAGENTO_PUBLIC_KEY",
            "password": "YOUR_MAGENTO_PRIVATE_KEY"
        }
    },
```

### Composer

Clone the [!DNL Upgrade Compatibility Tool] repository and run `composer install` in your terminal to install dependencies.

>[!WARNING]
>
>Als de **Adobe Commerce-toegangstoetsen** zijn niet correct gevormd, [!DNL Upgrade Compatibility Tool] zal niet installeren en u zult fouten krijgen wanneer het runnen van `composer install` gebruiken.

### Node.js

Om Node.js te installeren, zie Node.js [documentatie](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensies van derden

Adobe raadt u aan contact op te nemen met uw leverancier van extensies om te bepalen of uw extensie volledig compatibel is met de nieuwste versie van Adobe Commerce.

Zie [Het gereedschap uitvoeren](../upgrade-compatibility-tool/run.md) voor informatie over de uitvoering van de [!DNL Upgrade Compatibility Tool].
