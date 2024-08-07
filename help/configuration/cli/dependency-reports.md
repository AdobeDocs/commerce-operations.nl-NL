---
title: Afhankelijkheidsrapporten
description: Creeer rapporten die de totalen voor module, kringafhankelijkheden, en kadergebiedsdelen tonen.
exl-id: b7a32fe1-71c5-495f-8276-242503fb50ae
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Afhankelijkheidsrapporten

{{file-system-owner}}

U kunt de volgende typen rapporten uitvoeren:

- **de gebiedsdelen van de Module**: Toont het totale aantal gebiedsdelen tussen modules en of de gebiedsdelen hard of zacht zijn.
- **Cirkelgebiedsdelen**: Toont het totale aantal gebiedsketens en het aantal en de lijst van cirkelgebiedsdelen voor elke module.
- **gebiedsdelen van het Kader**: Toont het totale aantal gebiedsdelen op het kader van Commerce door module (met inbegrip van het totale aantal kaderingangen voor elke bibliotheek).

Een afhankelijkheid in een opmerking is ook een afhankelijkheid.

## Afhankelijkheidsrapporten uitvoeren

Opdrachtopties:

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

In de volgende tabel worden de opties, parameters en waarden van deze opdracht uitgelegd.

| Parameter | Waarde | Vereist? |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | Rapport voor moduleafhankelijkheden. | Ja |
| `show-modules-circular` | Cirkelafhankelijkheidsrapport. | Ja |
| `show-framework` | Rapport over frameafhankelijkheden. | Ja |
| `-d --directory` | Pad naar de basismap om te zoeken naar rapportgegevens. | Nee |
| `-o --output` | Specificeert de absolute weg van het dossiersysteem en de dossiernaam van het komma-gescheiden waarde (csv) outputdossier voor het rapport. | Nee |

Als er geen map of bestandsnaam als argument wordt doorgegeven, wordt de volgende hoofdmap van de toepassing gebruikt als de standaardmap en worden de volgende standaardbestandsnamen gebruikt:

| Opdracht | Bestandsnaam |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### Rapport voor afhankelijkheden van de module Voorbeeld

Het volgende is een gedeelte van de output voor een rapport van de gebiedsdelen van de steekproefmodule:

```
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### Voorbeeld van cirkelafhankelijkheidsrapport

Het volgende is een gedeelte van de output voor een steekproef cirkelafhankelijkheidsrapport:

```
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### Voorbeeld van rapport over frameafhankelijkheden

Het volgende is een deel van de output voor een rapport van de gebiedsdelen van het steekproefkader:

```
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
