---
title: Logbestand inschakelen
description: Leer hoe te om types van registreren toe te laten en onbruikbaar te maken.
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Logbestand inschakelen

{{file-system-owner}}

## Foutopsporingsregistratie

Door gebrek, schrijft de Handel aan zuivert logboek (`<install_directory>/var/log/debug.log`) als de standaardmodus is ingeschakeld of de ontwikkelmodus is ingeschakeld, maar niet als de modus productie actief is. Gebruik de `bin/magento setup:config:set --enable-debug-logging` gebruiken om de standaardwaarde te wijzigen.

>[!INFO]
>
>Vanaf Commerce 2.3.1 kunt u niet meer de `bin/magento config:set dev/debug/debug_logging` gebruiken om foutopsporingslogbestanden voor de huidige modus in of uit te schakelen.

### Foutopsporingsregistratie inschakelen

1. Gebruik de `setup:config:set` bevel toe te laten zuivert registreren voor de huidige wijze.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:flush
   ```

### Foutopsporingslogbestand uitschakelen

1. Gebruik de `setup:config:set` bevel om te onbruikbaar maken zuivert registreren voor de huidige wijze.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:flush
   ```

## Logboekregistratie van databases

Door gebrek, schrijft de Handel de logboeken van de gegevensbestandactiviteit aan `<install-dir>/var/debug/db.log` bestand.

### Databaseregistratie inschakelen

1. Gebruik de `dev:query-log` gebruiken om databaselogboekingen in of uit te schakelen.

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

## Cron logging

Met de release van versie 2.3.1 creëert de Commerce nu een aparte versie `cron` log. \
Recentelijk maakte de handel de houtkap breder, die meer informatie verstrekte maar de `system.log` aanzienlijk.
Verplaatsen `cron` info aan een specifiek logboek maakt beide logboeken gemakkelijker te lezen.

Standaard schrijft Commerce `cron` informatie aan de `<install-directory>/var/log/cron.log` bestand.

## Syslog-logboekregistratie

Standaard schrijft Commerce _syslog_ logboeken naar het besturingssysteem `syslog` bestand.
Vanaf Handel 2.3.1 moet u `magento` bevel om syslog toe te laten of onbruikbaar te maken.
De instelling in het beheerprogramma is verwijderd.

### Om syslog registreren toe te laten

Aanmelden bij `syslog` is standaard uitgeschakeld.

1. Gebruik de `setup:config:set` om de `dev/syslog/syslog_logging` databasewaarde naar `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:flush
   ```

### Om syslog registreren onbruikbaar te maken

1. Gebruik de `setup:config:set` om de `dev/syslog/syslog_logging` databasewaarde naar `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Maak de cache leeg.

   ```bash
   bin/magento cache:flush
   ```
