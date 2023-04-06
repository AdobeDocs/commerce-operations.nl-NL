---
title: "[!DNL Data Migration Tool] technische specificatie"
description: "Meer informatie over de implementatiedetails van de [!DNL Data Migration Tool] en hoe u de gegevensoverdracht tussen Magento 1 en Magento 2 kunt uitbreiden."
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '2079'
ht-degree: 0%

---


# [!DNL Data Migration Tool] technische specificatie

Deze sectie beschrijft [!DNL Data Migration Tool] implementatiedetails en hoe de functionaliteit ervan kan worden uitgebreid.

## Opslagplaatsen

Om toegang te krijgen tot [!DNL Data Migration Tool] broncode, zie GitHub [opslagplaats](https://github.com/magento/data-migration-tool).

## Systeemvereisten

De [systeemvereisten](../../installation/system-requirements.md) voor de [!DNL Data Migration Tool] zijn dezelfde als voor Magento 2.

## Interne structuur

### Directorystructuur

Het volgende diagram vertegenwoordigt de mappenstructuur van [!DNL Data Migration Tool]:

```terminal
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

Het script waarmee het migratieproces wordt uitgevoerd, bevindt zich in: `magento-root/bin/magento`.

## Configuratie

Het schema voor de configuratie `config.xsd` bestand bevindt zich in het dialoogvenster `etc/` directory. Het standaardconfiguratiebestand (`config.xml.dist`) wordt gemaakt voor elke versie van Magento 1.x. Het bevindt zich in een aparte directory onder `etc/`.

Het standaardconfiguratiebestand kan worden vervangen door een aangepast bestand (zie [opdrachtsyntaxis](migrate-data/overview.md#command-syntax)).

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

Voorvoegseloptie wijzigen voor het geval dat Magento met voorvoegsel in databasetabellen is geïnstalleerd. Deze kan worden ingesteld voor databases van Magento 1 en Magento 2. Gebruik de configuratieopties &quot;source_prefix&quot; en &quot;dest_prefix&quot; dienovereenkomstig.

De gegevens van de configuratie zijn toegankelijk met `\Migration\Config` klasse.

## Stappen van beschikbare bewerkingen

| Document | Veld |
|---|---|
| `step` | Knooppunt op het tweede niveau binnen het knooppunt Stappen. In de `title` kenmerk. |
| `integrity` | Geeft de PHP-klasse op die verantwoordelijk is voor de integriteitscontrole. Vergelijkt de namen, types, en andere info van de lijstgebieden om verenigbaarheid tussen Magento 1 en 2 gegevensstructuren te verifiëren. |
| `data` | Geeft de PHP-klasse op die verantwoordelijk is voor de gegevenscontrole. Hiermee worden de gegevens, tabel voor tabel, overgedragen van Magento 1 naar Magento 2. |
| `volume` | Geeft de PHP-klasse op die verantwoordelijk is voor de volumecontrole. Vergelijkt het aantal verslagen tussen lijsten om te verifiëren dat de overdracht succesvol was. |
| `delta` | Geeft de PHP-klasse op die verantwoordelijk is voor de deltacontrole. Brengt de delta van Magento 1 naar Magento 2 na de volledige gegevensmigratie over. |

## Kenmerken van de brondatabasegegevens

| Document | Veld | Vereist? |
|---|---|---|
| `name` | Databasenaam van de Magento 1-server. | ja |
| `host` | IP van de gastheer adres van de server Magento 1. | ja |
| `port` | Poortnummer van de Magento 1-server. | nee |
| `user` | Gebruikersnaam van de Magento 1-databaseserver. | ja |
| `password` | Wachtwoord van de Magento 1-databaseserver. | ja |
| `ssl_ca` | Pad naar SSL Certificate Authority-bestand. | nee |
| `ssl_cert` | Pad naar SSL-certificaatbestand. | nee |
| `ssl_key` | Pad naar SSL-sleutelbestand. | nee |

## Kenmerken van de gegevensbank van de bestemming

| Document | Veld | Vereist? |
|---|---|---|
| `name` | Databasenaam van de Magento 2-server. | ja |
| `host` | IP van de gastheer adres van de server van Magento 2. | ja |
| `port` | Poortnummer van de Magento 2-server. | nee |
| `user` | Gebruikersnaam van de Magento 2-databaseserver. | ja |
| `password` | Wachtwoord van de Magento 2-databaseserver. | ja |
| `ssl_ca` | Pad naar SSL Certificate Authority-bestand. | nee |
| `ssl_cert` | Pad naar SSL-certificaatbestand. | nee |
| `ssl_key` | Pad naar SSL-sleutelbestand. | nee |

## Verbinding maken via het TLS-protocol

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

## Interne stappen

Het migratieproces bestaat uit stappen.

Stap is een eenheid die functionaliteit verstrekt die voor migratie sommige gescheiden gegevens wordt vereist. De stap kan uit één of meerdere stadia (integriteitscontrole, gegevens, volumecontrole, en delta) bestaan.

Standaard zijn er verschillende stappen ([Kaart](#map-step), [EAV](#eav), [URL herschrijft](#url-rewrite-step), enzovoort). U kunt desgewenst ook uw eigen stappen toevoegen.

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

Als het gegevenswerkgebied terugdraaiacties ondersteunt, moet het `RollbackInterface` interface.

Visualisatie van de lopende stap wordt verstrekt door de component ProgressBar van Symfony (zie [Voortgangsbalk](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Open deze component in een stap als LogLevelProcessor.

De belangrijkste gebruiksmethoden zijn:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Stappen

### Integriteitscontrole

Elke stap moet controleren of de structuur van de gegevensbron (standaard Magento 1) en de structuur van de gegevensbestemming (Magento 2) compatibel zijn. Zo niet, dan wordt een fout weergegeven met entiteiten die niet compatibel zijn. Als velden verschillende datatypen hebben (hetzelfde veld heeft een decimaal gegevenstype in Magento 1 en een geheel getal in Magento 2), wordt een waarschuwingsbericht weergegeven (behalve wanneer het veld is opgenomen in het Kaartenbestand).

### Gegevensoverdracht

Als de integriteitscontrole wordt doorgegeven, worden gegevens overgedragen. Als er fouten optreden, wordt het terugdraaien uitgevoerd om terug te keren naar de vorige status van Magento 2. Als een stapklasse de klasse `RollbackInterface` en wordt de terugdraaimethode uitgevoerd wanneer er een fout optreedt.

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

Onder het knooppunt `<key>` er zijn regels die werken met de kolom &#39;path&#39; in het dialoogvenster `core_config_data` tabel. `<ignore>` voorkomt dat het gereedschap bepaalde instellingen overbrengt. Jokertekens kunnen in dit knooppunt worden gebruikt. Alle andere instellingen die niet worden vermeld in het dialoogvenster `<ignore>` knooppunt wordt gemigreerd. Als het pad naar een instelling is gewijzigd in Magento 2, moet dit worden toegevoegd aan `//key/rename` knooppunt, waarbij het oude pad aangeeft in `//key/rename/path` knooppunt en nieuw pad wordt aangegeven in `//key/rename/to` knooppunt.

Onder het knooppunt `<value>`, zijn er regels die werken met de kolom &#39;value&#39; in het dialoogvenster `core_config_data` tabel. Deze regels zijn bedoeld om de waarde van instellingen te transformeren door handlers (klassen die `Migration\Handler\HandlerInterface`) en aanpassen voor Magento 2.

### Gegevensmigratiemodus

In deze modus worden de meeste gegevens gemigreerd. Vóór gegevensmigratie worden de integriteitscontrolefasen voor elke stap uitgevoerd. Als de integriteitscontrole slaagt, kan de [!DNL Data Migration Tool] Hiermee installeert u Deltalog-tabellen (met voorvoegsel) `m2_cl_*`) en de bijbehorende triggers naar de Magento 1-database en voert de gegevensmigratiefase van stappen uit. Wanneer de migratie zonder fouten wordt voltooid, controleert de volumecontrole de gegevensconsistentie. Er kan een waarschuwingsbericht worden weergegeven als u de live winkel migreert. Maak u geen zorgen, delta migratie zorgt voor deze stijgende gegevens. De meest waardevolle migratiestappen zijn Kaart, URL herschrijft, en EAV.

