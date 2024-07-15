---
title: GraphQL Application Server
description: Volg deze instructies om de GraphQL Application Server in te schakelen bij uw Adobe Commerce-implementatie.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: c2f48db87f40498a84b2bf41569bb46202565701
workflow-type: tm+mt
source-wordcount: '2088'
ht-degree: 0%

---


# GraphQL Application Server

Met de Commerce GraphQL Application Server kan Adobe Commerce de status onderhouden van Commerce GraphQL API-aanvragen. De Server van de Toepassing van GraphQL, die op de uitbreiding van de Steekproef wordt voortgebouwd, werkt als proces met arbeidersdraden die verzoekverwerking behandelen. GraphQL Application Server bewaart de status van een bootstrapped toepassing bij GraphQL API-aanvragen en verbetert de verwerking van aanvragen en de algehele productprestaties. API-aanvragen worden aanzienlijk efficiënter.

GraphQL Application Server is alleen beschikbaar voor Adobe Commerce. Het is niet beschikbaar voor Magento Open Source. U moet [ een 1} kaartje van de Steun van Adobe Commerce voorleggen {om de Server van de Toepassing van GraphQL op Pro projecten toe te laten.](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide)

>[!NOTE]
>
>GraphQL Application Server is momenteel niet compatibel met [[!DNL Amazon Simple Storage Service (AWS S3)] ](https://aws.amazon.com/s3/) . Adobe Commerce op klanten van de wolkeninfrastructuur die momenteel [!DNL AWS S3] voor [ verre opslag ](../configuration/remote-storage/cloud-support.md) gebruiken kan de Server van de Toepassing van GraphQL tot de Adobe een hotfix later in 2024 vrijgeeft.

## Architectuur

GraphQL Application Server onderhoudt de status tussen Commerce GraphQL API-aanvragen en maakt bootstrapping overbodig. Door de status van de toepassing over alle processen te delen, worden GraphQL-verzoeken aanzienlijk efficiënter, waardoor de responstijden met maximaal 30% afnemen.

Het PHP-uitvoeringsmodel zonder delen biedt een uitdaging vanuit het perspectief van latentie, omdat voor elke aanvraag de overvulling van het framework vereist is. Dit bootstrapping proces omvat tijdrovende taken zoals lezingsconfiguratie, vestiging het laarzentrekkerproces, en het creëren van de voorwerpen van de de dienstklasse.

Het overbrengen van aanvraagbehandelingslogica aan een toepassing-vlakke gebeurtenislijn lijkt de uitdaging van het stroomlijnen van verzoekverwerking op ondernemingsniveau te richten. Deze benadering elimineert de behoefte aan bootstrapping tijdens de levenscyclus van de verzoekuitvoering.

## Voordelen

Met GraphQL Application Server kan Adobe Commerce de status ondersteunen tussen opeenvolgende Commerce GraphQL API-aanvragen. Door de status van toepassingen te delen tussen aanvragen wordt de efficiëntie van API-aanvragen verbeterd doordat de verwerkingsoverhead tot een minimum wordt beperkt en de aanvraagverwerking wordt geoptimaliseerd. Als gevolg hiervan kan de responstijd voor GraphQL-verzoeken tot 30% worden verkort.

## Systeemvereisten

Voor het uitvoeren van GraphQL Application Server is het volgende vereist:

* PHP 8.2 of hoger
* PHP-extensie v5+ geïnstalleerd
* Adequate RAM en CPU op basis van de verwachte belasting

## Inschakelen en implementeren op cloudinfrastructuur

Met de module `ApplicationServer` (`Magento/ApplicationServer/` ) schakelt u GraphQL Application Server in.

### Pro-projecten inschakelen

>[!NOTE]
>
>De toepassingsserver is een aanmeldingsfunctie voor Cloud Pro-instanties. Om het toe te laten, leg een steunverzoek voor.

Nadat de eigenschap van de Server van de Toepassing op uw Proproject wordt toegelaten, voltooi de volgende stappen alvorens de Server van de Toepassing van GraphQL op te stellen:

1. Stel Adobe Commerce op wolkeninfrastructuur op gebruikend het wolkenmalplaatje van [ 2.4.7-appserver tak ](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Zorg ervoor dat al uw aanpassingen en uitbreidingen van Commerce [ ](https://developer.adobe.com/commerce/php/development/components/app-server/) met de Server van de Toepassing van GraphQL compatibel zijn.
1. Clone your Commerce Cloud project.
1. Pas indien nodig de instellingen in het bestand &#39;application-server/nginx.conf.sample&#39; aan.
1. Maak een volledige commentaarregel van de actieve sectie &#39;Web&#39; in het `project_root/.magento.app.yaml` -bestand.
1. Verwijder de commentaarmarkering uit de volgende &#39;web&#39;-sectieconfiguratie in het `project_root/.magento.app.yaml` -bestand dat de opdracht GraphQL Application Server `start` bevat.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Zorg ervoor dat `/application-server/start.sh` uitvoerbaar is door de volgende opdracht uit te voeren:

   ```bash
   chmod +x application-server/start.sh
   ```

1. Voeg met deze opdracht bijgewerkte bestanden toe aan de git-index:

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. Leg uw wijzigingen vast met deze opdracht:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Pro-projecten implementeren

Nadat u de stappen voor activering hebt uitgevoerd, voert u wijzigingen door in uw it-opslagplaats om GraphQL Application Server te implementeren:

```bash
git push
```

### Starter-projecten inschakelen

Voltooi de volgende stappen alvorens de Server van de Toepassing van GraphQL op de projecten van de Aanzet op te stellen:

1. Stel Adobe Commerce op wolkeninfrastructuur op gebruikend het wolkenmalplaatje van [ 2.4.7-appserver tak ](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Zorg ervoor dat al uw Commerce-aanpassingen en -extensies compatibel zijn met GraphQL Application Server.
1. Controleer of de omgevingsvariabele `CRYPT_KEY` voor uw instantie is ingesteld. U kunt de status van deze variabele controleren op het Cloud Project Portal (onboarding UI).
1. Clone your Commerce Cloud project.
1. Wijzig de naam `application-server/.magento/.magento.app.yaml.sample` in `application-server/.magento/.magento.app.yaml` en pas indien nodig de instellingen in .magento.app.yaml aan.
1. Verwijder de commentaarmarkering voor de configuratie van de volgende route in het `project_root/.magento/routes.yaml` -bestand om `/graphql` -verkeer om te leiden naar de GraphQL Application Server.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Bijgewerkte bestanden toevoegen aan de it-index:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Uw wijzigingen vastleggen:

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>Zorg ervoor dat alle aangepaste instellingen in het basisbestand van `.magento.app.yaml` op de juiste wijze naar het `application-server/.magento/.magento.app.yaml` -bestand worden gemigreerd. Nadat het `application-server/.magento/.magento.app.yaml` dossier aan uw project wordt toegevoegd, zou u het naast het wortel `.magento.app.yaml` dossier moeten handhaven. Bijvoorbeeld, als u rabbitmq ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) moet vormen of [ Webeigenschappen ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) beheert u de zelfde configuratie aan `application-server/.magento/.magento.app.yaml` eveneens zou moeten toevoegen.[

### Starter-projecten implementeren

Na de voltooiing van de enablement [ stappen ](#before-you-begin-a-cloud-starter-deployment), duw veranderingen in uw git bewaarplaats om de Server van de Toepassing van GraphQL op te stellen:

```bash
git push
```

### Inschakelen voor cloudprojecten verifiëren

1. Voer een GraphQL-query of -mutatie uit op uw instantie om te bevestigen dat het `graphql` -eindpunt toegankelijk is. Bijvoorbeeld:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   De verwachte reactie zou op dit voorbeeld moeten lijken:

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Gebruik SSH om toegang te krijgen tot uw Cloud-instantie. De `project_root/var/log/application-server.log` moet een nieuwe logrecord bevatten voor elke GraphQL-aanvraag.

1. U kunt ook controleren of GraphQL Application Server wordt uitgevoerd door de volgende opdracht uit te voeren:

   ```bash
   ps aux|grep php
   ```

   Er moet een `bin/magento server:run` -proces met meerdere threads worden weergegeven.

Als deze verificatiestappen zijn geslaagd, wordt GraphQL Application Server uitgevoerd en worden `/graphql` -aanvragen verzonden.

## Projecten ter plaatse inschakelen

Met de module `ApplicationServer` (`Magento/ApplicationServer/` ) schakelt u GraphQL Application Server voor GraphQL API&#39;s in.

Voor het lokaal uitvoeren van GraphQL Application Server moeten de extensie SWOLE en een kleine wijziging in het Nginx-configuratiebestand van uw implementatie worden geïnstalleerd.

### Vereisten

Voer de volgende stappen uit voordat u de module `ApplicationServer` inschakelt:

* Nginx configureren
* De SWF v5+-extensie installeren en configureren

#### Nginx configureren

Uw specifieke Commerce-implementatie bepaalt hoe u Nginx kunt configureren. In het algemeen wordt het Nginx-configuratiebestand standaard met de naam `nginx.conf` geplaatst en in een van de volgende mappen geplaatst: `/usr/local/nginx/conf`, `/etc/nginx` of `/usr/local/etc/nginx` . Zie {de Gids van 0} Beginer ](https://nginx.org/en/docs/beginners_guide.html) voor meer informatie bij het vormen van Nginx.[

Voorbeeld-Nginxconfiguratie:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Koel installeren en configureren

Als u de GraphQL Application Server lokaal wilt uitvoeren, installeert u de extensie SWOLE (v5.0 of hoger). Deze extensie kan op meerdere manieren worden geïnstalleerd.

In de volgende procedure wordt beschreven hoe u de SWOLE-extensie voor PHP 8.2 kunt installeren op OSX-systemen. Het is een van de verschillende manieren om de extensie Swoole te installeren.

```bash
pecl install swoole
```

Tijdens de installatie geeft Adobe Commerce aanwijzingen weer om ondersteuning voor `openssl` , `mysqlnd` , `sockets` , `http2` en `postgres` in te schakelen. Voer `yes` in voor alle opties behalve `postgres` .

### Wisselinstallatie controleren

Controleer of de extensie is ingeschakeld:

```bash
php -m | grep swoole
```

### Algemene fouten bij de installatie van Wolk

Eventuele fouten die optreden tijdens de installatie van een wisselaar treden gewoonlijk op tijdens de installatiefase van `pecl` . Typische fouten zijn ontbrekende `openssl.h` - en `pcre2.h` -bestanden. U lost deze fouten op door ervoor te zorgen dat deze twee pakketten op uw lokale systeem zijn geïnstalleerd.

* Controleer de locatie van `openssl` door uit te voeren:

```bash
openssl version -d
```

Deze opdracht geeft het pad weer waarop `openssl` is geïnstalleerd.

* Controleer de locatie van `pcre2` door uit te voeren:

```bash
pcre2-config --prefix 
```

Gebruik Homebrew om de ontbrekende pakketten te installeren als de opdrachtuitvoer aangeeft dat bestanden ontbreken:

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### Problemen met openssl oplossen

Voer de volgende handelingen uit om problemen met betrekking tot `openssl` op te lossen:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Bevestig dat u het pad vanuit uw lokale `dev` omgeving gebruikt.

#### Bevestigen van oplossing voor openssl-gerelateerde kwesties

U kunt de volgende opdracht opnieuw uitvoeren om te controleren of aan opensels gerelateerde problemen zijn opgelost:

```bash
pecl install swoole
```

#### Problemen met pcre2.h oplossen

Als u problemen met `pcre2.h` wilt oplossen, symboliseert u het `pcre2.h` -pad naar de geïnstalleerde PHP-extensiemap. Uw specifieke geïnstalleerde versie van PHP en `pcr2.h` bepaalt de specifieke versie van het bevel dat u zou moeten gebruiken.

### GraphQL Application Server uitvoeren

GraphQL Application Server starten:

```bash
bin/magento server:run
```

Deze opdracht start een HTTP-poort op 9501. Zodra GraphQL Application Server wordt gestart, wordt poort 9501 een HTTP-proxyserver voor alle GraphQL-query&#39;s.

Om te bevestigen dat de Server van de Toepassing van GraphQL in uw plaatsing loopt:

```bash
ps aux | grep php
```

U kunt onder andere controleren of GraphQL Application Server wordt uitgevoerd:

* Controleer het `/var/log/application-server.log` -bestand op items die betrekking hebben op verwerkte GraphQL-aanvragen.
* Probeer verbinding te maken met de HTTP-poort waarop GraphQL Application Server wordt uitgevoerd. Bijvoorbeeld: `curl -g 'http://localhost:9501/graph` .

### Bevestig dat GraphQL-verzoeken worden verwerkt

GraphQL Application Server voegt de header `X-Backend` response met de waarde `graphql_server` toe aan elke aanvraag die wordt verwerkt. Om te controleren of een verzoek door de Server van de Toepassing van GraphQL is behandeld, controleer deze antwoordkopbal.

### Compatibiliteit met extensies en aanpassingen bevestigen

De ontwikkelaars en de handelaars van de uitbreiding zouden eerst moeten verifiëren dat hun uitbreiding en aanpassingscode aan de technische richtlijnen naleven die in [ worden beschreven Technische richtlijnen ](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Overweeg deze richtlijnen tijdens codeevaluatie:

* Serviceklassen (dat wil zeggen, klassen die gedrag maar geen gegevens, zoals `EventManager` leveren) mogen geen veranderbare status hebben.
* Vermijd tijdelijke koppeling.

## GraphQL Application Server uitschakelen

De procedures voor het uitschakelen van de GraphQL Application Server variëren afhankelijk van het feit of de server in een on-premisse of Cloud-implementatie wordt uitgevoerd.

### GraphQL Application Server (cloud) uitschakelen

1. Verwijder alle nieuwe bestanden en eventuele andere codewijzigingen die in `AppServer Enabled` zijn vastgelegd tijdens de voorbereidingen voor de implementatie.

1. Leg uw wijzigingen vast met deze opdracht:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Deze wijzigingen implementeren met deze opdracht:

   ```bash
   git push
   ```

### GraphQL Application Server uitschakelen (op locatie)

1. Maak een commentaarregel van de `/graphql` -sectie van het `nginx.conf` -bestand die u hebt toegevoegd bij het inschakelen van GraphQL Application Server.
1. Start nginx opnieuw.

Deze methode om GraphQL Application Server uit te schakelen kan nuttig zijn om de prestaties snel te testen of te vergelijken.

### Bevestig dat GraphQL Application Server is uitgeschakeld

Om te bevestigen dat GraphQL-verzoeken door `php-fpm` in plaats van GraphQL Application Server worden verwerkt, voert u de volgende opdracht in: `ps aux | grep php` .

Nadat GraphQL Application Server is uitgeschakeld:

* `bin/magento server:run` is inactief.
* `var/log/application-server.log` bevat geen items na GraphQL-aanvragen.

## Integratie- en functionele tests voor GraphQL Application Server

Extensieontwikkelaars kunnen twee integratietests uitvoeren om de compatibiliteit van extensies met GraphQL Application Server te controleren: `GraphQlStateTest` en `ResetAfterRequestTest` .

### GraphQlStateTest

`GraphQlStateTest` detecteert de status in gezamenlijke objecten die niet opnieuw mogen worden gebruikt voor meerdere aanvragen.

Deze test is ontworpen om statusveranderingen in de dienstvoorwerpen te ontdekken die door `ObjectManager` worden veroorzaakt. De test voert identieke vragen van GraphQL tweemaal uit en vergelijkt de staat van het de dienstvoorwerp vóór en na de tweede vraag.

#### GraphQlStateTest-fouten en mogelijke herstelmogelijkheden

* **kan niet toevoegen, overslaan, of filter een lijst**. Als u een mislukking tegenkomt die het niet veilig suggereert om, een lijst toe te voegen over te slaan of te filtreren, overweeg of de klasse op een achteruit-compatibele manier kan worden gerefactored om de fabrieken van de de dienstklassen te gebruiken die veranderlijke staat hebben.

* **Klasse toont een veranderbare staat**. Als de klasse zelf een veranderbare staat vertoont, probeer om uw code te herschrijven om deze staat te omzeilen. Als de veranderbare toestand om prestatieredenen is vereist, implementeert u `ResetAfterRequestInterface` en gebruikt u `_resetState()` om de oorspronkelijke geconstrueerde toestand van het object te herstellen.

* **Typed bezit $x moet niet vóór initialisatiebericht** worden betreden. De mislukkingen met dit type van bericht wijzen erop dat het gespecificeerde bezit niet door de aannemer is geïnitialiseerd. Dit is een vorm van tijdelijke koppeling die optreedt omdat het object niet kan worden gebruikt nadat het is geconstrueerd. Deze koppeling treedt ook op als de eigenschap privé is, omdat de verzamelaar die de gegevens van de eigenschappen ophaalt, de PHP-reflectie-functie gebruikt. Probeer in dit geval de klasse te vernieuwen om tijdelijke koppeling te voorkomen en muteerbare toestand te voorkomen. Als dat refactoring niet de mislukking oplost, kunt u het bezitstype in een nullable type veranderen zodat kan het aan ongeldig worden geïnitialiseerd.  Wanneer de eigenschap een array is, probeer dan de eigenschap als een lege array te initialiseren.

Voer `GraphQlStateTest` uit door `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php` uit te voeren.

### ResetAfterRequestTest

`ResetAfterRequestTest` zoekt naar alle klassen die `ResetAfterRequestInterface` implementeren en controleert of de methode `_resetState()` de status van een object retourneert in dezelfde toestand als die werd aangehouden nadat het object werd samengesteld door `ObjectManager` .  Met deze test maakt u een serviceobject met `ObjectManager` en klonen u dat object, roept u `_resetState()` aan en vergelijkt u vervolgens beide objecten. In de test worden geen methoden aangeroepen tussen het instantiëren van objecten en `_resetState()` , zodat het opnieuw instellen van muteerbare statussen niet wordt bevestigd. Er zijn echter problemen met het feit dat een bug of typefout in `_resetState()` de status kan instellen op iets anders dan oorspronkelijk het geval was.

#### ResetAfterRequestTest-fouten en mogelijke herstelbewerkingen

* **Klasse heeft inconsistente bezitswaarden**. Als deze test mislukt, controleert u of een klasse is gewijzigd met als resultaat dat het object na de constructie andere eigenschapswaarden heeft dan nadat de methode `_resetState()` is aangeroepen. Als de klasse waaraan u werkt niet de methode `_resetState()` zelf bevat, controleert u de klassehiërarchie op een superklasse die deze implementeert.

* **Typed bezit $x moet niet vóór initialisatiebericht** worden betreden. Dit probleem doet zich ook voor bij `GraphQlStateTest` .

  Voer `ResetAfterRequestTest` uit door: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php` uit.

### Functionele tests

De ontwikkelaars van de uitbreiding zouden functionele tests WebAPI voor GraphQL, evenals om het even welke douane geautomatiseerde of handfunctionele tests voor GraphQL moeten uitvoeren, terwijl het opstellen van de Server van de Toepassing van GraphQL. Deze functionele tests helpen ontwikkelaars potentiële fouten of compatibiliteitsproblemen te identificeren.

#### Statusmonitormodus

Tijdens het uitvoeren van functionele tests (of het manueel testen), kan de toepassingsserver met `--state-monitor mode` worden in werking gesteld helpen klassen vinden waar de staat onbedoeld opnieuw wordt gebruikt. Start de toepassingsserver normaal, behalve voeg de parameter `--state-monitor` toe.

```
bin/magento server:run --state-monitor
```

Nadat elke aanvraag is verwerkt, wordt een nieuw bestand toegevoegd aan de map `tmp` , bijvoorbeeld: `var/tmp/StateMonitor-thread-output-50-6nmxiK` . Als u klaar bent met testen, kunnen deze bestanden worden samengevoegd met de opdracht `bin/magento server:state-monitor:aggregate-output` , waarmee twee samengevoegde bestanden worden gemaakt: een in `XML` en een in `JSON` .

Voorbeelden:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Deze bestanden kunnen worden geïnspecteerd met elk gereedschap dat u gebruikt om XML of JSON weer te geven. Hierin worden de gewijzigde eigenschappen van serviceobjecten weergegeven, zoals GraphQlStateTest. De modus `--state-monitor` gebruikt dezelfde lijst met overslaan en filterlijst als GraphQlStateTest.

>[!NOTE]
>
>Gebruik de `--state-monitor` -modus niet in productie. Het is alleen ontworpen voor ontwikkeling en testen. Er worden veel uitvoerbestanden gemaakt en deze worden langzamer uitgevoerd dan normaal.

>[!NOTE]
>
>`--state-monitor` is niet compatibel met PHP-versies `8.3.0` - `8.3.4` vanwege een bug in de PHP-opschoonfunctie. Als u PHP 8.3 gebruikt, moet u een upgrade uitvoeren naar `8.3.5` of hoger om deze functie te kunnen gebruiken.
