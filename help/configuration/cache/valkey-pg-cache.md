---
title: Valkey configureren voor standaard- en paginacache
description: Leer hoe u Valkey configureert als de standaard- en paginacacheback voor Adobe Commerce. Ontdek CLI bevelen, env.php montages, en verbindingscontrole.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: d20f9d38a06fcd0eed872fe6f7ef1f3ee015a00f
workflow-type: tm+mt
source-wordcount: '1262'
ht-degree: 0%

---


# Valkey configureren voor standaard- en paginacache

Commerce biedt opdrachtregelopties voor het configureren van de standaardwaarden voor Valkey en het in cache plaatsen van pagina&#39;s. Hoewel u caching kunt vormen door het `<Commerce-install-dir>app/etc/env.php` dossier uit te geven, is het gebruiken van de bevellijn de geadviseerde methode, vooral voor aanvankelijke configuraties. De bevellijn verstrekt bevestiging, die de configuratie verzekeren syntactisch correct is.

**Vereiste:**

[&#x200B; installeer Valkey &#x200B;](config-valkey.md#install-valkey) alvorens verder te gaan.

## Ondersteunde frameworks


>[!BEGINTABS]

>[!TAB  Gebied Geheime voorgeheugen (2.4.8 en vroeger) ]

- **Gebied Geheime voorgeheugen van het Gebied (2.4.8 en vroeger)** — De achtergrond van de Verouderde Valtoets voor Commerce 2.4.8 en vroeger:
   - **Verouderde Valse backend** — Gebruikt de volledige klassenweg (`Magento\Framework\Cache\Backend\Valkey`)
   - **Preload sleutels** — Steunt het vooraf laden van vaak gebruikte geheim voorgeheugensleutels
   - **manuscripten Lua** — Lua voor huisvuilinzameling
   - **Compressie** — Steunt gegevenscompressie

>[!TAB  het Geheime voorgeheugen van de Symfony (2.4.9+) ]

- **het Geheime voorgeheugen van de Symfony (2.4.9+)** — Beginnend met Commerce 2.4.9, verstrekt het Geheime voorgeheugen van de Symfony een moderne, volgzame het in het voorgeheugen onderbrengende implementatie PSR-6 voor Valkey met significante prestatiesverbeteringen:
   - **Automatische Valkey die** door buizen leidt — stapelt veelvoudige verrichtingen in enige verzoeken in, die latentie verminderen
   - **PSR-6 TagAwareAdapter** — Efficiënte op markering-gebaseerde geheim voorgeheugenbevestiging met atomische verrichtingen
   - **Igbinary rangschikking** - de Binaire rangschikking vermindert geheim voorgeheugeningangsgrootte met 45% en verbetert snelheid door 5-10%
   - **Verbeterde blijvende verbindingen** — stabielere verbinding die met betere behandeling van verfprocessen samenvoegt
   - **Geoptimaliseerde manuscripten van Lua** — Server-zijuitvoering die met het buizen leiden voor maximumefficiency wordt gecombineerd

>[!ENDTABS]

## Standaardcaching voor sleutels configureren

Voer de opdracht `setup:config:set` uit en geef parameters op voor het standaard in cache plaatsen van Valkey.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` schakelt de standaardcaching van Valkey in. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--cache-backend-valkey-<parameter>=<value>` is een lijst van zeer belangrijk-waardeparen die het gebrek caching vormen:

{{valkey-redis-cli-note}}

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van `127.0.0.1` geeft aan dat Valkey is geïnstalleerd op de Commerce-server. | `127.0.0.1` |
| `cache-backend-valkey-port` | poort | Luisterpoort Valkey-server | `6379` |
| `cache-backend-valkey-db` | database | Vereist als u Valkey gebruikt voor zowel het standaard als volledig-paginacachegeheugen. Geef het databasenummer van een van de cache op; het andere geheime voorgeheugengebruik `0` door gebrek.<br><br>**Belangrijk**: Als u Valkey voor meer dan één type caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. Adobe raadt u aan het standaard cachedatabasenummer aan `0` toe te wijzen, het databasenummer voor het in cache plaatsen van pagina&#39;s in te stellen op `1` en het databasenummer voor de sessieopslag op `2` . | `0` |
| `cache-backend-valkey-password` | password | Als u een Valkey-wachtwoord configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de opdracht `auth` , die vereist dat clients worden geverifieerd voor toegang tot de database. Het wachtwoord wordt direct gevormd in het configuratiedossier van Valkey: `/etc/valkey/valkey.conf` | |
| `cache-backend-valkey-use-lua` | use_lua | LUA in- of uitschakelen. <br><br>**LUA**: Lua stelt ons in staat om een deel van de toepassingslogica binnen Valkey uit te voeren, die prestaties verbetert en gegevensconsistentie door zijn atomische uitvoering verzekert. | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | Schakel LUA in of uit voor opschonen. <br><br>**LUA**: Lua stelt ons in staat om een deel van de toepassingslogica binnen Valkey uit te voeren, die prestaties verbetert en gegevensconsistentie door zijn atomische uitvoering verzekert. | `1` |

## Voorbeeld, opdracht (standaardcache)

In het volgende voorbeeld wordt standaard het in cache plaatsen van Valkey ingeschakeld, wordt de host ingesteld op `127.0.0.1` en wordt het databasenummer toegewezen aan `0` . Valkey gebruikt standaardwaarden voor alle andere parameters.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## Opslaan van geldige pagina&#39;s in cache configureren

Als u het in cache plaatsen van Valkey-pagina op Commerce wilt configureren, voert u de opdracht `setup:config:set` uit met extra parameters.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Met de volgende parameters:

- `--page-cache=valkey` schakelt het in cache plaatsen van geldige pagina&#39;s in. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--page-cache-valkey-<parameter>=<value>` is een lijst van sleutel-en-waardeparen die pagina in het voorgeheugen onderbrengen vormen:

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van `127.0.0.1` geeft aan dat Valkey is geïnstalleerd op de Commerce-server. | `127.0.0.1` |
| `page-cache-valkey-port` | poort | De luisterpoort van de Valkey-server. | `6379` |
| `page-cache-valkey-db` | database | Vereist als u Valkey gebruikt voor zowel standaard als volledig-paginacache. Geef het databasenummer van een van de cache op; het andere geheime voorgeheugengebruik `0` door gebrek.<br/>**Belangrijk**: Als u Valkey voor meer dan één type caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaarddatabasenummer voor caching toe te wijzen aan `0` , het databasenummer voor het in cache plaatsen van pagina&#39;s aan `1` en het databasenummer voor sessieopslag aan `2` . | `0` |
| `page-cache-valkey-password` | password | Als u een Valkey-wachtwoord configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de opdracht `auth` , die vereist dat clients worden geverifieerd voor toegang tot de database. Vorm het wachtwoord binnen het Valkey configuratiedossier: `/etc/valkey/valkey.conf` | |

### Voorbeeld, opdracht (paginacache)

In het volgende voorbeeld wordt het in cache plaatsen van Valkey-pagina ingeschakeld, wordt de host ingesteld op `127.0.0.1` en wordt het databasenummer toegewezen aan `1` . Alle andere parameters worden ingesteld op de standaardwaarde.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### Commerce-omgevingsconfiguratie controleren

Als u de opdrachten uitvoert om Valkey-caching te configureren, wordt de Commerce-omgevingsconfiguratie (`<Commerce-install-dir>app/etc/env.php`) bijgewerkt:

>[!BEGINTABS]

>[!TAB  Gebied Geheime voorgeheugen (2.4.8 en vroeger) ]

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

>[!TAB  het Geheime voorgeheugen van de Symfony (2.4.9+) ]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
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

>[!NOTE]
>
>Vanaf Commerce 2.4.9 gebruikt u het vereenvoudigde achtergrondtype `'backend' => 'valkey'` in plaats van het volledige klassenpad. Het Geheime voorgeheugen van de symfony wordt automatisch gebruikt wanneer de vereenvoudigde naam wordt gespecificeerd.

>[!ENDTABS]

## Aanvullende opties voor caching configureren

### Functie Voorladen van Valkey

Aangezien Commerce configuratiegegevens opslaat in de cache van Valkey, kunt u vooraf gegevens laden die opnieuw worden gebruikt tussen pagina&#39;s. Als u toetsen wilt zoeken die vooraf moeten worden geladen, analyseert u de gegevens die van Valkey naar Commerce worden overgebracht. Adobe stelt voor om gegevens die op elke pagina worden geladen, zoals `SYSTEM_DEFAULT` , `EAV_ENTITY_TYPES` en `DB_IS_UP_TO_DATE` , vooraf te laden.

Valkey gebruikt `pipeline` voor samengestelde laadaanvragen. Toetsen moeten het databasevoorvoegsel bevatten; Als het databasevoorvoegsel bijvoorbeeld `061_` is, ziet de voorlaadtoets er als volgt uit: `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB  Gebied Geheime voorgeheugen ]

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

>[!TAB  het Geheime voorgeheugen van de Symfony ]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'valkey',
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

>[!ENDTABS]

Wanneer u de functie voor voorladen gebruikt met een L2-cache, moet u het achtervoegsel `:hash` aan de toetsen toevoegen. Het L2 geheime voorgeheugen brengt slechts de knoeiboel van de gegevens over, niet de daadwerkelijke gegevens.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### Parallelle generatie

Vanaf de Commerce 2.4.0-release heeft Adobe de optie `allow_parallel_generation` geïntroduceerd voor gebruikers die wachten op vergrendelingen niet meer hoeven te wachten. Deze functie is standaard uitgeschakeld en Adobe raadt u aan deze uit te schakelen totdat u te veel configuraties en/of blokken hebt.

**om parallelle generatie** toe te laten:

```shell
bin/magento setup:config:set --allow-parallel-generation
```

Aangezien het een vlag is, kunt u het met een bevel niet onbruikbaar maken. Stel handmatig de configuratiewaarde in op `false` :

>[!BEGINTABS]

>[!TAB  Gebied Geheime voorgeheugen ]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
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

>[!TAB  het Geheime voorgeheugen van de Symfony ]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]

## Optimalisatie van Symfony Cache-prestaties

Als u Symfony Cache gebruikt, kunt u prestaties verder optimaliseren door de Igbinary serializer te vormen, de igbinary extensie PHP en phpredis te installeren, en blijvende verbindingen toe te laten.

### Igbinary serializer

De Igbinary serializer verstrekt significante prestatiesverbeteringen over de standaardrangschikking van PHP. Deze moet handmatig worden geconfigureerd in `app/etc/env.php` :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### De extensie PHP Igbinary installeren

Om de igbinary rangschikking te gebruiken, moet u de PHP Igbinary uitbreiding installeren.

**Gebruikend apt (geadviseerd voor Debian/Ubuntu)**:

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**Gebruikend pecl (alternatieve methode)**:

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### PHP Redis-extensies: phpredis vs Predis

Commerce 2.4.9+ bevat automatische fallback tussen phpredis (native C-extensie) en Predis (pure PHP-bibliotheek). Installeer de volgende phpredis voor optimale prestaties:

**Gebruikend apt (geadviseerd voor Debian/Ubuntu)**:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Gebruikend pecl (alternatieve methode)**:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**vergelijking van Prestaties**:

| Bewerking | Predis | phpredis | Verbetering |
|-----------|--------|----------|-------------|
| Cache GET | 1-5 ms | 0,5-2 ms | 2-3 keer sneller |
| Cacheset | 2-6 ms | 0,8 - 2,5 ms | 2-3 keer sneller |
| Tagbewerkingen | 10-30 ms | 3-10 ms | 3-4 keer sneller |

### Blijvende verbindingen

Blijvende verbindingen maken opnieuw gebruik van bestaande Valkey-verbindingen tussen verschillende aanvragen, waardoor cachebewerkingen van 5 tot 15% sneller verlopen. Configureren in `app/etc/env.php` :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>Gebruik voor elk cachetype een unieke `persistent_id` om verbindingsconflicten te voorkomen.

### Volledige geoptimaliseerde configuratie

Hier is een productie-klaar configuratie die alle prestatiesoptimalisaties combineert:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## Valkeyverbinding verifiëren

Ga als volgt te werk om te controleren of Valkey en Commerce goed samenwerken:

1. Meld u aan bij de server waarop Valkey en Commerce worden uitgevoerd.
1. Open een terminal.
1. Controleer de verbinding met de opdracht `valkey-cli monitor` of `valkey-cli ping` .

Als de opdrachten slagen, wordt Valkey uitgevoerd en kan deze communiceren met de Commerce-toepassing. Als ze mislukken, is er een verbindingsprobleem tussen Valkey en Commerce dat u moet oplossen.

### Valkey, opdracht

```shell
valkey-cli monitor
```

Voorbeeld van uitvoer in cache plaatsen van pagina:

```text
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

```shell
valkey-cli ping
```

De verwachte reactie is: `PONG`

Als beide opdrachten zijn uitgevoerd, wordt Valkey op de juiste wijze ingesteld.

### Gecomprimeerde gegevens controleren

Om samengeperste zittingsgegevens en paginacache te inspecteren, gebruik het {[&#128279;](https://flathub.org/apps/app.resp.RESP) hulpmiddel 0} RESP.app. Deze ondersteunt automatische decompressie van Commerce 2-sessies en cachegegevens van pagina&#39;s en geeft PHP-sessiegegevens weer in een voor mensen leesbare indeling.

