---
title: Stappen voor migratie na gegevens
description: Leer welke stappen u moet ondernemen nadat u de opdracht [!DNL Data Migration Tool] om gegevens te migreren van Magento 1 naar Magento 2.
source-git-commit: b5a2c362b09de993e1dc196bdda90e74cf4a8ba2
workflow-type: tm+mt
source-wordcount: '93'
ht-degree: 0%

---


# Stappen voor migratie na gegevens

Nadat u de migratie hebt voltooid en uw nieuwe Magento 2-site grondig hebt getest, voert u de volgende taken uit:

* Magento 1 in de onderhoudsmodus plaatsen en alles permanent stoppen [Beheer](https://glossary.magento.com/admin) activiteiten

* Magento 2-cron-taken starten

* [Alle Magento 2-cachetypen leegmaken](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-cache.html#clean-and-flush-cache-types)

* [Alle Magento 2-indexen opnieuw indexeren](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#reindex)

* Wijzig DNS en load balancers om naar de Magento 2 productiehardware te wijzen
