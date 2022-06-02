---
title: '"Voer de [!DNL Upgrade Compatibility Tool]"'
description: Voer de volgende stappen uit [!DNL Upgrade Compatibility Tool] op uw Adobe Commerce-project.
source-git-commit: ee949c72e42d329fdfb7f4068aeeb3cdc20e1758
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---


# Download de [!DNL Upgrade Compatibility Tool]

{{commerce-only}

Ga als volgt te werk: [!DNL Upgrade Compatibility Tool] in een bevel-lijn interface, download het door het volgende bevel in werking te stellen:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

>[!NOTE]
>
> Zie de [voorwaarden](../upgrade-compatibility-tool/prerequisites.md) voor meer informatie over de minimumvereisten om het gereedschap te gebruiken.

## Voer de [!DNL Upgrade Compatibility Tool]

De [!DNL Upgrade Compatibility Tool] is een hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie door alle modules controleert te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

De [!DNL Upgrade Compatibility Tool] identificeert potentiële problemen die in uw code moeten worden opgelost alvorens te proberen om aan een nieuwere versie van Adobe Commerce te bevorderen.

Zie dit [videozelfstudie](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) voor meer informatie over de [!DNL Upgrade Compatibility Tool].

## Aanbevolen acties

### De resultaten optimaliseren

De [!DNL Upgrade Compatibility Tool] verstrekt een rapport dat resultaten met alle kwesties bevat die op uw project door gebrek worden geïdentificeerd. U kunt de resultaten optimaliseren om u te concentreren op de problemen die u moet verhelpen om de upgrade te voltooien:

- De optie gebruiken `--ignore-current-version-compatibility-issues`, waarin alle bekende kritieke problemen, fouten en waarschuwingen voor uw huidige Adobe Commerce-versie worden onderdrukt. Er worden alleen fouten weergegeven in de versie waarnaar u wilt upgraden.
- Voeg de `--min-issue-level` kunt u met deze instelling het minimale niveau van de uitgaven instellen, zodat u alleen de belangrijkste problemen met de upgrade kunt oplossen.
- Als u alleen een bepaalde leverancier, module of zelfs map wilt analyseren, kunt u het pad ook als optie opgeven. Voer de `bin` opdracht met de toegevoegde optie `-m`. Hierdoor wordt de [!DNL Upgrade Compatibility Tool] om een specifieke module onafhankelijk te analyseren, en hulp met geheugenkwesties die kunnen voorkomen wanneer het uitvoeren van [!DNL Upgrade Compatibility Tool].

### Aanbevolen procedures voor Adobe Commerce volgen

- Vermijd het gebruik van twee modules met dezelfde naam.
- Adobe Commerce volgen [coderingsnormen](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).

## Gebruik de `upgrade:check` command

De `upgrade:check` is de belangrijkste opdracht om het gereedschap uit te voeren:

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>De `<dir>` waarde is de map waarin uw Adobe Commerce-instantie zich bevindt.

De `upgrade:check` bevel stelt het bevel in werking [!DNL Upgrade Compatibility Tool] en controleert een aangepaste Adobe Commerce-instantie op een specifieke versie door alle daarin geïnstalleerde modules te analyseren. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van uw Adobe Commerce uitvoert.

>[!WARNING]
>
>Uitvoeren slechts wanneer de van de projectwortel (of hoofd) folder wordt verstrekt.

Met deze opdracht wordt gecontroleerd op wijzigingen in de kerncode voor die specifieke Adobe Commerce-instantie en op alle daarin geïnstalleerde wijzigingen in de aangepaste code.

U kunt de `core:code:changes` gebruiken om alleen wijzigingen in kerncode te analyseren voor die specifieke Adobe Commerce-instantie. Zie [Wijzigingen in de kerncode](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) sectie.

U kunt de `graphql:compare` bevel om twee schema&#39;s te vergelijken GraphQL om het even welke veranderingen tussen hen te controleren. Zie de [Compatibiliteitsverificatie van GraphQL-schema](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) sectie.

### Recommendations om de `upgrade:check` command

- De [!DNL Upgrade Compatibility Tool] vereist minstens 2 GB RAM om te kunnen worden uitgevoerd. Deze instelling wordt aanbevolen om problemen te voorkomen vanwege een lage geheugenbeperking. De [!DNL Upgrade Compatibility Tool] geeft een vraag weer als u de `upgrade:check` gebruiken met een lage `memory_limit` instellen.
- Geef de `-m` om het gereedschap uit te voeren op een specifieke module:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Waar de argumenten als volgt zijn:

- `<dir>`: Adobe Commerce-installatiemap.
- `[=MODULE-PATH]`: Specifieke modulepad.

### Gebruik de `--help` option

Als u de [!DNL Upgrade Compatibility Tool] algemene opties en Help gebruiken, uitvoeren:

```bash
bin/uct --help
```

Het is echter mogelijk om `--help` als een optie bij het uitvoeren van een specifieke opdracht, zoals `bin/uct upgrade:check`. Dit retourneert specifiek `--help` opties voor die opdracht:

```bash
bin/uct upgrade:check --help
```

Beschikbaar `--help` opties voor de `upgrade:check` opdracht:

- `-m, --module-path[=MODULE-PATH]`: Pad van de te analyseren modules
- `-a, --current-version[=CURRENT-VERSION]`: Huidige Adobe Commerce-versie, versie van de Adobe Commerce-installatie wordt gebruikt als deze wordt weggelaten.
- `-c, --coming-version[=COMING-VERSION]`: Adobe Commerce-doelversie, nieuwste releaseversie van Adobe Commerce wordt gebruikt als deze wordt weggelaten. Bevat een lijst met alle beschikbare Adobe Commerce-versies.
- `--json-output-path[=JSON-OUTPUT-PATH]`: Pad van het bestand waarin de uitvoer wordt geëxporteerd in de indeling JSON.
- `--html-output-path[=HTML-OUTPUT-PATH]`: Pad van het bestand waarin de uitvoer wordt geëxporteerd in HTML-indeling.
- `--min-issue-level`: Minimaal emissieniveau dat in het rapport moet worden weergegeven. Standaardniveau is [WAARSCHUWING].
- `-i, --ignore-current-version-compatibility-issues`: Gebruik deze optie als u geen bekende kritieke problemen, fouten en waarschuwingen in uw [!DNL Upgrade Compatibility Tool] verslag.
- `--context=CONTEXT`: Uitvoeringcontext. Deze optie is bedoeld voor integratiedoeleinden en heeft geen invloed op het resultaat van de uitvoering.
- `-h, --help`: Help weergeven voor die specifieke opdracht. Als er geen opdracht is opgegeven, `list` is het standaardresultaat.
- `-q, --quiet`: Geen berichten uitvoeren tijdens het uitvoeren van de opdracht.
- `-v, --version`: Toepassingsversie weergeven.
- `--ansi, --no-ansi`: Schakel ANSI-uitvoer in.
- `-n, --no-interaction`: Stel geen interactieve vraag terwijl het uitvoeren van het bevel.
- `-v, --vv, --vvv, --verbose`: Verhoog de breedtegraad van uitvoercommunicatie. 1 voor normale uitvoer, 2 voor uitgebreide uitvoer en 3 voor DEBUG-uitvoer.

### Gebruik de `--ignore-current-version-compatibility-issues` option

De [!DNL Upgrade Compatibility Tool] staat u toe om `upgrade:check` gebruiken met een `--ignore-current-version-compatibility-issues` zodat alleen nieuwe of onbekende kritieke problemen, fouten en waarschuwingen worden weergegeven. Gebruik deze optie als u geen bekende kritieke problemen, fouten en waarschuwingen in uw [!DNL Upgrade Compatibility Tool] verslag.

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>Dit geldt alleen voor PHP API-validaties.

### Vanilla-installatie

A _vanille_ De installatie is een schone installatie van een gespecificeerde versietag of tak voor een specifieke versieversie.

De `bin/uct core:code:changes` controleert of er een vanilla-instantie in uw systeem is. Als dit de eerste keer is met een vanilla-installatie, wordt u met een interactieve opdrachtregelvraag gevraagd het vanilla-project te downloaden van de Adobe Commerce-opslagplaats (`https://repo.magento.com/`).

U kunt een [!DNL Upgrade Compatibility Tool] gebruiken met de `--vanilla-dir` om de installatiemap van Adobe Commerce vanilla op te geven.

Zie de [Instantie vanilla implementeren](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) voor meer informatie.

## Gebruik de `list` command

Om een lijst van terug te keren [!DNL Upgrade Compatibility Tool] beschikbare opdrachten, uitvoeren:

```bash
bin/uct list
```

De `list` retourneert de volgende opdracht:

- `-h, --help`: Help weergeven voor die specifieke opdracht. Als er geen opdracht is opgegeven, `list` is het standaardresultaat.
- `-q, --quiet`: Geen berichten uitvoeren tijdens het uitvoeren van de opdracht.
- `-v, --version`: App-versie weergeven.
- `--ansi, --no-ansi`: Schakel ANSI-uitvoer in.
- `-n, --no-interaction`: Stel geen interactieve vraag terwijl het uitvoeren van het bevel.
- `-v, --vv, --vvv, --verbose`: Verhoog de breedtegraad van uitvoercommunicatie. 1 voor normale uitvoer, 2 voor uitgebreide uitvoer en 3 voor DEBUG-uitvoer.

## Gebruik de `core:code:changes` command

U kunt uw huidige Adobe Commerce-installatie vergelijken met een schone vanilla-installatie om te zien of de kerncode wijzigingen bevat die zijn aangebracht om een nieuwe functie of aanpassing te implementeren. Met deze validatie kunt u een schatting maken van de inspanning die de upgrade vereist op basis van deze wijzigingen.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Waar de argumenten als volgt zijn:

- `<dir>`: Adobe Commerce-installatiemap.
- `<vanilla dir>`: Adobe Commerce vanilla-installatiemap.

Er gelden enkele beperkingen voor het uitvoeren van deze opdracht:

- Uitvoeren slechts wanneer de van de projectwortel (of hoofd) folder wordt verstrekt.
- Hiermee geeft u alleen een lijst met kernwijzigingen weer.

### Gebruik de `core:code:changes` gebruiken met de `--help` option

Beschikbaar `--help` opties voor de `core:code:changes` opdracht:

- `-h, --help`: Help weergeven voor die specifieke opdracht. Als er geen opdracht is opgegeven, `list` is het standaardresultaat.
- `-q, --quiet`: Geen berichten uitvoeren tijdens het uitvoeren van de opdracht.
- `-v, --version`: App-versie weergeven.
- `--ansi, --no-ansi`: Schakel ANSI-uitvoer in.
- `-n, --no-interaction`: Stel geen interactieve vraag terwijl het uitvoeren van het bevel.
- `-v, --vv, --vvv, --verbose`: Verhoog de breedtegraad van uitvoercommunicatie. 1 voor normale uitvoer, 2 voor uitgebreide uitvoer en 3 voor DEBUG-uitvoer.

## Versie

U kunt uw huidige Adobe Commerce-installatie vergelijken met Adobe Commerce-versies `>=2.3`.

U moet de versie als parameter verstrekken wanneer het runnen van het bevel:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

>[!NOTE]
>
>Deze parameter biedt een lijst met alle beschikbare Adobe Commerce-versies.

Waar:

- `-c, --coming-version[=COMING-VERSION]`: De beoogde versie van Adobe Commerce.

Er gelden enkele beperkingen voor het uitvoeren van de vorige opdracht:

- Deze parameter verwijst naar elke tag die een specifieke versie van Adobe Commerce identificeert.
- Het is een vereiste om dit uitdrukkelijk te bepalen; alleen de waarde ervan opgeven werkt niet.
- Geef de versie van de tag zonder aanhalingstekens op (niet enkele of dubbele aanhalingstekens): ~~&quot;2.4.1-ontwikkeling&quot;~~.
- Geef GEEN oudere versies op dan de versie die u momenteel hebt geïnstalleerd, of ouder dan versie 2.3, de oudste versie die op dit moment wordt ondersteund.

### Gebruik de `refactor` command

De [!DNL Upgrade Compatibility Tool] kan automatisch een beperkte set problemen verhelpen:

- Functies die mochten worden gebruikt zonder een argument door te geven, maar met een dergelijk gebruik zijn nu afgekeurd.
- Gebruik van `$this` in Magento sjablonen.
- Gebruik van het trefwoord PHP `final` in methoden van het type private.

Uitvoeren:

```bash
bin/uct refactor <dir>
```

Waar de argumenten als volgt zijn:

- `<dir>`: Adobe Commerce-installatiemap.

## Compatibiliteitsverificatie van GraphQL-schema

De [!DNL Upgrade Compatibility Tool] biedt ook de optie om twee eindpunten GraphQL in te voeren en hun schema&#39;s te vergelijken die breken en gevaarlijke veranderingen tussen hen zoeken:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Waar de argumenten als volgt zijn:

- `<schema1>`: Eindpunt-URL voor de bestaande installatie.
- `<schema2>`: Endpoint URL for the vanilla installation.

U moet actief zijn `instance before` en `instance after` de upgrade.

### GraphQL-opdracht Vergelijken `--help` opties

Beschikbaar `--help` opties voor de `graphql:compare` opdracht:

- `-h, --help`: Help weergeven voor die specifieke opdracht. Als er geen opdracht is opgegeven, `list` is het standaardresultaat.
- `-q, --quiet`: Geen berichten uitvoeren tijdens het uitvoeren van de opdracht.
- `-v, --version`: App-versie weergeven.
- `--ansi, --no-ansi`: Schakel ANSI-uitvoer in.
- `-n, --no-interaction`: Stel geen interactieve vraag terwijl het uitvoeren van het bevel.
- `-v, --vv, --vvv, --verbose`: Verhoog de breedtegraad van uitvoercommunicatie. 1 voor normale uitvoer, 2 voor uitgebreide uitvoer en 3 voor DEBUG-uitvoer.

### Voorbeeld met een lijst van kritieke kwesties, fouten, en waarschuwingen voor GraphQL

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

## Problemen oplossen

### Fout in segmentfout

Wanneer twee modules de zelfde naam hebben [!DNL Upgrade Compatibility Tool] geeft een fout met een segmentatiefout weer.

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

### Lege uitvoer

>[!NOTE]
>
>De `M2_VERSION` Dit is de Adobe Commerce-doelversie die u wilt vergelijken met uw Adobe Commerce-exemplaar.

Indien na het uitvoeren van deze opdracht:

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

De enige uitvoer is `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

De waarschijnlijke oorzaak is een PHP geheugenbeperking.
De geheugenbeperking overschrijven door deze in te stellen `memory_limit` tot `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
