---
title: 'ACSD-61103: Aantal mislukte pogingen wordt niet opnieuw ingesteld op nul nadat de klant zich heeft aangemeld via de API'
description: Pas ACSD-61103 flard toe om de kwestie van Adobe Commerce te bevestigen waar de mislukkingstelling in de lijst &grave; customer_entity &grave; niet aan nul wordt teruggesteld nadat een klant met succes door API eindpunten het programma opent.
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61103: Aantal mislukte pogingen wordt niet opnieuw ingesteld op nul nadat de klant zich heeft aangemeld via de API

De ACSD-61103-patch lost het probleem op waarbij het aantal fouten in de `customer_entity` -tabel niet wordt teruggezet op nul nadat een klant zich met succes heeft aangemeld via API-eindpunten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 is geïnstalleerd. De patch-id is ACSD-61103. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het aantal fouten in de tabel `customer_entity` wordt niet teruggezet op nul, zelfs niet nadat een klant zich met succes heeft aangemeld via API-eindpunten.

<u> Stappen om </u> te reproduceren:

1. Maak een klantenaccount.
1. Een klanttoken genereren via de API met onjuiste gegevens.
1. Controleer de kolom `failures_num` in de `customer_entity` DB-tabel voor de bovenstaande klant.
1. Genereer een klanttoken via de API en gebruik de juiste details.
1. Controleer de kolom `failures_num` in de `customer_entity` DB-tabel voor de bovenstaande klant.

<u> Verwachte resultaten </u>:

De kolom `failures_num` moet op 0 worden teruggezet nadat de juiste referenties zijn gebruikt om een klanttoken te genereren via de API.

<u> Ware resultaten </u>:

De kolom `failures_num` wordt niet teruggesteld aan 0 nadat het gebruiken van de correcte geloofsbrieven om een klantenteken via API te produceren.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
