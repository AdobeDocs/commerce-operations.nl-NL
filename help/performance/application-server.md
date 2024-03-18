---
title: Toepassingsserver voor GraphQL API's
description: Volg deze instructies voor het inschakelen van de toepassingsserver voor GraphQL API's in uw Adobe Commerce-implementatie.
badgeCoreBeta: label="2.4.7-bèta" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 9d5795400880a65947b1b90c8806b9dcb14aba23
workflow-type: tm+mt
source-wordcount: '1897'
ht-degree: 0%

---

# Toepassingsserver voor GraphQL API&#39;s

Met de Commerce Application Server voor GraphQL API&#39;s kan Adobe Commerce de status handhaven bij aanvragen van de Commerce GraphQL API. De server van de Toepassing, die op de uitbreiding van de Steekproef wordt voortgebouwd, werkt als proces met arbeidersdraden die verzoekverwerking behandelen. Door een Bootstrapped toepassingsstaat onder GraphQL API verzoeken te bewaren, verbetert de Server van de Toepassing verzoekbehandeling en algemene productprestaties. API-aanvragen worden aanzienlijk efficiënter.

Toepassingsserver wordt alleen ondersteund in Adobe Commerce op het Starter- en Pro-project voor cloudinfrastructuur. Het is niet beschikbaar voor Magento Open Source projecten. De Adobe verleent geen steun voor op-gebouw plaatsingen van de Server van de Toepassing.

## Overzicht van toepassingsserverarchitectuur

De Server van de toepassing handhaaft staat tussen de verzoeken van GraphQL API van de Handel en elimineert de behoefte aan bootstrapping. Door de status van de toepassing over alle processen te delen, worden GraphQL-verzoeken aanzienlijk efficiënter, waardoor de responstijden met maximaal 30% afnemen.

Het PHP-uitvoeringsmodel zonder delen biedt een uitdaging vanuit het perspectief van latentie, omdat voor elke aanvraag de overvulling van het framework vereist is. Dit bootstrapping proces omvat tijdrovende taken zoals lezingsconfiguratie, vestiging het laarzentrekkerproces, en het creëren van de voorwerpen van de de dienstklasse.

Het overbrengen van aanvraagbehandelingslogica aan een toepassing-vlakke gebeurtenislijn lijkt de uitdaging van het stroomlijnen van verzoekverwerking op ondernemingsniveau te richten. Deze benadering elimineert de behoefte aan bootstrapping tijdens de levenscyclus van de verzoekuitvoering.

## Voordelen van het gebruik van toepassingsserver

De Server van de toepassing staat Adobe Commerce toe om staat tussen opeenvolgende GraphQL API verzoeken van de Handel te handhaven. Door de status van toepassingen te delen tussen aanvragen wordt de efficiëntie van API-aanvragen verbeterd doordat de verwerkingsoverhead tot een minimum wordt beperkt en de aanvraagverwerking wordt geoptimaliseerd. Als gevolg hiervan kan de responstijd voor GraphQL-verzoeken tot 30% worden verkort.

## Systeemvereisten

Voor het uitvoeren van de toepassingsserver is het volgende vereist:

* PHP 8.2 of hoger
* PHP-extensie v5+ geïnstalleerd
* Adequate RAM en CPU op basis van de verwachte belasting

## Toepassingsserver inschakelen

De `ApplicationServer` module (`Magento/ApplicationServer/`) schakelt Application Server voor GraphQL API&#39;s in. Toepassingsserver wordt ondersteund op locatie en in de cloud.

## Toepassingsserver inschakelen op Cloud Pro

Voltooi de volgende taken voordat u Application Server op Cloud Pro implementeert:

