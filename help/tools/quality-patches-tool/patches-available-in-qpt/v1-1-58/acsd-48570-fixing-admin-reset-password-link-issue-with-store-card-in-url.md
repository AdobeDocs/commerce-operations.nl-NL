---
title: 'ACSD-48570: Probleem met koppeling voor het opnieuw instellen van het wachtwoord voor beheerders oplossen met winkelcode in URL'
description: Pas de ACSD-48570-patch toe om het Adobe Commerce-probleem op te lossen waarbij de pagina voor het opnieuw instellen van het wachtwoord niet toegankelijk was via de koppeling Wachtwoord voor opnieuw instellen van Admin toen de [!UICONTROL Add Store Code to URLs] -configuratie was ingeschakeld.
feature: Security, User Account
role: Admin, Developer
exl-id: 049a82ff-80e3-46a1-8472-ac74de0e365f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570: Probleem met koppeling voor het opnieuw instellen van het wachtwoord voor beheerders oplossen met winkelcode in URL

De ACSD-48570-patch om het Adobe Commerce-probleem op te lossen waarbij de pagina voor het opnieuw instellen van het wachtwoord niet toegankelijk was via de koppeling Wachtwoord voor opnieuw instellen van Admin toen de *[!UICONTROL Add Store Code to URLs]* -configuratie was ingeschakeld. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-48570. De kwestie is opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer de instelling **[!UICONTROL Add Store Code to URLs]** is ingeschakeld, werkt de functie Wachtwoord voor opnieuw instellen van Admin niet correct.
Nadat een beheerder een wachtwoordinstelling heeft aangevraagd en op de herstelkoppeling in de e-mail heeft geklikt, wordt de gebruiker omgeleid naar de aanmeldingspagina of krijgt hij een fout van 404 in plaats van te worden doorgestuurd naar het formulier voor het opnieuw instellen van het wachtwoord. Dit voorkomt dat beheerders hun accounts kunnen terugkrijgen zonder handmatig ingrijpen.

<u> Stappen om </u> te reproduceren:

1. Schakel de **[!UICONTROL Add Store Code to URLs]** -configuratie in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]** .
1. Meld u af via het deelvenster Beheer en klik op de koppeling **[!UICONTROL Forgot your password?]** op de aanmeldingspagina voor beheerders.
1. Voer het e-mailadres van de Admin-gebruiker in, geef het Captcha door en klik op **[!UICONTROL Retrieve Password]** .
1. Open het e-mailbericht voor het opnieuw instellen van wachtwoorden en klik op de koppeling voor het herstellen van wachtwoorden.

<u> Verwachte resultaten </u>:

Het formulier voor het opnieuw instellen van het wachtwoord moet worden weergegeven.

<u> Ware resultaten </u>:

De aanmeldingspagina of een pagina met 404 fouten wordt weergegeven in plaats van het wachtwoordformulier voor opnieuw instellen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
