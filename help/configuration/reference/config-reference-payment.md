---
title: Verwijzing naar betalingspaden
description: Meer informatie over paden en methodewaarden voor betalingsconfiguraties in Adobe Commerce Admin. Ontdek de configuratieopties voor PayPal, creditcard en betaalgateway.
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '5833'
ht-degree: 0%

---

# Verwijzing naar betalingspaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **de Methoden van de Betaling**.

Het [`magento app:config:dump` bevel &#x200B;](../cli/export-configuration.md) schrijft deze waarden aan het gedeelde configuratiedossier, `app/etc/config.php`, dat in broncontrole zou moeten zijn. Om naar keuze om het even welke configuratiemontages met voeten te treden of gevoelige montages te plaatsen, zie [&#x200B; de milieuvariabelen van het Gebruik om configuratiemontages &#x200B;](override-config-settings.md#environment-variables) met voeten te treden. Dit onderwerp staat _lijst_ gevoelige en systeem-specifieke waarden [&#x200B; toe.](config-reference-sens.md)

De instellingen worden verder geordend via betalingsmethode.

## Paden van PayPal

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| Deze oplossing inschakelen | `payment/payflowpro/active` | Alles |
| In-Context Checkout-ervaring inschakelen | `payment/paypal_express/in_context` | Alles |
| PayPal-krediet inschakelen | `payment/payflow_express_bml/active` | Alles |
| PayPal-krediet inschakelen | `payment/paypal_express_bml/active` | Alles |
| Weergave | `payment/paypal_express_bml/homepage_display` | Alles |
| Positie | `payment/paypal_express_bml/homepage_position` | Alles |
| Grootte | `payment/paypal_express_bml/homepage_size` | Alles |
| Weergave | `payment/paypal_express_bml/categorypage_display` | Alles |
| Positie | `payment/paypal_express_bml/categorypage_position` | Alles |
| Grootte | `payment/paypal_express_bml/categorypage_size` | Alles |
| Weergave | `payment/paypal_express_bml/productpage_display` | Alles |
| Positie | `payment/paypal_express_bml/productpage_position` | Alles |
| Grootte | `payment/paypal_express_bml/productpage_size` | Alles |
| Weergave | `payment/paypal_express_bml/checkout_display` | Alles |
| Positie | `payment/paypal_express_bml/checkout_position` | Alles |
| Grootte | `payment/paypal_express_bml/checkout_size` | Alles |
| Weergeven op pagina met productdetails | `payment/payflow_express/visible_on_product` | Alles |
| Weergeven bij winkelwagentje | `payment/payflow_express/visible_on_cart` | Alles |
| Betaling van toepassing vanaf | `payment/payflow_express/allowspecific` | Alles |
| Betalingen in landen van toepassing uit | `payment/payflow_express/specificcountry` | Alles |
| SSL-verificatie inschakelen | `payment/payflow_express/verify_peer` | Alles |
| Objecten met winkelwagentjes overdragen | `payment/payflow_express/line_items_enabled` | Alles |
| Revisiestap bestelling overslaan | `payment/paypal_express/skip_order_review_step` | Alles |
| Objecten met winkelwagentjes overdragen | `payment/paypal_express/line_items_enabled` | Alles |
| Opties voor verzending | `payment/paypal_express/transfer_shipping_options` | Alles |
| Shortcut Buttons Flavis | `paypal/wpp/button_flavor` | Alles |
| Uitchecken van PayPal-gasten inschakelen | `payment/paypal_express/solution_type` | Alles |
| Factureringsadres van klant vereisen | `payment/paypal_express/require_billing_address` | Alles |
| Opname factureringsovereenkomst | `payment/paypal_express/allow_ba_signup` | Alles |
| Ingeschakeld | `payment/paypal_billing_agreement/active` | Alles |
| Titel | `payment/paypal_billing_agreement/title` | Alles |
| Sorteervolgorde | `payment/paypal_billing_agreement/sort_order` | Alles |
| Betalingsactie | `payment/paypal_billing_agreement/payment_action` | Alles |
| Betaling van toepassing vanaf | `payment/paypal_billing_agreement/allowspecific` | Alles |
| Betalingen in landen van toepassing uit | `payment/paypal_billing_agreement/specificcountry` | Alles |
| SSL-verificatie inschakelen | `payment/paypal_billing_agreement/verify_peer` | Alles |
| Objecten met winkelwagentjes overdragen | `payment/paypal_billing_agreement/line_items_enabled` | Alles |
| Wizard Factureringsovereenkomst toestaan | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | Alles |
| Automatisch ophalen inschakelen | `paypal/fetch_reports/active` | Alles |
| Schema | `paypal/fetch_reports/schedule` | Alles |
| Dag | `paypal/fetch_reports/time` | Alles |
| PayPal-productlogo | `paypal/style/logo` | Alles |
| Paginastijl | `paypal/style/page_style` | Alles |
| URL koptekstafbeelding | `paypal/style/paypal_hdrimg` | Alles |
| Achtergrondkleur koptekst | `paypal/style/paypal_hdrbackcolor` | Alles |
| Randkleur koptekst | `paypal/style/paypal_hdrbordercolor` | Alles |
| Achtergrondkleur pagina | `paypal/style/paypal_payflowcolor` | Alles |
| Deze oplossing inschakelen | `payment/paypal_express/active` | Alles |
| PayPal-creditering van betalingsopdracht sorteren | `payment/paypal_express_bml/sort_order` | Alles |
| Titel | `payment/paypal_express/title` | Alles |
| Sorteervolgorde | `payment/paypal_express/sort_order` | Alles |
| Betalingsactie | `payment/paypal_express/payment_action` | Alles |
| Weergeven op pagina met productdetails | `payment/paypal_express/visible_on_product` | Alles |
| Toegestane periode (dagen) | `payment/paypal_express/authorization_hoAllr_period` | Alles |
| Geldige periode bestellen (dagen) | `payment/paypal_express/order_valid_period` | Alles |
| Aantal vergunningen voor kinderen | `payment/paypal_express/child_authorization_number` | Alles |
| Weergeven bij winkelwagentje | `payment/paypal_express/visible_on_cart` | Alles |
| Aantal vergunningen voor kinderen | `payment/paypal_express/child_authorization_number` | Alles |
| Betaling van toepassing vanaf | `payment/paypal_express/allowspecific` | Alles |
| Aantal vergunningen voor kinderen | `payment/paypal_express/child_authorization_number` | Alles |
| Betalingen in landen van toepassing uit | `payment/paypal_express/specificcountry` | Alles |
| Aantal vergunningen voor kinderen | `payment/paypal_express/child_authorization_number` | Alles |
| SSL-verificatie inschakelen | `payment/paypal_express/verify_peer` | Alles |
| Aantal vergunningen voor kinderen | `payment/paypal_express/child_authorization_number` | Alles |
| Gepland ophalen | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |

{style="table-layout:auto"}

## PayPal Payments Pro

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| API-verificatiemethoden | `paypal/wpp/api_authentication` | Alles |
| API gebruikt proxy | `paypal/wpp/use_proxy` | Alles |
| Gepland ophalen | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alles |
| Gepland ophalen | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alles |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Verenigd Koninkrijk)

