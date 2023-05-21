---
title: Planning van implementatie
description: Leer over implementatie beste praktijken voor de planningsfase van projecten van Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Planning

De planningsfase omvat de volgende activiteiten:

- Vereisten verzamelen
- Architecturaal ontwerp
- Catalogusontwerp
- Projectbereikregels
- Accountprovisioning
- Toegang van gebruikers
- Extensie aanschaffen

De volgende secties omvatten beste praktijkinformatie voor de planningsfase.

## Vereisten verzamelen

- **Toepassingsconfiguratie**
   - [Aanbevolen procedures voor het configureren van sites, winkels en winkelweergaven (cloudinfrastructuur)](sites-stores-store-views.md)
   - [Hoe te om te verhinderen-en te bevestigen-de vijf gemeenschappelijkste configuratiekwesties voor de plaatsen van Adobe Commerce](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Aanbevolen procedures voor in cache plaatsen](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Volledige paginacache](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache-geheugengrootte](opcache-memory-size.md)
   - [Rapportageconfiguratie](reporting-configuration.md)

- **Databaseconfiguratie**
   - [Best practices voor databaseconfiguratie voor cloudimplementatie &#x200B;](database-on-cloud.md)
   - [MySQL-&#x200B; voor slave-verbinding](configure-mysql-slave-connection-on-cloud.md)
   - [MySQL triggergebruik](mysql-triggers-usage.md)

- **Services configureren**
   - [Snel instellen](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - Meldingskanalen configureren](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Aanbevolen werkwijzen voor &#x200B; van Redis-services](redis-service-configuration.md)
   - [Aanbevolen procedures voor het omzetten van cachegrootte in paden](realpath-cache-size.md)

## **Architecturaal ontwerp**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Werken met globale referentiearchitectuur](../../../implementation-playbook/architecture/global-reference.md)

## **Catalogusontwerp**

De volgende onderwerpen beschrijven best practices voor het optimaliseren van prestaties voor het configureren van uw Adobe Commerce-catalogus, inclusief aanbevolen maximumwaarden voor het aantal categorieën, producteffectieve SKU&#39;s, productvariaties, productkenmerken en opties, en meer.

- [Categorieconfiguratie](category-limits.md)
- [&#x200B;](product-sku-limits.md)
- [Configuratie productvariatie](product-variations.md)
- [Configuratie van productopties](product-options.md)
- [&#x200B; productkenmerken](product-attributes-and-options.md)
- [Pagineringsconfiguratie voor productaanbiedingen](product-listing-pagination.md)

## **Verkoop en marketing**

- [Aanbevolen werkwijzen voor productkartongrens](product-cart.md)
- [Aanbevolen procedures voor het configureren van promoties](product-cart-promotions.md)

## **Projectbereikregels**

- [Partnerescalaties](partner-escalation.md)
- [Betalingsopslagverwerking](payment-processing-storage.md)

## **Extensies kopen**

- [Aanbevolen procedures voor het gebruik van extensies van derden in Adobe Commerce](extensions.md)
