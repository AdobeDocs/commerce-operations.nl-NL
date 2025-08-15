---
title: 'ACSD-66041: postcodes in Ierland (IE) kunnen niet worden doorzocht naar ophaallocaties vanwege ontbrekende CountryID'
description: Pas de ACSD-66041-patch toe om het Adobe Commerce-probleem op te lossen waarbij Ierse postcodes (IE) niet konden worden gezocht naar ophaallocaties vanwege een ontbrekende CountryID.
feature: Shipping/Delivery, Shopping Cart
role: Admin, Developer
type: Troubleshooting
exl-id: 4c33da14-38b2-4a3c-a680-849b62dfb896
source-git-commit: fcbc85eaa6aceb5c02929d5b9dbee24f184c03b4
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# ACSD-66041: postcodes in Ierland (IE) kunnen niet worden doorzocht naar ophaallocaties omdat deze ontbreken `CountryID`

De ACSD-66041-patch verhelpt het probleem waarbij Ierse postcodes (IE) niet kunnen worden doorzocht naar ophaallocaties omdat er een ontbrekende `CountryID` is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 wordt geïnstalleerd. De patch-id is ACSD-66041. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Postcodes in Ierland (IE) kunnen niet worden doorzocht op ophaallocaties omdat er een ontbrekende `CountryID` is.

<u> Stappen om </u> te reproduceren:

1. Voer de volgende GraphQL-query uit:

   ```graphql
   query getStoresTestError($term: String!, $radius: Int!) {
       pickupLocations(
           sort: { distance: ASC }
           area: { radius: $radius, search_term: $term }
       ) {
           items {
                   pickup_location_code
                   name
                   description
   		    latitude
   		    longitude
   		    country_id
   		    region
   		    city
   		    street
   		    postcode
   		    phone
           }
       }
   }
   ```

1. Gebruik de volgende variabelen:

   ```
   {
       "radius": 81,
       "term": "dublin:IE"
   }
   ```

<u> Verwachte resultaten </u>:

Postcodes voor Ierland zijn beschikbaar voor het zoeken naar ophaallocaties.

<u> Ware resultaten </u>:

* Een *Interne Fout van de Server* is teruggekeerd.
* `var/log/exception.log` bevat de volgende fout:

  ```
  report.ERROR: Provided countryId does not exist.  {"exception":"[object] (GraphQL\\Error\\Error(code: 0): Provided countryId does not exist.
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
