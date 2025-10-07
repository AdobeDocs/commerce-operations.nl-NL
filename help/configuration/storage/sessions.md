---
title: Sessieopslaglocatie
description: Meer informatie over opslaglocaties voor sessies en bestandsbeheer in Adobe Commerce. Ontdek opslaglogica en configuratieopties.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Sessieopslaglocatie

In dit onderwerp wordt besproken hoe u kunt bepalen waar uw sessiebestanden worden opgeslagen. Het systeem gebruikt de volgende logica om zittingsdossiers op te slaan:

- Als u in het geheugen ondergebracht gevormde, de zittingen in RAM worden opgeslagen; zie [&#x200B; Gebruik in het geheugen ondergebracht voor zittingsopslag &#x200B;](memcached.md).
- Als u Redis vormde, worden de zittingen opgeslagen op de Redis server; zie [&#x200B; Redis van het Gebruik voor zittingsopslag &#x200B;](../cache/redis-session.md).
- Als u de standaard op een bestand gebaseerde sessieopslag gebruikt, slaan we sessies op de volgende locaties op in de weergegeven volgorde:

   1. Map gedefinieerd in [`env.php`](#example-in-envphp)
   1. Map gedefinieerd in [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## Voorbeeld in `env.php`

Hieronder volgt een voorbeeldfragment uit `<magento_root>/app/etc/env.php` :

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

In het voorgaande voorbeeld worden sessiebestanden opgeslagen in `/var/www/session`

## Voorbeeld in `php.ini`

Als gebruiker met `root` rechten opent u het `php.ini` -bestand en zoekt u naar de waarde van `session.save_path` . Hiermee geeft u aan waar de sessies worden opgeslagen.

## Sessiegrootte beheren

Zie het [&#x200B; beheer van de Zitting &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-session-management) in de _gids van de Gebruiker_.

## Configuratie van afvalophaling

Om verlopen zittingen schoon te maken, roept het systeem de `gc` (_huisvuilinzameling_) manager willekeurig volgens een waarschijnlijkheid die door de `gc_probability / gc_divisor` richtlijn wordt berekend. Bijvoorbeeld, als u deze richtlijnen aan `1/100` respectievelijk plaatst, betekent het een waarschijnlijkheid van `1%` (_waarschijnlijkheid van één vraag van huisvuilinzameling per 100 verzoeken_).

De manager van de huisvuilinzameling gebruikt `gc_maxlifetime` richtlijn-het aantal seconden waarna de zittingen als _huisvuil_ worden gezien en potentieel omhoog schoongemaakt.

Op sommige besturingssystemen (Debian/Ubuntu) is de standaard `session.gc_probability` instructie `0` , die voorkomt dat de handler voor afvalophaling wordt uitgevoerd.

U kunt de instructies `session.gc_` uit het `php.ini` -bestand in het `<magento_root>/app/etc/env.php` -bestand overschrijven:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

De configuratie varieert, afhankelijk van het verkeer en de specifieke behoeften van de website van de handelaar.
