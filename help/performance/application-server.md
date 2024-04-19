---
title: GraphQL Application Server
description: Volg deze instructies om de GraphQL Application Server in te schakelen bij uw Adobe Commerce-implementatie.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: b89ed5ddb4c6361de22d4a4439ffcfcc3ec8d474
workflow-type: tm+mt
source-wordcount: '2267'
ht-degree: 0%

---


# GraphQL Application Server

Met de Commerce GraphQL Application Server kan Adobe Commerce de status handhaven bij de Commerce GraphQL API-aanvragen. De Server van de Toepassing van GraphQL, die op de uitbreiding van de Steekproef wordt voortgebouwd, werkt als proces met arbeidersdraden die verzoekverwerking behandelen. GraphQL Application Server bewaart de status van een bootstrapped toepassing bij GraphQL API-aanvragen en verbetert de verwerking van aanvragen en de algehele productprestaties. API-aanvragen worden aanzienlijk efficiënter.

GraphQL Application Server is alleen beschikbaar voor Adobe Commerce. Het is niet beschikbaar voor Magento Open Source. U moet [een Adobe Commerce-ondersteuning verzenden](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) ticket om GraphQL Application Server in te schakelen voor Pro-projecten.

>[!NOTE]
>
>GraphQL Application Server is momenteel niet compatibel met [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). Adobe Commerce op cloudinfrastructuur die klanten momenteel gebruiken [!DNL AWS S3] for [externe opslag](../configuration/remote-storage/cloud-support.md) GraphQL Application Server kan pas worden gebruikt nadat de Adobe later in 2024 een hotfix heeft uitgebracht.

## Architectuur

GraphQL Application Server onderhoudt de status tussen GraphQL API-aanvragen voor handel en elimineert de noodzaak van bootstrapping. Door de status van de toepassing over alle processen te delen, worden GraphQL-verzoeken aanzienlijk efficiënter, waardoor de responstijden met maximaal 30% afnemen.

Het PHP-uitvoeringsmodel zonder delen biedt een uitdaging vanuit het perspectief van latentie, omdat voor elke aanvraag de overvulling van het framework vereist is. Dit bootstrapping proces omvat tijdrovende taken zoals lezingsconfiguratie, vestiging het laarzentrekkerproces, en het creëren van de voorwerpen van de de dienstklasse.

Het overbrengen van aanvraagbehandelingslogica aan een toepassing-vlakke gebeurtenislijn lijkt de uitdaging van het stroomlijnen van verzoekverwerking op ondernemingsniveau te richten. Deze benadering elimineert de behoefte aan bootstrapping tijdens de levenscyclus van de verzoekuitvoering.

## Voordelen

Met GraphQL Application Server kan Adobe Commerce de status ondersteunen tussen opeenvolgende GraphQL API-aanvragen voor handel. Door de status van toepassingen te delen tussen aanvragen wordt de efficiëntie van API-aanvragen verbeterd doordat de verwerkingsoverhead tot een minimum wordt beperkt en de aanvraagverwerking wordt geoptimaliseerd. Als gevolg hiervan kan de responstijd voor GraphQL-verzoeken tot 30% worden verkort.

## Systeemvereisten

Voor het uitvoeren van GraphQL Application Server is het volgende vereist:

* PHP 8.2 of hoger
* PHP-extensie v5+ geïnstalleerd
* Adequate RAM en CPU op basis van de verwachte belasting

## Inschakelen en implementeren op cloudinfrastructuur

De `ApplicationServer` module (`Magento/ApplicationServer/`) schakelt GraphQL Application Server in.

### Pro-projecten inschakelen

Voer de volgende stappen uit voordat u GraphQL Application Server inzet voor Pro-projecten:

