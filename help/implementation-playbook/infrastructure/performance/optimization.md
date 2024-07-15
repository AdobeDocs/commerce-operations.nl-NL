---
title: Optimalisatie van prestaties
description: Leer alles over prestatiesoptimalisering en stappen om de prestaties van uw implementatie van Adobe Commerce te herzien.
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Optimalisatie van prestaties

Prestaties zijn een groot onderwerp. Wanneer gebruikers een trage of niet-responsieve site ervaren, heeft dit invloed op de conversie. We raden u aan de volgende stappen uit te voeren om de prestaties van uw Adobe Commerce voor de implementatie van de cloud-infrastructuur te optimaliseren:

- Het probleem beoordelen
- Prestaties meten
- Een deel van het systeem identificeren dat essentieel is voor prestatieverbetering
- Een deel van het systeem wijzigen om het knelpunt te verwijderen
- De prestaties na de wijziging meten
- Indien beter, neem het of vervang het

## Typische prestatieproblemen

Het effect van een trage ervaring wordt meestal bepaald door twee indicatoren en elke factor kan om tonnen redenen worden veroorzaakt.

De hoge tijd-aan-eerste-byte (TTFB) wordt gewoonlijk beschouwd als indicator die de reactiesnelheid van de server bepaalt. De tijd komt niet alleen van broncode uitvoering voor de behandeling van het verzoek, maar het kan ook door de volgende factoren worden beïnvloed:

- DNS-zoekopdracht
- Langzame vragen uit DB-laag
- CPU-tijd van elke toepassingslaag
- Geheugenbeperking
- I/O-wachttijd kan van invloed zijn op het lezen en schrijven van bestanden, verbindingsservice via socket
- Software-instellingen (nginx, PHP, MySQL, Redis, Varnish)
- Netwerkbandbreedte
- Onjuiste caching
- Ongeldige code
- Beschadigde integratiebenadering
- Afhankelijkheid van trage servicerespons van derden
- Architectuur zonder schaalbaarheid

Lagere bronnen worden meestal beschouwd als een indicator die de statische bron definieert (CSS, JavaScript, afbeeldingen, video&#39;s, Ajax-callrespons van derden).

Adobe Commerce kan met uw bedrijf schalen dankzij de mogelijkheden:

![ Diagram die de scalable mogelijkheden van Adobe Commerce ](../../../assets/playbooks/scalable-capabilities.svg) tonen

Er zijn ook belangrijke factoren die de schaal van de handel stimuleren, die ook de algemene prestaties beïnvloeden.

- Complexe en grote productcatalogus
- Grote aantallen beheerders
- Wereldwijde winkelcentra
- Hoog variabel verkeer
- Aanraakpunten uitbreiden
- Transacties op grote volumes

Voor gelaagde en cacheable architecturen die voor schaal worden gebouwd, kunt u deze grafiek als verwijzing gebruiken.

![ Diagram die tonen hoe te om Adobe Commerce GraphQL API in een cacheable architectuur te gebruiken ](../../../assets/playbooks/cacheable-architecture.svg)
