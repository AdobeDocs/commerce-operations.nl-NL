---
title: Logboekdatabaseactiviteit
description: Configureer Commerce om databaseactiviteiten te registreren met behulp van de Logger-interface.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Logboekdatabaseactiviteit

In het volgende voorbeeld ziet u hoe u databaseactiviteiten kunt registreren met de `[Magento\Framework\DB\LoggerInterface](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/LoggerInterface.php)` , die twee implementaties heeft:

- Er wordt niets geregistreerd (standaard): [`Magento\Framework\DB\Logger\Quiet` ](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/Quiet.php)
- Logs to the `var/log` directory: [`Magento\Framework\DB\Logger\File` ](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/File.php)

>[!TIP]
>
>U kunt Commerce CLI gebruiken om [ gegevensbestand het registreren ](../cli/enable-logging.md#database-logging) toe te laten en onbruikbaar te maken.

Als u de standaardconfiguratie van `\Magento\Framework\DB\Logger\LoggerProxy` wilt wijzigen, bewerkt u uw `app/etc/di.xml` .

Wijzig eerst de standaardwaarden van `loggerAlias` - en `logCallStack` -argumenten in:

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

Geef vervolgens het bestandspad op voor `Magento\Framework\DB\Logger\File` :

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

