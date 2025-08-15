---
title: L2-cacheconfiguratie
description: Leer om het L2 geheime voorgeheugen te vormen.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: ba3c656566af47f16f58f476d7bc9f4781bb0234
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# L2-cacheconfiguratie

Het in cache plaatsen maakt het mogelijk het netwerkverkeer tussen de externe cacheopslag en de Commerce-toepassing te verminderen. Een standaard Commerce-instantie brengt ongeveer 300 kB per aanvraag over en het verkeer kan in sommige situaties snel toenemen tot meer dan ~1000 verzoeken.

Als u de netwerkbandbreedte voor Redis wilt verminderen, slaat u cachegegevens lokaal op elk webknooppunt op en gebruikt u de externe cache voor twee doeleinden:

- Controleer de versie van de cachegegevens en zorg ervoor dat de nieuwste cache lokaal wordt opgeslagen
- De nieuwste cache overbrengen van de externe computer naar de lokale computer

Commerce slaat de gehakte gegevensversie in Redis op, met het achtervoegsel &quot;:hash&quot;toegevoegd aan de regelmatige sleutel. Als er een verouderde lokale cache is, worden de gegevens overgebracht naar de lokale computer met een cacheadapter.

>[!INFO]
>
>Voor Adobe Commerce op wolkeninfrastructuur, kunt u [ gebruiken stelt variabelen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=nl-NL#redis_backend) voor L2 geheim voorgeheugenconfiguratie op.

## Voorbeeld van configuratie

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

Adobe raadt u aan Redis te gebruiken voor externe caching (`\Magento\Framework\Cache\Backend\Redis`) en `Cm_Cache_Backend_File` voor het lokaal in cache plaatsen van gegevens in gedeeld geheugen, met: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe raadt het gebruik van de functie [`cache preload`](redis-pg-cache.md#redis-preload-feature) aan, omdat deze de druk op Redis drastisch verlaagt. Vergeet niet om het achtervoegsel &quot;:hash&quot;voor preload sleutels toe te voegen.

## Cacheopties voor stijl

Vanaf [!DNL Commerce] 2.4 kan de optie `use_stale_cache` in bepaalde gevallen de prestaties verbeteren.

Over het algemeen, is de handel-off met vergrendelingswachten aanvaardbaar van de prestatieskant, maar groter het aantal Blokken of Geheime voorgeheugen de handelaar heeft, meer tijd wordt besteed die op sloten wacht. In sommige scenario&#39;s, kunt u a **aantallen sleutels** \* **raadplegingstijd** hoeveelheid tijd voor het proces wachten. In sommige zeldzame gevallen kan de handelaar honderden sleutels in het `Block/Config` geheime voorgeheugen hebben, zodat zelfs kleine raadplegingstijd voor slot seconden kan kosten.

Stale cache werkt alleen met een L2-cache. Met een verouderde cache kunt u een verouderde cache verzenden, terwijl een nieuwe cache parallel wordt gegenereerd. Als u verouderde cache wilt inschakelen, voegt u `'use_stale_cache' => true` toe aan de bovenste configuratie van de L2-cache.

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
