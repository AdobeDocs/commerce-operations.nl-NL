---
title: Hoofddatabases handmatig configureren
description: Zie begeleiding bij het manueel vormen van de gespleten gegevensbestandoplossing.
recommendations: noCatalog
exl-id: 2c357486-4a8a-4a36-9e13-b53c83f69456
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '1373'
ht-degree: 0%

---

# Hoofddatabases handmatig configureren

{{ee-only}}

{{deprecate-split-db}}

Als de Commerce-toepassing al in productie is of als u al aangepaste code of componenten hebt geïnstalleerd, moet u mogelijk splitsingsdatabases handmatig configureren. Neem voordat u doorgaat contact op met Adobe Commerce Support om te controleren of dit in uw geval noodzakelijk is.

Het handmatig splitsen van databases omvat:

- De OMS-databases (Checkout and Order Management System) maken
- Voer een reeks SQL-scripts uit die:

   - Externe toetsen
   - Back-ups maken van verkopen en databasetabellen citeren
   - De lijsten van de beweging van uw belangrijkste gegevensbestand aan verkoop en citeert gegevensbestanden

>[!WARNING]
>
>Als om het even welke douanecode JOINs met lijsten in de verkoop en citeert gegevensbestanden gebruikt, kunt u _niet_ gespleten gegevensbestanden gebruiken. Neem bij twijfel contact op met de auteurs van aangepaste code of extensies om ervoor te zorgen dat hun code geen JOIN&#39;s gebruikt.

Dit onderwerp gebruikt de volgende noemende overeenkomsten:

- De hoofddatabasenaam is `magento` en de gebruikersnaam en het wachtwoord zijn beide `magento`
- De databasenaam van het aanhalingsteken is `magento_quote` en de gebruikersnaam en het wachtwoord zijn beide `magento_quote`

  Het citaatgegevensbestand wordt ook bedoeld als _checkout_ gegevensbestand.

- De naam van de verkoopdatabase is `magento_sales` en de gebruikersnaam en het wachtwoord zijn beide `magento_sales`

  Het verkoopgegevensbestand wordt ook bedoeld als OMS gegevensbestand.

>[!INFO]
>
>In deze handleiding wordt ervan uitgegaan dat alle drie de databases zich op dezelfde host bevinden als de Commerce-toepassing. Nochtans, is de keus van waar te om van de gegevensbestanden de plaats te bepalen en wat zij worden genoemd aan u. We hopen dat onze voorbeelden de instructies makkelijker te volgen maken.

## Back-up maken van het Commerce-systeem

Adobe raadt u ten zeerste aan een back-up te maken van uw huidige database en bestandssysteem, zodat u deze kunt herstellen als u tijdens het proces problemen ondervindt.

**aan file uw systeem**:

