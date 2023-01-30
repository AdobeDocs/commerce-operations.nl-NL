---
title: Aanbevolen procedures voor Redis-serviceconfiguratie
description: Leer hoe u de prestaties van caching kunt verbeteren door de uitgebreide Redis-cacheimplementatie voor Adobe Commerce 2.3.5 te gebruiken.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 12de523cc7ea1486c894d54efe6944d92d87ded0
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Aanbevolen procedures voor Redis-serviceconfiguratie

- Voor Adobe Commerce 2.3.3 en later geïmplementeerd op cloudinfrastructuur, upgrade naar Redis versie 5.0.
- Gebruik voor Adobe Commerce versie 2.3.5 of hoger de uitgebreide Redis-cacheimplementatie. Deze implementatie omvat de volgende optimalisaties om het aantal vragen van Redis te minimaliseren die op elk verzoek van Adobe Commerce worden uitgevoerd:
   - De omvang van de netwerkgegevensoverdracht tussen Redis en Adobe Commerce verkleinen
   - Verlaag het CPU-verbruik van CPU-cycli door de adapter beter in staat te stellen automatisch te bepalen wat moet worden geladen
   - Verminder rassenvoorwaarden bij schrijven van Redis

## Betrokken producten en versies

Adobe Commerce op cloudinfrastructuur met versie 2.3.3 of hoger.
Adobe Commerce (alle implementatiemethoden), versie 2.3.5 en hoger

## Herdis-versie bijwerken voor cloudimplementaties

Voor Adobe Commerce-implementaties op cloudinfrastructuur met Adobe Commerce 2.3.3 of hoger, dient u de Redis-service te upgraden naar Redis versie 5.0. Raadpleeg de volgende onderwerpen in de documentatie over de cloudinfrastructuur van Adobe Commerce voor instructies:

- [Redis-service instellen](https://devdocs.magento.com/cloud/project/services-redis.html)
- [De serviceversie wijzigen](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## De uitgebreide cache-implementatie van Redis configureren

Voor Adobe Commerce 2.3.5 en hoger moet u uw configuratie bijwerken zodat deze de uitgebreide Redis-cache-implementatie gebruikt `\Magento\Framework\Cache\Backend\Redis`.

### Configuratie voor cloudimplementaties

Met `ece-tools` 2002.1.1 of hoger, configureer de verbeterde Redis-cache door de `REDIS_BACKEND` implementatievariabele in het configuratiebestand van de omgeving; `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Zie voor meer informatie [Variabelen implementeren > `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) in de documentatie voor Adobe Commerce over cloudinfrastructuur.

>[!NOTE]
>
> Gebruik de opdrachtregel om de versie van de bureaubladgereedschappen die in uw lokale cloud-omgeving is geïnstalleerd, te controleren met de `composer show magento/ece-tools` gebruiken. Indien nodig [update the ece tools version](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

>[!WARNING]
>
>Do _niet_ Een Redis-slave-verbinding configureren voor infrastructuurprojecten in de cloud met een [geschaalde architectuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Dit veroorzaakt Redis verbindingsfouten. Zie [de Redis-configuratiehandleiding](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) in de _Handel in Cloud-infrastructuur_ hulplijn.


### Configuratie voor implementaties op locatie

Voor Adobe Commerce-implementaties op locatie configureert u de nieuwe Redis-cacheimplementatie met behulp van de `bin/magento:setup` opdrachten. Zie voor instructies [Redis gebruiken voor standaardcache](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Aanvullende informatie

- [Adobe Commerce Release v2.3.5 - Prestatieverbeteringen](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Paginacache opnieuw weergeven](../../../configuration/cache/redis-pg-cache.md)


