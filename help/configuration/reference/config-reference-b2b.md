---
title: Verwijzing naar configuratiepaden voor B2B-extensie
description: Zie een lijst met B2B-gerelateerde configuratiewaarden.
exl-id: 3414dea1-17c9-4462-8b8a-51a6045b0bc9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 0%

---

# Verwijzing naar configuratiepaden voor B2B-extensie

_Dit is beschikbaar voor instanties waarop B2B voor Adobe Commerce is geïnstalleerd._

Dit onderwerp maakt een lijst van configuratiepaden voor de Uitbreiding van de Onderneming B2B van de Handel. De [`magento app:config:dump` command](../cli/export-configuration.md) deze waarden naar het gedeelde configuratiebestand schrijft, `app/etc/config.php`, die onder broncontrole moeten staan.

>[!INFO]
>
>Deze referentielijsten _alleen_ configuratiepaden die uniek zijn voor B2B voor Adobe Commerce. Deze extensie bevat alle configuratiepaden voor Adobe Commerce.

Zie voor deze configuratiepaden:

- [Paden voor betalingsconfiguratie](config-reference-payment.md)
- [Verwijzing naar gevoelige en systeemspecifieke configuratiepaden](config-reference-sens.md)

Om naar keuze om het even welke configuratiemontages met voeten te treden of gevoelige montages te plaatsen, zie [Omgevingsvariabelen gebruiken om configuratie-instellingen te overschrijven](override-config-settings.md#environment-variables).

## Algemene categorie

In deze sectie worden de namen van variabelen en de configuratiepaden weergegeven die beschikbaar zijn voor opties onder Beheer **[!UICONTROL Stores]** > Instellingen > **[!UICONTROL Configuration]** > **[!UICONTROL General]**.

### B2B-functies, paden

Deze configuratiewaarden zijn beschikbaar in de Admin in **[!UICONTROL Stores]** > Instellingen > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.

| Naam | Config-pad | Versleuteld? | Systeemspecifiek? | Gevoelig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Bedrijf inschakelen | `btob/website_configuration/company_active` |  |  |  |
| Gedeelde catalogus inschakelen | `btob/website_configuration/sharedcatalog_active` |  |  |  |
| B2B-offerte inschakelen | `btob/website_configuration/negotiablequote_active` |  |  |  |
| Snelle volgorde inschakelen | `btob/website_configuration/quickorder_active` |  |  |  |
| Aanvraaglijst inschakelen | `btob/website_configuration/requisition_list_active` |  |  |  |
| Toepasselijke betalingsmethoden | `btob/default_b2b_payment_methods/applicable_payment_methods` |  |  |  |
| Betalingsmethoden | `btob/default_b2b_payment_methods/available_payment_methods` |  |  |  |

{style="table-layout:auto"}

## Categorie Klanten

In deze sectie worden de namen van variabelen en configuratiepaden weergegeven die beschikbaar zijn voor opties in de beheerdersruimte onder **[!UICONTROL Stores]** > Instellingen > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]**.

### Bedrijfsconfiguratiepaden

Deze configuratiewaarden zijn beschikbaar in de Admin in **[!UICONTROL Stores]** > Instellingen > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Company Configuration]**.

