---
title: 'ACSD-65913: [!DNL OpenSearch]  werpt een illegal_argument_exception voor categorieën met producten die de zelfde prijs hebben'
description: Pas ACSD-65913 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL Opensearch]  een illegal_argument_exception ("[van] parameter niet negatief kan zijn") op de categorieën die alle producten met de zelfde prijs bevatten.
feature: Search
role: Admin, Developer
type: Troubleshooting
source-git-commit: fa4c50fdf6b51c981e49369dc9f70600f46b5689
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---


# ACSD-65913: [!DNL OpenSearch] genereert een `illegal_argument_exception` voor categorieën met producten met dezelfde prijs

De ACSD-65913-patch verhelpt het probleem waarbij [!DNL OpenSearch] een `illegal_argument_exception` gooide voor categorieën met producten met dezelfde prijs. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 wordt geïnstalleerd. De patch-id is ACSD-65913. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL OpenSearch] werpt `illegal_argument_exception` (*[van ] parameter kan niet negatief zijn*) wanneer het laden van categorieën waarin alle producten de zelfde prijs deelden.

<u> Stappen om </u> te reproduceren:

1. Installeer [!DNL OpenSearch] versie 2.19.1 en stel deze in als de standaard zoekengine.
1. Configureer het productkenmerk **[!UICONTROL Price]** dat zichtbaar moet zijn in Gelaagde navigatie:
   1. **[!UICONTROL Visible in Advanced Search]**: *ja*
   1. **[!UICONTROL Comparable on Storefront]**: *ja*
   1. **[!UICONTROL Use in Layered Navigation]**: *Filterable (met resultaten)*
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Layered Navigation]** . Plaats **[!UICONTROL Price Navigation Step Calculation]** aan *Automatisch (vergelijk producttellingen)*.
1. Maak een categorie met zes producten die allemaal dezelfde prijs hebben:
   1. SKU: product_super_0-1-1-1, Prijs: $150
   1. SKU: product_super_0-1-1, Prijs: $48
   1. SKU: product_super_0-1, Prijs: $48
   1. SKU: product_super_0, Prijs: $48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1-1-1-1, Prijs: $48
   1. SKU: product_super_0-1-1-1-1-1-1-1-1-1-1-1, Prijs: $48
1. Voer de volgende opdracht uit:
   `bin/magento indexer:reindex`
1. Open de categoriepagina. Er wordt een fout weergegeven:
   *[van ] parameter kan niet negatief zijn, gevonden [ - 1]*

<u> Verwachte resultaten </u>:

[!DNL OpenSearch] mag geen `illegal_argument_exception` genereren wanneer alle producten in een categorie dezelfde prijs hebben.

<u> Ware resultaten </u>:

* [!DNL OpenSearch] genereert een `illegal_argument_exception` met het bericht:
  *[van ] parameter kan niet negatief zijn, gevonden [ - 1]*

* Het bestand `var/log/exception.log` bevat:

  ```
  [2025-05-14T22:39:33.595272+00:00] report.CRITICAL: [!DNL OpenSearch]\Common\Exceptions\BadRequest400Exception: {"error":{"root_cause":[{"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"}],"type":"illegal_argument_exception","reason":"[from] parameter cannot be negative, found [-1]"},"status":400}
  ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
