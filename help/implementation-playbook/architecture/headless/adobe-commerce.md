---
title: Hoofdloze Adobe Commerce-architectuur
description: Meer informatie over wat de Adobe Commerce-benadering zonder kop uniek maakt.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Hoofdloze Adobe Commerce-architectuur

Het voordeel van de Adobe Commerce-architectuur is dat het geen alles-of-niets-voorstel is en een handelaar de juiste combinatie van oplossingen voor zijn bedrijf kan vinden. Zij kunnen een PWA Studio-aangedreven PWA voor hun primaire plaatservaring bouwen of Adobe Experience Manager gebruiken als laag in complexe klantenreizen, allen terwijl het bouwen van een douane voorkant om met nieuwe aanraakpunten te experimenteren. Geen enkel ander platform kan de tijd aanpassen aan de voordelen van de markt en de flexibiliteit die Adobe Commerce biedt met zijn meeslepende architectuur.

![Diagram met een Adobe Commerce storefronarchitectuur zonder kop](../../../assets/playbooks/headless-storefront-architecture.svg)

Elke aanpak sluit elkaar niet uit. Klanten kunnen hun eigen front-end (head) maken, PWA Studio gebruiken voor web/mobiele ervaringen en/of Adobe Experience Manager gebruiken voor het glas (in een volledige of hybride implementatie).

Adobe Commerce heeft altijd toestemming gegeven voor headless-implementaties met REST API&#39;s. Terwijl REST krachtig is, vooral voor bulkverwerking, als het op hoofdloze producten komt, laten GraphQL APIs snellere ontwikkeling door een intuïtieve ontwikkelaarservaring toe, grotere flexibiliteit door voor veranderingen toe te staan die geen invloed op bestaande APIs hebben, en betere prestaties door de hoeveelheid gegevens te minimaliseren die aan slechts precies wordt teruggewonnen wat nodig is.

GraphQL is een industriestandaard voor presterende API&#39;s, die wordt gebruikt door veel van de topplatforms voor e-commerce. Dat is een goede zaak, omdat dit betekent dat het een bewezen oplossing is en dat er deskundigheid bestaat op de markt.

Hoewel Adobe Commerce een gekoppelde opslagruimte als optie heeft, is het geenszins verplicht dat een handelaar die Adobe Commerce erfenis vooraf gebruikt. Een handelaar kan uit de best-in-klasse handeldiensten van Adobe Commerce voordeel halen om de achterste bedrijfsprocessen te behandelen en, gebruikend onze opslag APIs, hun eigen ontkoppelde opslagruimte te integreren om de frontend ervaring te drijven.

Laten we nu eens kijken naar de verschillende opties zonder kop.

## PWA Studio

Het eerste is een progressieve webtoepassing die met PWA Studio is gebouwd. Een deel hiervan wordt mogelijk gemaakt door het feit dat een PWA een koploze winkel is die los staat van de commerciële achtergrond. Met PWA Studio kunnen handelaren hoogwaardige, betrouwbare en voordelige PWA bovenop Adobe Commerce bouwen om de beste webbelevenissen van hun klasse te bieden, zowel op mobiele apparaten als op desktops. Als de tijd doorgaat, wordt de gekoppelde opslagruimte als de standaardoptie gebruikt.

De meeste handelaren begrijpen de richting die de industrie volgt met betrekking tot PWA en veel potentiële blokkers worden snel weggenomen.

Week in week, groeit het aantal partners bouwend deskundigheid in PWA Studio en wij hebben een versnelend aantal klantenlanceringen. De meest recente update van PWA Studio omvatte uitbreidbaarheid die belangrijke vooruitgang op het gebied van compatibiliteit met Adobe Commerce Marketplace-extensies zal helpen maken.

Veel handelaren hebben het gevoel dat ze niet klaar zijn voor krantenloze PWA omdat ze veel vertrouwen op ontwikkelaars nodig hebben. Een van de grote voordelen van zowel de handelstoepassing als de door Adobe Commerce ontwikkelde kop is dat deze de compatibiliteit tussen de verschillende handelscapaciteiten bevordert.

Om PWA toegankelijker en gemakkelijker te beheren voor onze handelaren te maken, stellen wij zakelijke gebruikers in staat wijzigingen in inhoud van dag tot dag te beheren, nieuwe bestemmingspagina&#39;s te maken en nog veel meer gebruik te maken van Page Builder. Deze twee krachtige mogelijkheden samen laten snelheid toe om over alle apparaten en ervaringen op de markt te brengen.

## Adobe Experience Manager

Adobe Experience Manager is een krachtige combinatie voor uw behoeften op het gebied van content en digitaal assetmanagement en helpt handelaren om sneller persoonlijke, inhoudgestuurde ervaringen op de markt te krijgen, door het beheer van digitale middelen te combineren met de kracht van machinaal leren, door Adobe Sensei aangedreven content en het beheer van de reis van klanten.

Adobe Commerce plus Adobe Experience Manager is een krachtig verhaal in die zin dat de handelingsmotor ondernemingen toestaat om handel door klanteninterfaces toe te laten die door Adobe Experience Manager worden aangedreven.

## Aangepaste koppen

De laatste optie die u hier wilt bespreken, is de optie om een aangepaste voorzijde te maken. Deze optie is voor ondernemingen die bestaande deskundigheid en interne ontwikkelaars hebben die in een bepaalde frontend stapel, zoals React worden gekwalificeerd. Als ze geen vaardigheden hebben in de traditionele frontendontwikkeling van Adobe Commerce, kunnen ze beslissen dat het rendabeler is om hun eigen aangepaste React frontend te bouwen.

Natuurlijk, vereist dit model sterke klant of systeemintegratie vooraf ontwikkelingsvaardigheden en middelen, en u krijgt niet het voordeel van inheemse verenigbaarheid met dingen zoals de Bouwer van de Pagina die u met PWA Studio krijgt. Telkens wanneer een handelaar iets volledig gebruikelijk bouwt, kunnen zij tijd-aan-markt voordelen verliezen.

Aangepaste front-ends maken ook innovaties en experimenten mogelijk. Er wordt veel gesproken over AR/VR of spraakhandel. Een architectuur als Adobe Commerce stelt handelaren in staat om deze opties te verkennen zonder dat dit gevolgen heeft voor hun bestaande webwinkels.
