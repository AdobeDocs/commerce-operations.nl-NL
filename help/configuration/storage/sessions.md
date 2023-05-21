---
title: Sessieopslaglocatie
description: Leer waar de sessiebestanden zijn opgeslagen.
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Sessieopslaglocatie

In dit onderwerp wordt besproken hoe u kunt bepalen waar uw sessiebestanden worden opgeslagen. Het systeem gebruikt de volgende logica om zittingsdossiers op te slaan:

- Als u geheugen vormde, worden de zittingen opgeslagen in RAM; zie [In cache geplaatste bestanden voor sessieopslag gebruiken](memcached.md).
- Als u Redis hebt geconfigureerd, worden de sessies opgeslagen op de Redis-server. zie [Redis gebruiken voor sessieopslag](../cache/redis-session.md).
- Als u de standaard op een bestand gebaseerde sessieopslag gebruikt, slaan we sessies op de volgende locaties op in de weergegeven volgorde:

   1. Map gedefinieerd in [`env.php`](#example-in-envphp)
   1. Map gedefinieerd in [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## Voorbeeld in `env.php`

Een voorbeeldfragment uit `<magento_root>/app/etc/env.php` volgt:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

In het voorgaande voorbeeld worden sessiebestanden opgeslagen in `/var/www/session`

## Voorbeeld in `php.ini`

Als gebruiker met `root` rechten, opent u uw `php.ini` en zoek naar de waarde van `session.save_path`. Hiermee geeft u aan waar de sessies worden opgeslagen.

## Sessiegrootte beheren

Zie de [Sessiebeheer](https://docs.magento.com/user-guide/stores/security-session-management.html) in de _Gebruikershandleiding_.

## Configuratie van afvalophaling

Om verlopen zittingen op te schonen, roept het systeem `gc` (_opschonen_) op willekeurige wijze afhandelen op basis van een waarschijnlijkheid die wordt berekend door de `gc_probability / gc_divisor` richtlijn. Als u deze richtlijnen bijvoorbeeld instelt op `1/100` wordt verstaan onder `1%` (_waarschijnlijkheid van één vraag van huisvuilinzameling per 100 verzoeken_).

De handler voor de afvalophaling gebruikt de optie `gc_maxlifetime` compileren—het aantal seconden waarna de sessies worden gezien als _vuilnis_ en mogelijk opgeruimd.

Bij sommige besturingssystemen (Debian/Ubuntu) is de standaardinstelling `session.gc_probability` richtlijn `0`, waardoor de handler voor afvalophaling niet kan worden uitgevoerd.

U kunt de `session.gc_` richtlijnen van de `php.ini` in het `<magento_root>/app/etc/env.php` bestand:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

De configuratie varieert, afhankelijk van het verkeer en de specifieke behoeften van de website van de handelaar.
