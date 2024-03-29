---
title: Redis configureren
description: Bekijk een overzicht van de functies van Redis en start de configuratie van Redis.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Redis configureren

Tot de volgende functies behoren:

- PHP-sessieopslag
- Cache opruimen op basis van tags zonder `foreach` lussen
- Opslaan op schijf en replicatie van hoofd/slave

## Redis installeren

De Redis-software installeren en configureren valt buiten het bereik van deze handleiding. Bronnen raadplegen, zoals:

- [Redis-pagina downloaden](https://redis.io/download)
- [Snelle start opnieuw dis](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Documentatiepagina Redis](https://redis.io/docs)

## Redis-configuratie instellen

Afhankelijk van uw installatie, kunt u uw configuratie van Redis gewoonlijk in één van de volgende dossiers vinden: `/etc/redis/redis.conf` of `/etc/redis/<port>.conf`

Om Redis instantie voor uw vereisten te optimaliseren, krijgt u beste resultaten door een specifieke instantie voor elke zitting, het geheime voorgeheugen van de Handel en FPC te gebruiken.

Voor sessies raadt de Adobe u aan de persistentie in te schakelen om Redis-gegevens naar schijf te kopiëren aan de hand van een van de volgende persistentieopties: gewone RDB-momentopnamen (Redis Database Backup) of AOF-persistentielogboeken (Only File) toevoegen.

- **Back-up van database opnieuw instellen** (RDB) de momentopnamen slaan het volledige gegevensbestand in een stortplaatsdossier na een bepaalde tijd op, wanneer een minimum aantal sleutels sinds laatste sparen zijn veranderd. Gebruik de `save` instellen in het dialoogvenster `redis.conf` bestand om deze instelling te configureren.

- **Alleen bestand toevoegen** (AOF) slaat elke schrijfbewerking die naar Redis is verzonden op in een dagboekbestand. Redis leest dit dossier bij nieuw begin slechts en gebruikt het om de originele dataset te herstellen.

U kunt zowel de opties RDB als AOF tegelijkertijd inschakelen. Zie voor meer informatie, waaronder de voor- en nadelen van de persistentieopties, de [Redis Persistence-documentatie](https://redis.io/topics/persistence).

Voor de geheim voorgeheugeninstantie, opstelling de instantie zodat het groot genoeg is om uw volledige geheime voorgeheugen van de Handel op te slaan. De groottevereisten zijn afhankelijk van verschillende factoren, zoals het aantal producten en de winkelweergave. Als uitgangspunt kunt u de grootte van de cachemap op uw bestandssysteem gebruiken. Als de `var/cache` De map op uw bestandssysteem is 5 GB. Stel uw Redis-exemplaar in met ten minste 5 GB om te starten. Persistence is not required for the cache instance because the Commerce cache can be restore. Zie [Cache-hulplijn opnieuw weergeven](https://redis.io/docs/manual/eviction/).

Voor het afstemmen van de prestaties kunt u de volgende instellingen inschakelen voor asynchrone verwijdering. Deze instellingen veranderen het gedrag van Redis niet.

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
