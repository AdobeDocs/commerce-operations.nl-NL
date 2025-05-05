---
title: Voer  [!DNL Upgrade Compatibility Tool] in
description: Volg deze stappen om  [!DNL Upgrade Compatibility Tool]  in een bevel-lijn interface voor uw project van Adobe Commerce in werking te stellen.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%

---

# Download de [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Als u wilt beginnen met de [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface, downloadt u deze via de volgende opdracht:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

U moet mogelijk uitvoerbare machtigingen voor het gereedschap opgeven met de opdracht `chmod` :

```bash
chmod +x ./uct/bin/uct
```

## De [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface

[!DNL Upgrade Compatibility Tool] is een hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie door alle modules controleert te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

Zie dit [ videoleerprogramma ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=nl-NL) (06:02) om meer over [!DNL Upgrade Compatibility Tool] te leren.

Beschikbare opdrachten voor de [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface:

| **Bevel** | **Beschrijving** |
|----------------|-----------------|
| `upgrade:check` | Met deze opdracht voert u de [!DNL Upgrade Compatibility Tool] uit door alle daarin geïnstalleerde modules te analyseren. |
| `dbschema:diff` | Met deze opdracht worden alle verschillen tussen de twee opgegeven Adobe Commerce-versies van het databaseschema weergegeven. |
| `core:code:changes` | Met deze opdracht vergelijkt u de huidige Adobe Commerce-installatie met een schone vanilleinstallatie. |
| `refactor` | Met deze opdracht corrigeert u automatisch een beperkte set problemen. |
| `graphql:compare` | Dit bevel verstrekt de optie om twee eindpunten van GraphQL in te voeren en hun schema&#39;s te vergelijken. |
| `list` | Deze opdracht retourneert een lijst met alle [!DNL Upgrade Compatibility Tool] beschikbare opdrachten. |
| `help` | Dit bevel keert alle beschikbare `help` opties voor [!DNL Upgrade Compatibility Tool] terug. Dit bevel kan evenals een optie met de vorige bevelen in werking worden gesteld. |

## De opdracht `upgrade:check` gebruiken

De opdracht `upgrade:check` controleert op kerncodewijzigingen voor die specifieke Adobe Commerce-instantie en alle daarin geïnstalleerde aangepaste codewijzigingen.

De opdracht `upgrade:check` is de belangrijkste opdracht voor het uitvoeren van het gereedschap:

```bash
bin/uct upgrade:check <dir>
```

Waar `<dir>` -waarde de map is waarin uw Adobe Commerce-instantie zich bevindt.

Beschikbare opties voor de opdracht `upgrade:check` :

| **Bevel** | **Beschikbare opties** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Geeft alle beschikbare opties.</li><li>—huidige versie: huidige Adobe Commerce-versie. Deze parameter is vereist en moet altijd worden gebruikt.</li><li>—min-issue-level: U kunt kwesties filtreren volgens het minimumemissieniveau (de standaardwaarde is WAARSCHUWING).</li><li>—ignore-current-version-Compatibility-issues (of -i): Als u geen kritieke kwesties, fouten, en waarschuwingen van de huidige versie in uw rapport wilt omvatten.</li><li>—komende versie (of -c): doel een specifieke Adobe Commerce-versie. Als u deze optie weglaat, wordt de meest recente versie gebruikt.</li></ul> |

Met [!DNL Upgrade Compatibility Tool] kunt u de opdracht `upgrade:check` uitvoeren met een optie `--ignore-current-version-compatibility-issues` . Gebruik deze optie als u alleen nieuwe uitgaven wilt ophalen die worden geïntroduceerd met de update van uw huidige versie naar de doelversie in uw [!DNL Upgrade Compatibility Tool] -rapport:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Dit geldt alleen voor PHP API-validaties.

### De optie `--coming-version` toevoegen

Met de optie `--coming-version` kunt u de huidige Adobe Commerce-installatie vergelijken met elke Adobe Commerce-versie `>=2.3` .

U moet de versie opgeven als parameter wanneer u de opdracht `upgrade:check` uitvoert:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Waar `-c, --coming-version[=COMING-VERSION]` verwijst naar de beoogde Adobe Commerce-versie.

Er zijn enkele beperkingen wanneer u `--coming-version` uitvoert:

- Deze parameter verwijst naar elke tag die een specifieke versie van Adobe Commerce identificeert.
- Het is een vereiste om dit uitdrukkelijk te verstrekken; het verstrekken van slechts de waarde van het werkt niet.
- Verstrek de markeringsversie zonder enige of dubbele aanhalingstekens (noch enkel noch dubbel): ~~&quot;2.4.1-develop&#39;~~.
- Geef GEEN oudere versies op dan de versie die u momenteel hebt geïnstalleerd, of ouder dan versie 2.3, de oudste versie die op dit moment wordt ondersteund.

## De opdracht `dbschema:diff` gebruiken

U kunt het verschil tussen het databaseschema van twee Adobe Commerce-versies ophalen.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Waar de argumenten als volgt zijn:

- `<current-version>`: elke Adobe Commerce-versie die kan worden vergeleken.
- `<target-version>`: ook elke Adobe Commerce-versie die kan worden vergeleken.

Voorbeeld van uitvoering:

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## De opdracht `core:code:changes` gebruiken

U kunt uw huidige Adobe Commerce-installatie vergelijken om te valideren of de kerncode van Adobe Commerce is gewijzigd om een aanpassing te implementeren. Dit bevel toont een lijst van kernwijzigingen slechts:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Waar de argumenten als volgt zijn:

- `<dir>`: Adobe Commerce-installatiemap.
- `<vanilla dir>`: Adobe Commerce vanilla-installatiemap.

Beschikbare opties voor de opdracht `core:code:changes` :

| **Bevel** | **Beschikbare opties** |
|----------------|-----------------|
| `core:code:changes` | `--help`: retourneert alle beschikbare `--help` -opties. |

>[!NOTE]
>
> Het wordt aanbevolen aangepaste code buiten de kerncode te houden. Zie Adobe Commerce 2.4 [ verbeteringsgids ](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=nl-NL) voor meer verbeteringsbeste praktijken.

### Vanilla-installatie

A _vanilla_ installatie is een schone installatie van een gespecificeerde versiemarkering of tak voor een specifieke versieversie.

De opdracht `bin/uct core:code:changes` controleert of er een vanilla-instantie in uw systeem is. Als dit de eerste keer gebruikend een vanilla installatie is, een interactieve bevel-lijn vraag u ertoe aanzet om het vanilleproject van de bewaarplaats van Adobe Commerce (`https://repo.magento.com/`) te downloaden.

U kunt een opdracht [!DNL Upgrade Compatibility Tool] uitvoeren met de optie `--vanilla-dir` om de installatiemap van Adobe Commerce vanilla op te geven.

Zie [ opstellen vanilla instantie ](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) onderwerp voor meer informatie.

## De opdracht `refactor` gebruiken

Met [!DNL Upgrade Compatibility Tool] kunt u automatisch een beperkte set problemen verhelpen:

- Functies die mochten worden gebruikt zonder een argument door te geven, maar met een dergelijk gebruik zijn nu vervangen.
- Gebruik van `$this` in sjablonen voor Magento&#39;s.
- Gebruik van het trefwoord PHP `final` in methoden van het type private.

Hiervoor voert u de opdracht `refactor` uit:

```bash
bin/uct refactor <dir>
```

Waar `<dir>` -waarde de map is waarin uw Adobe Commerce-instantie zich bevindt.

Beschikbare opties voor de opdracht `refactor` :

| **Bevel** | **Beschikbare opties** |
|----------------|-----------------|
| `refactor` | `--help`: retourneert alle beschikbare `--help` -opties. |

## De opdracht `graphql:compare` gebruiken

Deze opdracht biedt de [!DNL Upgrade Compatibility Tool] de mogelijkheid om twee GraphQL-eindpunten te bekijken en hun schema&#39;s te vergelijken op zoek naar onderbrekingen en gevaarlijke wijzigingen:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Waar de argumenten als volgt zijn:

- `<schema1>`: URL van eindpunt voor de bestaande installatie.
- `<schema2>`: eindpunt-URL voor de vanilla-installatie.

Beschikbare opties voor de opdracht `graphql:compare` :

| **Bevel** | **Beschikbare opties** |
|----------------|-----------------|
| `graphql:compare` | `--help`: retourneert alle beschikbare `--help` -opties. |

## De opdracht `list` gebruiken

Voer de volgende handelingen uit om een lijst met de [!DNL Upgrade Compatibility Tool] beschikbare opdrachten te retourneren:

```bash
bin/uct list
```

## De opdracht `help` gebruiken

Voer de volgende handelingen uit om de algemene opties en Help van de opdracht [!DNL Upgrade Compatibility Tool] weer te geven:

```bash
bin/uct --help
```

Dit retourneert een lijst met alle beschikbare `help` -opties voor de [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface:

```
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

`--help` kan als optie worden uitgevoerd wanneer een bepaalde opdracht wordt uitgevoerd. Er worden `--help` -opties voor de opgegeven opdracht geretourneerd.

Voorbeeld van de optie `upgrade:check` command met `--help` :

```bash
bin/uct upgrade:check --help
```

Hiermee worden specifieke opties geretourneerd die voor de opdracht `upgrade:check` kunnen worden uitgevoerd:

```
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## Aanbevolen procedures voor Adobe Commerce volgen

- Vermijd het gebruik van twee modules met dezelfde naam.
- Volg Adobe Commerce [ coderingsnormen ](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [ de gids van de Verbetering ](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf?lang=nl-NL) beste praktijken.
- Stel [!DNL Upgrade Compatibility Tool] van [[!DNL Site-Wide Analysis Tool] in werking ](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html?lang=nl-NL) voor [ Adobe Commerce op de projecten van de wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html?lang=nl-NL){target=_blank} .

## De resultaten optimaliseren

[!DNL Upgrade Compatibility Tool] verstrekt een rapport dat resultaten met alle kwesties bevat die op uw project door gebrek worden geïdentificeerd. U kunt de resultaten optimaliseren om u te concentreren op de problemen die u moet verhelpen om de upgrade te voltooien:

- Gebruik de optie `--ignore-current-version-compatibility-issues` als u alleen nieuwe uitgaven wilt ophalen die worden geïntroduceerd met de update van uw huidige versie naar de doelversie in uw [!DNL Upgrade Compatibility Tool] -rapport.
- Door de optie `--min-issue-level` toe te voegen, kunt u met deze instelling het minimale niveau van de uitgave instellen, zodat alleen de belangrijkste problemen met de upgrade prioriteit krijgen.
- Voor het uitvoeren van [!DNL Upgrade Compatibility Tool] is minstens 2 GB RAM vereist. Deze instelling wordt aanbevolen om problemen te voorkomen die te wijten zijn aan een lage geheugenbeperking. In [!DNL Upgrade Compatibility Tool] wordt een vraag weergegeven als u de opdracht `upgrade:check` uitvoert met een lage instelling `memory_limit` .
