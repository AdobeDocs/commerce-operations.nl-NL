---
title: '"Voer de [!DNL Upgrade Compatibility Tool]"'
description: Voer de volgende stappen uit [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface voor uw Adobe Commerce-project.
source-git-commit: a0bb188eea38688c5bfe68e8c6bb7b3d040f5e0a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Download de [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Ga als volgt te werk: [!DNL Upgrade Compatibility Tool] in een bevel-lijn interface, download het door het volgende bevel in werking te stellen:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Mogelijk moet u de uitvoerbare machtigingen voor het gereedschap opgeven bij de `chmod` opdracht:

```bash
chmod +x ./uct/bin/uct
```

## De [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface

De [!DNL Upgrade Compatibility Tool] is een hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie door alle modules controleert te analyseren die in het worden geïnstalleerd. Er wordt een lijst geretourneerd met kritieke problemen, fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

Zie dit [videozelfstudie](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) voor meer informatie over de [!DNL Upgrade Compatibility Tool].

Beschikbare opdrachten voor de [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface:

| **Opdracht** | **Beschrijving** |
|----------------|-----------------|
| `upgrade:check` | Met deze opdracht wordt de opdracht [!DNL Upgrade Compatibility Tool] door alle daarin geïnstalleerde modules te analyseren. |
| `core:code:changes` | Met deze opdracht vergelijkt u de huidige Adobe Commerce-installatie met een schone vanilleinstallatie. |
| `refactor` | Met deze opdracht corrigeert u automatisch een beperkte set problemen. |
| `graphql:compare` | Dit bevel verstrekt de optie om twee eindpunten te introspecteren GraphQL en hun schema&#39;s te vergelijken. |
| `list` | Deze opdracht geeft een lijst met alle [!DNL Upgrade Compatibility Tool] beschikbare opdrachten. |
| `help` | Deze opdracht retourneert alle beschikbare `help`opties voor de [!DNL Upgrade Compatibility Tool]. Dit bevel kan evenals een optie met de vorige bevelen in werking worden gesteld. |

## Gebruik de `upgrade:check` command

De `upgrade:check` controleert de opdracht of er kerncodewijzigingen zijn aangebracht voor die specifieke Adobe Commerce-instantie en of alle daarin geïnstalleerde wijzigingen in de aangepaste code worden doorgevoerd.

De `upgrade:check` is de belangrijkste opdracht om het gereedschap uit te voeren:

```bash
bin/uct upgrade:check <dir>
```

Wanneer `<dir>` waarde is de map waarin uw Adobe Commerce-instantie zich bevindt.

Beschikbare opties voor de `upgrade:check` opdracht:

| **Opdracht** | **Beschikbare opties** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Retourneert alle beschikbare opties.</li><li>—min-issue-level: U kunt problemen filteren op basis van het minimale uitgifteniveau (de standaardwaarde is WAARSCHUWING).</li><li>—ignore-current-version-compatibility-issues (or -i): Als u geen kritieke kwesties, fouten en waarschuwingen van de huidige versie in uw rapport wilt omvatten.</li><li>—volgende versie (of -c): Kies een specifieke Adobe Commerce-versie.</li></ul> |

De [!DNL Upgrade Compatibility Tool] staat u toe om `upgrade:check` gebruiken met een `--ignore-current-version-compatibility-issues` optie. Gebruik deze optie als u alleen nieuwe uitgaven wilt ophalen die worden geïntroduceerd met de update van uw huidige versie naar de doelversie in uw [!DNL Upgrade Compatibility Tool] rapport:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Dit geldt alleen voor PHP API-validaties.

### Het toevoegen van `--coming-version` option

U kunt uw huidige Adobe Commerce-installatie vergelijken met elke Adobe Commerce-versie `>=2.3` door `--coming-version` optie.

U moet de versie opgeven als parameter wanneer u de `upgrade:check` opdracht:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Wanneer `-c, --coming-version[=COMING-VERSION]` verwijst naar de beoogde versie van Adobe Commerce.

Er zijn enkele beperkingen wanneer u de `--coming-version`:

- Deze parameter verwijst naar elke tag die een specifieke versie van Adobe Commerce identificeert.
- Het is een vereiste om dit uitdrukkelijk te bepalen; alleen de waarde ervan opgeven werkt niet.
- Geef de versie van de tag zonder aanhalingstekens op (niet enkele of dubbele aanhalingstekens): ~~&quot;2.4.1-ontwikkeling&quot;~~.
- Geef GEEN oudere versies op dan de versie die u momenteel hebt geïnstalleerd, of ouder dan versie 2.3, de oudste versie die op dit moment wordt ondersteund.

## Gebruik de `core:code:changes` command

U kunt uw huidige Adobe Commerce-installatie vergelijken om te valideren of de kerncode van Adobe Commerce is gewijzigd om een aanpassing te implementeren. Dit bevel toont een lijst van kernwijzigingen slechts:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Waar de argumenten als volgt zijn:

- `<dir>`: Adobe Commerce-installatiemap.
- `<vanilla dir>`: Adobe Commerce vanilla-installatiemap.

Beschikbare opties voor de `core:code:changes` opdracht:

| **Opdracht** | **Beschikbare opties** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Hiermee worden alle beschikbare gegevens geretourneerd `--help` opties. |

>[!NOTE]
>
> Het wordt aanbevolen aangepaste code buiten de kerncode te houden. Zie Adobe Commerce 2.4 [upgradehulplijn](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) voor meer verbetering beste praktijken.

### Vanilla-installatie

A _vanille_ De installatie is een schone installatie van een gespecificeerde versietag of tak voor een specifieke versieversie.

De `bin/uct core:code:changes` controleert of er een vanilla-instantie in uw systeem is. Als dit de eerste keer is met een vanilla-installatie, wordt u met een interactieve opdrachtregelvraag gevraagd het vanilla-project te downloaden van de Adobe Commerce-opslagplaats (`https://repo.magento.com/`).

U kunt een [!DNL Upgrade Compatibility Tool] gebruiken met de `--vanilla-dir` om de installatiemap van Adobe Commerce vanilla op te geven.

Zie de [Instantie vanilla implementeren](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) voor meer informatie.

## Gebruik de `refactor` command

De [!DNL Upgrade Compatibility Tool] kan automatisch een beperkte set problemen verhelpen:

- Functies die mochten worden gebruikt zonder een argument door te geven, maar met een dergelijk gebruik zijn nu afgekeurd.
- Gebruik van `$this` in Magento sjablonen.
- Gebruik van het trefwoord PHP `final` in methoden van het type private.

Hiervoor voert u de opdracht `refactor` opdracht:

```bash
bin/uct refactor <dir>
```

Wanneer `<dir>` waarde is de map waarin uw Adobe Commerce-instantie zich bevindt.

Beschikbare opties voor de `refactor` opdracht:

| **Opdracht** | **Beschikbare opties** |
|----------------|-----------------|
| `refactor` | `--help`: Hiermee worden alle beschikbare gegevens geretourneerd `--help` opties. |

## Gebruik de `graphql:compare` command

Deze opdracht biedt de optie voor de [!DNL Upgrade Compatibility Tool] om twee eindpunten GraphQL in te voeren en hun schema&#39;s te vergelijken die breken en gevaarlijke veranderingen tussen hen zoeken:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Waar de argumenten als volgt zijn:

- `<schema1>`: Eindpunt-URL voor de bestaande installatie.
- `<schema2>`: Endpoint URL for the vanilla installation.

Beschikbare opties voor de `graphql:compare` opdracht:

| **Opdracht** | **Beschikbare opties** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Hiermee worden alle beschikbare gegevens geretourneerd `--help` opties. |

## Gebruik de `list` command

Om een lijst van terug te keren [!DNL Upgrade Compatibility Tool] beschikbare opdrachten, uitvoeren:

```bash
bin/uct list
```

## Gebruik de `--help` command

Als u de [!DNL Upgrade Compatibility Tool] algemene opties en Help gebruiken, uitvoeren:

```bash
bin/uct --help
```

Hiermee wordt een lijst met alle beschikbare gegevens geretourneerd `help` opties voor de [!DNL Upgrade Compatibility Tool] in een opdrachtregelinterface:

```terminal
- -m, --module-path[=MODULE-PATH]: Path of the modules to be analysed
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

Het is echter mogelijk om `--help` als een optie bij het uitvoeren van een specifieke opdracht. Hiermee wordt specifiek `--help` opties voor die specifieke opdracht.

Voorbeeld van het `upgrade:check` gebruiken met `--help` optie:

```bash
bin/uct upgrade:check --help
```

Hiermee worden specifieke opties geretourneerd die kunnen worden uitgevoerd voor de `upgrade:check` opdracht:

```terminal
--min-issue-level.
-i, --ignore-current-version-compatibility-issues.
```

## Aanbevolen procedures voor Adobe Commerce volgen

- Vermijd het gebruik van twee modules met dezelfde naam.
- Adobe Commerce volgen [coderingsnormen](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).
- Adobe Commerce 2.4 [Upgradehulplijn](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) beste praktijken.

## De resultaten optimaliseren

De [!DNL Upgrade Compatibility Tool] verstrekt een rapport dat resultaten met alle kwesties bevat die op uw project door gebrek worden geïdentificeerd. U kunt de resultaten optimaliseren om u te concentreren op de problemen die u moet verhelpen om de upgrade te voltooien:

- De optie gebruiken `--ignore-current-version-compatibility-issues` als u alleen nieuwe uitgaven wilt ophalen die worden geïntroduceerd met de update van uw huidige versie naar de doelversie in uw [!DNL Upgrade Compatibility Tool] verslag.
- Het toevoegen van `--min-issue-level` kunt u met deze instelling het minimale niveau van de uitgaven instellen, zodat u alleen de belangrijkste problemen met de upgrade kunt oplossen.
- De [!DNL Upgrade Compatibility Tool] vereist minstens 2 GB RAM om te kunnen worden uitgevoerd. Deze instelling wordt aanbevolen om problemen te voorkomen vanwege een lage geheugenbeperking. De [!DNL Upgrade Compatibility Tool] geeft een vraag weer als u de `upgrade:check` gebruiken met een lage `memory_limit` instellen.
- Als u alleen een bepaalde leverancier, module of zelfs map wilt analyseren, kunt u het pad ook als optie opgeven. Voer de `bin` opdracht met de toegevoegde optie `-m`. Hierdoor wordt de [!DNL Upgrade Compatibility Tool] om een specifieke module onafhankelijk te analyseren, en hulp met geheugenkwesties die kunnen voorkomen wanneer het uitvoeren van [!DNL Upgrade Compatibility Tool]. Geef de `-m` om het gereedschap uit te voeren op een specifieke module:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Waar de argumenten als volgt zijn:

- `<dir>`: Adobe Commerce-installatiemap.
- `[=MODULE-PATH]`: Specifieke modulepad.
