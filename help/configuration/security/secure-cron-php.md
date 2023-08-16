---
title: Beveiligde uitsnede PHP
description: Beperk wie het bestand cron.php in een browser kan uitvoeren.
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 1%

---

# Beveiligde uitsnede PHP

In dit onderwerp wordt beveiliging besproken `pub/cron.php` om te voorkomen dat het wordt gebruikt in een kwaadwillige uitbuiting. Als u geen kruin beveiligt, kon om het even welke gebruiker potentieel in werking stellen krun om uw toepassing van de Handel aan te vallen.

De gezamenlijke baan stelt verscheidene geplande taken in werking en is een essentieel deel van uw configuratie van de Handel. Geplande taken omvatten, maar zijn niet beperkt tot:

- Opnieuw indexeren
- E-mails genereren
- Nieuwsbrieven genereren
- Sitemaps genereren

>[!INFO]
>
>Zie [Uitsnede configureren en uitvoeren](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) voor meer informatie over kroongroepen .

U kunt een uitsnijdtaak op de volgende manieren uitvoeren:

- Met de [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) gebruiken vanaf de opdrachtregel of op een tab
- Toegang `pub/cron.php?[group=<name>]` in een webbrowser

>[!INFO]
>
>Als u de opdracht [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) gebruiken om een bewerking uit te voeren die al veilig is.

## Beveiligde uitsnede met Apache

In deze sectie wordt beschreven hoe u de uitsnede kunt beveiligen met HTTP Basic-verificatie met Apache. Deze instructies zijn gebaseerd op Apache 2.2 met CentOS 6. Raadpleeg een van de volgende bronnen voor meer informatie:

- [Zelfstudie over verificatie en autorisatie voor Apache 2.2](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Zelfstudie over verificatie en autorisatie voor Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

### Een wachtwoordbestand maken

Uit veiligheidsoverwegingen kunt u het wachtwoordbestand overal vinden, behalve in de hoofdmap van de webserver. In dit voorbeeld wordt het wachtwoordbestand opgeslagen in een nieuwe map.

Voer de volgende opdrachten in als een gebruiker met `root` rechten:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

Wanneer `<username>` Dit kan de gebruiker van de webserver of een andere gebruiker zijn. In dit voorbeeld gebruiken wij de gebruiker van de Webserver, maar de keus van gebruiker is aan u.

Volg de aanwijzingen op het scherm om een wachtwoord voor de gebruiker te maken.

Als u nog een gebruiker aan het wachtwoordbestand wilt toevoegen, voert u de volgende opdracht in als een gebruiker met `root` rechten:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### Gebruikers toevoegen om een geoorloofde uitsnijdgroep te maken (optioneel)

U kunt toestaan meer dan één gebruiker om te lopen door deze gebruikers aan uw wachtwoorddossier, met inbegrip van een groepsdossier toe te voegen.

Een andere gebruiker toevoegen aan uw wachtwoordbestand:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

Als u een geoorloofde groep wilt maken, maakt u overal buiten de hoofdmap van de webserver een groepsbestand. In het groepsbestand worden de naam van de groep en de gebruikers in de groep opgegeven. In dit voorbeeld is de groepsnaam `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

Inhoud van het bestand:

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### Beveiligde uitsnede `.htaccess`

Uitsnede beveiligen `.htaccess` bestand:

1. Meld u aan bij de Commerce-server als of schakel over naar de eigenaar van het bestandssysteem.
1. Openen `<magento_root>/pub/.htaccess` in een teksteditor.

   (omdat `cron.php` bevindt zich in de `pub` directory, deze bewerken `.htaccess` alleen.)

1. _Toegang tot uitsnijden voor een of meer gebruikers._ Bestaande vervangen `<Files cron.php>` richtlijn met de volgende punten :

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _Toegang tot uitsnijden voor een groep._ Bestaande vervangen `<Files cron.php>` richtlijn met de volgende punten :

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. Sla uw wijzigingen op in `.htaccess` en sluit de teksteditor af.
1. Doorgaan met [Controleren of de uitsnede beveiligd is](#verify-cron-is-secure).

## Beveiligde uitsnede met Nginx

In deze sectie wordt besproken hoe u de uitsnede kunt beveiligen met behulp van de Nginx-webserver. U moet de volgende taken uitvoeren:

1. Een gecodeerd wachtwoordbestand voor Nginx instellen
1. De configuratie van de index wijzigen om naar het wachtwoordbestand te verwijzen wanneer u het opent `pub/cron.php`

### Een wachtwoordbestand maken

Raadpleeg een van de volgende bronnen om een wachtwoordbestand te maken voordat u doorgaat:

- [Hoe te om de Authentificatie van het Wachtwoord van de Opstelling met Nginx op Ubuntu 14.04 (DigitaleOceaan) te vestigen](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Standaard HTTP-verificatie met Nginx (howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### Beveiligde uitsnede `nginx.conf.sample`

De handel verstrekt een geoptimaliseerd de configuratiedossier van steekproefNginx uit de doos. We raden u aan het te wijzigen om de afbeelding te beveiligen.

1. Voeg het volgende toe aan uw [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) bestand:

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

1. Doorgaan met [Controleren of de uitsnede beveiligd is](#verify-cron-is-secure).

## Controleren of de uitsnede beveiligd is

De eenvoudigste manier om te controleren of `pub/cron.php` is veilig is om te verifiëren dat het rijen in creeert `cron_schedule` databasetabel nadat u wachtwoordverificatie hebt ingesteld. In dit voorbeeld worden SQL-opdrachten gebruikt om de database te controleren, maar u kunt elk gewenst gereedschap gebruiken.

>[!INFO]
>
>De `default` uitsnijden die u uitvoert in dit voorbeeld, wordt uitgevoerd volgens het schema dat is gedefinieerd in `crontab.xml`. Een aantal snijtaken wordt slechts eenmaal per dag uitgevoerd. De eerste keer dat u de afbeelding uit de browser start, `cron_schedule` tabel wordt bijgewerkt, maar volgende `pub/cron.php` de verzoeken lopen bij het gevormde programma.

**Om te controleren dat de kroon veilig is**:

1. Meld u aan bij de database als gebruiker van de Commerce-database of als `root`.

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

1. Alle rijen verwijderen uit het dialoogvenster `cron_schedule` databasetabel:

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

   ![Draaien autoriseren met HTTP Basic](../../assets/configuration/cron-auth.png)

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
>Do _niet_ Draai de bewerking in een browser uit zonder deze eerst te beveiligen.

Als u een Apache-webserver gebruikt, moet u de beperking verwijderen uit de `.htaccess` voordat u het uitsnijden in een browser kunt uitvoeren:

1. Meld u aan bij uw Commerce-server als een gebruiker met rechten om naar het Commerce-bestandssysteem te schrijven.
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

- `<your hostname or IP>` is hostname of IP adres van uw installatie van de Handel
- `<Commerce root>` is de documentafhankelijke relatieve map van de webserver waarop u de Commerce-software hebt geïnstalleerd

  De exacte URL die u gebruikt om de toepassing van de Handel in werking te stellen hangt van af hoe u uw Webserver en virtuele gastheer vormde.

- `<group name>` is een geldige naam voor een uitsnijdgroep (optioneel)

Bijvoorbeeld:

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>U moet tweemaal uitsnijden uitvoeren: eerst om taken te ontdekken en opnieuw om de taken zelf uit te voeren. Zie [Uitsnede configureren en uitvoeren](../cli/configure-cron-jobs.md) voor meer informatie over kroongroepen .
