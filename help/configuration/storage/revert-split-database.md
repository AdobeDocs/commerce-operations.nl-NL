---
title: Gesplitste database herstellen
description: Keer van een afgekeurde gespleten gegevensbestandimplementatie aan één enkele gegevensbestandimplementatie terug.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Herstellen van gesplitste database

{{ee-only}}

Voor Adobe Commerce-klanten die [Database splitsen](multi-master.md), beschrijft het volgende onderwerp hoe te om terug naar één enkel gegevensbestand terug te keren of te migreren. We raden aan dat Adobe Commerce-handelaren die momenteel Split Database gebruiken en van plan zijn om te upgraden naar 2.4.2 en deze stappen later opnieuw te bekijken, evenals onze [aankondiging](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) over de geplande afbraak van gesplitste database.

Het terugkeren van een gesplitste database naar één database betekent het maken van back-ups van de `magento_quote` en `magento_sales` databases voordat deze in één database worden geladen `magento_main` database.

In dit voorbeeld, login aan alle drie gegevensbestanden, die op de zelfde gastheer (`magento2-mysql`) als de &quot;hoofdgebruiker&quot;. U moet deze waarden vervangen door de juiste waarden voor uw databases.

1. Maak een back-up van de `magento_quote` database:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Maak een back-up van de `magento_sales` database:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Laad de `magento_quote` in de `magento_main` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Laad de `magento_sales` in de `magento_main` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Zet de `magento_sales` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Zet de `magento_quote` database:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Verwijder de plaatsingsconfiguratie voor `checkout` en `sales` in de `connections` en `resources` van de `env.php` bestand.
1. Externe toetsen herstellen:

   ```bash
   bin/magento setup:upgrade
   ```

## Uw werk controleren

Om te controleren of de implementatie van één database goed werkt, voert u de volgende taken uit en controleert u of er gegevens zijn toegevoegd aan de `magento_main` databasetabellen met behulp van databasegereedschappen, zoals [phpMyAdmin](../../installation/prerequisites/optional-software.md#phpmyadmin):

1. Controleer of vreemde sleutels zijn hersteld. De `QUOTE_STORE_ID_STORE_STORE_ID` in de `quote` databasetabel.
1. Controleer of klanten bestellingen kunnen plaatsen vanuit de winkel.
1. Controleer of de orders die zijn gemaakt voordat de gesplitste database wordt teruggezet naar één database, beschikbaar zijn in de Admin.
