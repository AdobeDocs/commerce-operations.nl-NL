---
title: 'ACSD-59865: [!UICONTROL Cart Price Rule] kan vorige regels niet annuleren vanwege onvoldoende producthoeveelheid'
description: Pas de ACSD-59865-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de waarde *Korting op aantal korting* in *Vast bedrag,** Percentage van korting op productprijs* en *Koop X krijg Y* [!UICONTROL Cart Price Rules] de actie van vorige regels niet meer annuleert.
feature: Price Rules
role: Admin, Developer
exl-id: 5838a740-018d-44c2-8135-54426ea08627
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# ACSD-59865: [!UICONTROL Cart Price Rule] kan vorige regels niet annuleren vanwege onvoldoende producthoeveelheid

De ACSD-59865-patch verhelpt het probleem waarbij de *[!UICONTROL Discount quantity step]* -waarde in *[!UICONTROL Fixed amount discount],* *[!UICONTROL Percent of product price discount],* en *[!UICONTROL Buy X get Y]* [!UICONTROL Cart Price Rules] niet langer de actie van vorige regels annuleert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 wordt geïnstalleerd. De patch-id is ACSD-59865. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De [!UICONTROL Cart Price Rule] kan eerder toegepaste regels niet annuleren omdat er onvoldoende producten in de winkelwagentje zijn.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als beheerder.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]** en klik op **[!UICONTROL Add New rule]** .
   * Plaats **[!UICONTROL Rule Name]** = *Test - 1*
   * Selecteer alle *Websites* en *groepen van de Klant*
   * Plaats **[!UICONTROL Priority]** = *0*
   * Ga naar de sectie **[!UICONTROL Actions]** :
      * Plaats **[!UICONTROL Apply]** = *Percentage van de korting van de productprijs*
      * Plaats **[!UICONTROL Discount amount]** = *10*
      * Reeks **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Plaats **[!UICONTROL Discount Qty Step (Buy X)]** = *0*
      * Plaats **[!UICONTROL Discard subsequent rules]** aan *Nr*
1. Wis de cache.
1. Ga naar de Storefront, voeg één punt aan de kar toe, en ga aan *checkout/kar* te werk.
1. Verifieer dat de *10%* korting op uw kar wordt toegepast.
1. Ga terug naar **[!UICONTROL Cart Price Rules]** en maak een nieuwe regel.
   * Plaats **[!UICONTROL Rule Name]** = *Test - 2*
   * Alles selecteren **[!UICONTROL Websites]** en **[!UICONTROL Customer Groups]**
   * Plaats **[!UICONTROL Priority]** = *2*
   * Navigeer naar de sectie **[!UICONTROL Actions]** :
      * Plaats **[!UICONTROL Apply]** = *Percentage van de korting van de productprijs*
      * Reeks **[!UICONTROL Discount amount]** = *20*
      * Reeks **[!UICONTROL Maximum Qty Discount is Applied To]** = *100*
      * Plaats **[!UICONTROL Discount Qty Step (Buy X)]** = *3*
1. Wis de cache.
1. Ga opnieuw naar de Storefront.
1. Werk de kar bij om de regels te vernieuwen. Verifieer dat de *10%* korting niet meer wordt toegepast.
1. Voeg punten aan uw kar toe tot de hoeveelheid de *waarde van de Stap* voldoet die voor de tweede regel wordt vereist.

<u> Verwachte resultaten </u>:

De eerste [!UICONTROL Cart Price Rule] wordt toegepast wanneer aan de voorwaarden van de tweede regel wordt voldaan.

<u> Ware resultaten </u>:

Prijsregels worden toegepast op de manier die is geconfigureerd in het dashboard voor beheerders.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
