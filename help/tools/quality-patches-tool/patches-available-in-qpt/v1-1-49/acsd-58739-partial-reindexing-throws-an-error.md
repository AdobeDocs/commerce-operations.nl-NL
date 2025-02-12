---
title: 'ACSD-58739: Onvolledige herindexering veroorzaakt een fout'
description: Pas de ACSD-55241-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een fout optreedt bij gedeeltelijk opnieuw indexeren.
feature: Inventory, Products
role: Admin, Developer
exl-id: b4e6b8b4-43de-4434-94fb-6269a75e1c28
source-git-commit: c643d55823ae0791ecfa0f2220116bbcbd02668a
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 0%

---

# ACSD-58739: Onvolledige herindexering veroorzaakt een fout

De ACSD-58739-patch verhelpt het probleem waarbij een fout optreedt bij het opnieuw coderen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-58739. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij gedeeltelijk opnieuw indexeren treedt een fout op.

<u> Stappen om </u> te reproduceren:

1. Voeg slave-verbindingsinstellingen toe aan de `app/etc/env.php` .
1. Genereer maximaal 10000 producten en voer de volgende opdracht uit:

   ```
   bin/magento index:reindex
   ```

1. Gegenereerde product-id&#39;s toevoegen aan de databasetabel `catalogsearch_fulltext_cl` .

   ```
   insert into catalogsearch_fulltext_cl (entity_id) select entity_id from catalog_product_entity;
   ```

1. Voer de volgende opdracht uit om de gedeeltelijke herindex te activeren:

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1 
   ```

1. Controleer het `var/log/support_report.log` -bestand.

<u> Verwachte Resultaten </u>

Geen fout.

<u> Ware Resultaten </u>:

*de lijst of de mening van de Basis niet gevonden* fout komt voor wanneer het gedeeltelijke opnieuw indexeren wordt uitgevoerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Patches toepassen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de basis van de steunkennis zelf-te dienen
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
