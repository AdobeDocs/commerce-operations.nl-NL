---
title: Enterprise-verwijzingsarchitectuur
description: Leer hoe u Adobe Commerce implementeert met behulp van Adobe, de nieuwste composable commerce technologie.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Adobe Commerce Enterprise Reference Architectuur

Adobe Commerce is het ervaringsplatform dat op unieke wijze technische flexibiliteit combineert met gebruiksgemak, in dienst van het creëren van uitzonderlijke ervaringen die bedrijfsresultaten aansturen.

Commerce is geëvolueerd om te voldoen aan de vereisten van de onderneming op het gebied van prestaties, schaal en beveiliging. Een moderne implementatieaanpak waarbij gebruik wordt gemaakt van de nieuwste composable handeloplossingen van Adobe is van cruciaal belang voor het succes van bedrijven. Op deze pagina wordt de moderne Commerce-implementatieaanpak in detail beschreven.

Het volgende architectuurdiagram illustreert de gegevensstroom tussen Adobe Commerce en alle oplossingen van Adobe Experience Cloud.

![ Architecturaal diagram dat toont hoe Adobe Commerce met de oplossingen van Experience Cloud ](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"} verbindt

>[!NOTE]
>
>De gegevensstromen op hoog niveau die in het diagram worden getoond zijn verenigbaar over de meeste ondernemingsimplementaties. De belangrijkste component die implementaties uniek kan maken, is de manier waarop u uw catalogus bouwt (vooral voor B2B). U zou uw catalogusarchitectuur aan het [ Web APIs van Commerce zorgvuldig in kaart moeten brengen ](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud Foundation

[ Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) is de stichting van uw implementatie van Commerce. Het verstrekt a [ veilige ](../../security-and-compliance/shared-responsibility.md) geautomatiseerde het ontvangen platform van een zelfbediening benadering van het bouwen, het opstellen, het controleren, en het beheren van uw toepassing van Commerce in een wolk-inheems milieu.

Zie de volgende technische details van de cloudstichting:

- [**Schaalde architectuur** ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) - past automatisch capaciteit aan om gestage, voorspelbare prestaties te handhaven
- [**Veelvoudige milieu&#39;s** ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) - pre-provisioned met PHP, MySQL (MariaDB), Redis, RabbitMQ, en de gesteunde technologieën van de onderzoeksmotor om uw plaats te ontwikkelen, te testen en op te stellen
- [**het beheer van de Configuratie** ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview) - Aanpasbare dossiers van de milieuconfiguratie en bevel-lijn interface (CLI) om toepassingsmontages, routes te beheren, acties, en berichten op te stellen.
- [**Git-based werkschema** ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow) - bouw en stel automatisch na het duwen van codeveranderingen voor snelle ontwikkeling en ononderbroken plaatsing op
- [**Ingebouwde observability** ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance) - Hulpmiddelen die logboekgegevens van veelvoudige bronnen combineren om u te helpen de prestaties van uw plaats beheren en kwesties diagnostiseren
- [**Uitgebreide API dekking** ](https://developer.adobe.com/commerce/webapi/get-started/) - [ GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/) en [ REST ](https://developer.adobe.com/commerce/webapi/rest) APIs voor het integreren van de toepassing van kernCommerce met derdesystemen en het uitbreiden van de mogelijkheden van Commerce

## Integratie met Experience Cloud

Adobe Commerce integreert met alle oplossingen van Experience Cloud om [ gepersonaliseerde handelservaringen op schaal ](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu) te leveren.

[ Verbinding van Gegevens ](https://experienceleague.adobe.com/en/docs/commerce/data-connection/overview) ontgrendelt inzichten over het kopen van uw klanten gedrag zodat u gepersonaliseerde het winkelen ervaringen over alle kanalen met andere producten van de Ervaring van Adobe Digital kunt tot stand brengen.

>[!NOTE]
>
>Zie de volgende bronnen voor meer informatie:
>
>- [ Verblueprints van de Digitale Ervaring ](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) voor meer technisch detail.
>- Zie [ Personaliserend de Ervaring van de Klant ](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization).


## Integratie met systemen van derden

Adobe biedt ontwikkelaars uitgebreide uitbreidingspunten en tools om toepassingen te maken die de kernmogelijkheden van Commerce uitbreiden en Commerce integreren met systemen van derden (zoals CRM&#39;s, ERPS en PIMS). Met deze gereedschappen worden de totale eigendomskosten van het platform als volgt verminderd:

- **Scalability** - De toepassingen kunnen afzonderlijk van de kernsoftware worden geschraapt, die voor grotere efficiency en vereenvoudigde verbeteringen toestaat.
- **Isolatie** - een geïsoleerd milieu betekent dat de ontwikkelaars hun uitbreidingen bij hun discretie kunnen bevorderen of wijzigen zonder op een kernversie te vertrouwen.
- **Technologische onafhankelijkheid** - de Ontwikkelaars kunnen kiezen welke technologiestapels en coderende talen die hun behoeften passen.

Adobe biedt de volgende ontwikkelaarsgereedschappen voor het maken van integratie- en aanpassingsprocessen:

- [**API Net voor Adobe Developer App Builder** ](https://developer.adobe.com/graphql-mesh-gateway/) - coördineer en combineer veelvoudige API, GraphQL, REST, en andere bronnen in één enkel, queryable eindpunt van GraphQL.
- [**App Builder** ](https://developer.adobe.com/app-builder/docs/overview/) - bouw en stel veilige en scalable Webtoepassingen op die de functionaliteit van Commerce uitbreiden en met derdeoplossingen integreren.
- [**Gebeurtenissen** ](https://developer.adobe.com/commerce/extensibility/events/) - de trekkers van de douanegebeurtenis van het Gebruik om met andere verlengbare ontwikkelingshulpmiddelen in wisselwerking te staan.
- [**Webhooks** ](https://developer.adobe.com/commerce/extensibility/webhooks/) - Gebruik webhooks om interacties tussen Commerce en derdesystemen automatisch teweeg te brengen.
- [**Admin UI SDK** ](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/) - pas en verbeter Commerce Admin met nieuwe pagina&#39;s en eigenschappen voor uw handelaren aan.
- [**Uitrusting van de Aanzet van de Integratie** ](https://developer.adobe.com/commerce/extensibility/starter-kit/) - versnelt uw backkoffice integratie met verwijzingsintegratie, onboarding manuscripten, en een gestandaardiseerde architectuur.

>[!NOTE]
>
>Zie [ de Moderne benadering: De efficiënte Rekbaarheid in Adobe Commerce ](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility).

## Storefront-services

Adobe biedt een uitgebreide reeks intelligente, composable merchandizing-services waarmee u uw belangrijkste bedrijfsdoelen kunt ondersteunen. Deze services bieden ook API&#39;s die essentieel zijn voor het optimaliseren van prestaties op schaal.

- [ Levend Onderzoek ](https://experienceleague.adobe.com/en/docs/commerce/live-search/overview) - lever slimmere, snellere en relevante resultaten voor kopers met dit AI-Gerichte onderzoekshulpmiddel.
- [ Aanbevelingen van het Product ](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/overview) - voeg op AI-Gebaseerde aanbevelingen toe die op verkoopgedrag, populaire tendensen, productgelijkenis, en meer worden gebaseerd.
- [ de Dienst van de Catalogus ](https://experienceleague.adobe.com/en/docs/commerce/catalog-service/guide-overview) - geef uw klanten een geoptimaliseerde productervaring terwijl het opvoeren van prestaties, verbeterend scalability, en verhogend omzettingen.
- [ - De klantentevredenheid van de 1} Aandrijving van de Betaling van de Diensten van de 1} - aandrijving door diverse betalingsmethodes, met inbegrip van rentevrije betalingstermijnen aan te bieden, en één enkele mening in betalingsverwerking, orden, en facturen.](https://experienceleague.adobe.com/en/docs/commerce/payment-services/guide-overview)

## Hoofdloze winkel

Hoofdloze handel is API-eerste handel. Adobe Commerce heeft een volledig ontkoppelde architectuur die alle handelsdiensten en gegevens via een GraphQL API-laag biedt. Deze architectuur staat teams toe om hun frontends onafhankelijk van de kerntoepassing te ontwikkelen, die de behendigheid verstrekt om nieuwe aanraakpunten met nieuwe technologieën snel te bouwen en te testen.

Adobe verstrekt een moderne headless storefront technologie die de zelfde voordelen en de mogelijkheden omvat die door [ Edge Delivery Services ](https://www.aem.live/home) met document-gebaseerde creatie, een prestaties-eerste architectuur, en uit-van-de-doos inheemse experimentatie worden geleverd. Het hefboomwerkingen de schaal en de prestaties van Adobe Commerce [ storefront diensten ](#storefront-services) en de flexibiliteit en het gemak van [ drop-in componenten ](https://experienceleague.adobe.com/developer/commerce/storefront/) om commerciële mogelijkheden te leveren.

