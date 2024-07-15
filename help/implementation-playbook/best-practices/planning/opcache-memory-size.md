---
title: Aanbevolen werkwijze voor grootte van OPcache-geheugen
description: Beschrijft hoe te om prestatiesdegradatie door specifieke montages van OPcache geheugenconsumptie op Adobe Commerce projecten te vermijden.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 0%

---

# Aanbevolen werkwijze voor OPcache-geheugengrootte in Adobe Commerce

Voor Adobe Commerce op cloud Infrastructure Pro-planarchitectuur 2.3.x wordt aangeraden `opcache.memory_consumption` in te stellen op ten minste 2 GB om te voorkomen dat de prestaties achteruitgaan.

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure Pro-planarchitectuur 2.3.x
* PHP 7.0 en hoger

## Geheugen configureren

Wijs minstens **2GB** van geheugen voor de [ PHP module OPCache ](https://www.php.net/manual/en/book.opcache.php) toe. De OPcache-module is geconfigureerd in het `php.ini` -bestand. Stel `opcache.memory_consumption = 2048` in om 2048 MB geheugen toe te wijzen.

## Aanvullende informatie

* [ Beste praktijken van Prestaties - PHP Montages ](../../../performance/software.md#php-settings)
* [ vorm PHP opties ](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](database-on-cloud.md)
* [Meest voorkomende databaseproblemen in Adobe Commerce met cloudinfrastructuur](../maintenance/resolve-database-performance-issues.md)
* [Indexers &quot;Update On Schedule&quot; optimaliseert de Adobe Commerce-prestaties](../maintenance/indexer-configuration.md)
