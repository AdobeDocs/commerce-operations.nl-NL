---
title: 'ACSD-50817: Optimizes cron job sales_clean_quotes to run rapid'
description: Pas ACSD-50817 flard toe om de cron baan ` sales_clean_quotes' te optimaliseren om sneller te lopen door een samengestelde index op ` store_id ` en ` update_at' kolommen in de citaatlijst toe te voegen.
feature: Quotes
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-50817: hiermee wordt de snijtaak `sales_clean_quotes` geoptimaliseerd en sneller uitgevoerd

De ACSD-50817-patch optimaliseert de uitsnijdtaak `sales_clean_quotes` zodat deze sneller wordt uitgevoerd door een samengestelde index toe te voegen aan de kolommen `store_id` en `updated_at` in de aanhalingstabel. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.31 wordt geïnstalleerd. De patch-id is ACSD-50817.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De uitsnijdtaak `sales_clean_quotes` is te langzaam. Met deze patch is deze geoptimaliseerd voor een snellere uitvoering door een samengestelde index toe te voegen aan de kolommen `store_id` en `updated_at` in de aanhalingstabel.

<u> Stappen om </u> te reproduceren:

1. Genereer 50-80 MB aanhalingstekens met `updated_at` ingesteld op een periode van &lt; 30 dagen.
1. Voer de uitsnijdtaak `sales_clean_quotes` of de volgende query op de aanhalingstabel uit:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u> Verwachte resultaten </u>

De uitsnijdtaak `sales_clean_quotes` wordt geoptimaliseerd om sneller te worden uitgevoerd door een samengestelde index toe te voegen aan de kolommen `store_id` en `updated_at` in de tabel met aanhalingstekens.

<u> Ware resultaten </u>

De query is te langzaam.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
