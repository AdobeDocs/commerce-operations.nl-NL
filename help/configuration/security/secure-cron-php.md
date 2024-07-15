---
title: Beveiligde uitsnede PHP
description: Beperk wie het bestand cron.php in een browser kan uitvoeren.
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 1%

---

# Beveiligde uitsnede PHP

In dit onderwerp wordt het beveiligen van `pub/cron.php` besproken om te voorkomen dat het wordt gebruikt in een kwaadwillige uitvinding. Als u de uitsnede niet beveiligt, kan elke gebruiker mogelijk de uitsnede uitvoeren om uw Commerce-toepassing aan te vallen.

De bouwbaan stelt verscheidene geplande taken in werking en is een essentieel deel van uw configuratie van Commerce. Geplande taken omvatten, maar zijn niet beperkt tot:

- Opnieuw indexeren
- E-mails genereren
- Nieuwsbrieven genereren
- Sitemaps genereren

>[!INFO]
>
>Verwijs naar [ vormen en in werking stellen kruin ](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) voor meer informatie over cron groepen.

U kunt een uitsnijdtaak op de volgende manieren uitvoeren:

- De opdracht [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) gebruiken via de opdrachtregel of op een tab
- `pub/cron.php?[group=<name>]` openen in een webbrowser

>[!INFO]
>
>U hoeft niets te doen als u de opdracht [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) gebruikt om het uitsnijden uit te voeren, omdat hiervoor een ander proces wordt gebruikt dat al veilig is.

## Beveiligde uitsnede met Apache

In deze sectie wordt beschreven hoe u de uitsnede kunt beveiligen met HTTP Basic-verificatie met Apache. Deze instructies zijn gebaseerd op Apache 2.2 met CentOS 6. Raadpleeg een van de volgende bronnen voor meer informatie:

