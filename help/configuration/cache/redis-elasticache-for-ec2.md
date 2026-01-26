---
title: Redis configureren met AWS ElastiCache
description: Voor Commerce-instanties die worden gehost op EC2, leert u hoe u AWS ElastiCache gebruikt in plaats van een lokale Redis-instantie. Ontdek opdrachtregelopstelling, configuratieopties en validatietechnieken.
feature: Configuration, Cache
source-git-commit: b66479ee1350d92c1d59212283222e5068c263a6
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Redis configureren met AWS ElastiCache

Vanaf Commerce 2.4.3 kunnen instanties die worden gehost op Amazon EC2 een AWS ElastiCache gebruiken in plaats van een lokale Redis-instantie.

>[!WARNING]
>
>Deze sectie is alleen van toepassing op Commerce-instanties die op Amazon EC2 VPC&#39;s worden uitgevoerd. Het werkt niet voor installaties ter plaatse.

## Vereisten

- **creeer een Redis OSS serverless geheime voorgeheugen** - van de Console van het Beheer van AWS, creeer het geheime voorgeheugen van Redis in het zelfde gebied en VPC van de instantie EC2. Voor instructies, zie de [ documentatie van Elasticache van AWS ](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **verifieer de verbinding aan uw instantie van EC2 Commerce**

   - Een SSH-verbinding openen naar uw EC2-instantie
   - Installeer de Redis-client op het EC2-exemplaar:

     ```bash
     sudo apt-get install redis
     ```

   - Voeg een binnenkomende regel aan de EC2 veiligheidsgroep toe: Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Voeg een binnenkomende regel toe aan de ElastiCache Cluster-beveiligingsgroep: Type `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Verbind met Redis CLI:

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Commerce configureren voor gebruik van de cluster

Commerce ondersteunt meerdere typen configuraties in cache. Over het algemeen worden de configuraties in cache opgedeeld tussen front-end en backend. In cache plaatsen vóór wordt geclassificeerd als `default` en wordt gebruikt voor elk cachetype. U kunt caches op een lager niveau aanpassen of splitsen voor betere prestaties. Een algemene configuratie van Redis scheidt het standaardgeheime voorgeheugen en paginacache in hun eigen Gegevensbestand van Redis (RDB).

Voer `setup` -opdrachten uit om de eindpunten van Redis op te geven.

Commerce for Redis configureren als standaardcaching:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Commerce for Redis pagina caching configureren:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Commerce configureren voor gebruik van Redis voor sessieopslag:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Connectiviteit verifiëren

**om te verifiëren dat Commerce aan ElastiCache** spreekt:

1. Open een verbinding SSH aan de instantie van Commerce EC2.
1. Start de Redis-monitor.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Open een pagina in de gebruikersinterface van Commerce.
1. Verifieer de [ geheim voorgeheugenoutput ](#verify-the-redis-connection) in uw terminal.
