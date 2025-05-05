---
title: 'ACSD-63323: lost [!UICONTROL Select All] functionaliteit op en verbetert paginering en recordaantal in popup van de productcategorie'
description: Pas de ACSD-63323-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de optie [!UICONTROL Select All] niet werkt wanneer u producten aan een categorie toevoegt. Bovendien zorgt het ervoor dat paginering en het label voor het recordaantal correct werken wanneer u producten aan een categorie toevoegt via het popup-raster.
feature: Products
role: Admin, Developer
exl-id: 96e318fd-f1dd-4b15-b171-78ae1c8e4e0d
source-git-commit: d24909ea2571eacafac1ff6b225e87bc40d320bc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-63323: lost [!UICONTROL Select All] functionaliteit op en verbetert paginering en recordaantal in popup van de productcategorie

De ACSD-63323-patch verhelpt het probleem waarbij de optie **[!UICONTROL Select All]** niet werkt wanneer u producten aan een categorie toevoegt. Bovendien zorgt het ervoor dat paginering en het label voor het recordaantal correct werken wanneer u producten aan een categorie toevoegt via het popup-raster. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 wordt geïnstalleerd. De patch-id is ACSD-63323. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee wordt het probleem verholpen waarbij de optie **[!UICONTROL Select All]** niet werkt in Beheer > **[!UICONTROL Categories]** > Kies een categorie > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]** . Het helpt ook paginering en het etiket van de verslagtelling correct te functioneren wanneer het toevoegen van producten aan een categorie via popup net.


<u> Stappen om </u> te reproduceren:

1. Produceer *1200* producten gebruikend het bevel:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Open **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en zie het aantal producten: *1200* gevonden verslagen.
1. Open een standaardcategorie > **[!UICONTROL Products in Category]** > **[!UICONTROL Add Products]** .
1. Klik op **[!UICONTROL Assign]** > **[!UICONTROL Select All]** .
1. Verander het aantal producten op de pagina in waarde = *5*.


**Verwachte resultaten**:

*het bericht zou moeten zijn: 1200 gevonden verslagen (1200 geselecteerd)*

**Ware resultaten**:

* Paginering werkt niet.
* Het verkeerde bericht wordt getoond: *5* gevonden verslagen (*20* geselecteerd)

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
