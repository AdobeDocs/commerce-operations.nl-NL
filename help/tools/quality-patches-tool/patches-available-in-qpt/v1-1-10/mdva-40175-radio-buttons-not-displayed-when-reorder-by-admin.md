---
title: 'MDVA-40175: Radio buttons not displayed when reorder'
description: Met de MDVA-40175-patch wordt het probleem opgelost waarbij de keuzerondjes niet worden weergegeven wanneer gebruikers proberen de volgorde te wijzigen. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 is geïnstalleerd. De patch-id is MDVA-40175. De kwestie is opgelost in Adobe Commerce 2.4.3.
feature: Admin Workspace, Orders
role: Admin
exl-id: e84ff581-13ba-4f9f-9247-519b0b54807a
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40175: Radio buttons not displayed when reorder

Met de MDVA-40175-patch wordt het probleem opgelost waarbij de keuzerondjes niet worden weergegeven wanneer gebruikers proberen de volgorde te wijzigen. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 geïnstalleerd is. De patch-id is MDVA-40175. De kwestie is opgelost in Adobe Commerce 2.4.3.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Keuzerondjes worden niet weergegeven in het gedeelte Betalings- en verzendgegevens wanneer gebruikers de volgorde opnieuw proberen in te stellen.

<u> Eerste vereisten </u>:

1. Er wordt een Customer account aangemaakt met een verzendadres en een factuuradres.
1. Er wordt een eenvoudig product gemaakt.
1. Verschillende leveringsmethoden zijn geconfigureerd.
1. Er wordt ten minste één bestelling gemaakt.

<u> Stappen om </u> te reproduceren:

1. Ga naar het Admin paneel > **Verkoop** > **Orden**.
1. Selecteer de gemaakte volgorde.
1. Klik de **verbinding van de Mening**.
1. Klik **opnieuw rangschikken** knoop.
1. De rol neer de pagina aan de **Betaling &amp; Verzendinformatie** sectie.
1. Klik **klikken om het verschepen methode** te veranderen.

<u> Verwachte resultaten </u>:

De lijst met leveringsmethoden met keuzerondjes wordt weergegeven.

<u> Ware resultaten </u>:

De lijst met leveringsmethoden zonder keuzerondjes wordt weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
