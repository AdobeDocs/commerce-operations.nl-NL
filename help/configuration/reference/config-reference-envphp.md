---
title: env.php reference
description: Zie een lijst met waarden voor het bestand env.php.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# env.php reference

Het bestand `env.php` bevat de volgende secties:

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
| `directories` | Toewijzingsinstellingen voor Commerce-directory&#39;s |
| `downloadable_domains` | Lijst met downloadbare domeinen |
| `install` | De installatiedatum |
| `lock` | Providerinstellingen vergrendelen |
| `MAGE_MODE` | De [ toepassingswijze ](../bootstrap/application-modes.md) |
| `queue` | [ de rijen van het Bericht ](../queues/manage-message-queues.md) montages |
| `resource` | Toewijzing van de resourcenaam aan een verbinding |
| `session` | Opslaggegevens sessie |
| `system` | Schakelt het veld voor bewerken in de beheerder uit |
| `x-frame-options` | Het plaatsen voor [ x-kader-opties ][x-frame-options] |

## achterste

Vorm **frontName** voor Commerce admin url gebruikend de `backend` knoop in env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cachegeheugen

Configureer opnieuw pagina en zorg dat de standaardcaching plaatsvindt met het knooppunt `cache` in het `env.php` -bestand.

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

Leer meer in [ Redis Configuratie ](../cache/redis-pg-cache.md).

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

Leer meer over verschillende [ Types van Geheime voorgeheugen ](../cli/manage-cache.md).

## consumer_wait_for_messages

Geef op of consumenten moeten doorgaan met opiniepeilen voor berichten als het aantal verwerkte berichten kleiner is dan de waarde `max_messages` . De standaardwaarde is `1` .

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

De volgende opties zijn beschikbaar:

- `1` - De consumenten blijven berichten van de berichtrij verwerken tot het bereiken van de `max_messages` waarde die in het `env.php` dossier wordt gespecificeerd alvorens de verbinding van TCP te sluiten en het consumentenproces te beëindigen. Als de wachtrij leeg is voordat de waarde `max_messages` wordt bereikt, wacht de consument tot er meer berichten zijn.

  Wij adviseren dit het plaatsen voor grote handelaren omdat een constante berichtstroom wordt verwacht en de vertragingen in verwerking ongewenst zijn.

- `0` - De consumenten verwerken beschikbare berichten in de rij, sluiten de verbinding van TCP, en eindigen. Consumenten wachten niet op extra berichten om de wachtrij in te voeren, zelfs niet als het aantal verwerkte berichten kleiner is dan de `max_messages` -waarde die in het `env.php` -bestand is opgegeven. Dit kan helpen problemen met uitsnijdtaken voorkomen die worden veroorzaakt door lange vertragingen bij de verwerking van de wachtrij met berichten.

  Wij adviseren dit het plaatsen voor kleinere handelaren die geen constante berichtstroom verwachten en verkiezen gegevensverwerkingsmiddelen in ruil voor kleine verwerkingsvertragingen te besparen wanneer er geen berichten voor dagen zouden kunnen zijn.

## kraan

Hiermee schakelt u snijtaken voor de Commerce-toepassing in of uit. Standaard zijn snijtaken ingeschakeld. Als u deze wilt uitschakelen, voegt u de `cron` -configuratie toe aan het `env.php` -bestand en stelt u de waarde in op `0` .

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Wees voorzichtig wanneer u snijtaken uitschakelt. Als ze zijn uitgeschakeld, worden de essentiële processen die door de Commerce-toepassing worden vereist, niet uitgevoerd.

Leer meer over [ Crons ](../cli/configure-cron-jobs.md).

## coderen

Commerce gebruikt een coderingssleutel om wachtwoorden en andere vertrouwelijke gegevens te beschermen. Deze sleutel wordt gegenereerd tijdens het installatieproces.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Leer meer over [ Sleutel van de Encryptie ](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/encryption-key) in de _gids van de Gebruiker van Commerce_.

## db

Alle gegevensbestandconfiguraties zijn beschikbaar in deze knoop.

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

Bepaalt de standaardverbinding voor berichtrijen. De waarde kan `db`, `amqp`, of een systeem van de douanerij zoals `redismq` zijn. Als u een andere waarde dan `db` opgeeft, moet de software voor de wachtrij van berichten eerst worden geïnstalleerd en geconfigureerd. Anders worden berichten niet correct verwerkt.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Als `queue/default_connection` is opgegeven in het systeem `env.php` -bestand, wordt deze verbinding gebruikt voor alle berichtenrijen door het systeem, tenzij een specifieke verbinding is gedefinieerd in een `queue_topology.xml` -, `queue_publisher.xml` - of `queue_consumer.xml` -bestand.
Als `queue/default_connection` bijvoorbeeld `amqp` in `env.php` is maar een `db` -verbinding is opgegeven in de XML-bestanden van de configuratie van de wachtrij van een module, gebruikt de module MySQL als een berichtbroker.

## mappen

De facultatieve opties van de folderafbeelding die moeten worden geplaatst wanneer de Webserver wordt gevormd om Commerce te dienen app van de `/pub` folder voor [ betere veiligheid ](../../installation/tutorials/docroot.md).

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

Leer meer over [ Downloadbare Domeinen ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd).

## installeren

De installatiedatum van de Commerce-toepassing.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## vergrendelen

Instellingen voor vergrendelingsproviders worden geconfigureerd met het knooppunt `lock` .

Leer meer over [ de Configuratie van de Leverancier van het Slot ](../../installation/tutorials/lock-provider.md).

## MAGE_MODE

De opstellen wijze kan in deze knoop worden gevormd.

```conf
'MAGE_MODE' => 'developer'
```

Leer meer over [ toepassingswijzen ](../cli/set-mode.md).

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

Leer meer over [ Rij van het Bericht ][message-queue].

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

Sessieconfiguraties worden opgeslagen in het knooppunt `session` .

```conf
'session' => [
  'save' => 'files'
],
```

Leer meer over [ Zitting ](../storage/sessions.md).

## x-frame-opties

De header x-frame-options kan worden geconfigureerd met dit knooppunt.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Leer meer over [ x-kader-opties ](../security/xframe-options.md).

## systeem

Met dit knooppunt worden de configuratiewaarden in het `env.php` -bestand vergrendeld en wordt het veld in de beheerder uitgeschakeld.

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

Leer meer in [ env-php-config-reeks ](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
