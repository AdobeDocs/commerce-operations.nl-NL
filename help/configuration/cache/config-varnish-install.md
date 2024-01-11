---
title: Varnish installeren
description: Zie advies over het installeren van Varnish.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Varnish installeren

Het installeren van de Varnish software is voorbij het werkingsgebied van deze gids. Zie voor meer informatie over het installeren van Varnish:

- [installatiegids](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Vernis-installatiehulplijnen](https://www.varnish-cache.org/docs)
- [Varnish (Tecmint) installeren](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

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

Controleer of [Adobe Commerce en Magento Open Source](../../installation/system-requirements.md) de geïnstalleerde versie van Varnish alvorens verder te gaan. Als u een niet-ondersteunde versie uitvoert, moet u een upgrade uitvoeren naar een ondersteunde versie. Raadpleeg de documentatie bij de Varnish-installatie voor meer informatie.
