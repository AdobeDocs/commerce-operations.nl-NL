---
title: Cacheopties
description: Toegang tot cache op laag niveau configureren.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 0%

---

# Cacheopties op laag niveau

De toepassing Commerce gebruikt een laag niveau [cachegeheugen](https://glossary.magento.com/cache) [voorzijde](https://glossary.magento.com/frontend) en [achterste](https://glossary.magento.com/backend) om toegang te verlenen tot de cacheopslag.

## Voorste cache op laag niveau

Commerce extends [Zend_Cache_core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) door [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) frontend cache.

## Backend-cache op laag niveau

In het algemeen werkt de toepassing Commerce met elke back-end cache die [Zend_cache-achtergronden](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) ondersteunt. Deze handleiding is echter alleen van toepassing op de volgende kleine backend-caches:

- [Redis](config-redis.md)
- [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Bestandssysteem (standaard): Er is geen configuratie nodig om het in cache plaatsen van bestandssystemen te gebruiken.

[Varnish](config-varnish.md) hoeft u geen cache-backend op laag niveau in te stellen.
