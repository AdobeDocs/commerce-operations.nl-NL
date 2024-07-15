---
title: Voorbeelden van algemene referentiearchitectuur
description: Zie voorbeelden van het beheren van code voor grootschalige Adobe Commerce-projecten.
role: Developer, Architect
level: Experienced
hide: true
hidefromtoc: true
exl-id: 2a85b9bf-e547-4a2a-9234-210865f55609
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '816'
ht-degree: 0%

---

# Voorbeelden van algemene referentiearchitectuur

Dit onderwerp beschrijft gemeenschappelijke manieren om a [ globale verwijzingsarchitectuur (GRA) te organiseren ](overview.md) codebasis. Hoewel de [ afzonderlijke pakketten ](#option-1-separate-packages) optie de voorkeur heeft, vereisen sommige situaties één van de andere hieronder beschreven opties.

## Definities

{{$include /help/_includes/gra-definitions.md}}

## Optie 1: Afzonderlijke pakketten

Zie ](composer/project-structure.md) beste praktijken van de het projectstructuur van 0} Composer voor vestiging deze methode.[

![ Diagram die de afzonderlijke pakketoptie voor globale verwijzingsarchitectuur illustreren ](../../../assets/playbooks/gra-separate-packages.png)

De meest flexibele manier om pakketten van de Composer van GRA te beheren is door metapakketten. Metapakketten bevatten alleen een `composer.json` -bestand, dat andere pakketafhankelijkheden definieert. Creeer metapakketten gebruikend [ Privé Pakketten ](https://packagist.com/) bewaarplaatsen.

### Hoofdproject `composer.json`

```json
{
    "name": "example-client/region-1",
    "description": "Example Client Region 1",
    "type": "project",
    "require": {
        "magento/product-enterprise-edition": "2.3.5",
        "example-client/meta-region-1": "~1.0"
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": [
        {"type": "composer", "url": "https://repo.packagist.com/example-client/"},
        {"packagist.org": false}
    ]
}
```

### `example-client/meta-region-1 composer.json`

```json
{
    "name": "example-client/meta-region-1",
    "description": "Region 1 meta package",
    "type": "metapackage",
    "require": {
        "example-client/meta-gra": "~1.0",
        "example-client/theme-frontend-region1",
        "example-client/language-es-es",
        "ingenico/ogone-client"
    }
}
```

### `example-client/meta-gra composer.json`

```json
{
    "name": "example-client/meta-gra",
    "description": "GRA meta package",
    "type": "metapackage",
    "require": {
        "geoip2/geoip2": "~2.0",
        "magento-services/module-stackify-logger": "~1.1",
        "example-client/sap-connector",
        "example-client/service-chat",
        "example-client/store-locator"
    }
}
```

Elke module, taalpakket, thema en bibliotheek heeft een eigen Git-opslagruimte. Elke Git-opslagplaats synchroniseert automatisch met de Private Packagist-opslagplaats en genereert daar een pakket zolang er zich een `composer.json` -bestand in de hoofdmap van de Git-opslagplaats bevindt.

## Opties 2: Bulkpakketten

Hieronder ziet u een voorbeeld van meerdere modules in één Composer-pakket.

Een bulkpakket kan alleen pakketten van hetzelfde type bevatten. Als u bijvoorbeeld meerdere pakketten hebt voor Adobe Commerce-modules, -thema&#39;s, -taalpakketten en -bibliotheken, moet u voor elk type afzonderlijke bulkpakketten maken.

De bestandsstructuur in de directory van de leverancier moet er als volgt uitzien. Controleer uw project echter om te zien wat in uw Git-opslagplaats moet worden opgenomen):

```tree
.
└── example-client/
    └── gra/
        └── src/
            ├── SapConnector/
            │   ├── etc/
            │   └── registration.php
            ├── ServiceChat/
            │   ├── etc/
            │   └── registration.php
            ├── StoreLocator/
            │   ├── etc/
            │   └── registration.php
            └── composer.json
```

Het bestand `composer.json` moet er als volgt uitzien:

```json
{
    "name": "example-client/gra",
    "description": "GRA Modules",
    "require": {
        "magento/magento-composer-installer": "*"
    },
    "type": "magento2-module",
    "autoload": {
        "files": [
            "src/SapConnector/registration.php",
            "src/ServiceChat/registration.php",
            "src/StoreLocator/registration.php"
        ],
        "psr-4": {
            "ExampleClient\\SapConnector\\": "src/SapConnector",
            "ExampleClient\\ServiceChat\\": "src/ServiceChat",
            "ExampleClient\\StoreLocator\\": "src/StoreLocator"
        }
    }
}
```

## Optie 3: Git splitsen

Deze architectuur gebruikt vier Git-opslagplaatsen om code op te slaan:

- `core`: bevat de kerninstallatie van Adobe Commerce. Wordt gebruikt om Adobe Commerce-versies bij te werken.
- `GRA`: bevat GRA-code. Alle modules GRA, taalpakketten, witte etiketthema&#39;s, en bibliotheken.
- `brand/region`: Elk merk of elke regio heeft een eigen opslagplaats met alleen merk- of regiospecifieke code.
- `release`: Alle bovenstaande gegevens worden samengevoegd in deze Git-opslagplaats. Alleen samenvoegvastleggingen zijn hier toegestaan.

![ Diagram die de gespleten optie van het Git voor globale verwijzingsarchitectuur ](../../../assets/playbooks/gra-split-git.png) illustreert

Deze optie instellen:

1. Maak de vier typen opslagruimte in Git. Maak de `core` - en `GRA` -opslagruimten maar één keer. Maak één `brand/region` - en één `release` -opslagplaats voor elk merk.

   Aanbevolen opslagplaatsnamen:

   - `m2-core`
   - `m2-gra`
   - `m2-region-x`/`m2-brand-x` (bijvoorbeeld `m2-emea`/`m2-adobe`)
   - `m2-release-region-x`/`m2-release-brand-x` (bijvoorbeeld `m2-release-emea`/`m2-release-adobe`)

1. Maak een map `release/` en voer de volgende handelingen uit om een gedeelde Git-geschiedenis voor alle rapporten te maken.

   ```bash
   git init
   git remote add origin git@github.com:example-client/m2-release-brand-x.git
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   touch .gitkeep
   git add .gitkeep
   git commit -m 'initialize repository'
   git push -u origin master
   git push core master
   git push gra master
   git push region-x master
   ```

1. Clone each repository, behalve `core` , in a different directory on your computer.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   git clone git@github.com:example-client/m2-region-x.git
   git clone git@github.com:example-client/m2-gra.git
   ```

1. [ installeer Adobe Commerce met Composer ](../../../installation/composer.md). Verwijder het `.gitignore` -bestand, voeg het `core` -bestand toe, voeg de code toe en wijs deze toe en druk op.

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition m2-core
   cd m2-core
   git init
   rm .gitignore
   git remote add origin git@github.com:example-client/m2-core.git
   git fetch
   git checkout .gitkeep
   git add --all
   git commit -m 'install Adobe Commerce'
   git push
   ```

1. Maak in de `GRA` -opslagplaats de volgende mappen:

   - `app/code/`
   - `app/design/`
   - `app/i18n/`
   - `lib/`

1. Code toevoegen. Verwijder het `.gitignore` -bestand, voeg de code toe en wijs deze toe, voeg de code extern toe en druk op de toets.

1. In de `brand/region` repository. Doe het zelfde als in `GRA` bewaarplaats en houd in mening dat de dossiers uniek moeten zijn. U kunt niet hetzelfde bestand opnemen in zowel deze gegevensopslagruimte als in de `GRA` gegevensopslagruimte.

1. Pas de samenvoeging toe in de `release` -opslagplaats.

   ```bash
   git clone git@github.com:example-client/m2-release-brand-x.git
   cd m2-release-brand-x
   git remote add core git@github.com:example-client/m2-core.git
   git remote add gra git@github.com:example-client/m2-gra.git
   git remote add region-x git@github.com:example-client/m2-region-x.git
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

1. Verwijder het `.gitkeep` -bestand.

1. Implementeer de `release` -opslagplaats op de productie-, test-, QA- en ontwikkelingsservers. Als u code `core` , `GRA` en `brand` upgradet, kunt u de volgende opdrachten net zo eenvoudig uitvoeren:

   ```bash
   git fetch --all
   git merge core/master gra/master brand-a/master
   git push
   ```

## Optie 4: Monorepo (aanbevolen)

Deze strategie bootst de manier na waarop de Magento Open Source Git-opslagplaats werkt.

Alle code wordt ontwikkeld en getest in één enkele bewaarplaats. Automatisering distileert pakketten van deze afzonderlijke opslagplaats, die op UAT- en productieomgevingen kan worden geïnstalleerd met behulp van Composer.

![ Diagram die de monorepo optie voor globale verwijzingsarchitectuur illustreert ](../../../assets/playbooks/gra-monorepo1.png)

Met de optie Monorepo kunt u eenvoudig in één opslagplaats werken en tegelijkertijd de flexibiliteit bieden om instanties samen te stellen met pakketten.

Versioning en pakketdestillatie worden gedaan door automatisering, gebruikend Acties GitHub of Acties GitLab.

![ Diagram die de monorepo optie voor globale verwijzingsarchitectuur illustreert ](../../../assets/playbooks/gra-monorepo2.png)

Zie de volgende bronnen voor meer informatie over deze automatisering:

- [ https://github.com/symplify/monorepo-builder](https://github.com/symplify/monorepo-builder)
- [ https://github.com/danharrin/monorepo-split-github-action](https://github.com/danharrin/monorepo-split-github-action)

>[!TIP]
>
>Het opzetten van een monorepo is geavanceerd, maar biedt de meeste flexibiliteit tegen de laagste overheadkosten.

## Combineer geen strategieën

Het is niet aan te raden om een gecombineerde benadering te gebruiken met Composer voor GRA-pakketten en de map `app/` voor merk- of regiopakketten.

U niet alleen krijgt alle _voordelen_ maar ook alle _nadelen_ van beide methodes. U moet een van de twee selecteren (Git of Composer) om optimaal te werken.

## Oplossingen om te vermijden

- **Module noemende overeenkomsten om GRA of merk** te betekenen

  Het noemen van modules om GRA of merk te noemen leidt tot gebrek aan flexibiliteit. In plaats daarvan gebruikt u Composer-metagegevens om te bepalen tot welke groep een module behoort. Voor klant VF bevat pakket `vf/meta-gra` bijvoorbeeld verwijzingen naar alle GRA-pakketten en kan het worden geïnstalleerd met de opdracht `composer require vf/meta-gra` . Pakket `vf/meta-kipling` bevat verwijzingen naar alle specifieke pakketten voor Kipling en naar het `vf/meta-gra` -pakket. Modules krijgen bijvoorbeeld de naam `vf/module-sales` en `vf/module-sap` . Met deze naamgevingsconventie kunt u pakketten verplaatsen tussen merk- en GRA-status, met een lage impact.

- **de kernverbeteringen van Adobe Commerce per geval**

  Plan Adobe Commerce-kernupgrades, inclusief patchupgrades, zodat verschillende merken of regio&#39;s zo nauw mogelijk kunnen worden uitgevoerd. Het steunen van veelvoudige versies van Adobe Commerce voor gedeelde modules leidt tot het smeken van modules wegens verenigbaarheidsbeperkingen en meer dan verdubbelt de onderhoudsinspanning. Vermijd deze grotere inspanning door ervoor te zorgen dat alle instanties op de zelfde versie van Adobe Commerce alvorens regelmatige ontwikkeling lopen.
