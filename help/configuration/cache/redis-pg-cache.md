---
title: Redis voor standaard- en paginacache configureren
description: Leer hoe u Redis configureert als de standaard- en paginacacheback voor Adobe Commerce. Ontdek CLI bevelen, env.php montages, en verbindingscontrole.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: d20f9d38a06fcd0eed872fe6f7ef1f3ee015a00f
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 0%

---

# Redis configureren voor standaard- en paginacache

Commerce biedt opdrachtregelopties voor het configureren van de pagina Redis en het in cache plaatsen van standaardgegevens. Hoewel u caching kunt vormen door het `<Commerce-install-dir>app/etc/env.php` dossier uit te geven, is de bevellijn de geadviseerde methode, vooral voor aanvankelijke configuraties. De bevellijn verstrekt bevestiging om ervoor te zorgen dat de configuratie syntactisch correct is.

**Vereiste:**

[&#x200B; installeer Redis &#x200B;](config-redis.md#install-redis) alvorens verder te gaan.

>[!NOTE]
>
>Voor Commerce-instanties die worden gehost op EC2, kunt u AWS ElastiCache gebruiken in plaats van een lokale Redis-instantie. Zie [&#x200B; Elasticache voor instanties EC2 &#x200B;](redis-elasticache-for-ec2.md) vormen.

## Ondersteunde frameworks

>[!BEGINTABS]

>[!TAB  Gebied Geheime voorgeheugen (2.4.8 en vroeger) ]

- **Geheime voorgeheugen van het Gebied (2.4.8 en vroeger)** — De achtergrond van de Oudheid Redis voor Commerce 2.4.8 en vroeger:
   - **Verouderde Redis achtergrond** - Gebruikt de volledige klassenweg (`Magento\Framework\Cache\Backend\Redis`)
   - **Preload sleutels** — Steunt het vooraf laden van vaak gebruikte geheim voorgeheugensleutels
   - **manuscripten Lua** — Lua voor huisvuilinzameling
   - **Compressie** — Steunt gegevenscompressie

>[!TAB  het Geheime voorgeheugen van de Symfony (2.4.9+) ]

- **het Geheime voorgeheugen van de Symfony (2.4.9+)** — Beginnend met Commerce 2.4.9, verstrekt het Geheime voorgeheugen van de Symfony een moderne, volgzame het in het voorgeheugen onderbrengende implementatie PSR-6 voor Redis met significante prestatiesverbeteringen:
   - **Automatisch opnieuw opent pijlt** - de veelvoudige verrichtingen van batterijen in enige verzoeken, die latentie verminderen
   - **PSR-6 TagAwareAdapter** — Efficiënte op markering-gebaseerde geheim voorgeheugenbevestiging met atomische verrichtingen
   - **Igbinary rangschikking** - de Binaire rangschikking vermindert geheim voorgeheugeningangsgrootte met 45% en verbetert snelheid door 5-10%
   - **Verbeterde blijvende verbindingen** — stabielere verbinding die met betere behandeling van verfprocessen samenvoegt
   - **Geoptimaliseerde manuscripten van Lua** — Server-zijuitvoering die met het buizen leiden voor maximumefficiency wordt gecombineerd

>[!ENDTABS]


## Standaardcaching van Redis configureren

Voer de opdracht `setup:config:set` uit en geef parameters op die specifiek zijn voor de standaardcaching Redis.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Met de volgende parameters:

- `--cache-backend=redis` schakelt de standaardopmaak van Redis in. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--cache-backend-redis-<parameter>=<value>` is een lijst van sleutel-en-waardeparen die het gebrek in het voorgeheugen onderbrengen vormen:

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van 127.0.0.1 geeft aan dat Redis is geïnstalleerd op de Commerce-server. | `127.0.0.1` |
| `cache-backend-redis-port` | poort | Redis-poort voor luisteren naar server | `6379` |
| `cache-backend-redis-db` | database | Vereist als u Redis gebruikt voor zowel de standaardcache als de cache van de volledige pagina. Geef het databasenummer van een van de cache op; het andere geheime voorgeheugen gebruikt 0 door gebrek.<br><br>**Belangrijk**: Als u Redis voor meer dan één type caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaard cachedatabasenummer aan 0, het databasenummer voor het in cache plaatsen van pagina&#39;s aan 1 en het databasenummer voor de sessieopslag aan 2 toe te wijzen. | `0` |
| `cache-backend-redis-password` | password | Als u een Redis-wachtwoord configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de opdracht `auth` , die vereist dat clients worden geverifieerd voor toegang tot de database. Het wachtwoord wordt direct geconfigureerd in het configuratiebestand van Redis: `/etc/redis/redis.conf` | |
| `cache-backend-redis-use-lua` | use_lua | Lua in- of uitschakelen. <br><br>**Lua**: Lua maakt het mogelijk om een deel van de toepassingslogica binnen Redis uit te voeren, waardoor de prestaties worden verbeterd en de consistentie van gegevens wordt gewaarborgd door middel van atomische uitvoering. | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Schakel Lua in of uit voor opschonen. <br><br>**Lua**: Lua maakt het mogelijk om een deel van de toepassingslogica binnen Redis uit te voeren, waardoor de prestaties worden verbeterd en de consistentie van gegevens wordt gewaarborgd door middel van atomische uitvoering. | `1` |

## Voorbeeld, opdracht (standaardcache)

In het volgende voorbeeld wordt de standaardcaching Redis ingeschakeld, wordt de host ingesteld op `127.0.0.1` en wordt het databasenummer toegewezen aan 0. Redis gebruikt standaardwaarden voor alle andere parameters.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Pagina&#39;s opnieuw weergeven in cache plaatsen

Als u het in cache plaatsen van pagina&#39;s opnieuw wilt configureren op Commerce, voert u de opdracht `setup:config:set` uit met extra parameters.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Met de volgende parameters:

- `--page-cache=redis` schakelt het in cache plaatsen van pagina&#39;s opnieuw uit. Laat deze parameter weg als deze functie reeds is toegelaten.

- `--page-cache-redis-<parameter>=<value>` is een lijst van sleutel-en-waardeparen die pagina in het voorgeheugen onderbrengen vormen:

| Opdrachtregelparameter | Waarde | Betekenis | Standaardwaarde |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Volledig gekwalificeerde hostnaam, IP-adres of een absoluut pad naar een UNIX-socket. De standaardwaarde van 127.0.0.1 geeft aan dat Redis is geïnstalleerd op de Commerce-server. | `127.0.0.1` |
| `page-cache-redis-port` | poort | Redis-poort voor luisteren naar server | `6379` |
| `page-cache-redis-db` | database | Vereist als u Redis gebruikt voor zowel de standaardcache als de volledige paginacache. Geef het databasenummer van een van de cache op; het andere geheime voorgeheugen gebruikt 0 door gebrek.<br/>**Belangrijk**: Als u Redis voor meer dan één type caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaard cachedatabasenummer aan 0, het databasenummer voor het in cache plaatsen van pagina&#39;s aan 1 en het databasenummer voor de sessieopslag aan 2 toe te wijzen. | `0` |
| `page-cache-redis-password` | password | Als u een Redis-wachtwoord configureert, wordt een van de ingebouwde beveiligingsfuncties ingeschakeld: de opdracht `auth` , die vereist dat clients worden geverifieerd voor toegang tot de database. Configureer het wachtwoord in het Redis-configuratiebestand: `/etc/redis/redis.conf` | |

In het volgende voorbeeld wordt het in cache plaatsen van pagina&#39;s opnieuw verzonden ingeschakeld, wordt de host ingesteld op `127.0.0.1` en wordt het databasenummer toegewezen aan `1` . Alle andere parameters worden ingesteld op de standaardwaarde.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Commerce-omgevingsconfiguratie controleren

Als u de opdrachten uitvoert om Redis caching te configureren, wordt de Commerce-omgevingsconfiguratie (`<Commerce-install-dir>app/etc/env.php`) bijgewerkt:

>[!BEGINTABS]

>[!TAB  Gebied Geheime voorgeheugen (2.4.8 en vroeger) ]

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

>[!TAB  het Geheime voorgeheugen van de Symfony (2.4.9+) ]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'redis',
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
>Vanaf Commerce 2.4.9 gebruikt u het vereenvoudigde achtergrondtype `'backend' => 'redis'` in plaats van het volledige klassenpad. Het Geheime voorgeheugen van de symfony wordt automatisch gebruikt wanneer de vereenvoudigde naam wordt gespecificeerd.

>[!ENDTABS]

## Aanvullende opties voor caching configureren

### Redis, functie voor vooraf laden

Aangezien Commerce configuratiegegevens opslaat in de cache van Redis, kunt u vooraf gegevens laden die opnieuw worden gebruikt tussen pagina&#39;s. Als u toetsen wilt zoeken die vooraf moeten worden geladen, analyseert u de gegevens die van Redis naar Commerce worden overgedragen. Adobe stelt voor om gegevens die op elke pagina worden geladen, zoals `SYSTEM_DEFAULT` , `EAV_ENTITY_TYPES` en `DB_IS_UP_TO_DATE` , vooraf te laden.

Redis gebruikt `pipeline` om aanvragen voor samengestelde lading te verwerken. Toetsen moeten het databasevoorvoegsel bevatten; Als het databasevoorvoegsel bijvoorbeeld `061_` is, ziet de voorlaadtoets er als volgt uit: `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB  Gebied Geheime voorgeheugen ]

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

>[!TAB  het Geheime voorgeheugen van de Symfony ]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'redis',
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

>[!TAB  het Geheime voorgeheugen van de Symfony ]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'redis',
                'backend_options' => [
                    'server' => 'redis',
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
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### De extensie PHP Igbinary installeren

Om igbinary serialization te gebruiken, moet u de PHP Igbinary uitbreiding installeren.

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

Blijvende verbindingen maken opnieuw gebruik van bestaande Redis-verbindingen tussen aanvragen, waardoor cachebewerkingen van 5 tot 15% sneller verlopen. Configureren in `app/etc/env.php` :

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
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
                'server' => 'redis',
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

Hier is een productie-klaar configuratie van de Symfony die alle prestatiesoptimalisering combineert:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
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

## De Redis-verbinding controleren

Om te controleren of Redis en Commerce goed samenwerken:

1. Meld u aan bij de server waarop Redis en Commerce wordt uitgevoerd.
1. Open een terminal.
1. Controleer de verbinding met de opdracht `redis-cli monitor` of `redis-cli ping` .

Als de opdrachten slagen, wordt Redis uitgevoerd en kan het communiceren met de Commerce-toepassing. Als ze falen, is er een verbindingsprobleem tussen Redis en Commerce dat u moet oplossen.

### Redis-monitor, opdracht

```shell
redis-cli monitor
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
...
```

Als beide opdrachten slagen, wordt Redis op de juiste wijze ingesteld.

### Gecomprimeerde gegevens controleren

Om samengeperste zittingsgegevens en paginacache te inspecteren, gebruik het {[&#128279;](https://flathub.org/apps/details/app.resp.RESP) hulpmiddel 0} RESP.app. Deze ondersteunt automatische decompressie van Commerce 2-sessies en cachegegevens van pagina&#39;s en geeft PHP-sessiegegevens weer in een voor mensen leesbare vorm.
