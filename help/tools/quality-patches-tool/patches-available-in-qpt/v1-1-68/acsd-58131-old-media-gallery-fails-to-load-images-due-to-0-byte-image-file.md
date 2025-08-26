---
title: 'ACSD-58131: oude mediagalerie kan geen afbeeldingen laden vanwege het afbeeldingsbestand van 0 byte'
description: Pas de ACSD-58131-patch toe om het Adobe Commerce-probleem op te lossen waarbij de oude mediagalerie geen afbeeldingen rendert wanneer de map een afbeelding van 0 byte bevat.
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131: oude mediagalerie kan geen afbeeldingen laden vanwege het afbeeldingsbestand van 0 byte

De ACSD-58131-patch verhelpt het probleem waarbij de oude mediagalerie geen afbeeldingen rendert wanneer de map een afbeelding van 0 byte bevat. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 wordt geïnstalleerd. De patch-id is ACSD-58131. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.5.0.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Wanneer een afbeelding van 0 byte in de map met mediagalerieën wordt geplaatst, worden in de oude mediagalerie geen afbeeldingen weergegeven. Het bijgewerkte systeem slaat nu ongeldige 0-byte bestanden over, geeft naar behoren geldige afbeeldingen weer en geeft een waarschuwing voor elk ongeldig bestand weer.

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]** .
1. Plaats **[!UICONTROL Enable Old Media Gallery]** aan *ja*.
1. Plaats een paar afbeeldingen in de map `pub/media/wysiwyg` .
1. Maak een afbeelding van 0 byte in dezelfde map met `touch pub/media/wysiwyg/empty_image.png` .
1. Voeg een afbeelding uit de map `wysiwyg` toe via Page Builder onder alle inhoud (bijvoorbeeld een CMS-blok):
   1. Maak een nieuw blok. Ga naar **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]** en klik op **[!UICONTROL Add New Block]** .
   1. Bewerk de inhoudssectie met de Page Builder.
   1. Sleep onder **[!UICONTROL Layout]** een nieuwe **[!UICONTROL Row]** naar het werkgebied.
   1. Vouw **[!UICONTROL Media]** uit en sleep een tijdelijke aanduiding voor **[!UICONTROL Image]** naar de rij.
   1. Klik op **[!UICONTROL Select from Gallery]**.
   1. Selecteer de map `wysiwyg` als deze niet standaard is geselecteerd.

<u> Verwachte resultaten </u>:

De mediagalerie blijft functioneel, zelfs als er een afbeelding van 0 byte (of een ander bestand) bestaat.

<u> Ware resultaten </u>:

De mediagalerie kan geen afbeeldingen uit de map `wysiwyg` laden vanwege een kritieke fout bij het aanmelden `var/log/system.log` :

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
