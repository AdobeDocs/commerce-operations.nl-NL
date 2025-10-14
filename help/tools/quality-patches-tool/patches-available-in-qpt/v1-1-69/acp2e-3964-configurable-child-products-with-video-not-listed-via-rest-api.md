---
title: 'ACP2E-3964: configureerbare onderliggende producten met video die niet via REST API worden vermeld'
description: Pas de ACP2E-3964-patch toe om het Adobe Commerce-probleem op te lossen waarbij onderliggende producten van configureerbare producten met een video in de [!UICONTROL Media Gallery] niet via de REST API worden vermeld.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f48ced28035c65db561f4700113652574d302ec9
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---


# ACP2E-3964: configureerbare onderliggende producten met video die niet via REST API worden vermeld

De ACP2E-3964-patch verhelpt het probleem dat onderliggende producten van configureerbare producten met een video in de **[!UICONTROL Media Gallery]** niet via de REST API worden vermeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACP2E-3964. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onderliggende producten van configureerbare producten met een video in de **[!UICONTROL Media Gallery]** kunnen niet via REST API worden weergegeven, wat resulteert in een foutreactie.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuw configureerbaar product en voeg één onderliggend product toe.
1. Bewerk het kindproduct en voeg een video onder **[!UICONTROL Images and Videos]** toe (bijvoorbeeld, [&#x200B; https://vimeo.com/1084537 &#x200B;](https://vimeo.com/1084537)).
1. Sla het onderliggende product op.
1. Verzend een GET-aanvraag naar het REST API-eindpunt: `rest/v1/configurable-products/%sku%/children` met een beheerderstoken.

<u> Verwachte resultaten </u>:

De REST-API moet de gegevens van het onderliggende product zonder fouten retourneren, inclusief de videogegevens in de **[!UICONTROL Media Gallery]** .

<u> Ware resultaten </u>:

De REST API retourneert een fout:

```
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
