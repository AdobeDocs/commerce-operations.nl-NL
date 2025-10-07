---
title: Aanbevelingen voor software
description: Meer informatie over softwarevereisten en aanbevelingen voor Adobe Commerce. Ontdek gesteunde versies en configuratie beste praktijken voor productie.
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '1396'
ht-degree: 0%

---

# Aanbevelingen voor software

De volgende software is vereist voor productieinstanties van [!DNL Commerce] :

* [PHP](../installation/system-requirements.md)
* Nginx en [ PHP-FPM ](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] of OpenSearch](../installation/prerequisites/search-engine/overview.md)

Voor multiserver plaatsingen, of voor verkopers die op het schrapen van hun zaken plannen, adviseren wij het volgende:

* [[!DNL Varnish] cache](../configuration/cache/config-varnish.md)
* [ Redis ](../configuration/cache/redis-session.md) voor zittingen (van 2.0.6+)
* Een afzonderlijke Redis instantie als uw [ standaardgeheime voorgeheugen ](../configuration/cache/redis-pg-cache.md) (gebruik deze instantie niet voor paginacache)

Zie [ systeemvereisten ](../installation/system-requirements.md) voor informatie over gesteunde versies van elk type van software.

## Besturingssysteem

Configuraties en optimalisaties van besturingssystemen zijn vergelijkbaar voor [!DNL Commerce] in vergelijking met andere webtoepassingen met een hoge belasting. Naarmate het aantal gelijktijdige verbindingen dat door de server wordt afgehandeld toeneemt, kan het aantal beschikbare sockets volledig worden toegewezen. De Linux-kernel ondersteunt een mechanisme voor het &quot;hergebruiken&quot; van TCP-verbindingen. U kunt dit mechanisme inschakelen door de volgende waarde in te stellen in `/etc/sysctl.conf` :

>[!INFO]
>
>Het toelaten van net.ipv4.tcp_tw_reuse heeft geen effect op inkomende verbindingen.

```text
net.ipv4.tcp_tw_reuse = 1
```

De kernel-parameter `net.core.somaxconn` bepaalt het maximum aantal open sockets dat op verbindingen wacht. Deze waarde kan veilig worden verhoogd tot 1024, maar moet gecorreleerd zijn met de capaciteit van de server om deze hoeveelheid te verwerken. U kunt deze kernel-parameter inschakelen door de volgende waarde in te stellen in `/etc/sysctl.conf` :

```text
net.core.somaxconn = 1024
```

## PHP

Magento ondersteunt PHP 7.3 en 7.4 volledig. Er zijn verschillende factoren waarmee rekening moet worden gehouden bij het configureren van PHP voor maximale snelheid en efficiëntie bij het verwerken van aanvragen.

### PHP-extensies

We raden u aan de lijst met actieve PHP-extensies te beperken tot de extensies die vereist zijn voor [!DNL Commerce] -functionaliteit.

Magento Open Source en Adobe Commerce:

* Text-bcmath
* text-type
* Tekstkrullen
* ext-dom
* Text-fileinfo
* ext-gd
* text-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* text-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* text-soap
* tekstsockets
* ext-natrium
* text-tokenizer
* ext-xmlwriter
* ext-xsl
* text-zip
* lib-libxml
* lib-openssl

Daarnaast vereist Adobe Commerce:

* Text-bcmath
* text-type
* Tekstkrullen
* ext-dom
* Text-fileinfo
* ext-gd
* text-hash
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* text-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* text-soap
* tekstsockets
* ext-natrium
* text-spl
* text-tokenizer
* ext-xmlwriter
* ext-xsl
* text-zip
* lib-libxml
* lib-openssl

Als u meer extensies toevoegt, duurt het laden van de bibliotheek langer.

