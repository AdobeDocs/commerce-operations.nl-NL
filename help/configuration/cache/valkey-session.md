---
title: Valkey gebruiken voor sessieopslag
description: Leer hoe u Valkey voor sessieopslag configureert.
feature: Configuration, Cache
source-git-commit: 1850301e0b7f1abbc54613209940dd63d16ef145
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 1%

---

# Valkey gebruiken voor sessieopslag

>[!IMPORTANT]
>
>U moet [ Valkey ](config-valkey.md#install-valkey) installeren alvorens verder te gaan.

Adobe Commerce biedt opdrachtregelopties voor het configureren van de opslag van Valkey-sessies.

Voer de opdracht `setup:config:set` uit en geef specifieke parameters voor Valkey op.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-<parameter_name>=<parameter_value>...
```

- `--session-save=valkey` schakelt opslag van Valkey-sessies in. Laat deze parameter weg als deze functie reeds wordt toegelaten.

- `--session-save-valkey-<parameter_name>=<parameter_value>` is een lijst van parameter/waardeparen die zittingsopslag vormen:

| Opdrachtregelparameter | Parameternaam | Betekenis | Standaardwaarde |
|----------------------------------------------|--- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--- |
| session-save-valkey-host | host | Volledig - gekwalificeerde hostname, IP adres, of absolute weg als het gebruiken van de contactdozen van UNIX. | localhost |
| session-save-valkey-port | poort | De luisterpoort van de Valkey-server. | 6379 |
| session-save-valkey-password | password | Hiermee geeft u een wachtwoord op als uw Valkey-server verificatie vereist. | leeg |
| session-save-valkey-timeout | timeout | Time-out verbinding, in seconden. | 2,5 |
| session-save-valkey-persistent-id | persistent_identifier | Unieke tekenreeks om permanente verbindingen in te schakelen (bijvoorbeeld sess-db0).<br>[ Bekende kwesties met phpredis en php-fpm ](https://github.com/phpredis/phpredis/issues/70). |
| session-save-valkey-db | database | Uniek Valkey-databasenummer, dat wordt aanbevolen om te beschermen tegen gegevensverlies.<br><br>**Belangrijk**: Als u Valkey voor meer dan één type van caching gebruikt, moeten de gegevensbestandaantallen verschillend zijn. U wordt aangeraden het standaarddatabasenummer voor caching toe te wijzen aan `0` , het databasenummer voor het in cache plaatsen van pagina&#39;s aan `1` en het databasenummer voor sessieopslag aan `2` . | 0 |
| session-save-valkey-compression-threshold | compression_threshold | Stel in op `0` om compressie uit te schakelen (aanbevolen bij `suhosin.session.encrypt = On` ). | 2048 |
| session-save-valkey-compression-lib | compression_library | Opties: gzip, lzf, lz4 of snappy. | gzip |
| session-save-valkey-log-level | log_level | Stel de volgende waarden in op een van de volgende volgorde, van minimale breedtegraad tot breedste breedte:<ul><li>0 (noodsituatie: alleen de ernstigste fouten)<li>1 (waarschuwing: onmiddellijke actie vereist)<li>2 (kritiek: toepassingscomponent niet beschikbaar)<li>3 (fout: fouten bij uitvoering, niet kritiek, maar moet worden gecontroleerd)<li>4 (waarschuwing: aanvullende informatie, aanbevolen)<li>5 (mededeling: normale maar significante toestand)<li>6 (info: informatieve berichten)<li>7 (foutopsporing: de meeste informatie die u alleen kunt ontwikkelen of testen)</ul> | 1 |
| session-save-valkey-max-gelijktijdige | max_concurrency | Maximum aantal processen dat op een slot op één zitting kan wachten. Voor grote productieclusters stelt u dit in op ten minste 10% van het aantal PHP-processen. | 6 |
| session-save-valkey-break-after-frontend | break_after_frontend | Aantal seconden dat moet worden gewacht voordat wordt geprobeerd de vergrendeling voor de voorste (dat wil zeggen: storefront) sessie te verbreken. | 5 |
| session-save-valkey-break-after-adminhtml | break_after_adminhtml | Aantal seconden dat moet worden gewacht voordat wordt geprobeerd de vergrendeling te verbreken voor een beheersessie (dat wil zeggen Admin). | 30 |
| session-save-valkey-first-life | first_life | De levensduur, in seconden, van de sessie voor niet-bots bij de eerste schrijfbewerking of gebruik `0` om deze uit te schakelen. | 600 |
| session-save-valkey-bot-first-life | bot_first_life | Levensduur, in seconden, van sessie voor bots bij eerste schrijven of gebruik `0` om uit te schakelen. | 60 |
| session-save-valkey-bot-Tijdens | bot_life | Het leven, in seconden, van zitting voor bots bij volgende schrijft, of gebruik `0` om onbruikbaar te maken. | 7200 |
| session-save-valkey-disable-locking | disable_locking | Sessievergrendeling volledig uitschakelen. | 0 (false) |
| session-save-valkey-min-life | min_life | Minimale sessielevensduur, in seconden. | 60 |
| session-save-valkey-max-life | max_life | Maximale sessielevensduur, in seconden. | 2592000 (720 uur) |
| session-save-valkey-sentinel-master | sentinel_master | Valkey Sentinel master name. | leeg |
| session-save-valkey-sentinel-servers | sentinel_servers | Lijst met Valkey Sentinel-servers, gescheiden door komma&#39;s. | leeg |
| session-save-valkey-sentinel-verify-master | sentinel_verify_master | Verifieer Valkey Sentinel master statusvlag. | 0 (false) |
| session-save-valkey-sentinel-connect-retry | sentinel_connect_retry | De verbinding probeert opnieuw voor verklikkers. | 5 |

## Voorbeeld

In het volgende voorbeeld wordt Valkey ingesteld als de opslag van sessiegegevens, wordt de host ingesteld op `127.0.0.1` , wordt het logniveau ingesteld op `4` en wordt het databasenummer ingesteld op `2` . Alle andere parameters worden ingesteld op de standaardwaarde.

```bash
bin/magento setup:config:set --session-save=valkey --session-save-valkey-host=127.0.0.1 --session-save-valkey-log-level=4 --session-save-valkey-db=2
```

### Resultaat

Commerce voegt soortgelijke regels toe aan `<magento_root>app/etc/env.php` :

```php
'session' => [
    'save' => 'valkey',
    'redis' => [
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
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>TTL voor zittingsverslagen gebruikt de waarde voor het Leven van het Koekje, dat in Admin wordt gevormd. Als Cookie Lifetime is ingesteld op `0` (de standaardwaarde is `3600` ), verlopen Valkey-sessies binnen het aantal seconden dat is opgegeven in min_life (de standaardwaarde is `60` ). Deze discrepantie is het gevolg van verschillen in de manier waarop valkey- en sessiecookies een levensduurwaarde van `0` interpreteren. Als dat gedrag niet gewenst is, verhoog de waarde van min_life.

## Valkeyverbinding verifiëren

Als u wilt controleren of Valkey en Commerce goed samenwerken, meldt u zich aan bij de server waarop Valkey wordt uitgevoerd, opent u een terminal en gebruikt u de opdracht `valkey-cli monitor` of `redis-cli ping` .

### Valkey, opdracht

```bash
valkey-cli monitor
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

### Valkey, ping, opdracht

```bash
valkey-cli ping
```

De verwachte reactie is: `PONG`.

Als beide opdrachten zijn uitgevoerd, wordt Valkey op de juiste wijze ingesteld.

### Gecomprimeerde gegevens controleren

Om samengeperste zittingsgegevens en het paginacachegeheugen te inspecteren, [ RESP.app ](https://flathub.org/apps/app.resp.RESP) steunt automatische decompressie van Commerce 2 zitting en paginacache en toont PHP zittingsgegevens in een mens-leesbaar formaat.
