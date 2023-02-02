---
title: Implementatie van één computer
description: Leer hoe te om updates aan Handel op een productieserver op te stellen gebruikend de bevellijn.
source-git-commit: 2e1a06b59fda7db4a9b32d000e1b2a3ca88926d3
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Eén computer implementeren

Dit onderwerp verstrekt instructies voor het opstellen van updates aan Handel op een productieserver gebruikend de bevellijn. Dit proces is van toepassing op technische gebruikers die verantwoordelijk zijn voor winkels die op één computer worden uitgevoerd en waarop een aantal thema&#39;s en landinstellingen zijn geïnstalleerd.

## Aannames

- U hebt Commerce geïnstalleerd met [Composer](../../installation/composer.md).
- U past rechtstreeks updates toe op de server.

>[!WARNING]
>
>Deze handleiding is niet van toepassing als u `git clone` om Commerce te installeren.
>Medewerkers moeten [deze handleiding][install] om hun installatie van de Handel bij te werken.

## Implementatiestappen

1. Meld u aan bij uw productieserver als of schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).

1. Map wijzigen in de basismap Commerce:

   ```bash
   cd <Commerce base directory>
   ```

1. Onderhoudsmodus inschakelen met de opdracht:

   ```bash
   bin/magento maintenance:enable
   ```

1. Pas updates op Handel of zijn componenten toe gebruikend het volgende bevelpatroon:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **package**: De naam van het pakket dat u wilt bijwerken.

   Bijvoorbeeld:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **versie**: De doelversie van het pakket dat u wilt bijwerken.

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

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
