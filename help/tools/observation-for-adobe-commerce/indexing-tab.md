---
title: '"De [!UICONTROL Indexing] tab"'
description: Meer informatie over de [!UICONTROL Indexing] tabblad van [!DNL Observation for Adobe Commerce].
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# De [!UICONTROL Indexing] tab

De **[!UICONTROL Indexing]** het lusje probeert om kwesties met het indexeren te verklaren en potentiële oorzaken te identificeren.

## [!UICONTROL Core index invalidated]

![Core index is ongeldig](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

De **[!UICONTROL Core index invalidated]** frame bekijkt het indexeren van validatie over een geselecteerd tijdkader. Als het indexeren tezelfdertijd zoals andere middel-intensieve kronen gebeurt, zal het een zware lading op de plaatshulpmiddelen plaatsen.

* &#39;%Catalog Product Rule indexer is ongeldig gemaakt%&#39;) als &#39;catalog_product_rule_idx_reset&#39;
* &#39;%Catalog Rule Product indexer is ongeldig gemaakt%&#39;) als &#39;catalog_rule_product_idx_reset&#39;
* &#39;%Catalog Search indexer is ongeldig gemaakt%&#39;) als &#39;catalog_search_idx_reset&#39;
* &#39;%Categorie Producten indexer is ongeldig gemaakt%&#39;) als &#39;category_products_idx_reset&#39;
* &#39;%Klantenraster-index is ongeldig gemaakt%&#39;) als &#39;customer_grid_idx_reset&#39;
* &#39;%Design Config Grid indexer is ongeldig gemaakt%&#39;) als &#39;design_config_grid_idx_
* &#39;%Product Categories indexer is ongeldig gemaakt%&#39;) als &#39;product_category_idx_reset&#39;
* &#39;%Product EAV-indexeerprogramma is ongeldig gemaakt%&#39;) als &#39;product_eav_idx_reset&#39;
* &#39;%Product Price indexer has been invalidate%&#39;) as &#39;product_price_idx_reset&#39;
* &#39;%Stock-indexer is ongeldig gemaakt%&#39;) als &#39;stock_idx_reset&#39;
* &#39;%Inventory indexer is ongeldig gemaakt%&#39;) als &#39;voorraad_idx_reset&#39;
* &#39;%Inventory indexer is ongeldig gemaakt%&#39;) als &#39;voorraad_idx_reset&#39;
* &#39;%Sales Rule indexer is ongeldig gemaakt%&#39;) als &#39;sales_rule_idx_reset&#39;

## [!UICONTROL Core index rebuilds]

![Herbouw van de kernindex](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

De **[!UICONTROL Core index rebuilds]** frame bekijkt de rebuilds van de kernindex over een geselecteerd tijdkader. Hier volgen de tekenreeksen die vanuit de logbestanden worden geparseerd om aan te geven dat de index opnieuw is samengesteld.

* &#39;%Catalog Product Rule-index is opnieuw samengesteld%&#39;) als &#39;catalog_product_rule_idx&#39;
* &#39;%Catalog Rule Product Index has been rebuilt%&#39;) as &#39;catalog_rule_product_idx
* &#39;%Catalog Search index has been rebuilt%&#39;) as &#39;catalog_search_idx&#39;
* &#39;%Categorie Producten index is opnieuw samengesteld (%&#39;) als &#39;category_products_idx&#39;
* &#39;%index voor klantenraster is opnieuw samengesteld%&#39;) als &#39;customer_grid_idx&#39;
* &#39;%Design Config Grid-index is opnieuw samengesteld%&#39;) als &#39;design_config_grid_idx&#39;
* &#39;%Index van productcategorieën is opnieuw samengesteld%&#39;) als &#39;product_category_idx&#39;
* &#39;%Product EAV-index is opnieuw samengesteld%&#39;) als &#39;product_eav_idx&#39;
* &#39;%Product Price index has been rebuilt%&#39;) as &#39;product_price_idx&#39;
* &#39;%Stock-index is opnieuw samengesteld%&#39;) als &#39;stock_idx&#39;
* &#39;%Inventory index is opnieuw samengesteld (met succes%&#39;) als &#39;voorraad_idx&#39;
* %Product/Target-regelindex is opnieuw samengesteld (%&#39;) als &#39;prod_target_rule_idx&#39;
* &#39;%Sales Rule-index is opnieuw samengesteld (met succes%&#39;) als &#39;sales_rule_idx&#39;


## [!UICONTROL catalogsearch index table(s)]

![cataloguszoekindextabel(s)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

De **[!UICONTROL catalogsearch index table(s)]** frame bekijkt catalogusindextabellen in een geselecteerd tijdkader. In deze query wordt de duur van eventuele datastore-bewerkingen vergeleken met tabellen met &#39;%catalogsearch%&#39; in de tabelnaam.

## [!UICONTROL product index table(s)]

![productindextabel(s)](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

De **[!UICONTROL product index table(s)]** frame bekijkt de tabellen van de productindex over een geselecteerd tijdsbestek. In deze query wordt de duur van eventuele datastore-bewerkingen vergeleken met tabellen met &#39;%product%&#39; in de tabelnaam.
