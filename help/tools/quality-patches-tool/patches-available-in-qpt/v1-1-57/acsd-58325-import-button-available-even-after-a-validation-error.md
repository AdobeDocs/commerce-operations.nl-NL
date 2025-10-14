---
title: 'ACSD-58325: [!UICONTROL Import] knop beschikbaar zelfs na een validatiefout'
description: Pas de ACSD-58325-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de knop [!UICONTROL Import] zelfs na een validatiefout beschikbaar is.
feature: Data Import/Export
role: Admin, Developer
exl-id: 551a9ac7-9b7f-49b5-9255-2014c330fb07
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# ACSD-58325: [!UICONTROL Import] knop beschikbaar zelfs na een validatiefout

De ACSD-58325-patch verhelpt het probleem waarbij de knop **[!UICONTROL Import]** zelfs na een validatiefout beschikbaar is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-58325. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De knop [!UICONTROL Import] is zelfs beschikbaar na een validatiefout.

<u> Stappen om </u> te reproduceren:

1. Maak het CSV-bestand voor het importeren van het product met een onjuiste afbeeldingsnaam in het bestand.
1. Maak een geplande productimport met het gemaakte CSV-bestand.
1. Wacht tot het geplande importeren is uitgevoerd.
1. Controleer [!UICONTROL Last outcome] in het **[!UICONTROL Scheduled Imports/Exports]** -raster.

<u> Verwachte resultaten </u>:

[!UICONTROL Last outcome] moet [!UICONTROL Failed] zijn.

<u> Ware resultaten </u>:

[!UICONTROL Last outcome] is [!UICONTROL Successful] .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
