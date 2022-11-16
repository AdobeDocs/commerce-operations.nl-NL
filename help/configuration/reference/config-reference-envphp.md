---
title: env.php reference
description: Zie een lijst met waarden voor het bestand env.php.
source-git-commit: fe5e16d44213d1864a62230029e9e206eecd1717
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---


# env.php reference

De `env.php` bestand bevat de volgende secties:

| Naam | Beschrijving |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Instellingen voor het gebied Beheer |
| `cache` | Nieuwe pagina en standaardcache configureren |
| `cache_types` | Opslaginstellingen voor cache |
| `consumers_wait_for_messages` | Configureer hoe consumenten berichten uit de wachtrij met berichten verwerken |
| `cron` | De uitsnijdtaken in- of uitschakelen |
| `crypt` | De coderingssleutel voor cryptografische functies |
| `db` | Instellingen voor databaseverbinding |
| `default_connection` | Standaardverbinding voor wachtrij met berichten |
| `directories` | Toewijzingsinstellingen voor directory&#39;s voor handel |
| `downloadable_domains` | Lijst met downloadbare domeinen |
| `install` | De installatiedatum |
| `lock` | Providerinstellingen vergrendelen |
| `MAGE_MODE` | De [toepassingsmodus](../bootstrap/application-modes.md) |
| `queue` | [Berichtenrijen](../queues/manage-message-queues.md) instellingen |
| `resource` | Toewijzing van de resourcenaam aan een verbinding |
| `session` | Opslaggegevens sessie |
| `system` | Schakelt het veld voor bewerken in de beheerder uit |
| `x-frame-options` | Instellen voor [x-frame-opties][x-frame-options] |

## achterste

Configureer de **frontName** voor de admin-URL van de Commerce met behulp van de `backend` knooppunt in env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cachegeheugen

Nieuwe pagina&#39;s en standaardcaching configureren door `cache` knooppunt in `env.php` bestand.

```conf
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
]
```

Meer informatie in [Redis-configuratie](../cache/redis-pg-cache.md).

## cache_types

Alle configuraties van cachetypen zijn beschikbaar bij dit knooppunt.

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

Meer informatie over verschillende [Cachetypen](../cli/manage-cache.md).

## consumer_wait_for_messages

Geef op of consumenten moeten blijven opiniepeilen voor berichten als het aantal verwerkte berichten kleiner is dan `max_messages` waarde. De standaardwaarde is `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

De volgende opties zijn beschikbaar:

- `1`—De consumenten blijven berichten van de berichtrij verwerken tot het bereiken van `max_messages` waarde opgegeven in het dialoogvenster `env.php` dossier alvorens de verbinding van TCP te sluiten en het consumentenproces te beëindigen. Als de wachtrij wordt leeggemaakt voordat de wachtrij wordt bereikt `max_messages` waarde , de consument wacht op meer berichten .

   Wij adviseren dit het plaatsen voor grote handelaren omdat een constante berichtstroom wordt verwacht en de vertragingen in verwerking ongewenst zijn.

- `0`—De consumenten verwerken beschikbare berichten in de rij, sluiten de verbinding van TCP, en eindigen. De consumenten wachten niet op extra berichten om de rij in te gaan, zelfs als het aantal verwerkte berichten minder dan is `max_messages` waarde opgegeven in het dialoogvenster `env.php` bestand. Dit kan helpen problemen met uitsnijdtaken voorkomen die worden veroorzaakt door lange vertragingen bij de verwerking van de wachtrij met berichten.

   Wij adviseren dit het plaatsen voor kleinere handelaren die geen constante berichtstroom verwachten en verkiezen gegevensverwerkingsmiddelen in ruil voor kleine verwerkingsvertragingen te besparen wanneer er geen berichten voor dagen zouden kunnen zijn.

## kraan

Schakel snijtaken voor de toepassing Commerce in of uit. Standaard zijn snijtaken ingeschakeld. Om hen onbruikbaar te maken, voeg toe `cron` aan de `env.php` en stel de waarde in op `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Wees voorzichtig wanneer u snijtaken uitschakelt. Als ze uitgeschakeld zijn, worden essentiële processen die vereist zijn voor de toepassing Commerce niet uitgevoerd.

Meer informatie over [Crons](../cli/configure-cron-jobs.md).

## coderen

De handel gebruikt een encryptiesleutel om wachtwoorden en andere gevoelige gegevens te beschermen. Deze sleutel wordt gegenereerd tijdens het installatieproces.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Meer informatie over [Coderingssleutel](https://docs.magento.com/user-guide/system/encryption-key.html) in de _Handleiding voor commerciële gebruikers_.

## db

Alle databaseconfiguraties zijn beschikbaar in dit knooppunt.

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

Bepaalt de standaardverbinding voor berichtrijen. De waarde kan `db`, `amqp`of een aangepast wachtrijsysteem zoals `redismq`. Als u een andere waarde opgeeft dan `db`, moet de software van de berichtrij eerst worden geïnstalleerd en worden gevormd. Anders worden berichten niet correct verwerkt.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Indien `queue/default_connection` is opgegeven in het systeem `env.php` bestand, wordt deze verbinding gebruikt voor alle berichtrijen door het systeem, tenzij een specifieke verbinding in een `queue_topology.xml`, `queue_publisher.xml` of `queue_consumer.xml` bestand.
Als `queue/default_connection` is `amqp` in `env.php` maar `db` De verbinding wordt gespecificeerd in de dossiers van XML van de rijconfiguratie van een module, zal de module MySQL als berichtbroker gebruiken.

## mappen

Optionele mappingopties voor mappen die moeten worden ingesteld wanneer de webserver is geconfigureerd voor de toepassing Handelsgewijs vanuit de `/pub` map voor [verbeterde beveiliging](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadbaar_domeinen

Een lijst met downloadbare domeinen beschikbaar in dit knooppunt. De extra domeinen kunnen worden toegevoegd, worden verwijderd, of worden vermeld gebruikend bevelen CLI.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

Meer informatie over [Downloadbare domeinen](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## installeren

De installatiedatum van de toepassing Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## vergrendelen

Providerinstellingen vergrendelen worden geconfigureerd met de optie `lock` knooppunt.

Meer informatie over [Configuratie provider vergrendelen](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

De opstellen wijze kan in deze knoop worden gevormd.

```conf
'MAGE_MODE' => 'developer'
```

Meer informatie over [toepassingsmodi](../cli/set-mode.md).

## wachtrij

De de rijconfiguraties van het bericht zijn beschikbaar in deze knoop.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

Meer informatie over [Berichtenwachtrij][message-queue].

## resource

De de configuratiemontages van het middel zijn beschikbaar in deze knoop.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## sessie

Sessieconfiguraties worden opgeslagen in de `session` knooppunt.

```conf
'session' => [
  'save' => 'files'
],
```

Meer informatie over [Sessie](../storage/sessions.md).

## x-frame-opties

De header x-frame-options kan worden geconfigureerd met dit knooppunt.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Meer informatie over [x-frame-opties](../security/xframe-options.md).

## systeem

Gebruikend deze knoop, sluit de Handel de configuratiewaarden in `env.php` en schakelt u het veld in de beheerder uit.

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

Meer informatie in [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
