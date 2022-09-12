---
title: Taalpakketten verwijderen
description: Voer de volgende stappen uit om een Adobe Commerce- of Magento Open Source-taalpakket te verwijderen.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Taalpakketten verwijderen

In deze sectie wordt besproken hoe u een of meer taalpakketten kunt verwijderen, waarbij u eventueel de code van de taalpakketten uit het bestandssysteem kunt opnemen. U kunt eerst back-ups maken, zodat u de gegevens later kunt herstellen.

Deze opdracht wordt verwijderd *alleen* taalpakketten die zijn opgegeven in `composer.json`; met andere woorden, taalpakketten die worden geleverd als [Composer](https://glossary.magento.com/composer) pakketten. Als uw [taalpakket](https://glossary.magento.com/language-package) is geen Composer-pakket, moet u de toepassing handmatig verwijderen door de code van het taalpakket uit het bestandssysteem te verwijderen.

U kunt back-ups op elk gewenst moment herstellen met de [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) gebruiken.

Opdrachtgebruik:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

Met de opdracht Taalpakket verwijderen kunt u de volgende taken uitvoeren:

1. controles op afhankelijkheden; als zo, eindigt het bevel.

   Om dit te omzeilen, kunt u of alle afhankelijke taalpakketten tezelfdertijd verwijderen of u kunt de afhankelijke taalpakketten eerst desinstalleren.

1. Indien `--backup code` is opgegeven, maakt u een back-up van het bestandssysteem (exclusief `var` en `pub/static` mappen) naar `var/backups/<timestamp>_filesystem.tgz`
1. Hiermee verwijdert u bestanden met taalpakketten uit de codebase met `composer remove`.
1. Hiermee wist u de [cachegeheugen](https://glossary.magento.com/cache).

Als u bijvoorbeeld probeert een taalpakket te verwijderen waarvan een ander taalpakket afhankelijk is, wordt het volgende bericht weergegeven:

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

U kunt ook beide taalpakketten verwijderen nadat u een back-up van de codebase hebt gemaakt:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Berichten die lijken op de volgende weergave:

```terminal
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
