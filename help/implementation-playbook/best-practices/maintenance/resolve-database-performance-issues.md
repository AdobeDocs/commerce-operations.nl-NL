---
title: Aanbevolen procedures om prestatieproblemen met databases op te lossen
description: Leer hoe u databaseproblemen kunt verhelpen die de prestaties vertragen op Adobe Commerce-sites die worden geïmplementeerd op een cloudinfrastructuur.
role: Developer, Admin
feature: Best Practices
exl-id: e40e0564-a4eb-43a8-89dd-9f6c5cedb4a7
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

<!--Consider moving this topic to the Maintenance section-->

# Aanbevolen procedures om prestatieproblemen met databases op te lossen

In dit artikel wordt besproken hoe u databaseproblemen kunt oplossen die de databaseprestaties op Adobe Commerce op cloudinfrastructuursites negatief beïnvloeden.

## Betrokken versies

Adobe Commerce over cloudinfrastructuur

## Langdurige query&#39;s identificeren en oplossen

Bepaal of u langzaam lopende vragen MySQL hebt. Afhankelijk van uw Adobe Commerce-plan voor cloudinfrastructuur en dus de beschikbaarheid van tools, kunt u het volgende doen.

### Databasequery&#39;s analyseren met MySQL

Met MySQL kunt u langdurige query&#39;s op elk Adobe Commerce-infrastructuurproject identificeren en oplossen.

1. Voer de instructie [`SHOW \[FULL\] PROCESSLIST` ](https://dev.mysql.com/doc/refman/8.0/en/show-processlist.html) uit.
1. Als u lange lopende vragen ziet, looppas [ MySQL `EXPLAIN` en `EXPLAIN ANALYZE` ](https://mysqlserverteam.com/mysql-explain-analyze/) voor elk van hen, om te weten te komen wat tot de vraaglooppas voor een lange tijd maakt.
1. Gebaseerd op de gevonden kwesties, onderneem stappen om de vraag te bevestigen zodat loopt het sneller.

### Vragen analyseren met de Percona Toolkit (alleen voor Pro-architectuur)

Als uw project van Adobe Commerce op Pro architectuur wordt opgesteld, kunt u Toolkit Percona gebruiken om vragen te analyseren.

1. Voer de opdracht `pt-query-digest --type=slowlog` uit op basis van MySQL langzame querylogs.
   * Zie **[!UICONTROL Log locations > Service Logs]** (https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/test/log-locations#service-logs) in de ontwikkelaarsdocumentatie voor informatie over de locatie van de trage querylogboeken.
   * Zie [ Toolkit Percona > pt-vraag-samenvatting ](https://www.percona.com/doc/percona-toolkit/LATEST/pt-query-digest.html#pt-query-digest) documentatie.
1. Gebaseerd op de gevonden kwesties, onderneem stappen om de vraag te bevestigen zodat loopt het sneller.

## Controleren of alle tabellen een primaire sleutel hebben

Het bepalen van primaire sleutels is een vereiste voor goed gegevensbestand en lijstontwerp. Met primaire sleutels kunt u een enkele rij in een tabel op unieke wijze identificeren.

Als u tabellen zonder een primaire sleutel hebt, gebruikt de standaard database-engine voor Adobe Commerce (InnoDB) de eerste unieke niet-null-sleutel als primaire sleutel. Als er geen unieke sleutel beschikbaar is, maakt InnoDB een verborgen primaire sleutel (6 bytes). Het probleem met een impliciet gedefinieerde primaire sleutel is dat u er geen controle over hebt. Bovendien wordt de impliciete waarde globaal toegewezen voor alle tabellen zonder primaire sleutels. Deze configuratie kan conflicten veroorzaken als u gelijktijdig schrijft over deze lijsten uitvoert. Dit kan prestatieproblemen veroorzaken omdat de tabellen ook de algemene increment voor de index van verborgen primaire sleutels delen.

Vermijd deze kwesties door een primaire sleutel voor om het even welke lijsten te bepalen die geen hebben.

### Tabellen identificeren en bijwerken zonder primaire sleutel

1. Tabellen zonder primaire sleutel identificeren met de volgende SQL-query:

   ```sql
   SELECT table_catalog, table_schema, table_name, engine FROM information_schema.tables        WHERE (table_catalog, table_schema, table_name) NOT IN (SELECT table_catalog, table_schema, table_name FROM information_schema.table_constraints  WHERE constraint_type = 'PRIMARY KEY') AND table_schema NOT IN ('information_schema', 'pg_catalog');    
   ```

1. Voor elke tabel waarin een primaire sleutel ontbreekt, voegt u een primaire sleutel toe door het declaratieve schema `db_schema.xml` bij te werken met een knooppunt dat lijkt op het volgende:

   ```html
   <constraint xsi:type="primary" referenceId="PRIMARY">         <column name="id_column"/>     </constraint>    
   ```

   Wanneer u het knooppunt toevoegt, vervangt u de variabelen `referenceID` en `column name` door uw aangepaste waarden.

Voor meer informatie, zie [ declaratief schema ](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) in onze ontwikkelaarsdocumentatie vormen.

## Dubbele indexen identificeren en verwijderen

Identificeer om het even welke dubbele indexen in uw gegevensbestand en verwijder hen.

### Controleren op dubbele indexen

Voer de volgende SQL-query uit om te controleren op dubbele indexen op de architectuur van de Pro- of Starter-cloud.

```sql
SELECT s.INDEXED_COL,GROUP_CONCAT(INDEX_NAME) FROM (SELECT INDEX_NAME,GROUP_CONCAT(CONCAT(TABLE_NAME,'.',COLUMN_NAME) ORDER BY CONCAT(SEQ_IN_INDEX,COLUMN_NAME)) 'INDEXED_COL' FROM INFORMATION_SCHEMA.STATISTICS WHERE TABLE_SCHEMA = 'db?' GROUP BY INDEX_NAME)as s GROUP BY INDEXED_COL HAVING COUNT(1)>1
```

De vraag keert de kolomnamen en de namen van om het even welke dubbele indexen terug.

Pro-architectuurhandelaren kunnen de controle ook uitvoeren met de opdracht Percona Toolkit `[pt-duplicate-key checker](https://www.percona.com/doc/percona-toolkit/LATEST/pt-duplicate-key-checker.html%C2%A0)` .

### Dubbele indexen verwijderen

Gebruik de SQL [ Verklaring van de INDEX van de DROP ](https://dev.mysql.com/doc/refman/8.0/en/drop-index.html) om dubbele indexen te verwijderen.

```SQL
DROP INDEX
```

## Aanvullende informatie

[Best practices voor databaseconfiguratie voor cloudimplementatie](../planning/database-on-cloud.md)
