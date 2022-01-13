---
title: Adobe Commerce Microservices
description: In staat zijn onderscheid te maken tussen gezondheid en microdiensten, zoals deze betrekking hebben op Adobe Commerce.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 4e8f6ce05c14195433e7c46e6090a93a76b8b5f9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Koploze en microservices

Het is belangrijk dat we geen krantenkoppen verwarren met microdiensten. Vaak horen we discussies over microdiensten in dezelfde zin als zonder kop. Het zijn totaal andere dingen. U kunt ze samen gebruiken, maar ze zijn totaal verschillende concepten.

Een microdienstenarchitectuur is een term die wordt gebruikt om de praktijk te beschrijven om een toepassing in een inzameling van kleinere, losjes gekoppelde diensten op te splitsen. Met microservices kunnen individuele back-endservices worden:

- **Geïsoleerd van elkaar**—De prijsstellingsservice is bijvoorbeeld niet afhankelijk van de catalogusservice.

- **Een la carte implementeren**—Klanten implementeren alleen de onderdelen van de toepassing die ze nodig hebben.

- **onafhankelijk schalen**—De middelen kunnen aan de diensten van de hoge vraag, zoals inventarisraadpleging worden toegewezen.

- **Autonoom ontwikkeld**—Kan onafhankelijk van elkaar worden ontwikkeld en geïmplementeerd.

Microservices hebben niets te maken met het afhakken van de kop van de commercestapel of de API&#39;s. Als we in de kerncode denken aan de handelsservices die zich op de achterzijde van Adobe Commerce bevinden, gaat het erom die services van elkaar te isoleren. Een microservicearchitectuur is dus een losse opsplitsing van al die services, zoals de prijsstellingsservices, catalogusservice en inventarisatieservice, en het isoleren van elkaar.

Microservices kunnen onafhankelijk van elkaar worden geschaald en autonoom worden ontwikkeld. Microservices lijken op een SaaS-ontwikkelingsproces voor meerdere huurders. Veel moderne SaaS-producten voor meerdere huurders worden ontwikkeld met behulp van een multiservice-aanpak. Zelfs de eigen SaaS-producten van Adobe, zoals Order Management, het nieuwe AI-gedreven Product Recommendations-hulpmiddel en andere SaaS-componenten van Adobe Commerce, worden ontwikkeld met behulp van een microdienstenbenadering. Om heel duidelijk te zijn, Adobe Commerce 2.4.x is geen architectuur voor microservices, maar een architectuur zonder kop.
