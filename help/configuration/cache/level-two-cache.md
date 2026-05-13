---
title: L2 Cache Configuration for Performance Optimization
description: Leer hoe u de L2-cache in Adobe Commerce configureert om netwerkverkeer te beperken en de prestaties te verbeteren. Ontdek de implementatieopties voor verouderde en Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: 605b2e59d200bc8eeab43e91006a3f95e6a6c138
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 0%

---

# L2-cacheconfiguratie voor optimalisatie van prestaties

L2 (twee-vlakke) caching vermindert netwerkverkeer tussen de verre geheim voorgeheugenopslag (Redis of Valkey) en de toepassing van Commerce door een lokale geheim voorgeheugenlaag op elke Webknoop toe te voegen. Een standaard Commerce-instantie brengt ongeveer 300 kB per aanvraag over en het verkeer kan in sommige situaties snel toenemen tot meer dan 1000 verzoeken.

Met L2 caching, slaat elke Webknoop vaak betreden gegevens plaatselijk op en gebruikt het verre geheime voorgeheugen voor twee doeleinden:

- De versie van de cachegegevens controleren om te controleren of de nieuwste cache lokaal is opgeslagen
- Bijgewerkte cachegegevens van de externe opslagruimte overbrengen naar de lokale computer

Commerce slaat de versie van de gehashte gegevens op in de externe cache, waarbij het achtervoegsel `:hash` aan de gewone sleutel wordt toegevoegd. Wanneer de lokale cache verouderd is, worden de gegevens opgehaald van de externe computer via een cacheadapter.

Er zijn twee beschikbare L2 geheim voorgeheugenimplementaties:

