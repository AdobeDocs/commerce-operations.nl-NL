---
title: Het tabblad [!UICONTROL Elasticsearch]
description: Leer meer over het [!UICONTROL Elasticsearch] lusje van  [!DNL Observation for Adobe Commerce].
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Het tabblad [!UICONTROL Elasticsearch]

## [!UICONTROL Cluster Status Summary]:

![ Samenvatting van de Status van de Cluster ](../../assets/tools/cluster-status-summary.jpg)

Tijdens het geselecteerde tijdframe toont het **[!UICONTROL Cluster Status Summary]** -frame de kleurstatussen die de [!DNL Elasticsearch] -cluster heeft doorlopen. In dit voorbeeld was de cluster tijdens het geselecteerde tijdframe één keer groen en één keer geel in de status Geel tijdens het geselecteerde tijdframe.

## [!UICONTROL Active Primary Shards]

![ Actieve Primaire Delen ](../../assets/tools/active-primary-shards.jpg)

In het frame **[!UICONTROL Active Primary Shards]** worden de verschillende nummers weergegeven, afhankelijk van het aantal actieve primaire kaarten voor de service [!DNL Elasticsearch] van het geselecteerde account.

Van [!DNL Elasticsearch]: De definitieve Gids [ 2.x ]:

&quot;In [ dynamisch Updatable Indices ](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html), verklaarden wij dat een speld een index van Lucene is en dat een [!DNL Elasticsearch] index een inzameling van schepen is. Uw toepassing praat met een index, en [!DNL Elasticsearch] leidt uw verzoeken aan de aangewezen plaatsen. Een plank is de schaaleenheid. De kleinste index die u kunt hebben, is één met één enkele ruit. Dit kan meer dan voldoende zijn voor je behoeften — één enkele kaart kan veel gegevens bevatten — maar het beperkt je mogelijkheden om te schalen.&quot;

Wanneer een index wordt gecreeerd, zijn er verscheidene kaarten die met die index worden gecreeerd. Door gebrek, worden vijf primaire plaatsen toegewezen aan elke nieuwe index, die betekent dat een index over vijf knopen (één shard per knoop) kan worden verspreid. Er zijn ook replicaplanken. Deze zijn hoofdzakelijk voor failover. Replica-kaarten kunnen worden gebruikt voor leesverzoeken.

## [!UICONTROL Active Shards in Cluster]

![ Actieve delen in Cluster ](../../assets/tools/active-shards-in-cluster.jpg)

In het frame **[!UICONTROL Active Shards in Cluster]** wordt het totale aantal primaire en replica-shards in een [!DNL Elasticsearch] -cluster weergegeven.

## [!UICONTROL Index health - this will show the index name and color status]

](../../assets/tools/index-health.jpg) gezondheid van 0} Index![

In dit frame worden de naam van de index en het aantal statussen van de indexkleur weergegeven. Als u de tabel omlaag schuift, ziet u dezelfde indexnaam met de kleurstatus Geel en Rood. Het getal dat volgt op de 27 indexnaam is het getal van de statuskleur. Als de waarde nul is, waren er geen gevallen waarin de index zich in die kleurstatus bevond tijdens de geselecteerde tijdframes.

## [!UICONTROL Elasticsearch Status by node information]

![ Status van de Elasticsearch ](../../assets/tools/elasticsearch-status-by-node.jpg)

In het frame **[!UICONTROL Elasticsearch Status by node information]** wordt de clusterstatus van [!DNL Elasticsearch] weergegeven op kleur en knooppunt. Op deze manier kunt u aangeven welk knooppunt in de [!DNL Elasticsearch] -cluster de status retourneert tijdens de geselecteerde tijdsperiode.

## [!UICONTROL Elasticsearch index information]

![ de indexinformatie van de Elasticsearch ](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

In de tabel **[!UICONTROL Elasticsearch index information]** worden de indexnaam, het knooppunt waarop de tabel staat, het aantal geïndexeerde documenten, de indexstatus en de indexgrootte op een bepaald moment in MB weergegeven.

## [!UICONTROL Elasticsearch process CPU %]

![ het procescpu van de Elasticsearch ](../../assets/tools/elasticsearch-process-cpu.jpg)

Het **[!UICONTROL Elasticsearch process CPU %]** -frame toont het CPU-percentage van het proces volgens het [!DNL Elasticsearch] -proces gedurende het geselecteerde tijdframe.

## [!UICONTROL Elasticsearch Memory garbage collection]

![ garbage van het Geheugen van de Elasticsearch ](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] is een Java-proces. Als het op toegewezen geheugen laag loopt, zal het huisvuilinzameling in werking stellen om geheugen vrij te maken. Als de huisvuilinzameling frequent is, is het een aanwijzing dat er teveel indexen of schepen voor het toegewezen geheugen kunnen zijn. Het kan zijn dat u de indices en kaarten kunt opschonen, of [!DNL Elasticsearch] heeft meer geheugen nodig.

## [!UICONTROL Elasticsearch Index information]

![ de Informatie van de Index van de Elasticsearch ](../../assets/tools/elasticsearch-index-information-2.jpg)

Wanneer indexen worden gemaakt en bijgewerkt, kan de indexstatus veranderen.

## [!UICONTROL Elasticsearch Index Size]

{de grootte van de Index van 0} Elasticsearch ](../../assets/tools/elasticsearch-index-size.jpg)![

Het frame **[!UICONTROL Elasticsearch Index Size]** geeft de naam en de grootte van de index voor het geselecteerde tijdframe aan. Het kan problemen met de manier aangeven waarop een site wordt geïndexeerd.

## [!UICONTROL Elasticsearch Errors]

{de Fouten van de Elasticsearch 0} ](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)![

Het frame **[!UICONTROL Elasticsearch Errors]** bevat fouten met [!DNL Elasticsearch] zoals onvoldoende ruimte, overschakelen van de status Geel naar Rood, wanneer alle soorten zijn mislukt, wanneer er parameterproblemen zijn met zoekopdrachten, versiefouten en wanneer alle knooppunten niet beschikbaar zijn.

## [!UICONTROL Elasticsearch Unassigned Shards]:

![ Elasticsearch niet toegewezen deelt ](../../assets/tools/elasticsearch-unassigned-shards.jpg)

Niet toegewezen planken zorgen ervoor dat een cluster overschakelt van de status Groen naar de status Geel.
