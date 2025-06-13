---
title: 'ACSD-61756: Verslechtering van prestaties van filters AdvancedSalesRule toe te schrijven aan ontbrekende gegevensbestandindexen'
description: Pas de ACSD-61756-patch toe om het Adobe Commerce-probleem te verhelpen, waarbij de query &grave; magento_salesrule_filter&grave; een volledige tabelscan uitvoert zonder indexen te gebruiken. Dit leidt tot prestatievermindering bij het verwerken van grote volumes records. Dit flard verbetert prestaties door de ontbrekende gegevensbestandindexen voor filters te toevoegen AdvancedSalesRule.
feature: Price Rules, Price Indexer
role: Admin, Developer
exl-id: 418c7c40-83ee-4cd9-8ebb-b356886ffb58
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-61756: Prestatievermindering van `AdvancedSalesRule` -filters als gevolg van ontbrekende database-indexen

Pas de ACSD-61756-patch toe om de prestaties van de `AdvancedSalesRule` -filters te verbeteren door ontbrekende database-indexen toe te voegen. Hiermee wordt het probleem verholpen waarbij de `magento_salesrule_filter` -query een volledige tabelscan uitvoert zonder de indexen te gebruiken. Dit leidt tot prestatievermindering wanneer de tabel veel records bevat. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54 wordt geïnstalleerd. De patch-id is ACSD-61756. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p9

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De query `magento_salesrule_filter` voert een volledige tabelscan uit zonder indexen te gebruiken. Dit leidt tot een verslechtering van de prestaties van de `AdvancedSalesRule` -filters wanneer de tabel veel records bevat.

<u> Stappen om </u> te reproduceren:

1. Afhandeling met meerdere actieve verkoopregels.

<u> Verwachte resultaten </u>:

Verbeterde prestaties van de verkoopregels.

<u> Ware resultaten </u>:

De query voert een volledige tabelscan uit en maakt geen gebruik van indexen. Dit leidt tot prestatievermindering wanneer de tabel veel records bevat.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
