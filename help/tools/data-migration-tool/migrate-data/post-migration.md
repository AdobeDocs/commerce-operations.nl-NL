---
title: Stappen voor migratie na gegevens
description: Leer welke stappen u moet ondernemen nadat u de opdracht [!DNL Data Migration Tool] om gegevens te migreren van Magento 1 naar Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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
