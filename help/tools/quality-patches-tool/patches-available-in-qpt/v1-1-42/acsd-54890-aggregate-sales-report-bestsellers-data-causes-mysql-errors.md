---
title: 'ACSD-54890: &grave; aggregate_sales_report_bestsellers_data &grave; veroorzaakt  [!DNL MySQL]  fouten'
description: Pas ACSD-54890 flard toe om de kwestie van Adobe Commerce te bevestigen waar &grave; aggregate_sales_report_bestsellers_data &grave;  [!DNL MySQL]  fouten toe te schrijven aan &grave;/tmpdisk &grave; die uit ruimte zijn veroorzaakt.
feature: Attributes
role: Admin, Developer
exl-id: 21f926e0-a4f4-45ae-9397-4885a85db947
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-54890: `aggregate_sales_report_bestsellers_data` veroorzaakt MySQL-fouten

De ACSD-54890-patch verhelpt het probleem waarbij `aggregate_sales_report_bestsellers_data` [!DNL MySQL] fouten veroorzaakt omdat `/tmpdisk` onvoldoende ruimte heeft. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-54890. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`aggregate_sales_report_bestsellers_data` veroorzaakt **[!DNL MySQL]** fouten omdat `/tmpdisk` onvoldoende ruimte heeft.

<u> Stappen om </u> te reproduceren:

Voer de `aggregate_sales_report_bestsellers_data` -snijtaak uit wanneer de `sales_bestsellers_aggregated_daily` -tabel een enorme hoeveelheid records heeft, zoals tientallen miljoenen records.

<u> Verwachte resultaten </u>:

Er treden geen fouten op.

<u> Ware resultaten </u>:

De volgende fout treedt op:
`report.ERROR: Cron Job aggregate_sales_report_bestsellers_data has an error: SQLSTATE[HY000]: General error: 3 Error writing file '/tmp/#sql/fd=72' (Errcode: 28 "No space left on device")`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Patches toepassen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de basis van de steunkennis zelf-te dienen
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
