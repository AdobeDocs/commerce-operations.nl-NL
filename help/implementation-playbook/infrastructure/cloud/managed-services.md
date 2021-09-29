---
title: Managed Services
description: Review the responsibilities of Adobe Managed Services, customers, and cloud service providers for your Adobe Commerce on cloud infrastructure implementaiton.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 0%

---


# Managed services

Adobe Handel op beheerde services van cloudinfrastructuur is standaard veilig.

![Diagram met de beheerde diensten van de Adobe Commerce](../../../assets/playbooks/managed-services.svg)

## Gedeelde verantwoordelijkheid

Adobe Commerce Pro plans rely on a shared responsibility security model. In this model, different parties have different areas of responsibility for maintaining the security of the system. Deze benadering maakt zowel flexibiliteit mogelijk als gebruik van de beste cloudtechnologieën.

![Diagram met het model voor gedeelde verantwoordelijkheid voor Adobe Commerce](../../../assets/playbooks/shared-responsibility.svg)

### Adobe Managed Services-verantwoordelijkheden

Adobe Managed Services is verantwoordelijk voor de beveiliging en beschikbaarheid van de Adobe Commerce Pro-cloudomgeving, de kerncode van de Adobe Commerce Pro-toepassing en interne handelssystemen. Dit omvat onder meer, maar is niet beperkt tot:

- Server-level patching
- Exploitatie van de noodzakelijke services voor de levering van Adobe Commerce Pro-plannen
- Kwetsbaarheid testen
- Security event logging and monitoring
- Incidentbeheer
- Operationeel toezicht
- 24/7 support
- Ensuring that the customer infrastructure is available in accordance with SLAs

Adobe Managed Services is ook verantwoordelijk voor het beheer van configuraties van de serverfirewall (iptables) en configuraties van de perimeterfirewall (beveiligingsgroepen). Adobe kan ook regelmatig beveiligingsupdates vrijgeven voor de kerntoepassing. It is the customers responsibility to apply these patches. These areas are all covered by the PCI Certification of the Adobe Commerce on cloud infrastructure system.

### AWS-taken

Adobe Managed Services uses Amazon Web Services (AWS) for cloud server infrastructure. AWS is responsible for the security of the network, including routing, switching, and perimeter network security via firewall systems and intrusion detection systems (IDS). AWS is verantwoordelijk voor de fysieke beveiliging van de datacenters die de Adobe Commerce-cloudomgevingen beheren, en voor de beveiliging van het milieu om te zorgen dat er adequate besturingselementen voor voeding, koeling en mechanisme aanwezig zijn.

Gebruik van Adobe Commerce Pro-plannen:

- Amazon Elastic Compute Cloud (EC2)
- Amazon Simple Storage Service (S3)
- Amazon Elastic Block Store (EBS)
- Amazon Virtual Private Cloud (VPC)
- Amazon Elastic Load Balancer (ELB)
- Amazon Cloud Trail Services.

Amazon heeft een uitgebreid nalevingsprogramma, dat PCI DSS, SOC 2, en de certificatie van ISO 27001 omvat.

### Verantwoordelijkheden van de partner/klant van de oplossing

De klant is primair verantwoordelijk voor de veiligheid van hun aangepaste implementatie van de toepassing van de Handel van de Adobe die in de het planwolomgeving van de Adobe Commerce Pro loopt. This includes:

- Zorgen voor een veilige configuratie en codering van de activiteiten voor toepassings- en beveiligingscontrole, inclusief penetratietests en reguliere kwetsbaarheidsscans.

- De beveiliging van aanpassingen, extensies, andere toepassingen of integraties die in het systeem worden gebruikt.

- De veiligheid van hun gebruikers en het verlenen van toegang tot hun configuratie en toepassing.

- The customer controls all code deployments to their non-production environments. Deze controle komt ook met de verantwoordelijkheid om de flarden van de toepassingsveiligheid op de belangrijkste toepassing van de Handel van de Adobe, uitbreidingen, of om het even welke douanecode toe te passen.

- De klant moet de penetratietests van zijn aangepaste toepassing uitvoeren. Deze verantwoordelijkheden kunnen door technische middelen door de klant, implementatiepartners, of de professionele diensten van de Handel van Adobe worden gericht.

- Klanten zijn verantwoordelijk voor de PCI-vereisten van hun aangepaste toepassing en hun eigen processen. De naleving van PCI van de klant bouwt op de certificatie PCI van AWS en de Handel van de Adobe voort om de gebieden te minimaliseren die moeten worden herzien.
