---
title: Configureer de [!DNL Data Migration Tool]
description: Meer informatie over de twee methoden voor het configureren van de [!DNL Data Migration Tool] gegevens tussen Magento 1 en Magento 2 over te dragen.
exl-id: 273be997-8085-4488-a455-f6005a85b406
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# Configureer de [!DNL Data Migration Tool]

Nadat u de [!DNL Data Migration Tool], bevat de volgende map toewijzingsbestanden en configuratiebestanden:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Configuratie en scripts voor migreren van Magento Open Source 1 naar Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: Configuratie en scripts voor migratie van Magento Open Source 1 naar Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: Configuratie en scripts voor migratie van Adobe Commerce 1 naar Adobe Commerce 2

De voorgaande mappen bevatten submappen voor elke ondersteunde versie.

## De migratie configureren

Er zijn twee manieren om te vormen [!DNL Data Migration Tool]:

* Configureer de [!DNL Data Migration Tool] in een aparte module (aanbevolen)
* Wijzig de [!DNL Data Migration Tool] in de `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` directory.

Om broncontrole te gebruiken om uw migratieconfiguratie te beheren en het voor plaatsing te gebruiken, moet u een afzonderlijke module tot stand brengen.
Als u van plan bent de [!DNL Data Migration Tool] alleen lokaal kunt u bestanden bewerken in het dialoogvenster `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` rechtstreeks.

### Migratie configureren in een aparte module

Voordat u gegevens migreert, moet u een module Magento 2 maken.

1. Maak een Magento 2-module.

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. Kopieer de `config.xml.dist` configuratiebestand uit de desbetreffende map van het [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) in de `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` bestand.

   Als u bijvoorbeeld migreert `Magento 1.9.3.6 Community Edition` tot `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. In de `config.xml` bestand, moet u toegangsgegevens instellen voor M1- en M2-databases en coderingssleutel.

1. Als uw opslag M1 douaneveranderingen heeft, zou u de rest configuratiedossiers aan uw Magento 1 opslagaanpassingen moeten in kaart brengen. Zie [Werken met configuratie- en toewijzingsbestanden](#migration-config).

### Migratie configureren in `vendor` map

Voordat u gegevens kunt migreren, moet u een `config.xml` configuratiebestand uit het opgegeven voorbeeld.

Om het [!DNL Data Migration Tool] voor migratie:

1. Meld u aan bij de toepassingsserver als of schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).

1. Ga naar de volgende map:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Voer de volgende opdracht in om een `config.xml` uit het monster:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Openen `config.xml` in een teksteditor.

1. Het bestand config.xml moet ten minste toegangsgegevens bevatten voor de databases M1 en M2 en de coderingssleutels.

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   De &lt;crypt_key> -tag moet een waarde bevatten. U vindt het in de `<key>` -tag, die zich bevindt in het bestand app/etc/local.xml op uw Magento 1-exemplaar.

   Optionele parameters:

   * Wachtwoord databasegebruiker: `password=<password>`
   * Aangepaste poort database: `port=<port>`
   * Tabelvoorvoegsel: `<source_prefix>`, `<dest_prefix>`

   Als de gebruikersnaam van de eigenaar van de database bijvoorbeeld `root` met wachtwoord `pass` en u gebruikt het voorvoegsel `magento1` in uw Magento 1-database gebruikt u het volgende in `config.xml`:

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

Als u klaar bent, slaat u uw wijzigingen op in `config.xml` en sluit de teksteditor af.

### Verbinding maken via het TLS-protocol

U kunt ook verbinding maken met een database met behulp van het TLS-protocol (dat wil zeggen met cryptografische openbare/persoonlijke sleutels). Voeg de volgende optionele kenmerken toe aan de `database` element:

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

Bijvoorbeeld:

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## Werken met configuratie- en toewijzingsbestanden

De [!DNL Data Migration Tool] gebruik *toewijzingsbestanden* om u toe te laten om de afbeelding van het douanegegevensbestand tussen uw Magento 1 en Magento 2 gegevensbestanden uit te voeren, die omvatten:

* Tabelnamen wijzigen

* Veldnamen wijzigen

* Tabellen of velden negeren

* Gegevens van een veld aanpassen aan de indeling Magento 2

Toewijzingsbestanden voor ondersteunde Magento-versies bevinden zich in submappen van `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

