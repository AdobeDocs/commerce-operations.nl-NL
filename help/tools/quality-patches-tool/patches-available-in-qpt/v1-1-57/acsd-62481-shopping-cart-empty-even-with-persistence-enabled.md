---
title: 'ACSD-62481: winkelwagentje blijft leeg, zelfs als [!UICONTROL Persistence] is ingeschakeld'
description: Pas de ACSD-62481-patch toe om het Adobe Commerce-probleem op te lossen waarbij de functie voor het hardnekkige winkelwagentje mislukt tijdens het gebruik van de aanmeldingspop tijdens het uitchecken.
feature: Shopping Cart, Checkout
role: Admin, Developer
exl-id: 79fb3161-f56e-45f3-9933-cf95703f1554
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# ACSD-62481: winkelwagentje blijft leeg, zelfs als *[!UICONTROL Persistence]* is ingeschakeld

De ACSD-62481-patch verhelpt het probleem dat de functie voor het hardnekkige winkelwagentje niet werkt bij het gebruik van de aanmeldingspop tijdens het uitchecken, omdat het selectievakje *[!UICONTROL Remember Me]* ontbreekt, waardoor producten na het afmelden uit het winkelwagentje verdwijnen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-62481. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De functie Persistent winkelwagentje werkt niet wanneer de aanmeldingspop tijdens het uitchecken wordt gebruikt omdat het selectievakje *[!UICONTROL Remember Me]* ontbreekt. Dit zorgt ervoor dat producten uit het winkelwagentje verdwijnen nadat ze zijn afgemeld.

<u> Stappen om </u> te reproduceren:

1. In admin, vorm de gastrekening en de blijvende montages van het winkelwagentje als volgt:

   * Navigeer aan **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** en plaats *[!UICONTROL Allow Guest Checkout]* aan *Nr*.

      * Klik op **[!UICONTROL Save Config]**.

   * Navigeer aan **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Persistent Shopping Cart]** > **[!UICONTROL General Options]** en plaats *[!UICONTROL Enable Persistence]* aan *ja*.
   * Verlaat alle andere montages als gebrek, maar verander *[!UICONTROL Clear Persistence on Sign Out]* in *Nr*.

      * Klik op **[!UICONTROL Save Config]**.

1. Ga naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add product]** om een eenvoudig product aan de catalogus toe te voegen.

   * Vul de vereiste minimumgegevens in en zorg ervoor dat deze in voorraad zijn.

1. Maak op de voorzijde een klantenaccount met het hoofdformulier `(../customer/account/create/)` en meld u af.
1. Voeg het product als gast toe aan het winkelwagentje.
1. Open de minicart met het pictogram rechtsboven en klik op **[!UICONTROL View and Edit Cart]** .
1. Ga door met de kassa.
1. Meld u aan bij de nieuwe klantenaccount via het pop-updialoogvenster dat wordt weergegeven en meld u af.

<u> Verwachte resultaten </u>:

Het karretje behoudt de producten van de eerder aangemelde gebruiker.

<u> Ware resultaten </u>:

* De wagen is leeg.
* Het pop-upaanmeldingsvenster geeft de optie *[!UICONTROL Remember Me]* niet weer.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce on cloud Infrastructure: Upgrades and Patches > Apply Patches in the Commerce on Cloud Infrastructure guide.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
