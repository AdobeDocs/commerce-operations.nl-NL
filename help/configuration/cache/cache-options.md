---
title: Cacheopties
description: Meer informatie over cacheopties op laag niveau en opslagconfiguratie in Adobe Commerce. Ontdek frontend, backend, en opslagopstelling voor Redis en gegevensbestanden.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# Cacheopties op laag niveau

De Commerce-toepassing gebruikt een cachefront op laag niveau en een back-end voor toegang tot de cacheopslag.

## Voorste cache op laag niveau

Commerce breidt [ Zend_Cache_Core ](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) door [ Magento\Framework\Cache\Core ](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) frontend geheim voorgeheugen uit uit te voeren.

## Backend-cache op laag niveau

In het algemeen, werkt de toepassing van Commerce met om het even welk achterste voorgeheugen dat [ steunt Zend_Cache Achtergronden ](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html). Deze handleiding is echter alleen van toepassing op de volgende kleine backend-caches:

- [Redis](config-redis.md)
- [ Gegevensbestand ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Bestandssysteem (standaard): er is geen configuratie nodig om het in cache plaatsen van bestandssystemen te gebruiken.

[ Varnish ](config-varnish.md) vereist geen vestiging een laag-vlakke geheim voorgeheugensteun.
