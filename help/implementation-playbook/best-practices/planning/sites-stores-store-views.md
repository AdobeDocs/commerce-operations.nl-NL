---
title: Aanbevolen werkwijzen voor het configureren van sites, winkels en winkelweergaven
description: Leer beste praktijken voor het vormen van plaatsen, opslag, en opslagmening om plaatsprestaties te maximaliseren.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Beste praktijken voor het vormen van plaatsen, opslag en opslagmening

Voor de beste prestaties van de site configureert u maximaal 50 sites, 50 winkels en 50 winkelweergaven voor Adobe Commerce op projecten met cloudinfrastructuur.

>[!NOTE]
>
>Voor Adobe Commerce op cloudinfrastructuur zijn de beste werkwijzen specifiek van toepassing op de productieomgeving (en mogelijk op de Pro-architectuur, afhankelijk van de beperkingen van de resources), die meer middelen zou hebben dan de integratie- en ontwikkelomgevingen. Voor integratie (Pro en Starter) en het Opvoeren milieu&#39;s (Starter), verminder het aantal opslagmeningen tot minder dan 5 of 10 (onderworpen aan technische controle).

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Strategieën om de prestaties te verbeteren

Als voor uw project een groot aantal sites, winkels of winkelweergaven nodig is, kunt u de volgende strategieën gebruiken om de prestaties te verbeteren:

- Catalogus herstructureren door logica naar categorieën te verplaatsen
- Scheid prijslijsten van catalogusgegevens door externe prijs en een Prijsbeheersysteem (PMS) te gebruiken.
- Een alternatieve gegevensopslag zonder SQL gebruiken, zoals Elasticsearch

## Mogelijke gevolgen voor de prestaties

Websites en winkels zijn multipliers voor catalogusgegevens, zodat het hebben van veel websites en winkels de prestaties van sites op de volgende manieren negatief kan beïnvloeden:

- Grotere indextabellen vergen de tijd die nodig is om indexeringsbewerkingen te voltooien [Prijsindex].
- De hogere tijd om toepassingsconfiguratie terug te winnen degradeert storefront reactietijd voor niet caching cataloguspagina&#39;s.
- Er is aanzienlijk meer tijd nodig om opslagbewerkingen in de beheerder uit te voeren, aangezien de gegevens voor elke website afzonderlijk worden opgeslagen.


## Aanvullende informatie

- [Werken met websites, winkels en winkelweergaven](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Meerdere websites of winkels instellen](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
