---
title: Stappen voor migratie na gegevens
description: Leer welke stappen u moet ondernemen nadat u de opdracht [!DNL Data Migration Tool] om gegevens van Magento 1 naar Magento 2 te migreren.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---

# Stappen voor migratie na gegevens

Nadat u de migratie hebt voltooid en uw nieuwe Magento 2-site grondig hebt getest, voert u de volgende taken uit:

* Magento 1 in onderhoudsmodus plaatsen en alle beheeractiviteiten permanent stopzetten

* Magento 2-banen starten

* [Alle Magento 2-cachetypen leegmaken](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Alle Magento 2-indexen opnieuw indexeren](../../../configuration/cli/manage-indexers.md#reindex)

* Wijzig DNS en load balancers om naar Magento 2 productiehardware te wijzen