Deze opties zijn beschikbaar slechts als u het Verenigd Koninkrijk als [&#x200B; koopvaardijland &#x200B;](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths) koos.

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| Deze oplossing inschakelen | `payment/hosted_pro/active` | Alles |
| Titel | `payment/hosted_pro/title` | Alles |
| Sorteervolgorde | `payment/hosted_pro/sort_order` | Alles |
| Betalingsactie | `payment/hosted_pro/payment_action` | Alles |
| Uitdrukkelijke afhandeling weergeven in de stap Betalingsgegevens | `payment/hosted_pro/display_ec` | Alles |
| Betaling van toepassing vanaf | `payment/hosted_pro/allowspecific` | Alles |
| Betalingen in landen van toepassing uit | `payment/hosted_pro/specificcountry` | Alles |
| SSL-verificatie inschakelen | `payment/hosted_pro/verify_peer` | Alles |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| Vault ingeschakeld | `payment/payflowpro_cc_vault/active` | Alles |
| Titel | `payment/payflowpro/title` | Alles |
| Vault-titel | `payment/payflowpro_cc_vault/title` | Alles |
| Sorteervolgorde | `payment/payflowpro/sort_order` | Alles |
| Betalingsactie | `payment/payflowpro/payment_action` | Alles |
| Toegestane creditcardtypen | `payment/payflowpro/cctypes` | Alles |
| Betaling van toepassing vanaf | `payment/payflowpro/allowspecific` | Alles |
| Betalingen in landen van toepassing uit | `payment/payflowpro/specificcountry` | Alles |
| SSL-verificatie inschakelen | `payment/payflowpro/verify_peer` | Alles |
| CVV-item vereisen | `payment/payflowpro/useccv` | Alles |
| Transactie afwijzen als: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alles |
| AVS Street Does Allt Match | `payment/payflowpro/avs_street` | Alles |
| AVS ZIP komt alleen overeen | `payment/payflowpro/avs_zip` | Alles |
| De internationale AVS-indicator komt overeen | `payment/payflowpro/avs_international` | Alles |
| De beveiligingscode van de kaart komt overeen | `payment/payflowpro/avs_security_code` | Alles |
| Leverancier | `payment/payflowpro/vendor` | Alles |
| Proxy gebruiken | `payment/payflowpro/use_proxy` | Alles |
| Titel | `payment/payflow_express/title` | Alles |
| Sorteervolgorde | `payment/payflow_express/sort_order` | Alles |
| Betalingsactie | `payment/payflow_express/payment_action` | Alles |
| Gepland ophalen | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Alles |
| Partner | `payment/payflow_advanced/partner` | Alles |
| Leverancier | `payment/payflow_advanced/vendor` | Alles |
| Proxy gebruiken | `payment/payflow_advanced/use_proxy` | Alles |
| Deze oplossing inschakelen | `payment/payflow_advanced/active` | Alles |
| Titel | `payment/payflow_advanced/title` | Alles |
| Sorteervolgorde | `payment/payflow_advanced/sort_order` | Alles |
| Betalingsactie | `payment/payflow_advanced/payment_action` | Alles |
| Betaling van toepassing vanaf | `payment/payflow_advanced/allowspecific` | Alles |
| Betalingen in landen van toepassing uit | `payment/payflow_advanced/specificcountry` | Alles |
| SSL-verificatie inschakelen | `payment/payflow_advanced/verify_peer` | Alles |
| CVV-item is bewerkbaar | `payment/payflow_advanced/csc_editable` | Alles |
| CVV-item vereisen | `payment/payflow_advanced/csc_required` | Alles |
| E-mailbevestiging verzenden | `payment/payflow_advanced/email_confirmation` | Alles |

{style="table-layout:auto"}

## PayPal Payflow Link

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| Partner | `payment/payflow_link/partner` | Alles |
| Leverancier | `payment/payflow_link/vendor` | Alles |
| Enable Payflow Link | `payment/payflow_link/active` | Alles |
| Uitdrukkelijke afhandeling inschakelen | `payment/payflow_express/active` | Alles |
| PayPal-creditering van betalingsopdracht sorteren | `payment/payflow_express_bml/sort_order` | Alles |
| Betaling van toepassing vanaf | `payment/payflow_link/allowspecific` | Alles |
| Betalingen in landen van toepassing uit | `payment/payflow_link/specificcountry` | Alles |
| SSL-verificatie inschakelen | `payment/payflow_link/verify_peer` | Alles |
| CVV-item is bewerkbaar | `payment/payflow_link/csc_editable` | Alles |
| CVV-item vereisen | `payment/payflow_link/csc_required` | Alles |
| E-mailbevestiging verzenden | `payment/payflow_link/email_confirmation` | Alles |
| Gepland ophalen | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Alles |
| Titel | `payment/payflow_link/title` | Alles |
| Sorteervolgorde | `payment/payflow_link/sort_order` | Alles |
| Betalingsactie | `payment/payflow_link/payment_action` | Alles |

{style="table-layout:auto"}

## Paden voor subtotaal uitchecken nul

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| Ingeschakeld | `payment/free/active` | Alles |
| Titel | `payment/free/title` | Alles |
| Status van nieuwe bestelling | `payment/free/order_status` | Alles |
| Alle items automatisch factureren | `payment/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment/free/specificcountry` | Alles |
| Sorteervolgorde | `payment/free/sort_order` | Alles |

{style="table-layout:auto"}

## Betalingspaden onder rembours

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| Ingeschakeld | `payment/cashondelivery/active` | Alles |
| Titel | `payment/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment/cashondelivery/specificcountry` | Alles |
| Instructies | `payment/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment/cashondelivery/sort_order` | Alles |

{style="table-layout:auto"}

## Betalingspaden voor overschrijvingen

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| Ingeschakeld | `payment/banktransfer/active` | Alles |
| Titel | `payment/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment/banktransfer/specificcountry` | Alles |
| Instructies | `payment/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment/banktransfer/sort_order` | Alles |

{style="table-layout:auto"}

## Paden voor cheque of postwissel

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| Ingeschakeld | `payment/checkmo/active` | Alles |
| Titel | `payment/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment/checkmo/specificcountry` | Alles |
| Betaalbaar maken voor | `payment/checkmo/payable_to` | Alles |
| Totaal minimumbestelling | `payment/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment/checkmo/sort_order` | Alles |

{style="table-layout:auto"}

## Paden inkooporder

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| Ingeschakeld | `payment/purchaseorder/active` | Alles |
| Titel | `payment/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment/purchaseorder/sort_order` | Alles |

{style="table-layout:auto"}

## Internationale paden

>[!INFO]
>
>De beschikbare wegen worden bepaald door uw keus van [&#x200B; Merchant land &#x200B;](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Naam | Config-pad | Ondersteuning voor Commerce-versies? |
|--------------|--------------|--------------|
| SFTP-referenties | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | Alles |
| Gepland ophalen | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Deze oplossing inschakelen | `payment/wps_express/active` | Alles |
| Gepland ophalen | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Creditcardinstellingen | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | Alles |
| Transactie afwijzen als: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alles |
| Gepland ophalen | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alles |
| Ingeschakeld | `payment_nz/free/active` | Alles |
| Titel | `payment_nz/free/title` | Alles |
| Status van nieuwe bestelling | `payment_nz/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_nz/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_nz/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_nz/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_nz/free/sort_order` | Alles |
| Ingeschakeld | `payment_nz/cashondelivery/active` | Alles |
| Titel | `payment_nz/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_nz/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_nz/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_nz/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_nz/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_nz/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_nz/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_nz/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_nz/banktransfer/active` | Alles |
| Titel | `payment_nz/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_nz/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_nz/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_nz/banktransfer/specificcountry` | Alles |
| Instructies | `payment_nz/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_nz/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_nz/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_nz/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_nz/checkmo/active` | Alles |
| Titel | `payment_nz/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_nz/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_nz/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_nz/checkmo/specificcountry` | Alles |
| Betaalbaar maken voor | `payment_nz/checkmo/payable_to` | Alles |
| Controle verzenden naar | `payment_nz/checkmo/mailing_address` | Alles |
| Totaal minimumbestelling | `payment_nz/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_nz/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_nz/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_nz/purchaseorder/active` | Alles |
| Titel | `payment_nz/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_nz/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_nz/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_nz/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_nz/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_nz/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_nz/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_nz/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_nz/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_nz/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_nz/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_nz/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_nz/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_nz/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_nz/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_nz/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_nz/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_nz/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_nz/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_nz/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_nz/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_nz/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_nz/cybersource/title` | Alleen Commerce Enterprise |
| Status van nieuwe bestelling | `payment_nz/cybersource/order_status` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_nz/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_nz/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_nz/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_nz/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_nz/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_nz/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_nz/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_nz/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_nz/worldpay/title` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_nz/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_nz/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Handtekeningvelden | `payment_nz/worldpay/signature_fields` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_nz/worldpay/debug` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_nz/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_nz/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_nz/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_nz/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_nz/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_nz/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_nz/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_nz/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_nz/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_nz/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_nz/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_nz/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_nz/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_nz/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_nz/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_nz/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alles |
| Gepland ophalen | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_hk/free/active` | Alles |
| Titel | `payment_hk/free/title` | Alles |
| Status van nieuwe bestelling | `payment_hk/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_hk/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_hk/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_hk/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_hk/free/sort_order` | Alles |
| Ingeschakeld | `payment_hk/cashondelivery/active` | Alles |
| Titel | `payment_hk/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_hk/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_hk/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_hk/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_hk/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_hk/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_hk/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_hk/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_hk/banktransfer/active` | Alles |
| Titel | `payment_hk/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_hk/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_hk/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_hk/banktransfer/specificcountry` | Alles |
| Instructies | `payment_hk/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_hk/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_hk/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_hk/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_hk/checkmo/active` | Alles |
| Titel | `payment_hk/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_hk/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_hk/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_hk/checkmo/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_hk/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_hk/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_hk/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_hk/purchaseorder/active` | Alles |
| Titel | `payment_hk/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_hk/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_hk/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_hk/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_hk/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_hk/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_hk/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_hk/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_hk/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_hk/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_hk/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_hk/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_hk/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_hk/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_hk/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_hk/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_hk/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_hk/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_hk/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_hk/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_hk/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_hk/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_hk/cybersource/title` | Alleen Commerce Enterprise |
| Status van nieuwe bestelling | `payment_hk/cybersource/order_status` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_hk/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_hk/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_hk/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_hk/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_hk/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_hk/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_hk/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_hk/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_hk/worldpay/title` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_hk/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_hk/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_hk/worldpay/debug` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_hk/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_hk/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_hk/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_hk/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_hk/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_hk/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_hk/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_hk/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_hk/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_hk/eway/title` | Alleen Commerce Enterprise |
| Sandbox-modus | `payment_hk/eway/sandbox_flag` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_hk/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_hk/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_hk/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_hk/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_hk/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_hk/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alles |
| Gepland ophalen | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_es/free/active` | Alles |
| Titel | `payment_es/free/title` | Alles |
| Status van nieuwe bestelling | `payment_es/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_es/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_es/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_es/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_es/free/sort_order` | Alles |
| Ingeschakeld | `payment_es/cashondelivery/active` | Alles |
| Titel | `payment_es/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_es/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_es/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_es/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_es/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_es/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_es/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_es/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_es/banktransfer/active` | Alles |
| Titel | `payment_es/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_es/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_es/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_es/banktransfer/specificcountry` | Alles |
| Instructies | `payment_es/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_es/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_es/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_es/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_es/checkmo/active` | Alles |
| Titel | `payment_es/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_es/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_es/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_es/checkmo/specificcountry` | Alles |
| Betaalbaar maken voor | `payment_es/checkmo/payable_to` | Alles |
| Totaal minimumbestelling | `payment_es/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_es/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_es/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_es/purchaseorder/active` | Alles |
| Titel | `payment_es/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_es/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_es/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_es/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_es/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_es/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_es/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_es/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_es/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_es/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_es/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_es/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_es/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_es/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_es/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_es/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_es/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_es/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_es/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_es/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_es/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_es/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_es/cybersource/title` | Alleen Commerce Enterprise |
| Profiel-id | `payment_es/cybersource/profile_id` | Commerce Onderneming slechts \| ![&#x200B; Gecodeerd &#x200B;](/help/assets/configuration/cloud-enc.png) |
| Status van nieuwe bestelling | `payment_es/cybersource/order_status` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_es/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_es/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_es/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_es/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_es/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_es/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_es/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_es/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_es/worldpay/title` | Alleen Commerce Enterprise |
| Installatie-id | `payment_es/worldpay/installation_id` | Alleen Commerce Enterprise |
| Installatie-id voor extern beheer | `payment_es/worldpay/admin_installation_id` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_es/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_es/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Handtekeningvelden | `payment_es/worldpay/signature_fields` | Alleen Commerce Enterprise |
| Testmodus | `payment_es/worldpay/sandbox_flag` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_es/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_es/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_es/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_es/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_es/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_es/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_es/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_es/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_es/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_es/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_es/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_es/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_es/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_es/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_es/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_es/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alles |
| Gepland ophalen | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_it/free/active` | Alles |
| Titel | `payment_it/free/title` | Alles |
| Status van nieuwe bestelling | `payment_it/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_it/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_it/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_it/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_it/free/sort_order` | Alles |
| Ingeschakeld | `payment_it/cashondelivery/active` | Alles |
| Titel | `payment_it/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_it/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_it/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_it/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_it/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_it/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_it/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_it/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_it/banktransfer/active` | Alles |
| Titel | `payment_it/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_it/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_it/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_it/banktransfer/specificcountry` | Alles |
| Instructies | `payment_it/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_it/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_it/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_it/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_it/checkmo/active` | Alles |
| Titel | `payment_it/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_it/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_it/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_it/checkmo/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_it/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_it/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_it/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_it/purchaseorder/active` | Alles |
| Titel | `payment_it/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_it/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_it/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_it/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_it/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_it/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_it/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_it/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_it/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_it/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_it/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_it/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_it/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_it/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_it/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_it/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_it/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_it/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_it/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_it/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_it/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_it/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_it/cybersource/title` | Alleen Commerce Enterprise |
| Status van nieuwe bestelling | `payment_it/cybersource/order_status` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_it/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_it/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_it/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_it/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_it/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_it/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_it/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_it/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_it/worldpay/title` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_it/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_it/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Handtekeningvelden | `payment_it/worldpay/signature_fields` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_it/worldpay/debug` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_it/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_it/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_it/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_it/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_it/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_it/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_it/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_it/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_it/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_it/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_it/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_it/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_it/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_it/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_it/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_it/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alles |
| Gepland ophalen | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_fr/free/active` | Alles |
| Titel | `payment_fr/free/title` | Alles |
| Status van nieuwe bestelling | `payment_fr/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_fr/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_fr/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_fr/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_fr/free/sort_order` | Alles |
| Ingeschakeld | `payment_fr/cashondelivery/active` | Alles |
| Titel | `payment_fr/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_fr/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_fr/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_fr/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_fr/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_fr/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_fr/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_fr/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_fr/banktransfer/active` | Alles |
| Titel | `payment_fr/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_fr/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_fr/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_fr/banktransfer/specificcountry` | Alles |
| Instructies | `payment_fr/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_fr/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_fr/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_fr/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_fr/checkmo/active` | Alles |
| Titel | `payment_fr/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_fr/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_fr/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_fr/checkmo/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_fr/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_fr/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_fr/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_fr/purchaseorder/active` | Alles |
| Titel | `payment_fr/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_fr/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_fr/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_fr/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_fr/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_fr/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_fr/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_fr/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_fr/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_fr/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_fr/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_fr/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_fr/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_fr/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_fr/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_fr/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_fr/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_fr/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_fr/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_fr/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_fr/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_fr/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_fr/cybersource/title` | Alleen Commerce Enterprise |
| Status van nieuwe bestelling | `payment_fr/cybersource/order_status` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_fr/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_fr/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_fr/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_fr/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_fr/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_fr/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_fr/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_fr/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_fr/worldpay/title` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_fr/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_fr/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_fr/worldpay/debug` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_fr/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_fr/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_fr/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_fr/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_fr/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_fr/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_fr/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_fr/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_fr/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_fr/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_fr/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_fr/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_fr/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_fr/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_fr/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_fr/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alles |
| Gepland ophalen | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_jp/free/active` | Alles |
| Titel | `payment_jp/free/title` | Alles |
| Status van nieuwe bestelling | `payment_jp/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_jp/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_jp/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_jp/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_jp/free/sort_order` | Alles |
| Ingeschakeld | `payment_jp/cashondelivery/active` | Alles |
| Titel | `payment_jp/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_jp/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_jp/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_jp/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_jp/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_jp/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_jp/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_jp/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_jp/banktransfer/active` | Alles |
| Titel | `payment_jp/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_jp/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_jp/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_jp/banktransfer/specificcountry` | Alles |
| Instructies | `payment_jp/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_jp/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_jp/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_jp/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_jp/checkmo/active` | Alles |
| Titel | `payment_jp/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_jp/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_jp/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_jp/checkmo/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_jp/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_jp/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_jp/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_jp/purchaseorder/active` | Alles |
| Titel | `payment_jp/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_jp/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_jp/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_jp/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_jp/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_jp/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_jp/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_jp/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_jp/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_jp/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_jp/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_jp/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_jp/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_jp/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_jp/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_jp/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_jp/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_jp/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_jp/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_jp/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_jp/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_jp/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_jp/cybersource/title` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_jp/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_jp/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_jp/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_jp/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_jp/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_jp/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_jp/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_jp/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_jp/worldpay/title` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_jp/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_jp/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_jp/worldpay/debug` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_jp/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_jp/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_jp/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_jp/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_jp/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_jp/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_jp/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_jp/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_jp/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_jp/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_jp/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_jp/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_jp/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_jp/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_jp/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_jp/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alles |
| Gepland ophalen | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Creditcardinstellingen | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | Alles |
| Transactie afwijzen als: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alles |
| Gepland ophalen | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alles |
| Ingeschakeld | `payment_au/free/active` | Alles |
| Titel | `payment_au/free/title` | Alles |
| Status van nieuwe bestelling | `payment_au/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_au/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_au/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_au/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_au/free/sort_order` | Alles |
| Ingeschakeld | `payment_au/cashondelivery/active` | Alles |
| Titel | `payment_au/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_au/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_au/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_au/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_au/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_au/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_au/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_au/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_au/banktransfer/active` | Alles |
| Titel | `payment_au/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_au/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_au/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_au/banktransfer/specificcountry` | Alles |
| Instructies | `payment_au/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_au/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_au/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_au/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_au/checkmo/active` | Alles |
| Titel | `payment_au/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_au/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_au/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_au/checkmo/specificcountry` | Alles |
| Betaalbaar maken voor | `payment_au/checkmo/payable_to` | Alles |
| Controle verzenden naar | `payment_au/checkmo/mailing_address` | Alles |
| Totaal minimumbestelling | `payment_au/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_au/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_au/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_au/purchaseorder/active` | Alles |
| Titel | `payment_au/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_au/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_au/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_au/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_au/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_au/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_au/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_au/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_au/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_au/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_au/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_au/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_au/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_au/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_au/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_au/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_au/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_au/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_au/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_au/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_au/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_au/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_au/cybersource/title` | Alleen Commerce Enterprise |
| Merchant ID | `payment_au/cybersource/merchant_id` | De Onderneming van Commerce \| ![&#x200B; Gecodeerde &#x200B;](/help/assets/configuration/cloud-enc.png) |
| Profiel-id | `payment_au/cybersource/profile_id` | De Onderneming van Commerce \| ![&#x200B; Gecodeerde &#x200B;](/help/assets/configuration/cloud-enc.png) |
| Status van nieuwe bestelling | `payment_au/cybersource/order_status` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_au/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_au/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_au/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_au/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_au/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_au/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_au/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_au/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_au/worldpay/title` | Alleen Commerce Enterprise |
| Installatie-id | `payment_au/worldpay/installation_id` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_au/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_au/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Handtekeningvelden | `payment_au/worldpay/signature_fields` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_au/worldpay/debug` | Alleen Commerce Enterprise |
| Testmodus | `payment_au/worldpay/sandbox_flag` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_au/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_au/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_au/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_au/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_au/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_au/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_au/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_au/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_au/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_au/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_au/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_au/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_au/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_au/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_au/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_au/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Deze oplossing inschakelen | `payment/paypal_payment_pro/active` | Alles |
| Creditcardinstellingen | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | Alles |
| Transactie afwijzen als: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alles |
| Gepland ophalen | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alles |
| Creditcardinstellingen | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | Alles |
| Transactie afwijzen als: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alles |
| Gepland ophalen | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alles |
| Gepland ophalen | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_ca/free/active` | Alles |
| Titel | `payment_ca/free/title` | Alles |
| Status van nieuwe bestelling | `payment_ca/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_ca/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_ca/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_ca/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_ca/free/sort_order` | Alles |
| Ingeschakeld | `payment_ca/cashondelivery/active` | Alles |
| Titel | `payment_ca/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_ca/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_ca/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_ca/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_ca/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_ca/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_ca/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_ca/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_ca/banktransfer/active` | Alles |
| Titel | `payment_ca/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_ca/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_ca/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_ca/banktransfer/specificcountry` | Alles |
| Instructies | `payment_ca/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_ca/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_ca/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_ca/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_ca/checkmo/active` | Alles |
| Titel | `payment_ca/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_ca/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_ca/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_ca/checkmo/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_ca/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_ca/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_ca/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_ca/purchaseorder/active` | Alles |
| Titel | `payment_ca/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_ca/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_ca/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_ca/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_ca/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_ca/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_ca/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_ca/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_ca/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_ca/authorizenet_directpost/title` | Alles |
| Geaccepteerde valuta | `payment_ca/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_ca/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_ca/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_ca/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_ca/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_ca/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_ca/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_ca/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_ca/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_ca/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_ca/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_ca/cybersource/title` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_ca/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_ca/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_ca/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_ca/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_ca/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_ca/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_ca/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_ca/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_ca/worldpay/title` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_ca/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_ca/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Handtekeningvelden | `payment_ca/worldpay/signature_fields` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_ca/worldpay/debug` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_ca/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_ca/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_ca/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_ca/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_ca/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_ca/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_ca/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_ca/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_ca/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_ca/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_ca/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_ca/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_ca/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_ca/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_ca/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_ca/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_other/free/active` | Alles |
| Titel | `payment_other/free/title` | Alles |
| Status van nieuwe bestelling | `payment_other/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_other/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_other/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_other/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_other/free/sort_order` | Alles |
| Ingeschakeld | `payment_other/cashondelivery/active` | Alles |
| Titel | `payment_other/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_other/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_other/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_other/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_other/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_other/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_other/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_other/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_other/banktransfer/active` | Alles |
| Titel | `payment_other/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_other/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_other/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_other/banktransfer/specificcountry` | Alles |
| Instructies | `payment_other/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_other/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_other/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_other/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_other/checkmo/active` | Alles |
| Titel | `payment_other/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_other/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_other/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_other/checkmo/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_other/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_other/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_other/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_other/purchaseorder/active` | Alles |
| Titel | `payment_other/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_other/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_other/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_other/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_other/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_other/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_other/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_other/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_other/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_other/authorizenet_directpost/title` | Alles |
| Geaccepteerde valuta | `payment_other/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_other/authorizenet_directpost/debug` | Alles |
| E-mailklant | `payment_other/authorizenet_directpost/email_customer` | Alles |
| Typen creditcard | `payment_other/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_other/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_other/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_other/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_other/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_other/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_other/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_other/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_other/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_other/cybersource/title` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_other/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_other/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_other/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_other/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_other/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_other/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_other/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_other/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_other/worldpay/title` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_other/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_other/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Handtekeningvelden | `payment_other/worldpay/signature_fields` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_other/worldpay/debug` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_other/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_other/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_other/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_other/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_other/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_other/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_other/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_other/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_other/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_other/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_other/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_other/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_other/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_other/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_other/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_other/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_de/checkmo/active` | Alles |
| Titel | `payment_de/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_de/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_de/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_de/checkmo/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_de/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_de/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_de/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_de/banktransfer/active` | Alles |
| Titel | `payment_de/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_de/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_de/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_de/banktransfer/specificcountry` | Alles |
| Instructies | `payment_de/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_de/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_de/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_de/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_de/cashondelivery/active` | Alles |
| Titel | `payment_de/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_de/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_de/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_de/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_de/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_de/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_de/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_de/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_de/free/active` | Alles |
| Titel | `payment_de/free/title` | Alles |
| Status van nieuwe bestelling | `payment_de/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_de/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_de/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_de/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_de/free/sort_order` | Alles |
| Ingeschakeld | `payment_de/purchaseorder/active` | Alles |
| Titel | `payment_de/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_de/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_de/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_de/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_de/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_de/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_de/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_de/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_de/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_de/cybersource/title` | Alleen Commerce Enterprise |
| Status van nieuwe bestelling | `payment_de/cybersource/order_status` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_de/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_de/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_de/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_de/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_de/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_de/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_de/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_de/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_de/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_de/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_de/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_de/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_de/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_de/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_de/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_de/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_de/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_de/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_de/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_de/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_de/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_de/worldpay/title` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_de/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_de/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Handtekeningvelden | `payment_de/worldpay/signature_fields` | Alleen Commerce Enterprise |
| Testmodus | `payment_de/worldpay/sandbox_flag` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_de/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_de/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_de/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_de/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_de/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_de/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_de/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_de/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_de/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_de/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_de/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_de/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_de/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_de/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_de/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_de/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_gb/checkmo/active` | Alles |
| Titel | `payment_gb/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_gb/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_gb/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_gb/checkmo/specificcountry` | Alles |
| Betaalbaar maken voor | `payment_gb/checkmo/payable_to` | Alles |
| Totaal minimumbestelling | `payment_gb/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_gb/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_gb/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_gb/banktransfer/active` | Alles |
| Titel | `payment_gb/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_gb/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_gb/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_gb/banktransfer/specificcountry` | Alles |
| Instructies | `payment_gb/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_gb/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_gb/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_gb/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_gb/cashondelivery/active` | Alles |
| Titel | `payment_gb/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_gb/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_gb/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_gb/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_gb/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_gb/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_gb/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_gb/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_gb/free/active` | Alles |
| Titel | `payment_gb/free/title` | Alles |
| Status van nieuwe bestelling | `payment_gb/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_gb/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_gb/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_gb/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_gb/free/sort_order` | Alles |
| Ingeschakeld | `payment_gb/purchaseorder/active` | Alles |
| Titel | `payment_gb/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_gb/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_gb/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_gb/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_gb/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_gb/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_gb/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_gb/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_gb/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_gb/cybersource/title` | Alleen Commerce Enterprise |
| Status van nieuwe bestelling | `payment_gb/cybersource/order_status` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_gb/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_gb/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_gb/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_gb/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_gb/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_gb/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_gb/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_gb/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_gb/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_gb/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_gb/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_gb/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_gb/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_gb/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_gb/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_gb/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_gb/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_gb/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_gb/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_gb/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_gb/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_gb/worldpay/title` | Alleen Commerce Enterprise |
| MD5 Secret for Transactions | `payment_gb/worldpay/md5_secret` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_gb/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_gb/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Handtekeningvelden | `payment_gb/worldpay/signature_fields` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_gb/worldpay/debug` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_gb/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_gb/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_gb/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_gb/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_gb/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_gb/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_gb/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_gb/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_gb/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_gb/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_gb/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_gb/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_gb/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_gb/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_gb/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_gb/eway/sort_order` | Alleen Commerce Enterprise |
| Gepland ophalen | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | Alles |
| Creditcardinstellingen | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | Alles |
| Transactie afwijzen als: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alles |
| Gepland ophalen | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Alles |
| PayPal-krediet inschakelen | `payment/wps_express_bml/active` | Alles |
| Gepland ophalen | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | Alles |
| Creditcardinstellingen | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | Alles |
| Transactie afwijzen als: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | Alles |
| Gepland ophalen | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | Alles |
| Gepland ophalen | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | Alles |
| PayPal Merchant Pages Style | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | Alles |
| Ingeschakeld | `payment_us/free/active` | Alles |
| Titel | `payment_us/free/title` | Alles |
| Status van nieuwe bestelling | `payment_us/free/order_status` | Alles |
| Alle items automatisch factureren | `payment_us/free/payment_action` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_us/free/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_us/free/specificcountry` | Alles |
| Sorteervolgorde | `payment_us/free/sort_order` | Alles |
| Ingeschakeld | `payment_us/cashondelivery/active` | Alles |
| Titel | `payment_us/cashondelivery/title` | Alles |
| Status van nieuwe bestelling | `payment_us/cashondelivery/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_us/cashondelivery/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_us/cashondelivery/specificcountry` | Alles |
| Instructies | `payment_us/cashondelivery/instructions` | Alles |
| Totaal minimumbestelling | `payment_us/cashondelivery/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_us/cashondelivery/max_order_total` | Alles |
| Sorteervolgorde | `payment_us/cashondelivery/sort_order` | Alles |
| Ingeschakeld | `payment_us/banktransfer/active` | Alles |
| Titel | `payment_us/banktransfer/title` | Alles |
| Status van nieuwe bestelling | `payment_us/banktransfer/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_us/banktransfer/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_us/banktransfer/specificcountry` | Alles |
| Instructies | `payment_us/banktransfer/instructions` | Alles |
| Totaal minimumbestelling | `payment_us/banktransfer/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_us/banktransfer/max_order_total` | Alles |
| Sorteervolgorde | `payment_us/banktransfer/sort_order` | Alles |
| Ingeschakeld | `payment_us/checkmo/active` | Alles |
| Titel | `payment_us/checkmo/title` | Alles |
| Status van nieuwe bestelling | `payment_us/checkmo/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_us/checkmo/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_us/checkmo/specificcountry` | Alles |
| Betaalbaar maken voor | `payment_us/checkmo/payable_to` | Alles |
| Totaal minimumbestelling | `payment_us/checkmo/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_us/checkmo/max_order_total` | Alles |
| Sorteervolgorde | `payment_us/checkmo/sort_order` | Alles |
| Ingeschakeld | `payment_us/purchaseorder/active` | Alles |
| Titel | `payment_us/purchaseorder/title` | Alles |
| Status van nieuwe bestelling | `payment_us/purchaseorder/order_status` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_us/purchaseorder/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_us/purchaseorder/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_us/purchaseorder/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_us/purchaseorder/max_order_total` | Alles |
| Sorteervolgorde | `payment_us/purchaseorder/sort_order` | Alles |
| Ingeschakeld | `payment_us/authorizenet_directpost/active` | Alles |
| Betalingsactie | `payment_us/authorizenet_directpost/payment_action` | Alles |
| Titel | `payment_us/authorizenet_directpost/title` | Alles |
| Status van nieuwe bestelling | `payment_us/authorizenet_directpost/order_status` | Alles |
| Geaccepteerde valuta | `payment_us/authorizenet_directpost/currency` | Alles |
| Foutopsporing | `payment_us/authorizenet_directpost/debug` | Alles |
| Typen creditcard | `payment_us/authorizenet_directpost/cctypes` | Alles |
| Verificatie van creditcard | `payment_us/authorizenet_directpost/useccv` | Alles |
| Betaling door de kandidaat-lidstaten | `payment_us/authorizenet_directpost/allowspecific` | Alles |
| Betaling door specifieke landen | `payment_us/authorizenet_directpost/specificcountry` | Alles |
| Totaal minimumbestelling | `payment_us/authorizenet_directpost/min_order_total` | Alles |
| Maximum aantal bestellingen | `payment_us/authorizenet_directpost/max_order_total` | Alles |
| Sorteervolgorde | `payment_us/authorizenet_directpost/sort_order` | Alles |
| Ingeschakeld | `payment_us/cybersource/active` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_us/cybersource/payment_action` | Alleen Commerce Enterprise |
| Titel | `payment_us/cybersource/title` | Alleen Commerce Enterprise |
| Status van nieuwe bestelling | `payment_us/cybersource/order_status` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_us/cybersource/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_us/cybersource/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_us/cybersource/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_us/cybersource/specificcountry` | Alleen Commerce Enterprise |
| Totaal minimumbestelling | `payment_us/cybersource/min_order_total` | Alleen Commerce Enterprise |
| Maximum aantal bestellingen | `payment_us/cybersource/max_order_total` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_us/cybersource/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_us/worldpay/active` | Alleen Commerce Enterprise |
| Titel | `payment_us/worldpay/title` | Alleen Commerce Enterprise |
| Contactgegevens bewerken toestaan | `payment_us/worldpay/fix_contact` | Alleen Commerce Enterprise |
| Contactgegevens verbergen | `payment_us/worldpay/hide_contact` | Alleen Commerce Enterprise |
| Handtekeningvelden | `payment_us/worldpay/signature_fields` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_us/worldpay/debug` | Alleen Commerce Enterprise |
| Betalingsactie voor test | `payment_us/worldpay/test_action` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_us/worldpay/payment_action` | Alleen Commerce Enterprise |
| Betaling uit de betrokken landen | `payment_us/worldpay/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_us/worldpay/specificcountry` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor CVV | `payment_us/worldpay/cvv_fraud_case` | Alleen Commerce Enterprise |
| Status van bestelling instellen op vermoedelijke fraude voor Postcode AVS | `payment_us/worldpay/avs_fraud_case` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_us/worldpay/sort_order` | Alleen Commerce Enterprise |
| Ingeschakeld | `payment_us/eway/active` | Alleen Commerce Enterprise |
| Verbindingstype | `payment_us/eway/connection_type` | Alleen Commerce Enterprise |
| Titel | `payment_us/eway/title` | Alleen Commerce Enterprise |
| Betalingsactie | `payment_us/eway/payment_action` | Alleen Commerce Enterprise |
| Foutopsporing | `payment_us/eway/debug` | Alleen Commerce Enterprise |
| Typen creditcard | `payment_us/eway/cctypes` | Alleen Commerce Enterprise |
| Betaling door de kandidaat-lidstaten | `payment_us/eway/allowspecific` | Alleen Commerce Enterprise |
| Betaling door specifieke landen | `payment_us/eway/specificcountry` | Alleen Commerce Enterprise |
| Sorteervolgorde | `payment_us/eway/sort_order` | |

{style="table-layout:auto"}
