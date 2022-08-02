---
title: Codecompiler
description: Leer hoe te om de codecompiler van de bevellijn in werking te stellen.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Codecompiler

{{file-system-owner}}

De compilatie van de code omvat het volgende (in geen bepaalde orde):

- Toepassingscode genereren (fabrieken, proxy&#39;s)
- Samenvoeging van gebiedconfiguratie (geoptimaliseerd [afhankelijkheidsinjectie](https://glossary.magento.com/dependency-injection) configuraties per gebied)
- Interceptorgeneratie (geoptimaliseerde codering van interceptoren)
- Het produceren van de interceptiecache
- Opslagplaatsen voor het genereren van code (gegenereerde code voor API&#39;s)
- Genereren van servicekenmerken (gegenereerd) [extension](https://glossary.magento.com/extension) klassen voor gegevensobjecten)

U kunt de klassen van de codecompilatie in vinden [\Magento\Setup\Module\Di\App\Task\Operation][operation] naamruimte.

Om de enig-huurderscompiler in werking te stellen:

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Code compileren voordat de toepassing Commerce wordt geïnstalleerd:

In sommige gevallen, zou u code kunnen willen compileren alvorens u de toepassing van de Handel installeert.

1. Schakel de modules in.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Gebruik de `[-c|--clear-static-content]` optie voor wissen [statische inhoud](https://glossary.magento.com/static-content). Dit is nodig als u eerder modules hebt in- of uitgeschakeld en u de statische inhoud moet wissen die eerder voor deze modules is gegenereerd.

   Zie [Modules inschakelen](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html).

1. Compileer de code.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

Als u code zonder database wilt compileren, raadpleegt u [Statische weergavebestanden implementeren zonder Magento te installeren](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
