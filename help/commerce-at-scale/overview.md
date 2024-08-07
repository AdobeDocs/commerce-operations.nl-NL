---
title: Ervaringen op schaal leveren
description: Leer hoe u op schaal ervaringen kunt bieden met Adobe Commerce en Adobe Experience Manager.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Lever ervaringen op schaal met Adobe Commerce, Commerce integration framework en Adobe Experience Manager

Een aanbevolen integratiepatroon tussen AEM en Adobe Commerce waarbij CIF als connector wordt gebruikt, is dat AEM eigenaar is van de presentatielaag (het &quot;glas&quot;) en Adobe Commerce om de commerciële achterkant van stroom te voorzien als een &quot;headless&quot; achterkant. Deze integratiebenadering maakt gebruik van de sterke punten van elke toepassing: de creatie, personalisatie, en omnichannel mogelijkheden van AEM en e-commerce verrichtingen van Adobe Commerce.

In een AEM/CIF/Adobe Commerce-omgeving zullen bezoekers van de site voor e-commerce aanvankelijk bij AEM aankomen. AEM controleert of de gevraagde pagina beschikbaar is in de verzendcache van de pagina. Als de pagina bestaat, wordt deze pagina in de cache aan de bezoeker weergegeven en is geen verdere verwerking vereist. Als de verzender de gevraagde pagina niet bevat of is verlopen, vraagt de verzender de AEM uitgever om de pagina samen te stellen, waarbij de uitgever Adobe Commerce zo nodig oproept voor e-mailgegevens om de pagina samen te stellen. De ingebouwde pagina wordt vervolgens aan de verzender doorgegeven om de bezoeker te bedienen en wordt vervolgens in de cache geplaatst, zodat verdere laadbewerkingen niet op de servers hoeven te worden uitgevoerd wanneer andere bezoekers op dezelfde pagina een later verzoek indienen.

![ diagram van het Overzicht van de Manager van de Ervaring van de Adobe en de architectuur van Adobe Commerce ](../assets/commerce-at-scale/overview.png)

Een combinatie van rendering op de server en renderen op de client kan worden gebruikt in het model AEM/CIF/Adobe Commerce: renderen op de server om statische inhoud en renderen op de client te leveren om vaak veranderende of persoonlijke dynamische inhoud te leveren door Adobe Commerce rechtstreeks aan te roepen voor specifieke componenten
vanuit de browser van de gebruiker.

Een voorbeeld van de verschillende componenten in een Pagina van het Detail van het Product op een voorbeeld AEM e-commerce opslag kan in het hieronder voorbeeld worden gezien:

![ diagram van het Overzicht van de Manager van de Ervaring van de Adobe en de architectuur van Adobe Commerce ](../assets/commerce-at-scale/product-details-page.svg)

## Rendering op de server

E-commercepagina&#39;s zoals pagina&#39;s met productdetails (PDP&#39;s) en pagina&#39;s met productlijsten (PLP&#39;s) veranderen waarschijnlijk niet vaak en zijn geschikt om volledig in cache te worden geplaatst nadat ze op de server zijn gerenderd met AEM Core Components. De pagina&#39;s zouden op de AEM uitgever moeten worden teruggegeven gebruikend generische malplaatjes die in AEM worden gecreeerd. Deze componenten krijgen gegevens van Adobe Commerce via GraphQL API&#39;s. Deze pagina&#39;s worden dynamisch gemaakt, op de server weergegeven, in het cachegeheugen opgeslagen op de AEM dispatcher en vervolgens aan de browser geleverd. Voorbeelden hiervan worden weergegeven in de paarse vakken in het bovenstaande voorbeeld.

## Rendering op de client

Waar meer dynamische attributen zoals voorraadniveaus/beschikbaarheid of prijs worden getoond, bijvoorbeeld op de Pagina&#39;s van het Detail van het Product (PDPs), cliënt-zijcomponenten kunnen worden gebruikt. Hoewel de sjabloonpagina op de dispatcher kan worden gemaakt en in cache kan worden geplaatst met behulp van de hierboven beschreven rendermethode aan de serverzijde, kunnen er binnen de statische pagina zelf dynamische client-side webcomponenten zijn. Deze dynamische componenten kunnen gegevens direct in de browser van de cliënt van Adobe Commerce via GraphQL APIs ophalen om, bijvoorbeeld, huidig prijs of voorraadniveau in echt te controleren - tijd op PDP. Dit zorgt ervoor dat inhoud die doorgaans van essentieel belang is om in real-time te worden weergegeven, altijd wordt opgehaald bij het laden van de pagina. Voorbeelden hiervan worden weergegeven in de rode vakken in het bovenstaande voorbeeld.

Een combinatie van AEM sjablonen en renderen aan de clientzijde kan ook worden gebruikt tijdens het uitcheckproces: client-side cartcomponenten geven het winkelwagentje, het uitcheckformulier en de integratie met de betalingsdienstaanbieder. Deze hybride aanpak kan ook worden gebruikt voor Adobe Commerce-functies voor accountbeheer, zoals het maken van een account, het aanmelden bij een account en het vergeten wachtwoord.
