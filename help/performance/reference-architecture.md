---
title: Referentiearchitectuur
description: Diagrammen van de aanbevolen referentiearchitectuur voor Adobe Commerce-implementaties bekijken.
exl-id: 85a6d3d6-f47f-4806-97bd-fa7a73605f4c
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Referentiearchitectuur

In dit onderwerp wordt een algemene aanbevolen installatie voor Adobe Commerce-instanties beschreven met behulp van gewone servers die fysiek worden gehost in een datacenter (niet gevirtualiseerd) waarin bronnen niet met andere gebruikers worden gedeeld. Uw hostingprovider, met name als deze gespecialiseerd is in het hosten van hoge Commerce-prestaties, raadt mogelijk een andere instelling aan die even of effectiever is voor uw vereisten.

Voor Adobe Commerce op de milieu&#39;s van de wolkeninfrastructuur, zie [ de architectuur van de Aanzet ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/architecture/starter-architecture).

## [!DNL Commerce] Referentie-architectuurdiagram

Het [!DNL Commerce] diagram Referentiearchitectuur vertegenwoordigt de aanbevolen aanpak voor het instellen van een schaalbare [!DNL Commerce] -site.

De kleur van elk element in het diagram geeft aan of het element deel uitmaakt van Magento Open Source of Adobe Commerce en of dit vereist is.

* Voor Magento Open Source zijn oranje elementen vereist
* Grijswaarden zijn optioneel voor Magento Open Source
* Blauwe elementen zijn optioneel voor Adobe Commerce

![ Commerce het diagram van de verwijzingsarchitectuur ](../assets/performance/images/ref-architecture-2.3.png)

De volgende secties geven aanbevelingen en overwegingen voor elk gedeelte van het Commerce Reference Architecture-diagram.

### [!DNL Varnish]

* Een [!DNL Varnish] -cluster kan worden geschaald naar het verkeer van een site
* Instantiegrootte afstemmen op basis van het aantal benodigde cachepagina&#39;s
* Gebruik op een site met veel verkeer een [!DNL Varnish] stramien om ervoor te zorgen dat één aanvraag (maximaal) per weblaag in de cache wordt verwijderd

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

Magento biedt ondersteuning voor diverse engines (File, Memcache, Redis, [!DNL Varnish] ) die de pagina in cache plaatsen en voor uitgebreide dekking via extensies. [!DNL Varnish] is de aanbevolen cache-engine voor volledige pagina.  [!DNL Commerce] ondersteunt veel verschillende [!DNL Varnish] -configuraties.

Voor sites waarvoor geen hoge beschikbaarheid vereist is, raden we u aan een eenvoudige [!DNL Varnish] -installatie te gebruiken met Nginx SSL-beëindiging.

![ Eenvoudige [!DNL Varnish] Configuratie met SSL Beëindiging ](../assets/performance/images/single-varnish-with-ssl-termination.png)

Voor sites die hoge beschikbaarheid vereisen, raden we u aan een configuratie met twee niveaus [!DNL Varnish] te gebruiken met een SSL-terminating voor taakverdeling.

![ Hoge beschikbaarheid twee-rij [!DNL Varnish] configuratie met SSL beëindigend ladingsverdelingsmechanisme ](../assets/performance/images/ha-2-tier-varnish-with-ssl-term-load-balancer.png)
