---
title: Master databases automatisch configureren
description: Zie begeleiding bij het automatisch vormen van de gespleten gegevensbestandoplossing.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 1%

---


# Master databases automatisch configureren

{#ee-only}

{{deprecate-split-db}}

Dit onderwerp bespreekt hoe te beginnen met de gespleten gegevensbestandoplossing door:

1. Adobe Commerce installeren met één master database (genaamd `magento`)
1. Twee extra master databases maken voor [uitchecken](https://glossary.magento.com/checkout) en OMS (benoemd `magento_quote` en `magento_sales`)
1. Adobe Commerce configureren voor het gebruik van de databases voor uitchecken en verkopen

>[!INFO]
>
>Deze gids veronderstelt dat alle drie gegevensbestanden op de zelfde gastheer zoals de toepassing van de Handel zijn en dat zij worden genoemd `magento`, `magento_quote`, en `magento_sales`. Nochtans, is de keus van waar te om van de gegevensbestanden de plaats te bepalen en wat zij worden genoemd aan u. We hopen dat onze voorbeelden de instructies makkelijker te volgen maken.

## De Adobe Commerce-software installeren

U kunt gesplitste databases op elk gewenst moment inschakelen nadat u de Adobe Commerce-software hebt geïnstalleerd. Met andere woorden, u kunt gesplitste databases toevoegen aan een Adobe Commerce-systeem dat al gegevens voor kassa&#39;s en bestellingen heeft. Gebruik de instructies in Adobe Commerce README of in de [installatiegids](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html) om de Adobe Commerce-software te installeren met behulp van één master database.

## Aanvullende master databases instellen

Maak als volgt afrekenings- en OMS-master databases:

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

## Handel configureren om de master databases te gebruiken

Na vestiging in totaal van drie master gegevensbestanden, gebruik de bevellijn om Handel te vormen om hen te gebruiken. (Het bevel plaatst omhoog gegevensbestandverbindingen en verspreidt lijsten onder de master gegevensbestanden.)

### Eerste stappen

Zie [Opdrachten uitvoeren](../cli/config-cli.md#running-commands) aan login en looppas CLI bevelen.

### De database voor uitchecken configureren

Opdrachtsyntaxis:

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

Opdrachtsyntaxis:

```bash
bin/magento setup:db-schema:split-sales --host="<checkout db host or ip>" --dbname="<name>" --username="<checkout db username>" --password="<password>"
```

Bijvoorbeeld:

```bash
bin/magento setup:db-schema:split-sales --host="localhost" --dbname="magento_sales" --username="magento_sales" --password="magento_sales"
```

Het volgende bericht wordt weergegeven ter bevestiging van een geslaagde installatie:

```terminal
Migration has been finished successfully!
```
