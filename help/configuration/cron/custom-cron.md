---
title: Cron-taken
description: Meer informatie over uitsnijdgroepen en het maken van een aangepaste uitsnijdtaak.
exl-id: a9d83af7-9979-4653-adc9-30ffeb13a5ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Cron-taken

In deze onderwerpen wordt besproken hoe u een aangepaste uitsnijdtaak en eventueel een aangepaste uitsnijdgroep instelt. Als uw uitbreiding van de Handel geplande taken vereist om periodiek te lopen, kunt u deze onderwerpen aan opstelling gebruiken cron _baan_ (de geplande taak) en optioneel een uitsnede _groep_, die tegelijkertijd aangepaste taken uitvoert.

Als u een handel-Geleverde kroongroep gebruikt, moet u geen aangepaste kroongroep bepalen; als u echter wilt dat de taken voor uitsnijden volgens een ander schema worden uitgevoerd of dat ze allemaal tegelijk worden uitgevoerd, moet u een uitsnijdgroep definiëren

De toepassing van de Handel verstrekt de volgende kroongroepen:

- `default`, die de meeste banen in de kraan bevat
- `index`, die vernieuwt [indexeerders](../cli/manage-indexers.md)
- `consumers`, die een wachtrij met berichten uitvoert [consumenten](../cli/start-message-queues.md)
- Deze onderwerpen zijn alleen beschikbaar in Adobe Commerce
   - `staging`, die [Staging](https://docs.magento.com/user-guide/cms/content-staging.html) taken
   - `catalog_event`, die taken voor doel en winkelwagentje uitvoert
