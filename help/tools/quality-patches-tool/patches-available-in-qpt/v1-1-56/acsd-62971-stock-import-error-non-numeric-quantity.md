---
title: 'ACSD-62971: bij invoer van voorraadbronnen met niet-numerieke waarden wordt de hoeveelheid vastgesteld op 0'
description: Pas de ACSD-62971-patch toe om het Adobe Commerce-probleem op te lossen. Bij het importeren van voorraadbronnen met niet-numerieke waarden in de kolom 'Hoeveelheid' wordt de hoeveelheid ingesteld op 0.
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-62971: bij invoer van voorraadbronnen met niet-numerieke waarden wordt de hoeveelheid vastgesteld op 0

Met de ACSD-62971-patch is het probleem opgelost dat bij het importeren van voorraadbronnen met niet-numerieke waarden in de kolom &#39;Hoeveelheid&#39; de hoeveelheid wordt ingesteld op 0. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-62971. De kwestie zou volgens de planning in Adobe Commerce 2.4.8 worden opgelost.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Hiermee wordt het probleem verholpen waarbij bij het importeren van voorraadbronnen met niet-numerieke waarden in de kolom **[!UICONTROL Quantity]** de hoeveelheid wordt ingesteld op 0.

<u> Stappen om </u> te reproduceren:

1. Maken **[!UICONTROL Simple Product]** met qty=100
1. Importeren via een **[!UICONTROL Stock Sources]** -bestand met een onjuist aantal (&#39;abc&#39;)

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. Controleer de hoeveelheid na het importeren.

<u> Verwachte resultaten </u>:
Validatie van importgegevens moet mislukken.

<u> Ware resultaten </u>:
De hoeveelheid eenvoudig product is 0 geworden en het product wordt bijgewerkt als [!UICONTROL Out of Stock] .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
