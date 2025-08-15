---
title: 'ACSD-62577: optimalisatie van de zoekprestaties van Storefront'
description: Pas ACSD-62577 flard toe om de kwestie van Adobe Commerce te bevestigen waar de prestaties van het storefrontonderzoek wegens langzame vraaguitvoering door een grote "search_query"lijst worden veroorzaakt.
feature: Search
role: Admin, Developer
exl-id: 211c1e3c-0739-4ff6-a25c-b27d335920d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577: optimalisatie van de zoekprestaties van Storefront

De markering ACSD-62577 verhelpt de kwestie met langzame prestaties van storefront onderzoeksvragen door zowel vraag als lijstindexen te optimaliseren. Deze patch is beschikbaar bij [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. De patch-id is ACSD-62577. De kwestie zou volgens de planning in Adobe Commerce 2.4.8 worden opgelost.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6, 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Grote `search_query` -tabellen vertragen de zoekacties in de winkeliers aanzienlijk, waardoor de responstijden aan de voorzijde toenemen als gevolg van inefficiënte query&#39;s en het ontbreken van geoptimaliseerde tabelindexen.

<u> Stappen om </u> te reproduceren:

1. Stel Adobe Commerce Developer in met de prestatietoolset `small.xml` .
1. Open de SQL-opdrachtregel en verwijder de tabel `search_query` met de volgende opdrachten:

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. Vul de tabel `search_query` met een groot aantal records, bijvoorbeeld 4 miljoen records.
1. Trigger opnieuw indexeren en spoelcache.

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. Logboeken voor foutopsporing in database inschakelen:

   ```
   bin/magento dev:query-log:enable  
   ```

1. Een term zoeken in de zoekbalk van de winkel, bijvoorbeeld
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. Controleer `db.log` voor de tijd van de vraaguitvoering voor volgende SQL:

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u> Verwachte resultaten </u>:

De uitvoeringstijd van de query is geoptimaliseerd, wat resulteert in een minder significante toename van de responstijd bij het verwerken van grote `search_query` -tabellen.

<u> Ware resultaten </u>:

De uitvoeringstijd van de query neemt aanzienlijk toe als gevolg van een inefficiënte afhandeling van de grote `search_query` -tabel:

```
TIME: 10.8520 seconds  
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
