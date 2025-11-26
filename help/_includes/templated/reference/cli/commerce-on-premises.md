---
source-git-commit: 48dfdd81992a82bf984c3e7b0f30f8e5a69ee735
workflow-type: tm+mt
source-wordcount: '8232'
ht-degree: 0%

---
# bin/magento (Adobe Commerce op het terrein)

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->

**Versie**: 2.4.8

Deze verwijzing bevat 145 opdrachten die beschikbaar zijn via het opdrachtregelprogramma van `bin/magento` .
De eerste lijst wordt automatisch gegenereerd met de opdracht `bin/magento list` in Adobe Commerce.

## Algemeen

Gebruik [&#x200B; &quot;voeg CLI bevelen&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) gids toe om een douanebevel CLI toe te voegen.

U kunt `bin/magento` CLI bevelen roepen gebruikend kortere weg in plaats van de volledige bevelnaam. U kunt bijvoorbeeld `bin/magento setup:upgrade` aanroepen met `bin/magento s:up` , `bin/magento s:upg` . Zie [&#x200B; kortere wegsyntaxis &#x200B;](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) om te begrijpen hoe te om kortere weg met om het even welk bevel te gebruiken CLI.

Deze referentiedocumentatie wordt geproduceerd van de code van de toepassingsbron. Als u de documentatie wilt wijzigen, opent u
een trekkingsverzoek voor het overeenkomstige bevel in de relevante [&#x200B; codebase &#x200B;](https://github.com/magento) bewaarplaats. Zie
[&#x200B; de Bijdragen van de Code &#x200B;](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) voor meer informatie.

### Algemene opties

#### `--help`, `-h`

Help weergeven voor de opgegeven opdracht. Wanneer geen bevel vertoningshulp voor het lijstbevel wordt gegeven

- Standaard: `false`
- Accepteert geen waarde

#### `--quiet`, `-q`

Geen bericht uitvoeren

- Standaard: `false`
- Accepteert geen waarde

#### `--verbose`, `-v|-vv|-vvv`

Verhoog de breedheid van berichten: 1 voor normale output, 2 voor meer uitgebreide output en 3 voor zuivert

- Standaard: `false`
- Accepteert geen waarde

#### `--version`, `-V`

Deze toepassingsversie weergeven

- Standaard: `false`
- Accepteert geen waarde

#### `--ansi`

ANSI-uitvoer forceren (of uitschakelen —no-ansi)

- Accepteert geen waarde

#### `--no-ansi`

De optie &quot;—ansi&quot; negeren

- Standaard: `false`
- Accepteert geen waarde

#### `--no-interaction`, `-n`

Geen interactieve vraag stellen

- Standaard: `false`
- Accepteert geen waarde


## `_complete`

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Interne opdracht voor suggesties voor shell-voltooiing

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--shell`, `-s`

Het schelpdiertype (&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- Vereist een waarde

#### `--input`, `-i`

Een array van invoertokens (bv. COMP_WORDS of argv)

- Standaard: `[]`
- Vereist een waarde

#### `--current`, `-c`

De index van de &quot;input&quot;-array waarin de cursor zich bevindt (bijvoorbeeld COMP_CWORD)

- Vereist een waarde

#### `--api-version`, `-a`

De API-versie van het voltooiingsscript

- Vereist een waarde

#### `--symfony`, `-S`

verouderd

- Vereist een waarde


## `completion`

```bash
bin/magento completion [--debug] [--] [<shell>]
```

Het shell-voltooiingsscript dumpen

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    bin/magento completion  | sudo tee /etc/bash_completion.d/magento

Or dump the script to a local file and source it:

    bin/magento completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/www/html/magento2/bin/magento completion )"
```

### Argumenten

#### `shell`

Het shell type (bijvoorbeeld &quot;bash&quot;), de waarde van &quot;$SHELL&quot; env var zal worden gebruikt als dit niet wordt gegeven

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--debug`

Tik op het logbestand voor foutopsporing bij voltooien

- Standaard: `false`
- Accepteert geen waarde


## `help`

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

Help weergeven voor een opdracht

```
The help command displays help for a given command:

  bin/magento help list

You can also output the help in other formats by using the --format option:

  bin/magento help --format=xml list

To display the list of available commands, please use the list command.
```

### Argumenten

#### `command_name`

De opdrachtnaam

- Standaard: `help`

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--format`

De uitvoerindeling (txt, xml, json of md)

- Standaard: `txt`
- Vereist een waarde

#### `--raw`

Help bij de opdracht Uitvoeren

- Standaard: `false`
- Accepteert geen waarde


## `list`

```bash
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Lijstopdrachten

```
The list command lists all commands:

  bin/magento list

You can also display the commands for a specific namespace:

  bin/magento list test

You can also output the information in other formats by using the --format option:

  bin/magento list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  bin/magento list --raw
```

### Argumenten

#### `namespace`

De naamruimtenaam

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--raw`

Naar uitvoer RAW-opdrachtlijst

- Standaard: `false`
- Accepteert geen waarde

#### `--format`

De uitvoerindeling (txt, xml, json of md)

- Standaard: `txt`
- Vereist een waarde

#### `--short`

Om het beschrijven van de argumenten van bevelen over te slaan

- Standaard: `false`
- Accepteert geen waarde


## `admin:adobe-ims:disable`

```bash
bin/magento admin:adobe-ims:disable
```

Adobe IMS-module uitschakelen

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `admin:adobe-ims:enable`

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

Schakel Adobe IMS Module in.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--organization-id`, `-o`

Organisatie-id instellen voor Adobe IMS-configuratie. Vereist wanneer het toelaten van de module

- Accepteert een waarde

#### `--client-id`, `-c`

Stel de client-id in voor de Adobe IMS-configuratie. Vereist wanneer het toelaten van de module

- Accepteert een waarde

#### `--client-secret`, `-s`

Stel het clientgeheim in voor de configuratie van Adobe IMS. Vereist wanneer het toelaten van de module

- Accepteert een waarde

#### `--2fa`, `-t`

Controleer of 2FA is ingeschakeld voor Organisatie in Adobe Admin Console. Vereist wanneer het toelaten van de module

- Accepteert een waarde


## `admin:adobe-ims:info`

```bash
bin/magento admin:adobe-ims:info
```

Informatie over de configuratie van de Adobe IMS-module

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `admin:adobe-ims:status`

```bash
bin/magento admin:adobe-ims:status
```

Status van de Adobe IMS-module

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `admin:user:create`

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Hiermee wordt een beheerder gemaakt

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--admin-user`

(Vereist) Admin-gebruiker

- Vereist een waarde

#### `--admin-password`

(Vereist) Beheerderswachtwoord

- Vereist een waarde

#### `--admin-email`

(Vereist) E-mail beheerder

- Vereist een waarde

#### `--admin-firstname`

(Vereist) Voornaam beheerder

- Vereist een waarde

#### `--admin-lastname`

(Vereist) Achternaam beheerder

- Vereist een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `admin:user:unlock`

```bash
bin/magento admin:user:unlock <username>
```

Beheerdersaccount ontgrendelen

```
This command unlocks an admin account by its username.
To unlock:
      bin/magento admin:user:unlock username
```

### Argumenten

#### `username`

De te ontgrendelen admin-gebruikersnaam

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `app:config:dump`

```bash
bin/magento app:config:dump [<config-types>...]
```

Stortplaats van toepassing maken

### Argumenten

#### `config-types`

De ruimte-gescheiden lijst van configuratietypen of laat weg om alle [ werkingsgebied, thema&#39;s, systeem, i18n ] te dumpen

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `app:config:import`

```bash
bin/magento app:config:import
```

Gegevens uit gedeelde configuratiebestanden importeren naar de juiste gegevensopslag

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `app:config:status`

```bash
bin/magento app:config:status
```

Controleert of config-propagatie update vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `braintree:migrate`

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

Opgeslagen kaarten migreren uit een Magento 1-database

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--host`

Hostnaam/IP. Poort is optioneel

- Vereist een waarde

#### `--dbname`

Databasenaam

- Vereist een waarde

#### `--username`

Gebruikersnaam database. Leestoegang vereist

- Vereist een waarde

#### `--password`

Wachtwoord

- Vereist een waarde


## `cache:clean`

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Cachetype(s) wissen

### Argumenten

#### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

- Vereist een waarde


## `cache:clean:payment_services_merchant_scopes`

```bash
bin/magento cache:clean:payment_services_merchant_scopes
```

Cache van Merchant-bereik voor Clean Payment Services

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `cache:disable`

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Cachetype(s) uitschakelen

### Argumenten

#### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

- Vereist een waarde


## `cache:enable`

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Cachetype(s) inschakelen

### Argumenten

#### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

- Vereist een waarde


## `cache:flush`

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

Cacheopslag wordt gebruikt door cachetype(s)

### Argumenten

#### `types`

Lijst met door spaties gescheiden cachetypen of laten deze niet toe op alle cachetypen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

- Vereist een waarde


## `cache:status`

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

Hiermee wordt de cachestatus gecontroleerd

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--bootstrap`

parameters van de bootstrap toevoegen of overschrijven

- Vereist een waarde


## `catalog:images:resize`

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

Hiermee maakt u productafbeeldingen waarvan het formaat is gewijzigd

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--async`, `-a`

Afbeeldingen vergroten/verkleinen in asynchrone modus

- Standaard: `false`
- Accepteert geen waarde

#### `--skip_hidden_images`

Afbeeldingen die als verborgen op de productpagina zijn gemarkeerd, niet verwerken

- Standaard: `false`
- Accepteert geen waarde


## `catalog:product:attributes:cleanup`

```bash
bin/magento catalog:product:attributes:cleanup
```

Verwijdert ongebruikte productkenmerken.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `cms:wysiwyg:restrict`

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

Instellen of HTML-inhoudsvalidatie voor gebruikers moet worden afgedwongen of een waarschuwing moet weergeven

### Argumenten

#### `restrict`

y\n

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `config:sensitive:set`

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

Gevoelige configuratiewaarden instellen

### Argumenten

#### `path`

Configuratiepad, bijvoorbeeld groep/sectie/field_name


#### `value`

Configuratiewaarde

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--interactive`, `-i`

Interactieve modus inschakelen om alle gevoelige variabelen in te stellen

- Standaard: `false`
- Accepteert geen waarde

#### `--scope`

Bereik voor configuratie, indien niet ingesteld gebruik &#39;default&#39;

- Standaard: `default`
- Accepteert een waarde

#### `--scope-code`

Toepassingscode voor configuratie, standaard lege tekenreeks

- Standaard: &quot;
- Accepteert een waarde


## `config:set`

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

Systeemconfiguratie wijzigen

### Argumenten

#### `path`

Configuratiepad in indelingssectie/groep/veld_naam

- Vereist


#### `value`

Configuratiewaarde

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--scope`

Configuratiebereik (standaard, website of winkel)

- Standaard: `default`
- Vereist een waarde

#### `--scope-code`

Code bereik (alleen vereist als scope niet &#39;default&#39; is)

- Vereist een waarde

#### `--lock-env`, `-e`

Vergrendelingswaarde die wijziging in de beheerfunctie voorkomt (wordt opgeslagen in app/etc/env.php)

- Standaard: `false`
- Accepteert geen waarde

#### `--lock-config`, `-c`

Vergrendelen en waarde delen met andere installaties, wijzigingen voorkomen in Admin (wordt opgeslagen in app/etc/config.php)

- Standaard: `false`
- Accepteert geen waarde

#### `--lock`, `-l`

Vervangen, gebruik in plaats hiervan de optie —lock-env.

- Standaard: `false`
- Accepteert geen waarde


## `config:show`

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

Toont configuratiewaarde voor bepaalde weg. Als het pad niet is opgegeven, worden alle opgeslagen waarden weergegeven

### Argumenten

#### `path`

Configuratiepad, bijvoorbeeld section_id/group_id/field_id

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--scope`

Bereik voor configuratie, als niet gespecificeerd, dan &quot;gebrek&quot;werkingsgebied zal worden gebruikt

- Standaard: `default`
- Accepteert een waarde

#### `--scope-code`

Code bereik (alleen vereist als bereik niet `default` is)

- Standaard: &quot;
- Accepteert een waarde


## `cron:install`

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

Genereert en installeert een tab voor de huidige gebruiker

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--force`, `-f`

Installatietaken forceren

- Standaard: `false`
- Accepteert geen waarde

#### `--non-optional`, `-d`

Alleen de niet-optionele (standaard)taken installeren

- Standaard: `false`
- Accepteert geen waarde


## `cron:remove`

```bash
bin/magento cron:remove
```

Hiermee worden taken uit het tabblad Crontab verwijderd

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `cron:run`

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

Hiermee worden taken volgens schema uitgevoerd

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--group`

Alleen taken uitvoeren vanuit opgegeven groep

- Vereist een waarde

#### `--exclude-group`

Taken uitsluiten van de opgegeven groep

- Standaard: `[]`
- Accepteert meerdere waarden

#### `--bootstrap`

Parameters van de bootstrap toevoegen of overschrijven

- Vereist een waarde


## `customer:hash:upgrade`

```bash
bin/magento customer:hash:upgrade
```

De hash van de klant bijwerken volgens het meest recente algoritme

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `deploy:mode:set`

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

Toepassingsmodus instellen.

### Argumenten

#### `mode`

De toepassingsmodus die moet worden ingesteld. Beschikbare opties zijn &quot;developer&quot; of &quot;production&quot;

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--skip-compilation`, `-s`

Verwijdert het wissen en opnieuw genereren van statische inhoud (gegenereerde code, vooraf verwerkte CSS en elementen in pub/static/)

- Standaard: `false`
- Accepteert geen waarde


## `deploy:mode:show`

```bash
bin/magento deploy:mode:show
```

Geeft de huidige toepassingsmodus weer.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:di:info`

```bash
bin/magento dev:di:info <class> [<area>]
```

Verstrekt informatie over de configuratie van de Injectie van de Afhankelijkheid voor het Bevel.

### Argumenten

#### `class`

Klassenaam

- Vereist


#### `area`

Netnummer

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:email:newsletter-compatibility-check`

```bash
bin/magento dev:email:newsletter-compatibility-check
```

Scant nieuwsbrieven sjablonen voor mogelijke compatibiliteitsproblemen met variabeleverbruik

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:email:override-compatibility-check`

```bash
bin/magento dev:email:override-compatibility-check
```

Scant e-mailsjabloonoverschrijvingen voor mogelijke compatibiliteitsproblemen met variabelengebruik

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:profiler:disable`

```bash
bin/magento dev:profiler:disable
```

Maak profiler onbruikbaar.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:profiler:enable`

```bash
bin/magento dev:profiler:enable [<type>]
```

De analyse inschakelen.

### Argumenten

#### `type`

Type analyse

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:query-log:disable`

```bash
bin/magento dev:query-log:disable
```

Logboekregistratie van DB-query uitschakelen

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:query-log:enable`

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

Logbestand van DB-query inschakelen

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--include-all-queries`

Log alle query&#39;s. [ waar \|vals ]

- Standaard: `true`
- Accepteert een waarde

#### `--query-time-threshold`

Drempelwaarden voor zoektijd.

- Standaard: `0.001`
- Accepteert een waarde

#### `--include-call-stack`

Inclusief aanroepstack. [ waar \|vals ]

- Standaard: `true`
- Accepteert een waarde


## `dev:source-theme:deploy`

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

Hiermee worden bronbestanden voor thema verzameld en gepubliceerd.

### Argumenten

#### `file`

Bestanden die vooraf moeten worden verwerkt (bestand moet worden opgegeven zonder extensie)

- Standaard: `css/styles-mcss/styles-l`

- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--type`

Type van brondossiers: [ minder ]

- Standaard: `less`
- Vereist een waarde

#### `--locale`

Landinstelling: [ nl_NL ]

- Standaard: `en_US`
- Vereist een waarde

#### `--area`

Gebied: [ front\|adminhtml ]

- Standaard: `frontend`
- Vereist een waarde

#### `--theme`

Thema: [ Verkoper/thema ]

- Standaard: `Magento/luma`
- Vereist een waarde


## `dev:template-hints:disable`

```bash
bin/magento dev:template-hints:disable
```

Tips voor frontend-sjablonen uitschakelen. Wellicht is het leegmaken van de cache vereist.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:template-hints:enable`

```bash
bin/magento dev:template-hints:enable
```

Tips voor frontendsjablonen inschakelen. Wellicht is het leegmaken van de cache vereist.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:template-hints:status`

```bash
bin/magento dev:template-hints:status
```

Toon de status van frontend malplaatjewenken.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `dev:tests:run`

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

Tests bij uitvoering

### Argumenten

#### `type`

Type test dat moet worden uitgevoerd. Beschikbare types: allen, eenheid, integratie, integratie-allen, statisch, statisch-allen, integriteit, erfenis, gebrek

- Standaard: `default`

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--arguments`, `-c`

Aanvullende argumenten voor PHPUnit. Voorbeeld: &quot;-c&#39;—filter=MyTest&#39;&#39; (geen spaties)

- Standaard: &quot;
- Vereist een waarde


## `dev:urn-catalog:generate`

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

Genereert de catalogus van URNs aan *.xsd- afbeeldingen voor winde om xml te benadrukken.

### Argumenten

#### `path`

Pad naar bestand voor uitvoer van catalogus. Voor PHPStorm-gebruik .idea/misc.xml

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--ide`

Indeling waarin de catalogus wordt gegenereerd. Ondersteund: [ phpstorm, vscode ]

- Standaard: `phpstorm`
- Vereist een waarde


## `dev:xml:convert`

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

Hiermee wordt een XML-bestand geconverteerd met XSL-stijlpagina&#39;s

### Argumenten

#### `xml-file`

Pad naar XML-bestand dat moet worden getransformeerd

- Vereist


#### `processor`

Pad naar XSL-stijlpagina die wordt toegepast op XML-bestand

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--overwrite`, `-o`

XML-bestand overschrijven

- Standaard: `false`
- Accepteert geen waarde


## `downloadable:domains:add`

```bash
bin/magento downloadable:domains:add [<domains>...]
```

Domeinen toevoegen aan de whitelist van downloadbare domeinen

### Argumenten

#### `domains`

Naam van domein

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `downloadable:domains:remove`

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

Verwijder domeinen uit de downloadbare whitelist van domeinen

### Argumenten

#### `domains`

Domeinnamen

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `downloadable:domains:show`

```bash
bin/magento downloadable:domains:show
```

Downloadbare whitelist van domeinen weergeven

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `encryption:data:list-re-encryptors`

```bash
bin/magento encryption:data:list-re-encryptors
```

Toont een lijst van beschikbare gegevens re-encryptors.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `encryption:data:re-encrypt`

```bash
bin/magento encryption:data:re-encrypt [<encryptors>...]
```

Codeert gecodeerde gegevens opnieuw met de huidige coderingssleutel.

### Argumenten

#### `encryptors`

Lijst met hercoderingsapparaten met spaties als scheidingsteken.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `encryption:key:change`

```bash
bin/magento encryption:key:change [-k|--key [KEY]]
```

Wijzig de coderingssleutel in het bestand env.php.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--key`, `-k`

De sleutel moet een lange tekenreeks van 32 tekens zijn. Indien niet opgegeven, wordt een willekeurige sleutel gegenereerd.

- Accepteert een waarde


## `encryption:payment-data:update`

```bash
bin/magento encryption:payment-data:update
```

Codeert gecodeerde creditcardgegevens opnieuw met de nieuwste coderingssleutel.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `events:create-event-provider`

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]events:provider:create 
```

Maak een aangepaste gebeurtenisprovider in Adobe I/O Events voor deze instantie. Als u de label- en beschrijvingsopties niet opgeeft, moeten deze worden gedefinieerd in het bestand system app/etc/event-types.json.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--label`

Een label om uw aangepaste provider te definiëren.

- Accepteert een waarde

#### `--description`

Een beschrijving van uw provider.

- Accepteert een waarde


## `events:generate:module`

```bash
bin/magento events:generate:module
```

Module genereren op basis van de lijst met insteekmodules

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `events:info`

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```

Retourneert de payload van de opgegeven gebeurtenis.

### Argumenten

#### `event-code`

Gebeurteniscode

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--depth`

Het aantal niveaus in de gebeurtenislading om terug te keren

- Standaard: `2`
- Accepteert een waarde


## `events:list`

```bash
bin/magento events:list
```

Geeft een lijst met geabonneerde gebeurtenissen weer

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `events:list:all`

```bash
bin/magento events:list:all <module_name>
```

Hiermee wordt een lijst geretourneerd met abonnementsgebeurtenissen die in de opgegeven module zijn gedefinieerd

### Argumenten

#### `module_name`

Modulenaam

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `events:metadata:populate`

```bash
bin/magento events:metadata:populate
```

Hiermee maakt u metagegevens in Adobe I/O op basis van de configuratielijst (XML en toepassingsconfiguraties)

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `events:provider:info`

```bash
bin/magento events:provider:info
```

Hiermee worden gegevens over de geconfigureerde gebeurtenisprovider geretourneerd

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `events:registrations:list`

```bash
bin/magento events:registrations:list
```

Somt gebeurtenisregistraties in uw App Builder-project op

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `events:subscribe`

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [-d|--destination DESTINATION] [--hipaaAuditRequired] [--] <event-code>
```

Abonneren op de gebeurtenis

### Argumenten

#### `event-code`

Gebeurteniscode

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--force`, `-f`

Dwingt de gespecificeerde gebeurtenis om worden ingetekend, zelfs als het niet plaatselijk is bepaald.

- Standaard: `false`
- Accepteert geen waarde

#### `--fields`

De lijst met velden in de payload van gebeurtenisgegevens.

- Standaard: `[]`
- Vereist een waarde

#### `--parent`

De bovenliggende gebeurteniscode voor een gebeurtenisabonnement met regels of als een alias.

- Vereist een waarde

#### `--rules`

De lijst met regels voor het gebeurtenisabonnement, waarbij elke regel is opgemaakt als &quot;field\|operator\|value&quot;. Als u deze optie wilt gebruiken, moet u ook de optie &quot;bovenliggend item&quot; opgeven.

- Standaard: `[]`
- Vereist een waarde

#### `--priority`, `-p`

Versnelt de verzending van deze gebeurtenis. Geef deze optie op voor gebeurtenissen die direct moeten worden geleverd. Standaard worden gebeurtenissen eenmaal per minuut met een kroon verzonden.

- Standaard: `false`
- Accepteert geen waarde

#### `--destination`, `-d`

De bestemming van deze gebeurtenis. Geef deze optie op voor de gebeurtenissen die naar de aangepaste bestemming moeten worden verzonden.

- Standaard: `default`
- Vereist een waarde

#### `--hipaaAuditRequired`

Geeft aan dat de gebeurtenis gegevens bevat die worden gecontroleerd door HIPAA.

- Standaard: `false`
- Accepteert geen waarde


## `events:sync-events-metadata`

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

Metagegevens van gebeurtenissen synchroniseren voor deze instantie

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--delete`, `-d`

Metagegevens van gebeurtenissen verwijderen is niet langer vereist

- Standaard: `false`
- Accepteert geen waarde


## `events:unsubscribe`

```bash
bin/magento events:unsubscribe <event-code>
```

Hiermee wordt het abonnement op de opgegeven gebeurtenis verwijderd

### Argumenten

#### `event-code`

Gebeurteniscode waarvan abonnement moet worden opgezegd

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `i18n:collect-phrases`

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

Neemt zinnen op in de codebase

### Argumenten

#### `directory`

Mappad om te parseren. Niet nodig indien —magento-markering is ingesteld

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--output`, `-o`

Pad (inclusief bestandsnaam) naar een uitvoerbestand. Als er geen bestand is opgegeven, wordt standaard stdout toegepast.

- Vereist een waarde

#### `--magento`, `-m`

Gebruik de parameter —magento om de huidige Magento-codebase te parseren. Laat de parameter weg als een folder wordt gespecificeerd.

- Standaard: `false`
- Accepteert geen waarde


## `i18n:pack`

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

Slaat taalpakket op

### Argumenten

#### `source`

Pad naar bronwoordenboekbestand met vertalingen

- Vereist


#### `locale`

Doellandinstelling voor woordenboek, bijvoorbeeld &quot;de_DE&quot;

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--mode`, `-m`

Modus Opslaan voor woordenboek - &quot;replace&quot; - taalpakket vervangen door nieuw - &quot;merge&quot; - taalpakketten samenvoegen door standaard &quot;replace&quot;

- Standaard: `replace`
- Vereist een waarde

#### `--allow-duplicates`, `-d`

Gebruik de parameter —allow-duplicates om het opslaan van duplicaten van translate toe te staan. Laat anders de parameter weg.

- Standaard: `false`
- Accepteert geen waarde


## `i18n:uninstall`

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

Verwijdert taalpakketten

### Argumenten

#### `package`

Taalpakketnaam

- Standaard: `[]`
- Vereist

- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--backup-code`, `-b`

Back-up maken van code- en configuratiebestanden (behalve tijdelijke bestanden)

- Standaard: `false`
- Accepteert geen waarde


## `indexer:info`

```bash
bin/magento indexer:info
```

Toegestane indexen weergeven

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `indexer:reindex`

```bash
bin/magento indexer:reindex [<index>...]
```

Gegevens opnieuw indexeren

### Argumenten

#### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `indexer:reset`

```bash
bin/magento indexer:reset [<index>...]
```

Hiermee wordt de status van de indexeerder opnieuw ingesteld op ongeldig

### Argumenten

#### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `indexer:set-dimensions-mode`

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

Modus Indexerafmetingen instellen

### Argumenten

#### `indexer`

Indexernaam [ catalog_product_price|catalogispermissions_category ]


#### `mode`

Index_dimensiemodi catalog_product_price          none,website,klant_groep,website_and_customer_group catalogi_category    none,customer_group

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `indexer:set-mode`

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

Hiermee wordt het type indexmodus ingesteld

### Argumenten

#### `mode`

Het type van wijze van de indexeer [ realtime|programma ]


#### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `indexer:set-status`

```bash
bin/magento indexer:set-status <status> [<index>...]
```

Hiermee wordt de opgegeven indexeerstatus ingesteld

### Argumenten

#### `status`

Indexerstatus type [ ongeldig|opgeschort|geldig ]

- Vereist


#### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `indexer:show-dimensions-mode`

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

Geeft de Dimension-modus van Index weer

### Argumenten

#### `indexer`

Lijst met door spaties gescheiden indextypen of laat deze weg om toe te passen op alle indexen (catalog_product_price,catalogpermissions_category)

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `indexer:show-mode`

```bash
bin/magento indexer:show-mode [<index>...]
```

Indexmodus weergeven

### Argumenten

#### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `indexer:status`

```bash
bin/magento indexer:status [<index>...]
```

Hiermee wordt de status van Indexer weergegeven

### Argumenten

#### `index`

Lijst met door spaties gescheiden indextypen of laat toe om op alle indexen toe te passen.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `info:adminuri`

```bash
bin/magento info:adminuri
```

Hiermee wordt de Magento Admin URI weergegeven

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `info:backups:list`

```bash
bin/magento info:backups:list
```

Lijst met beschikbare back-upbestanden afdrukken

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `info:currency:list`

```bash
bin/magento info:currency:list
```

Geeft de lijst met beschikbare valuta&#39;s weer

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `info:dependencies:show-framework`

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

Geeft een aantal afhankelijkheden van het Magento-framework weer

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--output`, `-o`

Bestandsnaam rapport

- Standaard: `framework-dependencies.csv`
- Vereist een waarde


## `info:dependencies:show-modules`

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

Toont aantal gebiedsdelen tussen modules

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--output`, `-o`

Bestandsnaam rapport

- Standaard: `modules-dependencies.csv`
- Vereist een waarde


## `info:dependencies:show-modules-circular`

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

Toont aantal kringafhankelijkheden tussen modules

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--output`, `-o`

Bestandsnaam rapport

- Standaard: `modules-circular-dependencies.csv`
- Vereist een waarde


## `info:language:list`

```bash
bin/magento info:language:list
```

Geeft de lijst met beschikbare taallandinstellingen weer

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `info:timezone:list`

```bash
bin/magento info:timezone:list
```

Hiermee geeft u de lijst met beschikbare tijdzones weer

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `inventory:reservation:create-compensations`

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

Maak punten van voorbehoud door middel van opgegeven compensatieargumenten

### Argumenten

#### `compensations`

Lijst met argumenten voor compensatie in de notatie &quot;:::&quot;

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--raw`, `-r`

Onbewerkte uitvoer

- Standaard: `false`
- Accepteert geen waarde


## `inventory:reservation:list-inconsistencies`

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

Alle bestellingen en producten met inconsistenties in verkoopbare hoeveelheid tonen

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--complete-orders`, `-c`

Alleen inconsistenties voor volledige bestellingen tonen

- Standaard: `false`
- Accepteert geen waarde

#### `--incomplete-orders`, `-i`

Alleen inconsistenties tonen voor onvolledige orders

- Standaard: `false`
- Accepteert geen waarde

#### `--bunch-size`, `-b`

Hiermee bepaalt u hoeveel bestellingen tegelijkertijd worden geladen

- Standaard: `50`
- Accepteert een waarde

#### `--raw`, `-r`

Onbewerkte uitvoer

- Standaard: `false`
- Accepteert geen waarde


## `inventory-geonames:import`

```bash
bin/magento inventory-geonames:import <countries>...
```

Geo-namen downloaden en importeren voor het algoritme van de bronselectie

### Argumenten

#### `countries`

Lijst van landcodes die moeten worden ingevoerd

- Standaard: `[]`
- Vereist

- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `maintenance:allow-ips`

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

Plaatst onderhoudswijze vrijgestelde IPs

### Argumenten

#### `ip`

Toegestane IP adressen

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--none`

Toegestane IP-adressen wissen

- Standaard: `false`
- Accepteert geen waarde

#### `--add`

IP-adres toevoegen aan bestaande lijst

- Standaard: `false`
- Accepteert geen waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `maintenance:disable`

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Onderhoudsmodus uitschakelen

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--ip`

Toegestane IP adressen (gebruik &quot;niets&quot;om toegestane IP lijst te ontruimen)

- Standaard: `[]`
- Vereist een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `maintenance:enable`

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Onderhoudsmodus inschakelen

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--ip`

Toegestane IP adressen (gebruik &quot;niets&quot;om toegestane IP lijst te ontruimen)

- Standaard: `[]`
- Vereist een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `maintenance:status`

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

De status van de onderhoudsmodus weergeven

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `media-content:sync`

```bash
bin/magento media-content:sync
```

Inhoud synchroniseren met elementen

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `media-gallery:sync`

```bash
bin/magento media-gallery:sync
```

Mediaopslag en media-elementen in de database synchroniseren

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `module:config:status`

```bash
bin/magento module:config:status
```

Controleert de moduleconfiguratie in het &quot;app/etc/config.php&quot;dossier en rapporteert als zij of niet bijgewerkt zijn

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `module:disable`

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Hiermee worden opgegeven modules uitgeschakeld

### Argumenten

#### `module`

Naam van de module

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--force`, `-f`

Controle voor passageafhankelijkheden

- Standaard: `false`
- Accepteert geen waarde

#### `--all`

Alle modules uitschakelen

- Standaard: `false`
- Accepteert geen waarde

#### `--clear-static-content`, `-c`

Gegenereerde statische weergavebestanden wissen. Noodzakelijk als de module(s) statische weergavebestanden heeft

- Standaard: `false`
- Accepteert geen waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `module:enable`

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

Hiermee worden opgegeven modules ingeschakeld

### Argumenten

#### `module`

Naam van de module

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--force`, `-f`

Controle voor passageafhankelijkheden

- Standaard: `false`
- Accepteert geen waarde

#### `--all`

Alle modules inschakelen

- Standaard: `false`
- Accepteert geen waarde

#### `--clear-static-content`, `-c`

Gegenereerde statische weergavebestanden wissen. Noodzakelijk als de module(s) statische weergavebestanden heeft

- Standaard: `false`
- Accepteert geen waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `module:status`

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

Geeft de status van modules weer

### Argumenten

#### `module-names`

Optionele modulenaam

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--enabled`

Alleen ingeschakelde modules afdrukken

- Standaard: `false`
- Accepteert geen waarde

#### `--disabled`

Alleen uitgeschakelde modules afdrukken

- Standaard: `false`
- Accepteert geen waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `module:uninstall`

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

Hiermee verwijdert u modules die door de composer zijn geïnstalleerd

### Argumenten

#### `module`

Naam van de module

- Standaard: `[]`
- Vereist

- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--remove-data`, `-r`

Gegevens verwijderen die zijn geïnstalleerd door module(s)

- Standaard: `false`
- Accepteert geen waarde

#### `--backup-code`

Back-up maken van code- en configuratiebestanden (behalve tijdelijke bestanden)

- Standaard: `false`
- Accepteert geen waarde

#### `--backup-media`

Mediaback-up maken

- Standaard: `false`
- Accepteert geen waarde

#### `--backup-db`

Volledige back-up van de database maken

- Standaard: `false`
- Accepteert geen waarde

#### `--non-composer`

Alle modules, die hier voorbij zullen zijn zullen niet op composer gebaseerd zijn

- Standaard: `false`
- Accepteert geen waarde

#### `--clear-static-content`, `-c`

Gegenereerde statische weergavebestanden wissen. Noodzakelijk als de module(s) statische weergavebestanden heeft

- Standaard: `false`
- Accepteert geen waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `newrelic:create:deploy-marker`

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

Controleer de opstellen rij voor ingangen en creeer aangewezen plaatsingsteller.

### Argumenten

#### `message`

Bericht implementeren?

- Vereist


#### `change_log`

Logboek wijzigen?

- Vereist


#### `user`

Implementatiegebruiker


#### `revision`

Herziening

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `queue:consumers:list`

```bash
bin/magento queue:consumers:list
```

Lijst met consumenten van MessageQueue

```
This command shows list of MessageQueue consumers.
```

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `queue:consumers:restart`

```bash
bin/magento queue:consumers:restart
```

Gebruikers van MessageQueue opnieuw starten

```
Command put poison pill for MessageQueue consumers and force to restart them after next status check.
```

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `queue:consumers:start`

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

MessageQueue-consument starten

```
This command starts MessageQueue consumer by its name.

To start consumer which will process all queued messages and terminate execution:

    bin/magento queue:consumers:start someConsumer

To specify the number of messages which should be processed by consumer before its termination:

    bin/magento queue:consumers:start someConsumer --max-messages=50

To specify the number of messages per batch for the batch consumer:

    bin/magento queue:consumers:start someConsumer --batch-size=500

To specify the preferred area:

    bin/magento queue:consumers:start someConsumer --area-code='adminhtml'

To do not run multiple copies of one consumer simultaneously:

    bin/magento queue:consumers:start someConsumer --single-thread

To save PID enter path (This option is deprecated, use --single-thread instead):

    bin/magento queue:consumers:start someConsumer --pid-file-path='/var/someConsumer.pid'

To define the number of processes per consumer:

    bin/magento queue:consumers:start someConsumer --multi-process=4
```

### Argumenten

#### `consumer`

De naam van de consument die moet worden gestart.

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--max-messages`

Het aantal berichten dat de consument moet verwerken voordat het proces wordt beëindigd. Indien niet gespecificeerd - eindig na verwerking van alle een rij gevormde berichten.

- Vereist een waarde

#### `--batch-size`

Het aantal berichten per partij. Alleen van toepassing op de partijconsument.

- Vereist een waarde

#### `--area-code`

De standaardinstelling voor het voorkeursgebied (global, adminhtml, etc..) is global.

- Vereist een waarde

#### `--single-thread`

Met deze optie voorkomt u dat meerdere exemplaren van één consument tegelijk worden uitgevoerd.

- Standaard: `false`
- Accepteert geen waarde

#### `--multi-process`

Het aantal processen per consument.

- Accepteert een waarde

#### `--pid-file-path`

Het bestandspad voor het opslaan van PID (deze optie is afgekeurd, gebruik —enkele thread in plaats daarvan)

- Vereist een waarde


## `remote-storage:sync`

```bash
bin/magento remote-storage:sync
```

Mediabestanden synchroniseren met externe opslag.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `saas:resync`

```bash
bin/magento saas:resync [--feed FEED] [--no-reindex] [--cleanup-feed] [--dry-run] [--thread-count THREAD-COUNT] [--batch-size BATCH-SIZE] [--continue-resync] [--by-ids BY-IDS] [--id-type ID-TYPE]
```

Hersynchroniseert voedergegevens aan de dienst SaaS.

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--feed`

Geef de feed-naam op om opnieuw te synchroniseren met SaaS-service. Beschikbare feeds: orderproductie van betalingsservices, betalingsservicesbestelsandbox, orderstatus van betalingsservices, betalingsservicestatus sandbox, betalingsservices, winkelproductie van betalingsservices, zandbak in de winkel voor betalingsservices

- Vereist een waarde

#### `--no-reindex`

Voer de gegevens van de feed alleen opnieuw in bij de SaaS-service. Wordt niet opnieuw geindexeerd. (Deze optie is niet van toepassing op de producten, de producten, de prijzen en de feeds)

- Standaard: `false`
- Accepteert geen waarde

#### `--cleanup-feed`

Forceer om de indextabel van de feed vóór synchronisatie op te schonen.

- Standaard: `false`
- Accepteert geen waarde

#### `--dry-run`

Droge run. Gegevens worden niet geëxporteerd. Als u de payload wilt opslaan in het logbestand var/log/saas-export.log, voert u de variabele EXPORTER_EXTENDED_LOG=1 uit.

- Standaard: `false`
- Accepteert geen waarde

#### `--thread-count`

Aantal synchronisatiethread instellen.

- Vereist een waarde

#### `--batch-size`

Batchgrootte voor synchronisatie instellen

- Vereist een waarde

#### `--continue-resync`

Doorgaan met opnieuw synchroniseren vanaf de laatste opgeslagen positie (deze optie is van toepassing op de producten, de producten, de prijzen en de feeds)

- Standaard: `false`
- Accepteert geen waarde

#### `--by-ids`

Gedeeltelijk opnieuw synchroniseren door lijst met opgegeven id&#39;s. (Deze optie is van toepassing op de producten, productoverschrijvingen en de prijzen)

- Vereist een waarde

#### `--id-type`

Type id&#39;s voor gedeeltelijke resync (bijvoorbeeld: sku, productId, enz.)

- Vereist een waarde


## `sampledata:deploy`

```bash
bin/magento sampledata:deploy [--no-update]
```

Stel steekproefgegevensmodules voor op composer-gebaseerde installaties van Magento op

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--no-update`

Composer.json bijwerken zonder componentupdate uit te voeren

- Standaard: `false`
- Accepteert geen waarde


## `sampledata:remove`

```bash
bin/magento sampledata:remove [--no-update]
```

Alle pakketten met voorbeeldgegevens verwijderen uit composer.json

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--no-update`

Composer.json bijwerken zonder componentupdate uit te voeren

- Standaard: `false`
- Accepteert geen waarde


## `sampledata:reset`

```bash
bin/magento sampledata:reset
```

Alle modules met voorbeeldgegevens opnieuw instellen voor herinstallatie

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `security:recaptcha:disable-for-user-forgot-password`

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

reCAPTCHA uitschakelen voor wachtwoordformulier voor vergeten gebruiker van beheerder

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `security:recaptcha:disable-for-user-login`

```bash
bin/magento security:recaptcha:disable-for-user-login
```

reCAPTCHA uitschakelen voor aanmeldingsformulier voor beheerder

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `security:tfa:google:set-secret`

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

Stel het geheim in dat voor Google OTP-generatie wordt gebruikt.

### Argumenten

#### `user`

Gebruikersnaam

- Vereist


#### `secret`

Geheim

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `security:tfa:providers`

```bash
bin/magento security:tfa:providers
```

Alle beschikbare providers weergeven

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `security:tfa:reset`

```bash
bin/magento security:tfa:reset <user> <provider>
```

Configuratie voor één gebruiker opnieuw instellen

### Argumenten

#### `user`

Gebruikersnaam

- Vereist


#### `provider`

Providercode

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `server:run`

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-wn|--workerNum [WORKERNUM]] [-dm|--dispatchMode [DISPATCHMODE]] [-mr|--maxRequests [MAXREQUESTS]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]] [-mwt|--maxWaitTime [MAXWAITTIME]] [--state-monitor]
```

Toepassingsserver uitvoeren

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--port`, `-p`

poort die u wilt gebruiken

- Standaard: `9501`
- Accepteert een waarde

#### `--background`, `-b`

markering achtergrondmodus

- Standaard: `0`
- Accepteert een waarde

#### `--workerNum`, `-wn`

aantal te starten werknemersprocessen

- Standaard: `4`
- Accepteert een waarde

#### `--dispatchMode`, `-dm`

wijze van het verzenden van verbindingen aan de arbeidersprocessen

- Standaard: `3`
- Accepteert een waarde

#### `--maxRequests`, `-mr`

max. verzoeken voordat het arbeidersproces opnieuw wordt gestart

- Standaard: `10000`
- Accepteert een waarde

#### `--area`, `-a`

toepassingsservergebied

- Standaard: `graphql`
- Accepteert een waarde

#### `--magento-init-params`, `-mip`

magento bootstrap init params

- Standaard: &quot;
- Accepteert een waarde

#### `--maxWaitTime`, `-mwt`

hoe lang moet worden gewacht op workers na herladen (bijv. config verandering) alvorens hen te doden

- Standaard: `3600`
- Accepteert een waarde

#### `--state-monitor`

Statusbewaking inschakelen. Gebruik dit alleen voor foutopsporingsstatusproblemen.

- Standaard: `false`
- Accepteert geen waarde


## `server:state-monitor:aggregate-output`

```bash
bin/magento server:state-monitor:aggregate-output
```

Samengevoegde output van staatsmonitor van ApplicationServer

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `setup:backup`

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Maakt back-up van Magento Application Code base, media en database

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--code`

Back-up maken van code- en configuratiebestanden (behalve tijdelijke bestanden)

- Standaard: `false`
- Accepteert geen waarde

#### `--media`

Mediaback-up maken

- Standaard: `false`
- Accepteert geen waarde

#### `--db`

Volledige back-up van de database maken

- Standaard: `false`
- Accepteert geen waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:config:set`

```bash
bin/magento setup:config:set [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Creeert of wijzigt de plaatsingsconfiguratie

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--remote-storage-driver`

Extern opslagstuurprogramma

- Vereist een waarde

#### `--remote-storage-prefix`

Voorvoegsel voor externe opslag

- Standaard: &quot;
- Vereist een waarde

#### `--remote-storage-endpoint`

Extern opslageindpunt

- Vereist een waarde

#### `--remote-storage-bucket`

Externe opslagemmer

- Vereist een waarde

#### `--remote-storage-region`

Externe opslagregio

- Vereist een waarde

#### `--remote-storage-key`

Toegangstoets externe opslag

- Standaard: &quot;
- Vereist een waarde

#### `--remote-storage-secret`

Sleutel voor geheim opslagruimte

- Standaard: &quot;
- Vereist een waarde

#### `--remote-storage-path-style`

Padstijl voor externe opslag

- Standaard: `0`
- Vereist een waarde

#### `--backend-frontname`

Backend frontname (wordt automatisch gegenereerd als deze ontbreekt)

- Vereist een waarde

#### `--enable-debug-logging`

Foutopsporingsregistratie inschakelen

- Vereist een waarde

#### `--enable-syslog-logging`

syslog inschakelen

- Vereist een waarde

#### `--id_salt`

GraphQl Salt

- Vereist een waarde

#### `--checkout-async`

Afwisselende orderverwerking inschakelen? 1 - Ja, 0 - Nee

- Vereist een waarde

#### `--config-async`

Opslaan van asynchrone beheerconfiguratie inschakelen? 1 - Ja, 0 - Nee

- Vereist een waarde

#### `--amqp-host`

Amqp-serverhost

- Standaard: &quot;
- Vereist een waarde

#### `--amqp-port`

Amqp-serverpoort

- Standaard: `5672`
- Vereist een waarde

#### `--amqp-user`

Gebruikersnaam Amqp-server

- Standaard: &quot;
- Vereist een waarde

#### `--amqp-password`

Wachtwoord Amqp-server

- Standaard: &quot;
- Vereist een waarde

#### `--amqp-virtualhost`

AMQP virtualhost

- Standaard: `/`
- Vereist een waarde

#### `--amqp-ssl`

Amqp SSL

- Standaard: &quot;
- Vereist een waarde

#### `--amqp-ssl-options`

Amqp SSL-opties (JSON)

- Standaard: &quot;
- Vereist een waarde

#### `--consumers-wait-for-messages`

Moeten consumenten wachten op een bericht uit de wachtrij? 1 - Ja, 0 - Nee

- Vereist een waarde

#### `--queue-default-connection`

Standaardverbinding in wachtrij met berichten. Kan &#39;db&#39;, &#39;amqp&#39; of een aangepast wachtrijsysteem zijn. Het wachtrijsysteem moet worden geïnstalleerd en geconfigureerd, anders worden de berichten niet correct verwerkt.

- Vereist een waarde

#### `--deferred-total-calculating`

Uitgestelde totale berekening inschakelen? 1 - Ja, 0 - Nee

- Vereist een waarde

#### `--key`

Versleutelingssleutel

- Vereist een waarde

#### `--db-host`

Host databaseserver

- Vereist een waarde

#### `--db-name`

Databasenaam

- Vereist een waarde

#### `--db-user`

Gebruikersnaam databaseserver

- Vereist een waarde

#### `--db-engine`

Database-server-engine

- Vereist een waarde

#### `--db-password`

Wachtwoord databaseserver

- Vereist een waarde

#### `--db-prefix`

Voorvoegsel databasetabel

- Vereist een waarde

#### `--db-model`

Databasetype

- Vereist een waarde

#### `--db-init-statements`

Eerste set opdrachten database

- Vereist een waarde

#### `--skip-db-validation`, `-s`

Indien opgegeven, wordt de db-verbindingsvalidatie overgeslagen

- Standaard: `false`
- Accepteert geen waarde

#### `--http-cache-hosts`

http-cachehosts

- Vereist een waarde

#### `--db-ssl-key`

Volledig pad van clientsleutelbestand om een databaseverbinding tot stand te brengen via SSL

- Standaard: &quot;
- Vereist een waarde

#### `--db-ssl-cert`

Volledig pad van clientcertificaatbestand om een databaseverbinding tot stand te brengen via SSL

- Standaard: &quot;
- Vereist een waarde

#### `--db-ssl-ca`

Volledig pad van servercertificaatbestand om een databaseverbinding tot stand te brengen via SSL

- Standaard: &quot;
- Vereist een waarde

#### `--db-ssl-verify`

Servercertificering controleren

- Standaard: `false`
- Accepteert geen waarde

#### `--session-save`

Sessieopslaghandler

- Vereist een waarde

#### `--session-save-redis-host`

Volledig - gekwalificeerde gastheernaam, IP adres, of absolute weg als het gebruiken van de contactdozen van UNIX

- Vereist een waarde

#### `--session-save-redis-port`

Redis-poort voor luisteren naar server

- Vereist een waarde

#### `--session-save-redis-password`

Wachtwoord voor opnieuw verzonden server

- Vereist een waarde

#### `--session-save-redis-timeout`

Time-out verbinding, in seconden

- Vereist een waarde

#### `--session-save-redis-retries`

Opnieuw wordt verbinding opnieuw geprobeerd.

- Vereist een waarde

#### `--session-save-redis-persistent-id`

Unieke tekenreeks om permanente verbindingen in te schakelen

- Vereist een waarde

#### `--session-save-redis-db`

Databasenummer van Redis

- Vereist een waarde

#### `--session-save-redis-compression-threshold`

Compressiedrempel opnieuw instellen

- Vereist een waarde

#### `--session-save-redis-compression-lib`

Compressiebibliotheek opnieuw uitschakelen. Waarden: gzip (standaardwaarde), lzf, lz4, snappy

- Vereist een waarde

#### `--session-save-redis-log-level`

Opnieuw schijflogniveau. Waarden: 0 (minst uitgebreid) tot 7 (meest uitgebreide)

- Vereist een waarde

#### `--session-save-redis-max-concurrency`

Maximum aantal processen dat op een slot op één zitting kan wachten

- Vereist een waarde

#### `--session-save-redis-break-after-frontend`

Aantal seconden dat moet worden gewacht voordat wordt geprobeerd een vergrendeling voor een frontendsessie te verbreken

- Vereist een waarde

#### `--session-save-redis-break-after-adminhtml`

Aantal seconden dat moet worden gewacht voordat wordt geprobeerd een vergrendeling voor beheersessie te verbreken

- Vereist een waarde

#### `--session-save-redis-first-lifetime`

Levensduur, in seconden, van sessie voor niet-bots bij eerste schrijven (gebruik 0 om uit te schakelen)

- Vereist een waarde

#### `--session-save-redis-bot-first-lifetime`

Levensduur, in seconden, van sessie voor bots bij de eerste schrijfbewerking (gebruik 0 om uit te schakelen)

- Vereist een waarde

#### `--session-save-redis-bot-lifetime`

De levensduur van de sessie voor bots bij volgende schrijvingen (gebruik 0 om uit te schakelen)

- Vereist een waarde

#### `--session-save-redis-disable-locking`

Schakel vergrendeling opnieuw uit. Waarden: false (standaardwaarde), true

- Vereist een waarde

#### `--session-save-redis-min-lifetime`

Standaardsessielevensduur van Redis, in seconden

- Vereist een waarde

#### `--session-save-redis-max-lifetime`

Maximale sessielevensduur van Redis, in seconden

- Vereist een waarde

#### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Vereist een waarde

#### `--session-save-redis-sentinel-servers`

Redis Sentinel-servers, gescheiden door komma&#39;s

- Vereist een waarde

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verify master. Waarden: false (standaardwaarde), true

- Vereist een waarde

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel verbindt opnieuw pogingen.

- Vereist een waarde

#### `--cache-backend`

Standaardcachehandler

- Vereist een waarde

#### `--cache-backend-redis-server`

Redis-server

- Vereist een waarde

#### `--cache-backend-redis-db`

Databasenummer voor de cache

- Vereist een waarde

#### `--cache-backend-redis-port`

Redis-poort voor luisteren naar server

- Vereist een waarde

#### `--cache-backend-redis-password`

Wachtwoord voor opnieuw verzonden server

- Vereist een waarde

#### `--cache-backend-redis-compress-data`

Instellen op 0 om compressie uit te schakelen (standaard is 1, ingeschakeld)

- Vereist een waarde

#### `--cache-backend-redis-compression-lib`

Compressiellib om [ snappy, lzf, l4z, zstd, gzip ] te gebruiken (verlaten leeg om automatisch te bepalen)

- Vereist een waarde

#### `--cache-backend-redis-use-lua`

Ingesteld op 1 om lua in te schakelen (standaardwaarde is 0, uitgeschakeld)

- Vereist een waarde

#### `--cache-backend-redis-use-lua-on-gc`

Ingesteld op 0 om lua uit te schakelen bij opschonen (standaard is 1, ingeschakeld)

- Vereist een waarde

#### `--cache-id-prefix`

ID-voorvoegsel voor cachesleutels

- Vereist een waarde

#### `--allow-parallel-generation`

Genereren van cache op een niet-blokkerende manier toestaan

- Standaard: `false`
- Accepteert geen waarde

#### `--page-cache`

Standaardcachehandler

- Vereist een waarde

#### `--page-cache-redis-server`

Redis-server

- Vereist een waarde

#### `--page-cache-redis-db`

Databasenummer voor de cache

- Vereist een waarde

#### `--page-cache-redis-port`

Redis-poort voor luisteren naar server

- Vereist een waarde

#### `--page-cache-redis-password`

Wachtwoord voor opnieuw verzonden server

- Vereist een waarde

#### `--page-cache-redis-compress-data`

Ingesteld op 1 om de cache van de volledige pagina te comprimeren (gebruik 0 om uit te schakelen)

- Vereist een waarde

#### `--page-cache-redis-compression-lib`

De bibliotheek van de compressie om [ snappy, lzf, l4z, zstd, gzip ] te gebruiken (verlaten leeg om automatisch te bepalen)

- Vereist een waarde

#### `--page-cache-id-prefix`

ID-voorvoegsel voor cachesleutels

- Vereist een waarde

#### `--lock-provider`

Naam provider vergrendelen

- Vereist een waarde

#### `--lock-db-prefix`

Installatiespecifiek vergrendelingsvoorvoegsel om vergrendelingsconflicten te voorkomen

- Vereist een waarde

#### `--lock-zookeeper-host`

Host en poort voor verbinding met Zookeeper-cluster. Bijvoorbeeld: 127.0.0.1:2181

- Vereist een waarde

#### `--lock-zookeeper-path`

Het pad waar Zookeeper vergrendelingen opslaat. Het standaardpad is: /magento/locks

- Vereist een waarde

#### `--lock-file-path`

Het pad waar de bestandsvergrendelingen worden opgeslagen.

- Vereist een waarde

#### `--document-root-is-pub`

Markering om te tonen is dat Pub zich op de hoofdmap bevindt, kan alleen waar of onwaar zijn

- Vereist een waarde

#### `--backpressure-logger`

Handler voor achtergronddruklogger

- Vereist een waarde

#### `--backpressure-logger-redis-server`

Redis-server

- Vereist een waarde

#### `--backpressure-logger-redis-port`

Redis-poort voor luisteren naar server

- Vereist een waarde

#### `--backpressure-logger-redis-timeout`

Time-out bij opnieuw verzonden server

- Vereist een waarde

#### `--backpressure-logger-redis-persistent`

Redis persistent

- Vereist een waarde

#### `--backpressure-logger-redis-db`

Redis db-nummer

- Vereist een waarde

#### `--backpressure-logger-redis-password`

Wachtwoord voor opnieuw verzonden server

- Vereist een waarde

#### `--backpressure-logger-redis-user`

Redis-servergebruiker

- Vereist een waarde

#### `--backpressure-logger-id-prefix`

ID-voorvoegsel voor toetsen

- Vereist een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:db-data:upgrade`

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

Hiermee installeert en verbetert u gegevens in de database

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:db-declaration:generate-patch`

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

Patch genereren en in specifieke map plaatsen.

### Argumenten

#### `module`

Modulenaam

- Vereist


#### `patch`

Patchnaam

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--revertable`

Controleer of de patch teruggedraaid kan worden.

- Standaard: `false`
- Accepteert een waarde

#### `--type`

Ontdek welk type patch moet worden gegenereerd. Beschikbare waarden: `data`, `schema` .

- Standaard: `data`
- Accepteert een waarde


## `setup:db-declaration:generate-whitelist`

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

Een whitelist genereren van tabellen en kolommen die door het installatieprogramma van de declaratie mogen worden bewerkt

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--module-name`

Naam van de module waar whitelist wordt gegenereerd

- Standaard: `all`
- Accepteert een waarde


## `setup:db-schema:add-slave`

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Aan een betalingsaanhalingsteken gerelateerde tabellen verplaatsen naar een aparte databaseserver

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--host`

Slave DB Server-host

- Standaard: `localhost`
- Vereist een waarde

#### `--dbname`

Naam slave-database

- Vereist een waarde

#### `--username`

Gebruikersnaam slave DB

- Standaard: `root`
- Vereist een waarde

#### `--password`

Wachtwoord slave DB

- Accepteert een waarde

#### `--connection`

Naam slave-verbinding

- Standaard: `default`
- Accepteert een waarde

#### `--resource`

Naam slave-bron

- Standaard: `default`
- Accepteert een waarde

#### `--maxAllowedLag`

Max. toegestane lave-verbinding voor lave (in seconden)

- Standaard: &quot;
- Accepteert een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:db-schema:split-quote`

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Verplaats de aan uitchecken gerelateerde tabellen naar een aparte DB-server. Vervangen vanaf 2.4.2 en verwijderd

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--host`

Uitchecken DB Server-host

- Vereist een waarde

#### `--dbname`

Database-naam uitchecken

- Vereist een waarde

#### `--username`

Gebruikersnaam database voor uitchecken

- Vereist een waarde

#### `--password`

Wachtwoord database voor afhandeling

- Accepteert een waarde

#### `--connection`

Verbindingsnaam uitchecken

- Standaard: `checkout`
- Accepteert een waarde

#### `--resource`

Naam van resource voor uitchecken

- Standaard: `checkout`
- Accepteert een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:db-schema:split-sales`

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Verplaats verkoopgerelateerde tabellen naar een aparte DB-server. Vervangen vanaf 2.4.2 en verwijderd

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--host`

Verkoop DB Server-host

- Vereist een waarde

#### `--dbname`

Naam verkoopdatabase

- Vereist een waarde

#### `--username`

Gebruikersnaam verkoopdatabase

- Vereist een waarde

#### `--password`

Gebruikerswachtwoord verkoopdatabase

- Accepteert een waarde

#### `--connection`

Naam van verkoopverbinding

- Standaard: `sales`
- Accepteert een waarde

#### `--resource`

Naam verkoopbron

- Standaard: `sales`
- Accepteert een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:db-schema:upgrade`

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installeert en verbetert het schema van DB

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--convert-old-scripts`

Hiermee kunt u oude scripts (InstallSchema, UpgradeSchema) converteren naar de indeling db_schema.xml

- Standaard: `false`
- Accepteert een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:db:status`

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

Controleert of het schema of de gegevens van DB verbetering vereisen

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:di:compile`

```bash
bin/magento setup:di:compile
```

Genereert DI-configuratie en alle ontbrekende klassen die automatisch kunnen worden gegenereerd

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `setup:install`

```bash
bin/magento setup:install [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--config-async CONFIG-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-retries SESSION-SAVE-REDIS-RETRIES] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-backend-redis-use-lua CACHE-BACKEND-REDIS-USE-LUA] [--cache-backend-redis-use-lua-on-gc CACHE-BACKEND-REDIS-USE-LUA-ON-GC] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

De Magento-toepassing installeren

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--remote-storage-driver`

Extern opslagstuurprogramma

- Vereist een waarde

#### `--remote-storage-prefix`

Voorvoegsel voor externe opslag

- Standaard: &quot;
- Vereist een waarde

#### `--remote-storage-endpoint`

Extern opslageindpunt

- Vereist een waarde

#### `--remote-storage-bucket`

Externe opslagemmer

- Vereist een waarde

#### `--remote-storage-region`

Externe opslagregio

- Vereist een waarde

#### `--remote-storage-key`

Toegangstoets externe opslag

- Standaard: &quot;
- Vereist een waarde

#### `--remote-storage-secret`

Sleutel voor geheim opslagruimte

- Standaard: &quot;
- Vereist een waarde

#### `--remote-storage-path-style`

Padstijl voor externe opslag

- Standaard: `0`
- Vereist een waarde

#### `--backend-frontname`

Backend frontname (wordt automatisch gegenereerd als deze ontbreekt)

- Vereist een waarde

#### `--enable-debug-logging`

Foutopsporingsregistratie inschakelen

- Vereist een waarde

#### `--enable-syslog-logging`

syslog inschakelen

- Vereist een waarde

#### `--id_salt`

GraphQl Salt

- Vereist een waarde

#### `--checkout-async`

Afwisselende orderverwerking inschakelen? 1 - Ja, 0 - Nee

- Vereist een waarde

#### `--config-async`

Opslaan van asynchrone beheerconfiguratie inschakelen? 1 - Ja, 0 - Nee

- Vereist een waarde

#### `--amqp-host`

Amqp-serverhost

- Standaard: &quot;
- Vereist een waarde

#### `--amqp-port`

Amqp-serverpoort

- Standaard: `5672`
- Vereist een waarde

#### `--amqp-user`

Gebruikersnaam Amqp-server

- Standaard: &quot;
- Vereist een waarde

#### `--amqp-password`

Wachtwoord Amqp-server

- Standaard: &quot;
- Vereist een waarde

#### `--amqp-virtualhost`

AMQP virtualhost

- Standaard: `/`
- Vereist een waarde

#### `--amqp-ssl`

Amqp SSL

- Standaard: &quot;
- Vereist een waarde

#### `--amqp-ssl-options`

Amqp SSL-opties (JSON)

- Standaard: &quot;
- Vereist een waarde

#### `--consumers-wait-for-messages`

Moeten consumenten wachten op een bericht uit de wachtrij? 1 - Ja, 0 - Nee

- Vereist een waarde

#### `--queue-default-connection`

Standaardverbinding in wachtrij met berichten. Kan &#39;db&#39;, &#39;amqp&#39; of een aangepast wachtrijsysteem zijn. Het wachtrijsysteem moet worden geïnstalleerd en geconfigureerd, anders worden de berichten niet correct verwerkt.

- Vereist een waarde

#### `--deferred-total-calculating`

Uitgestelde totale berekening inschakelen? 1 - Ja, 0 - Nee

- Vereist een waarde

#### `--key`

Versleutelingssleutel

- Vereist een waarde

#### `--db-host`

Host databaseserver

- Vereist een waarde

#### `--db-name`

Databasenaam

- Vereist een waarde

#### `--db-user`

Gebruikersnaam databaseserver

- Vereist een waarde

#### `--db-engine`

Database-server-engine

- Vereist een waarde

#### `--db-password`

Wachtwoord databaseserver

- Vereist een waarde

#### `--db-prefix`

Voorvoegsel databasetabel

- Vereist een waarde

#### `--db-model`

Databasetype

- Vereist een waarde

#### `--db-init-statements`

Eerste set opdrachten database

- Vereist een waarde

#### `--skip-db-validation`, `-s`

Indien opgegeven, wordt de db-verbindingsvalidatie overgeslagen

- Standaard: `false`
- Accepteert geen waarde

#### `--http-cache-hosts`

http-cachehosts

- Vereist een waarde

#### `--db-ssl-key`

Volledig pad van clientsleutelbestand om een databaseverbinding tot stand te brengen via SSL

- Standaard: &quot;
- Vereist een waarde

#### `--db-ssl-cert`

Volledig pad van clientcertificaatbestand om een databaseverbinding tot stand te brengen via SSL

- Standaard: &quot;
- Vereist een waarde

#### `--db-ssl-ca`

Volledig pad van servercertificaatbestand om een databaseverbinding tot stand te brengen via SSL

- Standaard: &quot;
- Vereist een waarde

#### `--db-ssl-verify`

Servercertificering controleren

- Standaard: `false`
- Accepteert geen waarde

#### `--session-save`

Sessieopslaghandler

- Vereist een waarde

#### `--session-save-redis-host`

Volledig - gekwalificeerde gastheernaam, IP adres, of absolute weg als het gebruiken van de contactdozen van UNIX

- Vereist een waarde

#### `--session-save-redis-port`

Redis-poort voor luisteren naar server

- Vereist een waarde

#### `--session-save-redis-password`

Wachtwoord voor opnieuw verzonden server

- Vereist een waarde

#### `--session-save-redis-timeout`

Time-out verbinding, in seconden

- Vereist een waarde

#### `--session-save-redis-retries`

Opnieuw wordt verbinding opnieuw geprobeerd.

- Vereist een waarde

#### `--session-save-redis-persistent-id`

Unieke tekenreeks om permanente verbindingen in te schakelen

- Vereist een waarde

#### `--session-save-redis-db`

Databasenummer van Redis

- Vereist een waarde

#### `--session-save-redis-compression-threshold`

Compressiedrempel opnieuw instellen

- Vereist een waarde

#### `--session-save-redis-compression-lib`

Compressiebibliotheek opnieuw uitschakelen. Waarden: gzip (standaardwaarde), lzf, lz4, snappy

- Vereist een waarde

#### `--session-save-redis-log-level`

Opnieuw schijflogniveau. Waarden: 0 (minst uitgebreid) tot 7 (meest uitgebreide)

- Vereist een waarde

#### `--session-save-redis-max-concurrency`

Maximum aantal processen dat op een slot op één zitting kan wachten

- Vereist een waarde

#### `--session-save-redis-break-after-frontend`

Aantal seconden dat moet worden gewacht voordat wordt geprobeerd een vergrendeling voor een frontendsessie te verbreken

- Vereist een waarde

#### `--session-save-redis-break-after-adminhtml`

Aantal seconden dat moet worden gewacht voordat wordt geprobeerd een vergrendeling voor beheersessie te verbreken

- Vereist een waarde

#### `--session-save-redis-first-lifetime`

Levensduur, in seconden, van sessie voor niet-bots bij eerste schrijven (gebruik 0 om uit te schakelen)

- Vereist een waarde

#### `--session-save-redis-bot-first-lifetime`

Levensduur, in seconden, van sessie voor bots bij de eerste schrijfbewerking (gebruik 0 om uit te schakelen)

- Vereist een waarde

#### `--session-save-redis-bot-lifetime`

De levensduur van de sessie voor bots bij volgende schrijvingen (gebruik 0 om uit te schakelen)

- Vereist een waarde

#### `--session-save-redis-disable-locking`

Schakel vergrendeling opnieuw uit. Waarden: false (standaardwaarde), true

- Vereist een waarde

#### `--session-save-redis-min-lifetime`

Standaardsessielevensduur van Redis, in seconden

- Vereist een waarde

#### `--session-save-redis-max-lifetime`

Maximale sessielevensduur van Redis, in seconden

- Vereist een waarde

#### `--session-save-redis-sentinel-master`

Redis Sentinel Master

- Vereist een waarde

#### `--session-save-redis-sentinel-servers`

Redis Sentinel-servers, gescheiden door komma&#39;s

- Vereist een waarde

#### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verify master. Waarden: false (standaardwaarde), true

- Vereist een waarde

#### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel verbindt opnieuw pogingen.

- Vereist een waarde

#### `--cache-backend`

Standaardcachehandler

- Vereist een waarde

#### `--cache-backend-redis-server`

Redis-server

- Vereist een waarde

#### `--cache-backend-redis-db`

Databasenummer voor de cache

- Vereist een waarde

#### `--cache-backend-redis-port`

Redis-poort voor luisteren naar server

- Vereist een waarde

#### `--cache-backend-redis-password`

Wachtwoord voor opnieuw verzonden server

- Vereist een waarde

#### `--cache-backend-redis-compress-data`

Instellen op 0 om compressie uit te schakelen (standaard is 1, ingeschakeld)

- Vereist een waarde

#### `--cache-backend-redis-compression-lib`

Compressiellib om [ snappy, lzf, l4z, zstd, gzip ] te gebruiken (verlaten leeg om automatisch te bepalen)

- Vereist een waarde

#### `--cache-backend-redis-use-lua`

Ingesteld op 1 om lua in te schakelen (standaardwaarde is 0, uitgeschakeld)

- Vereist een waarde

#### `--cache-backend-redis-use-lua-on-gc`

Ingesteld op 0 om lua uit te schakelen bij opschonen (standaard is 1, ingeschakeld)

- Vereist een waarde

#### `--cache-id-prefix`

ID-voorvoegsel voor cachesleutels

- Vereist een waarde

#### `--allow-parallel-generation`

Genereren van cache op een niet-blokkerende manier toestaan

- Standaard: `false`
- Accepteert geen waarde

#### `--page-cache`

Standaardcachehandler

- Vereist een waarde

#### `--page-cache-redis-server`

Redis-server

- Vereist een waarde

#### `--page-cache-redis-db`

Databasenummer voor de cache

- Vereist een waarde

#### `--page-cache-redis-port`

Redis-poort voor luisteren naar server

- Vereist een waarde

#### `--page-cache-redis-password`

Wachtwoord voor opnieuw verzonden server

- Vereist een waarde

#### `--page-cache-redis-compress-data`

Ingesteld op 1 om de cache van de volledige pagina te comprimeren (gebruik 0 om uit te schakelen)

- Vereist een waarde

#### `--page-cache-redis-compression-lib`

De bibliotheek van de compressie om [ snappy, lzf, l4z, zstd, gzip ] te gebruiken (verlaten leeg om automatisch te bepalen)

- Vereist een waarde

#### `--page-cache-id-prefix`

ID-voorvoegsel voor cachesleutels

- Vereist een waarde

#### `--lock-provider`

Naam provider vergrendelen

- Vereist een waarde

#### `--lock-db-prefix`

Installatiespecifiek vergrendelingsvoorvoegsel om vergrendelingsconflicten te voorkomen

- Vereist een waarde

#### `--lock-zookeeper-host`

Host en poort voor verbinding met Zookeeper-cluster. Bijvoorbeeld: 127.0.0.1:2181

- Vereist een waarde

#### `--lock-zookeeper-path`

Het pad waar Zookeeper vergrendelingen opslaat. Het standaardpad is: /magento/locks

- Vereist een waarde

#### `--lock-file-path`

Het pad waar de bestandsvergrendelingen worden opgeslagen.

- Vereist een waarde

#### `--document-root-is-pub`

Markering om te tonen is dat Pub zich op de hoofdmap bevindt, kan alleen waar of onwaar zijn

- Vereist een waarde

#### `--backpressure-logger`

Handler voor achtergronddruklogger

- Vereist een waarde

#### `--backpressure-logger-redis-server`

Redis-server

- Vereist een waarde

#### `--backpressure-logger-redis-port`

Redis-poort voor luisteren naar server

- Vereist een waarde

#### `--backpressure-logger-redis-timeout`

Time-out bij opnieuw verzonden server

- Vereist een waarde

#### `--backpressure-logger-redis-persistent`

Redis persistent

- Vereist een waarde

#### `--backpressure-logger-redis-db`

Redis db-nummer

- Vereist een waarde

#### `--backpressure-logger-redis-password`

Wachtwoord voor opnieuw verzonden server

- Vereist een waarde

#### `--backpressure-logger-redis-user`

Redis-servergebruiker

- Vereist een waarde

#### `--backpressure-logger-id-prefix`

ID-voorvoegsel voor toetsen

- Vereist een waarde

#### `--base-url`

URL waar de winkel beschikbaar moet zijn. Vervangen, gebruik config :set met weg web/unsecure/base_url

- Vereist een waarde

#### `--language`

Standaardtaalcode. Vervangen, gebruiks config :set met weg algemeen/scène/code

- Vereist een waarde

#### `--timezone`

Standaardtijdzonecode. Vervangen, gebruiks config :set met weg algemeen/scène/timezone

- Vereist een waarde

#### `--currency`

Standaardvalutacode. Vervangen, gebruiks config :set met weg valuta/opties/basis, munt/opties/gebrek en munt/opties/allow

- Vereist een waarde

#### `--use-rewrites`

Herschrijven gebruiken. Vervangen, gebruik config :set met weg web/seo/use_rewrites

- Vereist een waarde

#### `--use-secure`

Gebruik veilige URL&#39;s. Schakel deze optie alleen in als SSL beschikbaar is. Vervangen, gebruik config :set met weg web/secure/use_in_frontend

- Vereist een waarde

#### `--base-url-secure`

Basis-URL voor SSL-verbinding Vervangen, gebruik config :set met weg web/secure/base_url

- Vereist een waarde

#### `--use-secure-admin`

Voer de beheerdersinterface uit met SSL. Vervangen, gebruik config :set met weg web/secure/use_in_adminhtml

- Vereist een waarde

#### `--admin-use-security-key`

Of een functie &#39;beveiligingssleutel&#39; moet worden gebruikt in Magento Admin URL&#39;s en formulieren. Vervangen, gebruik config :set met weg admin/security/use_form_key

- Vereist een waarde

#### `--admin-user`

Admin user

- Accepteert een waarde

#### `--admin-password`

Wachtwoord beheerder

- Accepteert een waarde

#### `--admin-email`

E-mailadres beheerder

- Accepteert een waarde

#### `--admin-firstname`

Voornaam beheerder

- Accepteert een waarde

#### `--admin-lastname`

Achternaam beheerder

- Accepteert een waarde

#### `--search-engine`

Zoekprogramma. Waarden: elasticsearch8, openssearch

- Vereist een waarde

#### `--elasticsearch-host`

Elasticsearch-serverhost.

- Vereist een waarde

#### `--elasticsearch-port`

Elasticsearch-serverpoort.

- Vereist een waarde

#### `--elasticsearch-enable-auth`

Stel dit in op 1 om verificatie in te schakelen. (standaardwaarde is 0, uitgeschakeld)

- Vereist een waarde

#### `--elasticsearch-username`

Elasticsearch gebruikersnaam. Alleen van toepassing als HTTP-auth is ingeschakeld

- Vereist een waarde

#### `--elasticsearch-password`

Elasticsearch-wachtwoord. Alleen van toepassing als HTTP-auth is ingeschakeld

- Vereist een waarde

#### `--elasticsearch-index-prefix`

Elasticsearch-indexvoorvoegsel.

- Vereist een waarde

#### `--elasticsearch-timeout`

Time-out Elasticsearch-server.

- Vereist een waarde

#### `--opensearch-host`

OpenSearch-serverhost.

- Vereist een waarde

#### `--opensearch-port`

OpenSearch-serverpoort.

- Vereist een waarde

#### `--opensearch-enable-auth`

Stel dit in op 1 om verificatie in te schakelen. (standaardwaarde is 0, uitgeschakeld)

- Vereist een waarde

#### `--opensearch-username`

OpenSearch gebruikersnaam. Alleen van toepassing als HTTP-auth is ingeschakeld

- Vereist een waarde

#### `--opensearch-password`

Wachtwoord voor OpenSearch. Alleen van toepassing als HTTP-auth is ingeschakeld

- Vereist een waarde

#### `--opensearch-index-prefix`

Prefix van de OpenSearch-index.

- Vereist een waarde

#### `--opensearch-timeout`

Time-out van OpenSearch-server.

- Vereist een waarde

#### `--cleanup-database`

De database opschonen voordat deze wordt geïnstalleerd

- Standaard: `false`
- Accepteert geen waarde

#### `--sales-order-increment-prefix`

Prefix van het inkoopordernummer

- Vereist een waarde

#### `--use-sample-data`

Voorbeeldgegevens gebruiken

- Standaard: `false`
- Accepteert geen waarde

#### `--enable-modules`

Lijst met door komma&#39;s gescheiden modulenamen. Dat moet tijdens de installatie worden opgenomen. Beschikbaar magische param &quot;all&quot;.

- Accepteert een waarde

#### `--disable-modules`

Lijst met door komma&#39;s gescheiden modulenamen. Dat moet tijdens de installatie worden voorkomen. Beschikbaar magische param &quot;all&quot;.

- Accepteert een waarde

#### `--convert-old-scripts`

Hiermee kunt u oude scripts (InstallSchema, UpgradeSchema) converteren naar de indeling db_schema.xml

- Standaard: `false`
- Accepteert een waarde

#### `--interactive`, `-i`

Interactieve Magento-installatie

- Standaard: `false`
- Accepteert geen waarde

#### `--safe-mode`

Veilige installatie van Magento met dumps bij destructieve bewerkingen, zoals het verwijderen van kolommen

- Accepteert een waarde

#### `--data-restore`

Verwijderde gegevens van dumps herstellen

- Accepteert een waarde

#### `--dry-run`

Magento Installation will be run in dry-run mode

- Standaard: `false`
- Accepteert een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:performance:generate-fixtures`

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

Genereert correcties

### Argumenten

#### `profile`

Pad naar profielconfiguratiebestand

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--skip-reindex`, `-s`

Herindexeren overslaan

- Standaard: `false`
- Accepteert geen waarde


## `setup:rollback`

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Hiermee wordt de Magento Application-codebase, -media en -database teruggedraaid

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--code-file`, `-c`

Basisnaam van het back-upbestand van de code in var/back-ups

- Vereist een waarde

#### `--media-file`, `-m`

Basisnaam van het back-upbestand van het medium in var/back-ups

- Vereist een waarde

#### `--db-file`, `-d`

Basename van het db reservedossier in var/steunen

- Vereist een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:static-content:deploy`

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

Statische weergavebestanden gebruiken

### Argumenten

#### `languages`

Lijst met door spaties gescheiden ISO-639-taalcodes waarvoor statische weergavebestanden moeten worden uitgevoerd.

- Standaard: `[]`
- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--force`, `-f`

Bestanden in elke modus implementeren.

- Standaard: `false`
- Accepteert geen waarde

#### `--strategy`, `-s`

Bestanden implementeren met behulp van de opgegeven strategie.

- Standaard: `quick`
- Accepteert een waarde

#### `--area`, `-a`

Alleen bestanden genereren voor de opgegeven gebieden.

- Standaard: `all`
- Accepteert meerdere waarden

#### `--exclude-area`

Genereer geen bestanden voor de opgegeven gebieden.

- Standaard: `none`
- Accepteert meerdere waarden

#### `--theme`, `-t`

Genereer statische weergavebestanden voor alleen de opgegeven thema&#39;s.

- Standaard: `all`
- Accepteert meerdere waarden

#### `--exclude-theme`

Geen bestanden voor de opgegeven thema&#39;s genereren.

- Standaard: `none`
- Accepteert meerdere waarden

#### `--language`, `-l`

Genereer bestanden alleen voor de opgegeven talen.

- Standaard: `all`
- Accepteert meerdere waarden

#### `--exclude-language`

Genereer geen bestanden voor de opgegeven talen.

- Standaard: `none`
- Accepteert meerdere waarden

#### `--jobs`, `-j`

Schakel parallelle verwerking in met het opgegeven aantal taken.

- Standaard: `0`
- Accepteert een waarde

#### `--max-execution-time`

De maximale verwachte uitvoeringstijd van implementatie statisch proces (in seconden).

- Standaard: `900`
- Accepteert een waarde

#### `--symlink-locale`

Creeer symlinks voor de dossiers van die scènes, die voor plaatsing worden overgegaan, maar geen aanpassingen hebben.

- Standaard: `false`
- Accepteert geen waarde

#### `--content-version`

Aangepaste versie van statische inhoud kan worden gebruikt als implementatie op meerdere knooppunten wordt uitgevoerd om ervoor te zorgen dat de versie van statische inhoud identiek is en dat caching correct werkt.

- Vereist een waarde

#### `--refresh-content-version-only`

Als u de versie van statische inhoud alleen vernieuwt, kunt u statische inhoud in de browsercache en CDN-cache vernieuwen.

- Standaard: `false`
- Accepteert geen waarde

#### `--no-javascript`

Implementeer geen JavaScript-bestanden.

- Standaard: `false`
- Accepteert geen waarde

#### `--no-js-bundle`

Implementeer geen JavaScript-bundelbestanden.

- Standaard: `false`
- Accepteert geen waarde

#### `--no-css`

CSS-bestanden niet implementeren.

- Standaard: `false`
- Accepteert geen waarde

#### `--no-less`

Implementeer geen LESS-bestanden.

- Standaard: `false`
- Accepteert geen waarde

#### `--no-images`

Implementeer geen afbeeldingen.

- Standaard: `false`
- Accepteert geen waarde

#### `--no-fonts`

Implementeer geen lettertypebestanden.

- Standaard: `false`
- Accepteert geen waarde

#### `--no-html`

Implementeer geen HTML-bestanden.

- Standaard: `false`
- Accepteert geen waarde

#### `--no-misc`

Implementeer geen bestanden van andere typen (.md, .jbf, .csv, enz.).

- Standaard: `false`
- Accepteert geen waarde

#### `--no-html-minify`

Maak geen minieme HTML-bestanden.

- Standaard: `false`
- Accepteert geen waarde

#### `--no-parent`

Bovenliggende thema&#39;s niet compileren. Alleen ondersteund in snelle en standaardstrategieën.

- Standaard: `false`
- Accepteert geen waarde


## `setup:store-config:set`

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Installeert de opslagconfiguratie. Vervangen vanaf 2.2.0. In plaats hiervan config :set gebruiken

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--base-url`

URL waar de winkel beschikbaar moet zijn. Vervangen, gebruik config :set met weg web/unsecure/base_url

- Vereist een waarde

#### `--language`

Standaardtaalcode. Vervangen, gebruiks config :set met weg algemeen/scène/code

- Vereist een waarde

#### `--timezone`

Standaardtijdzonecode. Vervangen, gebruiks config :set met weg algemeen/scène/timezone

- Vereist een waarde

#### `--currency`

Standaardvalutacode. Vervangen, gebruiks config :set met weg valuta/opties/basis, munt/opties/gebrek en munt/opties/allow

- Vereist een waarde

#### `--use-rewrites`

Herschrijven gebruiken. Vervangen, gebruik config :set met weg web/seo/use_rewrites

- Vereist een waarde

#### `--use-secure`

Gebruik veilige URL&#39;s. Schakel deze optie alleen in als SSL beschikbaar is. Vervangen, gebruik config :set met weg web/secure/use_in_frontend

- Vereist een waarde

#### `--base-url-secure`

Basis-URL voor SSL-verbinding Vervangen, gebruik config :set met weg web/secure/base_url

- Vereist een waarde

#### `--use-secure-admin`

Voer de beheerdersinterface uit met SSL. Vervangen, gebruik config :set met weg web/secure/use_in_adminhtml

- Vereist een waarde

#### `--admin-use-security-key`

Of een functie &#39;beveiligingssleutel&#39; moet worden gebruikt in Magento Admin URL&#39;s en formulieren. Vervangen, gebruik config :set met weg admin/security/use_form_key

- Vereist een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:uninstall`

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

De Magento-toepassing wordt verwijderd

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `setup:upgrade`

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

Hiermee worden de Magento-toepassing, DB-gegevens en het schema bijgewerkt

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--keep-generated`

Voorkomt dat gegenereerde bestanden worden verwijderd. We raden u af deze optie te gebruiken, behalve wanneer u een product gaat maken. Raadpleeg de systeemontwikkelaar of beheerder voor meer informatie.

- Standaard: `false`
- Accepteert geen waarde

#### `--convert-old-scripts`

Hiermee kunt u oude scripts (InstallSchema, UpgradeSchema) converteren naar de indeling db_schema.xml

- Standaard: `false`
- Accepteert een waarde

#### `--safe-mode`

Veilige installatie van Magento met dumps bij destructieve bewerkingen, zoals het verwijderen van kolommen

- Accepteert een waarde

#### `--data-restore`

Verwijderde gegevens van dumps herstellen

- Accepteert een waarde

#### `--dry-run`

Magento Installation will be run in dry-run mode

- Standaard: `false`
- Accepteert een waarde

#### `--magento-init-params`

Voeg aan om het even welk bevel toe om de initialisatieparameters van Magento bijvoorbeeld aan te passen: &quot;MAGE_MODE=developer&amp;MAGE_DIRS [ basis ][path]=/var/www/example.com&amp;MAGE_DIRS [ geheime voorgeheugen ][path]=/var/tmp/cache&quot;

- Vereist een waarde


## `store:list`

```bash
bin/magento store:list
```

Hiermee wordt de lijst met winkels weergegeven

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `store:website:list`

```bash
bin/magento store:website:list
```

De lijst met websites weergeven

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `support:backup:code`

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

Codeback-up maken

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--name`

Dumpingnaam

- Accepteert een waarde

#### `--output`, `-o`

Uitvoerpad

- Accepteert een waarde

#### `--logs`, `-l`

Logbestanden opnemen

- Standaard: `false`
- Accepteert geen waarde


## `support:backup:db`

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

DB-back-up maken

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--name`

Dumpingnaam

- Accepteert een waarde

#### `--output`, `-o`

Uitvoerpad

- Accepteert een waarde

#### `--logs`, `-l`

Logbestanden opnemen

- Standaard: `false`
- Accepteert geen waarde

#### `--ignore-sanitize`, `-i`

ontsmetten negeren

- Standaard: `false`
- Accepteert geen waarde


## `support:utility:check`

```bash
bin/magento support:utility:check [--hide-paths]
```

Vereiste back-uphulpprogramma&#39;s controleren

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--hide-paths`

Alleen vereiste consolehulpprogramma&#39;s controleren

- Standaard: `false`
- Accepteert geen waarde


## `support:utility:paths`

```bash
bin/magento support:utility:paths [-f|--force]
```

Lijst met paden voor hulpprogramma&#39;s maken

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--force`, `-f`

Kracht

- Standaard: `false`
- Accepteert geen waarde


## `theme:uninstall`

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

Thema wordt verwijderd

### Argumenten

#### `theme`

Pad van het thema. Het themapad moet worden opgegeven als een volledig pad dat gebied/leverancier/naam is. Voorkant/Magento/blank

- Standaard: `[]`
- Vereist

- Array

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--backup-code`

Back-up van code maken (behalve tijdelijke bestanden)

- Standaard: `false`
- Accepteert geen waarde

#### `--clear-static-content`, `-c`

Gegenereerde statische weergavebestanden wissen.

- Standaard: `false`
- Accepteert geen waarde


## `varnish:vcl:generate`

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--input-file INPUT-FILE] [--output-file OUTPUT-FILE]
```

Genereert Varnish VCL en echo het aan de bevellijn

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--access-list`

