---
user-guide-title: Configuratiegids
user-guide-description: Configureer uw Adobe Commerce-toepassingsfuncties en -services.
feature: Configuration
source-git-commit: 605b2e59d200bc8eeab43e91006a3f95e6a6c138
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 1%

---


# Configuratiegids {#configuration-guide}

+ [Overzicht](overview.md)
+ Algemene instelling {#setup}
   + [Initialisatie en bootstrap van toepassingen](bootstrap/initialization.md)
   + [Toepassingsmodi](bootstrap/application-modes.md)
   + [Bootstrap-parameters](bootstrap/set-parameters.md)
   + [Profielen](bootstrap/mage-profiler.md)
   + [Basismappaden](bootstrap/mage-directory.md)
+ Implementatie {#deployment}
   + [Overzicht van implementatie](deployment/overview.md)
   + [Implementatie van één computer](deployment/single-machine.md)
   + [Implementatie van pijpleidingen](deployment/technical-details.md)
   + [Vereisten](deployment/prerequisites.md)
   + [Installatie van ontwikkelsysteem](deployment/development-system.md)
   + [Systeeminstellingen samenstellen](deployment/build-system.md)
   + [Installatie van productiesysteem](deployment/production-system.md)
   + [Toegangsrechten voor bestandssystemen](deployment/file-system-permissions.md)
   + Voorbeelden {#examples}
      + [Een gedeelde configuratie gebruiken](deployment/example-shared-configuration.md)
      + [CLI-opdrachten gebruiken](deployment/example-using-cli.md)
      + [Omgevingsvariabelen gebruiken](deployment/example-environment-variables.md)
+ Cache {#cache}
   + [Overzicht van caching](cache/caching-overview.md)
   + [Vooruiteinden van cache configureren](cache/cache-types.md)
   + [Achtergrondopties cache](cache/cache-options.md)
   + [L2-cacheconfiguratie](cache/level-two-cache.md)
   + Redis {#redis}
      + [Redis installeren en instellen](cache/config-redis.md)
      + [Redis configureren voor standaard- en paginacache](cache/redis-pg-cache.md)
      + [Redis voor sessieopslag configureren](cache/redis-session.md)
      + [Redis configureren met AWS ElastiCache](cache/redis-elasticache-for-ec2.md)
   + Valkey {#valkey}
      + [Valkey installeren en instellen](cache/config-valkey.md)
      + [Valkey configureren voor standaard- en paginacache](cache/valkey-pg-cache.md)
      + [Valkey configureren voor sessieopslag](cache/valkey-session.md)
   + Varnish {#varnish}
      + [Varnish, overzicht](cache/config-varnish.md)
      + [Varnish installeren](cache/config-varnish-install.md)
      + [De webserver configureren](cache/config-varnish-server.md)
      + [Commerce-toepassing configureren](cache/configure-varnish-commerce.md)
      + [Geavanceerde Varnish-configuratie](cache/config-varnish-advanced.md)
      + [Varnish-configuratie verifiëren](cache/config-varnish-final.md)
      + [Cache wissen met Varnish](cache/use-varnish-cache.md)
      + [Cache wissen met meerdere instanties van Varnish](cache/use-multiple-varnish-cache.md)
      + [Varnish ESI-blok](cache/use-varnish-esi.md)
   + [Statische inhoudcache](cache/static-content-signing.md)
+ Opdrachtregel {#cli}
   + [Gereedschap Command-lijn](cli/config-cli.md)
   + [Algemene opdrachten](cli/common-cli-commands.md)
   + [Logbestand inschakelen](cli/enable-logging.md)
   + [De cache beheren](cli/manage-cache.md)
   + [Indexeerders beheren](cli/manage-indexers.md)
   + [Cron-taken configureren](cli/configure-cron-jobs.md)
   + [Code compileren](cli/code-compiler.md)
   + [Bewerkingsmodus](cli/set-mode.md)
   + [Gebruikers in de wachtrij met berichten starten](cli/start-message-queues.md)
   + [URN-markering](cli/urn-highlighter.md)
   + [Afhankelijkheidsrapporten](cli/dependency-reports.md)
   + [Lokalisatie](cli/localization.md)
   + Configuratiebeheer {#configuration-management}
      + [Waarden instellen](cli/set-configuration-values.md)
      + [Exportinstellingen](cli/export-configuration.md)
      + [Gegevens importeren](cli/import-configuration.md)
   + Statische weergave {#static-view}
      + [Implementatiestrategieën](cli/static-view-file-strategy.md)
      + [Statische weergavebestanden gebruiken](cli/static-view-file-deployment.md)
   + [Symlinks maken](cli/create-symlinks.md)
   + [Eenheidstests uitvoeren](cli/unit-tests.md)
   + [Layoutbestanden converteren](cli/convert-layout-files.md)
   + [Gegevens genereren voor het testen van prestaties](cli/generate-data.md)
   + [Ondersteuningsprogramma&#39;s uitvoeren (alleen Commerce)](cli/run-support-utilities.md)
+ Configuratiebestanden {#files}
   + [Configuratiebestanden voor implementatie](reference/deployment-files.md)
   + [Configuratietypen](reference/config-create-types.md)
   + [Modulebestanden](reference/module-files.md)
   + [Module-uitvoer](reference/disable-module-output.md)
   + [config.php](reference/config-reference-configphp.md)
   + [env.php](reference/config-reference-envphp.md)
   + [gitignore](reference/config-reference-gitignore.md)
   + [system.xml](reference/config-reference-systemxml.md)
+ Configuratiepaden {#paths}
   + [Algemeen](reference/config-reference-general.md)
   + [B2B-extensie](reference/config-reference-b2b.md)
   + [Catalogus](reference/config-reference-catalog.md)
   + [Klanten](reference/config-reference-customers.md)
   + [Betalingsmethoden](reference/config-reference-payment.md)
   + [Verkoop](reference/config-reference-sales.md)
   + [Services](reference/config-reference-services.md)
   + [Gevoelige en systeemspecifieke instellingen](reference/config-reference-sens.md)
   + [Configuratie-instellingen overschrijven](reference/override-config-settings.md)
+ Cron Jobs {#crons}
   + [Cron jobs and groups](cron/custom-cron.md)
   + [Referentie voor curven aanpassen](cron/custom-cron-reference.md)
   + [Een aangepaste uitsnijdtaak configureren](cron/custom-cron-tutorial.md)
+ Logboeken {#logs}
   + [Aangepaste logbestanden](logs/custom-logging.md)
   + [Aanmeldingsinterface](logs/logger-interface.md)
   + [Logboekdatabaseactiviteit](logs/database-activity.md)
   + [Naar een aangepast logbestand schrijven](logs/custom-log-files.md)
+ Berichtenrijen {#message-queues}
   + [Framework voor wachtrij met berichten](queues/message-queue-framework.md)
   + [Berichtenrijen beheren](queues/manage-message-queues.md)
   + [Amazon MQ instellen](queues/aws-mq.md)
   + [Consumenten](queues/consumers.md)
+ Meerdere sites {#multi-sites}
   + [Meerdere sites en weergaven](multi-sites/ms-overview.md)
   + [Toename-ID database-entiteit](multi-sites/change-increment-id.md)
   + [Instellen in de beheerder](multi-sites/ms-admin.md)
   + [Instellen met Nginx](multi-sites/ms-nginx.md)
   + [Instellen met Apache](multi-sites/ms-apache.md)
+ Zoekmachine {#search}
   + [Overzicht van zoekmachines](search/overview-search.md)
   + [Zoekmachine configureren](search/configure-search-engine.md)
   + [Filteren met stopwoorden](search/search-stopwords.md)
+ Beveiliging {#security}
   + [Beveiligingsoverzicht](security/overview.md)
   + [Wachtwoordhashing](security/password-hashing.md)
   + [Cachevergiftiging](security/cache-poisoning.md)
   + [Beveiligde uitsnede PHP](security/secure-cron-php.md)
   + [BeveiligingstXT](security/security-txt.md)
   + [Klik op Explosies oppakken](security/xframe-options.md)
+ Opslag {#storage}
   + [Databaseanalyse](storage/db-profiler.md)
   + Externe opslag {#remote-storage}
      + [Externe opslagmodule](remote-storage/remote-storage.md)
      + [AWS S3-emmertje](remote-storage/remote-storage-aws-s3.md)
      + [Afbeeldingsformaat wijzigen](remote-storage/remote-storage-image-resize.md)
      + [Externe opslag voor cloud](remote-storage/cloud-support.md)
   + Sessieopslag {#session-storage}
      + [Sessieopslaglocatie](storage/sessions.md)
      + [in cache geplaatst voor sessieopslag](storage/memcached.md)
      + [in cache geplaatst op CentOS](storage/memcache-centos.md)
      + [ingesloten op Ubuntu](storage/memcache-ubuntu.md)
   + Database splitsen {#split-db}
      + [Overzicht van gesplitste database](storage/multi-master.md)
      + [Automatische configuratie](storage/multi-master-masterdb.md)
      + [Handmatige configuratie](storage/multi-master-manual.md)
      + [Gesplitste database verifiëren](storage/multi-master-verify.md)
      + [Database-replicatie](storage/multi-master-replication.md)
      + [Eén database herstellen](storage/revert-split-database.md)
+ [Terugkeren naar operationele hulplijnen](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html?lang=nl-NL)
