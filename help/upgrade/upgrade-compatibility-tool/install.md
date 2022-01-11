---
title: Het gereedschap Compatibiliteit bijwerken installeren
description: Voer de volgende stappen uit om het hulpprogramma Compatibiliteit bijwerken voor uw Adobe Commerce-project te installeren.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '817'
ht-degree: 0%

---


# Het gereedschap Compatibiliteit bijwerken installeren

Het hulpmiddel van de Verenigbaarheid van de Verbetering is een bevel-lijn hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie controleert door alle modules te analyseren die in het worden geïnstalleerd. Er wordt een lijst met fouten en waarschuwingen geretourneerd die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

## Workflow

In het volgende diagram wordt de verwachte workflow getoond wanneer het gereedschap Compatibiliteit upgraden wordt uitgevoerd:

![Diagram van compatibiliteitsprogramma bijwerken](../../assets/upgrade-guide/mvp-diagram-v3.png)

## Voor wie is het hulpprogramma Compatibiliteit bijwerken?

In het volgende gebruiksgeval wordt het gebruikelijke proces beschreven dat een Adobe Commerce-partner moet doorvoeren om een clientexemplaar te upgraden:

1. De software engineer van een partner downloadt het upgradecompatibiliteitspakket van het [Adobe Commerce-opslagplaats](https://repo.magento.com/) en voert deze uit tijdens de bètafase van de nieuwste Adobe Commerce-versie. Zie de [Het gereedschap Compatibiliteit bijwerken downloaden](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) voor meer informatie.
1. De software engineer genereert een vanilla instantie voor de specifieke versie van Adobe Commerce die momenteel is geïnstalleerd. Zie de [Handleiding voor contribuanten](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) voor meer informatie over het gebruik van de `instance` gebruiken om een vanilleinstallatie te genereren.
1. De software engineer ziet dat er verschillende aangepaste gebieden in de inventarisatie- en catalogusmodules verbroken zijn en ze krijgen ook een complexiteitsscore van X. Zie de [Ontwikkelaar](../upgrade-compatibility-tool/developer.md) voor meer informatie over de complexiteitsscore.
1. Met deze informatie, kan de Ingenieur van de Software de ingewikkeldheid van de verbetering begrijpen en kan deze informatie terug naar de Manager van de Rekening van de partner teruggeven.
1. De accountmanager maakt een tijdlijn en kosten voor de Adobe Commerce-upgrade, zodat de beheerder deze kan goedkeuren.
1. Met de goedkeuring van hun manager, werkt de Ingenieur van de Software aan de vereiste codewijzigingen om de gebroken modules te bevestigen.
1. De software engineer voert het Upgrade Compatibility Tool nog één keer uit met een Adobe Commerce pre-release om ervoor te zorgen dat er geen nieuwe problemen zijn en dat de wijzigingen in de code de problemen verholpen die tijdens de bètafase werden gevonden.
1. Alles wordt uitgecheckt en de software engineer stuurt de code naar een testomgeving waar regressietests bevestigen dat alle tests groen zijn, waardoor ze de nieuwste Adobe Commerce-versie kunnen vrijgeven op dezelfde dag dat de Adobe Commerce pre-release wordt uitgebracht.

   ![Upgradecompatibiliteit publiek](../../assets/upgrade-guide/audience-uct-v3.png)

>[!NOTE]
>
>Een vanilla-instantie is een schone installatie van een opgegeven versietag of vertakking voor een specifieke releaseversie.

## Vereisten

Zie [voorwaarden](../upgrade-compatibility-tool/prerequisites.md) voor meer informatie .

>[!NOTE]
>
>U kunt het gereedschap Compatibiliteit bijwerken op elk besturingssysteem uitvoeren. U hoeft het hulpprogramma voor upgradecompatibiliteit niet uit te voeren op de locatie van uw Adobe Commerce-exemplaar. Het is nodig dat het gereedschap Compatibiliteit upgraden toegang heeft tot de broncode van het Adobe Commerce-exemplaar. U kunt het hulpprogramma bijvoorbeeld op de ene server installeren en naar de Adobe Commerce-installatie verwijzen op een andere server.

Als u het Hulpmiddel van de Verenigbaarheid van de Verbetering tegen een instantie van Adobe Commerce met grote modules en dossiers in werking stelt, zou het hulpmiddel een hoge hoeveelheid RAM, minstens 2 GB RAM kunnen vereisen.

### Aanbevolen acties

De beste praktijken van Adobe Commerce adviseren om het hebben van twee modules met de zelfde naam te vermijden. Als dit gebeurt, toont het Hulpmiddel van de Verenigbaarheid van de Verbetering een fout van de segmenteringsfout.

Als u deze fout wilt voorkomen, kunt u het beste de opdracht `bin` opdracht met de toegevoegde optie `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>De `<dir>` waarde is de map waarin uw Adobe Commerce-instantie zich bevindt.

De `-m` Met het gereedschap Compatibiliteit upgraden kunt u elke specifieke module afzonderlijk analyseren om te voorkomen dat er twee modules met dezelfde naam in uw Adobe Commerce-instantie voorkomen.

Met deze opdrachtoptie kan het gereedschap Compatibiliteit upgraden ook een map analyseren die verschillende modules bevat:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Deze aanbeveling helpt ook bij geheugenproblemen die kunnen optreden wanneer u het gereedschap Compatibiliteit upgraden uitvoert.

## Het gereedschap Compatibiliteit bijwerken downloaden

Voer de volgende opdracht uit om het gereedschap Compatibiliteit bijwerken te downloaden:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

## Installeren

Als u het gereedschap Compatibiliteit bijwerken wilt installeren, moet u de vereiste voorwaarden installeren:

* Adobe Commerce-toegangstoetsen
* Composer
* Node.js

### Adobe Commerce-toegangstoetsen

U moet [Adobe Commerce-toegangstoetsen](https://devdocs.magento.com/marketplace/sellers/profile-information.html#access-keys) om het gereedschap Compatibiliteit bijwerken te downloaden en gebruiken. Voeg je Adobe Commerce toegangstoetsen toe aan je `auth.json` bestand, dat zich bevindt op `~/.composer` standaard.

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

Kloont de opslagplaats voor upgradecompatibiliteitsprogramma&#39;s en voert deze uit `composer install` in uw terminal om gebiedsdelen te installeren.

>[!WARNING]
>
>Als de **Adobe Commerce-toegangstoetsen** niet correct zijn geconfigureerd, wordt het gereedschap Compatibiliteit bijwerken niet geïnstalleerd en worden fouten gegenereerd wanneer het programma `composer install` gebruiken.

### Node.js

Om Node.js te installeren, zie Node.js [documentatie](https://nodejs.dev/learn/how-to-install-nodejs).

## Extensies van derden

Adobe raadt u aan contact op te nemen met uw leverancier van extensies om te bepalen of uw extensie volledig compatibel is met Adobe Commerce 2.4.x.

Zie [Het gereedschap uitvoeren](../upgrade-compatibility-tool/run.md) voor informatie over het uitvoeren van het Hulpmiddel van de Verenigbaarheid van de Verbetering.
