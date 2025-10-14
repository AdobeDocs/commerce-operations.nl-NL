---
title: 'ACSD-60344: dubbele bevestiging van bestelling bij gebruik van [!UICONTROL Purchase Order] met automatische goedkeuring'
description: Pas de ACSD-60344-patch toe om het Adobe Commerce-probleem op te lossen, waarbij dubbele bevestigingse-mails voor bestellingen worden verzonden bij gebruik van een [!UICONTROL Purchase Order] met automatische goedkeuring.
feature: Purchase Orders
role: Admin, Developer
exl-id: c4d415ee-b1ac-4094-9209-19b91f9a7666
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344: dubbele bevestiging van bestelling bij gebruik van *[!UICONTROL Purchase Order]* met automatische goedkeuring

De ACSD-60344-patch verhelpt het probleem waarbij dubbele bevestigingse-mails voor bestellingen worden verzonden bij het gebruik van een *[!UICONTROL Purchase Order]* met automatische goedkeuring. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-60344. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er worden dubbele bevestigingse-mails verzonden wanneer u een *[!UICONTROL Purchase Order]* met automatische goedkeuring gebruikt.

<u> Eerste vereisten </u>

Schakel B2B-modules en *[!UICONTROL Purchase Order]* in.

<u> Stappen om </u> te reproduceren:

1. Maak een bedrijfsaccount en schakel een *[!UICONTROL Purchase Order]* voor dit account in.
1. Maak een normale gebruikersaccount en voeg deze als bedrijfsgebruiker toe aan de bedrijfsaccount.
1. Plaats een bestelling met dit account.
1. Uitsnijden en e-mails controleren.

<u> Verwachte resultaten </u>:

Per bestelling wordt slechts één bevestigingsbericht ontvangen.

<u> Ware resultaten </u>:

Er zijn twee e-mails ter bevestiging van bestelling ontvangen.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
