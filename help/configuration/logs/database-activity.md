---
title: Logboekdatabaseactiviteit
description: Vorm Handel om gegevensbestandactiviteit te registreren gebruikend de interface van de Registrator.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Logboekdatabaseactiviteit

In het volgende voorbeeld ziet u hoe u databaseactiviteiten kunt registreren met de [`Magento\Framework\DB\LoggerInterface`][interface], die twee implementaties heeft:

- Er wordt niets geregistreerd (standaard): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Logbestanden voor de `var/log` map: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>U kunt CLI van de Handel gebruiken aan [het toelaten en onbruikbaar maken van het gegevensbestandregistreren](../cli/enable-logging.md#database-logging).

De standaardconfiguratie wijzigen van `\Magento\Framework\DB\Logger\LoggerProxy`, bewerk uw `app/etc/di.xml`.

Wijzig eerst de standaardwaarden van `loggerAlias` en `logCallStack` argumenten voor:

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

Geef vervolgens het bestandspad op voor `Magento\Framework\DB\Logger\File`:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

Ten slotte compileert u de code met:

```bash
bin/magento setup:di:compile
```

En maak de cache schoon met:

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
