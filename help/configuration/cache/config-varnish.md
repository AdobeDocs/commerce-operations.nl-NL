---
title: Varnish configureren en gebruiken
description: Begrijp hoe Varnish dossiers opslaat en het verkeer van HTTP verbetert.
feature: Configuration, Cache
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '1049'
ht-degree: 0%

---

# Varnish configureren

[ Varnish Geheime voorgeheugen ] is een open-bron de toepassingsaccelerator van het Web (die ook als a _wordt bedoeld de accelerator van HTTP_ of _caching de omgekeerde volmacht van HTTP_). Varnish slaat (of geheime voorgeheugens) dossiers of fragmenten van dossiers in geheugen op, die Varnish toelaat om de reactietijd en het verbruik van de netwerkbandbreedte op toekomstige, gelijkwaardige verzoeken te verminderen. In tegenstelling tot webservers als Apache en nginx, werd Varnish uitsluitend ontworpen voor gebruik met het HTTP-protocol.

[ de vereisten van het Systeem ](../../installation/system-requirements.md) maakt een lijst van de gesteunde versies van Varnish.

>[!WARNING]
>
>Wij _adviseren sterk_ u Varnish in productie gebruikt. Ingebouwd volledig-pagina caching-aan of het dossiersysteem of [ gegevensbestand ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) - is veel langzamer dan Varnish, en Varnish wordt ontworpen om het verkeer van HTTP te versnellen.

Zie voor meer informatie over Varnish:

- [ het Grote Vierige Beeld ]
- [ Varnish startopties ]
- [ Varnish en de Prestaties van de Website ]

## Varnish topologiediagram

Het volgende cijfer toont een basismening van Varnish in uw topologie van Commerce.

![ Basis Varnish diagram ](../../assets/configuration/varnish-basic.png)

In het voorafgaande cijfer, resulteren de verzoeken van HTTP van gebruikers over Internet in talrijke verzoeken om CSS, HTML, JavaScript, en beelden (die collectief als _worden bedoeld activa_). Varnish bevindt zich vóór de webserver en verzendt deze aanvragen bij de webserver.

Wanneer de webserver elementen retourneert, worden cacheable elementen in het Varnish opgeslagen. Elke volgende aanvraag voor deze elementen wordt door Varnish ingewilligd (de aanvragen bereiken dus niet de webserver). Varnish retourneert bijzonder snel inhoud in de cache. De resultaten zijn snellere reactietijden om de inhoud aan gebruikers en een verminderd aantal verzoeken terug te keren die door Commerce moeten worden vervuld.

Assets in cache geplaatst door Varnish verloopt met een configureerbaar interval of wordt vervangen door nieuwere versies van dezelfde elementen. U kunt de cache ook handmatig wissen met de opdracht Admin of [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) .

## Procesoverzicht

Dit onderwerp bespreekt hoe te om Varnish met een minimale reeks parameters aanvankelijk te installeren en te testen dat het werkt. Vervolgens exporteert u een vernis-configuratie vanuit de Commerce-beheerder en test u deze opnieuw.

Het proces kan als volgt worden samengevat:

1. Installeer Varnish en test het door tot om het even welke pagina van Commerce toegang te hebben om te zien of krijgt u de antwoordkopballen van HTTP die erop wijzen Varnish werkt.
1. Installeer de Commerce-software en gebruik Admin om een Varnish-configuratiebestand te maken.
1. Vervang het bestaande Varnish-configuratiebestand door het bestand dat door de beheerder is gegenereerd.
1. Test alles opnieuw.

   Als er niets in uw `<magento_root>/var/page_cache` folder is, hebt u met succes Varnish met Commerce gevormd!

>[!NOTE]
>
>- Behalve waar genoteerd, moet u alle bevelen ingaan die in dit onderwerp als gebruiker met `root` voorrechten worden besproken.
>
>- Dit onderwerp is geschreven voor Varnish op CentOS en Apache 2.4. Als u Varnish in een verschillende omgeving instelt, kunnen sommige opdrachten anders zijn. Raadpleeg de documentatie bij Varnish voor meer informatie.

## Bekende problemen

We kennen de volgende kwesties met Varnish:

- [ Varnish steunt geen SSL ]

  Als alternatief, gebruiksSSL beëindiging of een SSL beëindigingsvolmacht.

- Als u de inhoud van de map `<magento_root>/var/cache` handmatig verwijdert, moet u Varnish opnieuw starten.

- Mogelijke fout bij het installeren van Commerce:

  ```terminal
  Error 503 Service Unavailable
  Service Unavailable
  XID: 303394517
  Varnish cache server
  ```

  Als deze fout optreedt, bewerkt u `default.vcl` en voegt u als volgt een time-out toe aan de `backend` stanza:

  ```conf
  backend default {
      .host = "127.0.0.1";
      .port = "8080";
      .first_byte_timeout = 600s;
  }
  ```

