---
title: '''ACSD-52606: Foutbericht dat wordt weergegeven wanneer de gebruiker klikt op ''De bestelling op de hoogte stellen is klaar voor afhalen'''''
description: Pas de ACSD-52606-patch toe om het Adobe Commerce-probleem op te lossen waarbij een foutbericht wordt weergegeven wanneer de gebruiker op **[!UICONTROL Notify Order is Ready for Pickup]** klikt.
feature: Orders, User Account
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# ACSD-52606: Foutbericht dat wordt weergegeven wanneer de gebruiker klikt op &quot;De bestelling op de hoogte stellen is klaar voor ophaalbewerking&quot;

ACSD-52606 flardfixes de kwestie waar een foutenmelding *Uw orde niet klaar voor bestelwagen* wordt getoond wanneer de gebruiker **[!UICONTROL Notify Order is Ready for Pickup]** klikt. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.37 wordt geïnstalleerd. De patch-id is ACSD-52606. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Een foutenmelding *Uw orde is niet klaar voor bestelwagen* wordt getoond op het scherm wanneer de gebruiker **[!UICONTROL Notify Order is Ready for Pickup]** klikt.

<u> Eerste vereisten </u>:

De inventarismodules worden geïnstalleerd.

<u> Stappen om </u> te reproduceren:

1. Nieuwe instantie installeren.
1. Maak een nieuwe bron en voorraad.
1. Wijs de nieuwe bron toe aan de standaardwebsite.
1. Ophaallocatie inschakelen voor de nieuwe bron.
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** en schakel **[!UICONTROL In-Store Delivery]** in.
1. Creeer a *in het 1} eenvoudige product van de Voorraad {met* QTY=0 *voor alle aandelen en *[!UICONTROL Manage Stock = No]*en wijs het aan beide bronnen toe.*
1. Maak een bestelling van de voorzijde met het product dat u in de vorige stap hebt gemaakt en kies *[!UICONTROL In-Store Pickup]* als de leveringsmethode.
1. Ga in Beheer naar **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]** .
1. Klik op **[!UICONTROL Notify order is ready for pickup]**.

<u> Verwachte resultaten </u>:

U krijgt een melding zonder fouten.

<u> Ware resultaten </u>:

U krijgt het volgende foutenbericht: *Uw orde is niet klaar voor bestelwagen*.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
