---
title: 'MDVA-44562: Winkel-id voor aanhalingstekens die standaard worden overschreven door winkel-id'
description: De patch MDVA-44562 verhelpt het probleem waarbij de standaard store-id de winkel-id overschrijft voor prijsaanhalingstekens voor GraphQL-aanvragen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44562. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562: Winkel-id voor aanhalingstekens die standaard worden overschreven door winkel-id

De patch MDVA-44562 verhelpt het probleem waarbij de standaard store-id de winkel-id overschrijft voor prijsaanhalingstekens voor GraphQL-aanvragen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.16 geïnstalleerd is. De patch-id is MDVA-44562. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De winkel-id voor aanhalingstekens wordt overschreven door de standaardopslagid voor GraphQL-aanvragen.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe winkelweergave.
1. Maak een nieuw eenvoudig product met verschillende namen per winkelweergave.
1. Maak een nieuwe klant.
1. Verkrijg het token voor klantautorisatie.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Creeer een nieuw citaat voor de klant gebruikend het toestemmingstoken.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Voeg een product toe aan de kar.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Haal de inhoud van het winkelwagentje op voor de standaardwinkelweergave.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Haal de inhoud van het winkelwagentje op voor de nieuwe winkelweergave.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u> Verwachte resultaten </u>:

De reactie van de nieuwe winkelweergave toont de productnaam van de nieuwe winkelweergave.

<u> Ware resultaten </u>:

De reactie van de nieuwe archiefmening toont de productnaam opstelling onder de standaardarchiefmening.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
