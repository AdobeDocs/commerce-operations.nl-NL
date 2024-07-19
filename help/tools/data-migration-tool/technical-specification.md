---
title: '[!DNL Data Migration Tool] technische specificatie'
description: Leer over de implementatiedetails van  [!DNL Data Migration Tool]  en hoe te om uit te breiden wanneer het overbrengen van gegevens tussen Magento 1 en Magento 2.
exl-id: fec3ac3a-dd67-4533-a29f-db917f54d606
topic: Commerce, Migration
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '2098'
ht-degree: 0%

---

# [!DNL Data Migration Tool] technische specificatie

In deze sectie worden de implementatiedetails van [!DNL Data Migration Tool] beschreven en wordt beschreven hoe u de functionaliteit ervan kunt uitbreiden.

## Opslagplaatsen

Om tot de [!DNL Data Migration Tool] broncode toegang te hebben, zie de [ bewaarplaats GitHub ](https://github.com/magento/data-migration-tool).

## Systeemvereisten

De [ systeemvereisten ](../../installation/system-requirements.md) voor [!DNL Data Migration Tool] zijn het zelfde als voor Magento 2.

## Interne structuur

### Directorystructuur

In het volgende diagram wordt de mapstructuur van [!DNL Data Migration Tool] weergegeven:

```
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains adapter for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── Exception.php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## Invoerpunt

Het script waarmee het migratieproces wordt uitgevoerd, bevindt zich in: `magento-root/bin/magento` .

## Configuratie

Het schema voor het configuratiebestand `config.xsd` bevindt zich in de map `etc/` . Het standaardconfiguratiedossier (`config.xml.dist`) wordt gecreeerd voor elke versie van Magento 1.x. Deze bevindt zich in een aparte map onder `etc/` .

Het standaardconfiguratiedossier kan door douane worden vervangen één (zie [ bevelsyntaxis ](migrate-data/overview.md#command-syntax)).

Het configuratiebestand heeft de volgende structuur:

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* stappen - beschrijft alle stappen die tijdens migratie worden verwerkt

* bron - configuratie voor gegevensbron. Beschikbare brontypen: database

* doel - configuratie voor gegevensbestemming. Beschikbare doeltypen: database

* opties - lijst met parameters. Bevat zowel verplichte (map_file, settings_map_file, bulk_size) als optionele (custom_option, resource_adapter_class_name, prefix_source, prefix_dest, log_file) parameters

Voorvoegseloptie wijzigen voor het geval dat Magento met voorvoegsel in databasetabellen is geïnstalleerd. Dit kan worden ingesteld voor databases van Magento 1 en Magento 2. Gebruik de configuratieopties &quot;source_prefix&quot; en &quot;dest_prefix&quot; dienovereenkomstig.

Configuratiegegevens zijn toegankelijk met de klasse `\Migration\Config` .

## Stappen van beschikbare bewerkingen

| Document | Veld |
|---|---|
| `step` | Knooppunt op het tweede niveau binnen het knooppunt Stappen. Beschrijving van de desbetreffende stap moet worden opgegeven in het kenmerk `title` . |
| `integrity` | Geeft de PHP-klasse op die verantwoordelijk is voor de integriteitscontrole. Vergelijkt de namen, de types, en andere info van de lijstgebieden om verenigbaarheid tussen Magento 1 en 2 gegevensstructuren te verifiëren. |
| `data` | Geeft de PHP-klasse op die verantwoordelijk is voor de gegevenscontrole. Brengt de gegevens, lijst door lijst van Magento 1 aan Magento 2 over. |
| `volume` | Geeft de PHP-klasse op die verantwoordelijk is voor de volumecontrole. Vergelijkt het aantal verslagen tussen lijsten om te verifiëren dat de overdracht succesvol was. |
| `delta` | Geeft de PHP-klasse op die verantwoordelijk is voor de deltacontrole. Brengt de delta van Magento 1 naar Magento 2 over na de volledige gegevensmigratie. |

## Kenmerken Source-databasegegevens

| Document | Veld | Vereist? |
|---|---|---|
| `name` | Databasenaam van de Magento 1-server. | ja |
| `host` | IP van de gastheer adres van Magento 1 server. | ja |
| `port` | Poortnummer van de Magento 1-server. | nee |
| `user` | Gebruikersnaam van Magento 1 gegevensbestandserver. | ja |
| `password` | Wachtwoord van Magento 1 gegevensbestandserver. | ja |
| `ssl_ca` | Pad naar SSL Certificate Authority-bestand. | nee |
| `ssl_cert` | Pad naar SSL-certificaatbestand. | nee |
| `ssl_key` | Pad naar SSL-sleutelbestand. | nee |

## Kenmerken van de gegevensbank van de bestemming

| Document | Veld | Vereist? |
|---|---|---|
| `name` | Databasenaam van de Magento 2-server. | ja |
| `host` | IP van de gastheer adres van Magento 2 server. | ja |
| `port` | Poortnummer van de Magento 2-server. | nee |
| `user` | Gebruikersnaam van Magento 2 gegevensbestandserver. | ja |
| `password` | Wachtwoord van Magento 2 gegevensbestandserver. | ja |
| `ssl_ca` | Pad naar SSL Certificate Authority-bestand. | nee |
| `ssl_cert` | Pad naar SSL-certificaatbestand. | nee |
| `ssl_key` | Pad naar SSL-sleutelbestand. | nee |

## Verbinding maken via het TLS-protocol

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

## Interne stappen

Het migratieproces bestaat uit stappen.

Stap is een eenheid die functionaliteit verstrekt die voor migratie sommige gescheiden gegevens wordt vereist. De stap kan uit één of meerdere stadia (integriteitscontrole, gegevens, volumecontrole, en delta) bestaan.

Door gebrek, zijn er verscheidene stappen ([ Kaart ](#map-step), [ EAV ](#eav), [ URL herschrijft ](#url-rewrite-step), etc.). U kunt desgewenst ook uw eigen stappen toevoegen.

De stappen verwante klassen worden gevestigd in de src/Migration/Step folder.

Om een klasse van de Stap uit te voeren, moet de klasse in config.xml- dossier worden bepaald.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

Elke werkgebiedklasse moet StageInterface implementeren.

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

Als het gegevenswerkgebied terugdraaiacties ondersteunt, moet de interface `RollbackInterface` worden geïmplementeerd.

Visualisatie van de lopende stap wordt verstrekt door de component ProgressBar van Symfony (zie [ bar van de Voortgang ](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Open deze component in een stap als LogLevelProcessor.

De belangrijkste gebruiksmethoden zijn:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Stappen

### Integriteitscontrole

Elke stap moet controleren dat de structuur van gegevensbron (Magento 1 door gebrek) en de structuur van gegevensbestemming (Magento 2) compatibel zijn. Als dat niet het geval is, wordt een fout weergegeven met entiteiten die niet compatibel zijn. Als velden verschillende datatypen hebben (hetzelfde veld heeft een decimaal gegevenstype in Magento 1 en een geheel getal in Magento 2), wordt een waarschuwingsbericht weergegeven (behalve wanneer het veld is opgenomen in het Kaartenbestand).

### Gegevensoverdracht

Als de integriteitscontrole wordt doorgegeven, worden de gegevens overgedragen. Als er fouten optreden, wordt het terugdraaien uitgevoerd om terug te keren naar de vorige status van Magento 2. Als een step-klasse de `RollbackInterface` -interface implementeert, wordt de terugdraaimethode uitgevoerd wanneer er een fout optreedt.

### Volume controleren

Nadat de gegevens zijn gemigreerd, biedt de Controle van het Volume extra controle dat alle gegevens correct werden overgebracht.

### Levering van delta

De deltefunctionaliteit is verantwoordelijk voor het leveren van de rest van gegevens die na de hoofdmigratie zijn toegevoegd.

## Runmodi

Het gereedschap moet in drie verschillende modi worden uitgevoerd, met name:

1. instellingen - migratie van systeeminstellingen
1. gegevens - belangrijkste migratie van gegevens
1. delta - migratie van de rest van gegevens die na hoofdmigratie zijn toegevoegd

Elke modus heeft een eigen lijst met stappen die moeten worden uitgevoerd. Zie config.xml

### Modus voor migratie van instellingen

De migratie-modus voor instellingen van dit gereedschap wordt gebruikt om de volgende entiteiten over te brengen:

1. Websites, winkels en winkelweergaven.
1. Winkelconfiguratie (voornamelijk opslag->Configuratie in M2 of System->Configuratie in M1)

Al opslagconfiguratie houdt zijn gegevens in core_config_data lijst in gegevensbestand. settings.xml file bevat regels voor deze lijst die tijdens migratieproces worden toegepast. In dit bestand worden instellingen beschreven die moeten worden genegeerd, hernoemd of waarvan de waarden moeten worden gewijzigd. settings.xml file heeft de volgende structuur:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

Onder het knooppunt `<key>` staan regels die werken met de kolom &#39;path&#39; in de tabel `core_config_data` . `<ignore>` voorkomt dat het gereedschap bepaalde instellingen overbrengt. Jokertekens kunnen in dit knooppunt worden gebruikt. Alle andere instellingen die niet in het knooppunt `<ignore>` worden vermeld, worden gemigreerd. Als het pad naar een instelling is gewijzigd in Magento 2, moet dit worden toegevoegd aan het knooppunt `//key/rename` , waar het oude pad wordt aangegeven in het knooppunt `//key/rename/path` node en het nieuwe pad in het knooppunt `//key/rename/to` .

Onder het knooppunt `<value>` staan regels die werken met de kolom &#39;value&#39; in de tabel `core_config_data` . Deze regels zijn bedoeld om de waarde van instellingen te transformeren door handlers (klassen die `Migration\Handler\HandlerInterface` implementeren) en deze aan te passen voor Magento 2.

### Gegevensmigratiemodus

In deze modus worden de meeste gegevens gemigreerd. Vóór gegevensmigratie worden de integriteitscontrolefasen voor elke stap uitgevoerd. Als de integriteitscontrole wordt uitgevoerd, installeert [!DNL Data Migration Tool] Deltalog-tabellen (met voorvoegsel `m2_cl_*` ) en de bijbehorende triggers naar de database van Magento 1 en wordt de gegevensmigratiefase met stappen uitgevoerd. Wanneer de migratie zonder fouten wordt voltooid, controleert de volumecontrole de gegevensconsistentie. Er kan een waarschuwingsbericht worden weergegeven als u de live winkel migreert. Maak u geen zorgen, delta migratie zorgt voor deze stijgende gegevens. De meest waardevolle migratiestappen zijn Kaart, URL herschrijft, en EAV.

#### Kaartstap

De stap van de kaart is verantwoordelijk voor het overbrengen van de meeste gegevens van Magento 1 aan Magento 2. Deze stap leest instructies uit het bestand map.xml (in de map `etc/` ). Het bestand beschrijft de verschillen tussen gegevensstructuren van bron (Magento 1) en doel (Magento 2). Als Magento 1 lijsten of gebieden bevat die tot één of andere uitbreiding behoren die niet in Magento 2 bestaat, dan kunnen deze entiteiten hier worden geplaatst om hen door de Stap van de Kaart te negeren. Anders wordt een foutbericht weergegeven.

Kaartbestand heeft de volgende indeling:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

Gebieden:

* *bron* - bevat regels van brongegevensbestand

* *bestemming* - bevat regels van bestemmingsgegevensbestand

Opties:

* *negeert* - document, gebied of datatype duidelijk met deze optie wordt genegeerd

* *anders noemen* - beschrijft naamverhoudingen tussen documenten met de verschillende naam. Als de naam van het doeldocument niet gelijk is aan de naam van het brondocument, kunt u de optie Naam wijzigen gebruiken om de naam van het brondocument gelijk te stellen aan de naam van de doeltabel

* *beweging* - reeksen regel om gespecificeerd gebied van brondocument naar bestemmingsdocument te bewegen. OPMERKING: de naam van het doeldocument moet gelijk zijn aan de naam van het brondocument. Als de naam van het bron- en doeldocument anders is, moet u de optie Naam wijzigen gebruiken voor documenten die een verplaatst veld bevatten

* *transformatie* - is een optie die gebruiker toestaat om gebieden volgens gedrag te migreren dat in managers wordt beschreven

* *manager* - beschrijft transformatiegedrag voor gebieden. Als u de handler wilt aanroepen, moet u een klassenaam voor de handler opgeven in een `<handler>` -tag. Gebruik de tag `<param>` met de naam en de waarde van de parameter om deze door te geven aan de handler

**Source** beschikbare verrichtingen:

| Document | Veld |
|--- |--- |
| naam wijzigen negeren | verplaatsen-transformatie negeren |

**Bestemming** beschikbare verrichtingen:

| Document | Veld |
|--- |--- |
| negeren | transformatie negeren |

#### Jokertekens

Als u documenten met vergelijkbare onderdelen wilt negeren (`document_name_1`, `document_name_2` ), kunt u jokertekenfunctionaliteit gebruiken. Zet het symbool `*` in plaats van het herhalende deel (`document_name_*`) en dit masker behandelt alle bron- of doeldocumenten die aan dit masker voldoen.

#### URL herschrijven stap

Deze stap is complex omdat er in Magento 1 veel verschillende algoritmen zijn ontwikkeld die niet compatibel zijn met Magento 2. Voor verschillende versies van Magento 1 kunnen er verschillende algoritmen zijn. Aldus onder de omslag Step/UrlRewrite zijn er klassen die voor sommige bepaalde versies van Magento werden ontwikkeld en Migration\Step\UrlRewrite\Version191to2000 is één van hen. URL kan URL overbrengen herschrijft gegevens van Magento 1.9.1 aan Magento 2.

#### EAV

Deze stap brengt alle attributen (product, klant, RMA) van Magento 1 aan Magento 2 over. Het gebruikt map-eav.xml- dossier dat regels gelijkend op degenen in map.xml- dossier voor specifieke gevallen van het verwerken van gegevens bevat.

Enkele tabellen die in de stap worden verwerkt:

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Delta-migratiemodus

Na hoofdmigratie, konden de extra gegevens aan het Magento 1 gegevensbestand (bijvoorbeeld, door klanten op opslag) worden toegevoegd. Om deze gegevens te volgen, plaatst het Hulpmiddel omhoog de gegevensbestandtrekkers voor lijsten in het begin van migratieproces. Voor meer informatie, zie [ gegevens migreren die door derdeuitbreidingen ](migrate-data/delta.md#migrate-data-created-by-third-party-extensions) worden gecreeerd.

## Gegevensbronnen

Om aan de gegevensbronnen van Magento 1 en Magento 2 te bereiken en met zijn gegevens (selecteren, bijwerken, opnemen, schrappen) te werken zijn er vele klassen in de omslag van het Middel. Migratie\ResourceModel\Source en Migration\ResourceModel\Destination zijn hoofdklassen. Alle migratiestappen gebruiken het om met gegevens te werken. Deze gegevens bevinden zich in klassen zoals Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure enzovoort.

Hier volgt een klassediagram van deze klassen:

![ Structuur van de Gegevens van het Hulpmiddel van de Migratie ](../../assets/data-migration/MmigrationToolDataStructure.png)

## Logboekregistratie

Om output van migratieproces uit te voeren en alle mogelijke niveaus te controleren PSR registreerapparaat, dat in Magento wordt gebruikt, wordt toegepast. `\Migration\Logger\Logger` -klasse is geïmplementeerd om logboekfunctionaliteit te bieden. Om het logger te gebruiken, moet u het injecteren via een constructorafhankelijke injectie.

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

Daarna kunt u deze klasse gebruiken voor het registreren van sommige gebeurtenissen:

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

Het is mogelijk aan te passen waar de logboekinformatie moet worden geschreven. U kunt dat doen door handler aan logboekregistratie toe te voegen met de methode pushHandler() van het logger. Elke handler moet de interface `\Monolog\Handler\HandlerInterface` implementeren. Er zijn nu twee handlers:

* ConsoleHandler: schrijft berichten naar console

* FileHandler: schrijft berichten naar logbestand dat is ingesteld in de configuratieoptie &quot;log_file&quot;

Het is ook mogelijk om het even welke extra manager uit te voeren. Er is een reeks managers in het kader van Magento. Voorbeeld van het toevoegen van handlers aan registreerapparaat:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Als u aanvullende gegevens voor registreerapparaten wilt instellen (huidige modus, tabelnaam), kunt u gebruikmaken van grotere processoren. Er is één bestaande processor (MessageProcessor). Het wordt gecreeerd om &quot;extra&quot;gegevens voor het registreren van berichten toe te voegen en wordt geroepen telkens als de logboekmethode wordt uitgevoerd. MessageProcessor heeft $extra var beveiligd, die lege waarden bevat voor &#39;mode&#39;, &#39;stage&#39;, &#39;step&#39; en &#39;table&#39;. Extra gegevens kunnen aan bewerker als tweede parameter (context) voor logboekmethode worden overgegaan. Extra gegevenssets die momenteel worden doorgegeven aan de processor in AbstractStep->runStage (huidige modus, werkgebied en stap naar processor), en gegevensklassen waar deze worden gebruikt in logger->debug-methode (de tabelnaam voor migreren doorgeven). Voorbeeld van het toevoegen van processors aan registreerapparaat:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Er is een mogelijkheid om het niveau van breedsprakigheid te bepalen. Op dit moment zijn er drie niveaus:

* `ERROR` (schrijft alleen fouten naar het logbestand)
* `INFO` (alleen belangrijke informatie wordt naar het logbestand geschreven, standaardwaarde)
* `DEBUG` (alles is geschreven)

Het niveau van het transparantielogboek kan voor elke manager afzonderlijk worden geplaatst door `setLevel()` methode te roepen. Als u een breedtepunt wilt instellen via een opdrachtregelparameter, moet u de optie &#39;verbose&#39; wijzigen bij het starten van de toepassing.

U kunt logberichten opmaken met de monoloog formatter. Om de formatterfunctionaliteit te laten werken, moet u de logboekmanager specificeren gebruikend de `setFormatter()` methode. Momenteel, hebben wij één formatter klasse (`MessageFormatter`) die bepaalde formaat (afhangt van breedtepunt) tijdens bericht behandeling (door de `format()` methode plaatst die van de manager wordt uitgevoerd).

Het manipuleren van het logger (het toevoegen van managers en bewerkers) en verwerking in uitgebreide wijze wordt uitgevoerd in de `process()` methode van de `Migration\Logger\Manager` klasse. De methode wordt aangeroepen wanneer de toepassing wordt gestart.

## Automatische tests

De [!DNL Data Migration Tool] bevat drie typen tests:

* Statisch
* Eenheid
* Integratie

Deze bevinden zich in de map `tests/` van het gereedschap. Dit is hetzelfde type test (eenheidstests staan in de map `tests/unit` ). Als u de test wilt starten, moet u de punit hebben geïnstalleerd. Wijzig de huidige map in de testmap en start de punit. Bijvoorbeeld:

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
