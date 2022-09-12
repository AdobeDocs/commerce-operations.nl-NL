---
title: Berichtconsumenten configureren
description: Voer de volgende stappen uit om het gedrag van gebruikers in de wachtrij met Adobe Commerce- of Magento Open Source-berichten te configureren.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
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
