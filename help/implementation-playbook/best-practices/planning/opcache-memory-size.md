---
title: Aanbevolen werkwijze voor grootte van OPcache-geheugen
description: Beschrijft hoe te om prestatiesdegradatie door specifieke montages van OPcache geheugenconsumptie op Adobe Commerce projecten te vermijden.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---


# Aanbevolen werkwijze voor OPcache-geheugengrootte in Adobe Commerce

Voor Adobe Commerce on cloud Infrastructure Pro-planarchitectuur 2.3.x wordt aanbevolen `opcache.memory_consumption` tot ten minste 2 GB om verslechtering van de prestaties te voorkomen.

## Betrokken producten en versies

* Adobe Commerce on cloud Infrastructure Pro-planarchitectuur 2.3.x
* PHP 7.0 en hoger

## Geheugen configureren

Minstens toewijzen **2 GB** van geheugen voor de [OPcache PHP-module](https://www.php.net/manual/en/book.opcache.php). De OPcache-module is geconfigureerd in de `php.ini` bestand. Om 2048 MB geheugen toe te wijzen, reeks `opcache.memory_consumption = 2048`.

## Aanvullende informatie

* [Best practices voor prestaties - PHP-instellingen](../../../performance/software.md#php-settings)
* [PHP-opties configureren](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](database-on-cloud.md)
* [Meest voorkomende databaseproblemen in Adobe Commerce met cloudinfrastructuur](../maintenance/resolve-database-performance-issues.md)
* [Indexers &quot;Update On Schedule&quot; optimaliseert de Adobe Commerce-prestaties](../maintenance/indexer-configuration.md)
