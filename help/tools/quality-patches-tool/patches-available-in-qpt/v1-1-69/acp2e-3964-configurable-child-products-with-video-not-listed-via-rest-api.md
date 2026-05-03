---
title: 'ACS2E-3964: Configureerbare onderliggende producten met video die niet via REST API worden vermeld'
description: Pas de ACP2E-3964-patch toe om het Adobe Commerce-probleem op te lossen waarbij onderliggende producten van configureerbare producten met een video in de [!UICONTROL Media Gallery] niet via de REST API worden vermeld.
feature: Products, Media, REST, Catalog Management
role: Admin, Developer
type: Troubleshooting
exl-id: 61c5b97c-79aa-4ee7-96b3-70924d2c85a0
source-git-commit: 319f3232d1ba5f5ed7cdd10ce85b9d7ffbeec89a
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACS2E-3964: Configureerbare onderliggende producten met video die niet via REST API worden vermeld

De ACP2E-3964-patch verhelpt het probleem dat onderliggende producten van configureerbare producten met een video in de **[!UICONTROL Media Gallery]** niet via de REST API worden vermeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACP2E-3964. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onderliggende producten van configureerbare producten met een video in de **[!UICONTROL Media Gallery]** kunnen niet via REST API worden weergegeven, wat resulteert in een foutreactie.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuw configureerbaar product en voeg één onderliggend product toe.
1. Bewerk het kindproduct en voeg een video onder **[!UICONTROL Images and Videos]** toe (bijvoorbeeld, [&#x200B; https://vimeo.com/1084537 &#x200B;](https://vimeo.com/1084537)).
1. Sla het onderliggende product op.
1. Verzend een GET-aanvraag naar het REST API-eindpunt: `rest/v1/configurable-products/%sku%/children` gebruiken van een beheerderstoken.

<u> Verwachte resultaten </u>:

De REST-API moet de gegevens van het onderliggende product zonder fouten retourneren, inclusief de videogegevens in de **[!UICONTROL Media Gallery]** .

<u> Ware resultaten </u>:

De REST API retourneert een fout:

```text
Error: Call to a member function getVideoProvider() on null in vendor/magento/module-product-video/Model/Product/Attribute/Media/ExternalVideoEntryConverter.php:87
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
