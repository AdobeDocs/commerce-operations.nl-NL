---
title: Moduleconfiguratiebestanden
description: Leer hoe te om een module aan te passen gebruikend configuratietypen.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '2019'
ht-degree: 0%

---


# Overzicht van moduleconfiguratiebestanden

De verantwoordelijkheden van de `config.xml` Het configuratiedossier dat in vroegere versies van de Handel wordt gebruikt wordt nu verdeeld over verscheidene dossiers, die in diverse modulefolders worden gevestigd. De veelvoudige configuratiedossiers van de handel laden op bestelling slechts wanneer een module om een specifiek configuratietype verzoekt.

U kunt deze bestanden gebruiken, ook wel _configuratietypen_—om specifieke aspecten van het gedrag van uw module aan te passen.

De veelvoudige modules kunnen configuratiedossiers verklaren die het zelfde configuratietype (bijvoorbeeld, gebeurtenissen) beïnvloeden, en deze veelvoudige configuratiedossiers worden samengevoegd.

Hieronder volgen algemene termen die in dit onderwerp worden gebruikt:

- **Configuration-object**—De bibliotheek of klasse van de Handel die voor het bepalen van en het bevestigen van het configuratietype verantwoordelijk is. Het configuratieobject voor `config.xml` is [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Configuratiefase**—Fases worden gedefinieerd als _primair_, _globaal_, en _gebied_. Elk stadium bepaalt wanneer het configuratietype wordt geladen en met zelfde-genoemde configuratietypen samengevoegd. Bijvoorbeeld: `module.xml` bestanden worden samengevoegd met andere `module.xml` bestanden.

- **Configuratiebereik**—Naast configuratiestadia, bepaalt een werkingsgebied het model van configuratietype. Bijvoorbeeld: `adminhtml` is een gebiedswerkingsgebied dat met in het stadium met andere modules wordt geladen &quot; `adminhtml` configuraties. Zie voor meer informatie [Modules en gebieden](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/components/modules/mod_and_areas.html).

## Configuratie laden en samenvoegen

In deze sectie wordt beschreven hoe configuratiebestanden worden geladen en samengevoegd.

### Hoe de Handel configuratiedossiers laadt

De handel laadt configuratiedossiers in de volgende orde (alle wegen zijn met betrekking tot uw de installatiemap van de Handel):

- Primaire configuratie ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Dit bestand wordt gebruikt om de handel op te starten.
- Algemene configuraties van modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Verzamelt bepaalde configuratiedossiers van alle modules en voegt hen samen samen.
- Vlakspecifieke configuratie uit modules (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Verzamelt configuratiedossiers van alle modules en voegt hen in de globale configuratie samen. Sommige gebiedsspecifieke configuraties kunnen de globale configuratie met voeten treden of uitbreiden.

waar

- `<your component base dir>` is de basismap waarin de component zich bevindt. Typische waarden zijn `app/code` of `vendor` ten opzichte van de installatiemap Handel.
- `<vendorname>` de leveranciersnaam van de component is; zo is de naam van de leverancier van Commerce `magento`.
- `<component-type>` is een van de volgende:

   - `module-`: Een extensie of module.
   - `theme-`: Thema.
   - `language-`: Taalpakket.

>[!INFO]
>
>Thema&#39;s bevinden zich momenteel onder `<magento_root>/app/design/frontend` of `<magento_root>/app/design/adminhtml`.

- `<component-name>`: Naam van de component zoals gedefinieerd in [composer.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Samenvoegen van configuratiebestand

Knooppunten in configuratiebestanden worden samengevoegd op basis van hun volledig gekwalificeerde XPath, waarvoor een speciaal kenmerk is gedefinieerd in `$idAttributes` array gedeclareerd als id. Deze id moet uniek zijn voor alle knooppunten die onder hetzelfde bovenliggende knooppunt zijn genest.

Samenvoegalgoritme voor handelingstoepassing:

- Als knoopherkenningstekens gelijk zijn (of als er geen herkenningsteken wordt bepaald), wordt al onderliggende inhoud in de knoop (attributen, kindknopen, en scalaire inhoud) met voeten getreden.
- Als knoopherkenningstekens niet gelijk zijn, is de knoop een nieuw kind van de ouderknoop.
- Als het oorspronkelijke document meerdere knooppunten met dezelfde id heeft, wordt een fout geactiveerd omdat de id&#39;s niet kunnen worden onderscheiden.

Nadat de configuratiedossiers worden samengevoegd, bevat het resulterende document alle knopen van de originele dossiers.

>[!INFO]
>
>U kunt [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) klasse voor het zuiveren en het begrijpen van de logica achter [loader configuratiebestanden](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) en [samenvoegen, configuraties](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) proces.

## Configuratietypen, objecten en interfaces

De volgende secties verstrekken informatie over configuratietypen, hun overeenkomstige configuratievoorwerpen, en interfaces die u kunt gebruiken om met de voorwerpen te werken:

- [Configuratietypen en -objecten](#config-files-classes-objects)
- [Configuratieinterfaces](#config-files-classes-int)

### Configuratietypen en -objecten

De volgende lijst toont elk configuratietype en het de configuratievoorwerp van de Handel waarop het betrekking heeft.

| Configuratiebestand | Beschrijving | Werkgebied | Configuration-object |
| --- | --- | --- | --- |
| `address_formats.xml` | Declaratie van adresformaat | primair, wereldwijd | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Toegangsbeheerlijst](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication.html#relationship-between-aclxml-and-webapixml) | globaal | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Geavanceerde rapportage](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | primair, wereldwijd | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Cachetype-declaratie | primair, wereldwijd | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Configuratie van cataloguskenmerken | globaal | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` en `env.php` | [Implementatieconfiguratie](../reference/deployment-files.md) | Deze bestanden zijn leesbaar/schrijfbaar door de interne configuratieprocessor. | Heeft geen object, kan niet worden aangepast |
| `config.xml` | Systeemconfiguratie | primair, wereldwijd | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Bepaalt aspecten van het systeem van de berichtrij](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#communicationxml) | globaal | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Hiermee configureert u afdekgroepen](../cron/custom-cron-reference.md#configure-cron-groups) | globaal | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Hiermee geeft u opties voor de uitsnijdgroep op](../cron/custom-cron-reference.md) | globaal | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Declaratief schema](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/declarative-schema/db-schema.html) | globaal | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [Injectie van afhankelijkheid](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/depend-inj.html) configuratie | primair, wereldwijd, gebied | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Biedt configuratie van EAV-kenmerken | globaal | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Configuratie van e-mailsjablonen | globaal | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Configuratie van stopwoorden voor zoekprogramma](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | globaal | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Configuratie van gebeurtenis/waarnemer | globaal, gebied | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Entiteitsconfiguratie exporteren | globaal | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Extensiekenmerken](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/attributes.html#extension) | globaal | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Veldsets definiëren | globaal | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Hiermee worden indexeerders gedeclareerd](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html) | globaal | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Hiermee worden importentiteiten gedeclareerd | globaal | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Hiermee worden menu-items voor de beheerder gedefinieerd | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Bepaalt module configuratiegegevens en zachte gebiedsafhankelijkheid | primair, wereldwijd | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [MView-configuratie](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/indexing-custom.html#mview-configuration) | primair, wereldwijd | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Configuratie van betalingsmodule | primair, wereldwijd | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_Blijvend](https://devdocs.magento.com/guides/v2.4/mrg/module-persistent.html) configuratiebestand | globaal | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | PDF-instellingen | globaal | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Biedt productoptieconfiguratie | globaal | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Hiermee wordt het producttype gedefinieerd | globaal | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Bepaalt de verhouding tussen een bestaande rij en zijn consument](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queueconsumerxml) | globaal | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Bepaalt de uitwisseling waar een onderwerp wordt gepubliceerd.](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuepublisherxml) | globaal | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Bepaalt het bericht dat regels verplettert, verklaart rijen en uitwisselingen](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/message-queues/config-mq.html#queuetopologyxml) | globaal | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Geavanceerde rapporten](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | globaal | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Definieert module resource | globaal | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [Route](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/routing.html) configuratie | gebied | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Definieert totale configuratie van verkoop | globaal | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Biedt configuratie van zoekprogramma&#39;s | globaal | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Definieert de zoekconfiguratie voor de catalogus | globaal | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Definieert handelingen die cachevalidatie voor blokken met persoonlijke inhoud activeren | voorzijde | [SectionInvalidationConfigReader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Definieert opties voor de systeemconfiguratiepagina | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | Configuratiebestand voor modulevalidatie | globaal | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Bepaalt de de meningsconfiguratiewaarden van Vendor_Module | globaal | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Een web-API configureren](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/service-contracts/service-to-web-service.html) | globaal | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Bepaalt REST douaneroutes](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/webapi/custom-routes.html) | globaal | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Widgets definiëren | globaal | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Hiermee definieert u de zip-codeopmaak voor elk land | globaal | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Configuratieinterfaces

U kunt met configuratiedossiers in wisselwerking staan gebruikend interfaces onder [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

U kunt deze interfaces gebruiken als u [een configuratietype maken](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` biedt de volgende interfaces:

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), die de XML in een in-geheugenarray representatie van de configuraties omzet.
- [Framework\Config\DataInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), die de configuratiegegevens in een gespecificeerd werkingsgebied terugwint.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), die de locatie aangeeft van bestanden die moeten worden gelezen [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), die de configuratiegegevens leest uit opslag en de opslag selecteert waarvan het leest.

Met andere woorden, het bestandssysteem, de database en andere opslagsystemen voegen de configuratiebestanden samen volgens de samenvoegingsregels en valideren de configuratiebestanden met de validatieschema&#39;s.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), die het XSD-schema zoekt.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), die een lijst met het bereik retourneert.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), die de validatiestatus ophaalt.
