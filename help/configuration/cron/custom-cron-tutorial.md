---
title: Een aangepaste uitsnijdtaak en uitsnijdgroep configureren (zelfstudie)
description: Leer hoe u met deze stapsgewijze zelfstudie voor Adobe Commerce aangepaste uitsnijdtaken kunt maken. De configuratie van de module en de groep van de cron ontdekken.
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Een aangepaste uitsnijdtaak configureren

Deze geleidelijke zelfstudie laat zien hoe u een aangepaste uitsnijdtaak en eventueel een uitsnijdgroep in een voorbeeldmodule kunt maken. U kunt een module gebruiken u reeds hebt of u kunt een steekproefmodule van onze [`magento2-samples` bewaarplaats &#x200B;](https://github.com/magento/magento2-samples) gebruiken.

Als u de uitsnijdtaak uitvoert, wordt een rij toegevoegd aan de `cron_schedule` -tabel met de naam van de uitsnijdtaak, `custom_cron` .

U ziet ook hoe u desgewenst een uitsnijdgroep kunt maken, waarmee u aangepaste uitsnijdtaken kunt uitvoeren met andere instellingen dan de standaardinstellingen van Commerce-toepassingen.

In deze zelfstudie gaan we uit van het volgende:

- De Commerce-toepassing wordt geïnstalleerd in `/var/www/html/magento2`
- De gebruikersnaam en het wachtwoord voor de Commerce-database zijn allebei `magento`
- U voert alle acties als [&#x200B; eigenaar van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md) uit

## Stap 1: Een voorbeeldmodule ophalen

Als u een aangepaste uitsnijdtaak wilt instellen, hebt u een voorbeeldmodule nodig. We raden de module `magento-module-minimal` aan.

Als u reeds een steekproefmodule hebt, kunt u het gebruiken; sla deze stap en de volgende stap over en ga met Stap 3 verder: creeer een klasse om kroon in werking te stellen.

**om een steekproefmodule** te krijgen:

1. Login aan uw server van Commerce als, of schakelaar aan, de [&#x200B; eigenaar van het dossiersysteem &#x200B;](../../installation/prerequisites/file-system/overview.md).
1. Ga naar een map die zich niet in de hoofdmap van de Commerce-toepassing bevindt (bijvoorbeeld de thuismap).
1. Kloont de [`magento2-samples` bewaarplaats &#x200B;](https://github.com/magento/magento2-samples).

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   Als het bevel met de fout `Permission denied (publickey).` ontbreekt, moet u [&#x200B; uw openbare sleutel van SSH aan GitHub.com &#x200B;](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) toevoegen.

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

   ```
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

1. De Commerce-database en -schema bijwerken:

   ```bash
   bin/magento setup:upgrade
   ```

1. De cache reinigen:

   ```bash
   bin/magento cache:clean
   ```

## Stap 2: Verifieer de steekproefmodule

Controleer voordat u verdergaat of de voorbeeldmodule is geregistreerd en ingeschakeld.

1. Voer de volgende opdracht uit:

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. Zorg ervoor dat de module wordt toegelaten.

   ```
   Module is enabled
   ```

>[!TIP]
>
>Als de output erop wijst dat `Module does not exist`, overzicht [&#x200B; Stap 1 &#x200B;](#step-1-get-a-sample-module) zorgvuldig. Zorg ervoor dat de code in de juiste map staat. Spelling en hoofdletters/kleine letters zijn belangrijk. Als iets anders is, wordt de module niet geladen. Vergeet ook niet `magento setup:upgrade` uit te voeren.

## Stap 3: Een klasse maken om afsnijden uit te voeren

In deze stap wordt een eenvoudige klasse weergegeven voor het maken van een uitsnijdtaak. De klasse schrijft alleen een rij naar de tabel `cron_schedule` die bevestigt dat deze is ingesteld.

Een klasse maken:

1. Maak een map voor de klasse en wijzig deze in de map:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. Er is een bestand met de naam `Test.php` gemaakt in die map met de volgende inhoud:

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

Het bestand `crontab.xml` stelt een schema in voor het uitvoeren van uw aangepaste uitsnijdcode.

Maak `crontab.xml` als volgt in de map `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` :

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

De voorgaande `crontab.xml` voert de `Magento/SampleMinimal/Cron/Test.php` -klasse eenmaal per minuut uit, waardoor een rij wordt toegevoegd aan de `cron_schedule` -tabel.

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

Hierbij is `system/config/path` een systeemconfiguratiepad dat is gedefinieerd in `etc/adminhtml/system.xml` van een module.

## Stap 5: Compileer en cache schoon

Compileer de code met deze opdracht:

```bash
bin/magento setup:di:compile
```

En maak de cache schoon met deze opdracht:

```bash
bin/magento cache:clean
```

## Stap 6: De uitsnijdtaak verifiëren

In deze stap ziet u hoe u de aangepaste uitsnijdtaak kunt verifiëren met een SQL-query in de databasetabel `cron_schedule` .

Uitsnijden verifiëren:

1. Uitvoeren van Commerce-taken voor uitsnijden:

   ```bash
   bin/magento cron:run
   ```

1. Voer de opdracht `magento cron:run` twee of drie keer in.

   De eerste keer dat u de opdracht invoert, worden de taken in de wachtrij geplaatst en daarna worden de uitsnijdtaken uitgevoerd. U moet het bevel _minstens_ tweemaal ingaan.

1. Voer de SQL-query `SELECT * from cron_schedule WHERE job_code like '%custom%'` als volgt uit:

   1. Enter `mysql -u magento -p`
   1. Typ `mysql>` bij de aanwijzing `use magento;` .
   1. Enter `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      Het resultaat moet vergelijkbaar zijn met het volgende:

      ```
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (Optioneel) Controleer of berichten naar het logboek van het Commerce-systeem worden geschreven:

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   U zou één of meerdere ingangen als het volgende moeten zien:

   ```
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Deze berichten zijn afkomstig van de methode `execute` in `Test.php` :

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Als de SQL-opdracht en het systeemlogboek geen items bevatten, voert u de opdracht `magento cron:run` nog een paar keer uit en wacht u. Het kan enige tijd duren voordat de database wordt bijgewerkt.

## Stap 7 (optioneel): Een aangepaste uitsnijdgroep instellen

In deze stap ziet u hoe u desgewenst een aangepaste uitsnijdgroep instelt. Stel een aangepaste uitsnijdgroep in als u wilt dat de aangepaste uitsnijdtaak volgens een andere planning wordt uitgevoerd dan andere uitsnijdtaken (doorgaans één keer per minuut) of als u meerdere aangepaste uitsnijdtaken met verschillende instellingen wilt uitvoeren.

Een aangepaste uitsnijdgroep instellen:

1. Open `crontab.xml` in een teksteditor.
1. `<group id="default">` wijzigen in `<group id="custom_crongroup">`
1. Sluit de teksteditor.
1. Maak `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` met de volgende inhoud:

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

Voor een beschrijving van wat de opties betekenen, zie [&#x200B; Aanpassen van de krantenverwijzing &#x200B;](custom-cron-reference.md).

## Stap 8: De aangepaste uitsnijdgroep verifiëren

Deze _facultatieve_ stap toont hoe te om uw groep van de douanecurn te verifiëren gebruikend Admin.

De aangepaste uitsnijdgroep verifiëren:

1. Commerce-taken voor uitsnijden uitvoeren voor uw aangepaste groep:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Voer de opdracht ten minste tweemaal uit.

1. De cache reinigen:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Meld u als beheerder aan bij de beheerder.
1. Klik **Slaat** op > **Montages** > **Configuratie** > **Geavanceerd** > **Systeem**.
1. In de juiste ruit, breid **Uitsnede** uit.

   Uw uitsnijdgroep wordt als volgt weergegeven:

   ![&#x200B; Uw groep van de douanecorrectie &#x200B;](../../assets/configuration/cron-group.png)

