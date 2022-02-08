---
title: Overzicht van cloudinfrastructuur
description: Meer informatie over Adobe Commerce op cloudinfrastructuur.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---

# Overzicht

Adobe Commerce zelf biedt een van de populairste opties voor beheerde hosting voor Adobe Commerce op AWS. Adobe Commerce on cloud Infrastructure is een volledig beheerd geautomatiseerd hostplatform voor de Adobe Commerce-software.

Adobe Commerce on cloud Infrastructure is een platform-as-a-service (PaaS) die een snelle implementatie van volledig aanpasbare, veilige en schaalbare webwinkels mogelijk maakt in combinatie met een toonaangevende infrastructuur voor hosting en beheerde services. Het biedt twee plannen met verschillende infrastructuur. Adobe Commerce Starter is het meest geschikt voor kleinere winkels met minder complexiteit en kleinere catalogi. Adobe Commerce Pro is gebouwd voor grotere winkels met meer complexiteit, grotere productcatalogi of piekverkeer. Adobe Commerce bepaalt de juiste architectuur met inbreng van partners.

Adobe Commerce is klaar voor de cloud met een volledig redundante hostinginfrastructuur voor meerdere cloud&#39;s die geoptimaliseerde prestaties, veerkracht en elastische schaalbaarheid biedt. U kunt uw handelsplatform op het netwerk van de inhoudslevering van de Fastly efficiënt in werking stellen, en met Nieuw Relisch voor controle en beheer kunt u uw winkelmilieu houden regelmatig lopend.

Adobe Commerce biedt alle voordelen van moderne cloud computing die het meest worden geassocieerd met SaaS-oplossingen: elastische schaalbaarheid, hoge veerkracht en beschikbaarheid, PCI-compatibiliteit en wereldwijde beschikbaarheid en geautomatiseerde patching, terwijl de flexibiliteit in softwareaanpassing die onze handelaren nodig hebben, behouden blijft.

![Diagram met architecturale elementen van Adobe Commerce op cloudinfrastructuur](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Voordelen

Andere voordelen van Adobe Commerce zijn:

- **Geoptimaliseerd voor Adobe Commerce**. Door Adobe Commerce ontwikkelde ontwikkelscripts en serviceconfiguratie zorgen ervoor dat elke instantie correct is afgestemd en geconfigureerd voor optimale bedrijfsprestaties.

- **Consistente, veilige releases**. Alle code plaatsingen zijn Git-gebaseerd voor consistentie en herhaalbaarheid, met read-only productiemilieu&#39;s voor geharde veiligheid.

- **Flexibiliteit voor partners**. Een volledige REST API en een scriptable opdrachtregelinterface zorgen voor eenvoudige integratie met externe systemen en compatibiliteit met bestaande workflows voor codebeheer.

- **Flexibele implementatietoolset**. Snel een onbeperkt aantal omgevingen omhoog draaien, samenvoegen, klonen en naar wens afbreken voor ontwikkelingstaken, QA-tests of diagnose van productiekwesties.

- **Continue levering van wolken**. Ga met vertrouwen van ontwikkeling aan UAT aan productie, op een ononderbroken manier over codetakken en ontwikkelingsteams.

## Diensten van derden

Laten we ook eens kijken naar de software die de voordelen van Adobe Commerce werkelijkheid maakt.

![Diagram van Adobe Commerce op de technologiestapel voor cloudinfrastructuur](../../../assets/playbooks/cloud-tech-stack.svg)

- Fastly CDN: Wanneer klanten toegang krijgen tot uw site en winkels, kunnen ze sneller in cache geplaatste pagina&#39;s laden. Fastly WAF verleent ook de beschermingsdienst DDoS.

- Het nieuwe Relic geeft u een volledige mening van uw toepassingen en werkende milieu. Zo kunt u belangrijke metriek van mobiele en browsertoepassingen combineren met ondersteunende services, gegevensopslag en hosts, zodat u de prestaties holistisch kunt optimaliseren en elk initiatief tot een goed einde kunt brengen.

- Composer beheert afhankelijkheden en upgrades in Adobe Commerce en biedt context over de opgenomen pakketten, wat de pakketten doen en hoe ze bij elkaar passen.

- Git is uw code in repositories. Het maakt lokale vertakkingen, handige staging gebieden en meerdere workflows mogelijk met automatische build en implementatie voor efficiënte snelle ontwikkeling en doorlopende implementatie.

- Platform-as-a-Service (PaaS) verstrekt een pre-provisioned infrastructuur die PHP, MySQL, Redis, RabbitMQ, en Elasticsearch technologieën omvat.

- AWS of de wolk van Azure bedienen de onderliggende infrastructuur-as-a-Service (IaaS), die een scalable en veilige omgeving voor online verkoop en detailhandel aanbiedt.