IPs toegangslijst die Varnish kan zuiveren

- Standaard: `localhost`
- Vereist een waarde

#### `--backend-host`

Host van de webinhoud

- Standaard: `localhost`
- Vereist een waarde

#### `--backend-port`

Poort van de webinhoud

- Standaard: `8080`
- Vereist een waarde

#### `--export-version`

De versie van het Varnish-bestand

- Standaard: `6`
- Vereist een waarde

#### `--grace-period`

Respijtperiode in seconden

- Standaard: `300`
- Vereist een waarde

#### `--input-file`

Invoerbestand dat vcl genereert van

- Vereist een waarde

#### `--output-file`

Pad naar het bestand om vcl te schrijven

- Vereist een waarde


## `webhooks:dev:run`

```bash
bin/magento webhooks:dev:run <name> <payload>
```

Voert een geregistreerde webhaak uit voor ontwikkelingsdoeleinden.

### Argumenten

#### `name`

Webhaak-naam

- Vereist


#### `payload`

De payload van de webhaak in JSON-indeling

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `webhooks:generate:module`

```bash
bin/magento webhooks:generate:module
```

Insteekmodules genereren op basis van webharegistraties

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `webhooks:info`

```bash
bin/magento webhooks:info [--depth [DEPTH]] [--] <webhook-name> [<webhook-type>]
```

Retourneert de lading van de opgegeven webhaak.

### Argumenten

#### `webhook-name`

Naam van de methode WebHaak

- Vereist


#### `webhook-type`

Het type Webhaak (voor, na)

- Standaard: `before`

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).

#### `--depth`

Het aantal niveaus in de WebHaakshlading om terug te keren

- Standaard: `3`
- Accepteert een waarde


## `webhooks:list`

```bash
bin/magento webhooks:list
```

Lijst met geabonneerde websites weergeven

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).


## `webhooks:list:all`

```bash
bin/magento webhooks:list:all <module_name>
```

Hiermee wordt een lijst geretourneerd met ondersteunde webhaakmethodenamen voor de opgegeven module

### Argumenten

#### `module_name`

Modulenaam

- Vereist

### Opties

Voor globale opties, zie [&#x200B; Globale opties &#x200B;](#global-options).
