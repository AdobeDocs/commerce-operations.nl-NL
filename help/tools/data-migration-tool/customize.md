---
title: Pas  [!DNL Data Migration Tool] aan
description: Leer hoe te om  [!DNL Data Migration Tool]  aan overdrachtgegevens aan te passen die door uitbreidingen tussen Magento 1 en Magento 2 worden gecreeerd.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# De [!DNL Data Migration Tool] configureren

Soms is het gegevensformaat en de structuur die door [&#x200B; wordt gecreeerd uitbreidingen &#x200B;](https://marketplace.magento.com/extensions.html) of douanecode verschillend tussen Magento 1 en Magento 2. Gebruik extensiepunten in de [!DNL Data Migration Tool] om deze gegevens te migreren. Als de gegevensindeling en -structuur hetzelfde zijn, kunnen de gegevens automatisch worden gemigreerd zonder tussenkomst van de gebruiker.

Tijdens migratie, scant de [&#x200B; Stap van de Kaart &#x200B;](technical-specification.md#map-step) en vergelijkt alle Magento 1 en Magento 2 lijsten, met inbegrip van die die door uitbreidingen worden gecreeerd. Als de tabellen overeenkomen, worden de gegevens automatisch gemigreerd. Als de tabellen verschillen, wordt het gereedschap beëindigd en wordt de gebruiker een melding gestuurd.

>[!NOTE]
>
>Lees de [&#x200B; Technische Specificatie &#x200B;](technical-specification.md) alvorens te proberen om [!DNL Data Migration Tool] uit te breiden. Ook, herzie de [&#x200B; Gids van de Migratie &#x200B;](../overview.md) voor algemene informatie over het gebruiken van het migratiehulpmiddel.


## Kleine wijzigingen in gegevensindeling en -structuur

In de meeste gevallen, verhelpt de [&#x200B; Stap van de Kaart &#x200B;](technical-specification.md#map-step) voldoende kleine gegevensformaat en structuurveranderingen gebruikend de volgende methodes in het `map.xml` dossier:

- Tabel- of veldnamen wijzigen met toewijzingsregels
- Gegevensindelingen transformeren met bestaande handlers of een aangepaste handler

In het volgende voorbeeld ziet u hoe u zowel toewijzingsregels als een handler kunt gebruiken. In dit voorbeeld wordt de extensie &#39;GreatBlog&#39; van Magento 1 gebruikt die voor Magento 2 is verbeterd.

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- Migreer geen overbodige gegevens uit de `great_blog_index` indextabel.
- De naam van de tabel `great_blog_publication` is gewijzigd in `great_blog_post` in Magento 2, zodat gegevens naar de nieuwe tabel worden gemigreerd.
   - De naam van het veld `summary` is gewijzigd in `title` , zodat gegevens naar het nieuwe veld worden gemigreerd.
   - Het veld `priority` is verwijderd en bestaat niet meer in Magento 2.
   - De gegevens in het veld `body` hebben een andere indeling en moeten worden verwerkt door de aangepaste handler: `\Migration\Handler\GreatBlog\NewFormat` .
- Er is een nieuwe ratingfunctie ontwikkeld voor de extensie &quot;GreatBlog&quot; in Magento 2.
   - Er is een nieuwe tabel van `great_blog_rating` gemaakt.
   - Er is een nieuw veld `great_blog_post.rating` gemaakt.

### Toewijzing in andere stappen uitbreiden

Andere stappen steunen afbeelding, zoals de [&#x200B; Stap EAV &#x200B;](technical-specification.md#eav-step) en de Stap van de Attributen van de Klant. Deze stappen migreren een vooraf gedefinieerde lijst met Magento-tabellen. Stel dat de extensie &quot;GreatBlog&quot; een extra veld heeft in de tabel `eav_attribute` en de naam is gewijzigd in Magento 2. Aangezien de lijst door de [&#x200B; Stap EAV &#x200B;](technical-specification.md#eav-step) wordt verwerkt, zouden de toewijzingsregels voor het `map-eav.xml` dossier moeten worden geschreven. De `map.xml` - en `map-eav.xml` -bestanden gebruiken hetzelfde `map.xsd` -schema, zodat de toewijzingsregels ongewijzigd blijven.

## Belangrijke wijzigingen in gegevensindeling en -structuur

Naast de Map Step zijn er andere stappen in het `config.xml` -bestand die gegevens migreren met belangrijke indelings- en structuurwijzigingen, zoals:

- [Stap voor herschrijven van URL](technical-specification.md#url-rewrite-step)
- Stap OrderGrids
- [EAV-stap](technical-specification.md#eav-step)

In tegenstelling tot de [&#x200B; Stap van de Kaart &#x200B;](technical-specification.md#map-step), scannen deze stappen een vooraf bepaalde lijst van lijsten in plaats van alle lijsten.

Maak een aangepaste stap voor belangrijke wijzigingen in de gegevensindeling en -structuur.

### Een aangepaste stap maken

Als u hetzelfde &#39;GreatBlog&#39;-voorbeeld gebruikt, gaat u ervan uit dat de extensie één tabel heeft in Magento 1, maar dat de extensie opnieuw is ontworpen voor twee tabellen in Magento 2.

In Magento 1 was er één `greatblog_post` -tabel:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

In Magento 2 is een nieuwe tabel voor tags `greatblog_post_tags` geïntroduceerd:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

Magento 2 `greatblog_post` -tabel ziet er nu als volgt uit:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Als u alle gegevens wilt migreren van de oude tabelstructuur naar een nieuwe, kunt u een aangepaste stap maken in het `config.xml` -bestand. Bijvoorbeeld:

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

Het gereedschap voert stappen uit op basis van de positie in het `config.xml` -bestand, van boven naar beneden. In ons voorbeeld wordt `GreatBlog Step` als laatste uitgevoerd.

De stappen kunnen vier types van klassen omvatten:

- Integriteitscontrole
- Gegevenslevering
- Volume controleren
- Delta levert

>[!NOTE]
>
>Verwijs naar [&#x200B; Configuratie &#x200B;](technical-specification.md#configuration), [&#x200B; Stap internals &#x200B;](technical-specification.md#step-internals), [&#x200B; Stages &#x200B;](technical-specification.md#step-stages), en [&#x200B; Lopende wijzen &#x200B;](technical-specification.md#running-modes) voor meer informatie.


Complexe SQL-query&#39;s kunnen binnen deze klassen worden verzameld om gegevens op te halen en te migreren. Ook, zouden deze lijsten &quot;moeten worden genegeerd&quot;in de [&#x200B; Stap van de Kaart &#x200B;](technical-specification.md#map-step) omdat het alle bestaande lijsten aftasten en probeert om de gegevens te migreren tenzij het in de `<ignore>` markering van het `map.xml` dossier is.

Definieer bij Integriteit controleren een extra kaartbestand in het `config.xml` -bestand om te controleren of de tabelstructuur naar verwachting is.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

Kaartbestand `map-greatblog.xml` :

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

De klasse Integrity checking `Vendor\Migration\Step\GreatBlog\Integrity` is een uitbreiding `Migration\App\Step\AbstractIntegrity` en bevat de methode `perform` waarmee de tabelstructuur wordt gecontroleerd:

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

Vervolgens moet u een klasse maken voor het verwerken en opslaan van gegevens in de Magento 2-database `Vendor\Migration\Step\GreatBlog\Data` :

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

In een klasse Volume `Vendor\Migration\Step\GreatBlog\Volume` controleren we of de gegevens volledig zijn gemigreerd:

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

Als u de deltabigatiefunctionaliteit wilt toevoegen, voegt u een nieuwe groep toe aan het `deltalog.xml` -bestand. Geef in `group` de naam op van de tabellen die op wijzigingen moeten worden gecontroleerd:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Maak vervolgens de `Delta` class `Vendor\Migration\Step\GreatBlog\Delta` die `Migration\App\Step\AbstractDelta` uitbreidt:

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

Na de implementatie van de aangepaste stap in de voorbeelden, neemt het systeem gegevens van de enige Magento 1-tabel.
het verwerken met de klasse `Vendor\Migration\Step\GreatBlog\Data` en de gegevens opslaan in twee Magento 2-tabellen. Nieuwe en gewijzigde records worden geleverd bij de migratie naar delta met behulp van de `Vendor\Migration\Step\GreatBlog\Delta` -klasse.

## Verboden extensiemethoden

Aangezien de [!DNL Data Migration Tool] en Magento 2 voortdurend evolueren, kunnen bestaande stappen en handlers worden gewijzigd. Wij adviseren hoogst niet het gedrag van stappen zoals de [&#x200B; Stap van de Kaart &#x200B;](technical-specification.md#map-step) met voeten te treden, [&#x200B; URL herschrijft Stap &#x200B;](technical-specification.md#url-rewrite-step), en managers door hun klassen uit te breiden.

Sommige stappen ondersteunen geen toewijzing en kunnen niet worden gewijzigd zonder de code te wijzigen. U kunt of een extra stap schrijven die gegevens aan het eind van migratie verandert of de kwestie van a [&#x200B; GitHub &#x200B;](https://github.com/magento/data-migration-tool/issues) creëren en om een nieuw uitbreidingspunt op de bestaande stap vragen.
