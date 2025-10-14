---
title: 'ACSD-55566: [!UICONTROL mergeCart] de mutatie ontbreekt met interne serverfout in  [!DNL GraphQL]  reactie'
description: Pas ACSD-55566 flard toe om de kwestie van Adobe Commerce te bevestigen waar de "mergeCart"mutatie met een interne serverfout in  [!DNL GraphQL]  reactie ontbreekt wanneer het samenvoegen van de bron en de bestemmingstaarten die de zelfde bundelpunten hebben.
feature: GraphQL, Shopping Cart
role: Admin, Developer
exl-id: 84c6fbb9-73b3-4197-aff3-49743f0ebb2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-55566: `mergeCart` mutatie mislukt bij interne serverfout in [!DNL GraphQL] response

De ACSD-55566-patch verhelpt het probleem waarbij de `mergeCart` -mutatie mislukt als er een interne serverfout optreedt in [!DNL GraphQL] -reactie. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 wordt geïnstalleerd. De patch-id is ACSD-5566. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

`mergeCart` mutatie mislukt met een interne serverfout in de reactie van [!DNL GraphQL] wanneer de bron- en doelwinkelwagentjes met dezelfde bundelitems worden samengevoegd.

<u> Stappen om </u> te reproduceren:

1. Een aangepaste bron en een aangepaste voorraad maken.
1. Wijs de gemaakte voorraad toe aan de hoofdwebsite.
1. Creeer een eenvoudig product en wijs aan het de gecreeerde bron (qty=2) toe.
1. Maak een bundelproduct met één optie en één onderliggend product (product gemaakt in stap 3).
1. Maak een gastenwagen via [!DNL GraphQL] .
1. Voeg een bundelproduct toe met beide geselecteerde opties.
1. Sparen *cartID*.
1. Maak een klant en genereer een klanttoken.
1. Maak een klantenkar.
1. Voeg hetzelfde bundelproduct met dezelfde configuratie toe aan het winkelwagentje.
1. Probeer de gastkar met de klantenkar samen te voegen.

<u> Verwachte resultaten </u>:

De klantenkar bevat producten van beide kisten.

<u> Ware resultaten </u>:

Er treedt een interne fout op.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
