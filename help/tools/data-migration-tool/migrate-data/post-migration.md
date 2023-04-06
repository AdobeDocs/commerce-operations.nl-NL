---
title: Stappen voor migratie na gegevens
description: Leer welke stappen u moet ondernemen nadat u de opdracht [!DNL Data Migration Tool] om gegevens te migreren van Magento 1 naar Magento 2.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Stappen voor migratie na gegevens

Nadat u de migratie hebt voltooid en uw nieuwe Magento 2-site grondig hebt getest, voert u de volgende taken uit:

* Magento 1 in onderhoudsmodus plaatsen en alle beheeractiviteiten permanent stopzetten

* Magento 2-cron-taken starten

* [Alle Magento 2-cachetypen leegmaken](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Alle Magento 2-indexen opnieuw indexeren](../../../configuration/cli/manage-indexers.md#reindex)

* Wijzig DNS en load balancers om naar de Magento 2 productiehardware te wijzen
