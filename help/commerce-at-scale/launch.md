---
title: Tips voor het testen van prestaties
description: Leer hoe u KPI's instelt voor het starten van uw Adobe Commerce- en Adobe Experience Manager-oplossing.
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Tips voor het testen van prestaties

Om de doeltreffendheid van alle hierboven vermelde wijzigingen te evalueren, moeten grondige prestatietests worden uitgevoerd voordat u live gaat en voordat u toekomstige grote implementaties in uw productieomgeving uitvoert. Bij het plannen van het testen van de belasting, is het belangrijk om echt het verkeer van de consument zoveel mogelijk te simuleren.

De meest bronintensieve gebieden van de plaats van AEM/CIF/Adobe Commerce zijn die die niet cacheable zoals het controleproces en plaatsonderzoek zijn. Statische, en daarom cacheable, paginanavigatie zoals voor de Pagina&#39;s van het Detail van de Productie (PDP&#39;s) en de Pagina&#39;s van de Lijst van het Product (PLP&#39;s) maken het grootste deel van het verkeer aan een e-commercesite in het algemeen uit en daarom zouden de manuscripten en de scenario&#39;s in de test dat moeten weerspiegelen om de grenzen van het platform te meten.

Als u één script hebt dat wordt uitgevoerd voor uw laadtest en dat zonder wachttijd tussen de stappen door de site navigeert, en dat ook altijd het uitcheckproces voltooit, geeft dit geen betrouwbare indicatie van de limieten van het platform, aangezien dat niet het geval is bij een levensecht scenario.

Het bepalen van KPIs zou de eerste stap in uw plan van de prestatietest moeten zijn: definieert u de metriek die u tijdens de eerste test kunt testen, maar meet deze vervolgens opnieuw in de toekomst en op terugkerende basis nadat de site actief is. Hierdoor kunt u de prestaties van de site bijhouden in de loop van de tijd - voor en na de introductie. Voorbeeld-KPI&#39;s die moeten worden gedefinieerd, zijn:

- Gemiddelde responstijd - tijd tot eerste byte of laatste byte
- Latentie
- Bytes/s (Througput)
- Foutfrequentie
- Orders per uur
- Paginaweergaven per uur
- Unieke gebruikers per uur (gelijktijdige kopers)

## Jmeterrichtlijnen

De volgende richtlijnen op hoog niveau voor Jmeter moeten in overweging worden genomen bij het ontwikkelen van uw AEM/CIF/Adobe Commerce-belastingstest:

- Splits uw manuscript in configureerbare scenario&#39;s, die, bijvoorbeeld zouden moeten behandelen:
   - Startpagina openen
   - Categoriepagina openen (PLP)
   - Eenvoudige producten (PDP) weergeven - 2 lussen binnen elke herhaling
   - Configureerbare Producten van de mening - 2 lijnen binnen elke herhaling
      - Stel de stappen hierboven bijvoorbeeld in op 60% van het verkeer
   - Zoeken in producten
      - Stel bijvoorbeeld het zoeken in de catalogus in op 37% van het verkeer
   - Winkelwagentje en Afhandeling
      - Bijvoorbeeld, zou een gebruiker die de Kar en het controlegedeelte van het manuscript voltooit aan een industrie standaardtarief van de de plaatsomzetting van de elektronische handel van rond 3% moeten in gebreke blijven
      - Aangezien de controlestroom uncached en gewoonlijk een middel intensieve verrichting is, zou het plaatsen van een onrealistisch hoog cijfer voor de aantallen mensen die orden voltooien tegenover het aantal plaatsbrowsers een onbetrouwbaar resultaat voor het volume van verkeer geven uw plaats kon behandelen.
- Reinig alle caches vóór elke testrun:
   - De cache van de AEM-verzender moet volledig worden schoongemaakt
   - Adobe Commerce Fastly en internal cache moeten volledig worden leeggemaakt en schoongemaakt - dit kan via de cachebesturing in Adobe Commerce-beheer.
