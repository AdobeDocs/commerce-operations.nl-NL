---
title: 'ACSD-63329: Datum- en tijdkenmerken worden niet ingesteld bij het maken van producten met de REST API'
description: Pas de ACSD-63329-patch toe om het Adobe Commerce-probleem op te lossen, waarbij geen standaardwaarden zijn ingesteld voor de datum- en tijdvelden wanneer u producten maakt met de REST API.
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63329: standaardwaarden voor datum- en tijdvelden worden niet ingesteld bij het maken van producten met de REST API

De ACSD-63329-patch verhelpt het probleem dat er geen standaardwaarden zijn ingesteld voor de datum- en tijdvelden bij het maken van een nieuw product met REST API: `/rest/default/V1/products` . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-63329. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Standaardwaarden worden niet ingesteld voor de datum- en tijdvelden wanneer u producten maakt met de REST API: `/rest/default/V1/products`

<u> Stappen om </u> te reproduceren:

1. Maak een **[!UICONTROL Product]** -kenmerk, stel de standaardwaarde ervan in op `12/31/2020` en stel **[!UICONTROL Catalog Input Type for Store Owner]** in op ***[!UICONTROL Date]*** of *** [!UICONTROL Date and Time] &#x200B;***.
1. Creeer een ander teksttypeattribuut en plaats de standaardwaarde aan ***testwaarde***.
1. Maak een nieuw product met een REST API POST request to `/rest/all/V1/products/`.

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. Controleer de opgeslagen waarden voor de bovenstaande kenmerken.

<u> Verwachte resultaten </u>:

De standaardwaarde moet worden opgeslagen in **[!UICONTROL Date/Datetime]** -tekstkenmerken wanneer u een product maakt met de API.

<u> Ware resultaten </u>:

De standaardwaarde wordt opgeslagen voor het kenmerk **[!UICONTROL Text]** , maar niet voor het kenmerk **[!UICONTROL Date type]** . De waarde voor het kenmerk **[!UICONTROL Date]** is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
