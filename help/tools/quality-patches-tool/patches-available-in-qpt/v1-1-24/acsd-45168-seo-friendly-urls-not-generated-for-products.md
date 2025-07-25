---
title: 'ACSD-45168: SEO-vriendelijke URL''s die niet zijn gegenereerd voor producten met overschreven URL_key-kenmerken'
description: Pas de ACSD-45168-patch toe om het Adobe Commerce-probleem op te lossen waarbij geen SEO-vriendelijke URL's worden gegenereerd voor producten met URL_key-kenmerken die zijn overschreven op archiefweergaveniveau.
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
exl-id: 7d908307-f60c-4758-ad0f-f108ebb94558
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-45168: SEO-vriendelijke URL&#39;s die niet zijn gegenereerd voor producten met overschreven URL_key-kenmerken

De ACSD-45168-patch verhelpt het probleem dat er geen SEO-vriendelijke URL&#39;s worden gegenereerd voor producten met URL_key-kenmerken die zijn overschreven op het niveau van de winkelweergave. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 wordt geïnstalleerd. De patch-id is ACSD-45168. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

SEO-vriendelijke URL&#39;s worden niet gegenereerd voor producten met URL_key-kenmerken die zijn overschreven op het niveau van de winkelweergave.

<u> Stappen om </u> te reproduceren:

1. Stel de configuratie als volgt in door naar **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]** te gaan:
   * [!UICONTROL Use Categories Path for Product URLs] = *ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *ja*
1. Reinig de configuratiecache.
1. Maak twee categorieën: [!UICONTROL Category 1] en [!UICONTROL Category 2] .
1. Maak twee producten: [!UICONTROL Product 1] in [!UICONTROL Category 1] , [!UICONTROL Product 2] in [!UICONTROL Category 1] .
1. Wijzig het bereik in [!UICONTROL Default Store View] for [!UICONTROL Product 1] .
1. Schakel de optionele URL [!UICONTROL Key] uit in [!UICONTROL Search Engine Optimization] .
1. Sla het product op.
1. Ga terug naar [!UICONTROL All Store Views] .
1. Voeg [!UICONTROL Product 1] toe aan [!UICONTROL Category 2] en voeg [!UICONTROL Product 2] toe aan [!UICONTROL Category 2] .
1. Controleer de `url_rewrite` tabel of [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites] .

<u> Verwachte resultaten </u>:

De SEO-vriendelijke URL voor [!UICONTROL Category 2] wordt gemaakt voor [!UICONTROL Product 1] .

<u> Ware resultaten </u>:

De SEO-vriendelijke URL voor [!UICONTROL Category 2] ontbreekt voor [!UICONTROL Product 1] omdat het URL-sleutelkenmerk is overschreven voor het weergavebereik van de winkel.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool]
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Patches toepassen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk

## Gerelateerde lezing

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de basis van de steunkennis zelf-te dienen
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids
* [ Beste praktijken voor het wijzigen van gegevensbestandlijsten ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) in het Playbook van de Implementatie van Commerce

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
