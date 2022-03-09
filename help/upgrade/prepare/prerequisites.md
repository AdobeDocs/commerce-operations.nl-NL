---
title: Volledige voorwaarden
description: Bereid uw Adobe Commerce- of Magento Open Source-project voor op een upgrade door deze vereiste stappen uit te voeren.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '1316'
ht-degree: 0%

---


# Volledige upgradevoorwaarden

Het is belangrijk om te begrijpen wat nodig is om Adobe Commerce of Magento Open Source te leiden. U moet eerst de [systeemvereisten](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) voor de versie waarnaar u wilt upgraden.

Nadat u de systeemvereisten hebt gecontroleerd, moet u aan de volgende voorwaarden voldoen voordat u de upgrade van uw systeem uitvoert:

- Alle software bijwerken
- Controleren of Elasticsearch is geïnstalleerd
- Limiet voor geopende bestanden instellen
- Controleren of uitsnijdtaken worden uitgevoerd
- Set `DATA_CONVERTER_BATCH_SIZE`
- Controleren op bestandssysteemmachtigingen
- Stel de `pub/` mapbasis
- De plug-in Composer-update installeren

## Alle software bijwerken

De [systeemvereisten](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) exact beschrijven welke versies van software van derden zijn getest met Adobe Commerce en Magento Open Source.

