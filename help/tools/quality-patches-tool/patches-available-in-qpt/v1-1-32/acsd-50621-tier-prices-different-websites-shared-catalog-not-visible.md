---
title: 'ACSD-50621: Niveau-prijzen voor verschillende websites in gedeelde catalogus zijn niet zichtbaar'
description: Pas de ACSD-50621-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de prijzen op niveaus voor verschillende websites in de gedeelde catalogus niet zichtbaar zijn wanneer u ze bewerkt in een omgeving met meerdere websites.
feature: Catalog Management, Orders
role: Admin
exl-id: 2256dee7-e544-4723-9753-ba9cf7247880
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-50621: Niveau-prijzen voor verschillende websites in gedeelde catalogus zijn niet zichtbaar

De ACSD-50621-patch verhelpt het probleem dat de prijzen op niveaus voor verschillende websites in de gedeelde catalogus niet zichtbaar zijn wanneer deze worden bewerkt in een omgeving met meerdere websites. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-50621. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Niveauprijzen voor verschillende websites in de gedeelde catalogus zijn niet zichtbaar wanneer u deze in een omgeving met meerdere websites bewerkt.

<u> Stappen om </u> te reproduceren:

1. Stel de waarde **[!UICONTROL Catalog Price Scope]** in op **[!UICONTROL Website]** .
1. Maak een aanvullende website, winkel en voorvertoning.
1. Maak een eenvoudig product en wijs dit toe aan alle websites.
1. Een aangepaste gedeelde catalogus maken.
1. Ga naar **[!UICONTROL Set Pricing and Structure]** voor de aangepaste gedeelde catalogus die u hebt gemaakt.
1. In Stap 1: selecteer producten voor catalogus. Voeg het eenvoudige product toe dat u hebt gemaakt.
1. In stap 2: stel aangepaste prijzen in en klik op **[!UICONTROL Configure]** .
1. Stel verschillende laagprijzen in voor verschillende websites.
1. Selecteer **[!UICONTROL Done]** en klik op **[!UICONTROL Generate Catalog]** en klik vervolgens op **[!UICONTROL Save]** .
1. Uitsnijden uitvoeren.
1. Navigeer naar **[!UICONTROL Set Pricing and Structure]** > **[!UICONTROL Configure]** > **[!UICONTROL Next]** > **[!UICONTROL Configure]** en controleer de laagprijs.

<u> Verwachte resultaten </u>:

Alle eerder geconfigureerde laagprijzen voor verschillende websites zijn aanwezig.

<u> Ware resultaten </u>:

Eerder geconfigureerde Tier-prijzen zijn niet aanwezig.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
