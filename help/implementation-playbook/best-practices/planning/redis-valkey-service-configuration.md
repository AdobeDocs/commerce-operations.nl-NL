---
title: Beste praktijken voor Redis en Valkey de Configuratie van de Dienst
description: Leer hoe u Redis en Valkey-services voor Adobe Commerce configureert. Verbeter de prestaties van caching met L2 cache, slave-verbindingen, verouderde cache en sessiescheiding.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: aedff83fe473691340f0f254e7c79ef7e632ac0d
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor Redis en Valkey-serviceconfiguratie

Gebruik deze aanbevelingen om Redis of Valkey voor Adobe Commerce caching en zittingen te vormen.

- L2-cache configureren
- Enable slave connection
- Toetsen vooraf laden
- Ophaalcache inschakelen
- Afzonderlijke cache en sessie
- De cache comprimeren
- Configuratievoorbeelden

>[!NOTE]
>
>Voor Commerce on Cloud-infrastructuuromgevingen controleert u of u de nieuwste versie van het `ece-tools` -pakket gebruikt. Als niet, [&#x200B; verbetering aan de recentste versie &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). U kunt de versie controleren die in uw lokale omgeving is geïnstalleerd met de opdracht `composer show magento/ece-tools` CLI.

## L2-cache configureren

Configureer de L2-cache door de `REDIS_BACKEND` - of `VALKEY_BACKEND` -implementatievariabele in te stellen in het `.magento.env.yaml` -configuratiebestand.

>[!BEGINTABS]

>[!TAB  herdis configuratie ]

Gebruik voor Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Voor milieuconfiguratie op de infrastructuur van de Wolk, zie [`REDIS_BACKEND` &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) configuratieverwijzing in _Commerce op de Gids van de Infrastructuur van de Wolk_.

Voor installaties op-gebouw, zie [&#x200B; Redis pagina caching &#x200B;](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) in de _Gids van de Configuratie_ vormen.

>[!TAB  Valkeyconfiguratie ]

Gebruik voor Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Voor milieuconfiguratie op wolkeninfrastructuur, zie [`VALKEY_BACKEND` &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) configuratieverwijzing in _Commerce op de Gids van de Infrastructuur van de Wolk_.

Voor installaties op-gebouw, zie [&#x200B; Valkey &#x200B;](../../../configuration/cache/config-valkey.md) in de _Gids van de Configuratie_ vormen.

>[!ENDTABS]


### Grootte L2-cachegeheugen voor Adobe Commerce Cloud

L2 geheim voorgeheugen gebruikt a [&#x200B; tijdelijk dossiersysteem &#x200B;](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) als zijn opslagmechanisme. In tegenstelling tot gespecialiseerde sleutelwaardewinkels, heeft tmpfs geen zeer belangrijk uitzettingsbeleid, zodat kan het geheugengebruik onbegrensd groeien. Om uitputting te verhinderen, ontruimt Adobe Commerce automatisch de L2 opslag wanneer het gebruik een configureerbare drempel (95% door gebrek) bereikt. U kunt het geheugengebruik beheren door een grotere `/dev/shm` hoeveelheid aan te vragen of door de opschoningsdrempel te verlagen.

Pas het maximale L2-cachegeheugengebruik aan op basis van uw projectvereisten. Gebruik een van de volgende methoden:

- Maak een ondersteuningsticket om de koppelingsgrootte van `/dev/shm` aan te passen. Voor dit scenario raadt Adobe aan de grootte van de `/dev/shm` -montage in te stellen op 15 GB.
- Pas de eigenschap `cleanup_percentage` op toepassingsniveau aan om het opslaggebruik te beperken en geheugen vrij te maken dat beschikbaar is voor andere services.
U kunt de configuratie in de plaatsingsconfiguratie onder de groep van de geheim voorgeheugenconfiguratie aanpassen `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>De `cleanup_percentage` configureerbare optie is geïntroduceerd in Adobe Commerce 2.4.4.

De volgende voorbeelden tonen de configuratiecode in het `.magento.env.yaml` dossier:

>[!BEGINTABS]

>[!TAB  herdis configuratie ]

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB  Valkeyconfiguratie ]

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!ENDTABS]

De vereisten van het geheime voorgeheugen variëren gebaseerd op uw projectconfiguratie en douanecode van de douanederde. Grootte van L2-cachegeheugen zodat de cache kan werken zonder frequente drempelwaarden te bereiken.

In het ideale geval stabiliseert het geheugengebruik van de L2-cache zich onder de drempel om te voorkomen dat de opslagruimte vaak wordt gewist.

U kunt het gebruik van het L2 geheime voorgeheugengeheugen op elke knoop van de cluster controleren door het volgende CLI bevel in werking te stellen en de `/dev/shm` lijn te herzien.

```bash
df -h /dev/shm
```

Het gebruik kan over knopen variëren, maar het zou in een gelijkaardige waarde moeten samenkomen.

## Aangepaste mappen voor L2-cache configureren

Wanneer het optimaliseren van L2 geheim voorgeheugenprestaties, kunt u verkiezen om de lokale geheim voorgeheugendossiers in een douane, krachtige folder, zoals een schijf van RAM op te slaan (`/dev/shm/`).

Voor consistentie in de hele toepassing en om gefragmenteerde cacheopslag te voorkomen, configureert u zowel de specifieke L2-backendopties als het algemene directoryregister in het `app/etc/env.php` -bestand.

**Beste praktijken:** bepaal zowel `local_backend_options['cache_dir']` als globaal `directories['cache']['path']`.

- **`local_backend_options['cache_dir']`**: hiermee stuurt u de cacheadapter voor de back-end (bijvoorbeeld `Cm_Cache_Backend_File` ) naar de gesynchroniseerde L2-cachebestanden op de opgegeven locatie.
- **`directories['cache']['path']`**: werkt het Adobe Commerce `DirectoryList` -register bij en stelt het aangepaste pad in als de definitieve systeemcachemap voor de gehele toepassing.

### Meten van gesplitste cachemappen en GlusterFS-segmentatiefouten voorkomen

Als u het aangepaste pad uitsluitend definieert in de `local_backend_options` , werkt de L2-cache-engine correct, maar blijft het algemene toepassingsregister `var/cache` herkennen als de standaardcachelocatie.

Deze configuratiestoornis resulteert in een &quot;split-brain&quot; scenario waarbij externe extensies of kernfallback-processen tijdelijke bestanden naar de standaardmap `var/cache` schrijven.

**Kritieke Gevolgen voor de Wolk van de Handel van Adobe:** Op Pro architectuur, wordt de `var/` folder opgezet op een gedeeld verdeeld dossiersysteem. Dwingend hoog-snelheidsgeheime voorgeheugen I/O over dit netwerk overweldigt de cliënt en is een primaire trekker voor **GlusterFS segmentatiefouten en cluster-brede stroomonderbrekingen**. Als u beide instellingen configureert, blijft alle I/O-cache volledig op de lokale, krachtige schijf staan.

### Voorbeeld van configuratie

Als u één, verenigde cachemap wilt afdwingen, werkt u het `env.php` -bestand bij en voegt u beide configuraties in:

```php
return [
    // 1. Override the global directory registry
    'directories' => [
        'cache' => [
            'path' => '/dev/shm/magento_cache'
        ]
    ],
    // 2. Configure the L2 cache engine
    'cache' => [
        'frontend' => [
            'default' => [
                'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
                'backend_options' => [
                    'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                    'server' => '127.0.0.1',
                    'port' => '6379',
                    'database' => '1',
                    // ... other redis configurations ...
                    'local_backend' => 'Cm_Cache_Backend_File',
                    'local_backend_options' => [
                        'cache_dir' => '/dev/shm/magento_cache' 
                    ]
                ]
            ]
        ]
    ],
    // ...
];
```

## Enable slave connection

Schakel de slave-verbinding in het `.magento.env.yaml` -bestand in als u wilt dat Adobe Commerce een extra alleen-lezen cacheverbinding gebruikt voor lezen terwijl het primaire eindpunt voor schrijven wordt gebruikt. Deze configuratie kan leesbelasting op de primaire cacheservice verminderen en leesverkeer effectiever distribueren.

>[!BEGINTABS]

>[!TAB  herdis configuratie ]

Gebruik voor Redis:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Voor milieuconfiguratie op de infrastructuur van Commerce Cloud, zie [&#x200B; REDIS_USE_SLAVE_CONNECTION &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) in _Commerce op de Gids van de Infrastructuur van de Wolk_.

Voor Adobe Commerce-installaties op locatie configureert u de nieuwe Redis-casimplementatie met de opdrachten `bin/magento setup` . Zie [&#x200B; Redis van het Gebruik voor standaardgeheime voorgeheugen &#x200B;](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) in de _Gids van de Configuratie_.

>[!TAB  Valkeyconfiguratie ]

Gebruik voor Valkey:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Voor milieuconfiguratie op de infrastructuur van Commerce Cloud, zie [&#x200B; VALKEY_USE_SLAVE_CONNECTION &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection) in _Commerce op de Gids van de Infrastructuur van de Wolk_.

Voor Adobe Commerce-installaties op locatie configureert u de nieuwe Valkey-casimplementatie met behulp van de `bin/magento setup` -opdrachten. Zie [&#x200B; Valkey &#x200B;](../../../configuration/cache/config-valkey.md) in de _Gids van de Configuratie_ vormen.

>[!ENDTABS]

## Toetsen vooraf laden

Magento laadt cachemarangen doorgaans één voor één uit Redis of Valkey. Met de functie voor vooraf laden kunt u een lijst met veelgebruikte sleutels opgeven die Magento in één pijpleiding ophaalt bij eerste toegang tijdens een aanvraag. Magento bewaart vervolgens de opgehaalde waarden in het PHP-geheugen voor de rest van dat verzoek, waardoor herhaalde ronde reizen naar Redis of Valkey worden gereduceerd en de opstartprestaties van deze toetsen worden verbeterd.

U kunt veelgebruikte toetsen identificeren door actieve opdrachten op Redis of Valkey te controleren:

>[!BEGINTABS]

>[!TAB  herstelt preload zeer belangrijke configuratie ]

De vooraf te laden sleutels worden gevormd in het `.magento.env.yaml` configuratiedossier.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Voer de volgende opdracht uit om de toetsen weer te geven:

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Druk na 10 seconden op **[!UICONTROL Ctrl+C]** . Voer vervolgens de volgende opdracht uit:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

In dit logbestand worden de toetsen weergegeven die u vooraf kunt laden. Voer de volgende opdracht uit om de inhoud van een toets weer te geven:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

Voor installaties op-gebouw, zie [&#x200B; Redis preload eigenschap &#x200B;](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) in de _Gids van de Configuratie_.

>[!TAB  Valkey preload zeer belangrijke configuratie ]

De vooraf te laden sleutels worden gevormd in het `.magento.env.yaml` configuratiedossier.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Voer de volgende opdracht uit om de toetsen weer te geven:

```terminal
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Druk na 10 seconden op **[!UICONTROL Ctrl+C]** . Voer vervolgens de volgende opdracht uit:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

In dit logbestand worden de toetsen weergegeven die u vooraf kunt laden. Voer de volgende opdracht uit om de inhoud van een toets weer te geven:

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

Voor installaties op-gebouw, zie [&#x200B; Valkey preload eigenschap &#x200B;](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) in de _Gids van de Configuratie_.

>[!ENDTABS]

## Ophaalcache inschakelen

Stale cache is een L2 cache-functie van `RemoteSynchronizedCache`. Als deze optie is ingeschakeld, kan Adobe Commerce vanaf `/dev/shm` een bestaande lokale cachewaarde gebruiken, terwijl een ander verzoek al dezelfde vermelding opnieuw genereert in plaats van dat elke gelijktijdige aanvraag wacht. Hiermee vermindert u cachestempels en vergrendelt u conflicten tijdens het opnieuw genereren van dure cachegegevens.

### Hoe werkt het

Met `RemoteSynchronizedCache` bewaart Magento twee exemplaren van elke cachevermelding: een lokale kopie in `/dev/shm` en een externe kopie in Redis of Valkey. Wanneer de externe kopie niet beschikbaar is en er al een regeneratievergrendeling voor die sleutel bestaat, kunnen gelijktijdige aanvragen de vorige lokale waarde ontvangen in plaats van te wachten tot de nieuwe waarde is geschreven.

Als u verouderde cache wilt inschakelen, configureert u deze in het `.magento.env.yaml` -bestand.

>[!BEGINTABS]

>[!TAB  vorm stapelgeheime voorgeheugen voor Redis ]

Voor Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!TAB  vorm stapelgeheime voorgeheugen voor Valkey ]

Voor Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>Het `full_page` geheim voorgeheugentype is niet relevant voor Adobe Commerce op de infrastructuurprojecten van de Wolk omdat zij [&#x200B; Fastly &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/cdn/fastly) gebruiken.

Voor installaties op-gebouw, zie [&#x200B; het geheim voorgeheugenopties van de Stale &#x200B;](../../../configuration/cache/level-two-cache.md#stale-cache-options) in de _Gids van de Configuratie_.

>[!WARNING]
>
>In de bovenstaande configuratie is de verouderde cache beschikbaar op de voorkant van de cache van `default` , die een &#39;verval-cache&#39;-gedrag toepast op alle cachemarkeringen die gebruikmaken van die voorkant. Magento core-cachetypen werken over het algemeen zoals u verwacht met deze instelling. Als uw project echter aangepaste code of extensies bevat die via de algemene `\Magento\Framework\App\Cache` API (bijvoorbeeld `$this->cache->save()` ) naar de cache schrijven zonder een toegewezen cachefront, kunnen die gegevens ook tijdens het opnieuw genereren worden gebruikt voor waarden van het type static.
>
>
>Als dit in onverwacht gedrag in uw aanpassingen resulteert, verlaten het geheime voorgeheugen van de schaal op `default` wordt onbruikbaar gemaakt en laat het slechts voor geselecteerde geheim voorgeheugentypes toe, zoals algemeen [&#x200B; op-gebouw &#x200B;](../../../configuration/cache/level-two-cache.md#stale-cache-options) wordt gedaan.

### Statische cache per cachetype afzonderlijk inschakelen

U kunt een uitgebreide cache alleen inschakelen voor geselecteerde cachetypen door een toegewezen cachefront in `.magento.env.yaml` te definiëren en de geselecteerde cachetypen hieraan toe te wijzen.

Voor een correcte werking moet de aangepaste voorzijde worden gedefinieerd als een volledige voorzijde onder `CACHE_CONFIGURATION.frontend` . Het is niet voldoende alleen `use_stale_cache: true` te definiëren voor een nieuwe naam voor de voorzijde.

**de configuraties van het Voorbeeld**

>[!BEGINTABS]

>[!TAB  vorm stapelgeheime voorgeheugen voor Redis ]

Voor Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!TAB  vorm stapelgeheime voorgeheugen voor Valkey ]

Voor Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':
 
        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!ENDTABS]

>[!NOTE]
>
>Als de bronvoorkant is geconfigureerd met extra achterste opties, zoals compressie, opnieuw proberen, vooraf laden van toetsen of andere waarden, kopieert u deze opties naar `stale_cache_enabled` zodat de nieuwe voorkant hetzelfde gedrag behoudt.


## Afzonderlijke cache- en sessieinstanties

Als u de cache scheidt van de sessies, kunt u deze onafhankelijk beheren. Het vermindert geschil tussen geheim voorgeheugen en zittingsverkeer, verhindert geheim voorgeheugengerelateerde druk zittingen te beïnvloeden, en staat elke instantie Redis of Valkey toe om voor zijn eigen werkbelasting worden gerangschikt en worden gestemd.

Voer de onderstaande stappen uit om een speciaal exemplaar voor sessies beschikbaar te stellen:

>[!BEGINTABS]

>[!TAB  Redis ]

1. Werk het configuratiebestand van `.magento/services.yaml` bij.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
     type: redis:6.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
     disk: 2048
   ```

1. Werk het configuratiebestand van `.magento.app.yaml` bij.

   ```yaml
      relationships:
        database: "mysql:mysql"
        redis: "redis:redis"
        redis-session: "redis-session:redis"   # Relationship of the new Redis instance
        search: "search:elasticsearch"
        rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Vraag om een nieuwe instantie Redis die gewijd is aan sessies over productie- en parkeeromgevingen.

   Verzend een [&#x200B; kaartje van de Steun van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Neem de bijgewerkte configuratiebestanden `.magento/services.yaml` en `.magento.app.yaml` op.

   Deze update veroorzaakt geen onderbreking, maar het vereist een plaatsing om de nieuwe dienst te activeren.

1. Controleer of de nieuwe instantie actief is en noteer het poortnummer.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Voeg het poortnummer toe aan het configuratiebestand van `.magento.env.yaml` .

   >[!IMPORTANT]
   >
   >Configureer de Redis-sessiepoort alleen als `ece-tools` deze niet automatisch kan detecteren in de definitie van de `MAGENTO_CLOUD_RELATIONSHIPS` Redis-sessieservice.

   >[!NOTE]
   >
   >Stel `disable_locking` in op `1` voor de beste prestaties. In zeldzame gevallen waarin zeldzame situaties voorkomen als gevolg van hoge gelijktijdige sessieactiviteit, stelt u deze in op `0` om vergrendeling mogelijk te maken.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Verwijder zittingen van het [&#x200B; standaardgegevensbestand &#x200B;](../../../configuration/cache/redis-pg-cache.md) (`db 0`) op Redis geheim voorgeheugeninstantie.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB  Valkey ]

1. Werk het configuratiebestand van `.magento/services.yaml` bij.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
   search:
     type: elasticsearch:7.9
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:3.8
     disk: 2048
   ```

1. Werk het configuratiebestand van `.magento.app.yaml` bij.

   ```yaml
   relationships:
     database: "mysql:mysql"
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Vraag om een nieuwe instantie Valkey die aan zittingen op Productie en het Opvoeren milieu&#39;s wordt gewijd.

   Verzend een [&#x200B; kaartje van de Steun van Adobe Commerce &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket). Neem de bijgewerkte configuratiebestanden `.magento/services.yaml` en `.magento.app.yaml` op.

   Deze update veroorzaakt geen onderbreking, maar het vereist een plaatsing om de nieuwe dienst te activeren.

1. Controleer of de nieuwe instantie actief is en noteer het poortnummer.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Voeg het poortnummer toe aan het configuratiebestand van `.magento.env.yaml` .

   >[!IMPORTANT]
   >
   >Configureer de poort voor Valkey-sessies alleen als `ece-tools` deze niet automatisch kan detecteren vanuit de definitie van de `MAGENTO_CLOUD_RELATIONSHIPS` Valkey-sessieservice.

   >[!NOTE]
   >
   >Stel `disable_locking` in op `1` voor de beste prestaties. In zeldzame gevallen waarin zeldzame situaties voorkomen als gevolg van hoge gelijktijdige sessieactiviteit, stelt u deze in op `0` om vergrendeling mogelijk te maken.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Verwijder zittingen van het [&#x200B; standaardgegevensbestand &#x200B;](../../../configuration/cache/redis-pg-cache.md) (`db 0`) op de Valkey geheim voorgeheugeninstantie.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Cachecompressie

Als u meer dan 6 GB Redis of Valkey `maxmemory` gebruikt, kunt u cachecompressie inschakelen om de ruimte te verminderen die door sleutels wordt verbruikt. Houd er rekening mee dat deze instelling de client-side prestaties voor geheugenbesparingen op zich neemt. Als u over onbenutte CPU-capaciteit beschikt, kunt u het ook inschakelen. Zie [&#x200B; Redis van het Gebruik voor zittingsopslag &#x200B;](../../../configuration/cache/redis-session.md) of [&#x200B; Valkey van het Gebruik voor zittingsopslag &#x200B;](../../../configuration/cache/valkey-session.md) in de _Gids van de Configuratie_.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Asynchrone vastzetten inschakelen

Om `lazyfree` op Adobe Commerce op wolkeninfrastructuur toe te laten, leg een [&#x200B; kaartje van de Steun van Adobe Commerce voor &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) verzoekend dat de volgende Redis of Valkey configuratie op uw milieu&#39;s wordt toegepast:

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

Wanneer `lazyfree` wordt toegelaten, schrapt Redis of Valkey geheugenterugwinning aan achtergronddraden voor uitzettingen, vervalsingen, server-in werking gestelde schrapt, schrapt de gebruiker, en replica dataset flushes. Dit vermindert het blokkeren van de belangrijkste-draad en kan verzoekvertraging verminderen.

>[!NOTE]
>
>De optie `lazyfree-lazy-user-del yes` zorgt ervoor dat de opdracht `DEL` zich gedraagt als `UNLINK` , die de koppelingen met toetsen direct ongedaan maakt en hun geheugen asynchroon vrijmaakt.

>[!WARNING]
>
>Omdat vrijmaken op de achtergrond plaatsvindt, blijft het geheugen dat door verwijderde, verlopen of verwijderde toetsen wordt gebruikt, toegewezen totdat de achtergrondthreads het werk voltooien. Als uw Redis- of Valkey-instantie al onder een krappe geheugendruk staat, moet u voorzichtig testen en overwegen om de geheugendruk eerst te verlagen. Schakel bijvoorbeeld de cache van het blok uit voor specifieke gevallen en maak de cache en de sessie opnieuw af, zoals hierboven beschreven.

## Multithreaded I/O inschakelen

Om Redis I/O-threading op Adobe Commerce op wolkeninfrastructuur toe te laten, leg een [&#x200B; kaartje van de Steun van Adobe Commerce voor &#x200B;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) verzoekend om de I/O-threading hieronder configuratie. Deze configuratie kan productie verbeteren door contactdooslezen te ontladen en schrijft en bevel het ontleden van de belangrijkste draad, ten koste van hoger gebruik CPU. Valideer onder lading en controleer uw gastheren.

>[!BEGINTABS]

>[!TAB  vorm I/O draden voor Redis ]

Voor Redis:

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB  vorm I/O draden voor Valkey ]

Voor Valkey:

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]


>[!NOTE]
>
>I/O-threads komen alleen overeen met client I/O en parseren. De uitvoering van de opdracht Redis blijft single-threaded.

>[!WARNING]
>
>Het inschakelen van I/O-threads kan het CPU-gebruik verhogen en niet elke werklast ten goede komen. Begin met een conservatieve waarde en benchmark. Als de latentie stijgt of CPU verzadigt, verlaagt u `io-threads` of schakelt u de leesvolgorde in I/O-threads uit.


## Time-outs en nieuwe pogingen voor de client vergroten

Verhoog de tolerantie van de Redis- of Valkey-cache-client voor korte verzadigingsperiodes door de achtergrondopties aan te passen in `.magento.env.yaml` .

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

Met deze instellingen kunt u intermitterende verbindings- en leestime-outfouten tijdens korte pieken verminderen door de instelling van de verbinding opnieuw te proberen en meer tijd vrij te maken voor reacties van Redis of Valkey.

>[!NOTE]
>
>Deze instellingen kunnen helpen bij korte congestie, maar verhelpen blijvende overbelasting niet.

## Configuratievoorbeelden

Gebruik de volgende voorbeelden als uitgangspunt voor uw Redis- of Valkey-serviceconfiguraties.


### Alle aanbevelingen voor best practices toepassen

>[!BEGINTABS]

>[!TAB  Redis ]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB  Valkey configuratievoorbeeld ]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### Pas alle aanbevelingen van best practices toe en scheiden de stapelcache op cachetype

>[!BEGINTABS]

>[!TAB  Redis ]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB  Valkey ]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## Aanvullende informatie

Zie de volgende verwante onderwerpen:

- [Paginacache opnieuw weergeven](../../../configuration/cache/redis-pg-cache.md)
- [Redis gebruiken voor sessieopslag](../../../configuration/cache/redis-session.md)
- [Valkey gebruiken voor standaardcache](../../../configuration/cache/valkey-pg-cache.md)
- [Valkey gebruiken voor sessieopslag](../../../configuration/cache/valkey-session.md)
