---
title: Cachevoorkeuren configureren
description: Leer hoe u cachevooreinden definieert en deze koppelt aan cachetypen in Adobe Commerce. Ontdek configuratiesyntaxis voor env.php en di.xml.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: de613310ad701dd594a6ee8fcd973aa2c3769870
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Vooruiteinden van cache configureren

Een cachefront is een interface tussen Commerce en de back-end van de cacheopslag. U kunt veelvoudige frontends, elk met verschillende achterste montages bepalen, en dan specifieke [ geheim voorgeheugentypes ](../cli/manage-cache.md#clean-and-flush-cache-types) toewijzen aan elk front.

Dit is nuttig wanneer u verschillende geheim voorgeheugenachtergronden of configuraties voor verschillende types van caching gegevens wilt gebruiken. U wilt bijvoorbeeld dat `full_page` in cache wordt geplaatst op een toegewezen Redis-database terwijl u een aparte database gebruikt voor `default` caching.

## De standaardvoorzijde gebruiken

Commerce biedt een voorzijde voor de cache van `default` die geschikt is voor alle typen cache. Het breidt [ Zend_Cache_Core ](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) uit door het [ Magento\Framework\Cache\Core ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) frontend geheime voorgeheugen uit te voeren.

In de meeste gevallen hoeft u de voorkant niet aan te passen. U hoeft alleen de backend te configureren. Zie [ achterste opties van het Geheime voorgeheugen ](cache-options.md).

## Een voorzijde voor een aangepaste cache definiëren

De volgende stappen lopen door het associëren van een geheim voorste voorkant van het geheime voorgeheugen met een geheim voorgeheugentype.

### Stap 1: Een cachefront definiëren en cachetypen toewijzen

Als u een voorkant van een aangepaste cache wilt definiëren, voegt u de configuratie toe aan `app/etc/env.php` (die `di.xml` overschrijft):

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
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Waarbij:

- `<unique frontend id>` — Een unieke naam voor de identificatie van de voorkant (bijvoorbeeld `default` , `page_cache` , `stale_cache_enabled` )
- `<cache options>` — Het type van achtergrond en de opties voor dit vooruitlopen (zie [ opties van het Geheime voorgeheugen ](cache-options.md))
- `<cache type>` — Een Commerce-cachetype dat aan dit front-end moet worden toegewezen (bijvoorbeeld `config` , `layout` , `block_html` , `full_page`)

>[!TIP]
>
>**Moderne implementatie van het Geheime voorgeheugen van het Symfony (2.4.9+):** Beginnend met Commerce 2.4.9, kunt u vereenvoudigde achterste types zoals `redis`, `valkey`, of `file` met de moderne implementatie van het Geheime voorgeheugen van het Symfony gebruiken. Zie [ Redis van het Gebruik voor standaardgeheime voorgeheugen ](redis-pg-cache.md) en [ Valkey van het Gebruik voor standaardgeheime voorgeheugen ](valkey-pg-cache.md) voor details.

### Stap 2: Opties voor front-end en back-end configureren

U kunt de configuratieopties voor de voorste cache en de achterste cache opgeven in `env.php` of `di.xml` . Deze taak is optioneel. Als u geen opties opgeeft, gebruikt Commerce de standaardinstellingen voor de voorzijde en de achterzijde.

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

Waarbij:

- `<frontend_type>` — Het front-end cachetype op laag niveau. Geef een klassenaam op die compatibel is met `Zend\Cache\Core` .
Als weggelaten, [ Magento\Framework\Cache\Core ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) wordt gebruikt.

- `<frontend_option>` , `<frontend_option_value>` — De naam en waarde van de opties die het Commerce-framework als een associatieve array doorgeeft aan de frontend-cache bij het maken.

- `<backend_type>` — Het type backend-cache op laag niveau. U kunt het volgende opgeven:
   - **Modern Geheime cache van het Symfony (2.4.9+, geadviseerd)**: Vereenvoudigde namen zoals `redis` , `valkey` of `file`
   - **Verouderde (op Zend-Gebaseerde)**: Volledige klassenaam is compatibel met `Zend_Cache_Backend` die `Zend_Cache_Backend_Interface` implementeert

- `<backend_option>` , `<backend_option_value>` — De naam en waarde van de opties die het Commerce-framework bij het maken als een associatieve array doorgeeft aan de back-end cache.

>[!NOTE]
>
>**Verouderd vs Moderne implementatie:**
>
>- **Verouderde (op Zend-Gebaseerde)**: `'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis'`
>- **Modern (het Geheime voorgeheugen van het Symfony)**: `'backend' => 'redis'` (aanbevolen voor Commerce 2.4.9+)
>
>De moderne implementatie van het Geheime voorgeheugen van Symfony verstrekt betere prestaties door naleving PSR-6, Igbinary rangschikking, gzip compressie, manuscripten Lua, en blijvende verbindingen.

Zie de [ documentatie van Laminas ](https://docs.laminas.dev/) voor op Zend-Gebaseerde opties, of de moderne gidsen van het Geheime voorgeheugen van het Symfony voor [ Redis ](redis-pg-cache.md) en [ Valkey ](valkey-pg-cache.md).
