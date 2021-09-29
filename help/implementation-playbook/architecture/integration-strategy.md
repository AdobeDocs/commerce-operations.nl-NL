---
title: Adobe Commerce Integration Strategy
description: Herzie integratiestrategieën en opties voor uw implementatie van de Handel van de Adobe.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Adobe Commerce-integratiestrategie

Over de mogelijkheid om uw platform te integreren kan niet worden onderhandeld. Companies want their ecommerce platforms accessible from a variety of touchpoints and seamlessly integrated into their technology systems, especially their ERP. Aanpasbaarheid, globale schaalbaarheid en betaalbaarheid spelen ook een rol bij de uiteindelijke platformaanschaf.

A holistic integration approach for both storefront and backend systems are supported by performant GraphQL APIs, comprehensive REST APIs, and batch-file import between Adobe Commerce and other systems or services.

De GrafiekQL API van de Handel van de Adobe verstrekt uitvoerige archiefrontdekking die u kunt gebruiken om met andere storefronts te integreren, die omvatten:

- Digital experience platforms (DXPs) like Adobe Exeprience Manaber and Bloomreach
- Inhoudsbeheersystemen zoals Drupal en WordPress
- Moderne aangepaste winkeltoepassing zoals Adobe Commerce, PWA Studio en Vue Storefront

GraphQL verstrekt een efficiënte, kanaalspecifieke reactie, geen overwinning van gegevens, en een flexibele plaatsing van nieuwe aanraakpunteigenschappen. It is also often chosen to integrate with sales channels such as mobile native apps, POS, IoT, social channels, and livestream commerce channels like Facebook, Google, Instagram, WeChat, and TikTok.

De Adobe Commerce REST API biedt uitgebreide dekking voor systeemconfiguratie en functies voor gegevensbeheer, waaronder product en catalogus; kar, citaat, en kassa; klanten, accounts en bedrijven; en bestellingen en retourneert. REST APIs support bulk operations, multiple authentication modes, and granular authorization, so REST APIs are often chosen to integrate with enterprise systems, including:

- ERP-systemen (Enterprise Resource Planning), zoals SAP
- PIM-systemen (Product Information Management) zoals Akeneo
- Customer relationship management (CRM) systems like Salesforce
- Order management systems (OMS) like MOM, Manhattan, and SAP
- Warehouse Management System (WMS) of een externe logistiek (3PL) zoals Oracle, NetSuite en SAP WM
- Vorm, Prijs, Citaat (CPQ) zoals SalesforceCPQ
- Digital Asset Management (DAM) like Adobe DAM.

De invoer van batchbestanden wordt ook beschouwd als een goede optie voor de integratie van bedrijfssystemen zoals ERP&#39;s en PIM&#39;s, aangezien die gegevens niet vaak veranderen en u vaak betere prestaties hebt bij de geplande bestandsimport. So, batch-file imports are usually chosen for bulk data synchronization on a daily/weekly basis and monthly full data synchronizations, whereas REST APIs are chosen for incremental data change synchronization, for better performance. Dit wordt ook slechts beschouwd als een geplande baan maar kan vaak-potentieel om de 15 min aan 1 uur-afhankelijk van bedrijfsbehoeften worden gedaan.

## Integratieopties

Adobe Commerce biedt drie flexibele integratieopties:

- Direct system-to-system integration with pre-built connectors. Op sommige systemen staan mogelijk al Adobe Commerce-extensies op de Commerce Marketplace van Adobe of op hun eigen website.

- System-to-system integration through custom middleware. De aangepaste middleware-oplossing die wordt geïmplementeerd, wordt gebruikt voor het in kaart brengen, vertalen en beheren van procesgegevens.

- Systeem-aan-systeem integratie door iPaaS (Integratie Platform-als-a-Dienst), die ook als EAI (het Platform van de Integratie van de Toepassing van de Onderneming) wordt bedoeld, zoals Mulesoft, Boomi, en Software AG.

![Adobe Commerce integration options](../../assets/playbooks/integration-options.svg)

Even though real-time integrations are usually desired, it’s not necessary for some scenarios. Adobe Commerce natively supports RabbitMQ as the message bus to enable asynchronous processes, which is recommended for some data that is not necessary to exchange in real time, but rather to update with batch-file exchange or REST batch data process API to process asynchronously.
