---
title: 'ACSD-6577: Ontbrekend veld "types" voor productafbeeldingstypen in GraphQL-aanvraag "MediaGallery"'
description: Pas de ACSD-65777-patch toe om het Adobe Commerce-probleem te verhelpen waarbij het veld "types" ontbreekt voor productafbeeldingstypen in het GraphQL-verzoek "MediaGallery".
feature: GraphQL, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 20866963-54a3-4859-9c2d-716945e37156
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# ACSD-6577: Veld **[!UICONTROL types]** ontbreekt voor productafbeeldingstypen in de `MediaGallery` GraphQL-aanvraag

De ACSD-65777-patch verhelpt het probleem waarbij het veld **[!UICONTROL types]** ontbreekt voor productafbeeldingstypen in het GraphQL-verzoek van `MediaGallery` . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 wordt geïnstalleerd. De patch-id is ACSD-6577. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het veld **[!UICONTROL types]** ontbreekt voor productafbeeldingstypen wanneer u mediagegevens ophaalt via de `MediaGallery` GraphQL-aanvraag.

<u> Stappen om </u> te reproduceren:

1. Maak een product.
1. Upload een afbeelding naar het product.
1. Mediagegevens ophalen met de volgende GraphQL.

   ```text
   query{
     products(search:"",filter:{sku:{eq:"p1"}})\{
       items{
         media_gallery{
           disabled
           label
           position
           url
         }
         media_gallery_entries\{
           types
         }
       }
     }
   }
   ```

<u> Verwachte resultaten </u>:

De `media_gallery` GraphQL-interface moet het **[!UICONTROL types]** -veld bevatten.

<u> Ware resultaten </u>:

Het veld `media_gallery` bevat niet het mediaveld **[!UICONTROL types]** .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
