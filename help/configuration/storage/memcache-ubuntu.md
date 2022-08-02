---
title: In cache plaatsen op Ubuntu
description: Installeer en configureer de gedeponeerde gegevens in Ubuntu.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# In cache plaatsen op Ubuntu

In deze sectie vindt u instructies voor het installeren van een memcached op Ubuntu.

>[!INFO]
>
>Adobe raadt u aan een memcacheversie 3.0.5 of hoger te gebruiken.

Omdat PHP geen native ondersteuning heeft voor memcache, moet je een extensie installeren voor PHP om deze te kunnen gebruiken. Er zijn twee PHP-extensies beschikbaar en het is belangrijk te decoderen welke extensie moet worden gebruikt:

- `memcache` (_neen d_) - een oudere maar populaire extensie die niet regelmatig wordt onderhouden.
De `memcache` momenteel extensie _niet_ werken met PHP 7. Zie [PHP-documentatie voor memcache](https://www.php.net/manual/en/book.memcache.php).

   De exacte naam is `php5-memcache` voor Ubuntu.

- `memcached` (_met een`d`_) - een nieuwere en onderhouden extensie die compatibel is met PHP 7. Zie [PHP-documentatie voor memcaching](https://www.php.net/manual/en/book.memcached.php).

   De exacte naam is `php5-memcached` voor Ubuntu.

## In de Ubuntu-cache plaatsen en configureren

**Om gebed op Ubuntu te installeren en te vormen**:

1. Als gebruiker met `root` rechten, voert u de volgende opdracht in:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Wijzig de instelling voor de configuratie-instelling in de cache voor `CACHESIZE` en `-l`:

   1. Openen `/etc/memcached.conf` in een teksteditor.
   1. Zoek de `-m` parameter.
   1. De waarde ten minste wijzigen in `1GB`
   1. Zoek de `-l` parameter.
   1. De waarde wijzigen in `127.0.0.1` of `localhost`
   1. Sla uw wijzigingen op in `memcached.conf` en sluit de teksteditor af.
   1. Start de cache opnieuw.

      ```bash
      service memcached restart
      ```

1. Start de webserver opnieuw.

   Voor Apache: `service apache2 restart`

1. Ga verder met de volgende sectie.

## Controleren of de cache werkt voordat Magento wordt geïnstalleerd

Adobe raadt aan een memcaching te testen om te controleren of deze werkt voordat u Commerce installeert. Dit duurt slechts een paar minuten en kan het oplossen van problemen later vereenvoudigen.

### Controleren of het in de cache geplaatste item wordt herkend door de webserver

Om te controleren of het in een cache plaatsen wordt herkend door de webserver:

1. Een `phpinfo.php` bestand in de hoofdmap van de webserver:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Ga naar die pagina in uw webbrowser. Bijvoorbeeld:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Zorg ervoor dat in het geheugen opgeslagen weergaven als volgt zijn:

   ![Bevestig dat in het geheugen wordt opgeslagen wordt herkend door de webserver](../../assets/configuration/memcache.png)

   Controleer of u versie 3.0.5 of hoger uit het geheugen gebruikt.

   Als de webserver niet wordt weergegeven in de cache, start u de webserver opnieuw en vernieuwt u de browserpagina. Als het nog steeds niet wordt weergegeven, controleert u of u de `php-pecl-memcached` extensie.

### Controleren of geheugen gegevens in cache kan plaatsen

In deze test wordt een PHP-script gebruikt om te controleren of in een cache opgeslagen en opgehaald kan worden [cachegeheugen](https://glossary.magento.com/cache) gegevens.

Voor meer informatie over deze test raadpleegt u [Memcache installeren en gebruiken in Ubuntu-zelfstudie](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Maken `cache-test.php` in de hoofdmap van de webserver met de volgende inhoud:

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

Wanneer `<memcached hostname or ip>` is ofwel `localhost`, `127.0.0.1`of de hostnaam van de memcache of het IP-adres. De `<memcached port>` de luisterpoort is; standaard `11211`.

Ga naar die pagina in een webbrowser. Bijvoorbeeld

```http
http://192.0.2.1/cache-test.php
```

De eerste keer dat u naar de pagina gaat, wordt het volgende weergegeven: `No matching key found. Refresh the browser to add it!`

Vernieuw de browser. Het bericht verandert in `Successfully retrieved the data!`

Tot slot kunt u de memachetoetsen bekijken gebruikend Telnet:

```bash
telnet localhost <memcache port>
```

Bij de herinnering, ga binnen

```shell
stats items
```

Het resultaat is vergelijkbaar met het volgende:

```terminal
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

Opslag in het geheugen leegmaken en Telnet afsluiten:

```shell
flush_all
```

```shell
quit
```

[Aanvullende informatie over de Telnet-test](https://darkcoding.net/software/memcached-list-all-keys/)
