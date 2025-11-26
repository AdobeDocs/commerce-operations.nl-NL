---
title: MySQL-richtlijnen
description: Voer de volgende stappen uit om MySQL en MariaDB te installeren en te configureren voor installaties op locatie van Adobe Commerce.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 2d17da1f8cbda1462839ad2fa3ea569833443827
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# Algemene MySQL-richtlijnen

Zie {de Vereisten van het 0} Systeem [&#x200B; voor gesteunde versies van MySQL.](../../system-requirements.md)

Adobe _adviseert sterk_ u de volgende norm waarneemt wanneer u opstelling uw gegevensbestand:

* Adobe Commerce gebruikt [&#x200B; MySQL gegevensbestandtrekkers &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) om gegevensbestandtoegang tijdens het opnieuw indexeren te verbeteren. Deze worden gecreeerd wanneer de indexeerwijze aan [&#x200B; programma &#x200B;](../../../configuration/cli/manage-indexers.md#configure-indexers) wordt geplaatst. De toepassing ondersteunt geen aangepaste triggers in de database omdat aangepaste triggers incompatibiliteiten met toekomstige Adobe Commerce-versies kunnen introduceren.
* Verken zich met [&#x200B; deze potentiële MySQL trekkerbeperkingen &#x200B;](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) alvorens u verdergaat.
* Om uw houding van de gegevensbestandveiligheid te verbeteren, laat [`STRICT_ALL_TABLES` &#x200B;](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL wijze toe om het opslaan van ongeldige gegevenswaarden te verhinderen, die ongewenste gegevensbestandinteractie zou kunnen veroorzaken.
* Adobe Commerce steunt __ geen op verklaring-gebaseerde replicatie MySQL. Zorg ervoor u _slechts_ [&#x200B; op rij-gebaseerde replicatie &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html) gebruikt.

>[!WARNING]
>
>Adobe Commerce gebruikt momenteel `CREATE TEMPORARY TABLE` verklaringen binnen transacties, die [&#x200B; onverenigbaar &#x200B;](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) met gegevensbestandimplementaties zijn gebruiken GTID-Gebaseerde replicatie, zoals [&#x200B; SQL van de Wolk van Google tweede generatie instanties &#x200B;](https://cloud.google.com/sql/docs/features#differences). Bekijk MySQL voor Cloud SQL 8.0 als alternatief.

>[!NOTE]
>
>Als uw Webserver en gegevensbestandserver op verschillende gastheren zijn, voer de taken uit die in dit onderwerp op de gastheer van de gegevensbestandserver dan worden besproken [&#x200B; Opstelling een verre MySQL gegevensbestandverbinding &#x200B;](mysql-remote.md).

## MySQL installeren op Ubuntu

Adobe Commerce 2.4 vereist een schone installatie van MySQL 8.0. Volg de onderstaande koppelingen voor instructies over het installeren van MySQL op uw computer.

* [&#x200B; Ubuntu &#x200B;](https://ubuntu.com/server/docs/databases-mysql)
* [&#x200B; CentOS &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Als u verwacht om grote aantallen producten in te voeren, kunt u de waarde voor [`max_allowed_packet` &#x200B;](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) verhogen die groter is dan het gebrek, 16 MB.

>[!NOTE]
>
>De standaardwaarde is op Adobe Commerce op wolkeninfrastructuur _en_ op-gebouwprojecten van toepassing. Adobe Commerce on cloud Infrastructure Pro-klanten moeten een ondersteuningsticket openen om de `max_allowed_packet` -waarde te verhogen. Adobe Commerce on cloud Infrastructure Starter-klanten kunnen de waarde verhogen door de configuratie in het `/etc/mysql/mysql.cnf` -bestand bij te werken.

Als u de waarde wilt verhogen, opent u het `/etc/mysql/mysql.cnf` -bestand in een teksteditor en zoekt u de waarde voor `max_allowed_packet` . Sla de wijzigingen in het `mysql.cnf` -bestand op, sluit de teksteditor en start MySQL opnieuw ( `service mysql restart` ).

Als u optioneel de waarde wilt verifiëren die u instelt, voert u de volgende opdracht in bij een `mysql>` -prompt:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Dan, [&#x200B; vorm de gegevensbestandinstantie &#x200B;](#configuring-the-database-instance).

## Wijzigingen in MySQL 8

Voor Adobe Commerce 2.4 hebben we ondersteuning toegevoegd voor MySQL 8.
Deze sectie beschrijft belangrijke veranderingen in MySQL 8 die de ontwikkelaars zich van bewust zouden moeten zijn.

### Verwijderde breedte voor typen gehele getallen (opvulling)

De specificatie van de vertoningsbreedte voor geheelgegevenstypes (TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT) is verouderd in MySQL 8.0.17. Instructies die definities van gegevenstypen in de uitvoer bevatten, geven niet langer de weergavebreedte voor typen gehele getallen weer, behalve voor TINYINT(1). MySQL-connectors gaan ervan uit dat TINYINT(1)-kolommen als BOOLEAN-kolommen zijn ontstaan. Deze uitzondering stelt hen in staat om die veronderstelling te blijven maken.

#### Voorbeeld

Beschrijf admin_user op mysql 8.19

| Veld | Type | Null | Sleutel | Standaard | Extra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| user\_id | `int unsigned` | NEE | PRI | `NULL` | `auto_increment` |
| `firstname` | `varchar(32)` | JA | | `NULL` | |
| `lastname` | `varchar(32`) | JA | | `NULL` | |
| `email` | `varchar(128)` | JA | | `NULL` | |
| `username` | `varchar(40)` | JA | UNI | `NULL` | |
| `password` | `varchar(255)` | NEE | | `NULL` | |
| `created` | `timestamp` | NEE | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` |
| `modified` | `timestamp` | NEE | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` bij bijwerken `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | JA | | `NULL` | |
| `lognum` | `smallint unsigned` | NEE | | `0` | |

Behalve _TINYINT (1)_, zou al geheel het opvullen (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) uit het `db_schema.xml` dossier moeten worden verwijderd.

Voor meer informatie, zie [&#x200B; https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature &#x200B;](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Standaardvolgorde OP, gedrag

Vóór 8.0 werden items gesorteerd op de buitenlandse sleutel. De standaardsorteervolgorde is afhankelijk van de gebruikte engine.
Geef altijd een sorteervolgorde op als de code afhankelijk is van een specifieke sortering.

### Vervangen ASC- en DESC-kwalificatietoetsen voor GROUP BY

Vanaf MySQL 8.0.13 zijn de afgekeurde `ASC` - of `DESC` kwalificfiers for `GROUP BY` -componenten verwijderd. Zoekopdrachten die eerder op `GROUP BY` sorteren zijn gebaseerd, kunnen resultaten opleveren die afwijken van eerdere MySQL-versies. Geef een `ORDER BY` -component op om een bepaalde sorteervolgorde te maken.

## Commerce en MySQL 8

Er zijn enkele wijzigingen aangebracht in Adobe Commerce om MySQL 8 correct te ondersteunen.

### Werking query en invoegen

Adobe Commerce heeft het normale validatiegedrag uitgeschakeld door SET SQL_MODE=&#39;&#39; in te stellen in `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.` . Als validatie is uitgeschakeld, is het mogelijk dat MySQL gegevens afkapt. In MySQL is het gedrag Query gewijzigd: `Select * on my_table where IP='127.0.0.1'` retourneert niet langer de resultaten omdat het IP-adres nu correct als een tekenreeks wordt beschouwd in plaats van als een geheel getal.

## Upgrade uitvoeren van MySQL 5.7 naar MySQL 8

Als u MySQL van versie 5.7 naar versie 8 correct wilt bijwerken, moet u de volgende stappen uitvoeren:

1. Upgrade Adobe Commerce naar 2.4.0.
Test alles en controleer of uw systeem werkt zoals u had verwacht.
1. Onderhoudsmodus inschakelen:

   ```bash
   bin/magento maintenance:enable
   ```

1. Maak een databaseback-up:

   ```bash
   bin/magento setup:backup --db
   ```

1. Werk MySQL bij naar versie 8.
1. Importeer de back-upgegevens in MySQL.
1. De cache reinigen:

   ```bash
   bin/magento cache:clean
   ```

1. Onderhoudsmodus uitschakelen:

   ```bash
   bin/magento maintenance:disable
   ```

## De database-instantie configureren

In deze sectie wordt besproken hoe u een database-instantie voor Adobe Commerce kunt maken. Hoewel een nieuwe database-instantie wordt aanbevolen, kunt u desgewenst Adobe Commerce met een bestaande database-instantie installeren.

Om een MySQL gegevensbestandinstantie te vormen:

1. Meld u als elke gebruiker aan bij uw databaseserver.
1. Krijg aan een MySQL bevelherinnering:

   ```bash
   mysql -u root -p
   ```

1. Voer het gebruikerswachtwoord van MySQL `root` in wanneer hierom wordt gevraagd.
1. Voer de volgende opdrachten in de volgorde in die wordt weergegeven om een database-instantie met de naam `magento` met gebruikersnaam `magento` te maken:

   ```sql
   create database magento;
   ```

   ```sql
   create user 'magento'@'localhost' IDENTIFIED BY 'magento';
   ```

   ```sql
   GRANT ALL ON magento.* TO 'magento'@'localhost';
   ```

   ```sql
   flush privileges;
   ```

1. Ga `exit` in om de bevelherinnering weg te gaan.

1. De database controleren:

   ```bash
   mysql -u magento -p
   ```

   Als de MySQL monitorvertoningen, u het gegevensbestand behoorlijk creeerde. Als er een fout wordt weergegeven, herhaalt u de voorgaande opdrachten.

1. Als uw Webserver en gegevensbestandserver op verschillende gastheren zijn, voer de taken uit die in dit onderwerp op de gastheer van de gegevensbestandserver dan worden besproken [&#x200B; Opstelling een verre MySQL gegevensbestandverbinding &#x200B;](mysql-remote.md).

   Wij adviseren u uw gegevensbestandinstantie zoals aangewezen voor uw zaken vormt. Houd rekening met het volgende wanneer u uw database configureert:

   * Indexeerders vereisen hogere waarden `tmp_table_size` en `max_heap_table_size` (bijvoorbeeld 64 M). Als u de parameter `batch_size` configureert, kunt u die waarde samen met de instellingen voor de tabelgrootte aanpassen om de indexeerprestaties te verbeteren. Verwijs naar de [&#x200B; Gids van de Optimalisering &#x200B;](../../../performance/configuration.md) voor meer informatie.

   * Voor optimale prestaties moet u ervoor zorgen dat alle MySQL- en Adobe Commerce-indextabellen in het geheugen kunnen worden opgeslagen (bijvoorbeeld `innodb_buffer_pool_size` configureren).

   * Het opnieuw indexeren op MariaDB 10.4 neemt meer tijd in vergelijking met andere versies MariaDB of MySQL. Zie [&#x200B; beste praktijken van de Configuratie &#x200B;](../../../performance/configuration.md#indexers).

1. Als u wilt dat MySQL `TIMESTAMP` -velden de voorkeuren en compositie volgen die worden verwacht door de declaratieve schemaarchitectuur van de toepassing, moet de systeemvariabele `explicit_defaults_for_timestamp` worden ingesteld op `on` .

   Referenties:

   * [&#x200B; MySQL 5.7 &#x200B;](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [&#x200B; MariaDB &#x200B;](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Als deze instelling niet is ingeschakeld, rapporteert `bin/magento setup:db:status` altijd dat de `Declarative Schema is not up to date` .

>[!NOTE]
>
>De instelling `explicit_defaults_for_timestamp` is vervangen. Deze instelling bestuurt verouderde TIMESTAMP-gedragingen die in een toekomstige MySQL-release zullen worden verwijderd. Wanneer deze gedragingen worden verwijderd, wordt de instelling `explicit_defaults_for_timestamp` ook verwijderd.

>[!WARNING]
>
>Voor Adobe Commerce op de projecten van de wolkeninfrastructuur, het `explicit_defaults_for_timestamp` plaatsen voor MySQL (MariaDB) gebreken aan _VAN_.

{{$include /help/_includes/maria-db-config.md}}

<!-- Last updated from includes: 2025-11-25 11:39:51 -->
