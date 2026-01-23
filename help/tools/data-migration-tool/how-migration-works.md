---
title: Hoe werkt gegevensmigratie?
description: Meer informatie over het migratieproces van gegevens tussen Magento 1 en Magento 2, zoals terminologie, workflowdiagrammen en stappen.
exl-id: 821492dc-ee5b-4c4a-9479-680ee8c5756d
topic: Commerce, Migration
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 0%

---

# Hoe werkt gegevensmigratie?

Dit onderwerp biedt een overzicht op hoog niveau van de manier waarop gegevens worden gemigreerd van Magento 1 naar Magento 2 met de [!DNL Data Migration Tool] .

[!DNL Data Migration Tool] is een opdrachtregelinterface-hulpmiddel (CLI) voor het overbrengen van gegevens van Magento 1 naar Magento 2. Het hulpmiddel verifieert consistentie tussen Magento 1 en 2 gegevensbestandstructuren (lijsten en gebieden), volgt de vooruitgang van de gegevensoverdracht, leidt tot logboeken, en stelt tests van de gegevenscontrole in werking.

## Terminologie

* **Wijzen** - een bevolen reeks verrichtingen voor het migreren van gegevens van Magento 1.x aan Magento 2.x.
* **Stappen** - de taken op een wijze die de soorten te migreren gegevens bepalen.
* **Stages** - de taken in stap die, de gegevens bevestigen overbrengen en verifiëren.
* **dossiers van de Kaart** - de dossiers van XML die de regels en de verbindingen tussen Magento 1.x en Magento 2.x gegevensstructuren voor de voltooiing van de stadia bepalen.

## Modi

[!DNL Data Migration Tool] verdeelt het migratieproces in drie fasen of *wijzen* om gegevens over te brengen en aan te passen van Magento 1.x aan Magento 2.x. De drie modi worden hier vermeld en moeten in deze volgorde worden uitgevoerd:

1. **Wijze van Montages**: migreert de systeemconfiguratie en website-verwante montages.
1. **Wijze van Gegevens**: migreert gegevensbestandactiva in bulk.
1. **Wijze van Delta**: migreert stijgende veranderingen (veranderingen sinds de laatste looppas), zoals nieuwe klanten en orden.

