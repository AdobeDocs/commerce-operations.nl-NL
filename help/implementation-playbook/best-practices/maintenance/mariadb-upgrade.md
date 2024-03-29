---
title: Adobe Commerce-upgradevoorwaarden voor MariaDB
description: Leer hoe u uw Adobe Commerce-database voorbereidt voor het upgraden van MariaDB vanaf een eerdere versie.
role: Developer
feature: Best Practices
exl-id: b86e471f-e81f-416b-a321-7aa1ac73d27c
source-git-commit: fb449f0ee7d503d0c7ba60bf6bfbe3f528060606
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# Voorwaarden voor upgrades voor MariaDB

Voordat u Adobe Commerce op de cloudinfrastructuur kunt upgraden, moet u mogelijk ook uw databasesoftware bijwerken als u MariaDB gebruikt. Bijvoorbeeld:

- Adobe Commerce 2.4.6 met MariaDB versie 10.5.1 of hoger
- Adobe Commerce 2.3.5 met MariaDB versie 10.3 of lager

## Adobe Commerce 2.4.6

Vanaf MariaDB 10.5.1 worden kolommen met oude tijdelijke indelingen gemarkeerd met een `/* mariadb-5.3 */` opmerking in de uitvoer van de `SHOW CREATE TABLE`, `SHOW COLUMNS`, `DESCRIBE` en in de `COLUMN_TYPE` kolom van de `INFORMATION_SCHEMA.COLUMNS` tabel. [Zie MariaDB-documentatie](https://mariadb.com/kb/en/datetime/#internal-format).

Adobe Commerce kan de datumkolommen niet toewijzen aan een juist gegevenstype vanwege de MariaDB-opmerking. Dit kan leiden tot onverwacht gedrag in aangepaste code.

Om onverwacht gedrag te voorkomen wanneer het bevorderen van MariaDB van oudere versies aan versie 10.6, adviseert de Adobe migrerend de kolommen aan het nieuwe interne formaat.

### Standaardconfiguratie

In MariaDB 10.1.2, werd een nieuw tijdelijk formaat geïntroduceerd van MySQL 5.6. De `mysql56_temporal_format` met een systeemvariabele kan de database de oude datumnotatie automatisch naar de nieuwe converteren wanneer een andere tabel wordt uitgevoerd of een database wordt geïmporteerd. De standaardconfiguratie voor `mysql56_temporal_format` is altijd ingeschakeld op Adobe Commerce op cloudinfrastructuur.

### Datumkolommen migreren

De volgende vraag toont de beïnvloede lijst en de kolommen die moeten worden gemigreerd na bevordering MariaDB aan 10.5.1 of later:

```mysql
SELECT * FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

Voor het migreren van de kolommen naar de nieuwe interne datumnotatie moet de database opnieuw worden geïmporteerd of moet de opgegeven kolom met dezelfde kolomdefinitie worden gewijzigd. De volgende vraag produceert de noodzakelijke veranderlijke vragen:

```mysql
SELECT CONCAT( 'ALTER TABLE `', COALESCE(TABLE_NAME), '`', ' MODIFY ', '`', COALESCE(COLUMN_NAME), '`', ' ', COALESCE(DATA_TYPE), ' ', IF(COALESCE(IS_NULLABLE)='YES','NULL', 'NOT NULL'), IF(COLUMN_DEFAULT IS NOT NULL,CONCAT(' DEFAULT ',COLUMN_DEFAULT),' '), ' ', COALESCE(EXTRA), ' COMMENT \'', COALESCE(COLUMN_COMMENT), '\';' ) as sql_query FROM INFORMATION_SCHEMA.`COLUMNS` WHERE TABLE_SCHEMA = DATABASE() AND COLUMN_TYPE LIKE '%mariadb%';
```

>[!NOTE]
>
>Het is belangrijk dat u de kolommen migreert naar de nieuwe interne datumnotatie _voor_ de nieuwe code implementeren om onverwacht gedrag te voorkomen.

## Adobe Commerce 2.3.5

De MariaDB-service in de cloudinfrastructuur wordt bijgewerkt van versie 10.0 of 10.2 naar versie 10.3, 10.4 of 10.5. Voor MariaDB-versie 10.3 en hoger moet de database de dynamische indeling voor tabelrijen gebruiken en voor Adobe Commerce is het gebruik van de InnoDB-opslagengine voor tabellen vereist. In dit artikel wordt uitgelegd hoe u uw database kunt bijwerken om aan deze MariaDB-vereisten te voldoen.

Nadat u de database hebt voorbereid, dient u een Adobe Commerce-ondersteuningsticket in om de versie van de MariaDB-service op uw cloudinfrastructuur bij te werken voordat u verdergaat met het Adobe Commerce-upgradeproces.

### Uw database voorbereiden voor de upgrade

Voordat het Adobe Commerce-ondersteuningsteam met het upgradeproces begint, moet u uw database voorbereiden door uw databasetabellen te converteren:

- De rijindeling omzetten van `COMPACT` tot `DYNAMIC`
- De opslagengine wijzigen van `MyISAM` tot `InnoDB`

Houd rekening met het volgende wanneer u de conversie plant en plant:

- Converteren vanuit `COMPACT` tot `DYNAMIC` tabellen kunnen enkele uren duren met een grote database.

- Als u gegevensbeschadiging wilt voorkomen, voltooit u de conversiewerkzaamheden op een livesite niet.

- Voltooi het omzettingswerk tijdens een lage verkeersperiode op uw plaats.

- Ga van site naar [onderhoudsmodus](../../../installation/tutorials/maintenance-mode.md) voordat u de opdrachten uitvoert om databasetabellen om te zetten.

#### Opmaak databasetabelrij converteren

U kunt tabellen op één knooppunt in uw cluster omzetten. De wijzigingen worden automatisch overgenomen in de andere serviceknoppen.

1. Gebruik vanuit uw Adobe Commerce op de cloud-infrastructuur SSH voor verbinding met knooppunt 1.

1. Log in bij MariaDB.

1. Tabellen identificeren die van compacte naar dynamische indeling moeten worden omgezet.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Bepaal de tabelgrootte zodat u de conversiewerkzaamheden kunt plannen.

   ```mysql
   SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
   ```

   Grotere tabellen duurt langer om te converteren. Controleer de tabellen en batchgeer het conversiewerk op prioriteit en op tabelgrootte om de vereiste onderhoudsvensters te plannen.

1. Zet alle tabellen een voor een om in een dynamische indeling.

   ```mysql
   ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
   ```

#### Opmaak databasetabelopslag converteren

U kunt tabellen op één knooppunt in uw cluster omzetten. De wijzigingen worden automatisch overgenomen in de andere serviceknoppen.

Het converteren van de opslagindeling is anders voor Adobe Commerce Starter- en Adobe Commerce Pro-projecten.

- Voor Starter architectuur, gebruik MySQL `ALTER` gebruiken om de indeling te converteren.
- Bij Pro architectuur, gebruik MySQL `CREATE` en `SELECT` opdrachten om een databasetabel te maken met `InnoDB` de gegevens uit de bestaande tabel opslaan en kopiëren naar de nieuwe tabel. Deze methode zorgt ervoor dat de wijzigingen worden gerepliceerd naar alle knooppunten in uw cluster.

**Opmaak voor tabelopslag converteren voor Adobe Commerce Pro-projecten**

1. Tabellen identificeren die `MyISAM` opslag.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Alle tabellen converteren naar `InnoDB` opslagindeling één voor één.

   - Wijzig de naam van de bestaande tabel om naamconflicten te voorkomen.

     ```mysql
     RENAME TABLE <existing_table> <table_old>;
     ```

   - Een tabel maken die `InnoDB` opslag met de gegevens uit de bestaande tabel.

     ```mysql
     CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
     ```

   - Controleer of de nieuwe tabel alle vereiste gegevens bevat.

   - Verwijder de oorspronkelijke tabel waarvan u de naam hebt gewijzigd.


**Opmaak voor tabelopslag converteren voor Adobe Commerce Starter-projecten**

1. Tabellen identificeren die `MyISAM` opslag.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Tabellen omzetten die `MyISAM` opslag naar `InnoDB` opslag.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

#### De databaseconversie controleren

De dag vóór de geplande upgrade naar MariaDB-versie 10.3, 10.4 of 10.6 controleert u of alle tabellen de juiste rijindeling en opslagengine hebben. De controle wordt vereist omdat de code plaatsingen die nadat u de omzetting wordt gemaakt sommige lijsten zouden kunnen veroorzaken om aan hun originele configuratie worden teruggezet.

1. Meld u aan bij uw database.

1. Controleren op alle tabellen die nog steeds de `COMPACT` rijindeling.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
   ```

1. Controleren op alle tabellen die nog steeds gebruikmaken van de `MyISAM` opslagindeling

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Herhaal de stappen om de indeling van de tabelrij en de opslagengine te wijzigen als er tabellen zijn teruggezet.

### De opslagengine wijzigen

Zie [MyISAM-tabellen converteren naar InnoDB](../planning/database-on-cloud.md).
