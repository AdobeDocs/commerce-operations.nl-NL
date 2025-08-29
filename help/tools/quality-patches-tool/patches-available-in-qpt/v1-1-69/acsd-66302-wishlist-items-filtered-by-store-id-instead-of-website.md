---
title: 'ACSD-66302: ishlist-items gefilterd door winkel-id in plaats van website'
description: Pas ACSD-66302 flard toe om de kwestie van Adobe Commerce te bevestigen waar de punten die van de verlanglijst door opslagidentiteitskaart in plaats van website in  [!DNL GraphQL]  verzoeken worden gefiltreerd.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: c1a9eadc-0321-4f5c-ba82-533286a1f24f
source-git-commit: bec27df19ce5d34be063dce3de74ffe253c3e8f4
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-66302: ishlist-items gefilterd door winkel-id in plaats van website

De ACSD-66302-patch verhelpt het probleem waarbij wenslijstonderdelen worden gefilterd met opslag-id in plaats van met website in [!DNL GraphQL] -aanvragen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-66302. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Items in de lijst met identieke objecten worden onjuist gefilterd door de winkel-id in plaats van door de website.

<u> Stappen om </u> te reproduceren:

1. Maak een eenvoudig product.
1. Maak een extra storeview.
1. Ga in Beheer naar **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Wish List]** > **[!UICONTROL General Options]** en stel **[!UICONTROL Enable Multiple Wish Lists]** in op `Yes` .
1. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL Url Options]** en stel **[!UICONTROL Add Store Code to Urls]** in op `Yes` .
1. Maak een klantenaccount.
1. Gebruik een [!DNL GraphQL] verzoek om het klantauteur symbolische terug te winnen.
1. Meld u aan als klant.
1. Selecteer **[!UICONTROL Default Store View]** en voeg het product aan de wenslijst toe.
1. De opslagmening van de schakelaar aan *test*.
1. Bevestig dat het product nog steeds in de verlanglijst staat (juist gedrag).
1. Voer de volgende [!DNL GraphQL] query uit:

   ```
   {
     customer {
       wishlists {
         id
         name
         items_count
         items_v2 {
           items {
             id
             product {
               uid
               name
               sku
             }
           }
         }
       }
     }
   }
   ```

1. Voer de vraag op de standaardopslag uit - het product verschijnt zoals verwacht.
1. Voer de zelfde vraag op de testopslag uit - het product verschijnt niet.

<u> Verwachte resultaten </u>:

Het product moet zichtbaar zijn in alle weergaven van de winkel op dezelfde website via [!DNL GraphQL] query&#39;s.

<u> Ware resultaten </u>:

Het product verdwijnt uit verlanglijst wanneer het schakelen van archiefmeningen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
