---
title: 'ACSD-62872: planningupdates zijn onjuist gevalideerd'
description: Pas de ACSD-62872-patch toe om het Adobe Commerce-probleem op te lossen met unieke kenmerkvalidatie waarbij geplande updates onjuist worden gevalideerd.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
source-git-commit: f734dab2316237d60164a430eeabed17782b0ae6
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-62872: planningupdates zijn onjuist gevalideerd

De ACSD-62872-patch verhelpt het probleem met unieke kenmerkvalidatie waarbij geplande updates onjuist worden gevalideerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-62872. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Geplande update naar een aangepast kenmerk wordt onjuist gevalideerd.

<u> Stappen om </u> te reproduceren:

1. Maak een aangepast kenmerk voor categorieën.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Maak een nieuwe categorie.
1. Ga in dezelfde categorie naar de sectie **[!UICONTROL Scheduled Updates]** .
1. Stel een nieuwe update voor deze categorie in met een toekomstig tijdstip.
1. Voordat u de geplande update start, probeert u de gemaakte planningupdate voor de categorie te bewerken.

<u> Verwachte resultaten </u>:

Moet de geplande update kunnen bijwerken.

<u> Ware resultaten </u>:

Een fout wordt geworpen: *de waarde van het &quot;attribuut van de Douane&quot;is niet uniek. Plaats een unieke waarde en probeer opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
