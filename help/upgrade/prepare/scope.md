---
title: Bereik voor upgrade
description: Leer over achterwaartse onverenigbare veranderingen in een versie die Adobe Commerce of Magento Open Source douanemodules of derdeuitbreidingen zou kunnen beïnvloeden.
source-git-commit: 682963fb66519097e54f14f2b84ed71528030054
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 0%

---


# Begrijp het werkingsgebied van verbetering

Controleer de [releaseopmerkingen](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) om het werkingsgebied van een versie, met inbegrip van verhogingen, insectenmoeilijke situaties, en bekende kwesties te begrijpen die derde en douanemodules zouden kunnen beïnvloeden.

## Achteruit incompatibele wijzigingen

Adobe Commerce- en Magento Open Source-releases kunnen niet-compatibele wijzigingen bevatten. Raadpleeg de volgende bronnen voor documentatie over achterwaartse en incompatibele wijzigingen:

- **[Belangrijke wijzigingsmarkeringen](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)**—Wijzigingen die een grote impact hebben en gedetailleerde uitleg en speciale instructies vereisen om ervoor te zorgen dat modules van derden blijven werken.
- **[Referentie kleine wijziging](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)**—Referentiedocumentatie die is gegenereerd vanuit de codebasis en die kleine wijzigingen beschrijft in klassen, API-lidmaatschap, database, afhankelijkheidsinjectie, interfaces, lay-outs, systeem en XSD.

## Extensies van derden

Het nieuwe compatibiliteitsbeleid van Adobe Commerce Marketplace zorgt ervoor dat _alles_ vermelde extensies binnen 30 dagen na de GA-datum compatibel zijn met de meest recente uitgebrachte versie. Daarom is het belangrijk dat u extensies van derden waar mogelijk ophaalt via de Marketplace.

## Aangepaste modules

Alle douanemodules zouden tegen de doelversie moeten worden gecontroleerd u aan bevordert. Dit is het meest tijd- en middel-intensieve proces van een verbetering. Wanneer het evalueren van uw douanemodules, moet u achteruit-incompatibele veranderingen zoeken en zich van nieuwe praktijken, zoals controlemechanismedecompositie bewust zijn. Meer informatie hierover vindt u in het gedeelte [releaseopmerkingen](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). Ook, zorg ervoor dat u volgt [best practices](https://developer.adobe.com/commerce/php/best-practices/extensions/) voor moduleontwikkeling.

## [!DNL Upgrade Compatibility Tool]

De [!DNL Upgrade Compatibility Tool] is een bevel-lijn hulpmiddel dat uw geval voor potentiële verbeteringskwesties analyseert. Er wordt gecontroleerd op problemen tussen de huidige versie die u hebt geïnstalleerd en de versie waarnaar u wilt upgraden.

Het gebruik van dit hulpmiddel vermindert de inspanning die van uw team wordt vereist om het werkingsgebied en het effect van een verbetering te begrijpen. Het helpt u gemeenschappelijke codekwesties te vermijden wanneer bevordering en verstrekt duidelijke richting op hoe te om geïdentificeerde kwesties op te lossen. Het helpt ook om voorrang te geven aan de meest kritieke kwesties noodzakelijk om een succesvolle verbetering te verzekeren, die zowel tijd als kosten bespaart wanneer het bevorderen.

Zie de volgende secties om aan de slag te gaan met de [!DNL Upgrade Compatibility Tool]. Zie de [!DNL Upgrade Compatibility Tool] [hulplijn](../upgrade-compatibility-tool/overview.md) voor meer technische details en gevallen van geavanceerd gebruik.

### Het gereedschap downloaden

Gebruik Composer om het gereedschap te downloaden. Hiervoor is PHP 7.3 of hoger vereist, ten minste 2 GB RAM, Node.js (als u de compatibiliteit met GraphQL controleert) en een Adobe Commerce-licentie.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Het gereedschap uitvoeren

Om uw exemplaar te analyseren en op fouten, waarschuwingen, en kritieke kwesties te controleren:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> De `<dir>` argument is de folder waar uw codebasis wordt opgeslagen. De `-c` vergelijkt uw codebasis met de gespecificeerde versie.

Om de meest kritieke kwesties voor uw team te identificeren om te richten:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

U kunt deze opdracht ook gebruiken met de volgende opties:

- `--ignore-current-version-compatibility-issues`—Onderdrukt alle bekende kritieke kwesties, fouten, en waarschuwingen tegen uw huidige versie. Er worden alleen fouten weergegeven in de versie die u wilt upgraden.

- `--min-issue-level`—Staat u toe om het minimumniveau van de uitgave te plaatsen helpen slechts de belangrijkste kwesties met uw verbetering voorrang geven. De opties zijn waarschuwing, fout, en kritiek in stijgende orde van strengheid.

- `-m | [=MODULE-PATH]`—Als u alleen een bepaalde leverancier, module of zelfs map wilt analyseren, kunt u het pad ook als optie opgeven.

- `--vanilla-dir`—Staat u toe om kerncode voor om het even welke niet standaardimplementatie van eigenschappen of aanpassingen te controleren. Het is belangrijk dat deze van tevoren worden opgeruimd. Een vanilla-exemplaar van uw versie wordt automatisch ter referentie gedownload.

   >[!NOTE]
   >
   > Dit kan ook gebeuren met de `core:code:changes` in het gereedschap).

