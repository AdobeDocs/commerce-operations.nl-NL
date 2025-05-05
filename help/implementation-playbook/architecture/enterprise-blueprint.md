---
title: Referentiearchitectuur voor ondernemingen
description: Leer hoe je Adobe Commerce implementeert met behulp van de nieuwste composable commerce-technologie van Adobe.
feature: App Builder, Cloud, GraphQL, Integration, Paas, Saas
exl-id: d066ab43-20e2-4e0b-8348-0c52d6a7ac8a
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 0%

---

# Adobe Commerce Enterprise referentiearchitectuur

Adobe Commerce is het ervaringsgestuurde platform dat technische flexibiliteit op unieke wijze combineert met gebruiksgemak, allemaal in dienst van het creëren van uitzonderlijke ervaringen die de bedrijfsresultaten stimuleren.

Commerce is geëvolueerd om te voldoen aan de eisen van ondernemingen op het gebied van prestaties, schaal en beveiliging. Het toepassen van een moderne implementatieaanpak die gebruikmaakt van de nieuwste composable commerce-oplossingen van Adobe is van cruciaal belang voor het succes van ondernemingen. Op deze pagina wordt de moderne Commerce-implementatieaanpak in detail beschreven.

Het volgende architectuurdiagram illustreert de gegevensstroom tussen Adobe Commerce en alle oplossingen van Adobe Experience Cloud.

![ Architecturaal diagram dat toont hoe Adobe Commerce met de oplossingen van Experience Cloud ](../../assets/playbooks/commerce-architecture-v3.svg){zoomable="yes"} verbindt

