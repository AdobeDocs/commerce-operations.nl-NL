---
title: Modules en extensies beheren (ontwikkelaar)
description: Adobe Commerce-modules en -extensies beheren met behulp van de opdrachtregelinterface en Composer-pakketbeheer.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 2%

---

# Modules en extensies beheren

Ontwikkelaars helpen modules en extensies bij te werken door hun versies op te geven in de Adobe Commerce of Magento Open Source `composer.json` bestand. Als u geen bijdragende ontwikkelaar bent, zie [Een upgrade uitvoeren](../implementation/perform-upgrade.md).

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
