---
title: Adobe Commerce-uitbreidingsstrategie
description: Leer hoe u met het uitbreidingsmodel van Adobe Commerce uw implementatie kunt aanpassen.
exl-id: fac4630d-8a41-40dc-899a-01eabceaa61e
feature: Extensibility
source-git-commit: 4873a51fbf67d305fdd1898f3740c73ac5ccbad8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Uitbreidingsstrategie

Met het uitbreidbaarheidsplatform van Adobe Commerce kunnen merken processen efficiënt aanpassen, systemen integreren en nieuwe mogelijkheden implementeren terwijl upgradebaarheid behouden blijft.

## Overzicht van de uitbreidingsstrategieën voor de handel

De uitbreiding van de mogelijkheden van het handelsplatform omvat de volgende benaderingen op hoog niveau:

* Uitbreiding van de native mogelijkheden van het Commerce-platform. Handelaars kunnen bijvoorbeeld Marketplace-toepassingen installeren (die vaak door derden zijn gemaakt) die de native mogelijkheden van het platform uitbreiden en verfijnen, bijvoorbeeld een uitbreiding die de verzendadressen tijdens het afrekenen kan valideren en snelle integratie met de UPS-API&#39;s voor het adresadres van de vervoerder mogelijk maakt.

* Toepassingen/extensies van derden integreren met het Commerce-platform. Ontwikkelaars kunnen de bestaande, uitgebreide REST- en GraphQL-API&#39;s van Commerce gebruiken om de handel rechtstreeks te integreren met oplossingen van derden.

Platformarchitectuur bepaalt echter de beste strategieën voor het uitbreiden van een platform. De handel verstrekt rijke GQL en REST API dekking voor hoofdloze plaatsing. De basis van de kerncode van de Handel blijft zich in de richting van een meer modulaire architectuur en één enkele integratielaag ontwikkelen, die nieuwe, betere aanpassingshulpmiddelen verstrekt:

* [App Builder voor Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/adobe-developer-app-builder/introduction-to-app-builder.html) is een ontwikkelingskader en een instrumentarium dat is gebaseerd op Adobe-infrastructuur. De ontwikkelaars kunnen het gebruiken om de uitbreidingen van de Handel tot stand te brengen die zich van gebruikerservaring/storefront aanpassingen aan middleware en bedrijfslogische uitbreidingen uitstrekken.

* [API-net voor Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) Hiermee kunnen ontwikkelaars meerdere gegevensbronnen combineren tot één API-eindpunt. Dit steunt APIorchestratie, of integratie, van privé en derde APIs en andere softwareinterfaces met Adobe Commerce APIs en andere producten van de Adobe die Adobe I/O gebruiken.

* [Adobe I/O Events voor Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/) stelt transactionele gegevens beschikbaar voor toepassingen die met de haken van de Bouwer van de App en van het derdeWeb worden ontwikkeld, ondersteunend de verwezenlijking van gebeurtenis-gedreven toepassingen.

Met deze gereedschappen hebt u toegang tot de ontwikkelaars van Adobe Developer Console en Adobe om API&#39;s te maken en aangepaste plug-ins en integratie te integreren.

In het volgende diagram worden de belangrijkste onderdelen van de exentibiliteitsstrategie voor de handel belicht.

![Adobe Commerce-diagram met uitbreidingsstrategie](../../assets/playbooks/extensibility-strategy-overview.png)
