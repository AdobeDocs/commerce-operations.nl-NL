---
title: 'MDVA-43102: verkoopbare hoeveelheid niet correct bijgewerkt'
description: De MDVA-43102-patch verhelpt het probleem dat de verkoopbare hoeveelheid niet correct wordt bijgewerkt wanneer de restitutie via REST API wordt uitgevoerd. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 is geïnstalleerd. De patch-id is MDVA-43102. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: 6a10f586-bbde-4252-9b8e-9b2b712f0fb3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-43102: verkoopbare hoeveelheid niet correct bijgewerkt

De MDVA-43102-patch verhelpt het probleem dat de verkoopbare hoeveelheid niet correct wordt bijgewerkt wanneer de restitutie via REST API wordt uitgevoerd. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 geïnstalleerd is. De patch-id is MDVA-43102. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.1 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het verkoopbare aantal wordt niet correct bijgewerkt wanneer een terugbetaling met REST API wordt gedaan.

<u> Stappen om </u> te reproduceren:

1. Voeg een item aan het winkelwagentje toe.
1. Controleer de voorraadhoeveelheid en de koopste hoeveelheid.
1. Maak een bestelling.
1. Maak indien nodig een factuur.
1. Verzend een REST-verzoek om de factuur terug te betalen met de volgende lading:

   * offline methode/volgorde/`<order_id>`/restitutie
   * online methode/factuur/`<invoice_id>`/restitutie

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. Verzend de objecten niet.
1. Vergelijk de voorraadhoeveelheid en de Salable Qty van voordien. Beide moeten met hetzelfde bedrag worden bijgewerkt.

<u> Verwachte resultaten </u>:

De verkoopbare hoeveelheid wordt correct bijgewerkt wanneer een restitutie wordt afgegeven voordat de bestelling wordt verzonden en het product aan de voorraad wordt teruggegeven.

<u> Ware resultaten </u>:

De verkoopbare hoeveelheid wordt niet bijgewerkt wanneer een restitutie wordt afgegeven voordat de bestelling wordt verzonden en het product wordt teruggebracht naar de voorraad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
