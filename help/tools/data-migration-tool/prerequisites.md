---
title: '[!DNL Data Migration Tool] voorwaarden'
description: Leer wat u moet doen alvorens u  [!DNL Data Migration Tool]  begint te gebruiken om gegevens tussen Magento 1 en Magento 2 over te brengen.
exl-id: 42dfa1ca-41ed-453d-a3e4-41ff36817ca3
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Data Migration Tool] voorwaarden

Voordat u de migratie start, moet u controleren of aan de volgende vereisten is voldaan.

## Magento 2-systeem

* Opstelling uw Magento 2 systeem zodat het aan de [&#x200B; systeemvereisten &#x200B;](../../installation/system-requirements.md) voldoet.

  Gebruik een topologie en een ontwerp dat minstens uw bestaand Magento 1 systeem aanpast.

* [&#x200B; installeer Magento 2 &#x200B;](../../installation/overview.md).

## Cron

Start Magento 2-banen niet.

## Database

* Na installatie, file of [&#x200B; stortplaats &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) uw Magento 2 gegevensbestand zo spoedig mogelijk. Hierdoor kunt u de initiële databasestatus herstellen als de migratie niet succesvol is.

* Controleer of de [!DNL Data Migration Tool] netwerktoegang heeft om de Magento 1- en Magento 2-databases te verbinden.

  Open poorten in uw firewall zodat het migratiehulpprogramma kan communiceren met de databases.

* Zorg ervoor dat uw MySQL-accounts over alle benodigde rechten beschikken om toegang te krijgen tot Magento-databases.

Als het Binaire Registreren voor uw Magento 1- gegevensbestand wordt toegelaten, plaats globale [`log_bin_trust_function_creators` &#x200B;](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL systeemvariabele aan `1`, of geef het [&#x200B; SUPER voorrecht &#x200B;](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) aan uw rekening toe.

* We raden u niet aan om vóór de migratie nieuwe entiteiten (producten, categorieën en kenmerken) in uw Magento 2-winkel te maken, omdat [!DNL Data Migration Tool] dergelijke nieuwe entiteiten vervangt door de oude entiteiten uit Magento 1.

## Extensies

Magento 1-extensiecode migreren naar Magento 2.

Ga naar [[!DNL [Commerce Marketplace]]](https://marketplace.magento.com/) of neem contact op met de leverancier van de extensies als u de meest recente versies van extensies wilt zoeken.

U kunt ook [[!DNL [Code Migration Tool]]](https://github.com/magento-commerce/code-migration/blob/develop/README.md) gebruiken.