- Neem een hellingperiode op in de Jmeter-test: Als er geen oplaadperiode is ingesteld, neemt het verkeer niet geleidelijk toe en kan de site geen van de vaak bezochte pagina&#39;s en onderdelen van de pagina in cache opslaan. In het echte leven, zou het ongebruikelijk zijn voor al piekverkeer om op een volledig uncached plaats op precies de zelfde tijd aan te komen, daarom zou een hellingperiode in de testmanuscripten van Jmeter moeten worden omvat om het geheime voorgeheugen toe te staan om op te bouwen zoals op een echte e-commerce plaats zou gebeuren.
- Een &quot;Wacht tijd&quot;tussen elke stap binnen een herhaling zou moeten worden gebruikt - in feite, zou een gebruiker niet onmiddellijk naar de volgende pagina op de plaats tijdens hun reis springen - er zou een wachttijd zijn terwijl de gebruiker de pagina leest en op hun volgende actie beslist.
- Door de thread-groepen oneindig in te stellen op een lus, maar voor een ingestelde tijd van x (bijvoorbeeld 60 minuten), wordt een herhaalbare test uitgevoerd met mediane responstijden tot vergelijkbaar met vorige testrun. Dit betekent dat er na de oplaadperiode van de set het doelaantal virtuele gebruikers is dat tegelijkertijd wordt uitgevoerd en dat dit gedurende de tijd van de set-lus zal duren.
- De mediane tijd moet worden gebruikt om een verbetering/afname van de gemiddelde responstijd te bereiken, niet gemiddeld. Als er verschillende randresultaten zijn die veel langer duren dan de andere resultaten, dan zou dit het gemiddelde resultaat scheeftrekken, maar wat we willen in de responstijd van de eindgebruiker voor de meeste gebruikers, die geschikter is voor de mediane maatregel.
- Ingesloten bronnen worden niet standaard in jmeter verzameld (bijvoorbeeld JS, CSS en andere bronnen die worden gedownload wanneer een echte gebruiker de pagina bezoekt). Dit kan worden toegelaten, maar slechts voor het domein u test - de externe middelvraag zou nog moeten worden uitgesloten (b.v. wij willen geen reactietijden van de extern ontvangen diensten, bijvoorbeeld omvatten. google analytics code , omdat we er geen controle over hebben ) .
- De Manager van het Geheime voorgeheugen van HTTP zou moeten worden toegelaten, dit toelaat Jmeter om paginagedeelten tijdens een reis als echte reis van de gebruiker tijdens hun doorbladeren van de website op hun eigen browser in het voorgeheugen onder te brengen. Tijdens hun reis door de site zou de browser van de gebruiker de bijbehorende ingesloten bronnen slechts één keer downloaden en deze zouden dan in de cache van de browser van de gebruiker worden geplaatst. Als dezelfde gebruiker enige tijd na zijn oorspronkelijke bezoek terugkeert naar de site, kan het ook nog steeds de cache zijn dat die elementen in de cache worden opgeslagen.
- Listeners moeten binnen de eigenlijke laadtestrun (bijvoorbeeld &quot;View Results Tree&quot; en &quot;Aggregate Report&quot;) worden gehouden. Het opnemen van deze gegevens in de niet-GUI-testrun voor werkelijke belasting kan van invloed zijn op de prestatieresultaten die door Jmeter worden gerapporteerd, aangezien de bronnen tijdens de echte testrun worden gebruikt om de rapporten te genereren. Deze listeners zijn verwijderd uit het testscript dat moet worden vervangen door een JTL-resultatenbestand dat vervolgens kan worden verwerkt met de functie Report Dashboard van Jmeter.
- Een doelreactietijd voor geëvalueerd zodat de &quot;Apdex score&quot;van het dashboard rapport als snelle manier kan worden gebruikt om het effect van veranderingen op prestaties tussen testlooppas te meten. De Apdex-score is gebaseerd op het feit dat een bepaalde hoeveelheid mensen de site binnen een aanvaardbare tijd kan openen. Als de reactietijd een bepaalde &quot;frustrerende&quot;hoeveelheid overschrijdt, vermindert dit de score. De tijden kunnen worden geplaatst gebruikend de &quot;apdex_specified_threshold&quot;en &quot;apdex_tolerated_threshold&quot;parameters.
- Plaats een doel &quot;Orders per uur&quot;metrisch om aan bedrijfsgebruikers voor te stellen, niet een Virtuele telling van de Gebruiker. &quot;Virtuele gebruikers&quot; kunnen een complex onderwerp zijn om te begrijpen wat in de praktijk de test meet. Door het tarief van de plaatsomzetting, orden per uur, gemiddelde tijd te berekenen een gebruiker op de plaats doorbrengt en tijd tussen elke paginading denkt, kunnen de industrie standaardberekeningen worden gebruikt om verschillende ladingstest scenario&#39;s voor te stellen die op orden per te bereiken uur worden gebaseerd.
- Tot slot zou uw Jmeter testserver op een server geografisch dichtbij moeten worden in werking gesteld waar het grootste deel van uw gebruikersverkeer uit komt en waar uw wolkeninfrastructuur wordt ontvangen - hopelijk zouden deze het zelfde zijn.
