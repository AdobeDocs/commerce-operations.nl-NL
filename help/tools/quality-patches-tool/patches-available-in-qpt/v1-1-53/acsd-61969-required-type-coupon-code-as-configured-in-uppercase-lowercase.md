---
title: 'ACSD-61969: vereist om couponcode te typen zoals geconfigureerd in hoofdletters of kleine letters'
description: Pas de ACSD-61969-patch toe om het Adobe Commerce-probleem op te lossen waarbij een gebruiker de couponcode precies moet typen zoals dit is geconfigureerd in hoofdletters of kleine letters.
feature: Price Rules
role: Admin, Developer
source-git-commit: b2660e3ca0dedbe4c9d8fa441f2e49b2e096474b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61969: vereist om couponcode te typen zoals geconfigureerd in hoofdletters of kleine letters

De ACSD-61969-patch verhelpt de kwestie waarbij een gebruiker de couponcode precies moet typen zoals deze is geconfigureerd in hoofdletters of kleine letters. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53 wordt geïnstalleerd. De patch-id is ACSD-61969. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

U moet de waardeboncode precies zo typen als in hoofdletters of kleine letters is geconfigureerd wanneer u deze vanaf de achterkant toepast. Ze zijn hoofdlettergevoelig in het aanmaken van de Admin-volgorde, maar niet hoofdlettergevoelig in de winkel.

<u> Stappen om </u> te reproduceren:

1. Creeer a *[!UICONTROL Cart Price Rule]* met een specifieke coupon *TEST*. Controleer of de couponcode in hoofdletters staat.
1. Maak een bestelling in Beheer.
1. Voeg *test* aan het *[!UICONTROL Apply Coupon Code]* gebied toe en klik de pijl dichtbij het gebied om de coupon toe te passen.
1. Bekijk het resultaat.

<u> Verwachte resultaten </u>:

De coupon is toegepast. Het couponveld is niet hoofdlettergevoelig.

<u> Ware resultaten </u>:

De coupon wordt niet toegepast. De volgende fout wordt weergegeven:

*de &quot;test&quot;couponcode is ongeldig. Verifieer de code en probeer opnieuw.*

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

[[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
