---
title: 'ACSD-42807: Aangepast valutateken niet weergegeven op de winkel'
description: De ACSD-42807-patch verhelpt het probleem waarbij het aangepaste valutasymbool niet op de winkel wordt weergegeven. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 is geïnstalleerd. De patch-id is ACSD-42807. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Storefront
role: Developer
exl-id: 9aa3dd73-fab8-4a5b-b177-5226a37ee3c2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-42807: Aangepast valutateken niet weergegeven op de winkel

De ACSD-42807-patch verhelpt het probleem waarbij het aangepaste valutasymbool niet op de winkel wordt weergegeven. Dit flard is beschikbaar wanneer het [&#x200B; Hulpmiddel van de Patches van de Kwaliteit (QPT) &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 geïnstalleerd is. De patch-id is ACSD-42807. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.0 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het aangepaste valutateken wordt niet weergegeven in de winkelruimte.

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Montages** > **Configuraties** > **Algemeen** > **Opstelling van de Valuta** en selecteer om het even welke douanemunt. Bijvoorbeeld, **Mexicaanse Peso**.
1. Ga naar **Opslag** > **Montages** > **Configuraties** > **Algemeen** > **Opties van de Plaats** en selecteer **Spaans (Mexico)**.
1. Ga naar **Opslag** > **Symbolen van de Valuta** en vorm het muntsymbool aan **MX$**.
1. Controleer het valutasymbool op de voorzijde.

<u> Verwachte resultaten </u>:

Het standaardvalutasymbool is &quot;MX$&quot; met de valuta ingesteld op &quot;Mexicaanse Peso&quot; en de landinstelling ingesteld op &quot;Spaans (Mexico)&quot;.

<u> Ware resultaten </u>:

Het standaardvalutasymbool geeft &quot;$&quot; aan.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [&#x200B; vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
