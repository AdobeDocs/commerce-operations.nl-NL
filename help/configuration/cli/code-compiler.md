---
title: Codecompiler
description: Leer hoe te om de codecompiler van de bevellijn in werking te stellen.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---


# Codecompiler

{{file-system-owner}}

De compilatie van de code omvat het volgende (in geen bepaalde orde):

- Toepassingscode genereren (fabrieken, proxy&#39;s)
- Samenvoeging van gebiedconfiguratie (geoptimaliseerde configuraties voor afhankelijkheidsinjectie per gebied)
- Interceptorgeneratie (geoptimaliseerde codering van interceptoren)
- Het produceren van de interceptiecache
- Opslagplaatsen voor het genereren van code (gegenereerde code voor API&#39;s)
- De gegevensattributen van de dienst produceren (geproduceerde uitbreidingsklassen voor gegevensvoorwerpen)

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

   Gebruik de `[-c|--clear-static-content]` optie om statische inhoud te wissen. Dit is nodig als u eerder modules hebt in- of uitgeschakeld en u de statische inhoud moet wissen die eerder voor deze modules is gegenereerd.

   Zie [Modules inschakelen](../../installation/tutorials/manage-modules.md).

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
