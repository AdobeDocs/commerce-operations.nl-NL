---
title: 'ACSD-48910: Gebundeld product met meerdere bronnen heeft geen voorraad na factuur en verzending'
description: Pas de ACSD-48910-patch toe om het Adobe Commerce-probleem op te lossen waarbij het gebundelde product dat aan meerdere bronnen is toegewezen, uit voorraad raakt nadat een bestelling is gefactureerd en verzonden, zelfs als het nog steeds een hoeveelheid heeft die niet gelijk is aan nul.
feature: Products, Inventory
role: Admin, Developer
exl-id: c8d86531-2db5-4115-92d5-a8d391c4f75d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-48910: Gebundeld product met meerdere bronnen heeft geen voorraad na factuur en verzending

De ACSD-48910-patch verhelpt de kwestie waar het gebundelde product dat aan meerdere bronnen is toegewezen uit voorraad komt nadat een bestelling is gefactureerd en verzonden, zelfs als het nog steeds een hoeveelheid heeft die niet gelijk is aan nul. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 wordt geïnstalleerd. De patch-id is ACSD-48910. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het gebundelde product dat aan veelvoudige bronnen wordt toegewezen gaat uit voorraad na facturering en verzending, zelfs als het nog beschikbaar is.

<u> Stappen om </u> te reproduceren:

1. Maak twee websites.
1. Maak twee weergaven voor winkels/winkels (één per website).
1. Maak twee eenvoudige producten (qty = 10) en wijs deze toe aan zowel voorraden als websites.
1. Maak een gebundeld product en voeg deze eenvoudige producten eraan toe. Wijs het gebundelde product aan beide websites toe.
1. Ga naar de winkel en voeg het gebundelde product aan de kar toe.
1. Check uit en plaats de bestelling.
1. Van Admin, factuur en verzend de orde.

<u> Verwachte resultaten </u>:

Het gebundelde product blijft in voorraad omdat we slechts 1 van de 10 artikelen hebben gekocht.

<u> Ware resultaten </u>:

Het gebundelde product wijzigt zijn status in out-of-stock.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
