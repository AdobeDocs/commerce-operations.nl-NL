---
title: Hardwareaanbevelingen
description: Meer informatie over hardwareaanbevelingen voor optimale Adobe Commerce-prestaties. Ontdek CPU-, geheugen- en opslagvereisten voor productieimplementaties.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Aanbevelingen voor hardware

## CPU&#39;s

[!DNL Commerce] -webknooppunten dienen voor alle aanvragen die niet in de cache zijn opgeslagen of die niet in de cache kunnen worden opgeslagen via de toepassing. Eén CPU-core kan op effectieve wijze ongeveer twee (soms wel vier) [!DNL Commerce] -aanvragen verwerken. Gebruik de volgende vergelijking om te bepalen hoeveel Webknopen/cores u alle inkomende verzoeken moet verwerken zonder hen in rij te zetten:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Als u verwacht dat de lading van een opslag verandert, kunt u het aantal Webknopen/cores voor een actieve verkoopperiode manueel verhogen. U kunt ook een model voor automatisch schalen gebruiken om automatisch weblagen uit te breiden.

## Geheugen

### PHP

Magento heeft verschillende PHP-geheugenvereisten, afhankelijk van hoe uw systeem wordt geïmplementeerd.  Over het algemeen raden we u aan PHP-geheugen voor 2G te configureren als u één serverwinkel instelt.  Als u een site instelt met behulp van pijpleidingimplementatie, raden we u aan 2 GB aan te houden op uw buildserver en 1 GB aan te schaffen op uw webknooppunten.

Scenario&#39;s en verwachte PHP-geheugenvereisten:

* Webnode die alleen winkelpagina&#39;s bedient: 256 MB
* Webnode die beheerpagina&#39;s bedient met een grote catalogus: 1 GB
* [!DNL Commerce] begin het indexeren van een plaats met een grote catalogus: >256 MB (Zie [&#x200B; geavanceerd-opstelling &#x200B;](../performance/advanced-setup.md) om voor optimale prestaties te stemmen.)
* [!DNL Commerce] statische elementen compileren en implementeren: 756 MB
* [!DNL Commerce] krachtige toolkit profile generation: > 1 GB PHP RAM, > 16 MB [!DNL MySQL] TMP_TABLE_SIZE &amp; MAX_HEAP_TABLE_SIZE settings

### [!DNL MySQL]

De [!DNL Commerce] -database (en elke andere database) is gevoelig voor de hoeveelheid geheugen die beschikbaar is voor het opslaan van gegevens en indexen. Als u [!DNL MySQL] -gegevensindexatie effectief wilt benutten, moet de hoeveelheid beschikbaar geheugen minimaal ongeveer de helft van de grootte van de gegevens die in de database zijn opgeslagen, bedragen.

### Cursussen

Als u meerdere [!DNL Commerce] implementeert en Redis of [!DNL Varnish] voor uw cache gebruikt, moet u de volgende principes in acht nemen:

* [!DNL Varnish] De validatie van het cachegeheugen van de volledige pagina is effectief. U kunt het beste voldoende geheugen toewijzen aan [!DNL Varnish] om de populairste pagina&#39;s in het geheugen op te slaan
* Het geheime voorgeheugen van de zitting is een goede kandidaat om voor een afzonderlijk geval van Redis te vormen.  De configuratie van het geheugen voor dit geheim voorgeheugentype zou de strategie van de het kartafstand van de plaats moeten overwegen en hoe lang een zitting in het geheime voorgeheugen zou moeten blijven
* Redis moet voldoende geheugen hebben toegewezen om alle andere cache in het geheugen te bewaren voor optimale prestaties.  Het geheime voorgeheugen van het blok zal de belangrijkste factor in het bepalen van de hoeveelheid geheugen zijn te vormen.  Het cachegeheugen van een blok wordt groter ten opzichte van het aantal pagina&#39;s op een site (aantal skus x aantal winkelweergaven)

## Netwerkbandbreedte

Voldoende netwerkbandbreedte is een van de belangrijkste vereisten voor gegevensuitwisseling tussen webknooppunten, database(s), caching/session-servers en andere services. Omdat [!DNL Commerce] effectief caching voor hoge prestaties gebruikt, kan uw systeem actief gegevens met caching servers zoals Redis uitwisselen. Als Redis zich op een externe server bevindt, moet u een voldoende netwerkkanaal tussen webknooppunten en de caching-server opgeven om knelpunten bij lees- en schrijfbewerkingen te voorkomen.
