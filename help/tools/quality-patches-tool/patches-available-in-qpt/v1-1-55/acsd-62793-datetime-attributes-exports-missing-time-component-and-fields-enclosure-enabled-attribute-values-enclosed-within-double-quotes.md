---
title: 'ACSD-62793: Datetime-kenmerken bij exporteren van ontbrekende tijdcomponent. Als **[!UICONTROL Fields Enclosure]** ingeschakeld is, worden ook kenmerkwaarden tussen dubbele aanhalingstekens weergegeven'
description: Pas de ACSD-62793-patch toe om het Adobe Commerce-probleem op te lossen waarbij datetime-kenmerken in geëxporteerde gegevens de tijdcomponent missen. Bovendien als **[!UICONTROL Fields Enclosure]** wordt toegelaten, zullen de attributenwaarden in de *additional_attributes* kolom binnen dubbel-citaten worden ingesloten.
feature: Attributes, Data Import/Export, Catalog Service
role: Admin, Developer
source-git-commit: 1645006f142c902ac729a99502f59b6d42266691
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---


# ACSD-62793: Datetime-kenmerken bij exporteren van ontbrekende tijdcomponent. Indien **[!UICONTROL Fields Enclosure]** ingeschakeld, worden ook kenmerkwaarden tussen dubbele aanhalingstekens weergegeven

De ACSD-62793-patch verhelpt het probleem waarbij datetime-kenmerken in geëxporteerde gegevens de tijdcomponent missen. Bovendien als **[!UICONTROL Fields Enclosure]** wordt toegelaten, zullen de attributenwaarden in de *additional_attributes* kolom binnen dubbel-citaten worden ingesloten. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 wordt geïnstalleerd. De patch-id is ACSD-62793. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Datumtijdkenmerken in geëxporteerde gegevens omvatten niet de tijdcomponent. Bovendien als **[!UICONTROL Fields Enclosure]** wordt toegelaten, zullen de attributenwaarden in de *additional_attributes* kolom binnen dubbel-citaten worden ingesloten.

<u> Stappen om </u> te reproduceren:

1. Maak een productkenmerk met **[!UICONTROL Catalog Input Type for Store Owner]** = **[!UICONTROL Date and Time]** .
1. Wijs het kenmerk toe aan de kenmerkset **[!UICONTROL Default]** .
1. Maak een eenvoudig product met een datum- en tijdwaarde voor het nieuwe kenmerk.
1. Exporteer het product naar een CSV-bestand vanuit **[!UICONTROL System]** > *Gegevensoverdracht* > **[!UICONTROL Export]** .
1. Controleer de attributenwaarde in de *extra_attributes* kolom. Het heeft alleen het datumgedeelte, maar niet de tijd.
1. Werk de kenmerkwaarde bij om de tijd te gebruiken, bijvoorbeeld &quot;08/10/22, 3:20 PM&quot;.
1. Het CSV-bestand importeren.
1. Controleer *catalog_product_entity_datetime* lijst.

<u> Verwachte resultaten </u>:

De datum en tijd worden naar behoren geëxporteerd en geïmporteerd.

<u> Ware resultaten </u>:

Alleen het datumgedeelte wordt geëxporteerd en geïmporteerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
