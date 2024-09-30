---
title: "ACSD-51305: niet-standaard samengestelde producten voor kinderen die niet beschikbaar zijn in GraphQL-reactie"
description: Pas de ACSD-51305-patch toe om het Adobe Commerce-probleem op te lossen wanneer samengestelde producten uit de voorraad niet beschikbaar zijn in de GraphQL-respons.
feature: Categories, GraphQL, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51305: Niet in GraphQL-antwoord beschikbare samengestelde producten van buiten de voorraad

De ACSD-51305-patch verhelpt het probleem dat niet-standaard samengestelde onderliggende producten beschikbaar zijn in de GraphQL-respons. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-51305. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Samengestelde onderliggende producten uit de voorraad zijn niet beschikbaar in de GraphQL-respons.

<u> Stappen om </u> te reproduceren:

1. Meld u aan bij de beheerwebsite.
1. Maak een categorie (cat1, id=3).
1. Creeer a *simple1* product (uit voorraad, niet zichtbaar individueel, toegewezen aan *cat1*).
1. Creeer a *simple2* product (in voorraad, niet zichtbaar individueel, toegewezen aan *cat1*).
1. Creeer a *bundle1* product met *simple1* en *simple2* kindproducten als radio-button *option1* producten en wijs het aan de *cat1* categorie toe.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** .

   * Plaats **[!UICONTROL Display Out of Stock Products]** aan *ja*.

1. Open het *bundle1* product op de storefront, en zorg ervoor dat zowel *simple1* als *simple2* kindproducten binnen het worden getoond.
1. Voer de volgende GraphQL-query uit:

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u> Verwachte resultaten </u>:

De sectie **[!UICONTROL Product]** in het **[!UICONTROL Options]** -blok is niet leeg.

<u> Ware resultaten </u>:

De sectie **[!UICONTROL Product]** in het **[!UICONTROL Options]** -blok is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
