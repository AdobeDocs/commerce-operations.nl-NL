---
title: AWS OpenSearch
description: Voer de volgende stappen uit om de AWS OpenSearch-webservice te configureren voor installaties in de bedrijfsruimten van Adobe Commerce en Magento Open Source.
exl-id: 39ca7fd0-e21f-4f14-bda6-ff00a61a1a4d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# AWS OpenSearch

Adobe Commerce en Magento Open Source 2.4.5 ondersteunen het gebruik van Amazon OpenSearch Service-clusters. Deze service is de opvolger van Amazon Elasticsearch Service. Dit onderwerp beschrijft hoe te om Handel te vormen om AWS OpenSearch te gebruiken, en hoe te om gegevens van een lokale instantie te migreren Elasticsearch of OpenSearch aan een cluster OpenSearch van AWS.

## Een AWS OpenSearch-servicedomein maken

U moet eerst een OpenSearch-instantie in AWS tot stand brengen.
Lezen [Amazon OpenSearch Service-domeinen maken en beheren](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/createupdatedomains.html) voor gedetailleerde instructies.

## Gegevens ophalen naar AWS OpenSearch

Zodra alles op AWS is voorbereid, is het tijd om het met gegevens te vullen.

Voor kleinere installaties raden we u aan om indices rechtstreeks op de AWS-instantie te maken, en wel om de volgende redenen:

* Het opnieuw maken van indexen is een snelle bewerking.
* Er kunnen versionverenigbaarheden tussen de oude instantie en de instantie AWS zijn, en deze kunnen worden vermeden door rechtstreeks op de instantie AWS voort te bouwen.

Grotere installaties willen mogelijk overwegen hun gegevensindexen van de bestaande instantie naar AWS te migreren. Hoewel dit downtime kan verminderen, is er nog steeds een klein risico op incompatibiliteitsproblemen als gevolg van verschillende versies tussen de oude Elasticsearch-server en AWS.

Het is niet nodig om indexen te migreren, omdat deze gemakkelijk opnieuw kunnen worden gemaakt op het AWS-exemplaar.
Zorg er echter voor dat de versies van Elasticsearch/OpenSearch compatibel zijn wanneer u gegevensindices migreert.

Zie Amazon [Migreren naar Amazon OpenSearch Service](https://docs.aws.amazon.com/opensearch-service/latest/developerguide/migration.html) instructies voor meer informatie .

### Handel configureren voor OpenSearch

Stappen voor het configureren van OpenSearch worden behandeld in de [Geavanceerde installatie](../../advanced.md) onderwerp.

Om te testen dat de nieuwe configuratie werkt, test direct het eindpunt OpenSearch:

1. Een product maken in de beheerfunctie (bijvoorbeeld: sku=&quot;testproduct1&quot;).
1. Opnieuw indexeren via de beheerder.
1. Vraag het eindpunt OpenSearch (gevonden in AWS UI):

   Als u indexen wilt ophalen, voegt u het volgende toe: `/_cat/indices/*?v=true` naar de URL:
   `<AWS OS endpoint>/_cat/indices/*?v=true`

Om producten van index te krijgen, voeg toe: `/magento2docker_product_1/_search?q=*` naar de URL:
`<AWS OS endpoint>/magento2docker_product_1/_search?q=testproduct1`

## Aanvullende bronnen

Zie voor meer informatie de [OpenSearch AWS-documentatie](https://docs.aws.amazon.com/opensearch-service/index.html).
