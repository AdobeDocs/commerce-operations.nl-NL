---
title: 'ACSD-63454: De standaardwaarde voor een vervolgkeuzelijst en de kenmerken Meerdere selecties wordt niet correct opgeslagen in de database'
description: Pas de ACSD-63454-patch toe om het Adobe Commerce-probleem op te lossen waarbij de standaardwaarde voor een vervolgkeuzelijst en meerdere selectiekenmerken niet correct in de database wordt opgeslagen.
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
source-git-commit: cb73a5a346ec0e8acd59accf73605e25ef35c3ca
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-63454: de standaardwaarde voor de kenmerken [!UICONTROL Dropdown] en [!UICONTROL Multiple Select] wordt niet correct opgeslagen in de database

De ACSD-63454-patch verhelpt het probleem waarbij de standaardwaarde voor een [!UICONTROL Dropdown] - en [!UICONTROL Multiple Select] -kenmerk niet correct in de database wordt opgeslagen. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 wordt geïnstalleerd. De patch-id is ACSD-63454. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De standaardwaarde voor de kenmerken [!UICONTROL Dropdown] en [!UICONTROL Multiple Select] wordt niet correct opgeslagen in de database. In plaats van de standaardwaarde bij te werken, wordt de nieuwe waarde aan de oude waarde toegevoegd, gescheiden door een komma.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]** en meld u aan op de achtergrond.
1. Klik op **[!UICONTROL Add New Attribute]**.
1. Stel op het tabblad **[!UICONTROL Properties]** het volgende in:
   * **[!UICONTROL Default Label]**: *test*
   * **[!UICONTROL Catalog Input Type for Store Owner]**: *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**: voeg twee opties toe zonder **[!UICONTROL Is Default]** te selecteren.
1. Klik op **[!UICONTROL Save Attribute]**.
1. Controleer in de database of de kolom `default_value` leeg is.

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. Ga terug en stel een van de twee opties in als **[!UICONTROL Is Default]** .
1. Controleer de database nogmaals om te controleren of `default_value` nu de geselecteerde optie-id bevat.
1. Ga terug en verander de standaardoptie door de andere optie te selecteren.

<u> Verwachte resultaten </u>:

De nieuwe standaardwaarde moet de oude waarde in de database vervangen.

<u> Ware resultaten </u>:

In plaats van de standaardwaarde te vervangen door de nieuwe, wordt de nieuwe waarde toegevoegd aan de oude waarde, gescheiden door een komma.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
