---
title: Modules en extensies beheren (ontwikkelaar)
description: Adobe Commerce-modules en -extensies beheren met behulp van de opdrachtregelinterface en Composer-pakketbeheer.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# Modules en extensies beheren

Ontwikkelaars die een bijdrage leveren, upgraden modules en extensies door hun versies op te geven in het Adobe Commerce `composer.json` -bestand. Als u geen bijdragende ontwikkelaar bent, zie [ een verbetering ](../implementation/perform-upgrade.md) uitvoeren.

U kunt een sectie `require` toevoegen aan het `composer.json` -bestand of u kunt de opdracht `composer require` als volgt gebruiken:

{{$include /help/_includes/server-login.md}}

U hebt de volgende opties:

## Beschikbare moduleversies ophalen

Opdrachtgebruik:

```bash
composer show --all <vendor>/<name>
```

Bijvoorbeeld:

```bash
composer show --all example/module
```

## De opdracht `composer require` gebruiken

Opdrachtgebruik:

```bash
composer require <vendor>/<name>:<version>
```

Bijvoorbeeld:

```bash
composer require example/module:1.0.0
```

Wacht terwijl Composer gebiedsdelen bijwerkt en de module installeert.

## Een sectie `require` toevoegen aan het bestand composer.json

1. Open de `composer.json` in een teksteditor.

1. Voeg een sectie `require` toe.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Sla de wijzigingen op in het `composer.json` -bestand en sluit de teksteditor af.

1. Los gebiedsdelen op en schrijf nauwkeurige versies aan het `composer.lock` dossier.

   ```bash
   composer update
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