>[!INFO]
>
>`php-mcrypt` is verwijderd uit PHP 7.2 en vervangen door de [`sodium` library ](https://www.php.net/manual/en/book.sodium.php) . Zorg ervoor dat [ natrium ](https://www.php.net/manual/en/sodium.installation.php) behoorlijk wordt toegelaten wanneer het bevorderen van PHP.

>[!INFO]
>
>De aanwezigheid van om het even welke het profileren en het zuiveren uitbreidingen kan de reactietijd van uw pagina&#39;s negatief beïnvloeden. Als voorbeeld, kan een actieve xDebug module zonder enige zuiveringszitting de tijd van de paginareactie met maximaal 30% verhogen.

### PHP-instellingen

Als u wilt garanderen dat alle [!DNL Commerce] -instanties correct worden uitgevoerd zonder gegevens of code op schijf te storten, stelt u de geheugenlimiet als volgt in:

```text
memory_limit=1G
```

Voor het zuiveren, verhoog deze waarde tot 2G.

#### Configuratie Realpath_cache

Als u de [!DNL Commerce] -prestaties wilt verbeteren, voegt u de volgende aanbevolen `realpath_cache` -instellingen toe aan of werkt u deze bij in het `php.ini` -bestand. Met deze configuratie kunnen PHP-processen paden naar bestanden in cache plaatsen in plaats van ze elke keer weer op te zoeken wanneer een pagina wordt geladen. Zie [ Prestaties die ](https://www.php.net/manual/en/ini.core.php) in de PHP documentatie stempelen.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Om maximale snelheid te krijgen uit [!DNL Commerce] op PHP 7, moet u de module OpCache activeren en behoorlijk vormen het. Deze instellingen worden aanbevolen voor de module:

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Wanneer u de geheugentoewijzing voor opcache precies afstemt, moet u rekening houden met de grootte van de Magento-codebasis en al uw extensies. Het prestatieteam van Magento gebruikt de waarden in het vorige voorbeeld voor het testen omdat het voldoende ruimte in opcache biedt voor het gemiddelde aantal geïnstalleerde extensies.

Als u een computer met weinig geheugen hebt en u niet veel extensies of aanpassingen hebt geïnstalleerd, gebruikt u de volgende instellingen voor een vergelijkbaar resultaat:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Wij adviseren toelatend de [ uitbreiding PHP APCu ](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) en [ vormend `composer` om het ](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) te steunen om voor maximumprestaties te optimaliseren. Met deze extensie worden bestandslocaties voor geopende bestanden in cache geplaatst, waardoor de prestaties van serveraanroepen van [!DNL Commerce] worden verhoogd, inclusief pagina&#39;s, Ajax-aanroepen en eindpunten.

Bewerk het `apcu.ini` -bestand en voeg het volgende toe:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Webserver

Magento biedt volledige ondersteuning voor de Nginx- en Apache-webservers. [!DNL Commerce] biedt voorbeelden van aanbevolen configuratiebestanden in de bestanden `<magento_home>/nginx.conf.sample` (Nginx) en `<magento_home>.htaccess.sample` (Apache).  Het Nginx-voorbeeld bevat instellingen voor betere prestaties en is zo ontworpen dat weinig herconfiguratie nodig is. Enkele van de belangrijkste die configuratiebeste praktijken in het steekproefdossier worden bepaald omvatten:

* Instellingen voor het in cache plaatsen van statische inhoud in een browser
* Instellingen voor geheugen en uitvoertijd voor PHP
* Instellingen voor compressie van inhoud

U zou het aantal draden voor de verwerking van het inputverzoek ook moeten vormen, zoals hieronder vermeld:

| Webserver | Kenmerknaam | Locatie | Verwante informatie |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [ het Tuning NGINX voor Prestaties ](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [ het Afstemmen van Prestaties Apache ](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [ Gemeenschappelijke Richtlijnen van Apache MPM ](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Dit document bevat geen uitgebreide [!DNL MySQL] afstemmingsinstructies, omdat elke winkel en omgeving anders zijn, maar we kunnen wel enkele algemene aanbevelingen doen.

Er zijn veel verbeteringen aangebracht in [!DNL MySQL] 5.7.9. We zijn ervan overtuigd dat [!DNL MySQL] met goede standaardinstellingen is gedistribueerd. De meest kritieke instellingen zijn:

| Parameter | Standaard | Beschrijving |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | De standaardwaarde is ingesteld op 8 om problemen te voorkomen met meerdere threads die toegang proberen te krijgen tot dezelfde instantie. |
| `innodb_buffer_pool_size` | 128 MB | Gecombineerd met de veelvoudige hierboven beschreven groepsinstanties, betekent dit een standaardgeheugentoewijzing van 1024MB. De totale grootte wordt over alle bufferpools verdeeld. Voor de beste efficiëntie geeft u een combinatie van `innodb_buffer_pool_instances` en `innodb_buffer_pool_size` op, zodat elke instantie van de bufferpool ten minste 1 GB bedraagt. |
| `max_connections` | 150 | De waarde van de parameter `max_connections` moet correleren met het totale aantal PHP threads dat is geconfigureerd in de toepassingsserver. Een algemene aanbeveling zou 300 zijn voor een klein milieu en 1000 voor een middelgroot milieu. |
| `innodb_thread_concurrency` | 0 | De beste waarde voor deze configuratie moet met de volgende formule worden berekend: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento raadt u ten zeerste aan [!DNL Varnish] te gebruiken als de cache-server voor alle pagina&#39;s voor uw winkel. De module PageCache is nog steeds aanwezig in de codebase, maar moet alleen voor ontwikkelingsdoeleinden worden gebruikt. Deze mag niet samen met of in plaats van [!DNL Varnish] worden gebruikt.

Installeer [!DNL Varnish] op een aparte server vóór de weblaag. Het zou alle inkomende verzoeken moeten goedkeuren en in het voorgeheugen ondergebrachte paginaaKopieën verstrekken. Als u [!DNL Varnish] wilt toestaan effectief te werken met beveiligde pagina&#39;s, kan een SSL-proxy vóór [!DNL Varnish] worden geplaatst. Nginx kan voor dit doel worden gebruikt.

[!DNL Commerce] verspreidt een voorbeeldconfiguratiebestand voor [!DNL Varnish] (versies 4 en 5) dat alle aanbevolen instellingen voor de prestaties bevat. De meest kritieke prestaties zijn onder andere:

* **Achterste gezondheidscontrole** pollt de [!DNL Commerce] server om te bepalen of het op een geschikte manier antwoordt.
* **wijze van de Grace** staat u toe om [!DNL Varnish] op te dragen om een voorwerp in geheim voorgeheugen voorbij zijn Tijd aan Levende (TTL) periode te houden en deze stapelinhoud te dienen als [!DNL Commerce] niet gezond is of als de verse inhoud nog niet is gehaald.
* **de wijze van Saint** zwarte lijsten ongezonde [!DNL Commerce] servers voor een configureerbare hoeveelheid tijd. Hierdoor kunnen ongezonde backends geen verkeer dienen wanneer [!DNL Varnish] als taakverdelingsmechanisme wordt gebruikt.

Zie [ Geavanceerde  [!DNL Varnish]  configuratie ](../configuration/cache/config-varnish-advanced.md) voor meer informatie over het uitvoeren van deze eigenschappen.

### Elementprestaties optimaliseren

Over het algemeen raden we u aan uw elementen (afbeeldingen, JS, CSS, enzovoort) op te slaan op een CDN voor optimale prestaties.

Als voor uw site geen groot aantal landinstellingen hoeft te worden geïmplementeerd en uw servers zich in hetzelfde gebied bevinden als de meeste klanten, kan het zijn dat u aanzienlijke prestatiewinsten tegen een lagere kostprijs kunt behalen door uw middelen op te slaan in [!DNL Varnish] in plaats van een CDN te gebruiken.

Als u uw elementen in [!DNL Varnish] wilt opslaan, voegt u de volgende VCL-items toe aan het `default.vcl` -bestand dat door [!DNL Commerce] voor [!DNL Varnish] 5 wordt gegenereerd.

Voeg aan het einde van de instructie `if` voor PURGE-aanvragen in de subroutine `vcl_recv` het volgende toe:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

Zoek in de subroutine `vcl_backend_response` naar de instructie `if` die de cookie voor `GET` - of `HEAD` -aanvragen ongedaan maakt.
Het bijgewerkte `if` -blok moet er als volgt uitzien:

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

Start de [!DNL Varnish] -server opnieuw om in de cache opgeslagen middelen te verwijderen wanneer u uw site upgradet of elementen implementeert/bijwerkt.

## In cache plaatsen en sessieservers

Magento biedt een aantal opties voor het opslaan van uw cache- en sessiegegevens, zoals Redis, Memcache, bestandssysteem en database. Enkele van deze opties worden hieronder besproken.

### Eén webknooppunt instellen

Als u al uw verkeer met slechts één Webknoop van plan bent te dienen, het niet steek houdt om uw geheime voorgeheugen op een verre server van Redis te zetten. Gebruik in plaats daarvan het bestandssysteem of een lokale Redis-server. Als u het bestandssysteem wilt gebruiken, plaatst u de cachemappen op een volume dat is gekoppeld aan een RAM-bestandssysteem. Als u een lokale Redis-server wilt gebruiken, raden wij u sterk aan Redis te configureren, zodat er sockets voor directe verbindingen worden gebruikt in plaats van gegevens via HTTP uit te wisselen.

### Meerdere webknooppunten instellen

Redis is de beste optie voor het instellen van meerdere webknooppunten. Omdat [!DNL Commerce] actief veel gegevens in cache plaatst voor betere prestaties, moet u rekening houden met uw netwerkkanaal tussen de webknooppunten en de Redis-server. U wilt niet dat het kanaal een knelpunt voor aanvraagverwerking wordt.

>[!INFO]
>
>Als u honderden en duizenden gelijktijdige verzoeken moet indienen, hebt u mogelijk een kanaal van maximaal 1 Gbit (of zelfs nog breder) aan uw Redis-server nodig.
