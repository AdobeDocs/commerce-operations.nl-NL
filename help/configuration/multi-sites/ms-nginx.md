---
title: Meerdere websites instellen met Nginx
description: Volg deze zelfstudie om meerdere websites in te stellen met Nginx.
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Meerdere websites instellen met Nginx

Wij gaan ervan uit dat:

- U werkt op een ontwikkelcomputer (laptop, virtuele machine of dergelijke).

  Er kunnen extra taken nodig zijn om meerdere websites in een gehoste omgeving te implementeren. Neem contact op met uw hostingprovider voor meer informatie.

  Er zijn extra taken nodig om Adobe Commerce in te stellen op cloudinfrastructuur. Nadat u de taken voltooit die in dit onderwerp worden besproken, zie [ Opstelling veelvoudige websites of opslag ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=nl-NL) in _Commerce op de gids van de Infrastructuur van de Wolk_.

- U accepteert meerdere domeinen in één virtueel hostbestand of gebruikt één virtuele host per website. De configuratiebestanden van de virtuele host bevinden zich in `/etc/nginx/sites-available` .
- U gebruikt de `nginx.conf.sample` die door Commerce wordt geleverd, alleen de wijzigingen die in deze zelfstudie worden besproken.
- De Commerce-software wordt geïnstalleerd in `/var/www/html/magento2` .
- U hebt twee andere websites dan de standaard:

   - `french.mysite.mg` met websitecode `french` en code van de opslagweergave `fr`
   - `german.mysite.mg` met websitecode `german` en code van de opslagweergave `de`
   - `mysite.mg` is de standaardwebsite- en winkelweergave

