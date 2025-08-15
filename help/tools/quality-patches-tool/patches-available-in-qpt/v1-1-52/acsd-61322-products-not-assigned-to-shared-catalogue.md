---
title: 'ACSD-61322: producten die niet aan [!UICONTROL Shared Catalogue] zijn toegewezen, worden opgenomen in XML-itemap'
description: Pas de ACSD-61322-patch toe om het Adobe Commerce-probleem op te lossen waarbij producten/categorieën die niet zijn toegewezen aan de [!UICONTROL Shared Catalog] voor de Standaard (Algemene) groep, nog steeds zijn opgenomen in de XML-itemap.
feature: Site Navigation, B2B
role: Admin, Developer
exl-id: 4698ba5a-673e-4bf0-b36c-39f6122dab26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# ACSD-61322: producten die niet aan [!UICONTROL Shared Catalogue] zijn toegewezen, worden opgenomen in XML-itemap

De ACSD-61322-patch verhelpt het probleem dat producten/categorieën die niet zijn toegewezen aan de groep [!UICONTROL Shared Catalog] Standaard (Algemeen), nog steeds in de XML-sitemap zijn opgenomen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 wordt geïnstalleerd. De patch-id is ACSD-61322. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Producten/categorieën die niet zijn toegewezen aan de groep [!UICONTROL Shared Catalog] Standaard (Algemeen), worden nog steeds opgenomen in de XML-itemap.

<u> Stappen om </u> te reproduceren:

1. Maak enkele categorieën en voeg producten toe (bijvoorbeeld Categorie 1 met Categorie 2).
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]** en schakel *[!UICONTROL Company and Shared Catalog]* in.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** en wijzig de standaardcatalogus.
1. Selecteer **[!UICONTROL Select]** in het vervolgkeuzemenu **[!UICONTROL Set Pricing and Structure]** en klik op **[!UICONTROL Configure]** .
1. Onder *Categorie 1 > Categorie 2* categorie, unselect sommige producten die niet in [!UICONTROL Shared Catalog] zouden moeten zijn.
1. Klik op **[!UICONTROL Next]** en genereer de catalogus.
1. Maak een klantenaccount in de winkel.
1. Ga naar *Categorie 1 > Categorie 2* categorie. Er worden alleen de producten weergegeven die aan de [!UICONTROL Shared Catalog] zijn toegewezen.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL SEO & Search]** > **[!UICONTROL Site Map]** en genereer een nieuwe sitemap.
1. Open `sitemap.xml` op de Storefront.
1. Zoek naar de producten die u niet in [!UICONTROL Shared Catalog] hebt opgenomen.

<u> Verwachte resultaten </u>:

De sitemap bevat geen koppelingen naar producten en categorieën die niet zijn toegewezen aan de [!UICONTROL Shared Catalog] .

<u> Ware resultaten </u>:

De sitemap bevat koppelingen naar producten en categorieën die niet zijn toegewezen aan de [!UICONTROL Shared Catalog] .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
