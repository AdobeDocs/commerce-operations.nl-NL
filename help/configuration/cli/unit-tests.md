---
title: Eenheidstests uitvoeren
description: Leer hoe u eenheidstests uitvoert die zijn gedefinieerd in de Adobe Commerce-codebase. Ontdek testopdrachten, uitvoeringsopties en resultaatrapportage.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Eenheidstests uitvoeren

{{file-system-owner}}

Deze opdracht voert een set tests uit die in de Commerce 2-codebasis zijn gedefinieerd. U kunt of alle tests in werking stellen of tests u selecteert. Wanneer een niet-ondersteund type wordt opgegeven, wordt het programma beëindigd en worden alle beschikbare typen weergegeven. Na uitvoering, toont een gedetailleerd rapportvertoningen die de testlooppas en de resultaten tonen.

## Vereisten

Alvorens u dit bevel in werking stelt, moet het volgende __ waar zijn:

- De module `Magento_Developer` moet zijn ingeschakeld. U kunt deze als volgt inschakelen:

  ```shell
  bin/magento module:enable [--force] Magento_Developer
  ```

  Gebruik de optie `--force` alleen als dit nodig is.

- Uw systeem moet zijn ingesteld om de gewenste tests uit te voeren.

Als u bijvoorbeeld integratietests wilt uitvoeren, moet u `dev/tests/integration/etc/install-config-mysql.php.dist` naar `dev/tests/integration/etc/install-config-mysql.php` kopiëren en deze aanpassen aan uw omgeving.

## Tests uitvoeren

Opdrachtgebruik:

```shell
bin/magento dev:tests:run <test>
```

U kunt als volgt de beschikbare testtypen weergeven:

```shell
bin/magento dev:tests:run --help
```

Voorbeeld van retournering:

```text
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Bijvoorbeeld om integratietests uit te voeren:

```shell
bin/magento dev:tests:run integration
```
