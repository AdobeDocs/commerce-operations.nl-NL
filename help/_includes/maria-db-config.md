---
source-git-commit: 631735eceb3609edd743c682291f373f6b01b399
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 1%

---
# MariaDB-configuratie-instellingen

Het opnieuw indexeren op MariaDB 10.4 en 10.6 vergt meer tijd in vergelijking met vorige versies MariaDB of MySQL. Om het opnieuw indexeren te versnellen, adviseren wij plaatsend deze MariaDB configuratieparameters:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

Als de prestaties achteruitgaan die niet samenhangen met indexering na de upgrade naar MariaDB 10.6, kunt u overwegen om [`--query-cache-type`](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) instellen. Bijvoorbeeld, `--query-cache-type=ON`.

Naast deze aanbevelingen, zou u met uw gegevensbestandbeheerder over het vormen van de volgende parameters moeten raadplegen:

>[!NOTE]
>
>Deze montages zijn beschikbaar voor op-gebouw slechts plaatsingen. Adobe Commerce op klanten met cloudinfrastructuur hebben geen toegang tot deze instellingen.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
