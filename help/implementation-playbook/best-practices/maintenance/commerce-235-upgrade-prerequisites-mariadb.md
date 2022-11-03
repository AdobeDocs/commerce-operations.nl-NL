---
title: Adobe Commerce 2.3.5-upgradevoorwaarden voor MariaDB
description: Leer hoe u uw Adobe Commerce-database voorbereidt voor een upgrade vanaf Adobe Commerce 2.3.5.
role: Developer
feature-set: Commerce
feature: Best Practices
source-git-commit: 1abe86197de68336e10c50cab7ad38eebb098aeb
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---


# Adobe Commerce 2.3.5-upgradevoorwaarden

In dit artikel wordt uitgelegd hoe u uw database voorbereidt wanneer u een upgrade uitvoert naar Adobe Commerce 2.3.5 vanuit versie 2.3.4 of eerder.

Voor deze upgrade moet het ondersteuningsteam MariaDB upgraden naar de cloudinfrastructuur van MariaDB 10.0 naar 10.2 om te voldoen aan de vereisten voor Adobe Commerce. Adobe Commerce versie 2.3.5 en hoger.

## Betrokken product en versies

Adobe Commerce op cloudinfrastructuur met Adobe Commerce versie 2.3.4 of lager en MariaDB versie 10.0 of lager.

## Uw database voorbereiden voor de upgrade

Voordat het Adobe Commerce Support-team begint met het upgradeproces, moet u uw database voorbereiden door de indeling voor alle tabellen te converteren vanuit `COMPACT` tot `DYNAMIC`. U moet ook het type opslagengine omzetten van `MyISAM` tot `InnoDB`.

Houd de volgende richtlijnen in mening wanneer u het plan en het programma creeert om het gegevensbestand om te zetten.

- Converteren vanuit `COMPACT` tot `DYNAMIC` tabellen kunnen enkele uren duren met een grote database.

- Voer de conversie niet uit wanneer uw site actief is om gegevensbeschadiging te voorkomen.

- Voltooi het omzettingswerk tijdens een lage verkeersperiode op uw plaats.

- Ga van site naar [onderhoudsmodus](../../../installation/tutorials/maintenance-mode.md) voordat u het `ALTER` opdrachten.

### Databasetabellen converteren

U kunt tabellen op één knooppunt in uw cluster omzetten. De wijzigingen worden overgenomen in de andere kernknooppunten in uw cluster.

1. Gebruik vanuit uw Adobe Commerce op de cloud-infrastructuur SSH om verbinding te maken met knooppunt 1.

1. Meld u aan bij MariaDB.

1. Zet de tabelindeling om.

   - Tabellen identificeren die van compacte naar dynamische indeling moeten worden omgezet.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format 'Compact';
      ```

   - Bepaal de tabelgrootte zodat u de conversiewerkzaamheden kunt plannen.

      ```mysql
      SELECT table_schema as 'Database', table_name AS 'Table', round(((data_length + index_length) / 1024 / 1024), 2) 'Size in MB' FROM information_schema.TABLES ORDER BY (data_length + index_length) DESC;
      ```

      Grotere tabellen duurt langer om te converteren. U zou dienovereenkomstig moeten plannen wanneer het nemen van uw plaats in en uit onderhoudsmodus welke partijen van lijsten in welke orde om te zetten, om de timing van de noodzakelijke onderhoudsvensters te plannen

   - Zet alle tabellen een voor een om in een dynamische indeling.

      ```mysql
      ALTER TABLE [ table name here ] ROW_FORMAT=DYNAMIC;
      ```

1. Werk de engine voor tabelopslag bij.

   - Tabellen identificeren die worden gebruikt `MyISAM` opslag.

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Tabellen omzetten die `MyISAM` opslag naar `InnoDB` opslag.

      ```mysql
      ALTER TABLE [ table name here ] ENGINE=InnoDB;
      ```

1. Controleer de conversie.

   Deze stap wordt vereist omdat de code plaatsingen die nadat u voltooide de omzetting worden gemaakt sommige lijsten zouden kunnen veroorzaken om aan hun originele configuratie worden teruggezet.

   - De dag vóór de geplande upgrade naar MariaDB versie 10.2 meldt u zich aan bij uw database en voert u de query&#39;s uit om de indeling en de opslagengine te controleren.

      ```mysql
      SELECT table_name, row_format FROM information_schema.tables WHERE table_schema=DATABASE() and row_format = 'Compact';
      ```

      ```mysql
      SELECT table_name FROM INFORMATION_SCHEMA.TABLES WHERE engine = 'MyISAM';
      ```

   - Herhaal de stappen om de tabel- en opslagengine te wijzigen als er tabellen zijn teruggezet.

## Aanvullende informatie

[Best practices voor databases voor Adobe Commerce op cloudinfrastructuur](../planning/database-on-cloud.md)
