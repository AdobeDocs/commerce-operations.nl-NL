---
title: 'ACSD-48262: producten die niet zichtbaar zijn op de winkel als [!UICONTROL Allow All Products Per Page] is ingesteld [!UICONTROL Yes]'
description: Pas de ACSD-48262-patch toe om het Adobe Commerce-probleem op te lossen, waarbij producten niet zichtbaar zijn op de winkel wanneer de [!UICONTROL Allow All Products Per Page] -instelling is ingesteld op [!UICONTROL Yes] .
feature: Admin Workspace, Cache, Categories, Orders, Products, Storefront
role: Admin
exl-id: 733ac476-5c3c-4cbe-88b7-f436d15f1c7d
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-48262: producten die niet zichtbaar zijn op de winkel als [!UICONTROL Allow All Products Per Page] is ingesteld *[!UICONTROL Yes]*

De ACSD-48262-patch verhelpt het probleem dat producten niet zichtbaar zijn op de winkel wanneer de [!UICONTROL Allow All Products Per Page] -instelling is ingesteld op *[!UICONTROL Yes]* . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-48262. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) >=2.4.5 &lt; 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ACSD-48262-patch verhelpt het probleem dat producten niet zichtbaar zijn op de winkel wanneer de [!UICONTROL Allow All Products Per Page] -instelling is ingesteld op *[!UICONTROL Yes]* .

<u> Stappen om </u> te reproduceren:

1. Maak een testcategorie.
1. Maak een testproduct in de testcategorie.
1. Blader naar de pagina met productcategorieën op de winkel en controleer of het product zichtbaar is.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** en stel de instelling [!UICONTROL Allow All Products Per Page] in op *[!UICONTROL Yes]* .
1. Cache wissen.
1. Categoriepagina controleren in de winkel.

<u> Verwachte resultaten </u>:

Het product is zichtbaar.

<u> Ware resultaten </u>:

Het product is niet zichtbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
