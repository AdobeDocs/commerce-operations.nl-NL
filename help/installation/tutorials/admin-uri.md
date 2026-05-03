---
title: De Admin-URI weergeven of wijzigen
description: Voer de volgende stappen uit om de URI van uw Adobe Commerce-beheertoepassing te bekijken en te wijzigen.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '99'
ht-degree: 0%

---

# De Admin-URI weergeven of wijzigen

Alvorens u dit bevel in werking stelt, moet u [ creëren of de plaatsingsconfiguratie ](deployment.md) bijwerken.

## De Admin-URI weergeven

Deze sectie bespreekt hoe te om de bevellijn te gebruiken om het Eenvormige Herkenningsteken van het Middel Admin ([ URI ](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)) te tonen.

Opdrachtopties:

```shell
bin/magento info:adminuri
```

Hieronder volgt een voorbeeldresultaat:

```text
Admin Panel URI: /admin_1wgrah
```

U kunt de Admin-URI ook weergeven in `<magento_root>/app/etc/env.php` . Een fragment volgt:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## De URL van de beheerder wijzigen

Gebruik de opdracht [`magento setup:config:set`](deployment.md) om de beheerderURI te wijzigen.
