---
title: 'ACSD-62670: [!UICONTROL Ordered Products Report] export to CSV and XML genereert een fout'
description: Pas de ACSD-62670-patch toe om het Adobe Commerce-probleem te verhelpen waarbij het exporteren van de [!UICONTROL Ordered Products Report] naar CSV en XML een fout veroorzaakt.
feature: Reporting, Admin Workspace, Data Import/Export
role: Admin, Developer
exl-id: 99d77ddd-4fb3-4eda-8771-62c0e25f49d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# ACSD-62670: *[!UICONTROL Ordered Products Report]* export to CSV and XML genereert een fout

De ACSD-62670-patch verhelpt het probleem dat bij het exporteren van de *[!UICONTROL Ordered Products Report]* naar CSV en XML een fout optreedt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=nl-NL) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-62670. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u *[!UICONTROL Ordered Products Report]* exporteert naar CSV en XML, treedt er een fout op.

<u> Stappen om </u> te reproduceren:

1. Ga naar het *Admin* paneel, en navigeer aan **[!UICONTROL Reports]** > **[!UICONTROL Products]** > **[!UICONTROL Ordered]**.
1. Probeer CSV- of Excel-bestanden te exporteren.

<u> Verwachte resultaten </u>:

Rapporten worden zonder fouten geëxporteerd.

<u> Ware resultaten </u>:

Het exporteren van de *[!UICONTROL Ordered Products Report]* resulteert in fout 404.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
