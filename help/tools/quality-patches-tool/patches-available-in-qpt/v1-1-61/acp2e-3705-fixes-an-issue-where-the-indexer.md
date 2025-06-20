---
title: 'ACP2E-3705: ` indexer_update_all_views ` de kroonuitvoering ontbreekt wanneer ` MAGE_INDEXER_THREADS_COUNT wordt geplaatst'
description: Pas het ACS2E-3705 flard toe om de kwestie van Adobe Commerce te bevestigen waar de ` indexer_update_all_views' kroonuitvoering ontbreekt wanneer ` MAGE_INDEXER_THREADS_COUNT ` wordt geplaatst.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705: `indexer_update_all_views` Het uitvoeren van de uitsnede mislukt wanneer `MAGE_INDEXER_THREADS_COUNT` is ingesteld

>[!NOTE]
>
>Dit flard vervangt [ ACSD-64112 ](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) voor versies 2.4.7 en hierboven.

De ACP2E-3705-patch verhelpt het probleem waarbij het uitvoeren van de `indexer_update_all_views` -uitsnede mislukt wanneer `MAGE_INDEXER_THREADS_COUNT` wordt ingesteld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 wordt geïnstalleerd. De patch-id is ACP2E-3705. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `indexer_update_all_views` bouwstijluitvoering ontbreekt wanneer `MAGE_INDEXER_THREADS_COUNT` aan een waarde groter dan *2* wordt geplaatst, specifiek beïnvloedend de [!UICONTROL Customer Segments] indexeerder met toegelaten B2B.

<u> Stappen om </u> te reproduceren:

1. Pas het QPT flard [ ACSD-64112 ](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) toe.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]** .
1. Schakel **[!UICONTROL Category Permissions]** in.
1. Stel de volgende indexen in op de modus **[!UICONTROL Update on Schedule]** :

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Maak enkele producten en wijs deze toe aan een categorie.
1. Voer een volledige redex uit.
1. Ga naar een categorie en stel **[!UICONTROL Category Permissions]** in.
1. De looppas `indexer_update_all_views` bouwbaan met `MAGE_INDEXER_THREADS_COUNT` plaatste aan *8*.

<u> Verwachte resultaten </u>:

Opnieuw indexeren is voltooid zonder fouten.

<u> Ware resultaten </u>:

De `indexer_update_all_views` -snijtaak kent de volgende fout:

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce on cloud Infrastructure: Upgrades and Patches > Apply Patches in the Commerce on Cloud Infrastructure guide.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
