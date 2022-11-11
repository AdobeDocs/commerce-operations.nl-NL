---
title: Adobe Commerce Integration Strategy
description: Herzie integratiestrategieën en opties voor uw implementatie van Adobe Commerce.
exl-id: af7cc59a-3ee2-461a-8489-a35fe0288277
source-git-commit: 1e545d8d5554e73f522469e526ed098395db9075
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# Integratiestrategie van Adobe Commerce

Over de mogelijkheid om uw platform te integreren kan niet worden onderhandeld. Bedrijven willen dat hun elektronische handelsplatforms toegankelijk zijn vanuit verschillende aanraakpunten en naadloos geïntegreerd zijn in hun technologiesystemen, met name hun ERP. Aanpasbaarheid, globale schaalbaarheid en betaalbaarheid spelen ook een rol bij de uiteindelijke platformaanschaf.

Een holistische integratieaanpak voor zowel opslag- als back-endsystemen wordt ondersteund door krachtige GraphQL API&#39;s, uitgebreide REST API&#39;s en het importeren van batchbestanden tussen Adobe Commerce en andere systemen of services.

De Adobe Commerce GraphQL API biedt uitgebreide storefront-dekking die u kunt gebruiken om te integreren met andere winkeliers, zoals:

- Digitale ervaringsplatforms (DXPs) zoals Adobe Experience Manager en Bloomreach
- Inhoudsbeheersystemen zoals Drupal en WordPress
- Moderne aangepaste winkeltoepassing zoals Adobe Commerce, PWA Studio en Vue Storefront

GraphQL verstrekt een efficiënte, kanaalspecifieke reactie, geen overwinning van gegevens, en een flexibele plaatsing van nieuwe aanraakpunteigenschappen. Het wordt ook vaak gekozen om met verkoopkanalen zoals mobiele inheemse apps, POS, IoT, sociale kanalen, en livestreamhandelkanalen zoals Facebook, Google, Instagram, WeChat, en TikTok te integreren.

De Adobe Commerce REST API biedt uitgebreide systeemconfiguratieredekking en functies voor gegevensbeheer, waaronder product en catalogus; kar, citaat, en kassa; klanten, accounts en bedrijven; en bestellingen en retourneert. REST API&#39;s ondersteunen bulkbewerkingen, meerdere verificatiemodi en korrelige autorisatie, zodat REST API&#39;s vaak worden gekozen voor integratie met bedrijfssystemen, waaronder:

- ERP-systemen (Enterprise Resource Planning), zoals SAP
- PIM-systemen (Product Information Management) zoals Akeneo
- Systemen voor relatiebeheer (CRM) van klanten zoals Salesforce
- Orderbeheersystemen (OMS) zoals MOM, Manhattan en SAP
- Warehouse Management System (WMS) of een externe logistiek (3PL) zoals Oracle, NetSuite en SAP WM
- Vorm, Prijs, Citaat (CPQ) zoals SalesforceCPQ
- DAM (Digital Asset Management), zoals Adobe DAM.

De invoer van batchbestanden wordt ook beschouwd als een goede optie voor de integratie van bedrijfssystemen zoals ERP&#39;s en PIM&#39;s, aangezien die gegevens niet vaak veranderen en u vaak betere prestaties hebt bij de geplande bestandsimport. Daarom wordt de invoer van batch-dossiers gewoonlijk gekozen voor bulkgegevenssynchronisatie op een dagelijkse/wekelijkse basis en maandelijkse volledige gegevenssynchronisaties, terwijl REST APIs voor stijgende synchronisatie van de gegevensverandering, voor betere prestaties wordt gekozen. Dit wordt ook slechts beschouwd als een geplande baan maar kan vaak-potentieel om de 15 min aan 1 uur-afhankelijk van bedrijfsbehoeften worden gedaan.

## Integratieopties

Adobe Commerce biedt drie flexibele integratieopties:

- Directe systeemintegratie met vooraf gebouwde connectors. Sommige systemen hebben mogelijk al Adobe Commerce-extensies op de Adobe Commerce Marketplace of op hun eigen website.

- Systeem-aan-systeem integratie door douane middleware. De aangepaste middleware-oplossing die wordt geïmplementeerd, wordt gebruikt voor het in kaart brengen, vertalen en beheren van procesgegevens.

- Systeem-aan-systeem integratie door iPaaS (Integratie Platform-als-a-Dienst), die ook als EAI (het Platform van de Integratie van de Toepassing van de Onderneming) wordt bedoeld, zoals Mulesoft, Boomi, en Software AG.

![Adobe Commerce-integratieopties](../../assets/playbooks/integration-options.svg)

Hoewel integratie in real time meestal gewenst is, is dit niet nodig voor bepaalde scenario&#39;s. Adobe Commerce biedt native ondersteuning voor RabbitMQ als de berichtenbus voor het inschakelen van asynchrone processen. Dit wordt aanbevolen voor sommige gegevens die niet in real-time hoeven te worden uitgewisseld, maar die wel moeten worden bijgewerkt met batch-bestandsuitwisseling of REST-batchgegevensverwerkings-API voor asynchroon verwerken.
