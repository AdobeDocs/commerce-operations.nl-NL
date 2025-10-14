---
title: 'ACSD-51204: Het product retourneert na het aanmaken van de kredietmemo niet meer in voorraad'
description: Pas de ACSD-51204-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het product na het maken van de creditmemo niet opnieuw in voorraad wordt genomen.
feature: Orders, Products, Returns
role: Admin
exl-id: a4dba28c-c239-4812-8b3a-ce0493f9b1aa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51204: Het product retourneert na het aanmaken van de kredietmemo niet meer in voorraad

De ACSD-51204-patch verhelpt het probleem waarbij het product na het maken van de creditmemo niet opnieuw in voorraad terugkeert. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-51204. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het uitgekozen product keert niet terug in voorraad na het aanmaken van de kredietmemo.

<u> Stappen om </u> te reproduceren:

1. Installeer **[!UICONTROL Adobe Commerce]** en laat **[!UICONTROL Inventory Management Module]** met standaard *bron* en *voorraad* slechts toe.
1. Voeg a **[!UICONTROL new product]** met een hoeveelheid *10* toe.
1. Wijs het product toe aan de **[!UICONTROL default stock]** .
1. Voeg het product in de winkel toe aan de kar en plaats een bestelling voor een totale beschikbare hoeveelheid van 10.
1. In het admin paneel, produceer een *factuur* en *lading* voor de orde.
1. Creeer a **[!UICONTROL Credit Memo]** met de *terugkeer aan voorraad* checkbox die voor alle punten wordt geselecteerd.
1. Controleer de **[!UICONTROL Salable Quantity]** van het product in Admin.

<u> Verwachte resultaten </u>:

De verkoopbare hoeveelheid van het product moet aan *10* terugkeren.

<u> Ware resultaten </u>:

De verkoopbare hoeveelheid van het product wordt verlaten als *0*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) in de [!DNL Quality Patches Tool] gids.
