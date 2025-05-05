---
title: Volledige voorwaarden
description: Bereid uw Adobe Commerce-project voor op een upgrade door deze vereiste stappen uit te voeren.
exl-id: f7775900-1d10-4547-8af0-3d1283d9b89e
source-git-commit: df185e21f918d32ed5033f5db89815b5fc98074f
workflow-type: tm+mt
source-wordcount: '1866'
ht-degree: 0%

---

# Volledige upgradevoorwaarden

Het is belangrijk te begrijpen wat nodig is om Adobe Commerce te runnen. U moet eerst de [ systeemvereisten ](../../installation/system-requirements.md) voor de versie herzien u van plan bent te bevorderen aan.

Nadat u de systeemvereisten hebt gecontroleerd, moet u aan de volgende voorwaarden voldoen voordat u de upgrade van uw systeem uitvoert:

* Alle software bijwerken
* Controleren of een ondersteund zoekprogramma is geïnstalleerd
* Database-tabelindeling converteren
* Limiet voor geopende bestanden instellen
* Controleren of uitsnijdtaken worden uitgevoerd
* Instellen `DATA_CONVERTER_BATCH_SIZE`
* Controleren op bestandssysteemmachtigingen
* De `pub/` hoofdmap instellen
* Installeer de Composer update plugin

## Alle software bijwerken

De [ systeemvereisten ](../../installation/system-requirements.md) beschrijven precies welke versies van derdesoftware met de versies van Adobe Commerce zijn getest.

