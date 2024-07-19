---
title: Redis gebruiken voor sessieopslag
description: Leer hoe u Redis voor sessieopslag configureert.
feature: Configuration, Cache
exl-id: f93f500d-65b0-4788-96ab-f1c3d2d40a38
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 1%

---

# Redis gebruiken voor sessieopslag

>[!IMPORTANT]
>
>U moet [ Redis ](config-redis.md#install-redis) installeren alvorens verder te gaan.


Commerce biedt nu opdrachtregelopties voor het configureren van Redis-sessieopslag. In vorige versies hebt u het bestand `<Commerce install dir>app/etc/env.php` bewerkt. De opdrachtregel biedt validatie en dit is de aanbevolen configuratiemethode, maar u kunt het `env.php` -bestand wel bewerken.

Voer de opdracht `setup:config:set` uit en geef Redis-specifieke parameters op.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

waar

`--session-save=redis` schakelt de opslag van Redis-sessies in. Laat deze parameter weg als deze functie reeds is toegelaten.

`--session-save-redis-<parameter_name>=<parameter_value>` is een lijst van parameter/waardeparen die zittingsopslag vormen:

| Opdrachtregelparameter | Parameternaam | Betekenis | Standaardwaarde |
|--- |--- |--- |--- |
| session-save-redis-host | host | Volledig - gekwalificeerde hostname, IP adres, of absolute weg als het gebruiken van de contactdozen van UNIX. | localhost |
| session-save-redis-port | poort | Redis server listen port. | 6379 |
| session-save-redis-password | password | Hiermee geeft u een wachtwoord op als uw Redis-server verificatie vereist. | leeg |
| session-save-redis-timeout | timeout | Time-out verbinding, in seconden. | 2,5 |
| session-save-redis-persistent-id | persistent_identifier | Unieke tekenreeks om permanente verbindingen in te schakelen (bijvoorbeeld sess-db0).<br>[ Bekende kwesties met phpredis en php-fpm ](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | database | Uniek Redis-databasenummer, dat wordt aanbevolen om te beschermen tegen gegevensverlies.<br><br>**Belangrijk**: Als u Redis voor meer dan één type van caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaard cachedatabasenummer aan 0, het databasenummer voor het in cache plaatsen van pagina&#39;s aan 1 en het databasenummer voor de sessieopslag aan 2 toe te wijzen. | 0 |
| session-save-hers-compression-threshold | compression_threshold | Stel de waarde in op 0 om compressie uit te schakelen (aanbevolen bij `suhosin.session.encrypt = On`).<br>[ Bekende kwestie met koorden van meer dan 64 KB ](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048 |
| session-save-redis-compression-lib | compression_library | Opties: gzip, lzf, lz4 of snappy. | gzip |
| session-save-redis-log-level | log_level | Stel de volgende waarden in op een van de volgende volgorde, van minimale breedtegraad tot breedste breedte:<ul><li>0 (noodsituatie: alleen de ernstigste fouten)<li>1 (waarschuwing: onmiddellijke actie vereist)<li>2 (kritiek: toepassingscomponent niet beschikbaar)<li>3 (fout: fouten bij uitvoering, niet kritiek, maar moet worden gecontroleerd)<li>4 (waarschuwing: aanvullende informatie, aanbevolen)<li>5 (mededeling: normale maar significante toestand)<li>6 (info: informatieve berichten)<li>7 (foutopsporing: de meeste informatie die u alleen kunt ontwikkelen of testen)</ul> | 1 |
| session-save-redis-max-gelijktijdige | max_concurrency | Maximum aantal processen dat op een slot op één zitting kan wachten. Voor grote productieclusters stelt u dit in op ten minste 10% van het aantal PHP-processen. | 6 |
| session-save-break-after-frontend | break_after_frontend | Aantal seconden dat moet worden gewacht voordat wordt geprobeerd de vergrendeling voor de voorste (dat wil zeggen: storefront) sessie te verbreken. | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | Aantal seconden dat moet worden gewacht voordat wordt geprobeerd de vergrendeling te verbreken voor een beheersessie (dat wil zeggen Admin). | 30 |
| session-save-redis-first-life | first_life | De levensduur, in seconden, van de sessie voor niet-bots bij de eerste schrijfbewerking, of gebruik 0 om uit te schakelen. | 600 |
| session-save-redis-bot-first-life | bot_first_life | Het leven, in seconden, van zitting voor bots op eerste schrijft, of gebruik 0 om onbruikbaar te maken. | 60 |
| session-save-redis-bot-Tijdens | bot_life | Het leven, in seconden, van zitting voor bots bij het verdere schrijven, of gebruik 0 om onbruikbaar te maken. | 7200 |
| session-save-redis-disable-locking | disable_locking | Sessievergrendeling volledig uitschakelen. | 0 (false) |
| session-save-redis-min-life | min_life | Minimale sessielevensduur, in seconden. | 60 |
| session-save-redis-max-life | max_life | Maximale sessielevensduur, in seconden. | 2592000 (720 uur) |
| session-save-redis-sentinel-master | sentinel_master | Redis Sentinel Master Name | leeg |
| session-save-redis-sentinel-servers | sentinel_servers | Lijst met Redis Sentinel-servers, gescheiden door komma&#39;s | leeg |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | Redis Sentinel-masterstatusvlag verifiëren | 0 (false) |
| session-save-redis-sentinel-connect-retry | sentinel_connect_retry | Verbindingspogingen voor verklikkers | 5 |

## Voorbeeld

In het volgende voorbeeld wordt Redis ingesteld als opslaglocatie voor sessiegegevens, wordt de host ingesteld op `127.0.0.1` , wordt het logniveau ingesteld op 4 en wordt het databasenummer ingesteld op 2. Alle andere parameters worden ingesteld op de standaardwaarde.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Resultaat

Commerce voegt soortgelijke regels toe aan `<magento_root>app/etc/env.php` :

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>TTL voor zittingsverslagen gebruikt de waarde voor het Leven van het Koekje, dat in Admin wordt gevormd. Als de Levensduur van het Koekje aan 0 wordt geplaatst (het gebrek is 3600), dan verlopen de zittingen Redis in het aantal seconden die in min_life worden gespecificeerd (het gebrek is 60). Deze discrepantie is toe te schrijven aan verschillen in de manier waarop Redis en zittingskoekjes een levenwaarde van 0 interpreteren. Als dat gedrag niet gewenst is, verhoog de waarde van min_life.

## Redis-verbinding verifiëren

Om te verifiëren dat Redis en Commerce samenwerken, login aan de server die Redis in werking stelt, een terminal openen, en Redis monitorbevel gebruiken of pingel bevel.

### Redis-monitor, opdracht

```bash
redis-cli monitor
```

Voorbeeld van sessieopslaguitvoer:

```
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Redis, ping, opdracht

```bash
redis-cli ping
```

`PONG` moet de reactie zijn.

Als beide opdrachten zijn uitgevoerd, wordt Redis op de juiste wijze ingesteld.

### Gecomprimeerde gegevens controleren

Om de samengeperste gegevens van de Zitting en het Geheime voorgeheugen van de Pagina te inspecteren, [ RESP.app ](https://flathub.org/apps/details/app.resp.RESP) steunt de automatische decompressie van Commerce 2 Sessie en het geheime voorgeheugen van de Pagina en toont PHP zittingsgegevens in een mens-leesbare vorm.
