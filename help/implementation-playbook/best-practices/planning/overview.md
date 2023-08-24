---
title: Planning van de implementatie
description: Leer over implementatie beste praktijken voor de planningsfase van projecten van Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# Planningsfase

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
   - [Volledige pagina&#39;s in cache plaatsen](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [OPcache-geheugengrootte](opcache-memory-size.md)
   - [Rapportageconfiguratie](reporting-configuration.md)

- **Databaseconfiguratie**
   - [Best practices voor databaseconfiguratie voor cloudimplementatie &#x200B;](database-on-cloud.md)
   - [MySQL-&#x200B;](mysql-configuration.md)

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

- [Categorieconfiguratie](catalog-management.md#category-limits)
- [&#x200B;](catalog-management.md#product-sku-limits)
- [Configuratie productvariatie](catalog-management.md#product-variations)
- [Configuratie van productopties](catalog-management.md#product-options)
- [&#x200B; productkenmerken](catalog-management.md#product-attributes)
- [Pagineringsconfiguratie voor productaanbiedingen](catalog-management.md#product-listing-pagination)

## **Verkoop en marketing**

- [Aanbevolen werkwijzen voor productkartongrens](catalog-management.md#cart-limits)
- [Aanbevolen procedures voor het configureren van promoties](catalog-management.md#promotions)

## **Projectbereikregels**

- [Partnerescalaties](partner-escalation.md)
- [Betalingsopslagverwerking](payment-processing-storage.md)

## **Extensies kopen**

- [Aanbevolen procedures voor het gebruik van extensies van derden in Adobe Commerce](extensions.md)