1. Login aan uw server van Commerce als, of schakelaar aan, de [&#x200B; eigenaar van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md).
1. Voer de volgende opdrachten in:

   ```bash
   magento setup:backup --code --media --db
   ```

1. Ga verder met de volgende sectie.

## Extra hoofddatabases instellen

Deze sectie bespreekt hoe te om gegevensbestandinstanties voor verkoop en citaatlijsten tot stand te brengen.

**om verkoop en OMS citaatgegevensbestanden** tot stand te brengen:

1. Meld u als elke gebruiker aan bij uw databaseserver.
1. Ga het volgende bevel in om aan een MySQL bevelherinnering te krijgen:

   ```bash
   mysql -u root -p
   ```

1. Voer het gebruikerswachtwoord van MySQL `root` in wanneer hierom wordt gevraagd.
1. Voer de volgende opdrachten in de volgorde in die wordt weergegeven om databaseinstanties met de naam `magento_quote` en `magento_sales` te maken met dezelfde gebruikersnamen en wachtwoorden:

   ```shell
   create database magento_quote;
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Ga `exit` in om de bevelherinnering weg te gaan.

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
- De tabel `magento_customercustomattributes_sales_flat_order` heeft ook invloed op

>[!INFO]
>
>Deze sectie bevat manuscripten met specifieke namen van gegevensbestandlijsten. Als u aanpassingen hebt uitgevoerd of als u een volledige lijst van lijsten wilt zien alvorens u acties op hen uitvoert, zie [&#x200B; manuscripten van de Verwijzing &#x200B;](#reference-scripts).

Zie voor meer informatie:

- [SQL-scripts maken voor de verkoopdatabase](#create-sales-database-sql-scripts)
- [Verkoopgegevens voor back-ups](#back-up-sales-data)

### SQL-scripts maken voor de verkoopdatabase

Maak de volgende SQL-scripts op een locatie die toegankelijk is voor de gebruiker als deze zich aanmeldt bij de Commerce-server. Als u zich bijvoorbeeld aanmeldt of opdrachten uitvoert als `root` , kunt u de scripts in de map `/root/sql-scripts` maken.

#### Externe toetsen verwijderen

Dit manuscript verwijdert buitenlandse sleutels die naar niet-verkooplijsten van het verkoopgegevensbestand verwijzen.

Maak het volgende script en geef het een naam zoals `1_foreign-sales.sql` . Vervang `<your main DB name>` door de naam van de database.

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

1. Meld u aan bij uw MySQL-database als de `root` - of beheergebruiker:

   ```bash
   mysql -u root -p
   ```

1. Voer het script bij de aanwijzing `mysql>` als volgt uit:

   ```shell
   source <path>/<script>.sql
   ```

   Bijvoorbeeld:

   ```shell
   source /root/sql-scripts/1_foreign-sales.sql
   ```

1. Voer `exit` in nadat het script is uitgevoerd.

### Verkoopgegevens voor back-ups

Deze sectie bespreekt hoe te file verkooplijsten van het belangrijkste gegevensbestand van Commerce zodat kunt u hen in het afzonderlijke verkoopgegevensbestand herstellen.

Als u momenteel bij de `mysql>` vraag bent, ga `exit` in om aan bevelshell terug te keren.

Voer de volgende `mysqldump` opdrachten één voor één uit vanuit de opdrachtshell. Vervang in elke sectie het volgende:

- `<your database root username>` met de naam van de basisgebruiker van de database
- `<your database root user password>` met het gebruikerswachtwoord
- `<your main Commerce DB name>` met de naam van uw Commerce-database
- `<path>` met een schrijfbaar systeempad

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

Als u de cluster van het a [&#x200B; Gegevensbestand van het Netwerk (NDB) &#x200B;](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) gebruikt:

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

  In dit onderwerp is de naam van de voorbeelddatabase `magento_sales` .

- `<root username>` met uw MySQL-hoofdgebruikersnaam
- `<root user password>` met het gebruikerswachtwoord
- Controleer de locatie van de back-upbestanden die u eerder hebt gemaakt (bijvoorbeeld `/var/sales.sql`)

## De quotedatabase configureren

Deze sectie bespreekt taken die worden vereist om buitenlandse sleutels van de lijsten van het verkoopgegevensbestand te laten vallen en lijsten naar het verkoopgegevensbestand te verplaatsen.

>[!INFO]
>
>Deze sectie bevat manuscripten met specifieke namen van gegevensbestandlijsten. Als u aanpassingen hebt uitgevoerd of als u een volledige lijst van lijsten wilt zien alvorens u acties op hen uitvoert, zie [&#x200B; manuscripten van de Verwijzing &#x200B;](#reference-scripts).

De namen van de de gegevensbestandlijsten van de citaat beginnen met `quote`. De tabellen `magento_customercustomattributes_sales_flat_quote` en `magento_customercustomattributes_sales_flat_quote_address` worden ook beïnvloed

### Externe toetsen uit aanhalingsteksttabellen neerzetten

Met dit script worden externe sleutels die verwijzen naar tabellen die niet verwijzen naar aanhalingstekens, verwijderd uit concepttabellen. Vervang `<your main Commerce DB name>` door de naam van uw Commerce-database.

Maak het volgende script en geef het een naam zoals `2_foreign-key-quote.sql` :

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

1. Voer het script bij de aanwijzing `mysql >` als volgt uit:
   `source <path>/<script>.sql`

   Bijvoorbeeld:

   ```shell
   source /root/sql-scripts/2_foreign-key-quote.sql
   ```

1. Voer `exit` in nadat het script is uitgevoerd.

### Back-up maken van prijsopgaven

In deze sectie wordt beschreven hoe u een back-up kunt maken van aanhalingsteksttabellen uit de hoofddatabase en deze kunt terugzetten in de database met aanhalingstekens.

Voer het volgende bevel van een bevelherinnering in werking:

```bash
mysqldump -u <your database root username> -p <your main Commerce DB name> magento_customercustomattributes_sales_flat_quote magento_customercustomattributes_sales_flat_quote_address quote quote_address quote_address_item quote_item quote_item_option quote_payment quote_shipping_rate quote_id_mask > /<path>/quote.sql;
```

### NDB-vereiste

Als u de cluster van het a [&#x200B; Gegevensbestand van het Netwerk (NDB) &#x200B;](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html) gebruikt:

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

Dit script verkoopt tabellen en citeert deze uit de Commerce-database. Vervang `<your main DB name>` door de naam van uw Commerce-database.

Maak het volgende script en geef het een naam zoals `3_drop-tables.sql` :

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

1. Voer het script bij de aanwijzing `mysql>` als volgt uit:

   ```shell
   source <path>/<script>.sql
   ```

   Bijvoorbeeld:

   ```shell
   source /root/sql-scripts/3_drop-tables.sql
   ```

1. Voer `exit` in nadat het script is uitgevoerd.

## Implementatieconfiguratie bijwerken

De laatste stap bij het handmatig splitsen van databases is het toevoegen van verbinding- en broninformatie aan de Commerce-implementatieconfiguratie, `env.php` .

Om de plaatsingsconfiguratie bij te werken:

1. Login aan uw server van Commerce als, of schakelaar aan, de [&#x200B; eigenaar van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md).
1. Maak een back-up van uw implementatieconfiguratie:

   ```bash
   cp <magento_root>/app/etc/env.php <magento_root>/app/etc/env.php.orig
   ```

1. Open `<magento_root>/app/etc/env.php` in een teksteditor en werk deze bij aan de hand van de richtlijnen die in de volgende secties worden besproken.

### Databaseverbindingen bijwerken

Zoek het blok met `'default'` (onder `'connection'` ) en voeg `'checkout'` - en `'sales'` -secties toe. Vervang voorbeeldwaarden door waarden die geschikt zijn voor uw site.

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

Zoek het blok met `'resource'` en voeg er als volgt secties `'checkout'` en `'sales'` aan toe:

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

Deze sectie bevat scripts die u kunt uitvoeren en waarmee een volledige lijst met desbetreffende tabellen wordt afgedrukt zonder dat er handelingen op worden uitgevoerd. U kunt ze gebruiken om te zien welke tabellen worden beïnvloed voordat u handmatig databases splitst. Dit kan handig zijn als u extensies gebruikt die het databaseschema aanpassen.

Deze scripts gebruiken:

1. Maak een SQL-script met de inhoud van elk script in deze sectie.
1. Vervang `<your main DB name>` in elk script door de naam van uw Commerce-database.

   In dit onderwerp is de naam van de voorbeelddatabase `magento` .

1. Elk script uitvoeren vanaf de aanwijzing `mysql>` als `source <script name>`
1. Onderzoek de uitvoer.
1. Kopieer het resultaat van elk manuscript aan een ander SQL manuscript, verwijderend de pijpkarakters (`|`).
1. Voer elk script uit vanaf de aanwijzing `mysql>` als `source <script name>` .

   Wanneer u dit tweede script uitvoert, worden de handelingen in uw Commerce-hoofddatabase uitgevoerd.

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

Met dit script worden verkooptabellen uit de Commerce-database verwijderd.

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

Zet alle tabellen neer die beginnen met `quote_` .
