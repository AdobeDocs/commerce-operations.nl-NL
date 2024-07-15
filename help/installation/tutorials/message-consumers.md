---
title: Berichtconsumenten configureren
description: Voer de volgende stappen uit om het gedrag van gebruikers in de wachtrij met Adobe Commerce-berichten te configureren.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# Berichtconsumenten configureren

Alvorens u dit bevel in werking stelt, moet u het volgende *doen of* u moet [ de toepassing ](../advanced.md) installeren:

* [Implementatieconfiguratie maken of bijwerken](deployment.md)
* [Het databaseschema maken](database.md)

## Het gedrag van de consument configureren

Het vormen van consumentengedrag wordt gedaan door sleutel/waardeparen binnen de opstellingsfunctie te verzenden:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeschrijvingen

{{$include /help/_includes/cli-consumers.md}}
