---
title: Aanbevolen procedures voor Redis-serviceconfiguratie
description: Leer hoe u de prestaties van caching kunt verbeteren met de uitgebreide Redis-cacheimplementatie voor Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: bbebb414ae3b8c255e17b1f3673a6c4b7c6f23b2
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Aanbevolen procedures voor Redis-serviceconfiguratie

- Redis L2-cache configureren
- Redis-slave-verbinding inschakelen
- Toetsen vooraf laden
- Ophaalcache inschakelen
- De Redis-cache scheiden van de Redis-sessie
- De Redis-cache comprimeren en `gzip` gebruiken voor hogere compressie

## Redis L2-cache configureren

Configureer de L2-cache van Redis door de implementatievariabele `REDIS_BACKEND` in het `.magento.env.yaml` -configuratiebestand in te stellen.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Voor milieuconfiguratie op de infrastructuur van de Wolk, zie [`REDIS_BACKEND` ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=nl-NL#redis_backend) in _Commerce op de Gids van de Infrastructuur van de Wolk_.

Voor installaties op-gebouw, zie [ Redis pagina caching ](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) in de _Gids van de Configuratie_ vormen.

>[!NOTE]
>
>Controleer of u de nieuwste versie van het pakket `ece-tools` gebruikt. Als niet, [ verbetering aan de recentste versie ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=nl-NL). U kunt de versie controleren die in uw lokale omgeving is geïnstalleerd met de opdracht `composer show magento/ece-tools` CLI.


### Grootte van L2-cachegeheugen (Adobe Commerce Cloud)

L2 geheim voorgeheugen gebruikt a [ tijdelijk dossiersysteem ](https://en.wikipedia.org/wiki/Tmpfs) als opslagmechanisme. Vergeleken met gespecialiseerde zeer belangrijke gegevensbestandsystemen, heeft een tijdelijk dossiersysteem geen zeer belangrijk verwijderingsbeleid om geheugengebruik te controleren.

Het gebrek aan controle van het geheugengebruik kan het L2 geheim voorgeheugengebruik veroorzaken om in tijd te groeien door het oude geheime voorgeheugen te accumuleren.

Om geheugenuitputting van L2 geheim voorgeheugenimplementaties te vermijden, ontruimt Adobe Commerce de opslag wanneer een bepaalde drempel wordt bereikt. De standaardwaarde is 95%.

Het is belangrijk om het maximale gebruik van het L2-cachegeheugen aan te passen op basis van de projectvereisten voor cacheopslag. Gebruik een van de volgende methoden om de grootte van de geheugencache te configureren:

- Maak een ondersteuningsticket om groottewijzigingen van de `/dev/shm` -montage aan te vragen.
- Pas de eigenschap `cleanup_percentage` op toepassingsniveau aan om het maximale vulpercentage van de opslagruimte te beperken. Het resterende vrije geheugen kan door andere diensten worden gebruikt.
U kunt de configuratie in de plaatsingsconfiguratie onder de groep van de geheim voorgeheugenconfiguratie aanpassen `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>De `cleanup_percentage` configureerbare optie is geïntroduceerd in Adobe Commerce 2.4.4.

De volgende code toont een voorbeeldconfiguratie in het `.magento.env.yaml` dossier:

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

De vereisten van het geheime voorgeheugen kunnen variëren gebaseerd op projectconfiguratie en douanecode van de douanederde. Het bereik van de grootte van het L2-cachegeheugen maakt het mogelijk dat de L2-cache werkt zonder te veel drempelresultaten.
In het ideale geval zou het geheugengebruik in de L2-cache zich op een bepaald niveau onder de drempelwaarde moeten stabiliseren, alleen om te voorkomen dat de opslagruimte vaak wordt gewist.

U kunt het gebruik van het L2 geheime voorgeheugengeheugen op elke knoop van de cluster controleren gebruikend het volgende CLI bevel en zoekend de `/dev/shm` lijn.
Het gebruik kan per knooppunt variëren, maar het moet in dezelfde waarde worden omgezet.

```bash
df -h
```

## Redis-slave-verbinding inschakelen

Schakel een Redis-slave-verbinding in het `.magento.env.yaml` -configuratiebestand in zodat slechts één knooppunt lees- en schrijfverkeer kan afhandelen en de andere knooppunten het alleen-lezen verkeer afhandelen.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Zie [ REDIS_USE_SLAVE_CONNECTION ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=nl-NL#redis_use_slave_connection) in _Commerce op de Gids van de Infrastructuur van de Wolk_.

Voor Adobe Commerce-installaties op locatie configureert u de nieuwe Redis-casimplementatie met de opdrachten `bin/magento:setup` . Zie [ Redis van het Gebruik voor standaardgeheime voorgeheugen ](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) in de _Gids van de Configuratie_.

>[!WARNING]
>
>Vorm __ geen Redis slave verbinding voor de projecten van de wolkeninfrastructuur met a [ geschraapte/gespleten architectuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html?lang=nl-NL). Dit veroorzaakt Redis verbindingsfouten. Zie [ opnieuw configuratiebegeleiding ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=nl-NL#redis_use_slave_connection) in _Commerce op de gids van de Infrastructuur van de Wolk_.

## Toetsen vooraf laden

Als u gegevens tussen pagina&#39;s wilt hergebruiken, geeft u de toetsen voor het vooraf laden op in het configuratiebestand van `.magento.env.yaml` .

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Voor installaties op-gebouw, zie [ Redis preload eigenschap ](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) in de _Gids van de Configuratie_.

## Ophaalcache inschakelen

Verminder vergrendelingstijd en verbeter de prestaties—vooral bij het omgaan met talloze Blokken en Cache keys—door een verouderde cache te gebruiken en tegelijkertijd een nieuwe cache te genereren. Stale cache inschakelen en cachetypen definiëren in het configuratiebestand van `.magento.env.yaml` :

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

>[!NOTE]
>
>In het vorige voorbeeld, is het `full_page` geheime voorgeheugen niet relevant voor Adobe Commerce op de projecten van de wolkeninfrastructuur, omdat zij [ Fastly ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/cdn/fastly) gebruiken.

Voor het vormen van installaties op-gebouw, zie [ het geheim voorgeheugenopties van de Stale ](../../../configuration/cache/level-two-cache.md#stale-cache-options) in de _Gids van de Configuratie_.

## Afzonderlijke Redis-cache en sessieinstanties

Door de Redis-cache te scheiden van de Redis-sessie kunt u de cache en de sessies onafhankelijk beheren. Het verhindert geheim voorgeheugenkwesties zittingen te beïnvloeden, die opbrengst zouden kunnen beïnvloeden. Elke Redis-instantie wordt op de eigen basis uitgevoerd, wat de prestaties verbetert.

1. Werk het configuratiebestand van `.magento/services.yaml` bij.

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
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

1. Verzend een [ kaartje van de Steun van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=nl-NL#submit-ticket) om de levering van een nieuwe instantie te verzoeken Redis gewijd aan zittingen op de milieu&#39;s van de Productie en van het Staging. Neem de bijgewerkte configuratiebestanden `.magento/services.yaml` en `.magento.app.yaml` op. Dit zal geen onderbreking veroorzaken, maar het vereist een plaatsing om de nieuwe dienst te activeren.

1. Controleer of de nieuwe instantie wordt uitgevoerd en noteer het poortnummer.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Voeg het poortnummer toe aan het configuratiebestand van `.magento.env.yaml` .

   >[!IMPORTANT]
   >
   >Configureer de opnieuw-sessiepoort alleen als `ece-tools` deze niet automatisch kan detecteren vanuit de definitie van de `MAGENTO_CLOUD_RELATIONSHIPS` opnieuw-sessieservice.

   >[!NOTE]
   >
   >`disable_locking` moet zijn ingesteld op `1` .

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374 # check the port in $MAGENTO_CLOUD_RELATIONSHIPS and put it here (by default, you can delete this line!!)
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Verwijder zittingen van het [ standaardgegevensbestand ](../../../configuration/cache/redis-pg-cache.md) (`db 0`) op Redis geheim voorgeheugeninstantie.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Tijdens plaatsing, zou u de volgende lijnen in [ moeten zien bouwen en logboek ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=nl-NL#build-and-deploy-logs) opstellen:

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## Cachecompressie

Als u meer dan 6 GB Redis `maxmemory` gebruikt, kunt u de compressie van het geheime voorgeheugen gebruiken om de ruimte te verminderen die door de sleutels wordt verbruikt. Houd er rekening mee dat er een compromis is met de prestaties aan de clientzijde. Als u over vrije cpu&#39;s beschikt, laat het toe. Zie [ Redis van het Gebruik voor zittingsopslag ](../../../configuration/cache/redis-session.md) in de _Gids van de Configuratie_.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Aanvullende informatie

- [Paginacache opnieuw weergeven](../../../configuration/cache/redis-pg-cache.md)
- [Redis gebruiken voor sessieopslag](../../../configuration/cache/redis-session.md)
