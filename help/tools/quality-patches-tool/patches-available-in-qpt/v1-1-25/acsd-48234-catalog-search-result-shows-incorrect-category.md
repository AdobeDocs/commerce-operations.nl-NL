---
title: 'ACSD-48234: zoekresultaat catalogus onjuiste telling categorie-items indien [!UICONTROL Display Out of Stock Products] ingeschakeld'
description: Pas de ACSD-48234-patch toe om het Adobe Commerce-probleem op te lossen waarbij het zoekresultaat van de catalogus een onjuist aantal categorieën van items weergeeft wanneer de optie [!UICONTROL Display Out of Stock Products] is ingeschakeld.
feature: Admin Workspace, Categories, Catalog Management, Orders, Products, Search
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-48234: zoekresultaten in catalogus tonen onjuist aantal categorieën **[!UICONTROL Display Out of Stock Products]** ingeschakeld

De ACSD-48234-patch lost het probleem op waarbij het zoekresultaat van de catalogus een onjuist aantal categorieën van items weergeeft wanneer de optie **[!UICONTROL Display Out of Stock Products]** is ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-48234. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.


## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het zoekresultaat van de catalogus geeft een onjuist aantal categorie-items weer wanneer de optie **[!UICONTROL Display Out of Stock Products]** is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en open **[!UICONTROL color]** -kenmerk.
1. Voeg twee opties toe, bijvoorbeeld oranje en groen. Sla het kenmerk op.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** en voeg het kenmerk **[!UICONTROL color]** toe aan de kenmerkset **[!UICONTROL Default]** .
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL CATALOG]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** en plaats **[!UICONTROL Display Out of Stock Products]** aan _ja_.
1. Categorie &#39;cat1&#39; maken.
1. Twee producten maken:
   1. Naam: prod1, Color: orange, Categorieën: cat1.
   1. Naam: prod2, Color: green, Categories: cat1.
1. Open de categorie kat1 op de winkel.
1. Selecteer de oranje kleur bij de gelaagde navigatie.

<u> Verwachte resultaten </u>:

Alleen product prod1 wordt weergegeven.

<u> Ware resultaten </u>:

Zowel prod1 als prod2 producten worden getoond.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
