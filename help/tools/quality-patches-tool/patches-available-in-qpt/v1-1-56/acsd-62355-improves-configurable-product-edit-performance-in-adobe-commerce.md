---
title: 'ACSD-62355: verbetert configureerbare productbewerkingsprestaties in Adobe Commerce'
description: Pas de ACSD-62355-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de configureerbare pagina voor productbewerking langzaam wordt geladen wanneer het product is gebaseerd op talrijke kenmerken met veel waarden.
feature: Admin Workspace
role: Admin, Developer
exl-id: cd934aa9-901a-4f03-ab83-716131e6bd85
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355: verbetert configureerbare productbewerkingsprestaties in Adobe Commerce

De ACSD-62355-patch verhelpt het probleem van de trage laadtijden en het hoge geheugengebruik op de configureerbare productbewerkingspagina wanneer het product vele kenmerken met talrijke waarden heeft. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-62355. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De configureerbare productbewerkingspagina duurt lang om te laden wanneer het configureerbare product is gebaseerd op meerdere kenmerken met veel waarden, waardoor vertragingen optreden en problemen met time-out of geheugenlimieten kunnen optreden.

<u> Stappen om </u> te reproduceren:

1. Maak 9 nieuwe kenmerken in de standaardkenmerkset, elk is [!UICONTROL Filterable] en heeft [!UICONTROL Scope] : [!UICONTROL Global] .
   * Kenmerk 1: 50 opties
   * Kenmerk 2: 20 opties
   * Kenmerk 3: 10 opties
   * Kenmerk 4: 5 opties
   * Kenmerk 5: 5 opties
   * Kenmerk 6: 5 opties
   * Kenmerk 7: 5 opties
   * Kenmerk 8: 3 opties
   * Kenmerk 9: 2 opties

1. Maak 9 eenvoudige producten met combinaties van opties van de nieuwe kenmerken.
   * Product 1: eerste optie van elk kenmerk
   * Product 2: tweede optie van elk kenmerk
   * Product 3: derde optie van elk kenmerk
   * Product 4: vierde optie van elk kenmerk
   * Als een attribuut minder opties dan het aantal producten heeft, wijs de resterende producten aan willekeurige opties binnen dat attribuut toe.

1. Maak een configureerbaar product dat de nieuwe kenmerken gebruikt:
   * Voeg één kindproduct met de volgende configuratie toe:
      * Gebruik de laatste optie van Kenmerk 1, en de eerste optie van Attributen 2 tot 9.
      * Dit resulteert in 1 configureerbaar product en 1 kindproduct.
1. Ga naar het tabblad **[!UICONTROL Configurations]** van het configureerbare product.
1. Klik handmatig op **[!UICONTROL Add Products]** en voeg de eerder gemaakte eenvoudige producten een voor een toe.
1. Sla de wijzigingen na elke toevoeging op.
1. Terwijl u producten toevoegt, observeert u de laadtijd van de configureerbare productpagina.
1. Na het toevoegen van 7 producten, zou u een significante verhoging van het verbruik van RAM en pagina ladingstijd moeten opmerken

<u> Verwachte resultaten </u>:

Het productbewerkingsformulier moet snel en efficiënt worden geladen zonder overmatig geheugengebruik.

<u> Ware resultaten </u>:

Het bewerken van het configureerbare product duurt lang en kan leiden tot geheugenlimieten of time-outfouten.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
