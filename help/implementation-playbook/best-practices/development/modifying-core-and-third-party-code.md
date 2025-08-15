---
title: Tips en trucs voor het wijzigen van PHP-code voor kern en derden
description: Leer hoe en wanneer u Adobe Commerce en PHP-code van derden wijzigt.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
exl-id: 32b3137d-fc00-4be8-ba02-5d8d48a51fe1
source-git-commit: d47567a8d69ccdae3db01e964f1db12e8ae26717
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# Tips en trucs voor het wijzigen of overschrijven van PHP-code voor core en derden

In dit document worden aanbevolen procedures beschreven wanneer u de functionaliteit, het resultaat of de invoer van code die u niet hebt gemaakt, moet wijzigen of niet rechtstreeks hoeft te beheren. Met andere woorden, kerncode en code van derden. Dit document richt zich vooral op de achterste PHP code.

## Methoden voor het wijzigen van code

Wanneer het wijzigen van code, is het belangrijk om het werkingsgebied van uw veranderingen te overwegen. Het &quot;bereik&quot; van de wijzigingen heeft betrekking op de mate waarin de effecten van de wijzigingen in de code verreikend zijn. Als beste praktijken, baseer het besluit voor hoe de uiteindelijke implementatie wordt voltooid gebaseerd op de optie die de kleinste voetafdruk en het minste middelgebruik heeft. Hoe breder de codoverschrijvingen zijn, des te meer wijkt een ontwikkelingsteam van de kernfunctionaliteit van Adobe Commerce af, waardoor de kans op fouten groter wordt en er meer inspanningen worden geleverd om de codebase in de toekomst te behouden.

### Reparatie

Een flard is een dossier dat instructies bevat om code binnen een dossier direct te veranderen dat niet onder de directe controle van het ontwikkelingsteam is. Dit is een optie die gewoonlijk als laatste redmiddel zou moeten worden beschouwd wanneer geen andere opties bestaan. Patches zijn bedoeld als een tijdelijke oplossing. Als u een pleister moet aanmaken, dient u de pleister te verwijderen voor een meer permanente oplossing binnen 2-4 weken. 

Patches worden gemakkelijk verbroken. Als de bestanden waarop de patch is gericht, worden bijgewerkt, werkt de patch vaak niet meer. Dat is omdat een flarddossier lijnaantallen en kolomaantallen bevat die specifiek wijzen op wat door de flardflatie moet worden veranderd. Als er niets overeenkomt met wat de patch had verwacht, wordt de code niet meer toegepast en wordt de code verbroken.

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### Wat kan worden veranderd met een pleister

Alles. Letterlijk, kan om het even welk karakter binnen om het even welk gericht dossier worden veranderd. Patches zijn niet beperkt tot een bepaald bestandstype of een bepaalde codetaal. Gewoonlijk gebruikt u een patch om bestanden in de map `vendor` als doel in te stellen. 

#### Wanneer gebruikt u een pleister

Als u zich realiseert dat er geen andere optie bestaat. Wanneer de leverancier bijvoorbeeld nog een oplossing voor de code moet publiceren, kunt u een patch gebruiken om het probleem tijdelijk aan te pakken terwijl u op een permanente oplossing wacht.

#### Nadelen

Patches worden gemakkelijk verbroken. Zodra de doelcode verandert, werkt de patch niet meer. Ze zijn alleen bedoeld als een kortetermijnoplossing.

### Voorkeur

Een voorkeur is een concept dat is ontworpen in het Adobe Commerce-platform. Het is in wezen een &quot;vervanging van de klasse PHP&quot;.

Het Adobe Commerce-platform gebruikt een &#39;objectmanager&#39; om PHP-klassen te instantiëren, omdat het geen PHP-klassen instantieert met het nieuwe trefwoord zoals in traditionele PHP-toepassingen. In plaats daarvan kruist de objectmanager de naam van de PHP-klasse die moet worden geïnstantieerd met een gecompileerde configuratie om te bepalen of een module een voorkeur voor de oorspronkelijke klasse heeft gedeclareerd. Als een voorkeur voor de PHP-klasse wordt gevonden, instantieert de objectmanager in plaats daarvan de opgegeven klasse.

Opgemerkt moet worden dat (gewoonlijk) de nieuwe PHP klasse die de oorspronkelijke PHP klasse vervangt, de oorspronkelijke PHP klasse uitbreidt/overerft van de oorspronkelijke PHP klasse. Dit gebeurt om een paar redenen:

