---
title: 'ACS2E-4050: [!UICONTROL Free Shipping] niet toegepast bij afhandeling voor meerdere verzendingen'
description: Pas de ACP2E-4050-patch toe om het Adobe Commerce-probleem op te lossen, waarbij [!UICONTROL Free Shipping] niet wordt toegepast tijdens het afrekenen van meerdere adressen wanneer [!UICONTROL Cart Price Rules] subselect-voorwaarden en producten met specifieke prijzen omvat.
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
exl-id: 447d2460-5c29-4849-81d0-a9aaf0a758b4
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACS2E-4050: **[!UICONTROL Free Shipping]** niet toegepast bij afhandeling voor meerdere verzendingen

De ACP2E-4050-patch verhelpt het probleem dat **[!UICONTROL Free Shipping]** niet wordt toegepast tijdens het afrekenen van meerdere verzendingen wanneer **[!UICONTROL Cart Price Rules]** subselectieve voorwaarden en producten met specifieke prijzen omvat. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACP2E-4050. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p10

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

**[!UICONTROL Free Shipping]** wordt niet toegepast tijdens afhandeling voor meerdere verzendingen wanneer **[!UICONTROL Cart Price Rules]** subselectieve voorwaarden en producten met specifieke prijzen omvat.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount met twee adressen.
1. Laat **[!UICONTROL Free Shipping]** toe en plaats **[!UICONTROL Minimum Order Amount]** aan *999999*.
1. Navigeer naar [!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules] en maak een regel voor de tekenprijs met de volgende voorwaarden:

```text
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. Voorbeeldgegevens installeren.
1. Voeg de volgende producten in de opgegeven volgorde toe aan het winkelwagentje:
   * Wayfarer Messenger Bag
   * Olivia 1/4 Zip Light Jacket
   * Sprite Yoga Companion Kit.
1. Open het winkelwagentje en controleer of de optie **[!UICONTROL Free Shipping]** beschikbaar is.
1. Klik op **[!UICONTROL Check Out with Multiple Addresses]** .
1. Selecteer een ander verzendadres voor het eenvoudige product.
1. Klik op **[!UICONTROL Go to Shipping Information]** .

<u> Verwachte resultaten </u>:

**[!UICONTROL Free Shipping]** is van toepassing op configureerbare en bundelproductverzendingen.

<u> Ware resultaten </u>:

**[!UICONTROL Free Shipping]** is niet beschikbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