#### Kaartstap

De stap van de kaart is verantwoordelijk voor het overbrengen van de meeste gegevens van Magento 1 aan Magento 2. Deze stap leest instructies van map.xml- dossier (in `etc/` directory). In het bestand worden de verschillen beschreven tussen gegevensstructuren van bron (Magento 1) en doel (Magento 2). Als Magento 1 lijsten of gebieden bevat die tot één of andere uitbreiding behoren die niet in Magento 2 bestaat, dan kunnen deze entiteiten hier worden geplaatst om hen door de Stap van de Kaart te negeren. Anders wordt een foutbericht weergegeven.

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

* *bron* - bevat regels voor de brondatabase

* *doel* - bevat regels voor de doeldatabase

Opties:

* *negeren* - het document, veld of gegevenstype dat met deze optie is gemarkeerd, wordt genegeerd

* *naam wijzigen* - een beschrijving van de naamrelaties tussen documenten met een andere naam. Als de naam van het doeldocument niet gelijk is aan de naam van het brondocument, kunt u de optie Naam wijzigen gebruiken om de naam van het brondocument gelijk te stellen aan de naam van de doeltabel

* *move* - stelt de regel in om het opgegeven veld van het brondocument naar het doeldocument te verplaatsen. OPMERKING: de naam van het doeldocument moet gelijk zijn aan de naam van het brondocument. Als de naam van het bron- en doeldocument anders is, moet u de optie Naam wijzigen gebruiken voor het document dat het verplaatste veld bevat

* *transformeren* - is een optie waarmee de gebruiker velden kan migreren volgens het gedrag dat in handlers wordt beschreven

