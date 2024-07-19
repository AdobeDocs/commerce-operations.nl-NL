---
title: Cron-taken configureren en uitvoeren
description: Leer hoe u taken voor uitsnijden beheert.
exl-id: 8ba2b2f9-5200-4e96-9799-1b00d7d23ce1
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '748'
ht-degree: 0%

---

# Cron-taken configureren

{{file-system-owner}}

Voor verschillende Commerce-functies is minstens één snijtaak vereist, die activiteiten in de toekomst plant. Hieronder volgt een gedeeltelijke lijst van deze activiteiten:

- Regels inzake catalogusprijzen
- Nieuwsbrieven
- Google-sitemaps genereren
- Waarschuwingen/meldingen van klanten (prijswijziging van producten, productvoorraad)
- Opnieuw indexeren
- Privéverkoop (alleen Adobe Commerce)
- Automatische actualisering van de wisselkoersen
- Alle e-mails van Commerce (inclusief bevestiging van bestelling en transactie)

>[!WARNING]
>
>U kunt `dev/tools/cron.sh` niet meer uitvoeren omdat het script is verwijderd.

>[!INFO]
>
>Commerce is voor veel belangrijke systeemfuncties, waaronder indexering, afhankelijk van de juiste configuratie voor de uitsnijdtaak. Als Commerce niet op de juiste wijze wordt ingesteld, werkt het niet zoals verwacht.

De systeemplanningstaken van UNIX die door bijzondere gebruikers worden uitgevoerd gebruikend a _contab_, die een dossier is dat instructies aan de cron daemon bevat die de daemon in feite vertellen om &quot;dit bevel op dit ogenblik op deze datum in werking te stellen&quot;. Elke gebruiker heeft zijn eigen contab, en de bevelen in om het even welk bepaald contab worden uitgevoerd als gebruiker die het bezit.

Om te lopen brein in Webbrowser, zie [ Veilig cron.php in browser ](../security/secure-cron-php.md) te lopen.

## De tab Commerce maken of verwijderen

In deze sectie wordt besproken hoe u uw Commerce-contexttabblad (de configuratie voor Commerce-taken voor uitsnijden) kunt maken of verwijderen.

Het _contraTab_ is de configuratie die wordt gebruikt om banen van de bouwsteen in werking te stellen.

De Commerce-toepassing gebruikt snijtaken die met verschillende configuraties kunnen worden uitgevoerd. De PHP bevel-lijn configuratie controleert de algemene kroonbaan die indexeerders opnieuw indexeert, e-mail produceert, sitemap, etc. produceert.

>[!WARNING]
>
>- Om problemen tijdens installatie en verbetering te vermijden, adviseren wij sterk u om de zelfde PHP montages op zowel de PHP bevel-lijn configuratie als op de configuratie van de PHP Webserver stop-in toe te passen. Voor meer informatie, zie [ Vereiste PHP montages ](../../installation/prerequisites/php-settings.md).
>- In een systeem met meerdere knooppunten kan de tab op slechts één knooppunt worden uitgevoerd. Dit geldt alleen voor u als u meer dan één webnode instelt om redenen die te maken hebben met prestaties of schaalbaarheid.

### De tab Commerce maken

Vanaf versie 2.2 maakt Commerce een tab voor u. We voegen het Commerce-contexttabblad toe aan een geconfigureerd contexttabblad voor de eigenaar van het Commerce-bestandssysteem. Met andere woorden, als u al catalogi voor andere extensies of toepassingen instelt, voegen we het Commerce-tabblad eraan toe.

De tab Commerce bevindt zich in de tabbladen `#~ MAGENTO START` en `#~ MAGENTO END` .

Het Commerce-tabblad maken:

1. Login als, of schakelaar aan, de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).
1. Ga naar de installatiemap van Commerce.
1. Voer de volgende opdracht in:

   ```bash
   bin/magento cron:install [--force]
   ```

