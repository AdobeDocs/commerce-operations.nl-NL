---
title: Cron-taken configureren en uitvoeren
description: Leer hoe u taken voor uitsnijden beheert.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# Cron-taken configureren

{{file-system-owner}}

Voor verschillende functies voor de handel is minstens één snijbaan vereist, die activiteiten in de toekomst plant. Hieronder volgt een gedeeltelijke lijst van deze activiteiten:

- Regels inzake catalogusprijzen
- Nieuwsbrieven
- Google-sitemaps genereren
- Waarschuwingen/meldingen van klanten (prijswijziging van producten, productvoorraad)
- Opnieuw indexeren
- Privéverkoop (alleen Adobe Commerce)
- Automatische actualisering van de wisselkoersen
- Alle e-mails met bericht van koophandel (inclusief bevestiging van bestelling en transactie)

>[!WARNING]
>
>U kunt niet meer uitvoeren `dev/tools/cron.sh` omdat het script is verwijderd.

>[!INFO]
>
>De handel hangt van juiste kroonbaanconfiguratie voor vele belangrijke systeemfuncties, met inbegrip van het indexeren af. Als deze niet op de juiste wijze wordt ingesteld, zal de handel niet functioneren zoals verwacht.

De systeemplanningstaken van UNIX die door bijzondere gebruikers moeten worden uitgevoerd gebruikend een _crontab_, een bestand dat instructies bevat aan de cron daemon die aangeven dat de daemon in werking is &quot;deze opdracht op dit moment op deze datum uitvoeren&quot;. Elke gebruiker heeft zijn eigen contab, en de bevelen in om het even welk bepaald contab worden uitgevoerd als gebruiker die het bezit.

Als u de functie voor uitsnijden in een webbrowser wilt uitvoeren, raadpleegt u [Secure cron.php to run in browser](../security/secure-cron-php.md).

## De tab Commerce maken of verwijderen

Deze sectie bespreekt hoe te om uw Commerce contab (namelijk de configuratie voor de borrelen van de Handel) tot stand te brengen of te verwijderen.

De _crontab_ Dit is de configuratie die wordt gebruikt om taken voor uitsnijden uit te voeren.

De toepassing van de Handel gebruikt kroontaken die met verschillende configuraties kunnen lopen. De PHP bevel-lijn configuratie controleert de algemene kroonbaan die indexeerders opnieuw indexeert, e-mail produceert, sitemap, etc. produceert.

>[!WARNING]
>
>- Om problemen tijdens installatie en verbetering te vermijden, adviseren wij sterk u om de zelfde PHP montages op zowel de PHP bevel-lijn configuratie als op de configuratie van de PHP Webserver stop-in toe te passen. Zie voor meer informatie [Vereiste PHP-instellingen](../../installation/prerequisites/php-settings.md).
>- In een systeem met meerdere knooppunten kan de tab op slechts één knooppunt worden uitgevoerd. Dit geldt alleen voor u als u meer dan één webnode instelt om redenen die te maken hebben met prestaties of schaalbaarheid.

### De tab Handelsverkeer maken

Beginnend met versie 2.2, leidt de Handel tot een rontab voor u. Wij voegen contab van de Handel aan om het even welk gevormd contab voor de eigenaar van het het dossiersysteem van de Handel toe. Met andere woorden, als u al aanknopingspunten voor andere extensies of toepassingen hebt, voegen wij de Commerce-contab eraan toe.

Het tabblad Handel bevindt zich in `#~ MAGENTO START` en `#~ MAGENTO END` opmerkingen op uw tabblad.

U kunt als volgt de Commerce-tab maken:

1. Meld u aan als, of schakel over naar, de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Verandering in uw de installatiemap van de Handel.
1. Voer de volgende opdracht in:

   ```bash
   bin/magento cron:install [--force]
   ```

Gebruiken `--force` om een bestaande tab te herschrijven.

>[!INFO]
>
>- `magento cron:install` herschrijft geen bestaande tab binnen `#~ MAGENTO START` en `#~ MAGENTO END` opmerkingen op uw tabblad.
>- `magento cron:install --force` heeft geen invloed op banen in de bouwsector die buiten de opmerkingen van de Commerce vallen.

Als u het tabblad wilt weergeven, voert u de volgende opdracht in als de eigenaar van het bestandssysteem:

```bash
crontab -l
```

Hieronder volgt een monster:

```terminal
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>De `update/cron.php` bestand is verwijderd in Commerce 2.4.0. Als dit bestand aanwezig is op uw installatie, kan het veilig worden verwijderd.
>
>Elke verwijzing naar `update/cron.php` en `bin/magento setup:cron:run` moet ook worden verwijderd uit de tab &quot;

### De tab Handel verwijderen

U zou de handelskrontab moeten verwijderen slechts alvorens de toepassing van de Handel te desinstalleren.

U verwijdert de tab Handel als volgt:

1. Aanmelden als of schakelen naar [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Ga naar de installatiemap Handel.
1. Voer de volgende opdracht in:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Deze opdracht heeft geen effect op snijtaken buiten de `#~ MAGENTO START` en `#~ MAGENTO END` opmerkingen op uw tabblad.

## Uitsnijden uitvoeren vanaf de opdrachtregel

Opdrachtopties:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

waar `--group` geeft de uitsnijdgroep aan die moet worden uitgevoerd (laat deze optie weg om de uitsnede voor alle groepen uit te voeren)

Voer de volgende gegevens in om de indexeringstaak uit te voeren:

```bash
bin/magento cron:run --group index
```

Voer de volgende gegevens in om de standaarduitsnijdtaak uit te voeren:

```bash
bin/magento cron:run --group default
```

Als u aangepaste uitsnijdtaken en -groepen wilt instellen, raadpleegt u [Aangepaste uitsnijdtaken en uitsnijdgroepen configureren](../cron/custom-cron.md).

>[!INFO]
>
>Je moet twee keer uitsnijden: de eerste keer dat je taken ontdekt die je moet uitvoeren en de tweede keer — om de taken zelf uit te voeren. De tweede uitsnijding moet op of na de `scheduled_at` tijd voor elke taak.

## Logboekregistratie

Alles `cron` taakgegevens zijn verplaatst van `system.log` in een aparte `cron.log`.
De informatie over de uitsnede is standaard beschikbaar op `<install_directory>/var/log/cron.log`.
Alle uitzonderingen op snijtaken worden vastgelegd door `\Magento\Cron\Observer\ProcessCronQueueObserver::execute`.

Naast het aanmelden `cron.log`:

- Mislukte taken met `ERROR` en `MISSED` statussen worden aangemeld bij de `<install_directory>/var/log/support_report.log`.

- Taken met een `ERROR` status wordt altijd geregistreerd als `CRITICAL` in `<install_directory>/var/log/exception.log`.

- Taken met een `MISSED` status wordt geregistreerd als `INFO` in de `<install_directory>/var/log/debug.log` directory (alleen in de ontwikkelaarsmodus).

>[!INFO]
>
>Alle snijgegevens worden ook naar de `cron_schedule` tabel in de Commerce-database. De tabel bevat een historie van snijtaken, waaronder:
>
>- Taak-id en code
>- Status
>- Aanmaakdatum
>- Geplande datum
>- Uitvoeringsdatum
>- Einddatum
>
>Om verslagen in de lijst te zien, login aan het gegevensbestand van de Handel op de bevellijn en ga binnen `SELECT * from cron_schedule;`.