- Om ervoor te zorgen dat de injectie van afhankelijkheid/type-hinting wordt nageleefd. Anders treedt een fatale fout op en wordt de toepassing afgebroken.
- Voor minimale code schrijven. Als de originele PHP klasse tien methodes bevat maar u slechts één methode moet met voeten treden, kunt u één methode gewoonlijk veranderen alleen en de andere negen methodes intact laten. Dit is belangrijk om ervoor te zorgen dat u geen updates van de kernfunctionaliteit blokkeert aangezien het platform aan nieuwe versies wordt bevorderd.

#### Een voorkeur declareren

Het is een vrij eenvoudig proces om een voorkeur te verklaren. Er moet één regel code worden toegevoegd aan een `di.xml` -bestand in een module. Dit kan globaal of binnen om het even welk Adobe Commerce &quot;gebied&quot;, zoals `frontend`, `adminhtml`, `graphql`, `webapi_rest`, en `crontab` worden gedaan.

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### Wat kan worden gewijzigd met een voorkeur

Alleen PHP-klassen kunnen met een voorkeur worden overschreven. Binnen de PHP klasse, kunt u openbare en beschermde methodes en eigenschappen wijzigen. Voor openbare en beschermde methodes, kunt u de methode volledig met voeten treden of u kunt de argumenten wijzigen die in (of het resultaat uit) de originele oudermethode gaan.

Particuliere methoden kunnen technisch niet worden overschreven. U kunt echter uw eigen vervanging maken voor de oorspronkelijke methode van het type private. U kunt zelfs een willekeurige naam geven, u kunt ook de oorspronkelijke naam gebruiken. Het maakt niet uit, omdat een methode van het type private alleen bestaat in het bestand dat deze methode bevat. Om een privé methode met voeten te treden, moet u de openbare of beschermde methode met voeten treden of wijzigen die de originele privé methode roept en u moet uw eigen functionaliteit in zijn plaats substitueren.

#### Wanneer gebruikt u een voorkeur

U kunt de voorkeuren opnieuw gebruiken als er geen andere optie bestaat en als u uw doel niet kunt bereiken met een injectie van afhankelijkheid, een plug-in of een waarnemer. Soms hebt u een voorkeur nodig als u methoden of eigenschappen van het type private of protected moet wijzigen of overschrijven. Er zij op gewezen dat de voorkeur spaarzaam moet worden toegepast. Ze zijn een nogal &#39;hebzuchtige&#39; methode om de toepassing te wijzigen en je neemt in feite de eigendom over van de PHP klasse. Dit kan tot conflicten met derdemodules leiden en updates aan de kernklasse blokkeren en tot moeilijk-aan-diagnose insecten leiden. Het Adobe Commerce-platform is ontworpen om andere mogelijkheden op te nemen waarmee wijzigingen in de onderliggende code met een kleinere voetafdruk kunnen worden aangebracht.

#### Nadelen

Voorkeuren zijn een vloeiende manier om code te wijzigen en moeten alleen worden gebruikt als andere opties niet bestaan. Voorkeuren kunnen vaak leiden tot conflicten binnen de codebase en erger nog, ze kunnen kernupdates blokkeren die optreden bij upgrades van het platform. 

### Waarnemer

Een waarnemer is het concept van een gebeurtenisluisteraar, zoals die in vele toepassingen, platforms, bibliotheken, en coderingstalen wordt gevonden. Het concept is niet uniek voor het Adobe Commerce-platform. Waarnemers zijn sinds de dagen van Magento 1 op het platform aangesloten en worden beschouwd als een primaire keuze voor het wijzigen van de kerncode en code van derden. 

De kerncodebase en alle modules van derden kunnen een gebeurtenis verzenden op een gekozen plaats in de code. De waarnemer, die wordt gedeclareerd in een `events.xml` -bestand en luistert naar de verzonden gebeurtenis op naam, kan op globaal niveau werken of worden beperkt tot elk Adobe Commerce-&quot;gebied&quot;, zoals `frontend` , `adminhtml` , `graphql` , `webapi_rest` en `crontab` .

#### Hoe een waarnemer te declareren

Waarnemers kunnen worden geconfigureerd in een globaal of gebiedspecifiek `events.xml` -bestand.

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### Wat kan met een waarnemer worden veranderd?

Waarnemers gelden alleen voor PHP-code binnen het Adobe Commerce-platform. U kunt alleen de specifieke gegevens en objecten wijzigen die met gebeurtenisverzending worden doorgegeven.

#### Wanneer een waarnemer wordt gebruikt

Wanneer beschikbaar! Als waarnemers meer beschikbaar en flexibeler zouden zijn, zouden ze de nummer twee in deze lijst krijgen. Waarnemers hebben minder verwerkingsoverhead dan plug-ins, ze zijn minder beschikbaar en minder flexibel.

