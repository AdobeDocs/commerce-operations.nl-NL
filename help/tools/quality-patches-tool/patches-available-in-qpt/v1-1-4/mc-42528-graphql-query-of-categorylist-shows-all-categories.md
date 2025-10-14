---
title: 'MC-42528: De vraag van GraphQL van categoryList toont alle categorieën'
description: De flard MC-42528 lost de kwestie op waar de vraag van GraphQL van &grave; categoryList' zowel toegewezen als niet toegewezen categorieën terugkeert wanneer de het doorbladeren Categorie van een bepaalde categorie aan "ontkent"wordt geplaatst. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 is geïnstalleerd. De patch-id is MC-42528. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Catalog Management, Categories, GraphQL, Customer Service
role: Admin
exl-id: 0611a7ff-9d55-4d95-9d4e-9ce1d9096bb6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# MC-42528: De vraag van GraphQL van categoryList toont alle categorieën

De patch MC-42528 lost het probleem op waar de vraag van GraphQL van `categoryList` zowel toegewezen als niet toegewezen categorieën terugkeert wanneer de het Bladeren categorie van een bepaalde categorie aan &quot;ontkent&quot;wordt geplaatst. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 geïnstalleerd is. De patch-id is MC-42528. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

GraphQL-query van `categoryList` retourneert zowel toegewezen als niet-toegewezen categorieën.

<u> Stappen om </u> te reproduceren:

1. Maak twee categorieën, CAT1 en CAT2, en wijs weinig producten aan elke categorie toe.
1. Een persoonlijke gedeelde catalogus maken.
1. Maak een bedrijfgebruiker en wijs deze toe aan de gemaakte gedeelde catalogus.
1. Wijs CAT1 aan de douanecatalogus toe en plaats de categorietoestemming aan &quot;het Bladeren van Categorie&quot;voor de klantengroep van de privé catalogus toestaan.
1. Stel de categorietoestemming voor CAT2 in op Browsercategorie &quot;Weigeren&quot; voor de klantengroep van de persoonlijke catalogus.
1. Voer de `categoryList` - of `categories` GraphQL-query uit als bedrijfsgebruiker.

<u> Verwachte resultaten </u>:

Alleen de CAT1 wordt weergegeven in de reactie.

<u> Ware resultaten </u>:

Alle categorieën worden weergegeven in het antwoord, ongeacht de bladermachtigingen van de categorie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [&#x200B; flarden beschikbaar in QPT &#x200B;](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