1. Adobe Commerce implementeren op cloudinfrastructuur met behulp van de cloudsjabloon van de [2.4.7 Aangepaste vertakking](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Zorg ervoor dat al uw aanpassingen en uitbreidingen van de Handel zijn [compatibel](https://developer.adobe.com/commerce/php/development/components/app-server/) met GraphQL Application Server.
1. Clone your Commerce Cloud project.
1. Pas indien nodig de instellingen in het bestand &#39;application-server/nginx.conf.sample&#39; aan.
1. Plaats de actieve sectie &#39;Web&#39; in `project_root/.magento.app.yaml` volledig.
1. Verwijder de commentaarmarkering uit de volgende &#39;web&#39;-sectieconfiguratie in het dialoogvenster `project_root/.magento.app.yaml` bestand dat de GraphQL Application Server bevat `start` gebruiken.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Voeg met deze opdracht bijgewerkte bestanden toe aan de git-index:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
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

1. Adobe Commerce implementeren op cloudinfrastructuur met behulp van de cloudsjabloon van de [2.4.7 Aangepaste vertakking](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Zorg ervoor dat al uw aanpassingen en uitbreidingen van de Handel met de Server van de Toepassing van GraphQL compatibel zijn.
1. Bevestig dat de `CRYPT_KEY` omgevingsvariabele wordt ingesteld voor uw instantie. U kunt de status van deze variabele controleren op het Cloud Project Portal (onboarding UI).
1. Clone your Commerce Cloud project.
1. Naam wijzigen `application-server/.magento/.magento.app.yaml.sample` tot `application-server/.magento/.magento.app.yaml` en pas indien nodig instellingen aan in .magento.app.yaml.
1. Uncomment de configuratie van de volgende route in `project_root/.magento/routes.yaml` bestand om te leiden `/graphql` verkeer naar GraphQL Application Server.

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
>Zorg ervoor dat alle aangepaste instellingen in de hoofdmap `.magento.app.yaml` bestand wordt naar behoren gemigreerd naar de `application-server/.magento/.magento.app.yaml` bestand. Na de `application-server/.magento/.magento.app.yaml` het dossier wordt toegevoegd aan uw project, zou u het naast de wortel moeten handhaven `.magento.app.yaml` bestand. Als u bijvoorbeeld [rabbitmq configureren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) of [webeigenschappen beheren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) u zou de zelfde configuratie aan moeten toevoegen `application-server/.magento/.magento.app.yaml` ook.

### Starter-projecten implementeren

Na voltooiing van enablement [stappen](#before-you-begin-a-cloud-starter-deployment), duw wijzigingen in uw git-opslagplaats om GraphQL Application Server te implementeren:

```bash
git push
```

### Inschakelen voor cloudprojecten verifiëren

1. Voer een GraphQL-query of -mutatie uit tegen uw instantie om te bevestigen dat de `graphql` het eindpunt is toegankelijk. Bijvoorbeeld:

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

1. Gebruik SSH om toegang te krijgen tot uw Cloud-instantie. De `project_root/var/log/application-server.log` moet voor elke GraphQL-aanvraag een nieuw logbestand bevatten.

1. U kunt ook controleren of GraphQL Application Server wordt uitgevoerd door de volgende opdracht uit te voeren:

   ```bash
   ps aux|grep php
   ```

   U dient een `bin/magento server:run` verwerken met meerdere threads.

Als deze verificatiestappen zijn geslaagd, wordt GraphQL Application Server uitgevoerd en wordt deze server gebruikt `/graphql` verzoeken.

## Projecten ter plaatse inschakelen

De `ApplicationServer` module (`Magento/ApplicationServer/`) maakt GraphQL Application Server voor GraphQL API&#39;s mogelijk.

Voor het lokaal uitvoeren van GraphQL Application Server moeten de extensie SWOLE en een kleine wijziging in het Nginx-configuratiebestand van uw implementatie worden geïnstalleerd.

### Vereisten

Voer de volgende stappen uit voordat u de `ApplicationServer` module:

* Nginx configureren
* De SWF v5+-extensie installeren en configureren

#### Nginx configureren

Uw specifieke plaatsing van de Handel bepaalt hoe te om Nginx te vormen. In het algemeen wordt het Nginx-configuratiebestand standaard benoemd `nginx.conf` en wordt in een van deze directory&#39;s geplaatst: `/usr/local/nginx/conf`, `/etc/nginx`, of `/usr/local/etc/nginx`. Zie [Beginnerengids](https://nginx.org/en/docs/beginners_guide.html) voor meer informatie over het configureren van Nginx.

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

Tijdens de installatie geeft Adobe Commerce aanwijzingen weer om ondersteuning voor `openssl`, `mysqlnd`, `sockets`, `http2`, en `postgres`. Enter `yes` voor alle opties behalve `postgres`.

### Wisselinstallatie controleren

Controleer of de extensie is ingeschakeld:

```bash
php -m | grep swoole
```

### Algemene fouten bij de installatie van Wolk

Eventuele fouten die optreden tijdens de installatie van de module Wisselen treden gewoonlijk op tijdens de `pecl` installatiefase. Tot de standaardfouten behoren ontbrekende `openssl.h` en `pcre2.h` bestanden. U lost deze fouten op door ervoor te zorgen dat deze twee pakketten op uw lokale systeem zijn geïnstalleerd.

* Controleer de locatie van `openssl` door uitvoering:

```bash
openssl version -d
```

Met deze opdracht wordt het pad getoond waar `openssl` is geïnstalleerd.

* Controleer de locatie van `pcre2` door uitvoering:

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

Om problemen op te lossen met betrekking tot `openssl`, run:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Bevestig dat u het pad vanaf uw lokale computer gebruikt `dev` milieu.

#### Bevestigen van oplossing voor openssl-gerelateerde kwesties

U kunt de volgende opdracht opnieuw uitvoeren om te controleren of aan opensels gerelateerde problemen zijn opgelost:

```bash
pecl install swoole
```

#### Problemen met pcre2.h oplossen

Om problemen op te lossen met betrekking tot `pcre2.h`, de `pcre2.h` pad naar de geïnstalleerde map voor PHP-extensies. Uw specifieke geïnstalleerde versie van PHP en `pcr2.h` bepaalt de specifieke versie van het bevel dat u zou moeten gebruiken.

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

* Controleer de `/var/log/application-server.log` bestand voor berichten die betrekking hebben op verwerkte GraphQL-aanvragen.
* Probeer verbinding te maken met de HTTP-poort waarop GraphQL Application Server wordt uitgevoerd. Bijvoorbeeld: `curl -g 'http://localhost:9501/graph`.

### Bevestig dat GraphQL-verzoeken worden verwerkt

GraphQL Application Server voegt de `X-Backend` responsheader met de waarde `graphql_server` aan elk verzoek dat het verwerkt. Om te controleren of een verzoek door de Server van de Toepassing van GraphQL is behandeld, controleer deze antwoordkopbal.

### Compatibiliteit met extensies en aanpassingen bevestigen

Extensieontwikkelaars en -handelaren moeten eerst controleren of hun code voor uitbreiding en aanpassing voldoet aan de technische richtlijnen die worden beschreven in [Technische richtsnoeren](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Overweeg deze richtlijnen tijdens codeevaluatie:

* De klassen van de dienst (namelijk klassen die gedrag maar geen gegevens verstrekken, zoals `EventManager`) mag niet muteerbaar zijn.
* Vermijd tijdelijke koppeling.

## GraphQL Application Server uitschakelen

De procedures voor het uitschakelen van de GraphQL Application Server variëren afhankelijk van het feit of de server in een on-premisse of Cloud-implementatie wordt uitgevoerd.

### GraphQL Application Server (cloud) uitschakelen

1. Verwijder alle nieuwe bestanden en eventuele andere codewijzigingen die zijn opgenomen in het dialoogvenster `AppServer Enabled` onderschrijven tijdens uw voorbereidingen voor de implementatie.

1. Leg uw wijzigingen vast met deze opdracht:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Deze wijzigingen implementeren met deze opdracht:

   ```bash
   git push
   ```

### GraphQL Application Server uitschakelen (op locatie)

1. Maak een opmerking in het dialoogvenster `/graphql` deel van `nginx.conf` bestand dat u hebt toegevoegd bij het inschakelen van GraphQL Application Server.
1. Start nginx opnieuw.

Deze methode om GraphQL Application Server uit te schakelen kan nuttig zijn om de prestaties snel te testen of te vergelijken.

### Bevestig dat GraphQL Application Server is uitgeschakeld

Bevestig dat GraphQL-aanvragen worden verwerkt door `php-fpm` in plaats van GraphQL Application Server, voert u deze opdracht in: `ps aux | grep php`.

Nadat GraphQL Application Server is uitgeschakeld:

* `bin/magento server:run` is inactief.
* `var/log/application-server.log` bevat geen items na GraphQL-aanvragen.

## Integratie- en functionele tests voor GraphQL Application Server

Extensieontwikkelaars kunnen twee integratietests uitvoeren om de compatibiliteit van extensies met GraphQL Application Server te controleren: `GraphQlStateTest` en `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` detecteert de status in gezamenlijke objecten die niet opnieuw mogen worden gebruikt voor meerdere aanvragen.

Deze test is ontworpen om statusveranderingen in de dienstvoorwerpen te ontdekken die door `ObjectManager`. De test voert identieke vragen van GraphQL tweemaal uit en vergelijkt de staat van het de dienstvoorwerp vóór en na de tweede vraag.

#### GraphQlStateTest-fouten en mogelijke herstelmogelijkheden

* **Kan een lijst niet toevoegen, overslaan of filteren**. Als u een mislukking tegenkomt die het niet veilig suggereert om, een lijst toe te voegen over te slaan of te filtreren, overweeg of de klasse op een achteruit-compatibele manier kan worden gerefactored om de fabrieken van de de dienstklassen te gebruiken die veranderlijke staat hebben.

* **Klasse vertoont een veranderbare status**. Als de klasse zelf een veranderbare staat vertoont, probeer om uw code te herschrijven om deze staat te omzeilen. Als de veranderbare staat om prestatiesredenen wordt vereist, dan voer uit `ResetAfterRequestInterface` en gebruik `_resetState()` om de oorspronkelijke geconstrueerde status van het object te herstellen.

* **Typed-eigenschap $x mag niet worden benaderd voordat een initialisatiebericht wordt weergegeven**. De mislukkingen met dit type van bericht wijzen erop dat het gespecificeerde bezit niet door de aannemer is geïnitialiseerd. Dit is een vorm van tijdelijke koppeling die optreedt omdat het object niet kan worden gebruikt nadat het is geconstrueerd. Deze koppeling treedt ook op als de eigenschap privé is, omdat de verzamelaar die de gegevens van de eigenschappen ophaalt, de PHP-reflectie-functie gebruikt. Probeer in dit geval de klasse te vernieuwen om tijdelijke koppeling te voorkomen en muteerbare toestand te voorkomen. Als dat refactoring niet de mislukking oplost, kunt u het bezitstype in een nullable type veranderen zodat kan het aan ongeldig worden geïnitialiseerd.  Wanneer de eigenschap een array is, probeer dan de eigenschap als een lege array te initialiseren.

Uitvoeren `GraphQlStateTest` door `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` zoekt alle klassen die uitvoeren `ResetAfterRequestInterface` en verifieert dat de `_resetState()` methode keert de staat van een voorwerp aan de zelfde staat terug het hield nadat werd geconstrueerd door `ObjectManager`.  Deze test leidt tot een de dienstvoorwerp met `ObjectManager`, klonen dan dat object, aanroepen `_resetState()`en vergelijkt vervolgens beide objecten. De test roept geen methoden aan tussen het instantiëren van objecten en `_resetState()`, zodat het opnieuw instellen van muteerbare toestanden niet wordt bevestigd. Er zijn wel problemen met een bug of typefout `_resetState()` kan de staat instellen op iets anders dan wat hij oorspronkelijk was.

#### ResetAfterRequestTest-fouten en mogelijke herstelbewerkingen

* **Klasse heeft inconsistente eigenschapswaarden**. Als deze test mislukt, controleert u of een klasse is gewijzigd met als resultaat dat het object na de constructie andere eigenschapswaarden heeft dan na de `_resetState()` wordt aangeroepen. Als de klasse waaraan u werkt, niet het `_resetState()` controleert u vervolgens de klassehiërarchie op een superklasse die deze implementeert.

* **Typed-eigenschap $x mag niet worden benaderd voordat een initialisatiebericht wordt weergegeven**. Dit probleem doet zich ook voor bij `GraphQlStateTest`.

  Uitvoeren `ResetAfterRequestTest` door uitvoering: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Functionele tests

De ontwikkelaars van de uitbreiding zouden functionele tests WebAPI voor GraphQL, evenals om het even welke douane geautomatiseerde of handfunctionele tests voor GraphQL moeten uitvoeren, terwijl het opstellen van de Server van de Toepassing van GraphQL. Deze functionele tests helpen ontwikkelaars potentiële fouten of compatibiliteitsproblemen te identificeren.

#### Statusmonitormodus

Tijdens het uitvoeren van functionele tests (of handmatige tests) kan de toepassingsserver werken met `--state-monitor mode` ingeschakeld om klassen te zoeken waarin de status onbedoeld opnieuw wordt gebruikt. Start de toepassingsserver normaal, behalve voeg de `--state-monitor` parameter.

```
bin/magento server:run --state-monitor
```

Nadat elke aanvraag is verwerkt, wordt een nieuw bestand toegevoegd aan de `tmp` map, bijvoorbeeld: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Als u klaar bent met testen, kunt u deze bestanden samenvoegen met de `bin/magento server:state-monitor:aggregate-output` gebruiken, waardoor twee samengevoegde bestanden worden gemaakt, één in `XML` en één in `JSON`.

Voorbeelden:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Deze bestanden kunnen worden geïnspecteerd met elk gereedschap dat u gebruikt om XML of JSON weer te geven. Hierin worden de gewijzigde eigenschappen van serviceobjecten weergegeven, zoals GraphQlStateTest. De `--state-monitor` De modus gebruikt dezelfde lijst met overslaan en filterlijst als GraphQlStateTest.

>[!NOTE]
>
>Gebruik de `--state-monitor` productiemodus. Het is alleen ontworpen voor ontwikkeling en testen. Er worden veel uitvoerbestanden gemaakt en deze worden langzamer uitgevoerd dan normaal.

>[!NOTE]
>
>`--state-monitor` is niet compatibel met PHP versies `8.3.0` - `8.3.4` vanwege een bug in de opschoonfunctie voor PHP. Als u PHP 8.3 gebruikt, moet u upgraden naar `8.3.5` of hoger is om deze functie te kunnen gebruiken.

## Bekende problemen

### Verzoeken die verloren gaan bij het beëindigen van een thread.

Als er een probleem met een arbeidersdraad is die de arbeidersdraad om veroorzaakt te beëindigen, dan zullen om het even welke HTTP- verzoeken die reeds aan die zelfde arbeidersdraad een rij worden gevormd een teruggestelde van de de contactdoosverbinding van TCP krijgen. Bij een reverse-proxy, zoals NGINX, vóór de server worden deze fouten weergegeven als `502` fouten. Workers kunnen sterven door vastlopen, door geheugengebruik of door PHP-fouten in extensies van derden. Dit probleem wordt veroorzaakt door het standaardgedrag van de HTTP-server van SWOLE. Standaard wordt de HTTP-server gestart in `SWOOLE_BASE` -modus. Op deze wijze, worden de HTTP- verzoeken die binnen komen toegewezen aan arbeidersdraden in een rij, zelfs als de arbeidersdraad nog een vorige verzoek verwerkt. Als u dit wijzigt in de `SWOOLE_PROCESS` in de modus, worden de verbindingen onderhouden door het hoofdproces en wordt aanzienlijk meer communicatie tussen processen gebruikt. De negatieve kant op `SWOOLE_PROCESS` PHP ZTS wordt niet ondersteund. Lees de [Brooddocumentatie](https://wiki.swoole.com/en/#/learn?id=swoole_process) voor meer informatie .

### Toepassingsserver kan onder bepaalde omstandigheden de vorige configuratie van kenmerken gebruiken.

De `CatalogGraphQl\Model\Config\AttributeReader` in `2.4.7` bevat een zeldzame fout die een GraphQL-verzoek kan veroorzaken om een reactie te krijgen met behulp van de vorige status van de configuratie Attributen. Er is een oplossing voor dit probleem geleverd in `2.4-develop`, maar niet op tijd voor `2.4.7` vrijgeven.
