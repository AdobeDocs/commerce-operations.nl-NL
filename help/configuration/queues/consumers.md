---
title: Gebruikers in de wachtrij met berichten
description: Meer informatie over gebruikers in de wachtrij met Adobe Commerce-berichten, waaronder de functies en systeemconfiguratie die aan deze gebruikers zijn gekoppeld.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Gebruikers in de wachtrij met berichten

De volgende lijst identificeert alle consumenten van de berichtrij, beschrijft wat zij doen, en identificeert de montages van de Admin systeemconfiguratie verbonden aan hen:

| Consumenten en beschrijving | Adobe Commerce | Adobe Commerce met B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Creeert berichten voor elke individuele taak van a [ bulkverrichting ](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), zoals het invoeren van of het uitvoeren van punten, het veranderen van prijzen op een massa schaal, en het toewijzen van producten aan een pakhuis. Vereist wanneer de optie [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) is ingesteld op **[!UICONTROL Run asynchronously]**&#x200B;in de configuratie-instellingen van het beheersysteem. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Hiermee genereert u asynchroon coupons op de achtergrond. Vereist om de [&#128279;](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) eigenschap van de de partijcoupon van 0&rbrace; te gebruiken. |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Controleert gebeurtenissen die als prioriteit in [ Gebeurtenissen van de Adobe I/O voor Adobe Commerce ](https://developer.adobe.com/commerce/events/get-started/) zijn geregistreerd. |
| `exportProcessor` | + | + | + |
| Verhindert verbindingsonderbrekingen tijdens de [ uitvoer ](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) van grote gegevensreeksen (bijvoorbeeld 200.000 producten). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corrigeert asynchroon de aandelenindex nadat een bestelling is geplaatst of een product is verwijderd. Vereist wanneer de optie [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#product-stock-options) in de montages van de Configuratie Admin wordt toegelaten. Zie [ Beste praktijken van Prestaties ](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Verwijdert asynchroon bronitems op product-SKU wanneer een product wordt verwijderd. Vereist wanneer de [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) voorraadoptie in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Verwerkt asynchroon verouderde voorraadpunten, werkt erfenis voorraadpunten bij, werkt standaardbronpunten bij, en herindexeert inventaris voor specifieke product SKUs. Vereist wanneer de [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) bulkverrichting in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Verwijdert asynchroon reserveringen door product SKU nadat een product wordt verwijderd. Vereist wanneer de [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) voorraadoptie in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Asynchroon werkt reserveringen door product SKU bij nadat een product wordt verwijderd. Vereist wanneer de [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory) voorraadoptie in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Hiermee werkt u de verkoopbare hoeveelheid van elk product dat aan een voorraad is toegewezen synchroon bij. Deze consument moet altijd actief zijn als u [!DNL Inventory Management] gebruikt. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Wisselt asynchroon bronitems opnieuw uit. Vereist wanneer [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) aan &quot;[!UICONTROL asynchronous]&quot;in de montages van de het systeemconfiguratie Admin wordt geplaatst. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Wederdexeert de voorraad asynchroon. Vereist wanneer [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/en/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) aan &quot;[!UICONTROL asynchronous]&quot;in de montages van de het systeemconfiguratie Admin wordt geplaatst. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Creeert een tijdelijke gegevensbestandlijst, beweegt elk [ klantensegment ](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) in het, schrapt alle segmenten die segmentidentiteitskaart aanpassen, en kopieert hen aan de klantensegmenten gebruikend segmentidentiteitskaart als indicator. Dit wordt allen gedaan in een transactie zodat als iets ontbreekt, het de transactie terugdraait aan wat het was vóór dit uitgevoerd. Na een transactie laat de consument de tijdelijke tabel vallen. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Hiermee zorgt u ervoor dat koppelingen naar toegewezen media voor producten, categorieën, CMS-blokken en CMS-pagina&#39;s correct worden toegewezen aan het element. Hiermee verwijdert u oude elementen die niet meer worden gebruikt. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Hiermee genereert en valideert u paden voor media-elementen. Het absolute pad naar een element wordt bepaald door de locatie op de server vanuit de mediamap. Afbeeldingen worden vergroot of verkleind (indien nodig) en naar de mediamap in het gegenereerde pad gekopieerd. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Hiermee importeert u afbeeldingsbestanden naar de databasetabel `media_gallery_asset` . |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| Asynchroon [ resizes ](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) catalogusbeelden. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Prijzen voor verhandelbare koersen worden bijgewerkt. Vereist wanneer de optie [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| Asynchroon [ verwerkt orden ](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), die orden zoals ontvangen merken, hen in de berichtrij plaatsen, en verwerkt hen in een eerste-in-eerste-uit basis. Overweeg a [ beste praktijken ](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) voor het verbeteren van het aantal orden die kunnen worden verwerkt omdat de klanten niet op backendprocessen hoeven te wachten om te voltooien alvorens een succesbericht te zien. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Asynchroon schrijft veranderingen in productkenmerken in het gegevensbestand na het gebruiken van Admin om [ updates ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html) te maken. |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Asynchroon schrijft veranderingen in productkenmerken voor een specifieke opslagmening in het gegevensbestand na het gebruiken van Admin aan [ updates ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html) maken. |                |                         |                     |
| `product_alert` | + | + | + |
| Hiermee stuurt u klanten e-mailberichten over productprijzen en voorraadwijzigingen. Vereist als de optie Vereist is wanneer de optie [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) is ingeschakeld in de configuratie-instellingen van het beheersysteem. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Zet kooporde in [ orde ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules) om. Vereist wanneer de optie [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Verzendt e-mails met inkooporder. Vereist wanneer de optie [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Valideert kooporder tegen relevante [ goedkeuringsregels ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules). Vereist wanneer de optie [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Slaat asynchroon de veranderingen van de opslagconfiguratie door sparen banen in een berichtrij te plaatsen op, die prestaties op plaatsingen kan verbeteren die een groot aantal opslag-vlakke configuraties bevatten. Vereist om de module [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) te gebruiken. |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Voorkomt een uitgifte waarbij coupons voor eenmalig gebruik meerdere keren kunnen worden gebruikt. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Hiermee werkt u categorieën bij die zijn toegewezen aan een gedeelde cataloguscategorie. Vereist wanneer de optie [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Hiermee werkt u de prijs bij voor elk product in een gedeelde catalogus. Vereist wanneer de optie [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Hiermee verwijdert u ongeldige of inactieve prijsaanhalingstekens wanneer een product uit de catalogus wordt verwijderd of uit het winkelwagentje wordt verwijderd. Vereist wanneer de optie [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/quotes/quotes) in de montages van de de systeemconfiguratie van Admin wordt toegelaten. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Hiermee werkt u actieve winkelwagentjes bij om de wijzigingen in de regels voor de winkelwagenprijs weer te geven. Vereist bij het bijwerken van [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
