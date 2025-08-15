---
title: 'MDVA-44703: Het totaal van de bestellingen in het orderrapport is onjuist berekend'
description: De patch MDVA-44703 verhelpt het probleem waarbij de ordertotalen in het orderrapport onjuist worden berekend voor de beperkte beheerder. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 is geïnstalleerd. De patch-id is MDVA-44703. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.
feature: Orders
role: Admin
exl-id: bdd38ba6-f282-4026-8f65-b76543859123
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44703: Het totaal van de bestellingen in het orderrapport is onjuist berekend

De patch MDVA-44703 verhelpt het probleem waarbij de ordertotalen in het orderrapport onjuist worden berekend voor de beperkte beheerder. Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16 geïnstalleerd is. De patch-id is MDVA-44703. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De totalen van de orde in het rapport van Orden worden verkeerd berekend voor de beperkte admin gebruiker.

<u> Stappen om </u> te reproduceren:

1. Maak een extra website met twee winkels.
1. Maak een beperkte beheerder met alleen toegang tot de nieuwe website.
1. Meld u aan als gebruiker met beperkte beheerdersrechten.
1. Maak twee bestellingen met verschillende totalen, één voor elke nieuwe winkel.
1. Maak facturen voor de bestellingen.
1. Ga naar **Rapporten** > **Verkoop** en open **het rapport van Orden**.
1. Vernieuw statistieken.
1. Zie het rapport voor elke winkel.

<u> Verwachte resultaten </u>:

De verkooptotalen komen overeen met het orderbedrag van elke winkel.

<u> Ware resultaten </u>:

Het totale verkooptotaal voor de hele website wordt voor elke winkel weergegeven.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
