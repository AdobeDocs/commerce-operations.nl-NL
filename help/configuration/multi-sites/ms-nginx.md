---
title: Meerdere websites instellen met Nginx
description: Volg deze zelfstudie om meerdere websites in te stellen met Nginx.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '961'
ht-degree: 0%

---


# Meerdere websites instellen met Nginx

Wij gaan ervan uit dat:

- U werkt op een ontwikkelcomputer (laptop, virtuele machine of dergelijke).

   Er kunnen extra taken nodig zijn om meerdere websites in een gehoste omgeving te implementeren. Raadpleeg uw hostingprovider voor meer informatie.

   Er zijn extra taken nodig om Adobe Commerce in te stellen op cloudinfrastructuur. Nadat u de taken voltooit die in dit onderwerp worden besproken, zie [Meerdere websites of winkels instellen](https://devdocs.magento.com/cloud/project/project-multi-sites.html) in de _Commerce Cloud-hulplijn_.

- U accepteert meerdere domeinen in één virtueel hostbestand of gebruikt één virtuele host per website. de virtuele dossiers van de gastheerconfiguratie in worden gevestigd `/etc/nginx/sites-available`.
- U gebruikt de `nginx.conf.sample` verstrekt door de Handel met slechts de wijzigingen die in deze zelfstudie worden besproken.
- De software Commerce is geïnstalleerd in `/var/www/html/magento2`.
- U hebt twee andere websites dan de standaard:

   - `french.mysite.mg` met websitecode `french` en archiefweergavecode `fr`
   - `german.mysite.mg` met websitecode `german` en archiefweergavecode `de`
   - `mysite.mg` is de standaardwebsite en de standaardwinkelweergave

>[!TIP]
>
>Zie [Websites maken](ms-admin.md#step-2-create-websites) en [Winkelweergaven maken](ms-admin.md#step-4-create-store-views) voor hulp bij het zoeken naar deze waarden.

Hieronder volgt een routekaart voor het instellen van meerdere websites met nginx:

1. [Websites, winkels en winkels instellen](ms-admin.md) in de Admin.
1. Een [Nginx virtuele host](#step-2-create-nginx-virtual-hosts)) om een groot aantal websites of één virtuele Nginx-host per Commerce-website toe te wijzen (hieronder beschreven stappen).
1. Geef de waarden van de [MAGE variabelen](ms-overview.md) `$MAGE_RUN_TYPE` en `$MAGE_RUN_CODE` naar nginx met behulp van de door Magento geleverde `nginx.conf.sample` (zie de onderstaande stappen).

   - `$MAGE_RUN_TYPE` kan `store` of `website`:

      - Gebruiken `website` om uw website in uw winkel te laden.
      - Gebruiken `store` om een winkelweergave in uw winkel te laden.
   - `$MAGE_RUN_CODE` is de unieke website- of opslagweergavecode die overeenkomt met `$MAGE_RUN_TYPE`.


1. Werk de configuratie van Basis URL op Commerce admin bij.

## Stap 1: Websites maken, winkels maken en weergaven opslaan in Beheer

Zie [Meerdere websites instellen, weergaven opslaan en opslaan in de beheerfunctie](ms-admin.md).

## Stap 2: Nginx virtuele hosts maken

In deze stap wordt besproken hoe u websites kunt laden op de [storefront](https://glossary.magento.com/storefront). U kunt websites gebruiken of meningen opslaan; als u opslagweergaven gebruikt, moet u de parameterwaarden dienovereenkomstig aanpassen. U moet de taken in deze sectie voltooien als gebruiker met `sudo` rechten.

Door slechts één te gebruiken [nginx virtueel hostbestand](#step-2-create-nginx-virtual-hosts), kunt u uw nginx-configuratie eenvoudig en schoon houden. Door meerdere virtuele hostbestanden te gebruiken, kunt u elke winkel aanpassen (om een aangepaste locatie te gebruiken voor `french.mysite.mg` bijvoorbeeld).

**Eén virtuele host maken** (vereenvoudigd):

Deze configuratie wordt uitgebreid [Nginx-configuratie](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/nginx.html).

1. Open een teksteditor en voeg de volgende inhoud toe aan een nieuw bestand met de naam `/etc/nginx/sites-available/magento`:

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

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Controleer de syntaxis van uw configuratiebestanden van de virtuele host als er fouten worden weergegeven.

1. Een symbolische koppeling maken in het dialoogvenster `/etc/nginx/sites-enabled` map:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Zie voor meer informatie over de kaartenrichtlijn [nginx - documentatie over de kaartenrichtlijn](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**Meerdere virtuele hosts maken**:

1. Open een teksteditor en voeg de volgende inhoud toe aan een nieuw bestand met de naam `/etc/nginx/sites-available/french.mysite.mg`:

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

1. Een ander bestand met de naam `german.mysite.mg` in dezelfde map met de volgende inhoud:

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

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Controleer de syntaxis van uw configuratiebestanden van de virtuele host als er fouten worden weergegeven.

1. Symbolische koppelingen maken in het dialoogvenster `/etc/nginx/sites-enabled` map:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## Stap 3: nginx.conf.sample wijzigen

>[!TIP]
>
>Bewerk de `nginx.conf.sample` bestand; het is een kernbestand voor Handel dat bij elke nieuwe release kan worden bijgewerkt. In plaats daarvan kopieert u de `nginx.conf.sample` en wijzigt u de naam van het bestand en bewerkt u het gekopieerde bestand.

**Het PHP-ingangspunt voor de hoofdtoepassing bewerken**:

Als u de `nginx.conf.sample` bestand**:

1. Een teksteditor openen en de `nginx.conf.sample` bestand,`<magento2_installation_directory>/nginx.conf.sample`. Zoek de volgende sectie:

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

1. Werk de `nginx.conf.sample` bestand met de volgende twee regels vóór de instructie include:

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

## Stap 4: De configuratie voor basis-URL bijwerken

U moet de basis-URL bijwerken voor het dialoogvenster `french` en de `german` websites in de Commerce-administratie.

### Basis-URL Franse website bijwerken

1. Meld u aan bij de Commerce-beheerder en navigeer naar **Winkels** > **Instellingen** > **Configuratie** > **Algemeen** > **Web**.
1. Wijzig de _configuratiebereik_ aan de `french` website.
1. Uitbreiden **Basis-URL&#39;s** en werkt de **Basis-URL** en **URL basiskoppeling** waarde aan `http://french.magento24.com/`.
1. Uitbreiden **Basis-URL&#39;s (veilig)** en werkt de **Beveiligde basis-URL** en **Secure Base Link URL** waarde aan `https://french.magento24.com/`.
1. Klikken **Config opslaan** en sla de configuratiewijzigingen op.

### URL van basis Duitse website bijwerken

1. Meld u aan bij de Commerce-beheerder en navigeer naar **Winkels** > **Instellingen** > **Configuratie** > **Algemeen** > **Web**.
1. Wijzig de _configuratiebereik_ aan de `german` website.
1. Uitbreiden **Basis-URL&#39;s** en werkt de **Basis-URL** en **URL basiskoppeling** waarde aan `http://german.magento24.com/`.
1. Uitbreiden **Basis-URL&#39;s (veilig)** en werkt de **Beveiligde basis-URL** en **Secure Base Link URL** waarde aan `https://german.magento24.com/`.
1. Klikken **Config opslaan** en sla de configuratiewijzigingen op.

### Cache reinigen

Voer de volgende opdracht uit om de `config` en `full_page` caches.

```bash
bin/magento cache:clean config full_page
```

## Uw site verifiëren

Tenzij u DNS opstelling voor de URL van uw opslag hebt, moet u een statische route aan de gastheer in uw toevoegen `hosts` bestand:

1. Het besturingssysteem zoeken `hosts` bestand.
1. Voeg de statische route in het formaat toe:

   ```conf
   <ip address> french.mysite.mg
   <ip address> german.mysite.mg
   ```

1. Ga naar een van de volgende URL&#39;s in uw browser:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Er kunnen extra taken nodig zijn om meerdere websites in een gehoste omgeving te implementeren. Raadpleeg uw hostingprovider voor meer informatie.
>- Er zijn extra taken nodig om Adobe Commerce op cloudinfrastructuur in te stellen. zie [Meerdere Cloud-websites of -winkels instellen](https://devdocs.magento.com/cloud/project/project-multi-sites.html) in de _Commerce Cloud-hulplijn_.


### Problemen oplossen

- Als uw Franse en Duitse sites 404s retourneren maar uw Admin-account wordt geladen, moet u de handeling voltooien [Stap 6: De code van de winkel toevoegen aan de basis-URL](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Als alle URL&#39;s 404 retourneren, moet u de webserver opnieuw starten.
- Als de beheerder niet correct werkt, zorg ervoor u opstelling uw virtuele gastheren behoorlijk.
