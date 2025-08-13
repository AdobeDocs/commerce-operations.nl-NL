---
title: 'ACSD-66084: ` row_total_incl_tax'' keert dichtbij-nul in plaats van 0.00 voor volledig verdisconteerde punten in orde API terug'
description: Pas de ACSD-66084-patch toe om het Adobe Commerce-probleem op te lossen, waarbij row_total_incl_tax is geretourneerd als een restwaarde van bijna nul in plaats van 0,00 voor items met volledige kortingen in de API-reactie voor bestelling.
feature: Orders, REST, Taxes, Payments, Checkout
role: Admin, Developer
type: Troubleshooting
exl-id: 421c6fe6-b6b1-4f33-acb6-fbd4306bcc4c
source-git-commit: 951738a4c671ed6fcc47b2a928d2110c78763d26
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# ACSD-66084: `row_total_incl_tax` retourneert bijna nul in plaats van 0,00 voor volledig gedisconteerde items in volgorde-API

De ACSD-66084-patch verhelpt het probleem waarbij `row_total_incl_tax` wordt geretourneerd als een restwaarde van bijna nul in de bestelling-API-respons in plaats van 0,00 voor items met volledige kortingen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 wordt geïnstalleerd. De patch-id is ACSD-66084. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`row_total_incl_tax` wordt geretourneerd als een restwaarde van bijna nul in de API-reactie voor bestelling in plaats van 0,00 voor items met volledige korting.

<u> Stappen om </u> te reproduceren:

1. Maak een product met een prijs en een speciale prijs. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > Klikken **[!UICONTROL Add Product]** > stel **[!UICONTROL Price]** in op $25 en **[!UICONTROL Special Price]** op $16.99 onder **[!UICONTROL Advanced Pricing]** .
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Taxes]** > **[!UICONTROL Tax Zones and Rates]** en voeg een frequentie van 20% toe. Ga vervolgens naar **[!UICONTROL Tax Rules]** en maak een regel en wijs
   **[!UICONTROL Taxable Goods]** als de productbelastingklasse.
1. Maak een verkoopregel met een korting van 100% en een coupon. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** en voeg een regel toe met een korting van 100%. Gebruik vervolgens **[!UICONTROL Specific Coupon]** en voer de code in.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > en configureer belastinginstellingen.
1. Gratis verzending inschakelen. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL Free Shipping]** . Stel **[!UICONTROL Enabled]** in op **[!UICONTROL Yes]** en pas de instellingen aan.
1. Ga naar de productpagina en selecteer **[!UICONTROL Add to Cart]** . Ga naar de winkelwagentje en pas de couponcode toe.
1. Plaats de bestelling bij de toepasselijke belastingzone.
1. Genereer een beheertoken (API) via REST API.
1. Bestelgegevens ophalen via REST API.
1. Controleer `row_total_incl_tax` in de reactie.

<u> Verwachte resultaten </u>:

`row_total_incl_tax` retourneert een valutawaarde zoals `0.00` wanneer het item volledig wordt gedisconteerd.

<u> Ware resultaten </u>:

`row_total_incl_tax` retourneert een zwevende-kommawaarde die bijna nul is, zoals `3.5527136788005e-15` , hetgeen niet geschikt is voor valutaweergave.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
