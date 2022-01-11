---
title: Modules en extensies upgraden
description: Gebruik de bevel-lijn interface en Composer om Adobe Commerce en Magento Open Source modules en uitbreidingen te bevorderen.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 0%

---


# Modules en extensies upgraden

Een module of extensie bijwerken of bijwerken:

1. Download het bijgewerkte bestand van Marketplace of een andere ontwikkelaar van extensies. Noteer de modulenaam en -versie.

1. Exporteer de inhoud naar de Adobe Commerce- of Magento Open Source-hoofdinstallatiemap.

1. Voer een van de volgende handelingen uit als er een Composer-pakket voor de module bestaat.

   Bijwerken per modulenaam:

   ```bash
   composer update vendor/module-name
   ```

   Bijwerken per versie:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Voer de volgende opdrachten uit om de cache te upgraden, te implementeren en schoon te maken.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
