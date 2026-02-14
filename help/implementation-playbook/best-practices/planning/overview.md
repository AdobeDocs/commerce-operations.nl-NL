---
title: Planning van de implementatie
description: Leer over implementatie beste praktijken voor de planningsfase van projecten van Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: ee7551374aa6d4ad462dd64ee3d05b934b43ce45
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Planningsfase

De planningsfase omvat de volgende activiteiten:

- Architecturaal ontwerp
- Catalogusontwerp
- Extensie aanschaffen
- Projectbereikregels
- Vereisten verzamelen
- Verkoop en marketing

De volgende secties omvatten beste praktijkinformatie voor de planningsfase.

## Vereisten verzamelen

<table>
<thead>
  <tr>
    <th>Beste praktijken</th>
    <th>Beschrijving</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>Toepassingsconfiguratie</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">Sites, opslagruimten en opslagweergaven configureren</a></td>
    <td>Configureer sites, sla weergaven op en sla ze op om de prestaties van de site te maximaliseren.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/nl/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">Algemene configuratieproblemen</a></td>
    <td>Los en verhinder de vijf gemeenschappelijkste configuratiekwesties voor de plaatsen van Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html?lang=nl-NL">Caching</a></td>
    <td>Gebruik de tools voor cachebeheer om de prestaties van uw site te verbeteren.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">In cache plaatsen van volledige pagina's</a></td>
    <td>Leer hoe u met openbare gegevens werkt wanneer u caching implementeert in uw Adobe Commerce-extensie.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">OPcache-geheugengrootte</a></td>
    <td>Vermijd prestatievermindering met specifieke instellingen voor OPcache-geheugenverbruik.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">Rapportage configureren</a></td>
    <td>Optimaliseer siteprestaties door de rapportmodule te verwijderen als u deze niet gebruikt.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Databaseconfiguratie</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">Database configureren voor cloudimplementaties</a></td>
    <td>Configureer database- en toepassingsinstellingen om de prestaties te verbeteren bij de implementatie van Adobe Commerce op cloud-infrastructuurprojecten.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">MySQL configureren</a></td>
    <td>Leer hoe MySQL triggers en slave verbindingen de prestaties van de site beïnvloeden en hoe u deze effectief kunt gebruiken.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Services configureren</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html?lang=nl-NL">Snel instellen</a></td>
    <td>Configureer snel services voor uw Adobe Commerce op het infrastructuurproject voor de cloud.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html?lang=nl-NL">Meldingskanalen voor New Relic configureren</a></td>
    <td>Open uw New Relic-dashboard en analyseer gegevens van uw Adobe Commerce over het infrastructuurproject in de cloud.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Redis configureren</a></td>
    <td>Verbeter de prestaties bij het in cache plaatsen door de uitgebreide Redis-cacheimplementatie voor Adobe Commerce te gebruiken.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Realpath cache-grootte</a></td>
    <td>Optimaliseer de prestaties door de cacheconfiguratie PHP ` readlpath` bij te werken om de aanbevolen instellingen te gebruiken.</td>
  </tr>
</tbody>
</table>

## Catalogusontwerp

| Beste praktijken | Beschrijving |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [&#x200B; configuratie van de Categorie &#x200B;](catalog-management.md#category-limits) | Productcategorieën configureren voor optimale prestaties. |
| [&#x200B; &#x200B; van de Productconfiguratie &#x200B;](catalog-management.md#product-sku-limits) | Vorm product SKUs voor optimale prestaties. |
| [&#x200B; de variatieconfiguratie van het Product &#x200B;](catalog-management.md#product-variations) | Productvariaties configureren voor optimale prestaties. |
| [&#x200B; de optieconfiguratie van het Product &#x200B;](catalog-management.md#product-options) | Configureer productopties voor optimale prestaties. |
| [&#x200B; &#x200B; van de attributenconfiguratie van het Product &#x200B;](catalog-management.md#product-attributes) | Productkenmerken configureren voor optimale prestaties. |
| [&#x200B; de configuratie van de Paginering voor productlijsten &#x200B;](catalog-management.md#product-listing-pagination) | Configureer productpaginering voor optimale prestaties. |

## Extensies

| Beste praktijken | Beschrijving |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [&#x200B; Gebruikend derdextensies in Adobe Commerce &#x200B;](extensions.md) | Leer hoe u prestatieproblemen kunt voorkomen die worden veroorzaakt door Adobe Commerce-extensies van derden. |

## Projectbereikregels

| Beste praktijken | Beschrijving |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [&#x200B; escalaties van de Partner &#x200B;](partner-escalation.md) | Bereid voor het escaleren van een partnerkwestie met een Team van de Rekening van Adobe voor of leer hoe te om een escalatie te vermijden. |
| [&#x200B; de opslagverwerking van Betalingen &#x200B;](payment-processing-storage.md) | Betalingsgegevens veilig verwerken en opslaan. |

## Verkoop en marketing

| Beste praktijken | Beschrijving |
|------------------------------------------------------------|--------------------------------------------------------------|
| [&#x200B; de grenzen van het Karretje van het Product &#x200B;](catalog-management.md#cart-limits) | Beheer de grenzen van winkelwagentjes voor optimale prestaties. |
| [&#x200B; het Vormen bevorderingen &#x200B;](catalog-management.md#promotions) | Configureer de verkoop en promoties voor objecten in een winkelwagentje. |
