---
title: In cache geplaatste bestanden voor sessieopslag gebruiken
description: Leer over het gebruiken van gegeheugen voor de zittingsopslag van de Handel.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# In cache geplaatste bestanden voor sessieopslag gebruiken

Het in het geheugen onderbrengen is een algemeen, verdeeld geheugen in het voorgeheugen onderbrengend systeem. Het wordt vaak gebruikt om dynamische database-gedreven websites te versnellen door gegevens en voorwerpen in RAM in het voorgeheugen op te nemen om het aantal tijden te verminderen een externe gegevensbron (zoals een gegevensbestand of API) moet worden gelezen.

Het in geheugen ondergebracht verstrekt een grote haktafel die over veelvoudige machines kan worden verdeeld. Als de tabel vol is, zorgen de invoegingen ervoor dat oudere gegevens worden gewist in de volgorde die het minst recent is gebruikt (LRU). De grootte van deze hash-tabel is vaak erg groot. (Bron: [memcached.org](https://www.memcached.org/))

De handel gebruikt getelegrafeerd voor zittingsopslag maar niet voor pagina caching. Voor het in cache plaatsen van pagina&#39;s raden we aan [Redis](../cache/redis-pg-cache.md) of [Varnish](../cache/config-varnish.md).

**Om Commerce te vormen om in het geheugen ondergebracht te gebruiken**:

1. Openen `<your install dir>/app/etc/env.php` in een teksteditor.
1. Zoek het volgende:

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. Wijzig deze als volgt:

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   in het geheugen ondergebracht heeft facultatieve startparameters die buiten het werkingsgebied van deze gids zijn. Meer informatie hierover vindt u in het dialoogvenster [ingesloten](https://www.php.net/manual/en/memcached.sessions.php) documentatie, broncode en wijzigingen.

1. Ga verder met de volgende sectie.

**Om in het geheugen ondergebrachte werken met de Handel te verifiëren**:

1. Verwijder de inhoud van de volgende directory&#39;s in de installatiemap van Commerce:

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Ga naar een willekeurige pagina in de winkel.

1. Meld u aan bij de beheerder en blader naar meerdere pagina&#39;s.

   Als er geen fouten worden weergegeven, feliciteert u! memcaching werkt! U kunt naar keuze naar in het geheugen opgeslagen gegevens kijken zoals in de volgende stap wordt besproken.

   Als de foutenvertoning (zoals HTTP 500 (de Interne Fout van de Server)), laat ontwikkelaarwijze toe en diagnoseer de kwestie. Zorg ervoor dat de in de cache opgeslagen gegevens worden uitgevoerd, correct zijn geconfigureerd en dat `env.php` heeft geen syntaxisfouten.

1. (Optioneel.) Gebruik Telnet om de in het geheugen ondergebrachte opslag te bekijken.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   De resultaten worden als volgt weergegeven:

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
