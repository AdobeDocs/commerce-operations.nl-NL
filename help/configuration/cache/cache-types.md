---
title: Cachetypen
description: Leer hoe u cachevooreinden kunt koppelen aan cachetypen in Adobe Commerce. Detecteer de configuratie en beheertechnieken van de cache.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Cachetypen

De volgende stappen lopen door het associëren van geheim voorste voorkant van het geheime voorgeheugen met een geheim voorgeheugentype.

## Stap 1: Definieer een voorkant van een cache

De toepassing van Commerce heeft a `default` geheim voorfront dat u voor om het even welk [ geheim voorgeheugentype ](../cli/manage-cache.md#clean-and-flush-cache-types) kunt gebruiken. In deze sectie wordt beschreven hoe u desgewenst een voorkant van een cache met een andere naam kunt definiëren. Dit is aan te raden als u uw voorkant wilt aanpassen.

>[!INFO]
>
>Als u het cachetype `default` wilt gebruiken, hoeft u `env.php` helemaal niet te wijzigen. U wijzigt Commerce global `di.xml` . Zie [ laag-vlakke geheim voorgeheugenopties ](cache-options.md).

U moet een aangepaste cachevoorzijde opgeven `app/etc/env.php` of Commerce global `app/etc/di.xml` .

In het volgende voorbeeld wordt getoond hoe u dit kunt definiëren in het `env.php` -bestand, dat het `di.xml` -bestand overschrijft:

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

Waar `<unique frontend id>` een unieke naam is om uw voorzijde te identificeren en `<cache options>` zijn opties die worden besproken in de onderwerpen die specifiek zijn voor elk type caching (database, Redis, enzovoort).

## Stap 2: Vorm het geheime voorgeheugen

U kunt de configuratieopties voor de voorste cache en de achterste cache opgeven in `env.php` of `di.xml` . Deze taak is optioneel.

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

- `<frontend_type>` is het cachetype op laag niveau frontend. Geef de naam op van een klasse die compatibel is met `Zend\Cache\Core` .
Als u `<frontend_type>` weglaat, [ Magento\Framework\Cache\Core ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) wordt gebruikt.

- `<frontend_option>` is `<frontend_option_value>` de naam en waarde van de opties die het Commerce-framework na het maken als een associatieve array doorgeeft aan de frontend-cache.
- `<backend_type>` is het lage type achterste cache. Geef de naam op van een klasse die compatibel is met `Zend_Cache_Backend` en die `Zend_Cache_Backend_Interface` implementeert.
- `<backend_option>` en `<backend_option_value>` zijn de naam en waarde van de opties die het Commerce-framework na het maken doorgeeft als een associatieve array om cache op te slaan als back-end.

Zie de [ documentatie van Laminas ](https://docs.laminas.dev/) voor de recentste informatie van het Gebied.
