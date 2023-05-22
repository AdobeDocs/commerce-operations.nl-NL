---
title: Cacheopties
description: Toegang tot cache op laag niveau configureren.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Cacheopties op laag niveau

De toepassing van de Handel gebruikt een laag-vlakke voorzijde van het geheime voorgeheugen en achterkant om toegang tot de geheim voorgeheugenopslag te verlenen.

## Voorste cache op laag niveau

Commerce extends [Zend_Cache_core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) door [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) frontend cache.

## Backend-cache op laag niveau

In het algemeen werkt de toepassing Commerce met elke back-end cache die [Zend_cache-achtergronden](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) ondersteunt. Deze handleiding is echter alleen van toepassing op de volgende kleine backend-caches:

- [Redis](config-redis.md)
- [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Bestandssysteem (standaard): Er is geen configuratie nodig om het in cache plaatsen van bestandssystemen te gebruiken.

[Varnish](config-varnish.md) hoeft u geen cache-backend op laag niveau in te stellen.
