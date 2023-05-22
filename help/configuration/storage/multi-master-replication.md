---
title: Database-replicatie
description: Zie de voordelen van het vormen van gegevensbestandreplicatie.
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Database-replicatie

{{ee-only}}

{{deprecate-split-db}}

De replicatie van het gegevensbestand van de vestiging verstrekt de volgende voordelen:

- Biedt gegevensback-up
- Hiermee wordt gegevensanalyse ingeschakeld zonder dat dit van invloed is op de master database
- Schaalbaarheid

MySQL-databases worden asynchroon gerepliceerd. Dit betekent dat slaven niet permanent hoeven te zijn verbonden om updates van de master databases te ontvangen.

## Database-replicatie configureren

Een diepgaande bespreking van gegevensbestandreplicatie is voorbij het werkingsgebied van deze gids. Als u dit wilt instellen, kunt u een bron raadplegen zoals:

- [MySQL-documentatie](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Master slave-replicatie instellen in MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

De handel verstrekt steekproefMySQL configuraties voor uw slave gegevensbestanden. Een eenvoudige configuratie wordt verstrekt met `ResourceConnections` class `README.md`.

Het volgende is geavanceerder en wordt slechts ter informatie verstrekt:

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## Prestatieverbetering

Om de prestaties van master-slave replicatie te verbeteren, kunt u sommige lijsten op slave instanties filtreren. We raden u aan alle tijdelijke tabellen te filteren met een naampatroon `search\_tmp\_%` die worden gebruikt voor het zoeken naar catalogi.

Hiervoor voegt u de volgende regel toe aan uw `my.cnf` bestand op uw slave-exemplaren:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
