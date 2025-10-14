---
title: 'ACSD-49706: standaardwaarde opgeslagen voor kenmerk van visueel staal wanneer geen waarde is geselecteerd'
description: Pas de ACSD-49706-patch toe om het Adobe Commerce-probleem op te lossen waarbij een standaardwaarde wordt opgeslagen voor een visueel staalkenmerk wanneer geen waarde is geselecteerd.
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706: standaardwaarde opgeslagen voor kenmerk van visueel staal wanneer geen waarde is geselecteerd

De ACSD-49706-patch verhelpt het probleem waarbij een standaardwaarde wordt opgeslagen voor een visueel staalkenmerk wanneer geen waarde is geselecteerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49706. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als er geen waarde is geselecteerd, wordt een standaardwaarde voor een visueel staalkenmerk opgeslagen.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** .
1. Klik op **[!UICONTROL Add New Attribute]**.
1. Vul de velden in.

   * Bijvoorbeeld, kies inputtype *[!UICONTROL Visual Swatch]*, en voeg veelvoudige opties (zoals *Rood* toe, *Groen*). Kies een van deze opties als standaardopties.
   * Klik op **[!UICONTROL Save Attribute]**.

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]** .
1. Bewerk de kenmerkset van *[!UICONTROL Default]* .
1. Verplaats *[!UICONTROL New Attribute]* van de kolom *[!UICONTROL Unassigned Attributes]* naar de map *[!UICONTROL Product Details]* in de middelste kolom.

   * Klik op **[!UICONTROL Save]**.

1. Maak een nieuw product met de kenmerkset *[!UICONTROL Default]* .

   * Laat de *[!UICONTROL New Attribute]* leeg en sla deze op.

1. Als de waarde eenmaal is opgeslagen, wordt deze weergegeven in *[!UICONTROL New Attribute]* .

<u> Verwachte resultaten </u>:

Er wordt standaard geen waarde toegewezen aan *[!UICONTROL New Attribute]* .

<u> Ware resultaten </u>:

Bij het opslaan van een product wordt een standaardwaarde op het kenmerk toegepast.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
