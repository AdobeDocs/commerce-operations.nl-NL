---
title: 'ACSD-55305: Pop-up vastzetten tijdens bewerken door bedrijfsgebruiker in [!UICONTROL My Account]'
description: Pas de ACSD-55305-patch toe om het Adobe Commerce-probleem op te lossen waarbij [!UICONTROL Edit Company User] popup op de pagina [!UICONTROL My Account] &gt; [!UICONTROL Company Structure] vastloopt met een lader op het scherm.
feature: Companies, B2B
role: Admin, Developer
exl-id: eeb2b136-022f-42d5-85e2-85537f4677d6
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-55305: Pop-up vastzetten tijdens bewerken door bedrijfsgebruiker in [!UICONTROL My Account]

De ACSD-55305-patch verhelpt het probleem waarbij [!UICONTROL Edit Company User] popup op de pagina [!UICONTROL My Account]> [!UICONTROL Company Structure] vastloopt met een lader op het scherm. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.43 wordt geïnstalleerd. De patch-id is ACSD-55305. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fout op wanneer u probeert de pop-up *[!UICONTROL Edit Company User]* op de pagina *[!UICONTROL My Account]* > *[!UICONTROL Company Structure]* te gebruiken, omdat deze vastloopt met een lader die op het scherm wordt weergegeven.

<u> Stappen om </u> te reproduceren:

1. Een B2B-bedrijf oprichten.
1. Maak een kenmerk met meerdere selecties voor klanten.
1. Wijs een waarde aan het pas gecreëerde attribuut voor bedrijfbeheerder toe.
1. Meld u aan als bedrijfsbeheerder.
1. Ga naar [!UICONTROL account dashboard] en navigeer naar **[!UICONTROL Company Structure]** .
1. Selecteer de gebruiker.
1. Klik op **[!UICONTROL Edit Selected]** .

<u> Verwachte resultaten </u>:

Het pop-upvenster van het formulier wordt correct weergegeven en biedt de mogelijkheid om bedrijfsgegevens te bewerken.

<u> Ware resultaten </u>:

Het pop-upvenster van het formulier wordt weergegeven zonder mogelijkheid om te bewerken.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
