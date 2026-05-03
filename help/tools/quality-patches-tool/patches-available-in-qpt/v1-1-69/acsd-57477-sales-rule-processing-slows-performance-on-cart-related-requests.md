---
title: 'ACSD-5747: Verkoop regelverwerking vertraagt de prestaties bij kartgerelateerde verzoeken'
description: Pas de ACSD-57477-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij in een project met veel beschikbare productkenmerken (bijvoorbeeld 1000 kenmerken), wanneer de AddProductsToCart-GraphQL-bewerking met variabelen wordt uitgevoerd, Commerce al deze productkenmerken probeert te laden en langzame prestatieproblemen veroorzaakt door de AddProductsToCart-GraphQL-bewerking.
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: 3944b4d4-09c0-49a4-9a7e-8e1758d9d73c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-5747: Verkoop regelverwerking vertraagt de prestaties bij kartgerelateerde verzoeken

De ACSD-57477-patch verhelpt het probleem waarbij de verwerking van verkoopregels tot trage prestaties leidt bij cart-gerelateerde verzoeken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-5747. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Verwerking van verkoopregels leidt tot trage prestaties bij aanvragen met betrekking tot winkelwagentjes als u de parameters verzendt als GraphQL-variabelen.

<u> Stappen om </u> te reproduceren:

1. Voeg 1000 productkenmerken toe.
1. Maak een winkelwagentje met behulp van de GraphQL-query.

   ```graphql
   mutation {createEmptyCart}{noformat}
   ```

1. Voeg een product toe aan winkelwagentje met behulp van de GraphQL-query.

   ```graphql
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. Stel deze variabelen in.

   ```json
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. Dit probleem doet zich alleen voor wanneer u de parameters als GraphQL-variabelen verzendt. Als u de parameters opneemt in de GraphQL-query zelf, doet dit probleem zich niet voor.
1. Verzend het zelfde **toevoegt aan het verzoek van de Kar** na het toevoegen van parameters in de vraag van GraphQL zelf.

   ```graphql
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u> Verwachte resultaten </u>:

De prestaties van de GraphQL-bewerking `AddProductsToCart` mogen niet worden verminderd.

<u> Ware resultaten </u>:

De prestaties van de GraphQL-bewerking van `AddProductsToCart` nemen af, omdat alle productkenmerken worden geladen wanneer parameters als variabelen worden verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] hulplijn
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in de gids van de Infrastructuur van Commerce op de Wolk toe

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen
