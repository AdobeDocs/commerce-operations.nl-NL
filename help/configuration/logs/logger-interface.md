---
title: Aanmeldingsinterface
description: Leer hoe u de logboekinterface in Adobe Commerce kunt gebruiken voor aangepaste logboekregistratie. Ontdek implementatie PSR-3 en logboekfuncties.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Aanmeldingsinterface

Als u met een logger wilt gaan werken, moet u een instantie van `\Psr\Log\LoggerInterface` maken. Met deze interface kunt u de volgende functies aanroepen om gegevens naar logbestanden te schrijven:

- [ alarm () ](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [ kritiek () ](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [ zuiveren () ](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [ noodgeval () ](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [ fout () ](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [ info () ](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [ logboek () ](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [ bericht () ](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [ waarschuwing () ](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Één manier om dat te doen wordt verklaard in het [ het gegevensbestandactiviteit van het Logboek ](../logs/database-activity.md) voorbeeld.

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

In het voorgaande voorbeeld wordt getoond dat `SomeModel` een `\Psr\Log\LoggerInterface` -object ontvangt met behulp van een constructorinjectie. Bij een methode `doSomething` wordt een fout gemeld bij een methode `critical` (`$this->logger->critical($e);`).

[ RFC 5424 ](https://datatracker.ietf.org/doc/html/rfc5424) bepaalt acht logboekniveaus (zuivert, info, bericht, waarschuwing, fout, kritiek, alarm, en noodsituatie).
