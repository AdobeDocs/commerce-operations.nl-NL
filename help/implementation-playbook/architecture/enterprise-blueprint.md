---
title: Enterprise-verwijzingsarchitectuur
description: Leer hoe u Adobe Commerce implementeert met behulp van de nieuwste composable commerce technologie van de Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 8eab688ed98eb1b9fcf4fc25f90fe2bbf99c02d6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 0%

---

# Adobe Commerce Enterprise Reference Architectuur

Adobe Commerce is het ervaringsplatform dat op unieke wijze technische flexibiliteit combineert met gebruiksgemak, in dienst van het creëren van uitzonderlijke ervaringen die bedrijfsresultaten aansturen.

De handel is geëvolueerd om aan ondernemingsvereisten voor prestaties, schaal, en veiligheid te voldoen. Een moderne implementatieaanpak waarbij gebruik wordt gemaakt van de nieuwste samengestelde handelsoplossingen van de Adobe is van cruciaal belang voor het succes van het bedrijfsleven. Deze pagina beschrijft de moderne implementatiebenadering van de Handel in technische details.

Het volgende architectuurdiagram illustreert de gegevensstroom tussen Adobe Commerce en alle oplossingen van Adobe Experience Cloud.

![Architecturaal diagram dat toont hoe Adobe Commerce met Experience Cloud oplossingen verbindt](../../assets/playbooks/commerce-architecture-v2.svg){zoomable=&quot;yes&quot;}

