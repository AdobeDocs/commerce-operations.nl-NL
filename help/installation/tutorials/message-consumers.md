---
title: Berichtconsumenten configureren
description: Voer de volgende stappen uit om het gedrag van gebruikers in de wachtrij met Adobe Commerce- of Magento Open Source-berichten te configureren.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# Berichtconsumenten configureren

Voordat u deze opdracht uitvoert, moet u het volgende doen: *of* u moet [de toepassing installeren](../advanced.md):

* [Implementatieconfiguratie maken of bijwerken](deployment.md)
* [Het databaseschema maken](database.md)

## Het gedrag van de consument configureren

Het vormen van consumentengedrag wordt gedaan door sleutel/waardeparen binnen de opstellingsfunctie te verzenden:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschrijvingen

{{$include /help/_includes/cli-consumers.md}}
