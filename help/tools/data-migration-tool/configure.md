---
title: Vorm  [!DNL Data Migration Tool]
description: Leer over de twee methodes om  [!DNL Data Migration Tool]  te vormen om gegevens tussen Magento 1 en Magento 2 over te brengen.
exl-id: 273be997-8085-4488-a455-f6005a85b406
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# De [!DNL Data Migration Tool] configureren

Nadat u [!DNL Data Migration Tool] hebt geïnstalleerd, bevat de volgende map toewijzings- en configuratiebestanden:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Configuratie en scripts voor migratie van Magento Open Source 1 naar Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: Configuratie en scripts voor migratie van Magento Open Source 1 naar Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: Configuratie en scripts voor migratie van Adobe Commerce 1 naar Adobe Commerce 2

De voorgaande mappen bevatten submappen voor elke ondersteunde versie.

## De migratie configureren

Er zijn twee manieren om [!DNL Data Migration Tool] te configureren:

* Configureer de [!DNL Data Migration Tool] in een aparte module (aanbevolen)
* Wijzig de [!DNL Data Migration Tool] -configuratie in de `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` -map.

Om broncontrole te gebruiken om uw migratieconfiguratie te beheren en het voor plaatsing te gebruiken, moet u een afzonderlijke module tot stand brengen.
Als u [!DNL Data Migration Tool] alleen lokaal wilt uitvoeren, kunt u bestanden in de map `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` rechtstreeks bewerken.

### Migratie configureren in een aparte module

Voordat u gegevens kunt migreren, moet u een Magento 2-module maken.

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

