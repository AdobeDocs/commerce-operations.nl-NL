---
title: Het tabblad [!UICONTROL Indexing]
description: Leer meer over het [!UICONTROL Indexing] lusje van  [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Het tabblad [!UICONTROL Indexing]

Het tabblad **[!UICONTROL Indexing]** probeert problemen met indexering uit te leggen en mogelijke oorzaken vast te stellen.

## [!UICONTROL Core index invalidated]

![&#x200B; ongeldig gemaakte index van de Kern &#x200B;](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

In het frame **[!UICONTROL Core index invalidated]** wordt de indexering van de validatie binnen een geselecteerd tijdkader weergegeven. Als indexering plaatsvindt op hetzelfde moment als andere bronnenintensieve [!DNL crons] , wordt de site zwaar belast.

* `%Catalog Product Rule indexer has been invalidated%`) als `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) als `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) als `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) als `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) als `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) als `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) als `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) als `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) als `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) als `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) als `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) als `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) als `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![&#x200B; de indexherbouwt van de Kern &#x200B;](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

Het frame **[!UICONTROL Core index rebuilds]** bekijkt de rebuilds van de kernindex over een geselecteerd tijdkader. Hier volgen de tekenreeksen die vanuit de logbestanden worden geparseerd om aan te geven dat de index opnieuw is samengesteld.

* `%Catalog Product Rule index has been rebuilt%`) als `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) als `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) als `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) als `category_products_idx`
* `%Customer Grid index has been rebuilt%`) als `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) als `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) als `product_categories_idx`
* `%Product EAV index has been rebuilt%`) als `product_eav_idx`
* `%Product Price index has been rebuilt%`) als `product_price_idx`
* `%Stock index has been rebuilt%`) als `stock_idx`
* `%Inventory index has been rebuilt successfully%`) als `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) als `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) als `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![&#x200B; lijst(en) van de cataloguszoekindex van de catalogi &#x200B;](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

Het frame **[!UICONTROL catalogsearch index table(s)]** bekijkt cataloguszoekindextabellen in een geselecteerd tijdkader. In deze query wordt gekeken naar de duur van eventuele datastore-bewerkingen ten opzichte van tabellen met `%catalogsearch%` in de tabelnaam.

## [!UICONTROL product index table(s)]

![&#x200B; lijst(en) van de productindex &#x200B;](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

In het frame **[!UICONTROL product index table(s)]** wordt gekeken naar de tabellen met de productindex voor een geselecteerd tijdsbestek. In deze query wordt gekeken naar de duur van eventuele datastore-bewerkingen ten opzichte van tabellen met `%product%` in de tabelnaam.
