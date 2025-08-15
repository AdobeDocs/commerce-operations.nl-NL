---
title: Realpath cache-grootte
description: Leer hoe u de Adobe Commerce-prestaties kunt optimaliseren door de PHP readlpath-cacheconfiguratie bij te werken en aanbevolen instellingen te gebruiken.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor configuratie van cache in realpath

De cache van Realpath slaat de echte bestandssysteempaden van bestandsnamen waarnaar wordt verwezen in in plaats van ze elke keer weer op te zoeken. Telkens wanneer verschillende bestandfuncties worden uitgevoerd of een bestand nodig hebben en een relatief pad gebruiken, moet PHP zoeken waar dat bestand echt bestaat.

Als u de Commerce-prestaties wilt verbeteren, kunt u de volgende aanbevolen instellingen gebruiken om de `realpath_cache` -instellingen in het `php.ini` -bestand te configureren:

- Cachegrootte aan 10 MB (`realpath cache_size=10M`) plaatsen
- Tijd instellen op live (ttl) tot 7200 seconden (`realpath_cache_ttl=7200`)

Voor configuratieinstructies, zie [ hoe te om PHP opties ](../../../installation/prerequisites/php-settings.md#how-to-set-php-options) te plaatsen.

## Betrokken producten en versies

- Adobe Commerce op locatie, alle versies 2.3.x en hoger
- Adobe Commerce op cloudinfrastructuur, alle versies 2.3.x en hoger

## Mogelijke gevolgen voor de prestaties

Als de de configuratiewaarden van het geheime voorgeheugen Realpath te laag of te hoog zijn, voegt het extra overheadkosten tijdens geheim voorgeheugengeneratie toe die prestaties vertraagt.

## Aanvullende informatie

- [Op locatie: PHP-instellingen](../../../performance/software.md#php-settings)
- Op cloudinfrastructuur:
   - [Best practices voor databases](database-on-cloud.md)
   - [Meest voorkomende databaseproblemen in de Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Indexers &quot;Update On Schedule&quot; optimaliseert de Magento-prestaties](../maintenance/indexer-configuration.md)
