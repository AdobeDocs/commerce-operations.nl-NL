---
title: Best practices voor configuratie
description: Optimaliseer de reactietijd van uw Adobe Commerce- of Magento Open Source-implementatie met deze best practices.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---


# Best practices voor configuratie

De handel verstrekt vele montages en hulpmiddelen die u kunt gebruiken om reactietijd op de pagina&#39;s te verbeteren evenals hogere productie te verstrekken.

## Cron Jobs

Alle asynchrone bewerkingen in [!DNL Commerce] worden uitgevoerd met behulp van Linux `cron` gebruiken. Zie [Uitsnede configureren en uitvoeren](../configuration/cli/configure-cron-jobs.md) om het correct te vormen.

## Indexers

Een indexeerprogramma kan worden uitgevoerd in **[!UICONTROL Update on Save]** of **[!UICONTROL Update on Schedule]** in. De **[!UICONTROL Update on Save]** wordt onmiddellijk geïndexeerd wanneer uw catalogus of andere gegevens veranderen. In deze modus wordt ervan uitgegaan dat de update- en bladerbewerkingen in uw winkel weinig intensief zijn. Dit kan leiden tot aanzienlijke vertragingen en onbeschikbaarheid van gegevens tijdens hoge belastingen. We raden u aan **Bijwerken in schema** in productie, omdat het informatie over gegevensupdates opslaat en indexatie door gedeelten op de achtergrond door een specifieke kroonbaan uitvoert. U kunt de modus van elk [!DNL Commerce] indexeer afzonderlijk op de  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** configuratiepagina.

Het opnieuw indexeren van MariaDB 10.4 kost meer tijd dan andere MariaDB of [!DNL MySQL] versies. Als tussenoplossing, stellen wij voor om de standaardconfiguratie te wijzigen MariaDB en de volgende parameters te plaatsen:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## Cursussen

Wanneer u uw winkel in productie start, activeert u alle caches vanuit de **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** pagina. We raden u aan het gebruik van [!DNL Varnish], omdat dit een efficiënte cacheoplossing voor productiepagina is.

## Asynchrone e-mailmeldingen

Als u de instelling voor &quot;Asynchrone e-mailmeldingen&quot; inschakelt, worden processen voor het uitchecken en bestellen van e-mailmeldingen naar de achtergrond verplaatst. Ga naar **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Zie [Verkoop-e-mails](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) in de _Handboek Magento Open Source_ voor meer informatie .

## Asynchrone gegevensverwerking

Er kunnen momenten zijn dat intensieve verkoop op een winkel plaatsvindt op hetzelfde moment dat [!DNL Commerce] voert intensieve orderverwerking uit. U kunt configureren [!DNL Commerce] om deze twee verkeerspatronen op het gegevensbestandniveau te onderscheiden om conflicten tussen lees te vermijden en verrichtingen in de overeenkomstige lijsten te schrijven. U kunt ordegegevens asynchroon opslaan en indexeren. Orders worden in tijdelijke opslag geplaatst en in bulk naar het orderbeheerraster verplaatst zonder dat er conflicten optreden. U kunt deze optie activeren vanuit **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Zie [Geplande rasterupdates](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) in de _Handboek Magento Open Source_ voor meer informatie .

>[!WARNING]
>
>De **[!UICONTROL Developer]** tab en opties zijn alleen beschikbaar in [Modus Ontwikkelaar](../configuration/cli/set-mode.md). [Adobe Commerce over cloudinfrastructuur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) ondersteunt niet `Developer` in.

## Uitgestelde voorraadupdate

