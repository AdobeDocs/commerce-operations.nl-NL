---
source-git-commit: 68ea73d407dd3e6daf880a66de8ef4b7bbef2360
workflow-type: tm+mt
source-wordcount: '1656'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versie**: 3.0.16

Deze verwijzing bevat 9 opdrachten die beschikbaar zijn via het `bin/uct` opdrachtregelprogramma.
De eerste lijst wordt automatisch gegenereerd met de opdracht `bin/uct list` op Adobe Commerce.

Meer informatie over het gereedschap in [Overzicht](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>Deze verwijzing wordt gegenereerd op basis van de toepassingscodebase. Als u de inhoud wilt wijzigen, kunt u de broncode voor de corresponderende opdrachtimplementatie bijwerken in het dialoogvenster [codebase](https://github.com/magento) opslaan en uw wijzigingen ter controle verzenden. Een andere manier is om _Feedback geven_ (zoek de koppeling in de rechterbovenhoek). Zie voor richtsnoeren voor bijdragen [Codebijdragen](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Interne opdracht voor suggesties voor shell-voltooiing

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

Het shell-type (&quot;bash&quot;)

- Vereist een waarde

### `--input`, `-i`

Een array van invoertokens (bv. COMP_WORDS of argv)

- Standaard: `[]`
- Vereist een waarde

### `--current`, `-c`

De index van de &quot;input&quot;-array waarin de cursor zich bevindt (bijvoorbeeld COMP_CWORD)

- Vereist een waarde

### `--symfony`, `-S`

De versie van het voltooiingsscript

- Vereist een waarde

### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen opdracht is gegeven, wordt de Help weergegeven voor de \&lt;info>list\&lt;/info> command

- Standaard: `false`
- Accepteert geen waarde

### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde


## `completion`

Het shell-voltooiingsscript dumpen

```bash
bin/uct completion [--debug] [--] [<shell>]
```


### `shell`

Het shell type (bijvoorbeeld &quot;bash&quot;), de waarde van &quot;$SHELL&quot; env var zal worden gebruikt als dit niet wordt gegeven


### `--debug`

Tik op het logbestand voor foutopsporing bij voltooien

- Standaard: `false`
- Accepteert geen waarde

### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen opdracht is gegeven, wordt de Help weergegeven voor de \&lt;info>list\&lt;/info> command

- Standaard: `false`
- Accepteert geen waarde

### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde


## `help`

Help weergeven voor een opdracht

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

De opdrachtnaam

- Standaard: `help`


### `--format`

De uitvoerindeling (txt, xml, json of md)

- Standaard: `txt`
- Vereist een waarde

### `--raw`

Help bij de opdracht Uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen opdracht is gegeven, wordt de Help weergegeven voor de \&lt;info>list\&lt;/info> command

- Standaard: `false`
- Accepteert geen waarde

### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde


## `list`

Lijstopdrachten

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


### `namespace`

De naamruimtenaam


### `--raw`

Naar uitvoer RAW-opdrachtlijst

- Standaard: `false`
- Accepteert geen waarde

### `--format`

De uitvoerindeling (txt, xml, json of md)

- Standaard: `txt`
- Vereist een waarde

### `--short`

Om het beschrijven van de argumenten van bevelen over te slaan

- Standaard: `false`
- Accepteert geen waarde

### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen opdracht is gegeven, wordt de Help weergegeven voor de \&lt;info>list\&lt;/info> command

- Standaard: `false`
- Accepteert geen waarde

### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde


## `refactor`

Hiermee lost u de problemen op die automatisch kunnen worden opgelost. De code in het opgegeven pad wordt bijgewerkt.

```bash
bin/uct refactor <path>
```


### `path`

Pad om problemen op te lossen in.

- Vereist

### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen opdracht is gegeven, wordt de Help weergegeven voor de \&lt;info>list\&lt;/info> command

- Standaard: `false`
- Accepteert geen waarde

### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde


## `core:code:changes`

Het hulpmiddel van de Verenigbaarheid van de Verbetering is een bevel-lijn hulpmiddel dat een instantie van Adobe Commerce tegen een specifieke versie door alle niet-Adobe Commerce modules controleert te analyseren die in het worden geïnstalleerd. Retourneert een lijst met fouten en waarschuwingen die u moet oplossen voordat u een upgrade naar een nieuwe versie van Adobe Commerce-code uitvoert.

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```


### `dir`

Adobe Commerce-installatiemap.

- Vereist

### `vanilla-dir`

Adobe Commerce vanilla-installatiemap.


### `--output`, `-o`

Pad van het bestand waarnaar de uitvoer wordt geëxporteerd (JSON-indeling)

- Accepteert een waarde

### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen opdracht is gegeven, wordt de Help weergegeven voor de \&lt;info>list\&lt;/info> command

- Standaard: `false`
- Accepteert geen waarde

### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde


## `dbschema:diff`

Adobe Commerce DB-schemaverschillen tussen twee geselecteerde versies weergeven. Beschikbare versies: 2.3.0 | 2.3.1. | 2.3.2. | 2.3.2-p2 | 2,3,3 | 2.3.3-p1 | 2.3.4. | 2.3.4-p1 | 2.3.4-p2 | 2.3.5. | 2.3.5-p1 | 2.3.5-p2 | 2.3.6. | 2.3.6-p1 | 2.3.7. | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0. | 2.4.0-p1 | 2.4.1. | 2.4.1-p1 | 2.4.2. | 2.4.2-p1 | 2.4.2-p2 | 2.4.3. | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4. | 2.4.4-p1 | 2.4.5. | 2.4.4-p2 | 2.4.5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2.4.5-p4 | 2.4.6. | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-bèta1 | 2.4.4-p6 | 2.4.5-p5 | 2.4.6-p3 | 2.4.7-bèta2 | 2.4.4-p7 | 2.4.5-p6 | 2.4.6-p4 | 2.4.7-bèta3 | 2.4.7. | 2.4.6-p5 | 2.4.5-p7 | 2.4.4-p8

```bash
bin/uct dbschema:diff <current-version> <target-version>
```


### `current-version`

huidige versie (bijvoorbeeld 2.3.2).

- Vereist

### `target-version`

doelversie (bijvoorbeeld 2.4.5).

- Vereist

### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen opdracht is gegeven, wordt de Help weergegeven voor de \&lt;info>list\&lt;/info> command

- Standaard: `false`
- Accepteert geen waarde

### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde


## `graphql:compare`

Compatibiliteitsverificatie GraphQL-schema

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```


### `schema1`

Eindpunt-URL die verwijst naar het eerste GraphQL-schema.

- Vereist

### `schema2`

Eindpunt-URL die verwijst naar het tweede GraphQL-schema.

- Vereist

### `--output`, `-o`

Pad van het bestand waarnaar de uitvoer wordt geëxporteerd (JSON-indeling)

- Accepteert een waarde

### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen opdracht is gegeven, wordt de Help weergegeven voor de \&lt;info>list\&lt;/info> command

- Standaard: `false`
- Accepteert geen waarde

### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde


## `upgrade:check`

Het hulpmiddel van de Verenigbaarheid van de Verbetering is een bevel-lijn hulpmiddel dat een Adobe Commerce aangepaste instantie tegen een specifieke versie controleert door alle modules te analyseren die in het worden geïnstalleerd. Retourneert een lijst met fouten en waarschuwingen die moeten worden opgelost voordat u de upgrade naar de nieuwste versie van Adobe Commerce uitvoert.

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```


### `dir`

Adobe Commerce-installatiemap.

- Vereist

### `--current-version`, `-a`

De huidige Adobe Commerce-versie, versie van de Adobe Commerce-installatie, wordt gebruikt als deze wordt weggelaten.

- Accepteert een waarde

### `--coming-version`, `-c`

Doel Adobe Commerce-versie. De meest recente, stabiele versie van Adobe Commerce wordt gebruikt als deze wordt weggelaten. Beschikbare Adobe Commerce-versies: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.7-bèta1 \| 2.4.7-bèta2 \| 2.4.7-bèta3 \| 2.4.7.

- Accepteert een waarde

### `--json-output-path`

Pad van het bestand waarin de uitvoer wordt geëxporteerd in de JPEG-indeling

- Accepteert een waarde

### `--html-output-path`

Het pad van het bestand waarnaar de uitvoer wordt geëxporteerd in de indeling HTML.

- Accepteert een waarde

### `--min-issue-level`

Minimale probleeminstelling die u in het rapport wilt zien (waarschuwing, fout of kritiek).

- Standaard: `warning`
- Accepteert een waarde

### `--ignore-current-version-compatibility-issues`, `-i`

Algemene problemen voor huidige en volgende versie negeren

- Standaard: `false`
- Accepteert geen waarde

### `--context`

Uitvoeringcontext. Deze optie is bedoeld voor integratiedoeleinden en heeft geen invloed op het resultaat van de uitvoering.

- Vereist een waarde

### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen opdracht is gegeven, wordt de Help weergegeven voor de \&lt;info>list\&lt;/info> command

- Standaard: `false`
- Accepteert geen waarde

### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde

