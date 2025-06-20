---
title: 'ACSD-62965: hiermee wordt het ontbrekende LocalizedException-bericht in de GraphQL-reactie voor de plaatsing van bestellingen gecorrigeerd'
description: Pas de ACSD-62965-patch toe om de Adobe Commerce-problemen op te lossen waarbij het "LocalizedException"-bericht niet was opgenomen in de GraphQL-reactie tijdens de plaatsing van de bestelling.
feature: Orders, GraphQL
role: Admin, Developer
exl-id: cf9d1409-6fe3-4019-9207-df5f12a41505
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# ACSD-62965: Ontbrekend `LocalizedException` bericht in GraphQL-reactie voor plaatsing van bestelling wordt gecorrigeerd

De ACSD-62965-patch verhelpt het probleem dat het `LocalizedException` -bericht niet was opgenomen in de GraphQL-reactie tijdens het plaatsen van de bestelling. Deze patch is beschikbaar bij [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. De patch-id is ACSD-62965. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De GraphQL-reactie voor orderplaatsing bevat geen `LocalizedException` -bericht, wat leidt tot onvoldoende foutdetails voor foutopsporing.

<u> Stappen om </u> te reproduceren:

1. Installeer een schone **[!DNL Adobe Commerce]** -instantie.
1. Voeg een product aan de kar toe en ga aan de stap van de orderplaatsing te werk.
1. Voeg een `LocalizedException` toe aan `Magento\Framework\Exception\LocalizedException` in `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php` .
1. Voeg de uitzondering in na de volgende regel:

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   Voeg de uitzondering toe:

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. Voer de plaatsorder GraphQL-aanvraag uit:

   ```
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. Bekijk het antwoord:
   1. Het bericht `LocalizedException` is niet opgenomen in het antwoord.
   1. Voorbeeld van een onjuiste reactie:

      ```
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u> Verwachte resultaten </u>:

Als een `LocalizedException` voorkomt, zou het uitzonderingsbericht in de reactie van GraphQL van de plaatsplaatsing van de orde voor betere fout behandeling moeten worden omvat.

<u> Ware resultaten </u>:

Als een `LocalizedException` voorkomt, is het uitzonderingsbericht niet inbegrepen in de orde plaatsing GraphQL reactie.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
