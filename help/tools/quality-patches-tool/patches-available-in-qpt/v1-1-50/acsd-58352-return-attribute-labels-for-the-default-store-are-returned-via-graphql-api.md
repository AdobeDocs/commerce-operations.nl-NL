---
title: 'ACSD-58352: De kenmerketiketten van de terugkeer voor de standaardopslag zijn teruggekeerd via  [!DNL GraphQL]  API'
description: Pas ACSD-58352 flard toe om de kwestie van Adobe Commerce te bevestigen waar de etiketten van de terugkeerattributen voor de standaardopslag via  [!DNL GraphQL]  API zijn teruggekeerd wanneer een niet-standaardopslagmening in de verzoekkopbal wordt gespecificeerd.
feature: GraphQL, Returns
role: Admin, Developer
exl-id: e513039e-42cd-4dac-963b-3068ba8bf7ee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-58352: Retourkenmerklabels voor de standaardwinkel worden geretourneerd via de [!DNL GraphQL] API

De ACSD-58352-patch verhelpt het probleem waarbij de labels van retourneringskenmerken voor de standaardwinkel via de [!DNL GraphQL] API worden geretourneerd wanneer een niet-standaard opslagweergave wordt opgegeven in de aanvraagheader. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-58352. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Retourkenmerklabels voor de standaardwinkel worden via de [!DNL GraphQL] API geretourneerd.

<u> Stappen om </u> te reproduceren:

1. Schakel de lus **[!UICONTROL Return Merchandising Authorization]** in.
1. Maak een *[!UICONTROL Additional Store]* en een *[!UICONTROL Store View]* onder de standaardwebsite.
1. Bewerk het retourkenmerk van **[!UICONTROL Reason for Return]** en voeg labels toe voor alle winkelweergaven.
1. Maak een *[!UICONTROL Order]* .
1. Maak een *[!UICONTROL Return]* voor die volgorde. Zorg ervoor dat de *[!UICONTROL Return]* de *[!UICONTROL Pending]* -status heeft.
1. Een query van de klant verzenden [!DNL GraphQL] met de opgegeven niet-standaard [!UICONTROL Store View] in de koptekst:

   ```
   query {
       customer {
           returns {
               items {
                   items {
                       custom_attributes {
                           label
                           value
                       }
                   }
               }
           }
       }
   }
   ```

1. Neem de reactie waar.

<u> Verwachte resultaten </u>

Retourlabels in de reactie [!DNL GraphQL] zijn voor de [!UICONTROL Store View] -set in de aanvraagkoptekst.

<u> Ware resultaten </u>:

Retourlabels in de reactie [!DNL GraphQL] zijn voor de standaardinstelling [!UICONTROL Store View] .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
