---
title: Verwijzing naar verkoopconfiguratiepaden
description: Zie een lijst van waarden van de verkoopconfiguratie.
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# Verwijzing naar verkoopconfiguratiepaden

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Verkoop**.

Het [`magento app:config:dump` bevel ](../cli/export-configuration.md) schrijft deze waarden aan het gedeelde configuratiedossier, `app/etc/config.php`, dat in broncontrole zou moeten zijn. Om naar keuze om het even welke configuratiemontages met voeten te treden of gevoelige montages te plaatsen, zie [ de milieuvariabelen van het Gebruik om configuratiemontages ](override-config-settings.md#environment-variables) met voeten te treden. Dit onderwerp __ lijst [ niet gevoelige en systeem-specifieke waarden ](config-reference-sens.md).

## Verkooppaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Verkoop**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| IP van klant verbergen | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Subtotaal | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Korting | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verzending | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Belasting | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vaste productbelasting | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Eindtotaal | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cadeaukaarten | `sales/totals_sort/giftcardaccount` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Winkelkrediet | `sales/totals_sort/customerbalance` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Opnieuw ordenen toestaan | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo voor PDF Print-outs (200 x 50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo voor HTML Print View | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Adres | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inschakelen | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimumbedrag | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inclusief BTW op bedrag | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beschrijving | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout bij weergeven in winkelwagentje | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Elk adres afzonderlijk valideren in de uitchecking van meerdere adressen | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bericht van beschrijving van meerdere adressen | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout met meerdere adressen die moet worden weergegeven in winkelwagentje | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaggregeerde gegevens gebruiken | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur betalingsopdracht in behandeling (minuten) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cadeausberichten op bestelniveau toestaan | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cadeausberichten toestaan voor bestellingstitems | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gift Wrapping toestaan op bestelniveau | `sales/gift_options/wrapping_allow_order` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Gift Wrapping toestaan voor bestellingen | `sales/gift_options/wrapping_allow_items` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Cadeaubevestiging toestaan | `sales/gift_options/allow_gift_receipt` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Afgedrukte kaart toestaan | `sales/gift_options/allow_printed_card` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Standaardprijs voor afgedrukte kaart | `sales/gift_options/printed_card_price` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| KAART inschakelen | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Werkelijke prijs weergeven | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardbericht voor pop-uptekst | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardtekstbericht &quot;Wat is dit?&quot; | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bestelling door SKU inschakelen voor Mijn account in winkelcentrum | `sales/product_sku/my_account_enable` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Knoptekst | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Klantengroepen | `sales/product_sku/allowed_groups` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Archivering inschakelen | `sales/magento_salesarchive/active` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Aangeschafte archiefbestellingen | `sales/magento_salesarchive/age` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Te archiveren statussen bestellen | `sales/magento_salesarchive/order_statuses` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| RMA inschakelen op Storefront | `sales/magento_rma/enabled` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| RMA inschakelen op productniveau | `sales/magento_rma/enabled_on_product` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Winkeladres gebruiken | `sales/magento_rma/use_store_address` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## E-mailpaden verkopen

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Verkoop E-mail van de Verkoop**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Asynchroon verzenden | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender nieuwe bestelbevestiging | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sjabloon voor nieuwe orderbevestiging | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nieuwe sjabloon voor orderbevestiging voor gast | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailkopieermethode voor bestelling verzenden | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender opmerking bestellen | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor opmerkingen bestellen | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor opmerkingen bestellen voor gast | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailkopiemethode voor opmerkingen verzenden | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Factuur-e-mailafzender | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Factuur-e-mailsjabloon | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Factuur-e-mailsjabloon voor gast | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode voor e-mail met factuur verzenden | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender Factuuropmerking | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon Factuuropmerking | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon Factuuropmerking voor gast | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailkopiemethode voor Factuuropmerkingen verzenden | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender verzending | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor verzending | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor verzending voor gast | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailkopieermethode voor verzending verzenden | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender van verzendopmerking | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor verzendopmerking | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor verzendopmerking voor gast | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailkopieermethode voor verzendopmerkingen verzenden | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender creditcard | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailtemplate voor creditcard | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailtemplate voor creditcard voor gast | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailkopieermethode voor creditcard verzenden | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender Opmerking creditmemo | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon Opmerking creditcard | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor opmerking via creditcard voor gast | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailkopieermethode voor opmerkingen over creditcard verzenden | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `sales_email/magento_rma/enabled` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| RMA E-mailafzender | `sales_email/magento_rma/identity` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| RMA-e-mailsjabloon | `sales_email/magento_rma/template` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| RMA-e-mailsjabloon voor gast | `sales_email/magento_rma/guest_template` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Methode voor kopiëren via RMA-e-mail verzenden | `sales_email/magento_rma/copy_method` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `sales_email/magento_rma_auth/enabled` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| E-mailafzender RMA-autorisatie | `sales_email/magento_rma_auth/identity` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| E-mailsjabloon voor RMA-autorisatie | `sales_email/magento_rma_auth/template` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| E-mailsjabloon voor RMA-autorisatie voor gast | `sales_email/magento_rma_auth/guest_template` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Kopieermethode voor RMA-autorisatie verzenden | `sales_email/magento_rma_auth/copy_method` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `sales_email/magento_rma_comment/enabled` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| RMA E-mailafzender opmerking | `sales_email/magento_rma_comment/identity` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| E-mailsjabloon voor RMA-opmerkingen | `sales_email/magento_rma_comment/template` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| E-mailsjabloon voor RMA-opmerkingen voor gast | `sales_email/magento_rma_comment/guest_template` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Methode voor kopiëren via RMA-e-mail verzenden | `sales_email/magento_rma_comment/copy_method` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `sales_email/magento_rma_customer_comment/enabled` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| RMA E-mailafzender opmerking | `sales_email/magento_rma_customer_comment/identity` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| E-mailontvanger voor RMA-opmerkingen | `sales_email/magento_rma_customer_comment/recipient` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| E-mailsjabloon voor RMA-opmerkingen | `sales_email/magento_rma_customer_comment/template` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Methode voor kopiëren via RMA-e-mail verzenden | `sales_email/magento_rma_customer_comment/copy_method` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Order-id weergeven in koptekst | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Order-id weergeven in koptekst | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Order-id weergeven in koptekst | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Belastingpaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Belasting**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Belastingklasse voor verzending | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Belastingsklasse voor Cadeauopties | `tax/classes/wrapping_tax_class` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Standaardbelastingklasse voor product | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardbelastingklasse voor klant | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Belastingberekeningsmethode gebaseerd op | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Belastingberekening op basis van | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Catalogusprijzen | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verzendprijzen | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Klantenbelasting toepassen | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Korting op prijzen toepassen | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Belasting toepassen op | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grensoverschrijdende handel inschakelen | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardland | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardstatus | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaard Post-code | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Productprijzen weergeven in catalogus | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verzendprijzen weergeven | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prijzen weergeven | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Subtotaal weergeven | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verzendbedrag weergeven | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wapprijzen voor geschenk weergeven | `tax/cart_display/gift_wrapping` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Afgedrukte kaartprijzen weergeven | `tax/cart_display/printed_card` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Inclusief BTW in besteltotaal | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Volledige belastingoverzicht weergeven | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Subtotaal btw-nul weergeven | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prijzen weergeven | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Subtotaal weergeven | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verzendbedrag weergeven | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wapprijzen voor geschenk weergeven | `tax/sales_display/gift_wrapping` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Afgedrukte kaartprijzen weergeven | `tax/sales_display/printed_card` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Inclusief BTW in besteltotaal | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Volledige belastingoverzicht weergeven | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Subtotaal btw-nul weergeven | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT inschakelen | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prijzen weergeven in productlijsten | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prijzen weergeven op de pagina Productweergave | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prijzen weergeven in verkoopmodules | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prijzen in e-mails weergeven | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Belasting toepassen op FPT | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| FPT opnemen in subtotaal | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Paden uitchecken

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Controle**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Afhandeling op één pagina inschakelen | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uitchecken door gasten toestaan | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Factuuradres weergeven op | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Voorwaarden en bepalingen inschakelen | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aanbiedingslevensduur (dagen) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nadat een product is omgeleid naar winkelwagentje | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gegroepeerde productafbeelding | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configureerbare productafbeelding | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aanbiedingslevensduur voorvertonen (minuten) | `checkout/cart/preview_quota_lifetime` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Winkeloverzicht weergeven | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Winkelwagentje weergeven | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal onlangs toegevoegde items weergeven | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling is mislukt E-mailafzender | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling mislukt e-mailontvanger | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingssjabloon mislukt | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verzenden van e-mailkopieermethode met betalingsfout | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Paden met instellingen voor verzending

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Verschepende Montages**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Aangepast verzendbeleid toepassen | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verzendbeleid | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Paden met meerdere instellingen

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **MultiShipping Montages**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Verzending naar meerdere adressen toestaan | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale toegestane hoeveelheid voor verzending naar meerdere adressen | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Paden van leveringsmethoden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Methoden van de Levering**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Ingeschakeld | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Naam methode | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prijs | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten berekenen | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutbericht weergeven | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar landen van toepassing | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar specifieke landen | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode tonen indien niet van toepassing | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Naam methode | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimumbedrag bestelling | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutbericht weergeven | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar landen van toepassing | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar specifieke landen | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode tonen indien niet van toepassing | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Naam methode | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Voorwaarde | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Virtuele producten opnemen in prijsberekening | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Exporteren | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importeren | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten berekenen | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutbericht weergeven | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar landen van toepassing | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar specifieke landen | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode tonen indien niet van toepassing | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld voor Afhandeling | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld voor RMA | `carriers/ups/active_rma` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Type UPS | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modus | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Oorsprong van de overbrenging | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gateway-URL | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Onderhandelde tarieven inschakelen | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type pakketaanvraag | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Container | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtseenheid | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Doeltype | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale pakketgewicht (Neem contact op met uw verzendende provider voor maximaal ondersteund verzendgewicht) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ophaalmethode | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimumgewicht van pakket (Neem contact op met uw verzendende maatschappij voor minimaal ondersteund verzendgewicht) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten berekenen | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegepaste afhandeling | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegestane methoden | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vrije methode | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gratis verzenddrempel inschakelen | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Drempel voor gratis verzendbedrag | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutbericht weergeven | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar landen van toepassing | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar specifieke landen | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode tonen indien niet van toepassing | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld voor Afhandeling | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld voor RMA | `carriers/usps/active_rma` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Modus | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type pakketaanvraag | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Container | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grootte | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lengte | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Breedte | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hoogte | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meisje | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bewerkbaar | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale pakketgewicht (Neem contact op met uw verzendende provider voor maximaal ondersteund verzendgewicht) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten berekenen | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegepaste afhandeling | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegestane methoden | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vrije methode | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gratis verzenddrempel inschakelen | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Drempel voor gratis verzendbedrag | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutbericht weergeven | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar landen van toepassing | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar specifieke landen | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode tonen indien niet van toepassing | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld voor Afhandeling | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld voor RMA | `carriers/fedex/active_rma` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Titel | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL van webservices (productie) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL voor webservices (sandbox) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type pakketaanvraag | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verpakken | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dropoff | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtseenheid | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale pakketgewicht (Neem contact op met uw verzendende provider voor maximaal ondersteund verzendgewicht) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten berekenen | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegepaste afhandeling | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingezetenschap | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegestane methoden | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hub-id | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vrije methode | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gratis verzenddrempel inschakelen | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Drempel voor gratis verzendbedrag | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutbericht weergeven | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar landen van toepassing | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar specifieke landen | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode tonen indien niet van toepassing | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld voor Afhandeling | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld voor RMA | `carriers/dhl/active_rma` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Titel | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Inhoudstype | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten berekenen | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegepaste afhandeling | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verhandelingskosten | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dikte van volgorde splitsen | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewichtseenheid | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grootte | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hoogte | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Diepte | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Breedte | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegestane methoden | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegestane methoden | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Klaar tijd | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutbericht weergeven | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vrije methode | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vrije methode | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gratis verzenddrempel inschakelen | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Drempel voor gratis verzendbedrag | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar landen van toepassing | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schip naar specifieke landen | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Methode tonen indien niet van toepassing | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Google API-paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Google API**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Inschakelen | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Accounttype | `google/analytics/type` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Inhoud-experimenten inschakelen | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Eigenschap List voor de cataloguspagina | `google/analytics/catalog_page_list_value` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| List, eigenschap voor het blok voor cross-sell | `google/analytics/crosssell_block_list_value` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| De bezit van de lijst voor het up-sell blok | `google/analytics/upsell_block_list_value` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Eigenschap List voor het verwante productblok | `google/analytics/related_block_list_value` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| De eigenschap List voor de pagina met zoekresultaten | `google/analytics/search_page_list_value` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| &#39;Interne aanbiedingen&#39; voor promoties in het veld &#39;Label&#39;. | `google/analytics/promotions_list_value` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Inschakelen | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conversie-id | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conversietaal | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conversie-indeling | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conversiekleur | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conversielabel | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Type omzetwaarde | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conversiewaarde | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Cadeaupaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **de Kaarten van het Cadeautje**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| E-mailafzender e-mailbericht voor creditcard | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor kennisgeving van creditcard | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Terugbetaalbaar | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur (dagen) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cadeaubericht toestaan | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale lengte geschenk | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Creditcardaccount genereren wanneer bestelitem is | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender creditcard | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cadeausjabloon | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lengte code | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codeopmaak | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codevoorvoegsel | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codeachtervoegsel | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Streep om de X-tekens | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nieuwe groepsgrootte | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Drempel lage codepool | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
