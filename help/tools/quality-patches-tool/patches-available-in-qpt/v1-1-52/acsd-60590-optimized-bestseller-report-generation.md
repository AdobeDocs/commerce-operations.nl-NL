---
title: "ACSD-60590: Verbeterende prestaties van Bestsellers Aggregated Daily Report generation"
description: Pas de ACSD-60590-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het samengevoegde Dagelijkse rapport van Bestsellers veel tijd kost om te genereren voor een groot aantal geplaatste bestellingen.
feature: Reporting
role: Admin, Developer
source-git-commit: 4fe3f205754c040b60b6b7f01c7109cb31f70af8
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-60590: Verbeterende prestaties van Bestsellers Aggregated Daily Report Generation

De ACSD-60590-patch verhelpt het probleem dat het samengevoegde Dagelijkse rapport van Bestsellers veel tijd kost om te genereren voor een groot aantal geplaatste bestellingen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.52 wordt geïnstalleerd. De patch-id is ACSD-60590. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het rapport Bestsellers Aggregated Daily kost veel tijd om te genereren voor een groot aantal geplaatste bestellingen.

<u> Eerste vereisten </u>

Een groot aantal orden (bijvoorbeeld: *500k*).

<u> Stappen om </u> te reproduceren:

1. Voer de volgende opdracht uit:

   `update sales_order set created_at = DATE(DATE_SUB(NOW(), INTERVAL ROUND(RAND()*3650) DAY))  ;`

1. Voer de `aggregate_sales_report_bestsellers_data` -taak uit.

<u> Verwachte resultaten </u>:

De taak wordt binnen 30 seconden voltooid.

<u> Ware resultaten </u>:

De query duurt ongeveer 10 minuten voor elke winkel voor `created_at` datums.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.