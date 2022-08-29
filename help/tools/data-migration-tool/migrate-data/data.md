---
title: Gegevens migreren
description: Leer hoe u begint met het migreren van gegevens van Magento 1 naar Magento 2 met de [!DNL Data Migration Tool].
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# Gegevens migreren

Voer de volgende stappen uit om voor te bereiden voordat u begint:

1. Meld u aan bij uw toepassingsserver als [de eigenaar van het bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Wijzigen in de installatiemap van de toepassing of controleren of deze aan uw systeem is toegevoegd `PATH`.

Zie de [eerste stappen](overview.md#first-steps) voor meer informatie.

## De opdracht voor gegevensmigratie uitvoeren

Voer de volgende handelingen uit om het migreren van gegevens te starten:

```bash
bin/magento migrate:data [-r|--reset] [-a|--auto] {<path to config.xml>}
```

Waar:

* `[-a|--auto]` is een optioneel argument dat voorkomt dat de migratie stopt wanneer integriteitscontroles worden uitgevoerd.

* `[-r|--reset]` is een optioneel argument dat de migratie vanaf het begin start. U kunt dit argument gebruiken voor het testen van migratie.

* `{<path to config.xml>}` is het absolute pad van het bestandssysteem naar `config.xml`; dit argument is vereist

In deze stap worden de [!DNL Data Migration Tool] leidt tot extra lijsten en trekkers voor de migratietabellen in het gegevensbestand van Magento 1. Zij worden gebruikt in [incrementele/delta](delta.md) migratie. Aanvullende tabellen bevatten informatie over gewijzigde records na de laatste migratieuitvoering. De trekkers van het gegevensbestand worden gebruikt om deze extra lijsten te bevolken, zodat als een nieuwe verrichting op de bepaalde lijst (een verslag wordt toegevoegd/gewijzigd/verwijderd) wordt uitgevoerd, deze gegevensbestandtrekker sparen informatie over deze verrichting aan de extra lijst. Als we een delta-migratieproces uitvoeren, [!DNL Data Migration Tool] controleert deze lijsten voor de onverwerkte verslagen en migreert de noodzakelijke inhoud in het gegevensbestand van Magento 2.

Elke nieuwe tabel bevat:

* `m2_cl` prefix
* `INSERT`, `UPDATE`, `DELETE` gebeurtenistriggers.

Bijvoorbeeld voor `sales_flat_order` de [!DNL Data Migration Tool] maakt:

* `m2_cl_sales_flat_order` tabel:

   ```sql
   CREATE TABLE `m2_cl_sales_flat_order` (
     `entity_id` int(11) NOT NULL COMMENT 'Entity_id',
     `operation` text COMMENT 'Operation',
     `processed` tinyint(1) NOT NULL DEFAULT '0' COMMENT 'Processed',
     PRIMARY KEY (`entity_id`)
   ) COMMENT='m2_cl_sales_flat_order';
   ```

* `trg_sales_flat_order_after_insert`, `trg_sales_flat_order_after_update`, `trg_sales_flat_order_after_delete` triggers:

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
>De [!DNL Data Migration Tool] bespaart zijn huidige vooruitgang aangezien het loopt. Als de fouten of een gebruikersinterventie het van het lopen tegenhouden, hervat het Hulpmiddel vooruitgang bij het laatst bekende goede staat. Om de [!DNL Data Migration Tool] als u vanaf het begin wilt starten, gebruikt u de `--reset` argument. In dat geval, adviseren wij u uw Magento 2 gegevensbestandstortplaats herstellen om het dupliceren van eerder gemigreerde gegevens te verhinderen.


## Mogelijke consistentiefouten

Tijdens het uitvoeren [!DNL Data Migration Tool] kan inconsistenties tussen Magento 1 en Magento 2 gegevensbestanden, en vertoningsberichten als het volgende melden:

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

Zie de [Problemen oplossen](https://support.magento.com/hc/en-us/articles/360033020451) voor meer informatie en aanbevelingen.

## Volgende migratie

[Wijzigingen migreren](delta.md)
