---
title: Adobe Commerce Microservices
description: Een onderscheid maken tussen gezondheid en microdiensten, zoals deze betrekking hebben op de Adobe-handel.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Koploze en microservices

Het is belangrijk dat we geen krantenkoppen verwarren met microdiensten. Vaak horen we discussies over microdiensten in dezelfde zin als zonder kop. Het zijn totaal andere dingen. U kunt ze samen gebruiken, maar ze zijn totaal verschillende concepten.

Een microdienstenarchitectuur is een term die wordt gebruikt om de praktijk te beschrijven om een toepassing in een inzameling van kleinere, losjes gekoppelde diensten op te splitsen. Met microservices kunnen individuele back-endservices worden:

- **Geïsoleerd van elkaar** - Bijvoorbeeld, heeft de het tarief dienst geen gebiedsdeel op de catalogusdienst.

- **Implementeerde een la carte**: klanten implementeren alleen de onderdelen van de toepassing die ze nodig hebben.

- **De schaal onafhankelijk**-Middelen kan aan de hoog-vraagdiensten, zoals inventarisraadpleging worden toegewezen.

- **Autonoom ontwikkeld** - kan onafhankelijk van elkaar worden ontwikkeld en worden opgesteld.

Microservices hebben niets te maken met het afhakken van de kop van de commercestapel of de API&#39;s. Als we in de kerncode denken aan de handelsservices die zich in het achterkantoor van de Adobe Commerce bevinden, gaat het erom die services van elkaar te isoleren. Een microservicearchitectuur is dus een losse opsplitsing van al die services, zoals de prijsstellingsservices, catalogusservice en inventarisatieservice, en het isoleren van elkaar. Dit zorgt ervoor dat ze een la-kar zijn, zodat u niet alle Adobe Commerce in één keer hoeft te kopen en te implementeren.

Microservices kunnen onafhankelijk van elkaar worden geschaald en autonoom worden ontwikkeld. Microservices lijken op een SaaS-ontwikkelingsproces voor meerdere huurders. Veel moderne SaaS-producten voor meerdere huurders worden ontwikkeld met behulp van een multiservice-aanpak. Zelfs de eigen SaaS-producten van Adobe, zoals Order Management, het nieuwe AI-gedreven Product Recommendations-hulpmiddel, en andere SaaS-componenten van Adobe Commerce worden ontwikkeld met behulp van een microdienstenbenadering. Om heel duidelijk te zijn, is de Handel 2.4.x van de Adobe geen microdienstenarchitectuur, maar eerder een headless architectuur.
