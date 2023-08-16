---
source-git-commit: 64c453adabb092075854b2c20bf7da73c4a5146e
workflow-type: tm+mt
source-wordcount: '17239'
ht-degree: 0%

---
# bin/magento (Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versie**: 2.4.6

Deze verwijzing bevat 114 bevelen beschikbaar door `bin/magento` opdrachtregelprogramma.
De eerste lijst wordt automatisch gegenereerd met de opdracht `bin/magento list` gebruiken bij Magento Open Source.
Gebruik de [&quot;CLI-opdrachten toevoegen&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) gids om een douane CLI bevel toe te voegen.

>[!NOTE]
>
>U kunt bellen `bin/magento` CLI bevelen die kortere weg in plaats van de volledige bevelnaam gebruiken. U kunt bijvoorbeeld `bin/magento setup:upgrade` gebruiken `bin/magento s:up`, `bin/magento s:upg`. Zie [sneltoetssyntaxis](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) om te begrijpen hoe te om kortere weg met om het even welk bevel CLI te gebruiken.

>[!NOTE]
>
>Deze verwijzing wordt gegenereerd op basis van de toepassingscodebase. Als u de inhoud wilt wijzigen, kunt u de broncode voor de corresponderende opdrachtimplementatie bijwerken in het dialoogvenster [codebase](https://github.com/magento) opslaan en uw wijzigingen ter controle verzenden. Een andere manier is om _Feedback geven_ (zoek de koppeling in de rechterbovenhoek). Zie voor richtsnoeren voor bijdragen [Codebijdragen](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Interne opdracht voor suggesties voor shell-voltooiing

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
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
bin/magento completion [--debug] [--] [<shell>]
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
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
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
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
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


## `admin:adobe-ims:disable`

Adobe IMS-module uitschakelen

```bash
bin/magento admin:adobe-ims:disable
```

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


## `admin:adobe-ims:enable`

Schakel Adobe IMS Module in.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

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


## `admin:adobe-ims:info`

Informatie over de configuratie van de Adobe IMS-module

```bash
bin/magento admin:adobe-ims:info
```

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


## `admin:adobe-ims:status`

Status van de Adobe IMS-module

```bash
bin/magento admin:adobe-ims:status
```

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


## `admin:user:create`

Hiermee wordt een beheerder gemaakt

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

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


## `admin:user:unlock`

Beheerdersaccount ontgrendelen

```bash
bin/magento admin:user:unlock <username>
```


### `username`

De te ontgrendelen admin-gebruikersnaam

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


## `app:config:dump`

Stortplaats van toepassing maken

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

Lijst met door spaties gescheiden configuratietypen of het weglaten om alles te dumpen [bereik, systeem, thema&#39;s, i18n]

- Standaard: `[]`

- Array

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


## `app:config:import`

Gegevens uit gedeelde configuratiebestanden importeren naar de juiste gegevensopslag

```bash
bin/magento app:config:import
```

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


## `app:config:status`

Controleert of config-propagatie update vereist

```bash
bin/magento app:config:status
```

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


## `braintree:migrate`

Opgeslagen kaarten migreren vanuit een Magento 1-database

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

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


## `cache:clean`

Cachetype(s) wissen

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`

- Array

### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

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


## `cache:disable`

Cachetype(s) uitschakelen

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`

- Array

### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

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


## `cache:enable`

Cachetype(s) inschakelen

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`

- Array

### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

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


## `cache:flush`

Cacheopslag wordt gebruikt door cachetype(s)

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`

- Array

### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

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


## `cache:status`

Hiermee wordt de cachestatus gecontroleerd

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

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


## `catalog:images:resize`

Hiermee maakt u productafbeeldingen waarvan het formaat is gewijzigd

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

Afbeeldingen vergroten/verkleinen in asynchrone modus

- Standaard: `false`
- Accepteert geen waarde

### `--skip_hidden_images`

Afbeeldingen die als verborgen op de productpagina zijn gemarkeerd, niet verwerken

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


## `catalog:product:attributes:cleanup`

Verwijdert ongebruikte productkenmerken.

```bash
bin/magento catalog:product:attributes:cleanup
```

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


## `cms:wysiwyg:restrict`

Instellen of validatie van HTML-inhoud van gebruiker moet worden afgedwongen of dat een waarschuwing moet worden weergegeven

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

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


## `config:sensitive:set`

Gevoelige configuratiewaarden instellen

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

Configuratiepad, bijvoorbeeld groep/sectie/field_name


### `value`

Configuratiewaarde


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


## `config:set`

Systeemconfiguratie wijzigen

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

Configuratiepad in indelingssectie/groep/veld_naam

- Vereist

### `value`

Configuratiewaarde

- Vereist

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


## `config:show`

Toont configuratiewaarde voor bepaalde weg. Als het pad niet is opgegeven, worden alle opgeslagen waarden weergegeven

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

Configuratiepad, bijvoorbeeld section_id/group_id/field_id


### `--scope`

Bereik voor configuratie, als niet gespecificeerd, dan &quot;gebrek&quot;werkingsgebied zal worden gebruikt

- Standaard: `default`
- Accepteert een waarde

### `--scope-code`

Code bereik (alleen vereist als het bereik niet is ingesteld) `default`)

- Standaard: &quot;
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


## `cron:install`

Genereert en installeert een tab voor de huidige gebruiker

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

Installatietaken forceren

- Standaard: `false`
- Accepteert geen waarde

### `--non-optional`, `-d`

Alleen de niet-optionele (standaard)taken installeren

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


## `cron:remove`

Hiermee worden taken uit het tabblad Crontab verwijderd

```bash
bin/magento cron:remove
```

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


## `cron:run`

Hiermee worden taken volgens schema uitgevoerd

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

### `--group`

Alleen taken uitvoeren vanuit opgegeven groep

- Vereist een waarde

### `--bootstrap`

Parameters van de bootstrap toevoegen of overschrijven

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


## `customer:hash:upgrade`

De hash van de klant bijwerken volgens het meest recente algoritme

```bash
bin/magento customer:hash:upgrade
```

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


## `deploy:mode:set`

Toepassingsmodus instellen.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

De toepassingsmodus die moet worden ingesteld. Beschikbare opties zijn &quot;developer&quot; of &quot;production&quot;

- Vereist

### `--skip-compilation`, `-s`

Verwijdert het wissen en opnieuw genereren van statische inhoud (gegenereerde code, vooraf verwerkte CSS en elementen in pub/static/)

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


## `deploy:mode:show`

Geeft de huidige toepassingsmodus weer.

```bash
bin/magento deploy:mode:show
```

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


## `dev:di:info`

Verstrekt informatie over de configuratie van de Injectie van de Afhankelijkheid voor het Bevel.

```bash
bin/magento dev:di:info <class>
```


### `class`

Klassenaam

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


## `dev:email:newsletter-compatibility-check`

Scant nieuwsbrieven sjablonen voor mogelijke compatibiliteitsproblemen met variabeleverbruik

```bash
bin/magento dev:email:newsletter-compatibility-check
```

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


## `dev:email:override-compatibility-check`

Scant e-mailsjabloonoverschrijvingen voor mogelijke compatibiliteitsproblemen met variabelengebruik

```bash
bin/magento dev:email:override-compatibility-check
```

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


## `dev:profiler:disable`

Maak profiler onbruikbaar.

```bash
bin/magento dev:profiler:disable
```

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


## `dev:profiler:enable`

De analyse inschakelen.

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

Type analyse


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


## `dev:query-log:disable`

Logboekregistratie van DB-query uitschakelen

```bash
bin/magento dev:query-log:disable
```

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


## `dev:query-log:enable`

Logbestand van DB-query inschakelen

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

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


## `dev:source-theme:deploy`

Hiermee worden bronbestanden voor thema verzameld en gepubliceerd.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

Bestanden die vooraf moeten worden verwerkt (bestand moet worden opgegeven zonder extensie)

- Standaard: `css/styles-mcss/styles-l`

- Array

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


## `dev:template-hints:disable`

Tips voor frontend-sjablonen uitschakelen. Wellicht is het leegmaken van de cache vereist.

```bash
bin/magento dev:template-hints:disable
```

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


## `dev:template-hints:enable`

Tips voor frontendsjablonen inschakelen. Wellicht is het leegmaken van de cache vereist.

```bash
bin/magento dev:template-hints:enable
```

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


## `dev:template-hints:status`

Toon de status van frontend malplaatjewenken.

```bash
bin/magento dev:template-hints:status
```

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


## `dev:tests:run`

Tests bij uitvoering

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

Type test dat moet worden uitgevoerd. Beschikbare types: allen, eenheid, integratie, integratie-allen, statisch, statisch-allen, integriteit, erfenis, gebrek

- Standaard: `default`


### `--arguments`, `-c`

Aanvullende argumenten voor PHPUnit. Voorbeeld: &quot;-c&#39;—filter=MyTest&#39;&#39; (geen spaties)

- Standaard: &quot;
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


## `dev:urn-catalog:generate`

Genereert de catalogus van URNs aan *.xsd- afbeeldingen voor winde om xml te benadrukken.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

Pad naar bestand voor uitvoer van catalogus. Voor PHPStorm-gebruik .idea/misc.xml

- Vereist

### `--ide`

Indeling waarin de catalogus wordt gegenereerd. Ondersteund: [phpstorm, vscode]

- Standaard: `phpstorm`
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


## `dev:xml:convert`

Hiermee wordt een XML-bestand geconverteerd met XSL-stijlpagina&#39;s

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

Pad naar XML-bestand dat moet worden getransformeerd

- Vereist

### `processor`

Pad naar XSL-stijlpagina die wordt toegepast op XML-bestand

- Vereist

### `--overwrite`, `-o`

XML-bestand overschrijven

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


## `downloadable:domains:add`

Domeinen toevoegen aan de whitelist van downloadbare domeinen

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

Naam van domein

- Standaard: `[]`

- Array

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


## `downloadable:domains:remove`

Verwijder domeinen uit de downloadbare whitelist van domeinen

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

Domeinnamen

- Standaard: `[]`

- Array

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


## `downloadable:domains:show`

Downloadbare whitelist van domeinen weergeven

```bash
bin/magento downloadable:domains:show
```

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


## `encryption:payment-data:update`

Codeert gecodeerde creditcardgegevens opnieuw met de nieuwste coderingssleutel.

```bash
bin/magento encryption:payment-data:update
```

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


## `i18n:collect-phrases`

Neemt zinnen op in de codebase

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

Mappad om te parseren. Niet nodig indien —magento-markering is ingesteld


### `--output`, `-o`

Pad (inclusief bestandsnaam) naar een uitvoerbestand. Als er geen bestand is opgegeven, wordt standaard stdout toegepast.

- Vereist een waarde

### `--magento`, `-m`

Gebruik de parameter —magento om de huidige codebase van het Magento te parseren. Laat de parameter weg als een folder wordt gespecificeerd.

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


## `i18n:pack`

Slaat taalpakket op

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

Pad naar bronwoordenboekbestand met vertalingen

- Vereist

### `locale`

Doellandinstelling voor woordenboek, bijvoorbeeld &quot;de_DE&quot;

- Vereist

### `--mode`, `-m`

Modus Opslaan voor woordenboek - &quot;replace&quot; - taalpakket vervangen door nieuw - &quot;merge&quot; - taalpakketten samenvoegen door standaard &quot;replace&quot;

- Standaard: `replace`
- Vereist een waarde

### `--allow-duplicates`, `-d`

Gebruik de parameter —allow-duplicates om het opslaan van duplicaten van translate toe te staan. Laat anders de parameter weg.

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


## `i18n:uninstall`

Verwijdert taalpakketten

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

Taalpakketnaam

- Standaard: `[]`

- Vereist
- Array

### `--backup-code`, `-b`

Back-up maken van code- en configuratiebestanden (behalve tijdelijke bestanden)

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


## `indexer:info`

Toegestane indexen weergeven

```bash
bin/magento indexer:info
```

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


## `indexer:reindex`

Gegevens opnieuw indexeren

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array

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


## `indexer:reset`

Hiermee wordt de status van de indexeerder opnieuw ingesteld op ongeldig

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array

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


## `indexer:set-dimensions-mode`

Modus IndexerDimensionen instellen

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

Indexnaam [catalog_product_price]


### `mode`

Dimensiemodi van indexeermodule catalog_product_price none,website,customer_group,website_and_customer_group


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


## `indexer:set-mode`

Hiermee wordt het type indexmodus ingesteld

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

Type indexmodus [realtime|plannen]


### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array

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


## `indexer:show-dimensions-mode`

Modus Dimension indexeren tonen

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

Lijst met door spaties gescheiden indextypen of laat deze weg om toe te passen op alle indexen (catalog_product_price)

- Standaard: `[]`

- Array

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


## `indexer:show-mode`

Indexmodus weergeven

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array

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


## `indexer:status`

Hiermee wordt de status van Indexer weergegeven

```bash
bin/magento indexer:status [<index>...]
```


### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`

- Array

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


## `info:adminuri`

Hiermee wordt de Magento Admin URI weergegeven

```bash
bin/magento info:adminuri
```

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


## `info:backups:list`

Lijst met beschikbare back-upbestanden afdrukken

```bash
bin/magento info:backups:list
```

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


## `info:currency:list`

Geeft de lijst met beschikbare valuta&#39;s weer

```bash
bin/magento info:currency:list
```

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


## `info:dependencies:show-framework`

Geeft aantal afhankelijkheden weer van raamwerk voor Magento&#39;s

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

Bestandsnaam rapport

- Standaard: `framework-dependencies.csv`
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


## `info:dependencies:show-modules`

Toont aantal gebiedsdelen tussen modules

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

Bestandsnaam rapport

- Standaard: `modules-dependencies.csv`
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


## `info:dependencies:show-modules-circular`

Toont aantal kringafhankelijkheden tussen modules

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

Bestandsnaam rapport

- Standaard: `modules-circular-dependencies.csv`
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


## `info:language:list`

Geeft de lijst met beschikbare taallandinstellingen weer

```bash
bin/magento info:language:list
```

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


## `info:timezone:list`

Hiermee geeft u de lijst met beschikbare tijdzones weer

```bash
bin/magento info:timezone:list
```

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


## `inventory:reservation:create-compensations`

Maak punten van voorbehoud door middel van opgegeven compensatieargumenten

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

Lijst met compensatieargumenten in de notatie &quot;\&lt;order_increment_id>:\&lt;sku>:\&lt;quantity>:\&lt;stock-id>&quot;

- Standaard: `[]`

- Array

### `--raw`, `-r`

Onbewerkte uitvoer

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


## `inventory:reservation:list-inconsistencies`

Alle bestellingen en producten met inconsistenties in verkoopbare hoeveelheid tonen

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

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


## `inventory-geonames:import`

Geo-namen downloaden en importeren voor het algoritme van de bronselectie

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

Lijst van landcodes die moeten worden ingevoerd

- Standaard: `[]`

- Vereist
- Array

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


## `maintenance:allow-ips`

Plaatst onderhoudswijze vrijgestelde IPs

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

Toegestane IP adressen

- Standaard: `[]`

- Array

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


## `maintenance:disable`

Onderhoudsmodus uitschakelen

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Toegestane IP adressen (gebruik &quot;niets&quot;om toegestane IP lijst te ontruimen)

- Standaard: `[]`
- Vereist een waarde

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `maintenance:enable`

Onderhoudsmodus inschakelen

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Toegestane IP adressen (gebruik &quot;niets&quot;om toegestane IP lijst te ontruimen)

- Standaard: `[]`
- Vereist een waarde

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `maintenance:status`

De status van de onderhoudsmodus weergeven

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `media-content:sync`

Inhoud synchroniseren met elementen

```bash
bin/magento media-content:sync
```

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


## `media-gallery:sync`

Mediaopslag en media-elementen in de database synchroniseren

```bash
bin/magento media-gallery:sync
```

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


## `module:config:status`

Controleert de moduleconfiguratie in het &quot;app/etc/config.php&quot;dossier en rapporteert als zij of niet bijgewerkt zijn

```bash
bin/magento module:config:status
```

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


## `module:disable`

Hiermee worden opgegeven modules uitgeschakeld

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Naam van de module

- Standaard: `[]`

- Array

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


## `module:enable`

Hiermee worden opgegeven modules ingeschakeld

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Naam van de module

- Standaard: `[]`

- Array

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


## `module:status`

Geeft de status van modules weer

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

Optionele modulenaam

- Standaard: `[]`

- Array

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


## `module:uninstall`

Hiermee verwijdert u modules die door de composer zijn geïnstalleerd

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


### `module`

Naam van de module

- Standaard: `[]`

- Vereist
- Array

### `--remove-data`, `-r`

Gegevens verwijderen die zijn geïnstalleerd door module(s)

- Standaard: `false`
- Accepteert geen waarde

### `--backup-code`

Back-up maken van code- en configuratiebestanden (behalve tijdelijke bestanden)

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


## `newrelic:create:deploy-marker`

Controleer de opstellen rij voor ingangen en creeer aangewezen plaatsingsteller.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

Bericht implementeren?

- Vereist

### `change_log`

Logboek wijzigen?

- Vereist

### `user`

Implementatiegebruiker


### `revision`

Herziening


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


## `queue:consumers:list`

Lijst met consumenten van MessageQueue

```bash
bin/magento queue:consumers:list
```

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


## `queue:consumers:restart`

Gebruikers van MessageQueue opnieuw starten

```bash
bin/magento queue:consumers:restart
```

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


## `queue:consumers:start`

MessageQueue-consument starten

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

De naam van de consument die moet worden gestart.

- Vereist

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


## `remote-storage:sync`

Mediabestanden synchroniseren met externe opslag.

```bash
bin/magento remote-storage:sync
```

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


## `sampledata:deploy`

Stel steekproefgegevensmodules voor op composer-gebaseerde Magento&#39;s installaties op

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

Composer.json bijwerken zonder componentupdate uit te voeren

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


## `sampledata:remove`

Alle pakketten met voorbeeldgegevens verwijderen uit composer.json

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

Composer.json bijwerken zonder componentupdate uit te voeren

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


## `sampledata:reset`

Alle modules met voorbeeldgegevens opnieuw instellen voor herinstallatie

```bash
bin/magento sampledata:reset
```

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


## `security:recaptcha:disable-for-user-forgot-password`

reCAPTCHA uitschakelen voor wachtwoordformulier voor vergeten gebruiker van beheerder

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

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


## `security:recaptcha:disable-for-user-login`

reCAPTCHA uitschakelen voor aanmeldingsformulier voor beheerder

```bash
bin/magento security:recaptcha:disable-for-user-login
```

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


## `security:tfa:google:set-secret`

Stel het geheim in dat voor Google OTP-generatie wordt gebruikt.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

Gebruikersnaam

- Vereist

### `secret`

Geheim

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


## `security:tfa:providers`

Alle beschikbare providers weergeven

```bash
bin/magento security:tfa:providers
```

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


## `security:tfa:reset`

Configuratie voor één gebruiker opnieuw instellen

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

Gebruikersnaam

- Vereist

### `provider`

Providercode

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


## `setup:backup`

Maakt een back-up van de codebasis, media en database van Magento Application

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

Back-up maken van code- en configuratiebestanden (behalve tijdelijke bestanden)

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


## `setup:config:set`

Creeert of wijzigt de plaatsingsconfiguratie

```bash
bin/magento setup:config:set [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--id_salt ID_SALT] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--enable-debug-logging`

Foutopsporingsregistratie inschakelen

- Vereist een waarde

### `--enable-syslog-logging`

syslog inschakelen

- Vereist een waarde

### `--backend-frontname`

Backend frontname (wordt automatisch gegenereerd als deze ontbreekt)

- Vereist een waarde

### `--id_salt`

GraphQl Salt

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

Sleutel voor geheim opslagruimte

- Standaard: &quot;
- Vereist een waarde

### `--remote-storage-path-style`

Padstijl voor externe opslag

- Standaard: `0`
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

Databasetype

- Vereist een waarde

### `--db-init-statements`

Eerste set opdrachten database

- Vereist een waarde

### `--skip-db-validation`, `-s`

Indien opgegeven, wordt de db-verbindingsvalidatie overgeslagen

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

Standaardsessielevensduur van Redis, in seconden

- Vereist een waarde

### `--session-save-redis-max-lifetime`

Maximale sessielevensduur van Redis, in seconden

- Vereist een waarde

### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Vereist een waarde

### `--session-save-redis-sentinel-servers`

Redis Sentinel-servers, gescheiden door komma&#39;s

- Vereist een waarde

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verify master. Waarden: false (standaardwaarde), true

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


## `setup:db-data:upgrade`

Hiermee installeert en verbetert u gegevens in de database

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `setup:db-declaration:generate-patch`

Patch genereren en in specifieke map plaatsen.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


### `module`

Modulenaam

- Vereist

### `patch`

Patchnaam

- Vereist

### `--revertable`

Controleer of de patch teruggedraaid kan worden.

- Standaard: `false`
- Accepteert een waarde

### `--type`

Ontdek welk type patch moet worden gegenereerd. Beschikbare waarden: `data`, `schema`.

- Standaard: `data`
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


## `setup:db-declaration:generate-whitelist`

Een whitelist genereren van tabellen en kolommen die door het installatieprogramma van de declaratie mogen worden bewerkt

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

Naam van de module waar whitelist wordt gegenereerd

- Standaard: `all`
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


## `setup:db-schema:upgrade`

Installeert en verbetert het schema van DB

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

Hiermee kunt u oude scripts (InstallSchema, UpgradeSchema) converteren naar de indeling db_schema.xml

- Standaard: `false`
- Accepteert een waarde

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `setup:db:status`

Controleert of het schema of de gegevens van DB verbetering vereisen

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `setup:di:compile`

Genereert DI-configuratie en alle ontbrekende klassen die automatisch kunnen worden gegenereerd

```bash
bin/magento setup:di:compile
```

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


## `setup:install`

Hiermee wordt de toepassing Magento geïnstalleerd

```bash
bin/magento setup:install [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--backend-frontname BACKEND-FRONTNAME] [--id_salt ID_SALT] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--enable-debug-logging`

Foutopsporingsregistratie inschakelen

- Vereist een waarde

### `--enable-syslog-logging`

syslog inschakelen

- Vereist een waarde

### `--backend-frontname`

Backend frontname (wordt automatisch gegenereerd als deze ontbreekt)

- Vereist een waarde

### `--id_salt`

GraphQl Salt

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

Sleutel voor geheim opslagruimte

- Standaard: &quot;
- Vereist een waarde

### `--remote-storage-path-style`

Padstijl voor externe opslag

- Standaard: `0`
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

Databasetype

- Vereist een waarde

### `--db-init-statements`

Eerste set opdrachten database

- Vereist een waarde

### `--skip-db-validation`, `-s`

Indien opgegeven, wordt de db-verbindingsvalidatie overgeslagen

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

Standaardsessielevensduur van Redis, in seconden

- Vereist een waarde

### `--session-save-redis-max-lifetime`

Maximale sessielevensduur van Redis, in seconden

- Vereist een waarde

### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Vereist een waarde

### `--session-save-redis-sentinel-servers`

Redis Sentinel-servers, gescheiden door komma&#39;s

- Vereist een waarde

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verify master. Waarden: false (standaardwaarde), true

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

Basis-URL voor SSL-verbinding Vervangen, gebruik config:reeks met weg web/secure/base_url

- Vereist een waarde

### `--use-secure-admin`

Voer de beheerdersinterface uit met SSL. Vervangen, gebruik config:reeks met weg web/secure/use_in_adminhtml

- Vereist een waarde

### `--admin-use-security-key`

Of een functie &#39;beveiligingssleutel&#39; moet worden gebruikt in URL&#39;s en formulieren voor beheer van Magento&#39;s. Vervangen, gebruik config:reeks met weg admin/security/use_form_key

- Vereist een waarde

### `--admin-user`

Admin user

- Accepteert een waarde

### `--admin-password`

Wachtwoord beheerder

- Accepteert een waarde

### `--admin-email`

E-mailadres beheerder

- Accepteert een waarde

### `--admin-firstname`

Voornaam beheerder

- Accepteert een waarde

### `--admin-lastname`

Achternaam beheerder

- Accepteert een waarde

### `--search-engine`

Zoekprogramma. Waarden: elasticsearch5, elasticsearch7, elasticsearch8, openssearch

- Vereist een waarde

### `--elasticsearch-host`

Server-host van Elasticsearch.

- Vereist een waarde

### `--elasticsearch-port`

De serverhaven van de Elasticsearch.

- Vereist een waarde

### `--elasticsearch-enable-auth`

Stel dit in op 1 om verificatie in te schakelen. (standaardwaarde is 0, uitgeschakeld)

- Vereist een waarde

### `--elasticsearch-username`

Gebruikersnaam Elasticsearch. Alleen van toepassing als HTTP-auth is ingeschakeld

- Vereist een waarde

### `--elasticsearch-password`

Wachtwoord Elasticsearch. Alleen van toepassing als HTTP-auth is ingeschakeld

- Vereist een waarde

### `--elasticsearch-index-prefix`

Prefix van Elasticsearch-index.

- Vereist een waarde

### `--elasticsearch-timeout`

Time-out server Elasticsearch.

- Vereist een waarde

### `--opensearch-host`

OpenSearch-serverhost.

- Vereist een waarde

### `--opensearch-port`

OpenSearch-serverpoort.

- Vereist een waarde

### `--opensearch-enable-auth`

Stel dit in op 1 om verificatie in te schakelen. (standaardwaarde is 0, uitgeschakeld)

- Vereist een waarde

### `--opensearch-username`

OpenSearch gebruikersnaam. Alleen van toepassing als HTTP-auth is ingeschakeld

- Vereist een waarde

### `--opensearch-password`

Wachtwoord voor OpenSearch. Alleen van toepassing als HTTP-auth is ingeschakeld

- Vereist een waarde

### `--opensearch-index-prefix`

Prefix van de OpenSearch-index.

- Vereist een waarde

### `--opensearch-timeout`

Time-out van OpenSearch-server.

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

Installatie van interactief Magento

- Standaard: `false`
- Accepteert geen waarde

### `--safe-mode`

Veilige installatie van Magento met dumps bij destructieve bewerkingen, zoals het verwijderen van kolommen

- Accepteert een waarde

### `--data-restore`

Verwijderde gegevens van dumps herstellen

- Accepteert een waarde

### `--dry-run`

De installatie van het Magento wordt uitgevoerd in de droge-uitvoeringsmodus

- Standaard: `false`
- Accepteert een waarde

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `setup:performance:generate-fixtures`

Genereert correcties

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

Pad naar profielconfiguratiebestand

- Vereist

### `--skip-reindex`, `-s`

Herindexeren overslaan

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


## `setup:rollback`

Draait codebase, media en database van Magento Application terug

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

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


## `setup:static-content:deploy`

Statische weergavebestanden gebruiken

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

Lijst met door spaties gescheiden ISO-639-taalcodes waarvoor statische weergavebestanden moeten worden uitgevoerd.

- Standaard: `[]`

- Array

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

Geen bestanden voor de opgegeven thema&#39;s genereren.

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


## `setup:store-config:set`

Installeert de opslagconfiguratie. Vervangen vanaf 2.2.0. Configureren gebruiken:instellen

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

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

Basis-URL voor SSL-verbinding Vervangen, gebruik config:reeks met weg web/secure/base_url

- Vereist een waarde

### `--use-secure-admin`

Voer de beheerdersinterface uit met SSL. Vervangen, gebruik config:reeks met weg web/secure/use_in_adminhtml

- Vereist een waarde

### `--admin-use-security-key`

Of een functie &#39;beveiligingssleutel&#39; moet worden gebruikt in URL&#39;s en formulieren voor beheer van Magento&#39;s. Vervangen, gebruik config:reeks met weg admin/security/use_form_key

- Vereist een waarde

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `setup:uninstall`

Hiermee wordt de toepassing Magento verwijderd

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `setup:upgrade`

Hiermee werkt u de toepassing van het Magento, de DB-gegevens en het schema bij

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

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

De installatie van het Magento wordt uitgevoerd in de droge-uitvoeringsmodus

- Standaard: `false`
- Accepteert een waarde

### `--magento-init-params`

Voeg aan om het even welke bevel toe om Magento initialisatieparameters aan te passen Bijvoorbeeld: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[basis][path]=/var/www/example.com&amp;MAGE_DIRS[cachegeheugen][path]=/var/tmp/cache&quot;

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


## `store:list`

Hiermee wordt de lijst met winkels weergegeven

```bash
bin/magento store:list
```

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


## `store:website:list`

De lijst met websites weergeven

```bash
bin/magento store:website:list
```

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


## `theme:uninstall`

Thema wordt verwijderd

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

Pad van het thema. Het themapad moet worden opgegeven als een volledig pad dat gebied/leverancier/naam is. Voorkant/Magento/blanco

- Standaard: `[]`

- Vereist
- Array

### `--backup-code`

Back-up van code maken (behalve tijdelijke bestanden)

- Standaard: `false`
- Accepteert geen waarde

### `--clear-static-content`, `-c`

Gegenereerde statische weergavebestanden wissen.

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


## `varnish:vcl:generate`

Genereert Varnish VCL en echo het aan de bevellijn

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

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
