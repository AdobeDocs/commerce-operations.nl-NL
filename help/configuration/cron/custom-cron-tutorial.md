---
title: Een aangepaste uitsnijdtaak en uitsnijdgroep configureren (zelfstudie)
description: Gebruik deze stapsgewijze zelfstudie om een aangepaste uitsnijdtaak te maken.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---


# Een aangepaste uitsnijdtaak configureren

In deze stapsgewijze zelfstudie wordt getoond hoe u een aangepaste uitsnijdtaak en eventueel een uitsnijdgroep in een voorbeeldmodule kunt maken. U kunt een module gebruiken u reeds hebt of u kunt een steekproefmodule van gebruiken [`magento2-samples` opslagplaats][samples].

Als de uitsnijdtaak wordt uitgevoerd, wordt een rij toegevoegd aan de opdracht `cron_schedule` tabel met de naam van de snijtaak, `custom_cron`.

Wij tonen u ook hoe te om naar keuze een kroongroep tot stand te brengen, die u kunt gebruiken om de banen van de douanecurn met montages buiten de toepassingsgebreken van de Handel in werking te stellen.

In deze zelfstudie gaan we uit van het volgende:

- De toepassing Commerce is geïnstalleerd in `/var/www/html/magento2`
- De gebruikersnaam en het wachtwoord van de Commerce-database zijn beide `magento`
- U voert alle handelingen uit als de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)

## Stap 1: Een voorbeeldmodule ophalen

Als u een aangepaste uitsnijdtaak wilt instellen, hebt u een voorbeeldmodule nodig. Wij stellen voor `magento-module-minimal` module.

Als u reeds een steekproefmodule hebt, kunt u het gebruiken; Sla deze stap en de volgende stap over en ga verder met stap 3: Maak een klasse om af te snijden.

**Een voorbeeldmodule ophalen**:

1. Meld u aan bij de Commerce-server als of schakel over naar de [eigenaar van bestandssysteem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Verandering in een folder die niet in uw de toepassingswortel van de Handel is (bijvoorbeeld, uw huisfolder).
1. Klonen met [`magento2-samples` opslagplaats][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   Als de opdracht mislukt met de fout `Permission denied (publickey).`moet u [voeg uw openbare sleutel van SSH aan GitHub.com toe][git-ssh].

1. Maak een map waarnaar de voorbeeldcode moet worden gekopieerd:

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Kopieer de code van de voorbeeldmodule:

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Controleer of de gekopieerde bestanden correct zijn gekopieerd:

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   U zou het volgende resultaat moeten zien:

   ```terminal
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. Werk het gegevensbestand en het schema van de Handel bij:

   ```bash
   bin/magento setup:upgrade
   ```

1. De cache reinigen:

   ```bash
   bin/magento cache:clean
   ```

## Stap 2: De voorbeeldmodule controleren

Controleer voordat u verdergaat of de voorbeeldmodule is geregistreerd en ingeschakeld.

1. Voer de volgende opdracht uit:

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. Zorg ervoor dat de module wordt toegelaten.

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>Als de uitvoer aangeeft dat de `Module does not exist`, evaluatie [Stap 1](#step-1-get-a-sample-module) zorgvuldig. Zorg ervoor dat de code in de juiste map staat. Spelling en case zijn belangrijk; als om het even wat verschillend is, zal de module niet laden. Vergeet ook niet om te starten `magento setup:upgrade`.

## Stap 3: Een klasse maken om af te snijden

In deze stap wordt een eenvoudige klasse weergegeven voor het maken van een uitsnijdtaak. De klasse schrijft alleen een rij naar de `cron_schedule` tabel waarin wordt bevestigd dat deze is ingesteld.

Een klasse maken:

1. Maak een map voor de klasse en wijzig deze in de map:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. Een bestand met de naam `Test.php` in die map met de volgende inhoud:

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## Stap 4: Maken `crontab.xml`

De `crontab.xml` Hiermee stelt u een schema in voor het uitvoeren van uw aangepaste uitsnijdcode.

Maken `crontab.xml` als volgt in de `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` map:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

De voorgaande `crontab.xml` voert de `Magento/SampleMinimal/Cron/Test.php` klasse eenmaal per minuut, waardoor een rij wordt toegevoegd aan de `cron_schedule` tabel.

Om het bouwplan configureerbaar van Admin te maken, gebruik de configuratiepad van uw gebied van de systeemconfiguratie.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

Wanneer `system/config/path` is een pad voor systeemconfiguratie gedefinieerd in `etc/adminhtml/system.xml` van een module.

## Stap 5: Compileer en cache schoon

Compileer de code met deze opdracht:

```bash
bin/magento setup:di:compile
```

En maak de cache schoon met deze opdracht:

```bash
bin/magento cache:clean
```

## Stap 6: De uitsnijdtaak controleren

In deze stap ziet u hoe u de aangepaste uitsnijdtaak kunt verifiëren met een SQL-query op het tabblad `cron_schedule` databasetabel.

Uitsnijden verifiëren:

1. Uitvoeren van Cron-taken:

   ```bash
   bin/magento cron:run
   ```

1. Voer de `magento cron:run` twee of drie keer gebruiken.

   De eerste keer dat u het bevel ingaat, vormt het banen een rij; vervolgens worden de banen in de kron gerund . U moet de opdracht invoeren _ten minste_ twee keer.

1. SQL-query uitvoeren `SELECT * from cron_schedule WHERE job_code like '%custom%'` als volgt:

   1. Enter `mysql -u magento -p`
   1. Bij de `mysql>` prompt, enter `use magento;`
   1. Enter `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      Het resultaat moet vergelijkbaar zijn met het volgende:

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (Optioneel) Controleer of de berichten naar het systeemlogboek van Commerce worden geschreven:

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   U zou één of meerdere ingangen als het volgende moeten zien:

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Deze berichten komen van `execute` methode in `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Als de SQL-opdracht en het systeemlogboek geen vermeldingen bevatten, voert u de opdracht `magento cron:run` nog een paar keer gebruiken en wachten. Het kan enige tijd duren voordat de database wordt bijgewerkt.

## Stap 7 (optioneel): Een aangepaste uitsnijdgroep instellen

In deze stap ziet u hoe u desgewenst een aangepaste uitsnijdgroep instelt. Stel een aangepaste uitsnijdgroep in als u wilt dat de aangepaste uitsnijdtaak volgens een andere planning wordt uitgevoerd dan andere uitsnijdtaken (doorgaans één keer per minuut) of als u meerdere aangepaste uitsnijdtaken met verschillende instellingen wilt uitvoeren.

Een aangepaste uitsnijdgroep instellen:

1. Openen `crontab.xml` in een teksteditor.
1. Wijzigen `<group id="default">` tot `<group id="custom_crongroup">`
1. Sluit de teksteditor.
1. Maken `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` met de volgende inhoud:

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

Voor een beschrijving van wat de opties betekenen, raadpleegt u [Referentie voor curven aanpassen](custom-cron-reference.md).

## Stap 8: Aangepaste uitsnijdgroep verifiëren

Dit _optioneel_ toont u hoe u uw aangepaste uitsnijdgroep kunt verifiëren met de beheerfunctie.

De aangepaste uitsnijdgroep verifiëren:

1. Uitvoeren van afhandelingstaken voor uw aangepaste groep:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Voer de opdracht ten minste tweemaal uit.

1. De cache reinigen:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Meld u als beheerder aan bij de beheerder.
1. Klikken **Winkels** > **Instellingen** > **Configuratie** > **Geavanceerd** > **Systeem**.
1. Vouw in het rechterdeelvenster uit **Cron**.

   Uw uitsnijdgroep wordt als volgt weergegeven:

   ![Je aangepaste uitsnijdgroep](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
