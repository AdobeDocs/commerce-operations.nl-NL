---
title: De databasestatus controleren
description: Ga als volgt te werk om de Adobe Commerce- of Magento Open Source-databasestatus te controleren.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 2%

---


# De databasestatus controleren

Voordat u deze opdracht uitvoert, moet u [Implementatieconfiguratie maken of bijwerken](deployment.md).

## Opdrachtgebruik

De status van de database controleren.

```bash
bin/magento setup:db:status
```

Deze opdracht heeft geen argumenten of opties.

Monsteruitvoer volgt:

```terminal
All modules are up to date.
```

De opdracht retourneert een van de volgende afsluitcodes:

| Afsluitcode | Beschrijving | Voorgestelde actie |
|--------------|--------------|---------------|
| 0 | Normaal | Geen |
| 1 | Sommige modules gebruiken codeversies die nieuwer of ouder zijn dan de database | Uitvoeren [`magento setup:upgrade`](database-upgrade.md) om het gegevensbestandschema bij te werken en in werking te stellen `composer update` in de hoofdmap van de toepassing om componentafhankelijkheden bij te werken |
| 2 | `magento setup:upgrade` is vereist | [`magento setup:upgrade`](database-upgrade.md) om de [databaseschema](https://glossary.magento.com/database-schema) |