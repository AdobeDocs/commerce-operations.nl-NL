---
title: 'ACSD-65775: Onjuiste "base_row_total"- en "row_total"-waarden in REST API-ordergegevens voor meerdere hoeveelheden'
description: Pas de ACSD-65775-patch toe om het Adobe Commerce-probleem op te lossen waarbij de REST API-orderdetails onjuiste "base_row_total"- en "row_total"-waarden retourneren wanneer meerdere hoeveelheden van hetzelfde item zijn geordend.
feature: REST
role: Admin, Developer
type: Troubleshooting
exl-id: c2a8f4ef-3998-4e73-af9e-69b17a10d684
source-git-commit: ce5a136dd59c52d5fa5b555b3ee74fe14d7e53a4
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---

# ACSD-65775: onjuiste `base_row_total` en `row_total` waarden in REST API-ordergegevens voor meerdere hoeveelheden

De ACSD-65775-patch verhelpt het probleem waarbij de REST API-ordergegevens onjuiste `base_row_total` - en `row_total` -waarden retourneren wanneer meerdere hoeveelheden van hetzelfde item zijn geordend. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 wordt geïnstalleerd. De patch-id is ACSD-65775. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De antwoorden `base_row_total` en `row_total` in de orderdetails REST API tonen de eenheidsprijs in plaats van de totale prijs wanneer meerdere hoeveelheden van hetzelfde item worden besteld.

<u> Stappen om </u> te reproduceren:

1. Maak twee eenvoudige producten: simple1 geprijsd voor $10 en simple2 geprijsd voor $15.
1. Maak een nieuwe klantenaccount.
1. Voeg simple1 toe aan het winkelwagentje met hoeveelheid 2 en simple2 met hoeveelheid 3.
1. Plaats de bestelling met behulp van de klantenaccount.
1. Verkrijg een beheerstoken door een POST- verzoek naar `/rest/V1/integration/admin/token` met de volgende nuttige lading te verzenden:

   ```
   {
     "username": "admin",
     "password": "password"
   }
   ```

1. Haal de ordergegevens op met een GET-aanvraag naar `/rest/default/V1/orders/1` .

<u> Verwachte resultaten </u>:

`base_row_total` en `row_total` moeten de totale prijs weergeven die is berekend als hoeveelheid vermenigvuldigd met de objectprijs (bijvoorbeeld 2 × $10 = $20 voor simple1).

<u> Ware resultaten </u>:

`base_row_total` en `row_total` retourneren alleen de eenheidsprijs (bijvoorbeeld $10 voor simple1 in plaats van $20).

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
