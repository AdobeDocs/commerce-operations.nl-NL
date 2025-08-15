---
title: 'ACSD-61785: Het bijwerken van het belonings_warning_notification attribuut niet mogelijk via de mutatie van GraphQL en de vraag van REST API'
description: Pas de ACSD-61785-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het bijwerken van het attribuut 'beloning_warning_notification' niet mogelijk is via GraphQL-mutatie en REST API-aanroepen.
feature: REST, GraphQL, Rewards
role: Admin, Developer
exl-id: 41f40452-4240-4b4a-b1bc-0da23139f19f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---

# ACSD-61785: Het bijwerken van het belonings_warning_notification attribuut niet mogelijk via de mutatie van GraphQL en de vraag van REST API

De ACSD-61785-patch verhelpt het probleem dat het bijwerken van het `reward_warning_notification` -kenmerk niet mogelijk is via GraphQL-mutatie en REST API-aanroepen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-61785. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het bijwerken van het kenmerk `reward_warning_notification` is niet mogelijk via GraphQL-mutatie en REST API-aanroepen.

<u> Stappen om </u> te reproduceren:

1. Controle GraphQL en REST API schema/documentatie voor *Abonneren voor de Updates van het Saldo* en *Abonneren voor de Berichten van de Vervalsing van Punten*.

<u> Verwachte resultaten </u>:

Het is mogelijk om voor *Updates van het Saldo van de Beloningen* en voor *Punten de Meldingen van de Vervalsing* via GraphQL en REST API in te tekenen.

<u> Ware resultaten </u>:

GraphQL en REST API hebben deze functionaliteit niet.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
