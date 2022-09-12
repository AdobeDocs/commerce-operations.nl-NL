---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Productiesysteem bijwerken

**Het productiesysteem bijwerken**:

1. Meld u als eigenaar van het bestandssysteem aan bij het productiesysteem.
1. Schakel over naar de hoofdmap van de toepassing en schakel de onderhoudsmodus in.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   Voor extra opties, zoals de capaciteit om een IP adres te plaatsen whitelist, zie [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Stop om het even welke lopende rijarbeiders door te plaatsen `cron_run` tot `false` in `app/etc/env.php` als volgt:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Werk de configuratie bij.

   ```bash
   bin/magento app:config:import
   ```

1. Tot slot: `kill` actieve consumentenprocessen.

   ```bash
   kill <PID>
   ```

   Wanneer `PID` is de proces-id die moet worden gedood, bijvoorbeeld:

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
