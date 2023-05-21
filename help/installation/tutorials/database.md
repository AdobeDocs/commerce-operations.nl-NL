---
title: Het databaseschema maken
description: Ga als volgt te werk om een database voor uw Adobe Commerce of Magento Open Source te maken.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
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
