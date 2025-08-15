---
title: 'MDVA-38447: "Niet zichtbaar individueel"configureerbare kindproducten zijn teruggekeerd in de reactie van GraphQL en langzaam MySQL vraag'
description: De patch MDVA-38447 Adobe Commerce lost het probleem op waarbij "Niet zichtbaar individueel"configureerbare kindproducten in de reactie van GraphQL worden teruggegeven en vraag MySQL voor de productvraag van GraphQL met categoriefilter vertragen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 is geïnstalleerd. De patch-id is MDVA-38447. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-38447: &quot;Niet zichtbaar individueel&quot;configureerbare kindproducten zijn teruggekeerd in de reactie van GraphQL en langzaam MySQL vraag

De patch MDVA-38447 Adobe Commerce lost het probleem op waarbij &quot;Niet zichtbaar individueel&quot;configureerbare kindproducten in de reactie van GraphQL worden teruggegeven en vraag MySQL voor de productvraag van GraphQL met categoriefilter vertragen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2 geïnstalleerd is. De patch-id is MDVA-38447. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

&quot;Niet zichtbaar individueel&quot;configureerbare kindproducten zijn teruggekeerd in de reactie van GraphQL en langzaam MySQL vraag voor de productvraag van GraphQL met categoriefilter.

<u> Eerste vereisten </u>:

B2B-modules moeten worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Creeer een configureerbaar product met eenvoudige die producten aan **worden geplaatst individueel niet zichtbaar**.
1. Stel a **volledige herdex** in werking.
1. Stel a **vraag van GraphQL** als in werking:

<pre>query getFilteredProducts()
  $filter: ProductAttributeFilterInput!
  $sort: ProductAttributeSortInput!
  $search: String
  $pageSize: Int!
  $currentPage: Int!
) &lbrace;
  products()
    filter: $filter
    sorteren: $sort
    zoekopdracht: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) &lbrace;
    total_count
    page_info &lbrace;
      total_pages
      current_page
      page_size
    &rbrace;
    items &lbrace;
      name
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

Variabelen:

<pre>&lbrace;"filter":{"user_group":{"eq":""},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u> Verwachte resultaten </u>:

Producten met zichtbaarheid ingesteld op Niet afzonderlijk zichtbaar worden niet geretourneerd als reactie op de aanvraag.

<u> Ware resultaten </u>:

Producten met zichtbaarheid ingesteld op &quot;Niet afzonderlijk zichtbaar&quot; worden als reactie gegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingstype:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over kwaliteitspatches voor Adobe Commerce:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) sectie.
