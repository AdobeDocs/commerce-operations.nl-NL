---
title: De databasestatus controleren
description: Ga als volgt te werk om de status van uw Adobe Commerce-database te controleren.
exl-id: 33d9b30a-4504-4955-b11a-0a642f23209b
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '104'
ht-degree: 2%

---

# De databasestatus controleren

Alvorens u dit bevel in werking stelt, moet u [ creëren of de plaatsingsconfiguratie ](deployment.md) bijwerken.

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
| 1 | Sommige modules gebruiken codeversies die nieuwer of ouder zijn dan de database | Voer [`magento setup:upgrade`](database-upgrade.md) uit om het databaseschema bij te werken en voer `composer update` uit vanuit de hoofdmap van de toepassing om componentafhankelijkheden bij te werken |
| 2 | `magento setup:upgrade` is vereist | [`magento setup:upgrade`](database-upgrade.md) om het databaseschema bij te werken |
