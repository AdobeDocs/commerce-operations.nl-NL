---
title: 'ACSD-63062: Onjuiste berekeningen van winkelwagenkortingen met meerdere overlappende regels'
description: Pas de ACSD-63062-patch toe om het Adobe Commerce-probleem op te lossen, waarbij onjuiste berekeningen van winkelwagentekortingen optreden wanneer meerdere overlappende regels worden toegepast.
feature: Price Rules
role: Admin, Developer
source-git-commit: 06fbdf730c670065e3105c62ae9604307b296a45
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-63062: Onjuiste berekeningen van winkelwagenkortingen met meerdere overlappende regels

Met de ACSD-63062-patch is het probleem opgelost waarbij onjuiste berekeningen van winkelwagentekortingen optreden wanneer meerdere overlappende regels worden toegepast. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-63062. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treden onjuiste berekeningen van winkelwagenkortingen op wanneer meerdere overlappende regels worden toegepast.

<u> Stappen om </u> te reproduceren:

1. Nieuwe instantie met voorbeeldgegevens installeren.
1. Maak drie eenvoudige producten:

   * simple1: $ 1.080
   * simple2: $ 260
   * simple3: $ 280

1. Maak vier *[!UICONTROL Cart Price Rules]* als volgt:

   * Regel 1:

      * *[!UICONTROL Priority]*: 100
      * *[!UICONTROL Conditions]* tabblad: gebruik het simple2-product ($280) als de totale hoeveelheid gelijk is aan of groter is dan 3
      * *[!UICONTROL Actions]* tab: SKU is simple2
      * *[!UICONTROL Fixed Amount Discount]*: $80

   * Regel 2:

      * *[!UICONTROL Priority]*: 200
      * *[!UICONTROL Actions]* tab: SKU is simple2
      * *[!UICONTROL Percentage of Product Price Discount]*: 20%

   * Regel 3:

      * *[!UICONTROL Priority]*: 300
      * *[!UICONTROL Conditions]* tab: Subtotaal is gelijk aan of groter dan $1000
      * *[!UICONTROL Fixed Amount Discount]* voor de hele winkelwagen: $100

   * Artikel 4:

      * *[!UICONTROL Priority]*: 400
      * *[!UICONTROL Conditions]* tabblad: gebruik het simple1-product ($1080) als de totale hoeveelheid gelijk is aan of groter is dan 2
      * *[!UICONTROL Actions]* tab: SKU is simple1
      * *[!UICONTROL Fixed Amount Discount]* voor de hele winkelwagen: $ 960

1. Ga naar de winkel en voeg de volgende producten met een bepaalde hoeveelheid toe aan de kar:

   * simple1 = 2
   * simple2 = 1
   * simple3 = 3

1. Controleer het winkelwagentje.

<u> Verwachte resultaten </u>:

De toegepaste korting is $1352.

<u> Ware resultaten </u>:

De toegepaste korting is $1525,33.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
