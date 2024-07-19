---
title: Onderhoudsmodusopties voor upgrade
description: Maak een aangepaste pagina voor de onderhoudsmodus die uw klanten op uw Adobe Commerce-winkel zien wanneer u een upgrade uitvoert.
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Opties voor de onderhoudsmodus voor upgrade

Dit onderwerp bespreekt hoe u een pagina van het douaneonderhoud aan vertoning aan gebruikers kunt tot stand brengen terwijl uw toepassing van het Magento wordt bevorderd. Het maken van een aangepaste pagina is optioneel, maar wordt aangeraden, omdat uw site tijdens een deel van de upgrade toegankelijk is.

Door een aangepaste pagina te maken waarnaar gebruikers kunnen omleiden, wordt geen toegang tot de site mogelijk en wordt uw gebruikers ook geïnformeerd dat er onderhoud aan de site wordt uitgevoerd.

>[!NOTE]
>
>U moet de taken in deze sectie uitvoeren als een gebruiker met `root` rechten. Aangepaste onderhoudspagina&#39;s kunnen niet worden ingesteld in de modus Ontwikkelaar.

## De aangepaste onderhoudspagina maken

Als u een onderhoudspagina wilt maken en deze wilt omleiden, maakt u eerst een onderhoudspagina met de naam:

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

Voeg de volgende inhoud toe:

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Aangepaste onderhoudspagina voor Apache

Deze sectie bespreekt hoe te om een pagina van het douaneonderhoud tot stand te brengen en hoe te om verkeer aan het om te leiden.

In het voorbeeld in deze sectie ziet u hoe u de volgende bestanden kunt wijzigen. Dit is een manier om uw onderhoudspagina in te stellen:

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` (Ubuntu), `/etc/httpd/conf/httpd.conf` (CentOS)

Verkeer omleiden naar een aangepaste onderhoudspagina:

1. Werk uw Apache-configuratie als volgt bij:

   - Alle verkeer omleiden naar de onderhoudspagina
   - Lijst van gewenste personen bepaalde IPs zodat kan een beheerder de software van het Magento bevorderen.

   In het volgende voorbeeld wordt de lijst van gewenste personen 192.0.2.110 toegepast.

   Voeg het volgende toe aan het einde van het Apache-configuratiebestand:

   ```
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Apache opnieuw starten:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

1. Voer de volgende opdracht in:

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [ bevorder uw systeem ](../implementation/perform-upgrade.md).
1. Test uw site om te controleren of deze correct werkt.
1. Verwijder `maintenance.enable` nadat de upgrade is voltooid.

## Aangepaste onderhoudspagina voor nginx

Deze sectie bespreekt hoe te om een pagina van het douaneonderhoud tot stand te brengen en hoe te om verkeer aan het om te leiden.

Verkeer omleiden naar een aangepaste onderhoudspagina:

1. Gebruik een tekstverwerker om het configuratiebestand van de nginx te openen dat uw serverblok bevat.
1. Voeg het volgende aan het serverblok toe (`server` wordt getoond voor duidelijkheid slechts; voeg geen tweede serverblok toe).

   De volgende lijsten van gewenste personen IP adres 192.0.2.110 en 192.0.2.115 op een systeem waar het Magento in `/var/www/html/magento2` wordt geïnstalleerd:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Voer de volgende opdracht in:

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. Laad de configuratie nginx opnieuw:

   ```bash
   service nginx reload
   ```

1. [ bevorder uw systeem ](../implementation/perform-upgrade.md).
1. Test uw site om te controleren of deze correct werkt.
1. Nadat de upgrade is voltooid, verwijdert u de upgrade of wijzigt u de naam van de toepassing `maintenance.enable`
1. Laad de configuratie nginx opnieuw:

   ```bash
   service nginx reload
   ```
