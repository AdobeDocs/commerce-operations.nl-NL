---
title: 'ACSD-62671: [!DNL GraphQL]  keert geen bijgewerkt adres op eerste poging terug'
description: Pas ACSD-62671 flard toe om de kwestie van Adobe Commerce te bevestigen waar het a [!DNL GraphQL]  verzoek geen bijgewerkte adresinformatie op de eerste poging terugkeert.
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671: [!DNL GraphQL] retourneert het bijgewerkte adres niet bij de eerste poging

De ACSD-62671-patch verhelpt het probleem waarbij een [!DNL GraphQL] -aanvraag bij de eerste poging geen actuele adresgegevens retourneert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-62671. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het gebruiken van [!DNL GraphQL Application Server], keert het verzoek van het klantenadres niet de meest recente gegevens terug.

<u> Stappen om </u> te reproduceren:

1. Installeren en starten [!DNL GraphQL Application Server] .
1. Zorg ervoor dat het cachetype `graphQL_query_resolver_result` is ingeschakeld.
1. Gebruik [!DNL GraphQL] om:

   * Maak een klant.
   * Een token genereren.
   * Gebruik het token om meerdere adressen voor de bovenstaande klant te maken.

1. Verzend [!DNL GraphQL] verzoek om de adressen van de klant op te halen.
1. Voeg een nieuw adres aan de klant toe.
1. Herhaal het verzoek van Stap #4 veelvoudige tijden terwijl het controleren van de teruggekeerde adrestelling in de reactie.

<u> Verwachte resultaten </u>:

[!DNL GraphQL] reactie bevat het correcte aantal klantenadressen.

<u> Ware resultaten </u>:

Soms wordt een onjuist aantal adressen geretourneerd in het [!DNL GraphQL] -antwoord.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
