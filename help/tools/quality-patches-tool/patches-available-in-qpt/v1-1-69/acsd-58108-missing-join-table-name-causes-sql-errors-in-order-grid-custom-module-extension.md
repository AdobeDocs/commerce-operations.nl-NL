---
title: 'ACSD-58108: SQL-fouten treden op in de extensie van de aangepaste module voor het raster omdat de naam van de samenvoegtabel ontbreekt'
description: Pas de markering ACSD-58108 toe om het Adobe Commerce-probleem te verhelpen waarbij een ontbrekende naam voor een join-tabel in de aangepaste moduleextensie van het raster SQL-fouten veroorzaakt bij het filteren van bepaalde kolommen.
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 26009fee51fb81e2517ad09319bac1190d127564
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-58108: SQL-fouten treden op in de extensie van de aangepaste module voor het raster omdat de naam van de samenvoegtabel ontbreekt

Het ACSD-58108 flard verhelpt de kwestie waar het ontbreken sluit zich bij lijstnaam in de uitbreiding van de de douanemodule van het ordennet SQL fouten veroorzaakt wanneer het filtreren van bepaalde kolommen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACSD-58108. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De ontbrekende naam van de verbindingslijst in de originele het halen lijst veroorzaakt SQL fouten in het ordennet wanneer het gebruiken van een uitbreiding van de douanemodule. Dit probleem doet zich voor omdat de functie `addFilterToMap` na het samenvoegen van de tabel **[!UICONTROL sales_order_item]** niet werkt voor bepaalde kolommen. Dit leidt tot fouten tijdens het filteren.

<u> Stappen om </u> te reproduceren:

&#x200B;01. Installeer een 2.4-ontwikkelexemplaar.
&#x200B;02. Maak een nieuwe volgorde.
&#x200B;03. Een aangepaste module met een SQL-extensie installeren.
&#x200B;04. Navigeer naar **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** .
&#x200B;05. Pas het filter **[!UICONTROL Purchase Date]** toe en wacht op het resultaat.
&#x200B;06. Pas het filter **[!UICONTROL Product SKU]** toe.

<u> Verwachte resultaten </u>:

Het filteren van orden in het ordennet werkt zonder fouten.

<u> Ware resultaten </u>:

Er treedt een fout op bij het toepassen van filters in het raster van de volgorde.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
