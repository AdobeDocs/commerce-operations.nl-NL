---
title: Migreren van Elasticsearch naar OpenSearch
description: Meer informatie over het vervangen van de zoekmachine die wordt gebruikt voor installaties in Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Migreren naar OpenSearch

OpenSearch is een open-source vork van Elasticsearch 7.10.2 die is gemaakt na de licentiewijziging van Elasticsearch.

Vanaf 2.4.4, 2.4.3-p2, en 2.3.7-p3, steunt Adobe Commerce OpenSearch. Installaties op locatie blijven Elasticsearch ondersteunen, maar worden niet meer ondersteund voor Adobe Commerce op cloudinfrastructuur. Vanaf versie 2.4.6 heeft OpenSearch een eigen module en velden in de beheerconfiguratie-instellingen.

## Migratiepad

De stappen voor migratie naar OpenSearch zijn eenvoudig en volgen grotendeels de stappen voor Elasticsearch-configuratie. Bij deze stappen wordt ervan uitgegaan dat Adobe Commerce de enige toepassing is die de zoekfunctie gebruikt. In gevallen waar de veelvoudige toepassingen de onderzoeksmotor gebruiken, volg de officiële migratiegids [ Bewegend van open bron Elasticsearch aan OpenSearch ](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/).

1. Zorg ervoor dat uw installatie aan de [ eerste vereisten van de onderzoeksmotor ](../../installation/prerequisites/search-engine/overview.md) voldoet.

1. Plaats de plaats in [ Wijze van het Onderhoud ](../../installation/tutorials/maintenance-mode.md).

1. Desgewenst kunt u Elasticsearch verwijderen.

1. [ installeer OpenSearch ](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [ vorm de onderzoeksmotor ](../../configuration/search/configure-search-engine.md) en voer verwante taken uit, zoals het leegmaken van het geheime voorgeheugen en het opnieuw indexeren van de index van het catalogusonderzoek.

Wijzigingen in configuratiewaarden zijn niet meer nodig.
