---
title: Master databases handmatig configureren
description: Zie begeleiding bij het manueel vormen van de gespleten gegevensbestandoplossing.
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 0%

---


# Master databases handmatig configureren

{{ee-only}}

{{deprecate-split-db}}

Als de toepassing van de Handel reeds in productie is of als u reeds douanecode of componenten hebt geïnstalleerd, zou u gespleten gegevensbestanden kunnen moeten manueel vormen. Neem voordat u doorgaat contact op met Adobe Commerce Support om te controleren of dit in uw geval noodzakelijk is.

Het handmatig splitsen van databases omvat:

- Maak de [uitchecken](https://glossary.magento.com/checkout) en gegevensbanken voor het beheer van bestellingen
- Voer een reeks SQL-scripts uit die:

   - Externe toetsen
   - Back-ups maken van verkopen en databasetabellen citeren
   - De lijsten van de beweging van uw belangrijkste gegevensbestand aan verkoop en citeert gegevensbestanden

>[!WARNING]
>
>Als om het even welke douanecode JOINs met lijsten in de verkoop en citeert gegevensbestanden gebruikt, u _kan_ gebruik gesplitste databases. Neem bij twijfel contact op met de auteurs van aangepaste code of extensies om ervoor te zorgen dat hun code geen JOIN&#39;s gebruikt.

Dit onderwerp gebruikt de volgende noemende overeenkomsten:

- De hoofddatabasenaam is `magento` en de gebruikersnaam en het wachtwoord beide zijn `magento`
- De naam van de quotadatabase is `magento_quote` en de gebruikersnaam en het wachtwoord beide zijn `magento_quote`

   De citaatdatabase wordt ook wel de _uitchecken_ database.

- De naam van de verkoopdatabase is `magento_sales` en de gebruikersnaam en het wachtwoord beide zijn `magento_sales`

   Het verkoopgegevensbestand wordt ook bedoeld als OMS gegevensbestand.

>[!INFO]
>
>Deze gids veronderstelt dat alle drie gegevensbestanden op de zelfde gastheer zoals de toepassing van de Handel zijn. Nochtans, is de keus van waar te om van de gegevensbestanden de plaats te bepalen en wat zij worden genoemd aan u. We hopen dat onze voorbeelden de instructies makkelijker te volgen maken.

## Back-up maken van het systeem van de handel

Adobe raadt u ten zeerste aan een back-up te maken van uw huidige database en bestandssysteem, zodat u deze kunt herstellen als u tijdens het proces problemen ondervindt.

**Een back-up van uw systeem maken**:

1. Meld u aan bij de Commerce-server als of schakel over naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Voer de volgende opdrachten in:

   ```bash
   magento setup:backup --code --media --db
   ```

1. Ga verder met de volgende sectie.

## Aanvullende master databases instellen

In deze sectie wordt besproken hoe u databaseinstanties voor verkoop en [aanhalingsteken](https://glossary.magento.com/quote) tabellen.

**Om verkoop en OMS citaatgegevensbestanden te creëren**:

1. Meld u als elke gebruiker aan bij uw databaseserver.
1. Ga het volgende bevel in om aan een MySQL bevelherinnering te krijgen:

   ```bash
   mysql -u root -p
   ```

1. Ga MySQL in `root` wachtwoord van de gebruiker wanneer daarom wordt gevraagd.
1. Voer de volgende opdrachten in in de volgorde die wordt weergegeven om databaseinstanties met de naam `magento_quote` en `magento_sales` met dezelfde gebruikersnamen en wachtwoorden:

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Enter `exit` om de bevelherinnering te verlaten.

1. Controleer de databases één voor één:

   quotadatabase:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   ```bash
   mysql -u magento_quote -p
   ```

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Als de MySQL monitorvertoningen, u het gegevensbestand behoorlijk creeerde. Als er een fout wordt weergegeven, herhaalt u de voorgaande opdrachten.

1. Ga verder met de volgende sectie.

## De verkoopdatabase configureren

Deze sectie bespreekt hoe te om SQL manuscripten tot stand te brengen en in werking te stellen die citaat gegevensbestandlijsten en file gegevens van die lijsten veranderen.

Tabelnamen van verkoopdatabase beginnen met:

- `salesrule_`
- `sales_`
- `magento_sales_`
- De `magento_customercustomattributes_sales_flat_order` ook de tabel wordt beïnvloed

>[!INFO]
>
>Deze sectie bevat manuscripten met specifieke namen van gegevensbestandlijsten. Als u aanpassingen hebt uitgevoerd of als u een volledige lijst van lijsten wilt zien alvorens u acties op hen uitvoert, zie [Referentiescripts](#reference-scripts).

Zie voor meer informatie:

- [SQL-scripts maken voor de verkoopdatabase](#create-sales-database-sql-scripts)
- [Verkoopgegevens voor back-ups](#back-up-sales-data)

### SQL-scripts maken voor de verkoopdatabase

Creeer de volgende SQL manuscripten in een plaats die door de gebruiker toegankelijk is aangezien u login aan uw server van de Handel. Als u zich bijvoorbeeld aanmeldt of opdrachten uitvoert als `root`kunt u de scripts in het dialoogvenster `/root/sql-scripts` directory.

#### Externe toetsen verwijderen

Dit manuscript verwijdert buitenlandse sleutels die naar niet-verkooplijsten van het verkoopgegevensbestand verwijzen.

Het volgende script maken en een soortgelijke naam geven `1_foreign-sales.sql`. Vervangen `<your main DB name>` met de naam van uw database.

```sql
use <your main DB name>;
ALTER TABLE salesrule_coupon_aggregated_order DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_aggregated_updated DROP FOREIGN KEY SALESRULE_COUPON_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_coupon_usage DROP FOREIGN KEY SALESRULE_COUPON_USAGE_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_customer_group DROP FOREIGN KEY SALESRULE_CSTR_GROUP_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_customer DROP FOREIGN KEY SALESRULE_CUSTOMER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE salesrule_label DROP FOREIGN KEY SALESRULE_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_ATTR_ID_EAV_ATTR_ATTR_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRD_ATTR_CSTR_GROUP_ID_CSTR_GROUP_CSTR_GROUP_ID;
ALTER TABLE salesrule_product_attribute DROP FOREIGN KEY SALESRULE_PRODUCT_ATTRIBUTE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE salesrule_website DROP FOREIGN KEY SALESRULE_WEBSITE_WEBSITE_ID_STORE_WEBSITE_WEBSITE_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_DAILY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_MONTHLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGRED_YEARLY_PRD_ID_CAT_PRD_ENTT_ENTT_ID;
ALTER TABLE sales_bestsellers_aggregated_daily DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_DAILY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_monthly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_MONTHLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_bestsellers_aggregated_yearly DROP FOREIGN KEY SALES_BESTSELLERS_AGGREGATED_YEARLY_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo_grid DROP FOREIGN KEY SALES_CREDITMEMO_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_creditmemo DROP FOREIGN KEY SALES_CREDITMEMO_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated_order DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoiced_aggregated DROP FOREIGN KEY SALES_INVOICED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice_grid DROP FOREIGN KEY SALES_INVOICE_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_invoice DROP FOREIGN KEY SALES_INVOICE_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_created DROP FOREIGN KEY SALES_ORDER_AGGREGATED_CREATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_aggregated_updated DROP FOREIGN KEY SALES_ORDER_AGGREGATED_UPDATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_CUSTOMER_ID_CUSTOMER_ENTITY_ENTITY_ID;
ALTER TABLE sales_order_grid DROP FOREIGN KEY SALES_ORDER_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_item DROP FOREIGN KEY SALES_ORDER_ITEM_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order_status_label DROP FOREIGN KEY SALES_ORDER_STATUS_LABEL_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_order DROP FOREIGN KEY SALES_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated_order DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_refunded_aggregated DROP FOREIGN KEY SALES_REFUNDED_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment_grid DROP FOREIGN KEY SALES_SHIPMENT_GRID_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipment DROP FOREIGN KEY SALES_SHIPMENT_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated_order DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_ORDER_STORE_ID_STORE_STORE_ID;
ALTER TABLE sales_shipping_aggregated DROP FOREIGN KEY SALES_SHIPPING_AGGREGATED_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_creditmemo_grid_archive DROP FOREIGN KEY MAGENTO_SALES_CREDITMEMO_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_invoice_grid_archive DROP FOREIGN KEY MAGENTO_SALES_INVOICE_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_CSTR_ID_CSTR_ENTT_ENTT_ID;
ALTER TABLE magento_sales_order_grid_archive DROP FOREIGN KEY MAGENTO_SALES_ORDER_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE magento_sales_shipment_grid_archive DROP FOREIGN KEY MAGENTO_SALES_SHIPMENT_GRID_ARCHIVE_STORE_ID_STORE_STORE_ID;
ALTER TABLE downloadable_link_purchased_item DROP FOREIGN KEY DL_LNK_PURCHASED_ITEM_ORDER_ITEM_ID_SALES_ORDER_ITEM_ITEM_ID;
ALTER TABLE downloadable_link_purchased DROP FOREIGN KEY DOWNLOADABLE_LINK_PURCHASED_ORDER_ID_SALES_ORDER_ENTITY_ID;
ALTER TABLE paypal_billing_agreement_order DROP FOREIGN KEY PAYPAL_BILLING_AGREEMENT_ORDER_ORDER_ID_SALES_ORDER_ENTITY_ID;
```

### De verkoopdatabase configureren

Voer het voorgaande script uit:

1. Meld u aan bij uw MySQL-database als de `root` of gebruiker met administratieve bevoegdheden:

   ```bash
   mysql -u root -p
   ```

1. Bij de `mysql>` vraag, stel het manuscript als volgt in werking:

   ```shell
   source <path>/<script>.sql
   ```

   Bijvoorbeeld:

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. Nadat het script is uitgevoerd, voert u `exit`.

### Verkoopgegevens voor back-ups

Deze sectie bespreekt hoe te file verkooplijsten van het belangrijkste gegevensbestand van de Handel zodat kunt u hen in het afzonderlijke verkoopgegevensbestand herstellen.

Als u momenteel bij `mysql>` prompt, enter `exit` om naar bevelshell terug te keren.

Voer het volgende uit `mysqldump` opdrachten, één voor één, uit de opdrachtshell. Vervang in elke sectie het volgende:

- `<your database root username>` met de naam van de basisgebruiker van de database
- `<your database root user password>` met het wachtwoord van de gebruiker
- `<your main Commerce DB name>` met de naam van uw Commerce-database
- `<path>` met een schrijfbaar bestandssysteempad

#### Script 1

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sales_bestsellers_aggregated_daily sales_bestsellers_aggregated_monthly sales_bestsellers_aggregated_yearly sales_creditmemo sales_creditmemo_comment sales_creditmemo_grid sales_creditmemo_item sales_invoice sales_invoice_comment sales_invoice_grid sales_invoice_item sales_invoiced_aggregated sales_invoiced_aggregated_order sales_order sales_order_address sales_order_aggregated_created sales_order_aggregated_updated sales_order_grid sales_order_item sales_order_payment sales_order_status sales_order_status_history sales_order_status_label sales_order_status_state sales_order_tax sales_order_tax_item sales_payment_transaction sales_refunded_aggregated sales_refunded_aggregated_order sales_sequence_meta sales_sequence_profile sales_shipment sales_shipment_comment sales_shipment_grid sales_shipment_item sales_shipment_track sales_shipping_aggregated sales_shipping_aggregated_order > /<path>/sales.sql
```

#### Script 2

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_sales_creditmemo_grid_archive magento_sales_invoice_grid_archive magento_sales_order_grid_archive magento_sales_shipment_grid_archive > /<path>/salesarchive.sql
```

#### Script 3

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_order magento_customercustomattributes_sales_flat_order_address > /<path>/customercustomattributes.sql
```

#### Script 4

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> sequence_creditmemo_0 sequence_creditmemo_1 sequence_invoice_0 sequence_invoice_1 sequence_order_0 sequence_order_1 sequence_rma_item_0 sequence_rma_item_1 sequence_shipment_0 sequence_shipment_1 > /<path>/sequence.sql
```

### Verkoopgegevens herstellen

Met dit script worden de verkoopgegevens in de quotadatabase hersteld.

#### NDB-vereiste

Als u een [Netwerkdatabase (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) cluster:

1. Tabellen van InnoDb naar NDB-type converteren in dump-bestanden:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Rijen met een FULLTEXT-sleutel verwijderen uit dumps omdat NDB-tabellen geen FULLTEXT ondersteunen.

#### De gegevens herstellen

Voer de volgende opdrachten uit:

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sales.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/sequence.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/salesarchive.sql
```

```bash
mysql -u <root username> -p <your sales DB name> < /<path>/customercustomattributes.sql
```

Wanneer

- `<your sales DB name>` met de naam van uw verkoopdatabase.

   In dit onderwerp, is de naam van het steekproefgegevensbestand `magento_sales`.

- `<root username>` met uw MySQL hoofdgebruikersnaam
- `<root user password>` met het wachtwoord van de gebruiker
- Controleer de locatie van de back-upbestanden die u eerder hebt gemaakt (bijvoorbeeld `/var/sales.sql`)

## De quotedatabase configureren

Deze sectie bespreekt taken die worden vereist om buitenlandse sleutels van de lijsten van het verkoopgegevensbestand te laten vallen en lijsten naar het verkoopgegevensbestand te verplaatsen.

>[!INFO]
>
>Deze sectie bevat manuscripten met specifieke namen van gegevensbestandlijsten. Als u aanpassingen hebt uitgevoerd of als u een volledige lijst van lijsten wilt zien alvorens u acties op hen uitvoert, zie [Referentiescripts](#reference-scripts).

De namen van de de gegevensbestandlijsten van het citaat beginnen met `quote`. De `magento_customercustomattributes_sales_flat_quote` en `magento_customercustomattributes_sales_flat_quote_address` ook de tabellen worden beïnvloed

### Externe toetsen uit aanhalingsteksttabellen neerzetten

Met dit script worden externe sleutels die verwijzen naar tabellen die niet verwijzen naar aanhalingstekens, verwijderd uit concepttabellen. Vervangen `<your main Commerce DB name>` met de naam van uw Commerce-database.

Het volgende script maken en een soortgelijke naam geven `2_foreign-key-quote.sql`:

```sql
use <your main DB name>;
ALTER TABLE quote DROP FOREIGN KEY QUOTE_STORE_ID_STORE_STORE_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_PRODUCT_ID_CATALOG_PRODUCT_ENTITY_ENTITY_ID;
ALTER TABLE quote_item DROP FOREIGN KEY QUOTE_ITEM_STORE_ID_STORE_STORE_ID;
```

Voer het script als volgt uit:

1. Meld u aan bij uw MySQL-database als de basis- of beheergebruiker:

   ```bash
   mysql -u root -p
   ```

1. Bij de `mysql >` vraag, stel het manuscript als volgt in werking:
   `source <path>/<script>.sql`

   Bijvoorbeeld:

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. Nadat het script is uitgevoerd, voert u `exit`.

### Back-up maken van prijsopgaven

In deze sectie wordt beschreven hoe u een back-up kunt maken van aanhalingsteksttabellen uit de hoofddatabase en deze kunt terugzetten in de database met aanhalingstekens.

Voer het volgende bevel van een bevelherinnering in werking:

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB-vereiste

Als u een [Netwerkdatabase (NDB)](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) cluster:

1. Tabellen van InnoDb naar NDB-type converteren in dump-bestanden:

   ```bash
   sed -ei 's/InnoDb/NDB/' <file name>.sql
   ```

1. Rijen met een FULLTEXT-sleutel verwijderen uit dumps omdat NDB-tabellen geen FULLTEXT ondersteunen.

### Tabellen herstellen naar de quotadatabase

```bash
mysql -u root -p magento_quote < /<path>/quote.sql
```

## Verkoop en prijsopgave uit de database neerzetten

Dit manuscript verkoopt en citeert lijsten van het gegevensbestand van de Handel. Vervangen `<your main DB name>` met de naam van uw Commerce-database.

Het volgende script maken en een soortgelijke naam geven `3_drop-tables.sql`:

```sql
use <your main DB name>;
SET foreign_key_checks = 0;
DROP TABLE magento_customercustomattributes_sales_flat_quote;
DROP TABLE magento_customercustomattributes_sales_flat_quote_address;
DROP TABLE quote;
DROP TABLE quote_address;
DROP TABLE quote_address_item;
DROP TABLE quote_item;
DROP TABLE quote_item_option;
DROP TABLE quote_payment;
DROP TABLE quote_shipping_rate;
DROP TABLE quote_id_mask;
DROP TABLE sales_bestsellers_aggregated_daily;
DROP TABLE sales_bestsellers_aggregated_monthly;
DROP TABLE sales_bestsellers_aggregated_yearly;
DROP TABLE sales_creditmemo;
DROP TABLE sales_creditmemo_comment;
DROP TABLE sales_creditmemo_grid;
DROP TABLE sales_creditmemo_item;
DROP TABLE sales_invoice;
DROP TABLE sales_invoice_comment;
DROP TABLE sales_invoice_grid;
DROP TABLE sales_invoice_item;
DROP TABLE sales_invoiced_aggregated;
DROP TABLE sales_invoiced_aggregated_order;
DROP TABLE sales_order;
DROP TABLE sales_order_address;
DROP TABLE sales_order_aggregated_created;
DROP TABLE sales_order_aggregated_updated;
DROP TABLE sales_order_grid;
DROP TABLE sales_order_item;
DROP TABLE sales_order_payment;
DROP TABLE sales_order_status;
DROP TABLE sales_order_status_history;
DROP TABLE sales_order_status_label;
DROP TABLE sales_order_status_state;
DROP TABLE sales_order_tax;
DROP TABLE sales_order_tax_item;
DROP TABLE sales_payment_transaction;
DROP TABLE sales_refunded_aggregated;
DROP TABLE sales_refunded_aggregated_order;
DROP TABLE sales_sequence_meta;
DROP TABLE sales_sequence_profile;
DROP TABLE sales_shipment;
DROP TABLE sales_shipment_comment;
DROP TABLE sales_shipment_grid;
DROP TABLE sales_shipment_item;
DROP TABLE sales_shipment_track;
DROP TABLE sales_shipping_aggregated;
DROP TABLE sales_shipping_aggregated_order;
DROP TABLE magento_sales_creditmemo_grid_archive;
DROP TABLE magento_sales_invoice_grid_archive;
DROP TABLE magento_sales_order_grid_archive;
DROP TABLE magento_sales_shipment_grid_archive;
DROP TABLE magento_customercustomattributes_sales_flat_order;
DROP TABLE magento_customercustomattributes_sales_flat_order_address;
DROP TABLE sequence_creditmemo_0;
DROP TABLE sequence_creditmemo_1;
DROP TABLE sequence_invoice_0;
DROP TABLE sequence_invoice_1;
DROP TABLE sequence_order_0;
DROP TABLE sequence_order_1;
DROP TABLE sequence_rma_item_0;
DROP TABLE sequence_rma_item_1;
DROP TABLE sequence_shipment_0;
DROP TABLE sequence_shipment_1;
SET foreign_key_checks = 1;
```

Voer het script als volgt uit:

1. Meld u aan bij uw MySQL-database als de basis- of beheergebruiker:

   ```bash
   mysql -u root -p
   ```

1. Bij de `mysql>` vraag, stel het manuscript als volgt in werking:

   ```shell
   source <path>/<script>.sql
   ```

   Bijvoorbeeld:

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. Nadat het script is uitgevoerd, voert u `exit`.

## Implementatieconfiguratie bijwerken

De definitieve stap in manueel het splitsen van gegevensbestanden moet verbinding en middelinformatie aan de plaatsingsconfiguratie van de Handel toevoegen, `env.php`.

Om de plaatsingsconfiguratie bij te werken:

1. Meld u aan bij de Commerce-server als of schakel over naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Maak een back-up van uw implementatieconfiguratie:

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. Openen `<magento_root>/app/etc/env.php` in een teksteditor en deze bij te werken aan de hand van de richtlijnen die in de volgende secties worden besproken.

### Databaseverbindingen bijwerken

Zoek het blok dat begint met `'default'` (onder `'connection'`) en toevoegen `'checkout'` en `'sales'` secties. Vervang voorbeeldwaarden door waarden die geschikt zijn voor uw site.

```php
 'default' =>
      array (
'host' => 'localhost',
'dbname' => 'magento',
'username' => 'magento',
'password' => 'magento',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'checkout' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_quote',
'username' => 'magento_quote',
'password' => 'magento_quote',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
      'sales' =>
      array (
'host' => 'localhost',
'dbname' => 'magento_sales',
'username' => 'magento_sales',
'password' => 'magento_sales',
'model' => 'mysql4',
'engine' => 'innodb',
'initStatements' => 'SET NAMES utf8;',
'active' => '1',
      ),
    ),
```

### Bronnen bijwerken

Zoek het blok dat begint met `'resource'` en toevoegen `'checkout'` en `'sales'` de volgende secties:

```php
'resource' =>
  array (
    'default_setup' =>
    array (
      'connection' => 'default',
    ),
    'checkout' =>
    array (
      'connection' => 'checkout',
    ),
    'sales' =>
    array (
      'connection' => 'sales',
    ),
```

## Referentiescripts

Deze sectie bevat scripts die u kunt uitvoeren en waarmee een volledige lijst met desbetreffende tabellen wordt afgedrukt zonder dat er handelingen op worden uitgevoerd. U kunt ze gebruiken om te zien welke tabellen worden beïnvloed voordat u handmatig databases splitst. Dit kan handig zijn als u extensies gebruikt die de [databaseschema](https://glossary.magento.com/database-schema).

Deze scripts gebruiken:

1. Maak een SQL-script met de inhoud van elk script in deze sectie.
1. In elk script vervangt u `<your main DB name>` met de naam van uw Commerce-database.

   In dit onderwerp, is de naam van het steekproefgegevensbestand `magento`.

1. Elk script uitvoeren vanaf het `mysql>` vragen als `source <script name>`
1. Onderzoek de uitvoer.
1. Kopieer het resultaat van elk script naar een ander SQL-script, waarbij de verticale streep (`|`).
1. Elk script uitvoeren vanaf het `mysql>` vragen als `source <script name>`.

   Wanneer u dit tweede script uitvoert, worden de handelingen in uw hoofddatabase van Commerce uitgevoerd.

### Externe sleutels verwijderen (verkooptabellen)

Dit manuscript verwijdert buitenlandse sleutels die naar niet-verkooplijsten van het verkoopgegevensbestand verwijzen.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|sales_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales_%' escape '|'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like  '<your main DB name>/|magento_sales|_%' escape '|'
    and ref_name not like  '<your main DB name>/|sales|_%' escape '|'
;
```

### Externe sleutels verwijderen (concepttabellen)

Met dit script worden externe sleutels die verwijzen naar tabellen die niet verwijzen naar aanhalingstekens, verwijderd uit concepttabellen.

```sql
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_sales\_%'
union all
select concat(
    'ALTER TABLE ',
    replace(for_name, '<your main DB name>/', ''),
    ' DROP FOREIGN KEY ',
    replace(id, '<your main DB name>/', ''),
    ';'
    )
from information_schema.INNODB_SYS_FOREIGN
where for_name like '<your main DB name>/%'
    and ref_name like '<your main DB name>/magento_customercustomattributes\_%'
;
```

### Verkooptabellen neerzetten

Dit manuscript laat verkooplijsten van het gegevensbestand van de Handel vallen.

```sql
use <your main DB name>;
select ' SET foreign_key_checks = 0;' as querytext
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_sales/_%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'magento_customercustomattributes_sales_flat_order%' escape '/'
union all
select
    concat('DROP TABLE IF EXISTS ' , table_name, ';')
from information_schema.tables
where table_schema = '<your main DB name>'
and table_name like 'sequence/_%' escape '/'
union all
select 'SET foreign_key_checks = 1;';
```

### Aanhalingstekens neerzetten

Alle tabellen neerzetten die beginnen met `quote_`.
