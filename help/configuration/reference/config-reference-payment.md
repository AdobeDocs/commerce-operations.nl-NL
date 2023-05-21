---
title: Verwijzing naar betalingspaden
description: Zie een lijst met configureerbare waarden voor betalingsmethoden.
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# Verwijzing naar betalingspaden

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Verkoop** > **Betalingsmethoden**.

De [`magento app:config:dump` command](../cli/export-configuration.md) deze waarden naar het gedeelde configuratiebestand schrijft, `app/etc/config.php`, die onder broncontrole moeten staan. Om naar keuze om het even welke configuratiemontages met voeten te treden of gevoelige montages te plaatsen, zie [Omgevingsvariabelen gebruiken om configuratie-instellingen te overschrijven](override-config-settings.md#environment-variables). Dit onderwerp doet _niet_ list [gevoelige en systeemspecifieke waarden](config-reference-sens.md).

De instellingen worden verder geordend via betalingsmethode.

## Paden van PayPal

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Deze oplossing inschakelen | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| In-Context Checkout-ervaring inschakelen | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-krediet inschakelen | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-krediet inschakelen | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergave | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Positie | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grootte | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergave | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Positie | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grootte | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergave | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Positie | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grootte | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergave | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Positie | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grootte | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergeven op pagina met productdetails | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergeven bij winkelwagentje | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling van toepassing vanaf | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingen in landen van toepassing uit | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-verificatie inschakelen | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Objecten met winkelwagentjes overdragen | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Revisiestap bestelling overslaan | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Objecten met winkelwagentjes overdragen | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opties voor verzending | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Shortcut Buttons Flavis | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uitchecken van PayPal-gasten inschakelen | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Factureringsadres van klant vereisen | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opname factureringsovereenkomst | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling van toepassing vanaf | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingen in landen van toepassing uit | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-verificatie inschakelen | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Objecten met winkelwagentjes overdragen | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wizard Factureringsovereenkomst toestaan | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch ophalen inschakelen | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Schema | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dag | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-productlogo | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paginastijl | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL koptekstafbeelding | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Achtergrondkleur koptekst | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Randkleur koptekst | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Achtergrondkleur pagina | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Deze oplossing inschakelen | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-creditering van betalingsopdracht sorteren | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergeven op pagina met productdetails | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Erkenningsperiode (dagen) | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geldige periode bestellen (dagen) | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aantal vergunningen voor kinderen | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergeven bij winkelwagentje | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling van toepassing vanaf | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingen in landen van toepassing uit | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-verificatie inschakelen | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payments Pro

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| API-verificatiemethoden | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| API gebruikt proxy | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Verenigd Koninkrijk)

