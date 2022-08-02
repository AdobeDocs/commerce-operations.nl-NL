---
title: Aanmeldingsinterface
description: Ga aan de slag met de logboekinterface.
source-git-commit: f489c3e68c91c6f2e16bff233cf59472ed684b5c
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Aanmeldingsinterface

Als u met een registreerapparaat wilt gaan werken, moet u een instantie maken van `\Psr\Log\LoggerInterface`. Met deze interface kunt u de volgende functies aanroepen om gegevens naar logbestanden te schrijven:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [kritiek()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [Emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Een manier om dat te doen wordt uitgelegd in de [Logboekdatabaseactiviteit](../logs/database-activity.md) voorbeeld.

Een andere manier:

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

In het voorgaande voorbeeld wordt getoond dat `SomeModel` ontvangt een `\Psr\Log\LoggerInterface` object met constructorinjectie. In een methode `doSomething`, als er een fout is opgetreden, wordt deze bij een methode aangemeld `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) bepaalt acht logboekniveaus (zuivert, info, bericht, waarschuwing, fout, kritiek, alarm, en noodsituatie).
