---
title: Caching configureren
description: Meer informatie over cachemechanismen en configuratieopties voor Adobe Commerce-toepassingen. Alternatieven voor standaardcaching van bestandssystemen ontdekken.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# Caching configureren

Met [!DNL Commerce] kunt u alternatieven configureren voor het in cache plaatsen van het standaardbestandssysteem. In deze gids worden enkele van die alternatieven besproken, namelijk:

- Stel de volgende cachemechanismen in de [!DNL Commerce] -configuratie in:

   - [&#x200B; Gegevensbestand &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Bestandssysteem (standaard): Er is geen configuratie nodig om standaardcaching van het bestandssysteem te gebruiken.

- Opstelling de [&#x200B; Vlek &#x200B;](config-varnish.md) zonder de [!DNL Commerce] configuratie te wijzigen.

## Caching terminologie

[!DNL Commerce] gebruikt de volgende terminologie in cache:

- **Frontend** - Gelijkaardig aan een interface of een gateway aan geheim voorgeheugenopslag, die door [&#x200B; Magento\Framework\Cache\Frontend &#x200B;](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend) wordt uitgevoerd.
- **types van Geheime voorgeheugen** - kan één van de types zijn die van [!DNL Commerce] worden voorzien of u kunt [&#x200B; uw eigen &#x200B;](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/) creëren.
- **Achtergrond** - specificeert details over [&#x200B; geheim voorgeheugenopslag &#x200B;](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), die door [&#x200B; Magento\Framework\Cache\Backend &#x200B;](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend) wordt uitgevoerd
- **dubbel-vlakke achtergrond** - slaat geheim voorgeheugenverslagen in twee achtergronden op: snellere en langzamere.

  >[!INFO]
  >
  >De twee-vlakke backend geheim voorgeheugenconfiguratie is voorbij het werkingsgebied van deze gids.

## Configuratieopties

- De meegeleverde voorzijde van de `default` cache wijzigen—

  U wijzigt alleen het `<magento_root>/app/etc/di.xml` -bestand, de algemene configuratie voor het injecteren van afhankelijkheden van de Commerce-toepassing.

- Uw eigen voorste cache configureren—

  U wijzigt alleen het `<magento_root>/app/etc/env.php` -bestand omdat dit de equivalente configuratie in het `di.xml` -bestand overschrijft.

>[!TIP]
>
>Voor vernis hoeft de configuratie van [!DNL Commerce] niet te worden gewijzigd. Zie [&#x200B; vormen en gebruiken Vierkant &#x200B;](config-varnish.md).
