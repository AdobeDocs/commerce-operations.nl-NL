---
title: Prestaties optimaliseren, Recommendations
description: Optimaliseer de prestaties van uw implementatie van de Handel van de Adobe door deze aanbevelingen te volgen.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 0%

---


# Evaluatie voor optimalisatie van prestaties

Even as performance optimization can come from many aspects, there are some general recommendations that should be considered for most scenarios. Dit omvat configuratieoptimalisering voor infrastructuurelementen, de achtergrondconfiguratie van de Handel van de Adobe, en architectuur scalability planning.

## Infrastructuur

In de volgende secties worden aanbevelingen voor infrastructuuroptimalisatie beschreven.

### DNS-zoekopdrachten

DNS lookup is the process of finding which IP address that the domain name belongs to. De browser moet wachten tot de DNS raadpleging volledig is alvorens het om het even wat voor elk verzoek kan downloaden. Het verminderen van DNS raadplegingen is belangrijk om algemene pagina ladingstijden te verbeteren.

### CDN (Content Delivery Network)

Gebruik een CDN om de downloadprestaties van elementen te optimaliseren. Adobe Commerce gebruikt snel. Als een implementatie van de Handel van Adobe op-gebouw heeft, zou u ook moeten overwegen toevoegend een laag CDN.

### Webvertraging

De locatie van het datacenter is van invloed op de webvertraging voor frontend-gebruikers.

### Netwerkbandbreedte

Sufficient network bandwidth is one of the key requirements for data exchange between web nodes, databases, caching/session servers, and other services.

Because Adobe Commerce effectively leverages caching for high performance, your system can actively exchange data with caching servers like Redis. Als Redis zich op een externe server bevindt, moet u een voldoende netwerkkanaal tussen webknooppunten en de caching-server opgeven om knelpunten bij lees- en schrijfbewerkingen te voorkomen.

### Besturingssysteem (OS)

Configuraties en optimalisaties van besturingssystemen zijn vergelijkbaar voor Adobe Commerce in vergelijking met andere webtoepassingen met hoge belasting. As the number of concurrent connections handled by the server increases, the number of available sockets can become fully allocated.

### CPU of web nodes

Eén CPU-core kan ongeveer 2-4 Adobe Commerce-aanvragen zonder cache uitvoeren. Om te bepalen hoeveel Webknopen/kernen nodig waren om alle inkomende verzoeken te verwerken zonder hen in rij te zetten, gebruik de vergelijking:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM-instellingen

Optimizing these settings depends on the performance test results for different projects.

- **ByteCode**—To get maximum speed out of Adobe Commerce on PHP 7, you must activate the `opcache` module and configure it properly.

- **APCU** - We raden u aan de PHP APCu-extensie in te schakelen en Composer te configureren voor optimale prestaties. Deze uitbreiding plaatst dossierplaatsen voor geopende dossiers in het voorgeheugen, die prestaties voor de servervraag van de Handel van de Adobe, met inbegrip van pagina&#39;s, Ajax vraag, en eindpunten verhoogt.

- **Realpath_cacheconfiguration**—Optimaliseren  `realpath_cache` maakt het mogelijk dat PHP-processen paden naar bestanden in cache plaatsen in plaats van ze elke keer weer op te zoeken wanneer een pagina wordt geladen.

### Web server

Slechts is een lichte herconfiguratie nodig om nginx als Webserver te gebruiken. De nginx-webserver biedt betere prestaties en is eenvoudig te configureren met behulp van het voorbeeldconfiguratiebestand van de Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- PHP-FPM met TCP correct instellen

- HTTP/2 en Gzip inschakelen

- De verbindingen van workers optimaliseren

### Database

This document does not provide in-depth MySQL tuning instructions because each store and environment is different, but we can make some general recommendations.

The Adobe Commerce database (as well as any other database) is sensitive to the amount of memory available for storing data and indexes. Om effectief hefboomwerking MySQL gegevensindexatie, zou de hoeveelheid beschikbaar geheugen, minstens, dicht aan de helft van de grootte van de gegevens moeten zijn die in het gegevensbestand worden opgeslagen.

Optimaliseer `innodb_buffer_pool_instances` plaatsen om kwesties met veelvoudige draden te vermijden die tot de zelfde instantie proberen toegang te hebben. De waarde van de parameter `max_connections` zou met het totale aantal PHP draden moeten correleren die in de toepassingsserver worden gevormd. Gebruik de volgende formule om de beste waarde voor `innodb-thread-concurrency` te berekenen:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Sessie in cache plaatsen

