---
title: 'ACP2E-3789: Mediabestanden gedupliceerd bij productupdate via WebAPI'
description: Pas de ACP2E-3789-patch toe om het Adobe Commerce-probleem op te lossen, waarbij productupdates via WebAPI gedupliceerde mediabestanden bevatten wanneer een media-id wordt opgegeven.
feature: Catalog Management, Media, REST, Products, Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8c1924a47248b22327dfc9a15ae426b2802e126b
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACP2E-3789: Mediabestanden gedupliceerd bij productupdate via WebAPI

De ACP2E-3789-patch verhelpt het probleem waarbij productupdates via WebAPI gedupliceerde mediabestanden bevatten wanneer een media-id wordt geleverd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 wordt geïnstalleerd. De patch-id is ACP2E-3789. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een product via WebAPI bijwerkt met een media-id, dupliceert het systeem mediabestanden in plaats van deze te vervangen. Er worden nieuwe bestanden gemaakt met elke API-aanroep. Dit leidt tot een samenstel van afbeeldingen die de `/pub/media/catalog/products/cache/` -map overladen.

<u> Stappen om </u> te reproduceren:

1. Maak een product en voeg een afbeelding toe.
1. Haal productgegevens op via de REST API op `base_url/rest/V1/products/<sku>` .
1. Voer een PUT-verzoek uit om het product bij te werken, waarbij `media_gallery_entrie` ongewijzigd blijft (dezelfde naam en hetzelfde bestand).
1. Controleer de map `pub/media/catalog/product/xx/yy` voor en na de update.

<u> Verwachte resultaten </u>:

Het afbeeldingsbestand wordt vervangen wanneer de media-id in de aanvraag wordt opgenomen.

<u> Ware resultaten </u>:

De afbeelding wordt gedupliceerd met een nieuwe naam (bijvoorbeeld wb04-blue-1.jpg), waardoor het bestand onnodig wordt opgebouwd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
