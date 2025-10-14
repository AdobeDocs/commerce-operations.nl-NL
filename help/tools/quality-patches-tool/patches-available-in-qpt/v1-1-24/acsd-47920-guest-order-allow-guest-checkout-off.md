---
title: 'ACSD-47920: een gastgebruiker kan opdrachten plaatsen via REST API, zelfs als [!UICONTROL Allow Guest Checkout] is uitgeschakeld'
description: Pas de ACSD-47920-patch toe om het Adobe Commerce-probleem op te lossen, waarbij orders via REST API als gastgebruiker kunnen worden geplaatst, zelfs als de [!UICONTROL Allow Guest Checkout] is uitgeschakeld.
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920: een gastgebruiker kan opdrachten plaatsen via REST API, zelfs als **[!UICONTROL Allow Guest Checkout]** is uitgeschakeld

De ACSD-47920-patch verhelpt het probleem waarbij orders via REST API als gastgebruiker kunnen worden geplaatst, zelfs als de **[!UICONTROL Allow Guest Checkout]** is uitgeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 wordt geïnstalleerd. De patch-id is ACSD-47920. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Orders kunnen via de rest-API als gastgebruiker worden geplaatst, zelfs als de **[!UICONTROL Allow Guest Checkout]** is uitgeschakeld.

<u> Stappen om </u> te reproduceren:

1. Ga naar Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > en plaats **[!UICONTROL Allow Guest Checkout]** aan _Nr_.
1. Gebruik REST API om een product aan een winkelwagentje toe te voegen en een bestelling te plaatsen.

<u> Verwachte resultaten </u>:

De controle API van de gast keert een fout *[!UICONTROL Sorry, guest checkout is not available]* terug als **[!UICONTROL Allow Guest Checkout]** aan _Nr_ wordt geplaatst.

<u> Ware resultaten </u>:

De controle API van de gast staat een orde toe om worden geplaatst zelfs als **[!UICONTROL Allow Guest Checkout]** aan _Nr_ wordt geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
