---
title: Aanbevolen werkwijzen voor het configureren van sites, winkels en winkelweergaven
description: Leer beste praktijken voor het vormen van plaatsen, opslag, en opslagmening om plaatsprestaties te maximaliseren.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Beste praktijken voor het vormen van plaatsen, opslag en opslagmening

Voor Adobe Commerce op cloudinfrastructuur zijn de beste werkwijzen specifiek van toepassing op de productieomgeving (en mogelijk op de Pro-architectuur, afhankelijk van de beperkingen van de resources), die meer middelen zou hebben dan de integratie- en ontwikkelomgevingen.

## Betrokken producten en versies

[&#x200B; Alle gesteunde versies &#x200B;](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Strategieën om de prestaties te verbeteren

Als voor uw project een groot aantal sites, winkels of winkelweergaven nodig is, kunt u de volgende strategieën gebruiken om de prestaties te verbeteren:

- Catalogus herstructureren door logica naar categorieën te verplaatsen
- Scheid prijslijsten van catalogusgegevens door externe prijs en een Prijsbeheersysteem (PMS) te gebruiken.
- Een alternatieve gegevensopslag zonder SQL gebruiken, zoals Elasticsearch

## Mogelijke gevolgen voor de prestaties

Websites en winkels zijn multipliers voor catalogusgegevens, zodat het hebben van veel websites en winkels de prestaties van sites op de volgende manieren negatief kan beïnvloeden:

- De grotere indexlijsten verhogen tijd die wordt vereist om indexerende verrichtingen [ index van de Prijs ] te voltooien.
- De hogere tijd om toepassingsconfiguratie terug te winnen degradeert storefront reactietijd voor niet caching cataloguspagina&#39;s.
- Er is aanzienlijk meer tijd nodig om opslagbewerkingen in de beheerder uit te voeren, aangezien de gegevens voor elke website afzonderlijk worden opgeslagen.


## Aanvullende informatie

- [&#x200B; Begrip websites, opslag, en opslagmeningen &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [&#x200B; Opstelling veelvoudige websites of opslag &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)
