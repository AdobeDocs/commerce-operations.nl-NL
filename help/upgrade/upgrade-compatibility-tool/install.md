---
title: Installeer de [!DNL Upgrade Compatibility Tool]
description: Voer de volgende stappen uit om de [!DNL Upgrade Compatibility Tool] voor uw Adobe Commerce-project.
source-git-commit: 3d9a721e33621b78f03f16b932a1ba2904ae4010
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# Installeer de [!DNL Upgrade Compatibility Tool]

De [!DNL Upgrade Compatibility Tool] is een opdrachtregelprogramma dat een aangepaste Adobe Commerce-instantie controleert op een specifieke versie door alle daarin geïnstalleerde modules te analyseren. Er wordt een lijst met fouten en waarschuwingen geretourneerd die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

## Workflow

Het volgende diagram toont het verwachte werkschema wanneer het runnen van [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagram](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Wie is de [!DNL Upgrade Compatibility Tool] for?

In het volgende gebruiksgeval wordt het gebruikelijke proces beschreven dat een Adobe Commerce-partner moet doorvoeren om een clientexemplaar te upgraden:

1. De software engineer van een partner downloadt de [!DNL Upgrade Compatibility Tool] pakket van de [Adobe Commerce-opslagplaats](https://repo.magento.com/) en voert deze uit tijdens de bètafase van de nieuwste Adobe Commerce-versie. Zie de [Download de [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) voor meer informatie.
1. De software engineer genereert een vanilla instantie voor de specifieke versie van Adobe Commerce die momenteel is geïnstalleerd. Zie de [Handleiding voor contribuanten](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) voor meer informatie over het gebruik van de `instance` gebruiken om een vanilleinstallatie te genereren.
1. De software engineer ziet dat er verschillende aangepaste gebieden in de inventarisatie- en catalogusmodules verbroken zijn en ze krijgen ook een complexiteitsscore van X. Zie de [Ontwikkelaar](../upgrade-compatibility-tool/developer.md) voor meer informatie over de complexiteitsscore.
1. Met deze informatie, kan de Ingenieur van de Software de ingewikkeldheid van de verbetering begrijpen en kan deze informatie terug naar de Manager van de Rekening van de partner teruggeven.
1. De accountmanager maakt een tijdlijn en kosten voor de Adobe Commerce-upgrade, zodat de beheerder deze kan goedkeuren.
1. Met de goedkeuring van hun manager, werkt de Ingenieur van de Software aan de vereiste codewijzigingen om de gebroken modules te bevestigen.
1. De software engineer voert de [!DNL Upgrade Compatibility Tool] nog een keer met een Adobe Commerce-pre-release om ervoor te zorgen dat er geen nieuwe problemen zijn en dat de wijzigingen in de code de problemen verholpen die tijdens de bètafase werden gevonden.
1. Alles wordt uitgecheckt en de software engineer stuurt de code naar een testomgeving waar regressietests bevestigen dat alle tests groen zijn, waardoor ze de nieuwste Adobe Commerce-versie kunnen vrijgeven op dezelfde dag dat de Adobe Commerce pre-release wordt uitgebracht.

   ![[!DNL Upgrade Compatibility Tool] publiek](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Een vanilla-instantie is een schone installatie van een opgegeven versietag of vertakking voor een specifieke releaseversie.

## Vereisten

Zie [voorwaarden](../upgrade-compatibility-tool/prerequisites.md) voor meer informatie .

>[!NOTE]
>
>U kunt de [!DNL Upgrade Compatibility Tool] in elk besturingssysteem. Er is geen vereiste om de [!DNL Upgrade Compatibility Tool] waar uw Adobe Commerce-exemplaar zich bevindt. Het is noodzakelijk [!DNL Upgrade Compatibility Tool] om toegang te hebben tot de broncode van de instantie Adobe Commerce. U kunt het hulpprogramma bijvoorbeeld op de ene server installeren en naar de Adobe Commerce-installatie verwijzen op een andere server.

Als u de [!DNL Upgrade Compatibility Tool] bij een Adobe Commerce-instantie met grote modules en bestanden kan het zijn dat voor het hulpprogramma een hoge hoeveelheid RAM nodig is, ten minste 2 GB RAM.

### Aanbevolen acties

De beste praktijken van Adobe Commerce adviseren om het hebben van twee modules met de zelfde naam te vermijden. Als dit gebeurt, wordt [!DNL Upgrade Compatibility Tool] geeft een fout met een segmentatiefout weer.

Als u deze fout wilt voorkomen, kunt u het beste de opdracht `bin` opdracht met de toegevoegde optie `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>De `<dir>` waarde is de map waarin uw Adobe Commerce-instantie zich bevindt.

De `-m` de optie [!DNL Upgrade Compatibility Tool] om elke specifieke module afzonderlijk te analyseren om te voorkomen dat er twee modules met dezelfde naam in uw Adobe Commerce-instantie voorkomen.

Met deze opdrachtoptie kunt u ook [!DNL Upgrade Compatibility Tool] om een map met meerdere modules te analyseren:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Deze aanbeveling helpt ook bij geheugenproblemen die kunnen optreden bij het uitvoeren van de [!DNL Upgrade Compatibility Tool].

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

Adobe raadt u aan contact op te nemen met uw leverancier van extensies om te bepalen of uw extensie volledig compatibel is met Adobe Commerce 2.4.x.

Zie [Het gereedschap uitvoeren](../upgrade-compatibility-tool/run.md) voor informatie over de uitvoering van de [!DNL Upgrade Compatibility Tool].