>[!NOTE]
>
>De gegevensstromen op hoog niveau die in het diagram worden getoond zijn verenigbaar over de meeste ondernemingsimplementaties. De belangrijkste component die implementaties uniek kan maken, is de manier waarop u uw catalogus bouwt (vooral voor B2B). U zou uw catalogusarchitectuur aan het [ Web APIs van Commerce zorgvuldig in kaart moeten brengen ](https://developer.adobe.com/commerce/webapi/get-started/).

## Cloud Foundation

[Adobe Commerce op cloudinfrastructuur](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/overview) vormt de basis van je Commerce-implementatie. Het verstrekt a [ veilige ](../../security-and-compliance/shared-responsibility.md) geautomatiseerde het ontvangen platform van een zelfbediening benadering van het bouwen, het opstellen, het controleren, en het beheren van uw toepassing van Commerce in een wolk-inheems milieu.

Zie de volgende technische details van de cloudstichting:

- [**Schaalde architectuur** ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture) - past automatisch capaciteit aan om gestage, voorspelbare prestaties te handhaven
- [**Veelvoudige milieu&#39;s** ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-architecture) - pre-provisioned met PHP, MySQL (MariaDB), Redis, RabbitMQ, en de gesteunde technologieën van de onderzoeksmotor om uw plaats te ontwikkelen, te testen en op te stellen
- [**het beheer van de Configuratie** ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/overview) - Aanpasbare dossiers van de milieuconfiguratie en bevel-lijn interface (CLI) om toepassingsmontages, routes te beheren, acties, en berichten op te stellen.
- [**Git-gebaseerde workflow**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow): automatisch bouwen en implementeren na het pushen van codewijzigingen voor snelle ontwikkeling en continue implementatie
- [**Ingebouwde waarneembaarheid**](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/monitor/performance): tools die loggegevens uit meerdere bronnen combineren om u te helpen de prestaties van uw site te beheren en problemen te diagnosticeren
- [**Uitgebreide API-dekking**](https://developer.adobe.com/commerce/webapi/get-started/):[ GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) en [REST](https://developer.adobe.com/commerce/webapi/rest) API&#39;s voor het integreren van de kern van de Commerce-applicatie met systemen van derden en het uitbreiden van Commerce-mogelijkheden

## Integratie met Experience Cloud

Adobe Commerce kan worden geïntegreerd met alle Experience Cloud-oplossingen om gepersonaliseerde commerce-ervaringen op schaal[&#128279;](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/customers-menu/personalize-scale#customers-menu) te bieden.

[Data Connection geeft inzicht in het koopgedrag van je shoppers, zodat je met andere Adobe Digital Experience-producten](https://experienceleague.adobe.com/en/docs/commerce/data-connection/overview) via alle kanalen gepersonaliseerde winkelervaringen kunt creëren.

>[!NOTE]
>
>Zie de volgende bronnen voor meer informatie:
>
>- [ Verblueprints van de Digitale Ervaring ](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/overview) voor meer technisch detail.
>- Zie [ Personaliserend de Ervaring van de Klant ](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/personalization).


## Integratie met systemen van derden

Adobe biedt ontwikkelaars uitgebreide uitbreidingspunten en tools om toepassingen te maken die de kernmogelijkheden van Commerce uitbreiden en Commerce integreren met systemen van derden (zoals CRM&#39;s, ERPS en PIMS). Deze tools verlagen uw totale eigendomskosten van het platform op de volgende manieren:

- **Scalability** - De toepassingen kunnen afzonderlijk van de kernsoftware worden geschraapt, die voor grotere efficiency en vereenvoudigde verbeteringen toestaat.
- **Isolatie** - een geïsoleerd milieu betekent dat de ontwikkelaars hun uitbreidingen bij hun discretie kunnen bevorderen of wijzigen zonder op een kernversie te vertrouwen.
- **Technologische onafhankelijkheid** - de Ontwikkelaars kunnen kiezen welke technologiestapels en coderende talen die hun behoeften passen.

Adobe biedt de volgende ontwikkelaarsgereedschappen voor het maken van integratie- en aanpassingsprocessen:

- [**API Net voor Adobe Developer App Builder** ](https://developer.adobe.com/graphql-mesh-gateway/) - coördineer en combineer veelvoudige API, GraphQL, REST, en andere bronnen in één enkel, queryable eindpunt van GraphQL.
- [**App Builder**](https://developer.adobe.com/app-builder/docs/overview/): bouw en implementeer veilige en schaalbare webapplicaties die de Commerce-functionaliteit uitbreiden en integreren met oplossingen van derden.
- [**Gebeurtenissen**](https://developer.adobe.com/commerce/extensibility/events/): Gebruik aangepaste gebeurtenistriggers om te communiceren met andere uitbreidbare ontwikkeltools.
- [**Webhooks**](https://developer.adobe.com/commerce/extensibility/webhooks/): Gebruik webhooks om automatisch interacties tussen Commerce en systemen van derden te activeren.
- [**Admin UI SDK**](https://developer.adobe.com/commerce/extensibility/admin-ui-sdk/): Pas de Commerce Admin aan en verbeter deze met nieuwe pagina&#39;s en functies voor uw verkopers.
- [**Integration Starter Kit**](https://developer.adobe.com/commerce/extensibility/starter-kit/)—Versnel uw backoffice-integraties met referentie-integraties, onboarding-scripts en een gestandaardiseerde architectuur.

>[!NOTE]
>
>Zie [De moderne aanpak: effectieve uitbreidbaarheid in Adobe Commerce](https://experienceleague.adobe.com/en/docs/events/the-skill-exchange-recordings/commerce/aug2024/extensibility).

## Diensten voor de etalage

Adobe biedt een uitgebreide set intelligente, samenstelbare merchandisingservices om je te helpen je belangrijkste bedrijfsdoelen te ondersteunen. Deze services bieden ook API&#39;s die essentieel zijn voor het optimaliseren van prestaties op schaal.

- [Live zoeken](https://experienceleague.adobe.com/en/docs/commerce/live-search/overview): lever slimmere, snellere en relevante resultaten voor shoppers met deze AI-gestuurde zoektool.
- [Productaanbevelingen](https://experienceleague.adobe.com/en/docs/commerce/product-recommendations/overview): voeg AI-gestuurde aanbevelingen toe op basis van shopper gedrag, populaire trends, productgelijkenis en meer.
- [ de Dienst van de Catalogus ](https://experienceleague.adobe.com/en/docs/commerce/catalog-service/guide-overview) - geef uw klanten een geoptimaliseerde productervaring terwijl het opvoeren van prestaties, verbeterend scalability, en verhogend omzettingen.
- [&#128279;](https://experienceleague.adobe.com/en/docs/commerce/payment-services/guide-overview) - De klantentevredenheid van de 1&rbrace; Aandrijving van de Betaling van de Diensten van de 1&rbrace; - aandrijving door diverse betalingsmethodes, met inbegrip van rentevrije betalingstermijnen aan te bieden, en één enkele mening in betalingsverwerking, orden, en facturen.

## Hoofdloze winkel

Hoofdloze handel is API-eerste handel. Adobe Commerce heeft een volledig ontkoppelde architectuur die alle handelsdiensten en gegevens via een GraphQL API-laag biedt. Deze architectuur staat teams toe om hun frontends onafhankelijk van de kerntoepassing te ontwikkelen, die de behendigheid verstrekt om nieuwe aanraakpunten met nieuwe technologieën snel te bouwen en te testen.

Adobe verstrekt een moderne headless storefront technologie die de zelfde voordelen en de mogelijkheden omvat die door [ Edge Delivery Services ](https://www.aem.live/home) met document-gebaseerde creatie, een prestaties-eerste architectuur, en uit-van-de-doos inheemse experimentatie worden geleverd. Het hefboomwerkingen de schaal en de prestaties van Adobe Commerce [ storefront diensten ](#storefront-services) en de flexibiliteit en het gemak van [ drop-in componenten ](https://experienceleague.adobe.com/developer/commerce/storefront/) om commerciële mogelijkheden te leveren.

