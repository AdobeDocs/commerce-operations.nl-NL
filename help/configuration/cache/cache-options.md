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

Commerce breidt [&#x200B; Zend_Cache_Core &#x200B;](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) door [&#x200B; Magento\Framework\Cache\Core &#x200B;](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) frontend geheim voorgeheugen uit uit te voeren.

## Backend-cache op laag niveau

In het algemeen, werkt de toepassing van Commerce met om het even welk achterste voorgeheugen dat [&#x200B; steunt Zend_Cache Achtergronden &#x200B;](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html). Deze handleiding is echter alleen van toepassing op de volgende kleine backend-caches:

- [Redis](config-redis.md)
- [&#x200B; Gegevensbestand &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- Bestandssysteem (standaard): er is geen configuratie nodig om het in cache plaatsen van bestandssystemen te gebruiken.

[&#x200B; Varnish &#x200B;](config-varnish.md) vereist geen vestiging een laag-vlakke geheim voorgeheugensteun.
