---
title: 'ACSD-61805: Oplossingen voor aandelenprobleem bij opslag na statusupdate voor backorder via REST API'
description: Pas de ACSD-61805-patch toe om het Adobe Commerce-probleem op te lossen waarbij producten uit voorraad blijven op de winkel na het bijwerken van de backorder status via de REST API
feature: REST, Catalog Management, Inventory
role: Admin, Developer
exl-id: ff85e747-6394-43db-a02a-87b1e5e59f00
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61805: Oplossingen voor aandelenprobleem bij opslag na statusupdate voor backorder via REST API

De ACSD-61805-patch verhelpt het probleem waarbij producten uit voorraad blijven op de winkel nadat de status van de backorder via REST API is bijgewerkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-61805. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Producten blijven op voorraad na het bijwerken van de status van de backorder via REST API.

<u> Stappen om </u> te reproduceren:

1. Installeer een schone instantie met monstergegevens.
1. Maak een nieuwe inventarisbron.
1. Maak een nieuw voorraadbestand en wijs de nieuwe bron hieraan toe.
1. Wijs de nieuwe bron aan product 24-MB01 toe.
1. Stel **[!UICONTROL Source Item Status]** in op `In Stock` voor beide productbronnen.
1. Plaats de hoeveelheid (**[!UICONTROL QTY]**) aan *0* voor beide producthoeveelheden.
1. Sla het product op.
1. Haal het beheerstoken van dit eindpunt URL: `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. Werk het product bij met behulp van het eindpunt: `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. Voer de cron-taken twee keer uit (één keer om planningen te maken en één keer om de planning uit te voeren):

   ```bash
   bin/magento cron:run
   ```

1. Ga naar de voorzijde en controleer het product.

<u> Verwachte resultaten </u>:

Het product zou *in Voorraad* moeten zijn.

<u> Ware resultaten </u>:

Het product is *uit voorraad*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
