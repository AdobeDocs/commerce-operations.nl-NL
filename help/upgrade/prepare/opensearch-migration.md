---
title: Migreren van Elasticsearch naar OpenSearch
description: Meer informatie over het vervangen van de zoekmachine die wordt gebruikt voor installaties in Adobe Commerce en Magento Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# Migreren naar OpenSearch

OpenSearch is een open-source vork van Elasticsearch 7.10 die is gemaakt na een licentiewijziging van Elasticsearch 2.

Vanaf 2.4.4, 2.4.3-p2, en 2.3.7-p3, steunen Adobe Commerce en Magento Open Source OpenSearch. Installaties op locatie blijven Elasticsearch ondersteunen, maar worden niet meer ondersteund voor Adobe Commerce op cloudinfrastructuur.

## Migratiepad

De stappen om naar OpenSearch te migreren zijn eenvoudig en volgen grotendeels de stappen voor de configuratie van Elasticsearch. Bij deze stappen wordt ervan uitgegaan dat Adobe Commerce de enige toepassing is die de zoekfunctie gebruikt. Wanneer meerdere toepassingen de zoekmachine gebruiken, volgt u de officiële migratiehandleiding [Van opensource-Elasticsearch naar OpenSearch verplaatsen](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Zorg ervoor dat uw installatie voldoet aan de [vereisten voor zoekprogramma&#39;s](../../installation/prerequisites/search-engine/overview.md).

1. Plaats de site in [Onderhoudsmodus](../../installation/tutorials/maintenance-mode.md).

1. Desgewenst Elasticsearch verwijderen.

1. [OpenSearch installeren](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [De zoekfunctie configureren](../../configuration/search/configure-search-engine.md) en voer verwante taken uit, zoals het leegmaken van de cache en het opnieuw indexeren van de zoekindex van de catalogus.

Wijzigingen in configuratiewaarden zijn niet meer nodig.
