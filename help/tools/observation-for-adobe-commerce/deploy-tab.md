---
title: "De [!UICONTROL Deploy] tab"
description: Meer informatie over de [!UICONTROL Deploy] tabblad van [!DNL Observation for Adobe Commerce].
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 0%

---

# De [!UICONTROL Deploy] tab

Dit lusje is een poging om kwesties en oorzaken van plaatsingsproblemen snel te isoleren.

## [!UICONTROL Deploy log Deployment Troubleshooter]

![ImplementatieTroubleshooter logboek implementeren](../../assets/tools/observation-for-adobe-commerce/deploy-tab-1.jpg)

De **[!UICONTROL Deploy log Deployment Troubleshooter]** het kader toont een aantal gebeurtenissen van het plaatsingslogboek die over het geselecteerde timeframe voorkwamen. De bedoeling is een overzichtsweergave van implementatieactiviteiten te bieden en de complexiteit van de implementatie door de telling te bepalen. De meer geregistreerde berichten, complexer de plaatsing typisch is.

## [!UICONTROL Deploy State]

![Status implementeren](../../assets/tools/observation-for-adobe-commerce/deploy-tab-2.jpg)

De **[!UICONTROL Deploy State]** frame toont de implementatiegebeurtenissen die zich tijdens het geselecteerde tijdframe hebben voorgedaan. De parser voor dit kader zoekt naar deze specifieke signalen:

* %NOTICE: Opdracht genereren%&#39;) starten als &#39;start_gen&#39;
* &#39;%git apply /app/vendor/magento/ece-tools/patches%&#39;) as &#39;apply_patches&#39;
* markering %Set: .static_content_Implementeren%&#39;) als &#39;SCD&#39;
* %NOTICE: Opdracht genereren voltooid%&#39;) als &#39;gen_compl&#39;
* %NOTICE: Implementatie starten.%&#39;) als &#39;start_opstellen&#39;
* %NOTICE: Implementatie voltooid%&#39;) als &#39;implementatie_compl&#39;
* %NOTICE: Na implementatie starten.%&#39;) als &#39;start_implementatie&#39;
* %NOTICE: Na implementatie is complete%&#39;) als &#39;implementatie&#39;
* &#39;%implementatie-complete%&#39;) als &#39;cl_implementatie_compl&#39;

## [!UICONTROL Deploy Log Detail]

![Logboekgegevens implementeren](../../assets/tools/observation-for-adobe-commerce/deploy-tab-3.jpg)

De **[!UICONTROL Deploy Log Detail]** Het kader toont de summiere details van het plaatsingslogboekbericht die over het geselecteerde tijdkader voorkwamen. Het kader ontleedt voor de volgende koorden in de plaatsingslogboeken:

