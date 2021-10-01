---
title: Optimalisatie van AEM prestaties
description: Optimaliseer uw standaardAdobe Experience Manager configuratie om hoge ladingen op de Handel van de Adobe te steunen.
source-git-commit: 63f153365398c3ae7dc7e6214b67705c8a4c7686
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Optimalisatie van AEM

De AEM dispatcher is een reverse-proxy die helpt een omgeving te leveren die zowel snel als dynamisch is. Het werkt als deel van een statische server van HTML, zoals de Server van Apache HTTP, met het doel om (of &quot;caching&quot;) zoveel mogelijk van de plaatsinhoud op te slaan mogelijk, in de vorm van statische middelen. Deze aanpak is erop gericht de noodzaak om toegang te krijgen tot de AEM paginerendering en de dienst GraphQL van de Handel van de Adobe zoveel mogelijk te minimaliseren. Het resultaat van het bedienen van een groot deel van de pagina&#39;s als statische HTML, CSS en JS biedt prestatievoordelen voor gebruikers en vermindert de infrastructuurvereisten voor de omgeving. Pagina&#39;s of query&#39;s die waarschijnlijk van gebruiker tot gebruiker op dezelfde manier worden herhaald, moeten in cache worden geplaatst.

In de volgende secties wordt op hoog niveau het aanbevolen technische aandachtsgebied weergegeven dat moet worden herzien om een effectieve caching op AEM in een CIF/Adobe Commerce-omgeving mogelijk te maken.

## Op TTL gebaseerde caching op AEM verzenders

Het in cache plaatsen van zoveel mogelijk van de site op de verzenders is de beste manier voor elk AEM project. Als u op tijd gebaseerde cachevalidatie gebruikt, worden aan de serverzijde gerenderde CIF-pagina&#39;s voor een bepaalde beperkte tijd in cache opgeslagen. Nadat de vastgestelde tijd is verlopen, zal het volgende verzoek de pagina van de uitgever van de AEM en GrafiekQL van de Handel van de Adobe opnieuw bouwen en zal het in het berichtkergeheime voorgeheugen opnieuw opslaan tot de volgende ongeldigverklaring.

De het caching van TTL eigenschap kan in AEM met het gebruiken van de &quot;Dispatcher TTL&quot;component binnen het pakket van de Commons ACS AEM en het plaatsen van /enableTTL &quot;1&quot;in de dispatcher.any configuratiedossier worden gevormd.

Indien toegelaten, zal de verzender de antwoordkopballen van het achtereind evalueren, en als zij een Cachebeheer maximum-leeftijd of Verlopen datum bevatten, wordt een hulpdossier, leeg naast het geheim voorgeheugendossier gecreeerd, met wijzigingstijd gelijk aan de vervaldatum. Wanneer het cachebestand na de wijzigingstijd wordt opgevraagd, wordt het automatisch opnieuw opgevraagd vanaf de achtergrond. Dit geeft een effectief caching mechanisme dat geen handmatige interventie of onderhoud vereist, zodra de vertraging van de productupdate (TTL) is erkend en aanvaard door belanghebbenden uit het bedrijfsleven.

## Browser in cache plaatsen

De hierboven vermelde benadering van de verzender TTL zal verzoeken en lading op de uitgever zeer verminderen, nochtans zijn er sommige activa die zeer onwaarschijnlijk zullen veranderen en daarom kunnen zelfs de verzoeken aan de verzender worden verminderd door relevante dossiers plaatselijk op browser van een gebruiker in het voorgeheugen onder te brengen. Het logo van de site, dat op elke pagina van de site in de sitesjabloon wordt weergegeven, hoeft bijvoorbeeld niet telkens te worden aangevraagd bij de verzender. Dit kan in plaats daarvan worden opgeslagen in de browsercache van de gebruiker. De vermindering van bandbreedtevereisten voor elke paginading zou een grote invloed hebben op de reactiesnelheid van de site en de laadtijden van de pagina.

Het cachegeheugen op browserniveau wordt doorgaans gebruikt via &#39;Cache-Control&#39;: max-age=&quot; responsheader. De maxage-instelling vertelt de browser hoeveel seconden het bestand in cache moet plaatsen voordat wordt geprobeerd het opnieuw te valideren of opnieuw van de site te vragen. Dit concept cache max-age wordt meestal &#39;Cache Expiration&#39; of TTL (&#39;Time to Live&#39;) genoemd. Op grote schaal handelservaringen bieden - met Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

Enkele gebieden van een AEM/CIF/Adobe Commerce-site die in de browser van de client in cache kunnen worden geplaatst, zijn:

