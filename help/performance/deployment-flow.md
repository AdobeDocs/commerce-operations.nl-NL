---
title: Implementatiestroom
description: Meer informatie over de stappen die nodig zijn voor het implementeren van Adobe Commerce in een productieomgeving.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Implementatiestroom

De [!DNL Commerce] -workflow voor productieimplementatie helpt een winkel maximale prestaties te behalen.

## Afhankelijkheden installeren

De `composer.json` - en `composer.lock` -bestanden beheren [!DNL Commerce] -afhankelijkheden en installeren de juiste versie voor elk pakket. U moet gebiedsdelen installeren vóór [ preprocessing de instructies van de gebiedsinjectie ](#preprocess-dependency-injection-instructions) als u van plan bent om [ autoloader ](#update-the-autoloader) bij te werken.

Om [!DNL Commerce] gebiedsdelen te installeren:

```bash
composer install --no-dev
```

## Instructies voor het injecteren van afhankelijkheden voorafgaand aan het proces

Wanneer u instructies voor het vooraf verwerken en compileren van de injectie voor afhankelijkheid (DI), Magento:

* Alle huidige configuratie lezen en verwerken
* Hiermee analyseert u afhankelijkheden tussen klassen
* Automatisch gegenereerde bestanden maken (inclusief proxy&#39;s, fabrieken, enz.)
* Slaat gecompileerde gegevens en configuratie in een geheime voorgeheugen op dat tot 25% van tijd op verzoekverwerking bewaart

Om instructies vooraf te verwerken en te compileren DI:

```bash
bin/magento setup:di:compile
```

## De autoloader bijwerken

Na compilatie voltooit, bevestig dat [ APCu ](../performance/software.md#php-settings) wordt toegelaten en autoloader bijwerkt:

De autoloader bijwerken:

>[!INFO]
>
>Met de optie `-o` wordt automatisch laden van PSR-0/4 omgezet in een klasse-toewijzing voor een snellere autoloader. De optie `--apcu` gebruikt APCu om gevonden/niet-gevonden klassen in de cache op te slaan.

```bash
composer dump-autoload -o --apcu
```

Als u van plan bent om autoloader bij te werken, moet u de volgende bevelen in orde in werking stellen:

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## Statische inhoud implementeren

Door het implementeren van statische inhoud voert [!DNL Commerce] de volgende handelingen uit:

* Alle statische bronnen analyseren
* Samenvoegen, minimaliseren en bundelen van inhoud uitvoeren
* Themagegevens lezen en verwerken
* Thema-fallback analyseren
* Sla alle verwerkte en gematerialiseerde inhoud op in een specifieke map voor verder gebruik

Als uw statische inhoud niet wordt geïmplementeerd, voert [!DNL Commerce] alle vermelde bewerkingen direct uit, wat resulteert in een aanzienlijke toename van de responstijd.

U kunt een verscheidenheid van opties gebruiken om plaatsingsverrichtingen aan te passen die op archiefgrootte en vervulling behoeften worden gebaseerd. Het meest algemeen is compact opstellen strategie. Zie [ Statische strategieën van de dossierplaatsing ](../configuration/cli/static-view-file-strategy.md)

Statische inhoud implementeren:

```bash
bin/magento setup:static-content:deploy
```

Met deze opdracht kan Composer de toewijzing aan projectbestanden opnieuw samenstellen, zodat deze sneller worden geladen.

## Productiemodus instellen

>[!INFO]
>
>Wanneer u de modus instelt op productie, worden automatisch `setup:di:compile` en `setup:static-content:deploy` uitgevoerd.

Tot slot moet u uw winkel in de productiemodus plaatsen. De productiemodus is speciaal geoptimaliseerd voor maximale prestaties in uw winkel. Bovendien worden alle ontwikkelaarspecifieke functies gedeactiveerd. Dit kan in uw `.htaccess` - of `nginx.conf` -bestand worden gedaan:

`SetEnv MAGE_MODE production`

U kunt statische inhoud ook opstellen, de inhoud compileren, en de wijze in één CLI bevel plaatsen:

```bash
bin/magento deploy:mode:set production
```

De opdracht wordt op de achtergrond uitgevoerd en u kunt geen aanvullende opties instellen voor elke specifieke stap.

## Aanvullende acties voorafgaand aan de lancering

Deze stappen worden aanbevolen, maar zijn niet verplicht. U kunt deze meteen uitvoeren voordat u de winkel in de productiemodus start. De lijst bevat:

* Wijzig de index van gegevens om te voorkomen dat er inconsistente gegevens in de indexen voorkomen.
* Maak de cache leeg om er zeker van te zijn dat er geen oude of onjuiste gegevens in de cache blijven staan.
* Warm omhoog het geheime voorgeheugen, dat de populairste of kritieke opslagpagina&#39;s vooraf roept, zodat wordt het geheime voorgeheugen voor hen geproduceerd en opgeslagen. Deze bewerking kan worden uitgevoerd met elke internetcrawler of handmatig, als u een kleine winkel hebt.
