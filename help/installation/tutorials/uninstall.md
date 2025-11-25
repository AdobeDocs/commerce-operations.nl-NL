---
title: Adobe Commerce verwijderen of opnieuw installeren
description: Voer de volgende stappen uit om installaties in Adobe Commerce te verwijderen en opnieuw te installeren.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Adobe Commerce verwijderen of opnieuw installeren

Alvorens u deze bevelen gebruikt, moet u [&#x200B; de toepassing &#x200B;](../tutorials/install.md) installeren.

## De toepassing bijwerken

De toepassing bijwerken:

* Als u de software van een archief installeerde of als u &quot;composer-creeer-project&quot;gebruikte, zie de [&#x200B; Gids van de Verbetering &#x200B;](../../upgrade/overview.md).
* Als u een bijdragende ontwikkelaar (namelijk gebruikt u `git clone`) bent, zie [&#x200B; Update de toepassing &#x200B;](../../upgrade/developer/git-installs.md).

## De toepassing opnieuw installeren

De manier waarop u de toepassing opnieuw installeert vanaf de opdrachtregel is afhankelijk van uw rol:

* Als u de software van een archief installeerde of als u &quot;composer-creeer-project&quot;gebruikte, zie [&#x200B; de installatiegebiedsdelen van de Update &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).
* Als u een bijdragende ontwikkelaar (namelijk bent u begonnen te gebruiken `git clone`), zie [&#x200B; de installatiegebiedsdelen van de Update &#x200B;](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).

## De toepassing verwijderen

Als u de toepassing verwijdert, wordt de database neergezet en hersteld, wordt de implementatieconfiguratie verwijderd en worden mappen onder `var` gewist.

Voer de volgende opdracht in om de toepassing te verwijderen:

```bash
bin/magento setup:uninstall
```

Het volgende bericht wordt weergegeven om te bevestigen dat het verwijderen is gelukt:

```
[SUCCESS]: Magento uninstallation complete.
```

## Optioneel gegenereerde bestanden behouden

Standaard wist `bin/magento setup:upgrade` gecompileerde code en de cache. Doorgaans gebruikt u `bin/magento setup:upgrade` om componenten bij te werken en kan elke component verschillende gecompileerde klassen vereisen.

Nochtans, in sommige situaties (in het bijzonder, opstellend aan productie), zou u kunnen willen vermijden ontruimend gecompileerde code omdat het wat tijd kan vergen. (De cache wordt nog steeds gewist.) Om het gegevensbestandschema en gegevens *bij te werken zonder* gecompileerde code te ontruimen, ga binnen:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>De facultatieve `--keep-generated` optie zou in beperkte omstandigheden door ervaren systeemintegrators *slechts* moeten worden gebruikt. Deze optie zou *nooit* in een ontwikkelomgeving moeten worden gebruikt. Onjuist gebruik van deze optionele parameter kan fouten veroorzaken tijdens de uitvoering van de code.

## De toepassing installeren

* [Installeren via de opdrachtregel](../advanced.md)
