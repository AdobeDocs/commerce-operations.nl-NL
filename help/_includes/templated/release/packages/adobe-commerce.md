---
source-git-commit: 1f8fda87e0d39fdcf2372f72373a0b2ea486d25a
workflow-type: tm+mt
source-wordcount: '1996'
ht-degree: 0%

---
# Adobe Commerce-pakketten

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/commerce/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-enterprise-edition' package
 -->

<!-- The edition variable contains `commerce` value from the _data/names.yml file
 -->

Adobe Commerce gebruikt Composer om PHP-pakketten te beheren.

In het bestand `composer.json` wordt de lijst met pakketten gedeclareerd, terwijl in het bestand van `composer.lock` een volledige lijst met pakketten (een volledige versie van elk pakket en de bijbehorende afhankelijkheden) is opgeslagen die zijn gebruikt om een installatie van Adobe Commerce te maken.

De volgende referentiedocumentatie wordt gegenereerd uit het `composer.lock` -bestand en omvat de vereiste pakketten die zijn opgenomen in Adobe Commerce 2.4.7-p1.

## Afhankelijkheden

`magento/product-enterprise-edition 2.4.7-p1` heeft de volgende afhankelijkheden:

```config
adobe-commerce/extensions-metapackage: ~2.0
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.16
colinmollenhour/credis: ^1.15
colinmollenhour/php-redis-session-abstract: ~1.5.3
composer/composer: ^2.0, !=2.2.16
elasticsearch/elasticsearch: ~7.17.0 || ~8.5.0
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-gd: *
ext-hash: *
ext-iconv: *
ext-intl: *
ext-mbstring: *
ext-openssl: *
ext-pdo_mysql: *
ext-simplexml: *
ext-soap: *
ext-sodium: *
ext-spl: *
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.17
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.17
laminas/laminas-code: ^4.13
laminas/laminas-db: ^2.19
laminas/laminas-di: ^3.13
laminas/laminas-escaper: ^2.13
laminas/laminas-eventmanager: ^3.11
laminas/laminas-feed: ^2.22
laminas/laminas-file: ^2.13
laminas/laminas-filter: ^2.33
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-mail: ^2.16
laminas/laminas-mime: ^2.9
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.6
laminas/laminas-oauth: ^2.6
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-server: ^2.16
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^2.4
league/flysystem-aws-s3-v3: ^2.4
lib-libxml: *
magento/composer: ^1.10.0-beta1
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework-foreign-key: 100.4.6
magento/magento-composer-installer: >=0.4.0
magento/magento2-ee-base: 2.4.7-p1
magento/module-admin-gws: 100.4.7
magento/module-admin-gws-configurable-product: 100.4.4
magento/module-admin-gws-staging: 100.4.4
magento/module-advanced-catalog: 100.4.4
magento/module-advanced-checkout: 100.4.7
magento/module-advanced-rule: 100.4.4
magento/module-advanced-sales-rule: 100.4.4
magento/module-application-server: 100.4.0
magento/module-application-server-new-relic: 100.4.0
magento/module-application-server-performance-monitor: 100.4.0
magento/module-application-server-state-monitor: 100.4.0
magento/module-application-server-state-monitor-graph-ql: 100.4.0
magento/module-async-order: 100.4.3
magento/module-async-order-graph-ql: 100.4.2
magento/module-aws-s3-customer-custom-attributes: 100.4.4
magento/module-aws-s3-gift-card-import-export: 100.4.4
magento/module-aws-s3-scheduled-import-export: 100.4.4
magento/module-banner: 101.2.7
magento/module-banner-customer-segment: 100.4.5
magento/module-banner-graph-ql: 100.4.3
magento/module-banner-staging: 100.4.1
magento/module-bundle-import-export-staging: 100.4.4
magento/module-bundle-staging: 100.4.7
magento/module-catalog-event: 101.1.6
magento/module-catalog-import-export-staging: 100.4.4
magento/module-catalog-inventory-staging: 100.4.5
magento/module-catalog-permissions: 100.4.7
magento/module-catalog-permissions-graph-ql: 100.4.5
magento/module-catalog-rule-staging: 100.4.7
magento/module-catalog-staging: 100.4.7
magento/module-catalog-staging-graph-ql: 100.4.6
magento/module-catalog-url-rewrite-staging: 100.4.6-p1
magento/module-checkout-address-search: 100.4.6
magento/module-checkout-address-search-gift-registry: 100.4.3
magento/module-checkout-staging: 100.4.6
magento/module-cms-staging: 100.4.7
magento/module-configurable-product-staging: 100.4.6
magento/module-custom-attribute-management: 100.4.6
magento/module-customer-balance: 100.4.7
magento/module-customer-balance-graph-ql: 100.4.4
magento/module-customer-custom-attributes: 100.4.7
magento/module-customer-custom-attributes-graph-ql: 100.4.0
magento/module-customer-finance: 100.4.4
magento/module-customer-segment: 102.1.7
magento/module-customer-segment-graph-ql: 100.4.0
magento/module-deferred-total-calculating: 100.4.2
magento/module-downloadable-staging: 100.4.6
magento/module-elasticsearch-catalog-permissions: 100.4.3
magento/module-elasticsearch-catalog-permissions-graph-ql: 100.4.2
magento/module-enterprise: 100.4.5
magento/module-gift-card: 101.3.7
magento/module-gift-card-account: 101.2.7
magento/module-gift-card-account-graph-ql: 100.4.5
magento/module-gift-card-graph-ql: 100.4.7
magento/module-gift-card-import-export: 100.4.4
magento/module-gift-card-staging: 100.4.4
magento/module-gift-message-staging: 100.4.4
magento/module-gift-registry: 101.2.7
magento/module-gift-registry-graph-ql: 100.4.3
magento/module-gift-wrapping: 101.2.6
magento/module-gift-wrapping-graph-ql: 100.4.4
magento/module-gift-wrapping-staging: 100.4.4
magento/module-google-optimizer-staging: 100.4.4
magento/module-google-tag-manager: 100.4.7
magento/module-grouped-product-staging: 100.4.5
magento/module-import-csv: 100.4.1
magento/module-import-csv-api: 100.4.1
magento/module-import-json: 100.4.0
magento/module-import-json-api: 100.4.0
magento/module-invitation: 100.4.6
magento/module-layered-navigation-staging: 100.4.4
magento/module-logging: 101.2.7
magento/module-login-as-customer-logging: 100.4.7
magento/module-login-as-customer-website-restriction: 100.4.5
magento/module-media-content-catalog-staging: 100.4.4
magento/module-msrp-staging: 100.4.5
magento/module-multicoupon: 100.4.0
magento/module-multicoupon-graph-ql: 100.4.0
magento/module-multicoupon-ui: 100.4.0
magento/module-multiple-wishlist: 100.4.7
magento/module-multiple-wishlist-graph-ql: 100.4.3
magento/module-payment-staging: 100.4.4
magento/module-persistent-history: 100.4.4
magento/module-price-permissions: 100.4.3
magento/module-product-video-staging: 100.4.4
magento/module-promotion-permissions: 100.4.4
magento/module-quote-commerce-graph-ql: 100.4.0
magento/module-quote-gift-card-options: 100.4.4
magento/module-quote-staging: 100.4.4
magento/module-reminder: 101.2.6
magento/module-remote-storage-commerce: 100.4.3
magento/module-resource-connections: 100.4.4
magento/module-review-staging: 100.4.4
magento/module-reward: 101.2.7
magento/module-reward-graph-ql: 100.4.6
magento/module-reward-staging: 100.4.4
magento/module-rma: 101.2.7
magento/module-rma-graph-ql: 100.4.6-p1
magento/module-rma-staging: 100.4.4
magento/module-sales-archive: 101.0.5
magento/module-sales-rule-staging: 100.4.6
magento/module-scalable-checkout: 100.4.6
magento/module-scalable-inventory: 100.4.5
magento/module-scalable-oms: 100.4.5
magento/module-scheduled-import-export: 101.2.7
magento/module-search-staging: 100.4.5
magento/module-staging: 101.2.7
magento/module-staging-graph-ql: 100.4.4
magento/module-support: 101.2.6
magento/module-swat: 100.4.5
magento/module-target-rule: 101.2.7
magento/module-target-rule-graph-ql: 100.4.4
magento/module-versions-cms: 101.2.7
magento/module-versions-cms-page-cache: 100.4.3
magento/module-versions-cms-url-rewrite: 100.4.5
magento/module-versions-cms-url-rewrite-graph-ql: 100.4.3
magento/module-visual-merchandiser: 100.4.7
magento/module-website-restriction: 100.4.6
magento/module-weee-staging: 100.4.4
magento/module-wishlist-gift-card: 100.4.3
magento/module-wishlist-gift-card-graph-ql: 100.4.3
magento/page-builder-commerce: 1.7.4-p1
magento/product-community-edition: 2.4.7-p1
magento/security-package-ee: 1.0.2-p1
magento/theme-adminhtml-spectrum: 100.4.2
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^2.7
opensearch-project/opensearch-php: ^1.0 || ^2.0
pelago/emogrifier: ^7.0
php: ~8.1.0||~8.2.0||~8.3.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
psr/log: ^2 || ^3
ramsey/uuid: ^4.2
symfony/console: ^6.4
symfony/intl: ^6.4
symfony/process: ^6.4
symfony/string: ^6.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.1
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^3.2
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
      <a href="https://github.com/elastic/elasticsearch-php.git"> elasticsearch/elasticsearch </a>
    </td>
    <td>bibliotheek</td>
    <td>PHP-client voor Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opensearch-project/opensearch-php.git"> openssearch-project/openssearch-php </a>
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
      <a href="https://github.com/adobe/stock-api-libphp.git"> astock/stock-api-libphp </a>
    </td>
    <td>bibliotheek</td>
    <td>Adobe Stock API-bibliotheek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php.git"> aws/aws-crt-php </a>
    </td>
    <td>bibliotheek</td>
    <td>AWS Common Runtime voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php.git"> aws/aws-sdk-php </a>
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
      <a href="https://github.com/wikimedia/less.php.git"> wikimedia/less.php</a>
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
      <a href="https://github.com/Bacon/BaconQrCode.git"> bacon/bacon-qr-code </a>
    </td>
    <td>bibliotheek</td>
    <td>BaconQrCode is een QR code generator voor PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum.git"> dasprid/enum </a>
    </td>
    <td>bibliotheek</td>
    <td>PHP 7.1 enum implementatie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer.git"> webimpress/safe-writer </a>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File.git"> colinmelenhour/cache-back-end-file </a>
    </td>
    <td>magento-module</td>
    <td>De stock Zend_Cache_Backend_File achtergrond heeft uiterst slechte prestaties voor schoonmaken door markeringen die het onbruikbaar maken maken aangezien het aantal caching punten stijgt. Deze backend brengt vele veranderingen met zich mee die in een enorme prestatiesverhoging, vooral voor markeringszuivering resulteren.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract.git"> colinmolenhour/php-redis-session-abstract </a>
    </td>
    <td>bibliotheek</td>
    <td>Een op Redis gebaseerde sessiehandler met optimistische vergrendeling</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt.git"> firebase/php-jwt </a>
    </td>
    <td>bibliotheek</td>
    <td>Een eenvoudige bibliotheek voor het coderen en decoderen van JSON Web Tokens (JWT) in PHP. Moet in overeenstemming zijn met de huidige specificatie.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/google/recaptcha.git"> google/recaptcha </a>
    </td>
    <td>bibliotheek</td>
    <td>Clientbibliotheek voor reCAPTCHA, een gratis service die websites beschermt tegen spam en misbruik.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha.git"> laminas/laminas-captcha </a>
    </td>
    <td>bibliotheek</td>
    <td>CAPTCHA's genereren en valideren met behulp van figuren, afbeeldingen, ReCaptcha en meer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code.git"> laminas/laminas-code </a>
    </td>
    <td>bibliotheek</td>
    <td>Extensies voor de PHP Reflectie-API, scannen van statische code en genereren van code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config.git"> laminas/laminas-config </a>
    </td>
    <td>bibliotheek</td>
    <td>biedt een geneste, op objecteigenschappen gebaseerde gebruikersinterface voor toegang tot deze configuratiegegevens binnen de toepassingscode</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-crypt.git"> laminas/laminas-crypt </a>
    </td>
    <td>bibliotheek</td>
    <td>Krachtige cryptografie en wachtwoordhashing</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-db.git"> laminas/laminas-db </a>
    </td>
    <td>bibliotheek</td>
    <td>De abstractielaag van het gegevensbestand, SQL abstractie, resultaatvastgestelde abstractie, en implementaties RowDataGateway en TableDataGateway</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di.git"> laminas/laminas-di </a>
    </td>
    <td>bibliotheek</td>
    <td>Geautomatiseerde afhankelijkheidsinjectie voor PSR-11 containers</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git"> laminas/laminas-escaper </a>
    </td>
    <td>bibliotheek</td>
    <td>Veilig en veilig ontsnappen aan HTML, HTML-kenmerken, JavaScript, CSS en URL's</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager.git"> laminas/laminas-eventmanager </a>
    </td>
    <td>bibliotheek</td>
    <td>Trigger en luister naar gebeurtenissen in een PHP-toepassing</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed.git"> laminas/laminas-voer </a>
    </td>
    <td>bibliotheek</td>
    <td>biedt functionaliteit voor het maken en gebruiken van RSS- en Atom-feeds</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-file.git"> laminas/laminas-dossier </a>
    </td>
    <td>bibliotheek</td>
    <td>PHP-lesbestanden zoeken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter.git"> laminas/laminas-filter </a>
    </td>
    <td>bibliotheek</td>
    <td>Gegevens en bestanden programmatisch filteren en normaliseren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http.git"> laminas/laminas-http </a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt een eenvoudige interface voor het uitvoeren van HTTP-aanvragen (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n.git"> laminas/laminas-i18n </a>
    </td>
    <td>bibliotheek</td>
    <td>Vertaal uw toepassing en filtert en valideert geïnternationaliseerde waarden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json.git"> laminas/laminas-json </a>
    </td>
    <td>bibliotheek</td>
    <td>biedt gebruiksvriendelijke methoden voor het serialiseren van native PHP naar JSON en het decoderen van JSON naar native PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader.git"> laminas/laminas-loader </a>
    </td>
    <td>bibliotheek</td>
    <td>Laden van autoloading en plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mail.git"> laminas/laminas-mail </a>
    </td>
    <td>bibliotheek</td>
    <td>Verstrekt algemene functionaliteit om zowel tekst als MIME-Volgzame meerdelige e-mailberichten samen te stellen en te verzenden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-math.git"> laminas/laminas-math </a>
    </td>
    <td>bibliotheek</td>
    <td>Cryptografisch veilige pseudo-willekeurige getallen maken en grote gehele getallen beheren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mime.git"> laminas/laminas-mime </a>
    </td>
    <td>bibliotheek</td>
    <td>MIME-berichten en -onderdelen maken en parseren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager.git"> laminas/laminas-modulemanager </a>
    </td>
    <td>bibliotheek</td>
    <td>Modulair toepassingssysteem voor laminas-mvc-toepassingen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc.git"> laminas/laminas-mvc </a>
    </td>
    <td>bibliotheek</td>
    <td>De gebeurtenis-gedreven laag MVC van Laminas, met inbegrip van Toepassingen MVC, Controllers, en Insteekmodules</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-oauth.git"> laminas/laminas-oauth </a>
    </td>
    <td>bibliotheek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl.git"> laminas/laminas-permissions-acl </a>
    </td>
    <td>bibliotheek</td>
    <td>Verstrekt een lichtgewichten flexibele implementatie van de toegangsbeheerlijst (ACL) voor toegangsbeheer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha.git"> laminas/laminas-recaptcha </a>
    </td>
    <td>bibliotheek</td>
    <td>OOP-wrapper voor de ReCaptcha-webservice</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router.git"> laminas/laminas-router </a>
    </td>
    <td>bibliotheek</td>
    <td>Flexibel verpletterend systeem voor HTTP en consoletoepassingen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server.git"> laminas/laminas-server </a>
    </td>
    <td>bibliotheek</td>
    <td>Op reflectie gebaseerde RPC-servers maken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager.git"> laminas/laminas-servicemanager </a>
    </td>
    <td>bibliotheek</td>
    <td>In de fabriek aangebrachte afhankelijkheidsinjectiecontainer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session.git"> laminas/laminas-zitting </a>
    </td>
    <td>bibliotheek</td>
    <td>Object-oriented interface aan PHP zittingen en opslag</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap.git"> laminas/laminas-soap </a>
    </td>
    <td>bibliotheek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib.git"> laminas/laminas-stdlib </a>
    </td>
    <td>bibliotheek</td>
    <td>SPL-extensies, arrayhulpprogramma's, fouthandlers en meer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text.git"> laminas/laminas-text </a>
    </td>
    <td>bibliotheek</td>
    <td>FIGlets en op tekst gebaseerde tabellen maken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri.git"> laminas/laminas-uri </a>
    </td>
    <td>bibliotheek</td>
    <td>Een component die helpt bij het manipuleren en valideren van URI's (Uniform Resource Identifiers)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator.git"> laminas/laminas-validator </a>
    </td>
    <td>bibliotheek</td>
    <td>Validatieklassen voor een groot aantal domeinen en de mogelijkheid om validators te ketenen om complexe validatiecriteria te maken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view.git"> laminas/laminas-mening </a>
    </td>
    <td>bibliotheek</td>
    <td>Flexibele weergavelaag die meerdere weergavelagen, hulplijnen en meer ondersteunt en biedt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser.git"> nikic/php-parser </a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP parser geschreven in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink.git"> tedivm/jshrink </a>
    </td>
    <td>bibliotheek</td>
    <td>Javascript Minifier geïntegreerd in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port.git"> tubalmartin/cssmin </a>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis.git"> colinmolenhour/cache-backend-redis </a>
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
      <a href="https://github.com/paragonie/sodium_compat.git"> paragonie/natrium_compat </a>
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
      <a href="https://github.com/ezyang/htmlpurifier.git"> ezyang/htmlpurifier </a>
    </td>
    <td>bibliotheek</td>
    <td>HTML-filter voldoet aan standaarden geschreven in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib.git"> php-amqplib/php-amqplib </a>
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
      <a href="https://github.com/braintree/braintree_php.git"> breintree/braintree_php </a>
    </td>
    <td>bibliotheek</td>
    <td>Braintree PHP-clientbibliotheek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git"> steen/math </a>
    </td>
    <td>bibliotheek</td>
    <td>Rekenkundige bibliotheek met willekeurige precisie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git"> baksteen/varexporter </a>
    </td>
    <td>bibliotheek</td>
    <td>Een krachtig alternatief voor var_export(), dat sluitingen en objecten zonder __set_state() kan exporteren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32.git"> christian-riesen/base32 </a>
    </td>
    <td>bibliotheek</td>
    <td>Base32 encoder/decoder volgens RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis.git"> colinmolenhour/credits </a>
    </td>
    <td>bibliotheek</td>
    <td>Credis is een lichtgewicht interface naar de sleutelwaardewinkel van Redis, waar de phpredis-bibliotheek wordt geplaatst als deze beschikbaar is voor betere prestaties.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle.git"> composer/ca-bundle </a>
    </td>
    <td>bibliotheek</td>
    <td>Hier vindt u een pad naar de CA-bundel van het systeem en een fallback naar de Mozilla CA-bundel.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator.git"> composer/klasse-kaart-generator </a>
    </td>
    <td>bibliotheek</td>
    <td>Hulpprogramma's voor het scannen van PHP-code en het genereren van klassenkaarten.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer.git"> composer/composer </a>
    </td>
    <td>bibliotheek</td>
    <td>Met Composer kunt u afhankelijkheden van PHP-projecten declareren, beheren en installeren. Zo weet u zeker dat u overal de juiste stapel hebt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier.git"> composer/metadata-minifier </a>
    </td>
    <td>bibliotheek</td>
    <td>Kleine nutsbibliotheek die meta-gegevensminificatie en uitbreiding behandelt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre.git"> composer/pcre </a>
    </td>
    <td>bibliotheek</td>
    <td>PCRE-wrapping-bibliotheek met type-veilige preg_* vervangingen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver.git"> composer/semver </a>
    </td>
    <td>bibliotheek</td>
    <td>Semverbibliotheek met hulpprogramma's, parsering en validatie van versiebeperkingen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses.git"> composer/spdx-vergunningen </a>
    </td>
    <td>bibliotheek</td>
    <td>Lijst met SPDX-licenties en validatiebibliotheek.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler.git"> composer/xdebug-manager </a>
    </td>
    <td>bibliotheek</td>
    <td>Start een proces zonder Xdebug opnieuw.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git"> endroid/qr-code </a>
    </td>
    <td>bibliotheek</td>
    <td>QR-code van Endroid</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams.git"> ezimuel/guzzlestreams </a>
    </td>
    <td>bibliotheek</td>
    <td>Vork van guzzle/streams (verlaten) voor gebruik met elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp.git"> ezimuel/ringphp </a>
    </td>
    <td>bibliotheek</td>
    <td>Vork van guzzle/RingPHP (verlaten) voor gebruik met elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle.git"> guzzlehttp/guzzle </a>
    </td>
    <td>bibliotheek</td>
    <td>Guzzle is een PHP HTTP client library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises.git"> guzzlehttp/promise </a>
    </td>
    <td>bibliotheek</td>
    <td>Guzzle belooft library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7.git"> guzzlehttp/psr7 </a>
    </td>
    <td>bibliotheek</td>
    <td>PSR-7 berichtimplementatie die ook gemeenschappelijke nutsmethodes verstrekt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema.git"> justinrainbow/json-schema </a>
    </td>
    <td>bibliotheek</td>
    <td>Een bibliotheek om een jseschema te valideren.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem.git"> liga/vliegsysteem </a>
    </td>
    <td>bibliotheek</td>
    <td>Abstractie van bestandsopslag voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git"> liga/flysystem-ws-s3-v3 </a>
    </td>
    <td>bibliotheek</td>
    <td>AWS S3-bestandssysteemadapter voor Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection.git"> liga/mime-type-opsporing </a>
    </td>
    <td>bibliotheek</td>
    <td>MIME-typedetectie voor Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog.git"> monolog/monolog </a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee verzendt u uw logbestanden naar bestanden, sockets, inboxen, databases en verschillende webservices</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php.git"> mtdowling/jmespath.php</a>
    </td>
    <td>bibliotheek</td>
    <td>Declaratief opgeven hoe elementen uit een JSON-document worden geëxtraheerd</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding.git"> paragonie/constant_time_encoding </a>
    </td>
    <td>bibliotheek</td>
    <td>Constante-tijdImplementaties van Codering RFC 4648 (basis-64, basis-32, basis-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat.git"> paragonie/random_compat </a>
    </td>
    <td>bibliotheek</td>
    <td>PHP 5.x polyfill for random_bytes() en random_int() van PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git"> pelago/emogrifier </a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee converteert u CSS-stijlen naar inline-stijlkenmerken in uw HTML-code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath.git"> phpgt/cssxpath </a>
    </td>
    <td>bibliotheek</td>
    <td>CSS-kiezers converteren naar XPath-query's.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom.git"> phpgt/dom </a>
    </td>
    <td>bibliotheek</td>
    <td>Moderne DOM API.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc.git"> phpgt/propfunc </a>
    </td>
    <td>bibliotheek</td>
    <td>Functies van accessoreigenschap en mutator.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat.git"> phpseclib/mcrypt_compat </a>
    </td>
    <td>bibliotheek</td>
    <td>PHP 5.x-8.x polyfill for mcrypt extension</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib.git"> phpseclib/phpseclib </a>
    </td>
    <td>bibliotheek</td>
    <td>PHP Secure Communications Library - Pure-PHP implementaties van RSA, AES, SSH2, SFTP, X.509 enz.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache.git"> psr/cache </a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene interface voor het in cache plaatsen van bibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock.git"> psr/klok </a>
    </td>
    <td>bibliotheek</td>
    <td>Gemeenschappelijke interface voor het lezen van de klok.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container.git"> psr/container </a>
    </td>
    <td>bibliotheek</td>
    <td>Common Container Interface (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher.git"> psr/event-dispatcher </a>
    </td>
    <td>bibliotheek</td>
    <td>Standaardinterfaces voor gebeurtenisafhandeling.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client.git"> psr/http-client </a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene interface voor HTTP-clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory.git"> psr/http-factory </a>
    </td>
    <td>bibliotheek</td>
    <td>PSR-17: Gemeenschappelijke interfaces voor PSR-7 HTTP- berichtfabrieken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git"> psr/http-message </a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene interface voor HTTP-berichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log.git"> psr/log </a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene interface voor logbibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders.git"> ralouphie/getallheaders </a>
    </td>
    <td>bibliotheek</td>
    <td>Een polyfill voor getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection.git"> ramsey/inzameling </a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP-bibliotheek voor het weergeven en manipuleren van verzamelingen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid.git"> ramsey/uuid </a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP-bibliotheek voor het genereren en gebruiken van universeel unieke id's (UUID's).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise.git"> reactie/belofte </a>
    </td>
    <td>bibliotheek</td>
    <td>Een lichte implementatie van CommonJS Promises/A voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser.git"> sabberworm/php-css-parser </a>
    </td>
    <td>bibliotheek</td>
    <td>Parser voor CSS-bestanden geschreven in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint.git"> seld/jsonlint </a>
    </td>
    <td>bibliotheek</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils.git"> seld/phar-utils </a>
    </td>
    <td>bibliotheek</td>
    <td>Hulpprogramma's voor PHAR-bestandsindelingen, bijvoorbeeld wanneer PHP je opbelt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git"> geselecteerd/signaal-manager </a>
    </td>
    <td>bibliotheek</td>
    <td>Eenvoudige unix signaalmanager die ongemerkt ontbreekt waar de signalen niet voor gemakkelijke dwars-platformontwikkeling worden gesteund</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap.git"> spomky-labs/aes-key-wrap </a>
    </td>
    <td>bibliotheek</td>
    <td>AES Key Wrap voor PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp.git"> spomky-labs/otphp </a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP bibliotheek voor het produceren van één tijdwachtwoorden volgens RFC 4226 (het Algoritme van HOTP) en RFC 6238 (TOTP Algorithm) en compatibel met de Authenticator van Google</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework.git"> spomky-labs/pki-kader </a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP-framework voor het beheren van infrastructuur voor openbare sleutels. Het omvat X.509 openbare zeer belangrijke certificaten, attributencertificaten, certificatieverzoeken en certificatiewegbevestiging.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config.git"> symfony/config </a>
    </td>
    <td>bibliotheek</td>
    <td>Helpt u configuratiewaarden van om het even welke aard te vinden, te laden, te combineren, automatisch te vullen en te bevestigen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console.git"> symfony/console </a>
    </td>
    <td>bibliotheek</td>
    <td>Versnelt het creëren van mooie en testable bevellijninterfaces</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector.git"> symfony/css-selector </a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee converteert u CSS-kiezers naar XPath-expressies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection.git"> symfony/afhankelijkheid-injectie </a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee kunt u de manier waarop objecten in uw toepassing worden gemaakt standaardiseren en centraliseren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts.git"> symfony/deprecation-Contracten </a>
    </td>
    <td>bibliotheek</td>
    <td>Een algemene functie en conventie voor het activeren van plaatsingsberichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler.git"> symfony/fout-manager </a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt tools om fouten te beheren en foutopsporing in PHP-code te vereenvoudigen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher.git"> symfony/event-dispatcher </a>
    </td>
    <td>bibliotheek</td>
    <td>Verstrekt hulpmiddelen die uw toepassingscomponenten toestaan om met elkaar te communiceren door gebeurtenissen te verzenden en aan hen te luisteren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts.git"> symfony/event-dispatcher-Contracts </a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene abstracties met betrekking tot verzendgebeurtenis</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem.git"> symfony/filesystem </a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt basisfuncties voor het bestandssysteem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder.git"> symfony/vinder </a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee zoekt u bestanden en mappen via een intuïtieve fluent-interface</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client.git"> symfony/http-client </a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt krachtige methoden om HTTP-bronnen synchroon of asynchroon op te halen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts.git"> symfony/http-client-Contracts </a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene abstracties met betrekking tot HTTP-clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation.git"> symfony/http-foundation </a>
    </td>
    <td>bibliotheek</td>
    <td>Definieert een objectgeoriënteerde laag voor de HTTP-specificatie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel.git"> symfony/http-kernel </a>
    </td>
    <td>bibliotheek</td>
    <td>Verstrekt een gestructureerd proces om een Verzoek in een Reactie om te zetten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git"> symfony/intl </a>
    </td>
    <td>bibliotheek</td>
    <td>Verleent toegang tot de localisatiegegevens van de bibliotheek ICU</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype.git"> symfony/polyfill-type </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor tekstfuncties</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme.git"> symfony/polyfill-intl-grapheme </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor de functies grapheme_* van intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn.git"> symfony/polyfill-intl-idn </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor de functies idn_to_ascii en idn_to_utf8</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer.git"> symfony/polyfill-intl-normalizer </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor de klasse Normalizer van intl en verwante functies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring.git"> symfony/polyfill-mbstring </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill voor de extensie Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php72.git"> symfony/polyfill-php72 </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 7.2+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73.git"> symfony/polyfill-php73 </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 7.3+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80.git"> symfony/polyfill-php80 </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.0+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81.git"> symfony/polyfill-php81 </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.1+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git"> symfony/polyfill-php83 </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.3+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process.git"> symfony/proces </a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee voert u opdrachten uit in subprocessen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts.git"> symfony/dienst-contracten </a>
    </td>
    <td>bibliotheek</td>
    <td>Algemene abstracties met betrekking tot schrijfdiensten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string.git"> symfony/koord </a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt een objectgeoriënteerde API voor tekenreeksen en behandelt bytes, UTF-8-codepunten en grafeemclusters op een uniforme manier</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper.git"> symfony/var-dumper </a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt mechanismen om willekeurige PHP variabelen te doorlopen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter.git"> symfony/var-exporter </a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee wordt het exporteren van eventuele serialiseerbare PHP-gegevensstructuur naar normale PHP-code toegestaan</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git"> web-token/jwt-framework </a>
    </td>
    <td>symfony-bundel</td>
    <td>JSON Object Signing and Encryption library for PHP and Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webmozarts/assert.git"> webmozart/beweert </a>
    </td>
    <td>bibliotheek</td>
    <td>Bevestigingen om methodeinput/output met aardige foutenmeldingen te bevestigen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php.git"> webonyx/graphql-php </a>
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
      <a href="https://github.com/2tvenom/CBOREncode.git"> 2tvenom/cancode </a>
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
