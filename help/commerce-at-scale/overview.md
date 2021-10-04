---
title: Ervaringen op schaal leveren
description: Leer hoe u op grote schaal ervaringen kunt opdoen met Adobe Commerce en Adobe Experience Manager.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Lever ervaringen op schaal met Adobe Commerce, het Kader van de Integratie van de Handel, en Adobe Experience Manager

Een geadviseerd integratiepatroon tussen AEM en de Handel van de Adobe die CIF als schakelaar gebruiken is voor AEM om de presentatielaag (het &quot;glas&quot;) te bezitten en de Handel van Adobe om de handelsafdeling als &quot;headless&quot;backend aan te drijven. Deze integratieaanpak maakt gebruik van de sterke punten van elke toepassing: de creatie, verpersoonlijking, en omnichannel mogelijkheden van AEM en e-commerce verrichtingen van de Handel van Adobe.

In een AEM/CIF/Adobe Commerce-omgeving zullen bezoekers van de site e-commerce in eerste instantie bij AEM aankomen. AEM controleert of de gevraagde pagina beschikbaar is in de verzendcache van de pagina. Als de pagina bestaat, wordt deze pagina in de cache aan de bezoeker weergegeven en is geen verdere verwerking vereist. Als de verzender niet de gevraagde pagina bevat, of het is verlopen, dan verzoekt de verzender de AEM uitgever om de pagina te bouwen, met de uitgever die Adobe Commerce voor e-commerce gegevens roept om de pagina indien nodig te bouwen. De ingebouwde pagina wordt vervolgens aan de verzender doorgegeven om de bezoeker te bedienen en wordt vervolgens in de cache geplaatst, zodat verdere laadbewerkingen niet op de servers hoeven te worden uitgevoerd wanneer andere bezoekers op dezelfde pagina een later verzoek indienen.

![Overzichtsdiagram van de Manager van de Ervaring van Adobe en de architectuur van de Handel van de Adobe](../assets/commerce-at-scale/overview.png)

Een combinatie van server-zijrendering en client-side rendering kan worden gebruikt in het AEM/CIF/Adobe Commerce-model: Server-kant teruggeven om statische inhoud te leveren en cliënt-kant teruggeven om vaak veranderende of persoonlijke dynamische inhoud te leveren door de Handel van Adobe voor specifieke componenten direct te roepen
vanuit de browser van de gebruiker.

Een voorbeeld van de verschillende componenten in een Pagina van het Detail van het Product op een voorbeeld AEM e-commerce opslag kan in het hieronder voorbeeld worden gezien:

![Overzichtsdiagram van de Manager van de Ervaring van Adobe en de architectuur van de Handel van de Adobe](../assets/commerce-at-scale/product-details-page.svg)

## Rendering op de server

E-commercepagina&#39;s zoals pagina&#39;s met productdetails (PDP&#39;s) en pagina&#39;s met productlijsten (PLP&#39;s) zullen waarschijnlijk niet vaak veranderen en zijn geschikt om volledig in cache te worden geplaatst nadat ze op de server zijn gerenderd met behulp van AEM CIF Core Components. De pagina&#39;s zouden op de AEM uitgever moeten worden teruggegeven gebruikend generische malplaatjes die in AEM worden gecreeerd. Deze componenten krijgen gegevens van de Handel van Adobe via GraphQL APIs. Deze pagina&#39;s worden dynamisch gemaakt, op de server weergegeven, in het cachegeheugen opgeslagen op de AEM dispatcher en vervolgens aan de browser geleverd. Voorbeelden hiervan worden weergegeven in de paarse vakken in het bovenstaande voorbeeld.

## Rendering op de client

Waar meer dynamische attributen zoals voorraadniveaus/beschikbaarheid of prijs worden getoond, bijvoorbeeld op de Pagina&#39;s van het Detail van het Product (PDP&#39;s), cliënt-zijcomponenten kunnen worden gebruikt. Hoewel de sjabloonpagina op de dispatcher kan worden gemaakt en in cache kan worden geplaatst met behulp van de hierboven beschreven rendermethode aan de serverzijde, kunnen er binnen de statische pagina zelf dynamische client-side webcomponenten zijn. Deze dynamische componenten kunnen gegevens direct in browser van de cliënt van de Handel van de Adobe via GraphQL APIs ophalen om, bijvoorbeeld, huidige prijs of voorraadniveau in echt te controleren - tijd op PDP. Dit zorgt ervoor dat inhoud die doorgaans van essentieel belang is om in real-time te worden weergegeven, altijd wordt opgehaald bij het laden van de pagina. Voorbeelden hiervan worden weergegeven in de rode vakken in het bovenstaande voorbeeld.

Een combinatie van AEM sjablonen en renderen aan de clientzijde kan ook worden gebruikt tijdens het uitcheckproces: clientcartonderdelen maken het winkelwagentje, het uitcheckformulier en de integratie met de betalingsdienstaanbieder. Deze hybride aanpak kan ook worden gebruikt voor de functies voor accountbeheer van Adobe Commerce, zoals het maken van een account, het aanmelden met account en het vergeten wachtwoord.
