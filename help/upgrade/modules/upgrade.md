---
title: Modules en extensies upgraden
description: Gebruik de opdrachtregelinterface en de Composer om Adobe Commerce-modules en -extensies te upgraden.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# Modules en extensies upgraden

Een module of extensie bijwerken of bijwerken:

1. Download het bijgewerkte bestand van Marketplace of een andere ontwikkelaar van extensies. Noteer de naam en de versie van de module.

1. Exporteer de inhoud naar de Adobe Commerce-hoofdinstallatiemap.

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

## Door leverancier gebundelde extensies (VBE&#39;s)

Alle Adobe verwijderd [VBEs](https://devdocs.magento.com/extensions/vendor/) in 2.4.4. Leveranciers blijven deze extensies ondersteunen op de Adobe Commerce Marketplace.

Als u deze extensies wilt blijven gebruiken met Adobe Commerce 2.4.4 en hoger, moet u de bijbehorende pakketafhankelijkheden bijwerken in uw `composer.json` file _voor_ opwaardering tot 2.4.4. Neem contact op met de leverancier voor de pakketnaam en -versie die u wilt gebruiken.

Zie de volgende Adobe Commerce Marketplace-aanbiedingen voor meer informatie:

- [Amazon Pay](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [Dotdigital](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)
- [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [Yotpo](https://marketplace.magento.com/yotpo-module-yotpo.html)
