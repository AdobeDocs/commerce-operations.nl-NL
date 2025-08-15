---
title: 'ACSD-65100: het verwijderen van de waarden [!UICONTROL Maximum Width] en [!UICONTROL Maximum Height] in de [!UICONTROL Media Gallery Image Optimization] -configuratie veroorzaakt een fout'
description: Pas de ACSD-65100-patch toe om het Adobe Commerce-probleem op te lossen, waarbij het verwijderen van de [!UICONTROL Maximum Width] - en [!UICONTROL Maximum Height] -waarden in de [!UICONTROL Media Gallery Image Optimization] -configuratie een fout veroorzaakt tijdens het optimalisatieproces van de afbeelding.
feature: Media
role: Admin, Developer
exl-id: 86197602-19a1-41c2-b129-1f695f303ce5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACSD-65100: het verwijderen van de waarden [!UICONTROL Maximum Width] en [!UICONTROL Maximum Height] in de [!UICONTROL Media Gallery Image Optimization] -configuratie veroorzaakt een fout

De ACSD-65100-patch verhelpt het probleem dat het verwijderen van de **[!UICONTROL Maximum Width]** - en **[!UICONTROL Maximum Height]** -waarden in de **[!UICONTROL Media Gallery Image Optimization]** -configuratie een fout veroorzaakt tijdens het optimalisatieproces van de afbeelding. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACSD-65100. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.7-p3

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-P5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt een fout op tijdens het optimalisatieproces voor de afbeelding wanneer de waarden voor **[!UICONTROL Maximum Width]** en **[!UICONTROL Maximum Height]** worden verwijderd uit de **[!UICONTROL Media Gallery Image Optimization]** -configuratie.

<u> Stappen om </u> te reproduceren:

1. Ga naar **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery Image Optimization]** .
1. Verwijder de waarden voor **[!UICONTROL Maximum Width]** en **[!UICONTROL Maximum Height]** .
1. Reinig de configuratiecache.
1. Navigeer naar **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]** .
1. Open een pagina om te bewerken.
1. In het inhoudsgebied:
   1. Selecteer **[!UICONTROL Add Layout]** > **[!UICONTROL Row]** .
   1. Selecteer **[!UICONTROL Add Elements]** > **[!UICONTROL Text]** .
   1. Klik in de WYSIWYG-editor op **[!UICONTROL Add Image]** .
   1. Upload een afbeelding en selecteer **[!UICONTROL Add Selected]** .
1. Controleer het `var/log/exception.log` -bestand.

<u> Verwachte resultaten </u>:

Geen fouten.

<u> Ware resultaten </u>:

Er wordt een soortgelijke fout als de volgende geregistreerd:

```
report.ERROR: InvalidArgumentException: Invalid image dimensions. in /var/www/html/vendor/magento/framework/Image/Adapter/AbstractAdapter.php:630
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
