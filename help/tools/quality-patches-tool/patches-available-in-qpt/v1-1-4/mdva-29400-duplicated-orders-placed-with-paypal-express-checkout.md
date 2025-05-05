---
title: 'MDVA-29400: dubbele bestellingen geplaatst met PayPal Express Checkout'
description: De MDVA-29400-patch lost het probleem op waarbij dubbele bestellingen worden gemaakt wanneer klanten bestellingen plaatsen met PayPal Express Checkout. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 is geïnstalleerd. De patch-id is MDVA-29400. De kwestie is opgelost in Adobe Commerce 2.4.1.
feature: Checkout, Orders, Payments
role: Admin
exl-id: 6f7291d3-d554-4e4e-a55d-89ea2b9dea33
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# MDVA-29400: dubbele bestellingen geplaatst met PayPal Express Checkout

De MDVA-29400-patch lost het probleem op waarbij dubbele bestellingen worden gemaakt wanneer klanten bestellingen plaatsen met PayPal Express Checkout. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4 geïnstalleerd is. De patch-id is MDVA-29400. De kwestie is opgelost in Adobe Commerce 2.4.1.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.3.7-p1, 2.4.0 - 2.4.0-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er worden dubbele bestellingen gemaakt wanneer gebruikers bestellingen plaatsen met PayPal Express Checkout.

<u> Eerste vereisten </u>:

Ingeschakeld en geconfigureerd PayPal Express Checkout.

<u> Stappen om </u> te reproduceren:

1. Voeg een product toe aan winkelwagentje.
1. Ga naar de betalingspagina en gebruik PayPal Express als betalingsmethode.
1. De pagina wordt omgeleid naar paypal/express/review/page.
1. Plaatsingsvolgorde. U wordt omgeleid naar de pagina met succesmeldingen.
1. Ga terug naar PayPal/express/review/Page.
1. Klik op de **knoop van de Orde van de Plaats**.

<u> Verwachte resultaten </u>:

Er wordt slechts één bestelling gemaakt.

<u> Ware resultaten </u>:

U krijgt de volgende fout: *Uitdrukkelijke het Teken van de Controle van PayPal bestaat niet*, maar de tweede orde wordt met succes geplaatst.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
