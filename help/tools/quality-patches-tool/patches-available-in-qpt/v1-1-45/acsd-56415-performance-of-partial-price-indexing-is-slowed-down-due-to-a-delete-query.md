---
title: 'ACSD-56415: Prestaties van [!UICONTROL Partial Price Indexing] vertraagd door "DELETE` query'
description: Pas de ACSD-56415-patch toe om het Adobe Commerce-probleem op te lossen waarbij de prestaties van [!UICONTROL Partial Price Indexing] worden vertraagd door een ` DELETE'-query wanneer de database veel gedeeltelijke prijsgegevens bevat die moeten worden geïndexeerd.
feature: Catalog Service
role: Admin, Developer
exl-id: c877844e-79d3-4756-97a5-de44e6fb5170
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-56415: De prestaties van [!UICONTROL Partial Price Indexing] worden vertraagd door `DELETE` query

De ACSD-56415-patch verhelpt het probleem waarbij de prestaties van [!UICONTROL Partial Price Indexing] worden vertraagd door een `DELETE` -query wanneer de database een hoop gedeeltelijke prijsindex heeft. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.45 wordt geïnstalleerd. De patch-id is ACSD-56023. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties van [!UICONTROL Partial Price Indexing] worden vertraagd door een `DELETE` -query wanneer de database een hoop gedeeltelijke index van prijsgegevens heeft.

<u> Stappen om </u> te reproduceren:

1. Creeer *300000 producten* en *10 websites* gebruikend het grote prestatiesprofiel.
1. Meld u aan bij het deelvenster Beheer.
1. Creeer *10 klantengroepen*.
1. Voer de onderstaande query uit om producten toe te voegen aan de tabel `_cl` :

   ``
    insert into catalog_product_price_cl (entity_id) select entity_id from catalog_product_entity
 ``

1. Voer het onderstaande bevel uit om het gedeeltelijke prijsindexeringsproces teweeg te brengen:

   ``
    bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
 ``

<u> Verwachte resultaten </u>:

De SQL query DELETE `main_table` FROM `catalog_product_index_price` wordt snel uitgevoerd.

<u> Ware resultaten </u>:

De SQL query DELETE `main_table` FROM `catalog_product_index_price` wordt zeer traag uitgevoerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Patches toepassen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de basis van de steunkennis zelf-te dienen
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
