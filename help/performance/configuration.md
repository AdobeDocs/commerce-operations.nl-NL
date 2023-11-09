---
title: Best practices voor configuratie
description: Optimaliseer de responstijd van uw Adobe Commerce- of Magento Open Source-implementatie met deze best practices.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 3c53efdaedea075e288d262e247bc9c42b5a2432
workflow-type: tm+mt
source-wordcount: '1448'
ht-degree: 0%

---

# Best practices voor configuratie

De handel verstrekt vele montages en hulpmiddelen die u kunt gebruiken om reactietijd op de pagina&#39;s te verbeteren evenals hogere productie te verstrekken.

## Cron Jobs

Alle asynchrone bewerkingen in [!DNL Commerce] worden uitgevoerd met behulp van Linux `cron` gebruiken. Zie [Uitsnede configureren en uitvoeren](../configuration/cli/configure-cron-jobs.md) om het correct te vormen.

## Indexers

Een indexeerprogramma kan worden uitgevoerd in **[!UICONTROL Update on Save]** of **[!UICONTROL Update on Schedule]** -modus. De **[!UICONTROL Update on Save]** wordt onmiddellijk geïndexeerd wanneer uw catalogus of andere gegevens veranderen. In deze modus wordt ervan uitgegaan dat de update- en bladerbewerkingen in uw winkel weinig intensief zijn. Dit kan leiden tot aanzienlijke vertragingen en onbeschikbaarheid van gegevens tijdens hoge belastingen. We raden u aan **Bijwerken in schema** in productie, omdat het informatie over gegevensupdates opslaat en indexatie door gedeelten op de achtergrond door een specifieke kroonbaan uitvoert. U kunt de modus van elk [!DNL Commerce] indexeer afzonderlijk op de  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** configuratiepagina

>[!TIP]
>
>Het opnieuw indexeren van MariaDB 10.4 en 10.6 kost meer tijd dan andere MariaDB of [!DNL MySQL] versies. Wij stellen voor de standaard MariaDB-configuratie-instelling te wijzigen. Deze instelling wordt beschreven in het dialoogvenster [installatievereisten](../installation/prerequisites/database/mysql.md).

## Cursussen

Wanneer u uw winkel in productie start, activeert u alle caches vanuit de **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** pagina. We raden u aan het gebruik van [!DNL Varnish], omdat dit een efficiënte cacheoplossing voor productiepagina is.

## Asynchrone e-mailmeldingen

Als u de instelling voor &quot;Asynchrone e-mailmeldingen&quot; inschakelt, worden processen voor het uitchecken en bestellen van e-mailmeldingen naar de achtergrond verplaatst. Ga naar **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Zie [Verkoop-e-mails](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) in de _Gebruikershandleiding voor Magento Open Source_ voor meer informatie .

## Asynchrone gegevensverwerking

Er kunnen momenten zijn dat intensieve verkoop op een winkel plaatsvindt op hetzelfde moment dat [!DNL Commerce] voert intensieve orderverwerking uit. U kunt [!DNL Commerce] om deze twee verkeerspatronen op het gegevensbestandniveau te onderscheiden om conflicten tussen lees te vermijden en verrichtingen in de overeenkomstige lijsten te schrijven. U kunt ordegegevens asynchroon opslaan en indexeren. Orders worden in tijdelijke opslag geplaatst en in bulk naar het orderbeheerraster verplaatst zonder dat er conflicten optreden. U kunt deze optie activeren vanuit **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Zie [Geplande rasterupdates](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) in de _Gebruikershandleiding voor Magento Open Source_ voor meer informatie .

>[!WARNING]
>
>De **[!UICONTROL Developer]** tab en opties zijn alleen beschikbaar in [Modus Ontwikkelaar](../configuration/cli/set-mode.md). [Adobe Commerce over cloudinfrastructuur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) ondersteunt niet `Developer` -modus.

## Asynchrone configuratie opslaan [!BADGE 2.4.7-bèta]{type=Informative url="/help/release/release-notes/commerce/2-4-7.md" tooltip="Alleen beschikbaar in 2.4.7 bèta"}

Voor projecten met een groot aantal opslag-vlakke configuraties, kan het bewaren van een opslagconfiguratie een ongeordende hoeveelheid tijd nemen of in een onderbreking resulteren. De _Async Config_ de module laat asynchrone configuratiebesparingen door een hulpbaan toe in werking te stellen die een consument gebruikt om sparen in een berichtrij te verwerken. AsyncConfig is **uitgeschakeld** standaard.

