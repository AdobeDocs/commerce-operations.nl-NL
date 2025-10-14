---
title: 'MDVA-40101: Objecten blijven miniwinkelwagentje na bestelling PayPal Express Checkout'
description: De MDVA-40101-patch verhelpt het probleem dat items niet uit de mini-kar worden verwijderd nadat een bestelling met PayPal Express Checkout is geplaatst. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 is geïnstalleerd. De patch-id is MDVA-40101. Deze kwestie is opgelost in Adobe Commerce 2.4.0.
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
exl-id: 8d3fa92e-39ed-4d8f-8dbe-9c08f787c6f1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# MDVA-40101: Objecten blijven miniwinkelwagentje na bestelling PayPal Express Checkout

De MDVA-40101-patch verhelpt het probleem dat items niet uit de mini-kar worden verwijderd nadat een bestelling met PayPal Express Checkout is geplaatst. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4 geïnstalleerd is. De patch-id is MDVA-40101. Deze kwestie is opgelost in Adobe Commerce 2.4.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.7

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De objecten blijven in de mini-kar staan, zelfs nadat een bestelling met PayPal Express Checkout is geplaatst.

<u> Stappen om </u> te reproduceren:

Plaats een bestelling met PayPal Express Checkout in de modus Incognito in een browser.

<u> Verwachte resultaten </u>:

Mini-cart moet leeg zijn nadat de bestelling met succes is voltooid.

<u> Ware resultaten </u>:

* Op de succespagina ziet u een lege miniwinkelwagen.
* Alle andere pagina&#39;s tonen een miniwinkelwagentje met aangeschafte objecten.
* Als u op de koppeling Kar klikt, wordt u omgeleid naar een lege kartpagina.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [&#x200B; flarden beschikbaar in QPT &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) sectie.
