---
title: Hoofdloze Adobe Commerce-architectuur
description: Leer hoe de hoofdloze architectuur van Adobe Commerce uniek is.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Headless Adobe Commerce Architecture

Het voordeel van de architectuur van de Handel van Adobe is dat het geen alles-of-niets voorstel is en een handelaar de juiste mengeling van oplossingen voor hun zaken kan vinden. Ze kunnen een PWA Studio-aangedreven PWA maken voor hun primaire siteervaring of Adobe Experience Manager gebruiken als de laag voor complexe klantritten, en tegelijk een aangepast front maken om te experimenteren met nieuwe aanraakpunten. Geen ander platform kan de tijd aan marktvoordelen en de flexibiliteit aanpassen die Adobe Commerce met zijn headless architectuur aanbiedt.

![Diagram met een Adobe Commerce-opslagarchitectuur zonder kop](../../../assets/playbooks/headless-storefront-architecture.svg)

Elke aanpak sluit elkaar niet uit. Klanten kunnen hun eigen front-end (head) maken, PWA Studio gebruiken voor web/mobiele ervaringen en/of Adobe Experience Manager gebruiken voor het glas (in een volledige of hybride implementatie).

De Handel van Adobe heeft altijd voor hoofdloze plaatsingen met REST APIs toegestaan. Terwijl REST krachtig is, met name voor bulkverwerking, als het op hoofdloos aankomt, laten GraphQL APIs snellere ontwikkeling door een intuïtieve ontwikkelaarservaring toe, grotere flexibiliteit door voor veranderingen toe te staan die geen invloed op bestaande APIs hebben, en betere prestaties door de hoeveelheid gegevens te minimaliseren die aan slechts precies wordt teruggewonnen wat nodig is.

GraphQL is een industriestandaard voor presterende APIs, die door veel van de hoogste elektronische handelsplatforms wordt gebruikt. Dat is een goede zaak, omdat dit betekent dat het een bewezen oplossing is en dat er deskundigheid bestaat op de markt.

Terwijl de Handel van Adobe een gekoppelde opslag als optie heeft, is het geenszins vereist dat een handelaar die Adobe Handel erfenis vooraf gebruikt. A merchant can take advantage of Adobe Commerce’s best-in-class commerce services to handle the backend business processes and, using our storefront APIs, integrate their own decoupled storefront to drive the frontend experience.

Laten we nu eens kijken naar de verschillende opties zonder kop.

## PWA Studio

The first is a progressive web application built with PWA Studio. Een deel hiervan wordt mogelijk gemaakt door het feit dat een PWA een koploze winkel is die los staat van de commerciële achtergrond. With PWA Studio, merchants can build high performing, reliable, and cost effective PWAs on top of Adobe Commerce to deliver best-in-class web experiences, both on mobile and desktop. As time goes on, this will overtake the coupled storefront as the default option.

De meeste handelaren begrijpen de richting die de industrie volgt met betrekking tot PWA en veel potentiële blokkers worden snel weggenomen.

Week in week, groeit het aantal partners bouwend deskundigheid in PWA Studio en wij hebben een versnelend aantal klantenlanceringen. The most recent update to PWA Studio included extensibility that will help make significant progress in compatibility with ADobe Commerce Marketplace extensions.

Veel handelaren hebben het gevoel dat ze niet klaar zijn voor krantenloze PWA, omdat ze veel vertrouwen op ontwikkelaars nodig hebben. Een van de grote voordelen van zowel de handelstoepassing als het hoofd dat door de Adobe Commerce is ontwikkeld, is dat deze de compatibiliteit tussen de verschillende handelscapaciteiten bevordert.

In order to make PWAs more accessible and easier to manage for our merchants, we empower business users to manage day-to-day content changes, create new landing pages, and more using Page Builder. Deze twee krachtige mogelijkheden samen laten snelheid toe om over alle apparaten en ervaringen op de markt te brengen.

## Adobe Experience Manager

Een krachtige combinatie voor uw behoeften op het gebied van content en digitaal assetmanagement, helpt de Adobe Experience Manager handelaren om gepersonaliseerde, content-gestuurde ervaringen sneller op de markt te krijgen, door het beheer van digitale middelen te combineren met de kracht van machinaal leren, Adobe Sensei-gebaseerde content en het beheer van de reis van klanten.

Adobe de Handel plus de Manager van de Ervaring van de Adobe is een krachtig verhaal in die zin dat de handelingsmotor ondernemingen toestaat om handel door klanteninterfaces toe te laten die door Adobe Experience Manager worden aangedreven.

## Aangepaste koppen

De laatste optie die u hier wilt bespreken, is de optie om een aangepaste voorzijde te maken. This option is for businesses that have existing expertise and in-house developers skilled in a particular frontend stack, like React. Als zij geen vaardigheden in de traditionele frontend ontwikkeling van de Handel van Adobe hebben, kunnen zij beslissen dat het rendabeler is om hun eigen douaneVoorwaarts te bouwen React.

Dit model vereist uiteraard sterke klant- of systeemintegratie vooraf ontwikkelingsvaardigheden en -bronnen en u profiteert niet van native compatibiliteit met bijvoorbeeld Page Builder die u bij PWA Studio krijgt. Telkens wanneer een handelaar iets volledig gebruikelijk bouwt, kunnen zij tijd-aan-markt voordelen verliezen.

Aangepaste front-ends maken ook innovaties en experimenten mogelijk. Er wordt veel gesproken over AR/VR of spraakhandel, en een architectuur zoals de Adobe Commerce staat verkopers toe om deze opties te verkennen zonder hun bestaande webwinkels te beïnvloeden.
