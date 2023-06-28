---
title: Beginselen van de ontwikkeling van Platforms
description: Begrijp fundamentele beginselen voor platformontwikkeling wanneer u met Adobe Commerce werkt.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Beginselen van platformontwikkeling

In dit afspeelboek duiken we dieper in een aantal van de belangrijkste normen voor Adobe Commerce-ontwikkeling, waaronder:

- Functionele en technische bereikregels in overeenstemming met het ontwikkelingsproces
- De beste praktijken van de ontwikkeling die op de architectuur MVC worden gericht
- Architectuuroverwegingen, met inbegrip van GRA
- Beveiligingsnormen tegen scripts en misbruik
- Aanbevolen werkwijzen voor ontwikkeling van extensies
- Web API-integratie met REST, SOAP en GraphQL
- Prestatieverbeteringen voor codering en infrastructuur
- Testgereedschappen, -strategieën en -methoden

Terwijl sommige oplossingsimplementators hun eigen voorkeur kunnen hebben wanneer het over de methodologieën, de processen, en de hulpmiddelen die door een implementatieproject worden gebruikt, richt playbook zich op algemeen erkende beste praktijken en methodologieën die over de meerderheid van implementaties kunnen worden gedeeld.

Net als bij elk groot IT-project is Adobe Commerce gebaseerd op coderingsstandaarden die best practices en standaardisering van de onderliggende technologieën (bijvoorbeeld PHP/Zend, Symfony, JavaScript, jQuery en HTML) gebruiken, en op standaarden die zijn vastgelegd in de Adobe Commerce Coding Standard. Het naleven van deze normen is een absolute must om insecten te elimineren en de kwaliteit en het onderhoud van douane-gebouwde code te verbeteren.

## Adobe Commerce over cloudinfrastructuur

Adobe Commerce on cloud Infrastructure is een beheerd, geautomatiseerd hostplatform voor de Adobe Commerce-software. Adobe Commerce op cloudinfrastructuur wordt geleverd met een aantal aanvullende functies die deze infrastructuur onderscheiden van Adobe Commerce- en Magento Open Source-implementaties in de bedrijfsruimten:

![Adobe Commerce-componentgegevens](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce on cloud Infrastructure biedt een vooraf ingerichte infrastructuur, waaronder PHP, MySQL, Redis, [!DNL RabbitMQ], en Elasticsearch-technologieën; een op Git-Gebaseerde werkschema met automatische bouwt en opstelt verrichtingen voor efficiënte snelle ontwikkeling en ononderbroken plaatsing telkens als de codeveranderingen in een Platform als milieu van de Dienst (PaaS) worden geduwd; zeer aanpasbare milieu-configuratiedossiers en hulpmiddelen; en AWS hosting die een schaalbare en veilige omgeving biedt voor online verkoop en detailhandel.

![Adobe Commerce-componentgegevens](../../assets/playbooks/cloud-tech-stack.svg)
