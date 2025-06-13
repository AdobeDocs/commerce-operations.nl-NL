---
title: 'ACSD-59229: onjuiste toewijzing van gegevens aan de klantengroep als gevolg van een verouderde waarde voor X-Magento-variëren'
description: Pas de ACSD-59229-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de groepsgerelateerde informatie van de klant in het verkeerde segment wordt opgeslagen vanwege een verouderde X-Magento-waarde in het verzoek.
feature: Customers, Personalization, Marketing Tools
role: Admin, Developer
exl-id: c039c114-d920-4b05-b5e9-3e9b73490ee0
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# ACSD-59229: onjuiste toewijzing van gegevens aan de klantengroep als gevolg van een verouderde waarde voor X-Magento-variëren

De ACSD-59229-patch verhelpt het probleem waarbij de groepsgerelateerde informatie van de klant in het verkeerde segment wordt opgeslagen vanwege een verouderde X-Magento-waarde in het verzoek. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 wordt geïnstalleerd. De patch-id is ACSD-59229. De kwestie is opgelost in 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Aan de groep gerelateerde informatie van de klant wordt opgeslagen in het verkeerde segment vanwege een verouderde waarde voor X-Magento-Variant in het verzoek.

<u> Eerste vereisten </u>:

Controleer of Adobe Commerce B2B met voorbeeldgegevens is geïnstalleerd en of [!DNL Varnish] is geconfigureerd.

<u> Stappen om </u> te reproduceren:

1. Geavanceerde prijzen instellen voor de [!DNL SKU 24-MB01] :
   1. [!UICONTROL Regular price] = *9999$*
   1. [!UICONTROL Catalog and Tier Price]:
      * *Wholesale* = *$200*
      * *Retailer* = *$30*

1. Maak twee klantenaccounts.
1. Wijs beide klanten aan de **Groothandel** groep toe.
1. Open twee verschillende browsersessies en meld u aan bij elke klant.
1. Navigeer naar de **[!UICONTROL 24-MB01]** productpagina voor elke klant en controleer of de weergegeven prijs *$200* is.
1. Verander de klantengroep voor één van de klanten in **Detailhandel**.
1. Wis het cachegeheugen met de opdracht: `bin/magento cache:flush full_page` .
1. Vernieuw de productpagina voor elke klant.

<u> Verwachte resultaten </u>:

1. De detailhandelsklant kan de correcte prijs van *$30* voor het product zien.
1. De grootafnemer kan de correcte prijs van *$200* voor het product zien.

<u> Ware resultaten </u>:

1. De detailhandelsklant kan de correcte prijs van *$30* voor het product zien.
1. De grootafnemer ziet een onjuiste prijs van *$30* (kleinhandelsprijs) voor het product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
