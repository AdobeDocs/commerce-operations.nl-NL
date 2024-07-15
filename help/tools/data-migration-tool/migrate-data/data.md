---
title: Gegevens migreren
description: Leer hoe te beginnen migrerend gegevens van Magento 1 aan Magento 2 met  [!DNL Data Migration Tool].
exl-id: f4ea8f6a-21f8-4db6-b598-c5efecec254f
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Gegevens migreren

Voer de volgende stappen uit om voor te bereiden voordat u begint:

1. Login aan uw toepassingsserver als [ de eigenaar van het dossiersysteem ](../../../installation/prerequisites/file-system/overview.md).
1. Wijzig de installatiemap van de toepassing of zorg ervoor dat deze aan uw systeem wordt toegevoegd `PATH` .

Zie de [ eerste stappen ](overview.md#first-steps) sectie voor meer details.

## De opdracht voor gegevensmigratie uitvoeren

Voer de volgende handelingen uit om het migreren van gegevens te starten:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Waarbij:

* `[-a|--auto]` is een optioneel argument dat voorkomt dat de migratie stopt wanneer integriteitscontroles worden uitgevoerd.

* `[-r|--reset]` is een optioneel argument dat de migratie vanaf het begin start. U kunt dit argument gebruiken voor het testen van migratie.

* `{<path to config.xml>}` is het absolute bestandsysteempad naar `config.xml` ; dit argument is vereist

Binnen deze stap maakt [!DNL Data Migration Tool] aanvullende tabellen en triggers voor de migratietabellen in de database Magento 1. Zij worden gebruikt in de [ stijgende/delta ](delta.md) migratiestap. Aanvullende tabellen bevatten informatie over gewijzigde records na de laatste migratieuitvoering. De trekkers van het gegevensbestand worden gebruikt om deze extra lijsten te bevolken, zodat als een nieuwe verrichting op de bepaalde lijst (een verslag wordt toegevoegd/gewijzigd/verwijderd) wordt uitgevoerd, deze gegevensbestandtrekker sparen informatie over deze verrichting aan de extra lijst. Wanneer we een deltamigratieproces uitvoeren, controleert [!DNL Data Migration Tool] deze tabellen op de niet-verwerkte records en wordt de benodigde inhoud gemigreerd naar de Magento 2-database.

Elke nieuwe tabel bevat:

* `m2_cl` prefix
* `INSERT`, `UPDATE`, `DELETE` gebeurtenistriggers.

Voor de lus `sales_flat_order` [!DNL Data Migration Tool] maakt u bijvoorbeeld:

* `m2_cl_sales_flat_order` tabel:

  ```sql
  CREATE TABLE `m2_cl_sales_flat_order` (
    `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
    `operation` text COMMENT 'Operation',
    `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
    PRIMARY KEY (`entity_id`)
  ) COMMENT='m2_cl_sales_flat_order';
  ```

* `trg_sales_flat_order_after_insert` , `trg_sales_flat_order_after_update` , `trg_sales_flat_order_after_delete` triggers:

  ```sql
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_insert` AFTER INSERT ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'INSERT')ON DUPLICATE KEY UPDATE operation = 'INSERT';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_update` AFTER UPDATE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (NEW.entity_id, 'UPDATE') ON DUPLICATE KEY UPDATE operation = 'UPDATE';
    END
  ;;
  
  DELIMITER ;;
  CREATE TRIGGER `trg_sales_flat_order_after_delete` AFTER DELETE ON `sales_flat_order`
    FOR EACH ROW
    BEGIN
     INSERT INTO m2_cl_sales_flat_order (`entity_id`, `operation`) VALUES (OLD.entity_id, 'DELETE')ON DUPLICATE KEY UPDATE operation = 'DELETE';
    END
  ;;
  ```

>[!NOTE]
>
>De [!DNL Data Migration Tool] slaat de huidige voortgang op terwijl deze wordt uitgevoerd. Als de fouten of een gebruikersinterventie het van het lopen tegenhouden, hervat het Hulpmiddel vooruitgang bij het laatst bekende goede staat. Gebruik het argument `--reset` om te zorgen dat [!DNL Data Migration Tool] vanaf het begin wordt uitgevoerd. In dat geval, adviseren wij u uw Magento 2 gegevensbestandstortplaats herstellen om het dupliceren van eerder gemigreerde gegevens te verhinderen.


## Mogelijke consistentiefouten

Tijdens het uitvoeren kan [!DNL Data Migration Tool] inconsistenties tussen Magento 1 en Magento 2 gegevensbestanden rapporteren, en berichten zoals het volgende tonen:

* `Source documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are missing: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Destination documents are not mapped: <EXTENSION_TABLE_1>,<EXTENSION_TABLE_2>,...<EXTENSION_TABLE_N>`
* `Source fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are missing. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Source fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Destination fields are not mapped. Document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Source document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Mismatch of data types. Destination document: <EXTENSION_TABLE>. Fields: <FIELD_1>,<FIELD_2>...<FIELD_N>`
* `Incompatibility in data. Source document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`
* `Incompatibility in data. Destination document: <EXTENSION_TABLE>. Field: <FIELD>. Error: <ERROR_MESSAGE>`

Zie de [ sectie van het Oplossen van problemen ](https://support.magento.com/hc/en-us/articles/360033020451) van deze gids voor meer informatie en aanbevelingen.

## Volgende migratie

[Wijzigingen migreren](delta.md)
