---
title: 'ACSD-64684: validatiefout bij het opslaan van een cadeaukaart met een waarde groter dan 999 vanwege de komma in duizend (1.000)'
description: Pas de ACSD-64684-patch toe om het Adobe Commerce-probleem op te lossen waarbij een validatiefout optreedt bij het opslaan van een cadeaukaart met een waarde groter dan 999 vanwege de komma in duizend (1.000).
feature: Catalog Management
role: Admin, Developer
source-git-commit: 58d385c0e3479f5f9d826dc6e892c8ec2ebfdbb5
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACSD-64684: validatiefout bij het opslaan van een cadeaukaart met een waarde groter dan 999 vanwege de komma in duizend (1.000)

De ACSD-64684-patch verhelpt het probleem waarbij een validatiefout optreedt bij het opslaan van een cadeaukaart met een waarde groter dan 999 als gevolg van de komma in duizend (1.000). Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 wordt geïnstalleerd. De patch-id is ACSD-64684. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een validatiefout op bij het bewerken en opslaan van een cadeaukaart met een waarde groter dan 999 vanwege de komma (het scheidingsteken voor duizendtallen) in het getal, zoals &#39;duizend&#39; (1000).

<u> Stappen om </u> te reproduceren:

1. Maak een kaartje voor cadeautjes.
   1. Voer 1.000 in als de [!UICONTROL Amount] .
   1. Klik op **[!UICONTROL Save]**.

<u> Verwachte resultaten </u>:

* De nieuwe cadeaukaart met een bedrag van 1.000 wordt opgeslagen.

<u> Ware resultaten </u>:

* Er treedt een validatiefout op wanneer het bedrag van de cadeau-kaart groter is dan 999.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
