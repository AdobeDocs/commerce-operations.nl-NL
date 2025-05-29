---
title: 'ACS2E-3841: De prijsregels voor winkelwagentjes voor producten die meerdere verzendingen hebben, zijn niet correct van toepassing wanneer subselect-voorwaarden worden gebruikt en gratis verzending is ingeschakeld'
description: Pas de ACS2E-3841-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de regels voor de kartprijs voor producten voor meerdere verzendingen niet correct worden toegepast wanneer subselect-voorwaarden worden gebruikt en gratis verzending is ingeschakeld.
feature: Shopping Cart, Price Rules
role: Admin, Developer
source-git-commit: 1abb32109d5ca4a90cdd1d210d1fae6a728699fd
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---


# ACS2E-3841: De prijsregels voor winkelwagentjes voor producten die meerdere verzendingen hebben, zijn niet correct van toepassing wanneer subselect-voorwaarden worden gebruikt en gratis verzending is ingeschakeld

De ACS2E-3841-patch stelt het probleem vast dat de regels voor de kartprijs van producten voor meerdere verzendingen niet correct worden toegepast wanneer subselect-voorwaarden worden gebruikt en gratis verzending is ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACP2E-3841. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p9

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.7-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prijsregels voor winkelwagentjes voor producten voor meerdere verzendingen zijn niet correct van toepassing wanneer subselecties worden gebruikt en gratis verzending is ingeschakeld.

<u> Eerste vereisten </u>:

**Montages:**
1. **[!UICONTROL Free Shipping]** = *Toegelaten*
1. **[!UICONTROL Minimum Order Amount]** = *99999999*

**Nodig categorieën:**
1. Categorie 1
1. Categorie 2

**Nodig producten:**
1. Producttest 1:
   1. Categorieën: Categorie 1
   1. Prijs: $ 45
1. Producttest 2:
   1. Categorieën: Categorie 2
   1. Prijs: $ 56,25 
      **(De prijzen moeten het zelfde zijn zoals hier getoond om de test te verzekeren correct werkt.)**

**de Regel van de Prijs van de Kar:**

Log in als beheerder en ga naar **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add new rule]** . Gebruik de volgende waarden:

**[!UICONTROL Rule Information]:**
1. **[!UICONTROL Rule Name]**: Gratis verzending testen
1. **[!UICONTROL Active]**: *ja*
1. **[!UICONTROL Websites]**: *Belangrijkste Website*
1. **[!UICONTROL Customer Groups]**: *NIET AANGEPAST IN, Algemeen, Groothandel, Retailer*
1. **[!UICONTROL Coupon]**: *Geen Coupon*
1. **[!UICONTROL Uses per Customer]**: *0*
1. **[!UICONTROL Priority]**: *1*

**[!UICONTROL Conditions]:**

**[!UICONTROL If ALL of these conditions are TRUE:]**


**[!UICONTROL If total amount (incl. tax) equals or greater than 100 for a subselection of items in cart matching ALL of these conditions:]**


**[!UICONTROL Category is]** *5,12,13*

Handelingen:

**[!UICONTROL Percent of product price discount]** = *10*

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de winkel.
2. Producttest toevoegen 1.
3. Voeg twee hoeveelheden producttest 2 toe.
4. Bezoek de kar.
5. Selecteer **[!UICONTROL Check Out with Multiple Addresses]** .

<u> Verwachte resultaten </u>:

Geen fouten.

<u> Ware resultaten </u>:

*500 fout*

*Bericht: Vervangen Functionaliteit: De impliciete omzetting van vlotter 112.5 aan int verliest precisie in /app/code/Magento/SalesRule/Model/Rule/Condition/Product/Subselect.php op lijn 214*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
