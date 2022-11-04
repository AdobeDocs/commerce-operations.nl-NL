---
title: Best practices voor configuratie voor verwerking van bestellingen
description: Leer best practices voor configuratie om de verwerkingsprestaties voor kassa's en bestellingen te verbeteren.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Best practices voor configuratie voor verwerking van bestellingen

Naarmate het ordervolume toeneemt op uw Commerce-sites, kunt u de prestaties van de kassa en de verwerking van de bestelling optimaliseren door de volgende opties voor winkelconfiguratie in te schakelen:

- **[!UICONTROL Asynchronous indexing]**—Laat deze optie toe om gegevensbestandsloten en vertraagde verwerking te verhinderen die kunnen voorkomen wanneer de grote aantallen orden gelijktijdig worden geplaatst.
- **[!UICONTROL Asynchronous email notifications]**—Schakel deze optie in om de prestaties bij het afrekenen te versnellen door het verzenden van afrekenings- en bestelberichten voor de verwerking van e-mailberichten met bepaalde intervallen in plaats van deze onmiddellijk te verzenden.
- **[!UICONTROL Enable Archiving]**—Schakel deze optie in om bestellingen te archiveren en databaseschijfruimte vrij te maken voor snellere verwerking van bestellingen. Zie [Archivering inschakelen](https://docs.magento.com/user-guide/sales/order-archive.html#to-enable-archiving).

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## asynchrone orderverwerking inschakelen

De stappen om asynchrone ordeverwerking toe te laten hangen van de plaatsingswijze af:

- Voor Adobe Commerce op wolkeninfrastructuur en op gebiedsplaatsen op Productiemodus, gebruik het volgende bevel van Magento CLI om asynchrone indexering toe te laten:

   ```php
   php bin/magento config:set dev/grid/async_indexing 1
   ```

- Voor Adobe Commerce-sites op locatie in de modus Standaard of Productie schakelt u asynchrone indexering in door de configuratie Rasterinstellingen in Admin bij te werken.

   Zie [Updates en opnieuw indexeren van het geplande raster inschakelen](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations.html#enable-scheduled-grid-updates-and-reindexing)

   >[!WARNING]
   >
   >Test altijd configuratiewijzigingen in de testomgeving voordat u de productieomgeving bijwerkt.

## Aanvullende informatie

- [Best practices voor configuratie](../../../performance/configuration.md)
- [Verwijzing naar algemene en geavanceerde configuratiepaden](../../../configuration/reference/config-reference-general.md)
- [Bestelverwerking met hoge doorvoer](../../../performance/high-throughput-order-processing.md)