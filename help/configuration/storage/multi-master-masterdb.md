---
title: Automatisch hoofddatabases configureren
description: Zie begeleiding bij het automatisch vormen van de gespleten gegevensbestandoplossing.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Automatisch hoofddatabases configureren

{{ee-only}}

{{deprecate-split-db}}

Dit onderwerp bespreekt hoe te beginnen met de gespleten gegevensbestandoplossing door:

1. Adobe Commerce installeren met één hoofddatabase (genaamd `magento`)
1. Het creëren van twee extra hoofdgegevensbestanden voor checkout en OMS (genoemd `magento_quote` en `magento_sales`)
1. Adobe Commerce configureren voor het gebruik van de databases voor uitchecken en verkopen

>[!INFO]
>
>Deze gids veronderstelt dat alle drie gegevensbestanden op de zelfde gastheer zoals de toepassing van de Handel zijn en dat zij worden genoemd `magento`, `magento_quote`, en `magento_sales`. Nochtans, is de keus van waar te om van de gegevensbestanden de plaats te bepalen en wat zij worden genoemd aan u. We hopen dat onze voorbeelden de instructies makkelijker te volgen maken.

## De Adobe Commerce-software installeren

U kunt gesplitste databases op elk gewenst moment inschakelen nadat u de Adobe Commerce-software hebt geïnstalleerd. Met andere woorden, u kunt gesplitste databases toevoegen aan een Adobe Commerce-systeem dat al gegevens voor kassa en bestelling bevat. Gebruik de instructies in Adobe Commerce README of in de [installatiegids](../../installation/overview.md) om de Adobe Commerce-software te installeren met één hoofddatabase.

## Extra hoofddatabases instellen

Maak als volgt uitcheckdatabases en OMS-hoofddatabases:

1. Meld u als elke gebruiker aan bij uw databaseserver.
1. Ga het volgende bevel in om aan een MySQL bevelherinnering te krijgen:

   ```bash
   mysql -u root -p
   ```

1. Ga MySQL in `root` wachtwoord van de gebruiker wanneer daarom wordt gevraagd.
1. Voer de volgende opdrachten in in de volgorde die wordt weergegeven om databaseinstanties met de naam `magento_quote` en `magento_sales` met dezelfde gebruikersnamen en wachtwoorden:

   ```shell
   create database magento_quote;
   ```

   ```shell
   GRANT ALL ON magento_quote.* TO magento_quote@localhost IDENTIFIED BY 'magento_quote';
   ```

   ```shell
   create database magento_sales;
   ```

   ```shell
   GRANT ALL ON magento_sales.* TO magento_sales@localhost IDENTIFIED BY 'magento_sales';
   ```

1. Enter `exit` om de bevelherinnering te verlaten.

1. Controleer de databases één voor één:

   Database uitchecken:

   ```bash
   mysql -u magento_quote -p
   ```

   ```shell
   exit
   ```

   Database van het systeem voor orderbeheer:

   ```bash
   mysql -u magento_sales -p
   ```

   ```shell
   exit
   ```

   Als de MySQL monitorvertoningen, u het gegevensbestand behoorlijk creeerde. Als er een fout wordt weergegeven, herhaalt u de voorgaande opdrachten.

## Handel configureren om de hoofddatabases te gebruiken

Na vestiging een totaal van drie hoofdgegevensbestanden, gebruik de bevellijn om Handel te vormen om hen te gebruiken. (Het bevel plaatst omhoog gegevensbestandverbindingen en verspreidt lijsten onder de hoofdgegevensbestanden.)

### Eerste stappen

Zie [Opdrachten uitvoeren](../cli/config-cli.md#running-commands) aan login en looppas CLI bevelen.

### De database voor uitchecken configureren

Command syntaxis:

```bash
bin/magento setup:db-schema:split-quote --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Bijvoorbeeld:

```bash
bin/magento setup:db-schema:split-quote --host="localhost" --dbname="magento_quote" --username="magento_quote" --password="magento_quote"
```

Het volgende bericht wordt weergegeven ter bevestiging van een geslaagde installatie:

```terminal
Migration has been finished successfully!
```

### De OMS-database configureren

Command syntaxis:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Bijvoorbeeld:

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

```bash
bin/magento setup:upgrade
```

Het volgende bericht wordt weergegeven ter bevestiging van een geslaagde installatie:

```terminal
Migration has been finished successfully!
```
