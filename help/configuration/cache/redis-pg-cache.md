---
title: Redis gebruiken voor standaardcache
description: Leer hoe u Redis configureert als de standaardcache voor Adobe Commerce. Ontdek opdrachtregelopstelling, configuratieopties en validatietechnieken.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: ee4a873a73e8fd747e7d4c8e157327fab1074cc9
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# Redis gebruiken voor standaardcache

Commerce biedt opdrachtregelopties voor het configureren van de pagina Redis en het in cache plaatsen van standaardgegevens. Hoewel u caching kunt vormen door het `<Commerce-install-dir>app/etc/env.php` dossier uit te geven, is het gebruiken van de bevellijn de geadviseerde methode, vooral voor aanvankelijke configuraties. De bevellijn verstrekt bevestiging, die de configuratie verzekeren syntactisch correct is.

U moet [&#x200B; Redis &#x200B;](config-redis.md#install-redis) installeren alvorens verder te gaan.

>[!NOTE]
>
>Voor Commerce-instanties die worden gehost op EC2, kunt u AWS ElastiCache gebruiken in plaats van een lokale Redis-instantie. Zie [&#x200B; Elasticache voor instanties EC2 &#x200B;](redis-elasticache-for-ec2.md) vormen.

## Standaardcaching van Redis configureren

Voer de opdracht `setup:config:set` uit en geef parameters op die specifiek zijn voor de standaardcaching Redis.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Met de volgende parameters:

- `--cache-backend=redis` schakelt de standaardopmaak van Redis in. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--cache-backend-redis-<parameter>=<value>` is een lijst van sleutel-en-waardeparen die het gebrek in het voorgeheugen onderbrengen vormen:

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van 127.0.0.1 geeft aan dat Redis is geïnstalleerd op de Commerce-server. | `127.0.0.1` |
| `cache-backend-redis-port` | poort | Redis-poort voor luisteren naar server | `6379` |
| `cache-backend-redis-db` | database | Vereist als u Redis gebruikt voor zowel de standaardcache als de cache van de volledige pagina. U moet het databasenummer van een van de caches opgeven; de andere cache gebruikt standaard 0.<br><br>**Belangrijk**: Als u Redis voor meer dan één type van caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaard cachedatabasenummer aan 0, het databasenummer voor het in cache plaatsen van pagina&#39;s aan 1 en het databasenummer voor de sessieopslag aan 2 toe te wijzen. | `0` |
| `cache-backend-redis-password` | password | Als u een Redis-wachtwoord configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de opdracht `auth` , waarvoor clients moeten worden geverifieerd voor toegang tot de database. Het wachtwoord wordt rechtstreeks geconfigureerd in het configuratiebestand van Redis: `/etc/redis/redis.conf` | |
| `--cache-backend-redis-use-lua` | use_lua | LUA in- of uitschakelen. <br><br>**LUA**: Lua laat ons toe om een deel van de toepassingslogica binnen Redis in werking te stellen, die prestaties verbeteren en gegevensconsistentie door zijn atomische uitvoering verzekeren. | `0` |
| `--cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Schakel LUA in of uit voor opschonen. <br><br>**LUA**: Lua laat ons toe om een deel van de toepassingslogica binnen Redis in werking te stellen, die prestaties verbeteren en gegevensconsistentie door zijn atomische uitvoering verzekeren. | `1` |

### Voorbeeld, opdracht

In het volgende voorbeeld wordt de standaardcaching Redis ingeschakeld, wordt de host ingesteld op `127.0.0.1` en wordt het databasenummer toegewezen aan 0. Redis gebruikt standaardwaarden voor alle andere parameters.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Pagina&#39;s opnieuw weergeven in cache plaatsen

Als u het in cache plaatsen van pagina&#39;s opnieuw wilt configureren op Commerce, voert u de opdracht `setup:config:set` uit met extra parameters.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Met de volgende parameters:

- `--page-cache=redis` schakelt het in cache plaatsen van pagina&#39;s opnieuw uit. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--page-cache-redis-<parameter>=<value>` is een lijst van sleutel-en-waardeparen die pagina in het voorgeheugen onderbrengen vormen:

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van 127.0.0.1 geeft aan dat Redis is geïnstalleerd op de Commerce-server. | `127.0.0.1` |
| `page-cache-redis-port` | poort | Redis-poort voor luisteren naar server | `6379` |
| `page-cache-redis-db` | database | Vereist als u Redis gebruikt voor zowel de standaardcache als de volledige paginacache. U moet het databasenummer van een van de caches opgeven; de andere cache gebruikt standaard 0.<br/>**Belangrijk**: Als u Redis voor meer dan één type van caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaard cachedatabasenummer aan 0, het databasenummer voor het in cache plaatsen van pagina&#39;s aan 1 en het databasenummer voor de sessieopslag aan 2 toe te wijzen. | `0` |
| `page-cache-redis-password` | password | Als u een Redis-wachtwoord configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de opdracht `auth` , waarvoor clients moeten worden geverifieerd voor toegang tot de database. Configureer het wachtwoord in het Redis-configuratiebestand: `/etc/redis/redis.conf` | |

### Voorbeeld, opdracht

In het volgende voorbeeld wordt het in cache plaatsen van pagina&#39;s opnieuw verzonden ingeschakeld, wordt de host ingesteld op `127.0.0.1` en wordt het databasenummer toegewezen aan 1. Alle andere parameters worden ingesteld op de standaardwaarde.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Commerce-omgevingsconfiguratie controleren

Als u de opdrachten uitvoert om het in cache plaatsen van Redis te configureren, wordt de Commerce-omgevingsconfiguratie (`<Commerce-install-dir>app/etc/env.php`) bijgewerkt:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
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

## Aanvullende opties voor caching configureren

In deze sectie wordt beschreven hoe u optionele configuratie-instellingen kunt inschakelen die standaard zijn uitgeschakeld.

### Redis, functie voor vooraf laden

Aangezien Commerce configuratiegegevens opslaat in de cache van Redis, kunnen we gegevens vooraf laden die opnieuw worden gebruikt tussen pagina&#39;s. Als u toetsen wilt zoeken die vooraf moeten worden geladen, analyseert u de gegevens die van Redis naar Commerce worden overgedragen. We raden u aan gegevens die op elke pagina worden geladen, bijvoorbeeld `SYSTEM_DEFAULT` , `EAV_ENTITY_TYPES` , `DB_IS_UP_TO_DATE` vooraf te laden.

Redis gebruikt `pipeline` om aanvragen voor samengestelde laden samen te stellen. Toetsen moeten het databasevoorvoegsel bevatten; als het databasevoorvoegsel bijvoorbeeld `061_` is, ziet de voorladertoets er als volgt uit: `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
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

Als u de functie voor voorladen gebruikt met de L2-cache, vergeet dan niet het achtervoegsel `:hash` aan uw sleutels toe te voegen, aangezien L2-cache alleen de hash van de gegevens overbrengt, niet de gegevens zelf:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### Parallelle generatie

Schakel de optie `allow_parallel_generation` in om het wachten op vergrendelingen te elimineren.

Deze optie is standaard uitgeschakeld en Adobe raadt u aan de optie uit te schakelen totdat u een groot aantal configuraties of blokken hebt.

**om parallelle generatie** toe te laten:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Aangezien deze optie een vlag is, kunt u het met een bevel niet onbruikbaar maken. U moet de configuratiewaarde handmatig instellen op `false` :

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
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

## De Redis-verbinding controleren

Om te verifiëren dat Redis en Commerce samenwerken, login aan de server die Redis in werking stelt, een terminal openen, en Redis monitorbevel gebruiken of pingel bevel.

### Redis-monitor, opdracht

```bash
redis-cli monitor
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

### Redis, ping, opdracht

```bash
redis-cli ping
```

De verwachte reactie is: `PONG`

Als beide opdrachten zijn uitgevoerd, wordt Redis op de juiste wijze ingesteld.

### Gecomprimeerde gegevens controleren

Om de samengeperste gegevens van de Zitting en het Geheime voorgeheugen van de Pagina te inspecteren, [&#x200B; RESP.app &#x200B;](https://flathub.org/apps/details/app.resp.RESP) steunt de automatische decompressie van Commerce 2 Sessie en het geheime voorgeheugen van de Pagina en toont PHP zittingsgegevens in een mens-leesbare vorm.
