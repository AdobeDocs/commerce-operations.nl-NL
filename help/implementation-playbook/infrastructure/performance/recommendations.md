---
title: Prestaties optimaliseren, Recommendations
description: Optimaliseer de prestaties van uw Adobe Commerce-implementatie met deze aanbevelingen.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
source-git-commit: 065c56f20ba5b1eef8c331c5c2f5649902f1442b
workflow-type: tm+mt
source-wordcount: '1288'
ht-degree: 0%

---

# Evaluatie voor optimalisatie van prestaties

Zelfs als prestatiesoptimalisering uit vele aspecten kan komen, zijn er sommige algemene aanbevelingen die voor de meeste scenario&#39;s moeten worden overwogen. Dit omvat configuratieoptimalisering voor infrastructuurelementen, Adobe Commerce backend configuratie, en architectuur scalability planning.

## Infrastructuur

In de volgende secties worden aanbevelingen voor infrastructuuroptimalisatie beschreven.

### DNS-zoekopdrachten

DNS raadpleging is het proces om te vinden welk IP adres dat de domeinnaam tot behoort. De browser moet wachten tot de DNS raadpleging volledig is alvorens het om het even wat voor elk verzoek kan downloaden. Het verminderen van DNS raadplegingen is belangrijk om algemene pagina ladingstijden te verbeteren.

### CDN (Content Delivery Network)

Gebruik een CDN om de downloadprestaties van elementen te optimaliseren. Adobe Commerce gebruikt Fastly. Als u een implementatie op locatie van Adobe Commerce hebt, kunt u ook overwegen een CDN-laag toe te voegen.

### Webvertraging

De locatie van het datacenter is van invloed op de webvertraging voor frontend-gebruikers.

### Netwerkbandbreedte

Voldoende netwerkbandbreedte is een van de belangrijkste vereisten voor gegevensuitwisseling tussen webknooppunten, databases, caching-/sessieservers en andere services.

Omdat Adobe Commerce effectief gebruik maakt van caching voor hoge prestaties, kan uw systeem actief gegevens uitwisselen met cacheservers zoals Redis. Als Redis zich op een externe server bevindt, moet u een voldoende netwerkkanaal tussen webknooppunten en de caching-server opgeven om knelpunten bij lees- en schrijfbewerkingen te voorkomen.

### Besturingssysteem (OS)

Configuraties en optimalisaties van besturingssystemen zijn vergelijkbaar voor Adobe Commerce in vergelijking met andere webtoepassingen met een hoge belasting. Naarmate het aantal gelijktijdige verbindingen dat door de server wordt afgehandeld toeneemt, kan het aantal beschikbare sockets volledig worden toegewezen.

### CPU van webknooppunten

Eén CPU-core kan ongeveer 2-4 Adobe Commerce-verzoeken zonder cache leveren. Om te bepalen hoeveel Webknopen/kernen nodig waren om alle inkomende verzoeken te verwerken zonder hen in rij te zetten, gebruik de vergelijking:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM-instellingen

Het optimaliseren van deze instellingen is afhankelijk van de resultaten van de prestatietest voor verschillende projecten.

- **ByteCode**—Als u de maximale snelheid van Adobe Commerce wilt bereiken op PHP 7, moet u de `opcache` en het behoorlijk vormen.

- **APCU**—We raden u aan de PHP APCu-extensie in te schakelen en Composer te configureren voor optimale prestaties. Deze extensie plaatst bestandslocaties voor geopende bestanden in cache, waardoor de prestaties van Adobe Commerce-serveraanroepen, zoals pagina&#39;s, Ajax-aanroepen en eindpunten, worden verhoogd.

- **Realpath_cacheconfiguration**—Optimaliseren `realpath_cache` PHP kan paden naar bestanden in cache plaatsen in plaats van ze elke keer dat een pagina wordt geladen, op te zoeken.

### Webserver

Slechts is een lichte herconfiguratie nodig om nginx als Webserver te gebruiken. De nginx-webserver biedt betere prestaties en is eenvoudig te configureren met het voorbeeldconfiguratiebestand van Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- PHP-FPM met TCP correct instellen

- HTTP/2 en Gzip inschakelen

- De verbindingen van workers optimaliseren

### Database

Dit document bevat geen uitgebreide MySQL-afstemmingsinstructies omdat elke winkel en omgeving anders zijn, maar we kunnen wel enkele algemene aanbevelingen doen.

De Adobe Commerce-database (en elke andere database) is gevoelig voor de hoeveelheid geheugen die beschikbaar is voor het opslaan van gegevens en indexen. Om effectief hefboomwerking MySQL gegevensindexatie, zou de hoeveelheid beschikbaar geheugen, minstens, dicht aan de helft van de grootte van de gegevens moeten zijn die in het gegevensbestand worden opgeslagen.

