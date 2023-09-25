---
title: Aanbevolen procedures voor Redis-serviceconfiguratie
description: Leer hoe u de prestaties van caching kunt verbeteren met de uitgebreide Redis-cacheimplementatie voor Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 156e6412b9f94b74bad040b698f466808b0360e3
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Aanbevolen procedures voor Redis-serviceconfiguratie

- Redis L2-cache configureren
- Redis-slave-verbinding inschakelen
- Toetsen vooraf laden
- Ophaalcache inschakelen
- De Redis-cache scheiden van de Redis-sessie
- De cache van Redis comprimeren en gebruiken `gzip` voor hogere compressie

## Redis L2-cache configureren

De Redis L2-cache configureren door de `REDIS_BACKEND` plaatsingsvariabele in `.magento.env.yaml` configuratiebestand.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Voor de configuratie van de omgeving op de Cloud-infrastructuur raadpleegt u [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) in de _Handleiding voor handel in Cloud-infrastructuur_.

Voor installaties ter plaatse, zie [Pagina&#39;s opnieuw weergeven in cache plaatsen](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) in de _Configuratiegids_.

>[!NOTE]
>
>Controleer of u de meest recente versie van het dialoogvenster `ece-tools` pakket. Zo niet, [upgrade naar de nieuwste versie](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). U kunt de in uw lokale omgeving geïnstalleerde versie controleren met de `composer show magento/ece-tools` CLI-opdracht.

## Redis-slave-verbinding inschakelen

Een slave-verbinding met Redis inschakelen in het dialoogvenster `.magento.env.yaml` configuratiedossier om slechts één knoop toe te staan om read-write verkeer te behandelen terwijl de andere knopen het read-only verkeer behandelen.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Zie [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) in de _Handleiding voor handel in Cloud-infrastructuur_.

Voor Adobe Commerce-installaties op locatie configureert u de nieuwe Redis-cacheimplementatie met behulp van de `bin/magento:setup` opdrachten. Zie [Redis gebruiken voor standaardcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) in de _Configuratiegids_.

>[!WARNING]
>
>Do _niet_ Een Redis-slave-verbinding configureren voor infrastructuurprojecten in de cloud met een [geschaalde/gesplitste architectuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Dit veroorzaakt Redis verbindingsfouten. Zie [Richtlijnen voor opnieuw configuratie](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) in de _Handel in Cloud-infrastructuur_ hulplijn.

## Toetsen vooraf laden

Als u gegevens opnieuw wilt gebruiken tussen pagina&#39;s, geeft u de toetsen voor vooraf laden op in het dialoogvenster `.magento.env.yaml` configuratiebestand.

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

Voor installaties ter plaatse, zie [Redis, functie voor vooraf laden](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) in de _Configuratiegids_.

## Ophaalcache inschakelen

Verminder vergrendelingstijd en verbeter de prestaties—vooral bij het omgaan met talloze Blokken en Cache keys—door een verouderde cache te gebruiken en tegelijkertijd een nieuwe cache te genereren. Stale cache inschakelen en cachetypen definiëren in het dialoogvenster `.magento.env.yaml` configuratiebestand:

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

Voor het vormen van installaties op-gebouw, zie [Cacheopties voor stijl](../../../configuration/cache/level-two-cache.md#stale-cache-options) in de _Configuratiegids_.

## Afzonderlijke Redis-cache en sessieinstanties

Door de Redis-cache te scheiden van de Redis-sessie kunt u de cache en de sessies onafhankelijk beheren. Het verhindert geheim voorgeheugenkwesties zittingen te beïnvloeden, die opbrengst zouden kunnen beïnvloeden. Elke Redis-instantie wordt op de eigen basis uitgevoerd, wat de prestaties verbetert.

1. Werk de `.magento/services.yaml` configuratiebestand.

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

1. Werk de `.magento.app.yaml` configuratiebestand.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Een [Adobe Commerce-ondersteuningsticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) om de levering aan te vragen van een nieuwe instantie Redis gewijd aan zittingen over de milieu&#39;s van de Productie en van het Staging. De bijgewerkte versie opnemen `.magento/services.yaml` en `.magento.app.yaml` configuratiebestanden. Dit zal geen onderbreking veroorzaken, maar het vereist een plaatsing om de nieuwe dienst te activeren.

1. Controleer of de nieuwe instantie wordt uitgevoerd en noteer het poortnummer.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Voeg het poortnummer toe aan de `.magento.env.yaml` configuratiebestand.

   >[!NOTE]
   >`disable_locking` moet worden ingesteld op `1`.
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Sessies verwijderen uit het dialoogvenster [standaarddatabase](../../../configuration/cache/redis-pg-cache.md) (`db 0`) op de Redis-cacheinstantie.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Tijdens plaatsing, zou u de volgende lijnen in moeten zien [logboek samenstellen en implementeren](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
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

Als u meer dan 6 GB Redis gebruikt `maxmemory`, kunt u cachecompressie gebruiken om de ruimte te verminderen die door de sleutels wordt verbruikt. Houd er rekening mee dat er een compromis is met de prestaties aan de clientzijde. Als u over vrije cpu&#39;s beschikt, laat het toe. Zie [Redis gebruiken voor sessieopslag](../../../configuration/cache/redis-session.md) in de _Configuratiegids_.

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
