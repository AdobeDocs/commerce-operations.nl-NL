---
title: 'ACSD-64113: Fout bij het uploaden van een afbeelding met een kleinere breedte dan de hoogte via  [!DNL Media Gallery]'
description: Pas ACSD-64113 flard toe om de kwestie van Adobe Commerce te bevestigen waar de fouten in admin wanneer het uploaden van beelden met een vrij kleine breedte in vergelijking met hun hoogte (of vice versa) via  [!DNL Media Gallery] voorkomen.
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113: Fout bij het uploaden van een afbeelding met een kleinere breedte dan de hoogte via [!DNL Media Gallery]

De ACSD-64113-patch verhelpt het probleem waarbij fouten optreden in de beheerder bij het uploaden van afbeeldingen met een relatief kleine breedte in vergelijking met de hoogte (of andersom) via de [!DNL Media Gallery] . Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 wordt geïnstalleerd. De patch-id is ACSD-64113. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treden fouten op in de beheerder wanneer afbeeldingen met een relatief kleine breedte worden geüpload ten opzichte van de hoogte (of andersom) via de [!DNL Media Gallery] .

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]** en selecteer de map **[!UICONTROL wysiwyg]** .
1. Upload de afbeelding met een relatief kleine breedte in verhouding tot de hoogte (of vice versa).

<u> Verwachte resultaten </u>:

De afbeelding wordt zonder fouten geüpload.

<u> Ware resultaten </u>:

1. Het volgende foutbericht wordt gegenereerd:

   *Een technisch probleem met de server leidde tot een fout. Probeer opnieuw om door te gaan wat u aan het doen was. Probeer het later opnieuw als het probleem zich blijft voordoen.*
1. `var/log/exception.log` bevat:

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   of

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [&#x200B; Verbeteringen en Patches > Pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
