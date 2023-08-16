---
title: MySQL-richtlijnen
description: Voer de volgende stappen uit om MySQL en MariaDB te installeren en te configureren voor installaties op locatie van Adobe Commerce en Magento Open Source.
exl-id: dc5771a8-4066-445c-b1cd-9d5f449ec9e9
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1142'
ht-degree: 0%

---

# Algemene MySQL-richtlijnen

Zie [Systeemvereisten](../../system-requirements.md) voor ondersteunde versies van MySQL.

Adobe _krachtig_ raadt u aan de volgende standaard in acht te nemen wanneer u uw database instelt:

* Adobe Commerce en gebruik van Magento Open Source [MySQL-databasetriggers](https://dev.mysql.com/doc/refman/8.0/en/triggers.html) de toegang tot de database tijdens het opnieuw indexeren te verbeteren. Deze worden gemaakt wanneer de indexeermodus is ingesteld op [schema](../../../configuration/cli/manage-indexers.md#configure-indexers). De toepassing ondersteunt geen aangepaste triggers in de database, omdat aangepaste triggers incompatibiliteiten met toekomstige Adobe Commerce- en Magento Open Source-versies kunnen introduceren.
* Verken uzelf met [Deze potentiële MySQL triggerbeperkingen](https://dev.mysql.com/doc/mysql-reslimits-excerpt/8.0/en/stored-program-restrictions.html) voordat u verdergaat.
* Om uw houding van de gegevensbestandveiligheid te verbeteren, laat toe [`STRICT_ALL_TABLES`](https://dev.mysql.com/doc/refman/5.7/en/sql-mode.html#sqlmode_strict_all_tables) SQL-modus om te voorkomen dat ongeldige gegevenswaarden worden opgeslagen, wat tot ongewenste databaseinteracties kan leiden.
* Adobe Commerce en Magento Open Source doen _niet_ op instructies gebaseerde replicatie van MySQL ondersteunen. Zorg ervoor dat u _alleen_ [op rijen gebaseerde replicatie](https://dev.mysql.com/doc/refman/8.0/en/replication-formats.html).

>[!WARNING]
>
>Adobe Commerce gebruikt momenteel `CREATE TEMPORARY TABLE` instructies binnen transacties, die [incompatibel](https://dev.mysql.com/doc/refman/5.7/en/replication-gtids-restrictions.html) met gegevensbestandimplementaties gebruiken op GTID-Gebaseerde replicatie, zoals [Google Cloud SQL-instanties van de tweede generatie](https://cloud.google.com/sql/docs/features#differences). Bekijk MySQL voor Cloud SQL 8.0 als alternatief.

>[!NOTE]
>
>Als uw Webserver en gegevensbestandserver op verschillende gastheren zijn, voer de taken uit die in dit onderwerp op de gastheer van de gegevensbestandserver worden besproken dan zien [Een externe MySQL-databaseverbinding instellen](mysql-remote.md).

## MySQL installeren op Ubuntu

Adobe Commerce en Magento Open Source 2.4 vereisen een schone installatie van MySQL 8.0. Volg de onderstaande koppelingen voor instructies over het installeren van MySQL op uw computer.

* [Ubuntu](https://ubuntu.com/server/docs/databases-mysql)
* [CentOS](https://dev.mysql.com/doc/refman/8.0/en/linux-installation-yum-repo.html)

Als u grote aantallen producten wilt importeren, kunt u de waarde voor [`max_allowed_packet`](https://dev.mysql.com/doc/refman/5.6/en/program-variables.html) dat groter is dan het gebrek, 16 MB.

>[!NOTE]
>
>De standaardwaarde is van toepassing op Adobe Commerce op cloudinfrastructuur _en_ projecten ter plaatse. Adobe Commerce on cloud Infrastructure Pro-klanten moeten een ondersteuningsticket openen om de `max_allowed_packet` waarde. Adobe Commerce on cloud Infrastructure Starter-klanten kunnen de waarde verhogen door de configuratie in de `/etc/mysql/mysql.cnf` bestand.

Als u de waarde wilt verhogen, opent u de knop `/etc/mysql/mysql.cnf` bestand in een teksteditor en zoek de waarde voor `max_allowed_packet`. Sla uw wijzigingen op in het dialoogvenster `mysql.cnf` bestand, sluit de teksteditor en start MySQL opnieuw (`service mysql restart`).

Om naar keuze de waarde te verifiëren die u plaatst, ga het volgende bevel bij a in `mysql>` prompt:

```sql
SHOW VARIABLES LIKE 'max_allowed_packet';
```

Dan, [De database-instantie configureren](#configuring-the-database-instance).

## Wijzigingen in MySQL 8

Voor Adobe Commerce en Magento Open Source 2.4 hebben we ondersteuning toegevoegd voor MySQL 8.
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
| `modified` | `timestamp` | NEE | | `CURRENT_TIMESTAMP` | `DEFAULT_GENERATED` bij update `CURRENT_TIMESTAMP` |
| `logdate` | `timestamp` | JA | | `NULL` | |
| `lognum` | `smallint unsigned` | NEE | | `0` | |

Met uitzondering van _TINYINT(1)_, moet alle opvulling van gehele getallen (TINYINT > 1, SMALLINT, MEDIUMINT, INT, BIGINT) worden verwijderd uit de `db_schema.xml` bestand.

Zie voor meer informatie [https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/news-8-0-19.html#mysqld-8-0-19-feature).

### Standaardvolgorde OP, gedrag

Vóór 8.0 werden items gesorteerd op de buitenlandse sleutel. De standaardsorteervolgorde is afhankelijk van de gebruikte engine.
Geef altijd een sorteervolgorde op als de code afhankelijk is van een specifieke sortering.

### Vervangen ASC- en DESC-kwalificatietoetsen voor GROUP BY

Vanaf MySQL 8.0.13 is de `ASC` of `DESC` kwalificeertekens voor `GROUP BY` clausules zijn verwijderd. Vraagstukken waarop eerder was vertrouwd `GROUP BY` sorteren kan resultaten opleveren die afwijken van eerdere MySQL-versies. Als u een bepaalde sorteervolgorde wilt maken, geeft u een `ORDER BY` clausule.

## Handel en MySQL 8

Er zijn enkele wijzigingen aangebracht in Adobe Commerce en Magento Open Source om MySQL 8 goed te ondersteunen.

### Werking query en invoegen

Adobe Commerce en Magento Open Source hebben het normale validatiegedrag uitgeschakeld door SQL_MODE=&#39; in te stellen in `/lib/internal/Magento/Framework/DB/Adapter/Pdo/Mysql.php:424.`. Als validatie is uitgeschakeld, is het mogelijk dat MySQL gegevens afkapt. In MySQL is het gedrag Query gewijzigd: `Select * on my_table where IP='127.0.0.1'` retourneert niet langer resultaten omdat het IP-adres nu correct als een tekenreeks wordt beschouwd in plaats van als een geheel getal.

## Upgrade uitvoeren van MySQL 5.7 naar MySQL 8

Als u MySQL van versie 5.7 naar versie 8 correct wilt bijwerken, moet u de volgende stappen uitvoeren:

1. Upgrade Adobe Commerce of Magento Open Source naar 2.4.0. Test alles en controleer of uw systeem werkt zoals u had verwacht.
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

In deze sectie wordt beschreven hoe u een database-instantie voor Adobe Commerce of Magento Open Source kunt maken. Hoewel een nieuwe database-instantie wordt aanbevolen, kunt u desgewenst Adobe Commerce of Magento Open Source met een bestaande database-instantie installeren.

Om een MySQL gegevensbestandinstantie te vormen:

1. Meld u als elke gebruiker aan bij uw databaseserver.
1. Krijg aan een MySQL bevelherinnering:

   ```bash
   mysql -u root -p
   ```

1. Ga MySQL in `root` wachtwoord van de gebruiker wanneer daarom wordt gevraagd.
1. Voer de volgende opdrachten in in de volgorde die wordt weergegeven om een database-instantie met de naam `magento` met gebruikersnaam `magento`:

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

1. Enter `exit` om de bevelherinnering te verlaten.

1. De database controleren:

   ```bash
   mysql -u magento -p
   ```

   Als de MySQL monitorvertoningen, u het gegevensbestand behoorlijk creeerde. Als er een fout wordt weergegeven, herhaalt u de voorgaande opdrachten.

1. Als uw Webserver en gegevensbestandserver op verschillende gastheren zijn, voer de taken uit die in dit onderwerp op de gastheer van de gegevensbestandserver worden besproken dan zien [Een externe MySQL-databaseverbinding instellen](mysql-remote.md).

   Wij adviseren u uw gegevensbestandinstantie zoals aangewezen voor uw zaken vormt. Houd rekening met het volgende wanneer u uw database configureert:

   * Indexeerders hebben hogere eisen `tmp_table_size` en `max_heap_table_size` waarden (bijvoorbeeld 64 M). Als u het `batch_size` kunt u deze waarde samen met de instellingen voor de tabelgrootte aanpassen om de indexprestaties te verbeteren. Zie de [Optimalisatiegids](../../../performance/configuration.md) voor meer informatie .

   * Voor optimale prestaties moet u ervoor zorgen dat alle MySQL- en Adobe Commerce- of Magento Open Source-indextabellen in het geheugen kunnen worden opgeslagen (bijvoorbeeld `innodb_buffer_pool_size`).

   * Het opnieuw indexeren op MariaDB 10.4 neemt meer tijd in vergelijking met andere versies MariaDB of MySQL. Zie [Best practices voor configuratie](../../../performance/configuration.md#indexers).

1. Voor MySQL `TIMESTAMP` velden die de voorkeuren en compositie volgen die worden verwacht door de declaratieve schemaarchitectuur van de toepassing, de systeemvariabele `explicit_defaults_for_timestamp` moet worden ingesteld op `on`.

   Referenties:

   * [MySQL 5.7](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_explicit_defaults_for_timestamp)
   * [MariaDB](https://mariadb.com/kb/en/server-system-variables/#explicit_defaults_for_timestamp)

   Als deze instelling niet is ingeschakeld, `bin/magento setup:db:status` meldt altijd dat de `Declarative Schema is not up to date`.

>[!NOTE]
>
>De `explicit_defaults_for_timestamp` deze instelling is vervangen. Deze instelling bestuurt verouderde TIMESTAMP-gedragingen die in een toekomstige MySQL-release zullen worden verwijderd. Wanneer deze gedragingen worden verwijderd, worden de `explicit_defaults_for_timestamp` de instelling wordt ook verwijderd.

>[!WARNING]
>
>Voor Adobe Commerce over infrastructuurprojecten in de cloud `explicit_defaults_for_timestamp` instellen voor MySQL (MariaDB) wordt standaard ingesteld op _UIT_.

{{$include /help/_includes/maria-db-config.md}}