Session caching is a good candidate to configure for a separate instance of Redis. Memory configuration for this cache type should consider the site’s cart abandonment strategy and how long a session should expect to remain in the cache.

Redis moet voldoende geheugen hebben om alle andere cache in het geheugen te bewaren voor optimale prestaties. Block cache will be the key factor in determining the amount of memory to configure. Het cachegeheugen van een blok wordt groter ten opzichte van het aantal pagina&#39;s op een site (aantal SKU-x-winkelweergaven).

### Page caching

We highly recommend using Varnish for full page cache on your Adobe Commerce store. The `PageCache` module is still present in the codebase, but it should be used for development purposes only.

Varnish installeren op een aparte server vóór de weblaag. It should accept all incoming requests and provide cached page copies. Om Varnish toe te staan om effectief met beveiligde pagina&#39;s te werken, kan een SSL beëindigingsvolmacht vóór Varnish worden geplaatst. Nginx can be used for this purpose.

Hoewel validatie van het volledige paginacachegeheugen van Varnish effectief is, raden we u aan voldoende geheugen toe te wijzen aan Varnish om uw populairste pagina&#39;s in het geheugen te houden.

### Berichtenrijen

The Message Queue Framework (MQF) is a system that allows a module to publish messages to queues. It also defines the consumers that receive the messages asynchronously. Adobe Commerce supports RabbitMQ as the messaging broker, which provides a scalable platform for sending and receiving messages.

### Performance testing and monitoring

Het testen van prestaties vóór elke productielevering wordt altijd geadviseerd om een schatting van het vermogen van uw e-commerceplatform te krijgen. Houd toezicht na het opstarten en heb een schaalbaarheid en back-upplan voor het afhandelen van piektijden.

>[!NOTE]
>
> Adobe Commerce on cloud infrastrucrure already applies all of the above infrastructure and architecture optimizations, except for the DNS lookup because it&#39;s out of scope.

### Search

Elasticsearch is vereist vanaf versie 2.4 van de Handel van de Adobe, maar het is ook een beste praktijk om het voor versies vóór 2.4 toe te laten.

## Operating models

Apart from the previoiusly mentioend common infrastructure optimization recommendations, there are also approaches to enhance the performance for specific business modes and scales. Dit document bevat geen gedetailleerde tuninginstructies voor alle scenario&#39;s, omdat elk scenario anders is, maar we kunnen wel een aantal opties op hoog niveau voor uw referentie bieden.

### Headless architecture

Er is een apart gedeelte gewijd aan de details van [headless](../../architecture/headless/adobe-commerce.md) en verschillende opties. Samengevat wordt de storefront-laag gescheiden van het platform zelf. It is still the same backend, but Adobe Commerce no longer processes requests directly and instead only supports custom storefronts through the GraphQL API.

### Adobe Commerce bijwerken

De Handel van de Adobe heeft altijd betere prestaties wanneer het runnen van de recentste versie. Zelfs als het niet mogelijk is om Adobe Commerce bijgewerkt te houden nadat elke nieuwe versie is uitgebracht, wordt het nog steeds aanbevolen om een upgrade uit te voeren wanneer Adobe Commerce belangrijke optimalisaties voor de prestaties introduceert.

In 2020 bijvoorbeeld publiceerde Adobe een optimalisatie naar de Redis-laag, waardoor veel inefficiëntie, verbindingsproblemen en onnodige gegevensoverdracht tussen Redis en Adobe Commerce werden gecorrigeerd. Overall performance between 2.3 and 2.4 is night and day and we saw significant improvements in cart, checkout, concurrent users, just because of the Redis optimization.

### Gegevensmodel optimaliseren

A lot of problems originate from data, including bad data models, data that is not structured properly, and data that is missing an index.

Het ziet er goed uit als je een paar verbindingen test, maar gezien in productie wanneer het echte verkeer raakt en dit is waar de traagheid binnenkomt. It’s very important that systems integrators know how to design a data model (especially for product attributes), avoid adding unnecessary attributes, and keep mandatory attributes that affect business logic (such as pricing, stock availability, and search).

For those attributes that do not affect business logic but still need to be present on the storefront, combine them into a few attributes (for example, JSON format).

Om platformprestaties te optimaliseren, als de bedrijfslogica niet op de opslag van gegevens of attributen wordt vereist die uit PIM of ERP worden genomen, is er geen behoefte om die eigenschap in de Handel van Adobe toe te voegen.

### Design for scalability

Dit is belangrijk voor bedrijven die campagnes voeren en vaak piektijden tegemoet zien. For architecture and application design to be easy to scale, this can increase resources during peak times and reduce them after it.
