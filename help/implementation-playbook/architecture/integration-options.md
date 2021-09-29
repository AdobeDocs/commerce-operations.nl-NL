---
title: Adobe Commerce Integration-opties
description: Onderzoek uw opties om andere systemen met uw implementatie van de Handel van de Adobe te integreren.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Typische integratiepunten en gegevensstromen

Er zijn twee belangrijke benaderingen van integratie en gegevensstromen, die zeer gelijkaardig zijn maar één zeer belangrijk verschil hebben.

## Monolithisch

In het volgende diagram wordt een monolithische benadering beschreven waarbij Adobe Commerce wordt gebruikt als back-end systeem en winkeltoepassing:

![Adobe Commerce-monolietdiagram](../../assets/playbooks/integration-monolith.svg)

## Koploos

The following diagram describes a headless approach that uses Adobe Commerce as the backend systenm integrated with a DXP/CMS/custom application as the storefront application:

![Adobe Commerce-headless-diagram](../../assets/playbooks/integration-headless.svg)

The only difference between the monolithic and headless approach is storefront integration, which impacts the user experience for customers. Met Monolithic wordt de Adobe Commerce-winkel rechtstreeks gebruikt om te integreren met services van derden, terwijl de kop niet afhankelijk is van de eigen winkel om zich aan te passen aan en te integreren met dezelfde services. Voor sommige services, zoals betaling en Single Sign-On (SSO), is zowel de aanpassing van de winkel als de Adobe Commerce vereist om de integratiestroom te voltooien.

## Systemen van derden

Sommige populaire services hebben al een groot aantal extensies voor ondersteuning van Adobe Commerce of populaire winkeloplossingen, zoals PWA Studio, Adobe Experience Manager en Vue Storefront, die u kunt vinden op hun website voor extensies of op websites van verwante derden. Zelfs als er geen uitbreiding bestaat, zijn de inspanningen om de integratie tussen de Adobe Commerce en andere koploze winkelcentra ten uitvoer te leggen vergelijkbaar. Alle derdediensten hebben gewoonlijk documenten om te verklaren hoe te met hen te integreren. Deze diensten zijn slechts enkele voorbeelden; verschillende landen en markten kunnen verschillende keuzes hebben .

## Enterprise integrations

Voor de integratie van ondernemingssystemen, die ook gewoonlijk backendintegratie worden genoemd, is er een effect op de bedrijfsgegevensstroom. Op basis van verschillende bedrijfstypen en -behoeften kan het drie verschillende integratieopties gebruiken, die we al hebben geïntroduceerd.

Product-mandatory data like SKUs, inventory, and base prices usually come from ERPs, while sales prices are usually managed by each sales channel (for example, Adobe Commerce) or CPQ (B2B or private sales). Omdat de product-verplichte gegevens (behalve voorraad) niet zeer vaak veranderen, is de beste praktijk om geplande partijupdates door REST API of bulkdossierinvoer te gebruiken. Voor inventarisatie is het de beste manier om dagelijks een volledige update te krijgen voor productinventaris die met verschillende verkoopkanalen wordt gedeeld om oververkoop te voorkomen. Bovendien zijn er binnen 24 uur incrementele wijzigingen gepland voor uw ERP.

Product catalog, metadata, and marketing content can be managed separately by each sales channel (for example, Adobe Commerce) or from a central PIM. Aangezien metagegevens ook niet vaak worden gewijzigd, kunt u het beste geplande batchupdates gebruiken via de REST API of het importeren van grote hoeveelheden bestanden.

Order data includes order, quote (B2B), shipment, return, and exchange data that is usually managed from a centralized OMS and WMS system. Ordergegevens moeten zo snel mogelijk worden gesynchroniseerd, dus REST API is meestal de beste optie. Voor betere prestaties, denk na verminderend het aantal API vraag. Voor de orderstatus, verzendingen, retourneren en gegevens uitwisselen, kunt u overwegen REST-batch-update-API&#39;s in uren of minuten te plannen.

B2B-gegevens worden gewoonlijk beheerd vanuit een gecentraliseerde CRM. Een real-time API wordt gebruikt om bestaande klanten te verifiëren en nieuwe klanten tot stand te brengen. Voor B2B, zou het het introduceren van meer APIs kunnen vereisen om verschillende bedrijfwerknemer, groep, en prijslijst tussen de Handel van Adobe en uw CRM of CPQ te synchroniseren.

There are some other system integrations like eDM for email marketing and business intelligence for business data analysis—which are usually done either via REST API or file export/import, which usually supported by existing extensions.
