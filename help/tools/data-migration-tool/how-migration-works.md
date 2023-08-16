---
title: Hoe werkt gegevensmigratie?
description: Leer over het proces van de gegevensmigratie tussen Magento 1 en Magento 2, met inbegrip van terminologie, werkschemadiagrammen, en stappen.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 0%

---

# Hoe werkt gegevensmigratie?

Dit onderwerp verstrekt een overzicht op hoog niveau van hoe de gegevens van Magento 1 aan Magento 2 worden gemigreerd gebruikend [!DNL Data Migration Tool].

De [!DNL Data Migration Tool] is een bevel-lijn interfacegereedschap (CLI) dat voor het overbrengen van gegevens van Magento 1 naar Magento 2 wordt gebruikt. Het hulpmiddel verifieert consistentie tussen Magento 1 en 2 gegevensbestandstructuren (lijsten en gebieden), volgt de vooruitgang van de gegevensoverdracht, leidt tot logboeken, en stelt tests van de gegevenscontrole in werking.

## Terminologie

* **Modi** - een geordende reeks bewerkingen voor het migreren van gegevens van Magento 1.x naar Magento 2.x.
* **Stappen** - de taken in een modus die bepalen welke soorten gegevens moeten worden gemigreerd.
* **Staven** - de taken in stap die, de gegevens bevestigen overbrengen en verifiëren.
* **Bestanden toewijzen** - XML-bestanden die de regels en verbindingen tussen Magento 1.x- en Magento 2.x-gegevensstructuren definiëren voor het voltooien van de fasen.

## Modi

De [!DNL Data Migration Tool] het migratieproces in drie fasen onderverdeeld of *modi* om gegevens van Magento 1.x naar Magento 2.x over te brengen en aan te passen. De drie modi worden hier vermeld en moeten in deze volgorde worden uitgevoerd:

1. **Instellingenmodus**: migreert de systeemconfiguratie en aan websites gerelateerde instellingen.
1. **Gegevensmodus**: migreert de database-elementen bulksgewijs.
1. **Delta-modus**: migreert incrementele wijzigingen (wijzigingen sinds de laatste uitvoering), zoals nieuwe klanten en bestellingen.

![Migratiemodi](../../assets/data-migration/MigrationModes2.png)

## Stappen

De [!DNL Data Migration Tool] gebruikt een lijst van *stappen* in elke modus om een bepaald type gegevens te migreren. In de modus Instellingen worden bijvoorbeeld twee stappen gebruikt om alle instellingsgegevens te migreren: de stap Opslag en de stap Instellingen. Meer informatie over de specifieke gegevens die in elk van deze stappen worden gemigreerd (en voor stappen in de andere modi) vindt u in de [[!DNL Data Migration Tool] Technische specificaties](technical-specification.md).

![Migratieoverzicht](../../assets/data-migration/MigrationOverview2.png)

## Staven

Binnen elke stap zijn er drie *fases* die altijd in deze volgorde worden uitgevoerd om ervoor te zorgen dat de gegevens correct worden gemigreerd:

1. **Integriteitscontrole**: Vergelijkt de namen, typen en andere gegevens van de tabelvelden om de compatibiliteit tussen Magento 1 en 2-gegevensstructuren te controleren.
1. **Gegevensoverdracht**: Brengt de gegevenslijst door lijst van Magento 1 en 2 over.
1. **Volume controleren**: Vergelijkt het aantal records tussen tabellen om te controleren of de overdracht is gelukt.

![Migratiefasen](../../assets/data-migration/MigrationSteps2.png)

## Bestanden toewijzen

Op het laagste niveau van de migratieprocessen zijn de XML *kaartbestanden*. De [!DNL Data Migration Tool] gebruikt kaartdossiers binnen de stadia van een stap om verschillende gegevensstructuren tussen de Magento 1.x en 2.x lijsten om te zetten.

Bijvoorbeeld, wanneer u gegevens van een gegevensbestand van de Magento Open Source 1.8.0.0 in Magento Open Source 2.x.x omzet, verklaart het kaartdossier het feit dat een lijst werd anders genoemd, en noemt het dienovereenkomstig in het bestemmingsgegevensbestand anders. Als er geen verschillen zijn in de gegevensstructuur of gegevensindeling, [!DNL Data Migration Tool] brengt het ongewijzigd, met inbegrip van gegevens van lijsten die door uitbreidingen worden gecreeerd, naar Magento 2 gegevensbestand over.

Wanneer verschillen niet in kaartbestanden worden gedeclareerd, wordt de [!DNL Data Migration Tool] geeft een fout weer en wordt niet gestart.

Toewijzingsbestanden worden nader besproken in [[!DNL Data Migration Tool] Technische specificatie].

## Migratiestroomdiagram

![Migratiestroom](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] Technische specificaties](technical-specification.md)

We zijn blij dat je overweegt om van het #1 commerceplatform van de wereld — Magento 1.x — over te stappen op het platform van de toekomst, Magento 2. We zijn blij dat we de details van dit proces, dat we migratie noemen, kunnen delen.

## Migratieonderdelen

Magento 2 migratie omvat vier componenten: gegevens, extensies en aangepaste code, thema&#39;s en aanpassingen.

### Gegevens

We hebben de **MAGENTO 2[!DNL Data Migration Tool]** om u te helpen efficiënt al uw producten, klanten, en bestellen gegevens bewegen, opslagconfiguraties, bevorderingen, en meer aan Magento 2. Deze handleiding bevat informatie over het gereedschap en tips en trucs voor het gebruik ervan bij het migreren van gegevens.

### Extensies en aangepaste code

We hebben hard samengewerkt met de ontwikkelingsgemeenschap om u te helpen bij het gebruik van de extensies voor Magento 1 in Magento 2. Nu zijn we er trots op de [Commerce Marketplace](https://marketplace.magento.com/), waar u de nieuwste versies van uw favoriete extensies kunt downloaden of aanschaffen.

Meer informatie over het ontwikkelen van extensies voor Magento 2 is beschikbaar in de [PHP-ontwikkelaarsgids](https://developer.adobe.com/commerce/php/development/).

### Thema&#39;s en aanpassingen

Magento 2 maakt gebruik van nieuwe benaderingen en technologieën die handelaren een ongekende mogelijkheid bieden om innovatieve boodschappenervaringen te creëren en op een hoger niveau te schalen. Om van deze vooruitgang te profiteren, moeten de ontwikkelaars veranderingen in hun thema&#39;s en aanpassingen aanbrengen. Documentatie is online beschikbaar voor het maken van Magento 2 [thema&#39;s](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [schermindelingen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/), en [aanpassingen](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Migratiepogingen

Net als bij een upgrade tussen 1.x-versies (bijvoorbeeld van v1.12 naar v1.14), is de mate van inspanning voor het migreren van Magento 1 naar Magento 2 afhankelijk van de manier waarop u uw site hebt gemaakt en het niveau van aanpassing.
We verbeteren echter voortdurend de [!DNL Data Migration Tool] (zie de [Changelog](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) voor meer details ) , zodat de inspanningen op het gebied van migratie voortdurend afnemen .
