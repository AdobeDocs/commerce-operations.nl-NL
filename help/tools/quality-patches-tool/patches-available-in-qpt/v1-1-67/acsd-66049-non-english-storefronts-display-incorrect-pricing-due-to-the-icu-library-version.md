---
title: 'ACSD-66049: niet-Engelse winkeliers geven onjuiste prijzen weer vanwege de ICU-bibliotheekversie'
description: Pas de ACSD-66049-patch toe om het Adobe Commerce-probleem op te lossen, waarbij niet-Engelse storefronts een onjuiste prijs weergeven omdat de ICU-bibliotheekversie niet overeenkomt in oudere PHP-omgevingen (versies 63.1 tot en met 74.1).
feature: Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 39e0b972dfa41f74f3c19e61d8fc1188d5c93f7c
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 0%

---


# ACSD-66049: niet-Engelse winkeliers geven onjuiste prijzen weer vanwege de ICU-bibliotheekversie

De ACSD-66049-patch verhelpt het probleem dat niet-Engelse winkeliers een onjuiste prijs weergeven vanwege een onjuiste versie van de ICU-bibliotheek in oudere PHP-omgevingen (versies 63.1 tot 74.1). Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 wordt geïnstalleerd. De patch-id is ACSD-66049. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p3 - 2.4.5-p13, 2.4.7 - 2.4.8-p1

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Niet-Engelstalige winkeliers geven een onjuiste prijs weer wanneer oudere versies van de PHP ICU-bibliotheek (63.1 tot 74.1) worden gebruikt.

<u> Stappen om </u> te reproduceren:

1. ICU-versie controleren:
   * Verbind met de server via SSH en stel het bevel in werking: `php -a`
   * Typ achter de vraag: `echo INTL_ICU_VERSION;`
1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale]** > **[!UICONTROL Locale Options]** . **[!UICONTROL Configure Locale]** = *[UICONTOL Hebreeuws (Israël)]*.
1. Maak een product met prijs = 100.
1. Bekijk de productpagina in de winkel.

<u> Verwachte resultaten </u>:

De weergegeven prijs is niet 0.

<u> Ware resultaten </u>:

Nadat u kort de waarde 100 hebt weergegeven, wordt de prijs onmiddellijk bijgewerkt naar 0.
(Dit probleem is van toepassing op PHP ICU library versions 63.1 to 74.1.)

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
