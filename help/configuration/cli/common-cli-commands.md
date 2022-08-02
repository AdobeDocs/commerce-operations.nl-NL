---
title: Algemene opdrachten
description: Bekijk een steekproef van gemeenschappelijke bevelen en gebruik van de Handel CLI.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 0%

---


# Algemene opdrachten

Hieronder volgt een overzicht van enkele beschikbare opdrachten.

**Een volledige lijst met opdrachten weergeven**:

```bash
bin/magento list
```

Voorbeeld van Help, opdracht:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

Opdrachten worden alleen in samengevatte vorm weergegeven. voor meer informatie over een bevel, klik de verbinding in de kolom van het Bevel.

| Opdracht | Beschrijving |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | De cache beheren |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Beheert de indexen |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Hiermee worden Cron-banen uitgevoerd |
| [`magento setup:di:compile`](../cli/code-compiler.md) | alle niet-bestaande proxy&#39;s en fabrieken samenstelt; en compileert vooraf klassendefinities, overervingsinformatie, en insteekdefinities voor één opslag en website. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | De gebiedsdelen van de module, kringafhankelijkheden, en het kadergebiedsdelen van de Handel. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Maakt een vertaalwoordenboek of een vertaalpakket |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Statische weergavebestanden gebruiken |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Maakt CSS van MINDER |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Voert geautomatiseerde tests uit |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Werk uw lay-outXML dossiers bij om de nieuwe Verlengbare stijlpagina van de Transformaties van de Taal van Stylesheet (XSLT) aan te passen |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Gegevens genereren om te gebruiken voor het testen van de prestaties. |
| [`magento sampledata:install`](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html) | Hiermee installeert u optionele voorbeeldgegevens nadat u de toepassing Commerce hebt geïnstalleerd.<br><br>Zie voor meer informatie over voorbeeldgegevens [Optionele voorbeeldgegevens](https://devdocs.magento.com/guides/v2.4/install-gde/install/sample-data.html). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Beheert back-endconfiguraties |
| [`magento admin:user:{create/unlock}`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-admin.html) | Hiermee maakt u beheergebruikers, bewerkt of ontgrendelt u deze. |
| [`magento dev:template-hints:{enable/disable}`](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/themes/debug-theme.html) | Hiermee schakelt u tips voor ontwikkelaarsjablonen in of uit. |

## Algemene argumenten

De volgende argumenten gelden voor alle opdrachten. Deze bevelen kunnen of vóór of na de software van de Handel worden in werking gesteld:

| Lange versie | Korte versie | Betekenis |
|--- |--- |--- |
| `--help` | `-h` | Krijg hulp voor om het even welk bevel. Bijvoorbeeld: `./magento help setup:install` of `./magento help setup:config:set`. |
| `--quiet` | `-q` | stille modus; geen uitvoer. |
| `--no-interaction` | `-n` | Geen interactieve vragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Verbositeitsniveau. Bijvoorbeeld: `--verbose=3` of `-vvv` vertoningen zuiveren breedtegraad, die de breedste output is. Standaard is `--verbose=1` of `-v`. |
| `--version` | `-V` | Deze toepassingsversie weergeven |
| `--ansi` | n.v.t. | ANSI-uitvoer forceren |
| `--no-ansi` | n.v.t. | ANSI-uitvoer uitschakelen |
