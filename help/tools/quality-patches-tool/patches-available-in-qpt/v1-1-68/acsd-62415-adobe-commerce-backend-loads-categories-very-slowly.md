---
title: 'ACSD-62415: Adobe Commerce-backend laadt [!UICONTROL Categories] zeer langzaam'
description: Pas de ACSD-62415-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de prestaties van de pagina [!UICONTROL Categories] in het deelvenster [!UICONTROL Admin] zeer traag worden geladen wanneer een groot aantal ankercategorieën aanwezig zijn.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8040414630cf3c992e0d68d5693990f8f50fdbcb
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---


# ACSD-62415: Adobe Commerce-backend laadt **[!UICONTROL Categories]** zeer langzaam wanneer ankercategorieën aanwezig zijn

De ACSD-62415-patch verhelpt het probleem waarbij de prestaties van de pagina **[!UICONTROL Categories]** in het deelvenster **[!UICONTROL Admin]** zeer traag worden geladen wanneer een groot aantal ankercategorieën aanwezig is. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-62415. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De pagina **[!UICONTROL Categories]** in het deelvenster **[!UICONTROL Admin]** wordt zeer traag geladen wanneer een groot aantal ankercategorieën aanwezig is.

<u> Stappen om </u> te reproduceren:

1. 3K-ankercategorieën genereren.
1. Open **[!UICONTROL Catalog]** > **[!UICONTROL Categories]** pagina in het deelvenster **[!UICONTROL Admin]** .

<u> Verwachte resultaten </u>:

De pagina **[!UICONTROL Categories]** wordt snel geladen en de query mag niet 1K keer worden herhaald.

<u> Ware resultaten </u>:

Het laden duurt 7 tot 20 seconden en de query wordt meer dan 1K keer uitgevoerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
