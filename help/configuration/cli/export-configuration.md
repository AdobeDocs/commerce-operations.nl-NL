---
title: Configuratieinstellingen exporteren
description: De de configuratiemontages van de uitvoer Adobe Commerce aan configuratiedossiers, die ook als config stortplaats worden bekend.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Configuratieinstellingen exporteren

In Commerce 2.2 en later [ model van de pijpleidingsplaatsing ](../deployment/technical-details.md), kunt u een verenigbare configuratie over systemen handhaven. Nadat u montages in Admin op uw ontwikkelingssysteem vormt, voer die montages naar configuratiedossiers uit gebruikend het volgende bevel:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ is een ruimte-gescheiden lijst van config types aan stortplaats. Beschikbare typen zijn `scopes` , `system` , `themes` en `i18n` . Als geen config types worden gespecificeerd, dumpt het bevel alle informatie van de systeemconfiguratie.

In het volgende voorbeeld worden alleen het bereik en de thema&#39;s dumpt:

```bash
bin/magento app:config:dump scopes themes
```

Als resultaat van de beveluitvoering, worden de volgende configuratiedossiers bijgewerkt:

- `app/etc/config.php`

  Dit is het gedeelde configuratiebestand voor al uw Commerce-instanties.
Neem dit op in de broncontrole zodat het kan worden gedeeld tussen de ontwikkelings-, bouw- en productiesystemen.

  Zie [ config.php verwijzing ](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  Dit is het milieu-specifieke configuratiedossier.
Het bevat gevoelige en systeemspecifieke instellingen voor afzonderlijke omgevingen.

  __ omvat dit dossier niet in broncontrole.

  Zie [ env.php verwijzing ](../reference/config-reference-envphp.md).

## Gevoelige of systeemspecifieke instellingen

Gebruik de opdracht `env.php` om de gevoelige instellingen in te stellen die naar [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) worden geschreven.

De waarden van de configuratie worden gespecificeerd als of gevoelig of systeem-specifiek door [`Magento\Config\Model\Config\TypePool` van verwijzingen te voorzien ](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) in het 2&rbrace; [`di.xml` dossier van de module &lbrace;.](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific)

Als u aanvullende systeeminstellingen wilt exporteren wanneer u `config_types` gebruikt, kunt u de opdracht [`bin/magento config:set`](set-configuration-values.md#set-values) gebruiken.
