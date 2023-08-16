---
title: L2-cacheconfiguratie
description: Leer om het L2 geheime voorgeheugen te vormen.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# L2-cacheconfiguratie

Caching laat een vermindering in netwerkverkeer tussen de verre geheim voorgeheugenopslag en de toepassing van de Handel toe. Een standaardinstantie van de Handel brengt ongeveer 300 kb per verzoek over, en het verkeer kan snel aan meer dan ~1000 verzoeken in sommige situaties groeien.

Als u de netwerkbandbreedte voor Redis wilt verminderen, slaat u cachegegevens lokaal op elk webknooppunt op en gebruikt u de externe cache voor twee doeleinden:

- Controleer de versie van de cachegegevens en zorg ervoor dat de nieuwste cache lokaal wordt opgeslagen
- De nieuwste cache overbrengen van de externe computer naar de lokale computer

De handel slaat de gehakte gegevensversie in Redis op, met achtervoegsel &quot;:hash&quot;toegevoegd aan de regelmatige sleutel. Als er een verouderde lokale cache is, worden de gegevens overgebracht naar de lokale computer met een cacheadapter.

>[!INFO]
>
>Voor Adobe Commerce op cloudinfrastructuur kunt u [variabelen implementeren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) voor L2 cacheconfiguratie.

## Voorbeeld van configuratie

In het volgende voorbeeld kunt u de bestaande cachesectie in het dialoogvenster `app/etc/env.php` bestand.

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
                ],
                'use_stale_cache' => false,
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

- `backend` is de L2 geheim voorgeheugenimplementatie.
- `backend_options` is de L2 geheim voorgeheugenconfiguratie.
   - `remote_backend` is de implementatie van de externe cache: Redis of MySQL.
   - `remote_backend_options` is de externe cacheconfiguratie.
   - `local_backend` is de lokale geheim voorgeheugenimplementatie: `Cm_Cache_Backend_File`
   - `local_backend_options` is de lokale geheim voorgeheugenconfiguratie.
      - `cache_dir` is een bestandcache-specifieke optie voor de map waarin de lokale cache is opgeslagen.
   - `use_stale_cache` is een vlag die het gebruik van het geheime voorgeheugen van de waliteit toelaat of onbruikbaar maakt.

Adobe raadt aan Redis te gebruiken voor externe caching (`\Magento\Framework\Cache\Backend\Redis`) en `Cm_Cache_Backend_File` voor de lokale caching van gegevens in gedeeld geheugen, die gebruiken: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe beveelt het gebruik van de [`cache preload`](redis-pg-cache.md#redis-preload-feature) Deze functie heeft een drastische vermindering van de druk op Redis. Vergeet niet het achtervoegsel &#39;:hash&#39; toe te voegen voor toetsen die vooraf worden geladen.

## Cacheopties voor stijl

Beginnen met [!DNL Commerce] 2.4 `use_stale_cache` deze optie kan in bepaalde specifieke gevallen de prestaties verbeteren.

Over het algemeen, is de handel-off met vergrendelingswachten aanvaardbaar van de prestatieskant, maar groter het aantal Blokken of Geheime voorgeheugen de handelaar heeft, meer tijd wordt besteed die op sloten wacht. In sommige gevallen kunt u een **aantal toetsen** \* **zoektime-out** hoeveelheid tijd voor het proces. In sommige zeldzame gevallen kan de handelaar honderden sleutels in hebben `Block/Config` cache, zodat zelfs een kleine zoektime-out voor vergrendeling seconden kan kosten.

Stale cache werkt alleen met een L2-cache. Met een verouderde cache kunt u een verouderde cache verzenden, terwijl een nieuwe cache parallel wordt gegenereerd. Als u een verouderde cache wilt inschakelen, voegt u `'use_stale_cache' => true` om config van het L2 geheime voorgeheugen te hoogste.

Adobe beveelt aan de `use_stale_cache` optie alleen voor cachetypen die er het meest van profiteren, zoals:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

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
                ],
                'use_stale_cache' => false,
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
