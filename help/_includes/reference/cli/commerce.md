---
source-git-commit: ebd32f3fac571efa729122d0e84471b6de540630
workflow-type: tm+mt
source-wordcount: '19002'
ht-degree: 0%

---
# magento-cloud (Adobe Commerce op cloudinfrastructuur)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versie**: 1.38.1. <!-- app.version -->

Deze verwijzing bevat 127 bevelen beschikbaar door `magento-cloud` opdrachtregelprogramma.
De eerste lijst wordt automatisch gegenereerd met de opdracht `magento-cloud list` in de editie.

>[!NOTE]
>
>Deze verwijzing wordt gegenereerd op basis van de codebase van de toepassing. Als u de inhoud wilt wijzigen, kunt u de broncode voor de corresponderende opdrachtimplementatie bijwerken in het dialoogvenster [codebase](https://github.com/magento) opslaan en uw wijzigingen ter controle verzenden. Een andere manier is om _Feedback geven_ (zoek de koppeling in de rechterbovenhoek). Zie voor richtsnoeren voor bijdragen [Codebijdragen](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

BASH-voltooiingshaak.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--generate-hook`, `-g`



BASH-code genereren waarmee de voltooiing van deze toepassing wordt ingesteld.
- Standaard: `false`
- Accepteert geen waarde



### `--program`, `-p`



Programmanaam die voltooiing zou moeten teweegbrengen &lt;comment>(wordt standaard ingesteld op het absolute pad van de toepassing)&lt;/comment>.
- Vereist een waarde



### `--multiple`, `-m`



De geproduceerde haak kan voor veelvoudige toepassingen worden gebruikt.
- Standaard: `false`
- Accepteert geen waarde


### `--shell-type`

Stel het shell-type (zsh of bash) in. Anders wordt dit automatisch bepaald.
- Accepteert een waarde <!-- options --> <!-- options.size -->

## `bot`

De Magento Cloud Bot

```bash
magento-cloud bot [--party] [--parrot]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--party`


- Standaard: `false`
- Accepteert geen waarde


### `--parrot`


- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `clear-cache`

De CLI-cache wissen

```bash
magento-cloud clear-cache
```

<!-- app.name -->

```bash
clearcache
```

<!-- app.name -->

```bash
cc
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `decode`

Een gecodeerde tekenreeks decoderen, zoals MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```

<!-- app.name --> <!-- command.usage -->

### `value`

De te decoderen variabelewaarde
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



De eigenschap die binnen de variabele moet worden weergegeven
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `docs`

De onlinedocumentatie openen

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```

<!-- app.name --> <!-- command.usage -->

### `search`

Zoekterm(en)

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--browser`

De browser die moet worden gebruikt om de URL te openen. Stel 0 in voor geen.
- Vereist een waarde


### `--pipe`

Voer de URL uit die u wilt stopzetten.
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `help`

Hiermee geeft u Help voor een opdracht weer

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

De opdrachtnaam
- Standaard: `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--format`

De uitvoerindeling (txt, xml, json of md)
- Standaard: `txt`
- Vereist een waarde


### `--raw`

Help bij de opdracht Uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `legacy-migrate`

Migreren vanuit de oude bestandsstructuur

```bash
magento-cloud legacy-migrate [--no-backup]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-backup`

Maak geen back-up van het project.
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `list`

Lijsten, opdrachten

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

De naamruimtenaam
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Naar uitvoer RAW-opdrachtlijst
- Standaard: `false`
- Accepteert geen waarde


### `--format`

De uitvoerindeling (txt, xml, json of md)
- Standaard: `txt`
- Vereist een waarde <!-- options --> <!-- options.size -->

## `multi`

Voer een bevel op veelvoudige projecten uit

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

De uit te voeren opdracht
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--projects`, `-p`



Een lijst met project-id&#39;s, gescheiden door komma&#39;s en/of witruimte
- Vereist een waarde


### `--continue`

Doorgaan met opdrachten, zelfs als een uitzondering wordt aangetroffen
- Standaard: `false`
- Accepteert geen waarde


### `--sort`

Een eigenschap waarmee de lijst met projectopties moet worden gesorteerd
- Standaard: `title`
- Vereist een waarde


### `--reverse`

De volgorde van projectopties omkeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `web`

De webinterface openen

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--browser`

De browser die moet worden gebruikt om de URL te openen. Stel 0 in voor geen.
- Vereist een waarde


### `--pipe`

Voer de URL uit die u wilt stopzetten.
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `welcome`

Welkom bij Magento Cloud

```bash
magento-cloud welcome
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `winky`



```bash
magento-cloud winky
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `activity:cancel`

Een activiteit annuleren

```bash
magento-cloud activity:cancel [--type TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

De activiteit-id. Wordt standaard ingesteld op de meest recente annuleerbare activiteit.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Filteren op type (bij het selecteren van een standaardactiviteit)
- Vereist een waarde



### `--all`, `-a`



Recente activiteiten in alle omgevingen controleren (bij het selecteren van een standaardactiviteit)
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `activity:get`

Gedetailleerde informatie over één activiteit weergeven

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

De activiteit-id. Wordt standaard ingesteld op de meest recente activiteit.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



De eigenschap die moet worden weergegeven
- Vereist een waarde


### `--type`

Filteren op type (bij het selecteren van een standaardactiviteit)
- Vereist een waarde


### `--state`

Filteren op status (bij het selecteren van een standaardactiviteit): in_progress, in behandeling, voltooid of geannuleerd
- Standaard: `[]`
- Vereist een waarde


### `--result`

Filteren op resultaat (bij het selecteren van een standaardactiviteit): succes of mislukking
- Vereist een waarde



### `--incomplete`, `-i`



Alleen onvolledige activiteiten opnemen (bij het selecteren van een standaardactiviteit). Dit is een verkorte versie voor &lt;info>—state=in_progress,in behandeling&lt;/info>
- Standaard: `false`
- Accepteert geen waarde



### `--all`, `-a`



Recente activiteiten in alle omgevingen controleren (bij het selecteren van een standaardactiviteit)
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `activity:list`

Een lijst met activiteiten voor een omgeving of project ophalen

```bash
magento-cloud activity:list [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
activities
```

<!-- app.name -->

```bash
act
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

Filteractiviteiten per type
- Vereist een waarde


### `--limit`

Beperk het aantal weergegeven resultaten
- Standaard: `10`
- Vereist een waarde


### `--start`

Alleen activiteiten die vóór deze datum zijn gemaakt, worden vermeld
- Vereist een waarde


### `--state`

Filteractiviteiten naar status: in_progress, in behandeling, voltooid of geannuleerd
- Standaard: `[]`
- Vereist een waarde


### `--result`

Filteractiviteiten op resultaat: succes of mislukking
- Vereist een waarde



### `--incomplete`, `-i`



Alleen onvolledige activiteiten weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--all`, `-a`



Activiteiten weergeven in alle omgevingen
- Standaard: `false`
- Accepteert geen waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `activity:log`

Logboek weergeven voor een activiteit

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

De activiteit-id. Wordt standaard ingesteld op de meest recente activiteit.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Vernieuwingsinterval voor activiteit (seconden). Stel de waarde in op 0 om vernieuwen uit te schakelen.
- Standaard: `3`
- Vereist een waarde



### `--timestamps`, `-t`



Een tijdstempel naast elk bericht weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--type`

Filteren op type (bij het selecteren van een standaardactiviteit)
- Vereist een waarde


### `--state`

Filteren op status (bij het selecteren van een standaardactiviteit): in_progress, in behandeling, voltooid of geannuleerd
- Standaard: `[]`
- Vereist een waarde


### `--result`

Filteren op resultaat (bij het selecteren van een standaardactiviteit): succes of mislukking
- Vereist een waarde



### `--incomplete`, `-i`



Alleen onvolledige activiteiten opnemen (bij het selecteren van een standaardactiviteit). Dit is een verkorte versie voor &lt;info>—state=in_progress,in behandeling&lt;/info>
- Standaard: `false`
- Accepteert geen waarde



### `--all`, `-a`



Recente activiteiten in alle omgevingen controleren (bij het selecteren van een standaardactiviteit)
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `api:curl`

Een geverifieerd cURL-verzoek uitvoeren op de Magento Cloud-API

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Het API-pad
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



De aanvraagmethode
- Vereist een waarde



### `--data`, `-d`



Te verzenden gegevens
- Vereist een waarde



### `--include`, `-i`



Koppen in de uitvoer opnemen
- Standaard: `false`
- Accepteert geen waarde



### `--head`, `-I`



Alleen kopteksten ophalen
- Standaard: `false`
- Accepteert geen waarde


### `--disable-compression`

Gebruik geen krullende —gecomprimeerde vlag
- Standaard: `false`
- Accepteert geen waarde


### `--enable-glob`

Grijsstructuuraanpassing inschakelen (de markering —globoff verwijderen)
- Standaard: `false`
- Accepteert geen waarde



### `--header`, `-H`



Extra koptekst(en)
- Standaard: `[]`
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `app:config-get`

De configuratie van een app weergeven

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



Het configuratiebezit aan mening
- Vereist een waarde


### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--identity-file`, `-i`



[Vervangen optie, niet meer gebruikt]
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `app:list`

Apps weergeven in het project

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
apps
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `auth:api-token-login`

Aanmelden bij Magento Cloud met een API-token

```bash
magento-cloud auth:api-token-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `auth:browser-login`

Aanmelden bij Magento Cloud via een browser

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```

<!-- app.name -->

```bash
login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Meld u opnieuw aan, zelfs als u zich al hebt aangemeld
- Standaard: `false`
- Accepteert geen waarde


### `--browser`

De browser die moet worden gebruikt om de URL te openen. Stel 0 in voor geen.
- Vereist een waarde


### `--pipe`

Voer de URL uit die u wilt stopzetten.
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `auth:info`

Je accountgegevens weergeven

```bash
magento-cloud auth:info [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

De accounteigenschap die moet worden weergegeven
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



De accounteigenschap die moet worden weergegeven (alternatieve syntaxis)
- Vereist een waarde


### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `auth:logout`

Afmelden bij Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```

<!-- app.name -->

```bash
logout
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Afmelden bij alle lokale sessies
- Standaard: `false`
- Accepteert geen waarde


### `--other`

Afmelden bij andere lokale sessies
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VEROUDERD ]&lt;/> Meld u aan bij Magento Cloud met een gebruikersnaam en wachtwoord

```bash
magento-cloud auth:password-login
```

<!-- app.name -->

```bash
auth:login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `auth:token`

Een OAuth 2-toegangstoken verkrijgen voor aanvragen voor Magento Cloud-API&#39;s

```bash
magento-cloud auth:token
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `blackfire:setup`

De integratie van Blackfire.io van de opstelling voor het project

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--server_id`

De server-id
- Vereist een waarde


### `--server_token`

Het servertoken
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `certificate:add`

Een SSL-certificaat toevoegen aan het project

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--cert`

Het pad naar het certificaatbestand
- Vereist een waarde


### `--key`

Het pad naar het persoonlijke sleutelbestand van het certificaat
- Vereist een waarde


### `--chain`

Het pad naar het certificaatkettingbestand
- Standaard: `[]`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `certificate:delete`

Een certificaat verwijderen uit het project

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

De certificaat-id (of het begin ervan)
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `certificate:get`

Een certificaat weergeven

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```

<!-- app.name --> <!-- command.usage -->

### `id`

De certificaat-id (of het begin ervan)
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



De certificaateigenschap die moet worden weergegeven
- Vereist een waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `certificate:list`

Projectcertificaten weergeven

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
certificates
```

<!-- app.name -->

```bash
certs
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--domain`

Filteren op domeinnaam (niet-hoofdlettergevoelige zoekopdracht)
- Vereist een waarde


### `--exclude-domain`

Certificaten uitsluiten, overeenkomend op domeinnaam (niet-hoofdlettergevoelige zoekopdracht)
- Vereist een waarde


### `--issuer`

Filteren op uitgever
- Vereist een waarde


### `--only-auto`

Alleen certificaten met automatische provisioning weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--no-auto`

Alleen handmatig toegevoegde certificaten weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ignore-expiry`

Verlopen en niet-verlopen certificaten weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--only-expired`

Alleen verlopen certificaten tonen
- Standaard: `false`
- Accepteert geen waarde


### `--no-expired`

Alleen niet-verlopen certificaten tonen (standaard)
- Standaard: `false`
- Accepteert geen waarde


### `--pipe-domains`

Retourneer alleen een lijst met domeinnamen die door de certificaten worden gedekt
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `commit:get`

Vastleggingsdetails tonen

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```

<!-- app.name --> <!-- command.usage -->

### `commit`

De commit SHA. Dit kan ook achtervoegsels &quot;HEAD&quot;, en invoegpunt (^) of tilde (~) accepteren voor bovenliggende komma&#39;s.
- Standaard: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



De eigenschap commit die moet worden weergegeven.
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde


### `--format`

VEROUDERD
- Vereist een waarde


### `--columns`

VEROUDERD
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

VEROUDERD
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `commit:list`

Lijstopdrachten

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```

<!-- app.name -->

```bash
commits
```

<!-- app.name --> <!-- command.usage -->

### `commit`

De beginstand past SHA toe. Dit kan ook achtervoegsels &quot;HEAD&quot;, en invoegpunt (^) of tilde (~) accepteren voor bovenliggende komma&#39;s.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--limit`

Het aantal verplichtingen dat moet worden weergegeven.
- Standaard: `10`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `db:dump`

Creeer een lokale stortplaats van het verre gegevensbestand

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
sql-dump
```

<!-- app.name -->

```bash
environment:sql-dump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--schema`

Het te dumpen schema. Laat weg om het standaardschema (gewoonlijk &quot;hoofd&quot;) te gebruiken.
- Vereist een waarde



### `--file`, `-f`



Een aangepaste bestandsnaam voor de dump
- Vereist een waarde



### `--directory`, `-d`



Een aangepaste map voor de stortplaats
- Vereist een waarde



### `--gzip`, `-z`



De stortplaats comprimeren met gzip
- Standaard: `false`
- Accepteert geen waarde



### `--timestamp`, `-t`



Een tijdstempel toevoegen aan de naam van het stortplaatje
- Standaard: `false`
- Accepteert geen waarde



### `--stdout`, `-o`



Uitvoeren naar STDOUT in plaats van een bestand
- Standaard: `false`
- Accepteert geen waarde


### `--table`

Op te nemen tabel(len)
- Standaard: `[]`
- Vereist een waarde


### `--exclude-table`

Uit te sluiten tabel(len)
- Standaard: `[]`
- Vereist een waarde


### `--schema-only`

Alleen schema&#39;s dumpen, geen gegevens
- Standaard: `false`
- Accepteert geen waarde


### `--charset`

De tekensetcodering voor de dump
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--relationship`, `-r`



De de dienstverhouding om te gebruiken
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `db:size`

Schatting van het schijfgebruik van een gegevensbestand

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Grootte in bytes weergeven.
- Standaard: `false`
- Accepteert geen waarde



### `--cleanup`, `-C`



Controleer of tabellen kunnen worden opgeschoond en geef me aanbevelingen (alleen InnoDb).
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--relationship`, `-r`



De de dienstverhouding om te gebruiken
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `db:sql`

SQL uitvoeren op de externe database

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```

<!-- app.name -->

```bash
sql
```

<!-- app.name -->

```bash
environment:sql
```

<!-- app.name --> <!-- command.usage -->

### `query`

Een SQL-instructie die moet worden uitgevoerd
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Onbewerkte, niet-tabelvormige uitvoer produceren
- Standaard: `false`
- Accepteert geen waarde


### `--schema`

Het schema dat moet worden gebruikt. Laat weg om het standaardschema (gewoonlijk &quot;hoofd&quot;) te gebruiken. Geef een lege tekenreeks door als u geen schema wilt gebruiken.
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--relationship`, `-r`



De de dienstverhouding om te gebruiken
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `domain:add`

Een nieuw domein toevoegen aan het project

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

De domeinnaam
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

Het pad naar het certificaatbestand voor dit domein
- Vereist een waarde


### `--key`

Het pad naar het bestand met de persoonlijke sleutel voor het opgegeven certificaat.
- Vereist een waarde


### `--chain`

Het pad naar het certificaatkettingbestand of de certificaatbestanden voor het opgegeven certificaat
- Standaard: `[]`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `domain:delete`

Een domein verwijderen uit het project

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

De domeinnaam
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `domain:get`

Gedetailleerde informatie voor een domein weergeven

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

De domeinnaam
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



De eigenschap domain die moet worden weergegeven
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `domain:list`

Een lijst met alle domeinen ophalen

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
domains
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `domain:update`

Een domein bijwerken

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

De domeinnaam
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--cert`

Het pad naar het certificaatbestand voor dit domein
- Vereist een waarde


### `--key`

Het pad naar het bestand met de persoonlijke sleutel voor het opgegeven certificaat.
- Vereist een waarde


### `--chain`

Het pad naar het certificaatkettingbestand of de certificaatbestanden voor het opgegeven certificaat
- Standaard: `[]`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:activate`

Een omgeving activeren

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name --> <!-- command.usage -->

### `environment`

De omgeving(en) die moet(en) worden geactiveerd

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--parent`

Een bovenliggende omgeving instellen voordat een omgeving wordt geactiveerd
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:branch`

Een omgeving vertakken

```bash
magento-cloud branch [--title TITLE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```

<!-- app.name -->

```bash
branch
```

<!-- app.name --> <!-- command.usage -->

### `id`

De id (vertakkingsnaam) van de nieuwe omgeving
<!-- argument -->

### `parent`

De bovenliggende omgeving van de nieuwe omgeving
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--title`

De titel van de nieuwe omgeving
- Vereist een waarde


### `--force`

Maak de nieuwe omgeving, zelfs als de vertakking niet lokaal kan worden uitgecheckt
- Standaard: `false`
- Accepteert geen waarde


### `--no-clone-parent`

De gegevens van de bovenliggende vertakking niet klonen
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:checkout`

Een omgeving uitchecken

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```

<!-- app.name -->

```bash
checkout
```

<!-- app.name --> <!-- command.usage -->

### `id`

De id van de omgeving die moet worden uitgecheckt. Bijvoorbeeld: &quot;sprint2&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:delete`

Een omgeving verwijderen

```bash
magento-cloud environment:deactivate [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--exclude EXCLUDE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```

<!-- app.name -->

```bash
environment:deactivate
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Te verwijderen omgeving(en)

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--delete-branch`

De externe Git-vertakking(en) verwijderen
- Standaard: `false`
- Accepteert geen waarde


### `--no-delete-branch`

De externe Git-vertakking(en) niet verwijderen
- Standaard: `false`
- Accepteert geen waarde


### `--inactive`

Alle niet-actieve omgevingen verwijderen
- Standaard: `false`
- Accepteert geen waarde


### `--merged`

Alle samengevoegde omgevingen verwijderen
- Standaard: `false`
- Accepteert geen waarde


### `--exclude`

Niet te verwijderen omgevingen
- Standaard: `[]`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:http-access`

De HTTP-toegangsinstellingen voor een omgeving bijwerken

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
httpaccess
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access`

Toegangsbeperking in de notatie &quot;permission:address&quot;. Gebruik 0 om alle adressen te wissen.
- Standaard: `[]`
- Vereist een waarde


### `--auth`

HTTP Basic auth credentials in the format &quot;username:password&quot;. Gebruik 0 om alle gegevens te wissen.
- Standaard: `[]`
- Vereist een waarde


### `--enabled`

Of toegangsbeheer zou moeten worden toegelaten: 1 om in te schakelen, 0 om uit te schakelen
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:info`

Eigenschappen voor een omgeving lezen of instellen

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
environment:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

De naam van de eigenschap
<!-- argument -->

### `value`

Een nieuwe waarde voor de eigenschap instellen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:init`

Een omgeving initialiseren vanuit een openbare Git-opslagplaats

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```

<!-- app.name --> <!-- command.usage -->

### `url`

Een URL naar een Git-opslagplaats
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--profile`

De naam van het profiel
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:list`

Een lijst met omgevingen ophalen

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
environments
```

<!-- app.name -->

```bash
env
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--no-inactive`, `-I`



Niet-actieve omgevingen tonen
- Standaard: `false`
- Accepteert geen waarde


### `--pipe`

Een eenvoudige lijst met milieu-id&#39;s uitvoeren.
- Standaard: `false`
- Accepteert geen waarde


### `--refresh`

Of de lijst moet worden vernieuwd.
- Standaard: `1`
- Vereist een waarde


### `--sort`

Een eigenschap waarop moet worden gesorteerd
- Standaard: `title`
- Vereist een waarde


### `--reverse`

Omgekeerde (aflopende) volgorde sorteren
- Standaard: `false`
- Accepteert geen waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:logs`

De logboeken van een omgeving lezen

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```

<!-- app.name -->

```bash
log
```

<!-- app.name -->

```bash
logs
```

<!-- app.name --> <!-- command.usage -->

### `type`

Het logtype, bijvoorbeeld &quot;access&quot; of &quot;error&quot;
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--lines`

Het aantal regels dat moet worden weergegeven
- Standaard: `100`
- Vereist een waarde


### `--tail`

Het logboek continu staart
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--worker`

De naam van een worker
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:merge`

Een omgeving samenvoegen

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
merge
```

<!-- app.name --> <!-- command.usage -->

### `environment`

De omgeving die moet worden samengevoegd
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:push`

Code naar een omgeving duwen

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```

<!-- app.name -->

```bash
push
```

<!-- app.name --> <!-- command.usage -->

### `source`

De bronverwijzing: een vertakkingsnaam of verbind knoeiboel
- Standaard: `HEAD`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

De naam van de doelvertakking
- Vereist een waarde



### `--force`, `-f`



Niet-snelle updates toestaan
- Standaard: `false`
- Accepteert geen waarde


### `--force-with-lease`

Niet-snelle updates toestaan als de verafgelegen traceringsvertakking up-to-date is
- Standaard: `false`
- Accepteert geen waarde



### `--set-upstream`, `-u`



De doelomgeving instellen als de upstream voor de bronvertakking
- Standaard: `false`
- Accepteert geen waarde


### `--activate`

De omgeving activeren voordat wordt gedrukt
- Standaard: `false`
- Accepteert geen waarde


### `--branch`

VEROUDERD: alias van —activate
- Standaard: `false`
- Accepteert geen waarde


### `--parent`

Een bovenliggende omgeving instellen voor een nieuwe omgeving (alleen gebruikt met —activate of —tak)
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:redeploy`

Een omgeving opnieuw implementeren

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```

<!-- app.name -->

```bash
redeploy
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:relationships`

Relaties van een omgeving tonen

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```

<!-- app.name -->

```bash
relationships
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Het milieu
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



De relatie-eigenschap die moet worden weergegeven
- Vereist een waarde


### `--refresh`

Of de relaties moeten worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:scp`

Bestanden kopiëren naar en van de huidige omgeving met behulp van scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```

<!-- app.name -->

```bash
scp
```

<!-- app.name --> <!-- command.usage -->

### `files`

Te kopiëren bestanden. De afstandsbediening gebruiken: voorvoegsel voor het definiëren van externe locaties.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--recursive`, `-r`



Gehele mappen recursief kopiëren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--worker`

De naam van een worker
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:set-remote`

De externe omgeving instellen op toewijzen aan een vertakking

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```

<!-- app.name --> <!-- command.usage -->

### `environment`

De naam van het omgevingssysteem. Instellen op 0 om de toewijzing voor een vertakking te verwijderen
- Vereist

   <!-- argument -->

### `branch`

De Git-vertakking die moet worden toegewezen (standaard ingesteld op de huidige vertakking)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:ssh`

SSH in de huidige omgeving

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```

<!-- app.name -->

```bash
ssh
```

<!-- app.name --> <!-- command.usage -->

### `cmd`

Een opdracht die op de omgeving moet worden uitgevoerd.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Alleen de SSH-URL uitvoeren.
- Standaard: `false`
- Accepteert geen waarde


### `--all`

Voer alle SSH-URL&#39;s uit (voor elke app).
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--worker`

De naam van een worker
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:synchronize`

De code en/of gegevens van een omgeving synchroniseren vanuit het bovenliggende element

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```

<!-- app.name -->

```bash
sync
```

<!-- app.name --> <!-- command.usage -->

### `synchronize`

Wat er moet worden gesynchroniseerd: &quot;code&quot;, &quot;data&quot; of beide

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--rebase`

Code synchroniseren door opnieuw te baseren in plaats van samen te voegen
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:url`

De openbare URL&#39;s van een omgeving ophalen

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
url
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--primary`, `-1`



Retourneert alleen de URL voor de primaire route
- Standaard: `false`
- Accepteert geen waarde


### `--browser`

De browser die moet worden gebruikt om de URL te openen. Stel 0 in voor geen.
- Vereist een waarde


### `--pipe`

Voer de URL uit die u wilt stopzetten.
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `environment:xdebug`

Een tunnel openen voor Xdebug in de omgeving

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name -->

```bash
xdebug
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

De lokale poort
- Standaard: `9000`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--worker`

De naam van een worker
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `integration:activity:get`

Gedetailleerde informatie weergeven over één integratieactiviteit

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Een integratie-id. Laat leeg om uit een lijst te kiezen.
<!-- argument -->

### `activity`

De activiteit-id. Wordt standaard ingesteld op de meest recente integratieactiviteit.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



De eigenschap die moet worden weergegeven
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



[Vervangen optie, niet gebruikt]
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `integration:activity:list`

Een lijst met activiteiten voor integratie ophalen

```bash
magento-cloud i:act [--type TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```

<!-- app.name -->

```bash
i:act
```

<!-- app.name -->

```bash
integration:activities
```

<!-- app.name --> <!-- command.usage -->

### `id`

Een integratie-id. Laat leeg om uit een lijst te kiezen.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Filteractiviteiten per type
- Vereist een waarde


### `--limit`

Beperk het aantal weergegeven resultaten
- Standaard: `10`
- Vereist een waarde


### `--start`

Alleen activiteiten die vóór deze datum zijn gemaakt, worden vermeld
- Vereist een waarde


### `--state`

Activiteiten filteren op status
- Standaard: `[]`
- Vereist een waarde


### `--result`

Activiteiten filteren op resultaat
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



[Vervangen optie, niet gebruikt]
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `integration:activity:log`

Logboek weergeven voor een integratieactiviteit

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```

<!-- app.name --> <!-- command.usage -->

### `integration`

Een integratie-id. Laat leeg om uit een lijst te kiezen.
<!-- argument -->

### `activity`

De activiteit-id. Wordt standaard ingesteld op de meest recente integratieactiviteit.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--timestamps`, `-t`



Een tijdstempel naast elk bericht weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



[Vervangen optie, niet gebruikt]
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `integration:add`

Integratie toevoegen aan het project

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--type`

Het integratietype (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webhaak&#39;, &#39;health.email&#39;, &#39;health.pagerduty&#39;, &#39;health.slack&#39;, &#39;health.webhaak&#39;, &#39;script&#39;)
- Vereist een waarde


### `--base-url`

De basis-URL van de serverinstallatie
- Vereist een waarde


### `--username`

De gebruikersnaam van de Bitmap-server
- Vereist een waarde


### `--token`

Een toegangstoken voor de integratie
- Vereist een waarde


### `--key`

Een OAuth-toets voor bitemmers
- Vereist een waarde


### `--secret`

Een Bitbucket OAuth-consumentengeheim
- Vereist een waarde


### `--server-project`

Het project (bv. &#39;namespace/repo&#39;)
- Vereist een waarde


### `--repository`

De bij te houden opslagplaats (bijvoorbeeld &quot;eigenaar/opslagplaats&quot;)
- Vereist een waarde


### `--build-merge-requests`

GitLab: samenvoegverzoeken als omgevingen samenstellen
- Standaard: `true`
- Vereist een waarde


### `--build-pull-requests`

Bouw elk trekkingsverzoek als milieu
- Standaard: `true`
- Vereist een waarde


### `--build-draft-pull-requests`

Conceptweergave-aanvragen samenstellen
- Standaard: `true`
- Vereist een waarde


### `--build-pull-requests-post-merge`

Trek verzoeken bouwen die op hun post-fusiestatus worden gebaseerd
- Standaard: `false`
- Vereist een waarde


### `--build-wip-merge-requests`

GitLab: WIP-fusieverzoeken samenstellen
- Standaard: `true`
- Vereist een waarde


### `--merge-requests-clone-parent-data`

GitLab: gegevens klonen voor samenvoegaanvragen
- Standaard: `true`
- Vereist een waarde


### `--pull-requests-clone-parent-data`

De gegevens van de bovenliggende omgeving klonen voor pull-aanvragen
- Standaard: `true`
- Vereist een waarde


### `--resync-pull-requests`

Hersynchroniseer de gegevens van het trekkingsverzoek op elke bouwstijl
- Standaard: `false`
- Vereist een waarde


### `--fetch-branches`

Alle vertakkingen ophalen van de externe server (als inactieve omgevingen)
- Standaard: `true`
- Vereist een waarde


### `--prune-branches`

Vertakkingen verwijderen die niet bestaan op de externe server
- Standaard: `true`
- Vereist een waarde


### `--room`

HipChat room ID
- Vereist een waarde


### `--url`

Webhaak: een URL om JSON-gegevens te ontvangen
- Vereist een waarde


### `--shared-key`

Webhaak: de gedeelde sleutel van het JWS
- Vereist een waarde


### `--file`

De naam van een lokaal bestand dat het te uploaden script bevat
- Vereist een waarde


### `--events`

Een lijst met gebeurtenissen waarop moet worden gereageerd, bijvoorbeeld environment.push
- Standaard: `*`
- Vereist een waarde


### `--states`

Een lijst met staten waar moet worden opgetreden, bijv. pending, in_progress, complete
- Standaard: `complete`
- Vereist een waarde


### `--environments`

De milieu-id&#39;s die moeten worden opgenomen
- Standaard: `*`
- Vereist een waarde


### `--excluded-environments`

De milieu-id&#39;s om uit te sluiten
- Standaard: `[]`
- Vereist een waarde


### `--from-address`

[Optioneel] Aangepast van adres voor e-mailberichten met een waarschuwing
- Vereist een waarde


### `--recipients`

E-mailadres(sen) van ontvanger
- Standaard: `[]`
- Vereist een waarde


### `--channel`

Het Slack-kanaal
- Vereist een waarde


### `--routing-key`

De PagerDuty-routeringssleutel
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `integration:delete`

Integratie uit een project verwijderen

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

De integratie-id. Laat leeg om uit een lijst te kiezen.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `integration:get`

Details van een integratie weergeven

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Een integratie-id. Laat leeg om uit een lijst te kiezen.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



De integratieeigenschap die moet worden weergegeven
- Accepteert een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `integration:list`

Een lijst met projectintegratie(s) weergeven

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
integrations
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `integration:update`

Integratie bijwerken

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--room ROOM] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

De id van de bij te werken integratie
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Het integratietype (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;hipchat&#39;, &#39;webhaak&#39;, &#39;health.email&#39;, &#39;health.pagerduty&#39;, &#39;health.slack&#39;, &#39;health.webhaak&#39;, &#39;script&#39;)
- Vereist een waarde


### `--base-url`

De basis-URL van de serverinstallatie
- Vereist een waarde


### `--username`

De gebruikersnaam van de Bitmap-server
- Vereist een waarde


### `--token`

Een toegangstoken voor de integratie
- Vereist een waarde


### `--key`

Een OAuth-toets voor bitemmers
- Vereist een waarde


### `--secret`

Een Bitbucket OAuth-consumentengeheim
- Vereist een waarde


### `--server-project`

Het project (bv. &#39;namespace/repo&#39;)
- Vereist een waarde


### `--repository`

De bij te houden opslagplaats (bijvoorbeeld &quot;eigenaar/opslagplaats&quot;)
- Vereist een waarde


### `--build-merge-requests`

GitLab: samenvoegverzoeken als omgevingen samenstellen
- Standaard: `true`
- Vereist een waarde


### `--build-pull-requests`

Bouw elk trekkingsverzoek als milieu
- Standaard: `true`
- Vereist een waarde


### `--build-draft-pull-requests`

Conceptweergave-aanvragen samenstellen
- Standaard: `true`
- Vereist een waarde


### `--build-pull-requests-post-merge`

Trek verzoeken bouwen die op hun post-fusiestatus worden gebaseerd
- Standaard: `false`
- Vereist een waarde


### `--build-wip-merge-requests`

GitLab: WIP-fusieverzoeken samenstellen
- Standaard: `true`
- Vereist een waarde


### `--merge-requests-clone-parent-data`

GitLab: gegevens klonen voor samenvoegaanvragen
- Standaard: `true`
- Vereist een waarde


### `--pull-requests-clone-parent-data`

De gegevens van de bovenliggende omgeving klonen voor pull-aanvragen
- Standaard: `true`
- Vereist een waarde


### `--resync-pull-requests`

Hersynchroniseer de gegevens van het trekkingsverzoek op elke bouwstijl
- Standaard: `false`
- Vereist een waarde


### `--fetch-branches`

Alle vertakkingen ophalen van de externe server (als inactieve omgevingen)
- Standaard: `true`
- Vereist een waarde


### `--prune-branches`

Vertakkingen verwijderen die niet bestaan op de externe server
- Standaard: `true`
- Vereist een waarde


### `--room`

HipChat room ID
- Vereist een waarde


### `--url`

Webhaak: een URL om JSON-gegevens te ontvangen
- Vereist een waarde


### `--shared-key`

Webhaak: de gedeelde sleutel van het JWS
- Vereist een waarde


### `--file`

De naam van een lokaal bestand dat het te uploaden script bevat
- Vereist een waarde


### `--events`

Een lijst met gebeurtenissen waarop moet worden gereageerd, bijvoorbeeld environment.push
- Standaard: `*`
- Vereist een waarde


### `--states`

Een lijst met staten waar moet worden opgetreden, bijv. pending, in_progress, complete
- Standaard: `complete`
- Vereist een waarde


### `--environments`

De milieu-id&#39;s die moeten worden opgenomen
- Standaard: `*`
- Vereist een waarde


### `--excluded-environments`

De milieu-id&#39;s om uit te sluiten
- Standaard: `[]`
- Vereist een waarde


### `--from-address`

[Optioneel] Aangepast van adres voor e-mailberichten met een waarschuwing
- Vereist een waarde


### `--recipients`

E-mailadres(sen) van ontvanger
- Standaard: `[]`
- Vereist een waarde


### `--channel`

Het Slack-kanaal
- Vereist een waarde


### `--routing-key`

De PagerDuty-routeringssleutel
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `integration:validate`

Een bestaande integratie valideren

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

Een integratie-id. Laat leeg om uit een lijst te kiezen.
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `local:build`

Het huidige project lokaal bouwen

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```

<!-- app.name -->

```bash
build
```

<!-- app.name --> <!-- command.usage -->

### `app`

Toepassingen opgeven die moeten worden gemaakt

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--abslinks`, `-a`



Absolute koppelingen gebruiken
- Standaard: `false`
- Accepteert geen waarde



### `--source`, `-s`



De bronmap. Wordt standaard ingesteld op de huidige hoofdmap van het project.
- Vereist een waarde



### `--destination`, `-d`



De bestemming, waaraan de webhoofdmap van elke app wordt gekoppeld. Standaard: _www
- Vereist een waarde



### `--copy`, `-c`



Kopiëren naar een build-directory in plaats van te symboliseren vanaf de bron
- Standaard: `false`
- Accepteert geen waarde


### `--clone`

Gebruik Git om de huidige HEAD naar de bouwstijldirectory te klonen
- Standaard: `false`
- Accepteert geen waarde


### `--run-deploy-hooks`

Implementatie- en/of post_implementatiehaken uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--no-clean`

Oude builds niet verwijderen
- Standaard: `false`
- Accepteert geen waarde


### `--no-archive`

Maak of gebruik geen build-archief
- Standaard: `false`
- Accepteert geen waarde


### `--no-backup`

Maak geen back-up van de vorige build
- Standaard: `false`
- Accepteert geen waarde


### `--no-cache`

Cache uitschakelen
- Standaard: `false`
- Accepteert geen waarde


### `--no-build-hooks`

Geen haken voor na het bouwen uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--no-deps`

Installeer geen build-afhankelijkheden lokaal
- Standaard: `false`
- Accepteert geen waarde


### `--working-copy`

Drush: gebruik git om een opslagplaats van elke Drupal-module te klonen in plaats van gewoon een versie te downloaden
- Standaard: `false`
- Accepteert geen waarde


### `--concurrency`

Drush: het aantal gelijktijdige projecten instellen die tegelijkertijd worden verwerkt
- Standaard: `4`
- Vereist een waarde


### `--lock`

Drush: een vergrendelingsbestand maken of bijwerken (alleen beschikbaar bij Dush versie 7+)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `local:clean`

Oude projectbuilds verwijderen

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```

<!-- app.name -->

```bash
clean
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep`

Het maximumaantal builds dat behouden moet blijven
- Standaard: `5`
- Vereist een waarde


### `--max-age`

De maximumleeftijd van builds, in seconden. Genegeerd als niet ingesteld.
- Vereist een waarde


### `--include-active`

Actieve build(s) ook verwijderen
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `local:dir`

De lokale hoofdmap van het project zoeken

```bash
magento-cloud dir [<subdir>]
```

<!-- app.name -->

```bash
dir
```

<!-- app.name --> <!-- command.usage -->

### `subdir`

De submap die moet worden gevonden (&#39;local&#39;, &#39;web&#39; of &#39;shared&#39;)
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `mount:download`

Bestanden downloaden van een berg, via resynchroniseren

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Downloaden vanaf alle locaties
- Standaard: `false`
- Accepteert geen waarde



### `--mount`, `-m`



De koppeling (als een pad dat relatief is ten opzichte van de toepassing)
- Vereist een waarde


### `--target`

De map waarnaar bestanden worden gedownload. Als —all wordt gebruikt, zal de koppelingsweg worden toegevoegd
- Vereist een waarde


### `--source-path`

Gebruik het bronpad van de koppeling (in plaats van het koppelingspad) als submap van het doel, wanneer —all wordt gebruikt
- Standaard: `false`
- Accepteert geen waarde


### `--delete`

Of vreemde bestanden in de doelmap moeten worden verwijderd
- Standaard: `false`
- Accepteert geen waarde


### `--exclude`

Bestand(en) om uit te sluiten van downloaden (patroon)
- Standaard: `[]`
- Vereist een waarde


### `--include`

Bestand(en) om op te nemen in downloaden (patroon)
- Standaard: `[]`
- Vereist een waarde


### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--worker`

De naam van een worker
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `mount:list`

Een lijst met bevestigingen ophalen

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name -->

```bash
mounts
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--paths`

Alleen de koppelingspaden uitvoeren (één per regel)
- Standaard: `false`
- Accepteert geen waarde


### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--worker`

De naam van een worker
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `mount:size`

Controleer het schijfgebruik van bevestigingen

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--bytes`, `-B`



Grootte in bytes weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--refresh`

De cache vernieuwen
- Standaard: `false`
- Accepteert geen waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--worker`

De naam van een worker
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `mount:upload`

Bestanden uploaden naar een koppelingsgebied, via opnieuw synchroniseren

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--source`

Een map met bestanden die moeten worden geüpload
- Vereist een waarde



### `--mount`, `-m`



De koppeling (als een pad dat relatief is ten opzichte van de toepassing)
- Vereist een waarde


### `--delete`

Of vreemde bestanden in de telling moeten worden verwijderd
- Standaard: `false`
- Accepteert geen waarde


### `--exclude`

Bestand(en) om uit te sluiten van uploaden (patroon)
- Standaard: `[]`
- Vereist een waarde


### `--include`

Bestand(en) om op te nemen in uploaden (patroon)
- Standaard: `[]`
- Vereist een waarde


### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--worker`

De naam van een worker
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `project:clear-build-cache`

De cache voor het samenstellen van een project wissen

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `project:curl`

Een geverifieerd cURL-verzoek uitvoeren op de API van een project

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Het API-pad
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--request`, `-X`



De aanvraagmethode
- Vereist een waarde



### `--data`, `-d`



Te verzenden gegevens
- Vereist een waarde



### `--include`, `-i`



Koppen in de uitvoer opnemen
- Standaard: `false`
- Accepteert geen waarde



### `--head`, `-I`



Alleen kopteksten ophalen
- Standaard: `false`
- Accepteert geen waarde


### `--disable-compression`

Gebruik geen krullende —gecomprimeerde vlag
- Standaard: `false`
- Accepteert geen waarde


### `--enable-glob`

Grijsstructuuraanpassing inschakelen (de markering —globoff verwijderen)
- Standaard: `false`
- Accepteert geen waarde



### `--header`, `-H`



Extra koptekst(en)
- Standaard: `[]`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `project:get`

Een project lokaal klonen

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```

<!-- app.name -->

```bash
get
```

<!-- app.name --> <!-- command.usage -->

### `project`

Project-id
<!-- argument -->

### `directory`

De map waarnaar moet worden gekloond. Wordt standaard ingesteld op de projecttitel
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--environment`, `-e`



De milieu-id die moet worden gekloond. Wordt standaard ingesteld op de standaardinstelling van het project of de eerste beschikbare omgeving
- Vereist een waarde


### `--depth`

Een ondiepe kloon maken: aantal vastleggingen in de geschiedenis beperken
- Vereist een waarde


### `--build`

Het project na het klonen maken
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `project:info`

Eigenschappen voor een project lezen of instellen

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```

<!-- app.name -->

```bash
project:metadata
```

<!-- app.name --> <!-- command.usage -->

### `property`

De naam van de eigenschap
<!-- argument -->

### `value`

Een nieuwe waarde voor de eigenschap instellen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `project:list`

Een lijst met alle actieve projecten ophalen

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
projects
```

<!-- app.name -->

```bash
pro
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--pipe`

Een eenvoudige lijst met project-id&#39;s uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--host`

Filter op regio hostnaam (exacte overeenkomst)
- Vereist een waarde


### `--title`

Filteren op titel (niet-hoofdlettergevoelig zoeken)
- Vereist een waarde


### `--my`

Alleen uw eigen projecten weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--refresh`

Of de lijst moet worden vernieuwd
- Standaard: `1`
- Vereist een waarde


### `--sort`

Een eigenschap waarop moet worden gesorteerd
- Standaard: `title`
- Vereist een waarde


### `--reverse`

Omgekeerde (aflopende) volgorde sorteren
- Standaard: `false`
- Accepteert geen waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `project:set-remote`

Het externe project instellen voor de huidige Git-opslagplaats

```bash
magento-cloud project:set-remote [<project>]
```

<!-- app.name --> <!-- command.usage -->

### `project`

Project-id
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VEROUDERD ]&lt;/> Een variabele uit een project verwijderen

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

De variabelenaam
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VEROUDERD ]&lt;/> Variabelen voor een project weergeven

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```

<!-- app.name -->

```bash
project-variables
```

<!-- app.name -->

```bash
pvget
```

<!-- app.name -->

```bash
project:variable:list
```

<!-- app.name --> <!-- command.usage -->

### `name`

De naam van de variabele
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--pipe`

Alleen de waarde van de volledige variabele uitvoeren (er moet een &quot;naam&quot; worden opgegeven)
- Standaard: `false`
- Accepteert geen waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VEROUDERD ]&lt;/> Een variabele instellen voor een project

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
pvset
```

<!-- app.name --> <!-- command.usage -->

### `name`

De variabelenaam
- Vereist

   <!-- argument -->

### `value`

De waarde van de variabele
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

De waarde markeren als JSON
- Standaard: `false`
- Accepteert geen waarde


### `--no-visible-build`

Deze variabele niet tijdens het samenstellen beschikbaar maken
- Standaard: `false`
- Accepteert geen waarde


### `--no-visible-runtime`

Deze variabele niet beschikbaar maken bij uitvoering
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `repo:cat`

Een bestand lezen in de gegevensopslagruimte van het project

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Het pad naar het bestand
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--commit`, `-c`



De commit SHA. Dit kan ook achtervoegsels &quot;HEAD&quot;, en invoegpunt (^) of tilde (~) accepteren voor bovenliggende komma&#39;s.
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `repo:ls`

Bestanden weergeven in de gegevensopslagruimte van het project

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Het pad naar een submap
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--directories`, `-d`



Alleen mappen tonen
- Standaard: `false`
- Accepteert geen waarde



### `--files`, `-f`



Alleen bestanden tonen
- Standaard: `false`
- Accepteert geen waarde


### `--git-style`

Stijl, uitvoer vergelijkbaar met &#39;git ls-tree&#39;
- Standaard: `false`
- Accepteert geen waarde



### `--commit`, `-c`



De commit SHA. Dit kan ook achtervoegsels &quot;HEAD&quot;, en invoegpunt (^) of tilde (~) accepteren voor bovenliggende komma&#39;s.
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `route:get`

Gedetailleerde informatie over een route weergeven

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```

<!-- app.name --> <!-- command.usage -->

### `route`

Originele URL van de route
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--id`

Een route-id om te selecteren
- Vereist een waarde



### `--primary`, `-1`



Selecteer de primaire route
- Standaard: `false`
- Accepteert geen waarde



### `--property`, `-P`



De weer te geven eigenschap
- Vereist een waarde


### `--refresh`

Het geheime voorgeheugen van routes omzeilen
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



[Vervangen optie, niet meer gebruikt]
- Vereist een waarde



### `--identity-file`, `-i`



[Vervangen optie, niet meer gebruikt]
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `route:list`

Alle routes weergeven voor een omgeving

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```

<!-- app.name -->

```bash
routes
```

<!-- app.name -->

```bash
environment:routes
```

<!-- app.name --> <!-- command.usage -->

### `environment`

De milieu-id
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--refresh`

Het geheime voorgeheugen van routes omzeilen
- Standaard: `false`
- Accepteert geen waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `self:install`

CLI-configuratiebestanden installeren of bijwerken

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```

<!-- app.name -->

```bash
local:install
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--shell-type`

Het shell-type voor automatisch aanvullen (bash of zsh)
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `self:stats`

Status weergeven op GitHub-pakketdownloads

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--page`, `-p`



Paginanummer
- Standaard: `1`
- Vereist een waarde



### `--count`, `-c`



Resultaten per pagina (max.: 100)
- Standaard: `20`
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `self:update`

CLI bijwerken naar de nieuwste versie

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```

<!-- app.name -->

```bash
self-update
```

<!-- app.name -->

```bash
update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-major`

Alleen bijwerken tussen kleine versies of patchversies
- Standaard: `false`
- Accepteert geen waarde


### `--unstable`

Bijwerken naar een nieuwe onstabiele versie, indien beschikbaar
- Standaard: `false`
- Accepteert geen waarde


### `--manifest`

De locatie van het manifestbestand overschrijven
- Vereist een waarde


### `--current-version`

De huidige versie overschrijven
- Vereist een waarde


### `--timeout`

Een time-out voor de versiecontrole
- Standaard: `30`
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `service:list`

De diensten van de lijst in het project

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
services
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `service:mongo:dump`

Een binaire archiefstortplaats maken van gegevens van MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongodump
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



De inzameling aan stortplaats
- Vereist een waarde



### `--gzip`, `-z`



De stortplaats comprimeren met gzip
- Standaard: `false`
- Accepteert geen waarde



### `--stdout`, `-o`



Uitvoeren naar STDOUT in plaats van een bestand
- Standaard: `false`
- Accepteert geen waarde



### `--relationship`, `-r`



De de dienstverhouding om te gebruiken
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `service:mongo:export`

Gegevens exporteren uit MongoDB

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongoexport
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



De verzameling die moet worden geëxporteerd
- Vereist een waarde


### `--jsonArray`

Gegevens exporteren als één JSON-array
- Standaard: `false`
- Accepteert geen waarde


### `--type`

Het exporttype, bijvoorbeeld &quot;csv&quot;
- Vereist een waarde



### `--fields`, `-f`



De velden die u wilt exporteren
- Standaard: `[]`
- Vereist een waarde



### `--relationship`, `-r`



De de dienstverhouding om te gebruiken
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `service:mongo:restore`

Herstel een binaire archiefstortplaats van gegevens in MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongorestore
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--collection`, `-c`



De te herstellen verzameling
- Vereist een waarde



### `--relationship`, `-r`



De de dienstverhouding om te gebruiken
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `service:mongo:shell`

De shell van MongoDB gebruiken

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name -->

```bash
mongo
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--eval`

Een JavaScript-fragment doorgeven aan de shell
- Vereist een waarde



### `--relationship`, `-r`



De de dienstverhouding om te gebruiken
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `service:redis-cli`

Toegang tot de CLI van Redis

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```

<!-- app.name -->

```bash
redis
```

<!-- app.name --> <!-- command.usage -->

### `args`

Argumenten die moeten worden toegevoegd aan de opdracht Redis
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--relationship`, `-r`



De de dienstverhouding om te gebruiken
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Tussen sessies schakelen

```bash
magento-cloud session:switch [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

De nieuwe sessie-id
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `snapshot:create`

Een opname maken van een omgeving

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```

<!-- app.name -->

```bash
backup
```

<!-- app.name -->

```bash
backup:create
```

<!-- app.name -->

```bash
environment:backup
```

<!-- app.name --> <!-- command.usage -->

### `environment`

Het milieu
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--live`

Live back-up: het milieu niet tegenhouden. Als deze optie is ingesteld, blijft de omgeving actief en kunnen er verbindingen worden gemaakt tijdens de back-up. Dit vermindert onderbreking, met het risico om gegevens in een inconsistente staat te steunen.
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `snapshot:list`

Beschikbare momentopnamen van een omgeving weergeven

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
snapshots
```

<!-- app.name -->

```bash
backups
```

<!-- app.name -->

```bash
backup:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--limit`

Het aantal momentopnamen beperken tot de lijst
- Standaard: `10`
- Vereist een waarde


### `--start`

Alleen momentopnamen die vóór deze datum zijn gemaakt, worden weergegeven
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `snapshot:restore`

Een omgevingsmomentopname herstellen

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```

<!-- app.name -->

```bash
environment:restore
```

<!-- app.name -->

```bash
snapshot:restore
```

<!-- app.name --> <!-- command.usage -->

### `snapshot`

De naam van de opname. Wordt standaard ingesteld op de meest recente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--target`

De omgeving die moet worden hersteld. Wordt standaard ingesteld op de huidige omgeving van de momentopname
- Vereist een waarde


### `--branch-from`

Als —target nog niet bestaat, specificeert dit de ouder van het nieuwe milieu
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Een bronbewerking uitvoeren

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```

<!-- app.name --> <!-- command.usage -->

### `operation`

De naam van de bewerking
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--variable`

Een variabele die tijdens de bewerking moet worden ingesteld, in de notatie &lt;info>type:name=value&lt;/info>
- Standaard: `[]`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `ssh-cert:info`

Informatie weergeven over het huidige SSH-certificaat

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-refresh`

Vernieuw het certificaat niet als het ongeldig is
- Standaard: `false`
- Accepteert geen waarde



### `--property`, `-P`



De certificaateigenschap die moet worden weergegeven
- Vereist een waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `ssh-cert:load`

Een SSH-certificaat genereren

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh-only`

Vernieuw slechts het certificaat, indien nodig (schrijf geen SSH config)
- Standaard: `false`
- Accepteert geen waarde


### `--new`

Het certificaat vernieuwen forceren
- Standaard: `false`
- Accepteert geen waarde


### `--new-key`

[Vervangen] Gebruik —nieuw in plaats hiervan
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `ssh-key:add`

Een nieuwe SSH-toets toevoegen

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Het pad naar een bestaande SSH-openbare sleutel
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--name`

Een naam om de sleutel te identificeren
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `ssh-key:delete`

Een SSH-toets verwijderen

```bash
magento-cloud ssh-key:delete [<id>]
```

<!-- app.name --> <!-- command.usage -->

### `id`

De id van de SSH-toets die moet worden verwijderd
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `ssh-key:list`

Een lijst met SSH-sleutels in uw account ophalen

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
ssh-keys
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `subscription:info`

Abonnementseigenschappen lezen of wijzigen

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```

<!-- app.name --> <!-- command.usage -->

### `property`

De naam van de eigenschap
<!-- argument -->

### `value`

Een nieuwe waarde voor de eigenschap instellen
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--id`, `-s`



Abonnement-id
- Vereist een waarde


### `--date-fmt`

De datumnotatie (als een PHP-datumnotatietekenreeks)
- Standaard: `c`
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `tunnel:close`

SSH-tunnels sluiten

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Alle tunnels sluiten
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `tunnel:info`

Relatie-informatie voor SSH-tunnels weergeven

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--property`, `-P`



De relatie-eigenschap die moet worden weergegeven
- Vereist een waarde



### `--encode`, `-c`



Uitvoer als base64-gecodeerde JSON
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `tunnel:list`

Lijst SSH-tunnels

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
tunnels
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--all`, `-a`



Alle tunnels weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `tunnel:open`

SSH-tunnels openen naar de relaties van een app

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--gateway-ports`, `-g`



Verre gastheren toestaan om met lokale door:sturen havens te verbinden
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `tunnel:single`

Eén SSH-tunnel openen voor een app-relatie

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--port`

De lokale poort
- Vereist een waarde



### `--gateway-ports`, `-g`



Verre gastheren toestaan om met lokale door:sturen havens te verbinden
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--app`, `-A`



De naam van de externe toepassing
- Vereist een waarde



### `--relationship`, `-r`



De de dienstverhouding om te gebruiken
- Vereist een waarde



### `--identity-file`, `-i`



Een SSH-identiteit (persoonlijke sleutel) die moet worden gebruikt
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `user:add`

Een gebruiker toevoegen aan het project

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

Het e-mailadres van de gebruiker
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



De projectrol (&#39;admin&#39; of &#39;viewer&#39;) van de gebruiker of een specifieke rol voor de omgeving (bijvoorbeeld &#39;master:contribuant&#39; of &#39;stage:viewer&#39;). Het teken % kan worden gebruikt als jokerteken in de milieu-id, bijvoorbeeld &#39;%:viewer&#39;. De rol kan worden afgekort, bijvoorbeeld &#39;master:c&#39;.
- Standaard: `[]`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `user:delete`

Een gebruiker verwijderen uit het project

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```

<!-- app.name --> <!-- command.usage -->

### `email`

Het e-mailadres van de gebruiker
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `user:get`

Rollen van gebruikers weergeven

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```

<!-- app.name -->

```bash
user:role
```

<!-- app.name --> <!-- command.usage -->

### `email`

Het e-mailadres van de gebruiker
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Rolniveau (&#39;project&#39; of &#39;milieu&#39;)
- Vereist een waarde


### `--pipe`

De rol uitvoeren die moet worden stopgezet (nadat eventuele wijzigingen zijn aangebracht)
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--role`, `-r`



[Vervangen: gebruiker gebruiken:bijwerken om de rol(en) van een gebruiker te wijzigen]
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `user:list`

Projectgebruikers weergeven

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```

<!-- app.name -->

```bash
users
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `user:update`

Gebruikersrol(s) voor een project bijwerken

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```

<!-- app.name --> <!-- command.usage -->

### `email`

Het e-mailadres van de gebruiker
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--role`, `-r`



De projectrol (&#39;admin&#39; of &#39;viewer&#39;) van de gebruiker of een specifieke rol voor de omgeving (bijvoorbeeld &#39;master:contribuant&#39; of &#39;stage:viewer&#39;). Het teken % kan worden gebruikt als jokerteken in de milieu-id, bijvoorbeeld &#39;%:viewer&#39;. De rol kan worden afgekort, bijvoorbeeld &#39;master:c&#39;.
- Standaard: `[]`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `variable:create`

Een variabele maken

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```

<!-- app.name --> <!-- command.usage -->

### `name`

De variabelenaam
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Het niveau waarop de variabele moet worden ingesteld (&#39;project&#39; of &#39;omgeving&#39;)
- Vereist een waarde


### `--name`

De variabelenaam
- Vereist een waarde


### `--value`

De waarde van de variabele
- Vereist een waarde


### `--json`

Of de variabele JSON-opgemaakt is
- Standaard: `false`
- Vereist een waarde


### `--sensitive`

Of de variabele gevoelig is
- Standaard: `false`
- Vereist een waarde


### `--prefix`

Het voorvoegsel van de variabelenaam (bijvoorbeeld &#39;none&#39; of &#39;env:&#39;)
- Standaard: `none`
- Vereist een waarde


### `--enabled`

Of de variabele moet worden ingeschakeld
- Standaard: `true`
- Vereist een waarde


### `--inheritable`

Of de variabele overerfbaar is door onderliggende omgevingen
- Standaard: `true`
- Vereist een waarde


### `--visible-build`

Of de variabele zichtbaar zou moeten zijn in bouwstijltijd
- Standaard: `true`
- Vereist een waarde


### `--visible-runtime`

Of de variabele zichtbaar moet zijn bij uitvoering
- Standaard: `true`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `variable:delete`

Een variabele verwijderen

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

De variabelenaam
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Variabel niveau (&#39;project&#39;, &#39;milieu&#39;, &#39;p&#39; of &#39;e&#39;)
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VEROUDERD ]&lt;/> Een ingeschakelde variabele op milieuniveau uitschakelen

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

De naam van de variabele
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VEROUDERD ]&lt;/> Een uitgeschakelde variabele op milieuniveau inschakelen

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

De naam van de variabele
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `variable:get`

Een variabele weergeven

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```

<!-- app.name -->

```bash
vget
```

<!-- app.name --> <!-- command.usage -->

### `name`

De naam van de variabele
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--property`, `-P`



Eén variabele-eigenschap weergeven
- Vereist een waarde



### `--level`, `-l`



Variabel niveau (&#39;project&#39;, &#39;milieu&#39;, &#39;p&#39; of &#39;e&#39;)
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde


### `--pipe`

[Vervangen optie] Alleen de waarde van de variabele uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `variable:list`

Lijstvariabelen

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

<!-- app.name -->

```bash
variables
```

<!-- app.name -->

```bash
var
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--level`, `-l`



Variabel niveau (&#39;project&#39;, &#39;milieu&#39;, &#39;p&#39; of &#39;e&#39;)
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ VEROUDERD ]&lt;/> Een variabele instellen voor een omgeving

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```

<!-- app.name -->

```bash
vset
```

<!-- app.name --> <!-- command.usage -->

### `name`

De variabelenaam
- Vereist

   <!-- argument -->

### `value`

De waarde van de variabele
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--json`

De waarde markeren als JSON
- Standaard: `false`
- Accepteert geen waarde


### `--disabled`

De variabele markeren als uitgeschakeld
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `variable:update`

Een variabele bijwerken

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```

<!-- app.name --> <!-- command.usage -->

### `name`

De variabelenaam
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--level`, `-l`



Variabel niveau (&#39;project&#39;, &#39;milieu&#39;, &#39;p&#39; of &#39;e&#39;)
- Vereist een waarde


### `--value`

De waarde van de variabele
- Vereist een waarde


### `--json`

Of de variabele JSON-opgemaakt is
- Standaard: `false`
- Vereist een waarde


### `--sensitive`

Of de variabele gevoelig is
- Standaard: `false`
- Vereist een waarde


### `--enabled`

Of de variabele moet worden ingeschakeld
- Standaard: `true`
- Vereist een waarde


### `--inheritable`

Of de variabele overerfbaar is door onderliggende omgevingen
- Standaard: `true`
- Vereist een waarde


### `--visible-build`

Of de variabele zichtbaar zou moeten zijn in bouwstijltijd
- Standaard: `true`
- Vereist een waarde


### `--visible-runtime`

Of de variabele zichtbaar moet zijn bij uitvoering
- Standaard: `true`
- Vereist een waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde



### `--no-wait`, `-W`



Wacht niet tot de bewerking is voltooid
- Standaard: `false`
- Accepteert geen waarde


### `--wait`

Wacht tot de bewerking is voltooid (standaardwaarde)
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `worker:list`

Een lijst met alle geïmplementeerde workers ophalen

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

<!-- app.name -->

```bash
workers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--refresh`

Of de cache moet worden vernieuwd
- Standaard: `false`
- Accepteert geen waarde



### `--project`, `-p`



De project-id of URL
- Vereist een waarde


### `--host`

De API-hostnaam van het project
- Vereist een waarde



### `--environment`, `-e`



De milieu-id
- Vereist een waarde


### `--format`

De uitvoerindeling (&quot;table&quot;, &quot;csv&quot;, &quot;tsv&quot; of &quot;plain&quot;)
- Standaard: `table`
- Vereist een waarde


### `--columns`

Weer te geven kolommen (lijst met door komma&#39;s gescheiden waarden of meerdere waarden)
- Standaard: `[]`
- Vereist een waarde


### `--no-header`

De tabelkoptekst niet uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--yes`, `-y`



Antwoord &quot;ja&quot; op ja/nee-vragen interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no`, `-n`



Antwoord &quot;nee&quot; op ja/nee-vragen. interactie uitschakelen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->