---
title: Aanbevolen werkwijzen voor het verwerken van uitzonderingen
description: Leer de geadviseerde methodes om uitzonderingen te registreren wanneer het ontwikkelen van de projecten van Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor het verwerken van uitzonderingen

Als een uitzondering niet naar de `exception.log` bestand met als uitzondering het model context, wordt het niet herkend en correct geanalyseerd in New Relic of andere PSR-3 monoloog-compatibele logboekopslag. Het registreren slechts een deel van de uitzondering (of het registreren van het aan het verkeerde dossier) leidt tot insecten in productie wanneer de uitzonderingen worden genegeerd.

## Uitzonderingsverwerking corrigeren

De volgende controlelijst verstrekt voorbeelden om correcte uitzonderingsbehandeling aan te tonen.

### ![correct](../../../assets/yes.svg) Schrijf aan het uitzonderingslogboek

Schrijf aan het uitzonderingslogboek gebruikend het volgende patroon, ongeacht verdere acties, tenzij er een dwingende reden is om niet te doen.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Deze aanpak slaat automatisch de `$e->getMessage` aan het logboekbericht en de `$e` object naar de context, na de [PSR-3 contextstandaard](https://www.php-fig.org/psr/psr-3/#13-context). Dit wordt gedaan in `\Magento\Framework\Logger\Monolog::addRecord`.

### ![correct](../../../assets/yes.svg) Signalen dempen

De signalen van de demping door uitzonderingen niet te registreren die deel van de voorgenomen verrichtingenstroom uitmaken. Er is geen follow-upactie nodig wanneer de uitzondering wordt aangetroffen, dus deze hoeft niet te worden geregistreerd en geanalyseerd wanneer deze zich voordoet. Voeg een opmerking toe die de reden voor het dempen van signalen aangeeft en die aangeeft dat dit opzettelijk is. Combineren met `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![correct](../../../assets/yes.svg) Uitzonderingen downgraden

De uitzonderingen van de downgrade door te volgen [PSR-3 contextstandaard](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![correct](../../../assets/yes.svg) Logboekregistratie is altijd de eerste

Als beste praktijk komt het registreren altijd eerst in de code om gevallen te verhinderen waar een andere uitzondering of een fatale fout alvorens aan het logboek wordt geworpen.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![correct](../../../assets/yes.svg) Logberichten en het volledige uitzonderingsspoor

De berichten van het logboek en het volledige uitzonderingsspoor door te volgen [PSR-3 contextstandaard](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Onjuiste uitzonderingsverwerking

In de volgende voorbeelden wordt een onjuiste afhandeling van uitzonderingen getoond.

### ![onjuist](../../../assets/no.svg) Logica voor logboekregistratie

De logica vóór registreren kan tot een andere uitzondering of fatale fout leiden, die de uitzondering verhindert worden geregistreerd en zou moeten worden vervangen door [correct voorbeeld](#correct-logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![onjuist](../../../assets/no.svg) Leeg `catch`

Leeg `catch` blokken kunnen een teken zijn van onbedoeld dempen en moeten worden vervangen door de [correct voorbeeld](#correct-mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![onjuist](../../../assets/no.svg) Dubbele lokalisatie

Als de gevangen gelokaliseerde uitzondering nog niet wordt vertaald, los het probleem op de plaats op waar de uitzondering de eerste keer wordt geworpen.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![onjuist](../../../assets/no.svg) Logberichten en tracering naar verschillende logbestanden

In de volgende code wordt de stacktracering voor een uitzondering verkeerd als een tekenreeks naar een logbestand geregistreerd.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

Deze benadering introduceert lijnonderbrekingen in het bericht, dat niet volgzaam met PSR-3 is. De uitzondering, met inbegrip van stapelspoor, moet deel van de berichtcontext uitmaken om ervoor te zorgen dat het correct met het bericht in New Relic of andere PSR-3 monolog-compatibele logboekopslag wordt bewaard.

Los dit probleem door de code te vervangen die de correcte die voorbeelden volgt in worden getoond [Schrijf aan het uitzonderingslogboek](#correct-write-to-the-exception-log) of [Uitzonderingen downgraden](#correct-downgrade-exceptions).

### ![onjuist](../../../assets/no.svg) Uitzonderingen downgraden zonder context

De uitzondering wordt gedowngraded naar een fout, die niet toestaat dat een object wordt doorgegeven, maar alleen een tekenreeks, vandaar de `getMessage()`. Hierdoor gaat het spoor verloren en moet het worden vervangen door de juiste voorbeelden in [Schrijf aan het uitzonderingslogboek](#correct-write-to-the-exception-log) of [Uitzonderingen downgraden](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![onjuist](../../../assets/no.svg) Logboek slechts het bericht aan het uitzonderingslogboek

In plaats van het object door te geven `$e`, alleen `$e->getMessage()` wordt doorgegeven. Dit veroorzaakt dat het spoor wordt verloren en zou door de correcte getoonde voorbeelden moeten worden vervangen [Schrijf aan het uitzonderingslogboek](#correct-write-to-the-exception-log) of [Uitzonderingen downgraden](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![onjuist](../../../assets/no.svg) Ontbreekt `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Het weglaten van `phpcs:ignore` De lijn brengt een waarschuwing in PHPCS teweeg en zou niet uw CI moeten overgaan. Deze moet worden vervangen door het juiste voorbeeld in [Signalen dempen](#correct-mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