U kunt AsyncConfig toelaten gebruikend de bevel-lijn interface:

```bash
bin/magento setup:config:set --config-async 1
```

De `set` opdracht schrijft het volgende naar de `app/etc/env.php` bestand:

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

In tijden van intensieve verkoop [!DNL Commerce] kan beursupdates met betrekking tot orders uitstellen. Dit minimaliseert het aantal verrichtingen en versnelt het proces van de orderplaatsing. Deze optie is echter riskant en kan alleen worden gebruikt wanneer Backorders in de winkel worden geactiveerd, omdat deze optie tot negatieve voorraadhoeveelheden kan leiden. Deze optie kan de prestaties van de afhandelingsstromen aanzienlijk verbeteren voor winkels die hun voorraad gemakkelijk op aanvraag kunnen hervullen. Als u uitgestelde voorraadupdates op uw site wilt activeren, gaat u naar **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Zie [Inventaris beheren](https://docs.magento.com/user-guide/catalog/inventory.html) in de _Adobe Commerce-gebruikershandleiding_ voor meer informatie .

>[!INFO]
>
>Deze optie is alleen beschikbaar als **[!UICONTROL Backorder with any mode]** is geactiveerd.

>[!INFO]
>
>Deze optie werkt ook met [Asynchrone orderplaatsing](high-throughput-order-processing.md#asynchronous-order-placement) in combinatie met [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Optimalisatie-instellingen aan de clientzijde

De responsiviteit van uw winkel verbeteren [!DNL Commerce] Ga bijvoorbeeld naar de modus Standaard of Ontwikkelaar en wijzig de volgende instellingen:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Instellingengroep | Instelling | Waarde |
| ------------------- | -------------------------- | ------ |
| Rasterinstellingen | Asynchrone indexering | Inschakelen |
| CSS-instellingen | CSS-bestanden miniaturen | Ja |
| [!DNL JavaScript] Instellingen | Minieren [!DNL JavaScript] Bestanden | Ja |
| [!DNL JavaScript] Instellingen | Inschakelen [!DNL JavaScript] Bundling | Ja |
| Sjablooninstellingen | Minify HTML | Ja |

>[!INFO]
>
>De **[!UICONTROL Developer]** tab en opties zijn alleen beschikbaar in [Modus Ontwikkelaar](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] over cloudinfrastructuur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) ondersteunt niet `Developer` -modus.

Wanneer u het dialoogvenster **[!UICONTROL Enable [!DNL JavaScript] Bundling]** toestaan, staat u de Handel toe om alle middelen JS in één of een reeks bundels samen te voegen die in storefront pagina&#39;s worden geladen. Het bundelen van JS resulteert in minder verzoeken aan de server, wat paginaprestaties verbetert. Het helpt de browser JS middelen van het geheime voorgeheugen op de eerste vraag en hergebruik hen voor allen verder het doorbladeren. Deze optie brengt ook luie evaluatie, aangezien al JS als tekst wordt geladen. Het initieert analyse en evaluatie van code slechts nadat de specifieke acties op de pagina worden teweeggebracht. Nochtans, wordt dit het plaatsen niet geadviseerd voor opslag waar de eerste tijd van de paginading uiterst kritiek is, omdat al inhoud JS op de eerste vraag zal worden geladen.

>[!INFO]
>
>Zie [CSS- en JavaScript-bestandsoptimalisatie op Adobe Commerce op cloudinfrastructuur en Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) in Adobe Commerce Help Center_ voor meer informatie over het optimaliseren van CSS en Javascript.

### Bunduiteinden

* Wij adviseren dat u derdehulpmiddelen voor minificatie en bundeling (zoals [r.js](https://requirejs.org/)). [!DNL Commerce] ingebouwde mechanismen zijn niet optimaal en worden verzonden als alternatieven voor alternatieven.
* Het activeren van het HTTP/2-protocol kan een goed alternatief zijn voor het gebruik van JS-bundeling. Het protocol biedt vrijwel dezelfde voordelen.
* We raden u niet aan vervangen instellingen te gebruiken, zoals het samenvoegen van JS- en CSS-bestanden, omdat deze alleen zijn ontworpen voor JS die synchroon zijn geladen in de sectie HEAD van de pagina. Het gebruik van deze techniek kan het bundelen veroorzaken en requireJS logica om verkeerd te werken.

## Validatie van klantsegmenten

Handelaren met een groot aantal [klantsegmenten](https://docs.magento.com/user-guide/marketing/customer-segments.html) kan aanzienlijke prestatievermindering ervaren met acties van klanten, zoals aanmeldingsgegevens van klanten en het toevoegen van producten aan het winkelwagentje.

De acties van de klant brengen een bevestigingsproces voor klantensegmenten teweeg, wat prestatiesdegradatie kan veroorzaken. Standaard valideert Adobe Commerce elk segment in real-time om te bepalen welke klantsegmenten overeenkomen en welke niet.

U voorkomt een verslechtering van de prestaties door de **[!UICONTROL Real-time Check if Customer is Matched by Segment]** systeemconfiguratieoptie voor **Nee** om klantensegmenten door één enkele gecombineerde voorwaardeSQL vraag te bevestigen.

Ga voor het inschakelen van deze optimalisatie naar **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Dit het plaatsen verbetert de prestaties van de bevestiging van het klantensegment als er vele klantensegmenten in het systeem zijn. Het werkt echter niet met [gesplitste database](../configuration/storage/multi-master.md) implementaties of wanneer er geen geregistreerde klanten zijn.

## Onderhoudsschema voor databases {#database}

We raden u aan periodieke databaseback-ups uit te voeren voor uw instanties van Staging en Productie. Vanwege de I/O-intensieve aard van back-upbewerkingen kunnen er langzamere back-ups en potentiële problemen optreden. Als databaseprocessen voor meerdere omgevingen tegelijkertijd worden uitgevoerd, kan dit mogelijk trager verlopen als gevolg van conflicten met beschikbare bronnen.

Voor betere prestaties, planning uw steunen om achtereenvolgens, één voor één, op off-piektijden te lopen. Met deze methode vermijdt u I/O-conflicten en verkort u de tijd om deze te voltooien, vooral voor kleinere exemplaren, grotere databases, enzovoort.

Bijvoorbeeld, adviseren wij het plannen van een steun van uw gegevensbestand van de Productie die door het Staging gegevensbestand wordt gevolgd wanneer uw opslag lagere bezoeken ontmoet.

## Limiet voor het aantal producten in het raster

Om de prestaties van het productnet voor grote catalogi te verbeteren, adviseren wij het beperken van het aantal producten in het net met **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** systeemconfiguratie-instelling.

Deze instelling voor systeemconfiguratie is standaard uitgeschakeld. Door het toe te laten, kunt u het aantal producten in het net tot een specifieke waarde beperken. **[!UICONTROL Records Limit]** is een aanpasbare instelling met een standaard minimumwaarde van `20000`.
Wanneer de **[!UICONTROL Limit Number of Products in Grid]** het plaatsen wordt toegelaten en het aantal producten in het net is groter dan de verslaggrens, dan is de beperkte inzameling van verslagen teruggekeerd. Wanneer de limiet is bereikt, worden de totale gevonden records, het aantal geselecteerde records en de pagineringselementen verborgen achter de rasterkop.

Wanneer het totale aantal producten in het raster beperkt is, heeft dit geen invloed op de massaacties van het productraster. Het beïnvloedt slechts de presentatielaag van het productnet. Er is bijvoorbeeld een beperkt aantal `20000` producten in het raster, klikt de gebruiker op **[!UICONTROL Select All]** selecteert u de **[!UICONTROL Update attributes]** massaactie, en werkt sommige attributen bij. Als gevolg hiervan worden alle producten bijgewerkt, niet de beperkte verzameling van `20000` records.

De beperking van het productraster is alleen van toepassing op productverzamelingen die worden gebruikt door UI-componenten. Deze beperking geldt dus niet voor alle productrasters. Alleen die welke `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
U kunt verzamelingen van productrasters alleen op de volgende pagina&#39;s beperken:

* Catalogusproductraster
* Raster Verwante producten/producten voor meerdere verkooppunten toevoegen
* Producten toevoegen aan bundelproduct
* Producten toevoegen aan productgroep
* Beheerderspagina voor bestelling maken

Als u niet wilt dat het productraster wordt beperkt, raden we u aan om filters nauwkeuriger te gebruiken zodat de resultatenverzameling minder items bevat dan **[!UICONTROL Records Limit]**.
