---
title: 'ACSD-46617: **[!UICONTROL Continue to Checkout] ** knoop grayed uit wanneer subtotaal groter dan gevormde minimumordehoeveelheid'
description: Pas ACSD-46617 flard toe om de kwestie van Adobe Commerce op te lossen waar de **[!UICONTROL Continue to Checkout] ** knoop uit grayed is zelfs als subtotal groter is dan de gevormde minimumordehoeveelheid.
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617: &quot;[!UICONTROL Continue to Checkout]&quot;knoop grayed uit wanneer subtotal groter dan &quot;[!UICONTROL Minimum Order Amount]&quot;

Deze ACSD-46617-patch lost het probleem op waarbij de knop **[!UICONTROL Continue to Checkout]** grijs wordt weergegeven, zelfs als het subtotaal groter is dan de geconfigureerde minimale orderhoeveelheid. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 wordt geïnstalleerd. De patch-id is ACSD-46617. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De knop **[!UICONTROL Continue to Checkout]** wordt grijs weergegeven, zelfs als het subtotaal groter is dan de geconfigureerde minimumorderhoeveelheid.

<u> Stappen om </u> te reproduceren:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** en stel het volgende in:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * &#x200B;
     [!UICONTROL Minimum Amount]: *2*

1. Maak een [!UICONTROL Cart Price Rule] .
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * &#x200B;
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Maak een product met een prijs van $25.
1. Voeg het product toe aan de kar.
1. Ga naar het winkelwagentje, selecteer de methode $5 **[!UICONTROL Flat Rate shipping]** en pas de couponcode toe.
1. Ga naar de kassa, voltooi de verzending en navigeer naar de sectie **[!UICONTROL Paytment]** .
1. Ga terug naar de winkelwagentje.

<u> Verwachte resultaten </u>:

Er is geen fout opgetreden met betrekking tot het minimale orderbedrag, aangezien het totaal van $2,4 groter is dan het vereiste bedrag van $2.

<u> Ware resultaten </u>:

* Er is een fout opgetreden met betrekking tot het minimale orderbedrag, zelfs als het totaal van $2.4 groter is dan het minimale bestelbedrag van $2.
* De knop **[!UICONTROL Continue to Checkout]** wordt grijs weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