In tijden van intensieve verkoop [!DNL Commerce] kan voorraadupdates met betrekking tot orders uitstellen. Dit minimaliseert het aantal verrichtingen en versnelt het proces van de orderplaatsing. Deze optie is echter riskant en kan alleen worden gebruikt wanneer Backorders in de winkel worden geactiveerd, omdat deze optie tot negatieve voorraadhoeveelheden kan leiden. Deze optie kan de prestaties van de afhandelingsstromen aanzienlijk verbeteren voor winkels die hun voorraad gemakkelijk op aanvraag kunnen hervullen. Als u uitgestelde voorraadupdates op uw site wilt activeren, gaat u naar **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Zie [Inventaris beheren](https://docs.magento.com/user-guide/catalog/inventory.html) in de _Adobe Commerce-gebruikershandleiding_ voor meer informatie .

>[!INFO]
>
>Deze optie is alleen beschikbaar als **[!UICONTROL Backorder with any mode]** is geactiveerd.

## Optimalisatie-instellingen aan de clientzijde

Om de storefront reactiesnelheid van uw [!DNL Commerce] Ga bijvoorbeeld naar de modus Standaard of Ontwikkelaar en wijzig de volgende instellingen:

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
>De **[!UICONTROL Developer]** tab en opties zijn alleen beschikbaar in [Modus Ontwikkelaar](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] over cloudinfrastructuur](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) ondersteunt niet `Developer` in.

Wanneer u het dialoogvenster **[!UICONTROL Enable [!DNL JavaScript] Bundling]** toestaan, staat u de Handel toe om alle middelen JS in één of een reeks bundels samen te voegen die in storefront pagina&#39;s worden geladen. Het bundelen van JS resulteert in minder verzoeken aan de server, wat paginaprestaties verbetert. Het helpt de browser JS middelen van het geheime voorgeheugen op de eerste vraag ook en hergebruik hen voor al verder het doorbladeren. Deze optie brengt ook luie evaluatie, aangezien al JS als tekst wordt geladen. Het initieert analyse en evaluatie van code slechts nadat de specifieke acties op de pagina worden teweeggebracht. Nochtans, wordt dit het plaatsen niet geadviseerd voor opslag waar de eerste tijd van de paginading uiterst kritiek is, omdat al inhoud JS op de eerste vraag zal worden geladen.

>[!INFO]
>
>Zie [CSS- en Javascript-bestandsoptimalisatie op Adobe Commerce op cloudinfrastructuur en Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) in Adobe Commerce Help Center_ voor meer informatie over het optimaliseren van CSS en Javascript.

### Bunduiteinden

* Wij adviseren dat u derdehulpmiddelen voor minificatie en bundeling (zoals [r.js](https://requirejs.org/)). [!DNL Commerce] ingebouwde mechanismen zijn niet optimaal en worden verzonden als alternatieven voor alternatieven.
* Het activeren van het HTTP2-protocol kan een goed alternatief zijn voor het gebruik van JS-bundeling. Het protocol biedt vrijwel dezelfde voordelen.
* We raden u niet aan vervangen instellingen te gebruiken, zoals het samenvoegen van JS- en CSS-bestanden, omdat deze alleen zijn ontworpen voor JS die synchroon zijn geladen in de sectie HEAD van de pagina. Het gebruik van deze techniek kan het bundelen veroorzaken en requireJS logica om verkeerd te werken.

## Onderhoudsschema voor databases {#database}

We raden u aan periodieke databaseback-ups uit te voeren voor uw instanties van Staging en Productie. Vanwege de I/O-intensieve aard van back-upbewerkingen kunnen er langzamere back-ups en potentiële problemen optreden. Als databaseprocessen voor meerdere omgevingen tegelijkertijd worden uitgevoerd, kan dit mogelijk trager verlopen als gevolg van conflicten met beschikbare bronnen.

Voor betere prestaties, planning uw steunen om achtereenvolgens, één voor één, op off-piektijden te lopen. Met deze methode vermijdt u I/O-conflicten en verkort u de tijd om deze te voltooien, vooral voor kleinere exemplaren, grotere databases, enzovoort.

Bijvoorbeeld, adviseren wij het plannen van een steun van uw gegevensbestand van de Productie die door het Staging gegevensbestand wordt gevolgd wanneer uw opslag lagere bezoeken ontmoet.
