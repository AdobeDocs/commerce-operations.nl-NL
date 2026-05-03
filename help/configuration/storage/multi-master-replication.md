---
title: Database-replicatie
description: Meer informatie over de voordelen van replicatie van databases voor Adobe Commerce, zoals back-up, offload van analysemogelijkheden en asynchrone MySQL-slave-configuratie.
recommendations: noCatalog
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: 41b8d77793f1c24f08ff7e6a2d35826a62477534
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 0%

---

# Database-replicatie

{{ee-only}}

{{deprecate-split-db}}

De replicatie van het gegevensbestand van de vestiging verstrekt de volgende voordelen:

- Biedt gegevensback-up
- Hiermee wordt gegevensanalyse ingeschakeld zonder dat dit van invloed is op de hoofddatabase
- Schaalbaarheid

MySQL-databases worden asynchroon gerepliceerd. Dit betekent dat slaven niet permanent hoeven te zijn verbonden om updates van de master te ontvangen.

## Database-replicatie configureren

Een diepgaande bespreking van gegevensbestandreplicatie is voorbij het werkingsgebied van deze gids. Als u dit wilt instellen, kunt u een bron raadplegen zoals:

- [MySQL-documentatie](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Masterslave-replicatie instellen in MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce biedt voorbeelden van MySQL-configuraties voor uw slave-databases. Een eenvoudige configuratie wordt geleverd bij de `ResourceConnections` -klasse `README.md` .

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

Om de prestaties van master-slave replicatie te verbeteren, kunt u sommige lijsten op slave instanties filtreren. U wordt aangeraden alle tijdelijke tabellen met een naampatroon `search\_tmp\_%` te filteren die worden gebruikt voor het zoeken naar catalogi.

Hiervoor voegt u de volgende regel toe aan uw `my.cnf` -bestand op uw slave-instanties:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
