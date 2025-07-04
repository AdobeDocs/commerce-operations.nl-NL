---
title: 'ACSD-61667: verbetert de voorraadprestaties voor het creëren van verzendingen'
description: Pas de ACSD-60584-patch toe om de voorraadprestaties te verbeteren voor het maken van verzendingen in het geval van veel bronnen met in-store-pickup.
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667: verbetert de voorraadprestaties voor het creëren van verzendingen

De ACSD-61667-patch verhelpt het probleem waarbij de handelaar de bestelling niet kan verzenden wanneer de [[!DNL Inventory Management for Commerce] ](https://experienceleague.adobe.com/nl/docs/commerce-admin/inventory/introduction) (voorheen MSI) bestelstore is ingeschakeld met meerdere bronnen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 wordt geïnstalleerd. De patch-id is ACSD-61667. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

U kunt de bestelling niet verzenden als Ophaalarchief MSI is ingeschakeld, met meerdere bronnen. Deze patch verbetert de voorraadprestaties om verzendingen te maken voor het geval dat veel bronnen worden opgehaald in de winkel.

<u> Eerste vereisten:</u>:

Adobe Commerce Inventory-modules worden geïnstalleerd en ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Creeer meer dan *10* bronnen en laat hun ophaalplaatsen toe.
1. De Ophaalwinkel wordt ingeschakeld onder **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** .
1. Maak een groot aantal ophaalbestellingen.
1. Ga naar **[!UICONTROL Admin login]** en selecteer **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]** .
1. Filter en controleer op in behandeling zijnde opdrachten.
1. Klik op **[!UICONTROL Ship]** .

<u> Verwachte resultaten </u>:

De verzendpagina wordt geladen zoals u had verwacht.

<u> Ware resultaten </u>:

U krijgt a *503 Maximale uitvoeringstijd uit* fout.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
