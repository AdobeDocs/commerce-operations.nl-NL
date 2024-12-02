---
title: 'ACSD-61200: Vorderingen op de heffingskorting voor korting in de totale verkoopberekeningen'
description: Pas ACSD-61200 flard toe om de kwestie van Adobe Commerce te bevestigen waar * [!UICONTROL Discount Tax Compensation Amount]* en * [!UICONTROL Shipping Discount Tax Compensation Amount]* in verkoop totale berekeningen ontbreken, veroorzakend discrepanties tussen de gegevens van de verkooporde en couponrapport.
feature: Reporting, Taxes
role: Admin, Developer
exl-id: eb908827-de29-4b2c-b094-b5db0931cd52
source-git-commit: 2e82c935145d71d0c66c531003fa51f564da6e41
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-61200: Vorderingen op de heffingskorting voor korting in de totale verkoopberekeningen

De ACSD-61200-patch verhelpt het probleem waarbij *[!UICONTROL Discount Tax Compensation Amount]* en *[!UICONTROL Shipping Discount Tax Compensation Amount]* ontbreken in *[!UICONTROL Total Amount]* - en *[!UICONTROL Total Amount Actual]* -berekeningen, wat resulteert in discrepanties tussen gegevens van de verkooporder en gegevens van het couponrapport. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 is geïnstalleerd. De patch-id is ACSD-61200. Het probleem wordt volgens de planning opgelost in Adobe Commerce versie 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

- Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

- Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onnauwkeurigheden in de gegevens van de verkooporder en de couponmelding omdat *[!UICONTROL Discount Tax Compensation Amount]* en *[!UICONTROL Shipping Discount Tax Compensation Amount]* ontbreken in de berekeningen van het verkooptotaal.

<u> Stappen om </u> te reproduceren:

1. Maak een [!UICONTROL Tax Zone] en een [!UICONTROL Tax Rule] .
1. Stel de volgende belastingconfiguraties in:
   - **[!UICONTROL Tax Class for Shipping]** = [!UICONTROL Taxable Goods]
   - **[!UICONTROL Catalog Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Shipping Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Apply Discount on Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Product Prices in Catalog]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Prices]** = [!UICONTROL Including Tax]
1. Werk de volgende weergaveinstellingen voor bestellingen, facturen en creditnota&#39;s bij:
   - **[!UICONTROL Display Prices]** = [!UICONTROL Including Tax]
   - **[!UICONTROL Display Subtotal]**= [!UICONTROL Including Tax]
   - **[!UICONTROL Display Shipping Amount]** = [!UICONTROL Including Tax]
1. Maak een [!UICONTROL Cart Price Rule] met coupon voor een korting van 10%.
1. Voltooi een bestelling met behulp van de coupon en maak een factuur en verzending.
1. Ga naar **[!UICONTROL Reports]** > **[!UICONTROL Sales]** > **[!UICONTROL Coupons]** en genereren een rapport.
1. Vergelijk de gegevens in de ordesamenvatting met die van het rapport.

<u> Verwachte resultaten </u>:

De berekeningen *[!UICONTROL Total Amount]* en *[!UICONTROL Total Amount Actual]* bevatten zowel *[!UICONTROL Discount Tax Compensation Amount]* als *[!UICONTROL Shipping Discount Tax Compensation Amount]* , die overeenkomen met het orderoverzicht en de rapportgegevens.

<u> Ware resultaten </u>:

De gegevens van de verkooporder en het couponrapport komen niet overeen, omdat *[!UICONTROL Discount Tax Compensation Amount]* en *[!UICONTROL Shipping Discount Tax Compensation Amount]* ontbreken in berekeningen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

- Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
- Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

[[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de gids van Hulpmiddelen zelf-te dienen.
