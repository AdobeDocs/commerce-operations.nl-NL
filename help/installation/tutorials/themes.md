---
title: Thema's verwijderen
description: Voer de volgende stappen uit om een Adobe Commerce-thema te verwijderen.
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Thema&#39;s verwijderen

Voordat u deze opdracht gebruikt, moet u weten welk relatief pad naar het thema is ingesteld. Thema&#39;s bevinden zich in een submap van `<magento_root>/app/design/<area name>`. U moet het pad naar het thema opgeven dat begint met het gebied: `frontend` (voor thema&#39;s van de winkel) of `adminhtml` (voor beheerthema&#39;s).

Het pad naar het thema Luma dat bij Adobe Commerce wordt geleverd, is bijvoorbeeld `frontend/Magento/luma`.

Zie voor meer informatie over thema&#39;s [themastructuur](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Overzicht van het verwijderen van thema&#39;s

In deze sectie wordt beschreven hoe u een of meer thema&#39;s kunt verwijderen. U kunt desgewenst ook de themacode uit het bestandssysteem opnemen. U kunt eerst back-ups maken, zodat u de gegevens later kunt herstellen.

Deze opdracht wordt verwijderd *alleen* thema&#39;s die worden opgegeven in `composer.json`Met andere woorden, thema&#39;s die als Composer-pakketten worden aangeboden. Als uw thema geen Composer-pakket is, moet u de toepassing handmatig verwijderen door:

* De `parent` knooppuntinformatie in `theme.xml` om verwijzingen naar het thema te verwijderen.
* Themacode verwijderen uit het bestandssysteem.

  [Meer informatie over themaovererving](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Thema&#39;s verwijderen

Opdrachtgebruik:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Wanneer

* `{theme path}` Dit is het relatieve pad naar het thema, te beginnen met de naam van het gebied. Het pad naar het lege thema dat bij Adobe Commerce wordt geleverd, is bijvoorbeeld `frontend/Magento/blank`.
* `--backup-code` maakt een back-up van de codebase, zoals beschreven in de volgende alinea&#39;s.
* `--clear-static-content` gegenereerde opschonen [statische weergavebestanden](../../configuration/cli/static-view-file-deployment.md), die nodig is om statische weergavebestanden correct weer te geven.

De opdracht voert de volgende taken uit:

1. Verifieert dat de gespecificeerde themawegen bestaan; als niet, eindigt het bevel.
1. Verifieert dat het thema een pakket Composer is; als niet, eindigt het bevel.
1. Controleert op gebiedsdelen en beëindigt het bevel als er om het even welke onvervulde gebiedsdelen zijn.

   Als u dit probleem wilt verhelpen, kunt u alle thema&#39;s tegelijkertijd verwijderen of de installatie van de thema&#39;s eerst ongedaan maken.

1. Verifieert dat het thema niet wordt gebruikt; als het wordt gebruikt, eindigt het bevel.
1. Verifieert dat het thema niet de basis van het virtuele thema is; als het de basis van een virtueel thema is, eindigt het bevel.
1. Hiermee plaatst u de winkel in de onderhoudsmodus.
1. Indien `--backup-code` is opgegeven, maakt u een back-up van de codebase, exclusief de `pub/static`, `pub/media`, en `var` mappen.

   De naam van het back-upbestand is `var/backups/<timestamp>_filesystem.tgz`

   U kunt back-ups op elk gewenst moment herstellen met de [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) gebruiken.

1. Hiermee verwijdert u thema&#39;s uit het dialoogvenster `theme` databasetabel.
1. Thema&#39;s uit de basis van code verwijderen met `composer remove`.
1. Wist de cache.
1. Hiermee worden gegenereerde klassen gewist
1. Indien `--clear-static-content` is opgegeven, cleans [gegenereerde statische weergavebestanden](../../configuration/cli/static-view-file-deployment.md).

Als u bijvoorbeeld probeert een thema te verwijderen waarvan een ander thema afhankelijk is, wordt het volgende bericht weergegeven:

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

U kunt beide thema&#39;s ook verwijderen terwijl u een back-up van de codebase maakt:

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Berichten die lijken op de volgende weergave:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Als u een beheerthema wilt verwijderen, moet u het ook verwijderen uit de configuratie voor injectie van afhankelijkheden van de component. `<component root directory>/etc/di.xml`.
