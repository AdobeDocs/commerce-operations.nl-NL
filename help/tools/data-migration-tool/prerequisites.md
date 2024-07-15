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

## Systeem van Magento 2

* Opstelling uw Magento 2 systeem zodat het aan de [ systeemvereisten ](../../installation/system-requirements.md) voldoet.

  Gebruik een topologie en een ontwerp dat minstens uw bestaand Magento 1 systeem aanpast.

* [ installeer Magento 2 ](../../installation/overview.md).

## Cron

Start geen Magento 2 cron-taken.

## Database

* Na installatie, file of [ stortplaats ](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) uw Magento 2 gegevensbestand zo spoedig mogelijk. Hierdoor kunt u de initiële databasestatus herstellen als de migratie niet succesvol is.

* Verifieer of [!DNL Data Migration Tool] netwerktoegang heeft om Magento 1 en Magento 2 gegevensbestanden aan te sluiten.

  Open poorten in uw firewall zodat het migratiehulpprogramma kan communiceren met de databases.

* Zorg ervoor uw rekeningen MySQL alle noodzakelijke voorrechten hebben om tot gegevensbestanden van het Magento toegang te hebben.

Als het Binaire Registreren voor uw Magento 1 gegevensbestand wordt toegelaten, plaats globale [`log_bin_trust_function_creators` ](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL systeemvariabele aan `1`, of geef het [ BEHEER ](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) recht van de SUPER aan uw rekening.

* We raden u niet aan nieuwe entiteiten (producten, categorieën en kenmerken) vóór de migratie in uw Magento 2-winkel te maken, omdat [!DNL Data Migration Tool] dergelijke nieuwe entiteiten vervangt door de oude entiteiten uit Magento 1.

## Extensies

Migreer Magento 1 uitbreidingscode aan Magento 2.

Ga naar [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) of neem contact op met de leverancier van de extensies als u de meest recente versies van extensies wilt zoeken.

U kunt ook [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md) gebruiken.
