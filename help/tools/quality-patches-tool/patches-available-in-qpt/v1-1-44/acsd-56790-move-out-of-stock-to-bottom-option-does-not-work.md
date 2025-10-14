---
title: 'ACSD-56790: **[!UICONTROL move out of stock to bottom]** optie werkt niet tijdens het sorteren van producten in  [!DNL Visual Merchandiser]'
description: Pas de ACSD-56790-patch toe om het Adobe Commerce-probleem op te lossen waarbij de optie 'van voorraad naar onderkant' niet werkt tijdens het sorteren van producten in Visual Merchandiser.
feature: Products, Categories
role: Admin, Developer
exl-id: a5e5f208-793d-45a5-a000-f8ff1c31d049
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# ACSD-56790: **[!UICONTROL move out of stock to bottom]** werkt niet tijdens het sorteren van producten in [!DNL Visual Merchandiser]

De ACSD-56790-patch verhelpt het probleem dat de optie om van voorraad naar beneden te gaan niet werkt bij het sorteren van producten in de [!DNL Visual Merchandiser] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 wordt geïnstalleerd. De patch-id is ACSD-56790. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De optie **[!UICONTROL move out of stock to bottom]** werkt niet tijdens het sorteren van producten in de [!DNL Visual Merchandiser]

<u> Stappen om </u> te reproduceren:

1. Adobe Commerce installeren.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en maak de volgende kenmerken.
1. Creeer een nieuwe website: **niet-hoofd**.
1. Creeer a **niet-belangrijkste Opslag** op deze nieuwe website.
1. Twee winkels maken:

   * Eerst in de **Belangrijkste websiteopslag**.
   * Tweede in de **Niet-belangrijkste Opslag**.

1. Maak twee bronnen:
   * Letters.
   * Getallen.

1. Twee bestanden maken:
   * Eerste hoofdkanaal - verkoopkanalen: hoofdwebsite - toegewezen bronnen: letters.
   * Tweede niet-hoofdproduct - verkoopkanalen: niet-hoofdbronnen - toegewezen bronnen: getallen.

1. Maak drie eenvoudige producten op beide websites, allemaal in de categorie Standaard, die allemaal zijn toegewezen aan beide bronnen:

   * ProductA - Aantal *10* in Brieven, Aantal *0* in Aantallen.
   * Product1 - Aantal *0* in Brieven, Aantal *10* in Aantallen.
   * ProductA1 - Aantal *10* in Brieven, Aantal *10* in Aantallen.

1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** en selecteer **[!UICONTROL Default category]** .
1. Verander het werkingsgebied in **eerst**.
1. Vouw de producten uit in de sectie Categorie.
1. Kies de sorteervolgorde als: **[!UICONTROL move out of stock to bottom]**

<u> Verwachte resultaten </u>:

De lijst van de producten met de **uit-van-voorraad** producten wordt verplaatst naar de bodem.

<u> Ware resultaten </u>:

De producten kunnen niet worden geladen. Een pagina wordt omgeleid naar het dashboard voor beheer met het foutbericht: `Invalid security or form key. Please refresh the page`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
