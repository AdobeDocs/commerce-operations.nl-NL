---
title: Het databaseschema en de gegevens bijwerken
description: Voer de volgende stappen uit om uw Adobe Commerce- of Magento Open Source-databaseschema bij te werken.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---


# Het databaseschema en de gegevens bijwerken

Voordat u deze opdracht gebruikt, moet u [de toepassing installeren](../advanced.md).

## Het databaseschema en de gegevens bijwerken

Telkens wanneer u een actie uitvoert die het gegevensbestandschema of de gegevens om veroorzaakt te veranderen, moet u hen bijwerken door het bevel in werking te stellen dat in deze sectie wordt besproken. Hieronder volgt een gedeeltelijke motivering:

* U hebt de toepassing bijgewerkt via de opdrachtregel
* U hebt een component geïnstalleerd of bijgewerkt via de opdrachtregel
* U hebt een component in- of uitgeschakeld via de opdrachtregel

>[!NOTE]
>
>A *component* kan een module, thema, of taalpak zijn; het maakt niet uit of de component uit de Commerce Marketplace komt of niet.

1. Start de upgrade:

   ```bash
   bin/magento setup:upgrade [--keep-generated]
   ```

   Wanneer `--keep-generated` is een optioneel argument dat niet wordt bijgewerkt [statische weergavebestanden](../../configuration/cli/static-view-file-deployment.md). Dit optionele argument is for use *alleen* in beperkte omstandigheden door ervaren systeemintegrators. Het moet worden gebruikt *alleen* in [productiemodus](../../configuration/bootstrap/application-modes.md#production-mode). Het moet *niet* worden gebruikt in [ontwikkelmodus](../../configuration/bootstrap/application-modes.md#developer-mode).

1. De cache reinigen:

   ```bash
   bin/magento cache:clean
   ```
