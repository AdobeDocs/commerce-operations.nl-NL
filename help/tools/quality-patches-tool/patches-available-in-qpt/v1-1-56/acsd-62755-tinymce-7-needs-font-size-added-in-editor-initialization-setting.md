---
title: 'ACSD-62755: [!DNL TinyMCE]  7 behoeften doopvontgrootte en doopvont die aan de montages van de redactierinitialisatie wordt toegevoegd'
description: Pas ACSD-62755 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL TinyMCE]  7 *font size* en *font familie* vereist om specifiek binnen de montages van de redactierinitialisatie worden toegevoegd.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
source-git-commit: 4aba81ea12cc08370881d3cc108e94ba410a2198
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# ACSD-62755: [!DNL TinyMCE] 7 vereist dat de fontgrootte en het font worden toegevoegd aan de initialisatie-instellingen van de editor

Het ACSD-62755 flard lost het probleem op waar [!DNL TinyMCE] 7 *doopvontgrootte* en *doopvontfamilie* selecteurs vereist om specifiek binnen de montages van de redactierinitialisatie worden toegevoegd. Deze patch is beschikbaar als [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 is geïnstalleerd. De patch-id is ACSD-62755. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5-p10

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL TinyMCE] 7 vereist *doopvontgrootte* en *doopvontfamilie* selecteurs om specifiek binnen de montages van de redactierinitialisatie worden toegevoegd.

<u> Stappen om </u> te reproduceren:

Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]** en selecteer *[!UICONTROL Show Editor]* .

<u> Verwachte resultaten </u>:

{de grootte van 0} Doopvont *en* doopvontfamilie *selecteurs zijn zichtbaar in de redacteur van WYSIWYG.*

<u> Ware resultaten </u>:

*selecteur van de grootte van het 1} doopvont* mist van de redacteur van WYSIWYG.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
