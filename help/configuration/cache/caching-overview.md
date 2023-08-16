---
title: Caching configureren
description: Leer over caching en hoe te om geheim voorgeheugenmechanismen voor de toepassing van Adobe Commerce en van de Magento Open Source te vormen.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Caching configureren

[!DNL Commerce] laat u toe om alternatieven aan het standaarddossiersysteem caching te vormen. In deze gids worden enkele van die alternatieven besproken, namelijk:

- De volgende cachemechanismen instellen in het dialoogvenster [!DNL Commerce] configuratie:

   - [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Bestandssysteem (standaard): Er is geen configuratie nodig om standaardcaching van het bestandssysteem te gebruiken.

- Stel de [Varnish](config-varnish.md) zonder de [!DNL Commerce] configuratie.

## Caching terminologie

[!DNL Commerce] gebruikt de volgende caching terminologie:

- **Frontend**—Gelijkaardig aan een interface of gateway om opslag in het voorgeheugen onder te brengen, die door wordt uitgevoerd [Magento\Framework\Cache\Frontend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend).
- **Cachetypen**—Kan één van de types zijn die met worden verstrekt [!DNL Commerce] of u kunt [uw eigen](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/).
- **Achtergrond**—Geeft details over [cacheopslag](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), geïmplementeerd door [Magento\Framework\Cache\Backend](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend)
- **Achtergrond met twee niveaus**—Hiermee slaat u cacherecords op in twee achtergronden: een snellere en een langzamere.

  >[!INFO]
  >
  >De twee-vlakke backend geheim voorgeheugenconfiguratie is voorbij het werkingsgebied van deze gids.

## Configuratieopties

- De verstrekte gegevens wijzigen `default` cachefront—

  U wijzigt alleen de `<magento_root>/app/etc/di.xml` bestand, de algemene configuratie voor injectie van afhankelijkheid van de toepassing Commerce.

- Uw eigen voorste cache configureren—

  U wijzigt alleen de `<magento_root>/app/etc/env.php` bestand omdat dit de equivalente configuratie in het dialoogvenster `di.xml` bestand.

>[!TIP]
>
>Varnish vereist geen wijzigingen in de [!DNL Commerce] configuratie. Zie [Varnish configureren en gebruiken](config-varnish.md).
