---
title: Cachetypen
description: De voorkanten van het geheime voorgeheugen van de vennoot met geheim voorgeheugentypes.
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Cachetypen

De volgende stappen lopen door het associëren van geheim voorste voorkant van het geheime voorgeheugen met een geheim voorgeheugentype.

## Stap 1: Een voorkant van een cache definiëren

De aanvraag voor handel bevat een `default` cachefront dat u kunt gebruiken voor elke [cachetype](../cli/manage-cache.md#clean-and-flush-cache-types). In deze sectie wordt beschreven hoe u desgewenst een voorkant van een cache met een andere naam kunt definiëren. Dit is aan te raden als u uw voorkant wilt aanpassen.

>[!INFO]
>
>Als u de opdracht `default` cachetype, hoeft u niet te wijzigen `env.php` überhaupt; u wijzigt de globale handels `di.xml`. Zie [Cacheopties op laag niveau](cache-options.md).

U moet een voorinstelling voor een aangepaste cache opgeven of `app/etc/env.php` of wereldwijde handel `app/etc/di.xml`.

In het volgende voorbeeld wordt getoond hoe u dit kunt definiëren in het dialoogvenster `env.php` bestand, dat het `di.xml` bestand:

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Wanneer `<unique frontend id>` is een unieke naam om uw voorzijde te identificeren en `<cache options>` zijn opties besproken in de onderwerpen specifiek voor elk type van caching (gegevensbestand, Redis, etc.).

## Stap 2: De cache configureren

U kunt de opties voor de configuratie van de front- en back-end cache opgeven in `env.php` of `di.xml`. Deze taak is optioneel.

`env.php` voorbeeld:

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

waar

- `<frontend_type>` is het front-end cachetype op laag niveau. Geef de naam op van een klasse die compatibel is met `Zend\Cache\Core`.
Als u weglaat `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) wordt gebruikt.

- `<frontend_option>`, `<frontend_option_value>` Dit zijn de naam en waarde van opties die het kader van de Handel als associatieve serie aan het frontend geheime voorgeheugen op zijn verwezenlijking overgaat.
- `<backend_type>` is het achterste cachetype op laag niveau. Geef de naam op van een klasse die compatibel is met `Zend_Cache_Backend` en dat `Zend_Cache_Backend_Interface`.
- `<backend_option>` en `<backend_option_value>` Dit zijn de naam en waarde van opties die het kader van de Handel als associatieve serie aan achterste voorgeheugen op zijn verwezenlijking overgaat.

Zie de [Documentatie Laminas](https://docs.laminas.dev/) voor de meest recente informatie van Zend.
