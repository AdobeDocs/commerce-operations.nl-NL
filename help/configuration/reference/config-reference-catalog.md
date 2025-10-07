---
title: Verwijzing naar catalogusconfiguratiepaden
description: Meer informatie over configuratiepaden en waarden voor catalogi vindt u in Adobe Commerce Admin-instellingen. Ontdek de configuratieopties voor product-, categorie- en catalogusbeheer.
feature: Configuration, Catalog Management
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '845'
ht-degree: 0%

---

# Verwijzing naar catalogusconfiguratiepaden

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Catalogus** op.

Het [`magento app:config:dump` bevel &#x200B;](../cli/export-configuration.md) schrijft deze waarden aan het gedeelde configuratiedossier, `app/etc/config.php`, dat in broncontrole zou moeten zijn. Om naar keuze om het even welke configuratiemontages met voeten te treden of gevoelige montages te plaatsen, zie [&#x200B; de milieuvariabelen van het Gebruik om configuratiemontages &#x200B;](override-config-settings.md#environment-variables) met voeten te treden. Dit onderwerp __ lijst [&#x200B; niet gevoelige en systeem-specifieke waarden &#x200B;](config-reference-sens.md).

## Cataloguspaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Catalogus** > **Catalogus**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Masker voor SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Masker voor Meta-titel | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Masker voor Meta-trefwoorden | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Masker voor Meta-beschrijving | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lijstmodus | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Producten per pagina op raster Toegestane waarden | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Producten per pagina op standaardwaarde van raster | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Producten per pagina in lijst met toegestane waarden | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Producten per pagina op standaardwaarde lijst | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aanbieding sorteren op | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle producten per pagina toestaan | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vlakke catalogus gebruiken | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plat catalogusproduct gebruiken | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stalen per product | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gasten toestaan beoordelingen te schrijven | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Waarschuwing toestaan bij wijziging van productprijs | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon Prijswaarschuwing | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Waarschuwing toestaan wanneer product weer in voorraad komt | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor voorraadwaarschuwing | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender waarschuwen | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequentie | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Begintijd | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout in e-mailafzender | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout in e-mailsjabloon | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergeven voor huidige | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaard aantal onlangs bekeken producten | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaard aantal onlangs vergeleken producten | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Basisvideo automatisch starten | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gerelateerde video weergeven | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Video automatisch opnieuw starten | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bereik catalogusprijs | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardproductprijs | `catalog/price/default_product_price` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Aantal producten weergeven | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prijsnavigatiestapberekening | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Navigatiestap standaardprijs | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prijsinterval als één prijs weergeven | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal prijsintervallen | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limiet intervaldivisie | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale diepte | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimale lengte query | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale lengte query | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zoekmachine | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Time-out Solr-server | `catalog/search/solr_server_timeout` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Indexeringsmodus | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zoeksuggesties inschakelen | `catalog/search/search_suggestion_enabled` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Aantal zoeksuggesties | `catalog/search/search_suggestion_count` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Aantal resultaten tonen voor elke suggestie | `catalog/search/search_suggestion_count_results_enabled` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Zoekaanbevelingen inschakelen | `catalog/search/search_recommendations_enabled` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Aantal zoekaanbevelingen | `catalog/search/search_recommendations_count` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Aantal resultaten tonen voor elke aanbeveling | `catalog/search/search_recommendations_count_results_enabled` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Minimale voorwaarden | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL voor &quot;categorie/product&quot; genereren Herschrijvingen | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Algemene zoektermen | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Achtervoegsel URL product | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Achtervoegsel categorie-URL | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Categoriepad gebruiken voor product-URL&#39;s | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Permanente omleiding maken voor URL&#39;s als URL-sleutel is gewijzigd | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Scheidingsteken paginatitel | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meta-tag voor canonieke koppeling gebruiken voor categorieën | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meta-tag voor Canonical Link gebruiken voor producten | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inschakelen | `catalog/magento_catalogpermissions/enabled` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Browsercategorie toestaan | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Klantengroepen | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Openingspagina | `catalog/magento_catalogpermissions/restricted_landing_page` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Productprijzen weergeven | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Klantengroepen | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Toevoegen aan winkelwagentje toestaan | `catalog/magento_catalogpermissions/grant_checkout_items` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Klantengroepen | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Cataloguszoekopdracht niet toestaan op | `catalog/magento_catalogpermissions/deny_catalog_search` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Itemstatus bestellen om downloads in te schakelen | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardmaximum aantal downloads | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aandeelbaar | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardvoorbeeldtitel | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardkoppelingstitel | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Koppelingen openen in nieuw venster | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inhoud verplaatsen gebruiken | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uitchecken door gasten uitschakelen als winkelwagentje downloadbare items bevat | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript-kalender gebruiken | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Volgorde datumvelden | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tijdnotatie | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bereik jaar | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Functionaliteit van catalogusgebeurtenissen inschakelen | `catalog/magento_catalogevent/enabled` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Widget Catalog-gebeurtenis inschakelen in Storefront | `catalog/magento_catalogevent/lister_output` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Aantal gebeurtenissen dat moet worden weergegeven in de widget Gebeurtenisregelaar | `catalog/magento_catalogevent/lister_widget_limit` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Per klik te schuiven gebeurtenissen in de widget Gebeurtenisregelaar | `catalog/magento_catalogevent/lister_widget_scroll` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Maximumaantal producten in lijst Verwante producten | `catalog/magento_targetrule/related_position_limit` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Verwante producten tonen | `catalog/magento_targetrule/related_position_behavior` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Rotatiemodus voor producten in de lijst Verwante producten | `catalog/magento_targetrule/related_rotation_mode` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal producten in de lijst voor producten voor meerdere verkooptransacties | `catalog/magento_targetrule/crosssell_position_limit` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Crosssellproducten tonen | `catalog/magento_targetrule/crosssell_position_behavior` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Rotatiemodus voor producten in de productlijst voor meerdere verkooppunten | `catalog/magento_targetrule/crosssell_rotation_mode` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Maximumaantal producten in lijst Upsell-producten | `catalog/magento_targetrule/upsell_position_limit` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Upselproducten weergeven | `catalog/magento_targetrule/upsell_position_behavior` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Rotatiemodus voor producten in Upsell-productlijst | `catalog/magento_targetrule/upsell_rotation_mode` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Inventarisatiepaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Catalogus** > **Voorraad**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Aantal verkleinen wanneer bestelling wordt geplaatst | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| De status van de items instellen op In voorraad bij annulering van bestelling | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Producten uit voorraad weergeven | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alleen X-linkerdrempel | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beschikbaarheid van producten in voorraad weergeven in winkel | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Synchroniseren met catalogus | `cataloginventory/options/synchronize_with_catalog` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Stock beheren | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Achtergronden | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uitgestelde voorraadupdate gebruiken | `cataloginventory/item_options/use_deferred_stock_update` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Maximale toegestane hoeveelheid in winkelwagentje | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Drempel voor voorraden | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimale toegestane hoeveelheid in winkelwagentje | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Melden voor hoeveelheid onder | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aantal verhogen inschakelen | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aantal toenamen | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Creditpost automatisch naar voorraad retourneren | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| asynchroon uitvoeren | `cataloginventory/bulk_operations/async` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Asynchrone batchgrootte | `cataloginventory/bulk_operations/batch_size` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Provider | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rekenmodus | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Waarde | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Visuele Merchandiserpaden

[!BADGE &#x200B; slechts PaaS &#x200B;]{type=Informative url="https://experienceleague.adobe.com/nl/docs/commerce/user-guides/product-solutions" tooltip="Is alleen van toepassing op Adobe Commerce op Cloud-projecten (door Adobe beheerde PaaS-infrastructuur) en op projecten in het veld."}

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Catalogus** > **Visuele Merchandiser**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Zichtbare kenmerken voor categorieregels | `visualmerchandiser/options/smart_attributes` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Minimale voorraaddrempel | `visualmerchandiser/options/minimum_stock_threshold` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Kleurkenmerkcode | `visualmerchandiser/options/color_attribute_code` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |
| Kleurvolgorde | `visualmerchandiser/options/color_order` | ![&#x200B; Commerce-slechts &#x200B;](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## XML-sitemappaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Sporen** > Montages > **Configuratie** > **Catalogus** > **Sitemap van XML**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Frequentie | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioriteit | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequentie | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioriteit | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afbeeldingen toevoegen aan Sitemap | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequentie | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prioriteit | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Begintijd | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequentie | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout in e-mailafzender | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout in e-mailsjabloon | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal URL&#39;s per bestand | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale bestandsgrootte | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verzending naar Robots.txt inschakelen | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## RSS feeds, paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Catalogus** > **RSS van voer**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| RSS inschakelen | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| RSS inschakelen | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nieuwe producten | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Speciale producten | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Coupons/Kortingen | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Categorie op hoofdniveau | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kennisgeving van status van klant | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## E-mailen naar vriendenpaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Catalogus** > **E-mail aan een Vriend**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Ingeschakeld | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon selecteren | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gasten toestaan | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Max. ontvangers | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximaal aantal verzonden producten binnen 1 uur | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verzenden beperken met | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
