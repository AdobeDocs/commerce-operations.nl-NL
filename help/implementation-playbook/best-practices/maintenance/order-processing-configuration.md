---
title: Best practices voor configuratie voor verwerking van bestellingen
description: Leer best practices voor configuratie om de verwerkingsprestaties voor kassa's en bestellingen te verbeteren.
role: Admin, User
feature: Best Practices
exl-id: d15fe845-670f-4f7e-9645-7e111e6e809f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Best practices voor configuratie voor verwerking van bestellingen

Naarmate het ordervolume op uw Commerce-sites toeneemt, kunt u de prestaties van de kassa en de verwerking van de bestelling optimaliseren door de volgende opties voor de configuratie van de winkel in te schakelen:

- **[!UICONTROL Asynchronous indexing]** - Schakel deze optie in om databasestlokken en vertraagde verwerking te voorkomen die kunnen optreden wanneer grote aantallen bestellingen tegelijkertijd worden geplaatst.
- **[!UICONTROL Asynchronous email notifications]**—Schakel deze optie in om de afrekenprestaties te versnellen door het verzenden van afrekenings- en bestelberichten voor de verwerking van e-mailberichten met bepaalde intervallen in plaats van deze onmiddellijk te verzenden.
- **[!UICONTROL Enable Archiving]** - Schakel deze optie in om de prestaties van bestellingen, facturen, verzendingen en creditnota&#39;s te verbeteren en uw werkruimte vrij te houden van onnodige informatie, zodat u zich kunt concentreren op het huidige bedrijf. Zie [&#x200B; archiveren &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/orders/order-archive) toelaten.

## Betrokken producten en versies

[&#x200B; Alle gesteunde versies &#x200B;](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## asynchrone orderverwerking inschakelen

De stappen om asynchrone ordeverwerking toe te laten hangen van de plaatsingswijze af:

- Voor Adobe Commerce op wolkeninfrastructuur en op gebiedsplaatsen op Productiemodus, gebruik het volgende CLI bevel van Magento om asynchrone indexering toe te laten:

  ```php
  php bin/magento config:set dev/grid/async_indexing 1
  ```

- Voor Adobe Commerce-sites op locatie in de modus Standaard of Productie schakelt u asynchrone indexering in door de configuratie Rasterinstellingen in Admin bij te werken.

  Zie [&#x200B; geplande netupdates en het opnieuw indexeren &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html?lang=nl-NL#enable-scheduled-grid-updates-and-reindexing) toelaten

  >[!WARNING]
  >
  >Test altijd configuratiewijzigingen in de testomgeving voordat u de productieomgeving bijwerkt.

## Aanvullende informatie

- [Best practices voor configuratie](../../../performance/configuration.md)
- [Verwijzing naar algemene en geavanceerde configuratiepaden](../../../configuration/reference/config-reference-general.md)
- [Bestelverwerking met hoge doorvoer](../../../performance/high-throughput-order-processing.md)
