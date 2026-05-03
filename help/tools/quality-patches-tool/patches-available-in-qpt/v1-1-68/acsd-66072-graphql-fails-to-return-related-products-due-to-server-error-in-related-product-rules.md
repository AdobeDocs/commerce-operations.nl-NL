---
title: 'ACSD-66072: GraphQL kan verwante producten niet retourneren op de pagina Productdetails'
description: Pas de ACSD-66072-patch toe om het Adobe Commerce-probleem op te lossen, waarbij gerelateerde producten niet via GraphQL worden geretourneerd op de pagina Productdetails vanwege een interne serverfout wanneer de Verwante productregels zijn geconfigureerd.
feature: GraphQL, Products
role: Admin, Developer
type: Troubleshooting
exl-id: a706a710-aed3-41a4-bc87-3150e9ba95f7
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-66072: GraphQL kan verwante producten niet retourneren op de pagina Productdetails

De ACSD-66072-patch verhelpt het probleem dat gerelateerde producten niet via GraphQL worden geretourneerd op de pagina Productdetails vanwege een interne serverfout wanneer **[!UICONTROL Related Products Rule]** is geconfigureerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66072. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Gerelateerde producten worden niet via GraphQL geretourneerd op de pagina Productdetails vanwege een interne serverfout wanneer **[!UICONTROL Related Products Rule]** is geconfigureerd.

<u> Stappen om </u> te reproduceren:

1. Configureerbare producten maken:
   * **Product 1**: `config1` with `option1`
   * **Product 2**: `config2` with `option2`

1. Producten maken en toewijzen aan een categorie
   * Creeer a **nieuwe categorie**.
   * Wijs beide producten (`config1` en `config2`) aan deze categorie toe.

1. Navigeer naar **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Related Products Rule]** en maak vervolgens een nieuwe regel met de volgende instellingen:

   * **[!UICONTROL Priority]**: 1
   * **[!UICONTROL Applies To]**: **[!UICONTROL Related Products]**
   * **[!UICONTROL Result Limit]**: 10
   * **[!UICONTROL Products to Match]**: **[!UICONTROL Attribute Set is Default]**
   * **[!UICONTROL Products to Display]**: `Product Category is the Same as Matched Product Categories`

1. Voer de volgende Magento CLI-opdrachten uit:

   ```shell
   bin/magento indexer:reindex
   bin/magento cache:clean
   ```

1. Verzend een POST-aanvraag naar `../graphql` met de volgende payload:

   ```graphql
   query getRelatedProductsForProductPage($urlKey: String!) 
   {
       products(filter: { url_key: { eq: $urlKey } }) 
       {
           items {
               id
               __typename
               uid
               url_key
               name
               sku
               related_products {
                   id
                   uid
                   name
                   sku
                   stock_status
                   url_key
                   small_image {
                       url
                       __typename
                       }
                       thumbnail {
                           url
                           __typename
                           }
                           image {
                               url
                               __typename
                               }
                               price_range {
                                   maximum_price {
                                       regular_price {
                                           currency
                                           value
                                           __typename
                                           }
                                           __typename
                                           }
                                           minimum_price {
                                               discount {
                                                   amount_off
                                                   percent_off
                                                   __typename
                                                   }
                                                   final_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       regular_price {
                                                           currency
                                                           value
                                                           __typename}
                                                           __typename}
                                                           __typename}
                                                           __typename
                                                           }
                                                           }
                                                           __typename
                                                           }
                                                           }
   ```

<u> Verwachte resultaten </u>:

De vraag keert het verwante product (`config1`) terug.

<u> Ware resultaten </u>:

```graphql
{
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 10,
                    "column": 7
                }
            ],
            "path": [
                "products",
                "items",
                0,
                "related_products"
            ]
        }
    ],
    "data": {
        "products": {
            "items": [
                {
                    "id": 4,
                    "__typename": "ConfigurableProduct",
                    "uid": "NA==",
                    "url_key": "config2",
                    "name": "config2",
                    "sku": "config2",
                    "related_products": null
                }
            ],
            "__typename": "Products"
        }
    }
}
```

Het bestand `var/log/exception.log` bevat:

```text
report.ERROR: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in /home/magento2ee/app/code/Magento/TargetRule/Model/ResourceModel/Index.php on line 557
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