* *handler* - beschrijft het transformatiegedrag voor velden. Om de manager te roepen, moet u een naam van de managerklasse in specificeren `<handler>` tag. Gebruik de `<param>` -tag met de parameternaam en -waardengegevens om deze door te geven aan de handler

**Bron** beschikbare bewerkingen:

| Document | Veld |
|--- |--- |
| naam wijzigen negeren | verplaatsen-transformatie negeren |

**Doel** beschikbare bewerkingen:

| Document | Veld |
|--- |--- |
| negeren | transformatie negeren |

#### Jokertekens

Documenten met vergelijkbare onderdelen negeren (`document_name_1`, `document_name_2`) kunt u jokertekens gebruiken. Put `*` symbool in plaats van herhalend deel (`document_name_*`) en dit masker geldt voor alle bron- of doeldocumenten die aan dit masker voldoen.

#### Stap voor herschrijven van URL

Deze stap is complex omdat er veel verschillende algoritmen zijn ontwikkeld in Magento 1 die niet compatibel zijn met Magento 2. Voor verschillende versies van Magento 1 kunnen er verschillende algoritmen zijn. Aldus onder de omslag Step/UrlRewrite zijn er klassen die voor sommige bepaalde versies van Magento en Migration\Step\UrlRewrite\Version191to2000 is one of them werden ontwikkeld. URL kan URL overbrengen herschrijft gegevens van Magento 1.9.1 aan Magento 2.

#### EAV-stap

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

Na de hoofdmigratie hadden extra gegevens kunnen worden toegevoegd aan de Magento 1-database (bijvoorbeeld door klanten op de winkel). Om deze gegevens te volgen, plaatst het Hulpmiddel omhoog de gegevensbestandtrekkers voor lijsten in het begin van migratieproces. Zie voor meer informatie [Gegevens migreren die door externe extensies zijn gemaakt](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Gegevensbronnen

Om aan de gegevensbronnen van Magento 1 en Magento 2 te bereiken en met zijn gegevens (selecteren, bijwerken, opnemen, schrappen) te werken zijn er vele klassen in de omslag van het Middel. Migratie\ResourceModel\Source and Migration\ResourceModel\Destination are main classes. Alle migratiestappen gebruiken het om met gegevens te werken. Deze gegevens bevinden zich in klassen zoals Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure enzovoort.

Hier volgt een klassediagram van deze klassen:

![Gegevensstructuur van migratiehulpprogramma](../../assets/data-migration/MmigrationToolDataStructure.png)

## Logboekregistratie

Om output van migratieproces uit te voeren en alle mogelijke niveausPSR registreerapparaat te controleren, dat in Magento wordt gebruikt, wordt toegepast. `\Migration\Logger\Logger` -klasse is geïmplementeerd om logboekfunctionaliteit te bieden. Om het logger te gebruiken, moet u het injecteren via een constructorafhankelijke injectie.

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

Het is mogelijk aan te passen waar de logboekinformatie moet worden geschreven. U kunt dat doen door handler aan logboekregistratie toe te voegen met de methode pushHandler() van het logger. Elke handler moet `\Monolog\Handler\HandlerInterface` interface. Er zijn nu twee handlers:

* ConsoleHandler: schrijft berichten aan console

* FileHandler: schrijft berichten aan logboekdossier dat in &quot;log_file&quot;configuratieoptie is geplaatst

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

* `ERROR` (schrijft slechts fouten aan het logboek)
* `INFO` (alleen belangrijke gegevens worden naar het logbestand geschreven, standaardwaarde)
* `DEBUG` (alles is geschreven)

Het niveau van het transparantielogboek kan voor elke manager afzonderlijk worden geplaatst door te roepen `setLevel()` methode. Als u een breedtepunt wilt instellen via een opdrachtregelparameter, moet u de optie &#39;verbose&#39; wijzigen bij het starten van de toepassing.

U kunt logberichten opmaken met de monoloog formatter. Om de formatterfunctionaliteit te laten werken, moet u de logboekmanager specificeren gebruikend `setFormatter()` methode. We hebben momenteel één opmaakklasse (`MessageFormatter`) die bepaalde indeling instelt (afhankelijk van het breedtepunt) tijdens berichtverwerking (via de `format()` methode uitgevoerd vanuit de handler).

Het manipuleren van de logger (het toevoegen van managers en bewerkers) en verwerking op uitgebreide wijze wordt uitgevoerd in `process()` methode `Migration\Logger\Manager` klasse. De methode wordt aangeroepen wanneer de toepassing wordt gestart.

## Automatische tests

Er zijn drie typen tests in de [!DNL Data Migration Tool]:

* Statisch
* Eenheid
* Integratie

Ze bevinden zich in de `tests/` directory, die hetzelfde is als het type test (eenheidstests staan in de map `tests/unit` directory). Als u de test wilt starten, moet u de punit hebben geïnstalleerd. Wijzig de huidige map in de testmap en start de punit. Bijvoorbeeld:

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
