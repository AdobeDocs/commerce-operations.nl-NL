---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '93'
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

   Voor extra opties, zoals de capaciteit om een IP adres te plaatsen whitelist, zie [`magento maintenance:enable`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

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
