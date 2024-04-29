---
title: Composer-projectstructuur
description: Leer hoe u de afzonderlijke pakketoptie instelt en onderhoudt die wordt beschreven in de algemene voorbeelden van de referentiearchitectuur.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 8757d5b8-8309-452f-bfb3-1188a816d14f
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Composer-projectstructuur

In deze handleiding wordt beschreven hoe u de [afzonderlijke pakketten, optie](../examples.md#option-1-separate-packages) beschreven in de algemene voorbeelden van de referentiearchitectuur (GRA).

## Vereisten

Controleer voordat u begint het volgende:

- U hebt een Git-opslagplaats
- U hebt een bewaarplaats Composer (dit onderwerp benadrukt Privé Packagist)
- U hebt uw Composer-opslagplaats zo geconfigureerd dat deze de `repo.magento.com` en `packagist.org` bewaarplaatsen

## Hoofd-Git-projectgegevensopslagplaats

De belangrijkste Git-projectgegevensopslagruimte mag alleen een Composer-project bevatten. U kunt alle andere elementen beheren met Composer-pakketten. Het hoofdproject mag alleen de volgende bestandsstructuur bevatten, omdat Composer alle andere pakketten via afhankelijkheden installeert:

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Voeg de volgende inhoud toe aan de `.gitignore` bestand:

```tree
/*
!/composer.json
!/composer.lock
```

## Het hoofdproject initialiseren

1. Een Git-opslagplaats maken met de naam `project-<region/country/brand>`.

1. Maken `composer.json` en `composer.lock` bestanden:

   ```bash
   composer create-project --no-install --repository-url=https://repo.magento.com/ magento/project-enterprise-edition project-<region/country/brand>
   cd <install-directory-name>
   printf '/*\n!/composer.json\n!/composer.lock\n!/.gitignore' > .gitignore
   composer config --unset version
   composer config name '<client>/project-<region/country/brand>'
   composer config description '<client> <region/country/brand> main composer project'
   composer config repositories.private-packagist composer https://repo.packagist.com/<client>/
   composer config repositories.packagist.org false
   composer config --unset repositories.0
   composer install
   git init
   git add --all
   git commit -m 'initialize project'
   git remote add origin git@bitbucket.org:<client>/project-<region/country/brand>.git
   git push -u origin master
   ```

## Niet-modulebestanden opslaan

1. Voeg de `app/etc/config.xml` naar de Git-opslagplaats.

   U kunt de module gebruiken die u gaat creëren om andere gebied of merkspecifieke dossiers, zoals te installeren `.htaccess`, Google- of Bing-verificatietekstbestanden, uitvoerbare bestanden of andere statische bestanden die niet worden beheerd door Adobe Commerce-modules.

   Gebruiken `magento2-component` typt u pakketten om een bestandstoewijzing te maken waarmee u bestanden tijdens het gebruik van het Git-bestand naar de hoofdopslagplaats kunt kopiëren `composer install` en `composer update` bewerkingen.

1. Een Git-opslagplaats maken die de naamgevingsconventie volgt `component-environment-<region/country/brand>`:

   ```bash
   bin/magento module:enable --all
   cd ../
   mkdir component-environment-<region/country/brand>
   cd component-environment-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/component-environment-<region/country/brand>' \
    --description='<client> <region/country/brand> environment files' \
    --type=magento2-component \
    --require="magento/magento-composer-installer:*"
   mkdir -p app/etc
   cp ../project-<region/country/brand>/app/etc/config.php app/etc/
   composer config -e
   ```

1. Voeg de `app/etc/config.php` bestand als een toewijzing in het dialoogvenster `extra.map` kenmerk van uw `composer.json` bestand:

   ```json
   {
       "name": "example-client/component-environment-emea",
       "description": "Example client EMEA environment files",
       "type": "magento2-component",
       "require": {
           "magento/magento-composer-installer": "*"
       },
       "extra": {
           "map": [
               [
                   "app/etc/config.php",
                   "app/etc/config.php"
               ]
           ]
       }
   }
   ```

1. Valideer uw `composer.json` en toewijzen aan de Git-opslagplaats:

   ```bash
   composer validate
   git init
   git add --all
   git commit -m 'initialize component'
   git remote add origin git@bitbucket.org:<client>/component-environment-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

## Metapakketten instellen

1. Maak de volgende Git-opslagruimten:

   - `meta-gra`
   - `meta-<region/country/brand>`

1. Stel de volgende afhankelijkheidsstructuur in:

   ```tree
   client/project-<region/country/brand>
   └─ requires -> client/meta-<region/country/brand>
                  ├─ requires -> client/component-environment-<region/country/brand>
                  └─ requires -> client/meta-gra
                                 └─ requires -> magento/product-enterprise-edition
   ```

1. Maak het GRA-metapakket:

   ```bash
   cd ..
   mkdir meta-gra
   cd meta-gra
   composer init --no-interaction \
    --name='<client>/meta-gra' \
    --description='<client> GRA meta package' \
    --type=metapackage \
    --require="magento/product-enterprise-edition:<exact.required.version>"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-gra.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Maak het merkpakket:

   ```bash
   cd ..
   mkdir meta-<region/country/brand>
   cd meta-<region/country/brand>
   composer init --no-interaction \
    --name='<client>/meta-<region/country/brand>' \
    --description='<client> <region/country/brand> meta package' \
    --type=metapackage \
    --require="<client>/component-environment-<region/country/brand>:~0.1" \
    --require="<client>/meta-gra:~0.1"
   git init
   git add --all
   git commit -m 'initialize meta package'
   git remote add origin git@bitbucket.org:<client>/meta-<region/country/brand>.git
   git push -u origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Vereisen de inzameling door gebiedsdeelbeheer in het belangrijkste project:

   ```bash
   cd ../project-<region/country/brand>
   rm app/etc/config.php
   composer remove --no-update magento/product-enterprise-edition
   composer require --no-update "<client>/meta-<region/country/brand>:~0.1"
   composer config minimum-stability alpha
   composer config prefer-stable true
   composer update
   git add --all
   git commit -m 'set up GRA dependency tree'
   git push origin master
   git tag 0.1.0 -m "0.1.0"
   git push --tags
   ```

1. Controleren of de Composer de `app/etc/config.php` bestand van `<client>/component-environment-<region/country/brand>`.

## Code implementeren

Op de webserver kunt u code implementeren met Composer, maar u kunt het hoofdproject niet bijwerken. Installeer het project opnieuw gebruikend Composer met elke nieuwe plaatsing, die het vereiste voor de productie en testservers om toegang tot Git elimineert te hebben.

## Andere instanties en pakketten toevoegen

Elke instantie (regio, merk of anderszins unieke Adobe Commerce-installatie) moet een eigen instantie krijgen **hoofdproject** instantie, **specifieke metapakketten**, en **milieucomponent**. De **GRA-metapakket** moeten **gedeeld** in alle gevallen.

Functionele pakketten (zoals Adobe Commerce-modules, thema&#39;s, taalpakketten en bibliotheken) en pakketten van derden moeten verplicht worden gesteld door:

- **GRA-metapakket**—Voor installatie op _alles_ instances
- **instantiespecifieke metapack**—Voor installatie op één merk of regio

>[!IMPORTANT]
>
>Geen pakketten in de hoofdprojecten vereisen `composer.json` bestand op de `main` of `release` bijkantoren.

## Voorbereiden op ontwikkeling

Voor ontwikkeling, installatie `develop` versies van alle modules die u handhaaft.

Afhankelijk van uw vertakkingsstrategie hebt u mogelijk `develop`, `qa`, `uat`, en `main` bijkantoren. Elke vertakking bestaat in Composer met een `dev-` voorvoegsel Dus de `develop` vertakking kan via Composer als versie worden vereist `dev-develop`.

1. Maken `develop` vertakkingen in alle modules en projectgegevensbanken.

   ```bash
   cd ../component-environment-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../meta-<region/country/brand>
   git checkout master
   git checkout -b develop
   
   git push -u origin develop
   
   
   cd ../meta-gra
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   cd ../project-<region/country/brand>
   git checkout master
   git checkout -b develop
   git push -u origin develop
   
   
   composer require \
   "magento-services/meta-fantasy-corp:dev-develop as 0.999" \
   "magento-services/meta-gra:dev-develop as 0.999" \
   "magento-services/component-environment-fantasy-corp:dev-develop as 0.999"
   ```

   De vorige stap genereert de volgende regels in uw `composer.json` bestand:

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**Niet samenvoegen** deze `composer.json` wijzigingen in uw productietak aan te brengen. Alleen stabiele versies van pakketten installeren op `release` en `main` bijkantoren. U kunt deze afhankelijkheden definiëren voor `qa` bijkantoren en andere niet-hoofdbijkantoren.
