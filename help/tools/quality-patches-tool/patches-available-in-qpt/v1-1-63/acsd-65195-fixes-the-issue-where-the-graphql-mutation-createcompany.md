---
title: 'ACSD-65195: mutatie GraphQL ` createCompany ` keert een fout voor een land zonder een vereiste regio terug'
description: Pas de ACSD-65195-patch toe om het Adobe Commerce-probleem op te lossen waarbij de GraphQL ` createCompany`-mutatie een fout veroorzaakt voor landen die geen regio nodig hebben.
feature: B2B, Companies, GraphQL
role: Admin, Developer
source-git-commit: 8eb1d7f9d787ddb3b1cc619744920ab8a9914ae8
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# ACSD-65195: GraphQL `createCompany` -mutatie retourneert een fout voor een land zonder vereiste regio

De ACSD-65195-patch verhelpt het probleem waarbij de [!UICONTROL GraphQL] `createCompany` -mutatie een fout veroorzaakt voor landen die geen regio nodig hebben. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 wordt geïnstalleerd. De patch-id is ACSD-65195. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De mutatie [!UICONTROL GraphQL] `createCompany` retourneert een fout wanneer een gebied wordt opgegeven voor een land dat er geen nodig heeft.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL B2B Companies]** in.
1. Verzend de `createCompany` [!UICONTROL GraphQL] -mutatie met een veld voor een bepaald gebied voor een land dat deze niet nodig heeft. Bijvoorbeeld: [!UICONTROL country_id]: *AE* en [!UICONTROL region]: *Dubai*.
1. Controleer het GraphQL-antwoord.

<u> Verwachte resultaten </u>:

Het bedrijf moet met succes worden opgericht zonder een fout te retourneren wanneer een regio is opgegeven voor een land dat geen regio nodig heeft.

<u> Ware resultaten </u>:

Het bedrijf wordt niet gemaakt en de volgende fout wordt geretourneerd:
`Error: Invalid value of "Dubai" provided for the region field.`

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce on cloud Infrastructure: Upgrades and Patches > Apply Patches in the Commerce on Cloud Infrastructure guide.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
