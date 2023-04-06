---
title: Initialisatie en bootstrap van toepassingen
description: Lees over initialisatie en bootstrap logica voor de toepassing van de Handel.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# Overzicht van initialisatie en bootstrap

Om de toepassing van de Handel in werking te stellen, worden de volgende acties uitgevoerd in [pub/index.php][index]:

- Inclusief [app/bootstrap.php][bootinitial], die essentiële initialisatieroutines uitvoert zoals foutafhandeling, het initialiseren van de autoloader, het instellen van profielopties en het instellen van de standaardtijdzone.
- Een instantie maken van [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Maak een instantie van een Commerce-toepassing: [\Magento\Framework\AppInterface][app-face]
- Commerce uitvoeren

## Bootstrap-logica

[Het bootstrap-object][bootinitial] gebruikt het volgende algoritme om de toepassing van de Handel in werking te stellen:

1. Initialiseert de fouthandler.
1. Hiermee maakt u de [objectbeheer][object] en gedeelde basisdiensten die overal worden gebruikt en door het milieu worden beïnvloed. De omgevingsparameters worden op de juiste wijze in deze objecten geïnjecteerd.
1. Hiermee wordt bevestigd dat de onderhoudsmodus _niet_ ingeschakeld; anders, beëindigt.
1. bevestigt dat de toepassing Commerce is geïnstalleerd; anders, beëindigt.
1. Start de toepassing Commerce.

   Alle niet-afgevangen uitzonderingen tijdens het starten van de toepassing worden automatisch doorgestuurd naar de afdeling Handel in het dialoogvenster `catchException()` methode die u kunt gebruiken om de uitzondering af te handelen. Deze moet ofwel `true` of `false`:

   - Indien `true`: De handel behandelde met succes uitzondering. U hoeft niets anders te doen.
   - Indien `false`: (of een ander leeg resultaat) De uitzondering is niet door de Handel afgehandeld. Het bootstrap-object voert de standaardsubroutine voor de afhandeling van uitzonderingen uit.

1. Verstuurt de reactie die door het toepassingsobject wordt geboden.

   >[!INFO]
   >
   >De beweringen dat de toepassing van de Handel en niet op onderhoudswijze geïnstalleerd is zijn het standaardgedrag van `\Magento\Framework\App\Bootstrap` klasse. U kunt het wijzigen met een script voor het ingangspunt wanneer u het bootstrap-object maakt.

   Voorbeeld van een berichtpuntscript waarmee het bootstrap-object wordt gewijzigd:

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## Standaarduitzonderingsbehandeling

Het bootstrap-object geeft als volgt aan hoe de toepassing Commerce niet-afgevangen uitzonderingen verwerkt:

- In [ontwikkelmodus](../bootstrap/application-modes.md#developer-mode)wordt de uitzondering ongewijzigd weergegeven.
- Op een andere wijze, probeert om uitzondering te registreren en een generisch foutenbericht te tonen.
- Beëindigt Handel met foutencode `1`

## Toepassingen voor instappunten

Wij hebben de volgende toepassingen van het ingangspunt (die, toepassingen door Handel worden bepaald die door de Webserver als folderindex worden gebruikt):

### HTTP-ingangspunt

[\Magento\Framework\App\Http][http] werkt als volgt:

1. Hiermee bepaalt u de [toepassingsgebied](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Begint het voorcontrolemechanisme en het verpletteren van systemen om een controlemechanismeactie te vinden en uit te voeren.
1. Gebruikt een HTTP-reactieobject om het resultaat van de controlleractie te retourneren.
1. Foutafhandeling (in de volgende prioriteitsvolgorde):

   1. Als u [ontwikkelmodus](../bootstrap/application-modes.md#developer-mode):
      - Als de toepassing van de Handel niet geïnstalleerd is, richt aan de Tovenaar van de Opstelling opnieuw.
      - Als de toepassing van de Handel geïnstalleerd is, toon een fout en de statuscode 500 van HTTP (de Interne Fout van de Server).
   1. Als de toepassing van de Handel op onderhoudswijze is, toon een gebruikersvriendelijke &quot;Dienst niet beschikbaar&quot;landingspagina met de statuscode van HTTP 503 (de Dienst niet beschikbaar).
   1. Als de aanvraag voor de handel _niet_ geïnstalleerd, omleiding naar de wizard Setup.
   1. Als de sessie ongeldig is, leidt u deze om naar de startpagina.
   1. Als er een andere toepassingsinitialisatiefout is, geeft u een gebruikersvriendelijke pagina &quot;Pagina niet gevonden&quot; weer met HTTP-statuscode 404 (Niet gevonden).
   1. Voor een andere fout, toon een gebruikersvriendelijke &quot;Dienst niet beschikbaar&quot;pagina met reactie 503 van HTTP en produceer een foutenrapport en toon zijn identiteitskaart op de pagina.

### Statisch invoerpunt voor bron

[\Magento\Framework\App\StaticResource][static-resource] is een toepassing voor het ophalen van statische bronnen (bijvoorbeeld CSS, JavaScript en afbeeldingen). Het stelt om het even welke acties met een statische middel uit tot het middel wordt gevraagd.

>[!INFO]
>
>Het ingangspunt voor statische weergavebestanden wordt niet gebruikt in [productiemodus](application-modes.md#production-mode) om potentiële misbruiken op de server te voorkomen. In de productiemodus verwacht de toepassing van de Handel dat alle noodzakelijke middelen in de `<your Commerce install dir>/pub/static` directory.

In gebrek of ontwikkelaarwijze, wordt een verzoek om een niet bestaande statische middel opnieuw gericht aan het statische ingangspunt volgens de herschrijfregels die door aangewezen worden gespecificeerd `.htaccess`.
Wanneer het verzoek aan het ingangspunt opnieuw wordt gericht, ontleedt de toepassing van de Handel gevraagde URL die op teruggewonnen parameters wordt gebaseerd en vindt het gevraagde middel.

- In [ontwikkelaar](application-modes.md#developer-mode) in de modus, wordt de inhoud van het bestand geretourneerd, zodat de geretourneerde inhoud bijgewerkt is wanneer de bron wordt opgevraagd.
- In [default](application-modes.md#default-mode) in de modus, wordt de opgehaalde bron gepubliceerd zodat deze toegankelijk is via de eerder aangevraagde URL.

   Alle toekomstige verzoeken om het statische middel worden verwerkt door de server het zelfde als statische dossiers; dat wil zeggen, zonder daarbij het ingangspunt te betrekken. Als gepubliceerde bestanden moeten worden gesynchroniseerd met de originele bestanden, worden de `pub/static` directory moet worden verwijderd; als gevolg hiervan worden bestanden automatisch opnieuw gepubliceerd met de volgende aanvraag.

### Invoerpunt van mediabron

[Magento\MediaStorage\App\Media][media] wint media middelen (d.w.z. om het even welke dossiers die aan media opslag worden geupload) van het gegevensbestand terug. Het wordt gebruikt wanneer het gegevensbestand als media opslag wordt gevormd.

`\Magento\Core\App\Media` pogingen om het mediabestand te vinden in de geconfigureerde databaseopslag en het naar de `pub/static` en retourneert vervolgens de inhoud ervan. Als er een fout optreedt, wordt er een HTTP 404 (Not Found)-statuscode zonder inhoud in de header geretourneerd.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
