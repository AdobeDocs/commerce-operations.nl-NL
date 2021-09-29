---
title: Optimalisatie van prestaties
description: Learn all about performance optimization and steps to take to review the performance of your Adobe Commerce implementation.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Performance optimization

Prestaties zijn een groot onderwerp. Wanneer gebruikers een trage of niet-responsieve site ervaren, heeft dit invloed op de conversie. We raden u aan de volgende stappen te volgen om de prestaties van uw Adobe Commerce-programma voor de implementatie van cloudinfrastructuur te optimaliseren:

- Assess the problem
- Prestaties meten
- Een deel van het systeem identificeren dat essentieel is voor prestatieverbetering
- Een deel van het systeem wijzigen om het knelpunt te verwijderen
- De prestaties na de wijziging meten
- Indien beter, neem het of vervang het

## Typische prestatieproblemen

Het effect van een trage ervaring wordt meestal bepaald door twee indicatoren en elke factor kan om tonnen redenen worden veroorzaakt.

De hoge tijd-aan-eerste-byte (TTFB) wordt gewoonlijk beschouwd als indicator die de reactiesnelheid van de server bepaalt. De tijd komt niet alleen van broncode uitvoering voor de behandeling van het verzoek, maar het kan ook door de volgende factoren worden beïnvloed:

- DNS-zoekopdracht
- Slow queries from DB layer
- CPU time from each application layer
- Memory limitation
- I/O-wachttijd kan van invloed zijn op het lezen en schrijven van bestanden, verbindingsservice via socket
- Software-instellingen (nginx, PHP, MySQL, Redis, Varnish)
- Netwerkbandbreedte
- Bad caching
- Bad code
- Beschadigde integratiebenadering
- Dependency of slow third-party service response
- Architecture without scalability

Slow-loading resources are usually regarded as an indicator that defines the static resource (CSS, JavaScript, images, videos, third-party Ajax call response).

De Handel van de Adobe kan met uw zaken door zijn mogelijkheden schrapen:

![Diagram showing the scalable capabilities of Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

There are also key factors driving scale in commerce, which also impact the overall performance.

- Complex and large product catalog
- Grote aantallen beheerders
- Wereldwijde winkelcentra
- Hoog variabel verkeer
- Aanraakpunten uitbreiden
- High-volume transactions

For layered and cacheable architectures built for scale, you can use this graph as a reference.

![Diagram dat toont hoe te om Adobe te gebruiken GrafiekQL API van de Handel in een cacheable architectuur](../../../assets/playbooks/cacheable-architecture.svg)