- [ Apache 2.2 authentificatie en vergunningsleerprogramma ](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [ Apache 2.4 authentificatie en vergunningsleerprogramma ](https://httpd.apache.org/docs/2.4/howto/auth.html)

### Een wachtwoordbestand maken

Uit veiligheidsoverwegingen kunt u het wachtwoordbestand overal vinden, behalve in de hoofdmap van de webserver. In dit voorbeeld wordt het wachtwoordbestand opgeslagen in een nieuwe map.

Voer de volgende opdrachten in als een gebruiker met `root` -rechten:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

Waar `<username>` de gebruiker van de Webserver of een andere gebruiker kan zijn. In dit voorbeeld gebruiken wij de gebruiker van de Webserver, maar de keus van gebruiker is aan u.

Volg de aanwijzingen op het scherm om een wachtwoord voor de gebruiker te maken.

Als u nog een gebruiker aan het wachtwoordbestand wilt toevoegen, voert u de volgende opdracht in als een gebruiker met `root` -rechten:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### Gebruikers toevoegen om een geoorloofde uitsnijdgroep te maken (optioneel)

U kunt toestaan meer dan één gebruiker om te lopen door deze gebruikers aan uw wachtwoorddossier, met inbegrip van een groepsdossier toe te voegen.

Een andere gebruiker toevoegen aan uw wachtwoordbestand:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

Als u een geoorloofde groep wilt maken, maakt u overal buiten de hoofdmap van de webserver een groepsbestand. In het groepsbestand worden de naam van de groep en de gebruikers in de groep opgegeven. In dit voorbeeld is de groepsnaam `MagentoCronGroup` .

```bash
vim /usr/local/apache/password/group
```

Inhoud van het bestand:

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### Uitsnede beveiligen in `.htaccess`

Uitsnijden beveiligen in `.htaccess` -bestand:

1. Meld u aan bij uw Commerce-server als eigenaar van het bestandssysteem of schakel over naar de eigenaar van het bestandssysteem.
1. Open `<magento_root>/pub/.htaccess` in een teksteditor.

   (Omdat `cron.php` zich in de `pub` -map bevindt, bewerkt u alleen dit `.htaccess` .)

1. _toegang van het Gewas voor één of meerdere gebruikers._ Vervang de bestaande `<Files cron.php>` -instructie door:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _toegang van het Gewas voor een groep._ Vervang de bestaande `<Files cron.php>` -instructie door:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. Sla de wijzigingen in `.htaccess` op en sluit de teksteditor af.
1. Ga met [ verder verifiëren kruin veilig ](#verify-cron-is-secure) is.

## Beveiligde uitsnede met Nginx

In deze sectie wordt besproken hoe u de uitsnede kunt beveiligen met behulp van de Nginx-webserver. U moet de volgende taken uitvoeren:

1. Een gecodeerd wachtwoordbestand voor Nginx instellen
1. De configuratie van uw nginx wijzigen om naar het wachtwoordbestand te verwijzen wanneer u `pub/cron.php` opent

### Een wachtwoordbestand maken

Raadpleeg een van de volgende bronnen om een wachtwoordbestand te maken voordat u doorgaat:

- [ hoe te Authentificatie van het Wachtwoord van de opstelling met Nginx op Ubuntu 14.04 (DigitalOcean) ](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [ BasisHTTP Authentificatie met Nginx (hoe te forge) ](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### Uitsnede beveiligen in `nginx.conf.sample`

Commerce beschikt over een geoptimaliseerd voorbeeld-nginx-configuratiebestand uit het vak. We raden u aan het te wijzigen om de afbeelding te beveiligen.

1. Voeg het volgende toe aan uw [`nginx.conf.sample` ](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) dossier:

   ```conf
   #Securing cron
   location ~ cron\.php$ {
      auth_basic "Cron Authentication";
      auth_basic_user_file /etc/nginx/.htpasswd;
   
      try_files $uri =404;
      fastcgi_pass   fastcgi_backend;
      fastcgi_buffers 1024 4k;
   
      fastcgi_read_timeout 600s;
      fastcgi_connect_timeout 600s;
   
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
   }
   ```

1. Start de engine opnieuw:

```bash
systemctl restart nginx
```

1. Ga met [ verder verifiëren kruin veilig ](#verify-cron-is-secure) is.

## Controleren of de uitsnede beveiligd is

De eenvoudigste manier om te controleren of `pub/cron.php` veilig is, is om te controleren of er rijen in de databasetabel van `cron_schedule` worden gemaakt nadat u wachtwoordverificatie hebt ingesteld. In dit voorbeeld worden SQL-opdrachten gebruikt om de database te controleren, maar u kunt elk gewenst gereedschap gebruiken.

>[!INFO]
>
>Het `default` -uitsnede dat u in dit voorbeeld uitvoert, wordt uitgevoerd volgens het schema dat is gedefinieerd in `crontab.xml` . Een aantal snijtaken wordt slechts eenmaal per dag uitgevoerd. De eerste keer dat u de functie voor uitsnijden uitvoert vanuit de browser, wordt de tabel `cron_schedule` bijgewerkt, maar volgende `pub/cron.php` -aanvragen worden uitgevoerd volgens het geconfigureerde schema.

**om te verifiëren kruin veilig** is:

1. Meld u aan bij de database als Commerce-databasegebruiker of als `root` .

   Bijvoorbeeld:

   ```bash
   mysql -u magento -p
   ```

1. Gebruik de Commerce-database:

   ```shell
   use <database-name>;
   ```

   Bijvoorbeeld:

   ```shell
   use magento;
   ```

1. Verwijder alle rijen uit de databasetabel `cron_schedule` :

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. Uitsnijden vanuit een browser uitvoeren:

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   Bijvoorbeeld:

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. Voer desgevraagd de naam en het wachtwoord van een geautoriseerde gebruiker in. In de volgende afbeelding ziet u een voorbeeld.

   ![ Authorizing cron using HTTP Basic ](../../assets/configuration/cron-auth.png)

1. Controleer of er rijen aan de tabel zijn toegevoegd:

   ```shell
   SELECT * from cron_schedule;
   
   mysql> SELECT * from cron_schedule;
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   | schedule_id | job_code                             | status  | messages | created_at        | scheduled_at      | executed_at | finished_at |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   |         1 | catalog_product_outdated_price_values_cleanup | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         2 | sales_grid_order_async_insert             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         3 | sales_grid_order_invoice_async_insert       | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         4 | sales_grid_order_shipment_async_insert      | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         5 | sales_grid_order_creditmemo_async_insert     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         6 | sales_send_order_emails                  | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         7 | sales_send_order_invoice_emails            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         8 | sales_send_order_shipment_emails           | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         9 | sales_send_order_creditmemo_emails         | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        10 | newsletter_send_all                     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:25:00 | NULL      | NULL      |
   |        11 | captcha_delete_old_attempts               | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        12 | captcha_delete_expired_images             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        13 | outdated_authentication_failures_cleanup     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        14 | magento_newrelicreporting_cron            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   14 rows in set (0.00 sec)
   ```

## Uitsnijden uitvoeren vanuit een webbrowser

U kunt uitsnijden op elk gewenst moment uitvoeren met een webbrowser, bijvoorbeeld tijdens het ontwikkelen.

>[!WARNING]
>
>Voer _niet_ kroon in browser in zonder het eerst te beveiligen.

Als u een Apache-webserver gebruikt, moet u de beperking uit het `.htaccess` -bestand verwijderen voordat u het uitsnijden in een browser kunt uitvoeren:

1. Meld u aan bij uw Commerce-server als een gebruiker met schrijfmachtigingen voor het Commerce-bestandssysteem.
1. Open een van de volgende opties in een teksteditor (afhankelijk van het invoerpunt voor Magento):

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. Verwijder of verwijder het volgende:

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   Bijvoorbeeld:

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. Sla de wijzigingen op en sluit de teksteditor af.

   Vervolgens kunt u de bewerking als volgt uitvoeren in een webbrowser:

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

Waarbij:

- `<your hostname or IP>` is de hostnaam of het IP-adres van uw Commerce-installatie
- `<Commerce root>` is de documentafhankelijke relatieve map van de webserver waarop u de Commerce-software hebt geïnstalleerd.

  De exacte URL die u gebruikt om de Commerce-toepassing uit te voeren, is afhankelijk van de configuratie van uw webserver en virtuele host.

- `<group name>` is een geldige naam voor een uitsnijdgroep (optioneel)

Bijvoorbeeld:

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>U moet tweemaal uitsnijden uitvoeren: eerst om taken te ontdekken en opnieuw om de taken zelf uit te voeren. Verwijs naar [ vormen en in werking stellen kruin ](../cli/configure-cron-jobs.md) voor meer informatie over cron groepen.
