---
title: 'ACSD-62635: Meerdere opslaggerelateerde producten die onjuist worden weergegeven in  [!DNL GraphQL]'
description: Pas ACSD-62635 flard toe om de kwestie van Adobe Commerce te bevestigen waar de multi-store verwante producten niet behoorlijk in de  [!DNL GraphQL]  productvraag tonen.
feature: B2B
role: Admin, Developer
exl-id: 540cd37b-4dc5-42d1-a968-2989262effdd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-62635: Meerdere winkelgerelateerde producten worden onjuist weergegeven in [!DNL GraphQL]

De ACSD-62635-patch verhelpt het probleem dat verwante producten met meerdere opslaglocaties niet correct worden weergegeven in de productquery van [!DNL GraphQL] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-62635. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer B2B wordt toegelaten, [!DNL GraphQL] keert het verzoek alle verwante producten van alle websites terug zelfs als een werkingsgebied van de archiefmening in het verzoek wordt gebruikt.

<u> Stappen om </u> te reproduceren:

1. Maak twee websites, sla deze op en sla weergaven op.
1. Maak de volgende eenvoudige producten:
   * Één hoofd met SKU *product1* die aan alle websites wordt toegewezen
   * Één die slechts aan *Website 1* wordt toegewezen
   * Één die slechts aan *Website 2* wordt toegewezen
   * Één toegewezen aan zowel *Website 1* als *Website 2*
1. Voeg alle producten zoals verwant met *product1* toe.
1. Schakel [!UICONTROL B2B] en [!UICONTROL Shared Catalog] in.
1. Alle producten toevoegen aan de standaard gedeelde catalogus.
1. Verzend [!DNL GraphQL] verzoek om *product1* en zijn verwante producten met de opslagcode van *Website 1* in de kopbal terug te winnen.

<u> Verwachte resultaten </u>:

De reactie bevat alleen verwante producten van de websites die overeenkomen met de opslagcode die in de aanvraagkoptekst is verzonden.

<u> Ware resultaten </u>:

De reactie bevat alle verwante producten van alle websites, ongeacht de opslagcode die in de aanvraag is opgegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
