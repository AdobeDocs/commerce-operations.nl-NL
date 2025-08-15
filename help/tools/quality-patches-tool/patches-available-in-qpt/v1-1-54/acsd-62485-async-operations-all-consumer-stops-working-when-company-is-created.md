---
title: 'ACSD-62485: &grave; async.operations.all&grave; de consument houdt op werkend wanneer het bedrijf wordt gecreeerd'
description: Pas het ACSD-62485 flard toe om de kwestie van Adobe Commerce te bevestigen waar de consument &grave; async.operations.all' ophoudt werkend wanneer een bedrijf B2B wordt gecreeerd.
feature: B2B, Companies
role: Admin, Developer
exl-id: 99d20555-fe55-4a04-a067-5a2b104811f5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# ACSD-62485: `async.operations.all` de consument werkt niet meer wanneer het bedrijf wordt gemaakt

De ACSD-62485-patch verhelpt het probleem waarbij de `async.operations.all` -consument stopt met werken wanneer een B2B-bedrijf wordt gemaakt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 is geïnstalleerd. De patch-id is ACSD-62485. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p7

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7, 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `async.operations.all` consument houdt op verwerkend berichten als een bedrijf B2B asynchroon wordt gecreeerd terwijl de consument nog loopt.

<u> Eerste vereisten </u>:

B2B-modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Maak twee klanten.
1. Verzend een REST bulkverzoek om twee bedrijven tot stand te brengen, toewijzend de gecreeerde klanten als bedrijfbeheerders.
1. Begin de consument gebruikend het volgende bevel:

   ``` bin/magento queue:consumer:start async.operations.all --max-messages=20000 ```

<u> Verwachte resultaten </u>:

De consument verwerkt 20.000 berichten en beëindigt succesvol.

<u> Ware resultaten </u>:

De consument houdt onmiddellijk op met zijn werk.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
