---
title: Verwijzing naar algemene configuratiepaden
description: Leer algemene en geavanceerde configuratiepaden en waarden voor Adobe Commerce. Ontdek systeem, veiligheid, en administratieve configuratieopties.
feature: Configuration, Observability, Roles/Permissions, System
exl-id: 3c557746-5182-4929-aebf-5b6fe76f0d8f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 0%

---

# Verwijzing naar algemene en geavanceerde configuratiepaden

Dit onderwerp maakt een lijst van algemene en geavanceerde configuratiewegen en __ [ niet gevoelige en systeem-specifieke waarden ](config-reference-sens.md). Het [`magento app:config:dump` bevel ](../cli/export-configuration.md) schrijft deze waarden aan het gedeelde configuratiedossier, `app/etc/config.php`, dat in broncontrole zou moeten zijn.

Om naar keuze om het even welke configuratiemontages met voeten te treden of gevoelige montages te plaatsen, zie [ de milieuvariabelen van het Gebruik om configuratiemontages ](override-config-settings.md#environment-variables) met voeten te treden.

## Algemene categorie

Deze sectie maakt een lijst van veranderlijke namen en configuratiewegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Algemeen**.

### Algemene paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > Algemeen > **Algemeen**.

| Naam | Config-pad | Alleen Commerce? | gevoelig? |
|--------------|--------------|--------------|--------------|
| Standaardland | `general/country/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Landen toestaan | `general/country/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Postcode is optioneel voor | `general/country/optional_zip_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| EU-landen | `general/country/eu_countries` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Bovenste bestemmingen | `general/country/destinations` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Status is vereist voor | `general/region/state_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Staat kiezen als dit optioneel is voor land | `general/region/display_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Tijdzone | `general/locale/timezone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Landinstelling | `general/locale/code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Gewichtseenheid | `general/locale/weight_unit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Eerste weekdag | `general/locale/firstday` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Weekenddagen | `general/locale/weekend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Toegangsbeperking | `general/restriction/is_active` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | |
| Restrictiemodus | `general/restriction/mode` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | |
| Opstartpagina | `general/restriction/http_redirect` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | |
| Openingspagina | `general/restriction/cms_page` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | |
| HTTP-respons | `general/restriction/http_status` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | |
| Winkelnaam | `general/store_information/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Telefoonnummer winkel | `general/store_information/phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Bewerkingstijden opslaan | `general/store_information/hours` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Land | `general/store_information/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Regio/staat | `general/store_information/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Postcode | `general/store_information/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Plaats | `general/store_information/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Adres | `general/store_information/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Straatadres, regel 2 | `general/store_information/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| BTW-nummer | `general/store_information/merchant_vat_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Modus Single Store inschakelen | `general/single_store_mode/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |

{style="table-layout:auto"}

### Webpaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Algemeen** > **Web**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Winkelcode toevoegen aan URL&#39;s | `web/url/use_store` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Automatisch omleiden naar basis-URL | `web/url/redirect_to_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Herschrijvingen webserver gebruiken | `web/seo/use_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beveiligde URL&#39;s gebruiken in winkelefront | `web/secure/use_in_frontend` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beveiligde URL&#39;s gebruiken in Beheer | `web/secure/use_in_adminhtml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP strikte vervoersbeveiliging (HSTS) inschakelen | `web/secure/enable_hsts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Onveilige upgrades | `web/secure/enable_upgrade_insecure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Offloader header | `web/secure/offloader_header` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Homepage van CMS | `web/default/cms_home_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS Geen routepagina | `web/default/cms_no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CMS No Cookies Page | `web/default/cms_no_cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Broodkruimels weergeven voor CMS-pagina&#39;s | `web/default/show_cms_breadcrumbs` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Cookie Lifetime | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Alleen HTTP gebruiken | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modus Cookie-beperking | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valideer REMOTE_ADDR. | `web/session/use_remote_addr` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_VIA valideren | `web/session/use_http_via` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_X_FORWARDED_FOR valideren | `web/session/use_http_x_forwarded_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTP_USER_AGENT valideren | `web/session/use_http_user_agent` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| SID gebruiken op Storefront | `web/session/use_frontend_sid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Omleiden naar CMS-pagina als Cookies zijn uitgeschakeld | `web/browser_capabilities/cookies` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bericht weergeven als JavaScript is uitgeschakeld | `web/browser_capabilities/javascript` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bericht weergeven als lokale opslag is uitgeschakeld | `web/browser_capabilities/local_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Paden voor instellen van valuta

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Algemene** > **opstelling van de Valuta**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Basisvaluta | `currency/options/base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardweergavemunt | `currency/options/default` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Toegestane valuta&#39;s | `currency/options/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Yahoo Finance Exchange | `TBD` | |
| Fixer.io | `TBD` | |
| Webservicex | `TBD` | |
| Time-out verbinding in seconden | `currency/yahoofinance/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Time-out verbinding in seconden | `currency/fixerio/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Time-out verbinding in seconden | `currency/webservicex/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld | `currency/import/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Service | `currency/import/service` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Begintijd | `currency/import/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequentie | `currency/import/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout bij e-mailontvanger | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout in e-mailafzender | `currency/import/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout in e-mailsjabloon | `currency/import/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Contactpaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Algemene** > **Contacten**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Contact met ons inschakelen | `contact/contact/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mails verzenden naar | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailsjabloon | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Paden rapporten

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Algemeen** > **Rapporten**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Jaarlijks begin | `reports/dashboard/ytd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Huidige maand start | `reports/dashboard/mtd_start` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Inhoudsbeheerpaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Algemeen** > **het Beheer van de Inhoud**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| WYSIWYG Editor inschakelen | `cms/wysiwyg/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Statische URL&#39;s gebruiken voor media-inhoud in WYSIWYG for Catalog | `cms/wysiwyg/use_static_urls_in_catalog` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hiërarchiefunctionaliteit inschakelen | `cms/hierarchy/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hiërarchiemetagegevens inschakelen | `cms/hierarchy/metadata_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Standaardlay-out voor hiërarchiemenu | `cms/hierarchy/menu_layout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### New Relic-rapportagepaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Algemeen** > **New Relic die** meldt.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| New Relic-integratie inschakelen | `newrelicreporting/general/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| New Relic-toepassingsnaam | `newrelicreporting/general/app_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Uitsnede inschakelen | `newrelicreporting/cron/enable_cron` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Geavanceerde categorie

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Geavanceerd**.

### Beheerpaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Geavanceerd** > **Admin**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| E-mailsjabloon wachtwoord vergeten | `admin/emails/forgot_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailafzender vergeten en opnieuw instellen | `admin/emails/forgot_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sjabloon voor gebruikersmeldingen | `admin/emails/user_notification_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opstartpagina | `admin/startup/menu_item_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aangepaste Admin-URL gebruiken | `admin/url/use_custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aangepast beheerpad gebruiken | `admin/url/use_custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Account delen beheren | `admin/security/admin_account_sharing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Beveiligingstype wachtwoord opnieuw instellen | `admin/security/password_reset_protection_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vervalperiode herstelkoppeling (uren) | `admin/security/password_reset_link_expiration_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Max. aantal aanvragen voor opnieuw instellen van wachtwoord | `admin/security/max_number_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Min. tijd tussen verzoeken om opnieuw wachtwoord instellen | `admin/security/min_time_between_password_reset_requests` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geheime sleutel toevoegen aan URL&#39;s | `admin/security/use_form_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aanmelden is hoofdlettergevoelig | `admin/security/use_case_sensitive_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur beheersessie (seconden) | `admin/security/session_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maximale aantal aanmeldfouten voor vergrendelingsaccount | `admin/security/lockout_failures` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vergrendelingstijd (minuten) | `admin/security/lockout_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wachtwoordlevensduur (dagen) | `admin/security/password_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Wachtwoordwijziging | `admin/security/password_is_forced` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Grafieken inschakelen | `admin/dashboard/enable_charts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CAPTCHA inschakelen in de beheerder | `admin/captcha/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lettertype | `admin/captcha/font` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Forms | `admin/captcha/forms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Weergavemodus | `admin/captcha/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aantal mislukte aanmeldpogingen | `admin/captcha/failed_attempts_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Time-out CAPTCHA (minuten) | `admin/captcha/timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aantal symbolen | `admin/captcha/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| In CAPTCHA gebruikte symbolen | `admin/captcha/symbols` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Hoofdlettergevoelig | `admin/captcha/case_sensitive` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakelde handelingen | `admin/magento_logging/actions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Systeempaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Geavanceerd** > **Systeem**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Levensduur berichten gelukt | `system/mysqlmq/successful_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Berichten opnieuw actief na | `system/mysqlmq/retry_inprogress_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verbroken levensduur berichten | `system/mysqlmq/failed_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur nieuwe berichten | `system/mysqlmq/new_messages_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Planningen elke genereren | `system/cron/index/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plan vooruit voor | `system/cron/index/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gemist als niet binnen loopt | `system/cron/index/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Historie opruimen elke | `system/cron/index/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur succesvolle historie | `system/cron/index/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Historieperiode mislukt | `system/cron/index/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afzonderlijk proces gebruiken | `system/cron/index/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Planningen elke genereren | `system/cron/default/schedule_generate_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Plan vooruit voor | `system/cron/default/schedule_ahead_for` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gemist als niet binnen loopt | `system/cron/default/schedule_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Historie opruimen elke | `system/cron/default/history_cleanup_every` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur succesvolle historie | `system/cron/default/history_success_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Historieperiode mislukt | `system/cron/default/history_failure_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Planningen elke genereren | `system/cron/staging/schedule_generate_every` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Plan vooruit voor | `system/cron/staging/schedule_ahead_for` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Gemist als niet binnen loopt | `system/cron/staging/schedule_lifetime` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Historie opruimen elke | `system/cron/staging/history_cleanup_every` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Levensduur succesvolle historie | `system/cron/staging/history_success_lifetime` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Historieperiode mislukt | `system/cron/staging/history_failure_lifetime` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Afzonderlijk proces gebruiken | `system/cron/staging/use_separate_process` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Planningen elke genereren | `system/cron/catalog/event/schedule_generate_every` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Plan vooruit voor | `system/cron/catalog/event/schedule_ahead_for` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Gemist als niet binnen loopt | `system/cron/catalog/event/schedule_lifetime` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Historie opruimen elke | `system/cron/catalog/event/history_cleanup_every` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Levensduur succesvolle historie | `system/cron/catalog/event/history_success_lifetime` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Historieperiode mislukt | `system/cron/catalog/event/history_failure_lifetime` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Afzonderlijk proces gebruiken | `system/cron/catalog/event/use_separate_process` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Afzonderlijk proces gebruiken | `system/cron/default/use_separate_process` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mailcommunicatie uitschakelen | `system/smtp/disable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Return-Path instellen | `system/smtp/set_return_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| E-mail met terugzendpad | `system/smtp/return_path_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geïnstalleerde valuta&#39;s | `system/currency/installed` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTTPS gebruiken om feed op te halen | `system/adminnotification/use_https` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequentie bijwerken | `system/adminnotification/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Laatste update | `system/adminnotification/last_update` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Geplande reservekopie inschakelen | `system/backup/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Back-uptype | `system/backup/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Begintijd | `system/backup/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequentie | `system/backup/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Onderhoudsmodus | `system/backup/maintenance` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Levensduur logbestandvermelding, dagen | `system/rotation/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Archiveringsfrequentie logboek | `system/rotation/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Caching-toepassing | `system/full_page_cache/caching_application` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| TTL voor openbare inhoud | `system/full_page_cache/ttl` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Respijtperiode | `system/full_page_cache/varnish/grace_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Configuratie exporteren | `system/full_page_cache/varnish/export_button_version4` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dagen opgeslagen in logbestand | `system/bulk/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Media-opslag | `system/media_storage_configuration/media_storage` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mediabase selecteren | `system/media_storage_configuration/media_database` (afgekeurd in Commerce 2.4.3) | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Update-tijd omgeving | `system/media_storage_configuration/configuration_update_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bestanden opslaan, dagen | `system/magento_scheduled_import_export_log/save_days` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opschonen van geplande bestandsgeschiedenis inschakelen | `system/magento_scheduled_import_export_log/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Begintijd | `system/magento_scheduled_import_export_log/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequentie | `system/magento_scheduled_import_export_log/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fout in e-mailsjabloon | `system/magento_scheduled_import_export_log/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

### Paden voor ontwikkelaars

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Geavanceerd** > **Ontwikkelaar**.

| Naam | Config-pad | Alleen Commerce? |
|--------------|--------------|--------------|
| Type workflow | `dev/front_end_development_workflow/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Symbolen toestaan | `dev/template/allow_symlink` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| HTML minificeren | `dev/template/minify_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tips voor sjabloonpad inschakelen voor Storefront | `dev/debug/template_hints_storefront` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tips voor sjabloonpad inschakelen voor Admin | `dev/debug/template_hints_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Bloknamen toevoegen aan hints | `dev/debug/template_hints_blocks` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Log naar bestand | `dev/debug/debug_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Log naar syslog | `dev/syslog/syslog_logging` |  |
| Ingeschakeld voor Storefront | `dev/translate_inline/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ingeschakeld voor Admin | `dev/translate_inline/active_admin` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript-bestanden samenvoegen | `dev/js/merge_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript Bundling inschakelen | `dev/js/enable_js_bundling` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| JavaScript-bestanden miniaturen | `dev/js/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Vertaalstrategie | `dev/js/translate_strategy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logbestand JS-fouten voor sessieopslag | `dev/js/session_storage_logging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS-bestanden samenvoegen | `dev/css/merge_css_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| CSS-bestanden miniaturen | `dev/css/minify_files` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Afbeeldingsadapter | `dev/image/default_adapter` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Statische bestanden ondertekenen | `dev/static/sign` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Asynchrone indexering | `dev/grid/async_indexing` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Door gebruiker gedefinieerde kenmerken in cache opslaan | `dev/caching/cache_user_defined_attributes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