| Implementatie | Versie | Beschrijving |
| -------------- | ------- | ----------- |
| [ Verouderd (`RemoteSynchronizedCache`) ](#legacy-l2-cache-configuration-remotesynchronizedcache) | 2,4 x | Cache van twee niveaus met `Cm_Cache_Backend_File` de waarde Zend voor lokale opslag |
| [ Modern (`symfony_l2`) ](#modern-symfony-l2-cache-implementation) | 2.4.9+ | Symfony op cache gebaseerde L2 met PSR-6-compatibiliteit en verbeterde prestaties |

>[!INFO]
>
>Voor Adobe Commerce op wolkeninfrastructuur, kunt u [ gebruiken stelt variabelen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) voor L2 geheim voorgeheugenconfiguratie op.

## Verouderde L2-cacheconfiguratie (RemoteSynchronizedCache)

In het volgende voorbeeld kunt u de bestaande cachesectie in het `app/etc/env.php` -bestand wijzigen of vervangen.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

Waarbij:

- `backend` is de L2 cache-implementatie.
- `backend_options` is de L2-cacheconfiguratie.
   - `remote_backend` is de implementatie van de externe cache: Redis of MySQL.
   - `remote_backend_options` is de configuratie van de externe cache.
   - `local_backend` is de lokale cache-implementatie: `Cm_Cache_Backend_File`
   - `local_backend_options` is de lokale cacheconfiguratie.
   - `cache_dir` is een bestandcache-specifieke optie voor de map waarin de lokale cache is opgeslagen.

Adobe raadt u aan Redis te gebruiken voor externe caching (`\Magento\Framework\Cache\Backend\Redis`) en `Cm_Cache_Backend_File` voor het lokaal in cache plaatsen van gegevens in gedeeld geheugen, door: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe raadt het gebruik van de functie [`cache preload`](redis-pg-cache.md#redis-preload-feature) aan, omdat deze de druk op Redis drastisch verlaagt. Vergeet niet om het achtervoegsel &quot;:hash&quot;voor preload sleutels toe te voegen.

## Cacheopties voor stijl

Vanaf Commerce 2.4 kunt u met de optie `use_stale_cache` de prestaties in specifieke gevallen verbeteren door eerder in de cache opgeslagen gegevens te verzenden terwijl nieuwe cachegegevens parallel worden gegenereerd.

Over het algemeen is de afweging met vergrendelingswachttijden acceptabel vanuit het oogpunt van prestaties. Nochtans, aangezien het aantal blokken of geheim voorgeheugeningangen groeit, neemt het slot meer tijd. In sommige scenario&#39;s, wacht kan tot **het aantal sleutels** x **raadplegingonderbreking** voor het proces zijn. In zeldzame gevallen kan een handelaar honderden sleutels in het `Block/Config` geheime voorgeheugen hebben, zodat zelfs een kleine raadplegingstijd voor een slot seconden kan kosten.

>[!IMPORTANT]
>
>Stale cache werkt alleen met L2-cache. Als u dit wilt inschakelen, voegt u `'use_stale_cache' => true` toe aan de configuratie op hoofdniveau van de voorkant van de L2-cache.

Adobe raadt aan de optie `use_stale_cache` alleen in te schakelen voor cachetypen die er het meest van profiteren, zoals:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe raadt u niet aan de optie `use_stale_cache` voor het cachetype `default` in te schakelen.

De volgende code toont een voorbeeldconfiguratie:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => true,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled']
    ],
],
```

## Moderne implementatie van Symfony L2-cache

[!BADGE  2.4.9-bèta ]{type=Negative tooltip="Alleen beschikbaar in bèta-2.4.9."}

Vanaf Commerce 2.4.9 kunt u de Symfony Cache-gebaseerde L2 cache-implementatie (`symfony_l2` backend) gebruiken, die een moderne, PSR-6-compatibele caching-implementatie biedt met aanzienlijke prestatieverbeteringen ten opzichte van de traditionele `RemoteSynchronizedCache` .

### Voordelen van Symfony L2 cache

- **Moderne Architectuur**: Gebaseerd op onderdelen van de Symfony Cache (compatibel met PSR-6)
- **Betere Prestaties**: Native ondersteuning voor Igbinary-serialisatie, gzip-compressie en Lua-scripts
- **Blijvende Verbindingen**: Vermindert Redis of Valkey verbindingsoverheadkosten met verbinding het groeperen
- **preload Sleutels**: Ondersteunt het vooraf laden van de cache-sleutel voor kritieke gegevens
- **de Steun van het Geheime voorgeheugen van de Vergroting**: Volledige compatibiliteit met de optie `use_stale_cache`
- **Vereenvoudigde Configuratie**: Cleaner backend type names (`redis` , `valkey`, `file`)

### Voorbeeld van configuratie met Symfony L2-cache

Gebruik het vereenvoudigde `symfony_l2` backend type voor L2 cache:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Redis with Symfony Cache
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### Symfony L2-cache met verouderde cache

Afzonderlijke voorkanten configureren voor ondersteuning van verouderde cache:

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'redis',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Achtergrondopties voor Symfony L2-cache

| Optie | Type | Standaard | Beschrijving |
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | string | `'redis'` | Type externe back-end: `redis` , `valkey` of `file` |
| `remote_backend_options` | array | `[]` | Externe back-endconfiguratie (zie de documentatie van Redis/Valkey) |
| `local_backend` | string | `'file'` | Lokaal type backend: `file` of `apcu` |
| `local_backend_options` | array | `[]` | Lokale back-endconfiguratie |
| `cleanup_percentage` | integer | `90` | L1-cache opschoondrempel (1-100) |
| `use_stale_cache` | boolean | `false` | Ophaalcache inschakelen voor hoge beschikbaarheid |

### Ondersteuning voor Valkey

De `symfony_l2` backend ondersteunt ook Valkey als de externe backend:

```php
'backend_options' => [
    'remote_backend' => 'valkey',  // Use Valkey instead of Redis
    'remote_backend_options' => [
        'server' => 'localhost',
        'database' => '0',
        'port' => '6379',
        'serializer' => 'igbinary',
        'compression_lib' => 'gzip',
    ],
    // ... rest of configuration
]
```

Voor gedetailleerde configuratieopties, zie:
- [Opnieuw cacheconfiguratie met Symfony Cache](redis-pg-cache.md)
- [Valkey-cacheconfiguratie met Symfony Cache](valkey-pg-cache.md)
