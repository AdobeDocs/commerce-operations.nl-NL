---
title: De databaseanalyse configureren
description: Zie een voorbeeld van hoe te om output voor gegevensbestand te vormen profiler.
feature: Configuration, Storage
badge: label="Bijgedragen door Atish Goswami" type="Informative" url="https://github.com/atishgoswami" tooltip="Atish Goswami"
exl-id: 87780db5-6e50-4ebb-9591-0cf22ab39af5
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# De databaseanalyse configureren

De Commerce-databaseanalyse geeft alle query&#39;s weer die op een pagina zijn geïmplementeerd, inclusief de tijd voor elke query en de parameters die zijn toegepast.

## Stap 1: Wijzig de plaatsingsconfiguratie

Wijzig `<magento_root>/app/etc/env.php` om de volgende verwijzing naar de [ klasse van gegevensbestandanalyse ](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/DB/Profiler.php) toe te voegen:

```php?start_inline=1
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
```

Hier volgt een voorbeeld:

```php?start_inline=1
 'db' =>
  array (
    'table_prefix' => '',
    'connection' =>
    array (
      'default' =>
      array (
        'host' => 'localhost',
        'dbname' => 'magento',
        'username' => 'magento',
        'password' => 'magento',
        'model' => 'mysql4',
        'engine' => 'innodb',
        'initStatements' => 'SET NAMES utf8;',
        'active' => '1',
        'profiler' => [
            'class' => '\Magento\Framework\DB\Profiler',
            'enabled' => true,
        ],
      ),
    ),
  ),
```

## Stap 2: Vorm de output

Configureer de uitvoer in het opstartbestand van de Commerce-toepassing. Dit kan `<magento_root>/pub/index.php` zijn of zich bevinden in een virtuele hostconfiguratie van de webserver.

In het volgende voorbeeld worden de resultaten in een tabel met drie kolommen weergegeven:

- Totale tijd (geeft de totale hoeveelheid tijd weer om alle query&#39;s op de pagina uit te voeren)
- SQL (toont alle SQL vragen; de rijkopbal toont de telling van vragen)
- De Params van de vraag (toont de parameters voor elke SQL vraag)

Als u de uitvoer wilt configureren, voegt u de volgende code toe na de regel `$bootstrap->run($app);` in het opstartbestand:

```php?start_inline=1
/** @var \Magento\Framework\App\ResourceConnection $res */
$res = \Magento\Framework\App\ObjectManager::getInstance()->get('Magento\Framework\App\ResourceConnection');
/** @var Magento\Framework\DB\Profiler $profiler */
$profiler = $res->getConnection('read')->getProfiler();
echo "<table cellpadding='0' cellspacing='0' border='1'>";
echo "<tr>";
echo "<th>Time <br/>[Total Time: ".$profiler->getTotalElapsedSecs()." secs]</th>";
echo "<th>SQL [Total: ".$profiler->getTotalNumQueries()." queries]</th>";
echo "<th>Query Params</th>";
echo "</tr>";
foreach ($profiler->getQueryProfiles() as $query) {
    /** @var Zend_Db_Profiler_Query $query*/
    echo '<tr>';
    echo '<td>', number_format(1000 * $query->getElapsedSecs(), 2), 'ms', '</td>';
    echo '<td>', $query->getQuery(), '</td>';
    echo '<td>', json_encode($query->getQueryParams()), '</td>';
    echo '</tr>';
}
echo "</table>";
```

## Stap 3: de resultaten bekijken

Ga naar een willekeurige pagina in uw winkel of Admin om de resultaten weer te geven. Hieronder volgt een monster:

![ Resultaten van het gegevensbestandanalyse van de Steekproef ](../../assets/configuration/db-profiler-results.png)