- Afbeeldingen (binnen de AEM sjabloon zelf, bijvoorbeeld het logo van de site en sjabloonontwerpafbeeldingen - catalogusproductafbeeldingen worden opgeroepen van de Adobe Commerce via Fastly, en deze afbeeldingen worden later besproken)
- HTML-bestanden (voor pagina&#39;s die niet vaak worden gewijzigd - pagina met voorwaarden enz.)
- CSS-bestanden
- Alle site-JavaScript-bestanden - inclusief CIF JavaScript-bestanden

## Verzendstatus, niveau en respijtperiode optimaliseren

De standaarddispatcherconfiguratie gebruikt /statfillevel &quot;0&quot;het plaatsen - dit betekent dat één enkel &quot;.stat&quot;dossier bij de wortel van htdocs folder (de folder van de documentwortel) wordt geplaatst. Als een wijziging in een pagina of bestand in AEM wordt aangebracht, wordt de wijzigingstijd van dit ene statusbestand bijgewerkt naar de tijd van de wijziging. Als de tijd nieuwer is dan wijzigingstijd van de bron, dan zal de verzender overwegen alle middelen ongeldig worden verklaard en om het even welk verder verzoek om een ongeldig gemaakt middel zal een vraag aan de Publish instantie teweegbrengen. Met deze instelling maakt elke activering de gehele cache ongeldig.

Voor om het even welke plaats, vooral handelsplaatsen met zware lading, zou dit een onnodige hoeveelheid lading op de AEM publiceren rij voor de volledige plaatsstructuur om met slechts één enkele paginaupdate ongeldig te worden.

In plaats daarvan, kan het statfileniveau plaatsen aan een hogere waarde worden gewijzigd, die aan de diepte van subdirectories in de htdocs folder van de folder van de documentwortel beantwoordt zodat wanneer een dossier dat op een bepaald niveau wordt gevestigd ongeldig wordt gemaakt dan slechts de dossiers op dat .stat folderniveau en hieronder worden bijgewerkt.

Bijvoorbeeld: Hier vindt u een sjabloon voor de productpagina op:

```
content/ecommerce/us/en/products/product-page.html
```

Elk mapniveau heeft een &quot;statusniveau&quot;, zoals weergegeven in de bovenstaande tabel.

| inhoud (docroot) | elektronische | ons | en | producten | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

Als u in dit geval de eigenschap statusLevel op de standaardwaarde &quot;0&quot; hebt ingesteld en de sjabloon product-page.html wordt bijgewerkt en geactiveerd waardoor een validatie wordt uitgevoerd, wordt elk .stat-bestand van docroot naar niveau 4 aangeraakt en worden bestanden ongeldig gemaakt, waardoor een nieuw verzoek van de AEM publicatieinstanties voor alle pagina&#39;s op de site (inclusief andere websites, landen en talen) van die ene wijziging wordt gedaan.

Als de eigenschap statusFileLevel echter is ingesteld op niveau 4 en de productpagina.html wordt gewijzigd, wordt alleen het .stat-bestand in de productmap voor die specifieke website/land/taal aangeraakt.

Houd er rekening mee dat het .stat-bestandsniveau niet op een te hoog niveau moet worden ingesteld. Een waarde van meer dan 20 kan van invloed zijn op de prestaties. Als u een bulkbestandsactivering uitvoert terwijl u een prestatietest uitvoert, krijgt u het juiste niveau waarop u het statusniveau wilt instellen.

Een andere verzender die plaatst om te optimaliseren wanneer het vormen van statfillevel is het plaatsen GracePeriod. Dit bepaalt het aantal seconden dat een autoongeldig gemaakte bron nog uit het geheime voorgeheugen kan worden gediend nadat de laatste activering plaatsvond. Auto-ongeldig gemaakte middelen worden ongeldig gemaakt door om het even welke activering (wanneer hun weg de verzender /invalidate sectie aanpast, en aan het niveau dat in het statfileslevel bezit wordt gespecificeerd). Het plaatsen van de alignmentPeriod aan 2 seconden kan worden gebruikt om een scenario te verhinderen waar de veelvoudige verzoeken voortdurend naar de uitgever worden verzonden, zelfs terwijl de uitgever nog bezig is de nieuwe pagina te bouwen.

>[!NOTE]
>
> Meer gedetailleerde lezing over dit onderwerp is beschikbaar in [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) bewaarplaats GitHub.

## CIF - GrafiekQL caching via componenten

Afzonderlijke componenten binnen AEM kunnen worden ingesteld op in cache plaatsen, wat betekent dat het GraphQL-verzoek aan Adobe
De handel wordt geroepen eens en dan verdere verzoeken, tot de gevormde tijdslimiet, worden teruggewonnen van het AEM geheime voorgeheugen en zou geen verdere lading op de Handel van de Adobe plaatsen. Voorbeelden zijn sitenavigatie op basis van een categoriestructuur die op elke pagina wordt weergegeven en opties binnen een beperkte zoekfunctionaliteit. Dit zijn slechts twee gebieden waarvoor bronintensieve query&#39;s op Adobe Commerce moeten worden uitgevoerd, maar die waarschijnlijk niet regelmatig zullen veranderen en daarom goede keuzes zijn voor caching. Op deze manier, bijvoorbeeld, zelfs wanneer een PDP of PLP door de uitgever worden herbouwd, zou het middel intensieve verzoek GraphQL voor de navigatiereeks niet de Handel van Adobe raken en kon uit het geheime voorgeheugen GraphQL op AEM CIF worden teruggewonnen.

Een voorbeeld hieronder is voor de navigatiecomponent om in het voorgeheugen onder te brengen omdat het de zelfde vraag GraphQL op alle pagina&#39;s in de plaats verzendt. In de onderstaande aanvraag worden de afgelopen 100 items gedurende 10 minuten in cache opgeslagen voor de navigatiestructuur:

```
venia/components/structure/navigation:true:100:600
```

In het onderstaande voorbeeld worden de afgelopen 100 beperkte zoekopties gedurende 1 uur in een zoekpagina opgeslagen:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

De aanvraag, inclusief alle aangepaste http-headers en -variabelen, moet exact overeenkomen om de cache te kunnen aanslaan en te voorkomen dat een aanroep van Adobe Commerce wordt herhaald. Hier moet worden opgemerkt dat er geen eenvoudige manier is om deze cache handmatig ongeldig te maken. Dit zou kunnen betekenen, daarom dat als een nieuwe categorie in de Handel van de Adobe wordt toegevoegd, het niet in de navigatie zou beginnen te verschijnen tot de vervaltijd die in het geheime voorgeheugen hierboven wordt geplaatst is verlopen en het verzoek GraphQL wordt verfrist. Hetzelfde geldt voor zoekfacetten. Gezien de prestatievoordelen die deze caching kan opleveren, is dit echter meestal een aanvaardbaar compromis.

De bovenstaande caching opties kunnen worden geplaatst gebruikend de AEM OSGi configuratieconsole in &quot;Cliënt GraphQL
Configuratie-fabriek&quot;. Elke ingang van de geheim voorgeheugenconfiguratie kan met het volgende formaat worden gespecificeerd:

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Hybride caching-cliënt kant GraphQL- verzoeken binnen caching dispatcherpagina&#39;s

Het is ook mogelijk om pagina&#39;s op een hybride manier in cache te plaatsen: het is mogelijk voor een CIF pagina om componenten te bevatten die altijd de recentste informatie van de Handel van de Adobe direct van browser van de klant zouden verzoeken. Dit kan handig zijn voor specifieke gebieden van de pagina in een sjabloon die belangrijk zijn om te worden bijgewerkt met real-time informatie: Productprijzen binnen een PDP, bijvoorbeeld. Wanneer de prijzen vaak veranderen toe te schrijven aan dynamische prijsaanpassing, kan die informatie worden gevormd om niet in het voorgeheugen ondergebracht op de verzender, eerder kunnen de prijzen cliënt-kant in browser van de klant van de Handel van de Adobe direct via GraphQL APIs met AEM CIF Webcomponenten worden gehaald.

Dit kan worden geconfigureerd via de instellingen voor AEM componenten. Voor Prijsinformatie op pagina&#39;s met productlijsten kunt u dit configureren in de sjabloon voor productlijsten, waarbij u de component met productlijsten op de pagina-instellingen selecteert en de optie &quot;Ladingsprijzen&quot; controleert. Hetzelfde geldt voor de voorraadniveaus.

Bovenstaande methoden mogen alleen worden gebruikt in het geval dat actuele en actuele informatie vereist is. In het voorbeeld hierboven met tarifering, kon het met bedrijfsbelanghebbenden worden overeengekomen om prijzen slechts dagelijks bij lage verkeerstijden bij te werken en geheim voorgeheugenspoelverrichting toen uit te voeren. Dit zou de behoefte aan de de informatieverzoeken van de prijsinformatie in real time en de verdere extra lading op de Handel van de Adobe wanneer het bouwen van elke pagina verwijderen die prijsinformatie toont.

## Niet-cacheable GraphQL-verzoeken

Specifieke dynamische gegevenscomponenten binnen pagina&#39;s zouden niet in het voorgeheugen ondergebracht moeten zijn en zullen altijd een vraag GraphQL aan de Handel van de Adobe, zoals voor het winkelwagentje en vraag door de controlepagina&#39;s vereisen. Deze informatie is specifiek voor een gebruiker en verandert voortdurend als gevolg van de activiteiten van de klant op de site, bijvoorbeeld door producten aan hun winkelwagentje toe te voegen.

De resultaten van de Vraag GraphQL zouden niet voor geregistreerde klanten in het voorgeheugen ondergebracht moeten worden als het ontwerp van de plaats verschillende reacties zou geven die op de rol van de gebruiker worden gebaseerd. U kunt bijvoorbeeld meerdere klantgroepen maken en verschillende productprijzen of een andere zichtbaarheid van de productcategorie voor elke groep instellen. Caching resultaten als deze kunnen klanten ertoe brengen om de prijzen van een andere klantengroep te zien of onjuiste categorieën te hebben tonen.

## Trackingparameters worden genegeerd bij AEM verzendercache

De plaatsen van de e-handel kunnen verkeer naar hun plaats drijven gebruikend PPC onderzoeksreclame of sociale media campagnes.

Als u deze media gebruikt, wordt een id voor bijhouden toegevoegd aan de uitgaande koppeling van dat platform. Facebook voegt bijvoorbeeld een Facebook Click ID (fbclid) toe aan de URL, Google Adverts voegt een Google Click ID (gclid) toe, zodat binnenkomende koppelingen naar uw AEM worden weergegeven zoals in het onderstaande voorbeeld:

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

Gclid en fbclid zullen met elke gebruiker veranderen die de reclame klikt, is dit voorgenomen voor het volgen doeleinden, maar met zijn standaardinstellingen, AEM zou elk verzoek als unieke pagina zien, die verzender zou omzeilen en onnodige extra lading op de uitgever en de Handel van de Adobe zou veroorzaken.

Tijdens een drukke gebeurtenis kan dit er zelfs toe leiden dat de AEM uitgevers overbelast raken en niet reageren. Wanneer een parameter is ingesteld om voor een pagina te worden genegeerd, wordt de pagina de eerste keer dat de pagina wordt opgevraagd, in de cache opgeslagen. Volgende aanvragen voor de pagina worden op de pagina in de cache geplaatst, ongeacht de waarde van de parameter in het verzoek.

>[!NOTE]
>
>Verder lezen over het belang van het instellen van `ignoreUrlParams` is beschikbaar in de [aem-dispatcher-experiments](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub-opslagplaats.

Het zou daarom moeten worden gevormd om alle parameters door gebrek in &quot;ignoreUrlParams&quot;te negeren, behalve waar een parameter van de GET wordt gebruikt die de structuur van HTML van een pagina zou veranderen. Een voorbeeld hiervan zou met een onderzoekspagina zijn waar de onderzoekstermijn in URL als parameter van de GET is - in dit geval zou u ignoreUrlParams dan manueel moeten vormen om parameters zoals gclid, fbclid en om het even welke andere het volgen parameters te negeren uw reclamekanalen gebruiken, verlatend de GET parameters die voor normale plaatsverrichtingen worden vereist onaangetast.

## Grenswaarden voor MPM-workers voor verzenders

De MPM-workers-instellingen zijn een geavanceerde Apache HTTP-serverconfiguratie die grondig moet worden getest om te worden geoptimaliseerd op basis van de beschikbare CPU en het RAM van de Dispatcher. Nochtans, in het werkingsgebied van dit whitepaper zouden wij suggereren dat ServerLimit en MaxRequestWorkers, tot een niveau zouden moeten worden verhoogd dat de beschikbare cpu en RAM van de server zouden steunen, en dan MinSpareThreads en MaxSpareThreads allebei worden verhoogd tot een niveau dat de MaxRequestWorkers aanpast.

Deze configuratie zou Apache HTTP op een &quot;volledige bereidheid plaatsen&quot;verlaten die een krachtige configuratie voor servers met significant RAM en veelvoudige cores van cpu is. Deze configuratie zal de best mogelijke reactietijden van Apache HTTP veroorzaken door blijvende open verbindingen te handhaven klaar om verzoeken te dienen en om het even welke vertraging in het paaien van nieuwe processen in reactie op plotselinge verkeerspieken, zoals tijdens flitsverkoop te verwijderen.
