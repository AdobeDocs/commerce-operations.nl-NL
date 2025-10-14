---
title: Aanbevolen werkwijzen voor het verwerken van uitzonderingen
description: Leer de geadviseerde methodes om uitzonderingen te registreren wanneer het ontwikkelen van de projecten van Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor het verwerken van uitzonderingen

Als een uitzondering niet naar het `exception.log` dossier met het uitzonderingsmodel als context wordt geschreven, wordt het niet erkend en correct geanalyseerd in New Relic of andere PSR-3 monolog-compatibele logboekopslag. Het registreren slechts een deel van de uitzondering (of het registreren van het aan het verkeerde dossier) leidt tot insecten in productie wanneer de uitzonderingen worden genegeerd.

## Uitzonderingsverwerking corrigeren

De volgende controlelijst verstrekt voorbeelden om correcte uitzonderingsbehandeling aan te tonen.

### ![&#x200B; correct &#x200B;](../../../assets/yes.svg) schrijft aan het uitzonderingslogboek

Schrijf aan het uitzonderingslogboek gebruikend het volgende patroon, ongeacht verdere acties, tenzij er een dwingende reden is om niet te doen.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Deze benadering bewaart automatisch `$e->getMessage` aan het logboekbericht en het `$e` voorwerp aan de context, na [&#x200B; PSR-3 contextstandaard &#x200B;](https://www.php-fig.org/psr/psr-3/#13-context). Dit gebeurt in `\Magento\Framework\Logger\Monolog::addRecord` .

### ![&#x200B; correcte &#x200B;](../../../assets/yes.svg) Geluidssignalen dempen

De signalen van de demping door uitzonderingen niet te registreren die deel van de voorgenomen verrichtingenstroom uitmaken. Er is geen follow-upactie nodig wanneer de uitzondering wordt aangetroffen, dus deze hoeft niet te worden geregistreerd en geanalyseerd wanneer deze zich voordoet. Voeg een opmerking toe die de reden voor het dempen van signalen aangeeft en die aangeeft dat dit opzettelijk is. Combineer met `phpcs:ignore` .

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![&#x200B; correcte &#x200B;](../../../assets/yes.svg) uitzonderingen van de Ondergraving

De uitzonderingen van de daling door [&#x200B; PSR-3 contextstandaard &#x200B;](https://www.php-fig.org/psr/psr-3/#13-context) te volgen.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![&#x200B; correct &#x200B;](../../../assets/yes.svg) het Registreren komt altijd eerst

Als beste praktijk komt het registreren altijd eerst in de code om gevallen te verhinderen waar een andere uitzondering of een fatale fout alvorens aan het logboek wordt geworpen.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![&#x200B; correcte &#x200B;](../../../assets/yes.svg) berichten van het Logboek en het volledige uitzonderingsspoor

De berichten van het logboek en het volledige uitzonderingsspoor door [&#x200B; PSR-3 contextstandaard &#x200B;](https://www.php-fig.org/psr/psr-3/#13-context) te volgen.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Onjuiste uitzonderingsverwerking

In de volgende voorbeelden wordt een onjuiste afhandeling van uitzonderingen getoond.

### ![&#x200B; onjuiste &#x200B;](../../../assets/no.svg) Logica alvorens te registreren

De logica vóór het registreren kan tot een andere uitzondering of fatale fout leiden, die de uitzondering verhindert worden geregistreerd en zou door [&#x200B; correct voorbeeld &#x200B;](#logging-always-comes-first) moeten worden vervangen.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![&#x200B; onjuist &#x200B;](../../../assets/no.svg) Leeg `catch`

Lege `catch` blokken kunnen een teken van onbedoeld dempen zijn en zouden door het [&#x200B; correcte voorbeeld &#x200B;](#mute-signals) moeten worden vervangen.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![&#x200B; onjuiste &#x200B;](../../../assets/no.svg) dubbele lokalisatie

Als de gevangen gelokaliseerde uitzondering nog niet wordt vertaald, los het probleem op de plaats op waar de uitzondering de eerste keer wordt geworpen.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![&#x200B; onjuiste &#x200B;](../../../assets/no.svg) de berichten van het Logboek en spoor aan verschillende logboekdossiers

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

Los dit probleem door de code na de correcte die voorbeelden te vervangen in [&#x200B; worden getoond schrijven aan het uitzonderingslogboek &#x200B;](#write-to-the-exception-log) of [&#x200B; uitzonderingen van de Ondergraving &#x200B;](#downgrade-exceptions).

### ![&#x200B; onjuiste &#x200B;](../../../assets/no.svg) de uitzonderingen van de Downgrade zonder context

De uitzondering wordt gedowngraded naar een fout, die niet toestaat dat een object wordt doorgegeven, maar alleen een tekenreeks, vandaar de `getMessage()` . Dit veroorzaakt het spoor dat moet worden verloren en door de correcte die voorbeelden worden vervangen in [&#x200B; worden getoond schrijven aan het uitzonderingslogboek &#x200B;](#write-to-the-exception-log) of [&#x200B; uitzonderingen van de Ondergraving &#x200B;](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![&#x200B; onjuist &#x200B;](../../../assets/no.svg) Logboek slechts het bericht aan het uitzonderingslogboek

In plaats van het object `$e` door te geven, wordt alleen `$e->getMessage()` doorgegeven. Dit veroorzaakt het spoor dat moet worden verloren en door de correcte getoonde voorbeelden [&#x200B; worden vervangen schrijft aan het uitzonderingslogboek &#x200B;](#write-to-the-exception-log) of [&#x200B; uitzonderingen van de Ondergraving &#x200B;](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![&#x200B; onjuist &#x200B;](../../../assets/no.svg) Ontbrekend `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Als u de regel `phpcs:ignore` weglaat, wordt een waarschuwing in PHPCS gegenereerd en wordt uw CI niet doorgegeven. Dit zou door het correcte voorbeeld moeten worden vervangen dat in [&#x200B; wordt getoond signalen van de Dempen &#x200B;](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