#### Nadelen

Terwijl de waarnemers een uitstekende manier zijn om code te onderscheppen en te wijzigen, moet de verzending van de gebeurtenissen in de kern of de derdencode worden toegevoegd om voor uw code beschikbaar te zijn om te luisteren naar. Hierdoor is het concept van het gebruik van waarnemers een beetje beperkt. U bent beperkt tot gebeurtenissen waarvoor een ontwikkelaar de voorspelling had om in de code op te nemen.

Een andere beperkende factor van waarnemers is dat de verzonden gebeurtenis alleen toegang biedt tot de specifieke gegevens en objecten die de ontwikkelaar heeft doorgegeven met de gebeurtenis.

### Insteekmodule

Een plug-in is een flexibel concept dat is geïntroduceerd in het Adobe Commerce-platform. Het staat u toe om het even welke openbare PHP methodes te onderscheppen, te vervangen en te wijzigen. Met behulp van insteekmodules kunt u de argumenten wijzigen die naar een methode gaan voordat de doelmethode wordt uitgevoerd, het resultaat wijzigen nadat de doelmethode is uitgevoerd of de doelmethode volledig vervangen. U kunt vele methoden van een bepaalde PHP-klasse wijzigen in één insteekmodulebestand. U kunt ook het argument `$subject` gebruiken om openbare methoden uit te voeren die in de beoogde PHP-klasse bestaan.

#### Een plug-in declareren

Plug-ins kunnen worden geconfigureerd in een globaal of gebiedspecifiek `di.xml` bestand.

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### Wat kan worden gewijzigd met een plug-in

Deze functionaliteit is alleen beschikbaar voor PHP-klassen. U kunt de invoer of uitvoer van een openbare methode wijzigen en u kunt een plug-in gebruiken om andere functionaliteit te activeren. Als meerdere plug-ins op dezelfde PHP-klasse zijn gericht, kan een sorteervolgorde voor het uitvoeren van plug-ins zodanig worden ingesteld dat de plug-in voor of na andere plug-ins kan worden uitgevoerd.

#### Wanneer gebruikt u een plug-in

Telkens wanneer de gebiedsvervanging niet beschikbaar is. De stop- ins wordt gebruikt algemeen door kerncodebase, derdencode, en kan algemeen in uw eigen douanecode worden gebruikt. Als u functies moet wijzigen die niet in het bezit zijn van of worden beheerd door uw aangepaste code, kunt u gewoonlijk met een plug-in werken.

#### Nadelen

Kan beschermde methoden of eigenschappen niet wijzigen. De verwerkingsoverhead is hoger dan die van een waarnemer. Dat is niet echt een argument om geen plug-ins te gebruiken, het verschil is triviaal. Dit is echter iets goeds om in gedachten te houden.

### Vervanging van afhankelijkheid

De injectie van de afhankelijkheid is een standaardobject-georiënteerd codeerconcept waarin u uw vereiste gebiedsdelen in een klasse met de aannemer doorgeeft. Het Adobe Commerce-platform zet dit echter een stap verder door meerdere manieren te bieden om afhankelijkheden te vervangen door XML. Hoofdzakelijk, gebiedsvervanging. De vervanging van de afhankelijkheid is niet geschikt voor elke situatie maar het staat voor minimale code het schrijven, lage overheadkosten toe, en u kunt nauwkeurige stukken van code slechts strikt richten. U kunt privé en beschermde methodes met gebiedsvervanging wijzigen.

#### Hoe te om gebiedsdeelvervanging te gebruiken

Afhankelijkheidsvervanging kan globaal of gebiedsspecifiek gebeuren.

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

Nadat u deze stappen hebt uitgevoerd, hebt u het gedrag van een methode van het type private gewijzigd.

#### Wat met gebiedsvervanging kan worden veranderd

De openbare, beschermde, en privé methodes kunnen met gebiedsvervanging worden veranderd. Net als met een plug-in kunt u de argumenten wijzigen die worden ingevoerd, de functie volledig vervangen of de uitvoer van de functie wijzigen.

#### Wanneer om gebiedsvervanging te gebruiken

Dit is een goede eerste optie, wanneer het de gewenste doelstelling zou bereiken, ervan uitgaande dat er niets te ingewikkeld hoeft te gebeuren om te implementeren.

#### Nadelen

Niet veel. Het is niet bruikbaar in elke situatie. Het belangrijkste nadeel is dat u de originele klasse moet uitbreiden die de functionaliteit bevat u wilt wijzigen. Dat druist in tegen het beginsel van &quot;Samenstelling over Overerving&quot;.
