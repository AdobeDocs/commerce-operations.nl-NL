---
title: 'ACSD-54264: Fout wanneer klant probeert uit te checken met verhandelbare aanhalingstekens'
description: Pas de ACSD-54264-patch toe om het Adobe Commerce-probleem op te lossen waarbij het foutbericht "U kunt het gevraagde kenmerk niet bijwerken. Rij-id:store_id" wordt weergegeven wanneer een klant een aanhalingsteken in een andere winkelweergave wil uitchecken met een verhandelbaar aanhalingsteken.
feature: B2B, Checkout
role: Admin, Developer
exl-id: b1696228-b2ed-44eb-9e75-bf25ccf2f1cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-54264: Fout verschijnt wanneer de klant probeert uit te checken met verhandelbare aanhalingstekens

Het ACSD-54264 flard lost de kwestie op waar een foutenmelding *u niet het gevraagde attribuut kunt bijwerken. Rij ID: store_id* verschijnt wanneer een klant probeert om met een verhandelbaar citaat van een andere archiefmening te controleren. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-54264. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een foutenmelding *U kunt niet de gevraagde attributen bijwerken. Rij ID: store_id* verschijnt wanneer een klant probeert om met een verhandelbaar citaat van een andere archiefmening te controleren.

<u> Eerste vereisten </u>:

Adobe Commerce B2B-modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Maak een extra winkelweergave voor de standaardwebsite.
1. Schakel *[!UICONTROL B2B Quote]* in de configuratie in.
1. Meld u aan als klant van een bedrijf in een van de winkelweergaven.
1. Voeg een product toe aan *[!UICONTROL Shopping Cart]*.
1. Het aanhalingsteken ter controle verzenden.
1. Als beheerder gaat u naar **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** en verzendt u het goedgekeurde aanhalingsteken.
1. Als bedrijfklant, verander de opslagmening in een verschillende archiefmening.
1. Probeer uit te checken.

<u> Verwachte resultaten </u>:

De klant plaatst een bestelling met dit citaat.

<u> Ware resultaten </u>:

* De fout treedt op bij het opslaan van de verzendgegevens:

  `You cannot update the request attribute. Row ID: store_id =#`

* De volgende fout wordt geregistreerd:

  `report.CRITICAL: Magento\Framework\Exception\InputException: You cannot update the requested attribute. Row ID: store_id = 2. in /app/code/Magento/NegotiableQuote/Plugin/Quote/Model/QuoteUpdateValidator.php:100`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
