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

Deze gids beschrijft hoe te opstelling en de [ afzonderlijke pakketoptie ](../examples.md#option-1-separate-packages) te handhaven die} in de globale die verwijzingsarchitectuur (GRA) voorbeelden wordt beschreven.

## Vereisten

Controleer voordat u begint het volgende:

- U hebt een Git-opslagplaats
- U hebt een bewaarplaats Composer (dit onderwerp benadrukt Privé Packagist)
- U hebt uw Composer-opslagplaats zo geconfigureerd dat deze de `repo.magento.com` - en `packagist.org` repositories spiegelt

## Hoofd-Git-projectgegevensopslagplaats

De belangrijkste Git-projectgegevensopslagruimte mag alleen een Composer-project bevatten. U kunt alle andere elementen beheren met Composer-pakketten. Het hoofdproject mag alleen de volgende bestandsstructuur bevatten, omdat Composer alle andere pakketten via afhankelijkheden installeert:

```tree
./
├─ .git/
├─ .gitignore
├─ composer.json
└─ composer.lock
```

Voeg de volgende inhoud toe aan het `.gitignore` -bestand:

```tree
/*
!/composer.json
!/composer.lock
```

## Het hoofdproject initialiseren

1. Maak een Git-gegevensopslagruimte met de naam `project-<region/country/brand>` .

1. Maak `composer.json` - en `composer.lock` -bestanden:

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

1. Voeg het `app/etc/config.xml` -bestand toe aan de Git-opslagplaats.

   Met de module die u gaat maken kunt u andere regio- of merkspecifieke bestanden installeren, zoals `.htaccess` -, Google- of Bing-verificatietekstbestanden, uitvoerbare bestanden of andere statische bestanden die niet door Adobe Commerce-modules worden beheerd.

   Gebruik `magento2-component` -typepakketten om een bestandstoewijzing te maken waarmee bestanden tijdens `composer install` - en `composer update` -bewerkingen naar de hoofdopslagplaats voor Git kunnen worden gekopieerd.

1. Maak een Git-opslagplaats die de naamgevingsconventie volgt `component-environment-<region/country/brand>` :

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

1. Voeg het `app/etc/config.php` -bestand toe als een toewijzing in het `extra.map` -kenmerk van het `composer.json` -bestand:

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

1. Valideer uw `composer.json` -bestand en wijs het toe aan de Git-opslagplaats:

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

1. Controleer of Composer het `app/etc/config.php` -bestand heeft gekopieerd van `<client>/component-environment-<region/country/brand>` .

## Code implementeren

Op de webserver kunt u code implementeren met Composer, maar u kunt het hoofdproject niet bijwerken. Installeer het project opnieuw gebruikend Composer met elke nieuwe plaatsing, die het vereiste voor de productie en testservers om toegang tot Git elimineert te hebben.

## Andere instanties en pakketten toevoegen

Elke instantie (gebied, merk, of anders unieke installatie van Adobe Commerce) zou zijn eigen **belangrijkste project** instantie, **specifieke metapack**, en **pakket van de milieucomponent** moeten krijgen. Het **metapakket GRA** zou **** over alle instanties moeten worden gedeeld.

Functionele pakketten (zoals Adobe Commerce-modules, thema&#39;s, taalpakketten en bibliotheken) en pakketten van derden moeten verplicht worden gesteld door:

- **metapack GRA** - voor installatie op _alle_ instanties
- **instantie-specifieke metapack** - voor installatie op één enkel merk of gebied

>[!IMPORTANT]
>
>Vereist geen pakketten in het `composer.json` -bestand van het hoofdproject in de `main` - of `release` -vertakkingen.

## Voorbereiden op ontwikkeling

Installeer voor ontwikkeling `develop` versies van alle modules die u onderhoudt.

Afhankelijk van uw vertakkingsstrategie kunt u `develop` , `qa` , `uat` en `main` vertakkingen hebben. Elke vertakking bestaat in Composer met een voorvoegsel `dev-` . De `develop` -vertakking kan dus als versie `dev-develop` via Composer worden vereist.

1. Maak `develop` -vertakkingen in alle modules en projectopslagruimten.

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

   Bij de vorige stap worden de volgende regels in het `composer.json` -bestand gegenereerd:

   ```json
   "require": {
       "magento-services/component-environment-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-fantasy-corp": "dev-develop as 0.999",
       "magento-services/meta-gra": "dev-develop as 0.999"
   },
   ```

   >[!IMPORTANT]
   >
   >**voeg** deze `composer.json` dossierveranderingen in uw productietak niet samen. Installeer alleen stabiele versies van pakketten in `release` - en `main` -vertakkingen. U kunt deze afhankelijkheden definiëren voor `qa` -vertakkingen en andere niet-hoofdvertakkingen.
