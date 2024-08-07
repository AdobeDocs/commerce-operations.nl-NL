---
title: Caching configureren
description: Leer over caching en hoe te om geheim voorgeheugenmechanismen voor de toepassing van Adobe Commerce te vormen.
feature: Configuration, Cache
exl-id: 6effa069-c043-411a-b161-01210be17391
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Caching configureren

Met [!DNL Commerce] kunt u alternatieven configureren voor het in cache plaatsen van het standaardbestandssysteem. In deze gids worden enkele van die alternatieven besproken, namelijk:

- Stel de volgende cachemechanismen in de [!DNL Commerce] -configuratie in:

   - [ Gegevensbestand ](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
   - [Redis](config-redis.md)
   - Bestandssysteem (standaard): Er is geen configuratie nodig om standaardcaching van het bestandssysteem te gebruiken.

- Opstelling de [ Vlek ](config-varnish.md) zonder de [!DNL Commerce] configuratie te wijzigen.

## Caching terminologie

[!DNL Commerce] gebruikt de volgende terminologie in cache:

- **Frontend** - Gelijkaardig aan een interface of een gateway aan geheim voorgeheugenopslag, die door [ Magento\Framework\Cache\Frontend ](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Frontend) wordt uitgevoerd.
- **types van Geheime voorgeheugen** - kan één van de types zijn die van [!DNL Commerce] worden voorzien of u kunt [ uw eigen ](https://developer.adobe.com/commerce/php/development/cache/partial/cache-type/) creëren.
- **Achtergrond** - specificeert details over [ geheim voorgeheugenopslag ](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html), die door [ Magento\Framework\Cache\Backend ](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Cache/Backend) wordt uitgevoerd
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
>Voor vernis hoeft de configuratie van [!DNL Commerce] niet te worden gewijzigd. Zie [ vormen en gebruiken Vierkant ](config-varnish.md).
