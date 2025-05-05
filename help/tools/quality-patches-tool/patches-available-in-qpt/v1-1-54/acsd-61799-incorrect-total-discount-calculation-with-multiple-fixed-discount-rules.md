---
title: 'ACSD-61799: Onjuiste berekening van de totale korting met meerdere regels voor een vast disagio toegepast op de prijsopgave'
description: Pas de ACSD-61799-patch toe om het Adobe Commerce-probleem op te lossen, waarbij de totale korting onjuist wordt berekend wanneer meerdere regels voor winkelwagentjes met vaste kortingen op de prijsopgave worden toegepast.
feature: Price Rules
role: Admin, Developer
exl-id: a87ec1cd-f141-43b9-bde1-eca354c12d4e
source-git-commit: 737204ae7418f49fdebfffbf351304796e9f5eb0
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# ACSD-61799: Onjuiste berekening van de totale korting met meerdere regels voor een vast disagio toegepast op de prijsopgave

Met de ACSD-61799-patch wordt het probleem opgelost of opgelost waarbij de totale korting onjuist wordt berekend wanneer meerdere regels met een winkelwagentje met vaste kortingen op de offerte worden toegepast. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 is geïnstalleerd. De patch-id is ACSD-61799. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4-p6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.4-p11

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De totale korting wordt onjuist berekend wanneer meerdere regels voor winkelwagentjes met *[!UICONTROL Fixed amount discount for the whole cart]* worden toegepast op een winkelwagentje.

<u> Stappen om </u> te reproduceren:

1. Maak vier producten met een prijs van $1000.
1. Maak drie regels voor de prijs van winkelwagentjes zonder voorwaarden die een korting van 100 dollar geven voor het hele winkelwagentje.
1. Maak nog een regel voor de winkelwagenprijs die een korting van 100 dollar geeft voor de hele winkelwagen, met een voorwaarde die voorkomt dat de regel wordt toegepast.
1. Schakel de regel uit.
1. Voeg drie producten toe aan het winkelwagentje en bekijk de korting in het winkelwagentje.
1. Voeg extra producten aan de kar toe en bekijk de korting in de kar.
1. Schakel de regel voor de gehandicapte winkelwagenprijs in.
1. Werk de winkelwagenpagina bij en bekijk de korting in het winkelwagentje.

<u> Verwachte resultaten </u>:

1. Het toevoegen van extra producten aan het winkelwagentje verandert niets aan de korting.
1. Als u de regel van de winkelwagenprijs inschakelt met een voorwaarde die niet van toepassing is, verandert de hoeveelheid korting niet.

<u> Ware resultaten </u>:

1. Als u extra producten aan de winkelwagentje toevoegt, wijzigt u het bedrag van de korting.
1. Als u de regel van de winkelwagenprijs inschakelt met een voorwaarde die niet van toepassing is, verandert de hoeveelheid korting.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
