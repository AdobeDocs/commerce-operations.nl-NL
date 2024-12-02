---
title: 'MDVA-40550: Producten die aan de voorzijde ontbreken na redexering'
description: Met de MDVA-40550-patch wordt het probleem opgelost waarbij opnieuw indexeren leidt tot enkele of alle ontbrekende producten in de winkelcategorieën. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 is geïnstalleerd. De patch-id is MDVA-40550. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: Categories, Console, Products
role: Admin
exl-id: 5ce7e341-e165-4668-9de7-8e9ca3a70c70
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# MDVA-40550: Producten die aan de voorzijde ontbreken na redexering

Met de MDVA-40550-patch wordt het probleem opgelost waarbij opnieuw indexeren leidt tot enkele of alle ontbrekende producten in de winkelcategorieën. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 geïnstalleerd is. De patch-id is MDVA-40550. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.5 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

<u> Stappen om </u> te reproduceren:

1. Maak een product.
1. De indexen van de schakelaar aan **Update door programma**.
   * Wijs het product toe aan een categorie.
1. Schakel Xdebug in en maak Xdebug-onderbrekingspunten in `\Magento\Indexer\Model\Indexer::reindexAll` en `\Magento\Indexer\Model\IndexMutex::execute` .
1. Voer a **volledige herdex** van `catalog_category_product` met het bevel in werking:

   ```bash
   bin/magento indexer:reindex catalog_category_product
   ```

   * Wacht tot de uitvoering wordt gestopt op het onderbrekingspunt `\Magento\Indexer\Model\Indexer::reindexAll`.

1. In een andere console, stel a **gedeeltelijke herdex** parallel met het bevel in werking:

   ```bash
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Wacht tot de uitvoering wordt gestopt op het onderbrekingspunt `\Magento\Indexer\Model\IndexMutex::execute`. De `catalog_category_product` indexer wordt vergrendeld.
1. Hervat de uitvoering van de volledige redex van `catalog_category_product` en wacht op een vergrendelingstijd (60 seconden).

<u> Verwachte resultaten </u>:

Geen foutberichten in console.

<u> Ware resultaten </u>:

De volgende fout treedt op:

*Kon geen slot voor index verwerven: catalog_category_product.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
