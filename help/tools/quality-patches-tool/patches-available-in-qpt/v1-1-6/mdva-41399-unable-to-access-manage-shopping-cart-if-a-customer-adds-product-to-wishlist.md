---
title: 'MDVA-41399: Kan geen toegang krijgen tot het winkelwagentje beheren als een klant een product aan de wenslijst toevoegt'
description: Met de MDVA-41399-patch wordt het probleem opgelost waarbij beheerders geen toegang hebben tot de pagina Winkelwagentje beheren als een klant een product aan de wenslijst toevoegt. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 is geïnstalleerd. De patch-id is MDVA-41399. De kwestie is opgelost in Adobe Commerce 2.4.2.
feature: Orders, Products, Shopping Cart
role: Admin
exl-id: 81a128b5-0c38-4f8f-b297-1f264952d431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41399: Kan geen toegang krijgen tot het winkelwagentje beheren als een klant een product aan de wenslijst toevoegt

Met de MDVA-41399-patch wordt het probleem opgelost waarbij beheerders geen toegang hebben tot de pagina Winkelwagentje beheren als een klant een product aan de wenslijst toevoegt. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6 geïnstalleerd is. De patch-id is MDVA-41399. De kwestie is opgelost in Adobe Commerce 2.4.2.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.3.3 - 2.4.1-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Admin-gebruikers hebben geen toegang tot de pagina Winkelwagentje beheren als een klant een product aan de verlanglijst toevoegt.

<u> Eerste vereisten </u>:

1. Maak twee of meer producten.
1. Maak een klant.
1. Schakel de modus Ontwikkelaar in.

<u> Stappen om </u> te reproduceren:

1. Ga naar Storefront en meld u aan als klant onder de voorwaarden.
1. Voeg een product toe aan de Gewenste lijst.
1. Ga naar het Admin paneel en navigeer aan de gecreeerde klant uitgeeft pagina en klik op **beheren het Vormen Kart** knoop.

<u> Verwachte resultaten </u>:

Admin-gebruiker kan het winkelwagentje beheren.

<u> Ware resultaten </u>:

Admin gebruiker krijgt een foutenmelding: *een fout is voorgekomen. Zie foutenlogboek voor details.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor info over andere flarden beschikbaar in QPT, verwijs naar de [ flarden beschikbaar in QPT ](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sectie.
