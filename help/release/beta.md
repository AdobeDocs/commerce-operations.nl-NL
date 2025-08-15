---
title: Beta-releases
description: Leer meer over de bètareleases van Adobe Commerce en hoe u hieraan kunt deelnemen.
exl-id: 662cb061-995f-4e09-a2ef-9e607cc0000b
source-git-commit: 879160b11fe4840eb3af97c64f080deb5f002827
workflow-type: tm+mt
source-wordcount: '862'
ht-degree: 0%

---

# Adobe Commerce bèta-releases

bètaprogramma&#39;s van Adobe Commerce zijn een manier voor handelaren om toegang te krijgen tot pre-releasefuncties en -code, feedback te geven en de toekomst van Adobe Commerce te begeleiden. Er zijn twee typen bètaprogramma&#39;s:

- Openbare Beta: alle klanten en partners van Adobe Commerce hebben een openbaar bètaprogramma
- Private Beta: een particulier bètaprogramma vereist mogelijk goedkeuring op basis van kwalificatiecriteria voor deelname

>[!IMPORTANT]
>
>Beta-releases kunnen defecten bevatten en worden geleverd als &quot;AS IS&quot; zonder enige garantie. Adobe is niet verplicht om de bètareleases te onderhouden, te corrigeren, bij te werken, te wijzigen of anderszins te ondersteunen (via Adobe Support Services of anderszins). Klanten wordt aangeraden voorzichtig te zijn en op geen enkele wijze te vertrouwen op de correcte werking of prestaties van de bètareleases en/of begeleidende documentatie of materialen. Functies en API&#39;s in bèta kunnen zonder voorafgaande kennisgeving worden gewijzigd. Bijgevolg is elk gebruik van de bètareleases volledig op eigen risico van de klant.

## Voordelen van deelname

Het krijgen van vroege toegang tot eigenschappen die Adobe ontwikkelt verstrekt klanten en partners de capaciteit om terugkoppelen te verstrekken, productontwikkeling te vormen, en zich voor te bereiden om nieuwe mogelijkheden vóór algemene beschikbaarheid aan te nemen.

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

Om Live Onderzoek bèta te installeren, zie de [ Levende gids van het Onderzoek ](https://experienceleague.adobe.com/nl/docs/commerce/live-search/install#install-the-live-search-beta).

### IBM Sterling Order Management System Integration (Private Beta)

Met deze integratieversneller voor IBM Sterling Order Management kunnen Adobe Commerce-klanten aan de slag gaan met geavanceerde mogelijkheden voor orderbeheer, aangedreven door IBM Sterling OMS. Met deze integratie krijgen handelaren:

- Real-time zichtbaarheid in inventarisniveaus en nauwkeurige leveringsdatums voor uw klanten.
- Geautomatiseerde sourcing voor bestellingen op basis van configureerbare regels, zodat u uw uitvoeringsnetwerk en inventaris kunt optimaliseren.
- Een universele weergave van bestellingen tussen kanalen vanaf één dashboard, zodat uw supportteams de uitzonderlijke service kunnen leveren en uitzonderingen snel kunnen identificeren en afhandelen.
- Een getemplitste stroom van het terugkeerbeheer om terugkeerbeheer te vereenvoudigen.

Om aan deze bèta deel te nemen, verzend een e-mailverzoek naar [ sbieber@adobe.com ](mailto:sbieber@adobe.com).

### Adobe Commerce Foundation (Public Alpha/Beta)

Elke Adobe Commerce Foundation alfa- en bètaversie bevat alle wijzigingen die tegen de geplande releasedatum aan de Adobe Commerce core-code worden geleverd, inclusief maar niet beperkt tot de volgende functionele gebieden:

- Laatste beveiligingsoplossingen
- Prestatieverbeteringen
- GraphQL-verbeteringen
- Oplossingen voor algemene problemen met kwaliteit
- Communautaire bijdragen
- Veranderingen die worden vereist om verenigbaarheid met [ de diensten van Adobe Commerce ](https://experienceleague.adobe.com/nl/docs/commerce/user-guides/home) te steunen

#### Naamgevingsconventie en -schema

Adobe geeft doorgaans meerdere keren per jaar alfa- en bètapatches uit.

Alpha-releasepakketten hebben het achtervoegsel `-alphaX` . Voor de alfareleasepakketten van Adobe Commerce 2.4.7 wordt bijvoorbeeld de volgende naamgevingsconventie gebruikt:

- `2.4.7-alpha1`
- `2.4.7-alpha2`

Beta-releasepakketten hebben het achtervoegsel `-betaX` . Voor de release van Adobe Commerce 2.4.7 beta wordt bijvoorbeeld de volgende naamgevingsconventie gebruikt:

- `2.4.7-beta1`
- `2.4.7-beta2`

Zie het [ versieschema ](schedule.md) voor de lijst van aanstaande openbare alpha en bètaversiedata.

#### Geen toegang

Adobe Commerce alfa- en bètareleases worden op dezelfde manier gedistribueerd als elke andere Adobe Commerce-patchrelease: als Composer-metapakketten op `https://repo.magento.com` . De broncode is beschikbaar op [ GitHub ](https://github.com/magento/magento2).

Zie [ Snel begin van de Installatie Composer ](../installation/composer.md) voor meer details.

#### Melding van problemen

Adobe biedt de standaard Adobe Support Service niet voor alfa- en bètareleases.

Om terugkoppelen met betrekking tot alpha- en bètaversies voor te leggen, volg de [ regelmatige kwestie die stroom ](https://developer.adobe.com/commerce/contributor/guides/code-contributions/) op [ GitHub ](https://github.com/magento/magento2) meldt.

Adobe houdt toezicht op alle kritieke problemen die zijn gemeld in vergelijking met de nieuwste alfa- of bètaversie en geeft prioriteit aan deze problemen om te worden opgelost vóór de GA-releasedatum.
