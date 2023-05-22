---
title: Verwijzing naar configuratiepaden van klanten
description: Zie een lijst van de waarden van de klantenconfiguratie.
feature: Configuration, Customers
exl-id: a0571423-6fbd-4cfc-9797-a13c0c24bb53
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 0%

---

# Verwijzing naar configuratiepaden van klanten

In deze sectie worden de namen van variabelen en configuratiepaden weergegeven die beschikbaar zijn voor opties in de beheerdersruimte onder **Winkels** > Instellingen > **Configuratie** > **Klanten**.

De [`magento app:config:dump` command](../cli/export-configuration.md) deze waarden naar het gedeelde configuratiebestand schrijft, `app/etc/config.php`, die onder broncontrole moeten staan. Om naar keuze om het even welke configuratiemontages met voeten te treden of gevoelige montages te plaatsen, zie [Omgevingsvariabelen gebruiken om configuratie-instellingen te overschrijven](override-config-settings.md#environment-variables). Dit onderwerp doet _niet_ list [gevoelige en systeemspecifieke waarden](config-reference-sens.md).

## Paden voor nieuwsbrief

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Klanten** > **Nieuwsbrief**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| Abonnement op gasten toestaan | `newsletter/subscription/allow_guest_subscribe` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Moet worden bevestigd | `newsletter/subscription/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bevestiging e-mailafzender | `newsletter/subscription/confirm_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bevestigings-e-mailsjabloon | `newsletter/subscription/confirm_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender succesvol | `newsletter/subscription/success_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon met succes | `newsletter/subscription/success_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abonnement op e-mailafzender opzeggen | `newsletter/subscription/un_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon voor abonnement opzeggen | `newsletter/subscription/un_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Configuratiepaden van de klant

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Klanten** > **Klantconfiguratie**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| Interval online minuten | `customer/online_customers/online_minutes_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Klantaccounts delen | `customer/account_share/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatische toewijzing aan Klantengroep inschakelen | `customer/create_account/auto_group_assign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Belastingberekening op basis van | `customer/create_account/tax_calculation_address_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardgroep | `customer/create_account/default_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groep voor geldige BTW-ID - Binnenland | `customer/create_account/viv_domestic_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groep voor geldig BTW-identificatienummer - Intra-Unie | `customer/create_account/viv_intra_union_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Groep voor ongeldig BTW-identificatienummer | `customer/create_account/viv_invalid_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Foutgroep validatie | `customer/create_account/viv_error_group` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valideren bij elke transactie | `customer/create_account/viv_on_each_transaction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardwaarde voor automatische groepswijzigingen op basis van BTW-ID uitschakelen | `customer/create_account/viv_disable_auto_group_assign_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Btw-nummer weergeven op winkel | `customer/create_account/vat_frontend_visibility` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaard-welkomste-mail | `customer/create_account/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaard welkomstbericht zonder wachtwoord | `customer/create_account/email_no_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender | `customer/create_account/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailbevestiging vereisen | `customer/create_account/confirm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailadres voor bevestiging | `customer/create_account/email_confirmation_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Welkom-e-mail | `customer/create_account/email_confirmed_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persoonlijke gebruikersnaam genereren | `customer/create_account/generate_human_friendly_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beveiligingstype wachtwoord opnieuw instellen | `customer/password/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Max. aantal aanvragen voor opnieuw instellen van wachtwoord | `customer/password/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Min. tijd tussen verzoeken om het opnieuw instellen van wachtwoorden | `customer/password/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon vergeten | `customer/password/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon onthouden | `customer/password/remind_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wachtwoordsjabloon opnieuw instellen | `customer/password/reset_password_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender wachtwoordsjabloon | `customer/password/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vervalperiode herstelkoppeling (uren) | `customer/password/reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch aanvullen inschakelen bij inlognaam/wachtwoordformulieren vergeten | `customer/password/autocomplete_on_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aantal vereiste tekenklassen | `customer/password/required_character_classes_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale aantal aanmeldfouten voor vergrendelingsaccount | `customer/password/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minimale wachtwoordlengte | `customer/password/minimum_password_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vergrendelingstijd (minuten) | `customer/password/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aantal lijnen in een Adres van de Straat | `customer/address/street_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Voorvoegsel tonen | `customer/address/prefix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opties voor neerzetten voorvoegsel | `customer/address/prefix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Middennaam tonen (oorspronkelijk) | `customer/address/middlename_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Achtervoegsel tonen | `customer/address/suffix_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opties achtervoegsel | `customer/address/suffix_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geboortedatum tonen | `customer/address/dob_show`<br>In overeenstemming met de huidige beste praktijken op het gebied van beveiliging en privacy, moet u zich bewust zijn van mogelijke juridische en beveiligingsrisico&#39;s die verbonden zijn aan de opslag van de volledige geboortedatum van de klant (maand, dag, jaar) samen met andere persoonlijke identificatoren, zoals volledige naam, voordat u dergelijke gegevens verzamelt of verwerkt. | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| BTW-nummer tonen | `customer/address/taxvat_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geslacht tonen | `customer/address/gender_show` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Kredietfunctie voor winkel inschakelen | `customer/magento_customerbalance/is_enabled` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Winkelcreditatiegeschiedenis aan klanten tonen | `customer/magento_customerbalance/show_history` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Winkelcreditering automatisch terugbetalen | `customer/magento_customerbalance/refund_automatically` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| E-mailafzender bijwerken van creditcard winkel | `customer/magento_customerbalance/email_identity` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| E-mailtemplate voor bijwerken van creditering opslaan | `customer/magento_customerbalance/email_template` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Klant omleiden naar het dashboard Account na aanmelding | `customer/startup/redirect_dashboard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tekst | `customer/address_templates/text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tekst één regel | `customer/address_templates/oneline` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML | `customer/address_templates/html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| PDF | `customer/address_templates/pdf` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Functionaliteit van klantsegment inschakelen | `customer/magento_customersegment/is_enabled` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| CAPTCHA inschakelen in Storefront | `customer/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lettertype | `customer/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `customer/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergavemodus | `customer/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aantal mislukte aanmeldpogingen | `customer/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Time-out CAPTCHA (minuten) | `customer/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aantal symbolen | `customer/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| In CAPTCHA gebruikte symbolen | `customer/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hoofdlettergevoelig | `customer/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Lijstpaden wissen

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Klanten** > **Wish List**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| Ingeschakeld | `wishlist/general/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Meerdere wenslijsten inschakelen | `wishlist/general/multiple_enabled` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Aantal lijsten met meerdere wensen | `wishlist/general/multiple_wishlist_number` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| E-mailafzender | `wishlist/email/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon | `wishlist/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximumaantal e-mails toegestaan om te worden verzonden | `wishlist/email/number_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lengtelimiet e-mailtekst | `wishlist/email/text_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Overzicht van wenslijsten weergeven | `wishlist/wishlist_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Uitnodigingspaden

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Klanten** > **Uitnodigingen**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| Uitnodigingsfunctionaliteit inschakelen | `magento_invitation/general/enabled` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Uitnodigingen inschakelen op Storefront | `magento_invitation/general/enabled_on_front` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Aangewezen klantengroep | `magento_invitation/general/registration_use_inviter_group` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Registratie van nieuwe accounts | `magento_invitation/general/registration_required_invitation` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Klanten toestaan eigen bericht toe te voegen aan e-mail met uitnodiging | `magento_invitation/general/allow_customer_message` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Max. uitnodigingen toegestaan om tegelijk te worden verzonden | `magento_invitation/general/max_invitation_amount_per_send` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| E-mailafzender Klantenuitnodiging | `magento_invitation/email/identity` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| E-mailsjabloon voor klantuitnodiging | `magento_invitation/email/template` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Padpaden achterwaarts

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Klanten** > **Punten omkeren**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| Functionaliteit voor beloningspunten inschakelen | `magento_reward/general/is_enabled` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Enable Reward Points Functionaliteit on Storefront | `magento_reward/general/is_enabled_on_front` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Klanten kunnen de historie van Punten terugbetalen bekijken | `magento_reward/general/publish_history` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Drempel voor saldoverlaging beloningspunten | `magento_reward/general/min_points_balance` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Punten in omgekeerde richting bij | `magento_reward/general/max_points_balance` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Punten omkeren verloopt over (dagen) | `magento_reward/general/expiration_days` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Berekening van de vervalpunten van de punten met terugwerkende kracht | `magento_reward/general/expiry_calculation` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Punten terugbetalen automatisch | `magento_reward/general/refund_automatically` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Terugbetalingspunten automatisch van restitutiebedrag aftrekken | `magento_reward/general/deduct_automatically` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Openingspagina | `magento_reward/general/landing_page` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Aanschaffen | `magento_reward/points/order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Registratie | `magento_reward/points/register` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Aanmelden voor nieuwsbrief | `magento_reward/points/newsletter` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Uitnodiging naar klant converteren | `magento_reward/points/invitation_customer` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Uitnodiging voor beperking aantal conversies van klanten | `magento_reward/points/invitation_customer_limit` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Uitnodiging omzetten in bestelling | `magento_reward/points/invitation_order` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Limiet voor aantal aanvragen voor omzetting van bestellingen | `magento_reward/points/invitation_order_limit` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Uitnodiging voor conversie naar order Reward | `magento_reward/points/invitation_order_frequency` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Inzending controleren | `magento_reward/points/review` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Limiet voor aantal ingediende revisies met beloning | `magento_reward/points/review_limit` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| E-mailafzender | `magento_reward/notification/email_sender` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Abonneren op klanten standaard | `magento_reward/notification/subscribe_by_default` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Update-e-mail balanceren | `magento_reward/notification/balance_update_template` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Waarschuwing: e-mail vervalt punten | `magento_reward/notification/expiry_warning_template` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Vervalwaarschuwing voor (dagen) | `magento_reward/notification/expiry_day_before` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Promotiepaden

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Klanten** > **Aanbiedingen**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| E-mails herinnering inschakelen | `promo/magento_reminder/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequentie | `promo/magento_reminder/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Interval | `promo/magento_reminder/interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Minuut van het uur | `promo/magento_reminder/minutes` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Begintijd | `promo/magento_reminder/time` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Maximum aantal e-mails per één run | `promo/magento_reminder/limit` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Drempel voor fout bij verzenden van e-mail | `promo/magento_reminder/threshold` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Herinnering E-mailafzender | `promo/magento_reminder/identity` | ![Alleen handel](/help/assets/configuration/cloud-ee.png) |
| Lengte code | `promo/auto_generated_coupon_codes/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codeopmaak | `promo/auto_generated_coupon_codes/format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codevoorvoegsel | `promo/auto_generated_coupon_codes/prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codeachtervoegsel | `promo/auto_generated_coupon_codes/suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Streep om de X-tekens | `promo/auto_generated_coupon_codes/dash` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Cadeauregisterpaden

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Klanten** > **Cadeauregister**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| Cadeauregister inschakelen | `magento_giftregistry/general/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximum aantal geregistreerde personen | `magento_giftregistry/general/max_registrant` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon | `magento_giftregistry/owner_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender | `magento_giftregistry/owner_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon | `magento_giftregistry/sharing_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender | `magento_giftregistry/sharing_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale drempel voor verzonden e-mailberichten | `magento_giftregistry/sharing_email/send_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon | `magento_giftregistry/update_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender | `magento_giftregistry/update_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Blijvende winkelwagentjes

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Klanten** > **Blijvende winkelwagentje**.

| Naam | Config-pad | Alleen handel? |
|--------------|--------------|--------------|
| Persistentie inschakelen | `persistent/options/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur (seconden) | `persistent/options/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| &quot;Onthoud mijn gegevens&quot; inschakelen | `persistent/options/remember_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardwaarde &quot;Onthouden&quot; | `persistent/options/remember_default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Persistentie bij afmelden wissen | `persistent/options/logout_clear` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Winkelwagentje behouden | `persistent/options/shopping_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gewenste lijst behouden | `persistent/options/wishlist` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Onlangs bestelde objecten behouden | `persistent/options/recently_ordered` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vergelijkbare producten behouden | `persistent/options/compare_current` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vergelijkingsgeschiedenis behouden | `persistent/options/compare_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Onlangs bekeken producten behouden | `persistent/options/recently_viewed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lidmaatschap en segmentatie van klantgroep behouden | `persistent/options/customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
