---
title: 'ACSD-55414: Slechte prestaties wanneer MariaDB probeert de machtigys_ids te casten'
description: Pas de ACSD-55414-patch toe om het Adobe Commerce-probleem op te lossen wanneer de MariaDB 'machtigys_ids' probeert om te zetten van string naar integer, wat de herindexering belemmert.
feature: Attributes
role: Admin, Developer
exl-id: 76309cef-559e-4a55-a27b-7d807ef9f74e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-55414: Slechte prestaties wanneer MariaDB probeert de `entitys_ids` te casten

De ACSD-55414-patch verhelpt het probleem waarbij het opnieuw indexeren wordt gehinderd wanneer de MariaDB `entitys_ids` probeert om te zetten van tekenreeks in geheel getal. Deze patch is beschikbaar wanneer [!DNL Quality Patches Tool (QPT)] 1.1.41 wordt geïnstalleerd. De patch-id is ACSD-55414. De kwestie is opgelost in Adobe Commerce 2.4.6.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5-p4

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.0 - 2.4.5-p5

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

De prestaties van opnieuw indexeren worden belemmerd wanneer MariaDB probeert om `entitys_ids` van koord aan geheel te werpen.

<u> Stappen om </u> te reproduceren:

1. Update `setup/performance-toolkit/profiles/ce/small.xml` door vestiging *50000* eenvoudige producten.
1. Genereer dit profiel door opdracht uit te voeren: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`.
1. Voer opnieuw index uit: `bin/magento indexer:reindex catalog_product_attribute`.

<u> Verwachte resultaten </u>:

De herindexering duurt redelijk lang.

<u> Ware resultaten </u>:

Het duurt te lang om de redex te voltooien.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Op locatie Adobe Commerce of Magento Open Source: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
