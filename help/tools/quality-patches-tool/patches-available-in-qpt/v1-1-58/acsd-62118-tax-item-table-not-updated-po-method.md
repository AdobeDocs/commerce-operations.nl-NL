---
title: 'ACSD-62118: tabel "sales_order_tax_item" is niet volledig bijgewerkt voor B2B-orders die zijn geplaatst met de methode [!UICONTROL Purchase Order]'
description: Pas de ACSD-62118-patch toe om het Adobe Commerce-probleem op te lossen waarbij de tabel "sales_order_tax_item" niet volledig wordt bijgewerkt wanneer B2B-orders worden geplaatst met de methode [!UICONTROL Purchase Order] .
feature: Purchase Orders, B2B
role: Admin, Developer
source-git-commit: 5812b90fe07a084a1d3487784d0f36a2b7958286
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# ACSD-62118: `sales_order_tax_item` tabel niet volledig bijgewerkt voor B2B-orders die zijn geplaatst met de methode [!UICONTROL Purchase Order]

De ACSD-62118-patch verhelpt het probleem waarbij de `sales_order_tax_item` -tabel niet volledig wordt bijgewerkt wanneer een B2B-volgorde wordt geplaatst met de *[!UICONTROL Purchase Order]* -methode. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-62118. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer B2B-orders worden geplaatst met de methode *[!UICONTROL Purchase Order]* , wordt de tabel `sales_order_tax_item` niet volledig bijgewerkt. Deze kwestie beïnvloedt belastingberekeningen en orderverwerking. De array `applied_taxes` is met name leeg wanneer de volgorde wordt opgevraagd via de API en zowel `tax_item_amount` als `tax_item_percent` zijn NULL.

<u> Stappen om </u> te reproduceren:

1. Voeg belastingregels toe voor zowel **[!UICONTROL Product]** als **[!UICONTROL Shipping]** .
1. Schakel de methode **[!UICONTROL Purchase Order]** in de bedrijfsinstellingen in.
1. Meld u aan als Admin-gebruiker van het bedrijf.
1. Plaats een **[!UICONTROL Purchase Order]** met behulp van een methode voor offlinebetaling.
1. Nadat [!UICONTROL Purchase Order] automatisch is goedgekeurd en in een bestelling is omgezet, controleert u de belastinggegevens in de `sales_order_tax_item` -tabel en via de REST API.

<u> Verwachte resultaten </u>:

* De tabel `sales_order_tax_item` moet `tax_item` -gegevens bevatten.
* De array `applied_taxes` moet de juiste belastinggegevens weergeven in de API-reactie voor inkooporders, net als bij andere betalingsmethoden (bijvoorbeeld Cheque/Money Order).

<u> Ware resultaten </u>:

* De tabel `sales_order_tax_item` bevat geen `tax_item` -gegevens.
* De arrays `applied_taxes` en `item_applied_taxes` zijn leeg in de API-respons voor de *[!UICONTROL Purchase Order]* .
* Er worden geen belastinggegevens weergegeven wanneer de betalingsmethode *[!UICONTROL Purchase Order]* wordt gebruikt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
