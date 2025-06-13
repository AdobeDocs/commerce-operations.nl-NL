---
title: 'MDVA-27239: Kruisverkoop wordt niet weergegeven'
description: De MDVA-27239-patch verhelpt het probleem waarbij cross-sell-producten niet worden weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 is geïnstalleerd. De kwestie is opgelost in Adobe Commerce 2.3.6.
feature: Products
role: Admin
exl-id: ab8fe64d-adbe-4756-be43-1a35ba6b4123
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-27239: Kruisverkoop wordt niet weergegeven

De MDVA-27239-patch verhelpt het probleem waarbij cross-sell-producten niet worden weergegeven. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.7 geïnstalleerd is. De kwestie is opgelost in Adobe Commerce 2.3.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.4, 2.4.0

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.5-p2, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Kruisverkoop-producten worden niet weergegeven in het cross-sellblok op de winkelwagentje.

<u> Eerste vereisten </u>:

1. Schakel de module Magento_TargetRule uit of verwijder deze uit het lay-outblok Magento\TargetRule\Block\Checkout\Cart\Crosssell.
1. Product 1 maken.
1. Creeer een planningsupdate voor Product 1, zodat zullen de nieuwe producten row_id verschillend van entity_id hebben.
1. Maak product 2, product 3 en product 4.
1. Stel Product 3 in als cross-sell voor Product 4.
1. Stel Product 4 in als cross-sell voor Product 2.

<u> Stappen om </u> te reproduceren:

1. Voeg product 4 en product 2 toe aan het winkelwagentje.
1. Controleer de winkelwagenpagina.

<u> Verwachte resultaten </u>:

Product 3 wordt weergegeven in een blok voor meerdere verkooppunten.

<u> Ware resultaten </u>:

Kruisverkoop is leeg.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
