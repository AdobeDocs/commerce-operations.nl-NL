---
title: Webserver configureren
description: Leer hoe u uw webserver configureert voor gebruik met Varnish.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---


# Uw webserver configureren

Vorm uw Webserver om op een haven buiten standaardhaven 80 te luisteren omdat Varnish direct aan inkomende HTTP- verzoeken, niet de Webserver antwoordt.

In de volgende secties wordt poort 8080 als voorbeeld gebruikt.

**De Apache 2.4-luisterpoort wijzigen**:

1. Openen `/etc/httpd/conf/httpd.conf` in een teksteditor.
1. Zoek de `Listen` richtlijn.
1. Wijzig de waarde van de listen-poort naar `8080`. (U kunt elke beschikbare listen-poort gebruiken.)
1. Sla uw wijzigingen op in `httpd.conf` en sluit de teksteditor af.

## De configuratie van het vernis-systeem wijzigen

Om de het systeemconfiguratie van Varnish te wijzigen:

1. Als gebruiker met `root` rechten, opent u het Vanish-configuratiebestand in een teksteditor:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Stel de Varnish listen-poort in op 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Voor Varnish 4.x, zorg ervoor dat DAEMON_OPTS de correcte luisterhaven voor bevat `-a` parameter (zelfs als VARNISH_LISTEN_PORT aan de correcte waarde wordt geplaatst):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Sla de wijzigingen op in het Varnish-configuratiebestand en sluit de teksteditor af.

### De standaard-VCL wijzigen

Deze sectie bespreekt hoe te om minimale configuratie te verstrekken zodat keert Varnish de antwoordkopballen van HTTP terug. Dit laat u toe om te verifiëren dat de werken van Varnish alvorens u vormt [!DNL Commerce] de aanvraag voor het gebruik van Varnish.

Varnish minimaliseren:

1. Back-up maken `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Openen `/etc/varnish/default.vcl` in een teksteditor.
1. Zoek de volgende spatie:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Vervang de waarde van `.host` met volledig - gekwalificeerde hostname of IP adres en luisterhaven van Varnish _achterste_ of _oorspronkelijke server_; Dat wil zeggen dat de server die de inhoud levert Varnish zal versnellen.

   Dit is doorgaans uw webserver. Zie [Backendeservers](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) in de _Varnish guide_.

1. Vervang de waarde van `.port` met de luisterpoort van de webserver (8080 in dit voorbeeld).

   Voorbeeld: Apache is geïnstalleerd op host 192.0.2.55 en Apache luistert naar poort 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Als Varnish en Apache op de zelfde gastheer lopen, adviseert Adobe dat u een IP adres of hostname en niet gebruikt `localhost`.

1. Sla uw wijzigingen op in `default.vcl` en sluit de teksteditor af.

1. Varnish opnieuw starten:

   ```bash
   service varnish restart
   ```

Als Varnish er niet in slaagt te beginnen, probeer het in werking stellen van het van de bevellijn als volgt:

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Dit zou foutenmeldingen moeten tonen.


>[!INFO]
>
>Als Varnish niet als dienst begint, moet u regels vormen SELinux om het toe te staan om te lopen.

## Controleer of Varnish werkt

De volgende secties bespreken hoe u kunt verifiëren dat Varnish werkt maar _zonder_ het vormen van Handel om het te gebruiken. U zou dit moeten proberen alvorens u Handel vormt.

Voer de taken uit die in de volgende secties in de getoonde orde worden besproken:

- [Varnish starten](#start-varnish)
- [&quot;netstat&quot;](#netstat)

### Varnish starten

Enter: `service varnish start`

Als Varnish er niet in slaagt om als dienst te beginnen, begin het van de bevellijn als volgt:

1. Start de Varnish CLI:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Start het Varnish child-proces:

   Typ desgevraagd `start`

   De volgende berichten worden weergegeven om te bevestigen dat het programma is gestart:

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Meld u aan bij de Varnish-server en voer de volgende opdracht in:

```bash
netstat -tulpn
```

Zoek in het bijzonder de volgende output:

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

In het voorgaande ziet u Varnish die op poort 80 wordt uitgevoerd en Apache die op poort 8080 wordt uitgevoerd.

Als u geen uitvoer ziet voor `varnishd`, zorg ervoor dat Varnish loopt.

Zie [`netstat` opties](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## De software Commerce installeren

Installeer de Commerce-software als u dat nog niet hebt gedaan. Wanneer ertoe aangezet voor een Basis URL, gebruik de Varnish gastheer en haven 80 (voor Varnish) omdat Varnish alle inkomende HTTP- verzoeken ontvangt.

Mogelijke fout bij het installeren van Commerce:

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Als deze fout optreedt, bewerkt u `default.vcl` en voeg een time-out toe aan de `backend` stanza, als hieronder:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## HTTP-antwoordheaders verifiëren

Nu kunt u verifiëren dat Varnish pagina&#39;s door HTML antwoordkopballen te bekijken die van om het even welke pagina zijn teruggekeerd.

Alvorens u kopballen kunt bekijken, moet u Handel voor ontwikkelaarwijze plaatsen. Er zijn verschillende manieren om het te doen, het eenvoudigste is te wijzigen `.htaccess` in de hoofdmap van de toepassing Commerce. U kunt ook de opdracht [`magento deploy:mode:set`](../cli/set-mode.md) gebruiken.

### Handel voor ontwikkelmodus instellen

Als u Handel voor de modus Ontwikkelaar wilt instellen, gebruikt u de optie [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) gebruiken.

### Kijk naar het Varnish log

Zorg ervoor dat Varnish dan het volgende bevel op de server van Varnish loopt ingaat:

```bash
varnishlog
```

Ga in een webbrowser naar een willekeurige handelspagina.

Een lange lijst van reactiekopballen tonen in uw bevel snelle venster. Zoek naar kopballen als het volgende:

```terminal
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

Als kopteksten zoals deze _niet_ weergave, vernis stoppen, controleer uw `default.vcl`en probeer het opnieuw.

### HTML-antwoordheaders bekijken

Er zijn verschillende manieren om naar antwoordheaders te kijken, bijvoorbeeld met een browserplug-in of een browsercontrole.

In het volgende voorbeeld wordt `curl`. U kunt dit bevel van om het even welke machine ingaan die tot de server van de Handel kan toegang hebben gebruikend HTTP.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Bijvoorbeeld:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Zoek naar kopballen als het volgende:

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
