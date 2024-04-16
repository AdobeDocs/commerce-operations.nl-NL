---
title: AWS OpenSearch
description: Voer de volgende stappen uit om de AWS OpenSearch-webservice te configureren voor installaties in de vestiging van Adobe Commerce.
feature: Install, Search
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce 2.4.5 ondersteunt het gebruik van Amazon OpenSearch Service-clusters. Deze service is de opvolger van Amazon Elasticsearch Service. Dit onderwerp beschrijft hoe te om Commerce te vormen om AWS OpenSearch te gebruiken, en hoe te om gegevens van een lokale Elasticsearch of instantie te migreren OpenSearch aan een cluster van AWS OpenSearch.

## Een AWS OpenSearch-servicedomein maken

U moet eerst een OpenSearch-instantie in AWS maken.
Lezen [Amazon OpenSearch Service-domeinen maken en beheren](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) voor gedetailleerde instructies.

## Gegevens ophalen naar AWS OpenSearch

Zodra alles op AWS is voorbereid, is het tijd om het met gegevens te vullen.

Voor kleinere installaties raden we u aan om indices rechtstreeks op de AWS-instantie te maken, en wel om de volgende redenen:

* Het opnieuw maken van indexen is een snelle bewerking.
* Er kunnen versionverenigbaarheden tussen de oude instantie en de instantie AWS zijn, en deze kunnen worden vermeden door rechtstreeks op de instantie AWS voort te bouwen.

Grotere installaties willen mogelijk overwegen hun gegevensindexen van de bestaande instantie naar AWS te migreren. Hoewel dit downtime kan verminderen, is er nog steeds een klein risico op incompatibiliteitsproblemen als gevolg van verschillende versies tussen de oude Elasticsearch server en AWS.

Het is niet nodig om indexen te migreren, omdat deze gemakkelijk opnieuw kunnen worden gemaakt op het AWS-exemplaar.
Wanneer u echter gegevensindexen migreert, moet u ervoor zorgen dat de versies van Elasticsearch/OpenSearch compatibel zijn.

Zie Amazon [Migreren naar Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) instructies voor meer informatie .

### Commerce for OpenSearch configureren

Stappen voor het configureren van OpenSearch worden behandeld in de [Geavanceerde installatie](../../advanced.md) onderwerp.

Om te testen dat de nieuwe configuratie werkt, test direct het eindpunt OpenSearch:

1. Maak een product in de Admin (bijvoorbeeld: sku=&quot;testproduct1&quot;).
1. Opnieuw indexeren via de beheerder.
1. Vraag het eindpunt OpenSearch (gevonden in AWS UI):

   Als u indexen wilt ophalen, voegt u het volgende toe: `/_cat/indices/*?v=true` naar de URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Om producten van index te krijgen, voeg toe: `/magento2docker_product_1/_search?q=*` naar de URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Aanvullende bronnen

Zie voor meer informatie de [OpenSearch AWS-documentatie](https://docs.aws.amazon.com/opensearch-service/index.html).
