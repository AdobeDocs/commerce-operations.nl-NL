---
title: Het databaseschema maken
description: Ga als volgt te werk om een database voor uw Adobe Commerce-project te maken.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Het databaseschema maken

Alvorens u dit bevel in werking stelt, moet u [&#x200B; creëren of de plaatsingsconfiguratie &#x200B;](deployment.md) bijwerken.

## De database configureren en gegevens toevoegen

Opdrachtgebruik:

```bash
bin/magento setup:db-schema:upgrade
```

Als u de status van de database wilt zien, voert u

```bash
bin/magento setup:db:status
```
