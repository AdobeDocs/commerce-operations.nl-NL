---
title: 'ACSD-47910: ontbrekende orders, facturen, overbrengingen, creditnota''s in de respectieve entiteitsnetwerken'
description: Pas de ACSD-47910-patch toe om het Adobe Commerce-probleem op te lossen wanneer er in de respectievelijke entiteitsnetwerken orders, facturen, verzendingen en creditnota's ontbreken.
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
exl-id: 09115cf3-62c3-425e-bc99-e8971398dd20
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-47910: ontbrekende orders, facturen, overbrengingen en creditnota&#39;s in de respectieve entiteitsnetwerken

De ACSD-47910-patch verhelpt het probleem waarbij orders, facturen, verzendingen en creditnota&#39;s ontbreken in de respectieve entiteitsnetwerken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.25 wordt geïnstalleerd. De patch-id is ACSD-47910. De versie waarin dit probleem wordt opgelost, is nog niet beschikbaar.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4-p1

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Ontbrekende orders, facturen, overbrengingen en creditnota&#39;s in de respectieve entiteitsnetwerken.

<u> Stappen om </u> te reproduceren:

1. Schakel **[!UICONTROL Asynchronous indexing]** in **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** .
1. Plaats twee bestellingen.
1. Voer het uitsnijden uit om deze bestellingen te synchroniseren met het raster.
1. Open een van de bestellingen en maak deze gereed om te worden gefactureerd. MAAK DE FACTUUR NOG NIET IN.
1. Maak een nieuwe orde klaar om op de voorzijde te worden geplaatst. KLIK NOG NIET OP DE KNOP VOLGORDE PLAATSEN.
1. Voeg een `sleep(30)` toe in de lus `foreach` at `NotSyncedDataProvider::L43` .
1. Voer `bin/magento cron:run` uit.
1. Plaats nu de nieuwe bestelling.
1. Factuur de vorige bestelling.
1. Voer het uitsnijden opnieuw uit, waarbij u verwacht dat de nieuwe volgorde wordt gesynchroniseerd.
1. Ga naar het orderraster in Beheer.

<u> Verwachte resultaten </u>:

De nieuwe orde zou op het ordennet moeten verschijnen.

<u> Ware resultaten </u>:

De vorige orderupdate is gesynchroniseerd met het raster (**[!UICONTROL status: Processing]**). De nieuwe volgorde wordt nooit op het raster weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
