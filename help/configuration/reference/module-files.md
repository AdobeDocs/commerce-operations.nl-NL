---
title: Moduleconfiguratiebestanden
description: Leer hoe u modules kunt aanpassen met configuratietypen in Adobe Commerce. Ontdek best practices voor het beheer van configuratiebestanden en het aanpassen van modules.
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1263'
ht-degree: 0%

---

# Overzicht van moduleconfiguratiebestanden

De verantwoordelijkheden van het `config.xml` -configuratiebestand dat in eerdere versies van Commerce wordt gebruikt, zijn nu verdeeld over verschillende bestanden in verschillende moduledirectory&#39;s. De veelvoudige configuratiedossiers van Commerce laden op bestelling slechts wanneer een module om een specifiek configuratietype verzoekt.

U kunt deze dossiers-ook gebruiken die als _worden bedoeld configuratietypen_ - om specifieke aspecten van het gedrag van uw module aan te passen.

De veelvoudige modules kunnen configuratiedossiers verklaren die het zelfde configuratietype (bijvoorbeeld, gebeurtenissen) beïnvloeden, en deze veelvoudige configuratiedossiers worden samengevoegd.

Hieronder vindt u algemene termen die in dit onderwerp worden gebruikt:

- **voorwerp van de Configuratie** - de bibliotheek of de klasse van Commerce die voor het bepalen van en het bevestigen van het configuratietype verantwoordelijk is. Bijvoorbeeld, is het configuratievoorwerp voor `config.xml` [ Magento\Framework\App\Config ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- {het stadium van de Configuratie 1} - de Staven van de 1} Configuratie worden bepaald als **primaire**, _globaal_, en _gebied_. __ Elk stadium bepaalt wanneer het configuratietype wordt geladen en met zelfde-genoemde configuratietypen samengevoegd. `module.xml` -bestanden worden bijvoorbeeld samengevoegd met andere `module.xml` -bestanden.

