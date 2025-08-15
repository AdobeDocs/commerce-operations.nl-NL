---
title: Aanbevolen procedures voor Valkey-serviceconfiguratie
description: Leer hoe u de prestaties in cache kunt verbeteren met de uitgebreide Valkey-cacheimplementatie voor Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: ca1598b0-07c6-4338-aed1-f2ba05375197
source-git-commit: 1ab977bf2b30c2851609f0bfcc636978e974f07a
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Aanbevolen procedures voor Valkey-serviceconfiguratie

Adobe raadt de volgende aanbevolen procedures aan bij het configureren van de service Valkey:

## Valkey L2-cache configureren

Configureer de Valkey L2-cache door de `VALKEY_BACKEND` -implementatievariabele in te stellen in het `.magento.env.yaml` -configuratiebestand.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Voor milieuconfiguratie op de infrastructuur van de Wolk, zie [`VALKEY_BACKEND` ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) in _Commerce op de Gids van de Infrastructuur van de Wolk_.

Voor installaties op-gebouw, zie [ Valkey pagina caching ](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) in de _Gids van de Configuratie_ vormen.

>[!NOTE]
>
>Controleer of u de nieuwste versie van het pakket `ece-tools` gebruikt. Als niet, [ verbetering aan de recentste versie ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). U kunt de versie controleren die in uw lokale omgeving is geïnstalleerd met de opdracht `composer show magento/ece-tools` CLI.

### Grootte van L2-cachegeheugen (Adobe Commerce Cloud)

L2 geheim voorgeheugen gebruikt a [ tijdelijk dossiersysteem ](https://en.wikipedia.org/wiki/Tmpfs) als opslagmechanisme. Vergeleken met gespecialiseerde toetsensetensystemen, heeft een tijdelijk dossiersysteem geen zeer belangrijk uitzettingsbeleid om geheugengebruik te controleren.

Het gebrek aan controle van het geheugengebruik kan het L2 geheim voorgeheugengebruik veroorzaken om in tijd te groeien door het oude geheime voorgeheugen te accumuleren.

Om geheugenuitputting van L2 geheim voorgeheugenimplementaties te vermijden, ontruimt Adobe Commerce de opslag wanneer een bepaalde drempel wordt bereikt. De standaardwaarde is 95%.

Het is belangrijk om het maximale gebruik van het L2-cachegeheugen aan te passen op basis van de projectvereisten voor cacheopslag. Gebruik een van de volgende methoden om de grootte van de geheugencache te configureren:

- Maak een ondersteuningsticket om groottewijzigingen van de `/dev/shm` -montage aan te vragen.
- Pas de eigenschap `cleanup_percentage` op toepassingsniveau aan om het maximale vulpercentage van de opslagruimte te beperken. Het resterende vrije geheugen kan door andere diensten worden gebruikt.
U kunt de configuratie in de plaatsingsconfiguratie onder de groep van de geheim voorgeheugenconfiguratie aanpassen `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>De configuratieoptie `cleanup_percentage` is geïntroduceerd in Adobe Commerce 2.4.4.

In het volgende voorbeeld wordt een `CACHE_CONFIGURATION` in het `.magento.env.yaml` -bestand getoond:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

De vereisten van het geheime voorgeheugen kunnen variëren gebaseerd op projectconfiguratie en douanecode van de douanederde. Het bereik van de grootte van het L2-cachegeheugen maakt het mogelijk dat de L2-cache werkt zonder overbodige drempelresultaten.
In het ideale geval zou het geheugengebruik in de L2-cache zich op een bepaald niveau onder de drempelwaarde moeten stabiliseren om te voorkomen dat de opslagcapaciteit vaak wordt gewist.

U kunt het gebruik van het L2 geheime voorgeheugengeheugen op elke knoop van de cluster controleren gebruikend het volgende CLI bevel en dan zoekend naar de `/dev/shm` lijn.
Het gebruik kan over verschillende knopen variëren, maar het zou in de zelfde waarde moeten samenkomen.

```bash
df -h
```

## Enable Valkey slave connection

Schakel een Valkey-slave-verbinding in het `.magento.env.yaml` -configuratiebestand in zodat slechts één knooppunt lees-schrijfverkeer kan verwerken en de andere knooppunten het alleen-lezen verkeer verwerken.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Voor meer details, zie [ VALKEY_USE_SLAVE_CONNECTION ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy.html#valkey_use_slave_connection) in _Commerce op de Gids van de Infrastructuur van de Wolk_.

Voor Adobe Commerce-installaties op locatie configureert u de nieuwe Valkey-casimplementatie met behulp van de `bin/magento:setup` -opdrachten. Voor meer informatie, zie [ Valkey van het Gebruik voor standaardgeheime voorgeheugen ](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) in de _Gids van de Configuratie_.

>[!WARNING]
>
>Vorm __ geen Valkeyslave verbinding voor de projecten van de wolkeninfrastructuur met a [ geschraapte/gespleten architectuur ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture). Dit veroorzaakt verbindingsfouten van Valkey. Voor meer informatie, voor meer informatie, zie de [ Valkey configuratiebegeleiding ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) in _Commerce op de gids van de Infrastructuur van de Wolk_.

## Toetsen vooraf laden

Als u gegevens tussen pagina&#39;s wilt hergebruiken, geeft u de toetsen voor het vooraf laden op in het configuratiebestand van `.magento.env.yaml` .

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Voor installaties op-gebouw, zie [ Valkey preload eigenschap ](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) in de _Gids van de Configuratie_.

## Ophaalcache inschakelen

Verminder vergrendelingswachttijden en verbeter de prestaties, vooral wanneer u met veel Blokken en Cachetoetsen werkt, door een verouderde cache te gebruiken en tegelijkertijd een nieuwe cache te genereren. Schakel het oude cachegeheugen in en definieer cachetypen in het configuratiebestand van `.magento.env.yaml` :

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

>[!NOTE]
>
>In het vorige voorbeeld, is het `full_page` geheime voorgeheugen niet relevant voor Adobe Commerce op de projecten van de wolkeninfrastructuur, omdat zij [ Fastly ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/cdn/fastly) gebruiken.

Voor het vormen van installaties op-gebouw, zie [ het geheim voorgeheugenopties van de Stale ](../../../configuration/cache/level-two-cache.md#stale-cache-options) in de _Gids van de Configuratie_.

Tijdens plaatsing, zou u de volgende lijnen in [ moeten zien bouwen en logboek ](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/test/log-locations.html#build-and-deploy-logs) opstellen:

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## Cachecompressie

Als u meer dan 6 GB Valkey `maxmemory` gebruikt, kunt u cachecompressie gebruiken om de ruimte te verminderen die door de sleutels wordt verbruikt. Houd er rekening mee dat er een compromis is met de prestaties aan de clientzijde. Als je reservekopiecapaciteiten hebt, stelt Adobe voor ze in te schakelen. Zie [ Valkey van het Gebruik voor zittingsopslag ](../../../configuration/cache/valkey-session.md) in de _Gids van de Configuratie_.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```
