---
title: Codecompiler
description: Leer hoe u de Adobe Commerce-codecompiler uitvoert vanaf de opdrachtregel. Ontdek compilatieprocessen en optimalisatietechnieken.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '169'
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

U kunt de klassen van de codecompilatie in [ \Magento\Setup\Module\Di\App\Task\Operation ](https://github.com/magento/magento2/blob/2.4.8/setup/src/Magento/Setup/Module/Di/App/Task/Operation) namespace vinden.

Om de enig-huurderscompiler in werking te stellen:

```bash
bin/magento setup:di:compile
```

```
Generated code and dependency injection configuration successfully.
```

U kunt als volgt de code compileren voordat u de Commerce-toepassing installeert:

In sommige gevallen kunt u code compileren voordat u de Commerce-toepassing installeert.

1. Schakel de modules in.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Gebruik de optie `[-c|--clear-static-content]` om statische inhoud te wissen. Dit is nodig als u eerder modules hebt in- of uitgeschakeld en u de statische inhoud moet wissen die eerder voor deze modules is gegenereerd.

   Zie [ modules ](../../installation/tutorials/manage-modules.md) toelaten.

1. Compileer de code.

   ```bash
   bin/magento setup:di:compile
   ```

   ```
   Generated code and dependency injection configuration successfully.
   ```

Om code zonder een gegevensbestand te compileren, zie [ statische meningsdossiers opstellen zonder Magento ](../cli/static-view-file-deployment.md) te installeren.

