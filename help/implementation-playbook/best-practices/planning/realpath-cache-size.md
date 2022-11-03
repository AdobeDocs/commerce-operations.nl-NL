---
title: Realpath-cachegrootte
description: Leer hoe u de Adobe Commerce-prestaties kunt optimaliseren door de PHP readlpath-cacheconfiguratie bij te werken en aanbevolen instellingen te gebruiken.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor configuratie van cache in realpath

De cache van Realpath slaat de echte bestandssysteempaden van bestandsnamen waarnaar wordt verwezen in in plaats van ze elke keer weer op te zoeken. Telkens wanneer verschillende bestandfuncties worden uitgevoerd of een bestand nodig hebben en een relatief pad gebruiken, moet PHP zoeken waar dat bestand echt bestaat.

Om de prestaties van de Handel te verbeteren, gebruik de volgende geadviseerde montages om te vormen `realpath_cache` in de `php.ini` bestand:

- De cachegrootte instellen op 10 MB (`realpath cache_size=10M`)
- Tijd instellen op live (ttl) tot 7200 seconden (`realpath_cache_ttl=7200`)

Voor configuratieinstructies, zie [PHP-opties instellen](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Betrokken producten en versies

- Adobe Commerce op locatie, alle versies 2.3.x en hoger
- Adobe Commerce op cloudinfrastructuur, alle versies 2.3.x en hoger

## Mogelijke gevolgen voor de prestaties

Als de de configuratiewaarden van het geheime voorgeheugen Realpath te laag of te hoog zijn, voegt het extra overheadkosten tijdens geheim voorgeheugengeneratie toe die prestaties vertraagt.

## Aanvullende informatie

- [Op het terrein: PHP-instellingen](../../../performance/software.md#php-settings)
- Op cloudinfrastructuur:
   - [Best practices voor databases](database-on-cloud.md)
   - [Meest voorkomende databaseproblemen in Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Met indexeerprogramma&#39;s &quot;Update On Schedule&quot; worden de Magento-prestaties geoptimaliseerd](../maintenance/indexer-configuration.md)

