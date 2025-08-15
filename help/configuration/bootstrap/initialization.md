---
title: Initialisatie en bootstrap van toepassingen
description: Lees meer over initialisatie en bootstrap-logica voor de Commerce-toepassing.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---

# Overzicht van initialisatie en bootstrap

Om de toepassing van Commerce in werking te stellen, worden de volgende acties uitgevoerd in [ pub/index.php ][index]:

- Omvat [ app/bootstrap.php ][bootinitial], die essentiële initialiseringsroutines zoals fout behandeling, initialiserend autoloader, plaatsend het profileren opties, en het plaatsen van standaardtimezone uitvoert.
- Creeer een geval van [ \Magento\Framework\App\Bootstrap.php ][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Creeer een de toepassingsinstantie van Commerce: [ \Magento\Framework\AppInterface][app-face]
- Commerce uitvoeren

## Bootstrap-logica

[ het bootstrap voorwerp ][bootinitial] gebruikt het volgende algoritme om de toepassing van Commerce in werking te stellen:

1. Initialiseert de fouthandler.
1. Creeert de [ objecten manager ][object] en de basis gedeelde diensten die overal worden gebruikt en door het milieu worden beïnvloed. De omgevingsparameters worden op de juiste wijze in deze objecten geïnjecteerd.
1. Bevestigt dat de onderhoudswijze _niet_ wordt toegelaten; anders, eindigt.
1. Hiermee wordt bevestigd dat de Commerce-toepassing is geïnstalleerd; anders wordt de toepassing beëindigd.
1. Start de Commerce-toepassing.

   Alle niet-afgevangen uitzonderingen tijdens het starten van de toepassing worden automatisch aan Commerce doorgegeven via de methode `catchException()` die u kunt gebruiken om de uitzondering af te handelen. De laatste functie moet `true` of `false` retourneren:

   - Als `true`: Commerce heeft de uitzondering verwerkt. U hoeft niets anders te doen.
   - Als `false`: (of een ander leeg resultaat), heeft Commerce de uitzondering niet afgehandeld. Het bootstrap-object voert de standaardsubroutine voor de afhandeling van uitzonderingen uit.

1. Verstuurt de reactie die door het toepassingsobject wordt geboden.

   >[!INFO]
   >
   >De bewering dat de Commerce-toepassing is geïnstalleerd en niet in de onderhoudsmodus is het standaardgedrag van de `\Magento\Framework\App\Bootstrap` -klasse. U kunt het wijzigen met een script voor het ingangspunt wanneer u het bootstrap-object maakt.

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

Met het bootstrap-object wordt als volgt aangegeven hoe de Commerce-toepassing niet-afgevangen uitzonderingen verwerkt:

- Op [ ontwikkelaarwijze ](../bootstrap/application-modes.md#developer-mode), toont de uitzondering zoals-is.
- Op een andere wijze, probeert om uitzondering te registreren en een generisch foutenbericht te tonen.
- Beëindigt Commerce met foutcode `1`

## Toepassingen voor instappunten

Er zijn de volgende toepassingen voor ingangspunten (toepassingen die door Commerce zijn gedefinieerd en die door de webserver worden gebruikt als een directoryindex):

### HTTP-ingangspunt

[ \Magento\Framework\App\Http ][http] werkt als volgt:

1. Bepaalt het [ toepassingsgebied ](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Begint het voorcontrolemechanisme en het verpletteren van systemen om een controlemechanismeactie te vinden en uit te voeren.
1. Gebruikt een HTTP-reactieobject om het resultaat van de controlleractie te retourneren.
1. Foutafhandeling (in de volgende prioriteitsvolgorde):

   1. Als u [ ontwikkelaarwijze ](../bootstrap/application-modes.md#developer-mode) gebruikt:
      - Als de Commerce-toepassing niet is geïnstalleerd, stuurt u deze om naar de wizard Setup.
      - Als de Commerce-toepassing is geïnstalleerd, geeft u een fout en HTTP-statuscode 500 weer (Interne serverfout).
   1. Als de Commerce-toepassing in de onderhoudsmodus staat, geeft u een gebruikersvriendelijke landingspagina met HTTP-statuscode 503 (Service Unavailable) weer.
   1. Als de toepassing van Commerce _niet_ geïnstalleerd is, richt aan de Tovenaar van de Opstelling opnieuw.
   1. Als de sessie ongeldig is, leidt u deze om naar de startpagina.
   1. Als er een andere toepassingsinitialisatiefout is, geeft u een gebruikersvriendelijke pagina &quot;Pagina niet gevonden&quot; weer met HTTP-statuscode 404 (Niet gevonden).
   1. Voor een andere fout, toon een gebruikersvriendelijke &quot;Dienst niet beschikbaar&quot;pagina met reactie 503 van HTTP en produceer een foutenrapport en toon zijn identiteitskaart op de pagina.

### Statisch invoerpunt voor bron

[ \Magento\Framework\App\StaticResource ][static-resource] is een toepassing voor het terugwinnen van statische middelen (bijvoorbeeld, CSS, JavaScript, en beelden). Het stelt om het even welke acties met een statische middel uit tot het middel wordt gevraagd.

>[!INFO]
>
>Het ingangspunt voor statische meningsdossiers wordt niet gebruikt op [ productiemodus ](application-modes.md#production-mode) om potentiële exploitaties op de server te vermijden. In de productiemodus verwacht de Commerce-toepassing dat de map `<your Commerce install dir>/pub/static` alle benodigde bronnen bevat.

In de standaard- of ontwikkelaarsmodus wordt een aanvraag voor een niet-bestaande statische bron omgeleid naar het statische ingangspunt volgens de herschrijfregels die door de betreffende `.htaccess` zijn opgegeven.
Wanneer de aanvraag naar het ingangspunt wordt omgeleid, parseert de Commerce-toepassing de gevraagde URL op basis van opgehaalde parameters en zoekt de gevraagde bron.

- Op [ ontwikkelaar ](application-modes.md#developer-mode) wijze, is de inhoud van het dossier teruggekeerd zodat telkens als het middel wordt gevraagd, de teruggekeerde inhoud bijgewerkt is.
- Op [ gebrek ](application-modes.md#default-mode) wijze, wordt het teruggewonnen middel gepubliceerd zodat is het toegankelijk door eerder gevraagde URL.

  Alle toekomstige verzoeken om het statische middel worden verwerkt door de server het zelfde als statische dossiers; namelijk zonder het ingangspunt te impliceren. Als gepubliceerde bestanden moeten worden gesynchroniseerd met de originele bestanden, moet de map `pub/static` worden verwijderd. Als gevolg hiervan worden bestanden automatisch opnieuw gepubliceerd met de volgende aanvraag.

### Invoerpunt van mediabron

[ Magento\MediaStorage\App\Media ][media] wint media middelen (namelijk om het even welke dossiers terug die aan media opslag) van het gegevensbestand worden geupload. Het wordt gebruikt wanneer het gegevensbestand als media opslag wordt gevormd.

`\Magento\Core\App\Media` probeert het mediabestand te zoeken in de geconfigureerde databaseopslag en het naar de map `pub/static` te schrijven en vervolgens de inhoud ervan te retourneren. Als er een fout optreedt, wordt er een HTTP 404 (Not Found)-statuscode zonder inhoud in de header geretourneerd.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
