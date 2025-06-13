---
title: 'ACSD-51857: Trage baan van ` aggregate_sales_report_bestsellers_data'' beïnvloedt prestaties'
description: Pas ACSD-51857 flard toe om de kwestie van Adobe Commerce te bevestigen waar de langzame bouwbaan ` aggregate_sales_report_bestsellers_data ` grote ` verkoop_order ` en ` verkoop_order_item' gegevensbestandlijsten beïnvloedt.
exl-id: 48e9852d-2cf6-411c-adf6-f91ac7743338
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857: langzame uitsnijdtaak van `aggregate_sales_report_bestsellers_data` heeft invloed op de prestaties

De ACSD-51857-patch verhelpt het probleem waarbij de trage uitsnijdtaak `aggregate_sales_report_bestsellers_data` van invloed is op grote `sales_order` - en `sales_order_item` databasetabellen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34 wordt geïnstalleerd. De patch-id is ACSD-51857. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties van de snijtaak van `aggregate_sales_report_bestsellers_data` zijn traag bij `sales_order` - en `sales_order_item` -databasetabellen.

Om dit op te lossen, is de belangrijkste gegevensvraag die grabs gegevens voor het rapport aan een efficiëntere vorm opnieuw geschreven. Het gebruikt nu een subquery om gegevenssubset te bepalen.

De subquery werkt zo snel mogelijk als volgt: er is een nieuwe index toegevoegd voor de databasetabel `sales_order` : `SALES_ORDER_STORE_STATE_CREATED` gebaseerd op de kolommen `store_id` , `state` en `created_at` .

<u> Eerste vereisten </u>

Zorg voor een groot aantal bestellingen per dag.

<u> Stappen om te reproduceren </u>

1. Voer de `aggregate_sales_report_bestsellers_data` -uitsnijdtaak uit.
1. Controleer de gegevens die moeten worden weergegeven op het dashboard Beheer, onder het tabblad **[!UICONTROL Bestsellers]** .

<u> Verwachte resultaten </u>:

*[!UICONTROL Quantity per source]* onder de tab **[!UICONTROL Configuration]** mag niet leeg zijn.

<u> Ware resultaten </u>:

*[!UICONTROL Quantity per source]* onder de tab **[!UICONTROL Configuration]** is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