- **werkingsgebied van de Configuratie** - Complementair aan configuratiestadia, bepaalt een werkingsgebied het model van het configuratietype. `adminhtml` is bijvoorbeeld een gebiedsbereik dat in het werkgebied wordt geladen met de `adminhtml` -configuraties van andere modules. Voor meer informatie, zie [ Modules en gebieden ](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## Configuratie laden en samenvoegen

In deze sectie wordt beschreven hoe configuratiebestanden worden geladen en samengevoegd.

### Hoe Commerce configuratiebestanden laadt

Commerce laadt configuratiebestanden in de volgende volgorde (alle paden zijn relatief ten opzichte van de installatiemap van Commerce):

- Primaire configuratie ([ app/etc/di.xml ](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Dit bestand wordt gebruikt om Commerce op te starten.
- Algemene configuraties van modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Verzamelt bepaalde configuratiedossiers van alle modules en voegt hen samen samen.
- Vlakspecifieke configuratie van modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Verzamelt configuratiedossiers van alle modules en voegt hen in de globale configuratie samen. Sommige gebiedsspecifieke configuraties kunnen de globale configuratie met voeten treden of uitbreiden.

waar

- `<your component base dir>` is de basismap waarin de component zich bevindt. De meeste waarden zijn `app/code` of `vendor` ten opzichte van de installatiemap van Commerce.
- `<vendorname>` is de leveranciersnaam van de component. De naam van de Commerce-leverancier is bijvoorbeeld `magento` .
- `<component-type>` is een van de volgende:

   - `module-`: Een extensie of module.
   - `theme-`: Thema.
   - `language-` : Taalpakket.

>[!INFO]
>
>Thema&#39;s bevinden zich momenteel onder `<magento_root>/app/design/frontend` of `<magento_root>/app/design/adminhtml` .

- `<component-name>`: Naam van uw component zoals die in [ wordt bepaald composer.json ](https://github.com/magento/magento2/blob/2.4/composer.json).

### Samenvoegen van configuratiebestand

Knooppunten in configuratiebestanden worden samengevoegd op basis van hun volledig gekwalificeerde XPails, waarvoor een speciaal kenmerk is gedefinieerd in de array `$idAttributes` die als id is gedeclareerd. Deze id moet uniek zijn voor alle geneste knooppunten onder hetzelfde bovenliggende knooppunt.

Samenvoegalgoritme Commerce-toepassing:

- Als knoopherkenningstekens gelijk zijn (of als er geen herkenningsteken wordt bepaald), wordt al onderliggende inhoud in de knoop (attributen, kindknopen, en scalaire inhoud) met voeten getreden.
- Als knoopherkenningstekens niet gelijk zijn, is de knoop een nieuw kind van de ouderknoop.
- Als het oorspronkelijke document meerdere knooppunten met dezelfde id heeft, wordt een fout geactiveerd omdat de id&#39;s niet kunnen worden onderscheiden.

Nadat de configuratiedossiers worden samengevoegd, bevat het resulterende document alle knopen van de originele dossiers.

>[!INFO]
>
>U kunt [ \Magento\Framework\Config\Reader\Filesystem ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) klasse gebruiken voor het zuiveren en het begrip van de logica achter [ configuratiedossiers loader ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) en [ samenvoegen vormt ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) proces.

## Configuratietypen, objecten en interfaces

De volgende secties verstrekken informatie over configuratietypen, hun overeenkomstige configuratievoorwerpen, en interfaces die u kunt gebruiken om met de voorwerpen te werken:

### Configuratietypen en -objecten

De volgende lijst toont elk configuratietype en het de configuratievoorwerp van Commerce waarop het betrekking heeft.

| Configuratiebestand | Beschrijving | Werkgebied | Configuration-object |
| --- | --- | --- | --- |
| `address_formats.xml` | Declaratie van adresformaat | primair, wereldwijd | [ \Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [ Lijst van het Toegangsbeheer ](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | globaal | [ \Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [ Geavanceerde rapportering ](https://developer.adobe.com/commerce/php/development/advanced-reporting/data-collection/) | primair, wereldwijd | [ \Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Cachetype-declaratie | primair, wereldwijd | [ \Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Configuratie van cataloguskenmerken | globaal | [ \Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` en `env.php` | [ configuratie van de Plaatsing ](../reference/deployment-files.md) | Deze bestanden zijn leesbaar/schrijfbaar door de interne configuratieprocessor. | Heeft geen object, kan niet worden aangepast |
| `config.xml` | Systeemconfiguratie | primair, wereldwijd | [ \Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [ bepaalt aspecten van het systeem van de berichtrij ](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | globaal | [ \Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [ Vormt cron groepen ](../cron/custom-cron-reference.md#configure-cron-groups) | globaal | [ \Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [ specificeert de opties van de cron groep ](../cron/custom-cron-reference.md) | globaal | [ \Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [ Verklarend schema ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | globaal | [ Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [ configuratie van de injectie van 0} Afhankelijkheid](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) | primair, wereldwijd, gebied | [ \Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Biedt configuratie van EAV-kenmerken | globaal | [ \Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Configuratie van e-mailsjablonen | globaal | [ \Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [ de motor van het Onderzoek locale stopwords config ](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | globaal | [ \Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Configuratie van gebeurtenis/waarnemer | globaal, gebied | [ \Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Entiteitsconfiguratie exporteren | globaal | [ \Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [ de attributen van de Uitbreiding ](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | globaal | [ \Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Veldsets definiëren | globaal | [ \Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [ verklaart indexeerders ](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | globaal | [ \Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Hiermee worden importentiteiten gedeclareerd | globaal | [ \Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Hiermee worden menu-items voor de beheerder gedefinieerd | adminhtml | [ \Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Bepaalt module configuratiegegevens en zachte gebiedsafhankelijkheid | primair, wereldwijd | [ \Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [ configuratie MView ](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | primair, wereldwijd | [ \Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Configuratie van de betalingsmodule | primair, wereldwijd | [ \Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [ Magento_Persistent ](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) configuratiedossier | globaal | [ \Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF-instellingen | globaal | [ \Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Biedt productconfiguratie | globaal | [ \Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Hiermee wordt het producttype gedefinieerd | globaal | [ \Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [ bepaalt het verband tussen een bestaande rij en zijn consument ](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | globaal | [ \Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [ bepaalt de uitwisseling waar een onderwerp wordt gepubliceerd.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | globaal | [ \Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [ bepaalt het bericht dat regels verplettert, verklaart rijen en uitwisselingen ](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | globaal | [ \Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [ Geavanceerde rapporten ](https://developer.adobe.com/commerce/php/development/advanced-reporting/report-xml/) | globaal | [ \Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Definieert module resource | globaal | [ \Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [ configuratie 0} van de Route {](https://developer.adobe.com/commerce/php/development/components/routing/) | gebied | [ Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Definieert totale configuratie verkoop | globaal | [ \Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Biedt configuratie van zoekprogramma&#39;s | globaal | [ Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Definieert de zoekconfiguratie voor de catalogus | globaal | [ \Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Definieert handelingen die cachevalidatie voor blokken met persoonlijke inhoud activeren | voorzijde | [ SectionInvalidationConfigReader ](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Definieert opties voor de systeemconfiguratiepagina | adminhtml | [ \Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Configuratiebestand voor modulevalidatie | globaal | [ \Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Bepaalt de de meningsconfiguratiewaarden van Vendor_Module | globaal | [ \Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [ vormt een Web API ](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | globaal | [ \Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [ bepaalt REST douaneroutes ](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | globaal | [ \Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Widgets definiëren | globaal | [ \Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Hiermee definieert u de zip-codeopmaak voor elk land | globaal | [ \Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Configuratieinterfaces

U kunt met configuratiedossiers in wisselwerking staan gebruikend interfaces onder [ Magento \ Kader \ Config ](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

U kunt deze interfaces gebruiken als u [ een configuratietype ](../reference/config-create-types.md#create-configuration-types) creeert.

`Magento\Framework\Config` biedt de volgende interfaces:

- [ Kader \ Config \ ConverterInterface ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), die XML in een in-geheugenserievertegenwoordiging van de configuraties omzet.
- [ Kader \ Config \ DataInterface ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), die de configuratiegegevens in een gespecificeerd werkingsgebied terugwint.
- [ Kader \ Config \ FileResolverInterface ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), die de plaats van dossiers identificeert die door [ Magento\Framework\Config\ReaderInterface ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php) moeten worden gelezen.
- [ Kader \ Config \ ReaderInterface ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), dat de configuratiegegevens van opslag leest en de opslag selecteert waarvan het leest.

Met andere woorden, het bestandssysteem, de database en andere opslagsystemen voegen de configuratiebestanden samen volgens de samenvoegingsregels en valideren de configuratiebestanden met de validatieschema&#39;s.

- [ Kader \ Config \ SchemaLocatorInterface ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), die van het XSD schema de plaats bepaalt.
- [ Kader \ Config \ ScopeListInterface ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), die een lijst van werkingsgebied terugkeert.
- [ Kader \ Config \ ValidationStateInterface ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), die de bevestigingsstaat terugwint.
