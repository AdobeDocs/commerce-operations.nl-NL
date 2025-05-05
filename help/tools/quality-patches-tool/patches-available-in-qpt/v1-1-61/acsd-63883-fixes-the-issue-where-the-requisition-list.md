---
title: 'ACSD-63883: Het bevestigen van onjuiste &grave; items_count &grave; in  [!DNL GraphQL]  reactie voor [!UICONTROL Requisition List]'
description: Pas ACSD-63883 flard toe om de kwestie te bevestigen waar [!UICONTROL Requisition List] onjuiste &grave; items_count &grave; in de  [!DNL GraphQL]  reactie terugkeert.
feature: B2B, GraphQL
role: Admin, Developer
source-git-commit: 5d8b78588b11534828a9b925cbab0cc945860367
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883: onjuiste `items_count` correcties in [!DNL GraphQL] reactie voor [!UICONTROL Requisition List]

De ACSD-63883-patch verhelpt het probleem waarbij de **[!UICONTROL Requisition List]** onjuiste `items_count` in het [!DNL GraphQL] -antwoord retourneert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 wordt geïnstalleerd. De patch-id is ACSD-63883. Het probleem wordt volgens de planning opgelost in Adobe Commerce B2B 1.5.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De **[!UICONTROL Requisition List]** retourneert een onjuiste `items_count` in het [!DNL GraphQL] -antwoord.


<u> Stappen om </u> te reproduceren:

1. Schakel de functie B2B **[!UICONTROL Requisition List]** in.
1. Maak een paar producten.
1. Maak een klantenaccount.
1. Klik op **[!UICONTROL Create new Requisition List]**.
1. Verzend de mutatieaanvraag `addProductsToRequisitionList` [!DNL GraphQL] met een product om deze toe te voegen aan de [!UICONTROL Requisition List] .

   ```
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. Verzend de mutatieaanvraag `addProductsToRequisitionList` [!DNL GraphQL] met drie andere producten om deze toe te voegen aan de [!UICONTROL Requisition List] .
1. Controleer de `items_count` in de reactie.

**Verwachte resultaten**:

* `items_count`: 4 moet worden geretourneerd in het antwoord.

**Ware resultaten**:

* `items_count`: 2 wordt geretourneerd in het antwoord.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
