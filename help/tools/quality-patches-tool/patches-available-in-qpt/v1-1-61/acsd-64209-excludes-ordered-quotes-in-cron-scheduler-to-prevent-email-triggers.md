---
title: 'ACSD-64209: Cron planner haalt verhandelbare aanhalingstekens op zonder [!UICONTROL Ordered] -aanhalingstekens uit te sluiten'
description: Pas de ACSD-64209-patch toe om het Adobe Commerce-probleem op te lossen waarbij de cron planner alle verhandelbare aanhalingstekens ophaalt zonder de aanhalingstekens met de status [!UICONTROL Ordered] uit te sluiten, waardoor een e-mail of e-mailbericht wordt geactiveerd.
feature:  B2B, Communications
role: Admin, Developer
exl-id: 51ba0edc-ad0c-4e32-acd7-2337a62bff53
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209: Cron planner haalt verhandelbare aanhalingstekens op zonder [!UICONTROL Ordered] -aanhalingstekens uit te sluiten

De ACSD-64209-patch verhelpt het probleem waarbij de cron planner alle verhandelbare aanhalingstekens ophaalt zonder de aanhalingstekens met de status **[!UICONTROL Ordered]** uit te sluiten, waardoor een e-mail of e-mailbericht wordt geactiveerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 wordt geïnstalleerd. De patch-id is ACSD-64209. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De uitsnijdplanner haalt alle verhandelbare aanhalingstekens op zonder de aanhalingstekens met de status **[!UICONTROL Ordered]** uit te sluiten, waardoor een e-mail of e-mailbericht wordt geactiveerd.

<u> Stappen om </u> te reproduceren:


1. Voor *Admin* sidebar, ga **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** en laat Bedrijf en B2B Citaat toe.
1. Plaats **[!UICONTROL Default Expiration Period]** aan *1* in *Admin* > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]**.
1. Creeer een bedrijf, activeer het, en login als bedrijfbeheerder.
1. Voeg een product toe aan de kar.
1. Vraag om een offerte.
1. Voor *Admin* sidebar, ga **[!UICONTROL Sales]** > **[!UICONTROL Quotes]**.
1. Selecteer het gemaakte aanhalingsteken en klik op **[!UICONTROL Send]** om het aanhalingsteken terug te sturen naar de koper.
1. Meld u aan als bedrijfsbeheerder op de winkel.
1. Selecteer het aanhalingsteken en klik op **[!UICONTROL Proceed to checkout]** om de aankoop te voltooien.
1. Controleer of de status van het aanhalingsteken **[!UICONTROL Ordered]** is en of er geen handelingen meer mogelijk zijn in de winkel.
1. Trigger de `negotiable_quote_send_emails` cron-taak.


<u> Verwachte resultaten </u>:

Aangezien de prijsopgave is besteld en geen verdere acties kunnen worden ondernomen, dienen geen e-mails over de vervaldatum van de prijsopgave te worden verzonden.

<u> Ware resultaten </u>:

Een e-mail *Citaat verloopt spoedig* wordt verzonden.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
