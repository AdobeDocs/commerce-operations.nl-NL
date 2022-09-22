---
source-git-commit: a5777f437430bc48b87aaea65c0e101d4ecd6574
workflow-type: tm+mt
source-wordcount: '15643'
ht-degree: 0%

---
# bin/magento (Adobe Commerce op het terrein)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**Versie**: 2.4.5. <!-- app.version -->

Deze verwijzing bevat 118 bevelen beschikbaar door `bin/magento` opdrachtregelprogramma.
De eerste lijst wordt automatisch gegenereerd met de opdracht `bin/magento list` in de editie.
Gebruik de [&quot;CLI-opdrachten toevoegen&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) gids om een douane CLI bevel toe te voegen.

>[!NOTE]
>
>U kunt bellen `bin/magento` CLI bevelen die kortere weg in plaats van de volledige bevelnaam gebruiken. U kunt bijvoorbeeld `bin/magento setup:upgrade` gebruiken `bin/magento s:up`, `bin/magento s:upg`. Zie [sneltoetssyntaxis](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) om te begrijpen hoe te om kortere weg met om het even welk bevel CLI te gebruiken.

>[!NOTE]
>
>Deze verwijzing wordt gegenereerd op basis van de codebase van de toepassing. Als u de inhoud wilt wijzigen, kunt u de broncode voor de corresponderende opdrachtimplementatie bijwerken in het dialoogvenster [codebase](https://github.com/magento) opslaan en uw wijzigingen ter controle verzenden. Een andere manier is om _Feedback geven_ (zoek de koppeling in de rechterbovenhoek). Zie voor richtsnoeren voor bijdragen [Codebijdragen](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

Help weergeven voor een opdracht

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `list`

Lijstopdrachten

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
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

## `admin:adobe-ims:disable`

Adobe IMS-module uitschakelen

```bash
bin/magento admin:adobe-ims:disable
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `admin:adobe-ims:enable`

Schakel Adobe IMS Module in.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--organization-id`, `-o`



Organisatie-id instellen voor Adobe IMS-configuratie. Vereist wanneer het toelaten van de module
- Accepteert een waarde



### `--client-id`, `-c`



Stel de client-id in voor de Adobe IMS-configuratie. Vereist wanneer het toelaten van de module
- Accepteert een waarde



### `--client-secret`, `-s`



Stel het clientgeheim in voor de configuratie van Adobe IMS. Vereist wanneer het toelaten van de module
- Accepteert een waarde



### `--2fa`, `-t`



Controleer of 2FA is ingeschakeld voor Organisatie in Adobe Admin Console. Vereist wanneer het toelaten van de module
- Accepteert een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `admin:adobe-ims:info`

Informatie over de configuratie van de Adobe IMS-module

```bash
bin/magento admin:adobe-ims:info
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `admin:adobe-ims:status`

Status van de Adobe IMS-module

```bash
bin/magento admin:adobe-ims:status
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `admin:user:create`

Hiermee wordt een beheerder gemaakt

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--admin-user`

(Vereist) Admin-gebruiker
- Vereist een waarde


### `--admin-password`

(Vereist) Beheerderswachtwoord
- Vereist een waarde


### `--admin-email`

(Vereist) E-mail beheerder
- Vereist een waarde


### `--admin-firstname`

(Vereist) Voornaam beheerder
- Vereist een waarde


### `--admin-lastname`

(Vereist) Achternaam beheerder
- Vereist een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `admin:user:unlock`

Beheerdersaccount ontgrendelen

```bash
bin/magento admin:user:unlock <username>
```

<!-- app.name --> <!-- command.usage -->

### `username`

De te ontgrendelen admin-gebruikersnaam
- Vereist

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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `app:config:dump`

Stortplaats van toepassing maken

```bash
bin/magento app:config:dump [<config-types>...]
```

<!-- app.name --> <!-- command.usage -->

### `config-types`

Lijst met door spaties gescheiden configuratietypen of het weglaten om alles te dumpen [bereik, thema&#39;s, systeem, i18n]

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `app:config:import`

Gegevens uit gedeelde configuratiebestanden importeren naar de juiste gegevensopslag

```bash
bin/magento app:config:import
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `app:config:status`

Controleert of config-propagatie update vereist

```bash
bin/magento app:config:status
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `braintree:migrate`

Opgeslagen kaarten migreren vanuit een Magento 1-database

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

Hostnaam/IP. Poort is optioneel
- Vereist een waarde


### `--dbname`

Databasenaam
- Vereist een waarde


### `--username`

Gebruikersnaam database. Leestoegang vereist
- Vereist een waarde


### `--password`

Wachtwoord
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `cache:clean`

Hiermee worden cachetype(s) gewist

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `cache:disable`

Cachetype(s) uitschakelen

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `cache:enable`

Cachetype(s) inschakelen

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `cache:flush`

Cacheopslag wordt gebruikt door cachetype(s)

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `cache:status`

Hiermee wordt de cachestatus gecontroleerd

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `catalog:images:resize`

Hiermee maakt u productafbeeldingen waarvan het formaat is gewijzigd

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--async`, `-a`



Afbeeldingen vergroten/verkleinen in asynchrone modus
- Standaard: `false`
- Accepteert geen waarde


### `--skip_hidden_images`

Afbeeldingen die als verborgen op de productpagina zijn gemarkeerd, niet verwerken
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `catalog:product:attributes:cleanup`

Verwijdert ongebruikte productkenmerken.

```bash
bin/magento catalog:product:attributes:cleanup
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `cms:wysiwyg:restrict`

Instellen of validatie van HTML-inhoud van gebruiker moet worden afgedwongen of een waarschuwing moet worden weergegeven

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

<!-- app.name --> <!-- command.usage -->

### `restrict`

y\n
- Vereist

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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `config:sensitive:set`

Gevoelige configuratiewaarden instellen

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Configuratiepad, bijvoorbeeld groep/sectie/field_name
<!-- argument -->

### `value`

Configuratiewaarde
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--interactive`, `-i`



Interactieve modus inschakelen om alle gevoelige variabelen in te stellen
- Standaard: `false`
- Accepteert geen waarde


### `--scope`

Bereik voor configuratie, indien niet ingesteld gebruik &#39;default&#39;
- Standaard: `default`
- Accepteert een waarde


### `--scope-code`

Toepassingscode voor configuratie, standaard lege tekenreeks
- Standaard: &quot;
- Accepteert een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `config:set`

Systeemconfiguratie wijzigen

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Configuratiepad in indelingssectie/groep/veld_naam
- Vereist

   <!-- argument -->

### `value`

Configuratiewaarde
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

Configuratiebereik (standaard, website of winkel)
- Standaard: `default`
- Vereist een waarde


### `--scope-code`

Code bereik (alleen vereist als scope niet &#39;default&#39; is)
- Vereist een waarde



### `--lock-env`, `-e`



Vergrendelingswaarde die wijziging in de beheerfunctie voorkomt (wordt opgeslagen in app/etc/env.php)
- Standaard: `false`
- Accepteert geen waarde



### `--lock-config`, `-c`



Vergrendelen en waarde delen met andere installaties, wijzigingen voorkomen in Admin (wordt opgeslagen in app/etc/config.php)
- Standaard: `false`
- Accepteert geen waarde



### `--lock`, `-l`



Vervangen, gebruik in plaats hiervan de optie —lock-env.
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `config:show`

Toont configuratiewaarde voor bepaalde weg. Als het pad niet is opgegeven, worden alle opgeslagen waarden weergegeven

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Configuratiepad, bijvoorbeeld section_id/group_id/field_id
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

Bereik voor configuratie, als niet gespecificeerd, dan &quot;gebrek&quot;werkingsgebied zal worden gebruikt
- Standaard: `default`
- Accepteert een waarde


### `--scope-code`

Code bereik (alleen vereist als het bereik niet is ingesteld) `default`)
- Standaard: &quot;
- Accepteert een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `cron:install`

Genereert en installeert een tab voor de huidige gebruiker

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Installatietaken forceren
- Standaard: `false`
- Accepteert geen waarde



### `--non-optional`, `-d`



Alleen de niet-optionele (standaard)taken installeren
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `cron:remove`

Hiermee worden taken uit het tabblad Crontab verwijderd

```bash
bin/magento cron:remove
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `cron:run`

Hiermee worden taken volgens schema uitgevoerd

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--group`

Alleen taken uitvoeren vanuit opgegeven groep
- Vereist een waarde


### `--bootstrap`

Parameters van de bootstrap toevoegen of overschrijven
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `customer:hash:upgrade`

De hash van de klant bijwerken volgens het meest recente algoritme

```bash
bin/magento customer:hash:upgrade
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `deploy:mode:set`

Toepassingsmodus instellen.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

<!-- app.name --> <!-- command.usage -->

### `mode`

De toepassingsmodus die moet worden ingesteld. Beschikbare opties zijn &quot;developer&quot; of &quot;production&quot;
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-compilation`, `-s`



Hiermee slaat u het wissen en opnieuw genereren van statische inhoud (gegenereerde code, vooraf verwerkte CSS en elementen in pub/static/) over.
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `deploy:mode:show`

Geeft de huidige toepassingsmodus weer.

```bash
bin/magento deploy:mode:show
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:di:info`

Verstrekt informatie over de configuratie van de Injectie van de Afhankelijkheid voor het Bevel.

```bash
bin/magento dev:di:info <class>
```

<!-- app.name --> <!-- command.usage -->

### `class`

Klassenaam
- Vereist

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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:email:newsletter-compatibility-check`

Scant nieuwsbrieven sjablonen voor mogelijke compatibiliteitsproblemen met variabeleverbruik

```bash
bin/magento dev:email:newsletter-compatibility-check
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:email:override-compatibility-check`

Scant e-mailsjabloonoverschrijvingen voor mogelijke compatibiliteitsproblemen met variabelengebruik

```bash
bin/magento dev:email:override-compatibility-check
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:profiler:disable`

De analyse uitschakelen.

```bash
bin/magento dev:profiler:disable
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:profiler:enable`

De analyse inschakelen.

```bash
bin/magento dev:profiler:enable [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

Het type Profiler
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:query-log:disable`

Logbestand van DB-query uitschakelen

```bash
bin/magento dev:query-log:disable
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:query-log:enable`

Logbestand van DB-query inschakelen

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--include-all-queries`

Log alle query&#39;s. [true\|false]
- Standaard: `true`
- Accepteert een waarde


### `--query-time-threshold`

Drempelwaarden voor zoektijd.
- Standaard: `0.001`
- Accepteert een waarde


### `--include-call-stack`

Inclusief aanroepstack. [true\|false]
- Standaard: `true`
- Accepteert een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:source-theme:deploy`

Hiermee worden bronbestanden voor thema verzameld en gepubliceerd.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

<!-- app.name --> <!-- command.usage -->

### `file`

Bestanden die vooraf moeten worden verwerkt (bestand moet worden opgegeven zonder extensie)
- Standaard: `css/styles-mcss/styles-l`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Type bronbestanden: [minder]
- Standaard: `less`
- Vereist een waarde


### `--locale`

Landinstelling: [nl_NL]
- Standaard: `en_US`
- Vereist een waarde


### `--area`

Gebied: [frontEnd\|adminhtml]
- Standaard: `frontend`
- Vereist een waarde


### `--theme`

Thema: [Leverancier/thema]
- Standaard: `Magento/luma`
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:template-hints:disable`

Tips voor frontend-sjablonen uitschakelen. Wellicht is een cache-leegloop vereist.

```bash
bin/magento dev:template-hints:disable
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:template-hints:enable`

Tips voor frontend sjablonen inschakelen. Wellicht is een cache-leegloop vereist.

```bash
bin/magento dev:template-hints:enable
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:template-hints:status`

Toon de status van frontend malplaatjewenken.

```bash
bin/magento dev:template-hints:status
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:tests:run`

Tests bij uitvoering

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

Type test dat moet worden uitgevoerd. Beschikbare typen: all, unit, integration, integration-all, static, static-all, integriteit, legacy, default
- Standaard: `default`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--arguments`, `-c`



Aanvullende argumenten voor PHPUnit. Voorbeeld: &quot;-c&#39;—filter=MyTest&#39;&#39; (geen spaties)
- Standaard: &quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:urn-catalog:generate`

Hiermee genereert u de catalogus van URL&#39;s naar *.xsd-toewijzingen voor de IDE om xml te markeren.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Pad naar bestand om de catalogus uit te voeren. Voor PHPStorm-gebruik .idea/misc.xml
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--ide`

Indeling waarin de catalogus wordt gegenereerd. Ondersteund: [phpstorm, vscode]
- Standaard: `phpstorm`
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `dev:xml:convert`

Hiermee wordt een XML-bestand geconverteerd met XSL-stijlpagina&#39;s

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

<!-- app.name --> <!-- command.usage -->

### `xml-file`

Pad naar XML-bestand dat moet worden getransformeerd
- Vereist

   <!-- argument -->

### `processor`

Pad naar XSL-stijlpagina die wordt toegepast op XML-bestand
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--overwrite`, `-o`



XML-bestand overschrijven
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `downloadable:domains:add`

Domeinen toevoegen aan de whitelist van downloadbare domeinen

```bash
bin/magento downloadable:domains:add [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

Naam van domein

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `downloadable:domains:remove`

Domeinen verwijderen uit de whitelist van downloadbare domeinen

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

Domeinnamen

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `downloadable:domains:show`

Downloadbare whitelist van domeinen weergeven

```bash
bin/magento downloadable:domains:show
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `encryption:payment-data:update`

Codeert gecodeerde creditcardgegevens opnieuw met de nieuwste coderingssleutel.

```bash
bin/magento encryption:payment-data:update
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `i18n:collect-phrases`

Neemt zinnen op in de codebase

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

<!-- app.name --> <!-- command.usage -->

### `directory`

Mappad om te parseren. Niet nodig indien —magento-markering is ingesteld
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--output`, `-o`



Pad (inclusief bestandsnaam) naar een uitvoerbestand. Als er geen bestand is opgegeven, wordt standaard stdout toegepast.
- Vereist een waarde



### `--magento`, `-m`



Gebruik de parameter —magento om de huidige Magento-codebase te parseren. Laat de parameter weg als een folder wordt gespecificeerd.
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `i18n:pack`

Slaat taalpakket op

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

<!-- app.name --> <!-- command.usage -->

### `source`

Pad naar bronwoordenboekbestand met vertalingen
- Vereist

   <!-- argument -->

### `locale`

Doellandinstelling voor woordenboek, bijvoorbeeld &quot;de_DE&quot;
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--mode`, `-m`



Modus Opslaan voor woordenboek - &quot;replace&quot; - taalpakket vervangen door nieuw - &quot;merge&quot; - taalpakketten samenvoegen door standaard &quot;replace&quot;
- Standaard: `replace`
- Vereist een waarde



### `--allow-duplicates`, `-d`



Gebruik de parameter —allow-duplicates om het opslaan van duplicaten van translate toe te staan. Laat anders de parameter weg.
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `i18n:uninstall`

Verwijdert taalpakketten

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

<!-- app.name --> <!-- command.usage -->

### `package`

Taalpakketnaam

- Standaard: `[]`
- Vereist

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--backup-code`, `-b`



Back-up maken van code- en configuratiebestanden (met uitzondering van tijdelijke bestanden)
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `indexer:info`

Toegestane indexen weergeven

```bash
bin/magento indexer:info
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `indexer:reindex`

Gegevens opnieuw indexeren

```bash
bin/magento indexer:reindex [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `indexer:reset`

Hiermee wordt de status van de indexeerder opnieuw ingesteld op ongeldig

```bash
bin/magento indexer:reset [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `indexer:set-dimensions-mode`

Modus Dimension indexeren instellen

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

Indexnaam [catalog_product_price|catalogispermissions_category]
<!-- argument -->

### `mode`

Indexer-dimensie-modi catalog_product_price none,website,customer_group,website_and_customer_group catalogispermissions_category none,customer_group
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `indexer:set-mode`

Hiermee wordt het type indexmodus ingesteld

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

<!-- app.name --> <!-- command.usage -->

### `mode`

Type indexmodus [realtime|plannen]
<!-- argument -->

### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `indexer:show-dimensions-mode`

Modus Dimension van index weergeven

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

Lijst met door spaties gescheiden indextypen of laat deze weg om toe te passen op alle indexen (catalog_product_price,catalogpermissions_category)

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `indexer:show-mode`

Indexmodus weergeven

```bash
bin/magento indexer:show-mode [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `indexer:status`

Hiermee wordt de status van Indexer weergegeven

```bash
bin/magento indexer:status [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `info:adminuri`

Hiermee wordt de URI voor Magento-beheer weergegeven

```bash
bin/magento info:adminuri
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `info:backups:list`

Lijst met beschikbare back-upbestanden afdrukken

```bash
bin/magento info:backups:list
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `info:currency:list`

Geeft de lijst met beschikbare valuta&#39;s weer

```bash
bin/magento info:currency:list
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `info:dependencies:show-framework`

Geeft het aantal afhankelijkheden weer van het Magento-framework

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Bestandsnaam rapport
- Standaard: `framework-dependencies.csv`
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules`

Toont aantal gebiedsdelen tussen modules

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Bestandsnaam rapport
- Standaard: `modules-dependencies.csv`
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules-circular`

Toont aantal kringafhankelijkheden tussen modules

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Bestandsnaam rapport
- Standaard: `modules-circular-dependencies.csv`
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `info:language:list`

Hiermee geeft u de lijst met beschikbare taallandinstellingen weer

```bash
bin/magento info:language:list
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `info:timezone:list`

Hiermee geeft u de lijst met beschikbare tijdzones weer

```bash
bin/magento info:timezone:list
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `inventory:reservation:create-compensations`

Maak punten van voorbehoud door middel van opgegeven compensatieargumenten

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

<!-- app.name --> <!-- command.usage -->

### `compensations`

Lijst van compensatieargumenten in formaat &quot;&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--raw`, `-r`



Onbewerkte uitvoer
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `inventory:reservation:list-inconsistencies`

Alle bestellingen en producten met inconsistenties in verkoopbare hoeveelheid tonen

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--complete-orders`, `-c`



Alleen inconsistenties voor volledige bestellingen tonen
- Standaard: `false`
- Accepteert geen waarde



### `--incomplete-orders`, `-i`



Alleen inconsistenties tonen voor onvolledige orders
- Standaard: `false`
- Accepteert geen waarde



### `--bunch-size`, `-b`



Hiermee bepaalt u hoeveel bestellingen tegelijkertijd worden geladen
- Standaard: `50`
- Accepteert een waarde



### `--raw`, `-r`



Onbewerkte uitvoer
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `inventory-geonames:import`

Geo-namen downloaden en importeren voor het algoritme van de bronselectie

```bash
bin/magento inventory-geonames:import <countries>...
```

<!-- app.name --> <!-- command.usage -->

### `countries`

Lijst van landcodes die moeten worden ingevoerd

- Standaard: `[]`
- Vereist

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `maintenance:allow-ips`

Plaatst onderhoudswijze vrijgestelde IPs

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

<!-- app.name --> <!-- command.usage -->

### `ip`

Toegestane IP adressen

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--none`

Toegestane IP-adressen wissen
- Standaard: `false`
- Accepteert geen waarde


### `--add`

IP-adres toevoegen aan bestaande lijst
- Standaard: `false`
- Accepteert geen waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `maintenance:disable`

Onderhoudsmodus uitschakelen

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

Toegestane IP adressen (gebruik &quot;niets&quot;om toegestane IP lijst te ontruimen)
- Standaard: `[]`
- Vereist een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `maintenance:enable`

Onderhoudsmodus inschakelen

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

Toegestane IP adressen (gebruik &quot;niets&quot;om toegestane IP lijst te ontruimen)
- Standaard: `[]`
- Vereist een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `maintenance:status`

De status van de onderhoudsmodus weergeven

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `media-content:sync`

Inhoud synchroniseren met elementen

```bash
bin/magento media-content:sync
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `media-gallery:sync`

Mediaopslag en media-elementen in de database synchroniseren

```bash
bin/magento media-gallery:sync
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `module:config:status`

Controleert de moduleconfiguratie in het &quot;app/etc/config.php&quot;dossier en rapporteert als zij of niet bijgewerkt zijn

```bash
bin/magento module:config:status
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `module:disable`

Hiermee worden opgegeven modules uitgeschakeld

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

Naam van de module

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



Controle voor passageafhankelijkheden
- Standaard: `false`
- Accepteert geen waarde


### `--all`

Alle modules uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--clear-static-content`, `-c`



Gegenereerde statische weergavebestanden wissen. Noodzakelijk als de module(s) statische weergavebestanden heeft
- Standaard: `false`
- Accepteert geen waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `module:enable`

Hiermee worden opgegeven modules ingeschakeld

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

Naam van de module

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



Controle voor passageafhankelijkheden
- Standaard: `false`
- Accepteert geen waarde


### `--all`

Alle modules inschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--clear-static-content`, `-c`



Gegenereerde statische weergavebestanden wissen. Noodzakelijk als de module(s) statische weergavebestanden heeft
- Standaard: `false`
- Accepteert geen waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `module:status`

Geeft de status van modules weer

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

<!-- app.name --> <!-- command.usage -->

### `module-names`

Optionele modulenaam

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--enabled`

Alleen ingeschakelde modules afdrukken
- Standaard: `false`
- Accepteert geen waarde


### `--disabled`

Alleen uitgeschakelde modules afdrukken
- Standaard: `false`
- Accepteert geen waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `module:uninstall`

Hiermee verwijdert u modules die door de composer zijn geïnstalleerd

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

<!-- app.name --> <!-- command.usage -->

### `module`

Naam van de module

- Standaard: `[]`
- Vereist

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--remove-data`, `-r`



Gegevens verwijderen die zijn geïnstalleerd door module(s)
- Standaard: `false`
- Accepteert geen waarde


### `--backup-code`

Back-up maken van code- en configuratiebestanden (met uitzondering van tijdelijke bestanden)
- Standaard: `false`
- Accepteert geen waarde


### `--backup-media`

Mediaback-up maken
- Standaard: `false`
- Accepteert geen waarde


### `--backup-db`

Volledige back-up van de database maken
- Standaard: `false`
- Accepteert geen waarde


### `--non-composer`

Alle modules, die hier voorbij zullen zijn zullen niet op composer gebaseerd zijn
- Standaard: `false`
- Accepteert geen waarde



### `--clear-static-content`, `-c`



Gegenereerde statische weergavebestanden wissen. Noodzakelijk als de module(s) statische weergavebestanden heeft
- Standaard: `false`
- Accepteert geen waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `newrelic:create:deploy-marker`

Controleer de opstellen rij voor ingangen en creeer aangewezen plaatsingsteller.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

<!-- app.name --> <!-- command.usage -->

### `message`

Bericht implementeren?
- Vereist

   <!-- argument -->

### `change_log`

Logboek wijzigen?
- Vereist

   <!-- argument -->

### `user`

Implementatiegebruiker
<!-- argument -->

### `revision`

Herziening
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `queue:consumers:list`

Lijst met consumenten van MessageQueue

```bash
bin/magento queue:consumers:list
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `queue:consumers:start`

MessageQueue-consument starten

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

<!-- app.name --> <!-- command.usage -->

### `consumer`

De naam van de consument die moet worden gestart.
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--max-messages`

Het aantal berichten dat de consument moet verwerken voordat het proces wordt beëindigd. Indien niet gespecificeerd - eindig na verwerking van alle een rij gevormde berichten.
- Vereist een waarde


### `--batch-size`

Het aantal berichten per partij. Alleen van toepassing op de partijconsument.
- Vereist een waarde


### `--area-code`

De standaardinstelling voor het voorkeursgebied (global, adminhtml, etc..) is global.
- Vereist een waarde


### `--single-thread`

Met deze optie voorkomt u dat meerdere exemplaren van één consument tegelijk worden uitgevoerd.
- Standaard: `false`
- Accepteert geen waarde


### `--multi-process`

Het aantal processen per consument.
- Accepteert een waarde


### `--pid-file-path`

Het bestandspad voor het opslaan van PID (deze optie is afgekeurd, gebruik —enkele thread in plaats daarvan)
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `remote-storage:sync`

Mediabestanden synchroniseren met externe opslag.

```bash
bin/magento remote-storage:sync
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `sampledata:deploy`

Stel steekproefgegevensmodules voor op composer-gebaseerde Magento installaties op

```bash
bin/magento sampledata:deploy [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

Composer.json bijwerken zonder composer-update uit te voeren
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `sampledata:remove`

Alle pakketten met voorbeeldgegevens verwijderen uit composer.json

```bash
bin/magento sampledata:remove [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

Composer.json bijwerken zonder composer-update uit te voeren
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `sampledata:reset`

Alle modules met voorbeeldgegevens opnieuw instellen voor herinstallatie

```bash
bin/magento sampledata:reset
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-forgot-password`

reCAPTCHA uitschakelen voor wachtwoordformulier voor vergeten gebruiker van beheerder

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-login`

reCAPTCHA uitschakelen voor aanmeldingsformulier voor beheerder

```bash
bin/magento security:recaptcha:disable-for-user-login
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `security:tfa:google:set-secret`

Stel het geheim in dat voor Google OTP-generatie wordt gebruikt.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

<!-- app.name --> <!-- command.usage -->

### `user`

Gebruikersnaam
- Vereist

   <!-- argument -->

### `secret`

Geheim
- Vereist

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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `security:tfa:providers`

Alle beschikbare providers weergeven

```bash
bin/magento security:tfa:providers
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `security:tfa:reset`

Configuratie voor één gebruiker opnieuw instellen

```bash
bin/magento security:tfa:reset <user> <provider>
```

<!-- app.name --> <!-- command.usage -->

### `user`

Gebruikersnaam
- Vereist

   <!-- argument -->

### `provider`

Providercode
- Vereist

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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:backup`

Maakt een back-up van de Magento Application Code base, media en database

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--code`

Back-up maken van code- en configuratiebestanden (met uitzondering van tijdelijke bestanden)
- Standaard: `false`
- Accepteert geen waarde


### `--media`

Mediaback-up maken
- Standaard: `false`
- Accepteert geen waarde


### `--db`

Volledige back-up van de database maken
- Standaard: `false`
- Accepteert geen waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:config:set`

Creeert of wijzigt de plaatsingsconfiguratie

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

Backend frontname (wordt automatisch gegenereerd als deze ontbreekt)
- Vereist een waarde


### `--enable-debug-logging`

Foutopsporingsregistratie inschakelen
- Vereist een waarde


### `--enable-syslog-logging`

Syslog-logboekregistratie inschakelen
- Vereist een waarde


### `--remote-storage-driver`

Extern opslagstuurprogramma
- Vereist een waarde


### `--remote-storage-prefix`

Voorvoegsel voor externe opslag
- Standaard: &quot;
- Vereist een waarde


### `--remote-storage-endpoint`

Extern opslageindpunt
- Vereist een waarde


### `--remote-storage-bucket`

Externe opslagemmer
- Vereist een waarde


### `--remote-storage-region`

Externe opslagregio
- Vereist een waarde


### `--remote-storage-key`

Toegangstoets externe opslag
- Standaard: &quot;
- Vereist een waarde


### `--remote-storage-secret`

Externe geheim van opslagsleutel
- Standaard: &quot;
- Vereist een waarde


### `--remote-storage-path-style`

Padstijl externe opslag
- Standaard: `0`
- Vereist een waarde


### `--checkout-async`

Afwisselende orderverwerking inschakelen? 1 - Ja, 0 - Nee
- Vereist een waarde


### `--amqp-host`

Amqp-serverhost
- Standaard: &quot;
- Vereist een waarde


### `--amqp-port`

Amqp-serverpoort
- Standaard: `5672`
- Vereist een waarde


### `--amqp-user`

Gebruikersnaam Amqp-server
- Standaard: &quot;
- Vereist een waarde


### `--amqp-password`

Wachtwoord Amqp-server
- Standaard: &quot;
- Vereist een waarde


### `--amqp-virtualhost`

AMQP virtualhost
- Standaard: `/`
- Vereist een waarde


### `--amqp-ssl`

Amqp SSL
- Standaard: &quot;
- Vereist een waarde


### `--amqp-ssl-options`

Amqp SSL-opties (JSON)
- Standaard: &quot;
- Vereist een waarde


### `--consumers-wait-for-messages`

Moeten consumenten wachten op een bericht uit de wachtrij? 1 - Ja, 0 - Nee
- Vereist een waarde


### `--queue-default-connection`

Standaardverbinding in wachtrij met berichten. Kan &#39;db&#39;, &#39;amqp&#39; of een aangepast wachtrijsysteem zijn. Het wachtrijsysteem moet worden geïnstalleerd en geconfigureerd, anders worden de berichten niet correct verwerkt.
- Vereist een waarde


### `--deferred-total-calculating`

Uitgestelde totale berekening inschakelen? 1 - Ja, 0 - Nee
- Vereist een waarde


### `--key`

Versleutelingssleutel
- Vereist een waarde


### `--db-host`

Host databaseserver
- Vereist een waarde


### `--db-name`

Databasenaam
- Vereist een waarde


### `--db-user`

Gebruikersnaam databaseserver
- Vereist een waarde


### `--db-engine`

Database-server-engine
- Vereist een waarde


### `--db-password`

Wachtwoord databaseserver
- Vereist een waarde


### `--db-prefix`

Voorvoegsel databasetabel
- Vereist een waarde


### `--db-model`

Type database
- Vereist een waarde


### `--db-init-statements`

Eerste set opdrachten database
- Vereist een waarde



### `--skip-db-validation`, `-s`



Indien opgegeven, wordt de validatie van de db-verbinding overgeslagen
- Standaard: `false`
- Accepteert geen waarde


### `--http-cache-hosts`

http-cachehosts
- Vereist een waarde


### `--db-ssl-key`

Volledig pad van clientsleutelbestand om een databaseverbinding tot stand te brengen via SSL
- Standaard: &quot;
- Vereist een waarde


### `--db-ssl-cert`

Volledig pad van clientcertificaatbestand om een databaseverbinding tot stand te brengen via SSL
- Standaard: &quot;
- Vereist een waarde


### `--db-ssl-ca`

Volledig pad van servercertificaatbestand om een databaseverbinding tot stand te brengen via SSL
- Standaard: &quot;
- Vereist een waarde


### `--db-ssl-verify`

Servercertificering controleren
- Standaard: `false`
- Accepteert geen waarde


### `--session-save`

Sessieopslaghandler
- Vereist een waarde


### `--session-save-redis-host`

Volledig - gekwalificeerde gastheernaam, IP adres, of absolute weg als het gebruiken van de contactdozen van UNIX
- Vereist een waarde


### `--session-save-redis-port`

Redis-poort voor luisteren naar server
- Vereist een waarde


### `--session-save-redis-password`

Wachtwoord voor opnieuw verzonden server
- Vereist een waarde


### `--session-save-redis-timeout`

Time-out verbinding, in seconden
- Vereist een waarde


### `--session-save-redis-persistent-id`

Unieke tekenreeks om permanente verbindingen in te schakelen
- Vereist een waarde


### `--session-save-redis-db`

Databasenummer van Redis
- Vereist een waarde


### `--session-save-redis-compression-threshold`

Compressiedrempel opnieuw instellen
- Vereist een waarde


### `--session-save-redis-compression-lib`

Compressiebibliotheek opnieuw uitschakelen. Waarden: gzip (standaardwaarde), lzf, lz4, snappy
- Vereist een waarde


### `--session-save-redis-log-level`

Opnieuw schijflogniveau. Waarden: 0 (minst uitgebreid) tot 7 (meest uitgebreide)
- Vereist een waarde


### `--session-save-redis-max-concurrency`

Maximum aantal processen dat op een slot op één zitting kan wachten
- Vereist een waarde


### `--session-save-redis-break-after-frontend`

Aantal seconden dat moet worden gewacht voordat wordt geprobeerd een vergrendeling voor een frontendsessie te verbreken
- Vereist een waarde


### `--session-save-redis-break-after-adminhtml`

Aantal seconden dat moet worden gewacht voordat wordt geprobeerd een vergrendeling voor beheersessie te verbreken
- Vereist een waarde


### `--session-save-redis-first-lifetime`

Levensduur, in seconden, van sessie voor niet-bots bij eerste schrijven (gebruik 0 om uit te schakelen)
- Vereist een waarde


### `--session-save-redis-bot-first-lifetime`

Levensduur, in seconden, van sessie voor bots bij de eerste schrijfbewerking (gebruik 0 om uit te schakelen)
- Vereist een waarde


### `--session-save-redis-bot-lifetime`

De levensduur van de sessie voor bots bij volgende schrijvingen (gebruik 0 om uit te schakelen)
- Vereist een waarde


### `--session-save-redis-disable-locking`

Schakel vergrendeling opnieuw uit. Waarden: false (standaardwaarde), true
- Vereist een waarde


### `--session-save-redis-min-lifetime`

Herdis min sessieduur, in seconden
- Vereist een waarde


### `--session-save-redis-max-lifetime`

Maximale sessielevensduur van Redis, in seconden
- Vereist een waarde


### `--session-save-redis-sentinel-master`

Redis Sentinel master
- Vereist een waarde


### `--session-save-redis-sentinel-servers`

Redis Sentinel-servers, gescheiden door komma&#39;s
- Vereist een waarde


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifieert master. Waarden: false (standaard), true
- Vereist een waarde


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel verbindt opnieuw pogingen.
- Vereist een waarde


### `--cache-backend`

Standaardcachehandler
- Vereist een waarde


### `--cache-backend-redis-server`

Redis-server
- Vereist een waarde


### `--cache-backend-redis-db`

Databasenummer voor de cache
- Vereist een waarde


### `--cache-backend-redis-port`

Redis-poort voor luisteren naar server
- Vereist een waarde


### `--cache-backend-redis-password`

Wachtwoord voor opnieuw verzonden server
- Vereist een waarde


### `--cache-backend-redis-compress-data`

Instellen op 0 om compressie uit te schakelen (standaard is 1, ingeschakeld)
- Vereist een waarde


### `--cache-backend-redis-compression-lib`

Te gebruiken compressielabel [snappy,lzf,l4z,zstd,gzip] (leeg laten om automatisch te bepalen)
- Vereist een waarde


### `--cache-id-prefix`

ID-voorvoegsel voor cachesleutels
- Vereist een waarde


### `--allow-parallel-generation`

Genereren van cache op een niet-blokkerende manier toestaan
- Standaard: `false`
- Accepteert geen waarde


### `--page-cache`

Standaardcachehandler
- Vereist een waarde


### `--page-cache-redis-server`

Redis-server
- Vereist een waarde


### `--page-cache-redis-db`

Databasenummer voor de cache
- Vereist een waarde


### `--page-cache-redis-port`

Redis-poort voor luisteren naar server
- Vereist een waarde


### `--page-cache-redis-password`

Wachtwoord voor opnieuw verzonden server
- Vereist een waarde


### `--page-cache-redis-compress-data`

Ingesteld op 1 om de cache van de volledige pagina te comprimeren (gebruik 0 om uit te schakelen)
- Vereist een waarde


### `--page-cache-redis-compression-lib`

Te gebruiken compressiebibliotheek [snappy,lzf,l4z,zstd,gzip] (leeg laten om automatisch te bepalen)
- Vereist een waarde


### `--page-cache-id-prefix`

ID-voorvoegsel voor cachesleutels
- Vereist een waarde


### `--lock-provider`

Naam provider vergrendelen
- Vereist een waarde


### `--lock-db-prefix`

Installatiespecifiek vergrendelingsvoorvoegsel om vergrendelingsconflicten te voorkomen
- Vereist een waarde


### `--lock-zookeeper-host`

Host en poort voor verbinding met Zookeeper-cluster. Bijvoorbeeld: 127.0.0.1:2181
- Vereist een waarde


### `--lock-zookeeper-path`

Het pad waar Zookeeper vergrendelingen opslaat. Het standaardpad is: /magento/locks
- Vereist een waarde


### `--lock-file-path`

Het pad waar de bestandsvergrendelingen worden opgeslagen.
- Vereist een waarde


### `--document-root-is-pub`

Markering om te tonen is dat Pub zich op de hoofdmap bevindt, kan alleen waar of onwaar zijn
- Vereist een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:db-data:upgrade`

Hiermee installeert en verbetert u gegevens in de database

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-patch`

Patch genereren en in specifieke map plaatsen.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

<!-- app.name --> <!-- command.usage -->

### `module`

Modulenaam
- Vereist

   <!-- argument -->

### `patch`

Patchnaam
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--revertable`

Controleer of de patch kan worden teruggedraaid of niet.
- Standaard: `false`
- Accepteert een waarde


### `--type`

Ontdek welk type patch moet worden gegenereerd. Beschikbare waarden: `data`, `schema`.
- Standaard: `data`
- Accepteert een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-whitelist`

Een whitelist genereren van tabellen en kolommen die door het installatieprogramma van de declaratie mogen worden bewerkt

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--module-name`

Naam van de module waar whitelist wordt gegenereerd
- Standaard: `all`
- Accepteert een waarde



### `--help`, `-h`



Dit Help-bericht weergeven
- Standaard: `false`
- Accepteert geen waarde



### `--quiet`, `-q`



Geen bericht uitvoeren
- Standaard: `false`
- Accepteert geen waarde



### `--verbose`, `-v|-vv|-vvv`



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:db-schema:add-slave`

Aan een betalingsaanhalingsteken gerelateerde tabellen verplaatsen naar een aparte databaseserver

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

Slave DB Server-host
- Standaard: `localhost`
- Vereist een waarde


### `--dbname`

Naam slave-database
- Vereist een waarde


### `--username`

Gebruikersnaam slave DB
- Standaard: `root`
- Vereist een waarde


### `--password`

Wachtwoord slave DB
- Accepteert een waarde


### `--connection`

Naam slave-verbinding
- Standaard: `default`
- Accepteert een waarde


### `--resource`

Naam slave-bron
- Standaard: `default`
- Accepteert een waarde


### `--maxAllowedLag`

Max. toegestane lave-verbinding voor lave (in seconden)
- Standaard: &quot;
- Accepteert een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:db-schema:split-quote`

Verplaats de aan uitchecken gerelateerde tabellen naar een aparte DB-server. Vervangen vanaf 2.4.2 en verwijderd

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

Uitchecken DB Server-host
- Vereist een waarde


### `--dbname`

Database-naam uitchecken
- Vereist een waarde


### `--username`

Gebruikersnaam database voor uitchecken
- Vereist een waarde


### `--password`

Wachtwoord database voor afhandeling
- Accepteert een waarde


### `--connection`

Verbindingsnaam uitchecken
- Standaard: `checkout`
- Accepteert een waarde


### `--resource`

Naam van resource voor uitchecken
- Standaard: `checkout`
- Accepteert een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:db-schema:split-sales`

Verplaats verkoopgerelateerde tabellen naar een aparte DB-server. Vervangen vanaf 2.4.2 en verwijderd

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--host`

Verkoop DB Server-host
- Vereist een waarde


### `--dbname`

Naam verkoopdatabase
- Vereist een waarde


### `--username`

Gebruikersnaam verkoopdatabase
- Vereist een waarde


### `--password`

Gebruikerswachtwoord verkoopdatabase
- Accepteert een waarde


### `--connection`

Naam van verkoopverbinding
- Standaard: `sales`
- Accepteert een waarde


### `--resource`

Naam verkoopbron
- Standaard: `sales`
- Accepteert een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:db-schema:upgrade`

Installeert en verbetert het schema van DB

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--convert-old-scripts`

Hiermee kunt u oude scripts (InstallSchema, UpgradeSchema) converteren naar de indeling db_schema.xml
- Standaard: `false`
- Accepteert een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:db:status`

Controleert of het schema of de gegevens van DB verbetering vereisen

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:di:compile`

Genereert DI-configuratie en alle ontbrekende klassen die automatisch kunnen worden gegenereerd

```bash
bin/magento setup:di:compile
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:install`

Hiermee wordt de Magento-toepassing geïnstalleerd

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

Backend frontname (wordt automatisch gegenereerd als deze ontbreekt)
- Vereist een waarde


### `--enable-debug-logging`

Foutopsporingsregistratie inschakelen
- Vereist een waarde


### `--enable-syslog-logging`

Syslog-logboekregistratie inschakelen
- Vereist een waarde


### `--remote-storage-driver`

Extern opslagstuurprogramma
- Vereist een waarde


### `--remote-storage-prefix`

Voorvoegsel voor externe opslag
- Standaard: &quot;
- Vereist een waarde


### `--remote-storage-endpoint`

Extern opslageindpunt
- Vereist een waarde


### `--remote-storage-bucket`

Externe opslagemmer
- Vereist een waarde


### `--remote-storage-region`

Externe opslagregio
- Vereist een waarde


### `--remote-storage-key`

Toegangstoets externe opslag
- Standaard: &quot;
- Vereist een waarde


### `--remote-storage-secret`

Externe geheim van opslagsleutel
- Standaard: &quot;
- Vereist een waarde


### `--remote-storage-path-style`

Padstijl externe opslag
- Standaard: `0`
- Vereist een waarde


### `--checkout-async`

Afwisselende orderverwerking inschakelen? 1 - Ja, 0 - Nee
- Vereist een waarde


### `--amqp-host`

Amqp-serverhost
- Standaard: &quot;
- Vereist een waarde


### `--amqp-port`

Amqp-serverpoort
- Standaard: `5672`
- Vereist een waarde


### `--amqp-user`

Gebruikersnaam Amqp-server
- Standaard: &quot;
- Vereist een waarde


### `--amqp-password`

Wachtwoord Amqp-server
- Standaard: &quot;
- Vereist een waarde


### `--amqp-virtualhost`

AMQP virtualhost
- Standaard: `/`
- Vereist een waarde


### `--amqp-ssl`

Amqp SSL
- Standaard: &quot;
- Vereist een waarde


### `--amqp-ssl-options`

Amqp SSL-opties (JSON)
- Standaard: &quot;
- Vereist een waarde


### `--consumers-wait-for-messages`

Moeten consumenten wachten op een bericht uit de wachtrij? 1 - Ja, 0 - Nee
- Vereist een waarde


### `--queue-default-connection`

Standaardverbinding in wachtrij met berichten. Kan &#39;db&#39;, &#39;amqp&#39; of een aangepast wachtrijsysteem zijn. Het wachtrijsysteem moet worden geïnstalleerd en geconfigureerd, anders worden de berichten niet correct verwerkt.
- Vereist een waarde


### `--deferred-total-calculating`

Uitgestelde totale berekening inschakelen? 1 - Ja, 0 - Nee
- Vereist een waarde


### `--key`

Versleutelingssleutel
- Vereist een waarde


### `--db-host`

Host databaseserver
- Vereist een waarde


### `--db-name`

Databasenaam
- Vereist een waarde


### `--db-user`

Gebruikersnaam databaseserver
- Vereist een waarde


### `--db-engine`

Database-server-engine
- Vereist een waarde


### `--db-password`

Wachtwoord databaseserver
- Vereist een waarde


### `--db-prefix`

Voorvoegsel databasetabel
- Vereist een waarde


### `--db-model`

Type database
- Vereist een waarde


### `--db-init-statements`

Eerste set opdrachten database
- Vereist een waarde



### `--skip-db-validation`, `-s`



Indien opgegeven, wordt de validatie van de db-verbinding overgeslagen
- Standaard: `false`
- Accepteert geen waarde


### `--http-cache-hosts`

http-cachehosts
- Vereist een waarde


### `--db-ssl-key`

Volledig pad van clientsleutelbestand om een databaseverbinding tot stand te brengen via SSL
- Standaard: &quot;
- Vereist een waarde


### `--db-ssl-cert`

Volledig pad van clientcertificaatbestand om een databaseverbinding tot stand te brengen via SSL
- Standaard: &quot;
- Vereist een waarde


### `--db-ssl-ca`

Volledig pad van servercertificaatbestand om een databaseverbinding tot stand te brengen via SSL
- Standaard: &quot;
- Vereist een waarde


### `--db-ssl-verify`

Servercertificering controleren
- Standaard: `false`
- Accepteert geen waarde


### `--session-save`

Sessieopslaghandler
- Vereist een waarde


### `--session-save-redis-host`

Volledig - gekwalificeerde gastheernaam, IP adres, of absolute weg als het gebruiken van de contactdozen van UNIX
- Vereist een waarde


### `--session-save-redis-port`

Redis-poort voor luisteren naar server
- Vereist een waarde


### `--session-save-redis-password`

Wachtwoord voor opnieuw verzonden server
- Vereist een waarde


### `--session-save-redis-timeout`

Time-out verbinding, in seconden
- Vereist een waarde


### `--session-save-redis-persistent-id`

Unieke tekenreeks om permanente verbindingen in te schakelen
- Vereist een waarde


### `--session-save-redis-db`

Databasenummer van Redis
- Vereist een waarde


### `--session-save-redis-compression-threshold`

Compressiedrempel opnieuw instellen
- Vereist een waarde


### `--session-save-redis-compression-lib`

Compressiebibliotheek opnieuw uitschakelen. Waarden: gzip (standaardwaarde), lzf, lz4, snappy
- Vereist een waarde


### `--session-save-redis-log-level`

Opnieuw schijflogniveau. Waarden: 0 (minst uitgebreid) tot 7 (meest uitgebreide)
- Vereist een waarde


### `--session-save-redis-max-concurrency`

Maximum aantal processen dat op een slot op één zitting kan wachten
- Vereist een waarde


### `--session-save-redis-break-after-frontend`

Aantal seconden dat moet worden gewacht voordat wordt geprobeerd een vergrendeling voor een frontendsessie te verbreken
- Vereist een waarde


### `--session-save-redis-break-after-adminhtml`

Aantal seconden dat moet worden gewacht voordat wordt geprobeerd een vergrendeling voor beheersessie te verbreken
- Vereist een waarde


### `--session-save-redis-first-lifetime`

Levensduur, in seconden, van sessie voor niet-bots bij eerste schrijven (gebruik 0 om uit te schakelen)
- Vereist een waarde


### `--session-save-redis-bot-first-lifetime`

Levensduur, in seconden, van sessie voor bots bij de eerste schrijfbewerking (gebruik 0 om uit te schakelen)
- Vereist een waarde


### `--session-save-redis-bot-lifetime`

De levensduur van de sessie voor bots bij volgende schrijvingen (gebruik 0 om uit te schakelen)
- Vereist een waarde


### `--session-save-redis-disable-locking`

Schakel vergrendeling opnieuw uit. Waarden: false (standaardwaarde), true
- Vereist een waarde


### `--session-save-redis-min-lifetime`

Herdis min sessieduur, in seconden
- Vereist een waarde


### `--session-save-redis-max-lifetime`

Maximale sessielevensduur van Redis, in seconden
- Vereist een waarde


### `--session-save-redis-sentinel-master`

Redis Sentinel master
- Vereist een waarde


### `--session-save-redis-sentinel-servers`

Redis Sentinel-servers, gescheiden door komma&#39;s
- Vereist een waarde


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifieert master. Waarden: false (standaard), true
- Vereist een waarde


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel verbindt opnieuw pogingen.
- Vereist een waarde


### `--cache-backend`

Standaardcachehandler
- Vereist een waarde


### `--cache-backend-redis-server`

Redis-server
- Vereist een waarde


### `--cache-backend-redis-db`

Databasenummer voor de cache
- Vereist een waarde


### `--cache-backend-redis-port`

Redis-poort voor luisteren naar server
- Vereist een waarde


### `--cache-backend-redis-password`

Wachtwoord voor opnieuw verzonden server
- Vereist een waarde


### `--cache-backend-redis-compress-data`

Instellen op 0 om compressie uit te schakelen (standaard is 1, ingeschakeld)
- Vereist een waarde


### `--cache-backend-redis-compression-lib`

Te gebruiken compressielabel [snappy,lzf,l4z,zstd,gzip] (leeg laten om automatisch te bepalen)
- Vereist een waarde


### `--cache-id-prefix`

ID-voorvoegsel voor cachesleutels
- Vereist een waarde


### `--allow-parallel-generation`

Genereren van cache op een niet-blokkerende manier toestaan
- Standaard: `false`
- Accepteert geen waarde


### `--page-cache`

Standaardcachehandler
- Vereist een waarde


### `--page-cache-redis-server`

Redis-server
- Vereist een waarde


### `--page-cache-redis-db`

Databasenummer voor de cache
- Vereist een waarde


### `--page-cache-redis-port`

Redis-poort voor luisteren naar server
- Vereist een waarde


### `--page-cache-redis-password`

Wachtwoord voor opnieuw verzonden server
- Vereist een waarde


### `--page-cache-redis-compress-data`

Ingesteld op 1 om de cache van de volledige pagina te comprimeren (gebruik 0 om uit te schakelen)
- Vereist een waarde


### `--page-cache-redis-compression-lib`

Te gebruiken compressiebibliotheek [snappy,lzf,l4z,zstd,gzip] (leeg laten om automatisch te bepalen)
- Vereist een waarde


### `--page-cache-id-prefix`

ID-voorvoegsel voor cachesleutels
- Vereist een waarde


### `--lock-provider`

Naam provider vergrendelen
- Vereist een waarde


### `--lock-db-prefix`

Installatiespecifiek vergrendelingsvoorvoegsel om vergrendelingsconflicten te voorkomen
- Vereist een waarde


### `--lock-zookeeper-host`

Host en poort voor verbinding met Zookeeper-cluster. Bijvoorbeeld: 127.0.0.1:2181
- Vereist een waarde


### `--lock-zookeeper-path`

Het pad waar Zookeeper vergrendelingen opslaat. Het standaardpad is: /magento/locks
- Vereist een waarde


### `--lock-file-path`

Het pad waar de bestandsvergrendelingen worden opgeslagen.
- Vereist een waarde


### `--document-root-is-pub`

Markering om te tonen is dat Pub zich op de hoofdmap bevindt, kan alleen waar of onwaar zijn
- Vereist een waarde


### `--base-url`

URL waar de winkel beschikbaar moet zijn. Vervangen, gebruik config:reeks met weg web/unsecure/base_url
- Vereist een waarde


### `--language`

Standaardtaalcode. Vervangen, gebruik config:reeks met weg algemeen/landinstelling/code
- Vereist een waarde


### `--timezone`

Standaardtijdzonecode. Vervangen, gebruik config:reeks met weg algemeen/landinstelling/timezone
- Vereist een waarde


### `--currency`

Standaardvalutacode. Vervangen, configuratie gebruiken:instellen met padvaluta/opties/basis, valuta/opties/standaard en valuta/opties/allow
- Vereist een waarde


### `--use-rewrites`

Herschrijven gebruiken. Vervangen, gebruik config:reeks met weg web/seo/use_rewrites
- Vereist een waarde


### `--use-secure`

Gebruik veilige URL&#39;s. Schakel deze optie alleen in als SSL beschikbaar is. Vervangen, gebruik config:reeks met weg web/secure/use_in_frontend
- Vereist een waarde


### `--base-url-secure`

Basis-URL voor SSL-verbinding. Vervangen, gebruik config:reeks met weg web/secure/base_url
- Vereist een waarde


### `--use-secure-admin`

Voer de beheerdersinterface uit met SSL. Vervangen, gebruik config:reeks met weg web/secure/use_in_adminhtml
- Vereist een waarde


### `--admin-use-security-key`

Of een functie &#39;beveiligingssleutel&#39; moet worden gebruikt in URL&#39;s en formulieren voor Magento Admin. Vervangen, gebruik config:reeks met weg admin/security/use_form_key
- Vereist een waarde


### `--admin-user`

Admin-gebruiker
- Accepteert een waarde


### `--admin-password`

Wachtwoord beheerder
- Accepteert een waarde


### `--admin-email`

E-mail beheerder
- Accepteert een waarde


### `--admin-firstname`

Voornaam beheerder
- Accepteert een waarde


### `--admin-lastname`

Achternaam beheerder
- Accepteert een waarde


### `--search-engine`

Zoekprogramma. Waarden: elasticsearch5, elasticsearch6, elasticsearch7
- Vereist een waarde


### `--elasticsearch-host`

Elasticsearch-serverhost.
- Vereist een waarde


### `--elasticsearch-port`

Elasticsearch-serverpoort.
- Vereist een waarde


### `--elasticsearch-enable-auth`

Stel dit in op 1 om verificatie in te schakelen. (standaardwaarde is 0, uitgeschakeld)
- Vereist een waarde


### `--elasticsearch-username`

Elasticsearch-gebruikersnaam. Alleen van toepassing als HTTP-auth is ingeschakeld
- Vereist een waarde


### `--elasticsearch-password`

Elasticsearch-wachtwoord. Alleen van toepassing als HTTP-auth is ingeschakeld
- Vereist een waarde


### `--elasticsearch-index-prefix`

Elasticsearch-indexvoorvoegsel.
- Vereist een waarde


### `--elasticsearch-timeout`

Time-out Elasticsearch-server.
- Vereist een waarde


### `--cleanup-database`

De database opschonen voordat deze wordt geïnstalleerd
- Standaard: `false`
- Accepteert geen waarde


### `--sales-order-increment-prefix`

Prefix van het inkoopordernummer
- Vereist een waarde


### `--use-sample-data`

Voorbeeldgegevens gebruiken
- Standaard: `false`
- Accepteert geen waarde


### `--enable-modules`

Lijst met door komma&#39;s gescheiden modulenamen. Dat moet tijdens de installatie worden opgenomen. Beschikbaar magische param &quot;all&quot;.
- Accepteert een waarde


### `--disable-modules`

Lijst met door komma&#39;s gescheiden modulenamen. Dat moet tijdens de installatie worden voorkomen. Beschikbaar magische param &quot;all&quot;.
- Accepteert een waarde


### `--convert-old-scripts`

Hiermee kunt u oude scripts (InstallSchema, UpgradeSchema) converteren naar de indeling db_schema.xml
- Standaard: `false`
- Accepteert een waarde



### `--interactive`, `-i`



Interactieve Magento-installatie
- Standaard: `false`
- Accepteert geen waarde


### `--safe-mode`

Veilige installatie van Magento met dumps bij destructieve bewerkingen, zoals het verwijderen van kolommen
- Accepteert een waarde


### `--data-restore`

Verwijderde gegevens van dumps herstellen
- Accepteert een waarde


### `--dry-run`

De Magento-installatie wordt uitgevoerd in de modus voor droog uitvoeren
- Standaard: `false`
- Accepteert een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:performance:generate-fixtures`

Genereert correcties

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

<!-- app.name --> <!-- command.usage -->

### `profile`

Pad naar profielconfiguratiebestand
- Vereist

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-reindex`, `-s`



Herindexeren overslaan
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:rollback`

Draait codebase, media en database van Magento Application terug

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--code-file`, `-c`



Basisnaam van het back-upbestand van de code in var/back-ups
- Vereist een waarde



### `--media-file`, `-m`



Basisnaam van het back-upbestand van het medium in var/back-ups
- Vereist een waarde



### `--db-file`, `-d`



Basename van het db reservedossier in var/steunen
- Vereist een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:static-content:deploy`

Statische weergavebestanden gebruiken

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

<!-- app.name --> <!-- command.usage -->

### `languages`

Lijst met door spaties gescheiden ISO-639-taalcodes waarvoor statische weergavebestanden moeten worden uitgevoerd.

- Standaard: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



Bestanden in elke modus implementeren.
- Standaard: `false`
- Accepteert geen waarde



### `--strategy`, `-s`



Bestanden implementeren met behulp van de opgegeven strategie.
- Standaard: `quick`
- Accepteert een waarde



### `--area`, `-a`



Alleen bestanden genereren voor de opgegeven gebieden.
- Standaard: `all`
- Accepteert meerdere waarden


### `--exclude-area`

Genereer geen bestanden voor de opgegeven gebieden.
- Standaard: `none`
- Accepteert meerdere waarden



### `--theme`, `-t`



Genereer statische weergavebestanden voor alleen de opgegeven thema&#39;s.
- Standaard: `all`
- Accepteert meerdere waarden


### `--exclude-theme`

Genereer geen bestanden voor de opgegeven thema&#39;s.
- Standaard: `none`
- Accepteert meerdere waarden



### `--language`, `-l`



Genereer bestanden alleen voor de opgegeven talen.
- Standaard: `all`
- Accepteert meerdere waarden


### `--exclude-language`

Genereer geen bestanden voor de opgegeven talen.
- Standaard: `none`
- Accepteert meerdere waarden



### `--jobs`, `-j`



Schakel parallelle verwerking in met het opgegeven aantal taken.
- Standaard: `0`
- Accepteert een waarde


### `--max-execution-time`

De maximale verwachte uitvoeringstijd van implementatie statisch proces (in seconden).
- Standaard: `900`
- Accepteert een waarde


### `--symlink-locale`

Creeer symlinks voor de dossiers van die scènes, die voor plaatsing worden overgegaan, maar geen aanpassingen hebben.
- Standaard: `false`
- Accepteert geen waarde


### `--content-version`

Aangepaste versie van statische inhoud kan worden gebruikt als implementatie op meerdere knooppunten wordt uitgevoerd om ervoor te zorgen dat de versie van statische inhoud identiek is en dat caching correct werkt.
- Vereist een waarde


### `--refresh-content-version-only`

Als u de versie van statische inhoud alleen vernieuwt, kunt u statische inhoud in de browsercache en CDN-cache vernieuwen.
- Standaard: `false`
- Accepteert geen waarde


### `--no-javascript`

Implementeer geen JavaScript-bestanden.
- Standaard: `false`
- Accepteert geen waarde


### `--no-js-bundle`

Implementeer geen JavaScript-bundelbestanden.
- Standaard: `false`
- Accepteert geen waarde


### `--no-css`

CSS-bestanden niet implementeren.
- Standaard: `false`
- Accepteert geen waarde


### `--no-less`

Implementeer geen LESS-bestanden.
- Standaard: `false`
- Accepteert geen waarde


### `--no-images`

Implementeer geen afbeeldingen.
- Standaard: `false`
- Accepteert geen waarde


### `--no-fonts`

Implementeer geen lettertypebestanden.
- Standaard: `false`
- Accepteert geen waarde


### `--no-html`

Implementeer geen HTML-bestanden.
- Standaard: `false`
- Accepteert geen waarde


### `--no-misc`

Implementeer geen bestanden van andere typen (.md, .jbf, .csv, enz.).
- Standaard: `false`
- Accepteert geen waarde


### `--no-html-minify`

Maak geen minieme HTML-bestanden.
- Standaard: `false`
- Accepteert geen waarde


### `--no-parent`

Bovenliggende thema&#39;s niet compileren. Alleen ondersteund in snelle en standaardstrategieën.
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:store-config:set`

Installeert de opslagconfiguratie. Vervangen vanaf 2.2.0. Configureren gebruiken:instellen

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--base-url`

URL waar de winkel beschikbaar moet zijn. Vervangen, gebruik config:reeks met weg web/unsecure/base_url
- Vereist een waarde


### `--language`

Standaardtaalcode. Vervangen, gebruik config:reeks met weg algemeen/landinstelling/code
- Vereist een waarde


### `--timezone`

Standaardtijdzonecode. Vervangen, gebruik config:reeks met weg algemeen/landinstelling/timezone
- Vereist een waarde


### `--currency`

Standaardvalutacode. Vervangen, configuratie gebruiken:instellen met padvaluta/opties/basis, valuta/opties/standaard en valuta/opties/allow
- Vereist een waarde


### `--use-rewrites`

Herschrijven gebruiken. Vervangen, gebruik config:reeks met weg web/seo/use_rewrites
- Vereist een waarde


### `--use-secure`

Gebruik veilige URL&#39;s. Schakel deze optie alleen in als SSL beschikbaar is. Vervangen, gebruik config:reeks met weg web/secure/use_in_frontend
- Vereist een waarde


### `--base-url-secure`

Basis-URL voor SSL-verbinding. Vervangen, gebruik config:reeks met weg web/secure/base_url
- Vereist een waarde


### `--use-secure-admin`

Voer de beheerdersinterface uit met SSL. Vervangen, gebruik config:reeks met weg web/secure/use_in_adminhtml
- Vereist een waarde


### `--admin-use-security-key`

Of een functie &#39;beveiligingssleutel&#39; moet worden gebruikt in URL&#39;s en formulieren voor Magento Admin. Vervangen, gebruik config:reeks met weg admin/security/use_form_key
- Vereist een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:uninstall`

Hiermee wordt de Magento-toepassing verwijderd

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `setup:upgrade`

Hiermee worden de Magento-toepassing, DB-gegevens en het schema bijgewerkt

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep-generated`

Voorkomt dat gegenereerde bestanden worden verwijderd. We raden u af deze optie te gebruiken, behalve wanneer u een product gaat maken. Raadpleeg de systeemontwikkelaar of beheerder voor meer informatie.
- Standaard: `false`
- Accepteert geen waarde


### `--convert-old-scripts`

Hiermee kunt u oude scripts (InstallSchema, UpgradeSchema) converteren naar de indeling db_schema.xml
- Standaard: `false`
- Accepteert een waarde


### `--safe-mode`

Veilige installatie van Magento met dumps bij destructieve bewerkingen, zoals het verwijderen van kolommen
- Accepteert een waarde


### `--data-restore`

Verwijderde gegevens van dumps herstellen
- Accepteert een waarde


### `--dry-run`

De Magento-installatie wordt uitgevoerd in de modus voor droog uitvoeren
- Standaard: `false`
- Accepteert een waarde


### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `store:list`

Hiermee wordt de lijst met winkels weergegeven

```bash
bin/magento store:list
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `store:website:list`

De lijst met websites weergeven

```bash
bin/magento store:website:list
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `support:backup:code`

Codeback-up maken

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--name`

Dumpingnaam
- Accepteert een waarde



### `--output`, `-o`



Uitvoerpad
- Accepteert een waarde



### `--logs`, `-l`



Logbestanden opnemen
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `support:backup:db`

DB-back-up maken

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--name`

Dumpingnaam
- Accepteert een waarde



### `--output`, `-o`



Uitvoerpad
- Accepteert een waarde



### `--logs`, `-l`



Logbestanden opnemen
- Standaard: `false`
- Accepteert geen waarde



### `--ignore-sanitize`, `-i`



ontsmetten negeren
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `support:utility:check`

Vereiste back-uphulpprogramma&#39;s controleren

```bash
bin/magento support:utility:check [--hide-paths]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--hide-paths`

Alleen vereiste consolehulpprogramma&#39;s controleren
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `support:utility:paths`

Lijst met paden voor hulpprogramma&#39;s maken

```bash
bin/magento support:utility:paths [-f|--force]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Kracht
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `theme:uninstall`

Thema wordt verwijderd

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

<!-- app.name --> <!-- command.usage -->

### `theme`

Pad van het thema. Het themapad moet worden opgegeven als een volledig pad dat gebied/leverancier/naam is. Voorkant/Magento/leeg

- Standaard: `[]`
- Vereist

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--backup-code`

Back-up van code maken (met uitzondering van tijdelijke bestanden)
- Standaard: `false`
- Accepteert geen waarde



### `--clear-static-content`, `-c`



Gegenereerde statische weergavebestanden wissen.
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size -->

## `varnish:vcl:generate`

Genereert Varnish VCL en echo het aan de bevellijn

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access-list`

IPs toegangslijst die Varnish kan zuiveren
- Standaard: `localhost`
- Vereist een waarde


### `--backend-host`

Host van de webinhoud
- Standaard: `localhost`
- Vereist een waarde


### `--backend-port`

Poort van de webinhoud
- Standaard: `8080`
- Vereist een waarde


### `--export-version`

De versie van het Varnish-bestand
- Standaard: `4`
- Vereist een waarde


### `--grace-period`

Respijtperiode in seconden
- Standaard: `300`
- Vereist een waarde


### `--output-file`

Pad naar het bestand om vcl te schrijven
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



Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuiveren
- Standaard: `false`
- Accepteert geen waarde



### `--version`, `-V`



Deze toepassingsversie weergeven
- Standaard: `false`
- Accepteert geen waarde


### `--ansi`

ANSI-uitvoer forceren
- Standaard: `false`
- Accepteert geen waarde


### `--no-ansi`

ANSI-uitvoer uitschakelen
- Standaard: `false`
- Accepteert geen waarde



### `--no-interaction`, `-n`



Geen interactieve vraag stellen
- Standaard: `false`
- Accepteert geen waarde <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->