### De uitvoer analyseren

De [!DNL Upgrade Compatibility Tool] Hiermee exporteert u een JSON-bestand waarin de desbetreffende code of modules, de ernst en een beschrijving van het probleem worden aangegeven voor elk probleem dat het tegenkomt. Het output ook een samenvattingsrapport met een ingewikkeldheidsscore, die uw team toestaat ruwweg te begrijpen wat het aan verbetering aan de recentste versie vergt. Hoe lager de score voor complexiteit, hoe eenvoudiger het is om de upgrade uit te voeren.

De volgende output toont een voorbeeld samenvattingsrapport:

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### Tips en advies

Alle kwesties die het geïdentificeerde hulpmiddel zijn vermeld zijn in het rapport met specifieke foutencodes. Gebruik de [error message reference](../upgrade-compatibility-tool/error-messages.md) voor meer informatie over elk onderwerp. Adobe geeft ook suggesties om elk type probleem te verhelpen, zodat u uw verholpen kunt plannen.

Gebruik het rapport om te schatten hoeveel moeite het zal vergen om uw code voor de verbetering bij te werken. Op basis van uw ervaring kunt u een schatting maken van de vereiste inspanning om een upgrade uit te voeren op basis van het totale aantal geïdentificeerde problemen en de ernst van de problemen. Aangezien dit een opdrachtregelprogramma is, kunt u dit opnemen in automatische test- en codeselecties en de JSON-uitvoer gebruiken om uw rapporten te genereren.

Wij adviseren besparend de resultaten van elk verbeteringsproject zodat u toekomstige verbeteringsresultaten met vorige resultaten kunt vergelijken. Als u doorgaat met het gebruik, krijgt u vanaf het samenvattingsrapport dat door het hulpprogramma wordt geleverd, een goed inzicht in het inspanningsniveau dat nodig is om te upgraden naar de volgende versie.

Wij adviseren ook dat u regelmatig het hulpmiddel in werking stelt terwijl het werken aan de verbetering om zicht in uw vooruitgang te hebben. Het aantal problemen moet afnemen wanneer u deze verhelpt. Dit helpt uw team ook beslissen over de beste benadering om werk te verdelen.

De [!DNL Upgrade Compatibility Tool] wordt verder verbeterd en in toekomstige versies worden functies zoals autofixes opgenomen om problemen zo snel mogelijk te verhelpen. De meest recente verbeteringen die in januari 2022 zijn geïntroduceerd, zijn onder andere compatibiliteitstests en HTML-visualisatiefuncties waarmee u snel gebieden kunt identificeren die meer moeite nodig hebben om te upgraden.
