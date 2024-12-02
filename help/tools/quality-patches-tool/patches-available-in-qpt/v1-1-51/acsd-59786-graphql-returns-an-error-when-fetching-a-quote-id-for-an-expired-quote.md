---
title: 'ACSD-59786: GraphQL retourneert een fout bij het ophalen van een ` quote_id'' voor een verlopen aanhalingsteken'
description: Pas het ACSD-59786 flard toe om de kwestie van Adobe Commerce te bevestigen waar een vraag van GraphQL een fout terugkeert wanneer het halen van ` quote_id ` voor een verlopen citaat.
feature: GraphQL, Quotes, Companies
role: Admin, Developer
exl-id: 3c7aaa99-a2e0-44fe-9426-b24095615915
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-59786: GraphQL retourneert een fout bij het ophalen van een `quote_id` voor een verlopen prijsopgave

De ACSD-59786-patch verhelpt het probleem waarbij een GraphQL-query een fout retourneert bij het ophalen van een `quote_id` voor een verlopen offerte. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 wordt geïnstalleerd. De patch-id is ACSD-59786. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een GraphQL-query retourneert een fout bij het ophalen van een `quote_id` voor een verlopen quote.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL Companies]** en **[!UICONTROL Purchase Orders]** in.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** en reeks **[!UICONTROL Enable Company]** aan *ja*.
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** > **[!UICONTROL Order Approval Configuration]** en reeks **[!UICONTROL Enable Purchase Orders]** aan *ja*.
1. Creeer een nieuw bedrijf en reeks **[!UICONTROL Enable Purchase Orders]** aan *ja* voor het zelfde.
1. Maak een eenvoudig product en wijs het toe aan een categorie.
1. Meld u aan bij Storefront met de beheerdersaccount van het bedrijf en maak een nieuwe bestelling met **[!UICONTROL Purchase Order]** als betalingsmethode.
1. Wijzig de **[!UICONTROL Quote Lifetime (days)]** .
   * **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Shopping Cart]** > **[!UICONTROL Quote Lifetime (days)]** = *0*.
1. Voer de opdracht `bin/magento c:f` uit.
1. Ga naar de DB `quote_table` en wijzig de waarden `created_at` en `updated_at` met één dag in het verleden.
1. Voer de opdracht `bin/magento cron:run --group="sales_clean_quotes` uit.
1. Voer de hieronder gegeven GraphQL-aanvraag uit met een geautoriseerde token voor de beheerder die de **[!UICONTROL Purchase Order]** maakt:

   ```GraphQL
   {
       customer {
           purchase_order(uid: "MQ==") {
               quote {
                   id
               }
           }
       }
   } 
   ```

<u> Verwachte resultaten </u>:

De GraphQL-query retourneert de `quote_id` .

<u> Ware resultaten </u>:

De GraphQL-query retourneert een interne serverfout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
