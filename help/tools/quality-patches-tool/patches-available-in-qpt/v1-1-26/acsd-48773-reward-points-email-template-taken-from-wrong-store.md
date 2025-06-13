---
title: 'ACSD-48773: e-mailsjabloon voor terugzendpunten uit verkeerde winkel'
description: Pas de ACSD-48773-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de sjabloon voor het e-mailadres wordt opgehaald uit de verkeerde winkel.
feature: Admin Workspace, Communications, Marketing Tools, Orders, Personalization, Rewards
role: Admin
exl-id: db8b6196-3e13-4c1b-8ae8-040487180817
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-48773: e-mailsjabloon voor terugzendpunten uit verkeerde winkel

De ACSD-48773-patch verhelpt het probleem waarbij de sjabloon voor bonuspunten uit de verkeerde winkel wordt gehaald. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-48773. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De productprijsherdex werkt niet als het bundelproduct niet aan een website wordt toegewezen.

<u> Stappen om </u> te reproduceren:

1. Maak twee websites, twee winkels en twee winkelweergaven.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Reviews]** en schakel **[!UICONTROL Reviews]** in.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Store Email Addresses]** .
Ga naar **[!DNL default website scope]**, en plaats het **[!UICONTROL Customer Support Sender Email]** adres, (bijvoorbeeld: *support_base@example.com*).
Schakelaar aan **[!DNL second website scope]**, en plaats het **[!UICONTROL Customer Support Sender Email]** adres aan een andere waarde (bijvoorbeeld: *support_second@example.com*).
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]** > **[!UICONTROL Share Customer Accounts]**, en reeks **[!UICONTROL Share Customer Accounts]** = *per Website*.
1. Stel onder **[!UICONTROL Reward Points]** het volgende in:
   **[!UICONTROL Enable Reward Points Functionality]** = *ja*
   **[!UICONTROL Enable Reward Points Functionality on Storefront]** = *ja*
   **[!UICONTROL Actions for Acquiring Reward Points by Customers]** > **[!UICONTROL Review Submission]** en reeks **[!UICONTROL Review Submission]** = *150*
   **[!UICONTROL Email Notification Settings]** > **[!UICONTROL Email Sender]** en reeks **[!UICONTROL Email Sender]** = *Klantenondersteuning*
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** en stel de wisselkoersen voor de tweede website in voor zowel **[!UICONTROL Points/Currency]** als **[!UICONTROL Currency/Points]** .
1. Maak een klantenaccount op de tweede website.
1. Meld u aan als klant op de tweede website.
1. Zorg ervoor dat u **[!UICONTROL Subscribe]** for **[!UICONTROL Balance Updates]** inschakelt.
1. Stuur een productoverzicht.
1. Ga naar **[!UICONTROL Marketing]** > **[!UICONTROL User Content]** > **[!UICONTROL Pending Reviews]** .
1. Wijzig de status van de nieuwe revisie in ***[!UICONTROL Approved]*** en **[!UICONTROL Save]** .
1. Wacht tot het e-mailbericht is ontvangen.

<u> Verwachte resultaten </u>:

De e-mail met beloningspunten die is bijgewerkt, had moeten zijn verzonden door de e-mailafzender die is geconfigureerd voor het tweede websitebereik.

<u> Ware resultaten </u>:

De e-mail met bonuspunten is verzonden door de e-mailafzender die is geconfigureerd voor het standaardbereik van de website.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
