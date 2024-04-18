---
title: Voorbeeldgegevensmodules verwijderen of bijwerken
description: Voer de volgende stappen uit om Adobe Commerce-voorbeeldgegevensmodules te beheren.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Voorbeeldgegevensmodules verwijderen of bijwerken

Dit onderwerp bespreekt hoe te:

* [Voorbeeldgegevensmodules verwijderen](#remove-sample-data-modules) vanuit een Adobe Commerce-installatie `composer.json`. Deze optie doet *niet* voorbeeldgegevens uit de database verwijderen.

* [Voorbeeldgegevens bijwerken voorbereiden](#prepare-to-update-sample-data) (bijvoorbeeld voordat u de toepassing Magento bijwerkt).

## Voorbeeldgegevensmodules verwijderen

Voer de volgende opdracht in:

```bash
bin/magento sampledata:remove
```

De volledige lijst van modules met steekproefgegevens volgt:

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

## Voorbeeldgegevens bijwerken voorbereiden

Met deze opdracht kunt u voorbeeldgegevens bijwerken voordat u Adobe Commerce bijwerkt.

Voer de volgende opdracht in om voorbeeldgegevens voor te bereiden voor het bijwerken:

```bash
bin/magento sampledata:reset
```

Daarna, [de toepassing bijwerken](../tutorials/uninstall.md#update-the-application).
