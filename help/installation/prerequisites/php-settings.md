---
title: PHP-instellingen
description: Volg deze stappen om vereiste PHP uitbreidingen te installeren en vereiste PHP montages voor op-gebouw installaties van Adobe Commerce en Magento Open Source te vormen.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# PHP-instellingen

In dit onderwerp wordt besproken hoe u vereiste PHP-opties kunt instellen.

>[!NOTE]
>
>Zie [systeemvereisten](../system-requirements.md) voor ondersteunde versies van PHP.

## Controleren of PHP is geïnstalleerd

Bij de meeste Linux-versies is PHP standaard geïnstalleerd. In dit onderwerp wordt ervan uitgegaan dat u PHP al hebt geïnstalleerd. Als u wilt controleren of PHP al is geïnstalleerd, typt u op de opdrachtregel:

```bash
php -v
```

Als PHP is geïnstalleerd, wordt een bericht weergegeven dat lijkt op het volgende:

```terminal
PHP 7.4.0 (cli) (built: Aug 14 2019 16:42:46) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.1.0, Copyright (c) 1998-2018 Zend Technologies with Zend OPcache v7.1.6, Copyright (c) 1999-2018, by Zend Technologies
```

Adobe Commerce en Magento Open Source 2.4 zijn compatibel met PHP 7.3, maar we testen en raden je aan om PHP 7.4 te gebruiken.

