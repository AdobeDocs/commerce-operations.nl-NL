---
title: Het databaseschema maken
description: Ga als volgt te werk om een database voor uw Adobe Commerce of Magento Open Source te maken.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '52'
ht-degree: 0%

---


# Het databaseschema maken

Voordat u deze opdracht uitvoert, moet u [Implementatieconfiguratie maken of bijwerken](deployment.md).

## De database configureren en gegevens toevoegen

Opdrachtgebruik:

```bash
bin/magento setup:db-schema:upgrade
```

Als u de status van de database wilt zien, voert u

```bash
bin/magento setup:db:status
```
