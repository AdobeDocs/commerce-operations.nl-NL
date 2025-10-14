---
title: 'ACSD-62475: Oplossingen voor problemen met het samenvoegen van cadeaukaarten in de kar'
description: Pas de ACSD-62475-patch toe om het Adobe Commerce-probleem op te lossen, waarbij geschenkkaartproducten met verschillende details ten onrechte worden samengevoegd tot één lijstitem in het winkelwagentje.
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: fc97c3c0-dc1b-4546-aad0-ef3b4b6a3415
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-62475: Oplossingen voor problemen met het samenvoegen van cadeaukaarten in de kar

De ACSD-62475-patch verhelpt het probleem dat cadeaukaartproducten met verschillende details ten onrechte worden samengevoegd tot één regel in het winkelwagentje. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-62475. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Cadeauproducten die met unieke verzender- of ontvangergegevens aan de kaart worden toegevoegd, worden ten onrechte samengevoegd tot één regelitem, wat leidt tot inconsistenties in de gegevens.

<u> Stappen om </u> te reproduceren:

1. Maak een [!UICONTROL Gift Card] -product met de volgende instellingen:
   * **[!UICONTROL Card Type]**: [!UICONTROL Virtual]
   * **[!UICONTROL Amount]**: 10

1. Maak in de winkel een nieuwe gebruiker en meld u aan.

1. Voeg het product Cadeaukaart toe aan het karretje met de volgende gegevens:
   * **[!UICONTROL Sender Name]**: Afzender 1
   * **[!UICONTROL Sender Email**]: sender1@test.com
   * **[!UICONTROL Recipient Name**]: Ontvanger 1
   * **[!UICONTROL Recipient Email**]: recipient1@test.com


1. Afmelden

1. Voeg hetzelfde Cadeauproduct toe aan de kar met de volgende details:
   * **[!UICONTROL Sender Name]**: Afzender 2
   * **[!UICONTROL Sender Email**]: sender2@test.com
   * **[!UICONTROL Recipient Name**]: Ontvanger 2
   * **[!UICONTROL Recipient Email**]: recipient2@test.com

1. Log terug in en controleer de wagen.

<u> Verwachte resultaten </u>:

Beide kaartjes moeten worden weergegeven als twee afzonderlijke regelitems met hun respectievelijke details.

<u> Ware resultaten </u>:

De creditcards worden samengevoegd tot één regel met een hoeveelheid van 2, waarbij de details van de eerste creditcard behouden blijven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
