---
title: 'ACSD-63283: [!UICONTROL Gift Registry] Oplossen van problemen met e-mail- en orderplaatsing in Adobe Commerce'
description: Pas de ACSD-63283-patch toe om het Adobe Commerce-probleem op te lossen waarbij het ordenen van items van de [!UICONTROL Gift Registry] een uitzondering veroorzaakt en ervoor zorgt dat [!UICONTROL Gift Registry Updates] alleen de juiste items bevat.
feature: Gift, Shopping Cart
role: Admin, Developer
exl-id: cff5b9e6-56ee-4df2-961a-6d90ec83c0c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-63283: [!UICONTROL Gift Registry] Oplossen van problemen met e-mail- en orderplaatsing in Adobe Commerce

De ACSD-63283-patch verhelpt het probleem waarbij het ordenen van items van de [!UICONTROL Gift Registry] een uitzondering veroorzaakt en ervoor zorgt dat [!UICONTROL Gift Registry Updates] alleen de juiste items bevat. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-63283. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

>[!NOTE]
>Dit flard vervangt en breidt [&#x200B; ACSD-56280 &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed) QPT flard uit.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De [!UICONTROL Gift Registry] -functionaliteit in Adobe Commerce wordt beïnvloed door twee belangrijke problemen:

* Wanneer een klant een order voor items plaatst vanuit [!UICONTROL Gift Registry] , mislukt het proces omdat een uitzondering wordt geactiveerd.
* Bovendien bevat het [!UICONTROL Gift Registry Updates] -e-mailbericht dat naar de registereigenaar wordt verzonden, onjuiste items uit alle cadeauregisters, in plaats van de updates te beperken tot items in het specifieke register die worden bijgewerkt.

<u> Stappen om </u> te reproduceren:

1. Maak twee producten: product A en product B.
1. Maak twee klanten: Klant A en Klant B.
1. Meld u aan als Klant A en maak een nieuwe [!UICONTROL Gift Registry] .
1. Navigeer naar de productpagina van Product A en voeg deze toe aan de [!UICONTROL Wishlist] . Open [!UICONTROL Wishlist Page] en verplaats Product A naar [!UICONTROL Gift Registry] using [!UICONTROL Add to Gift Registry] .
1. Meld u aan als Klant B, maak een nieuwe [!UICONTROL Gift Registry] en voeg daar Product B aan toe.
1. Als Klant B deelt u de [!UICONTROL Gift Registry] via e-mail: **[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]** .
1. Log uit als Klant B.
1. Klik op de koppeling die u in de e-mail hebt ontvangen. Voeg Product B aan [!UICONTROL Cart] toe en plaats een orde.

<u> Verwachte resultaten </u>:

Klant B ontvangt het e-mailbericht met bijgewerkte items alleen via het register met cadeaus.

<u> Ware resultaten </u>:

Klant B ontvangt het e-mailbericht met items van alle cadeauregisters.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
