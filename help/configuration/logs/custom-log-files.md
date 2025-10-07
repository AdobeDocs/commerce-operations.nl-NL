---
title: Naar aangepast logbestand schrijven
description: Leer hoe u aangepaste logbestanden maakt en configureert in Adobe Commerce. Ontdek loggermanagers en douane registrerenimplementatie.
feature: Configuration, Logs
badge: label="Bijgedragen door Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Naar een aangepast logbestand schrijven

De module `Magento\Framework\Logger` bevat de volgende handlerklassen:

| Klasse | Logbestand |
| ----- | -------- |
| [ Magento\Framework\Logger\Handler\Base][base] | - |
| [ Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [ Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [ Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [ Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

U vindt ze mogelijk in de map `lib/internal/Magento/Framework/Logger/Handler` .

U kunt een van de volgende methoden gebruiken om u aan te melden bij een aangepast bestand:

- Een aangepast logbestand instellen in het dialoogvenster `di.xml`
- Een aangepast bestand instellen in de aangepaste logboekafhandelingsklasse

## Een aangepast logbestand instellen in het dialoogvenster `di.xml`

Dit voorbeeld toont hoe te om [ virtuele types ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) te gebruiken om `debug` berichten in een dossier van het douanelogboek in plaats van een norm `/var/log/debug.log` te registreren.

1. In het `di.xml` dossier van uw module, bepaal een dossier van het douanelogboek als a [ virtueel type ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   De `name` waarde van `Magento\Payment\Model\Method\MyCustomDebug` moet uniek zijn.

1. Bepaal de manager in een ander [ virtueel type ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) met een uniek `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Injecteer het `MyCustomLogger` [ virtuele type ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) in het `Magento\Payment\Model\Method\Logger` voorwerp:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. De virtuele klasse `Magento\Payment\Model\Method\MyCustomDebug` wordt in de `debug` handler van de eigenschap `$logger` in de `Magento\Payment\Model\Method\Logger` -klasse geïnjecteerd.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Uitzonderingsberichten worden in het `/var/log/payment.log` -bestand aangemeld.

## Een aangepast logbestand instellen in de klasse Logger

In dit voorbeeld wordt getoond hoe u een aangepaste logboekafhandelingsklasse kunt gebruiken om `error` -berichten in een specifiek logbestand te registreren.

1. Maak een klasse waarin gegevens worden geregistreerd. In dit voorbeeld wordt de klasse gedefinieerd in `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php` .

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. Bepaal de manager voor deze klasse als a [ virtueel type ](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) in het 2} dossier van de module {.`di.xml`

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` is een unieke id.

1. Geef in de definitie `type` de klassenaam op waar de aangepaste logboekhandler wordt geïnjecteerd. Gebruik de virtuele typenaam van de vorige stap als argument voor dit type.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Source-code van `Vendor\ModuleName\Observer\MyObserver` -klasse:

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. De klasse `Vendor\ModuleName\Logger\Handler\ErrorHandler` wordt geïnjecteerd in de `error` handler van de eigenschap `$logger` in de `Vendor\ModuleName\Observer\MyObserver` .

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Uitzonderingsberichten worden in het `/var/log/my_custom_logger/error.log` -bestand aangemeld.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
