---
title: Het databaseschema maken
description: Ga als volgt te werk om een database voor uw Adobe Commerce-project te maken.
exl-id: 860c9918-44c4-4ef1-88a5-12614566307c
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# Het databaseschema maken

Alvorens u dit bevel in werking stelt, moet u [&#x200B; creëren of de plaatsingsconfiguratie &#x200B;](deployment.md) bijwerken.

## De database configureren en gegevens toevoegen

Opdrachtgebruik:

```shell
bin/magento setup:db-schema:upgrade
```

Als u de status van de database wilt zien, voert u

```shell
bin/magento setup:db:status
```
