---
title: In cache plaatsen op CentOS
description: In cache geplaatst op CentOS installeren en configureren.
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# In cache plaatsen op CentOS

In deze sectie vindt u instructies voor het installeren van een memcachegeheugen op CentOS. Voor extra informatie, raadpleeg [ memcached wiki ](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe raadt u aan de nieuwste, stabiele memcacheversie te gebruiken (momenteel 3.1.3 voor memcaching).

Omdat PHP geen native ondersteuning heeft voor memcache, moet je een extensie installeren voor PHP om deze te kunnen gebruiken. Er zijn twee PHP-extensies beschikbaar en het is belangrijk te decoderen welke extensie moet worden gebruikt:

- `memcache` (_geen d_) - een oudere maar populaire uitbreiding die niet regelmatig wordt gehandhaafd.
De `memcache` uitbreiding momenteel _werkt niet_ met PHP 7. Zie [ PHP documentatie voor memcache ](https://www.php.net/manual/en/book.memcache.php).

  De exacte naam is `php-pecl-memcache` voor CentOS.

- `memcached` (_met a`d`_) - een nieuwere en bewaarde uitbreiding die met PHP 7 compatibel is. Zie [ PHP documentatie voor in het geheugen ondergebracht ](https://www.php.net/manual/en/book.memcached.php).

  De exacte naam is `php-pecl-memcached` voor CentOS.

## In cache geplaatst geheugen installeren en configureren op CentOS

Als u in een cache geplaatste bestanden wilt installeren op CentOS, voert u de volgende taken uit als een gebruiker met `root` -rechten:

1. Installeer in het geheugen opgeslagen onderdelen en de afhankelijkheden ervan:

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >De syntaxis van de voorgaande opdrachten kan afhankelijk zijn van de opslagplaatsen voor pakketten die u gebruikt. Als u bijvoorbeeld webtatisch en PHP 5.6 gebruikt, voert u `yum install -y php56w-pecl-memcache` in. Gebruik `yum search memcache|grep php` om de juiste pakketnaam te zoeken.


1. Wijzig de instelling voor de configuratie-instellingen voor `CACHESIZE` en `OPTIONS` in de cache:

   1. Open `/etc/sysconfig/memcached` in een teksteditor.
   1. Zoek de waarde voor `CACHESIZE` en verander deze in ten minste 1 GB. Bijvoorbeeld:

      ```config
      CACHESIZE="1GB"
      ```

   1. Zoek de waarde voor `OPTIONS` en wijzig deze in `localhost` of `127.0.0.1`

1. Sla de wijzigingen in `memcached` op en sluit de teksteditor af.
1. Start de cache opnieuw.

   ```bash
   service memcached restart
   ```

1. Start de webserver opnieuw.

   Voor Apache:

   ```bash
   service httpd restart
   ```

1. Ga verder met de volgende sectie.

## De werking van een geheugen controleren voordat u Commerce installeert

Adobe raadt u aan een memcachegeheugen te testen om te controleren of dit werkt voordat u Commerce installeert. Dit neemt slechts een paar minuten in beslag en kan het oplossen van problemen later vereenvoudigen.

### Controleren of het in de cache geplaatste item wordt herkend door de webserver

Om te controleren dat het in een cache plaatsen wordt herkend door de webserver:

1. Maak een `phpinfo.php` -bestand in de hoofdmap van de webserver:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Ga naar die pagina in uw webbrowser.

   Bijvoorbeeld: `http://192.0.2.1/phpinfo.php`

1. Controleer of de geheugencache als volgt wordt weergegeven:

![ Bevestig memcache wordt erkend door de Webserver ](../../assets/configuration/memcache.png)

Controleer of u versie 3.0.5 of hoger uit het geheugen gebruikt.

Als het geheugen niet wordt weergegeven, start u de webserver opnieuw en vernieuwt u de browserpagina. Als de extensie nog steeds niet wordt weergegeven, controleert u of u de extensie `php-pecl-memcache` hebt geïnstalleerd.

### Een memcache-test maken die bestaat uit een MySQL-database en PHP-script

De test gebruikt een gegevensbestand MySQL, een lijst, en gegevens om te verifiëren u de gegevensbestandgegevens kunt terugwinnen en het in geheugen opslaan. Een PHP script zoekt eerst naar de cache. Als het resultaat niet bestaat, vraagt het manuscript gegevensbestand. Nadat de query door de oorspronkelijke database is uitgevoerd, slaat het script het resultaat op in het geheugen, met de opdracht `set` .

[ Meer details over deze test ](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Maak de MySQL-database:

```bash
mysql -u root -p
```

Voer bij de aanwijzing `mysql` de volgende opdrachten in:

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Maak `cache-test.php` in de hoofdmap van uw webserver:

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

Waar `<memcached hostname or ip>` `localhost` , `127.0.0.1` of de hostnaam of het IP-adres van de memcache is. De `<memcached port>` is de listen poort; standaard is dit `11211` .

Voer het script uit vanaf de opdrachtregel.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

Het eerste resultaat is `got result from mysql` . Dit betekent dat de sleutel niet in het geheugen werd opgeslagen maar uit MySQL werd teruggewonnen.

Het tweede resultaat is `got result from memcached` , waarmee wordt gecontroleerd of de waarde is opgeslagen in de cache.

Tot slot kunt u de memachetoetsen bekijken gebruikend Telnet:

```bash
telnet localhost <memcache port>
```

Bij de herinnering, ga

```bash
stats items
```

Het resultaat is vergelijkbaar met het volgende:

```
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Maak de geheugenopslag leeg en sluit Telnet weg:

```bash
flush_all
```

```bash
quit
```

[ Aanvullende informatie over de test van Telnet ](https://darkcoding.net/software/memcached-list-all-keys/)
