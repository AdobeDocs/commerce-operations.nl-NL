---
title: Modules in- of uitschakelen
description: Voer de volgende stappen uit om Adobe Commerce- of Magento Open Source-modules te beheren.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: 6e87d68df97adf47b5a61e8b6683ac11f600806c
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# Modules in- of uitschakelen

Deze opdracht heeft geen voorwaarden.

## Modulestatus

Gebruik het volgende bevel om toegelaten en gehandicapte modules een lijst te maken:

```bash
bin/magento module:status [--enabled] [--disabled] <module-list>
```

Wanneer

* `--enabled` maakt een lijst van alle toegelaten modules.
* `--disabled` Hiermee geeft u alle uitgeschakelde modules weer.
* `<module-list>` is een door spaties gescheiden lijst met modules om de status te controleren. Als een modulenaam speciale tekens bevat, plaatst u de naam tussen enkele of dubbele aanhalingstekens.

>[!NOTE]
>
>U kunt modules niet direct op wolkenprojecten toelaten of onbruikbaar maken. U moet deze opdrachten lokaal uitvoeren en vervolgens wijzigingen aanbrengen in het dialoogvenster `app/etc/config.php` bestand voor een omgeving. Zie [Workflow voor Pro-projecten: implementatieworkflow](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html#deployment-workflow).

## Module in-/uitschakelen

Om beschikbare modules toe te laten of onbruikbaar te maken, gebruik het volgende bevel:

```bash
bin/magento module:enable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

```bash
bin/magento module:disable [-c|--clear-static-content] [-f|--force] [--all] <module-list>
```

Wanneer

* `<module-list>` is een door spaties gescheiden lijst met modules die moeten worden in- of uitgeschakeld. Als een modulenaam speciale tekens bevat, plaatst u de naam tussen enkele of dubbele aanhalingstekens.
* `--all` om alle modules tezelfdertijd in of onbruikbaar te maken.
* `-f` of `--force` om een module te dwingen om ondanks gebiedsdelen worden toegelaten of worden onbruikbaar gemaakt. Voordat u deze optie gebruikt, raadpleegt u [Modules in- en uitschakelen](#about-enabling-and-disabling-modules).
* `-c` of `--clear-static-content` cleans [gegenereerde statische weergavebestanden](../../configuration/cli/static-view-file-deployment.md).

  Als u statische weergavebestanden niet wist, kunnen er problemen optreden als er meerdere bestanden met dezelfde naam zijn en u niet alle bestanden wist.

  Met andere woorden, vanwege de [fallback van statische bestanden](../../configuration/cli/static-view-file-deployment.md) regels, als u statische bestanden niet wist en er meerdere bestanden zijn met de naam `logo.svg` anders, zou de reserve het verkeerde dossier kunnen veroorzaken om te tonen.

Als u bijvoorbeeld de opdracht `Magento_Weee` -module, voert u in:

```bash
bin/magento module:disable Magento_Weee
```

Voor belangrijke informatie over het toelaten van en het onbruikbaar maken van modules, zie [Modules in- en uitschakelen](#about-enabling-and-disabling-modules).

## De database bijwerken

Als u een of meer modules hebt ingeschakeld, voert u de volgende opdracht uit om de database bij te werken:

```bash
bin/magento setup:upgrade
```

Maak vervolgens de cache schoon:

```bash
bin/magento cache:clean
```

## Modules in- en uitschakelen

Met Adobe Commerce en Magento Open Source kunt u de momenteel beschikbare modules in- of uitschakelen, met andere woorden elke module die door Adoben wordt geleverd of elke andere module die momenteel beschikbaar is.

Bepaalde modules hebben gebiedsdelen op andere modules, in welk geval u een module zou kunnen niet toelaten of onbruikbaar maken omdat het gebiedsdelen op andere modules heeft.

Bovendien kunnen er *conflicteren* modules die niet tegelijkertijd kunnen worden ingeschakeld.

Voorbeelden:

* Module A is afhankelijk van module B. U kunt Module B niet onbruikbaar maken tenzij u eerst Module A onbruikbaar maakt.

* Module A is afhankelijk van module B, die beide zijn uitgeschakeld. U moet module B toelaten alvorens u module A kunt toelaten.

* Module A veroorzaakt een conflict met module B. U kunt Module A en Module B onbruikbaar maken, of u kunt één van beide module onbruikbaar maken maar u *kan* Module A en Module B tegelijkertijd inschakelen.

* Afhankelijkheden worden gedeclareerd in het dialoogvenster `require` veld in Adobe Commerce en Magento Open Source `composer.json` bestand voor elke module. Conflicten worden gedeclareerd in de `conflict` veld in modules&quot; `composer.json` bestanden. Wij gebruiken die informatie om een gebiedsdeelgrafiek te bouwen: `A->B` betekent module A afhankelijk is van module B.

* A *afhankelijkheidsketen* Dit is het pad van een module naar een andere module. Bijvoorbeeld, als module A van module B en module B van module C afhangt, dan is de gebiedsdeelketen `A->B->C`.

Als u probeert om een module toe te laten of onbruikbaar te maken die van andere modules afhangt, toont de gebiedsdeelgrafiek in het foutenbericht.

>[!NOTE]
>
>Het is mogelijk dat module A&#39;s `composer.json` declareert een conflict met module B, maar niet omgekeerd.

*Alleen opdrachtregel:* Als u een module wilt inschakelen of uitschakelen, ongeacht de afhankelijkheden, gebruikt u de optie `--force` argument.

>[!NOTE]
>
>Gebruiken `--force` kan uw winkel uitschakelen en problemen met de beheerfunctie veroorzaken.