| Naam | Config-pad | Versleuteld? | Systeemspecifiek? | Gevoelig? |
|--------------|--------------|--------------|--------------|--------------|
| Bedrijfsregistratie toestaan vanuit de Storefront | `company/general/allow_company_registration` |  |  |  |
| E-mailontvanger bedrijfsinschrijving | `company/email/company_registration` |  |  | ![Gevoelig](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie van bedrijfsregistratie verzenden naar | `company/email/company_registration_copy` |  |  | ![Gevoelig](/help/assets/configuration/cloud-sens.png) |
| E-mailkopieermethode verzenden | `company/email/company_copy_method` |  |  |  |
| Standaard bedrijfsregistratie-e-mail | `company/email/company_notify_admin_template` |  |  |  |
| Aan klanten gerelateerde e-mails | `company/email/heading_customer` |  |  |  |
| Standaard e-mail aan verkoopvertegenwoordiger toegewezen | `company/email/customer_sales_representative_template` |  |  |  |
| Standaard Bedrijf toewijzen aan e-mail van klant | `company/email/customer_company_customer_assign_template` |  |  |  |
| Standaard bedrijfs Admin-e-mail toewijzen | `company/email/customer_assign_super_user_template` |  |  |  |
| Standaard bedrijfs Admin Inactieve E-mail | `company/email/customer_inactivate_super_user_template` |  |  |  |
| Standaard bedrijfbeheerder gewijzigd in e-mail voor lid | `company/email/customer_remove_super_user_template` |  |  |  |
| Standaardstatus actieve e-mail van klant | `company/email/customer_account_activated_template` |  |  |  |
| Standaard-e-mail met status van klant | `company/email/customer_account_locked_template` |  |  |  |
| Wijziging van bedrijfsstatus | `company/email/heading_company_status` |  |  |  |
| E-mailontvanger bedrijfstatus wijzigen | `company/email/company_status_change` |  |  |  |
| E-mailkopie bedrijfstatus wijzigen naar | `company/email/company_status_change_copy` |  |  | ![Gevoelig](/help/assets/configuration/cloud-sens.png) |
| E-mailkopieermethode verzenden | `company/email/company_status_copy_method` |  |  |  |
| Standaardbedrijfstatus wijzigen in Active 1-e-mail | `company/email/company_status_pending_approval_to_active_template` |  |  |  |
| Standaardbedrijfstatus wijzigen in Active 2-e-mail | `company/email/company_status_rejected_blocked_to_active_template` |  |  |  |
| Standaardwijziging bedrijfsstatus in afgewezen e-mail | `company/email/company_status_rejected_template` |  |  |  |
| Standaardwijziging bedrijfsstatus in geblokkeerde e-mail | `company/email/company_status_blocked_template` |  |  |  |
| Standaardwijziging bedrijfsstatus in afwachting van goedkeuring-e-mail | `company/email/company_status_pending_approval_template` |  |  |  |
| Bedrijfskrediet | `company/email/heading_company_credit` |  |  |  |
| E-mailafzender bedrijfskrediet wijzigen | `company/email/company_credit_change` |  |  | ![Gevoelig](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie van wijziging bedrijfskrediet verzenden naar | `company/email/company_credit_change_copy` |  |  |  |
| E-mailkopieermethode verzenden | `company/email/company_credit_copy_method` |  |  |  |
| Toegewezen e-mailsjabloon | `company/email/credit_allocated_email_template` |  |  |  |
| Bijgewerkte e-mailsjabloon | `company/email/credit_updated_email_template` |  |  |  |
| Terugbetaalde e-mailsjabloon | `company/email/credit_reimbursed_email_template` |  |  |  |
| Geretourneerde e-mailsjabloon | `company/email/credit_refunded_email_template` |  |  |  |
| Omgekeerde e-mailsjabloon | `company/email/credit_reverted_email_template` |  |  |  |

{style="table-layout:auto"}

### Bij aanvraag worden paden weergegeven

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Klanten** > **Aanvraaglijsten**.

| Naam | Config-pad | Versleuteld? | Systeemspecifiek? | Gevoelig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Aantal aanvraaglijsten | `requisitionlist/general/number_requisition_lists` |  |  |  |

{style="table-layout:auto"}

## Verkoopcategorie

In deze sectie worden de namen van variabelen en configuratiepaden weergegeven die beschikbaar zijn voor opties in de beheerdersruimte onder **Winkels** > Instellingen > **Configuratie** > **Verkoop**.

### E-mailpaden voor verkoop

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Verkoop** > **Verkoop-e-mails**.

| Naam | Config-pad | Versleuteld? | Systeemspecifiek? | Gevoelig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Ingeschakeld | `sales_email/quote/enabled` |  |  |  |
| Bijgewerkte prijsopgave (aan koper) | `sales_email/quote/updated_buyer_template` |  |  |  |
| Afgewezen prijssjabloon (aan koper) | `sales_email/quote/declined_buyer_template` |  |  |  |
| Nieuwe prijsopgave (voor verkoper) | `sales_email/quote/new_seller_template` |  |  |  |
| Bijgewerkte prijsopgave (voor verkoper) | `sales_email/quote/updated_seller_template` |  |  |  |
| Vervaldatum offerte (in 48 uur) | `sales_email/quote/expire_two_days_template` |  |  |  |
| Vervaldatum offerte (in 24 uur) | `sales_email/quote/expire_one_day_template` |  |  |  |
| Vervaldatum opnieuw instellen | `sales_email/quote/expire_reset_template` |  |  |  |
| E-mailkopie van offerte verzenden naar | `sales_email/quote/copy_to` |  |  | ![Gevoelig](/help/assets/configuration/cloud-sens.png) |
| Methode voor e-mail met offerte verzenden | `sales_email/quote/copy_method` |  |  |  |

{style="table-layout:auto"}

### Aanhalingspaden

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Verkoop** > **Aanhalingstekens**.

| Naam | Config-pad | Versleuteld? | Systeemspecifiek? | Gevoelig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Minimumbedrag | `quote/general/minimum_amount` |  |  |  |
| Bericht over minimumbedrag | `quote/general/minimum_amount_message` |  |  |  |
| Standaardvervalperiode | `quote/general/default_expiration_period` |  |  |  |
| Bestandsindelingen voor uploaden | `quote/attached_files/file_formats` |  |  |  |
| Maximale bestandsgrootte | `quote/attached_files/maximum_file_size` |  |  |  |
| Minimumbedrag | `quote/general/minimum_amount` |  |  |  |
| Bericht over minimumbedrag | `quote/general/minimum_amount_message` |  |  |  |
| Standaardvervalperiode | `quote/general/default_expiration_period` |  |  |  |
| Bestandsindelingen voor uploaden | `quote/attached_files/file_formats` |  |  |  |
| Maximale bestandsgrootte | `quote/attached_files/maximum_file_size` |  |  |  |

{style="table-layout:auto"}

## Paden voor betalingsmethoden

Deze configuratiewaarden zijn beschikbaar in de Admin in **Winkels** > Instellingen > **Configuratie** > **Verkoop** > **Betalingsmethoden**.

>[!INFO]
>
>De beschikbare paden worden bepaald door uw keuze van het Merchant-land.

| Naam | Config-pad | Versleuteld? | Systeemspecifiek? | Gevoelig? |
| -------------- | -------------- | -------------- | -------------- | -------------- |
| Ingeschakeld | `payment/au/companycredit/active` |  |  |  |
| Titel | `payment/au/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/au/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/au/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/au/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/au/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/au/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/au/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/es/companycredit/active` |  |  |  |
| Titel | `payment/es/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/es/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/es/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/es/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/es/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/es/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/es/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/companycredit/active` |  |  |  |
| Titel | `payment/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/nz/companycredit/active` |  |  |  |
| Titel | `payment/nz/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/nz/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/nz/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/nz/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/nz/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/nz/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/nz/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/us/companycredit/active` |  |  |  |
| Titel | `payment/us/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/us/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/us/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/us/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/us/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/us/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/us/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/gb/companycredit/active` |  |  |  |
| Titel | `payment/gb/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/gb/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/gb/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/gb/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/gb/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/gb/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/gb/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/de/companycredit/active` |  |  |  |
| Titel | `payment/de/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/de/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/de/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/de/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/de/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/de/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/de/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/other/companycredit/active` |  |  |  |
| Titel | `payment/other/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/other/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/other/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/other/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/other/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/other/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/other/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/ca/companycredit/active` |  |  |  |
| Titel | `payment/ca/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/ca/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/ca/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/ca/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/ca/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/ca/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/ca/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/hk/companycredit/active` |  |  |  |
| Titel | `payment/hk/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/hk/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/hk/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/hk/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/hk/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/hk/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/hk/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/jp/companycredit/active` |  |  |  |
| Titel | `payment/jp/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/jp/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/jp/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/jp/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/jp/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/jp/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/jp/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/fr/companycredit/active` |  |  |  |
| Titel | `payment/fr/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/fr/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/fr/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/fr/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/fr/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/fr/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/fr/companycredit/sort_order` |  |  |  |
| Ingeschakeld | `payment/it/companycredit/active` |  |  |  |
| Titel | `payment/it/companycredit/title` |  |  |  |
| Status van nieuwe bestelling | `payment/it/companycredit/order_status` |  |  |  |
| Betaling door de kandidaat-lidstaten | `payment/it/companycredit/allowspecific` |  |  |  |
| Betaling door specifieke landen | `payment/it/companycredit/specificcountry` |  |  |  |
| Totaal minimumbestelling | `payment/it/companycredit/min_order_total` |  |  |  |
| Maximum aantal bestellingen | `payment/it/companycredit/max_order_total` |  |  |  |
| Sorteervolgorde | `payment/it/companycredit/sort_order` |  |  |  |

{style="table-layout:auto"}
