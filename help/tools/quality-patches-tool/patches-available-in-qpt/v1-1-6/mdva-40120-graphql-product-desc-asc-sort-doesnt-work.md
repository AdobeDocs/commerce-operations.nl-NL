---
title: 'MDVA-40120: GraphQL product DESC/ASC sortering werkt niet'
description: De MDVA-40120-patch lost het probleem op dat GraphQL-sortering via DESC/ASC niet werkt met producten die dezelfde relevantie of prijs hebben. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 is geïnstalleerd. De patch-id is MDVA-40120. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: GraphQL, Products
role: Admin
exl-id: 4df7f14d-181b-4f34-aff7-0af823632015
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-40120: GraphQL product DESC/ASC sortering werkt niet

De MDVA-40120-patch lost het probleem op dat GraphQL-sortering via DESC/ASC niet werkt met producten die dezelfde relevantie of prijs hebben. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 geïnstalleerd is. De patch-id is MDVA-40120. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Eerste vereisten </u>:

Maak een paar verschillende producten met dezelfde prijs.

<u> Stappen om </u> te reproduceren:

1. Voer de volgende GraphQL-query uit:

   ```GraphQL
   {
     products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: ASC}) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Controleer het antwoord.
1. Verander de soortorde van **ASC** in **DESC** in de vraag van GraphQL:

   ```GraphQL
   {
     products(filter: {category_id: {eq: "{{cat_id}}"}}, sort: {relevance: DESC}) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Controleer het antwoord.

<u> Verwachte resultaten </u>:

De productvermelding in het GraphQL-antwoord moet worden gewijzigd volgens de sorteervolgorde.

<u> Ware resultaten </u>:

De sorteervolgorde blijft ongewijzigd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
