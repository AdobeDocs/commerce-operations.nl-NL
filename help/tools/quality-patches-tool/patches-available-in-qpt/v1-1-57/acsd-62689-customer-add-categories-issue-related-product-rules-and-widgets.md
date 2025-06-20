---
title: 'ACSD-62689: Kan geen categorieën toevoegen in [!UICONTROL Related Product Rules] en widgets na diepte 4'
description: Pas de ACSD-62689-patch toe om het Adobe Commerce-probleem op te lossen waarbij een klant na diepte 4 nesten geen categorieën in [!UICONTROL Related Product Rules] en widgets kan toevoegen.
feature: Categories
role: Admin, Developer
exl-id: 2506744a-01c8-462b-9a27-cd0bdb5664f9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-62689: Kan geen categorieën toevoegen in *[!UICONTROL Related Product Rules]* en widgets na diepte 4

>[!NOTE]
>
>Dit flard wordt vervangen door [ ACP2E-3689 ](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3689-issues-with-category-tree-display-reflect-anchor-non-anchor-relationships.md).

De ACSD-62689-patch verhelpt het probleem waarbij een klant na diepte vier nesten geen categorieën in *[!UICONTROL Related Product Rules]* en widgets kan toevoegen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-62689. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een klant kan geen categorieën in *[!UICONTROL Related Product Rules]* en widgets toevoegen na diepte vier het nesten.

<u> Stappen om </u> te reproduceren:

1. Maak twee categorieën met de naam *[!UICONTROL Anchor]* en *[!UICONTROL Non-Anchor]* onder de standaardhoofdcategorie.
   * Controleer of de markering *[!UICONTROL Is Anchor]* is uitgeschakeld voor de categorie *[!UICONTROL Non-Anchor]* .
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Widgets]** en maak een widget.
1. Selecteer onder *[!UICONTROL Layout Updates]* de optie **[!UICONTROL Non-Anchor Categories]** in het veld *[!UICONTROL Display on]* .
1. Klik op **[!UICONTROL Specific Categories]**.
1. Klik op het pictogram voor het selecteren van categorieën.
1. Vouw de hoofdcategorie uit.
1. Controleer de categorieën. Beide moeten zijn uitgeschakeld en niet selecteerbaar.
1. Selecteer onder *[!UICONTROL Layout Updates]* de optie **[!UICONTROL Anchor Categories]** in het veld *[!UICONTROL Display on]* . Voer vervolgens de stappen 5 en 6 uit.
1. Controleer de categorieën. Beide moeten zijn ingeschakeld en kunnen worden geselecteerd.

<u> Verwachte resultaten </u>:

In stap 7 moet alleen de categorie *[!UICONTROL Non-Anchor]* kunnen worden geselecteerd. In stap 9 moet de categorie *[!UICONTROL Anchor]* selecteerbaar zijn.

<u> Ware resultaten </u>:

In stap 7 kunnen beide categorieën niet worden geselecteerd. In stap 9 kunnen beide categorieën worden geselecteerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