1. Bevestig dat Adobe Commerce op Commerce Cloud is geïnstalleerd met gebruik van Cloud Template versie 2.4.7 of hoger.
1. Zorg ervoor dat al uw aanpassingen en uitbreidingen van de Handel zijn [compatibel](https://developer.adobe.com/commerce/php/development/components/app-server/) met toepassingsserver.
1. Clone your Commerce Cloud project.
1. Pas indien nodig de instellingen in het bestand &#39;application-server/nginx.conf.sample&#39; aan.
1. Plaats de actieve sectie &#39;Web&#39; in `project_root/.magento.app.yaml` volledig.
1. Verwijder de commentaarmarkering uit de volgende &#39;web&#39;-sectieconfiguratie in het dialoogvenster `project_root/.magento.app.yaml` bestand dat de opdracht Start van toepassingsserver bevat.

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

### Toepassingsserver implementeren op Cloud Pro

Na het uitvoeren van de in de eerste plaats vereiste taken, stel de Server van de Toepassing gebruikend dit bevel op:

```bash
git push
```

### Voordat u begint met de implementatie van Cloud Starter

Voltooi de volgende taken voordat u Application Server in Cloud Starter implementeert:

1. Bevestig dat Adobe Commerce op Commerce Cloud is geïnstalleerd met gebruik van Cloud Template versie 2.4.7 of hoger.
1. Zorg ervoor dat al uw aanpassingen en uitbreidingen van de Handel met de Server van de Toepassing compatibel zijn.
1. Bevestig dat de `CRYPT_KEY` omgevingsvariabele wordt ingesteld voor uw instantie. U kunt de status van deze variabele controleren op het Cloud Project Portal (onboarding UI).
1. Clone your Commerce Cloud project.
1. Naam wijzigen `application-server/.magento/.magento.app.yaml.sample` tot `application-server/.magento/.magento.app.yaml` en pas indien nodig instellingen aan in .magento.app.yaml.
1. Uncomment de configuratie van de volgende route in `project_root/.magento/routes.yaml` bestand om te leiden `/graphql` verkeer aan de Server van de Toepassing.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Voeg bijgewerkte bestanden toe aan de git-index met de volgende opdracht:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Leg uw wijzigingen vast met deze opdracht:

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
> Zorg ervoor dat alle aangepaste instellingen die u hebt, zich in de hoofdmap bevinden `.magento.app.yaml` bestand wordt naar behoren gemigreerd naar de `application-server/.magento/.magento.app.yaml` bestand. Wanneer de `application-server/.magento/.magento.app.yaml` het dossier wordt toegevoegd aan uw project, zou u het naast de wortel moeten handhaven `.magento.app.yaml` bestand.
> Als u bijvoorbeeld [rabbitmq configureren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) of [webeigenschappen beheren](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property) u zou de zelfde configuratie aan moeten toevoegen `application-server/.magento/.magento.app.yaml` ook.

### Toepassingsserver implementeren in de cloud

Na het voltooien van de [voorwaarden](#before-you-begin-a-cloud-starter-deployment), implementeert Application Server met deze opdracht:

```bash
git push
```

### Inschakelen van toepassingsserver op Cloud Starter verifiëren

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

1. U kunt ook controleren of Application Server wordt uitgevoerd door de volgende opdracht uit te voeren:

   ```bash
   ps aux|grep php
   ```

   U dient een `bin/magento server:run` verwerken met meerdere threads.

Als deze verificatiestappen met succes zijn uitgevoerd, wordt de toepassingsserver uitgevoerd en wordt deze `/graphql` verzoeken.


## De Server van de Toepassing op plaatsingen op het gebouw toelaten

De `ApplicationServer` module (`Magento/ApplicationServer/`) schakelt Application Server voor GraphQL API&#39;s in.

Voor het lokaal uitvoeren van de toepassingsserver is de installatie van de SWF-extensie en een kleine wijziging in het NGINX-configuratiebestand van uw implementatie vereist.

### Alvorens u met een plaatsing op-gebouw begint

Voltooi deze twee taken voordat u de `ApplicationServer` module:

* Nginx configureren

* De SWF v5+-extensie installeren en configureren

### Nginx configureren

Uw specifieke plaatsing van de Handel bepaalt hoe te om Nginx te vormen. In het algemeen wordt het Nginx-configuratiebestand standaard benoemd `nginx.conf` en wordt in een van deze directory&#39;s geplaatst: `/usr/local/nginx/conf`, `/etc/nginx`, of `/usr/local/etc/nginx`. Zie [Beginnerengids](https://nginx.org/en/docs/beginners_guide.html) voor meer informatie over het configureren van Nginx.

Voorbeeld-Nginxconfiguratie:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Koel installeren en configureren

Als u de toepassingsserver lokaal wilt uitvoeren, installeert u de extensie SWOLE (v5.0 of hoger). Deze extensie kan op meerdere manieren worden geïnstalleerd.

## Toepassingsserver uitvoeren

Start de toepassingsserver:

```bash
bin/magento server:run
```

Deze opdracht start een HTTP-poort op 9501. Zodra de Server van de Toepassing lanceert, wordt haven 9501 een volmachtsserver van HTTP voor alle vragen van GraphQL.

## Voorbeeld: Koel installeren (OSX)

Deze procedure laat zien hoe u de Swoole extensie installeert op PHP 8.2 voor OSX-systemen. Het is een van de verschillende manieren om de extensie Swoole te installeren.

### Koel installeren

Enter:

```bash
pecl install swoole
```

Tijdens de installatie geeft Adobe Commerce aanwijzingen weer om ondersteuning voor `openssl`, `mysqlnd`, `sockets`, `http2`, en `postgres`. Enter `yes` voor alle opties behalve `postgres`.

### De installatie van de module bevestigen

Uitvoeren `php -m | grep swoole` om te bevestigen dat de extensie is ingeschakeld.

### Algemene fouten bij de installatie van de module

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

### Bevestig dat de toepassingsserver wordt uitgevoerd

Om te bevestigen dat de Server van de Toepassing in uw plaatsing loopt, voer dit bevel uit:

```bash
ps aux | grep php
```

De extra manieren om te bevestigen dat de Server van de Toepassing loopt omvatten:

* Controleer de `/var/log/application-server.log` bestand voor berichten die betrekking hebben op verwerkte GraphQL-aanvragen.
* Probeer verbinding te maken met de HTTP-poort waarop de toepassingsserver wordt uitgevoerd. Bijvoorbeeld: `curl -g 'http://localhost:9501/graph`.

### Bevestig dat GraphQL-verzoeken worden verwerkt door Application Server

Toepassingsserver voegt de `X-Backend` responsheader met de waarde `graphql_server` aan elk verzoek dat het verwerkt. Om te controleren of een verzoek door de Server van de Toepassing is behandeld, controleer deze reactiekop.

### Bevestig uitbreiding en aanpassingsverenigbaarheid met de Server van de Toepassing

Extensieontwikkelaars en -handelaren moeten eerst controleren of hun code voor uitbreiding en aanpassing voldoet aan de technische richtlijnen die worden beschreven in [Technische richtsnoeren](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Overweeg deze richtlijnen tijdens codeevaluatie:

* De klassen van de dienst (namelijk klassen die gedrag maar geen gegevens verstrekken, zoals `EventManager`) mag niet muteerbaar zijn.
* Vermijd tijdelijke koppeling.

## Toepassingsserver uitschakelen

De procedures om de Server van de Toepassing onbruikbaar te maken variëren afhankelijk van of de server in een op-gebouw of plaatsing van de Wolk loopt.

### Toepassingsserver uitschakelen in de cloud

1. Verwijder alle nieuwe bestanden en eventuele andere codewijzigingen die zijn opgenomen in het dialoogvenster `AppServer Enabled` onderschrijven tijdens uw voorbereidingen voor de implementatie.

1. Leg uw wijzigingen vast met deze opdracht:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Deze wijzigingen implementeren met deze opdracht:

   ```bash
   git push
   ```

### Toepassingsserver uitschakelen

1. Maak een opmerking in het dialoogvenster `/graphql` deel van `nginx.conf` bestand dat u hebt toegevoegd bij het inschakelen van toepassingsserver.
1. Start nginx opnieuw.

Deze methode om de Server van de Toepassing onbruikbaar te maken kan nuttig zijn om prestaties snel te testen of te vergelijken.

### Bevestig dat Toepassingsserver is uitgeschakeld

Bevestig dat GraphQL-aanvragen worden verwerkt door `php-fpm` in plaats van Application Server, voert u deze opdracht in: `ps aux | grep php`.

Nadat de toepassingsserver is uitgeschakeld:

* `bin/magento server:run` is inactief.
* `var/log/application-server.log` bevat geen items na GraphQL-aanvragen.

## Integratie- en functionele tests voor PHP Application Server

De ontwikkelaars van de uitbreiding kunnen twee integratietests in werking stellen om uitbreidingsverenigbaarheid met de Server van de Toepassing te verifiëren: `GraphQlStateTest` en `ResetAfterRequestTest`.

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

De ontwikkelaars van de uitbreiding zouden functionele tests WebAPI voor GraphQL, evenals om het even welke douane geautomatiseerde of handfunctionele tests voor GraphQL moeten uitvoeren, terwijl het opstellen van de Server van de Toepassing. Deze functionele tests helpen ontwikkelaars potentiële fouten of compatibiliteitsproblemen te identificeren.