>[!TIP]
>
>Verwijs naar [ creeer websites ](ms-admin.md#step-2-create-websites) en [ creeer opslagmeningen ](ms-admin.md#step-4-create-store-views) voor hulp bij het bepalen van deze waarden.

Hieronder volgt een routekaart voor het instellen van meerdere websites met nginx:

1. [ Opstelling websites, opslag, en opslagmeningen ](ms-admin.md) in Admin.
1. Creeer een [ virtuele gastheer Nginx ](#step-2-create-nginx-virtual-hosts)) om vele websites of één virtuele gastheer Nginx per website van Commerce (hieronder gedetailleerde stappen) in kaart te brengen.
1. Geef de waarden van de [ variabelen van de GROOTTE ](ms-overview.md) `$MAGE_RUN_TYPE` en `$MAGE_RUN_CODE` aan nginx door Magento-Geleverde `nginx.conf.sample` (hieronder gedetailleerde stappen) te gebruiken.

   - `$MAGE_RUN_TYPE` kan `store` of `website` zijn:

      - Gebruik `website` om uw website in uw winkel te laden.
      - Gebruik `store` om een winkelweergave in uw winkelvoorkeuren te laden.

   - `$MAGE_RUN_CODE` is de unieke website- of opslagweergavecode die overeenkomt met `$MAGE_RUN_TYPE` .

1. Werk de configuratie van Basis URL op Commerce admin bij.

## Stap 1: Websites maken, winkels maken en weergaven opslaan in Beheer

Zie [ Opstelling veelvoudige websites, opslag, en opslagmeningen in Admin ](ms-admin.md).

## Stap 2: Nginx virtuele hosts maken

In deze stap wordt beschreven hoe u websites op de winkel kunt laden. U kunt websites of opslagweergaven gebruiken. Als u opslagweergaven gebruikt, moet u de parameterwaarden dienovereenkomstig aanpassen. U moet de taken in deze sectie uitvoeren als een gebruiker met `sudo` rechten.

Door enkel één [ nginx virtueel gastheerdossier ](#step-2-create-nginx-virtual-hosts) te gebruiken, kunt u uw nginxconfiguratie eenvoudig en schoon houden. Door verschillende virtuele hostbestanden te gebruiken, kunt u elke winkel aanpassen (bijvoorbeeld om een aangepaste locatie voor `french.mysite.mg` te gebruiken).

**om één virtuele gastheer** (vereenvoudigd) tot stand te brengen:

Deze configuratie breidt zich op [ nginx configuratie ](../../installation/prerequisites/web-server/nginx.md) uit.

1. Open een teksteditor en voeg de volgende inhoud toe aan een nieuw bestand met de naam `/etc/nginx/sites-available/magento` :

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Sla de wijzigingen in de bestanden op en sluit de teksteditor af.
1. Controleer de serverconfiguratie:

   ```bash
   nginx -t
   ```

1. Als dit gelukt is, wordt het volgende bericht weergegeven:

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Controleer de syntaxis van uw configuratiebestanden van de virtuele host als er fouten worden weergegeven.

1. Een symbolische koppeling maken in de map `/etc/nginx/sites-enabled` :

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Voor meer detail over de kaartrichtlijn, zie [ nginx documentatie over de kaartrichtlijn ](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**om veelvoudige virtuele gastheren** tot stand te brengen:

1. Open een teksteditor en voeg de volgende inhoud toe aan een nieuw bestand met de naam `/etc/nginx/sites-available/french.mysite.mg` :

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Maak een ander bestand met de naam `german.mysite.mg` in dezelfde map met de volgende inhoud:

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Sla de wijzigingen in de bestanden op en sluit de teksteditor af.
1. Controleer de serverconfiguratie:

   ```bash
   nginx -t
   ```

1. Als dit gelukt is, wordt het volgende bericht weergegeven:

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Controleer de syntaxis van uw configuratiebestanden van de virtuele host als er fouten worden weergegeven.

1. Symbolische koppelingen maken in de map `/etc/nginx/sites-enabled` :

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## Stap 3: Nginx.conf.sample wijzigen

>[!TIP]
>
>Bewerk het `nginx.conf.sample` -bestand niet. Het is een Commerce-kernbestand dat bij elke nieuwe release kan worden bijgewerkt. Kopieer in plaats daarvan het `nginx.conf.sample` -bestand, wijzig de naam ervan en bewerk vervolgens het gekopieerde bestand.

**om het PHP ingangspunt voor de belangrijkste toepassing uit te geven**:

Het `nginx.conf.sample` bestand** wijzigen:

1. Open een teksteditor en bekijk het `nginx.conf.sample` -bestand `<magento2_installation_directory>/nginx.conf.sample` . Zoek de volgende sectie:

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. Werk het `nginx.conf.sample` bestand bij met de volgende twee regels vóór de instructie include:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Een voorbeeld van een bijgewerkt PHP-ingangspunt voor de hoofdtoepassing ziet er als volgt uit:

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## Stap 4: Werk de basis-URL-configuratie bij

U moet de basis-URL voor de `french` - en `german` -websites bijwerken in de Commerce-beheerder.

### Basis-URL Franse website bijwerken

1. Login aan Commerce admin en navigeer aan **Opslag** > **Montages** > **Configuratie** > **Algemeen** > **Web**.
1. Verander het _configuratiewerkingsgebied_ in de `french` website.
1. Breid **Basis URLs** sectie uit en werk de **Basis URL** en **waarde van de Verbinding URL van de Basis** aan `http://french.magento24.com/` bij.
1. Breid **Basis URLs (Veilig) uit** sectie en werk de **Veilige Basis URL** en **Veilige waarde van de Verbinding URL van de Basis** aan `https://french.magento24.com/` bij.
1. Klik **sparen Config** en sla de configuratieveranderingen op.

### URL van basis Duitse website bijwerken

1. Login aan Commerce admin en navigeer aan **Opslag** > **Montages** > **Configuratie** > **Algemeen** > **Web**.
1. Verander het _configuratiewerkingsgebied_ in de `german` website.
1. Breid **Basis URLs** sectie uit en werk de **Basis URL** en **waarde van de Verbinding URL van de Basis** aan `http://german.magento24.com/` bij.
1. Breid **Basis URLs (Veilig) uit** sectie en werk de **Veilige Basis URL** en **Veilige waarde van de Verbinding URL van de Basis** aan `https://german.magento24.com/` bij.
1. Klik **sparen Config** en sla de configuratieveranderingen op.

### Cache reinigen

Voer de volgende opdracht uit om de cache van `config` en `full_page` leeg te maken.

```bash
bin/magento cache:clean config full_page
```

## Uw site verifiëren

Tenzij u DNS opstelling voor URLs van uw opslag hebt, moet u een statische route aan de gastheer in uw `hosts` dossier toevoegen:

1. Zoek het `hosts` -bestand van uw besturingssysteem.
1. Voeg de statische route in het formaat toe:

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Ga naar een van de volgende URL&#39;s in uw browser:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Er kunnen extra taken nodig zijn om meerdere websites in een gehoste omgeving te implementeren. Neem contact op met uw hostingprovider voor meer informatie.
>- De extra taken worden vereist aan opstelling Adobe Commerce op wolkeninfrastructuur; zie [ Opstelling veelvoudige websites of opslag van de Wolk ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=nl-NL) in _Commerce op de gids van de Infrastructuur van de Wolk_.

### Problemen oplossen

- Als uw Franse en Duitse plaatsen 404s maar uw Admin laadt terugkeren, zorg u [ Stap 6 voltooide: voeg de opslagcode aan basisURL ](ms-admin.md#step-6-add-the-store-code-to-the-base-url) toe.
- Als alle URL&#39;s 404 retourneren, moet u de webserver opnieuw starten.
- Als de beheerder niet correct werkt, zorg ervoor u opstelling uw virtuele gastheren behoorlijk.
