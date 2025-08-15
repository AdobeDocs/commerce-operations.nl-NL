---
title: 'ACSD-63067: Problemen met de validering van de hoeveelheid in gegroepeerde producten op de opslagplaats oplossen'
description: Pas de ACSD-63067-patch toe om het Adobe Commerce-probleem op te lossen, waarbij alle producthoeveelheden in gegroepeerde producten ten onrechte als ongeldig worden gemarkeerd wanneer slechts één product een onjuiste hoeveelheid heeft.
feature: Storefront
role: Admin, Developer
exl-id: a497f2c4-8bf0-41da-955a-a58e79f09c08
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# ACSD-63067: Problemen met de validering van de hoeveelheid in gegroepeerde producten op de opslagplaats oplossen

De ACSD-63067-patch verhelpt het probleem dat alle producthoeveelheden in gegroepeerde producten onjuist als ongeldig worden gemarkeerd wanneer slechts één product een onjuiste hoeveelheid heeft. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 wordt geïnstalleerd. De patch-id is ACSD-63067. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bij gegroepeerde producten leidt een ongeldige hoeveelheid in een van de subproducten ertoe dat alle hoeveelheden ten onrechte als ongeldig worden gemarkeerd. Daarnaast wordt een validatiebericht weergegeven voor alle producten in plaats van alleen voor de producten met de ongeldige hoeveelheid.

<u> Stappen om </u> te reproduceren:

1. Maak een nieuw gegroepeerd product met ten minste twee eenvoudige producten als opties.
1. Open het product op de winkel.
1. Voer een ongeldige hoeveelheid (bijvoorbeeld: -1) in voor een van de opties en een geldige hoeveelheid (bijvoorbeeld: 1) voor de overige opties.
1. Klik op **[!UICONTROL Add to Cart]** .

<u> Verwachte resultaten </u>:

Alleen het product met het ongeldige aantal wordt gemarkeerd als ongeldig.

<u> Ware resultaten </u>:

Alle producthoeveelheden worden als ongeldig gemarkeerd en het bericht *Geef de hoeveelheid product(en) op. wordt getoond voor alle producten*.


## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
