---
title: Valkey configureren
description: Bekijk een overzicht van Valkey-functies en start de Valkey-configuratie.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: b2cf71bfda3e5db8e27eb28d764cf99216454e33
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# Valkey configureren

Voorbeelden van geldige functies zijn:

- PHP-sessieopslag
- Cache opruimen op basis van tags zonder loops van `foreach`
- Opslaan op schijf en replicatie van hoofd/slave

## Valkey installeren

Raadpleeg de volgende bronnen voor installatie en configuratie van de Valkey-software:

- [ Download Valkey pagina ](https://valkey.io/download/)
- [ Valkey snel begin ](https://valkey.io/topics/quickstart/)
- [ Valkey documentatiepagina ](https://valkey.io/docs)

## Valkey-configuratie instellen

Afhankelijk van de installatie vindt u de Valkey-configuratie meestal in het `/etc/valkey/valkey.conf` -bestand of in het `/etc/valkey/<port>.conf` -bestand.

Als u de Valkey-instantie naar wens wilt optimaliseren, bereikt u de beste resultaten met een speciale instantie voor elke sessie, Commerce-cache en FPC.

Adobe raadt aan dat tijdens sessies geldige gegevens naar de schijf worden gekopieerd. U kunt resp. Valkey Database Backup (RDB)-momentopnamen of AOF-persistentielogboeken (Only File) gebruiken.

- **RDB** (Valkey Gegevensbestand) momentopnamen slaan het volledige gegevensbestand in een stortplaatsdossier na een bepaalde tijd op, wanneer een minimumaantal sleutels sinds laatste sparen zijn veranderd. Gebruik de instelling `save` in het `valkey.conf` -bestand om deze instelling te configureren.

- **voegt slechts Dossier** (AOF) toe slaat elke schrijfverrichting die naar Valkey in een dagboekdossier wordt verzonden op. Valkey leest dit dossier bij nieuw begin slechts en gebruikt het om de originele dataset te herstellen.

U kunt zowel de opties RDB als AOF tegelijkertijd inschakelen. Voor extra details met inbegrip van de voordelen en de nadelen van de persistentieopties, zie de [ documentatie van de Persistentie van de Sleutel ](https://valkey.io/topics/persistence/).

Voor de cacheinstantie moet u de instantie zo instellen dat deze groot genoeg is om de gehele Commerce-cache op te slaan. De groottevereisten zijn afhankelijk van verschillende factoren, zoals het aantal producten en de winkelweergave. Als uitgangspunt kunt u de grootte van de cachemap op uw bestandssysteem gebruiken. Als de map `var/cache` op uw bestandssysteem bijvoorbeeld 5 GB is, stelt u de instantie Valkey in met ten minste 5 GB om te starten. Voor de cacheinstantie is persistentie niet vereist omdat de Commerce-cache kan worden hersteld.

Voor het afstemmen van de prestaties kunt u de volgende instellingen inschakelen voor asynchrone verwijdering. Deze instellingen veranderen het gedrag van Valkey niet.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
