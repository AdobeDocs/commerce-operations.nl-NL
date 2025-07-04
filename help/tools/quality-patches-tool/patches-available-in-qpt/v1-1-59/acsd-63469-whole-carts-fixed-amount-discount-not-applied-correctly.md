---
title: 'ACSD-63469: Kortingen voor een vast bedrag worden niet correct toegepast met meerdere regels'
description: Pas de ACSD-63469-patch toe om het Adobe Commerce-probleem op te lossen, waarbij kortingen voor vaste bedragen voor de hele winkelwagen niet correct worden toegepast wanneer meerdere regels worden toegepast.
feature: Price Rules
role: Admin, Developer
exl-id: fb6dee57-281e-4165-8b70-7ff5949eb677
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# ACSD-63469: Kortingen voor een vast bedrag worden niet correct toegepast met meerdere regels

De ACSD-63469-patch verhelpt het probleem dat kortingen voor een vast bedrag voor de hele winkelwagen niet correct worden toegepast wanneer meerdere regels worden toegepast. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 wordt geïnstalleerd. De patch-id is ACSD-63469. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer meerdere **[!UICONTROL Fixed amount discount for whole cart]** -regels tegelijkertijd worden toegepast en de producten verlaagde of speciale prijzen hebben, wordt de kortingswaarde onjuist berekend.

<u> Stappen om </u> te reproduceren:

1. Maak twee producten tegen een prijs van 850 dollar en 85 dollar en stel de speciale prijzen in op respectievelijk 765 en 68 dollar.
1. Maak twee **[!UICONTROL Cart Price Rules]** als volgt:
   * Artikel 1
      * **[!UICONTROL Conditions]**: Voor het product $850, plaats *Aantal* aan *evenaart of groter dan 2*
      * **[!UICONTROL Actions]**: toepassen **[!UICONTROL Fixed amount discount for whole cart]** van *$153*
   * Artikel 2
      * **[!UICONTROL Conditions]**: Voor het product $85, plaats *Aantal* aan *evenaart of groter dan 2*
      * **[!UICONTROL Actions]**: toepassen **[!UICONTROL Fixed amount discount for whole cart]** van *$14*
1. Voeg beide producten aan de kar toe, elk met een hoeveelheid van 2.

<u> Verwachte resultaten </u>:

De korting die in de winkelwagen wordt toegepast, bedraagt $167.

<u> Ware resultaten </u>:

De korting die in de winkelwagen wordt toegepast, bedraagt $41.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Aanvullende stappen vereist na de installatie van de patch

(Deze sectie is optioneel; er kunnen enkele stappen vereist zijn na het aanbrengen van de patch om het probleem op te lossen.) 

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
