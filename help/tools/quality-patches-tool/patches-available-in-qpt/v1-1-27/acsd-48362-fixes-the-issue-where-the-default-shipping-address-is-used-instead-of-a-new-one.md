---
title: 'ACSD-48362: het standaardverzendadres wordt gebruikt in plaats van een nieuw adres.'
description: Pas de ACSD-48362-patch toe om het Adobe Commerce-probleem op te lossen waarbij het standaardverzendadres wordt gebruikt in plaats van een nieuw adres wanneer u een order plaatst met behulp van een verhandelbaar aanhalingsteken.
feature: Admin Workspace, B2B, Orders, Shipping/Delivery
role: Admin
exl-id: 6f0717a6-1e29-4059-9640-5b92586c36e4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# ACSD-48362: het standaardverzendadres wordt gebruikt in plaats van een nieuw adres

De ACSD-48362-patch verhelpt het probleem waarbij het standaardverzendadres wordt gebruikt in plaats van het zojuist toegevoegde adres wanneer een bestelling wordt geplaatst met behulp van een verhandelbaar aanhalingsteken. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 wordt geïnstalleerd. De patch-id is ACSD-48362. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het standaardverzendadres wordt gebruikt in plaats van het zojuist toegevoegde verzendadres wanneer u een bestelling plaatst met behulp van een verhandelbaar aanhalingsteken.

<u> Stappen om </u> te reproduceren:

1. U schakelt B2B-aanhalingsteken in door te navigeren naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B features]** > **[!UICONTROL Enable company]** > **[!UICONTROL Enable B2B quote]** .
1. Meld u aan als gebruiker van het bedrijf.
1. Voeg een product toe aan de kar.
1. Ga naar de winkelwagentje pagina en vraag een prijsopgave.
1. Ga naar de **[!UICONTROL My Quotes]** -pagina van de klant en selecteer de prijsopgave die zojuist is gemaakt.
1. Ga naar de sectie **[!UICONTROL Shipping Information]** van de aanhalingspagina van de klant.
   * Klik op **[!UICONTROL Add New Address]** , vul het formulier in en sla het adres op (selecteer **[!UICONTROL Use as my default billing address]** of **[!UICONTROL Use as my default shipping address]** niet).
1. Klik op **[!UICONTROL Send for Review]** op de aanhalingspagina van de klant.
1. Ga naar Adobe Commerce Admin als admin-gebruiker, open het citaat dat zojuist is gemaakt en klik op **[!UICONTROL Send]** .
1. Ga nu naar de aanhalingspagina van de klant, vernieuw de pagina, en klik **[!UICONTROL Proceed to Checkout]**.
1. Op de afhandelingspagina wordt het standaardverzendadres weergegeven, zelfs als het nieuwe verzendadres is geselecteerd.
1. Klik op **[!UICONTROL Continue]** en plaats de volgorde.

<u> Verwachte resultaten </u>:

De bestelling moet het nieuwe adres gebruiken zonder het standaardverzendadres op de afhandelingspagina opnieuw te selecteren.

<u> Ware resultaten </u>:

De bestelling wordt geplaatst met het standaardverzendadres.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe. 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
