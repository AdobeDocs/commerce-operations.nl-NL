---
title: 'ACSD-66179: als u een factuur met het betalingstype [!UICONTROL Not Capture] annuleert, wordt de foutpagina 404 weergegeven'
description: Pas de ACSD-66179-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het annuleren van een factuur met het betaaltype [!UICONTROL Not Capture] tot een foutpagina van 404 heeft geleid.
feature: Orders, Payments
role: Admin, Developer
type: Troubleshooting
exl-id: a7c1827d-fe28-40e2-9ec6-a04b4a5d33ee
source-git-commit: a35beeb278ac3b72701c54ac7727fd5423e687e7
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-66179: als u een factuur met het betalingstype [!UICONTROL Not Capture] annuleert, wordt de foutpagina 404 weergegeven

De ACSD-66179-patch verhelpt het probleem dat het annuleren van een factuur die met het betaaltype *[!UICONTROL Not Capture]* is gemaakt, heeft geleid tot een foutpagina van 404. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-66179. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p11 - 2.4.4-p14, 2.4.5-p10 - 2.4.5-p13, 2.4.6-p8 - 2.4.6-p11, 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u een factuur annuleert die met het betalingstype *[!UICONTROL Not Capture]* is gemaakt, verschijnt er een foutpagina van 404.

<u> Stappen om </u> te reproduceren:

1. Een bestelling maken met een betalingsmethode zoals PayPal Express Checkout.
1. Maak een factuur. Stel **[!UICONTROL Amount]** in op *[!UICONTROL Not Capture]* en verzend de factuur.
1. Open de gemaakte factuur en selecteer **[!UICONTROL Cancel]** .

<u> Verwachte resultaten </u>:

1. De factuur is geannuleerd.
1. Een succesbericht wordt getoond: *u annuleerde de factuur.*

<u> Ware resultaten </u>:

Een 404 foutenpagina wordt getoond: *Pagina niet Gevonden.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
