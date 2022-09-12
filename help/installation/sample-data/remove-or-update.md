---
title: Voorbeeldgegevensmodules verwijderen of bijwerken
description: Voer de volgende stappen uit om Adobe Commerce- en Magento Open Source-voorbeeldgegevensmodules te beheren.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# Voorbeeldgegevensmodules verwijderen of bijwerken

Dit onderwerp bespreekt hoe te:

* [Voorbeeldgegevensmodules verwijderen](#remove-sample-data-modules) van een Adobe Commerce- of Magento Open Source-installatie `composer.json`. Deze optie doet *niet* voorbeeldgegevens uit de database verwijderen.

* [Voorbeeldgegevens bijwerken voorbereiden](#prepare-to-update-sample-data) (bijvoorbeeld voordat u de Magento-toepassing bijwerkt).

## Voorbeeldgegevensmodules verwijderen

Voer de volgende opdracht in:

```bash
bin/magento sampledata:remove
```

De volledige lijst van modules met steekproefgegevens volgt:

Adobe Commerce en Magento Open Source:

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

Alleen Adobe Commerce:

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## Voorbeeldgegevens bijwerken voorbereiden

Met deze opdracht kunt u voorbeeldgegevens bijwerken voordat u Adobe Commerce of Magento Open Source bijwerkt.

Voer de volgende opdracht in om voorbeeldgegevens voor te bereiden voor het bijwerken:

```bash
bin/magento sampledata:reset
```

Daarna, [de toepassing bijwerken](../tutorials/uninstall.md#update-the-application).
