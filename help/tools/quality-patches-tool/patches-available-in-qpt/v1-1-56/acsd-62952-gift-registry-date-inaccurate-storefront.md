---
title: 'ACSD-62952: Cadeauregistratiedatum onjuist weergegeven op de opslagplaats'
description: Pas de ACSD-62952-patch toe om het Adobe Commerce-probleem op te lossen waarbij de datum van het Cadeauregister onjuist wordt weergegeven in de winkel.
feature: Gift, Storefront
role: Admin, Developer
exl-id: c11e95ab-775d-4aa7-828b-29ec52685d47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-62952: Cadeauregistratiedatum onjuist weergegeven op de opslagplaats

De ACSD-62952-patch verhelpt het probleem waarbij de datum van het Cadeauregister onjuist wordt weergegeven in de winkel. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-62952. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De gebeurtenisdatum die op de storefront voor een Gedeelde Registratie van het Cadeautje wordt getoond wordt verkeerd getoond zoals één dag vroeger dan de daadwerkelijke datum.

<u> Stappen om </u> te reproduceren:

1. Meld u als klant aan bij de frontend.
1. Klik in het dashboard van [!UICONTROL My Account] op **[!UICONTROL Gift Registry]** .
1. Als er geen bestaand register is, maakt u er een en geeft u een datum op.
1. Voeg om het even welk punt aan het karretje toe.
1. Klik op **[!UICONTROL Add all items to Gift Registry]** van de tekstpagina.
1. Deel het Cadeauregister.

<u> Verwachte resultaten </u>:

In het Cadeauregister wordt de juiste gebeurtenisdatum weergegeven.

<u> Ware resultaten </u>:

Het register van het Cadeautje dat vanaf uitnodigingsE-mail wordt geopend toont de gebeurtenisdatum zoals één dag vroeger.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce on cloud Infrastructure: Upgrades and Patches > Apply Patches in the Commerce on Cloud Infrastructure guide.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
