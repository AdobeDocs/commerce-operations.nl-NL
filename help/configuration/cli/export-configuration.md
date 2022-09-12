---
title: Configuratieinstellingen exporteren
description: De de configuratiemontages van de uitvoer Adobe Commerce aan configuratiedossiers, die ook als config stortplaats worden bekend.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Configuratieinstellingen exporteren

In Commerce 2.2 en hoger [implementatiemodel voor pijpleidingen](../deployment/technical-details.md), kunt u een consistente configuratie op verschillende systemen onderhouden. Nadat u montages in Admin op uw ontwikkelingssysteem vormt, voer die montages naar configuratiedossiers uit gebruikend het volgende bevel:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ is een spatie-gescheiden lijst van config types aan stortplaats. Beschikbare typen zijn `scopes`, `system`, `themes`, en `i18n`. Als geen config types worden gespecificeerd, dumpt het bevel alle informatie van de systeemconfiguratie.

In het volgende voorbeeld worden alleen het bereik en de thema&#39;s dumpt:

```bash
bin/magento app:config:dump scopes themes
```

Als resultaat van de beveluitvoering, worden de volgende configuratiedossiers bijgewerkt:

- `app/etc/config.php`

   Dit is het gedeelde configuratiedossier voor al uw instanties van de Handel.
Neem dit op in de broncontrole zodat het kan worden gedeeld tussen de ontwikkelings-, bouw- en productiesystemen.

   Zie [config.php reference](../reference/config-reference-configphp.md).

- `app/etc/env.php`

   Dit is het milieu-specifieke configuratiedossier.
Het bevat gevoelige en systeemspecifieke instellingen voor afzonderlijke omgevingen.

   Do _niet_ neem dit dossier in broncontrole op.

   Zie [env.php reference](../reference/config-reference-envphp.md).

## Gevoelige of systeemspecifieke instellingen

Om de gevoelige instellingen in te stellen waarnaar wordt geschreven `env.php`, gebruikt u de [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) gebruiken.

De waarden van de configuratie worden gespecificeerd als of gevoelig of systeem-specifiek door van verwijzingen te voorzien [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) in de module [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) bestand.

Aanvullende systeeminstellingen exporteren bij gebruik `config_types`kunt u de [`bin/magento config:set`](set-configuration-values.md#set-values) gebruiken.
