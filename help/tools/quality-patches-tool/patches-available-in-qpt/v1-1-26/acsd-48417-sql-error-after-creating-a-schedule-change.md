---
title: 'ACSD-48417: SQL-fout na het maken van een programmawijziging'
description: Pas de ACSD-48417-patch toe om het Adobe Commerce-probleem op te lossen, waarbij een SQL-fout optreedt nadat een wijziging in het programma voor een product is gemaakt en een ander product is opgeslagen.
feature: Storage
role: Admin
exl-id: c8e7c7aa-ac53-4218-8c3c-ea2240af17c9
type: Troubleshooting
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# ACSD-48417: SQL-fout na het maken van een programmawijziging

De ACSD-48417-patch verhelpt het probleem waarbij een SQL-fout optreedt na het maken van een programmawijziging voor een product en het opslaan van een ander product. Deze patch is beschikbaar wanneer [[!DNL Quality Patches Tool (QPT)] ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 wordt geïnstalleerd. De patch-id is ACSD-48417. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.7.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.1-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.5 - 2.4.6

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe [!DNL Quality Patches Tool] versies. Als u wilt controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : Zoek naar de pagina van flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

Er wordt een SQL-fout weergegeven na het maken van een programmawijziging voor een product en het opslaan van een ander product.

<u> Stappen om </u> te reproduceren:

1. Installeer Magento 2.4-develop EE + voorbeeldgegevens.
1. Ga naar het deelvenster Beheer > **[!UICONTROL Catalog]** > **[!UICONTROL Products]** .
1. Bewerk elk product (bijvoorbeeld Joust Duffle Bag [ SKU: 24-MB01 ]).
1. Een nieuwe update plannen:
   * Selecteren **[!UICONTROL Save as a New Update]**
   * Naam van update: &quot;Update 1&quot;
   * Begindatum: huidige tijd +1 min
   * Einddatum: huidige tijd +1 uur
   * Productnaam wijzigen in: &quot;Joust Duffle Bag 2&quot;
   * Sla het product op.
1. Ga naar CLI en voer uitsnijden uit en wacht tot het schema is toegepast.

   ```shell
   bin/magento cron:run && bin/magento cron:run
   ```

1. Ga opnieuw naar **[!UICONTROL Catalog]** > **[!UICONTROL Products]** en bewerk een configureerbaar product (bijvoorbeeld Chaz Kangeroo Hoodie [ SKU: MH01 ]).

   * Alle varianten uitschakelen. Ga naar de kolom Acties > **[!UICONTROL Select]** > **[!UICONTROL Disable Product]** .
   * Sla het configureerbare bestand op.

<u> Verwachte resultaten </u>:

Geen fout bij het opslaan van het product.

<u> Ware resultaten </u>:

De volgende fout treedt op:

```SQL
SQLSTATE[23000]: Integrity constraint violation: 1048 Column 'sku' cannot be null, query was: INSERT INTO `catalog_product_entity` (`entity_id`, `sku`, `row_id`, `created_in`, `updated_in`) VALUES (?, ?, ?, ?, ?)
```

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source ter plaatse: [[!DNL Quality Patches Tool] > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de [!DNL Quality Patches Tool] gids.
* Adobe Commerce op cloudinfrastructuur: [ Verbeteringen en Patches > pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Meer informatie over [!DNL Quality Patches Tool] vindt u in:

* [[!DNL Quality Patches Tool]  vrijgegeven: een nieuw hulpmiddel om kwaliteitsflarden ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!UICONTROL Quality Patches Tool] gids.


Zie [[!DNL Quality Patches Tool] voor meer informatie over andere patches die beschikbaar zijn in QPT: Zoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
