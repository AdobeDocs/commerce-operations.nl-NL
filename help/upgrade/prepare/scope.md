---
title: Omgaan met upgradebereik
description: Leer over achterwaartse onverenigbare veranderingen in een versie die de douanemodules van Adobe Commerce of derdeuitbreidingen zou kunnen beïnvloeden.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 9eeb0e3a1c75b25cc70b092d23f02ebfe355d6bd
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# Begrijp het werkingsgebied van verbetering

Herzie de [&#x200B; versienota&#39;s &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/notes/overview) om het werkingsgebied van een versie, met inbegrip van verhogingen, insectenmoeilijke situaties, en bekende kwesties te begrijpen die derde en douanemodules zouden kunnen beïnvloeden.

## Achteruit incompatibele wijzigingen

Adobe Commerce-releases kunnen niet-compatibele wijzigingen bevatten. Raadpleeg de volgende bronnen voor documentatie over achterwaartse en incompatibele wijzigingen:

- **[Belangrijke veranderingshoogtepunten &#x200B;](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/)** - Veranderingen die een belangrijk effect hebben en gedetailleerde verklaring en speciale instructies vereisen om ervoor te zorgen dat de derdemodules blijven werkend.
- **[kleine veranderingsverwijzing &#x200B;](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)** - de documentatie van de Verwijzing die van de codebasis wordt geproduceerd die minder belangrijke veranderingen in klassen, API lidmaatschap, gegevensbestand, gebiedsinjectie, interfaces, lay-outs, systeem, en XSD beschrijft.

## Extensies van derden

Het nieuwe verenigbaarheidsbeleid van Adobe Commerce Marketplace zorgt ervoor dat _alle_ vermelde uitbreidingen binnen 30 dagen na de GA datum compatibel met de recentste vrijgegeven versie zijn. Daarom is het belangrijk dat u extensies van derden waar mogelijk ophaalt via de Marketplace.

## Aangepaste modules

Alle douanemodules zouden tegen de doelversie moeten worden gecontroleerd u aan bevordert. Dit is het meest tijd- en middel-intensieve proces van een verbetering. Wanneer het evalueren van uw douanemodules, moet u achteruit-incompatibele veranderingen zoeken en zich van nieuwe praktijken, zoals controlemechanismedecompositie bewust zijn. U kunt meer over dit in de [&#x200B; versienota&#39;s &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/release/notes/overview) leren. Ook, zorg ervoor dat u [&#x200B; beste praktijken &#x200B;](https://developer.adobe.com/commerce/php/best-practices/extensions/) voor moduleontwikkeling volgt.

## [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] is een opdrachtregelprogramma dat uw instantie analyseert op mogelijke upgradeproblemen. Er wordt gecontroleerd op problemen tussen de huidige versie die u hebt geïnstalleerd en de versie waarnaar u wilt upgraden.

Het gebruik van dit hulpmiddel vermindert de inspanning die van uw team wordt vereist om het werkingsgebied en het effect van een verbetering te begrijpen. Het helpt u gemeenschappelijke codekwesties te vermijden wanneer bevordering en verstrekt duidelijke richting op hoe te om geïdentificeerde kwesties op te lossen. Het helpt ook om voorrang te geven aan de meest kritieke kwesties noodzakelijk om een succesvolle verbetering te verzekeren, die zowel tijd als kosten bespaart wanneer het bevorderen.

Zie de volgende secties om aan de slag te gaan met de [!DNL Upgrade Compatibility Tool] . Zie de [!DNL Upgrade Compatibility Tool] [&#x200B; gids &#x200B;](../upgrade-compatibility-tool/overview.md) voor meer technische details en geavanceerde gebruiksgevallen.

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
> Het argument `<dir>` is de map waarin uw codebasis is opgeslagen. Met de optie `-c` vergelijkt u de basiscode met de opgegeven versie.

Om de meest kritieke kwesties voor uw team te identificeren om te richten:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

U kunt deze opdracht ook gebruiken met de volgende opties:

- `--ignore-current-version-compatibility-issues` - Onderdrukt alle bekende kritieke kwesties, fouten, en waarschuwingen tegen uw huidige versie. Er worden alleen fouten weergegeven in de versie die u wilt upgraden.

- `--min-issue-level` - Staat u toe om het minimumniveau van de uitgave te plaatsen helpen slechts de belangrijkste kwesties met uw verbetering voorrang geven. De opties zijn waarschuwing, fout, en kritiek in stijgende orde van strengheid.

- `-m | [=MODULE-PATH]` - Als u alleen een bepaalde leverancier, module of zelfs map wilt analyseren, kunt u het pad ook als optie opgeven.

- `--vanilla-dir` - Hiermee kunt u de kerncode controleren op een niet-standaardimplementatie van functies of aanpassingen. Het is belangrijk dat deze van tevoren worden opgeruimd. Een vanilla-exemplaar van uw versie wordt automatisch ter referentie gedownload.

  >[!NOTE]
  >
  > Dit kan ook worden gedaan met de opdracht `core:code:changes` in het gereedschap).

### De uitvoer analyseren

[!DNL Upgrade Compatibility Tool] exporteert een JSON-bestand dat de betrokken code of modules, de ernst en een beschrijving van het probleem identificeert voor elk probleem dat het tegenkomt. Het output ook een samenvattingsrapport met een ingewikkeldheidsscore, die uw team toestaat ruwweg te begrijpen wat het aan verbetering aan de recentste versie vergt. Hoe lager de score voor complexiteit, hoe eenvoudiger het is om de upgrade uit te voeren.

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

Alle kwesties die het geïdentificeerde hulpmiddel zijn vermeld zijn in het rapport met specifieke foutencodes. Gebruik de [&#x200B; verwijzing van het foutenbericht &#x200B;](../upgrade-compatibility-tool/error-messages.md) om meer details over elke kwestie te krijgen. Adobe biedt ook suggesties om elk type probleem te verhelpen, zodat u de stappen voor het verhelpen van problemen kunt plannen.

Gebruik het rapport om te schatten hoeveel moeite het zal vergen om uw code voor de verbetering bij te werken. Op basis van uw ervaring kunt u een schatting maken van de vereiste inspanning om een upgrade uit te voeren op basis van het totale aantal geïdentificeerde problemen en de ernst van de problemen. Aangezien dit een opdrachtregelprogramma is, kunt u dit opnemen in automatische test- en codeselecties en de JSON-uitvoer gebruiken om uw rapporten te genereren.

Wij adviseren besparend de resultaten van elk verbeteringsproject zodat u toekomstige verbeteringsresultaten met vorige resultaten kunt vergelijken. Als u doorgaat met het gebruik, krijgt u vanaf het samenvattingsrapport dat door het hulpprogramma wordt geleverd, een goed inzicht in het inspanningsniveau dat nodig is om te upgraden naar de volgende versie.

Wij adviseren ook dat u regelmatig het hulpmiddel in werking stelt terwijl het werken aan de verbetering om zicht in uw vooruitgang te hebben. Het aantal problemen moet afnemen wanneer u deze verhelpt. Dit helpt uw team ook beslissen over de beste benadering om werk te verdelen.

[!DNL Upgrade Compatibility Tool] wordt verder verbeterd en in toekomstige versies worden functies zoals autofixes opgenomen om problemen zo snel mogelijk te verhelpen. De meest recente verbeteringen die in januari 2022 zijn geïntroduceerd, zijn onder andere compatibiliteitstests voor PHP 8.1 en HTML-visualisatiefuncties waarmee u snel gebieden kunt identificeren die meer moeite nodig hebben om te upgraden.
