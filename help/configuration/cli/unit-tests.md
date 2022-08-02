---
title: Eenheidstests uitvoeren
description: Voer eenheidstests uit die zijn gedefinieerd in de Adobe Commerce-codebasis.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Eenheidstests uitvoeren

{{file-system-owner}}

Dit bevel stelt een reeks tests in werking die in Commerce 2 codebasis worden bepaald. U kunt of alle tests in werking stellen of tests u selecteert. Wanneer een niet-ondersteund type wordt opgegeven, wordt het programma beëindigd en worden alle beschikbare typen weergegeven. Na uitvoering, toont een gedetailleerd rapportvertoningen die de testlooppas en de resultaten tonen.

## Vereisten

Voordat u deze opdracht uitvoert, moet u het volgende doen _moet_ waar zijn:

- De `Magento_Developer` moet zijn ingeschakeld. U kunt deze als volgt inschakelen:

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   Gebruik de `--force` alleen indien dit noodzakelijk is.

- Uw systeem moet zijn ingesteld om de gewenste tests uit te voeren.

Als u bijvoorbeeld integratietests wilt uitvoeren, moet u `dev/tests/integration/etc/install-config-mysql.php.dist` tot `dev/tests/integration/etc/install-config-mysql.php` en aanpassen aan uw omgeving.

## Tests uitvoeren

Opdrachtgebruik:

```bash
bin/magento dev:tests:run <test>
```

U kunt als volgt de beschikbare testtypen weergeven:

```bash
bin/magento dev:tests:run --help
```

Voorbeeld van retournering:

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Bijvoorbeeld om integratietests uit te voeren:

```bash
bin/magento dev:tests:run integration
```
