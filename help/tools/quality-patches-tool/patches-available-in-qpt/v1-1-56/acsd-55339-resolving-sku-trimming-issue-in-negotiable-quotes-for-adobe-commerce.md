---
title: 'ACSD-55339: Oplossen van SKU-trimingprobleem in verhandelbare koersen voor Adobe Commerce'
description: Pas de ACSD-55339-patch toe om het Adobe Commerce-probleem op te lossen waarbij product-SKU's met voorloopnullen worden bijgesneden, wat onderhandelingsfouten veroorzaakt.
feature: B2B, Quotes
role: Admin, Developer
exl-id: 7a9f92df-fb3e-4723-b731-155c6c4fc431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339: Oplossen van SKU-trimingprobleem in verhandelbare koersen voor Adobe Commerce

De ACSD-55339-patch verhelpt het probleem waarbij product-SKU&#39;s met voorloopnullen worden bijgesneden, wat resulteert in fouten tijdens het onderhandelingsproces. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-55339. Het probleem wordt volgens de planning opgelost in Adobe Commerce B2B 1.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Numerieke product-SKU&#39;s met voorloopnullen worden bijgesneden wanneer ze worden gebruikt in verhandelbare aanhalingstekens. Dit resulteert in fouten die het bijwerken van hoeveelheden of het instellen van prijzen verhinderen.

<u> Stappen om </u> te reproduceren:

1. Navigeer naar de sectie voor het maken van producten in het deelvenster Beheer.
1. Stel de [!UICONTROL SKU] voor het product in op 01910.
1. Meld u aan bij de winkel en voer de volgende bewerkingen uit:
   1. Voeg een product toe aan de kar.
   1. De winkelwagen weergeven en bewerken.
   1. Vraag om een offerte.
1. Ga naar [!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View] en [!UICONTROL Add Products by SKU] - 01910.

**Nota:** SKU wordt getoond als *1910* in plaats van *01910*. Deze discrepantie voorkomt dat de gebruiker de hoeveelheid bijwerkt of prijzen vaststelt, aangezien er geen product met SKU 1910 in de catalogus voorkomt.

<u> Verwachte resultaten </u>:

Het verhandelbare aanhalingsteken kan zonder fouten worden bijgewerkt.

<u> Ware resultaten </u>:

Er wordt een waarschuwingsbericht weergegeven waarin wordt aangegeven dat het product niet bestaat.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
