---
title: Redis configureren
description: Leer hoe u Redis caching configureert voor optimalisatie van de Adobe Commerce-prestaties. Ontdek eigenschappen, opstellingsstappen, en configuratie beste praktijken.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Redis configureren

Tot de volgende functies behoren:

- PHP-sessieopslag
- Cache opruimen op basis van tags zonder loops van `foreach`
- Opslaan op schijf en replicatie van hoofd/slave

## Redis installeren

De Redis-software installeren en configureren valt buiten het bereik van deze handleiding. Bronnen raadplegen, zoals:

- [ Redis pagina van de Download ](https://redis.io/download)
- [ Redis snel begin ](https://redis.io/docs/getting-started/)
- [ DigitalOcean ](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [ Redis documentatiepagina ](https://redis.io/docs)

## Redis-configuratie instellen

Afhankelijk van de installatie kunt u de Redis-configuratie meestal in een van de volgende bestanden vinden: `/etc/redis/redis.conf` of `/etc/redis/<port>.conf`

Als u de Redis-instantie naar wens wilt optimaliseren, krijgt u de beste resultaten door een speciale instantie voor elke sessie, Commerce-cache en FPC te gebruiken.

Voor sessies raadt Adobe aan dat u persistentie inschakelt om Redis-gegevens naar schijf te kopiëren met een van de volgende persistentieopties: gewone momentopnamen van Redis Database Backup (RDB) of persistentielogboeken van Alleen bestand toevoegen (AOF).

- **Redis de Steun van het Gegevensbestand** (RDB) momentopnamen slaan het volledige gegevensbestand in een stortplaatsdossier na een bepaalde tijd op, wanneer een minimumaantal sleutels sinds laatste sparen zijn veranderd. Gebruik de instelling `save` in het `redis.conf` -bestand om deze instelling te configureren.

- **voegt slechts Dossier** (AOF) toe slaat elke schrijfverrichting die naar Redis in een dagboekdossier wordt verzonden op. Redis leest dit dossier bij nieuw begin slechts en gebruikt het om de originele dataset te herstellen.

U kunt zowel de opties RDB als AOF tegelijkertijd inschakelen. Voor extra details met inbegrip van de voordelen en de nadelen van de persistentieopties, zie [ Redis documentatie van de Persistentie ](https://redis.io/topics/persistence).

Voor de cacheinstantie moet u de instantie zo instellen dat deze groot genoeg is om de gehele Commerce-cache op te slaan. De groottevereisten zijn afhankelijk van verschillende factoren, zoals het aantal producten en de winkelweergave. Als uitgangspunt kunt u de grootte van de cachemap op uw bestandssysteem gebruiken. Als de map `var/cache` op uw bestandssysteem bijvoorbeeld 5 GB is, stelt u Redis-instantie in met ten minste 5 GB om te starten. Voor de cacheinstantie is persistentie niet vereist omdat de Commerce-cache kan worden hersteld. Zie [ Redis geheim voorgeheugengids ](https://redis.io/docs/latest/develop/use/).

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
