---
title: Een externe MySQL-databaseverbinding instellen
description: Voer de volgende stappen uit om een externe databaseverbinding te configureren voor installaties op locatie van Adobe Commerce.
exl-id: 5fe304bd-ff38-4066-a1fd-8937575e4de4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 0%

---

# Een externe MySQL-databaseverbinding instellen

Soms wilt u de database op een aparte server hosten in plaats van de databaseserver en de webserver op dezelfde computer uit te voeren.

Adobe biedt een manier om verbinding te maken met een MySQL-server op een andere computer. Vanaf Adobe Commerce 2.4.3 kunt u de toepassing ook zodanig configureren dat deze een Amazon Web Services (AWS) Aurora-database zonder codewijzigingen gebruikt.

Aurora is een krachtige, volledig compatibele MySQL-server die op AWS wordt gehost.

## Verbinding maken met een AWS Aurora-database

Het gebruiken van Aurora als gegevensbestand is zo gemakkelijk zoals specificerend het gegevensbestand in de regelmatige de opstellingsconfiguratie van Adobe Commerce, gebruikend de standaardgegevensbestandschakelaar.

Wanneer u `bin/magento setup:install` uitvoert, gebruikt u de Aurora-informatie in de `db-` -velden:

```bash
bin/magento setup:install ... --db-host='database-aurora.us-east-1.rds.amazonaws.com' --db-name='magento2' --db-user='username' --db-password='password' ...
```

De waarde `db-host` is de URL van Aurora, waarbij de URL `https://` en de URL aan het einde `:portnumber` zijn verwijderd.

## Een externe databaseverbinding instellen

>[!NOTE]
>
>Dit is een geavanceerd onderwerp dat slechts door een ervaren netwerkbeheerder of gegevensbestandbeheerder zou moeten worden gebruikt. U moet `root` toegang hebben tot het bestandssysteem en u moet zich als `root` kunnen aanmelden bij MySQL.

### Vereisten

Voordat u begint, moet u:

* [ installeer server MySQL ](mysql.md) op de gegevensbestandserver.
* [ creeer een gegevensbestandinstantie ](mysql.md#configuring-the-database-instance) op de gegevensbestandserver.
* Installeer de MySQL-client op het Adobe Commerce-webknooppunt. Raadpleeg MySQL-documentatie voor meer informatie.

### Hoge beschikbaarheid

Gebruik de volgende richtlijnen om externe databaseverbindingen te configureren als uw webserver of databaseserver geclusterd is:

* U moet een verbinding voor elke knoop van de Webserver vormen.
* Typisch, vormt u een gegevensbestandverbinding aan het taakverdelingsmechanisme van het gegevensbestand; nochtans, kan het gegevensbestand zich groeperen complex zijn en het vormen is aan u. De Adobe doet geen specifieke aanbevelingen voor gegevensbestand zich groeperen.

  Voor meer informatie, zie [ documentatie MySQL ](https://dev.mysql.com/doc/refman/5.6/en/mysql-cluster.html).

### Verbindingsproblemen oplossen

Als u kwesties hebt die met één van beide gastheer verbinden, pingel eerst de andere gastheer om ervoor te zorgen het bereikbaar is. Mogelijk moet u verbindingen van de ene host naar de andere toestaan door de firewall en de SELinux-regels te wijzigen (als u SELinux gebruikt).

## De externe verbinding maken

Een externe verbinding maken:

1. Open het MySQL-configuratiebestand op uw databaseserver als een gebruiker met `root` -bevoegdheden.

   Voer de volgende opdracht in om het bestand te zoeken:

   ```bash
   mysql --help
   ```

   De locatie wordt als volgt weergegeven:

   ```
   Default options are read from the following files in the given order:
   /etc/my.cnf /etc/mysql/my.cnf /usr/etc/my.cnf ~/.my.cnf
   ```

   >[!NOTE]
   >
   >In Ubuntu 16 is het pad doorgaans `/etc/mysql/mysql.conf.d/mysqld.cnf` .

1. Zoek in het configuratiebestand naar `bind-address` .

   Wijzig, indien aanwezig, de waarde als volgt.

   Als deze niet bestaat, voegt u deze toe aan de sectie `[mysqld]` .

   ```conf
   bind-address = <ip address of your web node>
   ```

   Zie [ documentatie MySQL ](https://dev.mysql.com/doc/refman/5.6/en/server-options.html), vooral als u een gegroepeerde Webserver hebt.

1. Sla de wijzigingen in het configuratiebestand op en sluit de teksteditor af.
1. Start de MySQL-service opnieuw:

   * CentOS: `service mysqld restart`

   * Ubuntu: `service mysql restart`

   >[!NOTE]
   >
   >Als MySQL er niet in slaagt om te beginnen, zoek in syslog naar de bron van de kwestie. Los de kwestie op gebruikend [ documentatie MySQL ](https://dev.mysql.com/doc/refman/5.6/en/server-options.html#option_mysqld_bind-address) of een andere gebiedende bron.

## Toegang tot een databasegebruiker verlenen

Om uw Webknoop toe te laten om met de gegevensbestandserver te verbinden, moet u een gebruiker van het Webknoopgegevensbestand toegang tot het gegevensbestand op de verre server verlenen.

In dit voorbeeld krijgt de databasegebruiker van `root` volledige toegang tot de database op de externe host.

Toegang verlenen aan een databasegebruiker:

1. Log in bij de databaseserver.
1. Maak als `root` -gebruiker verbinding met de MySQL-database.
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

Als de MySQL-monitor als volgt wordt weergegeven, is de database gereed voor Adobe Commerce:

```
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 213 Server version: 5.6.26 MySQL Community Server (GPL)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its affiliates. Other names may be trademarks of their respective owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Als uw webserver is geclusterd, voert u de opdracht in op elke host van de webserver.

## De Adobe Commerce installeren

Wanneer u Adobe Commerce installeert, moet u het volgende opgeven:

* De basis URL (die ook als *wordt bedoeld opslagadres*) specificeert hostname of IP adres van de *Webknoop*
* De gastheer van het gegevensbestand is het *IP van de 0} verre gegevensbestandserver {adres (of ladingsverdelingsmechanisme als de gegevensbestandserver gegroepeerd is)*
* De gebruikersbenaming van het gegevensbestand is de *lokale knoop van het Web* gegevensbestandgebruiker waaraan u toegang gaf
* Databasewachtwoord is het wachtwoord van de gebruiker van het lokale webknooppunt
* Databasenaam is de naam van de database op de externe server
