---
title: 'ACSD-61622: [!DNL FedEx]  de rekeningsspecifieke tarieven ontbreken in REST API reactie'
description: Pas ACSD-61622 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL FedEx]  rekeningsspecifieke tarieven van de REST API reactie missen.
feature: Shipping/Delivery
role: Admin, Developer
source-git-commit: 24acc5f369e0001c8aeab3f81a2e1b51bc523333
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622: [!DNL FedEx] accountspecifieke snelheden ontbreken in REST API-respons

De ACSD-61622-patch verhelpt het probleem waarbij [!DNL FedEx's] -accountspecifieke frequenties ontbreken in de REST API-respons. Het `ACCOUNT` rate request type wordt toegevoegd aan de REST API request sent from Adobe Commerce to [!DNL FedEx] , dat een reactie retourneert die vergelijkbaar is met SOAP API response. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-61622. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

In de REST API-reactie ontbreken de accountspecifieke frequenties van [!DNL FedEx's] .

<u> Stappen om </u> te reproduceren:

1. Installeer een schoon Adobe Commerce-exemplaar.
1. Maak een eenvoudig product met een gewicht van 5 lbs.
1. Configureer [!DNL FedEx] voor REST API.
1. Schakel [!DNL FedEx] -verzendmethode in en wis de cache.
1. Waarnemen van logbestand beginnen: `var/log/shipping.log`
1. Voeg een eenvoudig product toe aan de winkelwagentje en ga naar de verzendpagina bij de afhandeling. Voorbeeld van klantgegevens:

   * Postcode: 58601
   * Namen: Jan Doe
   * Adres: 196 Eulalia Burg
   * Land: VS
   * Staat: North Dakota
   * Telefoonnummer: 187-563-3627

<u> Verwachte resultaten </u>:

`PAYOR_ACCOUNT_PACKAGE` -snelheden zijn beschikbaar in de REST API-respons, vergelijkbaar met SOAP API-reacties.

<u> Ware resultaten </u>:

In de reactie zijn alleen `PAYOR_LIST_PACKAGE` -snelheden beschikbaar, wat betekent dat er geen onderhandelde (account)tarieven van [!DNL FedEx] zijn.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
