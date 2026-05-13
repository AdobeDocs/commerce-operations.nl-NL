---
title: Opnieuw installeren en instellen
description: Leer hoe u Redis voor caching en sessieopslag met Adobe Commerce installeert en configureert. Ontdek opties voor optimalisatie en prestaties afstemmen.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: de613310ad701dd594a6ee8fcd973aa2c3769870
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Redis installeren en instellen

Redis is een opslagplaats voor gegevens in het geheugen die kan worden gebruikt als achterkant van het cachegeheugen en voor sessieopslag. Belangrijkste kenmerken zijn:

- PHP-sessieopslag
- Cache opruimen op basis van tags zonder loops van `foreach`
- Opslaan op schijf en replicatie van hoofd/slave

## Redis installeren

De Redis-software installeren en configureren valt buiten het bereik van deze handleiding. Bronnen raadplegen, zoals:

- [Redis-pagina downloaden](https://redis.io/download)
- [Snelle start opnieuw dis](https://redis.io/docs/latest/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Documentatiepagina Redis](https://redis.io/docs)

## Redis-configuratie instellen

Afhankelijk van uw installatie, kunt u uw configuratie van Redis gewoonlijk in één van de volgende dossiers vinden: `/etc/redis/redis.conf` of `/etc/redis/<port>.conf`

Als u de Redis-instantie naar wens wilt optimaliseren, krijgt u de beste resultaten door een speciale instantie voor elke sessie, Commerce-cache en FPC te gebruiken.

Voor sessies raadt Adobe u aan de persistentie in te schakelen om Redis-gegevens naar schijf te kopiëren met een van de volgende persistentieopties: reguliere Redis Database Backup (RDB)-momentopnamen of AOF-persistentielogboeken (Only File).

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
