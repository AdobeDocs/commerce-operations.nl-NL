---
title: 'ACSD-63325: De Fout van de syntaxis: Onverwachte &lt;EOF&gt; fout wanneer het voorleggen van leeg  [!DNL GraphQL]  verzoek'
description: Pas ACSD-63325 flard toe om de kwestie van Adobe Commerce te bevestigen waar een syntaxisfout voorkomt wanneer het voorleggen van een leeg  [!DNL GraphQL]  verzoek.
feature: GraphQL
Role: Admin, Developer
exl-id: a83a8c5f-a43a-4733-a601-7b92656e5325
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# ACSD-63325: &quot;Syntaxisfout: Onverwachte &lt; EOF >&quot;-fout bij het indienen van een lege [!DNL GraphQL] -aanvraag

De ACSD-63325-patch verhelpt het probleem waarbij een &quot;Syntaxisfout: Unexpected &lt; EOF >&quot;-fout en een niet-200-antwoordcode worden geretourneerd bij het indienen van een lege [!DNL GraphQL] -aanvraag. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-63325. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij het verzenden van een lege [!DNL GraphQL] aanvraag is er een interne HTTP-serverfout in plaats van een 200-antwoordcode.

<u> Stappen om </u> te reproduceren:

1. Een leeg GraphQL-verzoek verzenden

   ```graphql
   curl -i -X OPTIONS http://commerce.local/graphql
   ```

<u> Verwachte resultaten </u>:

De antwoordcode is 200 voor het verzoek.

```
curl -i -X OPTIONS http://commerce.local/graphql
```

<u> Ware resultaten </u>:

Er treedt een interne serverfout van 500 op, zoals getoond:

```
HTTP/1.1 500 Internal Server Error
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op de Infrastructuur van de Wolk: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
