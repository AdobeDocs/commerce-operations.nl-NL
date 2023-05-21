---
title: Een externe MySQL-databaseverbinding instellen
description: Voer de volgende stappen uit om een externe databaseverbinding te configureren voor installaties op locatie van Adobe Commerce en Magento Open Source.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 0%

---

# Een externe MySQL-databaseverbinding instellen

Soms wilt u de database op een aparte server hosten in plaats van de databaseserver en de webserver op dezelfde computer uit te voeren.

Adobe heeft een manier verstrekt om met een server MySQL op een verschillende machine te verbinden. Vanaf Adobe Commerce en Magento Open Source 2.4.3 kunt u de toepassing ook zodanig configureren dat deze een Amazon Web Services (AWS) Aurora-database zonder codewijzigingen gebruikt.

Aurora is een krachtige, volledig compatibele MySQL-server die op AWS wordt gehost.

## Verbinding maken met een AWS Aurora-database

Het gebruiken van Aurora als gegevensbestand is zo gemakkelijk zoals specificerend het gegevensbestand in de regelmatige configuratie van Adobe Commerce en van de Magento Open Source opstelling, gebruikend de standaardgegevensbestandschakelaar.

Bij uitvoering `bin/magento setup:install`, gebruikt u de Aurora-informatie in de `db-` velden:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

De `db-host` waarde is de Aurora-URL met de `https://` en trailing `:portnumber`  verwijderd.

## Een externe databaseverbinding instellen

>[!NOTE]
>
>Dit is een geavanceerd onderwerp dat slechts door een ervaren netwerkbeheerder of gegevensbestandbeheerder zou moeten worden gebruikt. U moet `root` toegang tot het bestandssysteem en u moet zich als volgt kunnen aanmelden bij MySQL `root`.

### Vereisten

Voordat u begint, moet u:

* [MySQL-server installeren](mysql.md) op de databaseserver.
* [Een database-instantie maken](mysql.md#configuring-the-database-instance) op de databaseserver.
* Installeer de MySQL-client op het Adobe Commerce- of Magento Open Source-webknooppunt. Raadpleeg MySQL-documentatie voor meer informatie.

### Hoge beschikbaarheid

Gebruik de volgende richtlijnen om externe databaseverbindingen te configureren als uw webserver of databaseserver geclusterd is:

* U moet een verbinding voor elke knoop van de Webserver vormen.
* Meestal configureert u een databaseverbinding met het taakverdelingsmechanisme van de database. nochtans, gegevensbestand dat zich groepeert kan complex zijn en het vormen is aan u. Adobe doet geen specifieke aanbevelingen voor gegevensbestand zich groeperen.

   Zie voor meer informatie [MySQL-documentatie](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Verbindingsproblemen oplossen

Als u kwesties hebt die met één van beide gastheer verbinden, pingel eerst de andere gastheer om ervoor te zorgen het bereikbaar is. Mogelijk moet u verbindingen van de ene host naar de andere toestaan door de firewall en de SELinux-regels te wijzigen (als u SELinux gebruikt).

## De externe verbinding maken

Een externe verbinding maken:

1. Op uw databaseserver, als een gebruiker met `root` voorrechten, open uw MySQL configuratiedossier.

   Voer de volgende opdracht in om het bestand te zoeken:

   ```bash
   mysql --help
   ```

   De locatie wordt als volgt weergegeven:

   ```terminal
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >Bij Ubuntu 16 is het pad doorgaans `/etc/mysql/mysql.conf.d/mysqld.cnf`.

1. Het configuratiebestand zoeken naar `bind-address`.

   Wijzig, indien aanwezig, de waarde als volgt.

   Als deze niet bestaat, voegt u deze toe aan de `[mysqld]` sectie.

   ```conf
   bind-address = <ip address of your web node>
   ```

   Zie [MySQL-documentatie](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), vooral als u een gegroepeerde webserver hebt.

1. Sla de wijzigingen in het configuratiebestand op en sluit de teksteditor af.
1. Start de MySQL-service opnieuw:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`
   >[!NOTE]
   >
   >Als MySQL er niet in slaagt om te beginnen, zoek in syslog naar de bron van de kwestie. Los het probleem op met [MySQL-documentatie](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) of een andere gezaghebbende bron.

## Toegang tot een databasegebruiker verlenen

Om uw Webknoop toe te laten om met de gegevensbestandserver te verbinden, moet u een gebruiker van het Webknoopgegevensbestand toegang tot het gegevensbestand op de verre server verlenen.

In dit voorbeeld wordt het `root` databasegebruiker volledige toegang tot de database op de externe host.

Toegang verlenen aan een databasegebruiker:

1. Meld u aan bij de databaseserver.
1. Maak verbinding met de MySQL-database als de `root` gebruiker.
1. Voer de volgende opdracht in:

   ```shell
   GRANT ALL ON <local database name>.* TO <remote web node username>@<remote web node server ip address> IDENTIFIED BY '<database user password>';
   ```

   Bijvoorbeeld:

   ```shell
   GRANT ALL ON magento_remote.* TO dbuser@192.0.2.50 IDENTIFIED BY 'dbuserpassword';
   ```

   >[!NOTE]
   >
   >Als uw webserver geclusterd is, voert u op elke webserver dezelfde opdracht in. U moet voor elke webserver dezelfde gebruikersnaam gebruiken.

## Databasetoegang controleren

Voer op de host van uw webknooppunt de volgende opdracht in om te controleren of de verbinding werkt:

```bash
mysql -u <local database username> -h <database server ip address> -p
```

Als de MySQL monitor als volgt toont, is het gegevensbestand klaar voor Adobe Commerce of Magento Open Source:

```terminal
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Als uw webserver is geclusterd, voert u de opdracht in op elke host van de webserver.

## Adobe Commerce of Magento Open Source installeren

Wanneer u Adobe Commerce of Magento Open Source installeert, moet u het volgende opgeven:

* De basis-URL (ook wel de *opslagadres*) geeft de hostnaam of het IP-adres van het *webknooppunt*
* De host van de database is de *externe databaseserver* IP-adres (of taakverdelingsmechanisme als de databaseserver geclusterd is)
* Gebruikersnaam database is de *lokaal webknooppunt* databasegebruiker waartoe u toegang hebt verleend
* Databasewachtwoord is het wachtwoord van de gebruiker van het lokale webknooppunt
* Databasenaam is de naam van de database op de externe server
