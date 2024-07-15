---
title: Composerontwikkeling
description: Leer over het ontwikkelen van modules Composer op zijn plaats in de ` verkoper/ ` folder.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 7664ffb5-2e46-49c3-b2e6-c133c35d2f6b
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Composerontwikkeling

Dit onderwerp beschrijft de geadviseerde benadering voor het ontwikkelen van modules Composer op zijn plaats (als bewaarplaatsen van Git in de `vendor/` folder) en het toevoegen van die modules aan uw belangrijkste project van Git.

>[!NOTE]
>
>Deze richtlijnen zijn hoofdzakelijk op [ globale verwijzingsarchitectuur (GRA) ](../overview.md) projecten van toepassing.

## Een ontwikkelingsvertakking voorbereiden

1. Maak of check de ontwikkelingsvertakking uit in uw belangrijkste Git-opslagplaats.
1. Vereisen ontwikkelingsversies voor elke module die u handhaaft.

   In dit voorbeeld vertegenwoordigt elke vertakking in de Git-hoofdopslagplaats een versie van het Composer-pakket. De aanbevolen naamgevingsconventie voor Composer-versies in dit scenario is `dev-` gevolgd door de naam van de vertakking. Bijvoorbeeld:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Als een ander Composer-pakket een specifieke versie van een module vereist (bijvoorbeeld `client/module-example 1.0.12`), installeert u deze met een alias:

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Vervang `dev-develop` door `dev-qa` voor de `qa` -vertakking.

## Pakketten omzetten in Git-opslagruimten

Pakketten bevatten standaard geen map `.git/` . Composer kan pakketten uitchecken vanuit Git in plaats van de vooraf gebouwde Composer-pakketten te gebruiken. Het voordeel van deze aanpak is dat u de pakketten tijdens de ontwikkeling eenvoudig kunt wijzigen.

1. Verwijder de module uit de map `vendor/` .

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Installeer de module opnieuw gebruikend de [ gespecificeerde bron van het Git ](#prepare-a-development-branch).

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

Werk de hoofdopslagplaats voor Git bij door het `composer.lock` -bestand te wijzigen. Als uw module nieuw is, laat het toe.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
