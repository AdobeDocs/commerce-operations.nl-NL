---
title: Algemene opdrachten
description: Meer informatie over algemene Adobe Commerce CLI-opdrachten en hun gebruiksvoorbeelden. Ontdek essentiële opdrachtregelprogramma's voor ontwikkeling en administratie.
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Algemene opdrachten

Hieronder volgt een overzicht van enkele beschikbare opdrachten.

**om een volledige lijst van bevelen** te tonen:

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

De bevelen worden getoond in summiere vorm slechts; voor meer informatie over een bevel, klik de verbinding in de kolom van het Bevel.

| Opdracht | Beschrijving |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | De cache beheren |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Beheert de indexen |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Hiermee worden Commerce-snijtaken uitgevoerd |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Hiermee worden alle niet-bestaande proxy&#39;s en fabrieken gecompileerd en worden klassendefinities, overervingsgegevens en plug-indefinities voor één winkel en website vooraf gecompileerd. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | De gebiedsdelen van de module, kringafhankelijkheden, en het kadergebiedsdelen van Commerce. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Maakt een vertaalwoordenboek of een vertaalpakket |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Statische weergavebestanden gebruiken |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Maakt CSS van MINDER |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Voert geautomatiseerde tests uit |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Werk uw lay-outXML dossiers bij om de nieuwe Verlengbare stijlpagina van de Transformaties van de Taal van Stylesheet (XSLT) aan te passen |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Gegevens genereren om te gebruiken voor het testen van de prestaties. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Hiermee installeert u optionele voorbeeldgegevens nadat u de Commerce-toepassing hebt geïnstalleerd.<br><br> voor meer details over steekproefgegevens, zie [&#x200B; Facultatieve steekproefgegevens &#x200B;](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Beheert back-endconfiguraties |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Hiermee maakt u beheergebruikers, bewerkt of ontgrendelt u deze. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Hiermee schakelt u tips voor ontwikkelaarsjablonen in of uit. |

## Algemene argumenten

De volgende argumenten zijn gemeenschappelijk aan [&#x200B; alle bevelen &#x200B;](/help/tools/reference/commerce-on-premises.md). Deze opdrachten kunnen worden uitgevoerd vóór of nadat de Commerce-software is geïnstalleerd:

| Lange versie | Korte versie | Betekenis |
|--- |--- |--- |
| `--help` | `-h` | Krijg hulp voor om het even welk bevel. Bijvoorbeeld `./magento help setup:install` of `./magento help setup:config:set` . |
| `--quiet` | `-q` | Stille modus; geen uitvoer. |
| `--no-interaction` | `-n` | Geen interactieve vragen. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Verbositeitsniveau. `--verbose=3` of `-vvv` geeft bijvoorbeeld een uitgebreide foutopsporing weer. Dit is de meest uitgebreide uitvoer. De standaardwaarde is `--verbose=1` of `-v` . |
| `--version` | `-V` | Deze toepassingsversie weergeven |
| `--ansi` | nvt | ANSI-uitvoer forceren |
| `--no-ansi` | nvt | ANSI-uitvoer uitschakelen |
