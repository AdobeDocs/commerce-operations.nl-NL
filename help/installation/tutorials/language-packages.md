---
title: Taalpakketten verwijderen
description: Voer de volgende stappen uit om een Adobe Commerce-taalpakket te verwijderen.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Taalpakketten verwijderen

In deze sectie wordt besproken hoe u een of meer taalpakketten kunt verwijderen, waarbij u eventueel de code van de taalpakketten uit het bestandssysteem kunt opnemen. U kunt eerst back-ups maken, zodat u de gegevens later kunt herstellen.

Dit bevel schrapt *slechts* taalpakketten die in `composer.json` worden gespecificeerd; met andere woorden, taalpakketten die als pakketten Composer worden verstrekt. Als uw taalpakket geen Composer-pakket is, moet u het handmatig verwijderen door de code van het taalpakket uit het bestandssysteem te verwijderen.

U kunt back-ups op elk gewenst moment herstellen met de opdracht [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) .

Opdrachtgebruik:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

Met de opdracht Taalpakket verwijderen kunt u de volgende taken uitvoeren:

1. Controleert op gebiedsdelen; als zo, eindigt het bevel.

   Om dit te omzeilen, kunt u of alle afhankelijke taalpakketten tezelfdertijd verwijderen of u kunt de afhankelijke taalpakketten eerst desinstalleren.

1. Als `--backup code` is opgegeven, maakt u een back-up van het bestandssysteem (exclusief mappen `var` en `pub/static` ) naar `var/backups/<timestamp>_filesystem.tgz`
1. Hiermee verwijdert u bestanden met taalpakketten uit de codebase met `composer remove` .
1. Wist de cache.

Als u bijvoorbeeld probeert een taalpakket te verwijderen waarvan een ander taalpakket afhankelijk is, wordt het volgende bericht weergegeven:

```
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

U kunt ook beide taalpakketten verwijderen nadat u een back-up van de codebase hebt gemaakt:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Berichten die lijken op de volgende weergave:

```
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
