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
>Zie [ algemene beste praktijken ](general.md) voor aanbevelingen op hoog niveau over algemeen beheer van het ontwikkelingsproces.

De volgende secties bevatten informatie over best practices voor de ontwikkelingsfase.

## Codebeheer

| Beste praktijken | Beschrijving |
|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| [ overzicht van de Code ](code-review.md) | Aanbevolen validatieproces om ervoor te zorgen dat de geïmplementeerde functionaliteit voldoet aan de vereisten |
| [ Composer vs Git ](code-management.md) | Bepaal hoe te om douanecode met aandacht voor versiebeheer, codeingewikkeldheid, en gebiedsdeelbeheer te verdelen |
| [ Vertakkende strategie ](git-branching.md) | Broncode beheren in Git-opslagruimten |

## Platform en diensten

| Beste praktijken | Beschrijving |
|--------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [ bouwt en plaatsing ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html) {target="_blank"} | Beschrijft beste praktijken voor de bouw en stel stadia van Adobe Commerce op de projecten van de wolkeninfrastructuur in |
| Foutopsporing | Fouten systematisch en effectief opsporen in het Adobe Commerce-kader |
| [ Statische inhoudsplaatsing ](static-content-deployment.md) | Vermijd problemen met statische inhoud die niet in uw winkelruimte wordt weergegeven |
| [ het Oplossen van problemen ](troubleshooting.md) | Problemen met algemene Adobe Commerce-implementatie oplossen |

## Database

| Beste praktijken | Beschrijving |
|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| [ de wijziging van de Lijst ](modifying-core-and-third-party-tables.md) | Bepaal hoe en wanneer om Adobe Commerce en derdegegevensbestandlijsten te wijzigen |

## Bestanden optimaliseren

| Beste praktijken | Beschrijving |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| [ het beeld van de Catalogus resizing ](catalog-image-resizing.md) | Biedt richtlijnen voor het vergroten of verkleinen van afbeeldingen voordat een winkel in productie wordt genomen voor optimale prestaties |
| [ CSS en JS ](optimize-css-js-files.md) | Cascading Style Sheet (CSS)- en JavaScript-bestanden (JS) samenvoegen en miniaturen via Beheer of de opdrachtregel |
| [ Beelden ](image-optimization.md) | Afbeeldingen optimaliseren en snel gebruiken om de responstijd te optimaliseren |

## Frontendement

| Beste praktijken | Beschrijving |
|----------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| [ de ontwikkeling van het Thema ](https://developer.adobe.com/commerce/frontend-core/guide/best-practices/) {target="_blank"} | Beschrijft ontwikkelingspatronen helpen verzekeren verenigbaarheid tussen uw thema, toekomstige versies van Adobe Commerce, en douanetoevoegdheden |

## PHP-ontwikkeling

| Beste praktijken | Beschrijving |
|-----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
| [ Uitzondering behandeling ](exception-handling.md) | Beschrijft geadviseerde methodes om uitzonderingen te registreren |
| [ Uitbreidingen ](https://developer.adobe.com/commerce/php/best-practices/) {target="_blank"} | Beschrijft ontwikkelingspatronen helpen verzekeren verenigbaarheid tussen uw uitbreiding, toekomstige versies van Adobe Commerce, en andere douaneuitbreidingen |
| [ Privé inhoudsblokken ](private-content-block-configuration.md) | Private-inhoudsblokken configureren om de prestaties van de winkel te optimaliseren |
| [ wijzig kern en derde PHP code ](modifying-core-and-third-party-code.md) | De functionaliteit, het resultaat of de invoer wijzigen van code die u niet hebt gemaakt of die u niet rechtstreeks beheert |
