---
title: Onzichtbaar  [!DNL reCAPTCHA]  ontbreekt tijdens controle, die de plaatsing van orde verhinderen
description: Pas ACSD-54656 flard toe om de kwestie van Adobe Commerce te bevestigen waar onzichtbaar  [!DNL reCAPTCHA]  niet behoorlijk tijdens controle werkt, die de plaatsing van een orde verhindert.
feature: Checkout, Gift
role: Admin, Developer
exl-id: 08850189-2e1b-4132-8d63-ce447b1f1211
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---

# ACSD-54656: Onzichtbaar [!DNL reCAPTCHA] werkt niet correct tijdens het uitchecken, waardoor het plaatsen van een bestelling wordt verhinderd.

De ACSD-54656-patch verhelpt het probleem dat het onzichtbare [!DNL reCAPTCHA] niet goed werkt tijdens het uitchecken, waardoor het plaatsen van een bestelling wordt verhinderd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46 wordt geïnstalleerd. De patch-id is ACSD-54656. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Onzichtbaar [!DNL reCAPTCHA] werkt niet correct tijdens het uitchecken, waardoor het plaatsen van een bestelling wordt verhinderd.

<u> Stappen om </u> te reproduceren:

1. Schakel elk type [!DNL reCAPTCHA] voor een cadeaukaart op de [!UICONTROL Checkout] -pagina in.
1. Voeg een product toe aan de winkelwagentje en ga naar de pagina **[!UICONTROL Checkout]** .
1. Vouw het formulier met de cadeau-kaart uit en vul een geldige coupon in.
1. Klik op de knop **[!UICONTROL See balance and apply]** .

<u> Verwachte Resultaten </u>:

Cadeaukaart is toegepast.

<u> Ware Resultaten </u>:

Foutbericht wordt weergegeven: *[!DNL reCAPTCHA]validatie is mislukt, probeer het opnieuw* .

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
