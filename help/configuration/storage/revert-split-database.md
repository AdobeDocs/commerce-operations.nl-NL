---
title: Gesplitste database herstellen
description: Keer van een afgekeurde gespleten gegevensbestandimplementatie aan één enkele gegevensbestandimplementatie terug.
feature: Configuration, Storage
exl-id: 2ece24e0-1f85-445a-8e22-fb10611403ff
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Herstellen van gesplitste database

{{ee-only}}

Voor de klanten van Adobe Commerce die [ Gesplitste Gegevensbestand ](multi-master.md) hebben uitgevoerd, beschrijft het volgende onderwerp hoe te terug naar één enkel gegevensbestand terugkeren of migreren. Wij adviseren dat de handelaren van Adobe Commerce momenteel het Gesplitste Gegevensbestand gebruiken en van plan zijn om aan 2.4.2 te bevorderen en later deze stappen, evenals onze [ aankondiging ](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) op de geplande veroudering van het Gesplitste Gegevensbestand herzien.

Als u een gesplitste database wilt terugzetten naar één database, maakt u back-ups van de `magento_quote` - en `magento_sales` -databases voordat u deze laadt in de enige `magento_main` -database.

In dit voorbeeld, login aan alle drie gegevensbestanden, die op de zelfde gastheer (`magento2-mysql`) als &quot;wortel&quot;gebruiker geïnstalleerd zijn. U moet deze waarden vervangen door de juiste waarden voor uw databases.

1. Maak een back-up van de `magento_quote` -database:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_quote > ./quote.sql
   ```

1. Maak een back-up van de `magento_sales` -database:

   ```bash
   mysqldump -h "magento2-mysql" -u root -p magento_sales > ./sales.sql
   ```

1. Laad de `magento_quote` -database in de `magento_main` -database:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./quote.sql
   ```

1. Laad de `magento_sales` -database in de `magento_main` -database:

   ```bash
   mysql -h "magento2-mysql" -u root -p magento_main < ./sales.sql
   ```

1. Zet de `magento_sales` -database neer:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_sales;"
   ```

1. Zet de `magento_quote` -database neer:

   ```bash
   mysql -h "magento2-mysql" -u root -p -e "DROP DATABASE magento_quote;"
   ```

1. Verwijder de implementatieconfiguratie voor `checkout` en `sales` in de secties `connections` en `resources` van het `env.php` -bestand.
1. Externe toetsen herstellen:

   ```bash
   bin/magento setup:upgrade
   ```

## Uw werk controleren

Om te verifiëren dat uw enige gegevensbestandimplementatie behoorlijk werkt, voer de volgende taken uit en verifieer dat het gegeven aan de `magento_main` gegevensbestandlijsten gebruikend een gegevensbestandhulpmiddel zoals [ phpMyAdmin ](../../installation/prerequisites/optional-software.md#phpmyadmin) wordt toegevoegd:

1. Controleer of vreemde sleutels zijn hersteld. Bijvoorbeeld de `QUOTE_STORE_ID_STORE_STORE_ID` -toets in de `quote` -databasetabel.
1. Verifieer dat de klanten orden van de opslagront kunnen plaatsen.
1. Controleer of de orders die zijn gemaakt voordat de gesplitste database wordt teruggezet naar één database, beschikbaar zijn in de Admin.
