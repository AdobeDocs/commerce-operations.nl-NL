---
title: Adobe Commerce verwijderen of opnieuw installeren
description: Voer de volgende stappen uit om installaties in Adobe Commerce te verwijderen en opnieuw te installeren.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Adobe Commerce verwijderen of opnieuw installeren

Voordat u deze opdrachten gebruikt, moet u [de toepassing installeren](../tutorials/install.md).

## De toepassing bijwerken

De toepassing bijwerken:

* Als u de software van een archief hebt geïnstalleerd of als u &#39;composer-create-project&#39; hebt gebruikt, raadpleegt u de [Upgradehandleiding](../../upgrade/overview.md).
* Als u een bijdragende ontwikkelaar bent (namelijk gebruikt u `git clone`), zie [De toepassing bijwerken](../../upgrade/developer/git-installs.md).

## De toepassing opnieuw installeren

De manier waarop u de toepassing opnieuw installeert vanaf de opdrachtregel is afhankelijk van uw rol:

* Als u de software van een archief hebt geïnstalleerd of als u &#39;composer-create-project&#39; hebt gebruikt, raadpleegt u [Installatieafhankelijkheden bijwerken](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Als u een bijdragende ontwikkelaar bent (namelijk bent u begonnen te gebruiken `git clone`), zie [Installatieafhankelijkheden bijwerken](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## De toepassing verwijderen

Wanneer de toepassing wordt verwijderd, wordt de database hersteld, wordt de implementatieconfiguratie verwijderd en worden mappen onder de database gewist `var`.

Voer de volgende opdracht in om de toepassing te verwijderen:

```bash
bin/magento setup:uninstall
```

Het volgende bericht wordt weergegeven om te bevestigen dat het verwijderen is gelukt:

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Optioneel gegenereerde bestanden behouden

Standaard, `bin/magento setup:upgrade` Wist gecompileerde code en het geheime voorgeheugen. Meestal gebruikt u `bin/magento setup:upgrade` om componenten bij te werken en elke component kan verschillende gecompileerde klassen vereisen.

Nochtans, in sommige situaties (in het bijzonder, opstellend aan productie), zou u kunnen willen vermijden ontruimend gecompileerde code omdat het wat tijd kan vergen. (De cache wordt nog steeds gewist.) Het databaseschema en de gegevens bijwerken *zonder* het ontruimen van gecompileerde code, ga binnen:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>De optionele `--keep-generated` in beperkte omstandigheden door ervaren systeemintegrators moeten worden gebruikt *alleen*. Deze optie moet *nooit* worden gebruikt in een ontwikkelomgeving. Onjuist gebruik van deze optionele parameter kan fouten veroorzaken tijdens de uitvoering van de code.

## De toepassing installeren

* [Installeren via de opdrachtregel](../advanced.md)
