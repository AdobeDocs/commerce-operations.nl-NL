---
title: Modules en extensies beheren (ontwikkelaar)
description: Adobe Commerce-modules en -extensies beheren met behulp van de opdrachtregelinterface en Composer-pakketbeheer.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# Modules en extensies beheren

Ontwikkelaars helpen modules en extensies bij te werken door hun versies op te geven in de Adobe Commerce `composer.json` bestand. Als u geen bijdragende ontwikkelaar bent, zie [Een upgrade uitvoeren](../implementation/perform-upgrade.md).

U kunt een `require` aan de `composer.json` of u kunt de `composer require` als volgt:

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

## Gebruik de `composer require` command

Opdrachtgebruik:

```bash
composer require <vendor>/<name>:<version>
```

Bijvoorbeeld:

```bash
composer require example/module:1.0.0
```

Wacht terwijl Composer gebiedsdelen bijwerkt en de module installeert.

## Voeg een `require` naar het bestand composer.json

1. Open de `composer.json` in een teksteditor.

1. Voeg een `require` sectie.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Sla uw wijzigingen op in het dialoogvenster `composer.json` en sluit de teksteditor af.

1. Los gebiedsdelen op en schrijf nauwkeurige versies aan `composer.lock` bestand.

   ```bash
   composer update
   ```
