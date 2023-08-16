---
title: Optionele software
description: Meer informatie over optionele software die u kunt installeren voor ondersteuning van installaties op locatie van Adobe Commerce en Magento Open Source.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Optionele software

Wij adviseren sterk u NTP installeert om ervoor te zorgen dat de cron-verwante taken behoorlijk presteren. (Serverdatums kunnen bijvoorbeeld in het verleden of in de toekomst zijn.)

De andere optionele hulpprogramma&#39;s die in dit onderwerp worden besproken, kunnen u helpen bij uw installatie. Ze zijn echter niet verplicht om Adobe Commerce of Magento Open Source te installeren of te gebruiken.

## Het installeren van en het Vormen het Protocol van de Tijd van het Netwerk (NTP)

[NTP](https://www.ntp.org/) laat servers toe om hun systeemklokken te synchroniseren gebruikend [wereldwijd beschikbare poolservers](https://www.ntppool.org/en/). Wij adviseren u servers NTP gebruikt u vertrouwt, of zij specifieke hardwareoplossingen uw intern netwerk of externe, openbare servers zijn.

Als u Adobe Commerce of Magento Open Source op veelvoudige gastheren opstelt, is NTP een eenvoudige manier om hun klokken te waarborgen allen gesynchroniseerd zijn, geen kwestie welke tijdzone de servers binnen zijn. Ook, hangen de op elkaar betrekking hebbende taken (zoals het indexeren en transactie e-mail) van de serverklok af nauwkeurig is.

### NTP installeren en configureren op Ubuntu

Ga het volgende bevel in om NTP te installeren:

```bash
apt-get install ntp
```

Doorgaan met [NTP-poolservers gebruiken](#use-ntp-pool-servers).

### NTP installeren en configureren op CentOS

NTP installeren en configureren:

1. Ga het volgende bevel in om de aangewezen software te vinden NTP:

   ```bash
   yum search ntp
   ```

1. Selecteer het pakket dat u wilt installeren. Bijvoorbeeld, `ntp.x86_64`.

1. Installeer het pakket.

   ```bash
   yum -y install ntp.x86_64
   ```

1. Ga het volgende bevel in zodat NTP begint wanneer de server begint.

   ```bash
   chkconfig ntpd on
   ```

1. Ga verder met de volgende sectie.

### NTP-poolservers gebruiken

U kunt poolservers selecteren. Als u NTP-poolservers gebruikt, raadt ntp.org u aan [poolservers](https://www.ntppool.org/en/) die dicht bij de tijdzone van uw servers zoals die op [Projectpagina NTP-pool](https://www.ntppool.org/en/use.html). Als u een privé server NTP hebt die aan alle gastheren in uw plaatsing beschikbaar is, kunt u die server in plaats daarvan gebruiken.

1. Openen `/etc/ntp.conf` in een teksteditor.

1. Zoek naar lijnen gelijkend op het volgende:

   ```conf
   server 0.centos.pool.ntp.org
   server 1.centos.pool.ntp.org
   server 2.centos.pool.ntp.org
   ```

1. Vervang die lijnen of voeg extra lijnen toe die uw NTP poolserver of andere servers NTP specificeren. Het is een goed idee om meer dan één te specificeren.

1. Een voorbeeld van het gebruiken van drie op Verenigde Staten-Gebaseerde servers NTP volgt:

   ```conf
   server 0.us.pool.ntp.org
   server 1.us.pool.ntp.org
   server 2.us.pool.ntp.org
   ```

1. Sla uw wijzigingen op in `/etc/ntp.conf` en sluit de teksteditor af.

1. Start de service opnieuw.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Enter `date` om de datum van de server te controleren.

   Als de datum onjuist is, zorg ervoor de NTP cliënthaven (typisch, UDP 123) open in uw firewall is.

   Probeer de `ntpdate _[pool server hostname]_` gebruiken. Als het ontbreekt, zoek naar de fout het terugkeert.

   Als de rest mislukt, start u de server opnieuw op.

## phpinfo.php maken

De [`phpinfo.php`](https://www.php.net/manual/en/function.phpinfo.php) bestand bevat een grote hoeveelheid informatie over PHP en zijn extensies.

>[!NOTE]
>
>Gebruiken `phpinfo.php` in een ontwikkelingssysteem _alleen_. Het kan een veiligheidskwestie in productie zijn.

Voeg de volgende code overal in de hoofdmap van uw webserver toe:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Zie de klasse [pagina met fpinfo-handleiding](https://www.php.net/manual/en/function.phpinfo.php).

Als u de resultaten wilt bekijken, voert u de volgende URL in het locatie- of adresveld van uw browser in:

```http
http://<web server host or IP>/phpinfo.php
```

Controleer het volgende als een fout van 404 (Niet gevonden) wordt weergegeven:

* Start indien nodig de webserver.
* Zorg ervoor dat uw firewall verkeer op haven 80 toestaat.

  [Help voor Ubuntu](https://help.ubuntu.com/community/UFW)

  [Help voor CentOS](https://wiki.centos.org/HowTos/Network/IPTables)

## phpMyAdmin

De phpMyAdmin-toepassing is een gebruiksvriendelijk, gratis hulpprogramma voor databasebeheer. U kunt het gebruiken om de inhoud van uw gegevensbestand te controleren en te manipuleren. U moet login aan phpMyAdmin als MySQL gegevensbestandadministratieve gebruiker.

Voor meer informatie over phpMyAdmin, zie [phpMyAdmin-startpagina](https://www.phpmyadmin.net/).

Voor meer gedetailleerde informatie over installatie, zie [PHPMyAdmin-installatiedocumentatie](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>PHPMyAdmin gebruiken in een ontwikkelingssysteem _alleen_. Het kan een veiligheidskwestie in productie zijn.

1. Als u phpMyAdmin wilt gebruiken, voert u de volgende opdracht in het adres- of locatieveld van uw browser in:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Meld u aan met uw MySQL-database wanneer hierom wordt gevraagd `root` of de gebruikersnaam en het wachtwoord van de beheerder.
