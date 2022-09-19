---
title: De toepassing configureren
description: Meer informatie over de configuratie na installatie die vereist is voor Adobe Commerce- en Magento Open Source-implementaties op locatie.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# De toepassing configureren

Nu u Adobe Commerce of Magento Open Source hebt geïnstalleerd, moet u het configureren. Dit onderwerp verstrekt sommige geadviseerde configuratiemontages.

## Uitsnede instellen

De UNIX taakplanner, cron, is kritiek aan de verrichtingen van dag tot dag van de toepassing. Het plant dingen zoals het opnieuw indexeren, nieuwsbrieven, e-mail, en sitemaps. A *crontab* is een uitsnijdconfiguratie.

U moet Adobe Commerce- en Magento Open Source-services installeren in het dialoogvenster *crontab* of sommige kernfuncties (en sommige extensies van derden) functioneren niet correct.

Zie voor meer informatie over uitsnijden, zoals hoe u een tab kunt verwijderen en een uitsnede kunt uitvoeren vanaf de opdrachtregel [Uitsnede configureren en uitvoeren](../../configuration/cli/configure-cron-jobs.md).

## Beveiligingsinstellingen en aanbevelingen

Na de installatie raden we het volgende aan:

* Zorg ervoor dat de eigendom van het bestand en de machtigingen correct zijn ingesteld.
* We raden u sterk aan [de standaardbeheerderURI wijzigen](../tutorials/admin-uri.md) van `admin` aan iets anders
* Zorg ervoor dat de [`X-Frame-Option` HTTP-header](../../configuration/security/xframe-options.md) wordt op de juiste wijze ingesteld.
* Voorzorgsmaatregelen nemen tegen XSS (cross-site scripting) door [uw sjablonen beveiligen](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Als u door [het klonen van de bewaarplaats van GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/), zorgt u ervoor dat wanneer u de toepassing implementeert, u alleen bestanden en mappen opneemt die vereist zijn voor de productieomgeving. Bestanden en mappen die niet vereist zijn, kunnen beveiligingsrisico&#39;s opleveren.

## Herschrijvingen van Apache-servers inschakelen

Als u de Apache-webserver gebruikt, moet u de weergave van herschrijvingen van pagina&#39;s door de server inschakelen. Anders ziet u pagina&#39;s zonder stijlen en andere problemen.

[Sectie op Apache-server herschrijft](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## In cache plaatsen in een omgeving met meerdere webknooppunten

Als u meerdere webknooppunten hebt, kunt u *kan* de standaardbestandcache van de toepassing gebruiken omdat er geen synchronisatie tussen de webknooppunten is. Met andere woorden, de activiteit op één webknooppunt wordt alleen naar het bestandssysteem van dat webknooppunt geschreven. Als een volgende activiteit wordt uitgevoerd op een ander webknooppunt, kunnen er onnodige bestanden worden geschreven of kunnen er fouten optreden.

Gebruik in plaats daarvan [Redis](../../configuration/cache/config-redis.md) voor beide standaardinstellingen [cachegeheugen](https://glossary.magento.com/cache) en de paginacache.

## Serverinstellingen

Deze sectie bespreekt kort montages die wij u adviseren voor de server overwegen waarop de toepassing loopt. Sommige van deze instellingen zijn niet rechtstreeks gerelateerd aan de toepassing. deze worden alleen als suggesties gegeven .

### Logrotatie

UNIX `logrotate` Het nut laat u toe om systemen te beheren die grote aantallen logboekdossiers produceren. Hiermee kunnen logbestanden automatisch worden geroteerd, gecomprimeerd, verwijderd en gemaild. Elk logbestand kan dagelijks, wekelijks, maandelijks of wanneer het logbestand een bepaalde grootte overschrijdt, worden afgehandeld.

Zie een van de volgende bronnen voor meer informatie:

* [Procedure: De ultieme opdrachtzelfstudie voor het roteren van logbestanden met tien voorbeelden](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stapeluitwisseling](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` man page](https://linuxconfig.org/logrotate-8-manual-page)

### Opstelling iptables regels om de diverse diensten toe te laten om mee te delen

Of u één server of vele hebt, moet u havens in de firewall openen om de diensten toe te laten om te communiceren. Als u bijvoorbeeld de zoekfunctie Solr in Adobe Commerce gebruikt, moet u deze inschakelen voor communicatie met de webserver. Als u meerdere webknooppunten hebt, moet u deze in staat stellen met elkaar te communiceren.

Meer informatie:

* Ubuntu: [Documentatiepagina Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [Hoe-kan-ik-bestand voor CentOS](https://wiki.centos.org/HowTos/Network/IPTables).

### Security Enhanced Linux (SELinux)-regels

We hebben geen aanbeveling voor het gebruik van SELinux. nochtans, als u het gebruikt, moet u de diensten vormen om met elkaar te communiceren gelijkend op het vormen iptables.

Meer informatie:

* Ubuntu: [Debian-handboek](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS wiki](https://wiki.centos.org/HowTos/SELinux)

### Een e-mailserver instellen

Adobe Commerce en Magento Open Source hebben een e-mailserver nodig. Wij adviseren geen bepaalde server, maar u kunt om het even welke volgend proberen:

* Postfix voor CentOS ([Lesbestand digitale oceaan](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS-documentatie](https://www.centos.org))
* Postfix voor Ubuntu ([Lesbestand digitale oceaan](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu-documentatie](https://help.ubuntu.com/community/MailServer))

### Verfijn de zoekmachine voor verbeterde prestaties:

Elasticsearch of OpenSearch is vereist voor alle installaties vanaf 2.4.0.

* [De zoekmachine installeren en configureren](../../configuration/search/overview-search.md)

### Een wachtrij met berichten instellen

Sinds versie 2.3.0 bevatten Adobe Commerce en Magento Open Source een functionaliteit voor een wachtrij met berichten. In eerdere versies is deze alleen beschikbaar voor Adobe Commerce.

* [KonijnMQ](../../configuration/queues/message-queue-framework.md)

## Alleen instellingen voor Adobe Commerce

U kunt het volgende slechts vormen als u Adobe Commerce gebruikt:

* [Databases splitsen voor uitchecken, orderbeheer en andere databasetabellen](../../configuration/storage/multi-master.md)