Zorg ervoor dat u alle systeemvereisten en afhankelijkheden in uw omgeving hebt bijgewerkt. Zie PHP [ 7.4 ](https://www.php.net/manual/en/migration74.php), PHP [ 8.0 ](https://www.php.net/manual/en/migration80.php), PHP [ 8.1 ](https://www.php.net/manual/en/migration81.php), en [ vereiste PHP montages ](../../installation/prerequisites/php-settings.md#php-settings).

>[!NOTE]
>
>Voor Adobe Commerce op de Pro projecten van de wolkeninfrastructuur, moet u a [&#128279;](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) kaartje van de Steun {creëren 0} om de diensten in het Opvoeren en van de Productie milieu&#39;s te installeren of bij te werken.  Geef aan welke servicewijzigingen nodig zijn en neem de bijgewerkte `.magento.app.yaml` - en `services.yaml` -bestanden en PHP-versie op in het ticket. Het kan tot 48 uur duren voordat het infrastructuurteam van de cloud uw project kan bijwerken. Zie [ Ondersteunde software en de diensten ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#supported-software-and-services).

## Controleer of een ondersteunde zoekmachine is geïnstalleerd

Adobe Commerce vereist dat Elasticsearch of OpenSearch is geïnstalleerd om de software te kunnen gebruiken.

**als u van 2.3.x aan 2.4** bevordert, moet u controleren of u MySQL, Elasticsearch, of een derdeuitbreiding als uw motor van de catalogusonderzoek in uw 2.3.x instantie gebruikt. Het resultaat bepaalt wat u _vóór_ bevordering aan 2.4 moet doen.

**als u flardversies binnen de 2.3.x of 2.4.x versielijnen** bevordert, als Elasticsearch 7.x reeds geïnstalleerd is, kunt u naar keuze [ migreren aan OpenSearch ](opensearch-migration.md).

U kunt de opdrachtregel of de beheerder gebruiken om de zoekengine voor de catalogus te bepalen:

* Voer de `bin/magento config:show catalog/search/engine` opdracht in. De opdracht retourneert een waarde van `mysql`, `elasticsearch` (die aangeeft dat Elasticsearch 2 is geconfigureerd), `elasticsearch5`, `elasticsearch6`, `elasticsearch7`of een aangepaste waarde, die aangeeft dat u een zoekmachine van derden hebt geïnstalleerd. Voor versies ouder dan 2.4.6 gebruikt u de `elasticsearch7` waarde voor de Elasticsearch 7- of OpenSearch-engine. Gebruik voor versie 2.4.6 en hoger de `opensearch` waarde voor de OpenSearch-engine.

* Controleer in de beheerder de waarde van het **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]** > **[!UICONTROL Search Engine]** veld.

In de volgende secties wordt beschreven welke acties u moet ondernemen voordat u een upgrade naar 2.4.0 uitvoert.

### MySQL

Vanaf 2.4, is MySQL niet meer een gesteunde motor van de catalogusonderzoek. U moet Elasticsearch of OpenSearch installeren en configureren voordat u een upgrade uitvoert. Gebruik de volgende bronnen om u door dit proces te begeleiden:

* [Elasticsearch installeren en configureren](../../configuration/search/overview-search.md)
* [ Installerend Elasticsearch ](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
* Vorm [ nginx ](../../installation/prerequisites/search-engine/configure-nginx.md) of [ Apache ](../../installation/prerequisites/search-engine/configure-apache.md) om met uw onderzoeksmotor te werken
* [ vorm Commerce om Elasticsearch ](../../configuration/search/configure-search-engine.md) en herdex te gebruiken

Bepaalde zoekprogramma&#39;s voor catalogi van derden worden boven op de zoekfunctie van Adobe Commerce uitgevoerd. Neem contact op met de leverancier om te bepalen of u de extensie moet bijwerken.

### Wijzigingen in MySQL 8.4

Adobe heeft in de release 2.4.8 ondersteuning toegevoegd voor MySQL 8.4.
Deze sectie beschrijft belangrijke veranderingen in MySQL 8.4 dat de ontwikkelaars zich van bewust zouden moeten zijn.

#### Vervangen niet-standaardsleutel

Het gebruik van niet-unieke of gedeeltelijke sleutels als refererende sleutels is niet-standaard en wordt afgeschaft in MySQL 8.4. Vanaf MySQL 8.4.0 moet u dergelijke sleutels expliciet inschakelen door deze in te stellen [`restrict_fk_on_non_standard_key`](https://dev.mysql.com/doc/refman/8.4/en/server-system-variables.html#sysvar_restrict_fk_on_non_standard_key) op `OFF`, of door de server te starten met de `--skip-restrict-fk-on-non-standard-key` optie.

#### Upgraden van MySQL 8.0 (of oudere versies) naar MySQL 8.4

Om MySQL correct te upgraden van versie 8.0 naar versie 8.4, moet u de volgende stappen volgen:

1. Onderhoudsmodus inschakelen:

   ```bash
   bin/magento maintenance:enable
   ```

1. Maak een back-up van de database:

   ```bash
   bin/magento setup:backup --db
   ```

1. Upgrade MySQL naar versie 8.4.
1. Stel `restrict_fk_on_non_standard_key` in op `OFF` in `[mysqld]` in het `my.cnf` -bestand.

   ```bash
   [mysqld]
   restrict_fk_on_non_standard_key = OFF 
   ```

   >[!WARNING]
   >
   >Als u de waarde van `restrict_fk_on_non_standard_key` niet wijzigt in `OFF` , treedt de volgende fout op tijdens het importeren:
   >
   >```sql
   > ERROR 6125 (HY000) at line 2164: Failed to add the foreign key constraint. Missing unique key for constraint 'CAT_PRD_FRONTEND_ACTION_PRD_ID_CAT_PRD_ENTT_ENTT_ID' in the referenced table 'catalog_product_entity'
   >```
1. Start de MySQL-server opnieuw.
1. Importeer de back-upgegevens in MySQL.
1. De cache reinigen:

   ```bash
   bin/magento cache:clean
   ```

1. Onderhoudsmodus uitschakelen:

   ```bash
   bin/magento maintenance:disable
   ```

#### MariaDB

{{$include /help/_includes/maria-db-config.md}}

### Zoekmachine

U moet Elasticsearch 7.6 of hoger of OpenSearch 1.2 installeren en configureren voordat u de upgrade naar 2.4.0 uitvoert. Adobe biedt niet langer ondersteuning voor Elasticsearch 2.x, 5.x en 6.x. [ de motorconfiguratie van het Onderzoek ](../../configuration/search/configure-search-engine.md) in de _Gids van de Configuratie_ beschrijft de taken u na de bevordering van Elasticsearch aan een gesteunde versie moet uitvoeren.

Verwijs naar [ Bevorderend Elasticsearch ](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) voor volledige instructies bij het steunen van uw gegevens, het ontdekken van potentiële migratiekwesties, en het testen van verbeteringen alvorens aan productie op te stellen. Afhankelijk van uw huidige versie van Elasticsearch is het mogelijk dat een volledige cluster opnieuw moet worden opgestart.

Elasticsearch vereist Java Development Kit (JDK) 1.8 of hoger. Zie [ de Uitrusting van de Ontwikkeling van de Software van Java installeren (JDK) ](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) om te controleren welke versie van JDK geïnstalleerd is.

#### OpenSearch

OpenSearch is een open-source vork van Elasticsearch 7.10.2, na de licentiewijziging van Elasticsearch. In de volgende versies van Adobe Commerce wordt ondersteuning voor OpenSearch geïntroduceerd:

* 2.4.6 (OpenSearch heeft een aparte module en instellingen)
* 2.4.5.
* 2.4.4.
* 2.4.3-p2
* 2.3.7-p3

U kunt [ migreren van Elasticsearch aan OpenSearch ](opensearch-migration.md) slechts als u aan een versie van hierboven vermelde Adobe Commerce (of hoger) bevordert.

Voor OpenSearch is JDK 1.8 of hoger vereist. Zie [ de Uitrusting van de Ontwikkeling van de Software van Java installeren (JDK) ](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) om te controleren welke versie van JDK geïnstalleerd is.

[ de motorconfiguratie van het Onderzoek ](../../configuration/search/configure-search-engine.md) beschrijft de taken u na het veranderen van onderzoeksmotoren moet uitvoeren.

#### Upgrade uitvoeren voor Elasticsearch

Elasticsearch 8.x werd in Adobe Commerce 2.4.6 ondersteund. De volgende instructies tonen een voorbeeld van het upgraden van Elasticsearch van 7.x naar 8.x:

>[!NOTE]
>
>In de aanstaande versie 2.4.8, zullen deze stappen niet noodzakelijk zijn omdat Elasticsearch 8 module door gebrek inbegrepen is en u zult niet het moeten afzonderlijk installeren.

1. Upgrade de Elasticsearch 7.x server naar 8.x en zorg ervoor dat deze actief is. Zie de [ documentatie van Elasticsearch ](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Schakel het veld `id_field_data` in door de volgende configuratie aan uw `elasticsearch.yml` -bestand toe te voegen en de Elasticsearch 8.x-service opnieuw te starten.

   ```yaml
   indices:
     id_field_data:
       enabled: true
   ```

   >[!INFO]
   >
   >Ter ondersteuning van Elasticsearch 8.x wordt in Adobe Commerce 2.4.6 de eigenschap `indices.id_field_data` standaard uitgeschakeld en wordt het veld `_id` in de eigenschap `docvalue_fields` gebruikt.

1. Werk in de hoofdmap van uw Adobe Commerce-project uw Composer-afhankelijkheden bij om de module `Magento_Elasticsearch7` te verwijderen en de module `Magento_Elasticsearch8` te installeren.

   ```bash
   composer require magento/module-elasticsearch-8 --update-with-all-dependencies
   ```

   Als u een gebiedsdeelfout voor `psr/http-message` ontmoet, klik om de volgende het oplossen van problemensectie uit te breiden:

   +++Problemen oplossen

   Als er afhankelijkheidsconflicten optreden tijdens de installatie van Elasticsearch 8, met name met `psr/http-message` , kunt u dit oplossen door de volgende stappen uit te voeren:

   1. Ten eerste hebt u de Elasticsearch 8-module nodig zonder andere afhankelijkheden bij te werken:

      ```bash
      composer require magento/module-elasticsearch-8 --no-update
      ```

   1. Werk vervolgens de Elasticsearch 8-module en `aws/aws-sdk-php` -pakketten bij:

      ```bash
      composer update magento/module-elasticsearch-8 aws/aws-sdk-php -W
      ```

   Deze aanpak werkt voor 2.4.7-p4 met PHP 8.3. Het probleem doet zich voor omdat `aws/aws-sdk-php` `psr/http-message >= 2.0` vereist, wat conflicten kan veroorzaken. De bovenstaande stappen helpen deze afhankelijkheidsproblemen op te lossen.

   +++

1. Werk uw projectcomponenten bij.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configureer Elasticsearch](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) in de [!DNL Admin].

1. Indexeer de catalogusindex opnieuw.

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

1. Verwijder alle items uit de ingeschakelde cachetypen.

   ```bash
   bin/magento cache:clean
   ```

#### Elasticsearch downgraden

Als u onbedoeld de versie van Elasticsearch op uw server verbetert of om een andere reden bepaalt dat u moet degraderen, moet u ook uw Adobe Commerce-projectgebiedsdelen bijwerken. Bijvoorbeeld om van Elasticsearch 8.x naar 7.x te verlagen

1. Verlaag de Elasticsearch 8.x-server naar 7.x en zorg ervoor dat deze actief is. Zie de [ documentatie van Elasticsearch ](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html).

1. Werk in de hoofdmap van uw Adobe Commerce-project uw Composer-afhankelijkheden bij om de module `Magento_Elasticsearch8` en de bijbehorende Composer-afhankelijkheden te verwijderen en installeer de module `Magento_Elasticsearch7` .

   ```bash
   composer remove magento/module-elasticsearch-8
   ```

1. Werk uw projectcomponenten bij.

   ```bash
   bin/magento setup:upgrade
   ```

1. [ vorm Elasticsearch ](../../configuration/search/configure-search-engine.md#configure-your-search-engine-from-the-admin) in [!DNL Admin].

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

U moet de indeling van alle databasetabellen omzetten van `COMPACT` in `DYNAMIC` . U moet ook het type opslagengine omzetten van `MyISAM` in `InnoDB` . Bekijk [best practices](../../implementation-playbook/best-practices/maintenance/mariadb-upgrade.md).

## De limiet voor geopende bestanden instellen

Door de limiet voor open bestanden (ulimit) in te stellen, kunt u voorkomen dat er fouten optreden door meerdere recursieve aanroepen van lange queryreeksen of problemen met het gebruik van de `bin/magento setup:rollback` opdracht. Dit commando is verschillend voor verschillende UNIX-shells. Raadpleeg uw individuele smaak voor meer informatie over het `ulimit` commando.

Adobe raadt aan om de geopende bestanden [u-limit](https://ss64.com/bash/ulimit.html) in te stellen op een waarde van `65536` of meer, maar u kunt indien nodig een grotere waarde gebruiken. U kunt de ulimit instellen op de opdrachtregel of u kunt er een permanente instelling van maken voor de shell van de gebruiker.

U stelt de limiet in vanaf de opdrachtregel:

1. Schakelaar aan de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).
1. Stel de limiet in op `65536` .

   ```bash
   ulimit -n 65536
   ```

De waarde in de Bash-shell instellen:

1. Schakelaar aan de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).
1. Open `/home/<username>/.bashrc` in een teksteditor.
1. Voeg de volgende regel toe:

   ```bash
   ulimit -n 65536
   ```

1. Sla de wijzigingen op in het `.bashrc` -bestand en sluit de teksteditor af.

>[!IMPORTANT]
>
>We raden u aan geen waarde in te stellen voor de eigenschap `pcre.recursion_limit` in het `php.ini` -bestand, omdat dit kan leiden tot onvolledige terugdraaiversies zonder foutmelding.

## Controleren of uitsnijdtaken worden uitgevoerd

De UNIX-taakplanner `cron` is van essentieel belang voor dagelijkse Adobe Commerce-bewerkingen. Het plant dingen zoals het opnieuw indexeren, nieuwsbrieven, e-mail, en sitemaps. Voor verschillende functies is minstens één snijtaak vereist die wordt uitgevoerd als de eigenaar van het bestandssysteem.

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

![ de berichten van het Systeem - krong loopt niet ](../../assets/upgrade-guide/cron-not-running.png)

Om de fout te zien, klik **Berichten van het Systeem** bij de bovenkant van het venster als volgt:

![ de berichten van het Systeem bericht ](../../assets/upgrade-guide/system-messages.png)

Zie [ uitsnede ](../../configuration/cli/configure-cron-jobs.md) voor meer informatie vormen en in werking stellen.

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

Als u veel gegevens hebt, kunt u de prestaties verbeteren door de waarde van een omgevingsvariabele in te stellen, `DATA_CONVERTER_BATCH_SIZE` . De waarde wordt standaard ingesteld op `50,000` .

De omgevingsvariabele instellen:

1. Schakelaar aan de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).
1. Stel de variabele in:

   ```bash
   export DATA_CONVERTER_BATCH_SIZE=100000
   ```

   >[!NOTE]
   >
   > Voor `DATA_CONVERTER_BATCH_SIZE` is geheugen vereist. Stel dit niet in op een grote waarde (ongeveer 1 GB) zonder deze eerst te testen.

1. Nadat de upgrade is voltooid, kunt u de instelling van de variabele ongedaan maken:

   ```bash
   unset DATA_CONVERTER_BATCH_SIZE
   ```

## Controleren op bestandssysteemmachtigingen

Om veiligheidsredenen vereist Adobe Commerce bepaalde machtigingen voor het bestandssysteem. De toestemmingen zijn verschillend van _[eigendom](../../upgrade/prepare/prerequisites.md#verify-file-system-permissions)_. Eigendom bepaalt wie handelingen op het bestandssysteem kan uitvoeren; machtigingen bepalen wat de gebruiker kan doen.

De folders in het dossiersysteem moeten door de [&#128279;](../../installation/prerequisites/file-system/overview.md) groep van de eigenaar van het 0&rbrace; dossiersysteem kunnen worden geschreven.

Om te controleren of de machtigingen voor het bestandssysteem correct zijn ingesteld, meldt u zich aan bij de toepassingsserver of gebruikt u de toepassing van het bestandsbeheer van de hostingprovider.

Voer bijvoorbeeld de volgende opdracht in als de toepassing is geïnstalleerd in `/var/www/html/magento2` :

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

* De meeste bestanden zijn `-rw-rw----` , dat is `660`
* `drwxrwx---` = `770`
* `-rw-rw-rw-` = `666`
* De eigenaar van het bestandssysteem is `magento_user`

Als u meer gedetailleerde informatie wilt, voert u de volgende opdracht in:

```bash
ls -la /var/www/html/magento2/pub
```

Omdat Adobe Commerce statische bestandselementen naar submappen van `pub` implementeert, is het een goed idee om ook daar machtigingen en eigendom te controleren.

Voor meer informatie, zie {de systeemtoestemmingen en eigendom van het 0} Dossier [&#128279;](../../installation/prerequisites/file-system/overview.md).

## De hoofdmap van de map `pub/` instellen

Zie [ docroot wijzigen om veiligheid ](../../installation/tutorials/docroot.md) voor meer details te verbeteren.

## De plug-in Composer-update installeren

De [`magento/composer-root-update-plugin` ](https://github.com/magento/composer-root-update-plugin) Composer-plug-in verhelpt wijzigingen die moeten worden aangebracht in het hoofdprojectbestand `composer.json` voordat de toepassing wordt bijgewerkt naar een nieuwe productvereiste.

De plug-in automatiseert de handmatige upgrade gedeeltelijk door afhankelijkheidsconflicten te identificeren en te helpen oplossen in plaats van deze handmatig te hoeven identificeren en te corrigeren.

De insteekmodule installeren:

1. Voeg het pakket toe aan het `composer.json` -bestand.

   ```bash
   composer require magento/composer-root-update-plugin ~2.0 --no-update
   ```

1. Werk de gebiedsdelen bij:

   ```bash
   composer update
   ```
