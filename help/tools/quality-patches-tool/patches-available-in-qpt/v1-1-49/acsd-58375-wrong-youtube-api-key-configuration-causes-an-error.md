---
title: 'ACSD-58375: onjuist geconfigureerde YouTube API-sleutel veroorzaakt een fout bij het toevoegen van video op archiefweergaveniveau'
description: Pas de ACSD-58375-patch toe om het Adobe Commerce-probleem op te lossen waarbij een onjuiste configuratie van de YouTube API-sleutel een fout veroorzaakt bij het toevoegen van een YouTube-video op het niveau van de winkelweergave.
feature: Catalog Management, Configuration
role: Admin, Developer
exl-id: 24187308-d9dc-4ce2-9cfa-70ccb7726a5b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-58735: onjuist geconfigureerde YouTube API-sleutel veroorzaakt een fout bij het toevoegen van video op archiefweergaveniveau

De ACSD-58735-patch verhelpt het probleem waarbij een onjuiste YouTube API-sleutelconfiguratie een fout veroorzaakt bij het toevoegen van een YouTube-video op het niveau van de winkelweergave. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 wordt geïnstalleerd. De patch-id is ACSD-58735. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6-p7

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onjuiste YouTube API-sleutelconfiguratie veroorzaakt een fout bij het toevoegen van een YouTube-video op het niveau van de winkelweergave.

<u> Stappen om </u> te reproduceren:

1. Ga naar Beheer > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Video]** .
1. Verander het *Reikwijdte* aan *[!UICONTROL Main Website]* niveau.
1. Voeg de YouTube API-sleutel toe.
1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** .
1. Selecteer een product en blader naar *[!UICONTROL Images and Video]* . Klik op **[!UICONTROL Add Video]**.
1. Kopieer een YouTube-videokoppeling en plak deze in het veld voor de videokoppeling. Uit het veld verplaatsen.

<u> Verwachte resultaten </u>:

De YouTube API-sleutel heeft een algemeen bereik en is verborgen op websiteniveau.

<u> Ware resultaten </u>:

De volgende fout wordt geworpen: *Video wordt niet getoond om de volgende reden: API sleutel ongeldig. Gelieve te gaan een geldige API sleutel* over.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