Als PHP niet is geïnstalleerd of als een versie-upgrade nodig is, installeert u deze aan de hand van instructies voor uw specifieke Linux-smaak.
Op CentOS, [eventueel zijn aanvullende stappen vereist](https://wiki.centos.org/HowTos/php7).

## Geïnstalleerde extensies verifiëren

Adobe Commerce en Magento Open Source vereisen dat een set extensies wordt geïnstalleerd.

{{$include /help/_includes/templated/php-extensions.md}}

Geïnstalleerde extensies controleren:

1. Geïnstalleerde modules weergeven.

   ```bash
   php -m
   ```

1. Controleer of alle vereiste extensies zijn geïnstalleerd.
1. Voeg ontbrekende modules toe aan de hand van dezelfde workflow die gebruikt wordt voor de installatie van PHP. Als u bijvoorbeeld `yum` Voor de installatie van PHP kunnen de PHP 7.4 modules worden toegevoegd met:

   ```bash
    yum -y install php74u-pdo php74u-mysqlnd php74u-opcache php74u-xml php74u-gd php74u-devel php74u-mysql php74u-intl php74u-mbstring php74u-bcmath php74u-json php74u-iconv php74u-soap
   ```

## PHP-instellingen controleren

>[!WARNING]
>
>Als u PHP 7.4.20 gebruikt, set `pcre.jit=0` in uw `php.ini` bestand. Dit komt rond een PHP [buigen](https://bugs.php.net/bug.php?id=81101) voorkomt dat CSS wordt geladen.

- Stel de systeemtijdzone voor PHP in. anders werken fouten zoals de volgende weergave tijdens de installatie en bewerkingen met betrekking tot tijd zoals cron mogelijk niet:

```terminal
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Stel de PHP-geheugenlimiet in.

  Onze gedetailleerde aanbevelingen zijn:

   - Compileren van code of het inzetten van statische activa, `1G`
   - Foutopsporing, `2G`
   - Testen; `~3-4G`

- De waarden voor PHP verhogen `realpath_cache_size` en `realpath_cache_ttl` aan aanbevolen instellingen:

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Met deze instellingen kunnen PHP-processen paden naar bestanden in cache plaatsen in plaats van ze elke keer weer op te zoeken wanneer een pagina wordt geladen. Zie [Prestaties afstemmen](https://www.php.net/manual/en/ini.core.php) in de PHP documentatie.

- Inschakelen [`opcache.save_comments`](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments), die vereist is voor Adobe Commerce en Magento Open Source 2.1 en hoger.

  We raden u aan de [PHP OPcache](https://www.php.net/manual/en/book.opcache.php) om prestatieredenen. De OPcache is in veel PHP distributies ingeschakeld.

  Adobe Commerce en Magento Open Source 2.1 en hoger gebruiken PHP-codeopmerkingen voor het genereren van code.

>[!NOTE]
>
>Om problemen tijdens installatie en verbetering te vermijden, adviseren wij sterk u om de zelfde PHP montages op zowel de PHP bevel-lijn configuratie als de PHP configuratie van de Webserver stop - in toe te passen. Zie de volgende sectie voor meer informatie.

## PHP-configuratiebestanden zoeken

In deze sectie wordt beschreven hoe u de configuratiebestanden vindt die nodig zijn om de vereiste instellingen bij te werken.

### Zoeken `php.ini` configuratiebestand

Als u de webserverconfiguratie wilt zoeken, voert u een [`phpinfo.php` file](optional-software.md#create-phpinfophp) in uw webbrowser en zoek naar `Loaded Configuration File` als volgt:

![PHP-informatiepagina](../../assets/installation/config_phpini-webserver.png)

Als u de PHP opdrachtregelconfiguratie wilt zoeken, typt u

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Als u slechts één `php.ini` , brengt u de wijzigingen aan in dat bestand. Als u twee `php.ini` bestanden, breng de wijzigingen aan in *alles* bestanden. Als u dit niet doet, kunnen er onvoorspelbare prestaties optreden.

### Configuratie-instellingen voor OPcache zoeken

PHP OPcache-instellingen bevinden zich doorgaans ook in `php.ini` of `opcache.ini`. De locatie kan afhankelijk zijn van uw besturingssysteem en PHP-versie. Het OPcache-configuratiebestand kan een `opcache` sectie of instellingen zoals `opcache.enable`.

Gebruik de volgende richtlijnen om het te vinden:

- Apache-webserver:

  Voor Ubuntu met Apache bevinden de OPcache-instellingen zich doorgaans in de `php.ini` bestand.

  Voor CentOS met Apache of Nginx bevinden de OPcache-instellingen zich doorgaans in `/etc/php.d/opcache.ini`

  Als niet, gebruik het volgende bevel om van het de plaats te bepalen:

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- Nginx-webserver met PHP-FPM: `/etc/php/7.2/fpm/php.ini`

Als u meer dan één `opcache.ini`en wijzigt u ze allemaal.

## PHP-opties instellen

PHP-opties instellen:

1. Een `php.ini` in een teksteditor.
1. Zoek de tijdzone van uw server in de beschikbare [tijdzone-instellingen](https://www.php.net/manual/en/timezones.php)
1. Zoek de volgende instelling en verwijder indien nodig de commentaarmarkering:

   ```conf
   date.timezone =
   ```

1. Voeg de tijdzone-instelling toe die u in stap 2 hebt gevonden.

1. De waarde wijzigen van `memory_limit` op een van de aan het begin van deze sectie aanbevolen waarden.

   Bijvoorbeeld:

   ```conf
   memory_limit=2G
   ```

1. Voeg de `realpath_cache` configuratie die overeenkomt met de volgende waarden:

   ```conf
   ;
   ; Increase realpath cache size
   ;
   realpath_cache_size = 10M
   
   ;
   ; Increase realpath cache ttl
   ;
   realpath_cache_ttl = 7200
   ```

1. Sla de wijzigingen op en sluit de teksteditor af.

1. De andere openen `php.ini` (als ze anders zijn) en breng dezelfde wijzigingen aan.

## Opties voor OPcache instellen

In te stellen `opcache.ini` opties:

1. Open het OPcache-configuratiebestand in een teksteditor:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/7.2/fpm/php.ini` (nginx-webserver (CentOS of Ubuntu)

1. Zoeken `opcache.save_comments` en verwijder indien nodig opmerkingen.
1. Controleer of de waarde is ingesteld op `1`.
1. Sla de wijzigingen op en sluit de teksteditor af.
1. Start de webserver opnieuw:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu en CentOS: `service nginx restart`

## Problemen oplossen

Raadpleeg de volgende Adobe Commerce Support-artikelen voor hulp bij het oplossen van problemen met PHP:

- [PHP-versiefout of 404-fout bij toegang tot Adobe Commerce in browser](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [Fouten in PHP-instellingen](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [PHP-coderingsextensie is niet correct geïnstalleerd](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [Problemen met gereedheid voor PHP-versie](https://support.magento.com/hc/en-us/articles/360033546411)
- [Veelvoorkomende fatale fouten en oplossingen in PHP](https://support.magento.com/hc/en-us/articles/360030568432)
