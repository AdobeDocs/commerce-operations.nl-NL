---
title: Referentie persoonlijke gegevens van klant (versie 2.x)
description: Meer informatie over dataflow-diagrammen en toewijzingen van database-entiteiten voor persoonlijke gegevens van klanten in Adobe Commerce 2.x.
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Referentie persoonlijke gegevens van klant (versie 2.x)

>[!NOTE]
>
>Dit is een van de onderwerpen die Adobe Commerce-handelaren en -ontwikkelaars helpen zich voor te bereiden op naleving van privacyregels. Raadpleeg uw juridisch adviseur om te bepalen of en hoe uw bedrijf aan om het even welke wettelijke verplichtingen moet voldoen.

Gebruik de volgende dataflow diagrammen en de afbeeldingen van de gegevensbestandentiteit ter referentie wanneer het ontwikkelen van nalevingsprogramma&#39;s voor privacyverordeningen zoals:

- [GDPR](gdpr.md)
- [CCPA](ccpa.md)

## Dataflow-diagrammen

In de dataflow-diagrammen worden de typen gegevens weergegeven die klanten en beheerders kunnen invoeren en ophalen van de winkel en Admin.

### Punten voor gegevensinvoer vóór

Een gebruiker kan klant-, adres- en betalingsgegevens invoeren bij het registreren voor een account, tijdens het afrekenen en vergelijkbare gebeurtenissen.

![ Voorste punten van de gegevensingang ](../../assets/security-compliance/frontend-data-entry-points.svg)

### Punten voor gegevenstoegang vóór

Adobe Commerce laadt klantgegevens wanneer de klant zich aanmeldt en verschillende pagina&#39;s bekijkt, of checkt deze uit.

![ de toegangspunten van de voorste gegevens ](../../assets/security-compliance/frontend-data-access-points.svg)

### Punten voor achtergrondgegevensinvoer

Een handelaar kan klantinformatie, adresgegevens, en betalingsgegevens ingaan wanneer het creëren van een klant of een orde van Admin.

![ De punten van de de gegevensingang van het achtereind ](../../assets/security-compliance/backend-data-entry-points.svg)

### Gegevenstoegangspunten op de achtergrond

Adobe Commerce laadt klanteninformatie wanneer een handelaar verscheidene types van netten bekijkt, op een net klikt om gedetailleerde informatie te zien, en diverse andere taken uitvoert.

![ de toegangspunten van de achterste gegevens ](../../assets/security-compliance/backend-data-access-points.svg)

## Database-entiteiten

Adobe Commerce slaat voornamelijk klantspecifieke informatie op in de tabellen voor klanten, adressen, bestellingen, aanhalingstekens en betalingen. Andere tabellen bevatten verwijzingen naar de klant-id.

### Klantgegevens

Adobe Commerce kan worden geconfigureerd om de volgende klantkenmerken op te slaan:

- Geboortedatum
- E-mail
- Voornaam
- Geslacht
- Achternaam
- Middennaam/Initiaal
- Voorvoegsel naam
- Achtervoegsel naam

>[!NOTE]
>
>In overeenstemming met de huidige beste praktijken op het gebied van beveiliging en privacy, moet u zich bewust zijn van mogelijke juridische en beveiligingsrisico&#39;s die verbonden zijn aan de opslag van de volledige geboortedatum van de klant (maand, dag, jaar) samen met andere persoonlijke identificatoren, zoals volledige naam, voordat u dergelijke gegevens verzamelt of verwerkt.

#### `customer_entity` en &#39;customer_entity&#39;-verwijzingen

De volgende kolommen in de tabel `customer_entity` bevatten klantgegevens:

| Kolom | Gegevenstype |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | date |
| `gender` | small(5) |

Deze tabellen verwijzen naar `customer_entity` en kunnen aangepaste klantkenmerken bevatten:

| Tabel | Kolom | Gegevenstype |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimaal (12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | text |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` table

De volgende kolommen in de tabel `customer_grid_flat` bevatten klantgegevens:

| Kolom | Gegevenstype |
| -------------------- | ------------ |
| `name` | text |
| `email` | varchar(255) |
| `dob` | date |
| `gender` | int(11) |
| `shipping_full` | text |
| `billing_full` | text |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### Adresgegevens

Adobe Commerce slaat de volgende klantkenmerken op:

- Plaats
- Bedrijf
- Land
- Fax
- Voornaam
- Achternaam
- Middennaam/Initiaal
- Voorvoegsel naam
- Achtervoegsel naam
- Telefoonnummer
- Staat/provincie
- Staat/provincie-id
- Adres
- BTW-nummer
- Postcode

#### `customer_address_entity` en `customer_address_entity` verwijzingen

De volgende kolommen in de tabel `customer_address_entity` bevatten klantgegevens:

| Kolom | Gegevenstype |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | text |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

Deze tabellen verwijzen naar `customer_address_entity` en kunnen aangepaste klantkenmerken bevatten:

| Tabel | Kolom | Gegevenstype |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimaal (12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | text |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Ordergegevens

De tabellen `sales_order` en verwante tabellen bevatten de naam, het facturerings- en verzendadres van de klant en verwante gegevens.

#### `sales_order` table

De volgende kolommen in de tabel `sales_order` bevatten klantgegevens:

| Kolom | Gegevenstype |
| --------------------- | ------------ |
| `customer_dob` | datetime |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address` table

De tabel `sales_order_address` bevat het adres van de klant.

| Kolom | Gegevenstype |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid` table

De volgende kolommen in de tabel `sales_order_grid` bevatten klantgegevens:

| Kolom | Gegevenstype |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### Offertegegevens

Aanhalingstekens bevatten de naam, het e-mailadres, het adres en verwante gegevens van een klant.

#### `quote` table

De volgende kolommen in de tabel `quote` bevatten klantgegevens:

| Kolom | Gegevenstype |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | datetime |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` table

De volgende kolommen in de tabel `quote_address` bevatten klantgegevens:

| Kolom | Gegevenstype |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### Betalingsgegevens

De tabel `sales_order_payment` bevat creditcardgegevens en andere transactiegegevens.

| Kolom | Gegevenstype |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | text |

### Uitnodigingsgegevens

Adobe Commerce kan zo worden geconfigureerd dat klanten uitnodigingen kunnen verzenden naar persoonlijke verkoop en gebeurtenissen.

#### `magento_invitation` table

De tabel `magento_invitation` bevat de klant-id, e-mail en referentie-id.

| Kolom | Gegevenstype |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` table

De tabel `magento_invitation_track` bevat ook klantgegevens.

| Kolom | Gegevenstype |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### Diverse tabellen die verwijzen naar klant

De volgende tabellen bevatten een kolom `customer_id` :

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