## Overzicht van het in cache plaatsen van Varnish

Varnish caching werkt met Commerce met behulp van:

- [`nginx.conf.sample` ](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) van Magento 2 de bewaarplaats van GitHub
- `.htaccess` gedistribueerd configuratiebestand voor Apache dat bij Commerce wordt geleverd
- `default.vcl` configuratie voor Varnish produceerde gebruikend [ Admin ](../cache/configure-varnish-commerce.md)

>[!INFO]
>
>Dit onderwerp behandelt slechts de standaardopties in de voorafgaande lijst. Er zijn vele andere manieren om caching in complexe scenario&#39;s (bijvoorbeeld, gebruikend een Netwerk van de Levering van de Inhoud) te vormen; die methodes zijn voorbij het werkingsgebied van deze gids.

Op het eerste browser verzoek, worden de cacheable activa geleverd aan cliëntbrowser van Varnish en caching op browser.

Daarnaast gebruikt Varnish een eenheidtag (ETag) voor statische activa. Met ETag kunt u bepalen wanneer statische bestanden op de server veranderen. Hierdoor worden statische elementen naar de client verzonden wanneer deze op de server worden gewijzigd. Dit kan op een nieuw verzoek van een browser of wanneer de client het cachegeheugen van de browser vernieuwt, meestal door op F5 of Control+F5 te drukken.

De volgende secties bevatten meer details.

## Caching door browser request

In deze sectie wordt een browsercontrole gebruikt om te tonen hoe elementen in de eerste aanvraag aan de browser worden geleverd en vervolgens uit de lokale browsercache worden geladen.

### Eerste browserverzoek

`nginx.conf.sample` en `.htaccess` bieden opties voor het in cache plaatsen van clients. Wanneer het eerste verzoek van browser voor een cacheable voorwerp wordt gemaakt, levert Varnish het aan de cliënt.

In de volgende afbeelding ziet u een voorbeeld met een browsercontrole:

![ de eerste keer een verzoek voor een cacheable voorwerp wordt gemaakt, levert Varnish het aan browser ](../../assets/configuration/varnish-apache-first-visit.png)

Het voorgaande voorbeeld toont een verzoek om de hoofdpagina van de storefront (`m2_ce_my`). CSS- en JavaScript-elementen worden in cache geplaatst in de clientbrowser.

>[!NOTE]
>
>De meeste statische elementen hebben een HTTP 200 (OK)-statuscode die aangeeft dat het element van de server is opgehaald.

### Tweede browserverzoek

Als dezelfde browser dezelfde pagina opnieuw opvraagt, worden deze elementen geleverd vanuit de lokale browsercache, zoals in de volgende afbeelding wordt getoond.

![ de volgende tijd het zelfde voorwerp wordt gevraagd, laden de activa van het lokale browser geheime voorgeheugen ](../../assets/configuration/varnish-apache-second-visit.png)

Let op het verschil in responstijd tussen het eerste en het tweede verzoek. Ook hier hebben statische elementen een antwoordcode van 200 (OK), omdat ze voor het eerst worden geleverd via de lokale cache.

## Hoe Commerce Etag gebruikt

In het volgende voorbeeld worden responsheaders voor een bepaald statisch element weergegeven.

![ ETag maakt het gemakkelijker om te bepalen of een statisch element of niet is veranderd ](../../assets/configuration/varnish-etag.png)

`calendar.css` heeft een ETag- antwoordkopbal wat betekent het CSS dossier op cliëntbrowser kan worden vergeleken met die op de server.

Daarnaast worden statische elementen geretourneerd met de HTTP-statuscode 304 (Niet gewijzigd), zoals in de volgende afbeelding wordt getoond.

![ HTTP 304 (Gewijzigd niet) antwoordcode wijst op het statische element in het lokale geheime voorgeheugen het zelfde als op de server ](../../assets/configuration/varnish-304.png) is

De 304-statuscode treedt op omdat de gebruiker de lokale cache ongeldig heeft gemaakt en de inhoud op de server niet is gewijzigd. Wegens de 304 statuscode, wordt de statische activa _inhoud_ niet overgebracht; slechts worden de kopballen van HTTP gedownload aan browser.

Als de inhoud op de server verandert, downloadt de client het statische element met een HTTP 200 (OK)-statuscode en een nieuwe ETag.

<!-- Link Definitions -->

[De Big Varnish Picture]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Varnish Cache]: https://varnish-cache.org
[Opstartopties vervagen]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[Vernish en Websites]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[Varnish ondersteunt SSL niet]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