Deze opties zijn alleen beschikbaar als u het Verenigd Koninkrijk als de [handelsland](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Deze oplossing inschakelen | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uitdrukkelijke afhandeling weergeven in de stap Betalingsgegevens | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling van toepassing vanaf | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingen in landen van toepassing uit | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-verificatie inschakelen | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Vault ingeschakeld | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vault-titel | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegestane creditcardtypen | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling van toepassing vanaf | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingen in landen van toepassing uit | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-verificatie inschakelen | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-item vereisen | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transactie afwijzen als: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS Street does not match | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| AVS ZIP komt niet overeen | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| De internationale AVS-indicator komt niet overeen | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| De beveiligingscode van de kaart komt niet overeen | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverancier | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Proxy gebruiken | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partner | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverancier | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Proxy gebruiken | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Deze oplossing inschakelen | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling van toepassing vanaf | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingen in landen van toepassing uit | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-verificatie inschakelen | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-item is bewerkbaar | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-item vereisen | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailbevestiging verzenden | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Link

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Partner | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Leverancier | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Enable Payflow Link | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uitdrukkelijke afhandeling inschakelen | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-creditering van betalingsopdracht sorteren | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling van toepassing vanaf | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingen in landen van toepassing uit | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SSL-verificatie inschakelen | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-item is bewerkbaar | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CVV-item vereisen | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailbevestiging verzenden | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Paden voor subtotaal uitchecken nul

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Ingeschakeld | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Betalingspaden onder rembours

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Ingeschakeld | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Betalingspaden voor overschrijvingen

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Ingeschakeld | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Paden voor cheque of postwissel

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Ingeschakeld | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaalbaar maken voor | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Paden inkooporder

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Ingeschakeld | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Internationale paden

>[!INFO]
>
>De beschikbare paden worden bepaald door uw keuze uit [Merchant Land](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Naam | Config-pad | Alleen handel? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| SFTP-referenties | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Deze oplossing inschakelen | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Creditcardinstellingen | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transactie afwijzen als: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaalbaar maken voor | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Controle verzenden naar | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_nz/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_nz/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_nz/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van nieuwe bestelling | `payment_nz/cybersource/order_status` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_nz/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_nz/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_nz/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_nz/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_nz/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_nz/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_nz/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_nz/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_nz/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_nz/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_nz/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Handtekeningvelden | `payment_nz/worldpay/signature_fields` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_nz/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_nz/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_nz/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_nz/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_nz/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_nz/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_nz/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_nz/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_nz/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_nz/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_nz/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_nz/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_nz/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_nz/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_nz/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_nz/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_nz/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_hk/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_hk/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_hk/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van nieuwe bestelling | `payment_hk/cybersource/order_status` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_hk/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_hk/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_hk/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_hk/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_hk/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_hk/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_hk/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_hk/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_hk/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_hk/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_hk/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_hk/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_hk/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_hk/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_hk/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_hk/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_hk/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_hk/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_hk/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_hk/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_hk/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_hk/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sandbox-modus | `payment_hk/eway/sandbox_flag` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_hk/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_hk/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_hk/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_hk/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_hk/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_hk/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaalbaar maken voor | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_es/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_es/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_es/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Profiel-id | `payment_es/cybersource/profile_id` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) | ![Gecodeerd](/help/assets/configuration/cloud-enc.png) |
| Status van nieuwe bestelling | `payment_es/cybersource/order_status` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_es/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_es/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_es/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_es/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_es/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_es/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_es/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_es/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_es/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Installatie-id | `payment_es/worldpay/installation_id` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Installatie-id voor extern beheer | `payment_es/worldpay/admin_installation_id` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_es/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_es/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Handtekeningvelden | `payment_es/worldpay/signature_fields` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Testmodus | `payment_es/worldpay/sandbox_flag` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_es/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_es/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_es/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_es/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_es/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_es/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_es/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_es/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_es/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_es/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_es/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_es/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_es/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_es/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_es/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_es/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_it/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_it/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_it/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van nieuwe bestelling | `payment_it/cybersource/order_status` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_it/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_it/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_it/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_it/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_it/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_it/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_it/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_it/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_it/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_it/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_it/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Handtekeningvelden | `payment_it/worldpay/signature_fields` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_it/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_it/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_it/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_it/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_it/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_it/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_it/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_it/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_it/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_it/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_it/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_it/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_it/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_it/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_it/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_it/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_it/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_fr/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_fr/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_fr/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van nieuwe bestelling | `payment_fr/cybersource/order_status` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_fr/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_fr/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_fr/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_fr/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_fr/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_fr/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_fr/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_fr/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_fr/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_fr/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_fr/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_fr/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_fr/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_fr/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_fr/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_fr/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_fr/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_fr/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_fr/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_fr/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_fr/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_fr/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_fr/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_fr/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_fr/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_fr/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_fr/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_fr/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_jp/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_jp/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_jp/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_jp/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_jp/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_jp/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_jp/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_jp/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_jp/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_jp/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_jp/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_jp/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_jp/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_jp/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_jp/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_jp/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_jp/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_jp/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_jp/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_jp/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_jp/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_jp/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_jp/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_jp/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_jp/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_jp/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_jp/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_jp/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_jp/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_jp/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_jp/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Creditcardinstellingen | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transactie afwijzen als: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaalbaar maken voor | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Controle verzenden naar | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_au/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_au/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_au/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Merchant ID | `payment_au/cybersource/merchant_id` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) | ![Gecodeerd](/help/assets/configuration/cloud-enc.png) |
| Profiel-id | `payment_au/cybersource/profile_id` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) | ![Gecodeerd](/help/assets/configuration/cloud-enc.png) |
| Status van nieuwe bestelling | `payment_au/cybersource/order_status` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_au/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_au/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_au/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_au/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_au/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_au/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_au/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_au/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_au/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Installatie-id | `payment_au/worldpay/installation_id` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_au/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_au/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Handtekeningvelden | `payment_au/worldpay/signature_fields` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_au/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Testmodus | `payment_au/worldpay/sandbox_flag` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_au/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_au/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_au/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_au/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_au/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_au/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_au/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_au/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_au/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_au/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_au/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_au/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_au/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_au/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_au/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_au/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Deze oplossing inschakelen | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Creditcardinstellingen | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transactie afwijzen als: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Creditcardinstellingen | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transactie afwijzen als: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_ca/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_ca/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_ca/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_ca/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_ca/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_ca/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_ca/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_ca/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_ca/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_ca/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_ca/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_ca/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_ca/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_ca/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Handtekeningvelden | `payment_ca/worldpay/signature_fields` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_ca/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_ca/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_ca/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_ca/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_ca/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_ca/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_ca/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_ca/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_ca/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_ca/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_ca/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_ca/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_ca/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_ca/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_ca/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_ca/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_ca/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailklant | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_other/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_other/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_other/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_other/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_other/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_other/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_other/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_other/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_other/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_other/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_other/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_other/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_other/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_other/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Handtekeningvelden | `payment_other/worldpay/signature_fields` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_other/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_other/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_other/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_other/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_other/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_other/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_other/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_other/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_other/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_other/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_other/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_other/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_other/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_other/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_other/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_other/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_other/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_de/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_de/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_de/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van nieuwe bestelling | `payment_de/cybersource/order_status` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_de/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_de/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_de/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_de/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_de/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_de/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_de/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_de/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_de/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_de/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_de/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Handtekeningvelden | `payment_de/worldpay/signature_fields` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Testmodus | `payment_de/worldpay/sandbox_flag` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_de/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_de/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_de/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_de/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_de/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_de/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_de/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_de/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_de/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_de/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_de/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_de/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_de/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_de/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_de/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_de/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaalbaar maken voor | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_gb/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_gb/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_gb/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van nieuwe bestelling | `payment_gb/cybersource/order_status` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_gb/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_gb/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_gb/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_gb/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_gb/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_gb/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_gb/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_gb/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_gb/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| MD5 Secret for Transactions | `payment_gb/worldpay/md5_secret` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_gb/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_gb/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Handtekeningvelden | `payment_gb/worldpay/signature_fields` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_gb/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_gb/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_gb/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_gb/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_gb/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_gb/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_gb/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_gb/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_gb/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_gb/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_gb/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_gb/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_gb/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_gb/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_gb/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_gb/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_gb/eway/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Gepland ophalen | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Creditcardinstellingen | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transactie afwijzen als: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal-krediet inschakelen | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Creditcardinstellingen | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Transactie afwijzen als: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gepland ophalen | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PayPal Merchant Pages Style | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alle items automatisch factureren | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Instructies | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaalbaar maken voor | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betalingsactie | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titel | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status van nieuwe bestelling | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geaccepteerde valuta | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutopsporing | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Typen creditcard | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verificatie van creditcard | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door de kandidaat-lidstaten | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Betaling door specifieke landen | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totaal minimumbestelling | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal bestellingen | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sorteervolgorde | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `payment_us/cybersource/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_us/cybersource/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_us/cybersource/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van nieuwe bestelling | `payment_us/cybersource/order_status` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_us/cybersource/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_us/cybersource/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_us/cybersource/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_us/cybersource/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Totaal minimumbestelling | `payment_us/cybersource/min_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal bestellingen | `payment_us/cybersource/max_order_total` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_us/cybersource/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_us/worldpay/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_us/worldpay/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens bewerken toestaan | `payment_us/worldpay/fix_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Contactgegevens verbergen | `payment_us/worldpay/hide_contact` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Handtekeningvelden | `payment_us/worldpay/signature_fields` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_us/worldpay/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie voor test | `payment_us/worldpay/test_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_us/worldpay/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling uit de betrokken landen | `payment_us/worldpay/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_us/worldpay/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_us/worldpay/cvv_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_us/worldpay/avs_fraud_case` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_us/worldpay/sort_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Ingeschakeld | `payment_us/eway/active` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Verbindingstype | `payment_us/eway/connection_type` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Titel | `payment_us/eway/title` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betalingsactie | `payment_us/eway/payment_action` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Foutopsporing | `payment_us/eway/debug` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Typen creditcard | `payment_us/eway/cctypes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door de kandidaat-lidstaten | `payment_us/eway/allowspecific` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Betaling door specifieke landen | `payment_us/eway/specificcountry` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Sorteervolgorde | `payment_us/eway/sort_order` |  |

{style="table-layout:auto"}
