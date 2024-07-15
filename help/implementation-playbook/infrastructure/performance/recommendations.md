---
title: Aanbevelingen voor optimalisatie van prestaties
description: Optimaliseer de prestaties van uw Adobe Commerce-implementatie met deze aanbevelingen.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
feature: Cloud
topic: Performance
source-git-commit: 8b09d734d8ac4490cd88af5673acd0a41b6cdf66
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---


# Evaluatie voor optimalisatie van prestaties

Zelfs als prestatiesoptimalisering uit vele aspecten kan komen, zijn er sommige algemene aanbevelingen die voor de meeste scenario&#39;s moeten worden overwogen. Algemene aanbevelingen omvatten configuratieoptimalisering voor infrastructuurelementen, Adobe Commerce backend configuratie, en architectuur scalability planning.

>[!TIP]
>
>Zie de [_Gids van Beste praktijken van Prestaties_](../../../performance/overview.md) voor meer informatie over prestatiesoptimalisering.

## Infrastructuur

In de volgende secties worden aanbevelingen voor infrastructuuroptimalisatie beschreven.

### DNS-zoekopdrachten

DNS raadpleging is het proces om te vinden welk IP adres dat de domeinnaam tot behoort. De browser moet wachten tot de DNS raadpleging volledig is alvorens het om het even wat voor elk verzoek kan downloaden. Het verminderen van DNS raadplegingen is belangrijk om algemene pagina ladingstijden te verbeteren.

### CDN (Content Delivery Network)

Gebruik een CDN om de downloadprestaties van elementen te optimaliseren. Adobe Commerce gebruikt Fastly. Als u een implementatie op locatie van Adobe Commerce hebt, zou u ook moeten overwegen toevoegend een laag CDN.

### Webvertraging

De locatie van het datacenter is van invloed op de webvertraging voor frontend-gebruikers.

### Netwerkbandbreedte

Voldoende netwerkbandbreedte is een van de belangrijkste vereisten voor gegevensuitwisseling tussen webknooppunten, databases, caching-/sessieservers en andere services.

Omdat Adobe Commerce effectief caching gebruikt voor hoge prestaties, kan uw systeem actief gegevens uitwisselen met caching servers zoals Redis. Als Redis op een externe server is geïnstalleerd, moet u een voldoende netwerkkanaal tussen webknooppunten en de caching-server opgeven om knelpunten bij lees- en schrijfbewerkingen te voorkomen.

### Besturingssysteem (OS)

Configuraties en optimalisaties van besturingssystemen zijn vergelijkbaar voor Adobe Commerce in vergelijking met andere webtoepassingen met een hoge belasting. Naarmate het aantal gelijktijdige verbindingen dat door de server wordt afgehandeld toeneemt, kan het aantal beschikbare sockets volledig worden toegewezen.

### CPU van webknooppunten

Eén CPU-core kan ongeveer 2-4 Adobe Commerce-verzoeken zonder cache leveren. Om te bepalen hoeveel Webknopen/kernen nodig waren om alle inkomende verzoeken te verwerken zonder hen in rij te zetten, gebruik de vergelijking:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM-instellingen

Het optimaliseren van deze instellingen is afhankelijk van de resultaten van de prestatietest voor verschillende projecten.

- **ByteCode** - om maximumsnelheid uit Adobe Commerce op PHP 7 te krijgen, moet u de `opcache` module activeren en het behoorlijk vormen.

- **APCU** - Adobe adviseert toelatend de uitbreiding PHP APCu en het vormen Composer om voor maximumprestaties te optimaliseren. Deze extensie plaatst bestandslocaties voor geopende bestanden in cache, waardoor de prestaties van Adobe Commerce-serveraanroepen, zoals pagina&#39;s, Ajax-aanroepen en eindpunten, worden verhoogd.