>[!NOTE]
>
>De gegevensstromen op hoog niveau die in het diagram worden getoond zijn verenigbaar over de meeste ondernemingsimplementaties. De belangrijkste component die implementaties uniek kan maken, is de manier waarop u uw catalogus bouwt (vooral voor B2B). U moet uw catalogusarchitectuur zorgvuldig toewijzen aan de [Handelsweb-API&#39;s](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud Foundation

[Adobe Commerce over cloudinfrastructuur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) is de basis van uw implementatie van de Handel. Het biedt een [beveiligen](../../security-and-compliance/shared-responsibility.md) geautomatiseerd hostingplatform met een zelfservicebenadering voor het ontwikkelen, implementeren, bewaken en beheren van uw toepassing Commerce in een cloud-native omgeving.

Zie de volgende technische details van de cloudstichting:

- [**Schaalbare architectuur**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture)—Automatisch aangepaste capaciteit om stabiele, voorspelbare prestaties te behouden
- [**Meerdere omgevingen**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture)—Vooraf ingericht met PHP, MySQL (MariaDB), Redis, RabbitMQ en ondersteunde zoekmachinetechnologieën om uw site te ontwikkelen, te testen en te implementeren
- [**Configuratiebeheer**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview)—Aanpasbare dossiers van de omgevingsconfiguratie en bevel-lijn interface (CLI) om toepassingsmontages, routes te beheren, acties, en berichten te bouwen en op te stellen.
- [**Workflow op basis van git**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow)—Automatisch bouwen en implementeren na het doorvoeren van codewijzigingen voor snelle ontwikkeling en continue implementatie
- [**Ingebouwde waarneming**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance)—Hulpmiddelen die logboekgegevens van veelvoudige bronnen combineren om u te helpen de prestaties van uw plaats beheren en kwesties diagnostiseren
- [**Uitgebreide API-dekking**](https://developer.adobe.com/commerce/webapi/get-started/)—[GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) en [REST](https://developer.adobe.com/commerce/webapi/rest) API&#39;s voor de integratie van de kerntoepassing Handel met systemen van derden en de uitbreiding van de mogelijkheden van de Handel

## Integratie met Experience Cloud

Adobe Commerce integreert met alle oplossingen voor Experiencen Cloud om [gepersonaliseerde commerciële ervaringen op schaal](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu).

[Gegevensverbinding](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/overview) Hiermee krijgt u inzicht in het aankoopgedrag van uw klanten, zodat u via alle kanalen persoonlijke boodschappen kunt doen met andere Adobe Digital Experience-producten.

>[!NOTE]
>
>Zie [Blauwdrukken voor digitale beleving](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) voor meer technische details.


## Integratie met systemen van derden

Adobe biedt ontwikkelaars uitgebreide uitbreidingspunten en tools om toepassingen te maken die de kernmogelijkheden voor handel uitbreiden en handel met systemen van derden (zoals CRM&#39;s, ERPS en PIMS) integreren. Met deze gereedschappen worden de totale eigendomskosten van het platform als volgt verminderd:

- **Schaalbaarheid**—Toepassingen kunnen afzonderlijk van de kernsoftware worden geschaald, zodat u efficiënter werkt en upgrades eenvoudiger kunt uitvoeren.
- **Isolatie**- Een geïsoleerde omgeving houdt in dat ontwikkelaars hun extensies naar eigen goeddunken kunnen upgraden of wijzigen zonder op een kernrelease te vertrouwen.
- **Technologische onafhankelijkheid**- Ontwikkelaars kunnen kiezen welke technologiestapels en coderingstalen op hun behoeften zijn afgestemd.

Adobe biedt de volgende ontwikkelaarshulpmiddelen voor het bouwen van integratie en aanpassingen:

- [**API-net voor Adobe Developer App Builder**](https://developer.adobe.com/graphql-mesh-gateway/)—Coördineer en combineer veelvoudige API, GraphQL, REST, en andere bronnen in één, queryable eindpunt van GraphQL.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/)—Bouw en stel veilige en scalable Webtoepassingen op die de functionaliteit van de Handel uitbreiden en met derdeoplossingen integreren.
- [**Gebeurtenissen**](https://developer.adobe.com/commerce/extensibility/events/)—Gebruik aangepaste gebeurtenistriggers voor interactie met andere uitbreidbare ontwikkelingsprogramma&#39;s.
- [**Webhaken**](https://developer.adobe.com/commerce/extensibility/webhooks/)—Gebruik webhaken om automatisch interactie tussen de handel en systemen van derden te activeren.
- [**Admin UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/)—Pas en verbeter de Admin van de Handel met nieuwe pagina&#39;s en eigenschappen voor uw handelaren aan.

## Storefront-services

De Adobe verstrekt een rijke reeks intelligente, composable merchandizing diensten om u te helpen uw belangrijkste bedrijfsdoelstellingen steunen. Deze services bieden ook API&#39;s die essentieel zijn voor het optimaliseren van prestaties op schaal.

- [Live zoeken](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/overview)—Bied slimmere, snellere en relevante resultaten voor kopers met dit AI-zoekprogramma.
- [Product Recommendations](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/overview)—Voeg door AI gevoede aanbevelingen toe die op verkoopgedrag, populaire tendensen, productgelijkenis, en meer worden gebaseerd.
- [Catalogusservice](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/catalog-service/guide-overview)—Geef uw klanten een geoptimaliseerde productervaring terwijl het verhogen van prestaties, het verbeteren van scalability, en het verhogen van omzettingen.
- [Betalingsdiensten](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/payment-services/guide-overview)—De tevredenheid van klanten vergroten door verschillende betalingsmethoden aan te bieden, waaronder rentevrije betalingstermijnen, en één overzicht van betalingsverwerking, bestellingen en facturen.

## Hoofdloze winkel

Hoofdloze handel is API-eerste handel. Adobe Commerce heeft een volledig ontkoppelde architectuur die alle handelsdiensten en gegevens via een GraphQL API-laag biedt. Deze architectuur staat teams toe om hun frontends onafhankelijk van de kerntoepassing te ontwikkelen, die de behendigheid verstrekt om nieuwe aanraakpunten met nieuwe technologieën snel te bouwen en te testen.

Adobe biedt een moderne, toonloze, toonaangevende technologie die dezelfde voordelen en mogelijkheden biedt als [Edge Delivery Services](https://www.aem.live/home) met documentgebaseerde ontwerpfuncties, een prestatiegerelateerde architectuur en native experimenteren buiten de box. Het gebruikt de schaal en de prestaties van Adobe Commerce [winkeldiensten](#storefront-services) en flexibiliteit en gemak [drop-in componenten](https://experienceleague.adobe.com/developer/commerce/storefront/) om commerciële mogelijkheden te leveren.

