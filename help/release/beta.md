---
title: Beta-releases
description: Leer meer over de bètareleases van Adobe Commerce en hoe u hieraan kunt deelnemen.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 4643c8392b6d92a2ccbbc2ec5b27d75c112d7521
workflow-type: tm+mt
source-wordcount: '1097'
ht-degree: 0%

---

# Adobe Commerce bèta-releases

bètaprogramma&#39;s van Adobe Commerce zijn een manier voor handelaren om toegang te krijgen tot pre-releasefuncties en -code, feedback te geven en de toekomst van Adobe Commerce te begeleiden. Er zijn twee typen bètaprogramma&#39;s:

- Openbare Beta: alle klanten en partners van Adobe Commerce hebben een openbaar bètaprogramma
- Private Beta: een particulier bètaprogramma vereist mogelijk goedkeuring op basis van kwalificatiecriteria voor deelname

>[!IMPORTANT]
>
>Beta-releases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de correcte werking of prestaties van de bètareleases en/of begeleidende documentatie of materialen. Functies en API&#39;s in bèta kunnen zonder voorafgaande kennisgeving worden gewijzigd. Bijgevolg is elk gebruik van de bètareleases volledig op eigen risico van de klant.

## Voordelen van deelname

Het krijgen van vroege toegang tot eigenschappen die de Adobe ontwikkelt verstrekt klanten en partners de capaciteit om terugkoppelen te verstrekken, productontwikkeling te vormen, en zich voor te bereiden om nieuwe mogelijkheden vóór algemene beschikbaarheid aan te nemen.

## Huidige Beta-programma&#39;s

Zie de volgende secties voor een lijst van actieve bètaprogramma&#39;s.

### Verbeterde zoekmogelijkheden voor Live zoeken (Public Beta)

Deze bèta steunt drie nieuwe mogelijkheden in [`productSearch` vraag ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/):

- **Gelaagd onderzoek** - Onderzoek binnen een andere onderzoekscontext - met dit vermogen, kunt u tot twee lagen van onderzoek naar uw onderzoeksvragen ondernemen. Bijvoorbeeld:

   - **Laag 1 onderzoek** - Onderzoek naar &quot;motor&quot;op &quot;product_attribute_1&quot;.
   - **Laag 2 onderzoek** - Onderzoek naar &quot;deelaantal 123&quot;op &quot;product_attribute_2&quot;. In dit voorbeeld wordt gezocht naar &quot;part number 123&quot; in de resultaten naar &quot;motor&quot;.

  Gelaagde zoekopdracht is beschikbaar voor zowel `startsWith` zoekindexatie als `contains` zoekindex, zoals hieronder wordt beschreven:

- **startWith onderzoeksindexatie** - Onderzoek gebruikend `startsWith` indexatie. Met deze nieuwe functie is het mogelijk:

   - Zoeken naar producten waarbij de kenmerkwaarde begint met een bepaalde tekenreeks.
   - Het vormen van &quot;beëindigt met&quot;onderzoek zodat kunnen de kopers naar producten zoeken waar de attributenwaarde met een bepaalde koord beëindigt. Om &quot;beëindigt met&quot;onderzoek toe te laten, moet het productattribuut in omgekeerde worden opgenomen en de API vraag zou ook een omgekeerde koord moeten zijn.

