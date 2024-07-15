---
title: Overzicht van de cloudinfrastructuur
description: Meer informatie over de Adobe Commerce op cloudinfrastructuur.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# Overzicht

Adobe Commerce zelf biedt een van de populairste opties voor beheerde hosting voor Adobe Commerce op AWS. Adobe Commerce on cloud Infrastructure is een volledig beheerd geautomatiseerd hostplatform voor de Adobe Commerce-software.

Adobe Commerce on cloud Infrastructure is een platform-as-a-service (PaaS) die een snelle implementatie van volledig aanpasbare, veilige en schaalbare webwinkels mogelijk maakt in combinatie met toonaangevende hosting- en Managed Services-infrastructuren. Het biedt twee plannen met verschillende infrastructuur. De plannen van de Aanzet van Adobe Commerce [ ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects) zijn best geschikt voor kleinere opslag met minder ingewikkeldheid en kleinere catalogi. De plannen van Adobe Commerce [ Pro ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects) worden ontworpen voor grotere opslag met grotere ingewikkeldheid, grotere productcatalogi, of verkeer dat piekt. De Adobe bepaalt de aangewezen architectuur met input van partners.

Adobe Commerce is klaar voor de cloud met een volledig redundante hostinginfrastructuur voor meerdere cloud&#39;s die geoptimaliseerde prestaties, veerkracht en elastische schaalbaarheid biedt. U kunt uw handelsplatform op het netwerk van de inhoudslevering van Fastly efficiënt in werking stellen, en met New Relic voor controle en beheer kunt u uw opslagmilieu houden lopend regelmatig.

Adobe Commerce biedt alle voordelen van moderne cloud computing die het meest worden geassocieerd met SaaS-oplossingen, terwijl de flexibiliteit op het gebied van softwareaanpassing behouden blijft:

- Elastische schaalbaarheid
- Hoge veerkracht en beschikbaarheid
- PCI-compatibiliteit
- Wereldwijde beschikbaarheid en geautomatiseerde patches

![ Diagram die architecturale elementen van Adobe Commerce op wolkeninfrastructuur tonen ](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Voordelen

Andere voordelen van Adobe Commerce zijn:

- **Geoptimaliseerd voor Adobe Commerce**. Door Adobe Commerce ontwikkelde ontwikkelscripts en serviceconfiguratie zorgen ervoor dat elke instantie correct is afgestemd en geconfigureerd voor optimale bedrijfsprestaties.

- **Consistente, veilige versies**. Alle code plaatsingen zijn Git-gebaseerd voor consistentie en herhaalbaarheid, met read-only productiemilieu&#39;s voor geharde veiligheid.

- **Flexibiliteit voor partners**. Een volledige REST API en een scriptbare opdrachtregelinterface zorgen voor eenvoudige integratie met externe systemen en compatibiliteit met bestaande workflows voor codebeheer.

- **Flexibele plaatsingstoolset**. Snel een onbeperkt aantal omgevingen omhoog draaien, samenvoegen, klonen en naar wens afbreken voor ontwikkelingstaken, QA-tests of diagnose van productiekwesties.

- **Ononderbroken wolkenlevering**. Ga met vertrouwen van ontwikkeling aan UAT aan productie, op een ononderbroken manier over codetakken en ontwikkelingsteams.

## Diensten van derden

In dit gedeelte worden de belangrijkste services en tools van derden voor Adobe Commerce over infrastructuurprojecten in de cloud samengevat. Zie [ stapel van de Technologie ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html) in de _Gids van de Wolk_ voor meer details.

- **Snelle CDN**: Aangezien de klanten tot uw plaats en opslag toegang hebben, raken de verzoeken snel om caching pagina&#39;s sneller te laden. Fastly WAF verleent ook de beschermingsdienst DDoS.

- **New Relic**: Verstrekt een volledige mening van uw toepassingen en werkend milieu. Met New Relic kunt u belangrijke meetgegevens van mobiele en browsertoepassingen combineren met ondersteunende services, gegevensopslag en hosts, zodat u de prestaties holistisch kunt optimaliseren en elk initiatief tot een goed einde kunt brengen.

- **Composer**: Beheert gebiedsdelen en verbeteringen in Adobe Commerce en verstrekt context over de inbegrepen pakketten, wat de pakketten doen, en hoe zij samen passen.

- **Git**: Verstrekt broncodebeheer. Met Git kunt u lokale vertakkingen, handige staging gebieden en meerdere workflows met automatische build en implementatie voor efficiënte snelle ontwikkeling en continue implementatie.

- **Platform-as-a-Dienst (PaaS)**: Verstrekt een pre-provisioned infrastructuur die PHP, MySQL, Redis, [!DNL RabbitMQ], en OpenSearch of technologieën van de Elasticsearch omvat.

- **de wolk van AWS of van Azure het ontvangen**: Beheert de onderliggende infrastructuur-as-a-Dienst (IaaS), die een scalable en veilige milieu voor online verkoop en detailhandel aanbiedt.
