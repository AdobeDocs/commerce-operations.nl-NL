---
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Productiesysteem bijwerken

**om het productiesysteem** bij te werken:

1. Meld u als eigenaar van het bestandssysteem aan bij het productiesysteem.
1. Schakel over naar de hoofdmap van de toepassing en schakel de onderhoudsmodus in.

   ```shell
   cd <Magento root dir>
   ```

   ```shell
   bin/magento maintenance:enable
   ```

   Zie [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md) voor extra opties, zoals de mogelijkheid om een IP-adreslijst in te stellen.

1. Stop alle actieve workers in de wachtrij door `cron_run` als volgt in te stellen op `false` in `app/etc/env.php` :

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Werk de configuratie bij.

   ```shell
   bin/magento app:config:import
   ```

1. Tot slot `kill` alle actieve consumentenprocessen.

   ```shell
   kill <PID>
   ```

   Waar `PID` de proces-id is die moet worden gedood, bijvoorbeeld:

   ```shell
   kill 1234
   ```

1. Trek code van broncontrole.

   ```shell
   git pull mconfig m2.2_deploy
   ```

1. Werk de configuratie bij.

   ```shell
   bin/magento app:config:import
   ```

1. Maak de cache leeg.

   ```shell
   bin/magento cache:clean
   ```

1. Eindonderhoudsmodus.

   ```shell
   bin/magento maintenance:disable
   ```
