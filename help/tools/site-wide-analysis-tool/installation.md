---
title: Hulplijn installeren
description: Gebruik deze gids om  [!DNL Site-Wide Analysis Tool]  voor uw website te installeren
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# Hulplijn installeren

>[!IMPORTANT]
>
>Met ingang van 23 april 2024 wordt de [!DNL Site-Wide Analysis Tool] voor alle Adobe Commerce-klanten op locatie buiten bedrijf gesteld.

De [!DNL Site-Wide Analysis Tool] biedt 24/7 realtime prestatiebewaking, rapporten en aanbevelingen om de beveiliging en operabiliteit van Adobe Commerce bij installatie van wolkeninfrastructuur te garanderen. Het biedt ook gedetailleerde informatie over beschikbare en geïnstalleerde patches, extensies van derden en uw Adobe Commerce-installatie.

>[!INFO]
>
>Leer [ hoe te om ](../site-wide-analysis-tool/access.md) toe te laten [!DNL Site-Wide Analysis Tool] en rapporten te produceren.

Als u een installatie van Adobe Commerce in de bedrijfsruimten hebt, installeert u een agent op uw infrastructuur om het hulpmiddel te gebruiken. U hoeft de agent niet op Adobe Commerce te installeren op cloudinfrastructuurprojecten.

## Agent

Met de [!DNL Site-Wide Analysis Tool] -agent kunt u de [!DNL Site-Wide Analysis Tool] gebruiken voor installaties op locatie van Adobe Commerce.

De [!DNL Site-Wide Analysis Tool] Agent verzamelt toepassings- en bedrijfsgegevens, analyseert deze en biedt aanvullende inzichten over de gezondheid van uw installatie zodat u de gebruikerservaring kunt verbeteren. Het controleert uw toepassing en helpt u prestaties, veiligheid, beschikbaarheid, en toepassingskwesties identificeren.

Het installeren van de agent vereist de volgende stappen:

1. Controleer de systeemvereisten.

1. Configureer API-sleutels in de extensie [!UICONTROL Commerce Services Connector] .

1. Installeer de agent.

1. Voer de agent uit.

>[!INFO]
>
>De agent ondersteunt Adobe Commerce-installaties met meerdere knooppunten. Installeer en vorm de agent op elke knoop.

## Systeemvereisten

Uw infrastructuur ter plaatse moet aan de volgende vereisten voldoen alvorens de agent te installeren:

- Besturingssystemen

   - [!DNL Linux x86-64] distributies, zoals [!DNL Red Hat® Enterprise Linux (RHEL)] , [!DNL CentOS] , [!DNL Ubuntu] , [!DNL Debian] en dergelijke

  >[!IMPORTANT]
  >
  >Adobe Commerce wordt niet ondersteund op [!DNL Microsoft Windows] of [!DNL macOS] .

- Adobe Commerce 2.4.5-p1 of hoger (vanwege de afhankelijkheid van de Serviceconnector)

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Hulpprogramma&#39;s voor basis/shell

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

De agent vereist de [[!DNL Commerce Services Connector] ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) uitbreiding die op uw systeem en [ wordt geïnstalleerd wordt gevormd ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) met API sleutels. Voer de volgende opdracht uit om te controleren of de extensie is geïnstalleerd:

```bash
bin/magento module:status Magento_ServicesId
```

Als u de uitbreiding hebt geïnstalleerd en het gevormd gebruikend een bestaande API sleutel voor de verschillende dienst, MOET u **de API sleutel** regenereren en het in Adobe Commerce Admin voor de agent bijwerken.

1. Zet uw website in [ onderhoudswijze ](../../installation/tutorials/maintenance-mode.md).