* ‘%NOTITIE: Implementatie starten.%&#39;) als &#39;start_dply&#39;
* &#39;%INFO: Beginscenario(s): scenario/deploy.xml%&#39;) als &#39;start_scenario&#39;
* %NOTICE: Vooraf implementeren%&#39;) starten als &#39;start_predply&#39;
* &#39;% INFO: Patchlogbestand (%&#39;) herstellen als &#39;rstr_ptch_log&#39;
* &#39;%INFO: Cacheconfiguratie bijwerken.%&#39;) als &#39;updt_cach_config&#39;
* &#39;%INFO: Redis slave connection%&#39;) instellen als &#39;redis_sec_conn_set&#39;
* &#39;%INFO: De statische plaatsing van inhoud werd uitgevoerd tijdens bouwstijlhaak, schoonmaakend oude inhoud%&#39;) zoals &quot;scd_build_hk&quot;
* &#39;%INFO: Poob/static% wissen) als &#39;clr_pub_static&#39;
* &#39;%NFO: Wissen, herstelt cache:%&#39;) als &#39;clr_redis_cache&#39;
* &#39;%INFO: var/cache directory%&#39;) wissen als &#39;clr_var_cach&#39;
* MELDING &#39;%: Onderhoudsmodus%&#39;) inschakelen als &#39;enable_maint_mode&#39;
* &#39;%INFO: Uitsnijden%&#39;) uitschakelen als &#39;disable_cron&#39;
* &#39;%INFO: Poging om hardlopende kroonbanen te doden en consumenten verwerken%&#39;) als &#39;kill_cron_try&#39;
* &#39;%INFO: Er zijn geen lopende Magento- en consumentenprocessen gevonden.%&#39;) als &#39;no_cron_fnd&#39;,
* %NOTICE: Validatie configuration%&#39;) als &#39;validate_config&#39;
* &#39;%De volgende beheergegevens zijn vereist om een beheergebruiker te maken tijdens de eerste installatie&#39;%&#39;) als &#39;no_admin&#39;
* &#39;%Recommended PHP version voldoende voor the constraint%&#39;) als &#39;php_ver_constraint&#39;
* &#39;%WAARSCHUWING: Configuratie corrigeren met opgegeven suggesties:%) als &#39;fix_config_sugg&#39;
* &#39;%WAARSCHUWING: [2003] De geneste niveauwaarde van de folder voor fout het melden is niet gevormd.%&#39;) as&#39;nest_err_reporting&#39;
* %NOTICE: Einde van validatie%&#39;) als &#39;end_validation&#39;
* %NOTICE: Update starten.%&#39;) als &#39;start_update&#39;
* &#39;%INFO: Env.php wordt bijgewerkt.%&#39;) als &#39;update_php_env&#39;
* &#39;%INFO: De configuratie van de env.php DB-verbinding wordt bijgewerkt.%&#39;) als &#39;update_php_env_db&#39;
* &#39;%INFO: env.php AMQP configuration%&#39;) bijwerken als &#39;update_php_env_amqp&#39;
* &#39;%INFO: Zoekprogramma instellen op: elasticsearch7%&#39;) als &#39;set_elastic7&#39;
* &#39;%elasticsearch 6.5.4 has passed EOL%&#39;) as &#39;elastic_ver_EOL&#39;
* &#39;%INFO: Zoekprogramma instellen op: elasticsearch6%&#39;) als &#39;set_elastic6&#39;
* &#39;%INFO: Beveiligde en onveilige URL&#39;s bijwerken (%&#39;) als &#39;update_urls&#39;
* &#39;%INFO: Installatie-upgrade wordt uitgevoerd.%&#39;) als &#39;setup_upgrade_run&#39;
* &#39;%INFO: Post-implementatiehaak ingeschakeld. Cron-mogelijkheden, cachereiniging en bewerkingen vóór verwarming worden uitgesteld (%) als &#39;post_haak_enabled&#39;
* %NOTICE: De onderhoudsmodus is uitgeschakeld.%&#39;) als &#39;maint_mode_disabled&#39;
* &#39;%INFO: Scenario(&#39;s voltooid%) als &#39;scenario_voltooid&#39;
* &#39;%WAARSCHUWING: Command-onderhoud:inschakelen voltooid met een fout. Een bestand voor de onderhoudsvlag (%&#39;) maken als &#39;enable_Maintenance_fail&#39;
* &#39;%MySQL server has away%&#39;) als &#39;MySQL_has_away_away&#39;

## [!UICONTROL Post Deploy Log Detail]

![Logboekgegevens plaatsen](../../assets/tools/observation-for-adobe-commerce/deploy-tab-4.jpg)

De **[!UICONTROL Post Deploy Log Detail]** het kader toont de post-opstellings logboekdetails die over het geselecteerde tijdkader voorkwamen. Dit kader is geconcentreerd op bepaalde logboekberichten die de volgende koorden bevatten:

* &#39;%Disabled Maintenance mode%&#39;) als &#39;disabled_maint_mode&#39;
* &#39;%INFO: Beginscenario(s): scenario/post-deploy.xml%&#39;) als &#39;start_push_scenario&#39;
* MELDING &#39;%: Validatie configuration%&#39;) als &#39;val_config&#39;
* MELDING &#39;%: Einde van validatie%&#39;) als &#39;end_val_config&#39;
* &#39;%INFO: Cron%&#39;) inschakelen als &#39;cron_enabled&#39;
* &#39;% INFO: Maak een back-up van belangrijke bestanden.%&#39;) als &#39;file_backup&#39;
* &#39;%INFO: Back-up is gemaakt (in%&#39;) als &#39;file_backup_success&#39;
* &#39;%INFO: Opwarmen van pagina%&#39;) starten als &#39;pg_warmup_start&#39;
* &#39;%INFO: Pagina met waarschuwing:%&#39;) als &#39;warmed_up_pg&#39;
* &#39;%ERROR: Opwarmen is mislukt:%&#39;) als &#39;warm_up_pg_err&#39;
* &#39;% INFO: Scenario(&#39;s voltooid%) als &#39;scenario_voltooid&#39;

## [!UICONTROL Cloud Log Detail]

![Cloud Log Detail](../../assets/tools/observation-for-adobe-commerce/deploy-tab-5.jpg)

De **[!UICONTROL Cloud Log Detail]** frame geeft de gegevens van het cloudlog weer die tijdens het geselecteerde tijdsbestek zijn opgetreden. De volgende tekenreeksen worden geparseerd en geretourneerd met het onderstaande AS-label:

* &#39;%DEBUG: /bin/bash-c &quot;set -o pipefail&quot;; php ./bin/magento setup:upgrade%&#39;) als &#39;start_update&#39;
* &#39;%Schema maken/bijwerken:%&#39;) als &#39;schema_updates&#39;
* &#39;%Niets te importeren.%&#39;) als &#39;mod_import_finish&#39;
* %NOTICE: Einde van update.%&#39;) als &#39;update_completed&#39;
* &#39;%DEBUG: Stappen: distribueren-statische inhoud%&#39;) als &#39;scd_run&#39;
* MELDING &#39;%: Statische inhoud wordt overgeslagen. SCD op verzoek is ingeschakeld.%&#39;) als &#39;scd_ondemand&#39;
* &#39;%INFO: Clearing%&#39;) as&#39;clr_dirs&#39;
* &#39;%DEBUG: Stap &quot;opstellen-statische-inhoud&quot; (voltooid%) als &quot;scd_voltooid&quot;
* %NOTICE: Compressie statische inhoud wordt overgeslagen. SCD op verzoek is ingeschakeld.%&#39;) als &#39;scd_compression_run&#39;,
* &#39;%INFO: var/cache directory%&#39;) wissen als &#39;clr_var_cach&#39;
* &#39;%DEBUG: Stap &quot;compress-static-content&quot; (voltooid%) als &quot;scd_compression_completed&quot;
* &#39;%DEBUG: Stappen: distribueren-complete%&#39;) als &#39;distribueren_voltooid&#39;
* &#39;%INFO: Post-implementatiehaak ingeschakeld. Het inschakelen van uitsnijden, het schoonmaken van de cache en het opwarmen van de beelden worden uitgesteld tot na de implementatie.%&#39;) als &#39;Post_opstellen_haak_enabled&#39;
* %NOTICE: De onderhoudsmodus is uitgeschakeld.%&#39;) als &#39;maint_mode_disabled&#39;
* &#39;%INFO: Scenario(&#39;s voltooid%) als &#39;scenario_voltooid&#39;
* &#39;%post-implementatie.xml%&#39;) als &#39;post_implementatie_start&#39;
* %NOTICE: Validatie configuration%&#39;) als &#39;validate_config&#39;
* &#39;%WAARSCHUWING: [2003] De geneste niveauwaarde van de folder voor fout het melden is niet gevormd.%&#39;) as&#39;nest_err_reporting&#39;
* %NOTICE: Einde van validatie%&#39;) als &#39;end_validation&#39;
* &#39;%INFO: Cron%&#39;) inschakelen als &#39;enable_cron&#39;
* &#39;%INFO: Maak een back-up van belangrijke bestanden (%&#39;) als &#39;create_backup&#39;
* &#39;%DEBUG: Stap &quot;back-up&quot; voltooid%&quot;) als &quot;back-up_voltooid&quot;
* &#39;%INFO: Opwarmen van pagina%&#39;) beginnen als &#39;warmup_start&#39;
* &#39;%ERROR: Opwarmen is mislukt:%&#39;) als &#39;warm_up_fail&#39;
* &#39;%DEBUG: Stap &quot;warm-up&quot; voltooid%&quot;) als &quot;warm-up_voltooid&quot;
* &#39;% FOUTOPSPORING: Stap &quot;time-to-first-byte&quot; completed%&quot;) als &quot;ttfb_completed&quot;
* &#39;%INFO: Scenario(&#39;s voltooid%) als &#39;post_implementatie_voltooid&#39;
* &#39;%DEBUG: Stappen: pre-build%&#39;) als &#39;run_pre-build&#39;
* &#39;%DEBUG: Markering .static_content_Implementation is al verwijderd%&#39;) als &#39;scd_flag_del&#39;
* &#39;%DEBUG: Stap &quot;pre-bouwstijl&quot; (voltooid%) als &quot;pre-build_completed&quot;
* %NOTICE: Patches toepassen (%&#39;) als &#39;apply_patches&#39;
* &#39;%has been applied%&#39;) als &#39;patches_applied&#39;
* &#39;%DEBUG: Stap &quot;apply-patches&quot; (voltooid%) als &quot;apply_patches_complete&quot;
* &#39;%Deploy using quick strategy%&#39;) als &#39;quick_strategy_deploy&#39;
* MELDING &#39;%: DI compilation%&#39;) uitvoeren als &#39;di_compliation_start&#39;
* %NOTICE: End of running DI compilation%&#39;) as &#39;di_compliation_completed&#39;
* %NOTICE: Nieuwe statische inhoud genereren%&#39;) als &#39;gen_frsh_static_content&#39;
* %magento instellen:static-content:distribueren%&#39;) als &#39;scd_executing&#39;
* %NOTICE: Einde van het genereren van verse statische inhoud%&#39;) als &#39;gen_frsh_static_cont_completed&#39;
* &#39;%INFO: Beginscenario(s): scenario/build/transfer.xml%&#39;) als &#39;start_transferxml&#39;
* &#39;%INFO: Poging om hardlopende kroontaken te doden (%&#39;) als &#39;kill_crons&#39;
* &#39;%INFO: Wissen herstelt cache:%&#39;) als &#39;clear_redis_cache&#39;
* &#39;%INFO: Controleren of db bestaat en hastables%&#39;) als &#39;db_check&#39;
* &#39;%WAARSCHUWING: [2010] De dienst van Elasticsearch wordt geïnstalleerd bij infrastructuurlaag maar niet gebruikt als onderzoeksmotor.%&#39;) as&#39;es_not_used&#39;
* %NOTICE: Update starten.%&#39;) als &#39;start_update&#39;
* &#39;%INFO: Zoekprogramma instellen op: mysql%&#39;) als &#39;mysql_search&#39;
* &#39;%SQLSTATE[HY000] [2006] MySQL-server is weggegaan (%&#39;) als &#39;mysql_away&#39;

## [!UICONTROL Count of modules imported during deploy]

![Aantal modules dat tijdens plaatsing wordt ingevoerd](../../assets/tools/observation-for-adobe-commerce/deploy-tab-6.jpg)

De **[!UICONTROL Count of modules imported during deploy]** frame geeft het aantal modules weer dat tijdens de implementatie in de geselecteerde tijdlijn wordt geïmporteerd.

## [!UICONTROL Deployed module list]

![Lijst met geïmplementeerde modules](../../assets/tools/observation-for-adobe-commerce/deploy-tab-7.jpg)

De **[!UICONTROL Deployed module list]** het kader toont opgestelde modules over geselecteerde timeframe.