- **bevat onderzoeksindexatie** - Onderzoek een attribuut gebruikend bevat indexatie. Met deze nieuwe functie is het mogelijk:

   - Zoeken naar een query binnen een grotere tekenreeks. Als een winkel bijvoorbeeld het productnummer &quot;PE-123&quot; zoekt in de tekenreeks &quot;HAPE-123&quot;.

      - Nota: Dit onderzoekstype is verschillend van het bestaande [ uitdrukkingsonderzoek ](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#phrase), dat een autocomplete onderzoek uitvoert. Als de waarde van het kenmerk van het product bijvoorbeeld &quot;outdoorbroek&quot; is, retourneert een zoekopdracht met woordgroepen een reactie voor &quot;out pan&quot;, maar wordt geen reactie voor &quot;of ants&quot; geretourneerd. A contains search, echter, retourneert wel een reactie op ‘or ants’.

Deze nieuwe voorwaarden verbeteren het het filtreren van de onderzoeksvraag mechanisme om onderzoeksresultaten te raffineren. Deze nieuwe voorwaarden hebben geen invloed op de hoofdzoekquery. Om aan bèta deel te nemen, verzend een e-mailverzoek naar [ handel-opslag-diensten ](mailto:commerce-storefront-services@adobe.com).

Om Live Onderzoek bèta te installeren, zie de [ Levende gids van het Onderzoek ](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install#install-the-live-search-beta).

### Experience Manager Assets Integration for Commerce (Private Beta)

De Experience Manager Assets Integration for Commerce maakt een efficiënt beheer en levering mogelijk van een groot aantal productafbeeldingen van Experience Manager Assets naar Adobe Commerce, waarbij weinig of geen operationele inspanningen vereist zijn.

Belangrijkste kenmerken:

- Integratie met plug-and-play-technologie — Verstrek een Adobe die Experience Manager Assets en Adobe Commerce de mogelijkheid biedt om hun producten te laten focussen op wat het belangrijkst is, met lagere bedrijfskosten en verbeterde efficiëntie.

- Pas productafbeeldingen aan op schaal-Gebruik Experience Manager Assets om miljoenen productvariaties te genereren voor gepersonaliseerde Commerce-ervaringen met eenvoudige bewerkingsgereedschappen op basis van de gebruikersinterface, creatieve inhoud maken met behulp van Adobe Firefly en toegewezen workflows voor bedrijfsmiddelen om de consistentie van merken te garanderen. Als u tevreden bent met de middelen, kunt u deze naadloos leveren aan uw Commerce-winkeliers via de Experience Manager Assets Integration.

- Eenvoudig aan boord nemen - Vereenvoudig uw zakelijke instaptoegang met een configureerbaar synchronisatieproces dat volledige synchronisatie tussen de Experience Manager Assets-opslagplaats en de Commerce-catalogus mogelijk maakt.

- Flexibele matchingstrategie - De integratie omvat standaardalgoritmen voor middelenmatching op basis van product-SKU&#39;s die afbeeldingen synchroniseren tussen AEM Assets en Commerce, en deze is uitbreidbaar met Adobe Developer App Builder. Werk samen met uw partner van de oplossing om een aangepaste strategie voor het afstemmen van bedrijfsmiddelen bovenop de integratie te bouwen om elke structuur van opslagplaatsen voor middelenbeheer te kunnen gebruiken.

Om aan bèta deel te nemen, verzend een e-mailverzoek naar [ Shaun McCran ](mailto:mccran@adobe.com).

### IBM Sterling Order Management System Integration (Private Beta)

Met deze integratieversneller voor IBM Sterling Order Management kunnen Adobe Commerce-klanten aan de slag gaan met geavanceerde mogelijkheden voor orderbeheer, aangedreven door IBM Sterling OMS. Met deze integratie krijgen handelaren:

- Real-time zichtbaarheid in inventarisniveaus en nauwkeurige leveringsdatums voor uw klanten.
- Geautomatiseerde sourcing voor bestellingen op basis van configureerbare regels, zodat u uw uitvoeringsnetwerk en inventaris kunt optimaliseren.
- Een universele weergave van bestellingen tussen kanalen vanaf één dashboard, zodat uw supportteams de uitzonderlijke service kunnen leveren en uitzonderingen snel kunnen identificeren en afhandelen.
- Een getemplitste stroom van het terugkeerbeheer om terugkeerbeheer te vereenvoudigen.

Om aan deze bèta deel te nemen, verzend een e-mailverzoek naar [ sbieber@adobe.com ](mailto:sbieber@adobe.com).

### Gegevensverbinding en Audience Activation (Public Beta)

Uitgebreide gegevensuitwisseling tussen Adobe Commerce en Adobe Experience Platform voor krachtigere persoonlijke ervaringen. Met deze mogelijkheid kunnen handelaren:

- Commerce-klantprofielen delen
- Aangepaste kenmerken maken

Om aan deze bèta deel te nemen, verzend een e-mailverzoek naar [ DataConnection@adobe.com ](mailto:DataConnection@adobe.com).

### Adobe Commerce Foundation (Public Beta)

Elke bètaversie van Adobe Commerce Foundation bevat alle wijzigingen die tegen de geplande releasedatum aan de Adobe Commerce-kerncode zijn geleverd, inclusief maar niet beperkt tot de volgende functionele gebieden:

- Laatste beveiligingsoplossingen
- Prestatieverbeteringen
- GraphQL-verbeteringen
- Oplossingen voor algemene problemen met kwaliteit
- Communautaire bijdragen
- Veranderingen die worden vereist om verenigbaarheid met [ de diensten van Adobe Commerce ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/home.html) te steunen

#### Naamgevingsconventie en -schema

Adobe geeft gewoonlijk twee keer per jaar bètapatches uit.

Beta-releasepakketten hebben het achtervoegsel `-betaX` . Voor de release van Adobe Commerce 2.4.7 beta wordt bijvoorbeeld de volgende naamgevingsconventie gebruikt:

- `2.4.7-beta1`
- `2.4.7-beta2`

Zie het [ versieschema ](schedule.md) voor de lijst van aanstaande openbare bètaversiedata.


#### Toegang tot Beta-release

Adobe Commerce beta-releases worden op dezelfde manier gedistribueerd als elke andere Adobe Commerce patch-release: als Composer-metapakketten op `https://repo.magento.com` . De broncode is beschikbaar op [ GitHub ](https://github.com/magento/magento2).

Zie [ Snel begin van de Installatie Composer ](../installation/composer.md) voor meer details.

#### Melding van problemen

Adobe biedt de standaard Adobe Support Service voor bètareleases niet.

Om terugkoppelen met betrekking tot bètaversies voor te leggen, volg onze [ regelmatige kwestie rapporterend stroom ](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) op [ GitHub ](https://github.com/magento/magento2).

Onze interne teams zullen alle kritieke kwesties controleren die tegen de recentste bètaversie worden gemeld en hen voorrang geven om vóór de GA-releasedatum te worden opgelost.
