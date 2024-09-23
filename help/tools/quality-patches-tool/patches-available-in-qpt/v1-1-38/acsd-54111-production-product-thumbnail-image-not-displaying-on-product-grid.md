---
title: 'ACSD-54111: Afbeelding met productminiaturen wordt niet weergegeven'
description: Pas de ACSD-54111-patch toe om het Adobe Commerce-probleem op te lossen, waarbij alle afbeeldingen worden vervangen door de standaardvoorlopige afbeelding van het product.
feature: Products
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-54111: Afbeelding met productminiatuur wordt niet weergegeven

Met de ACSD-54111-patch is het probleem verholpen waarbij alle afbeeldingen worden vervangen door de standaardvoorlopige afbeelding van het product. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.38 wordt geïnstalleerd. De patch-id is ACSD-5411. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden): 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden): 2.4.2 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De miniatuurafbeelding van het product wordt niet weergegeven.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** > **[!UICONTROL Edit Theme]** > **[!UICONTROL Product Image Watermarks]** > **[!UICONTROL Thumbnail]** .
1. Upload de afbeelding met een miniatuur en stel de afbeeldingspositie in op *[!UICONTROL Center]* .
1. Klik op **[!UICONTROL Save Configuration]** .
1. Cache wissen.
1. Ga naar de winkel als gast/klant.
1. Voeg een product toe aan de kar.
1. Voer `bin/magento catalog:image:resize` uit vanaf de console.
1. Open de miniwinkelwagentje op de voorkant of het productraster op de achtergrond om te zien of de miniaturen van de afbeelding zichtbaar zijn.

<u> Verwachte resultaten </u>:

Productafbeeldingen worden niet vervangen door de voorlopige afbeelding.

<u> Ware resultaten </u>:

Afbeeldingen van producten worden vervangen door de standaardafbeelding van de tijdelijke aanduiding voor het product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.