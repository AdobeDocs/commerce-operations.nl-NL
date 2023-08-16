---
title: Volledige voorwaarden
description: Bereid uw Adobe Commerce-project voor op een upgrade door deze vereiste stappen uit te voeren.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---

# Volledige upgradevoorwaarden

Het is belangrijk te begrijpen wat nodig is om Adobe Commerce te runnen. U moet eerst de [systeemvereisten](../../installation/system-requirements.md) voor de versie waarnaar u wilt upgraden.

Nadat u de systeemvereisten hebt gecontroleerd, moet u aan de volgende voorwaarden voldoen voordat u de upgrade van uw systeem uitvoert:

* Alle software bijwerken
* Controleren of een ondersteund zoekprogramma is geïnstalleerd
* Database-tabelindeling converteren
* Limiet voor geopende bestanden instellen
* Controleren of uitsnijdtaken worden uitgevoerd
* Set `DATA_CONVERTER_BATCH_SIZE`
* Controleren op bestandssysteemmachtigingen
* Stel de `pub/` mapbasis
* De plug-in Composer-update installeren

## Alle software bijwerken

De [systeemvereisten](../../installation/system-requirements.md) exact beschrijven welke versies van software van derden zijn getest met Adobe Commerce-releases.

Zorg ervoor dat u alle systeemvereisten en afhankelijkheden in uw omgeving hebt bijgewerkt. Zie PHP [7,4](https://www.php.net/manual/en/migration74.php), PHP [8,0](https://www.php.net/manual/en/migration80.php), PHP [8,1](https://www.php.net/manual/en/migration81.php), en [vereiste PHP-instellingen](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Voor Adobe Commerce op cloud Infrastructure Pro-projecten moet u een [Ondersteuning](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) ticket voor installatie of update van services in een testomgeving. Geef aan welke servicewijzigingen nodig zijn en neem uw bijgewerkte `.magento.app.yaml` en `services.yaml` bestanden en PHP-versie in het ticket. Het kan tot 48 uur duren voordat het infrastructuurteam van de cloud uw project kan bijwerken. Zie [Ondersteunde software en services](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Controleren of een ondersteund zoekprogramma is geïnstalleerd

Adobe Commerce vereist dat Elasticsearch of OpenSearch is geïnstalleerd om de software te kunnen gebruiken.

**Als u een upgrade uitvoert van 2.3.x naar 2.4**, moet u controleren of u MySQL, Elasticsearch, of een derdextensie als uw motor van de catalogusonderzoek in uw 2.3.x instantie gebruikt. Het resultaat bepaalt wat u moet doen _voor_ opwaardering tot 2.4.

**Als u patchreleases bijwerkt binnen de releaselijnen 2.3.x of 2.4.x** Als Elasticsearch 7.x al is geïnstalleerd, kunt u [migreren naar OpenSearch](opensearch-migration.md).

U kunt de opdrachtregel of de beheerder gebruiken om de zoekengine voor de catalogus te bepalen:

* Voer de `bin/magento config:show catalog/search/engine` gebruiken. De opdracht retourneert een waarde van `mysql`, `elasticsearch` (wat erop wijst dat Elasticsearch 2 wordt gevormd), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`of een aangepaste waarde die aangeeft dat u een zoekprogramma van derden hebt geïnstalleerd. Voor versies ouder dan 2.4.6 gebruikt u de opdracht `elasticsearch7` waarde voor Elasticsearch 7 of OpenSearch motor. Voor versie 2.4.6 en hoger gebruikt u de opdracht `opensearch` waarde voor de OpenSearch-engine.

* Controleer vanuit de beheerder de waarde van de **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** veld.

In de volgende secties wordt beschreven welke handelingen u moet uitvoeren voordat u de upgrade naar 2.4.0 uitvoert.

### MySQL

Vanaf 2.4, is MySQL niet meer een gesteunde motor van de catalogusonderzoek. U moet Elasticsearch of OpenSearch installeren en configureren voordat u een upgrade uitvoert. Gebruik de volgende bronnen om u door dit proces te begeleiden:

* [Elasticsearch installeren en configureren](../../configuration/search/overview-search.md)
* [Elasticsearch installeren](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Configureren [nginx](../../installation/prerequisites/search-engine/configure-nginx.md) of [Apache](../../installation/prerequisites/search-engine/configure-apache.md) om met uw zoekmachine te werken
* [Handel configureren om Elasticsearch te gebruiken](../../configuration/search/configure-search-engine.md) en opnieuw indexeren

Bepaalde zoekprogramma&#39;s voor catalogi van derden worden boven op de zoekfunctie van Adobe Commerce uitgevoerd. Neem contact op met de leverancier om te bepalen of u de extensie moet bijwerken.

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Zoekmachine

U moet of Elasticsearch 7.6 of hoger of OpenSearch 1.2 installeren en vormen alvorens aan 2.4.0 te bevorderen. Adobe ondersteunt Elasticsearch 2.x, 5.x en 6.x niet meer. [Configuratie van zoekmachine](../../configuration/search/configure-search-engine.md) in de _Configuratiegids_ beschrijft de taken u na bevordering van Elasticsearch aan een gesteunde versie moet uitvoeren.

Zie [Elasticsearch bijwerken](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) voor volledige instructies voor het maken van back-ups van uw gegevens, het opsporen van potentiële migratiekwesties en het testen van upgrades voordat u deze implementeert naar de productie. Afhankelijk van uw huidige versie van Elasticsearch is het mogelijk dat een volledige clusterherstart al dan niet vereist is.

Voor Elasticsearch is Java Development Kit (JDK) 1.8 of hoger vereist. Zie [De JDK (Java Software Development Kit) installeren](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) om te controleren welke versie van JDK is geïnstalleerd.

#### OpenSearch

OpenSearch is een open-source vork van Elasticsearch 7.10.2, na de licentiewijziging van de Elasticsearch. In de volgende versies van Adobe Commerce wordt ondersteuning voor OpenSearch geïntroduceerd:

* 2.4.6 (OpenSearch heeft een aparte module en instellingen)
* 2.4.5
* 2.4.4
* 2.4.3-p2
* 2.3.7-p3

U kunt [migreren van Elasticsearch naar OpenSearch](opensearch-migration.md) alleen als u een upgrade uitvoert naar een hierboven vermelde versie van Adobe Commerce (of hoger).

Voor OpenSearch is JDK 1.8 of hoger vereist. Zie [De JDK (Java Software Development Kit) installeren](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) om te controleren welke versie van JDK is geïnstalleerd.

[Configuratie van zoekmachine](../../configuration/search/configure-search-engine.md) beschrijft de taken u na veranderende onderzoeksmotoren moet uitvoeren.

#### Upgrade Elasticsearch

Ondersteuning voor Elasticsearch 8.x werd geïntroduceerd in Adobe Commerce 2.4.6. De volgende instructies tonen een voorbeeld van het upgraden van Elasticsearch van 7.x naar 8.x:

1. Voer een upgrade uit van de Elasticsearch 7.x-server naar 8.x en zorg ervoor dat deze actief is. Zie de [Documentatie Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. De optie `id_field_data` veld door de volgende configuratie aan uw `elasticsearch.yml` en opnieuw starten van de Elasticsearch 8.x-service.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Om Elasticsearch 8.x te ondersteunen, maakt Adobe Commerce 2.4.6 de `indices.id_field_data` eigenschap standaard in en gebruikt de `_id` in het veld `docvalue_fields` eigenschap.

1. Werk in de hoofdmap van uw Adobe Commerce-project uw Composer-afhankelijkheden bij om de `Magento_Elasticsearch7` en installeer de `Magento_Elasticsearch8` -module.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

1. Werk uw projectcomponenten bij.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Elasticsearch configureren](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) in de [!DNL Admin].

1. Indexeer de catalogusindex opnieuw.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Verwijder alle items uit de ingeschakelde cachetypen.

   ```bash
   bin/magento cache:clean
   ```

#### Elasticsearch verlagen

Als u per ongeluk de versie van de Elasticsearch op uw server bijwerkt of om een andere reden wilt verlagen, moet u ook uw Adobe Commerce-projectafhankelijkheden bijwerken. Bijvoorbeeld om van Elasticsearch 8.x aan 7.x te degraderen

1. Verlaag de Elasticsearch 8.x-server naar 7.x en zorg ervoor dat deze in gebruik is. Zie de [Documentatie Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Werk in de hoofdmap van uw Adobe Commerce-project uw Composer-afhankelijkheden bij om de `Magento_Elasticsearch8` en de bijbehorende Composer-afhankelijkheden en installeer de `Magento_Elasticsearch7` -module.

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Werk uw projectcomponenten bij.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Elasticsearch configureren](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) in de [!DNL Admin].

1. Indexeer de catalogusindex opnieuw.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Verwijder alle items uit de ingeschakelde cachetypen.

   ```bash
   bin/magento cache:clean
   ```

### Extensies van derden

We raden u aan contact op te nemen met uw leverancier van zoekprogramma&#39;s om te bepalen of uw extensie volledig compatibel is met een Adobe Commerce-versie.

## Database-tabelindeling converteren

U moet de indeling van alle databasetabellen omzetten vanuit `COMPACT` tot `DYNAMIC`. U moet ook het type opslagengine omzetten van `MyISAM` tot `InnoDB`. Zie [best practices](../../implementation-playbook/best-practices/maintenance/commerce-235-upgrade-prerequisites-mariadb.md).

## Limiet voor geopende bestanden instellen

Door de limiet voor geopende bestanden in te stellen (ulimit), kan worden voorkomen dat meerdere recursieve aanroepen van lange querytekenreeksen mislukken of dat er problemen optreden met het gebruik van de `bin/magento setup:rollback` gebruiken. Deze opdracht is anders voor verschillende UNIX-schelpen. Raadpleeg uw individuele smaak voor details over `ulimit` gebruiken.

Adobe raadt u aan de geopende bestanden in te stellen [ulimit](https://ss64.com/bash/ulimit.html) op een waarde van `65536` of meer, maar u kunt indien nodig een hogere waarde gebruiken. U kunt de limiet instellen op de opdrachtregel of u kunt deze instellen als een permanente instelling voor de shell van de gebruiker.

U stelt de limiet in vanaf de opdrachtregel:

1. Schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Stel de limiet in op `65536`.

   ```bash
   ulimit -n 65536
   ```

De waarde in de Bash-shell instellen:

1. Schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Openen `/home/<username>/.bashrc` in een teksteditor.
1. Voeg de volgende regel toe:

   ```bash
   ulimit -n 65536
   ```

1. Sla uw wijzigingen op in het dialoogvenster `.bashrc` en sluit de teksteditor af.

>[!IMPORTANT]
>
>We raden u aan geen waarde in te stellen voor de `pcre.recursion_limit` eigenschap in de `php.ini` bestand omdat dit kan resulteren in onvolledige terugdraaiversies zonder foutmelding.

## Controleren of uitsnijdtaken worden uitgevoerd

De de taakplanner van UNIX `cron` is essentieel voor dagelijkse Adobe Commerce-bewerkingen. Het plant dingen zoals het opnieuw indexeren, nieuwsbrieven, e-mail, en sitemaps. Voor verschillende functies is minstens één snijtaak vereist die wordt uitgevoerd als de eigenaar van het bestandssysteem.

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

Zie [Uitsnede configureren en uitvoeren](../../configuration/cli/configure-cron-jobs.md) voor meer informatie .

## DATA_CONVERTER_BATCH_SIZE instellen

Adobe Commerce 2.4 bevat beveiligingsverbeteringen waarvoor bepaalde gegevens moeten worden omgezet van geserialiseerde gegevens in JSON. Deze conversie vindt plaats tijdens de upgrade en kan lang duren, afhankelijk van de hoeveelheid gegevens in de database.

De volgende tabellen worden het meest beïnvloed:

* `catalogrule`
* `core_config_data`
* `magento_reward_history`
* `quote_payment`
* `quote`
* `sales_order_payment`
* `sales_order`
* `salesrule`
* `url_rewrite`

Als u een grote hoeveelheid gegevens hebt, kunt u de prestaties verbeteren door de waarde van een omgevingsvariabele in te stellen, `DATA_CONVERTER_BATCH_SIZE`. Standaard is de waarde ingesteld op `50,000`.

De omgevingsvariabele instellen:

1. Schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Stel de variabele in:

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > `DATA_CONVERTER_BATCH_SIZE` vereist geheugen; gebruik liever geen grote waarde (ongeveer 1 GB) zonder deze eerst te testen.

1. Nadat de upgrade is voltooid, kunt u de instelling van de variabele ongedaan maken:

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Controleren op bestandssysteemmachtigingen

Om veiligheidsredenen vereist Adobe Commerce bepaalde machtigingen voor het bestandssysteem. Machtigingen verschillen van _[eigendom](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. Eigendom bepaalt wie handelingen op het bestandssysteem kan uitvoeren; machtigingen bepalen wat de gebruiker kan doen.

Mappen in het bestandssysteem moeten door de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md) groep.

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

* De meeste bestanden zijn `-rw-rw----`, die `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* De eigenaar van het bestandssysteem is `magento_user`

Als u meer gedetailleerde informatie wilt, voert u de volgende opdracht in:

```bash
ls -la /var/www/html/magento2/pub
```

Omdat Adobe Commerce statische bestandselementen implementeert in submappen van `pub`, is het een goed idee om ook daar toestemmingen en eigendom te verifiëren.

Zie voor meer informatie [Machtigingen en eigendom van bestandssystemen](../../installation/prerequisites/file-system/overview.md).

## Stel de `pub/` mapbasis

Zie [Documenthoofdmap wijzigen om de beveiliging te verbeteren](../../installation/tutorials/docroot.md) voor meer informatie .

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
