---
title: Composerontwikkeling
description: Leer over het ontwikkelen van modules Composer op zijn plaats in de ` verkoper/ ` folder.
feature: Best Practices
role: Developer
source-git-commit: b4213c40fdf903fd962a15fc99b143f31aedbcde
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---


# Composerontwikkeling

In dit onderwerp wordt de aanbevolen aanpak beschreven voor het op locatie ontwikkelen van Composer-modules (als Git-opslagplaatsen in de `vendor/` directory) en het toevoegen van die modules aan uw belangrijkste project van het Git.

>[!NOTE]
>
>Deze richtsnoeren zijn in de eerste plaats van toepassing op [algemene referentiearchitectuur (GRA)](../overview.md) projecten.

## Een ontwikkelingsvertakking voorbereiden

1. Maak of check de ontwikkelingsvertakking uit in uw belangrijkste Git-opslagplaats.
1. Vereisen ontwikkelingsversies voor elke module die u handhaaft.

   In dit voorbeeld vertegenwoordigt elke vertakking in de Git-hoofdopslagplaats een versie van het Composer-pakket. De aanbevolen naamgevingsconventie voor Composer-versies in dit scenario is `dev-` gevolgd door de naam van de tak. Bijvoorbeeld:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Als een ander Composer-pakket een specifieke versie van een module vereist (bijvoorbeeld `client/module-example 1.0.12`), installeert u deze met een alias:

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Voor de `qa` vertakking, vervangen `dev-develop` with `dev-qa`.

## Pakketten omzetten in Git-opslagruimten

Pakketten bevatten standaard geen `.git/` directory. Composer kan pakketten uitchecken vanuit Git in plaats van de vooraf gebouwde Composer-pakketten te gebruiken. Het voordeel van deze aanpak is dat u de pakketten tijdens de ontwikkeling eenvoudig kunt wijzigen.

1. De module verwijderen uit het dialoogvenster `vendor/` directory.

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Installeer de module opnieuw met de [opgegeven Git-bron](#prepare-a-development-branch).

   ```bash
   composer install --prefer-source
   ```

1. Controleer of het Composer-pakket nu een Git-opslagplaats is:

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. Meerdere modules in Git-opslagruimten (bijvoorbeeld &quot;client&quot;-modules) in batch omzetten:

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## Ontwikkeling starten

1. Een functie/werkvertakking maken of uitchecken. In het volgende voorbeeld ziet u een vertakking met dezelfde naam als een Jira-ticket.

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. Nadat u vertakkingen in een module hebt gewijzigd, raadpleegt u de wijzigingen door de Adobe Commerce-cache en statische inhoud te leegmaken.

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## Het hoofdproject bijwerken met uw ontwikkeling

Werk uw hoofdopslagplaats voor Git bij door de `composer.lock` bestand. Als uw module nieuw is, laat het toe.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
