---
title: 'ACSD-59083: De basistabel of weergave bevat geen fouten tijdens gelijktijdige weergaveupdates'
description: Pas de ACSD-59083-patch toe om het Adobe Commerce-probleem op te lossen waarbij bepaalde databaseupdatebewerkingen mislukken met de fout 'Basistabel of -weergave niet gevonden'.
feature: System
role: Admin, Developer
exl-id: a0fa2ac9-e61f-43d5-81ff-edf178b1abc0
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-59083: *de lijst of de mening van de Basis niet gevonden* fouten tijdens gelijktijdige `mview` updates

De ACSD-59083-patch verhelpt het probleem dat bepaalde databaseupdatebewerkingen mislukken met de fout &#39;Basistabel of -weergave niet gevonden&#39; wanneer `mview` -updates tegelijkertijd worden uitgevoerd. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 wordt geïnstalleerd. De patch-id is ACSD-59083. De kwestie is opgelost in Adobe Commerce 2.4.8.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.5-p5

**Compatibel met de versies van Adobe Commerce:**

Adobe Commerce (alle implementatiemethoden) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Bepaalde bewerkingen in database-updates resulteren in &#39;Basistabel of weergave niet gevonden&#39; fouten wanneer `mview` -updates gelijktijdig worden uitgevoerd.

<u> Stappen om </u> te reproduceren:

1. Stel de indexeermodus in op **[!UICONTROL Update on Schedule]** .
1. Neem verslagen in `cl` lijsten op gebruikend de volgende SQL bevelen:

   ```sql
   INSERT INTO catalogrule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogsearch_fulltext_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_category_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_attribute_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_category_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_price_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO customer_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO design_config_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO salesrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_product_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_rule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   ```

1. Installeer het profiel `setup/performance-toolkit/profiles/ce/small.xml` .
1. Voeg een onderbrekingspunt in het dossier `magento2ee/lib/internal/Magento/Framework/ForeignKey/Config/DbReader.php` op lijn 72 toe.
1. Wis de cache.
1. Klik op **[!UICONTROL Add to Cart]** op een willekeurig product.
1. Start de uitsnijdtaak wanneer de uitvoering het onderbrekingspunt bereikt.
1. Hervat het proces na het starten van de uitsnijdtaak.

<u> Verwachte resultaten </u>:

De databasebewerkingen worden zonder fouten uitgevoerd.

<u> Ware resultaten </u>:

Er treedt een fout op tijdens de uitvoering:

```text
SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento24.design_config_dummy_cl__tmp663bb682960345_17794892' doesn't exist in /www/magento24/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik &#x200B;](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [&#x200B; Verbeteringen en Patches > pas Patches &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.


## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool] : Een zelfbedieningshulpmiddel voor kwaliteitspatches &#x200B;](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) in de gids van Hulpmiddelen.
