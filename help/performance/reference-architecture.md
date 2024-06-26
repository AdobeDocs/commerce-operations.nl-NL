---
title: Referentiearchitectuur
description: Diagrammen van de aanbevolen referentiearchitectuur voor Adobe Commerce-implementaties bekijken.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Referentiearchitectuur

In dit onderwerp wordt een algemene aanbevolen installatie voor Adobe Commerce-instanties beschreven met behulp van gewone servers die fysiek worden gehost in een datacenter (niet gevirtualiseerd) waarin bronnen niet met andere gebruikers worden gedeeld. Uw hostingprovider, met name als deze gespecialiseerd is in het hosten van hoge Commerce-prestaties, raadt mogelijk een andere instelling aan die even of effectiever is voor uw vereisten.

Voor Adobe Commerce over omgevingen met cloudinfrastructuren raadpleegt u [Starter-architectuur](https://devdocs.magento.com/cloud/architecture/starter-architecture.html).

## [!DNL Commerce] Referentie-architectuurdiagram

De [!DNL Commerce] Referentie-architectuurdiagram geeft de beste praktijkbenadering weer voor het instellen van een schaalbare [!DNL Commerce] site.

De kleur van elk element in het diagram geeft aan of het element deel uitmaakt van Magento Open Source of Adobe Commerce en of dit vereist is.

* Oranje elementen zijn vereist voor Magento Open Source
* Grijswaarden zijn optioneel voor Magento Open Source
* Blauwe elementen zijn optioneel voor Adobe Commerce

![Commerce-referentiearchitectuurdiagram](../assets/performance/images/ref-architecture-2.3.png)

De volgende secties geven aanbevelingen en overwegingen voor elk gedeelte van het Commerce Reference Architecture-diagram.

### [!DNL Varnish]

* A [!DNL Varnish] de cluster kan aan het verkeer van een plaats schrapen
* Instantiegrootte afstemmen op basis van het aantal benodigde cachepagina&#39;s
* Voor een hoge verkeersplaats, gebruik een [!DNL Varnish] Master om ervoor te zorgen dat één aanvraag (maximaal) per weblaag op de cache wordt verwijderd

### Web

* De schaal van knooppunten voor verkeer en redundantie inschakelen
* Eén knooppunt is master en voert uitsnede uit
* U kunt ook een toegewezen beheerdersknooppunten en werkbalkknooppunten gebruiken

### Cache

* Een aparte Redis-instantie voor sessies implementeren
* U kunt een Redis-instantie per cache hebben
* De grootte van uw instantie aanpassen om de grootste verwachte cachegrootte te bevatten

### Database en wachtrijen

* De hoge verkeersplaatsen kunnen de prestaties van OB met slave OBs en gesplitste OBs voor orden/karretjes (in Adobe Commerce) stemmen
* Gebruik een slave-database om snel herstel en gegevensback-ups mogelijk te maken
* Websites met weinig verkeer kunnen afbeeldingen opslaan in de database

### Zoeken {#search-heading}

* Het aantal instanties afstemmen op basis van zoekverkeer

### Opslag

* Overweeg GFS of GlusterFS te gebruiken voor pub/media-opslag
* Alternatief, gebruik de opslag van OB voor laag-verkeersplaatsen

### Aanbevolen [!DNL Varnish] referentiearchitectuur

Magento ondersteunt meerdere engines voor het in cache plaatsen van volledige pagina&#39;s (File, Memcache, Redis, Redis, [!DNL Varnish]) uit de doos, samen met uitgebreide dekking door uitbreidingen. [!DNL Varnish] is de aanbevolen cache-engine voor de volledige pagina.  [!DNL Commerce] ondersteunt veel verschillende [!DNL Varnish] configuraties.

Voor plaatsen die geen hoge beschikbaarheid vereisen, adviseren wij het gebruiken van eenvoudig [!DNL Varnish] installatie met Nginx SSL-beëindiging.

![eenvoudig [!DNL Varnish] Configuratie met SSL-beëindiging](../assets/performance/images/single-varnish-with-ssl-termination.png)

Voor plaatsen die hoge beschikbaarheid vereisen, adviseren wij gebruikend een 2 rij [!DNL Varnish] configuratie met een SSL-afsluitend taakverdelingsmechanisme.

![Hoge beschikbaarheid op twee niveaus [!DNL Varnish] configuratie met SSL-afsluitend taakverdelingsmechanisme](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
