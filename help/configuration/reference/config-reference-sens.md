---
title: Gevoelige en systeemspecifieke paden
description: Leer over gevoelige en systeem-specifieke configuratiepaden voor Adobe Commerce. Ontdek veilige configuratie en milieu veranderlijk beheer.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '3684'
ht-degree: 0%

---

# Gevoelige en systeemspecifieke instellingen

Dit onderwerp maakt een lijst van configuratiepaden voor systeem-specifieke en gevoelige montages:

- Het [`magento app:config:dump` bevel ](../cli/export-configuration.md) schrijft systeem-specifieke montages aan het systeem-specifieke configuratiedossier, `app/etc/env.php`, dat __ niet in broncontrole zou moeten zijn. Het schrijft ook gedeelde configuratie voor alle instanties van Commerce aan `app/etc/config.php`, zou dit dossier __ in broncontrole moeten zijn.
- De [`magento config:sensitive:set` bevel ](../cli/set-configuration-values.md) schrijft gevoelige montages aan `app/etc/env.php`.

  U kunt gevoelige waarden ook plaatsen gebruikend configuratievariabelen zoals die in [ het omgevingsvariabelen van het Gebruik worden besproken om configuratiemontages ](../reference/override-config-settings.md#environment-variables) met voeten te treden.

Voor een lijst van andere configuratiepaden raadpleegt u:

- [Alle configuratiepaden behalve betalingen](../reference/config-reference-general.md)
- [ de configuratiewegen van de Betaling ](../reference/config-reference-payment.md).

>[!INFO]
>
>Alle configuratiepaden in dit onderwerp zijn gevoelig. In de kolom `System-specific?` wordt aangegeven welke waarden ook systeemspecifiek zijn.

## Algemene categorie gevoelige en systeemspecifieke paden

Deze sectie maakt een lijst van veranderlijke namen en configuratiewegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Algemeen**.

### De wegen van het Web gevoelige en systeem-specifieke wegen

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Algemeen** > **Web**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Basis-URL | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| URL basiskoppeling | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Basis-URL voor statische weergavebestanden | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Basis-URL voor gebruikersmediabestanden | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Beveiligde basis-URL | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Secure Base Link URL | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Beveiligde basis-URL voor statische weergavebestanden | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Beveiligde basis-URL voor gebruikersmediabestanden | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Standaardweb-URL | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Standaard-geen-route-URL | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Pad cookie | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Cookie-domein | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Cookie Lifetime | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Alleen HTTP gebruiken | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Modus Cookie-beperking | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### De opstelling van de valuta gevoelige en systeem-specifieke wegen

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Algemene** > **opstelling van de Valuta**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fout bij e-mailontvanger | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### E-mailadresgevoelige en systeemspecifieke paden opslaan

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **E-mailConfiguratie** > **Algemene** > **E-mailadressen van de Opslag**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Naam afzender | `trans_email/ident_general/name` | | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail afzender | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Naam afzender | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail afzender | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Naam afzender | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail afzender | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Naam afzender | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail afzender | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Naam afzender | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail afzender | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Contacteert gevoelige en systeem-specifieke wegen

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Algemene** > **Contacten**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-mails verzenden naar | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailafzender | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailsjabloon | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### New Relic die gevoelige en systeemspecifieke wegen meldt

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Algemeen** > **New Relic die** meldt.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| New Relic-account-id | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| New Relic-toepassings-id | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| New Relic API-sleutel | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor inzichten | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| New Relic API-URL | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Insights API URL | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## De categorie van klanten gevoelige en systeemspecifieke wegen

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Klanten** op.

### De configuratiesgevoelig van de klant en systeem-specifieke wegen

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Klanten** > **de Configuratie van de Klant**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Standaard-e-maildomein | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Cataloguscategorie

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Catalogus** op.

### Met catalogi samenhangende en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Catalogus** > **Catalogus**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fout bij e-mailontvanger | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| YouTube API-sleutel | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Hostnaam van Solr Server | `catalog/search/solr_server_hostname` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Solr-serverpoort | `catalog/search/solr_server_port` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Gebruikersnaam server Solr | `catalog/search/solr_server_username` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Solr-server | `catalog/search/solr_server_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Pad naar soleserver | `catalog/search/solr_server_path` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Hostnaam Elasticsearch-server | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch-serverpoort | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch-indexvoorvoegsel | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Elasticsearch HTTP Auth inschakelen | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-gebruikersnaam | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-wachtwoord | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Time-out Elasticsearch-server | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-gebruikersnaam | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Elasticsearch HTTP-wachtwoord | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Time-out Elasticsearch-server | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Hostnaam van OpenSearch-server | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| OpenSearch-serverpoort | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Voorvoegsel van OpenSearch-index | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| OpenSearch HTTP Auth inschakelen | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| HTTP-gebruikersnaam van OpenSearch | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| HTTP-wachtwoord voor OpenSearch | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Time-out voor OpenSearch-server | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>OpenSearch-instellingen zijn geïntroduceerd in Adobe Commerce 2.4.6.

### Overzichtsgevoelige en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Catalogus** > **Voorraad**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Google API-sleutel | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### XML sitemap-gevoelige en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Sporen** > Montages > **Configuratie** > **Catalogus** > **Sitemap van XML**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fout bij e-mailontvanger | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Verkoopcategorie

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Verkoop**.

### Verzendinstellingen zijn gevoelig en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Verschepende Montages**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Land | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Regio/staat | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Postcode | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Plaats | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Adres | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Straatadres, regel 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Liveaccount | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Verkoop e-mailgevoelige en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Verkoop E-mail van de Verkoop**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-mailkopie van bestelling verzenden naar | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie voor bestelling verzenden naar | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Factuur-e-mailkopie verzenden naar | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie van factuuropmerking verzenden naar | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Verzendkopie verzenden naar | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie van verzendopmerking verzenden naar | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie van creditcard verzenden naar | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie van opmerking over creditcard verzenden naar | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie voor afhalen naar | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Uitchecken van gevoelige en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Controle**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Betaling is mislukt Kopie e-mail verzenden naar | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Voor Google API gevoelige en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Google API**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Container-id | `google/analytics/container_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Bezorgingsmethoden, gevoelige en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Methoden van de Levering**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Gateway-URL | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Beveiligde gateway-URL | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Titel | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gebruikersnaam | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Gebruikersnaam | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangsnummer | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| XML-URL bijhouden | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Gateway XML URL | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Verzendnummer | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Foutopsporing | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Account-id | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sleutel | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Meternummer | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegang-id | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Foutopsporing | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | |
| Rekeningnummer | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Gateway-URL | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox-modus | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Verkoopgevoelige en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Verkoop**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Naam contactpersoon | `sales/magento_rma/store_name` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Adres | `sales/magento_rma/address` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Adres | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Plaats | `sales/magento_rma/city` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Staat/provincie | `sales/magento_rma/region_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Postcode | `sales/magento_rma/zip` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Land | `sales/magento_rma/country_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| RMA-e-mailkopie verzenden naar | `sales_email/magento_rma/copy_to` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie voor RMA-autorisatie verzenden naar | `sales_email/magento_rma_auth/copy_to` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie van RMA-opmerking verzenden naar | `sales_email/magento_rma_comment/copy_to` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailkopie van RMA-opmerking verzenden naar | `sales_email/magento_rma_customer_comment/copy_to` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Google API-paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Opslag** > Montages > **Configuratie** > **Verkoop** > **Google API**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Rekeningnummer | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Geavanceerde categorie

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Geavanceerd**.

### Beheergevoelige en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Geavanceerd** > **Admin**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Aangepaste Admin-URL | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Aangepast beheerpad | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Systeemgevoelige en systeemspecifieke paden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Geavanceerd** > **Systeem**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Fout bij e-mailontvanger | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangslijst | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Fout in e-mailafzender | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Beheerbare en systeemspecifieke paden voor ontwikkelaars

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Geavanceerd** > **Ontwikkelaar**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Toegestane IPs (komma&#39;s gescheiden) | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Geavanceerde categorie

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Geavanceerd**.

### Systeempaden

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Geavanceerd** > **Systeem**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Poort (25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Backend-host | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Backend-poort | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Paden voor ontwikkelaars

Deze configuratiewaarden zijn beschikbaar in Admin in **Slaat** > Montages > **Configuratie** > **Geavanceerd** > **Ontwikkelaar**.

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Logbestand JS-fouten in opslagsleutel voor sessie | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Betalingsgevoelige en systeemspecifieke paden

Deze sectie maakt een lijst van veranderlijke namen en config wegen beschikbaar voor opties in Admin onder **Slaat** > Montages > **Configuratie** > **Verkoop** > **Betaling**.

### Algemene variabele

| Naam | Config-pad | Alleen Commerce? | Versleuteld? |
|--------------|--------------|--------------|--------------|
| Land van koophandel | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>Uw keus voor deze variabele bepaalt welke [ Internationale wegen ](#international-paths) u kunt gebruiken.

### PayPal-gevoelige en systeemspecifieke paden

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-mail gekoppeld aan PayPal Merchant Account (optioneel) | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant Account ID | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Uitgever-id | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Aanmelden | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Custom Endpoint Hostname of IP-Address | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox-modus | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Foutopsporingsmodus | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Foutopsporingsmodus | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| SFTP-referenties | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Pro-gevoelige en systeemspecifieke paden

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Gebruiker | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Aangepast pad | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Gebruiker | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Partner | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Proxyhost | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Proxypoort | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Foutopsporingsmodus | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| SFTP-referenties | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Creditcardinstellingen | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Link-gevoelige en systeemspecifieke paden

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Gebruiker | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Proxy gebruiken | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Proxyhost | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Proxypoort | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Foutopsporingsmodus | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Methode URL voor Cancel URL en Return URL | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Foutopsporingsmodus | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| SFTP-referenties | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro gevoelige en systeemspecifieke paden

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| API-gebruikersnaam | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-wachtwoord | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-handtekening | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-certificaat | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Proxyhost | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Proxypoort | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox-modus | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| SFTP-referenties | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro Gehoste gevoelige en systeemspecifieke paden

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Foutopsporingsmodus | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| SFTP-referenties | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Braintree-gevoelige en systeemspecifieke paden

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Merchant ID | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Openbare sleutel | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Persoonlijke sleutel | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant Account ID | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Kount Merchant ID | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant Name negeren | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Telefoon | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Paden voor cheque- en postwissel

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Controle verzenden naar | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Internationale paden

| Naam | Config-pad | Alleen Commerce? | Versleuteld? | Systeemspecifiek? | gevoelig? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Transactiecode | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_au/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_au/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_au/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_au/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Wachtwoord voor reactie op betaling | `payment_au/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_au/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox-modus | `payment_au/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_au/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_au/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_au/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_au/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_au/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_au/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_es/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_es/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_es/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_es/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Wachtwoord voor reactie op betaling | `payment_es/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_es/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_es/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Foutopsporing | `payment_es/worldpay/debug` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_es/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_es/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_es/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_es/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_es/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_es/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_es/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_nz/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_nz/worldpay/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_nz/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_nz/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_nz/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_nz/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_nz/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_nz/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_nz/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Proxyhost | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Proxypoort | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Foutopsporingsmodus | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Methode URL voor Cancel URL en Return URL | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_us/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_us/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_us/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_us/worldpay/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_us/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_us/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_us/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_us/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_us/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_us/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_us/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_gb/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_gb/worldpay/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_gb/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_gb/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_gb/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_gb/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_gb/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_gb/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_gb/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_de/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_de/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_de/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_de/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Transactiecode | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor reactie op betaling | `payment_de/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_de/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Foutopsporing | `payment_de/worldpay/debug` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_de/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_de/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_de/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_de/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_de/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_de/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_de/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Gateway-URL | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Transactiecode | `payment_other/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_other/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_other/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Status van nieuwe bestelling | `payment_other/cybersource/order_status` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_other/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Wachtwoord voor reactie op betaling | `payment_other/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_other/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_other/worldpay/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_other/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_other/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_other/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_other/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_other/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_other/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_other/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_ca/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_ca/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_ca/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Status van nieuwe bestelling | `payment_ca/cybersource/order_status` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Testmodus | `payment_ca/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Wachtwoord voor reactie op betaling | `payment_ca/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_ca/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_ca/worldpay/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_ca/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_ca/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_ca/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_ca/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_ca/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_ca/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_ca/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_hk/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_hk/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_hk/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_hk/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor reactie op betaling | `payment_hk/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_hk/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_hk/worldpay/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live API-sleutel | `payment_hk/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_hk/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_hk/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_hk/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_hk/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_hk/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_jp/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_jp/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_jp/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Status van nieuwe bestelling | `payment_jp/cybersource/order_status` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Testmodus | `payment_jp/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Wachtwoord voor reactie op betaling | `payment_jp/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_jp/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_jp/worldpay/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_jp/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_jp/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_jp/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_jp/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_jp/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_jp/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_jp/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_fr/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_fr/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_fr/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_fr/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Wachtwoord voor reactie op betaling | `payment_fr/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_fr/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_fr/worldpay/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |  | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_fr/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_fr/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_fr/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_fr/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_fr/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_fr/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_fr/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Gateway-URL | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiedetails URL | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_it/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_it/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_it/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_it/cybersource/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Wachtwoord voor reactie op betaling | `payment_it/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_it/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Testmodus | `payment_it/worldpay/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Sandbox-modus | `payment_it/eway/sandbox_flag` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) |
| Live API-sleutel | `payment_it/eway/live_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor Live API | `payment_it/eway/live_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Live Client-coderingssleutel | `payment_it/eway/live_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel voor sandbox | `payment_it/eway/sandbox_api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor sandbox-API | `payment_it/eway/sandbox_api_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Sandbox Client-side coderingssleutel | `payment_it/eway/sandbox_encryption_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-sleutel | `fraud_protection/signifyd/api_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-URL | `fraud_protection/signifyd/api_url` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |  | ![ Sys-specific ](/help/assets/configuration/cloud-env.png) | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_au/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_au/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_es/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_es/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_es/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties |
| SFTP-referenties | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_nz/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_nz/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_nz/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_nz/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_nz/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_nz/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor reactie op betaling | `payment_nz/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_nz/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_nz/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_nz/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_us/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_us/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_us/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_us/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor reactie op betaling | `payment_us/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_us/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_us/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_us/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_gb/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_gb/cybersource/transaction_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_gb/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Toegangstoets | `payment_gb/cybersource/access_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Geheime sleutel | `payment_gb/cybersource/secret_key` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Transactiecode | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_gb/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor reactie op betaling | `payment_gb/worldpay/response_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_gb/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Wachtwoord voor externe beheerdersautorisatie | `payment_gb/worldpay/auth_password` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Betaalbaar maken voor | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_de/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_de/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_de/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Installatie-id voor extern beheer | `payment_de/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_de/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Betaalbaar maken voor | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Status van nieuwe bestelling | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_other/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_other/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_other/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_other/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_other/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Betaalbaar maken voor | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Status van nieuwe bestelling | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_ca/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_ca/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_ca/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_ca/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_ca/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Betaalbaar maken voor | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_hk/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_hk/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_hk/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_hk/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_hk/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Handtekeningvelden | `payment_hk/worldpay/signature_fields` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Betaalbaar maken voor | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_jp/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_jp/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_jp/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) |
| Installatie-id voor extern beheer | `payment_jp/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_jp/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Handtekeningvelden | `payment_jp/worldpay/signature_fields` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Betaalbaar maken voor | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_fr/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_fr/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_fr/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_fr/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_fr/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Handtekeningvelden | `payment_fr/worldpay/signature_fields` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| SFTP-referenties | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Betaalbaar maken voor | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Controle verzenden naar | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| API-aanmeldings-id | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mailklant | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| E-mail van de handelaar | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Merchant ID | `payment_it/cybersource/merchant_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Profiel-id | `payment_it/cybersource/profile_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | ![ Gecodeerd ](/help/assets/configuration/cloud-enc.png) | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id | `payment_it/worldpay/installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| Installatie-id voor extern beheer | `payment_it/worldpay/admin_installation_id` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |
| MD5 Secret for Transactions | `payment_it/worldpay/md5_secret` | ![ Commerce-slechts ](/help/assets/configuration/cloud-ee.png) | | | ![ Gevoelig ](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
