---
title: Redis configureren
description: Bekijk een overzicht van de functies van Redis en start de configuratie van Redis.
source-git-commit: 5c0d285717a79d654af769cb734ec385d2d4046f
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Redis configureren

Tot de volgende functies behoren:

- PHP-sessieopslag
- Cache opruimen op basis van tags zonder `foreach` lussen
- Opslaan op schijf en master/slave-replicatie

## Redis installeren

De Redis-software installeren en configureren valt buiten het bereik van deze handleiding. Bronnen raadplegen, zoals:

- [Redis-pagina downloaden](https://redis.io/download)
- [Snelle start opnieuw dis](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Documentatiepagina Redis](https://redis.io/docs)

## Redis-configuratie instellen

Afhankelijk van de installatie kunt u de Redis-configuratie meestal in een van de volgende bestanden vinden: `/etc/redis/redis.conf` of `/etc/redis/<port>.conf`

Om Redis instantie voor uw vereisten te optimaliseren, krijgt u beste resultaten door een specifieke instantie voor elke zitting, het geheime voorgeheugen van de Handel en FPC te gebruiken.

Voor sessies raadt Adobe u aan de persistentie in te schakelen om Redis-gegevens naar schijf te kopiëren met een van de volgende persistentieopties: reguliere Redis Database Backup (RDB)-momentopnamen of AOF-persistentielogboeken (Only File).

- **Back-up van database opnieuw instellen** (RDB) de momentopnamen slaan het volledige gegevensbestand in een stortplaatsdossier na een bepaalde tijd op, wanneer een minimum aantal sleutels sinds laatste sparen zijn veranderd. Gebruik de `save` instellen in het dialoogvenster `redis.conf` bestand om deze instelling te configureren.

- **Alleen bestand toevoegen** (AOF) slaat elke schrijfbewerking die naar Redis is verzonden op in een dagboekbestand. Redis leest dit dossier bij nieuw begin slechts en gebruikt het om de originele dataset te herstellen.

U kunt zowel de opties RDB als AOF tegelijkertijd inschakelen. Zie voor meer informatie, waaronder de voor- en nadelen van de opties voor persistentie [Redis Persistence-documentatie](https://redis.io/topics/persistence).

Voor de geheim voorgeheugeninstantie, opstelling de instantie zodat het groot genoeg is om uw volledige geheime voorgeheugen van de Handel op te slaan. De groottevereisten zijn afhankelijk van verschillende factoren, zoals het aantal producten en de winkelweergave. Als uitgangspunt kunt u de grootte van de cachemap op uw bestandssysteem gebruiken. Als de `var/cache` De map op uw bestandssysteem is 5 GB. Stel uw Redis-exemplaar in met ten minste 5 GB om te starten. Persistence is not required for the cache instance because the Commerce cache can be restore. Zie [Cache-hulplijn opnieuw weergeven](https://redis.io/docs/manual/eviction/).

Voor het afstemmen van de prestaties kunt u ook de volgende instellingen inschakelen voor asynchrone verwijdering. Deze instellingen veranderen het gedrag van Redis niet. Zie ook [redis news](http://antirez.com/news/93) voor meer informatie over asynchrone verwijdering.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

Bij Redis 6.x en hoger kunt u ook de volgende waarde toevoegen:

```ini
lazyfree-lazy-user-del yes
```
