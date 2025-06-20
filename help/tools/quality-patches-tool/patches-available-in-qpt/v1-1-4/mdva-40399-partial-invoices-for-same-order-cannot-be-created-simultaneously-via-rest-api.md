---
title: 'MDVA-40399: Gedeeltelijke facturen voor dezelfde bestelling kunnen niet gelijktijdig worden gemaakt via de API'
description: De patch MDVA-40399 verhelpt het probleem waarbij gedeeltelijke facturen voor dezelfde volgorde niet gelijktijdig via de Rest API kunnen worden gemaakt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40399. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.
feature: REST, Invoices, Orders
role: Admin
exl-id: aa400a15-57b9-4f80-a49f-f4680b7e4705
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40399: Gedeeltelijke facturen voor dezelfde bestelling kunnen niet gelijktijdig worden gemaakt via de API

De patch MDVA-40399 verhelpt het probleem waarbij gedeeltelijke facturen voor dezelfde volgorde niet gelijktijdig via de Rest API kunnen worden gemaakt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 geïnstalleerd is. De patch-id is MDVA-40399. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.4.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onvolledige facturen voor dezelfde bestellingen kunnen niet gelijktijdig worden gemaakt met de Rest API.

<u> Eerste vereisten </u>:

Een configureerbaar product met ten minste twee variaties.

<u> Stappen om </u> te reproduceren:

1. Voeg beide varianten van het configureerbare product aan de kar toe.
1. Plaats de bestelling.
1. Maak twee facturen tegelijk voor de bestelling via de rest-API.

<u> Verwachte resultaten </u>:

* Beide facturen moeten zijn gemaakt.
* `qty_invoiced` moet voor beide facturen in de `sales_order_item` -tabel worden bijgewerkt.
* Beide producten hadden gefactureerde hoeveelheid moeten hebben.

<u> Ware resultaten </u>:

* Beide facturen zijn gemaakt.
* `qty_invoiced` wordt niet bijgewerkt op basis van een van de facturen in de `sales_order_item` -tabel.
* In de pagina van de Mening van de Orde van Admin **&#x200B;**, wordt de factuurhoeveelheid getoond slechts voor één product.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) sectie.
