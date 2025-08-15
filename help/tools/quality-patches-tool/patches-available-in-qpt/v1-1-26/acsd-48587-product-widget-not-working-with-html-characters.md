---
title: 'ACSD-48587: productwidget werkt niet met SKU''s die HTML-tekens bevatten'
description: Pas de ACSD-48587-patch toe om het Adobe Commerce-probleem op te lossen, waarbij HTML-speciale tekens in de widgetovereenkomsten verhinderen dat overeenkomende producten worden weergegeven.
feature: Admin Workspace, CMS, Orders, Products
role: Admin
exl-id: c3e31835-03be-46b4-a080-09edf55b5b4e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-48587: productwidget werkt niet met SKU&#39;s die HTML-tekens bevatten

De ACSD-48587-patch verhelpt het probleem waarbij speciale HTML-tekens in de widgetregels voorkomen dat overeenkomende producten worden weergegeven. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-48587. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.7 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De product widget werkt niet met SKUs die *&quot;&amp;&quot;* symbolen bevatten.

<u> Stappen om </u> te reproduceren:

1. Creeer een product dat *&quot;&amp;&quot;* in SKU (b.v., s000&amp;01) bevat.
1. Bewerk de inhoud van een pagina van CMS op de *Bouwer van de Pagina*.
1. Een widget producten toevoegen.
1. De widget bewerken en instellen **[!UICONTROL Select Products by]** = **[!UICONTROL SKU]** .
1. Ga SKU in die *&quot;&amp;&quot;* op het gebied van product SKUs bevat.
1. Sla de inhoud en de CMS-pagina op.
1. Controleer de *pagina van CMS* inhoud voor de *voorproef van de Bouwer van de Pagina* en productopslag.

<u> Verwachte resultaten </u>:

Het product met *&quot;&amp;&quot;* in SKU wordt getoond in de voorproef van de Bouwer van de Pagina en op de winkel.

<u> Ware resultaten </u>:

Het product met *&quot;&amp;&quot;* in SKU wordt niet getoond in de voorproef van de Bouwer van de Pagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
