---
title: Modules verwijderen
description: Voer de volgende stappen uit om een Adobe Commerce-module te verwijderen.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 0%

---

# Modules verwijderen

In deze sectie wordt besproken hoe u een of meer modules kunt verwijderen. Tijdens uninstallation, kunt u naar keuze de code van de modules, gegevensbestandschema, en gegevensbestandgegevens verwijderen. U kunt eerst back-ups maken, zodat u de gegevens later kunt herstellen.

Verwijder een module alleen als u zeker weet dat u deze niet wilt gebruiken. In plaats van het verwijderen van een module, kunt u het zoals die in [ wordt besproken onbruikbaar maken of modules ](manage-modules.md) toelaten onbruikbaar maken.

>[!NOTE]
>
>Deze opdracht controleert of alleen afhankelijkheden zijn gedeclareerd in het `composer.json` -bestand. Als u een module verwijdert die _niet_ in het `composer.json` dossier wordt bepaald, schrapt dit bevel de module zonder gebiedsdelen te controleren. Dit bevel verwijdert __ niet, echter, de code van de module uit het dossiersysteem. U moet bestandssysteemgereedschappen gebruiken om de code van de module te verwijderen (bijvoorbeeld `rm -rf <path to module>` ). Als alternatief, kunt u [ niet-Composer modules ](manage-modules.md) onbruikbaar maken.

Opdrachtgebruik:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Waar `{ModuleName}` de modulenaam in `<VendorName>_<ModuleName>` formaat specificeert. De naam van de module Klant is bijvoorbeeld `Magento_Customer` . Voer `magento module:status` in om een lijst met modulenamen op te halen.

Met de opdracht Module verwijderen worden de volgende taken uitgevoerd:

1. Verifieert dat de gespecificeerde modules in de codebasis bestaan en pakketten zijn die door Composer worden geïnstalleerd.

   Dit bevel werkt _slechts_ met modules die als pakketten Composer worden bepaald.

1. Controleert gebiedsdelen met andere modules en beëindigt het bevel als er om het even welke onvolkomenheden gebiedsdelen zijn.

   Om rond dit te werken, kunt u of alle modules tezelfdertijd desinstalleren of u kunt de afhankelijke modules eerst desinstalleren.

1. Verzoekt om bevestiging om verder te gaan.
1. Hiermee plaatst u de winkel in de onderhoudsmodus.
1. Verwerkt de volgende bevelopties.

   | Optie | Betekenis | Back-upbestandsnaam en -locatie |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Een back-up maken van het bestandssysteem (behalve `var` en `pub/static` directory&#39;s). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Hiermee maakt u een back-up van de map pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Maak een back-up van de database. | `var/backups/<timestamp>_db.gz` |

1. Als `--remove-data` is opgegeven, verwijdert u het databaseschema en de gegevens die zijn gedefinieerd in de `Uninstall` -klassen van de module.

   Roept de methode `uninstall` in de klasse `Uninstall` aan om elke opgegeven module te verwijderen. Deze klasse moet van [ Magento\Framework\Setup\UninstallInterface ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php) erven.

1. Hiermee worden de opgegeven modules verwijderd uit de databasetabel `setup_module` .
1. Verwijdert de gespecificeerde modules uit de modulelijst in de [ plaatsingsconfiguratie ](../../configuration/reference/deployment-files.md).
1. Hiermee verwijdert u code uit de codebase met `composer remove` .

   >[!NOTE]
   >
   >Het verwijderen van een module _altijd_ looppas `composer remove`. Met de optie `--remove-data` verwijdert u databasegegevens en -schema die door de klasse `Uninstall` van de module zijn gedefinieerd.

1. Wist de cache.
1. Werkt gegenereerde klassen bij.
1. Als `--clear-static-content` wordt gespecificeerd, ontruimt [ geproduceerde statische meningsdossiers ](../../configuration/cli/static-view-file-deployment.md).
1. Neemt de opslag uit onderhoudswijze.

Als u bijvoorbeeld probeert een module te verwijderen waarvan een andere module afhankelijk is, wordt het volgende bericht weergegeven:

```
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Één alternatief moet beide modules na het steunen van het systeem van het moduledossier, `pub/media` dossiers, en gegevensbestandlijsten desinstalleren maar _niet_ verwijderend het het gegevensbestandschema of gegevens van de module:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Berichten die lijken op de volgende weergave:

```
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

Hierbij is `<filename>` de naam van het back-upbestand in de map `<app_root>/var/backups` . Voer `magento info:backups:list` in als u een lijst met back-upbestanden wilt weergeven.

>[!WARNING]
>
>Met deze opdracht verwijdert u de opgegeven bestanden of de database voordat u ze herstelt. Met de optie `--media-file` verwijdert u bijvoorbeeld media-elementen onder de map `pub/media` voordat u deze herstelt uit het opgegeven terugdraaibestand. Zorg ervoor dat u het bestandssysteem of de database die u wilt behouden niet hebt gewijzigd voordat u deze opdracht gebruikt.

>[!NOTE]
>
>Voer `magento info:backups:list` in om een lijst met beschikbare back-upbestanden weer te geven

Deze opdracht voert de volgende taken uit:

1. Hiermee plaatst u de winkel in de onderhoudsmodus.
1. Controleert de naam van het back-upbestand.
1. Als u een bestand voor het terugdraaien van code opgeeft:

   a. Controleert of de terugdraaidoellocaties schrijfbaar zijn (de mappen `pub/static` en `var` worden genegeerd).

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

* Een back-up van een bestand met de naam `1433876616_filesystem.tgz` herstellen:

  ```bash
  magento setup:rollback --code-file="1433876616_filesystem.tgz"
  ```

  Berichten die lijken op de volgende weergave:

  ```
  Enabling maintenance mode
  Code rollback is starting ...
  Code rollback filename: 1433876616_filesystem.tgz
  Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
  [SUCCESS]: Code rollback has completed successfully.
  Disabling maintenance mode
  ```

>[!NOTE]
>
>Als u de opdracht `magento` opnieuw wilt uitvoeren zonder mappen te wijzigen, moet u mogelijk `cd pwd` invoeren.
