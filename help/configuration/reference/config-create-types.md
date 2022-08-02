---
title: Configuratietypen
description: Creeer of breid configuratietypen uit.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---


# Configuratietypen

## Configuratietypen uitbreiden

Om een bestaand configuratietype uit te breiden, moet u slechts een configuratiedossier in uw creëren [module](https://glossary.magento.com/module).

Als u bijvoorbeeld een gebeurteniswaarnemer wilt toevoegen, maakt u `app/code/{VendorName}/{ModuleName}/etc/events.xml` en een nieuwe waarnemer te verklaren.

Omdat het type van gebeurtenisconfiguratie in Handel bestaat, de lader en `events.xsd` het valideren van het schema is al aanwezig en werkt.

Uw nieuwe `events.xml` wordt automatisch verzameld uit uw module en samengevoegd met andere `events.xml` bestanden voor andere modules.

## Configuratietypen maken

Om een configuratietype tot stand te brengen, moet u minstens toevoegen:

- Een lader
- XSD-validatieschema
- XML-configuratiebestanden

Als u bijvoorbeeld een [adapter](https://glossary.magento.com/adapter) voor een nieuwe onderzoeksserver die uitbreidingen toelaat om te vormen hoe zijn entiteiten in die server worden geïndexeerd, creeer:

- Een lader
- Een XSD-schemabestand
- Een correct benoemd configuratiebestand. Bijvoorbeeld, `search.xml`. Dit bestand wordt op basis van uw schema gelezen en gevalideerd.
- Alle andere klassen die vereist zijn voor uw werk.

>[!INFO]
>
>Als nieuwe modules een `search.xml` worden deze bij het laden met uw bestand samengevoegd.

### Voorbeelden van het gebruik

Een configuratietype maken:

1. Maak uw XSD-bestand.
1. Maak uw XML-bestand.
1. Definieer het configuratieobject in uw `di.xml`.

   Het volgende voorbeeld van de module Magento_Sales [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) illustreert hoe een configuratievoorwerp zou moeten kijken als.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - Het eerste type knooppunt stelt de bestandsnaam van de Reader in, gekoppeld `Converter` en `SchemaLocator` klassen.
   - Dan, `pdfConfigDataStorage` Virtual Type-knooppunt koppelt de Reader-klasse aan een instantie van [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - Tot slot koppelt de laatste typeknoopknoop dat config gegevens virtueel type aan het [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) klasse, die wordt gebruikt voor het lezen van waarden in [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) bestanden.

1. Een lezer definiëren door deze uit te breiden [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) klasse en herschrijf de volgende parameters:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Voorbeeld:**

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>Als u liever uw eigen versie van de lezer maakt, kunt u dit doen door `\Magento\Framework\Config\ReaderInterface`. Zie [Magento_Analytics config-lezer](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Nadat u de lezer hebt gedefinieerd, gebruikt u deze om de configuratiebestanden te verzamelen, samen te voegen, te valideren en om te zetten in een interne arrayrepresentatie.

## Een configuratietype valideren

Elk configuratiedossier wordt bevestigd tegen een schema specifiek voor zijn configuratietype. Voorbeeld: gebeurtenissen, die, in vroegere versies van de Handel werden gevormd in `config.xml`, zijn nu geconfigureerd in `events.xml`.

Configuratiebestanden kunnen zowel voor (optioneel) als na het samenvoegen van meerdere bestanden met hetzelfde configuratietype worden gevalideerd. Tenzij de validatieregels voor de afzonderlijke en samengevoegde bestanden identiek zijn, moet u twee schema&#39;s opgeven voor het valideren van de configuratiebestanden:

- Schema om een individu te valideren
- Schema om een samengevoegd bestand te valideren

Nieuwe configuratiebestanden moeten vergezeld gaan van XSD-validatieschema&#39;s. Een XML-configuratiebestand en het bijbehorende XSD-validatiebestand moeten dezelfde naam hebben.

Als u twee XSD-bestanden moet gebruiken voor één XML-bestand, moeten de namen van de schema&#39;s herkenbaar zijn en aan het XML-bestand zijn gekoppeld.
Als u een `events.xml` bestand en een eerste `events.xsd` bestand, de XSD-bestanden voor het samengevoegde `events.xml` bestand kan een naam krijgen `events_merged.xsd`.
Om ervoor te zorgen dat een XML-bestand wordt gevalideerd door het juiste XSD-bestand, moet u de URL (Uniform Resource Name) toevoegen aan het XSD-bestand in het XML-bestand. Bijvoorbeeld:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

Uw IDE kan uw configuratiedossiers zowel runtime als tijdens ontwikkeling bevestigen.
