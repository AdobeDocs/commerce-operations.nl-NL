---
title: 'ACSD-48627: configureerbaar product buiten voorraad veroorzaakt een fout'
description: Pas de ACSD-48627-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het configureerbare product uit de voorraad een fout veroorzaakt bij het verzenden van een GraphQL-verzoek om kaartgegevens.
feature: Admin Workspace, Configuration, Orders, Products
role: Admin
exl-id: 457c605e-d0c3-479e-b515-9b2851a71a08
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-48627: configureerbaar product buiten voorraad veroorzaakt een fout

De ACSD-48627-patch verhelpt het probleem waarbij het configureerbare product van buiten de voorraad een fout veroorzaakt bij het verzenden van een GraphQL-aanvraag om kaartgegevens op te halen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-48627. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het configureerbare product van buiten de voorraad veroorzaakt een fout wanneer het verzenden van een GraphQL verzoek om kartdetails te krijgen.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount.
1. Voeg bepaalde producten aan de kar toe, met inbegrip van een configureerbaar product.
1. Ga naar admin backend, en geef het configureerbare product uit door al kindproductenKwaliteit aan 0 te plaatsen.
1. Het configureerbare product zal uit voorraad raken aangezien alle kindproducten uit voorraad zijn.
1. Controleer de `catalog_product_index_price` tabel. De record met dit product is leeg.
1. Voer een GraphQL-aanvraag in om de klanttoken op te halen.

   ```GraphQL
   mutation {
       generateCustomerToken(
           email: "test@example.com"
           password: "xxxx"
           ) {
               token
               }
               }
   ```

1. Voer een GraphQL-aanvraag in om cartId op te halen.

   ```GraphQL
   Headers: Authentication => Bearer [customer token in step 6]
   ```

   ```GraphQL
   {
       customerCart {
           id
           items {
               id
               product {
                   name
                   sku
                   }
                   quantity
                   }
                   }
                   }
   ```

1. Voer een GraphQL-aanvraag in om de gegevens van het winkelwagentje op te halen.

   ```GraphQL
   Headers: Authentication => Bearer [customer token in step 6]
   ```

   ```GraphQL
   query GetCartDetails($cartId: String!) {
       cart(cart_id: $cartId) {
           id
           ...CartPageFragment
           __typename
           }
           }
           fragment CartPageFragment on Cart {
               id
               total_quantity
               ...AppliedCouponsFragment
               ...ProductListingFragment
               ...PriceSummaryFragment
               __typename
               }
               fragment AppliedCouponsFragment on Cart {
                   id
                   applied_coupons {
                       code
                       __typename
                       }
                       __typename
                       }
                       fragment ProductListingFragment on Cart {
                           id
                           items {
                               uid
                               product {
                                   uid
                                   name
                                   sku
                                   url_key
                                   url_suffix
                                   thumbnail {
                                       url
                                       __typename
                                       }
                                       small_image {
                                           url
                                           __typename
                                           }
                                           stock_status
                                           price_range {
                                               minimum_price {
   
                                               final_price {
                                                   currency
                                                   value
                                                   __typename
                                                   }
                                                   regular_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       __typename
                                                       }
                                                       __typename
                                                       }
                                                       stock_status
                                                       ... on ConfigurableProduct {
                                                           variants {
                                                               attributes {
                                                                   uid
                                                                   __typename
                                                                   }
                                                                   product {
                                                                       uid
                                                                       small_image {
                                                                           url
                                                                           __typename
                                                                           }
                                                                           stock_status
                                                                           __typename
                                                                           }
                                                                           __typename
                                                                           }
                                                                           __typename
                                                                           }
                                                                           __typename
                                                                           }
                                                                           prices {
                                                                               price {
                                                                                   currency
                                                                                   value
                                                                                   __typename
                                                                                   }
                                                                                   __typename
                                                                                   }
                                                                                   quantity
                                                                                   ... on
                                                                                   ConfigurableCartItem {
                                                                                       configurable_options {
                                                                                           id
                                                                                           configurable_product_option_uid
                                                                                           option_label
                                                                                           configurable_product_option_value_uid
                                                                                           value_label
                                                                                           __typename
                                                                                           }
                                                                                           __typename
                                                                                           }
                                                                                           __typename
                                                                                           }
                                                                                           __typename
                                                                                           }
                                                                                           fragment PriceSummaryFragment on Cart {
                                                                                               id
                                                                                               items {
                                                                                                   uid
                                                                                                   quantity
                                                                                                   __typename
                                                                                                   }
                                                                                                   ...ShippingSummaryFragment
                                                                                                   prices {
                                                                                                       ...TaxSummaryFragment
                                                                                                       ...DiscountSummaryFragment
                                                                                                       ...GrandTotalFragment
                                                                                                       subtotal_excluding_tax {
                                                                                                           currency
                                                                                                           value
                                                                                                           __typename
                                                                                                           }
                                                                                                           subtotal_including_tax {
                                                                                                               currency
                                                                                                               value
                                                                                                               __typename
                                                                                                               }
                                                                                                               __typename
                                                                                                               }
                                                                                                               __typename
                                                                                                               }
                                                                                                               fragment DiscountSummaryFragment on
                                                                                                               CartPrices {
                                                                                                                   discounts {
                                                                                                                       amount {
                                                                                                                           currency
                                                                                                                           value
                                                                                                                           __typename
                                                                                                                           }
                                                                                                                           label
                                                                                                                           __typename
                                                                                                                           }
                                                                                                                           __typename
                                                                                                                           }
                                                                                                                           fragment GrandTotalFragment on CartPrices {
                                                                                                                               grand_total {
                                                                                                                                   currency
                                                                                                                                   value
                                                                                                                                   __typename
                                                                                                                                   }
                                                                                                                                   __typename
                                                                                                                                   }
                                                                                                                                   fragment ShippingSummaryFragment on Cart {
                                                                                                                                       id
                                                                                                                                       shipping_addresses {
                                                                                                                                           selected_shipping_method {
                                                                                                                                               amount {
                                                                                                                                                   currency
                                                                                                                                                   value
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   street
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   __typename
                                                                                                                                                   }
                                                                                                                                                   fragment TaxSummaryFragment on CartPrices {
                                                                                                                                                       applied_taxes {
                                                                                                                                                           amount {
                                                                                                                                                               currency
                                                                                                                                                               value
                                                                                                                                                               __typename
                                                                                                                                                               }
                                                                                                                                                               __typename
                                                                                                                                                               }
                                                                                                                                                               __typename
                                                                                                                                                               }
   ```

<u> Verwachte resultaten </u>:

Geen *Interne serverfout* in de reactie.

<u> Ware resultaten </u>:

Er is een *Interne serverfout* in de reactie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Patches toepassen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de basis van de steunkennis zelf-te dienen
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
