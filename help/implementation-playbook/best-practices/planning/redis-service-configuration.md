---
title: Aanbevolen procedures voor Redis-serviceconfiguratie
description: Leer hoe u de prestaties van caching kunt verbeteren met de uitgebreide Redis-cacheimplementatie voor Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Aanbevolen procedures voor Redis-serviceconfiguratie

- Gebruik de uitgebreide Redis cache-implementatie, die de volgende optimalisaties bevat om het aantal Redis-query&#39;s dat op elk verzoek van Adobe Commerce wordt uitgevoerd, tot een minimum te beperken:
   - Verkleint de omvang van de netwerkgegevensoverdracht tussen Redis en Adobe Commerce
   - Verlaagt het gebruik van CPU-cycli door de adapter beter in staat te stellen automatisch te bepalen wat moet worden geladen
   - Vermindert rassenvoorwaarden bij het schrijven van Redis verrichtingen
- De Redis-cache scheiden van de Redis-sessie
- De cache van Redis comprimeren en gebruiken `gzip` prestaties verbeteren

## Uitgebreide Redis-cacheimplementatie

Werk uw configuratie bij om de uitgebreide Redis-cacheimplementatie te gebruiken `\Magento\Framework\Cache\Backend\Redis`.

### Cloudimplementaties configureren

De uitgebreide Redis-cache configureren door de `REDIS_BACKEND` plaatsingsvariabele in `.magento.env.yaml` configuratiebestand.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Zie voor meer informatie de [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) variabele beschrijving in de _Handel in de infrastructuurgids voor de cloud_.

>[!NOTE]
>
> Controleer de `ece-tools` versie geïnstalleerd in uw lokale omgeving vanaf de opdrachtregel met behulp van de `composer show magento/ece-tools` gebruiken. Indien nodig [bijwerken naar de laatste versie](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>Do _niet_ Een Redis-slave-verbinding configureren voor infrastructuurprojecten in de cloud met een [geschaalde architectuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Dit veroorzaakt Redis verbindingsfouten. Zie [de Redis-configuratiehandleiding](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) in de _Handel in Cloud-infrastructuur_ hulplijn.

### Implementaties op locatie configureren

Voor Adobe Commerce-implementaties op locatie configureert u de nieuwe Redis-cacheimplementatie met behulp van de `bin/magento:setup` opdrachten. Zie voor instructies [Redis gebruiken voor standaardcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Afzonderlijke cache- en sessieinstanties

Als u de cache van Redis scheidt van de Redis-sessie, kunt u de cache en de sessies onafhankelijk beheren om te voorkomen dat cacheproblemen de sessies beïnvloeden.

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

1. Een [Adobe Commerce-ondersteuningsticket](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) om de serviceconfiguratie van Redis te wijzigen in Pro Production- en Staging-omgevingen. De bijgewerkte versie opnemen `.magento/services.yaml` en `.magento.app.yaml` configuratiebestanden.

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

Gebruik cachecompressie, maar houd er rekening mee dat er een compromis is met de prestaties op de client. Als u over vrije cpu&#39;s beschikt, laat het toe. Zie [Redis gebruiken voor sessieopslag](../../../configuration/cache/redis-session.md).

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
