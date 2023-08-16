---
title: Managed Services
description: Controleer de verantwoordelijkheden van Adobe Managed Services, klanten en cloudserviceproviders voor uw Adobe Commerce voor de implementatie van cloudinfrastructuur.
exl-id: b1442e31-06f4-4aa6-b24a-b6cda630d52f
feature: Cloud, Services
source-git-commit: 7c2e2bdabf47e1367ffb6761230d3d43f0f9d0cf
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---

# Beheerde services

Adobe Commerce op services met beheer van cloudinfrastructuur is standaard veilig.

![Diagram met door Adobe Commerce beheerde services](../../../assets/playbooks/managed-services.svg)

## Gedeelde verantwoordelijkheid

Adobe Commerce Pro-plannen zijn gebaseerd op een beveiligingsmodel voor gedeelde verantwoordelijkheid. In dit model zijn verschillende partijen verantwoordelijk voor het handhaven van de veiligheid van het systeem. Deze benadering maakt zowel flexibiliteit mogelijk als gebruik van de beste cloudtechnologieën.

![Diagram met Adobe Commerce-model voor gedeelde verantwoordelijkheid](../../../assets/playbooks/shared-responsibility.svg)

### Adobe Managed Services-verantwoordelijkheden

Adobe Managed Services is verantwoordelijk voor de beveiliging en beschikbaarheid van de Adobe Commerce Pro-cloudomgeving, de belangrijkste Adobe Commerce Pro-toepassingscode en interne handelssystemen. Dit omvat onder meer, maar is niet beperkt tot:

- Reparatie op serverniveau
- De vereiste services gebruiken voor het uitvoeren van Adobe Commerce Pro-plannen
- Kwetsbaarheid testen
- Logboekregistratie en bewaking van beveiligingsgebeurtenissen
- Incidentbeheer
- Operationeel toezicht
- 24/7-ondersteuning
- Ervoor zorgen dat de infrastructuur van de klant beschikbaar is in overeenstemming met SLA&#39;s

Adobe Managed Services is ook verantwoordelijk voor het beheer van configuraties van de serverfirewall (iptables) en firewallconfiguraties van de perimeter (veiligheidsgroepen). Adobe kan ook regelmatig beveiligingsupdates voor de kerntoepassing vrijgeven. Het is de verantwoordelijkheid van de klant om deze patches toe te passen. Deze gebieden vallen allemaal onder de PCI-certificering van de Adobe Commerce op het systeem van de cloudinfrastructuur.

### AWS-verantwoordelijkheden

Adobe Managed Services gebruikt Amazon Web Services (AWS) voor cloudserverinfrastructuur. AWS is verantwoordelijk voor de veiligheid van het netwerk, met inbegrip van het verpletteren, het schakelen, en de veiligheid van het perimeternetwerk via firewallsystemen en de systemen van de binnendringenopsporing (IDS). AWS is verantwoordelijk voor de fysieke beveiliging van de datacenters die de Adobe Commerce-cloudomgevingen beheren, en voor de beveiliging van het milieu, zodat de juiste besturingselementen voor voeding, koeling en mechanisme zijn geïnstalleerd.

Voor Adobe Commerce Pro-plannen:

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service (S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Amazon Elastic Load Balancer (ELB)
- Amazon Cloud Trail Services.

Amazon heeft een uitgebreid nalevingsprogramma, dat PCI DSS, SOC 2, en de certificatie van ISO 27001 omvat.

### Verantwoordelijkheden van partner/klant van oplossing

De klant is in de eerste plaats verantwoordelijk voor de beveiliging van de aangepaste implementatie van de Adobe Commerce-toepassing die wordt uitgevoerd in de cloud-omgeving van het Adobe Commerce Pro-abonnement. Dit omvat:

- Zorgen voor een veilige configuratie en codering van de activiteiten voor toepassings- en beveiligingscontrole, inclusief penetratietests en reguliere kwetsbaarheidsscans.

- De beveiliging van aanpassingen, extensies, andere toepassingen of integraties die in het systeem worden gebruikt.

- De veiligheid van hun gebruikers en het verlenen van toegang tot hun configuratie en toepassing.

- De klant bestuurt alle codeplaatsingen aan hun niet-productiemilieu&#39;s. Deze controle wordt ook geleverd met de verantwoordelijkheid om toepassings veiligheidspatches op de kerntoepassing van Adobe Commerce, uitbreidingen, of om het even welke douanecode toe te passen.

- De klant moet de penetratietests van zijn aangepaste toepassing uitvoeren. Deze verantwoordelijkheden kunnen door technische middelen door de klant, implementatiepartners, of de professionele diensten van Adobe Commerce worden gericht.

- Klanten zijn verantwoordelijk voor de PCI-vereisten van hun aangepaste toepassing en hun eigen processen. De PCI-compatibiliteit van de klant is gebaseerd op de PCI-certificeringen van AWS en Adobe Commerce om de gebieden die moeten worden gecontroleerd, tot een minimum te beperken.
