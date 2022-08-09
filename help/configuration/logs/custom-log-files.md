---
title: Naar aangepast logbestand schrijven
description: Leer aangepaste logbestanden instellen.
contributor_name: Atwix
contributor_link: https://www.atwix.com/
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# Naar een aangepast logbestand schrijven

De `Magento\Framework\Logger` module bevat de volgende klassen voor handlers:

| Klasse | Logbestand |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

U vindt ze misschien in het dialoogvenster `lib/internal/Magento/Framework/Logger/Handler` directory.

U kunt een van de volgende methoden gebruiken om u aan te melden bij een aangepast bestand:

- Een aangepast logbestand instellen in het dialoogvenster `di.xml`
- Een aangepast bestand instellen in de aangepaste logboekafhandelingsklasse

## Een aangepast logbestand instellen in het dialoogvenster `di.xml`

In dit voorbeeld wordt getoond hoe u kunt gebruiken [virtuele typen](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) aan logbestand `debug` berichten naar een aangepast logbestand in plaats van naar een standaard `/var/log/debug.log`.

1. In de `di.xml` een aangepast logbestand van uw module definiëren als een [virtueel type](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   De `name` waarde van `Magento\Payment\Model\Method\MyCustomDebug` moet uniek zijn.

1. De handler in een andere handler definiëren [virtueel type](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) met een unieke `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Injecteer de `MyCustomLogger` [virtueel type](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) in de `Magento\Payment\Model\Method\Logger` object:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. De virtuele klasse `Magento\Payment\Model\Method\MyCustomDebug` wordt geïnjecteerd in de `debug` van de `$logger` eigenschap in de `Magento\Payment\Model\Method\Logger` klasse.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

De berichten van de uitzondering worden geregistreerd in `/var/log/payment.log` bestand.

## Een aangepast logbestand instellen in de klasse Logger

In dit voorbeeld wordt getoond hoe u een aangepaste logboekafhandelingsklasse kunt gebruiken voor het loggen `error` berichten naar een specifiek logbestand.

1. Maak een klasse waarin gegevens worden geregistreerd. In dit voorbeeld wordt de klasse gedefinieerd in `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

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

1. De handler voor deze klasse definiëren als een [virtueel type](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) in de module `di.xml` bestand.

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

1. In de `type` Geef de klassenaam op waar de aangepaste logboekhandler wordt geïnjecteerd. Gebruik de virtuele typenaam van de vorige stap als argument voor dit type.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Broncode van `Vendor\ModuleName\Observer\MyObserver` klasse:

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

1. De klasse `Vendor\ModuleName\Logger\Handler\ErrorHandler` wordt geïnjecteerd in de `error` van de `$logger` eigenschap in de `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

De berichten van de uitzondering worden het programma geopend in `/var/log/my_custom_logger/error.log` bestand.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php