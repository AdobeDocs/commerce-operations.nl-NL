---
title: Configuratietypen
description: Creeer of breid configuratietypen uit.
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 4116d0983edc797ce42d24e711fb5ecdbf8fdec9
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Configuratietypen

## Configuratietypen uitbreiden

Om een bestaand configuratietype uit te breiden, moet u slechts een configuratiedossier in uw module tot stand brengen.

Als u bijvoorbeeld een gebeurteniswaarnemer wilt toevoegen, maakt u `app/code/{VendorName}/{ModuleName}/etc/events.xml` en declareert u een nieuwe waarnemer.

Omdat het type gebeurtenisconfiguratie in Commerce bestaat, zijn de lader en het `events.xsd` validerende schema al aanwezig en functioneel.

Uw nieuwe `events.xml` wordt automatisch verzameld uit uw module en samengevoegd met andere `events.xml` -bestanden voor andere modules.

## Configuratietypen maken

Om een configuratietype tot stand te brengen, moet u minstens toevoegen:

- Een lader
- XSD-validatieschema
- XML-configuratiebestanden

Als u bijvoorbeeld een adapter wilt introduceren voor een nieuwe zoekserver waarmee extensies kunnen configureren hoe de entiteiten op die server worden geïndexeerd, maakt u:

- Een lader
- Een XSD-schemabestand
- Een correct benoemd configuratiebestand. Bijvoorbeeld `search.xml` . Dit bestand wordt op basis van uw schema gelezen en gevalideerd.
- Alle andere klassen die vereist zijn voor uw werk.

>[!INFO]
>
>Als de nieuwe modules een `search.xml` dossier hebben, worden zij samengevoegd met uw dossier wanneer het laadt.

### Voorbeelden van gebruik

Een configuratietype maken:

1. Maak uw XSD-bestand.
1. Maak uw XML-bestand.
1. Definieer het configuratieobject in de `di.xml` .

   Het volgende voorbeeld van Magento_Sales module [ di.xml ](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) illustreert hoe een configuratievoorwerp als zou moeten kijken.

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

   - Het eerste type knooppunt stelt de bestandsnaam van de Reader, de gekoppelde `Converter` - en `SchemaLocator` -klassen in.
   - Dan, verbindt de `pdfConfigDataStorage` virtuele typeknoop de lezerklasse aan een geval van [ Magento\Framework\Config\Data ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - En tenslotte, verbindt de laatste typeknoop dat config gegevens virtueel type aan de [ Magento\Sales\Model\Order\Pdf\Config ](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) klasse, die voor eigenlijk het lezen van waarden binnen van die [ pdf.xml ](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) dossiers wordt gebruikt.

1. Bepaal een lezer door [ Magento\Framework\Config\Reader\Filesystem ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) klasse uit te breiden en de volgende parameters te herschrijven:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Voorbeeld:**

```php
<?php
/**
 * Copyright [first year code created] Adobe
 * All Rights Reserved.
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
>Als u liever uw eigen versie van de lezer maakt, kunt u dit doen door `\Magento\Framework\Config\ReaderInterface` te implementeren. Zie [ Magento_Analytics config reader ](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Nadat u de lezer hebt gedefinieerd, kunt u deze gebruiken voor het verzamelen, samenvoegen, valideren en omzetten van de configuratiebestanden in een interne arrayrepresentatie.

## Een configuratietype valideren

Elk configuratiedossier wordt bevestigd tegen een schema specifiek voor zijn configuratietype. Voorbeeld: gebeurtenissen die in eerdere Commerce-versies in `config.xml` zijn geconfigureerd, worden nu geconfigureerd in `events.xml` .

Configuratiebestanden kunnen zowel voor (optioneel) als na het samenvoegen van meerdere bestanden met hetzelfde configuratietype worden gevalideerd. Tenzij de validatieregels voor de afzonderlijke en samengevoegde bestanden identiek zijn, moet u twee schema&#39;s opgeven voor het valideren van de configuratiebestanden:

- Schema om een individu te valideren
- Schema om een samengevoegd bestand te valideren

Nieuwe configuratiebestanden moeten vergezeld gaan van XSD-validatieschema&#39;s. Een XML-configuratiebestand en het bijbehorende XSD-validatiebestand moeten dezelfde naam hebben.

Als u twee XSD-bestanden moet gebruiken voor één XML-bestand, moeten de namen van de schema&#39;s herkenbaar zijn en aan het XML-bestand zijn gekoppeld.
Als u een `events.xml` -bestand en een eerste `events.xsd` -bestand hebt, kunnen de XSD-bestanden voor het samengevoegde `events.xml` -bestand de naam `events_merged.xsd` krijgen.
Om ervoor te zorgen dat een XML-bestand wordt gevalideerd door het juiste XSD-bestand, moet u de URL (Uniform Resource Name) toevoegen aan het XSD-bestand in het XML-bestand. Bijvoorbeeld:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

Uw IDE kan uw configuratiedossiers zowel runtime als tijdens ontwikkeling bevestigen.