Optimaliseren `innodb_buffer_pool_instances` het plaatsen om kwesties met veelvoudige draden te vermijden die tot de zelfde instantie proberen toegang te hebben. De waarde van de `max_connections` Deze parameter moet correleren met het totale aantal PHP threads dat is geconfigureerd in de toepassingsserver. Gebruik de volgende formule om de beste waarde te berekenen voor `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Sessie in cache plaatsen

Het in cache plaatsen van sessies is een goede kandidaat om te configureren voor een afzonderlijk geval van Redis. Bij de geheugenconfiguratie voor dit cachetype moet rekening worden gehouden met de strategie voor het verlaten van het winkelwagentje van de site en met de tijd die een sessie naar verwachting in de cache zal blijven.

Redis moet voldoende geheugen hebben om alle andere cache in het geheugen te bewaren voor optimale prestaties. Het geheime voorgeheugen van het blok zal de belangrijkste factor in het bepalen van de hoeveelheid geheugen zijn te vormen. Het cachegeheugen van een blok wordt groter ten opzichte van het aantal pagina&#39;s op een site (aantal SKU-x-winkelweergaven).

### Pagina in cache plaatsen

We raden u ten zeerste aan Varnish te gebruiken voor de volledige paginacache in uw Adobe Commerce-winkel. De `PageCache` de module is nog steeds aanwezig in de codebase, maar mag alleen voor ontwikkelingsdoeleinden worden gebruikt.

Varnish installeren op een aparte server vóór de weblaag. Het zou alle inkomende verzoeken moeten goedkeuren en in het voorgeheugen ondergebrachte paginaaKopieën verstrekken. Om Varnish toe te staan om effectief met beveiligde pagina&#39;s te werken, kan een SSL beëindigingsvolmacht vóór Varnish worden geplaatst. Nginx kan voor dit doel worden gebruikt.

Hoewel validatie van het volledige paginacachegeheugen van Varnish effectief is, raden we u aan voldoende geheugen toe te wijzen aan Varnish om uw populairste pagina&#39;s in het geheugen te houden.

### Berichtenrijen

Het Kader van de Rij van het Bericht (MQF) is een systeem dat een module toestaat om berichten aan rijen te publiceren. Het bepaalt ook de consumenten die de berichten asynchroon ontvangen. Adobe Commerce-ondersteuning [!DNL RabbitMQ] als overseinenmakelaar, die een scalable platform voor het verzenden van en het ontvangen van berichten verstrekt.

### Prestatietests en -bewaking

Het testen van prestaties vóór elke productielevering wordt altijd geadviseerd om een schatting van het vermogen van uw e-commerceplatform te krijgen. Houd toezicht na het opstarten en heb een schaalbaarheid en back-upplan voor het afhandelen van piektijden.

>[!NOTE]
>
> Adobe Commerce op cloudinfrastructuur past al alle bovenstaande infrastructuren en architectuuroptimalisaties toe, behalve voor de DNS-zoekopdracht omdat deze buiten het bereik valt.

### Zoeken {#search-heading}

Elasticsearch is vereist vanaf Adobe Commerce versie 2.4, maar het is ook aan te raden dit in te schakelen voor versies ouder dan 2.4.

## Operationele modellen

Naast de eerder genoemde gemeenschappelijke aanbevelingen voor optimalisatie van de infrastructuur, zijn er ook benaderingen om de prestaties voor specifieke bedrijfswijzen en schalen te verbeteren. Dit document bevat geen gedetailleerde tuninginstructies voor alle scenario&#39;s, omdat elk scenario anders is, maar we kunnen wel een aantal opties op hoog niveau voor uw referentie bieden.

### Hoofdloze architectuur

Er is een aparte sectie gewijd aan het gedetailleerd weergeven van [koploos](../../architecture/headless/adobe-commerce.md) is en verschillende opties. Samengevat wordt de storefront-laag gescheiden van het platform zelf. Het is nog steeds dezelfde achtergrond, maar Adobe Commerce verwerkt aanvragen niet meer rechtstreeks en ondersteunt in plaats daarvan alleen aangepaste winkels via de GraphQL API.

### Adobe Commerce bijwerken

Adobe Commerce presteert altijd beter wanneer de nieuwste versie wordt uitgevoerd. Zelfs als het niet mogelijk is om Adobe Commerce bijgewerkt te houden nadat elke nieuwe versie is uitgebracht, wordt het nog steeds aanbevolen [upgrade](../../../upgrade/overview.md) als Adobe Commerce belangrijke prestatieoptimalisaties introduceert.

In 2020 heeft Adobe bijvoorbeeld een optimalisatie uitgevoerd naar de Redis-laag, waardoor een groot aantal inefficiënties, verbindingsproblemen en onnodige gegevensoverdracht tussen Redis en Adobe Commerce zijn verholpen. De algehele prestaties tussen 2,3 en 2,4 zijn &#39;s nachts en &#39;s nachts en we zagen aanzienlijke verbeteringen in het winkelwagentje, de kassa en de gebruikers die tegelijk met elkaar werken, alleen vanwege de Redis-optimalisatie.

### Gegevensmodel optimaliseren

Veel problemen komen voort uit gegevens, waaronder slechte gegevensmodellen, gegevens die niet goed zijn gestructureerd en gegevens die een index missen.

Het ziet er goed uit als je een paar verbindingen test, maar gezien in productie wanneer het echte verkeer raakt en dit is waar de traagheid binnenkomt. Het is zeer belangrijk dat systeemintegrators weten hoe ze een gegevensmodel kunnen ontwerpen (met name voor productkenmerken), voorkomen dat ze onnodige kenmerken toevoegen en verplichte kenmerken behouden die van invloed zijn op de bedrijfslogica (zoals prijzen, beschikbaarheid van voorraden en zoeken).

Voor die kenmerken die geen invloed hebben op de bedrijfslogica, maar die nog wel op de storefront aanwezig moeten zijn, combineert u ze in een paar kenmerken (bijvoorbeeld JSON-indeling).

Om platformprestaties te optimaliseren, als bedrijfslogica niet op het storefront van gegevens of attributen wordt vereist die van PIM of ERP worden genomen, is er geen behoefte om die eigenschap in Adobe Commerce toe te voegen.

### Ontwerpen voor schaalbaarheid

Dit is belangrijk voor bedrijven die campagnes voeren en vaak piektijden tegemoet zien. Architectuur en toepassingsontwerp kunnen eenvoudig geschaald worden uitgebreid, waardoor de bronnen tijdens piektijden toenemen en daarna afnemen.