De toewijzingsbestanden gebruiken:

1. Kopiëren van `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` tot `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` en verwijder de `.dist` extensie.

1. Het pad naar het zojuist gekopieerde bestand in het dialoogvenster `<options>` knooppunt van `config.xml`. Het bijgewerkte pad moet een van de volgende zijn:

   1. Absoluut bestandspad, bijv. g. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. relatief bestandspad magento/data-migration-tool module: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Hoofdmapafhankelijk relatief bestandspad Magento: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

De `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` en `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` mappen bevatten de volgende configuratiebestanden:

Hoewel u met de `map.xml.dist` in de volgende tabel wordt meestal elke toewijzing en andere bestanden besproken.

| Bestandsnaam toewijzen | Beschrijving |
| --- | --- |
| `class-map.xml.dist` | Woordenboek van klassentoewijzingen tussen Magento 1 en Magento 2 |
| `config.xml.dist` | Hoofdconfiguratiedossier dat Magento 1 en Magento 2 gegevensbestandconfiguraties, step configuratie, en verbindingen aan toewijzingsdossiers specificeert |
| *Alleen Adobe Commerce*. `customer-attr-document-groups.xml.dist` | Lijst van lijsten die in de stap van de attributen van de douaneklanten worden gebruikt. |
| *Alleen Adobe Commerce*. `customer-attr-map.xml.dist` | Het dossier van de kaart dat in de Stap van de Attributen van de Klant van de Douane wordt gebruikt. |
| `deltalog.xml.dist` | Bevat de lijst van lijsten die voor de opstelling van gegevensbestandroutines worden vereist. |
| `eav-attribute-groups.xml.dist` | Bevat een lijst met kenmerken die in Eav Step worden gebruikt. |
| `eav-document-groups.xml.dist` | Bevat een lijst van lijsten die in Stap Eav worden gebruikt. |
| `log-document-groups.xml.dist` | Bevat een lijst van lijsten die in de Stap van het Logboek worden gebruikt. |
| `map-eav.xml.dist` | Het dossier van de kaart dat in Stap EAV wordt gebruikt. |
| `map-log.xml.dist` | Logboektoewijzingsbestand. |
| *Alleen Adobe Commerce*. `map-sales.xml.dist` | Het dossier van de kaart dat in Stap SalesOrder wordt gebruikt. |
| `map.xml.dist` | Toewijzingsbestand vereist voor de kaartstap. |
| `settings.xml.dist` | Het migratieconfiguratiedossier plaatsen dat regels vereist voor migratie specificeert `core_config_data` tabel. |
| `customer-attribute-groups.xml.dist` | Bevat een lijst van attributen die in de Stap van Attributen van de Klant worden gebruikt. |
| `customer-document-groups.xml.dist` | Bevat lijst van lijsten die in de Stap van Attributen van de Klant worden gebruikt. |
| `map-customer.xml.dist` | Het dossier van de kaart dat in de Stap van Attributen van de Klant wordt gebruikt. |
| `order-grids-document-groups.xml.dist` | Bevat een lijst van lijsten die in de Stap OrderGrids worden gebruikt. |
| `map-document-groups.xml.dist` | Hiermee wordt gedefinieerd welke velden worden bijgewerkt wanneer er duplicaten optreden bij het invoegen van gegevens |
| `map-stores.xml.dist` | Kaartbestand dat wordt gebruikt in Opslagstap. |
| `map-tier-price.xml.dist` | Het dossier van de kaart dat in de Stap van de Prijs van de Rij wordt gebruikt. |
| *Alleen Adobe Commerce*. `visual_merchandiser_map.xml.dist` | Het dossier van de kaart dat in Stap VisualMerchandiser wordt gebruikt. |
| *Alleen Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | Bevat lijst van attributen die in Stap VisualMerchandiser worden gebruikt. |
| *Alleen Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | Bevat lijst van lijsten die in Stap VisualMerchandiser worden gebruikt. |

U kunt verwijzen naar [[!DNL Data Migration Tool] Technische specificaties](technical-specification.md) voor meer informatie .
