---
title: PHP-instellingen
description: Volg deze stappen om vereiste PHP uitbreidingen te installeren en vereiste PHP montages voor op-gebouw installaties van Adobe Commerce te vormen.
feature: Install, Configuration
exl-id: 84064442-7053-42ab-a8a6-9b313e5efc78
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 0%

---


# PHP-instellingen

In dit onderwerp wordt besproken hoe u vereiste PHP-opties kunt instellen.

>[!NOTE]
>
>Voor de nieuwste versie van Adobe Commerce is minimaal PHP 8.1 vereist. Zie [ systeemvereisten ](../system-requirements.md) voor alle gesteunde versies van PHP.

Voor de configuratiebegeleiding van de Wolk, zie [ PHP montages ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html?lang=nl-NL) in _Commerce op de gids van de Infrastructuur van de Wolk_.

## PHP Process Control

{{php-process-control}}

## Controleren of PHP is geïnstalleerd

PHP is standaard geïnstalleerd op de meeste Linux distributies. In dit onderwerp wordt ervan uitgegaan dat u PHP al hebt geïnstalleerd. Om te controleren of PHP is geïnstalleerd, voert u het volgende in op de opdrachtregel:

```bash
php -v
```

Als PHP is geïnstalleerd, wordt een bericht weergegeven dat lijkt op het volgende:

```
PHP 8.1.2-1ubuntu2.14 (cli) (built: Aug 18 2023 11:41:11) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2-1ubuntu2.14, Copyright (c), by Zend Technologies
```

Als PHP niet is geïnstalleerd (of een upgrade nodig heeft), installeert u het door de instructies voor de Linux-distributie te volgen.

## Geïnstalleerde extensies verifiëren

Adobe Commerce vereist bepaalde PHP extensies. In de volgende lijsten worden de vereiste extensies voor elke editie van Commerce opgegeven. De lijsten worden automatisch geproduceerd van een plaatsing die de recentste versie van elke uitgave in werking stelt.

{{$include /help/_includes/templated/php-extensions.md}}

Geïnstalleerde extensies controleren:

1. Geïnstalleerde modules weergeven.

   ```bash
   php -m
   ```

1. Controleer of alle vereiste extensies zijn geïnstalleerd.
1. Voeg ontbrekende modules toe aan de hand van dezelfde workflow die gebruikt wordt voor de installatie van PHP.

## PHP-instellingen controleren

