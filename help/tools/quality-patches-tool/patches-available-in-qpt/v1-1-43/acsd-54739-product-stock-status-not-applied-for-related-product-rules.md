---
title: 'ACSD-54739: *[!UICONTROL Product Stock] * status niet toegepast op *[!UICONTROL Related Product Rules] *'
description: Pas de ACSD-54739-patch toe om het Adobe Commerce-probleem op te lossen waarbij de *[!UICONTROL Product Stock]*-status niet wordt toegepast voor *[!UICONTROL Related Product Rules]*.
feature: Products
role: Admin, Developer
exl-id: d6d3b25d-b10e-4ccb-a9c4-b5c1c7773eb6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-54739: *[!UICONTROL Product stock]* status niet toegepast voor *[!UICONTROL Related Product Rules]*

De ACSD-54739-patch verhelpt het probleem waarbij de *[!UICONTROL Product stock]* -status niet wordt toegepast op *[!UICONTROL Related Product Rules]* . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 wordt geïnstalleerd. De patch-id is ACSD-54739. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

*[!UICONTROL Product stock]* status wordt niet toegepast voor *[!UICONTROL Related Product Rules]* .

<u> Stappen om </u> te reproduceren:

1. Plaats de **[!UICONTROL Display Out of Stock Products]** configuratie aan *ja*.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** > **[!UICONTROL Search quantity attribute]** en plaats *ja* voor de voorwaarde van de bevorderingsregel.
1. Maak de regel Verwante producten. Ga naar **[!UICONTROL Product rule information]** > **[!UICONTROL Products to match]** > Een voorwaarde met kenmerkhoeveelheid toevoegen (selecteer in voorraad/uit voorraad).
1. Controleer de producten aan de voorzijde.

<u> Verwachte resultaten </u>:

Het product uit de voorraad of uit de voorraad komt overeen met *[!UICONTROL Related Product Rules]*.

<u> Ware resultaten </u>:

Het product in voorraad/in voorraad komt niet overeen met de waarde *[!UICONTROL Related Product Rules]*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
