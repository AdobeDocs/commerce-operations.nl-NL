---
title: Valkey gebruiken voor standaardcache
description: Leer Valkey te configureren als de standaardcache voor Adobe Commerce.
feature: Configuration, Cache
source-git-commit: 2891c8b2ff9cfae120d01605aad6eb543f01315d
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 0%

---

# Valkey gebruiken voor standaardcache

Commerce biedt opdrachtregelopties om de Valkey-pagina en de standaardcaching te configureren. Hoewel u caching kunt vormen door het `<Commerce-install-dir>app/etc/env.php` dossier uit te geven, is het gebruiken van de bevellijn de geadviseerde methode, vooral voor aanvankelijke configuraties. De bevellijn verstrekt bevestiging, die de configuratie verzekeren syntactisch correct is.

U moet [ Valkey ](config-redis.md#install-redis) installeren alvorens verder te gaan.

## Standaardcaching voor sleutels configureren

Voer de opdracht `setup:config:set` uit en geef parameters op voor het standaard in cache plaatsen van Valkey.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` schakelt de standaardcaching voor sleutels in. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--cache-backend-valkey-<parameter>=<value>` is een lijst van zeer belangrijk-waardeparen die het gebrek caching vormen:

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van `127.0.0.1` geeft aan dat Valkey is geïnstalleerd op de Commerce-server. | `127.0.0.1` |
| `cache-backend-valkey-port` | poort | Luisterpoort Valkey-server | `6379` |
| `cache-backend-valkey-db` | database | Vereist als u Valkey gebruikt voor zowel het standaard als volledig-paginacachegeheugen. U moet het databasenummer opgeven van een van de caches; de andere cache gebruikt standaard `0` .<br><br>**Belangrijk**: Als u Valkey voor meer dan één type van caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. Adobe raadt u aan het standaard cachedatabasenummer aan `0` toe te wijzen, het databasenummer voor het in cache plaatsen van pagina&#39;s in te stellen op `1` en het databasenummer voor de sessieopslag op `2` . | `0` |
| `cache-backend-valkey-password` | password | Wanneer u een wachtwoord voor Valkey configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de opdracht `auth` , waarvoor clients moeten worden geverifieerd voor toegang tot de database. Het wachtwoord is rechtstreeks geconfigureerd in het configuratiebestand van Valkey: `/etc/valkey/valkey.conf` | |

### Voorbeeld, opdracht

In het volgende voorbeeld wordt standaard het in cache plaatsen van Valkey ingeschakeld, wordt de host ingesteld op `127.0.0.1` en wordt het databasenummer toegewezen aan `0` . Valkey gebruikt standaardwaarden voor alle andere parameters.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

## Pagina in cache plaatsen configureren

Als u het in cache plaatsen van Valkey-pagina op Commerce wilt configureren, voert u de opdracht `setup:config:set` uit met extra parameters.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Met de volgende parameters:

- `--page-cache=valkey` schakelt het in cache plaatsen van geldige pagina&#39;s in. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--page-cache-valkey-<parameter>=<value>` is een lijst van sleutel-en-waardeparen die pagina in het voorgeheugen onderbrengen vormen:

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van `127.0.0.1` geeft aan dat Valkey is geïnstalleerd op de Commerce-server. | `127.0.0.1` |
| `page-cache-valkey-port` | poort | De luisterpoort van de Valkey-server. | `6379` |
| `page-cache-valkey-db` | database | Vereist als u Valkey gebruikt voor zowel standaard als volledig-paginacache. U moet het databasenummer opgeven van een van de caches; de andere cache gebruikt standaard `0` .<br/>**Belangrijk**: Als u Valkey voor meer dan één type van caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaarddatabasenummer voor caching toe te wijzen aan `0` , het databasenummer voor het in cache plaatsen van pagina&#39;s aan `1` en het databasenummer voor sessieopslag aan `2` . | `0` |
| `page-cache-valkey-password` | password | Wanneer u een wachtwoord voor Valkey configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de opdracht `auth` , waarvoor clients moeten worden geverifieerd voor toegang tot de database. Configureer het wachtwoord in het configuratiebestand Valkey: `/etc/valkey/valkey.conf` | |

### Voorbeeld, opdracht

In het volgende voorbeeld wordt het in cache plaatsen van Valkey-pagina ingeschakeld, wordt de host ingesteld op `127.0.0.1` en wordt het databasenummer toegewezen aan `1` . Alle andere parameters worden ingesteld op de standaardwaarde.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

## Resultaten

Als resultaat van de twee voorbeeldopdrachten voegt Commerce soortgelijke regels toe aan `<Commerce-install-dir>app/etc/env.php` :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

## Nieuwe Valkey-cache-implementatie

[!BADGE &#x200B; 2.4.9-alpha &#x200B;]{type=Negative tooltip="Alleen beschikbaar in 2.4.9-alfa."}

Vanaf Adobe Commerce 2.4.9 raadt Adobe aan de Valkey-cache-implementatie te gebruiken: `\Magento\Framework\Cache\Backend\Valkey` .

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Functie Voorladen van Valkey

Aangezien Commerce configuratiegegevens opslaat in de cache van Valkey, kunt u vooraf gegevens laden die opnieuw worden gebruikt tussen pagina&#39;s. Als u toetsen wilt zoeken die vooraf moeten worden geladen, analyseert u de gegevens die van Valkey naar Commerce worden overgebracht. Adobe stelt voor om gegevens die op elke pagina worden geladen, zoals `SYSTEM_DEFAULT` , `EAV_ENTITY_TYPES` en `DB_IS_UP_TO_DATE` , vooraf te laden.

Valkey gebruikt `pipeline` voor samengestelde laadaanvragen. Toetsen moeten het databasevoorvoegsel bevatten. Als het databasevoorvoegsel bijvoorbeeld `061_` is, ziet de voorladertoets er als volgt uit: `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

Wanneer u de functie voor voorladen gebruikt met een L2-cache, moet u het achtervoegsel `:hash` aan de toetsen toevoegen. Het L2 geheime voorgeheugen brengt slechts de knoeiboel van de gegevens over, niet de daadwerkelijke gegevens.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Parallelle generatie

Vanaf de Commerce 2.4.0-release heeft Adobe de optie `allow_parallel_generation` geïntroduceerd voor gebruikers die wachten op vergrendelingen willen elimineren.
Deze functie is standaard uitgeschakeld en Adobe raadt u aan deze uit te schakelen totdat u te veel configuraties en/of blokken hebt.

**om parallelle generatie** toe te laten:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Aangezien het een vlag is, kunt u het met een bevel niet onbruikbaar maken. U moet de configuratiewaarde handmatig instellen op `false` :

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

## Valkeyverbinding verifiëren

Als u wilt controleren of Valkey en Commerce goed samenwerken, meldt u zich aan bij de server waarop Valkey wordt uitgevoerd, opent u een terminal en gebruikt u de opdracht `valkey-cli monitor` of `redis-cli ping` .

### Valkey, opdracht

```bash
valkey-cli monitor
```

Voorbeeld van uitvoer in cache plaatsen van pagina:

```
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Valkey, ping, opdracht

```bash
redis-cli ping
```

De verwachte reactie is: `PONG`

Als beide opdrachten zijn uitgevoerd, wordt Valkey op de juiste wijze ingesteld.

### Gecomprimeerde gegevens controleren

Om samengeperste zittingsgegevens en het paginacachegeheugen te inspecteren, [ RESP.app ](https://flathub.org/apps/app.resp.RESP) steunt automatische decompressie van Commerce 2 zitting en paginacache en toont PHP zittingsgegevens in een mens-leesbaar formaat.