Zorg ervoor dat u alle systeemvereisten en afhankelijkheden in uw omgeving hebt bijgewerkt. Zie PHP [7,4](https://www.php.net/manual/en/migration74.php), PHP [8,0](https://www.php.net/manual/en/migration80.php), PHP [8,1](https://www.php.net/manual/en/migration81.php), en [vereiste PHP-instellingen](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/php-settings.html#php-required-set).

## Controleren of Elasticsearch is geïnstalleerd

Adobe Commerce en Magento Open Source vereisen dat Elasticsearch is geïnstalleerd om de software te kunnen gebruiken. Voordat u een upgrade uitvoert van 2.3.x naar 2.4, moet u controleren of u MySQL, Elasticsearch of een extensie van een andere fabrikant gebruikt als zoekprogramma voor de catalogus in uw 2.3.x-instantie. Het resultaat bepaalt wat u moet doen _voor_ opwaardering tot 2.4.

U kunt de opdrachtregel of de beheerder gebruiken om de zoekengine voor de catalogus te bepalen:

- Voer de `bin/magento config:show catalog/search/engine` gebruiken. De opdracht retourneert een waarde van `mysql`, `elasticsearch` (wat erop wijst dat Elasticsearch 2 wordt gevormd), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`of een aangepaste waarde die aangeeft dat u een zoekprogramma van derden hebt geïnstalleerd.

- Controleer vanuit de beheerder de waarde van de **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** veld.

In de volgende secties wordt beschreven welke handelingen u moet uitvoeren voordat u de upgrade naar 2.4.0 uitvoert.

### MySQL

Vanaf 2.4, is MySQL niet meer een gesteunde motor van de catalogusonderzoek. U moet Elasticsearch installeren en configureren voordat u een upgrade uitvoert. Gebruik de volgende bronnen om u door dit proces te begeleiden:

- [Elasticsearch installeren en configureren](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-overview.html)
- [Elasticsearch installeren](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Elasticsearch configureren om mee te werken [nginx](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-nginx.html) of [Apache](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/es-config-apache.html)
- [Handel configureren om Elasticsearch te gebruiken](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) en opnieuw indexeren

Bepaalde zoekprogramma&#39;s voor catalogi van derden worden boven op de zoekfunctie van Adobe Commerce uitgevoerd. Neem contact op met de leverancier om te bepalen of u de extensie moet bijwerken.

### Elasticsearch

U moet Elasticsearch installeren en configureren voordat u de upgrade uitvoert naar 2.4.0. Adobe ondersteunt geen Elasticsearch 2.x, 5.x en 6.x meer.

Zie [Elasticsearch bijwerken](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) voor volledige instructies voor het maken van back-ups van uw gegevens, het opsporen van potentiële migratiekwesties en het testen van upgrades voordat u deze implementeert naar de productie. Afhankelijk van uw huidige versie van Elasticsearch, is het mogelijk dat een volledige clusterherstart al dan niet vereist is.

Elasticsearch vereist JDK 1.8 of hoger. Zie [De JDK (Java Software Development Kit) installeren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) om te controleren welke versie van JDK is geïnstalleerd.

[Magento configureren voor gebruik van Elasticsearch](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) beschrijft de taken u na het bijwerken van Elasticsearch 2 aan een gesteunde versie moet uitvoeren.

### Extensies van derden

We raden u aan contact op te nemen met de leverancier van de zoekmachine om te bepalen of uw extensie volledig compatibel is met versie 2.4.

## Limiet voor geopende bestanden instellen

Door de limiet voor geopende bestanden in te stellen (ulimit), kan worden voorkomen dat meerdere recursieve aanroepen van lange querytekenreeksen mislukken of dat er problemen optreden met het gebruik van de `bin/magento setup:rollback` gebruiken. Deze opdracht is anders voor verschillende UNIX-schelpen. Raadpleeg uw individuele smaak voor details over `ulimit` gebruiken.

Adobe raadt u aan de geopende bestanden in te stellen [ulimit](http://ss64.com/bash/ulimit.html) op een waarde van `65536` of meer, maar u kunt indien nodig een hogere waarde gebruiken. U kunt de limiet instellen op de opdrachtregel of u kunt deze instellen als een permanente instelling voor de shell van de gebruiker.

U stelt de limiet in vanaf de opdrachtregel:

1. Naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Stel de limiet in op 65536.

   ```bash
   ulimit -s 65536
   ```

   >[!NOTE]
   >
   > De syntaxis voor de maximale waarde voor open bestanden is afhankelijk van de UNIX-shell die u gebruikt. De voorgaande instelling werkt alleen met CentOS en Ubuntu met Bash-shell. Voor Mac OS is de juiste instelling echter -S 65532. Raadpleeg een hoofdpagina of referentie van het besturingssysteem voor meer informatie.

De waarde in de Bash-shell instellen:

1. Naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Openen `/home/<username>/.bashrc` in een teksteditor.
1. Voeg de volgende regel toe:

   ```bash
   ulimit -s 65536
   ```

1. Sla uw wijzigingen op in het dialoogvenster `.bashrc` en sluit de teksteditor af.

>[!IMPORTANT]
>
>We raden u aan geen waarde in te stellen voor de `pcre.recursion_limit` eigenschap in de `php.ini` bestand omdat dit kan resulteren in onvolledige terugdraaiversies zonder foutmelding.

## Controleren of uitsnijdtaken worden uitgevoerd

De de taakplanner van UNIX `cron` is essentieel voor dagelijkse Adobe Commerce- en Magento Open Source-bewerkingen. Het plant dingen als het opnieuw indexeren, nieuwsbrieven, e-mail, sitemaps, etc. Voor verschillende functies is minstens één snijtaak vereist die wordt uitgevoerd als de eigenaar van het bestandssysteem.

Als u wilt controleren of de uitsnijdtaak op de juiste wijze is ingesteld, controleert u de tab door de volgende opdracht in te voeren als de eigenaar van het bestandssysteem:

>[!NOTE]
>
>De tab is het configuratiebestand dat verantwoordelijk is voor het uitvoeren van snijtaken.

```bash
crontab -l
```

Resultaten die vergelijkbaar zijn met het volgende, moeten worden weergegeven:

```cron
#~ MAGENTO START c5f9e5ed71cceaabc4d4fd9b3e827a2b
* * * * * /usr/bin/php /var/www/html/magento2/bin/magento cron:run 2>&1 | grep -v "Ran jobs by schedule" >> /var/www/html/magento2/var/log/magento.cron.log
#~ MAGENTO END c5f9e5ed71cceaabc4d4fd9b3e827a2b
```

Een ander symptoom van niet-actieve kroon is de volgende fout in de Admin:

![](../../assets/upgrade-guide/cron-not-running.png)

Klik op **Systeemberichten** boven aan het venster als volgt:

![](../../assets/upgrade-guide/system-messages.png)

Zie [Uitsnede configureren en uitvoeren](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) voor meer informatie.

## DATA_CONVERTER_BATCH_SIZE instellen

Adobe Commerce 2.4 bevat beveiligingsverbeteringen waarvoor bepaalde gegevens moeten worden omgezet van geserialiseerde gegevens in JSON. Deze conversie vindt plaats tijdens de upgrade en kan lang duren, afhankelijk van de hoeveelheid gegevens in de database.

De volgende tabellen worden het meest beïnvloed:

- `catalogrule`
- `core_config_data`
- `magento_reward_history`
- `quote_payment`
- `quote`
- `sales_order_payment`
- `sales_order`
- `salesrule`
- `url_rewrite`

Als u een grote hoeveelheid gegevens hebt, kunt u de prestaties verbeteren door de waarde van een omgevingsvariabele in te stellen, `DATA_CONVERTER_BATCH_SIZE`. Standaard is de waarde ingesteld op `50,000`.

De omgevingsvariabele instellen:

1. Naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Stel de variabele in:

   ```bash
   export DATA_CONVERTER_BATCH_SIZE 100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` vereist geheugen; U kunt het niet instellen op een grote waarde (ongeveer 1 GB) zonder deze eerst te testen.

1. Nadat de upgrade is voltooid, kunt u de instelling van de variabele ongedaan maken:

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Controleren op bestandssysteemmachtigingen

Om veiligheidsredenen hebben Adobe Commerce en Magento Open Source bepaalde machtigingen voor het bestandssysteem nodig. Machtigingen verschillen van _[eigendom](https://devdocs.magento.com/guides/v2.4/comp-mgr/prereq/prereq_compman-checklist.html#magento-owner-group)_. De eigendom bepaalt wie acties op het dossiersysteem kan uitvoeren; machtigingen bepalen wat de gebruiker kan doen.

Mappen in het bestandssysteem moeten door de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) groep.

Om te controleren of de machtigingen voor het bestandssysteem correct zijn ingesteld, meldt u zich aan bij de toepassingsserver of gebruikt u de toepassing van het bestandsbeheer van de hostingprovider.

Voer bijvoorbeeld de volgende opdracht in als de toepassing is geïnstalleerd in `/var/www/html/magento2`:

```bash
ls -l /var/www/html/magento2
```

Voorbeelduitvoer:

```console
total 1028
drwxrwx---. 12 magento_user apache   4096 Jun  7 07:55 .
drwxr-xr-x.  3 root         root     4096 May 11 14:29 ..
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 app
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 bin
-rw-rw----.  1 magento_user apache 439792 Apr 27 21:23 CHANGELOG.md
-rw-rw----.  1 magento_user apache   3422 Apr 27 21:23 composer.json
-rw-rw----.  1 magento_user apache 425214 Apr 27 21:27 composer.lock
-rw-rw----.  1 magento_user apache   3425 Apr 27 21:23 CONTRIBUTING.md
-rw-rw----.  1 magento_user apache  10011 Apr 27 21:23 CONTRIBUTOR_LICENSE_AGREEMENT.html
-rw-rw----.  1 magento_user apache    631 Apr 27 21:23 COPYING.txt
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 dev
-rw-rw----.  1 magento_user apache   2926 Apr 27 21:23 Gruntfile.js
-rw-rw----.  1 magento_user apache   7592 Apr 27 21:23 .htaccess
-rw-rw----.  1 magento_user apache   6419 Apr 27 21:23 .htaccess.sample
drwxrwx---.  4 magento_user apache   4096 Jun  7 07:53 lib
-rw-rw----.  1 magento_user apache  10376 Apr 27 21:23 LICENSE_AFL.txt
-rw-rw----.  1 magento_user apache  30634 Apr 27 21:23 LICENSE_EE.txt
-rw-rw----.  1 magento_user apache  10364 Apr 27 21:23 LICENSE.txt
-rw-rw----.  1 magento_user apache   4108 Apr 27 21:23 nginx.conf.sample
-rw-rw----.  1 magento_user apache   1427 Apr 27 21:23 package.json
-rw-rw----.  1 magento_user apache   1659 Apr 27 21:23 .php_cs
-rw-rw----.  1 magento_user apache    804 Apr 27 21:23 php.ini.sample
drwxrwx---.  2 magento_user apache   4096 Jun  7 07:53 phpserver
drwxrwx---.  6 magento_user apache   4096 Jun  7 07:53 pub
-rw-rw----.  1 magento_user apache   2207 Apr 27 21:23 README_EE.md
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 setup
-rw-rw----.  1 magento_user apache   3731 Apr 27 21:23 .travis.yml
drwxrwx---.  7 magento_user apache   4096 Jun  7 07:53 update
drwxrws---. 11 magento_user apache   4096 Jun 13 16:05 var
drwxrws---. 29 magento_user apache   4096 Jun  7 07:53 vendor
```

Zie het volgende voor een verklaring van de steekproefoutput:

- De meeste bestanden zijn `-rw-rw----`, die `660`
- `drwxrwx---` = `770`
- `-rw-rw-rw-` = `666`
- De eigenaar van het bestandssysteem is `magento_user`

Als u meer gedetailleerde informatie wilt, voert u de volgende opdracht in:

```bash
ls -la /var/www/html/magento2/pub
```

Omdat Adobe Commerce en Magento Open Source de statische dossieractiva aan subdirectories van `pub`Het is raadzaam ook hier de machtigingen en de eigendom te controleren.

Zie voor meer informatie [Machtigingen en eigendom van bestandssystemen](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

## Stel de `pub/` mapbasis

Zie [Documenthoofdmap wijzigen om de beveiliging te verbeteren](https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html) voor meer informatie .

## De plug-in Composer-update installeren

De [`magento/composer-root-update-plugin`](https://github.com/magento/composer-root-update-plugin) Composer-plug-in verhelpt wijzigingen die in het hoofdproject moeten worden aangebracht `composer.json` bestand te openen voordat de toepassing wordt bijgewerkt naar een nieuwe productvereiste.

De plug-in automatiseert de handmatige upgrade gedeeltelijk door afhankelijkheidsconflicten te identificeren en te helpen oplossen in plaats van deze handmatig te hoeven identificeren en te corrigeren.

De insteekmodule installeren:

1. Voeg het pakket toe aan uw `composer.json` bestand.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Werk de gebiedsdelen bij:

   ```bash
   composer update
   ```