---
title: 'ACP2E-3689: Meerdere problemen met de boomcategorie worden op diepere niveaus weergegeven en weerspiegelen ankerverhoudingen/niet-ankerrelaties'
description: Pas de ACS2E-3689-patch toe om het Adobe Commerce-probleem op te lossen met de vermelding van de categoriestructuur op meer dan diepte vier nesten en die ankerrelaties/niet-ankerrelaties weerspiegelt.
feature: Categories, Page Content
role: Admin, Developer
source-git-commit: af8b7b44274b828b3f60f92fd78f9f3d3983abb8
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---


# ACP2E-3689: Meerdere problemen met de boomcategorie worden op diepere niveaus weergegeven en weerspiegelen ankerverhoudingen/niet-ankerrelaties

>[!NOTE]
>
>Dit flard vervangt [ ACSD-62689 ](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-57/acsd-62689-customer-add-categories-issue-related-product-rules-and-widgets.md) voor versies 2.4.7 en hierboven.

De ACS2E-3689-patch verhelpt meerdere problemen met de weergave van de categoriestructuur op meer dan diepte vier nesting en weerspiegelt de relatie tussen anker en niet-anker. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 wordt geïnstalleerd. De patch-id is ACP2E-3689. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De categoriestructuur op diepere niveaus (4+) wordt niet correct weergegeven en weerspiegelt ankerrelaties/niet-ankerrelaties.

<u> Stappen om </u> te reproduceren:

1. Stel een categoriestructuur in met geneste categorieën van meer dan 4 niveaus.
1. Vouw de categoriestructuur in Beheer uit die op verschillende plaatsen wordt weergegeven:
   1. Stel een voorwaarde in [!UICONTROL Related Products Rule] en stel deze in op basis van categorieën.
   1. Maak een widget en selecteer [!UICONTROL Layout Updates] [!UICONTROL Anchor categories] .

<u> Verwachte resultaten </u>:

Alle niveaus van de categoriestructuur worden correct weergegeven.

<u> Ware resultaten </u>:

Alleen de eerste paar niveaus (&lt;4) van de categoriestructuur zijn beschikbaar.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
