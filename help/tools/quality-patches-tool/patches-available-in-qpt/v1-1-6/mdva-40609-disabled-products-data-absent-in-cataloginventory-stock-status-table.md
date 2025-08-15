---
title: 'MDVA-40609: Afgeschakelde productgegevens ontbreken in catalogusvoorraad_voorraad_status tabel'
description: De patch MDVA-40609 lost het probleem op waar de gegevens van gehandicapte producten niet in de "catalogvoorraad_stock_status"indexlijst worden getoond die tot onjuiste producthoeveelheden leidt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 is geïnstalleerd. De patch-id is MDVA-40609. De kwestie is opgelost in Adobe Commerce 2.4.3.
feature: Catalog Management, Inventory, Orders, Products
role: Admin
exl-id: e207ee55-b6ce-4065-bae1-2be89dcf5092
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-40609: Afgeschakelde productgegevens ontbreken in catalogusvoorraad_voorraad_status tabel

Met de MDVA-40609-patch wordt het probleem opgelost waarbij de gegevens over uitgeschakelde producten niet worden weergegeven in de `cataloginventory_stock_status` -indextabel, zodat onjuiste producthoeveelheden worden weergegeven. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 geïnstalleerd is. De patch-id is MDVA-40609. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Uitgeschakelde productgegevens worden niet weergegeven in de `cataloginventory_stock_status` -indextabel, waardoor onjuiste producthoeveelheden worden weergegeven.

<u> Eerste vereisten </u>:

De voorraadmodule is geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Stel twee websites in met winkels en winkelweergaven.
1. Maak een extra bron en voorraad.
1. Voeg een eenvoudig product toe:
   * Plaats laat Product toe aan *Nr*.
   * Wijs twee bronnen toe met Source Item Status = Instock en Aantal groter dan nul.
1. Sla het product op.
1. Controleer het **Aanpasbare Aantal van het Product** lusje.

<u> Verwachte resultaten </u>:

Beide bestanden hebben waarden ingevoerd die groter zijn dan nul.

<u> Ware resultaten </u>:

Eén voorraad heeft een nulwaarde.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
