---
title: 'ACSD-60234: [!DNL PayPal]  toont een onjuist bedrag wanneer de korting wordt toegepast'
description: Pas ACSD-60234 flard toe om de kwestie van Adobe Commerce te bevestigen waar  [!DNL PayPal]  een onjuist bedrag toont wanneer de korting door de betalingsmethode wordt toegepast.
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234: [!DNL PayPal] geeft een onjuist bedrag weer wanneer de korting wordt toegepast

De ACSD-60234-patch verhelpt het probleem waarbij [!DNL PayPal] een onjuist bedrag weergeeft wanneer de korting wordt toegepast via de betalingsmethode. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.51 wordt geïnstalleerd. De patch-id is ACSD-60234. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5-p1

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL PayPal] geeft een onjuist bedrag weer wanneer de korting wordt toegepast via de betalingsmethode.

<u> Stappen om </u> te reproduceren:

1. Configureer *[!DNL PayPal Express]* in **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]** .
   * [!UICONTROL Enable In-Context Checkout] kan [!UICONTROL Yes] of [!UICONTROL NO] zijn, het probleem wordt in beide scenario&#39;s gereproduceerd.
1. Maak een *[!UICONTROL Cart Rule]* in **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]** .
   * Voorwaarde: als aan al deze voorwaarden wordt voldaan: *[!UICONTROL Payment Method]* is *[!DNL PayPal Express Checkout]* .
   * Handelingen: Alle handelingen.
1. Maak een product.
1. Ga naar de winkel, voeg het product toe aan de winkelwagen en ga vervolgens naar de stap **[!UICONTROL Payment Method]** in de kassa.
1. Selecteer *[!DNL PayPal Express]* en controleer of de korting op de juiste wijze is toegepast.
1. Klik op **[!DNL PayPal]** .
1. Meld u aan en bekijk de inhoud van de pop-up.

<u> Verwachte resultaten </u>:

Het bedrag dat moet worden betaald aan [!DNL PayPal] bevat de korting zoals deze in de winkelwagen staat.

<u> Ware resultaten </u>:

Het totale te betalen bedrag omvat niet de korting.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
