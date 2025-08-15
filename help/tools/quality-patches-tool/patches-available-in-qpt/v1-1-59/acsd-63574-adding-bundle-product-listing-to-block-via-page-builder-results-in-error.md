---
title: 'ACSD-63574: Het toevoegen van [!UICONTROL Bundle Product] lijst aan blok via  [!DNL Page Builder]  resulteert in fout'
description: Pas ACSD-63574 flard toe om de kwestie van Adobe Commerce te bevestigen waar het toevoegen ** [!UICONTROL Bundle Product]** met &grave; Checkbox &grave; of &grave; Multi Uitgezochte opties &grave; aan een blok via  [!DNL Page Builder]  in een fout resulteert.
feature: Page Builder, Page Content
role: Admin, Developer
exl-id: bb56c0c2-e094-4173-8260-da154df79748
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-63574: het toevoegen van [!UICONTROL Bundle Product] -vermelding om te blokkeren via [!DNL Page Builder] resulteert in een fout

De ACSD-63574-patch verhelpt het probleem dat het toevoegen van **[!UICONTROL Bundle Product]** met `Checkbox` - of `Multi Select` -opties aan een blok via [!DNL Page Builder] resulteert in een fout. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 wordt geïnstalleerd. De patch-id is ACSD-63574. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4-p10

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer het toevoegen van **[!UICONTROL Bundle Product]** aan een blok gebruikend [!DNL Page Builder], de voorproef van de product widget breekt en toont het foutenbericht *Wij vinden het jammer, is een fout voorgekomen terwijl het produceren van deze inhoud*. Dit probleem treedt specifiek op wanneer het bundelproduct `Checkbox` of `Multi Select` optietypen bevat en `indexer dimension mode` is ingesteld op `website_and_customer_group` . In het uitzonderingenlogboek wordt de volgende fout weergegeven:

    &quot;
     report.CRITICAL: PDOException: SQLSTATE[42S02]: De lijst of de mening van de basis niet gevonden: 1146 Lijst &quot;db_name.catalog_product_index_price_cg0_ws0&quot;bestaan niet in /home/vendor/magento/framework/DB/Statement/Pdo/Mysql.php:90 
    &quot;

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** .
1. Vouw in het linkerdeelvenster **[!UICONTROL Catalog]** uit en selecteer **[!UICONTROL Catalog]** in de onderstaande opties.
1. Schuif omlaag naar de sectie **[!UICONTROL Price]** en stel **[!UICONTROL Catalog Price Scope]** in op **[!UICONTROL Global]** .
1. Stel `Indexer dimension mode` in op `website_and_customer_group` met behulp van de onderstaande opdracht:

   `bin/magento indexer:set-dimensions-mode catalog_product_price website_and_customer_group`

1. Maak een **[!UICONTROL Bundle Product]** met een type bundeloptie `Checkbox` of `Multi Select` en wijs het product aan een categorie toe.
1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Blocks]** > **[!UICONTROL Edit Content with Page Builder]** .
1. Selecteer de categorie waaraan het gemaakte product is toegewezen en probeer **[!UICONTROL Save]** .

<u> Verwachte resultaten </u>:

Product zonder fouten toegevoegd.

<u> Ware resultaten </u>:

Kan geen product toevoegen tot en met [!DNL Page Builder] wanneer het optietype **[!UICONTROL Bundle Product]** `Checkbox` of `Multi Select` is en `indexer dimension mode` op `website_and_customer_group` is ingesteld. Het werpt de fout: *wij spijt, is een fout voorgekomen terwijl het produceren van deze inhoud*.


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
