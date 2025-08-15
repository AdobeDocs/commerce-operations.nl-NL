---
title: 'ACSD-63572: De indexeertabellen ` catalogrule` worden niet schoongemaakt als het indexeerproces wordt beëindigd'
description: Pas de ACSD-63572-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de indexeertabellen niet worden opgeschoond toen het proces werd beëindigd vanwege een systeemupgrade of stilstand in [!UICONTROL CLI] .
feature: System
Role: Admin, Developers
exl-id: 1cab7058-ca20-4d43-bfca-9b0e3ad35f42
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-63572: `catalogrule` tijdelijke indextabellen worden niet schoongemaakt als het indexeerproces wordt beëindigd

De ACSD-63572-patch verhelpt het probleem waarbij de tijdelijke indexeertabellen niet worden opgeschoond wanneer het proces werd beëindigd vanwege een systeem/upgrade of stilstand in [!UICONTROL CLI] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-63572. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Tijdelijke tabellen met indexering worden niet opgeschoond wanneer het proces werd beëindigd vanwege een systeemupgrade of stilstand in [!UICONTROL CLI] .

<u> Stappen om </u> te reproduceren:

1. Open [!UICONTROL CLI].
1. Uitvoeren, opdracht: `bin/magento indexer:reindex catalogrule_rule`.
1. Annuleer het proces voordat het is voltooid met: `^C` .
1. Stel indexen opnieuw in met: `bin/magento indexer:reset catalogrule_rule catalogrule_product`.
1. Herhaal de vorige stappen een aantal keren.
1. Controleren op de volgende tijdelijke tabellen die in de database zijn gemaakt:

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u> Verwachte resultaten </u>:

De oude tijdelijke tabellen worden verwijderd wanneer deze niet nodig zijn.

<u> Ware resultaten </u>:

De oude tijdelijke tabellen worden niet verwijderd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
