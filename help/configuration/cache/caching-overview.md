---
title: Caching configureren
description: Leer over caching en hoe te om geheim voorgeheugenmechanismen voor de toepassing van Adobe Commerce en van de Magento Open Source te vormen.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Caching configureren

[!DNL Commerce] laat u toe om alternatieven aan het standaarddossiersysteem caching te vormen. In deze gids worden enkele van deze alternatieven besproken; namelijk:

- De volgende cachemechanismen instellen in het dialoogvenster [!DNL Commerce] configuratie:

   - [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Bestandssysteem (standaard): Er is geen configuratie nodig om de standaardcaching van het bestandssysteem te gebruiken.

- Stel de [Varnish](config-varnish.md) zonder de [!DNL Commerce] configuratie.

## Caching terminologie

[!DNL Commerce] gebruikt de volgende caching terminologie:

- **Voorzijde**—Gelijkaardig aan een interface of gateway om opslag in het voorgeheugen onder te brengen, die door wordt uitgevoerd [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Cachetypen**—Kan één van de types zijn die met worden verstrekt [!DNL Commerce] of u kunt [uw eigen](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Achtergrond**—Geeft details over [cacheopslag](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), geïmplementeerd door [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Achtergrond met twee niveaus**—Hiermee slaat u cacherecords op in twee achtergronden: sneller en langzamer.

   >[!INFO]
   >
   >De twee-vlakke backend geheim voorgeheugenconfiguratie is voorbij het werkingsgebied van deze gids.

## Configuratieopties

- De verstrekte gegevens wijzigen `default` cachefront—

   U wijzigt alleen de `<magento_root>/app/etc/di.xml` bestand, de algemene configuratie voor injectie van afhankelijkheden van de toepassing Commerce.

- Uw eigen voorste cache configureren—

   U wijzigt alleen de `<magento_root>/app/etc/env.php` bestand omdat dit de equivalente configuratie in het dialoogvenster `di.xml` bestand.

>[!TIP]
>
>Varnish vereist geen wijzigingen in de [!DNL Commerce] configuratie. Zie [Varnish configureren en gebruiken](config-varnish.md).
