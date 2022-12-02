---
title: Adobe Commerce 2.3.5-upgradevoorwaarden voor MariaDB
description: Leer hoe u uw Adobe Commerce-database voorbereidt voor een upgrade vanaf Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 071e88c6a07df0f74b6d4b09cce858710c9332cc
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---


# Adobe Commerce 2.3.5-upgradevoorwaarden

In dit artikel wordt uitgelegd hoe u uw database voorbereidt wanneer u een upgrade uitvoert naar Adobe Commerce 2.3.5 vanuit versie 2.3.4 of eerder.

Voor deze upgrade moet het ondersteuningsteam MariaDB upgraden naar de cloudinfrastructuur van MariaDB 10.0 naar 10.2 om te voldoen aan de vereisten voor Adobe Commerce versie 2.3.5 en hoger.

## Betrokken product en versies

Adobe Commerce op cloudinfrastructuur met Adobe Commerce versie 2.3.4 of lager en MariaDB versie 10.0 of lager.

## Uw database voorbereiden voor de upgrade

Voordat het Adobe Commerce-ondersteuningsteam met het upgradeproces begint, moet u uw database voorbereiden door uw databasetabellen te converteren:

- De rijindeling omzetten van `COMPACT` tot `DYNAMIC`
- De opslagengine converteren vanuit `MyISAM` tot `InnoDB`

Houd rekening met het volgende wanneer u de conversie plant en plant:

- Converteren vanuit `COMPACT` tot `DYNAMIC` tabellen kunnen enkele uren duren met een grote database.

- Als u gegevensbeschadiging wilt voorkomen, voltooit u de conversiewerkzaamheden op een livesite niet.

- Voltooi het omzettingswerk tijdens een lage verkeersperiode op uw plaats.

- Ga van site naar [onderhoudsmodus](../../../installation/tutorials/maintenance-mode.md) voordat u de opdrachten uitvoert om databasetabellen om te zetten.

### Opmaak databasetabelrij converteren

U kunt tabellen op één knooppunt in uw cluster omzetten. De wijzigingen worden automatisch overgenomen in de andere serviceknoppen.

1. Gebruik vanuit uw Adobe Commerce op de cloud-infrastructuur SSH om verbinding te maken met knooppunt 1.

1. Meld u aan bij MariaDB.

1. Tabellen identificeren die van compacte naar dynamische indeling moeten worden omgezet.

   ```mysql
   SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
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

### Opmaak databasetabelopslag converteren

U kunt tabellen op één knooppunt in uw cluster omzetten. De wijzigingen worden automatisch overgenomen in de andere serviceknoppen.

Het converteren van de opslagindeling is anders voor Adobe Commerce Starter- en Adobe Commerce Pro-projecten.

- Voor Starter architectuur, gebruik MySQL `ALTER` gebruiken om de indeling te converteren.
- Bij Pro architectuur, gebruik MySQL `CREATE` en `SELECT` opdrachten om een databasetabel te maken met `InnoDB` de gegevens uit de bestaande tabel opslaan en kopiëren naar de nieuwe tabel. Deze methode zorgt ervoor dat de wijzigingen worden gerepliceerd naar alle knooppunten in uw cluster.

**Opmaak voor tabelopslag converteren voor Adobe Commerce Pro-projecten**

1. Tabellen identificeren die worden gebruikt `MyISAM` opslag.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Alle tabellen converteren naar `InnoDB` opslagindeling één voor één.

   - Wijzig de naam van de bestaande tabel om naamconflicten te voorkomen.

      ```mysql
      RENAME TABLE <existing_table> <table_old>;
      ```

   - Een tabel maken die `InnoDB` opslag met behulp van de gegevens uit de bestaande tabel.

      ```mysql
      CREATE TABLE <existing_table> ENGINE=InnoDB SELECT * from <table_old>;
      ```

   - Controleer of de nieuwe tabel alle vereiste gegevens bevat.

   - Verwijder de oorspronkelijke tabel waarvan u de naam hebt gewijzigd.


**Opmaak voor tabelopslag converteren voor Adobe Commerce Starter-projecten**

1. Tabellen identificeren die worden gebruikt `MyISAM` opslag.

   ```mysql
   SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
   ```

1. Tabellen omzetten die `MyISAM` opslag naar `InnoDB` opslag.

   ```mysql
   ALTER TABLE [ table name here ] ENGINE=InnoDB;
   ```

### De databaseconversie controleren

De dag vóór de geplande upgrade naar MariaDB-versie 10.2 controleert u of alle tabellen de juiste rijindeling en opslagengine hebben. De controle wordt vereist omdat de code plaatsingen die nadat u de omzetting wordt gemaakt sommige lijsten zouden kunnen veroorzaken om aan hun originele configuratie worden teruggezet.

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

## Aanvullende informatie

[Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](../planning/database-on-cloud.md)
