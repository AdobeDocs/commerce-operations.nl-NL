---
title: Eenheidstests uitvoeren
description: Voer eenheidstests uit die zijn gedefinieerd in de Adobe Commerce-codebasis.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Eenheidstests uitvoeren

{{file-system-owner}}

Deze opdracht voert een set tests uit die in de Commerce 2-codebasis zijn gedefinieerd. U kunt of alle tests in werking stellen of tests u selecteert. Wanneer een niet-ondersteund type wordt opgegeven, wordt het programma beëindigd en worden alle beschikbare typen weergegeven. Na uitvoering, toont een gedetailleerd rapportvertoningen die de testlooppas en de resultaten tonen.

## Vereisten

Alvorens u dit bevel in werking stelt, moet het volgende __ waar zijn:

- De module `Magento_Developer` moet zijn ingeschakeld. U kunt deze als volgt inschakelen:

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  Gebruik de optie `--force` alleen als dit nodig is.

- Uw systeem moet zijn ingesteld om de gewenste tests uit te voeren.

Als u bijvoorbeeld integratietests wilt uitvoeren, moet u `dev/tests/integration/etc/install-config-mysql.php.dist` naar `dev/tests/integration/etc/install-config-mysql.php` kopiëren en deze aanpassen aan uw omgeving.

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

```
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Bijvoorbeeld om integratietests uit te voeren:

```bash
bin/magento dev:tests:run integration
```
