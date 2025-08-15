---
title: 'ACSD-64112: De uitvoering van de cron van "indexer_update_all_views" mislukt wanneer "MAGE_INDEXER_THREADS_COUNT" is ingesteld'
description: Pas het ACSD-64112 flard toe om de kwestie van Adobe Commerce te bevestigen waar de &grave; indexer_update_all_views' kroonuitvoering ontbreekt wanneer &grave; MAGE_INDEXER_THREADS_COUNT &grave; wordt geplaatst.
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112: `indexer_update_all_views` de uitvoering van het uitsnijden mislukt wanneer `MAGE_INDEXER_THREADS_COUNT` is ingesteld

>[!NOTE]
>
>Dit flard werd vervangen met [ ACP2E-3705 ](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md) voor de versies van Adobe Commerce boven 2.4.7.

De ACSD-64112-patch verhelpt het probleem waarbij de uitvoering van de `indexer_update_all_views` -uitsnede mislukt wanneer `MAGE_INDEXER_THREADS_COUNT` wordt ingesteld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 wordt geïnstalleerd. De patch-id is ACSD-64112. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p10

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De uitvoering van de `indexer_update_all_views` uitsnede mislukt wanneer `MAGE_INDEXER_THREADS_COUNT` wordt ingesteld op een waarde groter dan 2, wat specifiek van invloed is op de [!UICONTROL Customer Segments] -index met B2B ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Installeer een schone instantie met B2B.
1. Schakel **[!UICONTROL B2B Company]** en **[!UICONTROL Shared Catalog]** in.
1. Maak een categorie.
1. Maak enkele producten en wijs deze toe aan de categorie.
1. Voer een volledige redex uit.
1. Stel de volgende indexen in op **[!UICONTROL Update on Schedule]** :

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Ga naar de achterkant en laad de nieuwe categorie.
1. Klik op **[!UICONTROL Category Permissions]** en maak een **[!UICONTROL New Permission]** voor een bestaande klantengroep.
1. Zorg ervoor dat de `catalogpermissions_category` indexer een achterstand heeft. Voer het volgende bevel uit om dit te verifiëren:

   ```
   bin/magento indexer:status
   ```

1. Stel het volgende aantal indexerthread in in `env.php` :

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. De snijtaak uitvoeren:

   ```
   bin/magento cron:run
   ```

<u> Verwachte resultaten </u>:

De uitsnijdtaak moet zonder problemen worden uitgevoerd.

<u> Ware resultaten </u>:

De `indexer_update_all_views` -snijtaak kent de volgende fout:

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Aanvullende stappen vereist na de installatie van de patch

(Deze sectie is optioneel; er kunnen enkele stappen vereist zijn na het aanbrengen van de patch om het probleem op te lossen.) 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
