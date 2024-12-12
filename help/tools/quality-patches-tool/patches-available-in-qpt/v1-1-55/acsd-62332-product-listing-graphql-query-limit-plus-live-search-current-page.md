---
title: 'ACSD-62332: De vraag van GraphQL van de lijst van het product beperkt tot 10.000 producten en  [!DNL Live Search]  plaatst huidige pagina aan 1'
description: Pas ACSD-62332 flard toe om de kwesties van Adobe Commerce te bevestigen waar de productlijst GraphQL vraag tot een total_count van 10.000 producten beperkt is en waar  [!DNL Live Search]  de huidige pagina aan *1* in plaats van pagina *2* in de onderzoekscriteria wanneer gevraagd via GraphQL plaatst.
feature: GraphQL, Products, Search
role: Admin, Developer
source-git-commit: 276fe6ca8d1166a8f4254aca5d49cbb4b1aa607b
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332: GraphQL-query voor productaanbieding beperkt tot 10.000 producten en [!DNL Live Search] stelt de huidige pagina in op 1

>[!NOTE]
>
>Dit flard is een bijgewerkte versie van [ ACSD-55100 ](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) en vervangt [ ACSD-52801 ](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) op 2.4.6 - 2.4.6-p8 versies. Zie de desbetreffende artikelen voor meer informatie.

ACSD-62332 flardmoeilijke situatie de kwesties waar de product lijst GraphQL vraag tot a `total_count` van 10.000 producten beperkt is en waar [!DNL Live Search] de huidige pagina aan *1* in plaats van pagina *2* in de onderzoekscriteria plaatst wanneer gevraagd via GraphQL. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-62332. De problemen zijn opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het product dat van GraphQL vraag een lijst maakt is beperkt tot een total_count van 10.000 producten en waar [!DNL Live Search] de huidige pagina aan *1* in plaats van pagina *2* in de onderzoekscriteria wanneer gevraagd via GraphQL plaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
