---
title: 'ACSD-62872: planningupdates zijn onjuist gevalideerd'
description: Pas de ACSD-62872-patch toe om het Adobe Commerce-probleem op te lossen met unieke kenmerkvalidatie waarbij geplande updates onjuist worden gevalideerd.
feature: Catalog Management, Admin Workspace
role: Admin, Developer
exl-id: bd0d452b-aae3-4682-8a2c-471a7f8bf132
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---

# ACSD-62872: planningupdates zijn onjuist gevalideerd

De ACSD-62872-patch verhelpt het probleem met unieke kenmerkvalidatie waarbij geplande updates onjuist worden gevalideerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-62872. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch is gemarkeerd als verouderd voor versies 2.4.4 - 2.4.6-p8 in de 1.1.58 QPT-release.

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Geplande update naar een aangepast kenmerk wordt onjuist gevalideerd.

<u> Stappen om </u> te reproduceren:

1. Maak een aangepast kenmerk voor categorieën.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Maak een nieuwe categorie.
1. Ga in dezelfde categorie naar de sectie **[!UICONTROL Scheduled Updates]** .
1. Stel op elk gewenst moment een nieuwe update voor deze categorie in.
1. Voordat u de geplande update start, probeert u de gemaakte planningupdate voor de categorie te bewerken.

<u> Verwachte resultaten </u>:

Moet de geplande update kunnen bijwerken.

<u> Ware resultaten </u>:

Een fout wordt geworpen: *de waarde van het &quot;attribuut van de Douane&quot;is niet uniek. Plaats een unieke waarde en probeer opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op de Infrastructuur van de Wolk: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
