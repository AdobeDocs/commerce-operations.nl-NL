---
title: 'ACSD-63520: de beelden die door de Configuratie van het Uploaden van het Beeld worden geupload overschrijden de gevormde groottegrenzen'
description: Pas de ACSD-63520-patch toe om het Adobe Commerce-probleem op te lossen waarbij images die via de Images Upload Configuration in het beheerpaneel zijn geüpload, niet voldoen aan de maximale limiet voor uploadgrootte.
feature: Media, Products
role: Admin, Developer
exl-id: 5132bfa9-813a-4623-8e02-a8801f6396e8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-63520: de beelden uploaden door [!UICONTROL Image Upload Configuration] overschrijden de gevormde groottegrenzen

De ACSD-63520-patch verhelpt een probleem waarbij afbeeldingen die via [!UICONTROL Images Upload Configuration] zijn geüpload niet voldoen aan de maximale limiet voor uploadgrootte. Hiertoe configureert u de [!UICONTROL Images Upload Configuration] -instellingen in het deelvenster [!UICONTROL Admin] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 wordt geïnstalleerd. De patch-id is ACSD-63520. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.7

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw [!DNL Adobe Commerce] -versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] pagina &#39;Patches zoeken&#39; ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Afbeeldingen die via [!UICONTROL Images Upload Configuration] in het deelvenster [!UICONTROL Admin] zijn geüpload, voldoen niet aan de maximale limiet voor uploadgrootte.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij het deelvenster **[!UICONTROL Admin]** .
1. Navigeer naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]** en stel in:
   * Kwaliteit: 100
   * Formaat randdikte wijzigen inschakelen: Ja
   * Maximale breedte: 800
   * Maximumhoogte: 600
1. Uitvouwen **[!UICONTROL Media Gallery Image Optimization]** en instellen:
   * Optimalisatie van afbeelding inschakelen: Ja
   * Maximale breedte: 1000
   * Maximumhoogte: 1000
1. Navigeer naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]** .
   1. Voeg **[!UICONTROL Product Name]**, **[!UICONTROL SKU]** en **[!UICONTROL Price]** toe.
   1. Klik op **[!UICONTROL Create Configurations]** , selecteer **[!UICONTROL Attributes]** en klik op **[!UICONTROL Next]** .
   1. Kies grootten (S, M, L, XL) en klik op **[!UICONTROL Next]** .
   1. Selecteer onder **[!UICONTROL Images]** de optie **[!UICONTROL Apply single set of images to all SKUs]** .
   1. Upload een afbeelding (minimaal 1024 x 1024) en klik op **[!UICONTROL Next]** .
   1. Klik op **[!UICONTROL Generate Product]**.
1. Klik op **[!UICONTROL Save]**.

<u> Verwachte resultaten </u>:

Voor afbeeldingen moet de geconfigureerde uploadgrootte worden aangehouden en de maximale grootte worden aangepast.

<u> Ware resultaten </u>:

Afbeeldingen worden niet vergroot of verkleind en overschrijden de limiet voor de geconfigureerde uploadgrootte.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
