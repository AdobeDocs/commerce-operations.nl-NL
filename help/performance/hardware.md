---
title: Hardware Recommendations
description: Bekijk een lijst met aanbevolen hardware voor optimale prestaties van Adobe Commerce-implementaties.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Aanbevelingen voor hardware

## CPU&#39;s

[!DNL Commerce] Webknooppunten dienen voor alle aanvragen die niet in de cache zijn opgeslagen of die niet in de cache kunnen worden opgeslagen via de toepassing. Eén CPU-core kan ongeveer twee (soms maximaal vier) processors gebruiken [!DNL Commerce] verzoeken effectief. Gebruik de volgende vergelijking om te bepalen hoeveel Webknopen/cores u alle inkomende verzoeken moet verwerken zonder hen in rij te zetten:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Als u verwacht dat de lading van een opslag verandert, kunt u het aantal Webknopen/cores voor een actieve verkoopperiode manueel verhogen. U kunt ook een model voor automatisch schalen gebruiken om automatisch weblagen uit te breiden.

## Geheugen

### PHP

Magento heeft verschillende PHP geheugenvereisten, gebaseerd op hoe uw systeem wordt opgesteld.  Over het algemeen raden we u aan PHP-geheugen voor 2G te configureren als u één serverwinkel instelt.  Als u een site instelt met behulp van pijpleidingimplementatie, raden we u aan 2 GB aan te houden op uw buildserver en 1 GB aan te schaffen op uw webknooppunten.

Scenario&#39;s en verwachte PHP-geheugenvereisten:

* Webnode die alleen winkelpagina&#39;s bedient: 256 MB
* Webnode die beheerpagina&#39;s bedient met een grote catalogus: 1 GB
* [!DNL Commerce] een site met een grote catalogus indexeren: >256 MB (Zie [geavanceerd instellen](../performance/advanced-setup.md) voor optimale prestaties.)
* [!DNL Commerce] Statische elementen compileren en implementeren: 756 MB
* [!DNL Commerce] Krachtige toolkit profile generation: >1 GB PHP RAM, >16 MB [!DNL MySQL] TMP_TABLE_SIZE &amp; MAX_HEAP_TABLE_SIZE-instellingen

### [!DNL MySQL]

De [!DNL Commerce] database (en elke andere database) is gevoelig voor de hoeveelheid geheugen die beschikbaar is voor het opslaan van gegevens en indexen. Efficiënt benutten [!DNL MySQL] de gegevensindexatie, zou de hoeveelheid beschikbaar geheugen, minstens, dicht bij de helft van de grootte van de gegevens moeten zijn die in het gegevensbestand worden opgeslagen.

### Cursussen

Als u veelvoudige opstelt [!DNL Commerce] en met Redis of [!DNL Varnish] voor uw geheime voorgeheugens , let op de volgende beginselen :

* [!DNL Varnish] volledige ongeldigmaking van het paginacachegeheugen is effectief, raadt u aan voldoende geheugen toe te wijzen aan [!DNL Varnish] om uw populairste pagina&#39;s in het geheugen te houden
* Het geheime voorgeheugen van de zitting is een goede kandidaat om voor een afzonderlijk geval van Redis te vormen.  De configuratie van het geheugen voor dit geheim voorgeheugentype zou de strategie van de het kartafstand van de plaats moeten overwegen en hoe lang een zitting in het geheime voorgeheugen zou moeten blijven
* Redis moet voldoende geheugen hebben toegewezen om alle andere cache in het geheugen te bewaren voor optimale prestaties.  Het geheime voorgeheugen van het blok zal de belangrijkste factor in het bepalen van de hoeveelheid geheugen zijn te vormen.  Het cachegeheugen van een blok wordt groter ten opzichte van het aantal pagina&#39;s op een site (aantal skus x aantal winkelweergaven)

## Netwerkbandbreedte

Voldoende netwerkbandbreedte is een van de belangrijkste vereisten voor gegevensuitwisseling tussen webknooppunten, database(s), caching/session-servers en andere services. Omdat [!DNL Commerce] effectief gebruikt caching voor hoge prestaties, kan uw systeem actief gegevens met caching servers zoals Redis uitwisselen. Als Redis zich op een externe server bevindt, moet u een voldoende netwerkkanaal tussen webknooppunten en de caching-server opgeven om knelpunten bij lees- en schrijfbewerkingen te voorkomen.
