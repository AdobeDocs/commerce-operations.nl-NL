---
title: 'ACSD-58163: [!UICONTROL Cart Price Rule] past geen korting toe op overeenkomende [!UICONTROL Customer Segment] -winkelwagentje zonder couponcode'
description: Pas de ACSD-58163-patch toe om het Adobe Commerce-probleem op te lossen, waarbij [!UICONTROL Cart Price Rule] geen korting toepast voor een gast van de overeenkomende [!UICONTROL Customer Segment] -winkelwagen zonder couponcode.
feature: Products
role: Admin, Developer
exl-id: 209a50f7-32d9-40e9-bfd5-4658e4ca392d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-58163: [!UICONTROL Cart Price Rule] past geen korting toe op overeenkomende [!UICONTROL Customer Segment] -winkelwagentje zonder couponcode

De ACSD-58163-patch verhelpt het probleem waarbij [!UICONTROL Cart Price Rule] geen korting toepast op de overeenkomende [!UICONTROL Customer Segment] -winkelwagen zonder couponcode. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-58163. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!UICONTROL Cart Price Rule] past geen korting toe op een gast van de overeenkomende [!UICONTROL Customer Segment] -winkelwagen zonder couponcode.

<u> Stappen om </u> te reproduceren:

1. Klantsegment maken:
   * Voor bezoekers.
   * Met de voorwaarde om één product in het winkelwagentje te hebben.

1. Een *[!UICONTROL Cart Price Rule]* maken:
   * Zonder couponcode.
   * Met de voorwaarde om met het segment van de bezoekersklant aan te passen.

1. Maak een eenvoudig product.
1. Open storefront als gast.
1. Voeg één eenvoudig product aan de kar toe.
1. Ga naar de winkelwagentje.

<u> Verwachte resultaten </u>:

*[!UICONTROL Cart Price Rule]* korting wordt toegepast.

<u> Ware resultaten </u>:

*[!UICONTROL Cart Price Rule]* -korting wordt niet toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
