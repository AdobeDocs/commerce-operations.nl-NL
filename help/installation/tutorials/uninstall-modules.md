---
title: Modules verwijderen
description: Voer de volgende stappen uit om een Adobe Commerce-module te verwijderen.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Modules verwijderen

In deze sectie wordt besproken hoe u een of meer modules kunt verwijderen. Tijdens uninstallation, kunt u naar keuze de code van de modules, gegevensbestandschema, en gegevensbestandgegevens verwijderen. U kunt eerst back-ups maken, zodat u de gegevens later kunt herstellen.

Verwijder een module alleen als u zeker weet dat u deze niet wilt gebruiken. In plaats van een module te verwijderen, kunt u deze uitschakelen zoals beschreven in [Modules in- of uitschakelen](manage-modules.md).

>[!NOTE]
>
>Dit bevel controleert dat slechts gebiedsdelen die in worden verklaard `composer.json` bestand. Als u een module verwijdert die _niet_ in de `composer.json` bestand, verwijdert deze opdracht de module zonder afhankelijkheden te controleren. Deze opdracht doet _niet_, echter, verwijder de code van de module uit het dossiersysteem. U moet bestandssysteemgereedschappen gebruiken om de code van de module te verwijderen (bijvoorbeeld `rm -rf <path to module>`). Als alternatief kunt u [disable](manage-modules.md) niet-composer-modules.

Opdrachtgebruik:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Wanneer `{ModuleName}` geeft de modulenaam op in `<VendorName>_<ModuleName>` gebruiken. De naam van de module Klant is bijvoorbeeld `Magento_Customer`. Om een lijst van modulenamen te krijgen, ga `magento module:status`

Met de opdracht Module verwijderen worden de volgende taken uitgevoerd:

1. Verifieert dat de gespecificeerde modules in de codebasis bestaan en pakketten zijn die door Composer worden geïnstalleerd.

   Deze opdracht werkt _alleen_ met modules gedefinieerd als Composer-pakketten.

1. Controleert gebiedsdelen met andere modules en beëindigt het bevel als er om het even welke onvolkomenheden gebiedsdelen zijn.

   Om rond dit te werken, kunt u of alle modules tezelfdertijd desinstalleren of u kunt de afhankelijke modules eerst desinstalleren.

1. Verzoekt om bevestiging om verder te gaan.
1. Hiermee plaatst u de winkel in de onderhoudsmodus.
1. Verwerkt de volgende bevelopties.

   | Optie | Betekenis | Back-upbestandsnaam en -locatie |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Back-ups maken van het bestandssysteem (exclusief `var` en `pub/static` mappen). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Hiermee maakt u een back-up van de map pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Maak een back-up van de database. | `var/backups/<timestamp>_db.gz` |

1. Indien `--remove-data` wordt gespecificeerd, verwijder het gegevensbestandschema en gegevens die in de module worden bepaald `Uninstall` klassen.

   Voor elke opgegeven module die moet worden verwijderd, wordt het `uninstall` in haar `Uninstall` klasse. Deze klasse moet overerven van [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. Hiermee verwijdert u de opgegeven modules uit het dialoogvenster `setup_module` databasetabel.
1. Hiermee verwijdert u de opgegeven modules uit de lijst met modules in het dialoogvenster [implementatieconfiguratie](../../configuration/reference/deployment-files.md).
1. Hiermee verwijdert u code uit de codebase met `composer remove`.

   >[!NOTE]
   >
   >Een module verwijderen _altijd_ looppas `composer remove`. De `--remove-data` optie verwijdert gegevensbestandgegevens en schema dat door de module wordt bepaald `Uninstall` klasse.

1. Wist de cache.
1. Werkt gegenereerde klassen bij.
1. Indien `--clear-static-content` is opgegeven, cleans [gegenereerde statische weergavebestanden](../../configuration/cli/static-view-file-deployment.md).
1. Neemt de opslag uit onderhoudswijze.

Als u bijvoorbeeld probeert een module te verwijderen waarvan een andere module afhankelijk is, wordt het volgende bericht weergegeven:

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Eén mogelijkheid is om beide modules te verwijderen nadat u een back-up hebt gemaakt van het bestandssysteem van de module. `pub/media` bestanden en databasetabellen, maar _niet_ het verwijderen van het de gegevensbestandschema of gegevens van de module:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Berichten die lijken op de volgende weergave:

```terminal
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>De vertoning van fouten als u probeert om een module met een gebiedsdeel van een andere module te desinstalleren. In dat geval kunt u één module niet verwijderen. U moet beide verwijderen.

## Bestandssysteem, database of mediabestanden terugdraaien

Gebruik de volgende opdracht om de codebase te herstellen naar de toestand waarin u er een back-up van hebt gemaakt:

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Wanneer `<filename>` is de naam van het back-upbestand in het dialoogvenster `<app_root>/var/backups` directory. Als u een lijst met back-upbestanden wilt weergeven, voert u `magento info:backups:list`

>[!WARNING]
>
>Met deze opdracht verwijdert u de opgegeven bestanden of de database voordat u ze herstelt. Bijvoorbeeld de `--media-file` Hiermee verwijdert u media-elementen onder de optie `pub/media` map voordat het terugdraaibestand wordt teruggezet uit het opgegeven terugdraaibestand. Zorg ervoor dat u het bestandssysteem of de database die u wilt behouden niet hebt gewijzigd voordat u deze opdracht gebruikt.

>[!NOTE]
>
>Als u een lijst met beschikbare back-upbestanden wilt weergeven, voert u `magento info:backups:list`

Deze opdracht voert de volgende taken uit:

1. Hiermee plaatst u de winkel in de onderhoudsmodus.
1. Controleert de naam van het back-upbestand.
1. Als u een bestand voor het terugdraaien van code opgeeft:

   a. verifieert dat de het terugschroeven van prijzenbestemmingsplaatsen beschrijfbaar zijn (merk op dat `pub/static` en `var` mappen worden genegeerd).

   b. Verwijdert alle bestanden en mappen in de installatiemap van de toepassing.

   c. Extraheert het archiefbestand naar de doellocaties.

1. Als u een terugdraaibestand voor de database opgeeft:

   a. De gehele database wordt verwijderd.

   b. Herstelt de database met behulp van de back-up van de database.

1. Als u een terugdraaibestand voor media opgeeft:

   a. Verifieert dat de het terugschroeven van prijzenbestemmingsplaatsen beschrijfbaar zijn.

   b. Hiermee worden alle bestanden en mappen verwijderd onder `pub/media`

   c. Extraheert het archiefbestand naar de doellocaties.

1. Neemt de opslag uit onderhoudswijze.

Als u bijvoorbeeld een back-up van een code (dat wil zeggen bestandssysteem) wilt herstellen, voert u de volgende opdrachten in de getoonde volgorde in:

* Een lijst met back-ups weergeven:

  ```bash
  magento info:backups:list
  ```

* Een back-up van een bestand met de naam `1433876616_filesystem.tgz`:

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  Berichten die lijken op de volgende weergave:

  ```terminal
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>Als u het dialoogvenster `magento` bevel opnieuw zonder folders te veranderen, zou u kunnen moeten ingaan `cd pwd`.
