---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Systeem voor bijwerken van build

**Het constructiesysteem bijwerken**:

1. Meld u aan bij het constructiesysteem als de eigenaar van het bestandssysteem.
1. Wijzig de hoofdmap van de toepassing.

   ```bash
   cd <Magento root dir>
   ```

1. Breng de wijzigingen aan in `app/etc/config.php` van broncontrole.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Compileer code.

   ```bash
   bin/magento setup:di:compile
   ```

1. Nadat de code is gecompileerd, produceer statische meningsdossiers.

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. Controleer de veranderingen in broncontrole.

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
