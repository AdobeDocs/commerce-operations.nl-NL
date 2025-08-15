---
title: 'ACSD-50260: zoekresultaten voor GraphQL-producten zijn beperkt'
description: Pas de ACSD-50260-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de zoekresultaten van het GraphQL-product beperkt zijn tot 10.000 resultaten.
feature: Admin Workspace, Categories, GraphQL, Products, Search
role: Admin
exl-id: a9099fab-226d-439b-b2d0-f354d6b5638f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 0%

---

# ACSD-50260: zoekresultaten voor GraphQL-producten zijn beperkt

De ACSD-50260-patch verhelpt het probleem waarbij de zoekresultaten voor GraphQL-producten beperkt zijn tot 10.000 resultaten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-50260. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De zoekresultaten voor GraphQL-producten zijn beperkt tot 10.000 resultaten.

<u> Stappen om </u> te reproduceren:

1. *[!UICONTROL 15,000 products]* genereren in één categorie.
1. Vraag die categorie met hieronder bijgevoegde GraphQL-aanvraag:

```GraphQL
{
  products(
    filter: { category_id: { eq: "{CATEGORY_ID}" } }
    pageSize: 5
    currentPage: 1
  ) {
    total_count
    page_info {
      current_page
      page_size
      total_pages
    }

    aggregations {
      attribute_code
      count
      label
      options {
        label
        value
      }
    }

    items {
      uid
      sku
      is_for_clearance
      categories {
        name
        breadcrumbs {
          category_name
          category_uid
        }
        display_mode
        description
      }
    }
  }
}
```

<u> Verwachte resultaten </u>:

`total_count = 15k`

Mogelijkheid om alle producten op te halen in de zoekresultaten.

<u> Ware resultaten </u>:

`total_count = 10k`

Er is geen mogelijkheid om producten na deze 10k-batch op te halen in de zoekresultaten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
