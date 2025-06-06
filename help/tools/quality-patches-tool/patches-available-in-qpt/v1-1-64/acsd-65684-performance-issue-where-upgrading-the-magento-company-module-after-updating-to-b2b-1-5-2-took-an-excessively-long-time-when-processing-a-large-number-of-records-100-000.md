---
title: 'ACSD-65684: Het upgraden van Magento_Company in B2B 1.5.2 is langzaam met meer dan 100.000 verslagen in company_structure'
description: Pas de ACSD-65684-patch toe om het Adobe Commerce-probleem op te lossen waarbij het upgraden van de Magento_Company-module in B2B 1.5.2 te lang duurt vanwege het verwerken van een groot aantal records (~100.000+) in de company_structure-tabel.
feature: B2B
role: Admin, Developer
source-git-commit: dbf1bf3483aa7e52f5d1c950ab82f504c44fc989
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACSD-65684: het upgraden van `Magento_Company` in [!DNL B2B] 1.5.2 gaat langzaam met meer dan 100.000 records in `company_structure`

De ACSD-65684-patch verhelpt een prestatieprobleem waarbij het bijwerken van de `Magento_Company` -module in [!DNL B2B] 1.5.2 te lang duurt wanneer 100.000+-records in de `company_structure` -tabel worden verwerkt. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 is geïnstalleerd. De patch-id is ACSD-65684. Dit probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.9.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce B2B (alle implementatiemethoden) 1.5.2

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce B2B (alle implementatiemethoden) 1.5.2

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=nl-NL) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Prestatieprobleem waarbij het bijwerken van de `Magento_Company` -module in [!DNL B2B] 1.5.2 te lang duurt wanneer 100.000+-records in de `company_structure` -tabel worden verwerkt.

<u> Stappen om </u> te reproduceren:

1. Installeer Adobe Commerce 2.4.7-p4 met [!DNL B2B].
1. Voeg 100.000 records toe aan de tabel `company_structure` .
1. Voer een upgrade uit naar Adobe Commerce 2.4.7-p5 en de nieuwste [!DNL B2B] -module (1.5.2).
1. Pas de patch ACSD-65540 toe.
1. Uitvoeren:

```
bin/magento setup:upgrade
```

<u> Verwachte resultaten </u>:

`setup:upgrade` wordt binnen een redelijke tijd voltooid.

<u> Ware resultaten </u>:

`setup:upgrade` duurt te lang om te voltooien.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=nl-NL) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]: Een zelfbedieningshulpmiddel voor kwaliteitspatches ](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