Gebruik `--force` om een bestaande tab te herschrijven.

>[!INFO]
>
>- `magento cron:install` herschrijft een bestaand contexttabblad binnen `#~ MAGENTO START` - en `#~ MAGENTO END` -opmerkingen in uw contab niet.
>- `magento cron:install --force` heeft geen effect op snijtaken buiten de Commerce-opmerkingen.

Als u het tabblad wilt weergeven, voert u de volgende opdracht in als de eigenaar van het bestandssysteem:

```bash
crontab -l
```

Hieronder volgt een monster:

```
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

>[!INFO]
>
>Het `update/cron.php` -bestand is verwijderd in Commerce 2.4.0. Als dit bestand aanwezig is op de installatie, kan het veilig worden verwijderd.
>
>Elke verwijzing naar `update/cron.php` en `bin/magento setup:cron:run` moet ook worden verwijderd uit de tab &#39;

### De tab Commerce verwijderen

U moet het Commerce-tabblad alleen verwijderen voordat u de Commerce-toepassing verwijdert.

Het Commerce-tabblad verwijderen:

1. Login als of schakelaar aan de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).
1. Ga naar de Commerce-installatiemap.
1. Voer de volgende opdracht in:

   ```bash
   bin/magento cron:remove
   ```

>[!INFO]
>
>Deze opdracht heeft geen effect op uitsnijdtaken buiten de opmerkingen `#~ MAGENTO START` en `#~ MAGENTO END` op de tab.

## Uitsnijden uitvoeren vanaf de opdrachtregel

Opdrachtopties:

```bash
bin/magento cron:run [--group="<cron group name>"]
```

waarbij `--group` de uit te voeren uitsnijdgroep aangeeft (deze optie weglaten om voor alle groepen uit te voeren)

Voer de volgende gegevens in om de indexeringstaak uit te voeren:

```bash
bin/magento cron:run --group index
```

Voer de volgende gegevens in om de standaarduitsnijdtaak uit te voeren:

```bash
bin/magento cron:run --group default
```

Aan opstellings de banen en de groepen van de douanecurn, zie [ de banen van de douanecurn en de kantelgroepen van de opstelling ](../cron/custom-cron.md) vormen.

>[!INFO]
>
>Je moet twee keer uitsnijden: de eerste keer dat je taken ontdekt die je moet uitvoeren en de tweede keer — om de taken zelf uit te voeren. De tweede uitvoering voor uitsnijden moet plaatsvinden op of na de `scheduled_at` -tijd voor elke taak.

## Logboekregistratie

Alle `cron` taakgegevens zijn verplaatst van `system.log` naar een aparte `cron.log` .
Standaard vindt u de informatie over de uitsnede in `<install_directory>/var/log/cron.log` .
Alle uitzonderingen op snijtaken worden vastgelegd door `\Magento\Cron\Observer\ProcessCronQueueObserver::execute` .

Naast het aanmelden `cron.log` :

- Mislukte taken met `ERROR` - en `MISSED` -statussen worden bij de `<install_directory>/var/log/support_report.log` aangemeld.

- Taken met de status `ERROR` worden altijd als `CRITICAL` in `<install_directory>/var/log/exception.log` aangemeld.

- Taken met de status `MISSED` worden als `INFO` in de map `<install_directory>/var/log/debug.log` geregistreerd (alleen in de modus Ontwikkelaar).

>[!INFO]
>
>Alle snijgegevens worden ook naar de tabel `cron_schedule` in de Commerce-database geschreven. De tabel bevat een historie van snijtaken, waaronder:
>
>- Taak-id en code
>- Status
>- Aanmaakdatum
>- Geplande datum
>- Uitvoeringsdatum
>- Einddatum
>
>Als u records in de tabel wilt zien, meldt u zich aan bij de Commerce-database op de opdrachtregel en voert u `SELECT * from cron_schedule;` in.
