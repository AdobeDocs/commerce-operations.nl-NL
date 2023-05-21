---
title: Aanbevolen werkwijzen voor gegevensmigratie
description: Volg deze best practices voor gegevensmigratie om een geslaagde upgrade van Magento 1 naar Magento 2 te garanderen.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor gegevensmigratie

Deze sectie bevat de beste aanbevelingen om uw migratie te versnellen en te vereenvoudigen en u kunt aangeven hoeveel tijd het kost.

* **Een kopie van de database uit een Magento 1-instantie gebruiken** bij het uitvoeren van migratietests. Gebruik niet de productieinstantie van uw Magento 1 opslaggegevensbestand.

* **Verouderde en overtollige gegevens verwijderen** van uw Magento 1-database vóór de migratie.

Dergelijke gegevens kunnen logboeken, orderaanhalingstekens, onlangs bekeken of vergeleken producten, bezoekers, gebeurtenisspecifieke categorieën, en promotieregels omvatten.

* **Volg de [algemene regels voor een geslaagde migratie](migrate-data/overview.md#migration-overview)**.

* Om de prestaties te verbeteren, **de `direct_document_copy` option** in uw `config.xml` bestand:

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Zowel moeten Magento 1 als Magento 2 gegevensbestanden op de zelfde server worden gevestigd MySQL en de gegevensbestandrekening moet toegang tot beide gegevensbestanden hebben.

## Benchmarking

Adobe heeft de gegevensmigratie op het volgende systeem getest:

* Virtual Box VM, CentOS 6, 2,5 GB RAM, CPU 1 core 2,6 GHz
* Database met 177.000 producten, 355.000 bestellingen en 214.000 klanten

## Prestatieresultaten

* Migratietijd instellingen: ~10 minuten
* Tijdstip gegevensmigratie: ~9 uur (alle gegevens behalve URL herschrijven, ~85% van het totaal aan gegevens)
* Schatting van downtime van site: enkele minuten om DNS-instellingen opnieuw te definiëren en te wijzigen. Er is meer tijd nodig om de cache van de pagina op te warmen.
