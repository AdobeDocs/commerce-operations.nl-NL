---
title: Documenthoofdmap wijzigen om de beveiliging te verbeteren
description: Ongeoorloofde browsertoegang tot het Adobe Commerce-bestandssysteem op locatie voorkomen.
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Documenthoofdmap wijzigen om de beveiliging te verbeteren

In een standaardinstallatie met een Apache-webserver wordt Adobe Commerce geïnstalleerd als de standaardhoofdmap van het web: `/var/www/html/magento2` .

De map `magento2/` bevat het volgende:

- `pub/`
- `setup/`
- `var/`

De toepassing wordt vanuit `/var/www/html/magento2/pub` verzonden. De rest van het bestandssysteem is kwetsbaar omdat het vanuit een browser toegankelijk is.
Als u de webroot instelt op de map `pub/` , hebben sitebezoekers geen toegang tot gevoelige gebieden van het bestandssysteem vanuit een browser.

In dit onderwerp wordt beschreven hoe u de Apache-hoofdmap van een bestaande instantie wijzigt om bestanden uit de map `pub/` te bedienen. Deze map is veiliger.

## Een opmerking over nginx

Als u [ nginx ](../prerequisites/web-server/nginx.md) en het [`nginx.conf.sample` ](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) dossier inbegrepen in de installatiemap gebruikt, dient u waarschijnlijk reeds dossiers van de `pub/` folder.

Wanneer de configuratie van `nginx.conf.sample` wordt gebruikt in uw serverblok dat uw site definieert, worden de hoofdmapinstellingen van uw server genegeerd om bestanden uit de map van `pub/` te bedienen. Zie bijvoorbeeld de laatste regel in de volgende configuratie:

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## Voordat u begint

Als u deze zelfstudie wilt voltooien, hebt u toegang nodig tot een werkende installatie die op een LAMP-stapel wordt uitgevoerd:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) of OpenSearch (1.2)
- Adobe Commerce (2.4+)

>[!NOTE]
>
>Verwijs naar [ Eerste vereisten ](../prerequisites/overview.md) en de [ Gids van de Installatie ](../overview.md) voor meer informatie.

## 1. De serverconfiguratie bewerken

De naam en locatie van het virtuele hostbestand zijn afhankelijk van de versie van Apache die u uitvoert. In dit voorbeeld worden de naam en locatie van het virtuele hostbestand op Apache v2.4 weergegeven.

1. Meld u aan bij uw toepassingsserver.
1. Bewerk uw virtuele hostbestand:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Voeg het pad naar de map `pub/` toe aan de aanwijzing `DocumentRoot` :

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. Apache opnieuw starten:

   ```bash
   systemctl restart apache2
   ```

## 2. Werk uw basis-URL bij

Als u een mapnaam aan de hostnaam of het IP-adres van de server hebt toegevoegd om de basis-URL te maken wanneer u de toepassing hebt geïnstalleerd (bijvoorbeeld `http://192.168.33.10/magento2` ), moet u deze verwijderen.

>[!NOTE]
>
>Vervang `192.168.33.10` door de hostnaam van de server.

1. Meld u aan bij de database:

   ```bash
   mysql -u <user> -p
   ```

1. Geef de database op die u hebt gemaakt toen u de toepassing installeerde:

   ```shell
   use <database-name>
   ```

1. De basis-URL bijwerken:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. Werk het bestand env.php bij

Voeg het volgende knooppunt toe aan het `env.php` -bestand.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Verwijs naar de {](../../configuration/reference/config-reference-envphp.md) verwijzing 0} env.php voor meer informatie.[

## 4. Overschakelmodi

[ de wijzen van de Toepassing ](../../configuration/bootstrap/application-modes.md), die `production` en `developer` omvatten, worden ontworpen om veiligheid te verbeteren en ontwikkeling gemakkelijker te maken. Zoals de namen suggereren, moet u overschakelen op de modus `developer` wanneer u de toepassing uitbreidt of aanpast en overschakelen op de modus `production` wanneer u in een live omgeving werkt.

Het schakelen tussen wijzen is een belangrijke stap om te verifiëren dat uw serverconfiguratie behoorlijk werkt. U kunt tussen wijzen schakelen gebruikend het CLI hulpmiddel:

1. Ga naar de installatiemap.
1. Schakel over naar de modus `production` .

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Vernieuw de browser en controleer of de winkel goed wordt weergegeven.
1. Schakel over naar de modus `developer` .

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Vernieuw de browser en controleer of de winkel goed wordt weergegeven.

## 5. Controleer de opslagplaats

Ga naar de winkel in webbrowser om te controleren of alles werkt.

1. Open een webbrowser en voer op de adresbalk de hostnaam of het IP-adres van de server in. Bijvoorbeeld `http://192.168.33.10` .

   In de volgende afbeelding ziet u een voorbeeldwinkelpagina. Als het als volgt toont, was uw installatie een succes!

   ![ Storefront die een succesvolle installatie ](../../assets/installation/install-success_store.png) verifieert

   Verwijs naar de [ het oplossen van problemensectie ](https://support.magento.com/hc/en-us/articles/360032994352) als de pagina 404 (niet Gevonden) toont of er niet in slaagt om andere activa zoals beelden, CSS, en JS te laden.

1. Probeer een toepassingsmap vanuit een browser te openen. Voeg de mapnaam toe aan de hostnaam of het IP-adres van de server op de adresbalk:

   Als u een bericht van 404 of &quot;Toegang ontkend&quot;ziet, hebt u met succes toegang tot het dossiersysteem beperkt.

   ![ Ontkende Toegang ](../../assets/installation/access-denied.png)
