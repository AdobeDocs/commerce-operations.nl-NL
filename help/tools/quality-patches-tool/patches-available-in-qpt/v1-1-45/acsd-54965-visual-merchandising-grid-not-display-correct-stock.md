---
title: 'ACSD-54965: [!UICONTROL Visual Merchandising] op het raster wordt het juiste bestand niet weergegeven'
description: Pas de ACSD-54965-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het [!UICONTROL Visual Merchandising] -raster niet de juiste voorraad weergeeft wanneer een product wordt toegewezen aan aangepaste voorraad.
feature: Merchandising, Categories
role: Admin, Developer
source-git-commit: d722ba5ba25ffc03d87b9eddeb2830353124055d
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965: [!UICONTROL Visual Merchandising] in het raster wordt de juiste voorraad niet weergegeven

De ACSD-54965-patch verhelpt het probleem waarbij het [!UICONTROL Visual Merchandising] -raster niet de juiste voorraad weergeeft wanneer een product aan aangepaste voorraad wordt toegewezen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-54965. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het raster [!UICONTROL Visual Merchandising] geeft niet de juiste voorraad weer wanneer een product wordt toegewezen aan aangepaste voorraad.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe bron.
1. Maak een nieuwe voorraad.
1. Twee producten maken:
   * Eén product met alleen de aangepaste voorraad.
   * Eén product met alleen de standaardvoorraad.
1. Voeg deze producten toe aan een categorie.
1. Ga naar het [!UICONTROL visual Merchandising] raster (*[!UICONTROL Products in Category]*).

<u> Ware Resultaten </u>:

In het *[!UICONTROL All Store Views]* bereik geeft het product met aangepaste voorraad geen hoeveelheid weer. Alleen wanneer het bereik van *[!UICONTROL Default Store View]* is geselecteerd, wordt in de aangepaste voorraad de hoeveelheid van het product weergegeven.

<u> Verwachte Resultaten </u>:

Het raster bevat alle aandeleninformatie als het bereik *[!UICONTROL All Store Views]* is.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
