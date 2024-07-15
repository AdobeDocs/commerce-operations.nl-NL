---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Productiesysteem bijwerken

**om het productiesysteem** bij te werken:

1. Meld u als eigenaar van het bestandssysteem aan bij het productiesysteem.
1. Schakel over naar de hoofdmap van de toepassing en schakel de onderhoudsmodus in.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
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

   ```bash
   bin/magento app:config:import
   ```

1. Tot slot `kill` alle actieve consumentenprocessen.

   ```bash
   kill <PID>
   ```

   Waar `PID` de proces-id is die moet worden gedood, bijvoorbeeld:

   ```bash
   kill 1234
   ```

1. Trek code van broncontrole.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Werk de configuratie bij.

   ```bash
   bin/magento app:config:import
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:clean
   ```

1. Eindonderhoudsmodus.

   ```bash
   bin/magento maintenance:disable
   ```
