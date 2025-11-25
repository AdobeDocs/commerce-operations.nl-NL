---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 1%

---
# MariaDB-configuratie-instellingen

Het opnieuw indexeren op MariaDB 10.4 en 10.6 vergt meer tijd in vergelijking met vorige versies MariaDB of MySQL. Om het opnieuw indexeren te versnellen, adviseren wij plaatsend deze MariaDB configuratieparameters:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/docs/server/server-management/variables-and-modes/server-system-variables#optimizer_use_condition_selectivity)

Als u prestatiesdegradatie niet verwant met indexatie na bevordering aan MariaDB 10.6 ervaart, denk na toelatend het [`--query-cache-type` &#x200B;](https://mariadb.com/kb/en/server-system-variables/#query_cache_type) plaatsen. Bijvoorbeeld `--query-cache-type=ON` .

Alvorens Adobe Commerce op de projecten van de wolkeninfrastructuur te bevorderen, kunt u ook MariaDB moeten bevorderen ([&#x200B; zie MariaDB beste praktijken &#x200B;](../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md) bevorderen).

Bijvoorbeeld:

* Adobe Commerce 2.4.6 met MariaDB versie 10.5.1 of hoger
* Adobe Commerce 2.3.5 met MariaDB versie 10.3 of lager

Naast deze aanbevelingen, zou u met uw gegevensbestandbeheerder over het vormen van de volgende parameters moeten raadplegen:

>[!NOTE]
>
>Deze montages zijn beschikbaar voor op-gebouw slechts plaatsingen. Adobe Commerce op klanten met cloudinfrastructuur hebben geen toegang tot deze instellingen.

* [`--query-cache-limit`](https://mariadb.com/kb/en/server-system-variables/#query_cache_limit)
* [`--query-cache-size`](https://mariadb.com/kb/en/server-system-variables/#query_cache_size)
* [`--join-buffer-size`](https://mariadb.com/kb/en/server-system-variables/#join_buffer_size)
* [`--innodb-buffer-pool-size`](https://mariadb.com/kb/en/innodb-buffer-pool/#innodb_buffer_pool_size)
