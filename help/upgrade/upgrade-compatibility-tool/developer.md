---
title: '"[!DNL Upgrade Compatibility Tool] Informatie over ontwikkelaar"'
description: De [!DNL Upgrade Compatibility Tool] de API-indexintegratie gebruiken.
source-git-commit: 317a044e66fe796ff66b9d8cf7b308f741eb82c1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# [!DNL Upgrade Compatibility Tool] ontwikkelaarsinformatie

{{commerce-only}

Dit onderwerp bevat informatie voor ontwikkelaars die nauw met de code van Adobe Commerce samenwerken en gedetailleerde informatie over willen leren [!DNL Upgrade Compatibility Tool]. U kunt deze kennis gebruiken om de componenten van het gereedschap aan te passen.

## Integratie van Adobe Commerce API-index

Adobe Commerce API indexintegratie is een interne integratieoplossing die een reeks hulpmiddelen omvat om de uitbreidingen van Adobe Commerce te onderzoeken die door Adobe, de Partners van Adobe Commerce, en derdeverkopers worden ontwikkeld die op statische codeanalyse worden gebaseerd.

De integratie met de Adobe Commerce API-index gebeurt via:

`sut\Domain\MRay\MRayInterface`

Het wordt uitgevoerd via de `config/services.yaml` bestand. De waarde ervan bepaalt waar de reactie van methoden plaatsvindt `api()` en `modules()` komt van.

Bewerk dit bestand om de reactie aan te passen aan uw installatie. Vervang de waarde die is toegewezen aan `sut\Domain\MRay\MRayInterface`:

### Voorbeeld van een aangepaste waarde

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

In het vorige voorbeeld wordt [!DNL Upgrade Compatibility Tool] gebruik `@sut_mray_mock` als de `MRayInterface` uitvoering. De reacties van de `api()` en `modules()` methoden zijn afkomstig uit de volgende bestanden:

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>Wanneer u de `services.yaml` bestand verwijderen `var/cache/` om de wijzigingen correct toe te passen.

## Eenheid testen

Voer een van de volgende opdrachten uit om de eenheidstests uit te voeren:

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## Integratie testen

Voer een van de volgende opdrachten uit om de integratietests uit te voeren:

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## Acceptatietest

1. Voordat u acceptatietests uitvoert, moet u de Adobe Commerce-URL instellen in het dialoogvenster `phpunit` configuratiebestand.
1. De standaardinstelling kopiëren `tests/acceptance/phpunit.xml` bestand (zonder het achtervoegsel .dist).
1. Wijzig de `TESTS_BASE_URL` Geef een waarde op die verwijst naar de Adobe Commerce-URL die u wilt testen.
1. Voer een van de volgende opdrachten uit om de acceptatietests uit te voeren:

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## GraphQL-eenheidstests en ESLint-codeanalyse

### Vereisten

>[!NOTE]
>
>U moet Node.js op uw systeem hebben, zie [Node.js-documentatie](https://nodejs.dev/learn/how-to-install-nodejs).

De volgende instructies gelden voor MacOS-systemen:

1. Open een terminal en navigeer naar de hoofdmap van het project.
1. Projectafhankelijkheden installeren:

   ```bash
   npm install
   ```

### GrafiekQL-eenheidstests

De [Jest](https://jestjs.io/docs/getting-started) framework is gebruikt om deze JS-eenheidstests te maken:

De tests bevinden zich in `dev/tests/Js`.

De tekenreeksschema&#39;s voor testen bevinden zich binnen `dev/tests/Acceptance/_files/graphql_schemas`.

Eenheidstests uitvoeren of `jest` als volgt:

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### ESLint-codeanalyse

[ESLint](https://eslint.org/docs/user-guide/getting-started) is een statisch hulpmiddel voor codeanalyse voor het identificeren van problematische patronen die in code JavaScript worden gevonden, met het doel code consistenter te maken en insecten te vermijden.

Uitvoeren `eslint` codeanalyse als volgt:

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## Complexiteit score

De **complexiteitsscore** is een cijfer dat erop wijst hoe moeilijk een verbetering van de huidige versie aan nieuwe zou kunnen zijn. Lagere nummers geven aan dat upgrades eenvoudiger zijn.

>[!NOTE]
>
>Complexiteit scores liggen tussen 0 en∞.

Deze score is gebaseerd op de resultaten van de analyse:

- Aantal geconstateerde problemen
- Ernst van de geconstateerde problemen

De [!DNL Upgrade Compatibility Tool] berekent deze score op basis van de onderstaande formule voor de score &#39;complexiteit&#39;.

### Complexiteit score-formule

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>Dit zijn absolute waarden.