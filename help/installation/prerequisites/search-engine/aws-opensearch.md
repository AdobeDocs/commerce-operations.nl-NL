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

Adobe Commerce 2.4.5 ondersteunt het gebruik van Amazon OpenSearch Service-clusters. Deze service is de opvolger van Amazon Elasticsearch Service. In dit onderwerp wordt beschreven hoe u Commerce configureert voor het gebruik van AWS OpenSearch en hoe u gegevens van een lokale Elasticsearch- of OpenSearch-instantie migreert naar een AWS OpenSearch-cluster.

## Een AWS OpenSearch-servicedomein maken

U moet eerst een OpenSearch-instantie in AWS maken.
Lees [ Creërend en het leiden de domeinen van de Dienst van Amazon OpenSearch ](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) voor gedetailleerde instructies.

## Gegevens ophalen naar AWS OpenSearch

Zodra alles op AWS is voorbereid, is het tijd om het met gegevens te vullen.

Voor kleinere installaties raden we u aan om indices rechtstreeks op de AWS-instantie te maken, en wel om de volgende redenen:

* Het opnieuw maken van indexen is een snelle bewerking.
* Er kunnen versionverenigbaarheden tussen de oude instantie en de instantie AWS zijn, en deze kunnen worden vermeden door rechtstreeks op de instantie AWS voort te bouwen.

Grotere installaties willen mogelijk overwegen hun gegevensindexen van de bestaande instantie naar AWS te migreren. Hoewel dit de downtime kan verminderen, is er nog steeds een klein risico op incompatibiliteitsproblemen als gevolg van verschillende versies tussen de oude Elasticsearch-server en AWS.

Het is niet nodig om indexen te migreren, omdat deze gemakkelijk opnieuw kunnen worden gemaakt op het AWS-exemplaar.
Bij het migreren van gegevensindexen moet u er echter voor zorgen dat de versies van Elasticsearch/OpenSearch compatibel zijn.

Zie Amazon [ migrerend aan de instructies van de Dienst OpenSearch van Amazon ](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) voor meer informatie.

### Commerce for OpenSearch configureren

De stappen voor het vormen OpenSearch worden behandeld in [ Geavanceerd installeert ](../../advanced.md) onderwerp.

Om te testen dat de nieuwe configuratie werkt, test direct het eindpunt OpenSearch:

1. Maak een product in de Admin (bijvoorbeeld: sku=&quot;testproduct1&quot;).
1. Opnieuw indexeren via de beheerder.
1. Vraag het eindpunt OpenSearch (gevonden in AWS UI):

   Als u indexen wilt ophalen, voegt u het volgende toe: `/_cat/indices/*?v=true` aan de URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Als u producten wilt ophalen uit index, voegt u het volgende toe: `/magento2docker_product_1/_search?q=*` aan de URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Aanvullende bronnen

Voor extra informatie, zie de [ documentatie van OpenSearch AWS ](https://docs.aws.amazon.com/opensearch-service/index.html).
