---
source-git-commit: 24c075622b569948292ca09136d4ac9225f33c18
workflow-type: tm+mt
source-wordcount: '1994'
ht-degree: 0%

---
# Adobe Commerce met B2B-pakketten

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/b2b/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/b2b/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce-b2b` value from the _data/names.yml file
 -->

B2B voor Adobe Commerce gebruikt Composer om PHP-pakketten te beheren.

De `composer.json` het bestand de lijst met pakketten declareert, terwijl het bestand `composer.lock` slaat een volledige lijst van de pakketten (een volledige versie van elk pakket en zijn gebiedsdelen) op die wordt gebruikt om een installatie van B2B voor Adobe Commerce te bouwen.

De volgende referentiedocumentatie wordt gegenereerd op basis van de `composer.lock` en omvat de vereiste pakketten in B2B voor Adobe Commerce 1.4.2.

## Afhankelijkheden

`magento/extension-b2b 1.4.2` heeft de volgende afhankelijkheden:

```config
magento/framework: >=103.0.6 <=103.0.7
magento/magento2-b2b-base: 1.4.2
magento/module-b2b: 100.4.1
magento/module-bundle-negotiable-quote: 100.4.0
magento/module-bundle-requisition-list: 100.4.0
magento/module-bundle-requisition-list-graph-ql: 1.4.0
magento/module-bundle-shared-catalog: 100.4.0
magento/module-checkout-address-search-negotiable-quote: 100.4.1
magento/module-checkout-agreements-negotiable-quote: 100.4.0
magento/module-checkout-agreements-purchase-order: 1.4.0
magento/module-company: 101.2.1
magento/module-company-credit: 100.4.0
magento/module-company-credit-graph-ql: 1.4.0
magento/module-company-graph-ql: 1.4.0
magento/module-company-payment: 100.4.0
magento/module-company-shipping: 1.4.0
magento/module-configurable-negotiable-quote: 100.4.0
magento/module-configurable-requisition-list: 100.4.1
magento/module-configurable-requisition-list-graph-ql: 1.4.0
magento/module-configurable-shared-catalog: 100.4.0
magento/module-downloadable-requisition-list-graph-ql: 1.4.0
magento/module-gift-card-negotiable-quote: 100.4.0
magento/module-gift-card-requisition-list: 100.4.0
magento/module-gift-card-requisition-list-graph-ql: 1.4.0
magento/module-gift-card-shared-catalog: 100.4.0
magento/module-grouped-requisition-list: 100.4.0
magento/module-grouped-shared-catalog: 100.4.0
magento/module-negotiable-quote: 100.4.2
magento/module-negotiable-quote-async-order: 1.4.1
magento/module-negotiable-quote-graph-ql: 1.4.0
magento/module-negotiable-quote-shared-catalog: 100.4.1
magento/module-negotiable-quote-weee: 100.4.1
magento/module-order-history-search: 100.4.2
magento/module-paypal-negotiable-quote: 1.4.1
magento/module-paypal-purchase-order: 1.4.0
magento/module-purchase-order: 100.4.1
magento/module-purchase-order-graph-ql: 1.4.0
magento/module-purchase-order-rule: 100.4.0
magento/module-purchase-order-rule-graph-ql: 1.4.0
magento/module-quick-order: 100.4.0
magento/module-quick-order-graph-ql: 1.4.0
magento/module-requisition-list: 100.4.1
magento/module-requisition-list-graph-ql: 1.4.0
magento/module-shared-catalog: 100.4.1
magento/module-shared-catalog-graph-ql: 1.4.0
magento/security-package-b2b: 1.0.4
```

## Licenties van derden

### Apache-2.0, alleen LGPL-2.1

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git">elasticsearch/elasticsearch</a>
    </td>
    <td>bibliotheek</td>
    <td>PHP-client voor Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git">openssearch-project/openssearch-php</a>
    </td>
    <td>bibliotheek</td>
    <td>PHP-client voor OpenSearch</td>
  </tr>
  </tbody>
</table>

### Apache-2.0

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/adobe/stock-api-libphp.git">astock/stock-api-libphp</a>
    </td>
    <td>bibliotheek</td>
    <td>Adobe Stock API-bibliotheek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git">aws/aws-crt-php</a>
    </td>
    <td>bibliotheek</td>
    <td>AWS Common Runtime voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git">aws/aws-sdk-php</a>
    </td>
    <td>bibliotheek</td>
    <td>AWS SDK voor PHP - Amazon Web Services gebruiken in uw PHP project</td>
  </tr>
  <tr>
    <td>
      paypal/module-breintree
    </td>
    <td>pakket</td>
    <td>Magento Braintree</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php.git">wikimedia/less.php</a>
    </td>
    <td>bibliotheek</td>
    <td>PHP poort van de LESS processor</td>
  </tr>
  </tbody>
</table>

### BSD-2-Clause

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/Bacon/BaconQrCode.git">bacon/bacon-qr-code</a>
    </td>
    <td>bibliotheek</td>
    <td>BaconQrCode is een QR code generator voor PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git">dasprid/enum</a>
    </td>
    <td>bibliotheek</td>
    <td>PHP 7.1 enum implementatie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git">webimpress/safe-writer</a>
    </td>
    <td>bibliotheek</td>
    <td>Gereedschap om bestanden veilig te schrijven om rasomstandigheden te voorkomen</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git">colinmolenhour/cache-back-end file</a>
    </td>
    <td>magento-module</td>
    <td>De stock Zend_Cache_Backend_File achtergrond heeft uiterst slechte prestaties voor schoonmaken door markeringen die het onbruikbaar maken maken aangezien het aantal caching punten stijgt. Deze backend brengt vele veranderingen met zich mee die in een enorme prestatiesverhoging, vooral voor markeringszuivering resulteren.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git">colinmolenhour/php-redis-session-abstract</a>
    </td>
    <td>bibliotheek</td>
    <td>Een op Redis gebaseerde sessiehandler met optimistische vergrendeling</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git">vuurbase/php-jwt</a>
    </td>
    <td>bibliotheek</td>
    <td>Een eenvoudige bibliotheek voor het coderen en decoderen van JSON Web Tokens (JWT) in PHP. Moet in overeenstemming zijn met de huidige specificatie.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git">google/recaptcha</a>
    </td>
    <td>bibliotheek</td>
    <td>Clientbibliotheek voor reCAPTCHA, een gratis service die websites beschermt tegen spam en misbruik.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git">laminas/laminas-captcha</a>
    </td>
    <td>bibliotheek</td>
    <td>CAPTCHA's genereren en valideren met behulp van figuren, afbeeldingen, ReCaptcha en meer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git">laminas/laminas-code</a>
    </td>
    <td>bibliotheek</td>
    <td>Extensies voor de PHP Reflectie-API, scannen van statische code en genereren van code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git">laminas/laminas-config</a>
    </td>
    <td>bibliotheek</td>
    <td>biedt een geneste, op objecteigenschappen gebaseerde gebruikersinterface voor toegang tot deze configuratiegegevens binnen de toepassingscode</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git">laminas/laminas-crypt</a>
    </td>
    <td>bibliotheek</td>
    <td>Krachtige cryptografie en wachtwoordhashing</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git">laminas/laminas-db</a>
    </td>
    <td>bibliotheek</td>
    <td>De abstractielaag van het gegevensbestand, SQL abstractie, resultaatvastgestelde abstractie, en implementaties RowDataGateway en TableDataGateway</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git">laminas/laminas-di</a>
    </td>
    <td>bibliotheek</td>
    <td>Geautomatiseerde afhankelijkheidsinjectie voor PSR-11 containers</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">laminas/laminas-escaper</a>
    </td>
    <td>bibliotheek</td>
    <td>U kunt veilig ontsnappen aan HTML-, HTML-kenmerken, JavaScript-, CSS- en URL's</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git">laminas/laminas-eventmanager</a>
    </td>
    <td>bibliotheek</td>
    <td>Trigger en luister naar gebeurtenissen in een PHP-toepassing</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git">laminas/diervoeder voor laminas</a>
    </td>
    <td>bibliotheek</td>
    <td>biedt functionaliteit voor het maken en gebruiken van RSS- en Atom-feeds</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git">laminas/laminas-file</a>
    </td>
    <td>bibliotheek</td>
    <td>PHP-lesbestanden zoeken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git">laminas/laminas-filter</a>
    </td>
    <td>bibliotheek</td>
    <td>Gegevens en bestanden programmatisch filteren en normaliseren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git">laminas/laminas-http</a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt een eenvoudige interface voor het uitvoeren van HTTP-aanvragen (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git">laminas/laminas-i18n</a>
    </td>
    <td>bibliotheek</td>
    <td>Vertaal uw toepassing en filtert en valideert geïnternationaliseerde waarden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git">laminas/laminas-json</a>
    </td>
    <td>bibliotheek</td>
    <td>biedt gebruiksvriendelijke methoden voor het serialiseren van native PHP naar JSON en het decoderen van JSON naar native PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git">laminas/laminas-loader</a>
    </td>
    <td>bibliotheek</td>
    <td>Laden van autoloading en plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git">laminas/laminas-mail</a>
    </td>
    <td>bibliotheek</td>
    <td>Verstrekt algemene functionaliteit om zowel tekst als MIME-Volgzame meerdelige e-mailberichten samen te stellen en te verzenden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git">laminas/laminas-math</a>
    </td>
    <td>bibliotheek</td>
    <td>Cryptografisch veilige pseudo-willekeurige getallen maken en grote gehele getallen beheren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git">laminas/laminas-mime</a>
    </td>
    <td>bibliotheek</td>
    <td>MIME-berichten en -onderdelen maken en parseren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git">laminas/laminas-modulemanager</a>
    </td>
    <td>bibliotheek</td>
    <td>Modulair toepassingssysteem voor laminas-mvc-toepassingen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git">laminas/laminas-mvc</a>
    </td>
    <td>bibliotheek</td>
    <td>De gebeurtenis-gedreven laag MVC van Laminas, met inbegrip van Toepassingen MVC, Controllers, en Insteekmodules</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git">laminas/laminas-oauth</a>
    </td>
    <td>bibliotheek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git">laminas/laminas-permissions-acl</a>
    </td>
    <td>bibliotheek</td>
    <td>Verstrekt een lichtgewichten flexibele implementatie van de toegangsbeheerlijst (ACL) voor toegangsbeheer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git">laminas/laminas-recaptcha</a>
    </td>
    <td>bibliotheek</td>
    <td>OOP-wrapper voor de ReCaptcha-webservice</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git">laminas/laminas-router</a>
    </td>
    <td>bibliotheek</td>
    <td>Flexibel verpletterend systeem voor HTTP en consoletoepassingen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
    </td>
    <td>bibliotheek</td>
    <td>Op reflectie gebaseerde RPC-servers maken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git">laminas/laminas-servicemanager</a>
    </td>
    <td>bibliotheek</td>
    <td>In de fabriek aangebrachte afhankelijkheidsinjectiecontainer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git">laminas/laminas-sessie</a>
    </td>
    <td>bibliotheek</td>
    <td>Object-oriented interface aan PHP zittingen en opslag</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git">laminas/laminas-soap</a>
    </td>
    <td>bibliotheek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git">laminas/laminas-stdlib</a>
    </td>
    <td>bibliotheek</td>
    <td>SPL-extensies, arrayhulpprogramma's, fouthandlers en meer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git">laminas/laminas-text</a>
    </td>
    <td>bibliotheek</td>
    <td>FIGlets en op tekst gebaseerde tabellen maken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git">laminas/laminas-uri</a>
    </td>
    <td>bibliotheek</td>
    <td>Een component die helpt bij het manipuleren en valideren van URI's (Uniform Resource Identifiers)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git">laminas/laminas-validator</a>
    </td>
    <td>bibliotheek</td>
    <td>Validatieklassen voor een groot aantal domeinen en de mogelijkheid om validators te ketenen om complexe validatiecriteria te maken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git">laminas/laminasweergave</a>
    </td>
    <td>bibliotheek</td>
    <td>Flexibele weergavelaag die meerdere weergavelagen, hulplijnen en meer ondersteunt en biedt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git">nikic/php-parser</a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP parser geschreven in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git">tedivm/jkrimpink</a>
    </td>
    <td>bibliotheek</td>
    <td>Javascript Minifier geïntegreerd in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git">tubalmartin/cssmin</a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP-poort van de YUI CSS-compressor</td>
  </tr>
  </tbody>
</table>

### BSD-3-Clause-Modification

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git">colinmolenhour/cache-backend-redis</a>
    </td>
    <td>magento-module</td>
    <td>Zend_Cache backend met Redis met volledige ondersteuning voor tags.</td>
  </tr>
  </tbody>
</table>

### ISC

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/paragonie/sodium_compat.git">paragonie/natrium_compat</a>
    </td>
    <td>bibliotheek</td>
    <td>Puur PHP implementatie van libnatrium; gebruikt de PHP extensie als deze bestaat</td>
  </tr>
  </tbody>
</table>

### LGPL-2.1 of hoger

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/ezyang/htmlpurifier.git">ezyang/htmlpurifier</a>
    </td>
    <td>bibliotheek</td>
    <td>HTML-filter voldoet aan standaarden geschreven in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git">php-amqplib/php-amqplib</a>
    </td>
    <td>bibliotheek</td>
    <td>Vroeger videlalvaro/php-amqplib.  Deze bibliotheek is een pure PHP-implementatie van het AMQP-protocol. Het is getest op RabbitMQ.</td>
  </tr>
  </tbody>
</table>

### MIT

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/braintree/braintree_php.git">hersenboom/hersenboom_php</a>
    </td>
    <td>bibliotheek</td>
    <td>Braintree PHP-clientbibliotheek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git">steen/wiskunde</a>
    </td>
    <td>bibliotheek</td>
    <td>Rekenkundige bibliotheek met willekeurige precisie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">baksteen/varexporter</a>
    </td>
    <td>bibliotheek</td>
    <td>Een krachtig alternatief voor var_export(), dat sluitingen en objecten zonder __set_state() kan exporteren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git">christian-riesen/base32</a>
    </td>
    <td>bibliotheek</td>
    <td>Base32 encoder/decoder volgens RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git">colinmolenuur/credits</a>
    </td>
    <td>bibliotheek</td>
    <td>Credis is een lichtgewicht interface naar de sleutelwaardewinkel van Redis, waar de phpredis-bibliotheek wordt geplaatst als deze beschikbaar is voor betere prestaties.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git">composer/ca-bundle</a>
    </td>
    <td>bibliotheek</td>
    <td>Hier vindt u een pad naar de CA-bundel van het systeem en een fallback naar de Mozilla CA-bundel.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git">composer/class-map-generator</a>
    </td>
    <td>bibliotheek</td>
    <td>Hulpprogramma's voor het scannen van PHP-code en het genereren van klassenkaarten.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git">composer/composer</a>
    </td>
    <td>bibliotheek</td>
    <td>Met Composer kunt u afhankelijkheden van PHP-projecten declareren, beheren en installeren. Zo weet u zeker dat u overal de juiste stapel hebt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git">composer/metadata-minifier</a>
    </td>
    <td>bibliotheek</td>
    <td>Kleine nutsbibliotheek die meta-gegevensminificatie en uitbreiding behandelt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git">composer/pcre</a>
    </td>
    <td>bibliotheek</td>
    <td>PCRE-wrapping-bibliotheek met type-veilige preg_* vervangingen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git">componist/semver</a>
    </td>
    <td>bibliotheek</td>
    <td>Semverbibliotheek met hulpprogramma's, parsering en validatie van versiebeperkingen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git">componist/spdx-licenties</a>
    </td>
    <td>bibliotheek</td>
    <td>Lijst met SPDX-licenties en validatiebibliotheek.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git">composer/xdebug-handler</a>
    </td>
    <td>bibliotheek</td>
    <td>Start een proces zonder Xdebug opnieuw.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">endroid/qr-code</a>
    </td>
    <td>bibliotheek</td>
    <td>QR-code van Endroid</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git">ezimuel/guzzlestreams</a>
    </td>
    <td>bibliotheek</td>
    <td>Vork van guzzle/streams (verlaten) voor gebruik met elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git">ezimuel/ringphp</a>
    </td>
    <td>bibliotheek</td>
    <td>Vork van guzzle/RingPHP (verlaten) voor gebruik met elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git">guzzlehttp:</a>
    </td>
    <td>bibliotheek</td>
    <td>Guzzle is een PHP HTTP client library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git">guzzlehttp:</a>
    </td>
    <td>bibliotheek</td>
    <td>Guzzle belooft library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git">guzzlehttp/psr7</a>
    </td>
    <td>bibliotheek</td>
    <td>PSR-7 berichtimplementatie die ook gemeenschappelijke nutsmethodes verstrekt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/justinrainbow/json-schema.git">justinrainbow/json-schema</a>
    </td>
    <td>bibliotheek</td>
    <td>Een bibliotheek om een jseschema te valideren.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git">liga/vliegsysteem</a>
    </td>
    <td>bibliotheek</td>
    <td>Abstractie van bestandsopslag voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">liga/flysystem-aws-s3-v3</a>
    </td>
    <td>bibliotheek</td>
    <td>AWS S3-bestandssysteemadapter voor Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git">liga/mime-type-detectie</a>
    </td>
    <td>bibliotheek</td>
    <td>MIME-typedetectie voor Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git">monoloog/monoloog</a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee verzendt u uw logbestanden naar bestanden, sockets, inboxen, databases en verschillende webservices</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git">mtdowling/jmespath.php</a>
    </td>
    <td>bibliotheek</td>
    <td>Declaratief opgeven hoe elementen uit een JSON-document worden geëxtraheerd</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git">paragonie/constante_time_encoding</a>
    </td>
    <td>bibliotheek</td>
    <td>Constante-tijdImplementaties van Codering RFC 4648 (basis-64, basis-32, basis-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git">paragonie/random_compat</a>
    </td>
    <td>bibliotheek</td>
    <td>PHP 5.x polyfill for random_bytes() en random_int() van PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">pelago/emogrifier</a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee converteert u CSS-stijlen naar inline-stijlkenmerken in uw HTML-code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git">phpgt/cssxpath</a>
    </td>
    <td>bibliotheek</td>
    <td>CSS-kiezers converteren naar XPath-query's.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
    </td>
    <td>bibliotheek</td>
    <td>Moderne DOM API.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc.git">phpgt/propfunc</a>
    </td>
    <td>bibliotheek</td>
    <td>Functies van accessoreigenschap en mutator.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git">phpseclib/mcrypt_compat</a>
    </td>
    <td>bibliotheek</td>
    <td>PHP 5.x-8.x polyfill for mcrypt extension</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git">phpseclib/phpseclib</a>
    </td>
    <td>bibliotheek</td>
    <td>PHP Secure Communications Library - Pure-PHP implementaties van RSA, AES, SSH2, SFTP, X.509 enz.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git">psr/klok</a>
    </td>
    <td>bibliotheek</td>
    <td>Gemeenschappelijke interface voor het lezen van de klok.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git">psr/container</a>
    </td>
    <td>bibliotheek</td>
    <td>Common Container Interface (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git">psr/event-dispatcher</a>
    </td>
    <td>bibliotheek</td>
    <td>Standaardinterfaces voor gebeurtenisafhandeling.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git">psr/http-client</a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene interface voor HTTP-clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git">psr/http-factory</a>
    </td>
    <td>bibliotheek</td>
    <td>Gemeenschappelijke interfaces voor PSR-7 HTTP- berichtfabrieken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-message</a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene interface voor HTTP-berichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git">psr/log</a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene interface voor logbibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git">ralouphie/getallheaders</a>
    </td>
    <td>bibliotheek</td>
    <td>Een polyfill voor getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git">ramsey/collectie</a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP-bibliotheek voor het weergeven en manipuleren van verzamelingen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git">ramsey/uuid</a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP-bibliotheek voor het genereren en gebruiken van universeel unieke id's (UUID's).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git">reageren/beloven</a>
    </td>
    <td>bibliotheek</td>
    <td>Een lichte implementatie van CommonJS Promises/A voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git">sabberworm/php-css-parser</a>
    </td>
    <td>bibliotheek</td>
    <td>Parser voor CSS-bestanden geschreven in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git">seld/jsonlint</a>
    </td>
    <td>bibliotheek</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git">seld/phhar-utils</a>
    </td>
    <td>bibliotheek</td>
    <td>Hulpprogramma's voor PHAR-bestandsindelingen, bijvoorbeeld wanneer PHP je opbelt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/signaalhandler</a>
    </td>
    <td>bibliotheek</td>
    <td>Eenvoudige unix signaalmanager die ongemerkt ontbreekt waar de signalen niet voor gemakkelijke dwars-platformontwikkeling worden gesteund</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git">spomky-labs/aes-key-wrap</a>
    </td>
    <td>bibliotheek</td>
    <td>AES Key Wrap voor PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git">spomky-labs/otphp</a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP bibliotheek voor het produceren van één tijdwachtwoorden volgens RFC 4226 (het Algoritme van HOTP) en RFC 6238 (TOTP Algorithm) en compatibel met de Authenticator van Google</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git">spomky-labs/pki-framework</a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP-framework voor het beheren van infrastructuur voor openbare sleutels. Het omvat X.509 openbare zeer belangrijke certificaten, attributencertificaten, certificatieverzoeken en certificatiewegbevestiging.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git">symfony/config</a>
    </td>
    <td>bibliotheek</td>
    <td>Helpt u configuratiewaarden van om het even welke aard te vinden, te laden, te combineren, automatisch te vullen en te bevestigen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git">symfony/console</a>
    </td>
    <td>bibliotheek</td>
    <td>Versnelt het creëren van mooie en testable bevellijninterfaces</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git">symfony/css-selector</a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee converteert u CSS-kiezers naar XPath-expressies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git">symfony/verslaving-injectie</a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee kunt u de manier waarop objecten in uw toepassing worden gemaakt standaardiseren en centraliseren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git">symfony/verval-contracten</a>
    </td>
    <td>bibliotheek</td>
    <td>Een algemene functie en conventie voor het activeren van plaatsingsberichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git">symfony/error-handler</a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt tools om fouten te beheren en foutopsporing in PHP-code te vereenvoudigen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git">symfony/event-dispatcher</a>
    </td>
    <td>bibliotheek</td>
    <td>Verstrekt hulpmiddelen die uw toepassingscomponenten toestaan om met elkaar te communiceren door gebeurtenissen te verzenden en aan hen te luisteren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git">symfony/event-dispatcher-Contracts</a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene abstracties met betrekking tot verzendgebeurtenis</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git">symfony/filesystem</a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt basisfuncties voor het bestandssysteem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git">symfony/finder</a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee zoekt u bestanden en mappen via een intuïtieve fluent-interface</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client.git">symfony/http-client</a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt krachtige methoden om HTTP-bronnen synchroon of asynchroon op te halen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git">symfony/http-client-Contracts</a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene abstracties met betrekking tot HTTP-clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git">symfony/http-foundation</a>
    </td>
    <td>bibliotheek</td>
    <td>Definieert een objectgeoriënteerde laag voor de HTTP-specificatie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git">symfony/http-kernel</a>
    </td>
    <td>bibliotheek</td>
    <td>Verstrekt een gestructureerd proces om een Verzoek in een Reactie om te zetten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">symfony/intl</a>
    </td>
    <td>bibliotheek</td>
    <td>Verleent toegang tot de localisatiegegevens van de bibliotheek ICU</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git">symfony/polyfill-type</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor tekstfuncties</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git">symfony/polyfill-intl-grapheme</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor de functies grapheme_* van intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git">symfony/polyfill-intl-idn</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor de functies idn_to_ascii en idn_to_utf8</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git">symfony/polyfill-intl-normalizer</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor de klasse Normalizer van intl en verwante functies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git">symfony/polyfill-mbstring</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor de extensie Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git">symfony/polyfill-php72</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 7.2+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git">symfony/polyfill-php73</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 7.3+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git">symfony/polyfill-php80</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.0+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git">symfony/polyfill-php81</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.1+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git">symfony/polyfill-php83</a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.3+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git">symfonie/proces</a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee voert u opdrachten uit in subprocessen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git">symfony/dienstverleningscontracten</a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene abstracties met betrekking tot schrijfdiensten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git">symfony/tekenreeks</a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt een objectgeoriënteerde API voor tekenreeksen en behandelt bytes, UTF-8-codepunten en grafeemclusters op een uniforme manier</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git">symfony/var-dumper</a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt mechanismen om willekeurige PHP variabelen te doorlopen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git">symfony/var-exporter</a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee wordt het exporteren van eventuele serialiseerbare PHP-gegevensstructuur naar normale PHP-code toegestaan</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git">web-token/jwt-framework</a>
    </td>
    <td>symfony-bundel</td>
    <td>JSON Object Signing and Encryption library for PHP and Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git">webmozart/assert</a>
    </td>
    <td>bibliotheek</td>
    <td>Bevestigingen om methodeinput/output met aardige foutenmeldingen te bevestigen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git">webonyx/graphql-php</a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP-poort van GraphQL referentie-implementatie</td>
  </tr>
  </tbody>
</table>

### OSL-3.0, AFL-3.0

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-breintree-customer-balance
    </td>
    <td>magento2-module</td>
    <td>NVT</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>magento2-module</td>
    <td>NVT</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>magento2-module</td>
    <td>NVT</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>NVT</td>
  </tr>
  </tbody>
</table>

### OSL-3.0

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### PHP

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      <a href="https://github.com/2tvenom/CBOREncode.git">2tvenom/cancode</a>
    </td>
    <td>bibliotheek</td>
    <td>CBOR encoder voor PHP</td>
  </tr>
  </tbody>
</table>

### Eigen

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>

### bedrijfseigen

<table>
  <thead>
    <tr>
      <th>Naam</th>
      <th>Type</th>
      <th>Beschrijving</th>
    </tr>
  </thead>
  <tbody>
  <tr>
    <td>
      paypal/module-breintree-core
    </td>
    <td>magento2-module</td>
    <td>Vork uit de Magento Braintree 2.2.0 module door Gene Commerce for PayPal.</td>
  </tr>
  </tbody>
</table>
