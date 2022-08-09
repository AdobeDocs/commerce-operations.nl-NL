---
title: config.php reference
description: Zie een lijst met waarden in het bestand config.php.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---


# config.php reference

De `config.php` bestand bevat de volgende secties:

| Naam | Beschrijving |
| --------- | -------------------|
| `i18n` | Alle inline-vertaalgegevens. Het lezen vanuit deze sectie wordt niet ondersteund. |
| `modules` | De lijst van toegelaten en gehandicapte modules. |
| `scopes` | De lijst met winkels, winkelgroepen en websites met verwante informatie. |
| `system` | De systeemconfiguraties die vereist zijn voor de implementatie van statische inhoud. |
| `themes` | De configuratie van geïnstalleerde thema&#39;s. |

## modules

Bevat een array van modules en hun statussen. Als module is ingeschakeld, is de waarde 1. Anders is de waarde 0.

```conf
'modules' => [
    'Magento_Store' => 1,
    'Magento_Theme' => 0,
    'Magento_Backend' => 0,
    'Magento_Eav' => 1
]
```

Meer informatie over [Modules].

## bereik

Bevat een array van bereikconfiguratiewaarden. Het heeft de volgende subnodes:

| Naam | Beschrijving |
| ---------- | -----------------------------------|
| `websites` | Websiteconfiguratie |
| `groups` | Configuratie van winkels |
| `stores` | Configuratie van weergaven opslaan |

```conf
'scopes' => [
  'websites' => [
    'admin' => [
      'website_id' => '0',
      'code' => 'admin',
      'name' => 'Admin',
      'sort_order' => '0',
      'default_group_id' => '0',
      'is_default' => '0'
    ]
  ],
  'groups' => [
    0 => [
      'group_id' => '0',
      'website_id' => '0',
      'code' => 'default',
      'name' => 'Default',
      'root_category_id' => '0',
      'default_store_id' => '0'
    ]
  ],
  'stores' => [
    'admin' => [
      'store_id' => '0',
      'code' => 'admin',
      'website_id' => '0',
      'group_id' => '0',
      'name' => 'Admin',
      'sort_order' => '0',
      'is_active' => '1'
    ]
  ]
]
```

Meer informatie over [Commerciële aspecten][scopes].

## systeem

Bevat een array van configuratiewaarden voor systeemvelden.

```conf
'system'=> [
    'default' =>[
        'checkout' => [
            'cart' => [
                'delete_quote_after' => 31
            ]
        ]
    ]
]
```

Meer informatie over [Systeemspecifieke configuraties](config-reference-sens.md).

## thema&#39;s

Bevat een array van waarden voor themaconfiguratie.

```conf
'themes' => [
  'frontend/Magento/luma' => [
    'parent_id' => 'Magento/blank',
    'theme_path' => 'Magento/luma',
    'theme_title' => 'Magento Luma',
    'is_featured' => '0',
    'area' => 'frontend',
    'type' => '0',
    'code' => 'Magento/luma'
  ]
]
```

Meer informatie over [Thema&#39;s].

<!-- link definitions -->

[Modules]: https://devdocs.magento.com/videos/fundamentals/create-a-new-module/
[scopes]: https://docs.magento.com/user-guide/configuration/scope.html
[Thema&#39;s]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/theme-create.html