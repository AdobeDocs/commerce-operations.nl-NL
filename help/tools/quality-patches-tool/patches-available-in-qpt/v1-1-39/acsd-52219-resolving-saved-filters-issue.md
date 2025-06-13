---
title: 'ACSD-52219: Het probleem met het filter voor beheerrasters oplossen in het schakelen tussen bladwijzerweergaven'
description: Pas de ACSD-52219-patch toe om het Adobe Commerce-probleem op te lossen waarbij de opgeslagen filters van de beheerrasters niet werken zoals u had verwacht wanneer vaak wordt geschakeld tussen bladwijzerweergaven.
feature: Admin Workspace
role: Admin
exl-id: 3f1af6ba-88a0-480c-b16e-c00c655e346f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52219: Het probleem met het filter voor beheerrasters oplossen in het schakelen tussen bladwijzerweergaven

De ACSD-52219-patch verhelpt het probleem waarbij de opgeslagen filters van de beheerrasters niet werken zoals u had verwacht wanneer vaak wordt geschakeld tussen bladwijzerweergaven. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 wordt geïnstalleerd. De patch-id is ACSD-52219. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer vaak wordt geschakeld tussen bladwijzerweergaven, werken de opgeslagen filters in beheerrasters niet naar behoren.

<u> Stappen om </u> te reproduceren:

1. Open het [!DNL Sales Order] -raster in Beheer.
1. Maak twee tot drie filters.
1. Controleer de filterinstellingen door over te schakelen op een andere weergave om te controleren of deze op de juiste wijze zijn opgeslagen.
1. Ga naar Filter1 of Filter2.
1. Vernieuw de pagina om de weergegeven gegevens bij te werken.
1. Schakel over naar een andere weergave. De filters blijven ongewijzigd.
1. In de standaardweergave worden nu de gefilterde resultaten weergegeven, ook al is er geen specifiek filter voor ingesteld.

<u> Verwachte resultaten </u>:

De filters worden niet uitgewisseld en behouden hun oorspronkelijke staat.

<u> Ware resultaten </u>:

Wanneer u een weergave wijzigt, worden de filters gemengd en wordt de juiste weergave niet opgeslagen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
