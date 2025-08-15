---
title: 'ACSD-62591: Het thema schakelt niet wanneer **[!UICONTROL User Agent Rules]* gevormd'
description: Pas ACSD-62591 flard toe om de kwestie van Adobe Commerce te bevestigen waar het thema niet behoorlijk schakelt wanneer **[!UICONTROL User Agent Rules] ** wordt gevormd.
feature: Themes
role: Admin, Developer
exl-id: 7b206b25-8918-40a6-a956-d38d5058d38f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# ACSD-62591: Thema schakelt niet naar behoren wanneer [!UICONTROL User Agent Rules] is geconfigureerd

De ACSD-62591-patch verhelpt het probleem waarbij het thema niet correct wordt geschakeld wanneer de **[!UICONTROL User Agent Rules]** wordt geconfigureerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-62591. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**
* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het thema schakelt niet correct over wanneer **[!UICONTROL User Agent Rules]** wordt gevormd.

<u> Stappen om </u> te reproduceren:

1. Open Commerce **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Design]** > **[!UICONTROL Configuration]** .
1. Bewerk het thema van de winkelweergave.
1. Stel `/iPhone|iPod|BlackBerry|Palm|Googlebot-Mobile|Mobile|mobile|mobi|Windows Mobile|Safari Mobile|Android|Opera Mini/i` in **[!UICONTROL User Agent Rules]** in en kies een ander thema.
1. Wijzigingen opslaan en caches wissen.
1. Open een Storefront-pagina op een mobiel apparaat.
1. Open dezelfde pagina vanuit een desktopbrowser.

<u> Verwachte resultaten </u>:

De desktopbrowser en de pagina&#39;s op het mobiele apparaat geven hun respectievelijke thema&#39;s weer.

<u> Ware resultaten </u>:

De desktopbrowser geeft de pagina in de cache weer met het mobiele thema.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.

