---
title: Webserver configureren
description: Leer hoe u uw webserver configureert voor gebruik met Varnish caching voor Adobe Commerce. Ontdek havenconfiguratie en opstellingsvereisten.
feature: Configuration, Cache, Install, Logs
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 0%

---

# Uw webserver configureren

Vorm uw Webserver om op een haven buiten standaardhaven 80 te luisteren omdat Varnish direct aan inkomende HTTP- verzoeken, niet de Webserver antwoordt.

In de volgende secties wordt poort 8080 als voorbeeld gebruikt.

**om Apache 2.4 te veranderen luistert haven**:

1. Open `/etc/httpd/conf/httpd.conf` in een teksteditor.
1. Zoek de aanwijzing `Listen` .
1. Wijzig de waarde van de listen-poort in `8080` . (U kunt elke beschikbare listen-poort gebruiken.)
1. Sla de wijzigingen in `httpd.conf` op en sluit de teksteditor af.

## De configuratie van het vernis-systeem wijzigen

Om de het systeemconfiguratie van Varnish te wijzigen:

1. Als gebruiker met `root` bevoegdheden opent u het Vanish-configuratiebestand in een teksteditor:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Stel de Varnish listen-poort in op 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Voor Varnish 4.x, zorg ervoor dat DAEMON_OPTS de correcte luisterhaven voor de `-a` parameter bevat (zelfs als VARNISH_LISTEN_PORT aan de correcte waarde wordt geplaatst):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Sla de wijzigingen op in het Varnish-configuratiebestand en sluit de teksteditor af.

### De standaard-VCL wijzigen

Deze sectie bespreekt hoe te om minimale configuratie te verstrekken zodat keert Varnish de antwoordkopballen van HTTP terug. Hierdoor kunt u controleren of Varnish werkt voordat u de [!DNL Commerce] -toepassing configureert voor gebruik van Varnish.

Varnish minimaliseren:

1. Back-up maken `default.vcl` :

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Open `/etc/varnish/default.vcl` in een teksteditor.
1. Zoek de volgende spatie:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Vervang de waarde van `.host` met volledig - gekwalificeerd hostname of IP adres en luister haven van de Varnish _achterkant_ of _oorsprongserver_; namelijk zal de server die de inhoud verstrekt Varnish versnellen.

   Dit is doorgaans uw webserver. Zie [ servers van het Achterste 1} in de ](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) Versijke gids _._

1. Vervang de waarde van `.port` door de listen-poort van de webserver (8080 in dit voorbeeld).

   Voorbeeld: Apache is geïnstalleerd op de host 192.0.2.55 en Apache luistert naar poort 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Als Varnish en Apache op de zelfde gastheer lopen, adviseert Adobe dat u een IP adres of hostname en niet `localhost` gebruikt.

1. Sla de wijzigingen in `default.vcl` op en sluit de teksteditor af.

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

De volgende secties bespreken hoe u kunt verifiëren dat Varnish maar _werkt zonder_ het vormen Commerce om het te gebruiken. Probeer dit voordat u Commerce configureert.

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

   Typ `start` bij de aanwijzing

   De volgende berichten worden weergegeven om te bevestigen dat het programma is gestart:

   ```
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

```
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

In het voorgaande ziet u Varnish die op poort 80 wordt uitgevoerd en Apache die op poort 8080 wordt uitgevoerd.

Als u de uitvoer voor `varnishd` niet ziet, controleert u of Varnish wordt uitgevoerd.

Zie [`netstat` opties ](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## De Commerce-software installeren

Installeer de Commerce-software als u dat nog niet hebt gedaan. Wanneer ertoe aangezet voor een Basis URL, gebruik de Varnish gastheer en haven 80 (voor Varnish) omdat Varnish alle inkomende HTTP- verzoeken ontvangt.

Mogelijke fout bij het installeren van Commerce:

```
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

## HTTP-antwoordheaders verifiëren

Nu kunt u controleren of Varnish pagina&#39;s voorstelt door HTML-antwoordheaders te bekijken die vanaf een pagina worden geretourneerd.

Voordat u naar kopteksten kunt kijken, moet u de Commerce for developer-modus instellen. Er zijn verschillende manieren om dit te doen. U kunt `.htaccess` het eenvoudigst wijzigen in de hoofdmap van de Commerce-toepassing. U kunt ook de opdracht [`magento deploy:mode:set`](../cli/set-mode.md) gebruiken.

### Commerce instellen voor de modus Ontwikkelaar

Gebruik de opdracht [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) om de Commerce for developer-modus in te stellen.

### Kijk naar het Varnish log

Zorg ervoor dat Varnish dan het volgende bevel op de server van Varnish loopt ingaat:

```bash
varnishlog
```

Ga in een webbrowser naar een willekeurige Commerce-pagina.

Een lange lijst van reactiekopballen tonen in uw bevel snelle venster. Zoek naar kopballen als het volgende:

```
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

Als de kopballen als deze _niet_ tonen, vernis tegenhouden, uw `default.vcl` controleren, en opnieuw proberen.

### Koppen van HTML-reacties bekijken

Er zijn verschillende manieren om naar antwoordheaders te kijken, bijvoorbeeld met een browserplug-in of een browsercontrole.

In het volgende voorbeeld wordt `curl` gebruikt. U kunt deze opdracht invoeren vanaf elke computer die via HTTP toegang heeft tot de Commerce-server.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Bijvoorbeeld:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Zoek naar kopballen als het volgende:

```
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
