---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Systeem voor bijwerken van build

**om het bouwstijlsysteem** bij te werken:

1. Meld u aan bij het constructiesysteem als de eigenaar van het bestandssysteem.
1. Wijzig de hoofdmap van de toepassing.

   ```shell
   cd <Magento root dir>
   ```

1. Trek de wijzigingen in `app/etc/config.php` van het bronbesturingselement.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Compileer code.

   ```shell
   bin/magento setup:di:compile
   ```

1. Nadat de code is gecompileerd, produceer statische meningsdossiers.

   ```shell
   bin/magento setup:static-content:deploy -f
   ```

1. Controleer de veranderingen in broncontrole.

   ```shell
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
