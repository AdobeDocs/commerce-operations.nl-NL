---
title: 'ACSD-51294: Prijs, hoeveelheid, belasting, verschepen, opbrengst die als koord wordt verzonden naar  [!DNL Google Analytics]  en GTM'
description: Pas ACSD-51294 flard toe om de kwestie van Adobe Commerce te bevestigen waar de prijs, de hoeveelheid, de belasting, de scheepvaart, en de opbrengst als koord aan  [!DNL Google Analytics]  en GTM worden verzonden.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 99d2a311-2543-4007-99fd-6c34a2950773
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-51294: Prijs, hoeveelheid, belasting, verzendkosten, omzet als tekenreeks verzonden aan [!DNL Google Analytics] en GTM

De ACSD-51294-patch verhelpt het probleem waarbij prijs, hoeveelheid, belasting, verzending en inkomsten als een tekenreeks worden verzonden naar [!DNL Google Analytics] en GTM. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.32 wordt geïnstalleerd. De patch-id is ACSD-51294. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Prijs, hoeveelheid, belasting, verzending en inkomsten worden als een tekenreeks verzonden naar [!DNL Google Analytics] en GTM.

<u> Stappen om </u> te reproduceren:

1. Configureer [!DNL Google Tag Manager] door naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]** te navigeren.
2. Maak een eenvoudig product.
3. Voltooi het afrekenen met dat product.
4. Controleer de `dataLayer` JavaScript-variabele op de pagina met succesmeldingen bij afrekenen.

<u> Verwachte resultaten </u>

De prijs en het aantal zijn numerieke waarden.

<u> Ware resultaten </u>

Prijs- en kwantitatieve waarden zijn tekenreeksen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL>) in de [!DNL Quality Patches Tool] gids.