1. Kopieer het `config.xml.dist` configuratiebestand uit de juiste map van [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>` ) naar het `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` -bestand.

   Als u bijvoorbeeld `Magento 1.9.3.6 Community Edition` naar `Magento 2 Open Source` migreert:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. In het `config.xml` -bestand moet u toegangsgegevens instellen voor de M1- en M2-databases en de coderingssleutel.

1. Als uw M1-winkel aangepaste wijzigingen heeft, moet u de rest van uw configuratiebestanden toewijzen aan uw Magento 1-winkel-aanpassingen. Zie [&#x200B; Werk met configuratie en kaartdossiers &#x200B;](#migration-config).

### Migratie configureren in map `vendor`

Voordat u gegevens migreert, moet u een `config.xml` -configuratiebestand maken op basis van het opgegeven voorbeeld.

U kunt als volgt de [!DNL Data Migration Tool] for migration configureren:

1. Login aan uw toepassingsserver als, of schakelaar aan, de [&#x200B; eigenaar van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md).

1. Ga naar de volgende map:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Voer de volgende opdracht in om een `config.xml` van het opgegeven voorbeeld te maken:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Open `config.xml` in een teksteditor.

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

   De tag &lt;crypt_key> moet een waarde bevatten. U vindt deze in de tag `<key>` , die zich bevindt in het bestand app/etc/local.xml op uw Magento 1-exemplaar.

   Optionele parameters:

   * Wachtwoord databasegebruiker: `password=<password>`
   * Aangepaste poort database: `port=<port>`
   * Tabelvoorvoegsel: `<source_prefix>`, `<dest_prefix>`

   Als de gebruikersnaam van de eigenaar van de database bijvoorbeeld `root` met wachtwoord `pass` is en u het voorvoegsel `magento1` gebruikt in de Magento 1-database, gebruikt u het volgende in `config.xml` :

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

Als u klaar bent, slaat u de wijzigingen op in `config.xml` en sluit u de teksteditor.

### Verbinding maken via het TLS-protocol

U kunt ook verbinding maken met een database met behulp van het TLS-protocol (dat wil zeggen met cryptografische openbare/persoonlijke sleutels). Voeg de volgende optionele kenmerken toe aan het element `database` :

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

[!DNL Data Migration Tool] gebruikt *kaartdossiers* om u toe te laten om douanedatabatstoewijzing tussen uw Magento 1 en Magento 2 gegevensbestanden uit te voeren, die omvatten:

* Tabelnamen wijzigen

* Veldnamen wijzigen

* Tabellen of velden negeren

* Gegevens van een veld naar Magento 2-indeling overdragen

Toewijzingsbestanden voor ondersteunde Magento-versies bevinden zich in submappen van `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

De toewijzingsbestanden gebruiken:

1. Kopieer deze uit `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` naar `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` en verwijder de extensie `.dist` .

1. Werk het pad naar het zojuist gekopieerde bestand bij in het knooppunt `<options>` van `config.xml` . Het bijgewerkte pad moet een van de volgende zijn:

   1. Absoluut bestandspad, bijvoorbeeld `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. magento/data-migration-tool module relatief bestandspad: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Magento-pad naar hoofdmapafhankelijk bestand: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

De mappen `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` en `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` bevatten de volgende configuratiebestanden:

Hoewel u het grootste deel van de tijd met het `map.xml.dist` dossier werkt, bespreekt de volgende lijst elke afbeelding en andere dossiers.

| Bestandsnaam toewijzen | Beschrijving |
| --- | --- |
| `class-map.xml.dist` | Woordenboek van klassentoewijzingen tussen Magento 1 en Magento 2 |
| `config.xml.dist` | Hoofdconfiguratiebestand dat de configuraties van de Magento 1- en Magento 2-database, de stapconfiguratie en koppelingen naar toewijzingsbestanden opgeeft |
| *slechts Adobe Commerce*. `customer-attr-document-groups.xml.dist` | Lijst van lijsten die in de stap van de attributen van de douaneklanten worden gebruikt. |
| *slechts Adobe Commerce*. `customer-attr-map.xml.dist` | Het dossier van de kaart dat in de Stap van de Attributen van de Klant van de Douane wordt gebruikt. |
| `deltalog.xml.dist` | Bevat de lijst van lijsten die voor de opstelling van gegevensbestandroutines worden vereist. |
| `eav-attribute-groups.xml.dist` | Bevat een lijst met kenmerken die worden gebruikt in Eav-stap. |
| `eav-document-groups.xml.dist` | Bevat een lijst van lijsten die in Stap Eav worden gebruikt. |
| `log-document-groups.xml.dist` | Bevat een lijst van lijsten die in de Stap van het Logboek worden gebruikt. |
| `map-eav.xml.dist` | Het dossier van de kaart dat in Stap EAV wordt gebruikt. |
| `map-log.xml.dist` | Logboektoewijzingsbestand. |
| *slechts Adobe Commerce*. `map-sales.xml.dist` | Het dossier van de kaart dat in Stap SalesOrder wordt gebruikt. |
| `map.xml.dist` | Toewijzingsbestand vereist voor de kaartstap. |
| `settings.xml.dist` | Setting migration configuration file that specifies rules required for migrating the `core_config_data` table. |
| `customer-attribute-groups.xml.dist` | Bevat een lijst van attributen die in de Stap van Attributen van de Klant worden gebruikt. |
| `customer-document-groups.xml.dist` | Bevat lijst van lijsten die in de Stap van Attributen van de Klant worden gebruikt. |
| `map-customer.xml.dist` | Het dossier van de kaart dat in de Stap van Attributen van de Klant wordt gebruikt. |
| `order-grids-document-groups.xml.dist` | Bevat een lijst van lijsten die in de Stap OrderGrids worden gebruikt. |
| `map-document-groups.xml.dist` | Hiermee wordt gedefinieerd welke velden worden bijgewerkt wanneer er duplicaten optreden bij het invoegen van gegevens |
| `map-stores.xml.dist` | Kaartbestand dat wordt gebruikt in Opslagstap. |
| `map-tier-price.xml.dist` | Het dossier van de kaart dat in de Stap van de Prijs van de Rij wordt gebruikt. |
| *slechts Adobe Commerce*. `visual_merchandiser_map.xml.dist` | Het dossier van de kaart dat in Stap VisualMerchandiser wordt gebruikt. |
| *slechts Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | Bevat lijst van attributen die in Stap VisualMerchandiser worden gebruikt. |
| *slechts Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | Bevat lijst van lijsten die in Stap VisualMerchandiser worden gebruikt. |

U kunt naar [[!DNL Data Migration Tool]  Technische Specificatie &#x200B;](technical-specification.md) voor meer details verwijzen.
