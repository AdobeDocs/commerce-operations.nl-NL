---
title: Modules in- of uitschakelen
description: Voer de volgende stappen uit om Adobe Commerce-modules te beheren.
exl-id: 7155950a-a66a-4254-a71c-1a9aeab47606
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '572'
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

* In `--enabled` worden alle ingeschakelde modules weergegeven.
* In `--disabled` worden alle uitgeschakelde modules weergegeven.
* `<module-list>` is een door spaties gescheiden lijst met modules om de status te controleren. Als een modulenaam speciale tekens bevat, plaatst u de naam tussen enkele of dubbele aanhalingstekens.

>[!NOTE]
>
>U kunt modules niet direct op wolkenprojecten toelaten of onbruikbaar maken. U moet deze opdrachten lokaal uitvoeren en vervolgens wijzigingen in het `app/etc/config.php` -bestand doorvoeren voor een omgeving. Zie [&#x200B; Pro projectwerkschema: Het werkschema van de Plaatsing &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=nl-NL#deployment-workflow).

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
* `--all` om alle modules tegelijkertijd in of uit te schakelen.
* `-f` of `--force` gebruiken om een module in- of uit te schakelen ondanks afhankelijkheden. Alvorens u deze optie gebruikt, zie [&#x200B; Ongeveer toelatend en onbruikbaar makend modules &#x200B;](#about-enabling-and-disabling-modules).
* `-c` of `--clear-static-content` ontruimt [&#x200B; geproduceerde statische meningsdossiers &#x200B;](../../configuration/cli/static-view-file-deployment.md).

  Als u statische weergavebestanden niet wist, kunnen er problemen optreden als er meerdere bestanden met dezelfde naam zijn en u niet alle bestanden wist.

  Met andere woorden, wegens de [&#x200B; statische dossierreserve &#x200B;](../../configuration/cli/static-view-file-deployment.md) regels, als u geen statische dossiers ontruimt en er meer dan één dossier genoemd `logo.svg` is die verschillend zijn, zou de reserve het verkeerde dossier aan vertoning kunnen veroorzaken.

Als u bijvoorbeeld de module `Magento_Weee` wilt uitschakelen, voert u het volgende in:

```bash
bin/magento module:disable Magento_Weee
```

Voor belangrijke informatie over het toelaten van en het onbruikbaar maken van modules, zie [&#x200B; over het toelaten van en het onbruikbaar maken van modules &#x200B;](#about-enabling-and-disabling-modules).

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

Met Adobe Commerce kunt u de momenteel beschikbare modules in- of uitschakelen, met andere woorden elke module die door Adobe wordt geleverd of elke andere module die momenteel beschikbaar is.

Bepaalde modules hebben gebiedsdelen op andere modules, in welk geval u een module zou kunnen niet toelaten of onbruikbaar maken omdat het gebiedsdelen op andere modules heeft.

Bovendien zou er *het in conflict brengen* modules kunnen zijn die niet allebei kunnen tezelfdertijd worden toegelaten.

Voorbeelden:

* Module A is afhankelijk van module B. U kunt Module B niet onbruikbaar maken tenzij u eerst Module A onbruikbaar maakt.

* Module A is afhankelijk van module B, die beide zijn uitgeschakeld. U moet module B toelaten alvorens u module A kunt toelaten.

* Module A veroorzaakt een conflict met module B. U kunt Module A en Module B onbruikbaar maken, of u kunt één van beide module onbruikbaar maken maar u *kunt niet* module A en Module B tezelfdertijd toelaten.

* Afhankelijkheden worden voor elke module gedeclareerd in het veld `require` in het Adobe Commerce `composer.json` -bestand. Conflicten worden gedeclareerd in het veld `conflict` in de `composer.json` -bestanden van modules. Deze informatie wordt gebruikt om een afhankelijkheidsgrafiek samen te stellen: `A->B` betekent dat module A afhankelijk is van module B.

* A *gebiedsdeelketen* is de weg van een module aan een andere. Als module A bijvoorbeeld afhankelijk is van module B en module B van module C, is de afhankelijkheidsketen `A->B->C` .

Als u probeert om een module toe te laten of onbruikbaar te maken die van andere modules afhangt, toont de gebiedsdeelgrafiek in het foutenbericht.

>[!NOTE]
>
>Het is mogelijk dat module A `composer.json` een conflict met module B maar niet omgekeerd verklaart.

*lijn van het Bevel slechts:* om een module te dwingen om ongeacht zijn gebiedsdelen worden toegelaten of worden onbruikbaar gemaakt, gebruik het facultatieve `--force` argument.

>[!NOTE]
>
>Als u `--force` gebruikt, kan de winkel worden uitgeschakeld en kunnen er problemen optreden bij de toegang tot de beheerder.