![&#x200B; de Wijzen van de Migratie &#x200B;](../../assets/data-migration/MigrationModes2.png)

## Stappen

[!DNL Data Migration Tool] gebruikt een lijst van *stappen* binnen elke wijze om een bepaald type van gegevens te migreren. In de modus Instellingen worden bijvoorbeeld twee stappen gebruikt om alle instellingsgegevens te migreren: de stap Opslag en de stap Instellingen. De details over de specifieke gegevens die in elk van deze stappen (en voor stappen in de andere wijzen) worden gemigreerd, kunnen in de [[!DNL Data Migration Tool]  Technische Specificatie &#x200B;](technical-specification.md) worden gevonden.

![&#x200B; Overzicht van de Migratie &#x200B;](../../assets/data-migration/MigrationOverview2.png)

## Staven

Binnen elke stap zijn drie *stadia* die altijd in deze orde worden uitgevoerd om ervoor te zorgen dat de gegevens behoorlijk worden gemigreerd:

1. **Controle van de Integriteit**: Vergelijkt de namen, de types, en andere info van het lijstgebied om verenigbaarheid tussen Magento 1 en 2 gegevensstructuren te verifiëren.
1. **Overdracht van Gegevens**: Brengt de gegevenslijst door lijst van Magento 1 en 2 over.
1. **Controle van het Volume**: Vergelijkt het aantal verslagen tussen lijsten om te verifiëren dat de overdracht succesvol was.

![&#x200B; de stadia van de Migratie &#x200B;](../../assets/data-migration/MigrationSteps2.png)

## Bestanden toewijzen

Op het laagste niveau van de migratieprocessen zijn de *kaartdossiers van XML*. In [!DNL Data Migration Tool] worden kaartbestanden gebruikt in de fasen van een stap voor het transformeren van verschillende gegevensstructuren tussen de Magento 1.x- en 2.x-tabellen.

Wanneer u bijvoorbeeld gegevens transformeert van een Magento Open Source 1.8.0.0 -database naar Magento Open Source 2.x.x, wordt in het kaartbestand het feit verwerkt dat de naam van een tabel is gewijzigd en wordt de naam van de tabel dienovereenkomstig gewijzigd in de doeldatabase. Als er geen verschillen in gegevensstructuur of gegevensformaat zijn, brengt [!DNL Data Migration Tool] het ongewijzigd, met inbegrip van gegevens van lijsten die door uitbreidingen worden gecreeerd, aan het gegevensbestand van Magento 2 over.

Als verschillen niet worden gedeclareerd in toewijzingsbestanden, geeft de [!DNL Data Migration Tool] een fout weer en wordt deze niet gestart.

De dossiers van de toewijzing worden besproken meer in detail in [[!DNL Data Migration Tool] Technische Specificatie].

## Migratiestroomdiagram

![&#x200B; Stroom van de Migratie &#x200B;](../../assets/data-migration/migration_flow.png)

[[!DNL Data Migration Tool] Technische specificaties](technical-specification.md)

We zijn blij dat je overweegt om van het #1 commerceplatform van de wereld — Magento 1.x — over te stappen op het platform van de toekomst, Magento 2. We zijn blij dat we de details van dit proces, dat we migratie noemen, kunnen delen.

## Migratieonderdelen

Magento 2-migratie omvat vier componenten: gegevens, extensies en aangepaste code, thema&#39;s en aanpassingen.

### Gegevens

Wij hebben **Magento 2[!DNL Data Migration Tool]** ontwikkeld om u te helpen efficiënt al uw producten, klanten, en ordegegevens bewegen, configuraties, bevorderingen, en meer aan Magento 2 opslaan. Deze handleiding bevat informatie over het gereedschap en tips en trucs voor het gebruik ervan bij het migreren van gegevens.

### Extensies en aangepaste code

We hebben hard samengewerkt met de ontwikkelingsgemeenschap om u te helpen uw Magento 1-extensies te gebruiken in Magento 2. Nu zijn wij trots om [&#x200B; Commerce Marketplace &#x200B;](https://commercemarketplace.adobe.com//) voor te stellen, waar u de recentste versies van uw favoriete uitbreidingen kunt downloaden of kopen.

Meer informatie bij het ontwikkelen van uitbreidingen voor Magento 2 is beschikbaar in de [&#x200B; Gids van de Ontwikkelaar PHP &#x200B;](https://developer.adobe.com/commerce/php/development/).

### Thema&#39;s en aanpassingen

Magento 2 maakt gebruik van nieuwe benaderingen en technologieën die handelaren een ongeëvenaarde mogelijkheid bieden om innovatieve boodschappenervaringen te creëren en op een hoger niveau te schalen. Om van deze vooruitgang te profiteren, moeten de ontwikkelaars veranderingen in hun thema&#39;s en aanpassingen aanbrengen. De documentatie is online beschikbaar voor het creëren van Magento 2 [&#x200B; thema&#39;s &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/themes/), [&#x200B; lay-outs &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/layouts/), en [&#x200B; aanpassingen &#x200B;](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-manage/).

## Migratiepogingen

Net als bij een upgrade tussen 1.x-versies (bijvoorbeeld van v1.12 naar v1.14), is de mate van inspanning voor het migreren van Magento 1 naar Magento 2 afhankelijk van de manier waarop u uw site hebt gemaakt en het niveau van aanpassing.
Nochtans, verbeteren wij constant [!DNL Data Migration Tool] (zie [&#x200B; Changelog &#x200B;](https://github.com/magento/data-migration-tool/blob/2.3/CHANGELOG.md) voor meer details); zodat nemen de migratieinspanningen voortdurend af.
