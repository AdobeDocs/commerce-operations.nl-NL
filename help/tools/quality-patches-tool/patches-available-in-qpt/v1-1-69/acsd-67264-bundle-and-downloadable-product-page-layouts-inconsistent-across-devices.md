---
title: 'ACSD-67264: bundel en downloadbare productpaginalay-outs zijn inconsistent voor alle apparaten'
description: Pas de ACSD-67264-patch toe om de Adobe Commerce-bundel en downloadbare pagina's te repareren die tijdens layoutproblemen zijn opgetreden als gevolg van een herschikking van het mediablok met productinformatie.
feature: Page Content, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9b6794366ba552d86cdfc6a3d6f699c307fcd8f6
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---


# ACSD-67264: bundel en downloadbare productpaginalay-outs zijn inconsistent voor alle apparaten

De ACSD-67264-patch verhelpt het probleem dat de lay-outs voor bundelpagina&#39;s en downloadbare productpagina&#39;s op verschillende apparaten niet consistent zijn. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-67264. Dit probleem is opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij bundeling en downloadbare productpagina&#39;s traden layoutproblemen op als gevolg van een herschikking van het mediablok met productinformatie.

<u> Stappen om </u> te reproduceren:

1. Installeer de voorbeeldgegevens.
1. Open de productpagina van de bundel en controleer de lay-out op de Desktop.
1. Voeg de pagina met het bundelproduct toe aan de verlanglijst, navigeer naar de verlanglijst, klik op het pictogram Bewerken en controleer de lay-out.
1. Herhaal stap 2 en 3 voor een downloadbaar product.

<u> Verwachte resultaten </u>:

De PDP Bundel Product wordt weergegeven zonder problemen.

<u> Ware resultaten </u>:

De PDP van het Product van de Bundel wordt teruggegeven met willekeurige ruimten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Patches toepassen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen
