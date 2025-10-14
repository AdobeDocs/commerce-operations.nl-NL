---
title: De databasestatus controleren
description: Ga als volgt te werk om de status van uw Adobe Commerce-database te controleren.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 2%

---

# De databasestatus controleren

Alvorens u dit bevel in werking stelt, moet u [&#x200B; creëren of de plaatsingsconfiguratie &#x200B;](deployment.md) bijwerken.

## Opdrachtgebruik

De status van de database controleren.

```bash
bin/magento setup:db:status
```

Deze opdracht heeft geen argumenten of opties.

Monsteruitvoer volgt:

```
All modules are up to date.
```

De opdracht retourneert een van de volgende afsluitcodes:

| Afsluitcode | Beschrijving | Voorgestelde actie |
|--------------|--------------|---------------|
| 0 | Normaal | Geen |
| 1 | Sommige modules gebruiken codeversies die nieuwer of ouder zijn dan de database | Voer [`magento setup:upgrade`](database-upgrade.md) uit om het databaseschema bij te werken en voer `composer update` uit vanuit de hoofdmap van de toepassing om componentafhankelijkheden bij te werken |
| 2 | `magento setup:upgrade` is vereist | [`magento setup:upgrade`](database-upgrade.md) om het databaseschema bij te werken |
