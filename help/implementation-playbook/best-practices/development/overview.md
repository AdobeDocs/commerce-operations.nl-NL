---
title: Ontwikkelingsfase implementatie
description: Leer over implementatie beste praktijken voor de ontwikkelingsfase van projecten van Adobe Commerce.
exl-id: 499c16df-0e4d-4950-8169-96356bdff1a7
feature: Best Practices
role: Developer
source-git-commit: cca301a72b972d843b878fae28901a47c8fc0489
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# Ontwikkelingsfase

De ontwikkelingsfase omvat de volgende activiteiten:

- Lokale en staging-omgeving instellen
- Afdrukplanning
- Uitvoering van ticket
- Problemen oplossen
- Codeoverzicht, samenvoegen en testen
- Sprint review
- Afmelden bij klant

>[!TIP]
>
>Zie [&#x200B; algemene beste praktijken &#x200B;](general.md) voor aanbevelingen op hoog niveau over algemeen beheer van het ontwikkelingsproces.

De volgende secties bevatten informatie over best practices voor de ontwikkelingsfase.

## Codebeheer

| Beste praktijken | Beschrijving |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [&#x200B; overzicht van de Code &#x200B;](code-review.md) | Aanbevolen validatieproces om ervoor te zorgen dat de geïmplementeerde functionaliteit voldoet aan de vereisten |
| [&#x200B; Composer vs Git &#x200B;](code-management.md) | Bepaal hoe te om douanecode met aandacht voor versiebeheer, codeingewikkeldheid, en gebiedsdeelbeheer te verdelen |
| [&#x200B; Vertakkende strategie &#x200B;](git-branching.md) | Broncode beheren in Git-opslagruimten |

## Platform en diensten

| Beste praktijken | Beschrijving |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [&#x200B; bouwt en plaatsing &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html?lang=nl-NL){target="_blank"} | Beschrijft beste praktijken voor de bouw en stel stadia van Adobe Commerce op de projecten van de wolkeninfrastructuur in |
| Foutopsporing | Fouten systematisch en effectief opsporen in het Adobe Commerce-kader |
| [&#x200B; Statische inhoudsplaatsing &#x200B;](static-content-deployment.md) | Vermijd problemen met statische inhoud die niet in uw winkelruimte wordt weergegeven |
| [&#x200B; het Oplossen van problemen &#x200B;](troubleshooting.md) | Problemen met algemene Adobe Commerce-implementatie oplossen |

## Database

| Beste praktijken | Beschrijving |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [&#x200B; de wijziging van de Lijst &#x200B;](modifying-core-and-third-party-tables.md) | Bepaal hoe en wanneer om Adobe Commerce en derdegegevensbestandlijsten te wijzigen |

## Bestanden optimaliseren

| Beste praktijken | Beschrijving |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [&#x200B; het beeld van de Catalogus resizing &#x200B;](catalog-image-resizing.md) | Biedt richtlijnen voor het vergroten of verkleinen van afbeeldingen voordat een winkel in productie wordt genomen voor optimale prestaties |
| [&#x200B; CSS en JS &#x200B;](optimize-css-js-files.md) | Cascading Style Sheet (CSS)- en JavaScript-bestanden (JS) samenvoegen en miniaturen via Beheer of de opdrachtregel |
| [&#x200B; Beelden &#x200B;](image-optimization.md) | Afbeeldingen optimaliseren en snel gebruiken om de responstijd te optimaliseren |

## Frontendement

| Beste praktijken | Beschrijving |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [&#x200B; de ontwikkeling van het Thema &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/best-practices/){target="_blank"} | Beschrijft ontwikkelingspatronen helpen verzekeren verenigbaarheid tussen uw thema, toekomstige versies van Adobe Commerce, en douanetoevoegdheden |

## PHP-ontwikkeling

| Beste praktijken | Beschrijving |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [&#x200B; Uitzondering behandeling &#x200B;](exception-handling.md) | Beschrijft geadviseerde methodes om uitzonderingen te registreren |
| [&#x200B; Uitbreidingen &#x200B;](https://developer.adobe.com/commerce/php/best-practices/){target="_blank"} | Beschrijft ontwikkelingspatronen helpen verzekeren verenigbaarheid tussen uw uitbreiding, toekomstige versies van Adobe Commerce, en andere douaneuitbreidingen |
| [&#x200B; Privé inhoudsblokken &#x200B;](private-content-block-configuration.md) | Private-inhoudsblokken configureren om de prestaties van de winkel te optimaliseren |
| [&#x200B; wijzig kern en derde PHP code &#x200B;](modifying-core-and-third-party-code.md) | De functionaliteit, het resultaat of de invoer wijzigen van code die u niet hebt gemaakt of die u niet rechtstreeks beheert |
