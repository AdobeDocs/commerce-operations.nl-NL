---
title: De toepassing configureren
description: Meer informatie over de configuratie na installatie die vereist is voor Adobe Commerce-implementaties op locatie.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: a28dad04dac23075234a6ac3c2b362d125c9d981
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# De toepassing configureren

Nu u Adobe Commerce hebt geïnstalleerd, moet u het configureren. Dit onderwerp verstrekt sommige geadviseerde configuratiemontages.

## Uitsnede instellen

De UNIX taakplanner, cron, is kritiek aan de verrichtingen van dag tot dag van de toepassing. Het plant dingen zoals het opnieuw indexeren, nieuwsbrieven, e-mail, en sitemaps. A *crontab* is een kroonconfiguratie.

U moet de diensten van Adobe Commerce in *contab* installeren, of sommige kernfunctionaliteit (en sommige derdeuitbreidingen) functioneren niet behoorlijk.

Voor meer informatie over kroon, met inbegrip van hoe te om een krontab te verwijderen en kroon in werking te stellen van de bevellijn, zie [ kroon ](../../configuration/cli/configure-cron-jobs.md) vormen en in werking stellen.

## Beveiligingsinstellingen en aanbevelingen

Na de installatie raden we het volgende aan:

* Zorg ervoor dat de eigendom van het bestand en de machtigingen correct zijn ingesteld.
* Wij adviseren sterk [ veranderend standaardAdmin URI ](../tutorials/admin-uri.md) van `admin` in iets anders
* Zorg ervoor dat de [`X-Frame-Option` HTTP-header ](../../configuration/security/xframe-options.md) juist is ingesteld.
* Neem voorzorgsmaatregelen tegen dwars-plaats scripting (XSS) door [ uw malplaatjes ](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/) te beveiligen

Als u door [ het klonen van de bewaarplaats GitHub ](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) installeerde, zorg ervoor dat wanneer u de toepassing opstelt, u slechts dossiers en omslagen omvat die voor het productiemilieu worden vereist. Bestanden en mappen die niet vereist zijn, kunnen beveiligingsrisico&#39;s opleveren.

## Herschrijvingen van Apache-servers inschakelen

Als u de Apache-webserver gebruikt, moet u de weergave van herschrijvingen van pagina&#39;s door de server inschakelen. Anders ziet u pagina&#39;s zonder stijlen en andere problemen.

[Sectie op Apache-server herschrijft](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## In cache plaatsen in een omgeving met meerdere webknooppunten

Als u veelvoudige Webknopen hebt, kunt u *niet* het standaard dossier caching van de toepassing gebruiken omdat er geen synchronisatie tussen Webknopen is. Met andere woorden, de activiteit op één webknooppunt wordt alleen naar het bestandssysteem van dat webknooppunt geschreven. Als een volgende activiteit wordt uitgevoerd op een ander webknooppunt, kunnen er onnodige bestanden worden geschreven of kunnen er fouten optreden.

In plaats daarvan, gebruikt [ opnieuw ](../../configuration/cache/config-redis.md) voor zowel het standaardgeheime voorgeheugen als het paginacache.

## Serverinstellingen

Deze sectie bespreekt kort montages die wij u adviseren voor de server overwegen waarop de toepassing loopt. Sommige van deze instellingen houden niet rechtstreeks verband met de toepassing. Deze instellingen worden alleen als suggesties geleverd.

### Logrotatie

Met het hulpprogramma UNIX `logrotate` kunt u systemen beheren die een groot aantal logbestanden genereren. Hiermee kunt u logbestanden automatisch roteren, comprimeren, verwijderen en verzenden. Elk logbestand kan dagelijks, wekelijks, maandelijks of wanneer het logbestand een bepaalde grootte overschrijdt, worden afgehandeld.

Zie een van de volgende bronnen voor meer informatie:

* [ HowTo: Het uiteindelijke logboek roteert bevelleerprogramma met tien voorbeelden ](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [ Uitwisseling van de Stapel ](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` man page ](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>De volgende informatie over beschikbaarheid is van toepassing op Adobe Commerce voor projecten in de cloud-infrastructuur:
>
>* Starteromgevingen hebben geen logrotatie.
>
>* U kunt logrotatie niet configureren in Pro Integration-omgevingen. U moet een douaneoplossing/manuscript uitvoeren en [ vormt uw kruin ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) om het manuscript in werking te stellen zoals nodig.

### Opstelling iptables regels om de diverse diensten toe te laten om mee te delen

Of u één server of vele hebt, moet u havens in de firewall openen om de diensten toe te laten om te communiceren. Als u bijvoorbeeld de zoekfunctie Solr in Adobe Commerce gebruikt, moet u deze inschakelen voor communicatie met de webserver. Als u meerdere webknooppunten hebt, moet u deze in staat stellen met elkaar te communiceren.

Meer informatie:

* Ubuntu: [ Ubuntu documentatiepagina ](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [ CentOS hoe-aan ](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### Security Enhanced Linux (SELinux)-regels

Wij hebben geen aanbeveling voor of u SELinux gebruikt; nochtans, als u het gebruikt, moet u de diensten vormen om met elkaar gelijkend op het vormen van iptables te communiceren.

Meer informatie:

* Ubuntu: [ Debian handboek ](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [ wiki CentOS ](https://wiki.centos.org/HowTos/SELinux)

### Een e-mailserver instellen

Adobe Commerce heeft een e-mailserver nodig. Wij adviseren geen bepaalde server, maar u kunt om het even welke volgend proberen:

* Postfix voor CentOS ([ Digital Ocean tutorial ](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [ documentatie CentOS ](https://www.centos.org))
* Postfix voor Ubuntu ([ Digital Ocean tutorial ](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [ documentatie Ubuntu ](https://help.ubuntu.com/community/MailServer))

### Verfijn de zoekmachine voor verbeterde prestaties:

Elasticsearch of OpenSearch is vereist voor alle installaties vanaf 2.4.0.

* [De zoekmachine installeren en configureren](../../configuration/search/overview-search.md)

### Een wachtrij met berichten instellen

Sinds versie 2.3.0 bevat Adobe Commerce functionaliteit voor een wachtrij met berichten. In eerdere versies is deze alleen beschikbaar voor Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Alleen instellingen voor Adobe Commerce

U kunt het volgende slechts vormen als u Adobe Commerce gebruikt:

* [Databases splitsen voor uitchecken, orderbeheer en andere databasetabellen](../../configuration/storage/multi-master.md)
