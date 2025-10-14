---
title: Het tabblad [!UICONTROL PHP]
description: Leer meer over het [!UICONTROL PHP] lusje van  [!DNL Observation for Adobe Commerce].
exl-id: 0989a7f5-75b0-4fb5-ac5e-2618603bf548
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# Het tabblad [!UICONTROL PHP]

Het **PHP** lusje toont PHP proceskwesties om een diepere analyse in PHP problemen te verstrekken.

## [!UICONTROL PHP active process details]

![&#x200B; PHP actieve procesdetails &#x200B;](../../assets/tools/php-active-process-details.jpg)

Het frame **[!UICONTROL PHP active process details]** toont de PHP-processen, inclusief php-fpm, over de geselecteerde tijd.

## [!UICONTROL PHP process load (# of PHP processes and % of CPU load)]

![&#x200B; PHP proceslading &#x200B;](../../assets/tools/php-process-load.jpg)

Het **[!UICONTROL PHP process load (# of PHP processes and % of CPU load)]** -frame toont de CPU load van PHP-FPM processen over de geselecteerde tijdsperiode.

## [!UICONTROL PHP Memory detail]

![&#x200B; PHP de detail van het Geheugen &#x200B;](../../assets/tools/php-memory-detail.jpg)

In het frame **[!UICONTROL PHP Memory detail]** wordt het geheugengebruik van PHP-processen in de geselecteerde tijdsperiode weergegeven.

## [!UICONTROL PHP CPU Utilization]

![&#x200B; PHP CPU Utilization &#x200B;](../../assets/tools/php-cpu-utilization.jpg)

In het **[!UICONTROL PHP CPU Utilization]** frame wordt het CPU-percentage weergegeven van het gebruik van PHP processen gedurende de geselecteerde tijdsperiode.

## [!UICONTROL PHP Process states]

![&#x200B; PHP staten van het Proces &#x200B;](../../assets/tools/php-process-states-image-1.jpg)

In het frame **[!UICONTROL PHP Process states]** worden de PHP-processtatussen in de geselecteerde tijdlijn weergegeven. Het wordt weergegeven wanneer PHP-processen worden beëindigd en opnieuw worden gestart. Wees voorzichtig met afgesloten PHP-processen die geen nieuwe start laten zien.

* &#39;%NOTICE: Terminating ...%&#39;) as &#39;php_term&#39;
* &quot;% NOTITIE: afsluiten, afscheid!%&#39;) als &#39;php_exit&#39;
* &#39;% OPMERKING: fpm wordt uitgevoerd, pid%&#39;) als &#39;fpm_start&#39;
* &#39;%NOTICE: ready to handle connections%&#39;) as &#39;php_ready&#39;

## [!UICONTROL PHP Errors]

![&#x200B; de Fouten van PHP &#x200B;](../../assets/tools/php-errors-image-1.jpg)

Het frame **[!UICONTROL PHP Errors]** toont het aantal PHP-arbeidersfouten in de geselecteerde tijdlijn. Foutberichten die worden geparseerd en weergegeven, zijn:

* &#39;%worker_connections are not genoeg%&#39;) als &#39;worker&#39;
* &#39;%PHP Fatale error: Allowed memory size!%&#39;) als &#39;mem_size&#39;
* &#39;%exited on signaal 11 (SIGSEGV)%&#39;) as &#39;sig_11&#39;
* &#39;%exited on signaal 7 (SIGBUS)%&#39;) as &#39;sig_7&#39;
* &#39;%rise pm.start_servers%&#39;) als &#39;pmstart_serv&#39;
* &#39;%max_children%&#39;) als &#39;max_children_cnt&#39;
* &#39;%PHP Fatale error: allowed memory size of%&#39;) as &#39;mem_exhst_coun&#39;
* &#39;%Kan geheugen voor pool%&#39;) niet toewijzen als &#39;opc_mem_count&#39;
* &#39;%Warning Interned String buffer overflow%&#39;) als &#39;opc_str_buf&#39;
* &#39;%Illegal string offsetl%&#39;) als &#39;opc_sv_comments&#39;
* &#39;%PHP Fatal error: Uncaught RedisException: read error on connection%&#39;) as &#39;php_exc&#39;

## [!UICONTROL PHP processes count]

![&#x200B; PHP procestelling &#x200B;](../../assets/tools/php-processes-count.jpg)

Het frame **[!UICONTROL PHP processes count]** toont een aantal PHP-processen over de geselecteerde tijd.

## [!UICONTROL Database Errors]

![&#x200B; Fouten van het Gegevensbestand &#x200B;](../../assets/tools/php-tab-database-errors.jpg)

In het frame **[!UICONTROL Database Errors]** worden databasefouten over de geselecteerde tijdlijn weergegeven. Voorbeelden van geparseerde fouten:

* &#39;%Geheugengrootte toegewezen voor de tijdelijke tabel is meer dan 20% van de waarde van onschuldig_buffer_pool_size%&#39;) als &#39;temp_tbl_buff_pool&#39;
* &#39;%\[ERROR\] WSREP: rbr write fail%&#39;) als &#39;rbr_write_fail&#39;
* &#39;%mysqld: Schijf vol%&#39;) als &#39;disk_full&#39;
* &#39;%Error number 28%&#39;) als &#39;err_28&#39;
* &#39;%rollback%&#39;) als &#39;rollback&#39;
* &#39;%Foreign key-beperking mislukt voor table%&#39;) als &#39;foreign_key_constraint&#39;
* &#39;%Error_code: 1114%&#39;) als &#39;sql_1114_full&#39;
* &#39;%CRITICAL: SQLSTATE [ HY000 ] [ 2006 ] MySQL server is away%&#39;) als &quot;sql_went&quot;
* &quot;%SQLSTATE [ HY000 ] [ 1040 ] Te veel verbindingen%&quot;) als &quot;sql_1040&quot;
* &#39;%CRITICAL: SQLSTATE [ HY000 ] [ 2002 ]%&#39;) als &quot;sql_2002&quot;
* &quot;%SQLSTATE [ 08S01 ]:%&quot;) als &quot;sql_1047&quot;
* &quot;% [ Waarschuwing ] Geaborteerde connection%&quot;) als &quot;aborted_conn&quot;
* &quot;%SQLSTATE [ 23000 ]: Schending van de de beperkingsbeperking van de integriteit:%&quot;) als &quot;sql_23000&quot;
* &#39;%1205 Lock wait timeout%&#39;) als &#39;sql_1205&#39;
* &quot;%SQLSTATE [ HY000 ] [ 1049 ] Onbekende database%&quot;) als &quot;sql_1049&quot;
* &quot;%SQLSTATE [ 42S02 ]: De lijst van de basis of de mening niet gevonden:%&quot;) als &quot;sql_42S02&quot;
* &#39;%Algemene fout: 1114%&#39;) als &#39;sql_1114&#39;
* &#39;%SQLSTATE [ 40001 ]%&#39;) als &quot;sql_1213&quot;
* &quot;%SQLSTATE [ 42S22 ]: Kolom niet gevonden: 1054 Onbekende kolom%&quot;) als &quot;sq1_1054&quot;
* &quot;%SQLSTATE [ 42000 ]: De fout van de syntaxis of toegangsschending:%&quot;) als &quot;sql_42000&quot;
* &quot;%SQLSTATE [ 21000 ]: Kardinaliteitsschending:%&quot;) als &quot;sql_1241&quot;
* &quot;%SQLSTATE [ 22003 ]:%&quot;) als &quot;sql_22003&quot;
* &quot;%SQLSTATE [ HY000 ] [ 9000 ] Cliënt met IP adres%&quot;) als &quot;sql_9000&quot;
* &#39;%SQLSTATE [ HY000 ]: Algemene fout: 2014%&#39;) als &quot;sql_2014&quot;
* &#39;%1927 Verbinding is gedood%&#39;) als &#39;sql_1927&#39;
* &#39;%1062 \[ERROR\] InnoDB:%&#39;) als &#39;sql_1062_e&#39;
* &quot;% [ Nota ] WSREP: Het flushing geheugenkaart aan schijf..%&quot;) als &quot;mem_map_flush&quot;
* &#39;%Internal MariaDB error code: 1146%&#39;) as &#39;sql_1146&#39;
* &#39;%Internal MariaDB foutcode: 1062%&#39;) als &#39;sql_1062&#39; * &#39;%1062 [ Waarschuwing ] InnoDB:%&#39;) als &#39;sql_1062_w&#39;
* &#39;%Internal MariaDB error code: 1064%&#39;) as &#39;sql_1064&#39;
* &#39;%InnoDB: bevestiging mislukt in bestand%&#39;) als &#39;assertion_err&#39;
* &#39;%mysqld_safe Aantal processen dat nu wordt uitgevoerd: 0%&#39;) als &#39;mysql_oom&#39;
* &#39;%\[ERROR\] mysqld heeft signaal%&#39;) als &#39;mysql_sigterm&#39;
* &#39;%1452 Cannot add%&#39;) as &#39;sql_1452&#39;
* &#39;%ERROR 1698%&#39;) als &#39;sql_1698&#39;
* &#39;%SQLSTATE [ HY000 ]: Algemene fout: 3%&#39;) als &quot;cnt_wrt_tmp&quot;
* &#39;%Algemene fout: 1 %&#39;) als &#39;sql_syntax&#39;
* &#39;%42S22%&#39;) als &#39;sql_42S22&#39;
* &#39;%InnoDB: Error (Duplicate key)%&#39;) as &#39;innodb_dup_key&#39;

## [!UICONTROL Database traces]

![&#x200B; sporen van het Gegevensbestand &#x200B;](../../assets/tools/php-tab-database-traces.jpg)

In het frame **[!UICONTROL Database traces]** worden traceergegevens van de database weergegeven. Dit frame wordt uitgelijnd op de APM-transactieoverzichtsweergave voor de geselecteerde tijdlijn.

## [!UICONTROL Database mysql-slow.log]

![&#x200B; Gegevensbestand mysql-slow.log &#x200B;](../../assets/tools/php-tab-database-mysql-slow-log.jpg)

In het frame **[!UICONTROL Database mysql-slow.log]** worden de typen queryinstructies weergegeven die zich in het `mysql-slow.log` -bestand binnen de geselecteerde tijdlijn bevonden.
