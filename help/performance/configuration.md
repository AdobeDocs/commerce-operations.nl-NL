---
title: Best practices voor configuratie
description: Leer meer over best practices voor configuratie om de Adobe Commerce-prestaties te optimaliseren. Ontdek instellingen en gereedschappen om de responstijd en -doorvoer te verbeteren.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: be13bed02b6307d0906e9c640962ee7d8c05d855
workflow-type: tm+mt
source-wordcount: '1407'
ht-degree: 0%

---

# Best practices voor configuratie

Commerce biedt veel instellingen en gereedschappen waarmee u de responstijd op de pagina&#39;s kunt verbeteren en een hogere doorvoer kunt garanderen.

## Cron Jobs

Alle asynchrone bewerkingen in [!DNL Commerce] worden uitgevoerd met de Linux-opdracht `cron` . Zie [&#x200B; uitsnijden vormen en in werking stellen &#x200B;](../configuration/cli/configure-cron-jobs.md) om het correct te vormen.

## Indexers

Een indexeerprogramma kan in de modus **[!UICONTROL Update on Save]** of **[!UICONTROL Update on Schedule]** worden uitgevoerd. De modus **[!UICONTROL Update on Save]** wordt direct geïndexeerd wanneer de catalogus of andere gegevens veranderen. In deze modus wordt ervan uitgegaan dat de update- en bladerbewerkingen in uw winkel weinig intensief zijn. Dit kan leiden tot aanzienlijke vertragingen en onbeschikbaarheid van gegevens tijdens hoge belastingen. Wij adviseren gebruikend **Update op Programma** voor prestatiesdoeleinden, omdat het informatie over gegevensupdates opslaat en indexatie door gedeelten op de achtergrond door een specifieke kroonbaan uitvoert. U kunt de modus van elke [!DNL Commerce] -index afzonderlijk wijzigen op de configuratiepagina **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** . De [!UICONTROL Customer Grid] -index moet altijd worden ingesteld op de **[!UICONTROL Update on Save]** -modus.

>[!TIP]
>
>Het opnieuw indexeren van MariaDB 10.4 en 10.6 kost meer tijd dan andere MariaDB- of [!DNL MySQL] -versies. Wij stellen voor het gebrek MariaDB configuratie het plaatsen te wijzigen, die in de [&#x200B; installatieeerste vereisten &#x200B;](../installation/prerequisites/database/mysql.md) wordt beschreven.

## Cursussen

Wanneer u de winkel in productie start, activeert u alle cache op de pagina **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** . We raden u aan [!DNL Varnish] te gebruiken, omdat dit een efficiënte cacheoplossing voor productiepagina&#39;s is.

## Asynchrone e-mailmeldingen

Als u de instelling voor &quot;Asynchrone e-mailmeldingen&quot; inschakelt, worden processen voor het uitchecken en bestellen van e-mailmeldingen naar de achtergrond verplaatst. Ga naar **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]** om deze functie in te schakelen. Zie [&#x200B; Verkoop E-mail &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/config/sales/sales-emails) in de _Gids van de Gebruiker Admin_ voor meer informatie.

## Asynchrone gegevensverwerking

Er kunnen momenten zijn dat intensieve verkoop op een winkel plaatsvindt terwijl [!DNL Commerce] intensieve verwerking van bestellingen uitvoert. U kunt [!DNL Commerce] zo configureren dat deze twee verkeerspatronen worden onderscheiden op databaseniveau, zodat er geen conflicten ontstaan tussen lees- en schrijfbewerkingen in de corresponderende tabellen. U kunt ordegegevens asynchroon opslaan en indexeren. Bestellingen worden tijdelijk opgeslagen en in bulk naar het Order Management-raster verplaatst zonder botsingen. U kunt deze optie activeren via **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]** . Zie [&#x200B; Geplande Updates van het Net &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing) in de _Gids van de Gebruiker Admin_ voor meer informatie.

>[!WARNING]
>
>Het **[!UICONTROL Developer]** lusje en de opties zijn slechts beschikbaar op [&#x200B; wijze van de Ontwikkelaar &#x200B;](../configuration/cli/set-mode.md). [&#x200B; Adobe Commerce op wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) steunt niet `Developer` wijze.

## Asynchrone configuratie opslaan

Voor projecten met een groot aantal opslag-vlakke configuraties, kan het bewaren van een opslagconfiguratie een ongeordende hoeveelheid tijd nemen of in een onderbreking resulteren. De _module Async Config_ laat asynchrone configuratie toe bewaart door een kroonbaan in werking te stellen die een consument gebruikt om sparen in een berichtrij te verwerken. AsyncConfig is **gehandicapt** door gebrek.

U kunt AsyncConfig toelaten gebruikend de bevel-lijn interface:

```bash
bin/magento setup:config:set --config-async 1
```

Met de opdracht `set` schrijft u het volgende naar het `app/etc/env.php` -bestand:

```conf
...
   'config' => [
       'async' => 1
   ]
```

Begin de volgende Consumenten beginnen de berichten in de rij op een eerste-in-eerste-uit basis te verwerken:

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Uitgestelde voorraadupdate

In tijden van intensieve verkoop, [!DNL Commerce] kan voorraadupdates met betrekking tot orden vertragen. Dit minimaliseert het aantal verrichtingen en versnelt het proces van de orderplaatsing. Deze optie is echter riskant en kan alleen worden gebruikt wanneer Backorders in de winkel worden geactiveerd, omdat deze optie tot negatieve voorraadhoeveelheden kan leiden. Deze optie kan de prestaties van de afhandelingsstromen aanzienlijk verbeteren voor winkels die hun voorraad gemakkelijk op aanvraag kunnen hervullen. Als u uitgestelde stock-updates op uw site wilt activeren, gaat u naar **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]** . Zie [&#x200B; Leidend Inventaris &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud) in de _Gids van de Gebruiker van Adobe Commerce_ voor meer informatie.

>[!INFO]
>
>Deze optie is alleen beschikbaar als **[!UICONTROL Backorder with any mode]** is geactiveerd.

>[!INFO]
>
>Deze optie werkt ook met [&#x200B; Asynchrone ordeplaatsing &#x200B;](high-throughput-order-processing.md#asynchronous-order-placement) in combinatie met [&#x200B; Inventory management &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html?lang=nl-NL).

## Optimalisatie-instellingen aan de clientzijde

Als u de responsiviteit van de winkel van uw [!DNL Commerce] -instantie wilt verbeteren, gaat u naar Beheer in de modus Standaard of Ontwikkelaar en wijzigt u de volgende instellingen:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Instellingengroep | Instelling | Waarde |
| ------------------- | -------------------------- | ------ |
| Rasterinstellingen | Asynchrone indexering | Inschakelen |
| CSS-instellingen | CSS-bestanden miniaturen | Ja |
| [!DNL JavaScript] Instellingen | [!DNL JavaScript] Bestanden miniaturen | Ja |
| [!DNL JavaScript] Instellingen | [!DNL JavaScript] Bundelen inschakelen | Ja |
| Sjablooninstellingen | Minify HTML | Ja |

>[!INFO]
>
>Het **[!UICONTROL Developer]** lusje en de opties zijn slechts beschikbaar op [&#x200B; wijze van de Ontwikkelaar &#x200B;](../configuration/cli/set-mode.md). [&#x200B; Adobe  [!DNL Commerce]  op wolkeninfrastructuur &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) steunt niet `Developer` wijze.

Wanneer u de optie **[!UICONTROL Enable [!DNL JavaScript] Bundling]** activeert, kunt u Commerce toestaan alle JS-bronnen samen te voegen tot één of een set bundels die in winkelpagina&#39;s worden geladen. Het bundelen van JS resulteert in minder verzoeken aan de server, wat paginaprestaties verbetert. Het helpt de browser JS middelen van het geheime voorgeheugen op de eerste vraag en hergebruik hen voor allen verder het doorbladeren. Deze optie brengt ook luie evaluatie, aangezien al JS als tekst wordt geladen. Het initieert analyse en evaluatie van code slechts nadat de specifieke acties op de pagina worden teweeggebracht. Nochtans, wordt dit het plaatsen niet geadviseerd voor opslag waar de eerste tijd van de paginading uiterst kritiek is, omdat al inhoud JS op de eerste vraag zal worden geladen.

>[!INFO]
>
>Zie [&#x200B; middeldossiers &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/optimize-css-js-files) voor meer informatie over het optimaliseren van CSS en Javascript optimaliseren.

### Bunduiteinden

* Wij adviseren dat u derdehulpmiddelen voor minificatie en bundeling (als [&#x200B; r.js &#x200B;](https://requirejs.org/)) gebruikt. [!DNL Commerce] ingebouwde mechanismen zijn niet optimaal en worden verzonden als alternatieven voor fallback.
* Het activeren van het HTTP/2-protocol kan een goed alternatief zijn voor het gebruik van JS-bundeling. Het protocol biedt veel van dezelfde voordelen. Het wordt door gebrek toegelaten in Adobe Commerce op de projecten van de wolkeninfrastructuur.
* We raden u niet aan vervangen instellingen te gebruiken, zoals het samenvoegen van JS- en CSS-bestanden, omdat deze alleen zijn ontworpen voor JS die synchroon zijn geladen in de HEAD-sectie van de pagina. Het gebruik van deze techniek kan het bundelen veroorzaken en requireJS logica om verkeerd te werken.

## Validatie van klantsegmenten

De handelaren die een groot aantal [&#x200B; klantensegmenten &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-admin/customers/segments/customer-segments) hebben kunnen significante prestatiesdegradatie met klantenacties, zoals klantenlogin ervaren en producten toevoegen aan de kar.

De acties van de klant brengen een bevestigingsproces voor klantensegmenten teweeg, wat prestatiesdegradatie kan veroorzaken. Standaard valideert Adobe Commerce elk segment in real-time om te bepalen welke klantsegmenten overeenkomen en welke niet.

Om prestatiesdegradatie te vermijden, kunt u de **[!UICONTROL Real-time Check if Customer is Matched by Segment]** optie van de systeemconfiguratie aan **Nr** plaatsen om klantensegmenten door één enkele gecombineerde voorwaardeSQL vraag te bevestigen.

Ga naar **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]** om deze optimalisatie in te schakelen.

Dit het plaatsen verbetert de prestaties van de bevestiging van het klantensegment als er vele klantensegmenten in het systeem zijn. Nochtans, werkt het niet met [&#x200B; gespleten gegevensbestand &#x200B;](../configuration/storage/multi-master.md) implementaties of wanneer er geen geregistreerde klanten zijn.

## Onderhoudsschema voor databases {#database}

We raden u aan periodieke databaseback-ups uit te voeren voor uw instanties van Staging en Productie. Vanwege de I/O-intensieve aard van back-upbewerkingen kunnen er langzamere back-ups en potentiële problemen optreden. Als databaseprocessen voor meerdere omgevingen tegelijkertijd worden uitgevoerd, kan dit mogelijk trager verlopen als gevolg van conflicten met beschikbare bronnen.

Voor betere prestaties, planning uw steunen om achtereenvolgens, één voor één, op off-piektijden te lopen. Met deze methode vermijdt u I/O-conflicten en verkort u de tijd om deze te voltooien, vooral voor kleinere exemplaren, grotere databases, enzovoort.

Bijvoorbeeld, adviseren wij het plannen van een steun van uw gegevensbestand van de Productie die door het Staging gegevensbestand wordt gevolgd wanneer uw opslag lagere bezoeken ontmoet.

## Limiet voor het aantal producten in het raster

Als u de prestaties van het productraster voor grote catalogi wilt verbeteren, kunt u het beste het aantal producten in het raster beperken met de instelling **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** voor de systeemconfiguratie.

Deze instelling voor systeemconfiguratie is standaard uitgeschakeld. Door het toe te laten, kunt u het aantal producten in het net tot een specifieke waarde beperken. **[!UICONTROL Records Limit]** is een aanpasbare instelling met de standaardwaarde `20000` .
Wanneer de instelling **[!UICONTROL Limit Number of Products in Grid]** is ingeschakeld en het aantal producten in het raster groter is dan de recordlimiet, wordt de beperkte verzameling records geretourneerd. Wanneer de limiet is bereikt, worden de totale gevonden records, het aantal geselecteerde records en de pagineringselementen verborgen achter de rasterkop.

Wanneer het totale aantal producten in het raster beperkt is, heeft dit geen invloed op de massaacties van het productraster. Het beïnvloedt slechts de presentatielaag van het productnet. Het raster bevat bijvoorbeeld een beperkt aantal `20000` -producten, de gebruiker klikt op **[!UICONTROL Select All]** , selecteert de **[!UICONTROL Update attributes]** -massaactie en werkt een aantal kenmerken bij. Hierdoor worden alle producten bijgewerkt, niet de beperkte verzameling van `20000` -records.

De beperking van het productraster is alleen van toepassing op productverzamelingen die worden gebruikt door UI-componenten. Deze beperking geldt dus niet voor alle productrasters. Alleen diegenen die `Magento\Catalog\Ui\DataProvider\Product\ProductCollection` gebruiken.
U kunt verzamelingen van productrasters alleen op de volgende pagina&#39;s beperken:

* Catalogusproductraster
* Raster Verwante producten/producten voor meerdere verkooppunten toevoegen
* Producten toevoegen aan bundelproduct
* Producten toevoegen aan productgroep
* Beheerderspagina voor bestelling maken

Als u niet wilt dat het productraster wordt beperkt, raden we u aan om filters nauwkeuriger te gebruiken zodat de resultatenverzameling minder items bevat dan **[!UICONTROL Records Limit]** .
