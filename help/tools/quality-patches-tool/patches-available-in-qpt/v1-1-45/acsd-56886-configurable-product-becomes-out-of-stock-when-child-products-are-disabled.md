---
title: 'ACSD-56886: configureerbaar product is niet meer beschikbaar als onderliggende producten zijn uitgeschakeld'
description: Pas de ACSD-56886-patch toe om het Adobe Commerce-probleem op te lossen waarbij het configureerbare product uit voorraad komt te zitten wanneer de producten worden uitgeschakeld.
feature: Products
role: Admin, Developer
exl-id: 5e9c1fd4-b56a-42c0-83e7-75e868213124
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-56886: configureerbaar product is niet meer beschikbaar als onderliggende producten zijn uitgeschakeld

De ACSD-56886-patch verhelpt het probleem waarbij het configureerbare product uit voorraad raakt als onderliggende producten worden uitgeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-56886. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het configureerbare product wordt uit voorraad wanneer de kindproducten worden onbruikbaar gemaakt.

<u> Stappen om </u> te reproduceren:

1. Meld u aan als beheerder.
1. Stel alle indexen in de modus **[!UICONTROL Update By Schedule]** in.
1. Maak het volgende configureerbare product:

   * Naam = *CONFIGURABLE 1 VAN DE TEST*
   * Attribuut = *kleur*
   * Waarden = *rood* en *zwart*
   * Prijs van het **rode** kindproduct = *$100*;
   * Prijs van het &quot;zwarte&quot; onderliggende product = *$200*.

1. Maak de volgende geplande update voor het configureerbare product:

   * Datum van het begin = *3* notulen van nu.
   * Einddatum = *5* notulen na de Datum van het Begin.
   * De Naam van het product = *CONFIGURABLE 1 bewerkte TEST*.
   * Maak het **rode** kindproduct in **Configurable** sectie onbruikbaar.

1. Wacht op de Begindatum.
1. Open de configureerbare productdetails op de Storefront.

<u> Verwachte resultaten </u>:

Het configureerbare product wordt getoond als **in Voorraad** met **zo laag zoals 200** etiket.

<u> Ware resultaten </u>:

Het configureerbare product wordt getoond als **uit Voorraad**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
