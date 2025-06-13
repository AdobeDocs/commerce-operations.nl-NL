---
title: 'ACSD-48366: productafbeelding niet weergegeven in de [!UICONTROL Back to Stock] e-mailsjabloon'
description: Pas de ACSD-48366-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de miniatuurafbeelding van het product niet wordt weergegeven in de voorraadwaarschuwingsmail van het product.
feature: Admin Workspace, Communications, Orders, Products
role: Admin
exl-id: a721f399-f50a-4a13-9f5d-17ae7f3985f6
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48366: productafbeelding niet weergegeven in de [!UICONTROL Back to Stock] e-mailsjabloon

De ACSD-48366-patch verhelpt het probleem dat de miniatuurafbeelding van het product niet wordt weergegeven in het bericht voor voorraadwaarschuwingen van het product. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-48366. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De productafbeelding wordt niet weergegeven in de e-mailsjabloon van [!UICONTROL Back to Stock] .

<u> Stappen om </u> te reproduceren:

1. Schakel *[!UICONTROL Product Alert]* voor *[!UICONTROL Back in Stock]* in door naar **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]** > **[!UICONTROL Allow Alert When Product Comes Back in Stock]** = *[!UICONTROL Yes]* .
1. Schakel *[!UICONTROL Display Out of Stock Products]* in door naar **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Display Out of Stock]** = *[!UICONTROL Yes]* .
1. Maak een eenvoudig product met qty = 0.
1. Maak een klant van de winkel en meld u aan voor het bovenstaande product om productwaarschuwingen te ontvangen wanneer het product in voorraad is.
1. Maak het product in voorraad.
1. Voer de waarschuwing voor het product uit.

   ```
   n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Start de productwaarschuwing voor de klant.

   ```
   bin/magento queue:consumers:start product_alert
   ```

1. Controleer het e-mailbericht. Het e-mailbericht met voorraadwaarschuwingen moet nu beschikbaar zijn in de e-mailcatcher.

<u> Verwachte resultaten </u>:

De afbeelding van het product wordt weergegeven in het bericht voor voorraadwaarschuwing.

<u> Ware resultaten </u>:

De afbeelding van het product is niet beschikbaar in het bericht voor voorraadwaarschuwingen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
