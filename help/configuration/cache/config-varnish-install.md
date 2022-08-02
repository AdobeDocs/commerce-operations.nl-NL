---
title: Varnish installeren
description: Zie advies over het installeren van Varnish.
source-git-commit: 688db9fcc9cd196d1560e49719b03ef32d13870d
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# Varnish installeren

Het installeren van de Varnish software is voorbij het werkingsgebied van deze gids. Zie voor meer informatie over het installeren van Varnish:

- [installatiewiki](http://wiki.mikejung.biz/Varnish)
- [Vernis-installatiehulplijnen](https://www.varnish-cache.org/docs)
- [Varnish (Tecmint) installeren](http://www.tecmint.com/install-varnish-cache-web-accelerator)

>[!INFO]
>
>Dit onderwerp is geschreven voor Varnish op CentOS en Apache 2.4. Als u Varnish in een verschillende omgeving instelt, zijn sommige opdrachten waarschijnlijk anders. Raadpleeg de voorgaande documentatie voor meer informatie.
>
>Als u Varnish modules (vmods), zoals saint wijze wilt installeren, zou u Varnish door de code te compileren moeten installeren, eerder dan installerend van een pakket. Zie [Sint-modus](config-varnish-advanced.md#saint-mode) voor meer informatie .

## Vierige versie bevestigen

Open een terminal en voer de volgende opdracht in om de versie van Varnish weer te geven:

```bash
varnishd -V
```

Hieronder volgt een monster:

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

Zorg ervoor dat de versie 6.x is voordat u doorgaat. Als u versie lager dan 6.x uitvoert, moet u een upgrade naar een ondersteunde versie uitvoeren. Raadpleeg de documentatie bij de Varnish-installatie voor meer informatie.
