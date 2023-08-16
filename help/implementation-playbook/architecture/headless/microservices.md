---
title: Adobe Commerce Microservices
description: U kunt onderscheid maken tussen headless en microservices zoals deze voor Adobe Commerce gelden.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
feature: Integration, Services
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Koploze en microservices

Het is belangrijk dat we geen krantenkoppen verwarren met microdiensten. Vaak horen we discussies over microdiensten in dezelfde zin als zonder kop. Het zijn totaal andere dingen. Ze kunnen samen worden gebruikt, maar het zijn totaal verschillende concepten.

Een microdienstenarchitectuur is een term die wordt gebruikt om de praktijk te beschrijven om een toepassing in een inzameling van kleinere, losjes gekoppelde diensten op te splitsen. Met behulp van microservices kunnen individuele back-endservices:

- **Geïsoleerd van elkaar**—De prijsstellingsservice is bijvoorbeeld niet afhankelijk van de catalogusservice.

- **Een la carte implementeren**—Klanten implementeren alleen de onderdelen van de toepassing die ze nodig hebben.

- **onafhankelijk schalen**—De middelen kunnen aan de diensten van de hoge vraag, zoals inventarisraadpleging worden toegewezen.

- **Zelfontwikkeld**—Kan onafhankelijk van elkaar worden ontwikkeld en geïmplementeerd.

Microservices hebben niets te maken met het afhakken van de kop van de commercestapel of de API&#39;s. Als we denken aan die handelsdiensten in de kerncode die zich in het achterkantoor van Adobe Commerce bevinden, gaat het om het isoleren van die diensten van elkaar. Een microservicearchitectuur is dus een losse opsplitsing van al die services, zoals de prijsstellingsservices, catalogusservice en inventarisatieservice, en het isoleren van elkaar.

Microservices kunnen onafhankelijk van elkaar worden geschaald en autonoom worden ontwikkeld. Microservices lijken op een SaaS-ontwikkelingsproces voor meerdere huurders. Veel moderne SaaS-producten voor meerdere huurders worden ontwikkeld met behulp van een multiservice-aanpak. Zelfs de eigen SaaS-producten van Adobe, zoals Order Management, het nieuwe AI-gedreven Product Recommendations-hulpmiddel en andere SaaS-componenten van Adobe Commerce, worden ontwikkeld met behulp van een microdienstenbenadering. Om heel duidelijk te zijn, Adobe Commerce 2.4.x is geen architectuur voor microservices, maar een architectuur zonder kop.