- **Realpath_cacheconfiguration** - het optimaliseren `realpath_cache` staat PHP processen toe om wegen aan dossiers in het voorgeheugen onder te brengen in plaats van hen te kijken telkens als een pagina laadt.

### Webserver

Slechts is een lichte herconfiguratie nodig om nginx als Webserver te gebruiken. De nginx Webserver verstrekt betere prestaties en is gemakkelijk te vormen gebruikend het dossier van de steekproefconfiguratie van Adobe Commerce ([`nginx.conf.sample` ](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- PHP-FPM correct instellen met TCP

- HTTP/2 en Gzip inschakelen

- De verbindingen van workers optimaliseren

### Database

Dit document bevat geen uitgebreide MySQL-afstemmingsinstructies omdat elke winkel en omgeving anders zijn, maar Adobe kan algemene aanbevelingen doen.

De Adobe Commerce-database (en elke andere database) is gevoelig voor de hoeveelheid geheugen die beschikbaar is voor het opslaan van gegevens en indexen. Om MySQL gegevensindexatie effectief te gebruiken, zou de beschikbare hoeveelheid geheugen, minstens, dicht aan de helft van de grootte van de gegevens moeten zijn die in het gegevensbestand worden opgeslagen.

Optimaliseer `innodb_buffer_pool_instances` plaatsen om kwesties met veelvoudige draden te vermijden die tot de zelfde instantie proberen toegang te hebben. De waarde van de parameter `max_connections` moet correleren met het totale aantal PHP threads dat is geconfigureerd in de toepassingsserver. Gebruik de volgende formule om de beste waarde voor `innodb-thread-concurrency` te berekenen:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Sessie in cache plaatsen

Het in cache plaatsen van sessies is een goede kandidaat om te configureren voor een afzonderlijk geval van Redis. De configuratie van het geheugen voor dit geheim voorgeheugentype zou de strategie van de het kartontroeping van de plaats moeten overwegen en hoe lang een zitting zou moeten verwachten om in het geheime voorgeheugen te blijven.

Redis moet voldoende geheugen hebben toegewezen om alle andere cache in het geheugen te bewaren voor optimale prestaties. Het geheime voorgeheugen van het blok is de belangrijkste factor in het bepalen van de hoeveelheid geheugen te vormen. Het cachegeheugen van een blok wordt groter ten opzichte van het aantal pagina&#39;s op een site (aantal SKU x aantal winkelweergaven).

### Pagina in cache plaatsen

Adobe raadt u ten zeerste aan Varnish te gebruiken voor het cachegeheugen van volledige pagina&#39;s in uw Adobe Commerce-winkel. De module `PageCache` is nog steeds aanwezig in de codebase, maar moet alleen worden gebruikt voor ontwikkelingsdoeleinden.

Varnish installeren op een aparte server vóór de weblaag. Het zou alle inkomende verzoeken moeten goedkeuren en in het voorgeheugen ondergebrachte paginaaKopieën verstrekken. Om Varnish toe te staan om effectief met beveiligde pagina&#39;s te werken, kan een SSL beëindigingsvolmacht vóór Varnish worden geplaatst. Nginx kan voor dit doel worden gebruikt.

Hoewel validatie van het volledige paginacachegeheugen van Varnish effectief is, raadt de Adobe aan voldoende geheugen toe te wijzen aan Varnish om de populairste pagina&#39;s in het geheugen te houden.

### Berichtenrijen

Het Kader van de Rij van het Bericht (MQF) is een systeem dat een module toestaat om berichten aan rijen te publiceren. Het bepaalt ook de consumenten die de berichten asynchroon ontvangen. Adobe Commerce ondersteunt [!DNL RabbitMQ] als de berichtenmakelaar, die een schaalbaar platform biedt voor het verzenden en ontvangen van berichten.

### Prestatietests en -bewaking

Het testen van prestaties vóór elke productielevering wordt altijd geadviseerd om een schatting van de capaciteit van uw e-commerceplatform te krijgen. Houd toezicht na het opstarten en heb een schaalbaarheid en back-upplan voor het afhandelen van piektijden.

>[!NOTE]
>
> Adobe Commerce op cloudinfrastructuur past de bovenstaande infrastructuur en architectuuroptimalisaties al toe, behalve voor de DNS-zoekopdracht omdat deze buiten het bereik valt.

### Zoeken {#search-heading}

Elasticsearch (of OpenSearch) is vereist vanaf Adobe Commerce versie 2.4, maar het is ook raadzaam dit in te schakelen voor versies vóór 2.4.

## Operationele modellen

Naast de eerder genoemde gemeenschappelijke aanbevelingen voor optimalisatie van de infrastructuur, zijn er ook benaderingen om de prestaties voor specifieke bedrijfswijzen en schalen te verbeteren. Dit document bevat geen gedetailleerde tuninginstructies voor alle scenario&#39;s omdat elk scenario anders is, maar Adobe kan een aantal opties op hoog niveau voor uw referentie bieden.

### Hoofdloze architectuur

Er is een afzonderlijke sectie gewijd aan [ zonder kop ](../../architecture/enterprise-blueprint.md#headless-storefront). Samengevat wordt de storefront-laag gescheiden van het platform zelf. Het is nog steeds dezelfde achtergrond, maar Adobe Commerce verwerkt aanvragen niet meer rechtstreeks en ondersteunt in plaats daarvan alleen aangepaste winkels via de GraphQL API.

### Adobe Commerce bijwerken

Adobe Commerce presteert altijd beter wanneer de nieuwste versie wordt uitgevoerd. Zelfs als het niet mogelijk is om Adobe Commerce bijgewerkt te houden nadat elke nieuwe versie wordt vrijgegeven, wordt het nog geadviseerd om [ te bevorderen ](../../../upgrade/overview.md) wanneer Adobe Commerce significante prestatiesoptimalisaties introduceert.

In 2020 heeft Adobe bijvoorbeeld een optimalisatie voor de Redis-laag uitgebracht, waardoor veel inefficiënties, verbindingsproblemen en onnodige gegevensoverdracht tussen Redis en Adobe Commerce zijn verholpen. De algehele prestaties tussen 2,3 en 2,4 zijn &#39;s nachts en &#39;s nachts en leverden aanzienlijke verbeteringen op in het winkelwagentje, de kassa en de gebruikers tegelijk, alleen vanwege de Redis-optimalisatie.

### Gegevensmodel optimaliseren

Veel problemen komen voort uit gegevens, waaronder slechte gegevensmodellen, gegevens die niet goed zijn gestructureerd en gegevens die een index missen.

Het lijkt fijn als u een paar verbindingen test, maar nadat u aan productie opstelt zou u ernstige prestatiesdegradatie kunnen zien. Het is belangrijk dat systeemintegratoren weten hoe ze een gegevensmodel kunnen ontwerpen (met name voor productkenmerken), voorkomen dat ze onnodige kenmerken toevoegen en verplichte kenmerken behouden die van invloed zijn op bedrijfslogica (zoals prijsstelling, beschikbaarheid van voorraden en zoekopdracht).

Voor die attributen die geen bedrijfslogica beïnvloeden maar nog op de storefront moeten aanwezig zijn, combineer hen in een paar attributen (bijvoorbeeld, formaat JSON).

Om platformprestaties te optimaliseren, als bedrijfslogica niet op het storefront van gegevens of attributen wordt vereist die van PIM of ERP worden genomen, is er geen behoefte om die eigenschap in Adobe Commerce toe te voegen.

### Ontwerpen voor schaalbaarheid

Schaalbaarheid is belangrijk voor bedrijven die campagnes voeren en vaak geconfronteerd worden met piekverkeerstijden. Een schaalbare architectuur en een toepassingsontwerp kunnen bronnen tijdens piektijden verhogen en deze na piektijden verminderen.
