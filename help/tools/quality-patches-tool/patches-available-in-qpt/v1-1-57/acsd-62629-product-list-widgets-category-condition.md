---
title: 'ACSD-62629: productlijst in widgets geeft onjuiste categorieën weer'
description: Pas de ACSD-62629-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een productlijst die in widgets wordt gebruikt, niet voldoet aan de categorievoorwaarde.
feature: Page Content
role: Admin, Developer
source-git-commit: 6440738bf01a95a2f1e666826685d325bf393249
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---


# ACSD-62629: productlijst in widgets geeft onjuiste categorieën weer

De ACSD-62629-patch verhelpt het probleem waarbij de productlijst die in widgets wordt gebruikt, niet voldoet aan de categorievoorwaarde. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-62629. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De lijst met producten die in widgets wordt gebruikt, voldoet niet aan de categorievoorwaarde.

<u> Stappen om </u> te reproduceren:

1. Maak een [!UICONTROL simple product] met de naam TEST en voeg deze toe aan categorie 1.
1. Maak een testupdate zonder einddatum voor het TEST-product. Wacht tot de update actief wordt.
1. Maak een [!UICONTROL configurable product] genaamd TEST 2 met twee onderliggende producten en voeg deze toe aan categorie 2.
1. Maak nog een [!UICONTROL simple product] genaamd TEST 5 en voeg deze toe aan categorie 1.
1. Voer een volledige herindex uit.
1. Navigeer naar **[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** en bewerk de startpagina.
1. Voeg een [!UICONTROL Products] widget toe met *[!UICONTROL Appearance]* ingesteld op *[!UICONTROL Product Carousel]* en *[!UICONTROL Category]* ingesteld op Categorie 2. Sla de pagina op.
1. Ga naar de voorkant en open de homepage.

<u> Verwachte resultaten </u>:

Alleen het (configureerbare) TEST 2-product moet op de pagina aanwezig zijn.

<u> Ware resultaten </u>:

De pagina bevat zowel de producten TEST 5 (eenvoudig) als TEST 2 (configureerbaar).

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
