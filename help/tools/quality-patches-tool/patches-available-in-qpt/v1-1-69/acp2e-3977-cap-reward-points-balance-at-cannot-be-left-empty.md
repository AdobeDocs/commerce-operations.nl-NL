---
title: 'ACP2E-3977: [!UICONTROL Cap Reward Points Balance At] -veld mag niet leeg worden gelaten'
description: Pas de ACS2E-3977-patch toe om het Adobe Commerce-probleem op te lossen waarbij het veld **[!UICONTROL Cap Reward Points Balance At]*** niet leeg kon worden gelaten wanneer het veld **[!UICONTROL Rewards Points Balance Redemption Threshold]*** was ingesteld, wat een validatiefout veroorzaakte.
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
source-git-commit: 83ce590c5078d70f0414276e2f03a71bdcdad321
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# ACP2E-3977: **[!UICONTROL Cap Reward Points Balance At]** -veld mag niet leeg worden gelaten

De ACP2E-3977-patch verhelpt het probleem dat **[!UICONTROL Cap Reward Points Balance At]** -veld niet leeg mag worden gelaten, zelfs als dit wel moet worden toegestaan. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 wordt geïnstalleerd. De patch-id is ACP2E-3977. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p10

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Als u **[!UICONTROL Cap Reward Points Balance At]** leeg laat, treedt er een validatiefout op, ook al moet u de initiaal uitschakelen als u deze leeg laat.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]** .
1. Plaats **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*.
1. Laat **[!UICONTROL Cap Reward Points Balance At]** leeg.
1. Opslaan.

<u> Verwachte resultaten </u>:

Een lege waarde voor **[!UICONTROL Cap Reward Points Balance At]** is toegestaan en schakelt de beperking uit.

<u> Ware resultaten </u>:

*het Saldo van Punten van de Terugkeer van het Uiteinde is ongeldig. De balans moet een positief getal zijn of leeg blijven. Verifieer en probeer het opnieuw.* -fout wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
