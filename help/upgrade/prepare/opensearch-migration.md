---
title: Migreren van Elasticsearch naar OpenSearch
description: Meer informatie over het vervangen van de zoekmachine die wordt gebruikt voor installaties in Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Migreren naar OpenSearch

OpenSearch is een open-source vork van Elasticsearch 7.10.2 die is gemaakt na de licentiewijziging van de Elasticsearch.

Vanaf 2.4.4, 2.4.3-p2, en 2.3.7-p3, steunt Adobe Commerce OpenSearch. Installaties ter plaatse blijven ondersteuning bieden voor Elasticsearch, maar worden niet meer ondersteund voor Adobe Commerce op cloudinfrastructuur. Vanaf versie 2.4.6 heeft OpenSearch een eigen module en velden in de beheerconfiguratie-instellingen.

## Migratiepad

De stappen om naar OpenSearch te migreren zijn eenvoudig en volgen grotendeels de stappen voor de configuratie van de Elasticsearch. Bij deze stappen wordt ervan uitgegaan dat Adobe Commerce de enige toepassing is die de zoekfunctie gebruikt. In gevallen waar de veelvoudige toepassingen de onderzoeksmotor gebruiken, volg de officiële migratiegids [ Bewegend van open bron Elasticsearch aan OpenSearch ](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Zorg ervoor dat uw installatie aan de [ eerste vereisten van de onderzoeksmotor ](../../installation/prerequisites/search-engine/overview.md) voldoet.

1. Plaats de plaats in [ Wijze van het Onderhoud ](../../installation/tutorials/maintenance-mode.md).

1. Desinstalleer desgewenst Elasticsearch.

1. [ installeer OpenSearch ](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [ vorm de onderzoeksmotor ](../../configuration/search/configure-search-engine.md) en voer verwante taken uit, zoals het leegmaken van het geheime voorgeheugen en het opnieuw indexeren van de index van het catalogusonderzoek.

Wijzigingen in configuratiewaarden zijn niet meer nodig.
