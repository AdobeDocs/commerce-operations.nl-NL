---
title: 'ACSD-63242: langzaam importeren bij het toevoegen van meer dan 10.000 catalogusproducten'
description: Pas de ACSD-63242-patch toe om het Adobe Commerce-probleem van trage import te verhelpen wanneer catalogusproducten met meer dan 10.000 items worden toegevoegd.
feature: Data Import/Export
role: Admin, Developer
source-git-commit: 5fe00c9341414a0a2ba6b535d992d6c64e1c3b3a
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# ACSD-63242: langzaam importeren bij het toevoegen van meer dan 10.000 catalogusproducten

De ACSD-63242-patch verhelpt het probleem van langzame import wanneer catalogusproducten met meer dan 10.000 items worden toegevoegd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 wordt geïnstalleerd. De patch-id is ACSD-63242. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6-p8

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p8 en 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Het importeren van producten gaat traag als er catalogusproducten met meer dan 10.000 items worden toegevoegd.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL System]** > **[!UICONTROL Import]** > **[!UICONTROL Products]** > **[!UICONTROL Add/Update]** .
1. Bestand importeren met meer dan 10.000 items.

<u> Verwachte resultaten </u>:

Het importeren van catalogusproducten wordt op het verwachte tijdstip uitgevoerd.

<u> Ware resultaten </u>:

Het importeren van producten verloopt traag. De `var/log/exception.log` bevat:

```PHP
Exception: Warning: DOMXPath::query(): Recursion limit exceeded in /var/www/html/lib/internal/Magento/Framework/Validator/HTML/ConfigurableWYSIWYGValidator.php on line 114 in /var/www/html/lib/internal/Magento/Framework/App/ErrorHandler.php:62
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
