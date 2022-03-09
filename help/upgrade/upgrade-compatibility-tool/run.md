---
title: Voer de [!DNL Upgrade Compatibility Tool]
description: Voer de volgende stappen uit [!DNL Upgrade Compatibility Tool] op uw Adobe Commerce-project.
source-git-commit: bcb8fced43c5d9972291f15a5039dbbc2a692a59
workflow-type: tm+mt
source-wordcount: '1864'
ht-degree: 0%

---


# Voer de [!DNL Upgrade Compatibility Tool]

{{commerce-only}

De [!DNL Upgrade Compatibility Tool] is een opdrachtregelprogramma dat een aangepaste Adobe Commerce-instantie controleert op een specifieke versie door alle daarin geïnstalleerde modules te analyseren. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

De [!DNL Upgrade Compatibility Tool] identificeert potentiële problemen die in uw code moeten worden opgelost alvorens te proberen om aan een nieuwere versie van Adobe Commerce te bevorderen.

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

Terwijl u `graphql:compare` bevel om twee schema&#39;s te vergelijken GraphQL om het even welke veranderingen tussen hen te controleren. Zie [Compatibiliteitsverificatie van GraphQL-schema](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) sectie.

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
- `-c, --coming-version[=COMING-VERSION]`: Adobe Commerce-doelversie, versie van de Adobe Commerce-installatie wordt gebruikt als deze wordt weggelaten.
- `--json-output-path[=JSON-OUTPUT-PATH]`: Pad van het bestand waarin de uitvoer wordt geëxporteerd in de indeling JSON.
- `--html-output-path[=HTML-OUTPUT-PATH]`: Pad van het bestand waarin de uitvoer wordt geëxporteerd in HTML-indeling.
- `--min-issue-level`: Minimaal emissieniveau dat in het rapport moet worden weergegeven. Standaard is [WAARSCHUWING].
- `--ignore-current-version-compatibility-issues`: Gebruik deze optie als u geen bekende kritieke problemen, fouten en waarschuwingen in uw [!DNL Upgrade Compatibility Tool] verslag.
- `--context=CONTEXT`: Uitvoeringcontext. Deze optie is bedoeld voor integratiedoeleinden en heeft geen invloed op het resultaat van de uitvoering.
- `-h, --help`: Help weergeven voor die specifieke opdracht. Als er geen opdracht is opgegeven, `list` is het standaardresultaat.
- `-q, --quiet`: Geen berichten uitvoeren tijdens het uitvoeren van de opdracht.
- `-v, --version`: Toepassingsversie weergeven.
- `--ansi, --no-ansi`: Schakel ANSI-uitvoer in.
- `-n, --no-interaction`: Stel geen interactieve vraag terwijl het uitvoeren van het bevel.
- `-v, --vv, --vvv, --verbose`: Verhoog de breedtegraad van uitvoercommunicatie. 1 voor normale uitvoer, 2 voor uitgebreide uitvoer en 3 voor DEBUG-uitvoer.

### Uitvoer

Als gevolg van de uitgevoerde analyse [!DNL Upgrade Compatibility Tool] Hiermee wordt een rapport geëxporteerd dat een lijst met problemen voor elk bestand bevat waarin de ernst, foutcode en beschrijving van de fout worden vermeld.

Zie het onderstaande voorbeeld:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Controleer de [Verwijzing naar foutbericht](error-messages.md) voor meer informatie.

Het verslag bevat ook een gedetailleerde samenvatting die het volgende laat zien:

- *Huidige versie*: de versie die momenteel is geïnstalleerd.
- *Doelversie*: de versie waarnaar u wilt upgraden.
- *Uitvoeringstijd*: de hoeveelheid tijd die de analyse nodig had om het rapport op te stellen (mm:ss).
- *Modules die update vereisen*: het percentage modules dat compatibiliteitsproblemen bevat en moet worden bijgewerkt.
- *Bestanden die moeten worden bijgewerkt*: het percentage bestanden dat compatibiliteitsproblemen bevat en moet worden bijgewerkt.
- *Totaal aantal kritieke fouten*: het aantal aangetroffen kritieke fouten.
- *Totaal aantal fouten*: het aantal gevonden fouten.
- *Totaal aantal waarschuwingen*: het aantal gevonden waarschuwingen.

Zie het onderstaande voorbeeld:

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>Standaard worden de [!DNL Upgrade Compatibility Tool] het rapport wordt in twee verschillende formaten geëxporteerd: `json` en `html`.

#### JSON

Het JSON-bestand bevat exact dezelfde informatie als wordt weergegeven bij uitvoer:

- Lijst van de geïdentificeerde problemen.
- Samenvatting van de analyse.

Voor elke ondervonden kwestie, verstrekt het rapport gedetailleerde informatie zoals de ernst en de beschrijving van het probleem.

>[!NOTE]
>
>Het standaardpad voor de uitvoermap is `var/output/[TIME]-results.json`.

Voer de volgende handelingen uit om dit rapport naar een andere uitvoermap te exporteren:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Waar de argumenten als volgt zijn:

- `<dir>`: Adobe Commerce-installatiemap.
- `[=JSON-OUTPUT-PATH]`: Padmap om het pad te exporteren `.json` uitvoerbestand.

>[!NOTE]
>
>Het standaardpad voor de uitvoermap is `var/output/[TIME]-results.json`.

#### HTML

Het HTML-bestand bevat ook een lijst met geïdentificeerde problemen en een overzicht van de analyse. Het omvat ook vier verschillende grafieken:

- **Modules naar uitgifteernst**: Toont strengheidsverdeling door modules.
- **Bestanden met de ernst van de uitgave**: Hiermee geeft u de verdeling van de ernst per bestand weer.
- **Modules geordend op totaal aantal emissies**: Toont de 10 meest gecompromitteerde modules rekening houdend met waarschuwingen, fouten, en kritieke fouten.
- **Modules met relatieve grootten en problemen**: Hoe meer bestanden een module bevat, hoe groter de cirkel. Hoe meer problemen een module heeft, hoe meer rood de cirkel wordt weergegeven.

Met deze grafieken kunt u (in één oogopslag) de onderdelen identificeren die het meest gecompromitteerd zijn en die waarvoor meer werk nodig is om een upgrade uit te voeren.

![HTML-rapport - Samenvatting](../../assets/upgrade-guide/uct-html-summary.png)

![HTML-rapport - Details](../../assets/upgrade-guide/uct-html-details.png)

Dit rapport exporteren naar een andere uitvoermap:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Waar de argumenten als volgt zijn:

- `<dir>`: installatiemap {site.data.var.ee} .
- `[=HTML-OUTPUT-PATH]`: Padmap om het pad te exporteren `.html` uitvoerbestand.

>[!NOTE]
>
>Het standaardpad voor de uitvoermap is `var/output/[TIME]-results.html`.

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

De `bin/uct core:code:changes` controleert of er een vanilla-instantie in uw systeem is. Als dit de eerste keer gebruikend een vanilla installatie is, een interactieve bevel-lijn vraag u ertoe aanzet om het vanilla project van te downloaden [Adobe Commerce-opslagplaats](https://repo.magento.com/).

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

Zie [Informatie over ontwikkelaars](../upgrade-compatibility-tool/developer.md) voor meer informatie .

U kunt de [!DNL Upgrade Compatibility Tool] met een uitvoeringsconfiguratie via de insteekmodule PhpStorm. Zie de [[!DNL Upgrade Compatibility Tool] Configuratie uitvoeren](https://devdocs.magento.com/guides/v2.3/ext-best-practices/phpstorm/uct-run-configuration.html) voor meer informatie.

## Aanbevolen acties

### De resultaten optimaliseren

De [!DNL Upgrade Compatibility Tool] verstrekt een rapport dat resultaten met alle kwesties bevat die op uw project door gebrek worden geïdentificeerd. U kunt de resultaten optimaliseren om u te concentreren op de problemen die u moet verhelpen om de upgrade te voltooien:

- De optie gebruiken `--ignore-current-version-compatibility-issues`, waarin alle bekende kritieke problemen, fouten en waarschuwingen voor uw huidige Adobe Commerce-versie worden onderdrukt. Er worden alleen fouten weergegeven in de versie waarnaar u wilt upgraden.
- Voeg de `--min-issue-level` kunt u met deze instelling het minimale niveau van de uitgaven instellen, zodat u alleen de belangrijkste problemen met de upgrade kunt oplossen. Als u alleen een bepaalde leverancier, module of zelfs map wilt analyseren, kunt u het pad ook als optie opgeven.
- Voer de `bin` opdracht met de toegevoegde optie `-m`. Hierdoor wordt de [!DNL Upgrade Compatibility Tool] om een specifieke module onafhankelijk te analyseren, en hulp met geheugenkwesties die kunnen voorkomen wanneer het uitvoeren van [!DNL Upgrade Compatibility Tool].

### Aanbevolen procedures voor Adobe Commerce volgen

- Vermijd het gebruik van twee modules met dezelfde naam.
- Adobe Commerce volgen [coderingsnormen](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).

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
