---
title: 'ACSD-65540: SQL-fout treedt op als gevolg van ontbrekende REGEXP_LIKE-functie in bedrijf_structure-updates'
description: Pas de ACSD-65540-patch toe om het Adobe Commerce-probleem op te lossen waarbij SQL-fout optreedt als gevolg van ontbrekende REGEXP_LIKE-functie in bedrijf_structure-updates.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# ACSD-65540: SQL-fout treedt op als de functie `REGEXP_LIKE` ontbreekt in `company_structure` -updates

De ACSD-65540-patch verhelpt het probleem waarbij SQL-fout optreedt als de functie `REGEXP_LIKE` ontbreekt in `company_structure` -updates. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACSD-65540.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce B2B (alle implementatiemethoden) 1.5.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce B2B (alle implementatiemethoden) 1.5.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er treedt SQL-syntaxisfout op omdat de functie `REGEXP_LIKE` ontbreekt in `company_structure` -updates.

<u> Stappen om </u> te reproduceren:

1. [!DNL B2B] bijwerken naar versie 1.5.2.
1. Voer de volgende opdracht uit:

```
bin/magento setup:upgrade
```

<u> Verwachte resultaten </u>:

De upgrade is voltooid.

<u> Ware resultaten </u>:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
