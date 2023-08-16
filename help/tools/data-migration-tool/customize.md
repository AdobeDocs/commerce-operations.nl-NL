---
title: De [!DNL Data Migration Tool]
description: Leer hoe u de [!DNL Data Migration Tool] gegevens die zijn gemaakt door extensies over te brengen tussen Magento 1 en Magento 2.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Vorm [!DNL Data Migration Tool]

Soms wordt de gegevensindeling en -structuur gemaakt door [extensions](https://marketplace.magento.com/extensions.html) of aangepaste code verschilt tussen Magento 1 en Magento 2. Extensiepunten gebruiken in het dialoogvenster [!DNL Data Migration Tool] deze gegevens migreren. Als de gegevensindeling en -structuur hetzelfde zijn, kunnen de gegevens automatisch worden gemigreerd zonder tussenkomst van de gebruiker.

Tijdens de migratie [Kaartstap](technical-specification.md#map-step) scant en vergelijkt alle Magento 1 en Magento 2 lijsten, met inbegrip van die gecreeerd door uitbreidingen. Als de tabellen overeenkomen, worden de gegevens automatisch gemigreerd. Als de tabellen verschillen, wordt het gereedschap beëindigd en wordt de gebruiker een melding gestuurd.

>[!NOTE]
>
>Lees de [Technische specificaties](technical-specification.md) voordat u probeert de [!DNL Data Migration Tool]. Lees ook de [Migratiehandleiding](../overview.md) voor algemene informatie over het gebruik van het migratiehulpmiddel.


## Kleine wijzigingen in gegevensindeling en -structuur

In de meeste gevallen wordt [Kaartstap](technical-specification.md#map-step) Hiermee worden kleine wijzigingen in de gegevensindeling en -structuur voldoende opgelost met de volgende methoden in het dialoogvenster `map.xml` bestand:

- Tabel- of veldnamen wijzigen met toewijzingsregels
- Gegevensindelingen transformeren met bestaande handlers of een aangepaste handler

In het volgende voorbeeld ziet u hoe u zowel toewijzingsregels als een handler kunt gebruiken. In dit voorbeeld wordt de extensie &#39;GreatBlog&#39; gebruikt van een hypothetisch Magento 1 dat is verbeterd voor Magento 2.

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

- Geen onnodige gegevens migreren uit de `great_blog_index` indextabel.
- De tabel `great_blog_publication` is hernoemd naar `great_blog_post` in Magento 2, zodat worden de gegevens gemigreerd aan de nieuwe lijst.
   - De `summary` veld is hernoemd naar `title`gegevens worden dus naar het nieuwe veld gemigreerd.
   - De `priority` is verwijderd en bestaat niet meer in Magento 2.
   - De gegevens in de `body` Het veld heeft een andere indeling en moet worden verwerkt door de aangepaste handler: `\Migration\Handler\GreatBlog\NewFormat`.
- In Magento 2 is een nieuwe ratingfunctie ontwikkeld voor de extensie &quot;GreatBlog&quot;.
   - Een nieuwe `great_blog_rating` tabel is gemaakt.
   - Een nieuwe `great_blog_post.rating` is gemaakt.

### Toewijzing in andere stappen uitbreiden

Andere stappen ondersteunen toewijzing, zoals de [EAV-stap](technical-specification.md#eav-step) en de stap Kenmerken van de Klant. Met deze stappen migreert u een vooraf gedefinieerde lijst met tabellen met Magento&#39;s. Stel dat de extensie &quot;GreatBlog&quot; een extra veld heeft in het dialoogvenster `eav_attribute` tabel en de naam gewijzigd in Magento 2. Aangezien de tabel door de [EAV-stap](technical-specification.md#eav-step), moeten toewijzingsregels worden opgesteld voor de `map-eav.xml` bestand. De `map.xml` en `map-eav.xml` bestanden gebruiken dezelfde `map.xsd` schema, zodat blijven de toewijzingsregels het zelfde.

## Belangrijke wijzigingen in gegevensindeling en -structuur

Naast de Stap van de Kaart, zijn er andere stappen in `config.xml` bestanden die gegevens migreren met belangrijke wijzigingen in indeling en structuur, zoals:

- [Stap voor herschrijven van URL](technical-specification.md#url-rewrite-step)
- Stap OrderGrids
- [EAV-stap](technical-specification.md#eav-step)

In tegenstelling tot [Kaartstap](technical-specification.md#map-step)Met deze stappen kunt u een vooraf gedefinieerde lijst met tabellen scannen in plaats van alle tabellen.

Maak een aangepaste stap voor belangrijke wijzigingen in de gegevensindeling en -structuur.

### Een aangepaste stap maken

Gebruikend het zelfde &quot;GroteBlog&quot;voorbeeld, veronderstel dat de uitbreiding één lijst in Magento 1 heeft, maar opnieuw werd ontworpen om twee lijsten in Magento 2 te hebben.

In Magento 1 was er één `greatblog_post` tabel:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

In Magento 2, een nieuwe lijst voor markeringen `greatblog_post_tags` is ingevoerd:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

MAGENTO 2 `greatblog_post` de tabel ziet er nu als volgt uit :

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Als u alle gegevens wilt migreren van de oude tabelstructuur naar een nieuwe structuur, kunt u een aangepaste stap maken in het dialoogvenster `config.xml` bestand. Bijvoorbeeld:

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

Het gereedschap voert stappen uit op basis van de positie in het dialoogvenster `config.xml` bestand; van boven naar beneden. In ons voorbeeld `GreatBlog Step` loopt als laatste.

De stappen kunnen vier types van klassen omvatten:

- Integriteitscontrole
- Gegevenslevering
- Volume controleren
- Delta levert

>[!NOTE]
>
>Zie [Configuratie](technical-specification.md#configuration), [Interne stappen](technical-specification.md#step-internals), [Staven](technical-specification.md#step-stages), en [Runmodi](technical-specification.md#running-modes) voor meer informatie .


Complexe SQL-query&#39;s kunnen binnen deze klassen worden verzameld om gegevens op te halen en te migreren. Deze tabellen moeten ook worden &quot;genegeerd&quot; in het dialoogvenster [Kaartstap](technical-specification.md#map-step) omdat het alle bestaande tabellen scant en de gegevens probeert te migreren, tenzij deze zich in het dialoogvenster `<ignore>` tag van de `map.xml` bestand.

Definieer voor Integriteit controleren een extra kaartbestand in het dialoogvenster `config.xml` bestand om te controleren of de tabelstructuur naar verwachting is.

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

Kaartbestand `map-greatblog.xml`:

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

Integriteitscontrole, klasse `Vendor\Migration\Step\GreatBlog\Integrity` extends `Migration\App\Step\AbstractIntegrity` en bevat de `perform` methode voor het controleren van de tabelstructuur:

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

Vervolgens moet u een klasse maken voor het verwerken en opslaan van gegevens in de database Magento 2 `Vendor\Migration\Step\GreatBlog\Data`:

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

In een klasse Volume `Vendor\Migration\Step\GreatBlog\Volume`, controleren wij of de gegevens volledig zijn gemigreerd:

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

Als u de deltabigatiefunctionaliteit wilt toevoegen, voegt u een nieuwe groep toe aan de `deltalog.xml` bestand. In `group`geeft u de naam op van de tabellen die op wijzigingen moeten worden gecontroleerd:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Maak vervolgens de `Delta` class `Vendor\Migration\Step\GreatBlog\Delta` die `Migration\App\Step\AbstractDelta`:

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

Nadat de implementatie van de douanestappen in de voorbeelden wordt verstrekt, neemt het systeem gegevens van enige Magento 1 lijst, het verwerken gebruikend `Vendor\Migration\Step\GreatBlog\Data` en slaat de gegevens op in twee Magento 2-tabellen. Nieuwe en gewijzigde records worden geleverd bij de migratie naar delta met behulp van de `Vendor\Migration\Step\GreatBlog\Delta` klasse.

## Verboden extensiemethoden

Aangezien de [!DNL Data Migration Tool] en Magento 2 evolueert voortdurend en de bestaande stappen en handlers kunnen veranderen . We raden u ten zeerste aan het gedrag van stappen als de [Kaartstap](technical-specification.md#map-step), [URL-herschrijfstap](technical-specification.md#url-rewrite-step)en handlers door hun klassen uit te breiden.

Sommige stappen ondersteunen geen toewijzing en kunnen niet worden gewijzigd zonder de code te wijzigen. U kunt of een extra stap schrijven die gegevens aan het eind van migratie verandert of tot een [GitHub-probleem](https://github.com/magento/data-migration-tool/issues) en vraagt om een nieuw verlengingspunt op de bestaande stap.
