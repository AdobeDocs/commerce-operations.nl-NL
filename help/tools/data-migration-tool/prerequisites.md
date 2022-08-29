---
title: '"[!DNL Data Migration Tool] voorwaarden"'
description: '"Leer wat je moet doen voordat je begint met het gebruik van de [!DNL Data Migration Tool] om gegevens tussen Magento 1 en Magento 2 over te brengen."'
source-git-commit: 87298a6dfd783fed264f275495a3ad72374eb9f6
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# [!DNL Data Migration Tool] voorwaarden

Voordat u de migratie start, moet u controleren of aan de volgende vereisten is voldaan.

## Magento 2-systeem

* Stel uw Magento 2-systeem zo in dat het voldoet aan de [systeemvereisten](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html).

   Gebruik een topologie en een ontwerp dat minstens uw bestaand Magento 1 systeem aanpast.

* [Magento 2 installeren](https://devdocs.magento.com/guides/v2.4/install-gde/bk-install-guide.html).

## Cron

Start geen Magento 2-cron-taken.

## Database

* Na installatie, file of [stortplaats](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html) uw Magento 2-database zo snel mogelijk. Hierdoor kunt u de initiële databasestatus herstellen als de migratie niet succesvol is.

* Controleren of de [!DNL Data Migration Tool] heeft netwerktoegang om de Magento 1 en Magento 2 gegevensbestanden te verbinden.

   Open poorten in uw firewall zodat het migratiehulpprogramma kan communiceren met de databases.

* Zorg ervoor uw rekeningen MySQL alle noodzakelijke voorrechten hebben om tot gegevensbestanden van Magento toegang te hebben.

Als Binaire Logging voor uw Magento 1 gegevensbestand wordt toegelaten, plaats globale [`log_bin_trust_function_creators`](https://dev.mysql.com/doc/refman/5.7/en/server-system-variables.html#sysvar_log_bin_trust_function_creators) MySQL-systeemvariabele naar `1`of de [SUPER-bevoegdheden](https://dev.mysql.com/doc/refman/5.7/en/privileges-provided.html#priv_super) naar uw account.

* We raden u niet aan nieuwe entiteiten (producten, categorieën en kenmerken) vóór de migratie in uw Magento 2-winkel te maken, omdat de [!DNL Data Migration Tool] deze nieuwe entiteiten worden overschreven door de oude entiteiten uit Magento 1.

## Extensies

Migreer Magento 1 uitbreidingscode aan Magento 2.

Ga naar [!DNL [Commerce Marketplace]](https://marketplace.magento.com/) of neem contact op met uw extensieprovider.

U kunt ook de opdracht [!DNL [Code Migration Tool]](https://github.com/magento-commerce/code-migration/blob/develop/README.md).
