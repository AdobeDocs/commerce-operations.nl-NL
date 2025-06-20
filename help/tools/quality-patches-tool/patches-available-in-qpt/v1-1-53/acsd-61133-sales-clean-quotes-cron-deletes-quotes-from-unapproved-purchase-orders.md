---
title: 'ACSD-61133: "sales_clean_quotes" cron verwijdert aanhalingstekens uit niet-goedgekeurde inkooporders'
description: Pas het ACSD-61133-patch toe om het Adobe Commerce-probleem op te lossen, waarbij met de garn 'sales_clean_quotes' aanhalingstekens uit niet-goedgekeurde inkooporders worden verwijderd.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133: met `sales_clean_quotes` cron worden aanhalingstekens van niet-goedgekeurde inkooporders verwijderd

De ACSD-61133-patch verhelpt het probleem waarbij de `sales_clean_quotes` -cron aanhalingstekens verwijdert van niet-goedgekeurde inkooporders. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.53 wordt geïnstalleerd. De patch-id is ACSD-61133. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10, en 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Met `sales_clean_quotes` cron verwijdert u aanhalingstekens uit niet-goedgekeurde inkooporders. De *[B2B Inkooporder]* kan niet in de orde van het citaat worden omgezet verbonden aan de gekochte orde aangezien de cron het schrapt.

<u> Eerste vereisten </u>:

Adobe Commerce [!UICONTROL B2B] -modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Schakel *[!UICONTROL B2B Purchase Order]* in.
1. Maak een bedrijf.
1. Maak een *[!UICONTROL Purchase Order]* .
1. Wacht tot het aanhalingsteken verloopt en door de kruin wordt geschrapt. De vervalperiode van de prijsopgave kan worden ingesteld met **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]** .
1. Zet *[!UICONTROL Purchase Order]* om in de volgorde via *[!UICONTROL My Purchase Order in Customer Dashboard]* of met [!DNL GraphQL] `placeOrderForPurchaseOrder` mutatie.

<u> Verwachte resultaten </u>:

Het aanhalingsteken dat aan de actieve *[!UICONTROL Purchase Order]* is gekoppeld, wordt niet verwijderd omdat de uitsnede dit heeft verlopen. De volgorde wordt in de winkel of via [!DNL GraphQL] geplaatst.

<u> Ware resultaten </u>:

De volgorde wordt niet geplaatst en er wordt een fout weergegeven op de opslagachtergrond of geretourneerd in het [!DNL GraphQL] -antwoord.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
