---
title: 'AC-15223: De pagina Storefront toont caching inhoud na omschakelingsopslag'
description: Pas de AC-15223-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de pagina na het schakelen wordt opgeslagen vanuit het cachegeheugen en de winkel niet wordt geschakeld zoals verwacht.
feature: Cache
role: Admin, Developer
type: Troubleshooting
source-git-commit: ea3584e180acad1765f5b8105c45170725c71269
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---


# AC-15223: De pagina Storefront toont caching inhoud na omschakelingsopslag

Het AC-15223 flard verhelpt de kwestie waar na omschakelingsopslag, de pagina van geheim voorgeheugen wordt gediend aangezien de opslagschakelaar niet werkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is AC-15223. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Na het schakelen wordt de pagina bediend van geheim voorgeheugen (de archiefschakelaar werkt niet).

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL All Stores]** .
2. Maak een nieuwe winkelweergave.
3. Ga naar de winkel en probeer de winkelweergave te veranderen.

<u> Verwachte resultaten </u>:

De winkelweergave is veranderd.

<u> Ware resultaten </u>:

De naam van de winkelweergave wordt pas gewijzigd in de koptekst nadat de cache vanaf de achtergrond is schoongemaakt.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
