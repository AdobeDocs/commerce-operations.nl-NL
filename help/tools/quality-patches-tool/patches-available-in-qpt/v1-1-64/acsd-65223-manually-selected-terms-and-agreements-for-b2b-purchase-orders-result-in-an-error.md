---
title: 'ACSD-65223: handmatig geselecteerde voorwaarden en overeenkomsten voor inkooporders van B2B resulteren in een fout'
description: Pas de ACSD-65223-patch toe om het Adobe Commerce-probleem op te lossen dat ertoe leidt dat met [!UICONTROL Purchase Orders] gemaakte bestellingen niet met online betalingsmethoden zoals creditcards kunnen worden voltooid wanneer de voorwaarden voor het afrekenen vereist zijn.
feature: B2B, Purchase Orders
role: Admin, Developer
source-git-commit: 57c0cb63f1e2c7b12d11b759eddf0d21b5db78b2
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# ACSD-65223: handmatig geselecteerde voorwaarden en overeenkomsten voor inkooporders van B2B resulteren in een fout

De ACSD-65223-patch verhelpt het probleem dat met **[!UICONTROL Purchase Orders]** gemaakte bestellingen niet met online betalingsmethoden zoals creditcards kunnen worden voltooid wanneer de voorwaarden voor het afrekenen vereist zijn. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACSD-65223.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) B2B 1.5.1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) B2B 1.5.1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als de voorwaarden vereist zijn om een bestelling te plaatsen en u een bestelling wilt voltooien die u met [!UICONTROL Purchase Orders] hebt gemaakt, kan de bestelling niet worden geplaatst met behulp van online betalingsmethoden zoals creditcards.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** en kies **[!UICONTROL B2B Features]** .
1. Plaats **[!UICONTROL Enable Company]** en **[!UICONTROL Enable Purchase Orders]** aan *ja*.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Terms and Conditions]** en maak een nieuwe voorwaarde. Stel **[!UICONTROL Applied]** in op *[!UICONTROL Manually]* .
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** en plaats **[!UICONTROL Enable Terms and Conditions]** aan *ja*.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment Methods]** en configureer [!DNL Braintree] .
1. Creëer in de winkel een bedrijf.
1. Ga in de beheerder naar **[!UICONTROL Customers]** > **[!UICONTROL Companies]** .
1. Het bedrijf goedkeuren en **[!UICONTROL Purchase Orders]** toestaan.
1. Meld u op de voorzijde aan bij de account.
1. Voeg een item aan het winkelwagentje toe.
1. Plaats een volgorde met **[!UICONTROL Purchase Order]** .
1. Klik op het tabblad **[!UICONTROL Purchase Orders]** in het dashboard van de klant.
1. Maak een bestelling op basis van de nieuwe inkooporder. Selecteer vervolgens creditcard als betalingsmethode.
1. Ga akkoord met de voorwaarden.
1. Plaats de bestelling.

<u> Verwachte resultaten </u>:

U kunt een bestelling plaatsen met een online betalingsmethode op goedgekeurde inkooporders als de voorwaarden en bepalingen vereist zijn voor het afrekenen.

<u> Ware resultaten </u>:

U kunt geen bestelling plaatsen met een online betalingsmethode op goedgekeurde inkooporders als de voorwaarden en bepalingen vereist zijn voor afhandeling.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
