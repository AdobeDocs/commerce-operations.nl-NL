---
title: Zelfhostingoverzicht
description: Leer over zelf-ontvangende beste praktijken om te overwegen. De onderwerpen variëren van veiligheidselementen, aan rampenterugwinning veel meer. Deze onderwerpen zijn hier om een bedrijf bij te staan dat heeft besloten om hun eigen versie van Adobe Commerce te ontvangen. De gepresenteerde items zijn niet allemaal inclusief, maar moeten een goede reeks concepten bieden om een veilige, stabiele en veerkrachtige website te bevorderen.
landing-page-description: Leer enkele concepten en zaken die u in acht moet nemen wanneer u Adobe Commerce op uw eigen computer host.
short-description: Leer strategieën en concepten voor het hosten van Adobe Commerce zelf.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 1c63d082-c6fb-4795-81cd-75d097c03e6b
feature: Install
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 0%

---

# Adobe Commerce-overzicht met zelfhosting

Wanneer u de overstap naar een e-commerceplatform als Adobe Commerce overweegt, hebt u de luxe van opties. Met deze opties komen echter extra kosten, risico en verplichtingen in aanmerking. Het ontvangen van een plaats van Commerce kan worden gedaan gebruikend een verpakte oplossing, zoals [ Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html) {target="_blank"}, waar de infrastructuur, de servers, e-mail, SSL certificaten en veel meer pre-gevormd en klaar voor gebruik zijn. Het vinden van een goede hostingoplossing zoals Adobe Commerce op cloudinfrastructuur maakt het hele proces gemakkelijker. Er zijn dwingende redenen om uw Commerce-site zelf te hosten. Binnen de begeleidende pagina&#39;s, zijn er vele onderwerpen die inzicht en begeleiding over de diensten, de technieken, en de concepten verstrekken die zelf het ontvangen verstrekt. De informatie is hier niet volledig en het is niet te verwachten dat u elke suggestie uitvoert. Deze artikelen kunnen u echter helpen inzicht te krijgen in de ideeën en concepten die ervoor kunnen zorgen dat de Adobe Commerce zelf zo stabiel en veilig mogelijk optreedt.

Wanneer u niet met Adobe Commerce gaat op cloudinfrastructuur, zijn de gebruikte termen zelfhosting of on-premise, of zelfs on-prem wordt gebruikt. Op-gebouw betekent niet alleen in een datacenter in een gebouw dat eigendom is van een bedrijf. Deze term staat voor alles wat Adobe Commerce op zijn infrastructuur niet beheert. Er zijn hostingbedrijven die zich bezighouden met Adobe Commerce, maar die worden ook beschouwd als zelfstandige of on-prem.

Wat Adobe Commerce en Magento Open-source betreft, werken de meeste adviezen en tips voor beide versies. Hoewel het niet direct kan aangeven, is de verwachting dat het voor beide van toepassing is. Binnen dit onderwerp van zelf-ontvangende opties voor Adobe Commerce, worden beide versies overwogen. En tenslotte, zijn de meeste onderwerpen relevant voor [ Adobe Commerce op wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html) {target="_blank"} wordt geselecteerd als ontvangende leverancier.

## Vastgestelde terminalniveau

De volgende termijnen worden algemeen gebruikt door de artikelen van het Experience League, wanneer het spreken met het team DevOps, en het werken met bedrijfsteun:

* **DevOps** is een termijn die wordt gebruikt om de teams te beschrijven die de serveropstelling, de configuratie, het beheer, SSL certificaten en alles anders over de daadwerkelijke servers en de diensten behandelen die worden gebruikt om een plaats van Adobe Commerce in werking te stellen. Deze term wordt gebruikt om aan te geven wanneer de verantwoordelijkheid van een ontwikkelaar gewoonlijk eindigt en waar de reis en ondersteuning van een infrastructuurteam begint.

* **Concepten van de Veiligheid** omvatten verscheidene onderwerpen en overwegingen om de codebase van Adobe Commerce, dossiers, en dossiersysteem op de servers en om het even welke configuraties of updates te maken die de aanvalsoppervlakte voor vele bekende exploitatiepatronen verminderen.

* **de Controle Hulpmiddelen** behandelt een paar bestaande hulpmiddelen en de diensten die websites van Adobe Commerce controleren. Deze gereedschappen kunnen soms tips geven voor het verbeteren van zaken of het opsporen van problemen en beveiligingsproblemen.

* **de hulp van de Terugwinning van de Ramp** verstrekt sommige concepten en overwegingen voor het ongelukkige geval van een beschadigd of geëxploiteerd project.

* **uiteinden van Prestaties** verstrekken sommige pro uiteinden en begeleiding voor het maken van de toepassing van Adobe Commerce zo presterend mogelijk zijn.

* **Onjuiste actor** is de termijn die voor een persoon of een team wordt gebruikt die probeert om iets kwaadwillig of onbevoegd te doen. Het is niet beperkt tot de handelstoepassing, maar is ook van toepassing op de infrastructuur of een component die met de website verband houdt.

* **de hulp van de Firewall van de Toepassing van het Web van 0} {door elke verzoekrubriek naar de handelstoepassing te letten en blokkeert bekende patronen en exploiteert.** Vaak wordt een WAF gebruikt samen met douanefilters en regels helpen de aanvallen van DDOS beheren.

* **Verspreid Ontkenning van Dienst** (DDoS) is een methode van aanval om de servers te dwingen die de website in werking stellen met vals verzoek met genoeg volume worden verbruikt dat zij niet meer aan wettig verzoek kunnen antwoorden.

## Wat is de volgende?

Deze onderwerpen staan niet in een speciale volgorde of volgorde. Ze zijn bedoeld om gesprekspunten te bieden aan een DevOps-engineer, de Commerce Architect, en aan iedereen die betrokken is bij het nemen van deze belangrijke beslissing over waar en hoe Adobe Commerce moet worden gehost.

{{$include /help/_includes/hosting-related-links.md}}
