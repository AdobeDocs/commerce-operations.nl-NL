---
title: Logbestand inschakelen
description: Leer hoe u verschillende typen aanmelding in Adobe Commerce in- en uitschakelt. Ontdek registrerenconfiguratie en beheerstechnieken.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Logbestand inschakelen

{{file-system-owner}}

## Foutopsporingsregistratie

Door gebrek, schrijft Commerce aan het zuivert logboek (`<install_directory>/var/log/debug.log`) wanneer het in gebrek is of wijze ontwikkelt, maar niet wanneer het op productiemodus is. Gebruik de opdracht `bin/magento setup:config:set --enable-debug-logging` om de standaardwaarde te wijzigen.

>[!INFO]
>
>Vanaf Commerce 2.3.1 kunt u de opdracht `bin/magento config:set dev/debug/debug_logging` niet meer gebruiken om foutopsporingslogbestanden in of uit te schakelen voor de huidige modus.

### Foutopsporingsregistratie inschakelen

1. Gebruik de opdracht `setup:config:set` om foutopsporingslogboeken in te schakelen voor de huidige modus.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:flush
   ```

### Foutopsporingslogbestand uitschakelen

1. Gebruik de opdracht `setup:config:set` om foutopsporingsregistratie voor de huidige modus uit te schakelen.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:flush
   ```

## Logboekregistratie van databases

Standaard schrijft Commerce de logboeken voor databaseactiviteiten naar het `<install-dir>/var/debug/db.log` -bestand.

### Databaseregistratie inschakelen

1. Gebruik de opdracht `dev:query-log` om databaselogboekingen in of uit te schakelen.

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:flush
   ```

## Gekruist registreren

Met de release van versie 2.3.1 maakt Commerce nu een apart `cron` -logboek. \
Commerce heeft onlangs de registratie van cron uitgebreid gemaakt, waardoor meer informatie werd verschaft maar de `system.log` aanzienlijk werd verlengd.
Door `cron` info naar een toegewezen logboek te verplaatsen, zijn beide logbestanden gemakkelijker te lezen.

Standaard schrijft Commerce `cron` info naar het `<install-directory>/var/log/cron.log` -bestand.

## Syslog-logboekregistratie

Door gebrek, schrijft Commerce _syslog_ logboeken aan het werkende systeem `syslog` dossier.
Vanaf Commerce 2.3.1 moet u de opdracht `magento` gebruiken om de syslog in of uit te schakelen.
De instelling in het beheerprogramma is verwijderd.

### Om syslog registreren toe te laten

Logboekregistratie naar `syslog` is standaard uitgeschakeld.

1. Gebruik de opdracht `setup:config:set` om de databasewaarde `dev/syslog/syslog_logging` in `true` te wijzigen.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:flush
   ```

### syslog registreren onbruikbaar maken

1. Gebruik de opdracht `setup:config:set` om de databasewaarde `dev/syslog/syslog_logging` in `false` te wijzigen.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:flush
   ```
