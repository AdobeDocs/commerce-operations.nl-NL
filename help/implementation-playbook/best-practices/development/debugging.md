---
title: Aanbevolen werkwijzen voor foutopsporing
description: Leer technieken om algemene Adobe Commerce-ontwikkelingsproblemen op te lossen.
feature: Best Practices
role: Developer
exl-id: 78fbea7b-28e8-4713-990d-b4cae159250c
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# Aanbevolen procedures voor foutopsporing voor Adobe Commerce

In dit onderwerp worden manieren uitgelegd om het Adobe Commerce-framework systematisch en effectief te debuggen. Het doel is om u te helpen snel de wortel van een probleem bereiken en onderzoekstijd minimaliseren.

## Problemen oplossen: standaardverdachten

Deze sectie beschrijft de gemeenschappelijkste kwesties die u tijdens ontwikkeling zou kunnen ontmoeten.

### Cache

- De cache leegmaken voor verder onderzoek
- Bekijk de APC-cache, CDN, Varnish, gegenereerde code en de mappen `var/view_preprocessed` en `pub/static/`
- Wachtrij-handlers stoppen en opnieuw starten nadat de cache is leeggemaakt of code is gewijzigd

Het volgende codevoorbeeld verstrekt nuttige bevelen met betrekking tot het beheren van het geheime voorgeheugen (loopt niet op productiemilieu&#39;s):

```bash
# restart php-fpm to flush APC
sudo service php-fpm restart
 
# restart varnish to force full flush
sudo service varnish restart
 
# clear generated files
rm -rf generated/*
 
# clear static file cache
rm -rf var/view_preprocessed/*
rm -rf pub/static/*
 
# flush redis cache
redis-cli -n <db_number> FLUSHDB
 
# flush redis cache and sessions
redis-cli FLUSHALL
 
# flush redis cache with telnet
telnet <ip_or_host> 6379
SELECT <db_number>
FLUSHDB
Ctrl + ]
quit
 
# flush redis cache and sessions with telnet
telnet <ip_or_host> 6379
FLUSHALL
Ctrl + ]
quit
 
# find consumers
pgrep -af queue:consumers:start
 
# kill all queue consumers (they will restart by cron job)
sudo pkill -f queue:consumers:start
 
# kill a specific queue consumer (it will restart by cron job)
sudo kill <process_id>
```

### Geïndexeerde gegevens

Wijzig de index van alles als de uitgave betrekking kan hebben op een index. Fouten opsporen in geïndexeerde gegevens gebeurt doorgaans in niet-productieomgevingen. Bij productieomgevingen kunt u de oorsprong van de indexonjuiste uitlijning onderzoeken voordat u de index opnieuw indexeert. De kenmerken van de slechte staat kunnen je iets vertellen over de oorsprong van het probleem.

### Composer

U zou verouderde code wegens een takverandering of wegens kerndossiers kunnen hebben die in een vorige het zuiveren inspanning werden uitgegeven. Voer de volgende opdrachten uit om potentiële problemen te voorkomen:

```bash
rm -rf vendor/*
composer clear-cache
composer install
```

### Gegenereerde inhoud

Voordat u fouten opspoort in de gegenereerde inhoud in JS, CSS, afbeeldingen, vertalingen en andere bestanden, moet u de bestanden opnieuw samenstellen.

```bash
rm -rf generated/* var/cache/* var/page_cache/* var/session/* var/view_preprocessed/* pub/static/*
bin/magento setup:static-content:deploy
bin/magento cache:flush
```

### Modus Ontwikkelaar

Controleer of de lokale installatie in de modus `developer` staat.

### Nieuwe module

Als u een module hebt gemaakt, controleert u op de volgende problemen:

- Is de module toegelaten?

  ```bash
  bin/magento module --enable Your_Module
  ```

  Controleer het bestand `app/etc/config.php` op de nieuwe module.

- Controleer het nesten van de bestand- en mapstructuur. Zijn lay-outbestanden bijvoorbeeld in de map `view/layout/` in plaats van in de map `view/frontend/layout` ? Worden sjablonen in de map `view/frontend/template` in plaats van in de map `view/frontend/templates` ?

## Problemen oplossen: halfsplitsen

Als de gebruikelijke verdachten geen oplossing voor het probleem bieden, is de snelste manier om verder te gaan door het probleem te halveren (of te bedelen). Met deze methode, elimineert u grote brokken en verdeelt wat wordt verlaten om van de worteloorzaak de plaats te bepalen in plaats van lineair door de code te gaan.

Zie de volgende diagrammen:

![ Bisect diagram ](../../../assets/playbooks/bisect.png)

![ Bisect diagram ](../../../assets/playbooks/bisect2.png)

Er zijn verschillende manieren om te discussiëren, maar de Adobe beveelt aan deze volgorde te volgen:

- Bisect per onderwerp
- Bisect op verbintenissen
- Bestanden verbergen

### Stap 1: Bisect per onderwerp

Als het probleem code-verwant zou kunnen zijn, elimineer eerst de grote brokken. Enkele van de grote brokken die u moet bedenken zijn:

- **kader van Adobe Commerce** - is het probleem met betrekking tot Adobe Commerce bij allen of kon het met een ander verbonden systeem verwant zijn?
- **Server en cliënt** - ontruim het browser geheime voorgeheugen en de opslag. Is het probleem opgelost? Dat kan een servergerelateerde oorzaak uitsluiten. Bestaat dit probleem nog? U hoeft geen tijd meer te verspillen aan foutopsporing in de browser.
- **Zitting** - komt het probleem voor elke gebruiker voor? Als niet, zou uw probleem tot zitting of browser-verwante onderwerpen kunnen worden beperkt.
- **Geheime voorgeheugen** - wijzigt het onbruikbaar maken van alle geheime voorgeheugens om het even wat? Als zo, kunt u zich op voorgeheugen-verwante onderwerpen concentreren.
- **Gegevensbestand** - komt het probleem op elk milieu voor dat de zelfde code in werking stelt? Als niet, zoek problemen in configuratie en andere op gegevensbestand betrekking hebbende onderwerpen.
- **code** - zoek codekwesties als niets van bovengenoemd het probleem oplost.

### Stap 2: Bisect by commit

Als het probleem tussen nu en twee maanden geleden begon, rolt u de code terug naar twee maanden geleden. Controleer of het probleem nog steeds bestaat. Eén maand vooruit. Doet het probleem zich daar voor? Indien niet, ga twee weken verder. Komt het nu voor? Ga een week terug. Nog steeds? Ga vier dagen terug. Op een bepaald punt, hebt u slechts één verlaten begaat die waarschijnlijk code met betrekking tot het probleem zal bevatten. De hoofdoorzaak is nu waarschijnlijk beperkt tot de bestanden die zijn bewerkt in de toewijzing.

U kunt weken en dagen vervangen door verbintenissen. Bijvoorbeeld, rol terug 100 begaat, door:sturen 50, door:sturen 25, terug 12.

### Stap 3: Bestanden archiveren

- Verdeel Adobe Commerce op bestandstypen (core en non-core). Eerst, maak alle klant en marktplaatsmodules onbruikbaar. Bestaat dit probleem nog? Het is hoogstwaarschijnlijk een niet-kernkwestie.
- Schakel (ongeveer) de helft van de modules opnieuw in het `app/etc/config.php` -bestand in. Houd rekening met afhankelijkheden. Het is best om moduleclusters met het zelfde onderwerp allen in één keer toe te laten. Bestaat dit probleem nog?
- Laat een kwart van de resterende modules toe. Bestaat dit probleem nog? Schakel de helft uit van wat u hebt ingeschakeld. Deze methode kan u helpen de worteloorzaak aan één enkele module isoleren.

## Tijdbesparing

Naast de het oplossen van problementechnieken, verstrekt deze sectie sommige algemene regels die kunnen helpen tijd tijdens het zuiveren besparen.

### Beperkingsgegevens

Overweeg of u de volledige catalogus of alle opslagmeningen nodig hebt om de kwestie te herhalen. U kunt fouten in indexeringsproblemen opsporen met een databasekloon waarbij u 95% van de catalogus hebt verwijderd voordat u de foutopsporing start. Deze methode bespaart veel tijd tijdens het indexeren van processen. Maak een duplicaat van de clientdatabase met een lager aantal winkels en een lagere catalogus. Dit kan ook op andere entiteiten (zoals klanten) afhankelijk van het gebied van toepassing zijn u zuivert.

### Meer informatie vragen

Soms is het een eenvoudige stap om te vergeten hoe de code en het technische werk zijn: om meer informatie vragen. Op volledig scherm worden beelden vastgelegd, een video, een videoconferentiegesprek met de persoon die het probleem heeft geïdentificeerd, replicatiestappen, vragen of er andere schijnbaar onbelangrijke dingen zijn gebeurd rond de problematische gebeurtenis. Vraag wat iemand had verwacht. Is dit echt een bug of misschien gewoon een misverstand over de manier waarop de code werkt?

### Taal en interpretatie

Is de beschrijving van het probleem duidelijk? Weet u zeker dat termen of beschrijvingen niet op meerdere manieren kunnen worden geïnterpreteerd? Als dat het geval is, zorg er dan voor dat u het over hetzelfde heeft.

### Internet zoeken

Voer een internetzoekopdracht uit met termen die betrekking hebben op het probleem. Het is mogelijk dat iemand anders al hetzelfde probleem heeft ondervonden. Onderzoek door de [ kwesties van Adobe Commerce GitHub ](https://github.com/magento/magento2/issues).

### Onderbreken

Als u een probleem te lang bekijkt, kan het uitdagend zijn om een oplossing te vinden. Zet je werk neer en neem een andere taak op of ga wandelen. Het antwoord kan op u komen als u de kwestie een tijdje vergeet.

## Gereedschappen

De n98 magerun CLI Hulpmiddelen ([ https://github.com/netz98/n98-magerun2 ](https://github.com/netz98/n98-magerun2)) verstrekken nuttige mogelijkheden om met Adobe Commerce van de bevellijn te werken. Dit zijn vooral de volgende opdrachten:

```bash
n98-magerun2.phar dev:console
n98-magerun2.phar sys:cron:run
n98-magerun2.phar db:console
n98-magerun2.phar index:trigger:recreate
```


## Codefragmenten

De volgende onderwerpen verstrekken codefragmenten die kunnen worden gebruikt om kwesties in de projecten van Commerce te registreren of te identificeren.

### Controleren of Commerce een XML-bestand gebruikt

Voeg een duidelijke syntaxisfout in een dossier van XML toe om te zien of wordt het gebruikt. Open een tag en sluit deze bijvoorbeeld niet:

```xml
<?xml version="1.0"?>
<test
```

Als dit bestand wordt gebruikt, wordt een fout gegenereerd. Als dit niet het geval is, wordt de module mogelijk niet gebruikt of niet ingeschakeld, of bevindt het XML-bestand zich mogelijk op de verkeerde locatie.

### Logboekregistratie

>[!BEGINTABS]

>[!TAB  Adobe Commerce ]

```php
\Magento\Framework\App\ObjectManager::getInstance()
    ->get(\Psr\Log\LoggerInterface::class)->debug('message');
```

>[!TAB  Monolog ]

```php
$log = new \Monolog\Logger('custom', [new \Monolog\Handler\StreamHandler(BP.'/var/log/test.log')]);
$log->info('Your Logging Message', ['context' => ['email' => 'john@example.com']]);
```

>[!TAB  Zend ]

```php
$writer = new \Zend\Log\Writer\Stream(BP . '/var/log/test.log');
$logger = new \Zend\Log\Logger();
$logger->addWriter($writer);
$logger->info('Your text message');
$logger->info(print_r($yourArray, true));
```

>[!ENDTABS]

### Logboekregistratie op laag niveau

Twee voorbeelden die altijd in een PHP-bestand werken:

```php
file_put_contents('/var/www/html/var/log/example.log', "example line\n", FILE_APPEND);
file_put_contents('/var/www/html/var/log/example.log', print_r($yourArray, true) . "\n", FILE_APPEND);
```

En voor een stacktracering:

```php
try {
    throw new \Exception('example');
} catch (\Exception $e) {
    file_put_contents('/var/www/html/var/log/example.log', $e->getTraceAsString() . "\n", FILE_APPEND);
}
```