1. Logboek in [ account.magento.com ](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > Als u problemen hebt die tot uw rekening toegang hebben, zie [ Onbekwaam aan login aan de steun van Adobe Commerce of de wolkenrekening ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) voor het oplossen van problemenhulp.

1. Klik op **[!UICONTROL API Portal]**.

1. Klik op **[!UICONTROL Delete]** naast de bestaande API-sleutel.

1. [ vorm ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) een nieuwe API sleutel.

>[!IMPORTANT]
>
> Als u nieuwe sleutels in het Portaal van API produceert, werk onmiddellijk de sleutels API in [!DNL Admin configuration] bij. Als u nieuwe sleutels produceert en niet de sleutels in [!DNL Admin] bijwerkt, zullen uw uitbreidingen SaaS niet meer werken en u zult waardevolle gegevens verliezen.

Als de extensie niet is geïnstalleerd, gebruikt u de volgende instructies om deze te installeren:

1. Voeg de extensie toe aan uw `composer.json` -bestand en installeer deze.

   ```bash
   composer require magento/services-id
   ```

1. De extensie inschakelen.

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. Werk het databaseschema bij.

   ```bash
   bin/magento setup:upgrade
   ```

1. Wis de cache.

   ```bash
   bin/magento cache:clean
   ```

1. [ vorm API Sleutels ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) om de uitbreiding met uw systeem te verbinden.

## De agent installeren

Wij hebben a [ shell manuscript ](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) gecreeerd om installatie te vereenvoudigen. Wij adviseren gebruikend het shell manuscript, maar u kunt de [ handinstallatie ](#manual) methode indien nodig volgen.

>[!INFO]
>
>Nadat de agent wordt geïnstalleerd, zal het automatisch bijwerken wanneer een nieuwe versie beschikbaar is.

### Scripts

1. Download en voer het shellscript uit.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >We raden u aan de agent buiten de Adobe Commerce-hoofdprojectmap te installeren.

1. Controleer de installatie.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Na het downloaden en het installeren van de agent, [ vormt het om ](#run-the-agent) in werking te stellen gebruikend één van de volgende methodes:

   - [ Dienst ](#service) (aangewezen als u worteltoegang hebt)

   - [Cron](#cron)

### Handmatig {#manual}

Als u niet ons [ shell manuscript ](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) wilt gebruiken om de agent te installeren, dan moet u het manueel installeren door deze stappen te volgen:

1. Maak een directory waarin u de agent wilt downloaden.

   >[!TIP]
   >
   >We raden u aan de agent buiten de Adobe Commerce-hoofdprojectmap te installeren.

1. Download het binaire bestand en pak het uit.

   >[!INFO]
   >
   >Als u [!DNL Site-Wide Analysis Tool] wilt gebruiken, moet u eerst de Gebruiksvoorwaarden lezen en accepteren die worden weergegeven wanneer u het dashboard opent via Adobe Commerce Admin.

   Voor de **AMD64** architectuur:

   1. Download het archief van de startprogramma.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Pak het archief van de draagprogramma&#39;s uit.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   Voor de **ARM64** architectuur:

   1. Download het archief van de startprogramma.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Pak het archief van de draagprogramma&#39;s uit.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *(Facultatief)* verifieer de handtekening voor het checksum dossier.

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(Facultatief)* verifieer de controlesom.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Maak het `config.yaml` -bestand met de volgende inhoud.

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. Controleer de installatie.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Na het downloaden en het installeren van de agent, moet u het [ vormen om ](#run-the-agent) gebruikend één van de volgende methodes in werking te stellen:

   - [ Dienst ](#service) (aangewezen als u worteltoegang hebt)

   - [Cron](#cron)

## De agent uitvoeren {#run-the-agent}

Wij adviseren vormend de agent om als dienst te lopen. Als u beperkte toegang tot uw infrastructuur hebt en geen worteltoestemmingen hebt, dan moet u [ bebouwen ](#cron) in plaats daarvan gebruiken.

### Service {#service}

1. Maak een systeemeenheidsbestand `(/etc/systemd/system/scheduler.service)` met de volgende configuratie (vervang `<filesystemowner>` door de UNIX®-gebruiker die eigenaar is van de map waarin de agent en de Adobe Commerce-software zijn geïnstalleerd). Als u de agent als hoofdgebruiker hebt gedownload, wijzigt u de map en de eigenaar van geneste bestanden.

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. Start de service.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Bevestig dat de dienst in gebruik is.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Als u geen worteltoestemmingen hebt of geen toestemmingen hebt om de dienst als wortel te vormen, kunt u in plaats daarvan kroon gebruiken.

Uw uitsnijdschema bijwerken:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Verwijderen

Voer de volgende opdrachten uit om de service van uw systeem te verwijderen en alle gegenereerde bestanden te verwijderen:

1. Stop de planner.

   ```bash
   systemctl stop scheduler
   ```

1. Schakel de planner uit.

   ```bash
   systemctl disable scheduler
   ```

1. Verwijder het `systemd` eenheidsdossier van de plannerdienst.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Laad de `systemd` -beheerconfiguratie opnieuw.

   ```bash
   systemctl daemon-reload
   ```

1. Stel om het even welke `systemd` eenheden van een ontbroken staat terug.

   ```bash
   systemctl reset-failed
   ```

1. Verwijder de folder van de plannerdienst.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Verwijder het binaire dossier van de planner.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Als u de agent aan looppas met kroon vormde, gebruik in plaats daarvan de volgende instructies:

1. Verwijder de agent uit de contextlijst.

   ```bash
   crontab -e
   ```

1. Stop de actieve taak.

   ```bash
   ps aux | grep scheduler
   ```

1. Verwijder de folder waar u de agent installeerde.

   ```bash
   rm -rf swat-agent
   ```

## Problemen oplossen

### Toegangstoetsen niet correct geparseerd

U ziet mogelijk de volgende fout als uw toegangstoetsen niet correct worden geparseerd:

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Voer de volgende stappen uit om deze fout op te lossen:

1. Doe a [ gescripte installeert ](#scripted), sparen de output, en herzie de output voor fouten.
1. Controleer het gegenereerde `config.yaml` bestand en controleer of het pad naar uw Commerce-instantie en PHP juist is.
1. Zorg ervoor dat de gebruiker die de planner in werking stelt in de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md) Unix groep is of de zelfde gebruiker zoals de eigenaar van het dossiersysteem is.
1. Zorg ervoor dat de ](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) sleutels van de Schakelaar van de Diensten van 0} Commerce correct geïnstalleerd zijn en probeer hen bij te werken om de uitbreiding met uw systeem te verbinden.[
1. [ desinstalleer ](#uninstall) de agent na het bijwerken van de sleutels en herinstalleer gebruikend [ installeer manuscript ](#scripted).
1. Stel de planner in werking en zie of ontvangt u nog de zelfde fout.
1. Als u nog steeds dezelfde fout ontvangt, verhoogt u het logniveau in de `config.yaml` om fouten op te sporen en een ondersteuningsticket te openen.

### *SIGFAULT* Fout

Als u a *SIGFAULT* fout wanneer het runnen van binair getal ziet, stelt u waarschijnlijk niet dit als dossiereigenaar van Adobe Commerce en de dossiers van de Agent in werking.
Om op te lossen, gelieve te controleren of alle dossiers binnen de agentenfolder die de zelfde gebruiker hebben zoals de fileowner die de dossiers van Adobe Commerce hebben, en binair zou ook onder die gebruiker moeten worden in werking gesteld.
U kunt de opdracht `chown` gebruiken om de eigenaar van de bestanden te wijzigen en over te schakelen op de juiste gebruiker.
Zorg ervoor dat het proces onder de juiste gebruiker wordt uitgevoerd met het mechanisme voor demonisatie (Cron of System.d).

>[!INFO]
>
>Zie [ hoe te om tot  [!DNL Site-Wide Analysis Tool]  toegang te hebben en rapporten ](../site-wide-analysis-tool/access.md) te produceren.
