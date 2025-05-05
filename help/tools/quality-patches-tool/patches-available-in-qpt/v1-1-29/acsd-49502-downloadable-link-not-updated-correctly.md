---
title: '"ACSD-49502: Downloadbare verbinding niet correct bijgewerkt na  [!DNL staging]  update'''
description: Pas ACSD-49502 flard toe om de kwestie van Adobe Commerce te bevestigen waar de downloadbare verbinding niet correct wordt bijgewerkt nadat de a [!DNL staging]  update op het downloadbare product wordt toegepast.
feature: Staging
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-49502: Downloadbare koppeling wordt niet correct bijgewerkt na [!DNL staging] -update

De ACSD-49502-patch verhelpt het probleem dat de downloadbare koppeling niet correct wordt bijgewerkt nadat een [!DNL staging] -update op het downloadbare product is toegepast. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29 wordt geïnstalleerd. De patch-id is ACSD-49502. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De downloadbare koppeling wordt niet correct bijgewerkt nadat een [!DNL staging] -update is toegepast op het downloadbare product.

<u> Stappen om </u> te reproduceren:

1. Een downloadbaar product maken met een of meer koppelingen.
1. Maak een klantenaccount en meld u aan.
1. Voeg het downloadbare product vanuit de winkel toe aan de winkelwagentje.
1. Plan in **[!UICONTROL Admin]** een nieuwe update voor het downloadbare product en laat de geplande update voltooid zijn.
1. Voltooi de bestelling op de winkel.

<u> Verwachte resultaten </u>:

Downloadbare koppelingen blijven behouden wanneer geplande updates worden gebruikt terwijl eerder toegevoegde producten zich in het winkelwagentje bevinden.

<u> Ware resultaten </u>:

Downloadbare koppelingen ontbreken zowel onder de *[!UICONTROL My Account]* ([!UICONTROL My Downloadable Products]) van de klant als onder de weergavepagina&#39;s in de **[!UICONTROL Admin]**.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
