---
title: "ACSD-52399: Product met een verkoopbare hoeveelheid 0 in voorraad"
description: Pas de ACSD-52399-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de configureerbare productoptie met een verkoopbare hoeveelheid van 0 *In Stock* op de productpagina wordt weergegeven.
feature: Products, Configuration
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-52399: product met verkoopbare hoeveelheid 0 in voorraad

Het ACSD-52399 flard bevestigt de kwestie waar de configureerbare productoptie met een verkoopbare hoeveelheid nul (0) *toont In Voorraad* op de productpagina. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.35 wordt geïnstalleerd. De patch-id is ACSD-52399. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De configureerbare productoptie met een verkoopbare hoeveelheid van nul (0) toont *In Voorraad* op de productpagina.

<u> Stappen om </u> te reproduceren:

1. Maak een configureerbaar product met de optie 0 (verkoopbaar) product.
1. Ga naar de productpagina op de winkel en selecteer het configureerbare product om een variatie/configuratie te controleren.
1. Selecteer **[!UICONTROL Add to Cart]** .

<u> Verwachte resultaten </u>:

*[!UICONTROL Add to Cart]* knoop is niet beschikbaar wanneer het selecteren *uit voorraad* productconfiguratie.

<u> Ware resultaten </u>:

Configureerbare variaties zijn beschikbaar op de winkelserver en u kunt ze selecteren en aan de winkelwagentje toevoegen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.