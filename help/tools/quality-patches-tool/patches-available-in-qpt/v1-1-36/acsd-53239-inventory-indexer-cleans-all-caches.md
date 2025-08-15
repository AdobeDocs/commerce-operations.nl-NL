---
title: 'ACSD-53239: Inventory indexer wist alle caches'
description: Pas de ACSD-53239-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de inventarisindexator alle caches in de modus [!UICONTROL Update on Schedule] wist.
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: 69e71e2d-8f26-4200-ad4a-6bd9e45627e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-53239: De indexeerder van de inventaris schrapt alle geheime voorgeheugens op [!UICONTROL Update on Schedule] wijze

De ACSD-53239-patch verhelpt het probleem waarbij de inventarisindexator alle caches in de modus [!UICONTROL Update on Schedule] wist. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36 wordt geïnstalleerd. De patch-id is ACSD-53239. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De inventarisindexeerder wist alle geheime voorgeheugens in de [!UICONTROL Update on Schedule] wijze.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** en selecteer ongeveer *1200* producten.
2. Werk *[!UICONTROL Qty]* bij naar een nieuwe waarde en klik op **[!UICONTROL Save]** .
3. Voer `bin/magento cron:run` onmiddellijk uit na het opslaan.
4. Voer de volgende GraphQL-query uit:

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u> Verwachte resultaten </u>

De query wordt binnen de gebruikelijke tijd verwerkt.

<u> Ware resultaten </u>

De query wordt ongebruikelijk traag verwerkt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
