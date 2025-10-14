---
title: Automatisch hoofddatabases configureren
description: Zie begeleiding bij het automatisch vormen van de gespleten gegevensbestandoplossing.
recommendations: noCatalog
exl-id: a27ad097-de60-4cdd-81f9-eb1ae84587e4
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# Automatisch hoofddatabases configureren

{{ee-only}}

{{deprecate-split-db}}

Dit onderwerp bespreekt hoe te beginnen met de gespleten gegevensbestandoplossing door:

1. Adobe Commerce installeren met één hoofddatabase (genaamd `magento`)
1. Twee extra hoofddatabases maken voor uitchecken en OMS (genaamd `magento_quote` en `magento_sales`)
1. Adobe Commerce configureren voor het gebruik van de databases voor uitchecken en verkopen

>[!INFO]
>
>In deze handleiding wordt ervan uitgegaan dat alle drie databases zich op dezelfde host bevinden als de Commerce-toepassing en dat ze de namen `magento` , `magento_quote` en `magento_sales` hebben. Nochtans, is de keus van waar te om van de gegevensbestanden de plaats te bepalen en wat zij worden genoemd aan u. We hopen dat onze voorbeelden de instructies makkelijker te volgen maken.

## De Adobe Commerce-software installeren

U kunt gesplitste databases op elk gewenst moment inschakelen nadat u de Adobe Commerce-software hebt geïnstalleerd. Met andere woorden, u kunt gesplitste databases toevoegen aan een Adobe Commerce-systeem dat al gegevens voor kassa en bestelling bevat. Gebruik de instructies in Adobe Commerce README of de [&#x200B; installatiegids &#x200B;](../../installation/overview.md) om de software van Adobe Commerce te installeren gebruikend één enkel hoofdgegevensbestand.

## Extra hoofddatabases instellen

Maak als volgt uitcheckdatabases en OMS-hoofddatabases:

1. Meld u als elke gebruiker aan bij uw databaseserver.
1. Ga het volgende bevel in om aan een MySQL bevelherinnering te krijgen:

   ```bash
   mysql -u root -p
   ```

1. Voer het gebruikerswachtwoord van MySQL `root` in wanneer hierom wordt gevraagd.
1. Voer de volgende opdrachten in de volgorde in die wordt weergegeven om databaseinstanties met de naam `magento_quote` en `magento_sales` te maken met dezelfde gebruikersnamen en wachtwoorden:

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

1. Ga `exit` in om de bevelherinnering weg te gaan.

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

## Commerce configureren voor het gebruik van de hoofddatabases

Na vestiging in totaal van drie hoofdgegevensbestanden, gebruik de bevellijn om Commerce te vormen om hen te gebruiken. (Het bevel plaatst omhoog gegevensbestandverbindingen en verspreidt lijsten onder de hoofdgegevensbestanden.)

### Eerste stappen

Zie [&#x200B; Lopende bevelen &#x200B;](../cli/config-cli.md#running-commands) aan login en looppas bevelen CLI.

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

```
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

```
Migration has been finished successfully!
```