>[!WARNING]
>
>Als u PHP 7.4.20 gebruikt, stelt u `pcre.jit=0` in in uw `php.ini` -bestand. Dit krijgt rond een PHP [ insect ](https://bugs.php.net/bug.php?id=81101) dat CSS verhindert te laden.

- Stel de tijdzone van het systeem in voor PHP. Anders werken fouten zoals de volgende weergave tijdens de installatie en bewerkingen met betrekking tot tijd zoals cron mogelijk niet:

```
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more messages follow]
```

- Stel de PHP-geheugenlimiet in.

  Adobe beveelt het volgende aan:

   - Code compileren of statische elementen implementeren, `1G`
   - Foutopsporing, `2G`
   - Testen, `~3-4G`

- Verhoog de waarden voor PHP `realpath_cache_size` en `realpath_cache_ttl` tot de aanbevolen instellingen:

  ```conf
  realpath_cache_size=10M
  realpath_cache_ttl=7200
  ```

  Met deze instellingen kunnen PHP-processen paden naar bestanden in cache plaatsen in plaats van ze te bekijken bij het laden van de pagina. Zie [ Prestaties die ](https://www.php.net/manual/en/ini.core.php) in de PHP documentatie stempelen.

- Schakel [`opcache.save_comments` ](https://www.php.net/manual/en/opcache.configuration.php#ini.opcache.save-comments) in. Dit is vereist voor Adobe Commerce 2.1 en hoger.

  De Adobe adviseert toelatend [ PHP OPcache ](https://www.php.net/manual/en/book.opcache.php) voor prestatiesredenen. De OPcache is in veel PHP distributies ingeschakeld.

  Adobe Commerce 2.1 en hoger gebruiken PHP-codeopmerkingen voor het genereren van code.

>[!NOTE]
>
>Om problemen tijdens installatie en verbetering te vermijden, adviseert de Adobe sterk dat u de zelfde montages PHP op zowel de PHP bevel-lijn configuratie als de PHP configuratie van de Webserver stop - in configuratie toepast. Zie de volgende sectie voor meer informatie.

## PHP-configuratiebestanden zoeken

In deze sectie wordt beschreven hoe u de configuratiebestanden vindt die nodig zijn om de vereiste instellingen bij te werken.

### Configuratiebestand `php.ini` zoeken

Als u de webserverconfiguratie wilt zoeken, voert u een [`phpinfo.php` bestand ](optional-software.md#create-phpinfophp) in uw webbrowser uit en zoekt u de `Loaded Configuration File` als volgt:

![ PHP- infopagina ](../../assets/installation/config_phpini-webserver.png)

Als u de PHP opdrachtregelconfiguratie wilt zoeken, typt u

```bash
php --ini | grep "Loaded Configuration File"
```

>[!NOTE]
>
>Als u slechts één `php.ini` -bestand hebt, wijzigt u dat bestand. Als u twee `php.ini` dossiers hebt, verander *allebei* dossiers. Als u dit niet doet, kunnen er onvoorspelbare prestaties optreden.

### Configuratie-instellingen voor OPcache zoeken

PHP OPcache-instellingen bevinden zich doorgaans in `php.ini` of `opcache.ini` . De locatie kan afhankelijk zijn van uw besturingssysteem en PHP-versie. Het OPcache-configuratiebestand heeft mogelijk een `opcache` -sectie of instellingen, zoals `opcache.enable` .

Gebruik de volgende richtlijnen om het te vinden:

- Apache-webserver:

  Voor Ubuntu met Apache bevinden de OPcache-instellingen zich doorgaans in het `php.ini` -bestand.

  Voor CentOS met Apache of nginx bevinden de instellingen voor OPcache zich doorgaans in `/etc/php.d/opcache.ini`

  Als niet, gebruik het volgende bevel om van het de plaats te bepalen:

  ```bash
  sudo find / -name 'opcache.ini'
  ```

- nginx-webserver met PHP-FPM: `/etc/php/8.1/fpm/php.ini`

Als u meer dan één `opcache.ini` hebt, wijzigt u ze allemaal.

## PHP-opties instellen

PHP-opties instellen:

1. Open een `php.ini` in een teksteditor.
1. Bepaal de plaats van de tijdzone van uw server in de beschikbare [ montages van de tijdzone ](https://www.php.net/manual/en/timezones.php)
1. Zoek de volgende instelling en verwijder indien nodig de commentaarmarkering:

   ```conf
   date.timezone =
   ```

1. Voeg de tijdzone-instelling toe die u in stap 2 hebt gevonden.

1. Wijzig de waarde van `memory_limit` in een van de waarden die aan het begin van deze sectie worden aanbevolen.

   Bijvoorbeeld:

   ```conf
   memory_limit=2G
   ```

1. Voeg de configuratie van `realpath_cache` toe of werk deze bij zodat deze overeenkomt met de volgende waarden:

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

1. Open de andere `php.ini` (als deze verschillend zijn) en breng dezelfde wijzigingen aan.

## Opties voor OPcache instellen

U stelt `opcache.ini` -opties als volgt in:

1. Open het OPcache-configuratiebestand in een teksteditor:

   - `opcache.ini` (CentOS)
   - `php.ini` (Ubuntu)
   - `/etc/php/8.1/fpm/php.ini` (nginx-webserver (CentOS of Ubuntu))

1. Zoek `opcache.save_comments` en verwijder indien nodig de commentaarmarkering.
1. Controleer of de waarde is ingesteld op `1` .
1. Sla de wijzigingen op en sluit de teksteditor af.
1. Start de webserver opnieuw:

   - Apache, Ubuntu: `service apache2 restart`
   - Apache, CentOS: `service httpd restart`
   - nginx, Ubuntu en CentOS: `service nginx restart`

## Problemen oplossen

Raadpleeg de volgende Adobe Commerce Support-artikelen voor hulp bij het oplossen van problemen met PHP:

- [ PHP versiefout of fout 404 wanneer het toegang tot van Adobe Commerce in browser ](https://support.magento.com/hc/en-us/articles/360033117152-PHP-version-error-or-404-error-when-accessing-Magento-in-browser)
- [ PHP montagesfouten ](https://support.magento.com/hc/en-us/articles/360034599631-PHP-settings-errors)
- [ PHP crypt uitbreiding niet behoorlijk geïnstalleerd ](https://support.magento.com/hc/en-us/articles/360034280132-PHP-mcrypt-extension-not-installed-properly-)
- [ PHP de kwesties van de de versiescontrole ](https://support.magento.com/hc/en-us/articles/360033546411)
- [ Gemeenschappelijke PHP Onherstelbare Fouten en oplossingen ](https://support.magento.com/hc/en-us/articles/360030568432)
