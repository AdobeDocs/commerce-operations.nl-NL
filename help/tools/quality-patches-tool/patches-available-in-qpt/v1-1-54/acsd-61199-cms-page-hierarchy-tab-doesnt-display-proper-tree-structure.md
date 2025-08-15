---
title: 'ACSD-61199: Het tabblad CMS-pagina [!UICONTROL Hierarchy] geeft geen juiste boomstructuur weer'
description: Pas ACSD-61199 flard toe om de kwestie van Adobe Commerce te bevestigen waar het lusje van de pagina van CMS * [!UICONTROL Hierarchy] * geen juiste boomstructuur toont wanneer het uitgeven van een pagina van CMS met bestaand * [!UICONTROL Hierarchy] *.
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199: het tabblad [!UICONTROL Hierarchy] van de CMS-pagina geeft geen juiste boomstructuur weer

De ACSD-61199-patch verhelpt het probleem dat op het tabblad *[!UICONTROL Hierarchy]* van de CMS-pagina geen goede boomstructuur wordt weergegeven wanneer een CMS-pagina met een bestaande *[!UICONTROL Hierarchy]* wordt bewerkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 is geïnstalleerd. De patch-id is ACSD-61199. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Op het tabblad *[!UICONTROL Hierarchy]* van de CMS-pagina wordt geen goede boomstructuur weergegeven wanneer u een CMS-pagina bewerkt met een bestaande *[!UICONTROL Hierarchy]* .

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** .
1. Maak een nieuwe **[!UICONTROL CMS page]** . Deze wordt toegevoegd aan de hoofdmap van de website in de *[!UICONTROL Hierarchy]* .
1. Sla de pagina op.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]** .
1. Voeg eventuele andere bestaande pagina&#39;s toe aan de *[!UICONTROL Hierarchy]* .
1. Sla de *[!UICONTROL Hierarchy]* op.
1. Ga naar **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** .
1. Bewerk een van de bestaande pagina&#39;s en open de *[!UICONTROL Hierarchy]* .

<u> Verwachte resultaten </u>:

De *[!UICONTROL Hierarchy]* wordt geladen zoals u had verwacht.

<u> Ware resultaten </u>:

*[!UICONTROL Hierarchy]* wordt niet geladen in het tabblad.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

[[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
