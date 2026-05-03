---
title: 'ACSD-55004: Validator loopt vast tijdens het uploaden van een importbestand dat groter is dan de waarde'
description: Pas de ACSD-55004-patch toe om het Adobe Commerce-probleem te verhelpen waarbij een validator vastloopt tijdens het uploaden van een importbestand dat groter is dan de waarde die in php.ini is geconfigureerd.
feature: Data Import/Export
role: Admin, Developer
exl-id: c889f645-a3ae-4330-8ca9-45f8b6616ac8
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-55004: Validator loopt vast tijdens het uploaden van een importbestand dat groter is dan de waarde

De ACSD-55004-patch verhelpt het probleem waarbij een validator vastloopt tijdens het uploaden van een importbestand dat groter is dan de waarde die in `php.ini` is geconfigureerd. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.40 wordt geïnstalleerd. De patch-id is ACSD-55004. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De validator loopt vast tijdens het uploaden van een importbestand dat groter is dan de waarde die in `php.ini` is geconfigureerd.

<u> Stappen om </u> te reproduceren:

Probeer een importbestand te uploaden dat groter is dan geconfigureerd in `php.ini` .

<u> Verwachte resultaten </u>:

De bestandsgrootte wordt zonder fouten gevalideerd.

<u> Ware resultaten </u>:

Validator crasht.

`var/log/exception.log` bevat:

```shell
[2023-10-06T21:36:30.470618+00:00] report.CRITICAL: Error: Class "Zend_Validate_File_Upload" not found in ../module-import-export/Model/Source/Upload.php:81
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [&#x200B; Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) in de [!DNL Quality Patches Tool] gids.
