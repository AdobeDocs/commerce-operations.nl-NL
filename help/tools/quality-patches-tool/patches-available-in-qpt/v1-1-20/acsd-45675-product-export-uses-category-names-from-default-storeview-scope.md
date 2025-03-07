---
title: 'ACSD-45675: Bij het exporteren van producten worden categorienamen gebruikt van het standaardweergavebereik van de winkel'
description: De ACSD-45675-patch verhelpt het probleem waarbij het exportproduct categorienamen uit het standaardweergavebereik van de winkel gebruikt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 is geïnstalleerd. De patch-id is ACSD-45675. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
source-git-commit: b1f7739688a538b25b738efc337fa81f15a5bac8
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-45675: Bij het exporteren van producten worden categorienamen gebruikt van het standaardweergavebereik van de winkel

De ACSD-45675-patch verhelpt het probleem waarbij het exportproduct categorienamen uit het standaardweergavebereik van de winkel gebruikt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 wordt geïnstalleerd. De patch-id is ACSD-45675. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij exporteren van product worden categorienamen uit het standaardweergavebereik van de winkel gebruikt.

<u> Stappen om </u> te reproduceren:

1. Maak een aangepaste winkelweergave **[!UICONTROL Thai]** in de hoofdwinkel.
1. Maak **[!UICONTROL Thai]** de standaardwinkelweergave van de hoofdwebsite.
1. Maak de volgende categoriestructuur onder **[!UICONTROL Default Category]** :

   *[!UICONTROL Default category/Tea/Black]*

1. Selecteer de categorie **[!UICONTROL Tea]** en wijzig **[!UICONTROL Scope]** in **[!UICONTROL Thai]** .
1. Stel de **[!UICONTROL Category Name]** in op **[!UICONTROL ชาดำ]** .
1. Maak een eenvoudig product **[!UICONTROL SP001]** en wijs de categorie **[!UICONTROL Black]** toe.
1. Controleer of de uitsnede niet wordt uitgevoerd.
1. Een product exporteren. Filter op SKU en selecteer **[!UICONTROL SP001]**.
1. Controleer de kolom **[!UICONTROL categories]** in het geëxporteerde CSV-bestand.

<u> Verwachte resultaten </u>:

Aangezien er tijdens het exporteren geen winkel is geselecteerd, kunt u het best een categoriepad als het volgende ophalen: *[!UICONTROL Default Category/Tea/Black]* .

<u> Ware resultaten </u>:

Categoriepad heeft gemengde talen: *[!UICONTROL Default Category/ชาดำ/Black]*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tools] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding voor het gereedschap Kwaliteitspatches.
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
