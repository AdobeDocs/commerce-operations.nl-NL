---
title: 'ACSD-62056: Het uploaden van images voor configureerbaar product mislukt als MSI is geïnstalleerd'
description: Pas de ACSD-62056-patch toe om het Adobe Commerce-probleem op te lossen, waarbij images voor configureerbare producten niet worden toegevoegd als MSI is geïnstalleerd.
feature: Products, Media
role: Admin, Developer
source-git-commit: 9c186e936492ebcab3903949f40d73745d2a28d3
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056: Het uploaden van images voor configureerbaar product mislukt als MSI is geïnstalleerd

De ACSD-62056-patch verhelpt het probleem dat afbeeldingen voor configureerbare producten niet worden toegevoegd als MSI is geïnstalleerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 is geïnstalleerd. De patch-id is ACSD-62056. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer u een configureerbaar product bewerkt waarvoor [!UICONTROL Inventory Management/MSI] is ingeschakeld, werken de opties voor het toevoegen van afbeeldingen niet. Dit is van invloed op de opties [!UICONTROL Apply a single set of images to all SKUs] en [!UICONTROL Apply unique images by attribute to each SKU] .

<u> Eerste vereisten </u>:

[!UICONTROL Inventory Management/MSI] -modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe bron.
1. Maak een nieuw bestand en wijs de nieuwe bron toe.
1. Bewerk een configureerbaar product.
1. Klik op **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**.
1. Selecteer een van de volgende opties en voeg een afbeelding toe.

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u> Verwachte resultaten </u>:

De afbeeldingen worden toegevoegd.

<u> Ware resultaten </u>:

De afbeeldingen worden niet toegevoegd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
