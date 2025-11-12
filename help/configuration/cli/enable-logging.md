---
title: Logbestand inschakelen
description: Leer hoe u verschillende typen aanmelding in Adobe Commerce in- en uitschakelt. Ontdek registrerenconfiguratie en beheerstechnieken.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: aff705cefcd4de38d17cad41628bc8dbd6d630cb
workflow-type: tm+mt
source-wordcount: '352'
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

### Opslaglocatie voor query-logboekregistratie

Wanneer databaselogbestanden zijn ingeschakeld, slaat Commerce querylogbestanden op de volgende locatie op:

- **het logboekdossier van de Vraag**: `<install-directory>/var/debug/db.log`
- **folder van het Logboek**: `<install-directory>/var/debug/`

Het querylogboek bevat:
- SQL-query&#39;s uitgevoerd door de toepassing
- Uitvoeringstijden van query
- Parameters en bindingen voor query
- Gegevens databaseverbinding

>[!NOTE]
>
>Het dossier van het vraaglogboek kan snel in hoog-verkeersmilieu&#39;s groeien. De schijfruimte van de monitor en overweegt het uitvoeren van logboekomwenteling of periodieke schoonmaak van het dossier van het vraaglogboek.

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

### Zoeklogs weergeven

U kunt de vraaglogboeken bekijken gebruikend standaarddossier het bekijken bevelen:

```bash
# View the entire query log
cat var/debug/db.log

# View the last 100 lines of the query log
tail -n 100 var/debug/db.log

# Monitor the query log in real-time
tail -f var/debug/db.log

# Search for specific queries
grep "SELECT" var/debug/db.log
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
