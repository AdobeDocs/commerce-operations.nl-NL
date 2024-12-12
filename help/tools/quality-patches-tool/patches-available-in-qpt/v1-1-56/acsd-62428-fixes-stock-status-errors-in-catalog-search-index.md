---
title: 'ACSD-62428: fouten met de voorraadstatus in de zoekindex van de catalogus'
description: Pas het ACSD-62428 flard toe om de kwestie te bevestigen waar de ` is_out_of_stock ` waarde in de index van het catalogusonderzoek verkeerd wordt geplaatst wanneer SKU niet als doorzoekbaar attribuut is.
feature: Inventory, Catalog Management
role: Admin, Developer
source-git-commit: 633aa46886d65f45e8b503e3892e47bb24e40fc0
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62428: fouten met de voorraadstatus in de zoekindex van de catalogus

De ACSD-62428-patch verhelpt het probleem waarbij `is_out_of_stock` -waarden in de zoekindex van de catalogus op een onjuiste waarde worden ingesteld wanneer het SKU-kenmerk niet is ingesteld als doorzoekbaar. Deze patch is beschikbaar bij [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. De patch-id is ACSD-62428. De kwestie zou volgens de planning in Adobe Commerce 2.4.8 worden opgelost.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p5

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De `is_out_of_stock` -waarde in de zoekindex van de catalogus wordt op een onjuiste waarde ingesteld wanneer de SKU niet is geconfigureerd als een doorzoekbaar kenmerk, wat leidt tot een onjuiste voorraadweergave.

<u> Stappen om </u> te reproduceren:

1. Maak een aangepaste [!UICONTROL Source] en aangepaste [!UICONTROL Stock] .
1. Maak drie eenvoudige producten en wijs hun overzicht toe aan de aangepaste [!UICONTROL Source] . Wijs deze producten toe aan een categorie.
1. Stel de *[!UICONTROL Inventory (MSI) Indexer]* in op *[!UICONTROL Update on Save]* voor eenvoudige replicatie.
1. Stel de *[!UICONTROL Source Item Status]* in op *[!UICONTROL In Stock]* en wijs een *[!UICONTROL Quantity]* toe.
1. Sla het product op.
1. Navigeer naar **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** en open het kenmerk **[!UICONTROL SKU]** .
1. Stel *[!UICONTROL Use In]* in op *[!UICONTROL No]* .
1. Wijzig de producthoeveelheid (controleer of deze niet is ingesteld op 0).
1. Sla het product op.

<u> Verwachte resultaten </u>:

De `is_out_of_stock` -waarde geeft de voorraadstatus van het product correct weer, zelfs als de SKU geen doorzoekbaar kenmerk is.

<u> Ware resultaten </u>:

De waarde `is_out_of_stock` wordt onjuist ingesteld op 1 en het SKU-kenmerk ontbreekt in de geïndexeerde gegevens.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
