---
title: "ACSD-59925: Items in [!UICONTROL Media Gallery] sorteren op positie in GraphQL"
description: Pas de ACSD-59925-patch toe om het Adobe Commerce-probleem op te lossen, waarbij items in de [!UICONTROL Media Gallery] niet op positie worden gesorteerd. Dit leidt tot een onjuiste weergavevolgorde.
feature: Media, GraphQL
role: Admin, Developer
source-git-commit: 97e3ab77e7c8f5f1efd9b616b5e1d198a1b41ab0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-59925: Items in de [!UICONTROL Media Gallery] sorteren op positie in GraphQL

De ACSD-59925-patch verhelpt het probleem waarbij items in de [!UICONTROL Media Gallery] niet op positie worden gesorteerd. Dit leidt tot een onjuiste weergavevolgorde. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.52 wordt geïnstalleerd. De patch-id is ACSD-59925. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Items in de [!UICONTROL Media Gallery] worden niet op positie gesorteerd. Dit leidt tot een onjuiste weergavevolgorde.

<u> Stappen om </u> te reproduceren:

1. Maak/bewerk het product.
1. Voeg twee of meer afbeeldingen toe en sla deze op.
1. Bewerk hetzelfde product, maar sleep nu de laatste afbeelding naar de eerste positie.
1. Sla het product op.
1. Opnieuw indexeren.
1. Ga naar GraphQL-client.
1. GraphQL-query uitvoeren:

   ```GraphQL
   {
     products(filter: { sku: { eq: "24-MB01" } }) {
        items {
          name
          sku
          url_key
          stock_status
          media_gallery {
             __typename
             ... on ProductVideo {
               video_content {
                 video_url
                 video_title
                 __typename
               }
               __typename
             }
             ... on ProductImage {
               url
               __typename
             }
               position
               disabled
            }
         }
         total_count
         page_info {
         page_size
        }
      }
    }
   ```

<u> Verwachte resultaten </u>:

Items in de `media_gallery` worden gesorteerd op positie.

<u> Ware resultaten </u>:

Items in de `media_gallery` worden niet op positie gesorteerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.