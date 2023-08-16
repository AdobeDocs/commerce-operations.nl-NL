---
title: De Admin-URI weergeven of wijzigen
description: Voer de volgende stappen uit om de URI van uw Adobe Commerce- of Magento Open Source-beheertoepassing weer te geven en te wijzigen.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# De Admin-URI weergeven of wijzigen

Voordat u deze opdracht uitvoert, moet u [Implementatieconfiguratie maken of bijwerken](deployment.md).

## De Admin-URI weergeven

In deze sectie wordt besproken hoe u de opdrachtregel kunt gebruiken om de Admin Uniform Resource Identifier ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Opdrachtopties:

```bash
bin/magento info:adminuri
```

Hieronder volgt een voorbeeldresultaat:

```terminal
Admin Panel URI: /admin_1wgrah
```

U kunt ook de Admin-URI weergeven in `<magento_root>/app/etc/env.php`. Een fragment volgt:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## De URL van de beheerder wijzigen

Als u de beheerinterface wilt wijzigen, gebruikt u de opdracht [`magento setup:config:set`](deployment.md) gebruiken.
