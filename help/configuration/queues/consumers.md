---
title: Gebruikers in de wachtrij met berichten
description: Meer informatie over gebruikers in de wachtrij met Adobe Commerce- en Magento Open Source-berichten, inclusief de functies en systeemconfiguratie die eraan zijn gekoppeld.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '972'
ht-degree: 0%

---

# Gebruikers in de wachtrij met berichten

De volgende lijst identificeert alle consumenten van de berichtrij, beschrijft wat zij doen, en identificeert de montages van de Admin systeemconfiguratie verbonden aan hen:

| Consumenten en beschrijving | Adobe Commerce | Adobe Commerce met B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Hiermee maakt u berichten voor elke afzonderlijke taak van een [bulkbewerking](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), zoals het importeren of exporteren van producten, het massaal wijzigen van de prijzen en het toewijzen van producten aan een pakhuis. Vereist wanneer de [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) optie is ingesteld op **[!UICONTROL Run asynchronously]**in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| Hiermee genereert u asynchroon coupons op de achtergrond. Vereist om de [batch coupon genereren](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) gebruiken. |  |  |  |
| `commerce.eventing.event.publish` | + | + |  |
| Controleert op gebeurtenissen die als prioriteit zijn geregistreerd in [Adobe I/O Events voor Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Verhindert verbindingsonderbrekingen tijdens [export](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) van grote gegevenssets (bijvoorbeeld 200.000 producten). |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| Corrigeert asynchroon de aandelenindex nadat een bestelling is geplaatst of een product is verwijderd. Vereist wanneer de [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) Deze optie is ingeschakeld in de configuratie-instellingen voor Admin. Zie [Aanbevolen werkwijzen voor prestaties](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| Verwijdert asynchroon bronitems op product-SKU wanneer een product wordt verwijderd. Vereist wanneer de [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) De aandelenoptie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `inventory.mass.update` | + | + | + |
| Verwerkt asynchroon verouderde voorraadpunten, werkt erfenis voorraadpunten bij, werkt standaardbronpunten bij, en herindexeert inventaris voor specifieke product SKUs. Vereist wanneer de [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) bulkbewerking is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| Verwijdert asynchroon reserveringen door product SKU nadat een product wordt verwijderd. Vereist wanneer de [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) De aandelenoptie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `inventory.reservations.update` | + | + | + |
| Asynchroon werkt reserveringen door product SKU bij nadat een product wordt verwijderd. Vereist wanneer de [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) De aandelenoptie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Hiermee werkt u de verkoopbare hoeveelheid van elk product dat aan een voorraad is toegewezen synchroon bij. Deze consument moet altijd actief zijn als u [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| Wisselt asynchroon bronitems opnieuw uit. Vereist wanneer de [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) is ingesteld op &quot;[!UICONTROL asynchronous]&quot; in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| Wederdexeert de voorraad asynchroon. Vereist wanneer de [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) is ingesteld op &quot;[!UICONTROL asynchronous]&quot; in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| Maakt een tijdelijke databasetabel, verplaatst elke tabel [klantensegment](https://docs.magento.com/user-guide/marketing/customer-segments.html) in het, schrapt alle segmenten die segmentidentiteitskaart aanpassen, en kopieert hen aan de klantensegmenten gebruikend segmentidentiteitskaart als indicator. Dit wordt allen gedaan in een transactie zodat als iets ontbreekt, het de transactie terugdraait aan wat het was vóór dit uitgevoerd. Na een transactie laat de consument de tijdelijke tabel vallen. |  |  |  |
| `media.content.synchronization` | + | + | + |
| Hiermee zorgt u ervoor dat koppelingen naar toegewezen media voor producten, categorieën, CMS-blokken en CMS-pagina&#39;s correct worden toegewezen aan het element. Hiermee verwijdert u oude elementen die niet meer worden gebruikt. |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| Hiermee genereert en valideert u paden voor media-elementen. Het absolute pad naar een element wordt bepaald door de locatie op de server vanuit de mediamap. Afbeeldingen worden vergroot of verkleind (indien nodig) en naar de mediamap in het gegenereerde pad gekopieerd. |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| Hiermee importeert u afbeeldingsbestanden naar de `media_gallery_asset` databasetabel. |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| Asynchroon [resizes](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) catalogusafbeeldingen. |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| Prijzen voor verhandelbare koersen worden bijgewerkt. Vereist wanneer de [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) Deze optie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `placeOrderProcessor` | + | + |  |
| Asynchroon [procesorders](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), die orden zoals ontvangen markeren, hen in de berichtrij plaatst, en hen in een eerste-in-eerste-uit basis verwerkt. Wordt beschouwd als een [beste praktijken](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) voor het verbeteren van het aantal orden die kunnen worden verwerkt omdat de klanten niet op backendprocessen hoeven te wachten om te voltooien alvorens een succesbericht te zien. |  |  |  |
| `product_action_attribute.update` | + | + | + |
| Wijzigingen in productkenmerken in de database worden asynchroon geschreven nadat de Admin [updates uitvoeren](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| Schrijft asynchroon wijzigingen in productkenmerken voor een specifieke archiefweergave in de database nadat u de beheerfunctie hebt gebruikt voor [updates uitvoeren](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| Hiermee stuurt u klanten e-mailberichten over productprijzen en voorraadwijzigingen. Vereist wanneer de [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) Deze optie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| Hiermee converteert u een inkooporder naar [bestellen](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Vereist wanneer de [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) Deze optie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| Verzendt e-mails met inkooporder. Vereist wanneer de [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) Deze optie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `purchaseorder.validation` |  | + |  |
| Valideert kooporder op basis van relevante [goedkeuringsregels](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Vereist wanneer de [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) Deze optie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| Voorkomt de [kwestie](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) waarbij coupons voor eenmalig gebruik meerdere keren kunnen worden gebruikt. |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| Hiermee werkt u categorieën bij die zijn toegewezen aan een gedeelde cataloguscategorie. Vereist wanneer de [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) Deze optie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| Hiermee werkt u de prijs bij voor elk product in een gedeelde catalogus. Vereist wanneer de [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) Deze optie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `quoteItemCleaner` | + | + |  |
| Hiermee verwijdert u ongeldige of inactieve prijsaanhalingstekens wanneer een product uit de catalogus wordt verwijderd of uit het winkelwagentje wordt verwijderd. Vereist wanneer de [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) Deze optie is ingeschakeld in de configuratie-instellingen van het beheersysteem. |  |  |  |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Hiermee werkt u actieve winkelwagentjes bij om de wijzigingen in de regels voor de winkelwagenprijs weer te geven. Vereist bij bijwerken [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |  |  |  |

{style="table-layout:auto"}
