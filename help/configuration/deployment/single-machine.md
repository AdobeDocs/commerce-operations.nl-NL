---
title: Implementatie van één computer
description: Leer hoe u updates voor Commerce op een productieserver kunt implementeren via de opdrachtregel.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 1%

---

# Implementatie van één computer

Dit onderwerp verstrekt instructies voor het opstellen van updates aan Commerce op een productieserver gebruikend de bevellijn. Dit proces is van toepassing op technische gebruikers die verantwoordelijk zijn voor winkels die op één computer worden uitgevoerd en waarop een aantal thema&#39;s en landinstellingen zijn geïnstalleerd.

## Veronderstellingen

- U installeerde Commerce gebruikend [ Composer ](../../installation/composer.md).
- U past rechtstreeks updates toe op de server.

>[!WARNING]
>
>Deze handleiding is niet van toepassing als u Commerce hebt geïnstalleerd met `git clone` .
>De bijdragende ontwikkelaars zouden [ deze gids ](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies) moeten gebruiken om hun installatie van Commerce bij te werken.

## Implementatiestappen

1. Login aan uw productieserver als, of schakelaar aan, de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).

1. Map wijzigen in de basismap van Commerce:

   ```bash
   cd <Commerce base directory>
   ```

1. Onderhoudsmodus inschakelen met de opdracht:

   ```bash
   bin/magento maintenance:enable
   ```

1. Pas updates toe op Commerce of de componenten ervan met behulp van het volgende opdrachtpatroon:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **pakket**: De naam van het pakket u wilt bijwerken.

   Bijvoorbeeld:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **versie**: De doelversie van het pakket u wilt bijwerken.

1. Componenten bijwerken met Composer:

   ```bash
   composer update
   ```

1. Werk het databaseschema en de gegevens bij:

   ```bash
   bin/magento setup:upgrade
   ```

1. Compileer de code:

   ```bash
   bin/magento setup:di:compile
   ```

1. Statische inhoud implementeren:

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. De cache reinigen:

   ```bash
   bin/magento cache:clean
   ```

1. Onderhoudsmodus afsluiten:

   ```bash
   bin/magento maintenance:disable
   ```

