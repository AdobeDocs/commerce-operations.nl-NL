---
title: 'ACSD-63974: hiermee wordt de langzaam [!UICONTROL Requisition List] te laden tijd gecorrigeerd met paginering'
description: Pas de ACSD-63974-patch toe om het probleem op te lossen waarbij het laden van de pagina [!UICONTROL Requisition List] lang duurt wanneer er te veel items zijn.
feature: B2B
role: Admin, Developer
source-git-commit: e5f8112b870e3550b4f3a9113be48428a54d454a
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# ACSD-63974: hiermee wordt de langzaam [!UICONTROL Requisition List] te laden tijd gecorrigeerd met paginering

De ACSD-63974-patch verhelpt het probleem waarbij het laden van de pagina **[!UICONTROL Requisition List]** veel tijd in beslag neemt als er te veel items zijn. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 wordt geïnstalleerd. De patch-id is ACSD-63974. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het laden van de pagina **[!UICONTROL Requisition List]** duurt lang wanneer er veel items zijn (2000+). Dit is te wijten aan het ontbreken van paginering, waardoor alle items in één keer worden geladen.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]** .
1. Plaats **[!UICONTROL Enable Requisition List]** aan *ja*.
1. Produceer meer dan 2000 producten door `simple_products` knoop in `setup/performance-toolkit/profiles/ce/small.xml` uit te geven.
1. Voer de opdracht uit:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Maak een klant en meld u aan.
1. Voeg alle producten toe aan **[!UICONTROL Requisition List]**.
1. Bekijk **[!UICONTROL Requisition List]** op de Storefront.


<u> Verwachte resultaten </u>:

De pagina moet binnen een redelijke tijd worden geladen.


<u> Ware resultaten </u>:

De laadtijd van de pagina neemt toe met het aantal items omdat alle items tegelijk worden geladen omdat de paginering ontbreekt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce on cloud Infrastructure: Upgrades and Patches > Apply Patches in the Commerce on Cloud Infrastructure guide.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
