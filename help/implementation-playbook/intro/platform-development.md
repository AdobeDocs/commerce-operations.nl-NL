---
title: Principles of Platform Development
description: Understand fundamental platform development principles when working with Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Beginselen van platformontwikkeling

In dit playbook duiken we dieper in enkele van de belangrijkste normen van de ontwikkeling van de Adobe Handel, met inbegrip van:

- Functionele en technische bereikregels in overeenstemming met het ontwikkelingsproces
- De beste praktijken van de ontwikkeling die op de architectuur MVC worden gericht
- Architectuuroverwegingen, met inbegrip van GRA
- Beveiligingsnormen tegen scripts en misbruik
- Extension development best practices
- Web API-integratie met REST, SOAP en GraphQL
- Prestatieverbeteringen voor codering en infrastructuur
- Testgereedschappen, -strategieën en -methoden

While some solution implementers may have their own preferences when it comes to the methodologies, processes, and tools used throughout an implementation project, this playbook focuses on generally accepted best practices and methodologies that can be shared across the majority of implementations.

Net als bij elk groot IT-project is Adobe Commerce gebaseerd op coderingsstandaarden die best practices en standaardiseringen van de onderliggende technologieën (bijvoorbeeld PHP/Zend, Symfony, JavaScript, jQuery en HTML) gebruiken, en op standaarden die zijn vastgelegd in de norm voor Adobe Commerce Coding. Het naleven van deze normen is een absolute must om insecten te elimineren en de kwaliteit en het onderhoud van douane-gebouwde code te verbeteren.

## Adobe Handel in cloudinfrastructuur

Adobe Commerce op cloudinfrastructuur is een beheerd, geautomatiseerd hostingplatform voor de Adobe Commerce-software. De Handel van de Adobe op wolkeninfrastructuur komt met een verscheidenheid van extra eigenschappen die het behalve op-gebouw Adobe Handel en Magento Open Source implementaties plaatst:

![Adobe Commerce component infgraphics](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce op cloudinfrastructuur biedt een vooraf ingerichte infrastructuur die PHP-, MySQL-, Redis-, RabbitMQ- en Elasticsearch-technologieën omvat; een op Git-Gebaseerde werkschema met automatische bouwt en opstelt verrichtingen voor efficiënte snelle ontwikkeling en ononderbroken plaatsing telkens als de codeveranderingen in een Platform als milieu van de Dienst (PaaS) worden geduwd; zeer aanpasbare milieu-configuratiedossiers en hulpmiddelen; en AWS-hosting die een schaalbare en veilige omgeving biedt voor online verkoop en detailhandel.

![Adobe Commerce component infgraphics](../../assets/playbooks/cloud-tech-stack.svg)
