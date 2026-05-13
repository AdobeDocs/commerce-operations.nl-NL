---
title: Opties voor cache-back-up en Naslaggids voor opslag
description: Meer informatie over de back-endopties voor cache in Adobe Commerce, zoals bestandssysteem, Redis, Valkey en databaseopslag. Maak kennis met oude en moderne benaderingen.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 9cd0f2a84772e2d68fd15a00651216abfa9ec91c
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Achtergrondopties voor cache en opslagreferentie

De Commerce-toepassing gebruikt een cachefront op laag niveau en biedt toegang tot cacheopslag. Commerce biedt ondersteuning voor verschillende achtergronden en strategieën voor het in cache plaatsen, elk geschikt voor verschillende gebruiksgevallen. Op deze pagina worden de beschikbare achtergronden beschreven en wordt aangegeven hoe deze verschillen.

>[!NOTE]
>
>Voor details over frontend geheim voorgeheugenconfiguratie, zie [&#x200B; voorkanten van het geheime voorgeheugen vormen &#x200B;](cache-types.md).

## Opties voor achtergrondcache

De volgende tabel geeft een overzicht van de beschikbare backend-caches:

| Achtergrond | Beschrijving | Configuratiegids |
| ------- | ----------- | ------------------- |
| Bestandssysteem | Standaard. Hiermee worden cachegegevens opgeslagen in bestanden onder `var/cache/` . Geen configuratie vereist. | NVT |
| [&#x200B; Redis &#x200B;](config-redis.md) | Opslag van gegevens in het geheugen voor krachtige caching. | [&#x200B; Redis van het Gebruik voor standaardgeheime voorgeheugen &#x200B;](redis-pg-cache.md) |
| [&#x200B; Valkey &#x200B;](config-valkey.md) | Open-source, Redis-compatibel alternatief. | [&#x200B; Valkey van het Gebruik voor standaardgeheime voorgeheugen &#x200B;](valkey-pg-cache.md) |
| [&#x200B; Gegevensbestand &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | Door database ondersteund in cache plaatsen. | [&#x200B; creeer de motoren van het douanegeheime voorgeheugen &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} (de documentatie van de ontwikkelaar van Adobe) |

>[!NOTE]
>
>[&#x200B; Varkenshaar &#x200B;](config-varnish.md) behandelt volledige pagina caching op het niveau van HTTP en gebruikt niet de laag-vlakke geheim voorgeheugensteun.

## Implementatiebenaderingen

Commerce ondersteunt twee achterwaartse implementatiemethoden. Welke benadering u kiest, is afhankelijk van uw Commerce-versie:

>[!BEGINTABS]

>[!TAB  Verouderd Zend-based geheime voorgeheugen (2.4.8 en vroeger) ]

Gebruikt volledige klassennamen voor de achterste configuratie:

| Achtergrond | Klassenaam |
| ------- | ---------- |
| Redis | `Magento\Framework\Cache\Backend\Redis` |
| Valkey | `Magento\Framework\Cache\Backend\Valkey` |

Deze zijn compatibel met de interface `Zend_Cache_Backend` .

**configuratie van het Voorbeeld:**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB  Modern geheime voorgeheugen van het Symfony (2.4.9 en later, geadviseerd) ]

>[!TIP]
>
>De moderne implementatie van het Geheime voorgeheugen van Symfony verstrekt betere prestaties door naleving PSR-6, Igbinary rangschikking, gzip compressie, manuscripten Lua, en blijvende verbindingen.

Gebruikt vereenvoudigde achterste tekstnamen:

| Achtergrond | Naam type |
| ------- | --------- |
| Redis | `redis` |
| Valkey | `valkey` |
| Bestandssysteem | `file` |

**configuratie van het Voorbeeld:**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

Voor volledige configuratieopties, zie:

- [Redis gebruiken voor standaardcache](redis-pg-cache.md)
- [Valkey gebruiken voor standaardcache](valkey-pg-cache.md)
- [L2-cacheconfiguratie](level-two-cache.md)

Zie de [&#x200B; documentatie van Laminas &#x200B;](https://docs.laminas.dev/) voor erfenis Zend-based opties.
