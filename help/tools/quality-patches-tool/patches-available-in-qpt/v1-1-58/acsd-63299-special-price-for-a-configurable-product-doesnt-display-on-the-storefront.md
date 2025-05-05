---
title: 'ACSD-63299: Speciale prijs voor een configureerbaar product wordt niet weergegeven op de winkel'
description: Pas de ACSD-63299-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het speciale prijskenmerk niet langer van invloed is op de weergave van speciale prijzen voor configureerbare producten.
feature: Catalog Management
Role: Admin, Developer
source-git-commit: 238d3fa6d7729f729aeb79c98ae28db331ad7509
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-63299: Speciale prijs voor een configureerbaar product wordt niet weergegeven op de winkel

De ACSD-63299-patch verhelpt het probleem waarbij het speciale prijskenmerk niet langer van invloed is op de weergave van speciale prijzen voor configureerbare producten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-63299. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

In [!DNL Adobe Commerce], beïnvloedt het veranderen van *Gebruikt in Product dat* waarde voor het speciale prijsattribuut niet meer hoe de speciale prijzen voor configureerbare producten worden getoond.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Products]** .
1. Zoek het kenmerk ***[!UICONTROL special_price]*** en navigeer naar **[!UICONTROL Storefront Properties]** .
1. Wijzig ***[!UICONTROL Used in Product Listing]*** in ***[!UICONTROL No] &#x200B;***.
1. Maak een configureerbaar product met één onderliggend element:
   * Naam en SKU: Testen
   * Prijs: $ 159,00
   * Optie genereren op basis van kleur. Een nieuwe kleur toevoegen: Blauw
   * Opslaan
1. Open het onderliggende product en voer de volgende stappen uit:
   * Stel een speciale prijs in op $99,90 in **[!UICONTROL Advanced Pricing]**
   * Wijzig [!UICONTROL Visibility] in **[!UICONTROL Catalog, Search]** .
1. Open de eenvoudige productpagina en bevestig dat de speciale prijs zichtbaar is.
1. Open de configureerbare productpagina.
1. Selecteer het blauwe product.

<u> Verwachte resultaten </u>:

De speciale prijs is op dezelfde manier zichtbaar als voor het eenvoudige product.

<u> Ware resultaten </u>:

1. De volledige prijs wordt getoond wanneer een configureerbaar product wordt geselecteerd.
1. Er is een wanverhouding tussen de secties *zo laag als...* ($99.90) en de daadwerkelijke prijs ($99.90 + $59.10 = $159.00).

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
