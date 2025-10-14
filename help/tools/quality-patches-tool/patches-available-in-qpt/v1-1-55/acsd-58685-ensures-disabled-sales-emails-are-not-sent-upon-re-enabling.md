---
title: 'ACSD-58685: e-mails met uitgeschakelde verkoop worden verzonden wanneer ze opnieuw worden ingeschakeld'
description: Pas de ACSD-58685-patch toe om het Adobe Commerce-probleem op te lossen, waarbij e-mailberichten die tijdens de communicatie via e-mail worden geïnitieerd, worden verzonden zodra de e-mailcommunicatie opnieuw is ingeschakeld.
feature: Configuration
role: Admin, Developer
exl-id: 773c0e0e-92c3-42b1-8fbf-fcb05e0e8311
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# ACSD-58685: e-mails met uitgeschakelde verkoop worden verzonden wanneer ze opnieuw worden ingeschakeld

De ACSD-58685-patch verhelpt het probleem dat e-mailberichten die tijdens het verzenden van e-mailberichten zijn gestart, worden verzonden zodra de e-mailcommunicatie opnieuw is ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-58685. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

E-mailberichten die worden verzonden terwijl communicatie via e-mail is uitgeschakeld, worden verzonden zodra de e-mailcommunicatie opnieuw is ingeschakeld.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Mail Sending Settings]** en stel **[!UICONTROL Disable Email Communications]** in op *[!UICONTROL No]* .
1. Navigeer naar **[!UICONTROL Sales]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales Emails]** > **[!UICONTROL General Settings]** en stel **[!UICONTROL Asynchronous Sending]** in op *[!UICONTROL Yes]* .
1. Wis het configuratiecache.
1. Plaats een bestelling.
1. E-mailcommunicatie inschakelen.
1. Plaats een andere volgorde.
1. Voer de uitsnede uit.

<u> Verwachte resultaten </u>:

Alleen de e-mail voor de tweede bestelling wordt verzonden.

<u> Ware resultaten </u>:

E-mails voor zowel de eerste als de tweede bestelling worden verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

[[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
