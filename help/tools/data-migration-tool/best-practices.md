---
title: Aanbevolen werkwijzen voor gegevensmigratie
description: Volg deze best practices voor gegevensmigratie om een geslaagde upgrade van Magento 1 naar Magento 2 te garanderen.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor gegevensmigratie

Deze sectie bevat de beste aanbevelingen om uw migratie te versnellen en te vereenvoudigen en u kunt aangeven hoeveel tijd het kost.

* **Gebruik een exemplaar van het gegevensbestand van Magento 1 instantie** wanneer het uitvoeren van migratie het testen. Gebruik de productieinstantie van uw Magento 1-opslagdatabase niet.

* **verwijder verouderde en overtollige gegevens** uit uw Magento 1 gegevensbestand vóór migratie.

Dergelijke gegevens kunnen logboeken, orderaanhalingstekens, onlangs bekeken of vergeleken producten, bezoekers, gebeurtenisspecifieke categorieën, en promotieregels omvatten.

* **volg de [&#x200B; algemene regels voor succesvolle migratie](migrate-data/overview.md#migration-overview)**.

* Om prestaties op te voeren, **laat `direct_document_copy` optie** in uw `config.xml` dossier toe:

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>Zowel Magento 1- als Magento 2-databases moeten zich op dezelfde MySQL-server bevinden en de databaseaccount moet toegang hebben tot beide databases.

## Benchmarkingsramingen

Adobe heeft de gegevensmigratie op het volgende systeem getest:

* Virtual Box VM, CentOS 6, 2,5 GB RAM, CPU 1 core 2,6 GHz
* Database met 177.000 producten, 355.000 bestellingen en 214.000 klanten

## Prestatieresultaten

* Migratietijd voor instellingen: ~10 minuten
* Tijd van gegevensmigratie: ~9 uur (alle gegevens behalve URL herschrijven, ~85% van het totaal aan gegevens)
* Raming van downtime van site: enkele minuten om DNS-instellingen opnieuw te definiëren en te wijzigen. Er is meer tijd nodig om de cache van de pagina op te warmen.
