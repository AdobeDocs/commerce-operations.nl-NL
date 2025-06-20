---
title: 'ACSD-58735: Beperkte beheerders kunnen verlaten winkelwagentjes niet bekijken op klantenaccount voor de bijbehorende website'
description: Pas de ACSD-58735-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een beperkte beheerder de verlaten winkelwagentjes niet kan weergeven op de pagina voor klantenaccounts in Commerce Admin voor een bijbehorende website.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
exl-id: b5dcc12f-325d-4de5-bae5-ff938ec77b13
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-58735: Beperkte beheerders kunnen verlaten winkelwagentjes niet bekijken op klantenaccount voor de bijbehorende website

De ACSD-58735-patch verhelpt het probleem dat een beheerder met een beperkte rol de winkelwagentjes van verlaten klanten niet kan weergeven op het tabblad Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]** .

Dit probleem doet zich voor omdat bij de weergave van de rasterweergave voor meerdere websites, als een verlaten winkelwagentje standaard wordt geladen in het deelvenster Beheer, de bijbehorende winkel-id niet wordt weergegeven.

Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-58735. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Beperkte beheerders kunnen verlaten winkelwagentjes niet weergeven op de pagina voor klantenaccounts in het deelvenster Beheer.

<u> Stappen om </u> te reproduceren:

1. Maak een beheerdersrol met toegang tot slechts een van de websites.
1. Maak een verlaten wagen.
1. Meld u aan als beheerder met volledige rechten. Controleer **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** en controleer of het winkelwagentje wordt weergegeven.
1. Schakel **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** in als gebruiker met beperkte beheerdersrechten.

<u> Verwachte resultaten </u>:

De beperkte beheerder kan verlaten winkelwagentjes voor de bijbehorende website zien.

<u> Ware resultaten </u>:

De beperkte beheerder ziet geen verlaten winkelwagentjes voor de bijbehorende website.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
