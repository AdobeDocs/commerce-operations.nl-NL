---
title: 'ACSD-66404: De baan van het gewricht ontbreekt om veranderingslijsten te ontruimen toe te schrijven aan {de grenzen van de 0} transactiegrootte [!DNL Galera Cluster] '
description: Pas ACSD-66404 flard toe om de kwestie van Adobe Commerce te bevestigen waar met cron baan die geen veranderingslijsten ontruimt en  [!DNL Galera Cluster]  kwesties in het geval van grote hoeveelheid gegevens in deze lijsten veroorzaakt.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 42bd5934782ca65b891a36f61102083356c92e59
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66404: de baan van de Kroon slaagt er niet in om veranderingslijsten wegens [!DNL Galera Cluster] transactiegrootte grenzen te ontruimen

De ACSD-66404-patch verhelpt het probleem waarbij de snijtaak geen wijzigingstabellen wist, wat [!DNL Galera Cluster] -problemen veroorzaakt bij het verwerken van grote hoeveelheden gegevens. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-66404. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p6, 2.4.7-p6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De baan van de kroon ontruimt veranderingslijsten niet en veroorzaakt [!DNL Galera Cluster] kwesties in het geval van grote hoeveelheid gegevens in deze lijsten.

<u> Stappen om </u> te reproduceren:

1. Genereer veel producten met behulp van prestatieprofielen.
1. Voer een bulkupdate voor alle producten in het systeem uit, zodat zijn er veel ingangen in de lijst van `inventory_cl` OB.
1. Voer de `indexer_clean_all_changelogs` -uitsnijdtaak uit.

<u> Verwachte resultaten </u>:

De `indexer_clean_all_changelogs` -cron-taak kan wijzigingsopruiming uitvoeren bij grote wijzigingen (10+ GB) in meerdere verwijderquery&#39;s, zonder dat dit leidt tot [!DNL Galera Cluster] -problemen.

<u> Ware resultaten </u>:

De `indexer_clean_all_changelogs` -uitsnijdtaak voert een wijzigingsopruiming uit bij grote wijzigingen (10+ GB) in één verwijderquery, wat leidt tot [!DNL Galera Cluster] -problemen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Patches toepassen &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen
