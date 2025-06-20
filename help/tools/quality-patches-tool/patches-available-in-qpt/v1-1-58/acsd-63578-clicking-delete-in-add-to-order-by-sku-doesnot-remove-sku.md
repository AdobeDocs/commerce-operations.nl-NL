---
title: 'ACSD-63578: klik op het pictogram [!UICONTROL Delete] in [!UICONTROL Add to Order by SKU] om SKU niet te verwijderen'
description: Pas de ACSD-63578-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het klikken op het pictogram [!UICONTROL Delete] in [!UICONTROL Add to Order by SKU] in Admin de SKU niet verwijdert.
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-63578: als u op het pictogram **[!UICONTROL Delete]** in *[!UICONTROL Add to Order by SKU]* klikt, wordt SKU niet verwijderd

De ACSD-63578-patch verhelpt het probleem dat wanneer u op het pictogram **[!UICONTROL Delete]** in *[!UICONTROL Add to Order by SKU]* in Admin klikt, de SKU niet wordt verwijderd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-63578. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p7

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u op het pictogram **[!UICONTROL Delete]** in *[!UICONTROL Add to Order by SKU]* in Beheer klikt, wordt de SKU niet uit de volgorde verwijderd.

<u> Stappen om </u> te reproduceren:

1. Ga naar Beheer > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** en klik op **[!UICONTROL Create New Order]** .
1. Kies een klant.
1. Klik op **[!UICONTROL Add to Order by SKU]**.
   * Voer een SKU in.
   * Klik op **[!UICONTROL Add another]** .
1. Klik op het pictogram **[!UICONTROL Delete]** .

<u> Verwachte resultaten </u>:

* Producten worden toegevoegd aan en verwijderd uit een bestelling in de Admin.

<u> Ware resultaten </u>:

* Het pictogram **[!UICONTROL Delete]** werkt niet.
* Er is een fout in de console:

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
