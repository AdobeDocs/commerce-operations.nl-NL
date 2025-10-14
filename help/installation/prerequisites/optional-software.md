---
title: Optionele software
description: Meer informatie over optionele software die u kunt installeren voor de ondersteuning van installaties in Adobe Commerce op locatie.
exl-id: 533ff52b-3301-4624-b691-3dfddde6ce0b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Optionele software

Wij adviseren sterk u NTP installeert om ervoor te zorgen dat de cron-verwante taken behoorlijk presteren. (Serverdatums kunnen bijvoorbeeld in het verleden of in de toekomst zijn.)

De andere optionele hulpprogramma&#39;s die in dit onderwerp worden besproken, kunnen u helpen bij uw installatie. Ze zijn echter niet verplicht om Adobe Commerce te installeren of te gebruiken.

## Het installeren van en het Vormen het Protocol van de Tijd van het Netwerk (NTP)

[&#x200B; NTP &#x200B;](https://www.ntp.org/) laat servers toe om hun systeemklokken te synchroniseren gebruikend [&#x200B; globaal beschikbare poolservers &#x200B;](https://www.ntppool.org/en/). Wij adviseren u servers NTP gebruikt u vertrouwt, of zij specifieke hardwareoplossingen uw intern netwerk of externe, openbare servers zijn.

Als u Adobe Commerce op veelvoudige gastheren opstelt, is NTP een eenvoudige manier om hun klokken te waarborgen allen gesynchroniseerd zijn, geen kwestie welke tijdzone de servers binnen zijn. Ook, hangen de op elkaar betrekking hebbende taken (zoals het indexeren en transactie e-mail) van de serverklok af nauwkeurig is.

### NTP installeren en configureren op Ubuntu

Ga het volgende bevel in om NTP te installeren:

```bash
apt-get install ntp
```

Ga met [&#x200B; de poolservers van het Gebruik NTP &#x200B;](#use-ntp-pool-servers) verder.

### NTP installeren en configureren op CentOS

NTP installeren en configureren:

1. Ga het volgende bevel in om de aangewezen software te vinden NTP:

   ```bash
   yum search ntp
   ```

1. Selecteer het pakket dat u wilt installeren. Bijvoorbeeld `ntp.x86_64` .

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

U kunt poolservers selecteren. Als u NTP poolservers gebruikt, adviseert ntp.org u [&#x200B; poolservers &#x200B;](https://www.ntppool.org/en/) gebruikt die dicht bij de tijdzone van uw servers zoals besproken op de [&#x200B; NTP de pagina van het poolproject &#x200B;](https://www.ntppool.org/en/use.html) zijn. Als u een privé server NTP hebt die aan alle gastheren in uw plaatsing beschikbaar is, kunt u die server in plaats daarvan gebruiken.

1. Open `/etc/ntp.conf` in een teksteditor.

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

1. Sla de wijzigingen in `/etc/ntp.conf` op en sluit de teksteditor af.

1. Start de service opnieuw.

   * Ubuntu: `service ntp restart`

   * CentOS: `service ntpd restart`

1. Voer `date` in om de datum van de server te controleren.

   Als de datum onjuist is, zorg ervoor de NTP cliënthaven (typisch, UDP 123) open in uw firewall is.

   Probeer de opdracht `ntpdate _[pool server hostname]_` . Als het ontbreekt, zoek naar de fout het terugkeert.

   Als de rest mislukt, start u de server opnieuw op.

## phpinfo.php maken

In het bestand [`phpinfo.php` &#x200B;](https://www.php.net/manual/en/function.phpinfo.php) wordt een grote hoeveelheid informatie over PHP en zijn extensies weergegeven.

>[!NOTE]
>
>Gebruik `phpinfo.php` in een ontwikkelingssysteem _slechts_. Het kan een veiligheidskwestie in productie zijn.

Voeg de volgende code overal in de hoofdmap van uw webserver toe:

```php
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
```

Voor meer informatie, zie de [&#x200B; phpinfo handpagina &#x200B;](https://www.php.net/manual/en/function.phpinfo.php).

Als u de resultaten wilt bekijken, voert u de volgende URL in het locatie- of adresveld van uw browser in:

```http
http://<web server host or IP>/phpinfo.php
```

Controleer het volgende als een fout van 404 (Niet gevonden) wordt weergegeven:

* Start indien nodig de webserver.
* Zorg ervoor dat uw firewall verkeer op haven 80 toestaat.

  [&#x200B; Hulp voor Ubuntu &#x200B;](https://help.ubuntu.com/community/UFW)

  [&#x200B; Hulp voor CentOS &#x200B;](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html)

## phpMyAdmin

De phpMyAdmin-toepassing is een gebruiksvriendelijk, gratis hulpprogramma voor databasebeheer. U kunt het gebruiken om de inhoud van uw gegevensbestand te controleren en te manipuleren. U moet login aan phpMyAdmin als MySQL gegevensbestandadministratieve gebruiker.

Voor meer informatie over phpMyAdmin, zie de [&#x200B; phpMyAdmin homepage &#x200B;](https://www.phpmyadmin.net/).

Voor meer gedetailleerde informatie over installatie, zie de [&#x200B; phpMyAdmin installatiedocumentatie &#x200B;](https://docs.phpmyadmin.net/en/latest/setup.html#quick-install).

>[!NOTE]
>
>Gebruik phpMyAdmin in een ontwikkelingssysteem _slechts_. Het kan een veiligheidskwestie in productie zijn.

1. Als u phpMyAdmin wilt gebruiken, voert u de volgende opdracht in het adres- of locatieveld van uw browser in:

   ```http
   http://<web server host or IP>/phpmyadmin
   ```

1. Meld u aan met de MySQL-database `root` of de gebruikersnaam en het wachtwoord van de beheerder.
