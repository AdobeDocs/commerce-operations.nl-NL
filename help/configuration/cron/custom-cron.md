---
title: Cron-taken
description: Meer informatie over uitsnijdgroepen en het maken van een aangepaste uitsnijdtaak.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---

# Cron-taken

In deze onderwerpen wordt besproken hoe u een aangepaste uitsnijdtaak en eventueel een aangepaste uitsnijdgroep instelt. Als uw uitbreiding van Commerce regelmatige taken vereist om periodiek in werking te stellen, kunt u deze onderwerpen aan opstelling gebruiken een baan van de kruin __ (de geplande taak) en naar keuze een kruin _groep_, die douanetaken tezelfdertijd in werking stelt.

Als u een door Commerce verschafte uitsnijdgroep gebruikt, hoeft u geen aangepaste uitsnijdgroep te definiëren. Als u echter wilt dat de uitsnijdtaken volgens een ander schema worden uitgevoerd of dat ze allemaal samen worden uitgevoerd, moet u een uitsnijdgroep definiëren

De Commerce-toepassing biedt de volgende uitsnijdgroepen:

- `default` , dat de meeste snijtaken bevat
- `index`, die [ indexeerders ](../cli/manage-indexers.md) vernieuwt
- `consumers`, die berichtrij [ consumenten ](../cli/start-message-queues.md) in werking stelt
- Deze onderwerpen zijn alleen beschikbaar in Adobe Commerce
   - `staging`, die [ op Staging betrekking hebbende ](https://experienceleague.adobe.com/en/docs/commerce-admin/content-design/staging/content-staging) taken in werking stelt
   - `catalog_event` , dat taken voor doel en het winkelwagentje regels uitvoert
