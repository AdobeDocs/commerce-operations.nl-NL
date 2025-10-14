---
title: 'ACSD-52815: invoerveld voor kwantiteitsveld van niet-standaardbron ondersteunt slechts maximaal 6 cijfers'
description: Pas de ACSD-52815-patch toe om het Adobe Commerce-prestatieprobleem op te lossen, waarbij het invoerveld voor het kwantitatieve veld van een niet-standaard bron maximaal 6 cijfers ondersteunt, in tegenstelling tot 8 voor een standaardvoorraad.
feature: Inventory, Products
role: Admin
exl-id: d863af1f-8a7f-4a43-893e-54525ab68cd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# ACSD-52815: invoerveld voor kwantiteitsveld van niet-standaardbron ondersteunt slechts maximaal 6 cijfers

De ACSD-52815-patch verhelpt het probleem dat het invoerveld voor het kwantitatieve veld van een niet-standaardbron slechts maximaal zes cijfers ondersteunt, in tegenstelling tot 8 voor een standaardvoorraad. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52815. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het invoerveld voor het kwantitatieve veld van een niet-standaardbron ondersteunt slechts maximaal 6 cijfers, in tegenstelling tot 8 voor een standaardvoorraad.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuwe voorraad en bron.
1. Maak een product met de nieuwe bronvoorraad ingesteld op 123.
1. Controleer de verkoopbare hoeveelheid (123).
1. Werk de bronhoeveelheid bij naar 12345678.
1. Controleer de verkochte hoeveelheid opnieuw.

<u> Verwachte resultaten </u>:

De juiste hoeveelheid wordt aangegeven.

<u> Ware resultaten </u>:

De verkoopbare hoeveelheid bedraagt 999999,9999.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
