---
title: Redis gebruiken voor standaardcache
description: Leer Redis te configureren als de standaardcache voor Adobe Commerce en Magento Open Source.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '1067'
ht-degree: 0%

---

# Redis gebruiken voor standaardcache

De handel verstrekt bevel-lijn opties om de Redis pagina en gebrek caching te vormen. Hoewel u caching kunt vormen door het uitgeven van `<Commerce-install-dir>app/etc/env.php` is de aanbevolen methode, met name voor initiële configuraties. De bevellijn verstrekt bevestiging, die de configuratie verzekeren syntactisch correct is.

U moet [Redis installeren](config-redis.md#install-redis) voordat u verdergaat.

## Standaardcaching van Redis configureren

Voer de `setup:config:set` en geef parameters op die specifiek zijn voor de standaardcaching Redis.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Met de volgende parameters:

- `--cache-backend=redis` Hiermee schakelt u de standaardcaching Redis in. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--cache-backend-redis-<parameter>=<value>` is een lijst van sleutel-en-waardeparen die het gebrek caching vormen:

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van 127.0.0.1 wijst op Redis is geïnstalleerd op de server van de Handel. | `127.0.0.1` |
| `cache-backend-redis-port` | poort | Redis-poort voor luisteren naar server | `6379` |
| `cache-backend-redis-db` | database | Vereist als u Redis gebruikt voor zowel de standaardcache als de cache van de volledige pagina. U moet het databasenummer van een van de caches opgeven. de andere cache gebruikt standaard 0.<br><br>**Belangrijk**: Als u Redis voor meer dan één type caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaard cachedatabasenummer aan 0, het databasenummer voor het in cache plaatsen van pagina&#39;s aan 1 en het databasenummer voor de sessieopslag aan 2 toe te wijzen. | `0` |
| `cache-backend-redis-password` | password | Als u een Redis-wachtwoord configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de `auth` gebruiken, waarvoor clients moeten worden geverifieerd voor toegang tot de database. Het wachtwoord wordt direct geconfigureerd in het configuratiebestand van Redis: `/etc/redis/redis.conf` |  |

### Voorbeeld, opdracht

In het volgende voorbeeld wordt de standaardcaching Redis ingeschakeld en wordt de host ingesteld op `127.0.0.1`en wijst het databasenummer toe aan 0. Redis gebruikt standaardwaarden voor alle andere parameters.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Pagina&#39;s opnieuw weergeven in cache plaatsen

Om Redis pagina caching op Handel te vormen, stel in werking `setup:config:set` gebruiken met extra parameters.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Met de volgende parameters:

- `--page-cache=redis` Hiermee schakelt u het in cache plaatsen van pagina&#39;s van Redis in. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--page-cache-redis-<parameter>=<value>` is een lijst van zeer belangrijk-en-waardeparen die pagina in het voorgeheugen onderbrengen vormen:

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van 127.0.0.1 wijst op Redis is geïnstalleerd op de server van de Handel. | `127.0.0.1` |
| `page-cache-redis-port` | poort | Redis-poort voor luisteren naar server | `6379` |
| `page-cache-redis-db` | database | Vereist als u Redis gebruikt voor zowel de standaardcache als de volledige paginacache. U moet het databasenummer van een van de caches opgeven. de andere cache gebruikt standaard 0.<br/>**Belangrijk**: Als u Redis voor meer dan één type caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaard cachedatabasenummer aan 0, het databasenummer voor het in cache plaatsen van pagina&#39;s aan 1 en het databasenummer voor de sessieopslag aan 2 toe te wijzen. | `0` |
| `page-cache-redis-password` | password | Als u een Redis-wachtwoord configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de `auth` gebruiken, waarvoor clients moeten worden geverifieerd voor toegang tot de database. Configureer het wachtwoord in het Redis-configuratiebestand: `/etc/redis/redis.conf` |  |

### Voorbeeld, opdracht

In het volgende voorbeeld wordt het in cache plaatsen van pagina&#39;s door Redis ingeschakeld. De host wordt ingesteld op `127.0.0.1`en wijst het databasenummer toe aan 1. Alle andere parameters worden ingesteld op de standaardwaarde.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Resultaten

Als resultaat van de twee voorbeeldbevelen, voegt de Handel lijnen gelijkend op het volgende aan toe `<Commerce-install-dir>app/etc/env.php`:

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

## AWS ElastiCache gebruiken met uw EC2-exemplaar

Vanaf Commerce 2.4.3 kunnen instanties die worden gehost op Amazon EC2 een AWS ElastiCache gebruiken in plaats van een lokale Redis-instantie.

>[!WARNING]
>
>Deze sectie werkt alleen voor instanties Commerce die op Amazon EC2 VPC&#39;s worden uitgevoerd. Het werkt niet voor installaties ter plaatse.

### Een Redis-cluster configureren

Na [Redis-cluster instellen op AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/), vorm de EC2 instantie om ElastiCache te gebruiken.

1. [Een ElastiCache-cluster maken](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) in dezelfde regio en VPC van de EG2-instantie.
1. Controleer de verbinding.

   - Een SSH-verbinding openen naar uw EC2-instantie
   - Installeer de Redis-client op het EC2-exemplaar:

      ```bash
      sudo apt-get install redis
      ```

   - Voeg een binnenkomende regel aan de EC2 veiligheidsgroep toe: Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Voeg een binnenkomende regel aan de ElastiCache de veiligheidsgroep van de Cluster toe: Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Verbind met Redis CLI:

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### Handel configureren om de cluster te gebruiken

De handel steunt veelvoudige types van caching configuraties. Over het algemeen worden de configuraties in cache opgedeeld tussen front-end en backend. caching aan de voorzijde is geclassificeerd als `default`, wordt gebruikt voor elk type cache. U kunt caches op een lager niveau aanpassen of splitsen voor betere prestaties. Een algemene configuratie van Redis scheidt het standaardgeheime voorgeheugen en paginacache in hun eigen Gegevensbestand van Redis (RDB).

Uitvoeren `setup` opdrachten om de eindpunten van Redis op te geven.

Om Commerce voor Redis als gebrek caching te vormen:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Om Commerce voor Redis pagina caching te vormen:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Om Commerce te vormen om Redis voor zittingsopslag te gebruiken:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Connectiviteit verifiëren

**Om te verifiëren dat de Handel met ElastiCache spreekt**:

1. Open een verbinding SSH aan de instantie van de Handel EC2.
1. Start de Redis-monitor.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Open een pagina in de interface van de Handel.
1. Controleer de [cacheuitvoer](#verify-redis-connection) in uw terminal.

## Nieuwe Redis-cacheimplementatie

Vanaf Commerce 2.3.5, wordt het geadviseerd om de uitgebreide Redis geheim voorgeheugenimplementatie te gebruiken: `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Redis, functie voor vooraf laden

Aangezien de Handel configuratiegegevens in het geheime voorgeheugen van Redis opslaat, kunnen wij gegevens vooraf laden die tussen pagina&#39;s opnieuw worden gebruikt. Om sleutels te vinden die moeten worden vooraf geladen, analyseer gegevens die van Redis aan Handel worden overgebracht. We raden aan gegevens die op elke pagina zijn geladen, vooraf te laden, zoals `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

Redis gebruikt de `pipeline` om een aanvraag voor samengestelde lading te kunnen indienen. Toetsen moeten het databasevoorvoegsel bevatten; bijvoorbeeld als het databasevoorvoegsel `061_`ziet u als volgt uit: `061_SYSTEM_DEFAULT`

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

Als u de functie voor voorladen gebruikt met de L2-cache, vergeet dan niet om de functie `:hash` het achtervoegsel aan uw sleutels, aangezien het geheime voorgeheugen L2 slechts de knoeiboel van de gegevens, niet de gegevens zelf overbrengt:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Parallelle generatie

Vanaf de 2.4.0 release introduceerden we de `allow_parallel_generation` optie voor de gebruikers die wachten voor sloten willen elimineren.
Deze functie is standaard uitgeschakeld en u wordt aangeraden deze uit te schakelen totdat u te veel configuraties en/of blokken hebt.

**Om parallelle generatie mogelijk te maken**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Aangezien het een vlag is, kunt u het met een bevel niet onbruikbaar maken. U moet de configuratiewaarde handmatig instellen op `false`:

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

## Redis-verbinding verifiëren

Om te verifiëren dat Redis en de Handel samenwerken, login aan de server die Redis in werking stelt, een terminal openen, en Redis monitorbevel gebruiken of pingel bevel.

### Redis-monitor, opdracht

```bash
redis-cli monitor
```

Voorbeeld van uitvoer in cache plaatsen van pagina:

```terminal
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

Als u gecomprimeerde sessiegegevens en paginacache wilt inspecteren, [RESP.app](https://flathub.org/apps/details/app.resp.RESP) ondersteunt de automatische decompressie van het cachegeheugen voor 2 sessies en pagina&#39;s van Handel en geeft PHP-sessiegegevens weer in een leesbare vorm.
