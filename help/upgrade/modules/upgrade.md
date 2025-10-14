---
title: Modules en extensies upgraden
description: Gebruik de opdrachtregelinterface en de Composer om Adobe Commerce-modules en -extensies te upgraden.
exl-id: 017d75df-fd21-4fb4-abc9-80a35fc47d0f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
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

Adobe verwijderde al [&#x200B; VBEs &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/upgrade-guide/modules/upgrade) in 2.4.4. Leveranciers blijven deze extensies ondersteunen op de Adobe Commerce Marketplace.

Als u deze uitbreidingen met Adobe Commerce 2.4.4 en later wilt blijven gebruiken, moet u de overeenkomstige pakketgebiedsdelen in uw `composer.json` dossier _vóór_ bevordering aan 2.4.4 bijwerken. Neem contact op met de leverancier voor de pakketnaam en -versie die u wilt gebruiken.

Zie de volgende Adobe Commerce Marketplace-aanbiedingen voor meer informatie:

- [&#x200B; Betalen Amazon &#x200B;](https://marketplace.magento.com/amzn-amazon-pay-magento-2-module.html)
- [&#x200B; Dotdigital &#x200B;](https://marketplace.magento.com/dotdigital-dotdigital-magento2-os-package.html)
- [&#x200B; Klarna &#x200B;](https://marketplace.magento.com/klarna-m2-klarna.html)
- [&#x200B; Hoekpunt &#x200B;](https://marketplace.magento.com/vertexinc-vertex-tax-module.html)
- [&#x200B; Yotpo &#x200B;](https://marketplace.magento.com/yotpo-module-yotpo.html)
