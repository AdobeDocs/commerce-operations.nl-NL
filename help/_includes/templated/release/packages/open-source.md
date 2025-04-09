---
source-git-commit: ba444c5f74cdeec86c842014d02775faf16b2f50
workflow-type: tm+mt
source-wordcount: '2073'
ht-degree: 0%

---
# Magento Open Source-pakketten

<!-- The 'packages' variable contains the 'packages' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'packages-dev' variable contains the 'packages-dev' node of the '_data/codebase/open-source/composer_lock.json' file
 -->

<!-- The 'product' variable contains data of the 'magento/product-community-edition' package
 -->

<!-- The edition variable contains `open-source` value from the _data/names.yml file
 -->

Magento Open Source gebruikt Composer om PHP-pakketten te beheren.

In het bestand `composer.json` wordt de lijst met pakketten gedeclareerd, terwijl in het bestand van `composer.lock` een volledige lijst met pakketten (een volledige versie van elk pakket en de bijbehorende afhankelijkheden) is opgeslagen die zijn gebruikt om een installatie van Magento Open Source te maken.

De volgende referentiedocumentatie wordt gegenereerd uit het `composer.lock` -bestand en omvat de vereiste pakketten die in Magento Open Source 2.4.8 zijn opgenomen.

## Afhankelijkheden

`magento/product-community-edition 2.4.8` heeft de volgende afhankelijkheden:

```config
adobe-commerce/os-extensions-metapackage: 1.0.1
colinmollenhour/cache-backend-file: ^1.4
colinmollenhour/cache-backend-redis: ^1.16
colinmollenhour/credis: ^1.15
colinmollenhour/php-redis-session-abstract: ^2.0
composer/composer: ^2.0, !=2.2.16
duosecurity/duo_api_php: ^1.1
duosecurity/duo_universal_php: ^1.0
elasticsearch/elasticsearch: ^8.15
ext-bcmath: *
ext-ctype: *
ext-curl: *
ext-dom: *
ext-ftp: *
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
ext-xsl: *
ext-zip: *
ezyang/htmlpurifier: ^4.17
guzzlehttp/guzzle: ^7.5
laminas/laminas-captcha: ^2.18
laminas/laminas-code: ^4.13
laminas/laminas-di: ^3.15
laminas/laminas-escaper: ^2.13
laminas/laminas-eventmanager: ^3.11
laminas/laminas-feed: ^2.22
laminas/laminas-filter: ^2.33
laminas/laminas-http: ^2.15
laminas/laminas-i18n: ^2.17
laminas/laminas-modulemanager: ^2.11
laminas/laminas-mvc: ^3.6
laminas/laminas-permissions-acl: ^2.10
laminas/laminas-servicemanager: ^3.16
laminas/laminas-soap: ^2.10
laminas/laminas-stdlib: ^3.11
laminas/laminas-uri: ^2.9
laminas/laminas-validator: ^2.23
league/flysystem: ^3.0
league/flysystem-aws-s3-v3: ^3.0
lib-libxml: *
magento/composer: ^1.10.1-beta1
magento/composer-dependency-version-audit-plugin: ^0.1
magento/framework: 103.0.8
magento/framework-amqp: 100.4.6
magento/framework-bulk: 101.0.4
magento/framework-message-queue: 100.4.8
magento/inventory-metapackage: 1.2.8
magento/language-de_de: 100.4.0
magento/language-en_us: 100.4.0
magento/language-es_es: 100.4.0
magento/language-fr_fr: 100.4.0
magento/language-nl_nl: 100.4.0
magento/language-pt_br: 100.4.0
magento/language-zh_hans_cn: 100.4.0
magento/magento-composer-installer: >=0.4.0
magento/magento-zf-db: ^3.21.0
magento/magento2-base: 2.4.8
magento/module-admin-analytics: 100.4.7
magento/module-admin-notification: 100.4.7
magento/module-advanced-pricing-import-export: 100.4.8
magento/module-advanced-search: 100.4.6
magento/module-amqp: 100.4.5
magento/module-analytics: 100.4.8
magento/module-application-performance-monitor: 100.4.1
magento/module-application-performance-monitor-new-relic: 100.4.1
magento/module-async-config: 100.4.1
magento/module-asynchronous-operations: 100.4.8
magento/module-authorization: 100.4.8
magento/module-aws-s3: 100.4.6
magento/module-backend: 102.0.8
magento/module-backup: 100.4.8
magento/module-bundle: 101.0.8
magento/module-bundle-graph-ql: 100.4.8
magento/module-bundle-import-export: 100.4.7
magento/module-cache-invalidate: 100.4.6
magento/module-captcha: 100.4.8
magento/module-cardinal-commerce: 100.4.6
magento/module-catalog: 104.0.8
magento/module-catalog-analytics: 100.4.5
magento/module-catalog-cms-graph-ql: 100.4.4
magento/module-catalog-customer-graph-ql: 100.4.7
magento/module-catalog-graph-ql: 100.4.8
magento/module-catalog-import-export: 101.1.8
magento/module-catalog-inventory: 100.4.8
magento/module-catalog-inventory-graph-ql: 100.4.5
magento/module-catalog-rule: 101.2.8
magento/module-catalog-rule-configurable: 100.4.7
magento/module-catalog-rule-graph-ql: 100.4.5
magento/module-catalog-search: 102.0.8
magento/module-catalog-url-rewrite: 100.4.8
magento/module-catalog-url-rewrite-graph-ql: 100.4.6
magento/module-catalog-widget: 100.4.8
magento/module-checkout: 100.4.8
magento/module-checkout-agreements: 100.4.7
magento/module-checkout-agreements-graph-ql: 100.4.4
magento/module-cms: 104.0.8
magento/module-cms-graph-ql: 100.4.5
magento/module-cms-url-rewrite: 100.4.7
magento/module-cms-url-rewrite-graph-ql: 100.4.6
magento/module-compare-list-graph-ql: 100.4.4
magento/module-config: 101.2.8
magento/module-configurable-import-export: 100.4.6
magento/module-configurable-product: 100.4.8
magento/module-configurable-product-graph-ql: 100.4.8
magento/module-configurable-product-sales: 100.4.5
magento/module-contact: 100.4.7
magento/module-contact-graph-ql: 100.4.1
magento/module-cookie: 100.4.8
magento/module-cron: 100.4.8
magento/module-csp: 100.4.7
magento/module-currency-symbol: 100.4.6
magento/module-customer: 103.0.8
magento/module-customer-analytics: 100.4.5
magento/module-customer-downloadable-graph-ql: 100.4.4
magento/module-customer-graph-ql: 100.4.8
magento/module-customer-import-export: 100.4.8
magento/module-deploy: 100.4.8
magento/module-developer: 100.4.8
magento/module-dhl: 100.4.7
magento/module-directory: 100.4.8
magento/module-directory-graph-ql: 100.4.6
magento/module-downloadable: 100.4.8
magento/module-downloadable-graph-ql: 100.4.8
magento/module-downloadable-import-export: 100.4.7
magento/module-eav: 102.1.8
magento/module-eav-graph-ql: 100.4.5
magento/module-elasticsearch: 101.0.8
magento/module-elasticsearch-8: 101.0.0
magento/module-email: 101.1.8
magento/module-encryption-key: 100.4.6
magento/module-fedex: 100.4.6
magento/module-gift-message: 100.4.7
magento/module-gift-message-graph-ql: 100.4.6
magento/module-google-adwords: 100.4.5
magento/module-google-analytics: 100.4.4
magento/module-google-gtag: 100.4.3
magento/module-google-optimizer: 100.4.7
magento/module-graph-ql: 100.4.8
magento/module-graph-ql-cache: 100.4.5
magento/module-graph-ql-new-relic: 100.4.1
magento/module-graph-ql-resolver-cache: 100.4.1
magento/module-grouped-catalog-inventory: 100.4.5
magento/module-grouped-import-export: 100.4.6
magento/module-grouped-product: 100.4.8
magento/module-grouped-product-graph-ql: 100.4.8
magento/module-import-export: 101.0.8
magento/module-indexer: 100.4.8
magento/module-instant-purchase: 100.4.7
magento/module-integration: 100.4.8
magento/module-integration-graph-ql: 100.4.1
magento/module-jwt-framework-adapter: 100.4.4
magento/module-jwt-user-token: 100.4.3
magento/module-layered-navigation: 100.4.8
magento/module-login-as-customer: 100.4.8
magento/module-login-as-customer-admin-ui: 100.4.8
magento/module-login-as-customer-api: 100.4.7
magento/module-login-as-customer-assistance: 100.4.7
magento/module-login-as-customer-frontend-ui: 100.4.7
magento/module-login-as-customer-graph-ql: 100.4.5
magento/module-login-as-customer-log: 100.4.6
magento/module-login-as-customer-page-cache: 100.4.7
magento/module-login-as-customer-quote: 100.4.6
magento/module-login-as-customer-sales: 100.4.7
magento/module-marketplace: 100.4.6
magento/module-media-content: 100.4.6
magento/module-media-content-api: 100.4.7
magento/module-media-content-catalog: 100.4.6
magento/module-media-content-cms: 100.4.6
magento/module-media-content-synchronization: 100.4.7
magento/module-media-content-synchronization-api: 100.4.6
magento/module-media-content-synchronization-catalog: 100.4.5
magento/module-media-content-synchronization-cms: 100.4.5
magento/module-media-gallery: 100.4.7
magento/module-media-gallery-api: 101.0.7
magento/module-media-gallery-catalog: 100.4.5
magento/module-media-gallery-catalog-integration: 100.4.5
magento/module-media-gallery-catalog-ui: 100.4.5
magento/module-media-gallery-cms-ui: 100.4.5
magento/module-media-gallery-integration: 100.4.7
magento/module-media-gallery-metadata: 100.4.6
magento/module-media-gallery-metadata-api: 100.4.5
magento/module-media-gallery-renditions: 100.4.6
magento/module-media-gallery-renditions-api: 100.4.5
magento/module-media-gallery-synchronization: 100.4.7
magento/module-media-gallery-synchronization-api: 100.4.6
magento/module-media-gallery-synchronization-metadata: 100.4.4
magento/module-media-gallery-ui: 100.4.7
magento/module-media-gallery-ui-api: 100.4.6
magento/module-media-storage: 100.4.7
magento/module-message-queue: 100.4.8
magento/module-msrp: 100.4.7
magento/module-msrp-configurable-product: 100.4.5
magento/module-msrp-grouped-product: 100.4.5
magento/module-multishipping: 100.4.8
magento/module-mysql-mq: 100.4.6
magento/module-new-relic-reporting: 100.4.6
magento/module-newsletter: 100.4.8
magento/module-newsletter-graph-ql: 100.4.5
magento/module-offline-payments: 100.4.6
magento/module-offline-shipping: 100.4.7
magento/module-open-search: 100.4.2
magento/module-order-cancellation: 100.4.1
magento/module-order-cancellation-graph-ql: 100.4.1
magento/module-order-cancellation-ui: 100.4.1
magento/module-page-cache: 100.4.8
magento/module-payment: 100.4.8
magento/module-payment-graph-ql: 100.4.3
magento/module-paypal: 101.0.8
magento/module-paypal-captcha: 100.4.5
magento/module-paypal-graph-ql: 100.4.6
magento/module-persistent: 100.4.8
magento/module-product-alert: 100.4.7
magento/module-product-video: 100.4.8
magento/module-quote: 101.2.8
magento/module-quote-analytics: 100.4.7
magento/module-quote-bundle-options: 100.4.4
magento/module-quote-configurable-options: 100.4.4
magento/module-quote-downloadable-links: 100.4.4
magento/module-quote-graph-ql: 100.4.8
magento/module-related-product-graph-ql: 100.4.5
magento/module-release-notification: 100.4.6
magento/module-remote-storage: 100.4.6
magento/module-reports: 100.4.8
magento/module-require-js: 100.4.4
magento/module-review: 100.4.8
magento/module-review-analytics: 100.4.5
magento/module-review-graph-ql: 100.4.4
magento/module-robots: 101.1.4
magento/module-rss: 100.4.6
magento/module-rule: 100.4.7
magento/module-sales: 103.0.8
magento/module-sales-analytics: 100.4.5
magento/module-sales-graph-ql: 100.4.8
magento/module-sales-inventory: 100.4.5
magento/module-sales-rule: 101.2.8
magento/module-sales-rule-graph-ql: 100.4.1
magento/module-sales-sequence: 100.4.5
magento/module-sample-data: 100.4.6
magento/module-search: 101.1.8
magento/module-security: 100.4.8
magento/module-send-friend: 100.4.6
magento/module-send-friend-graph-ql: 100.4.4
magento/module-shipping: 100.4.8
magento/module-sitemap: 100.4.7
magento/module-store: 101.1.8
magento/module-store-graph-ql: 100.4.6
magento/module-swagger: 100.4.7
magento/module-swagger-webapi: 100.4.4
magento/module-swagger-webapi-async: 100.4.4
magento/module-swatches: 100.4.8
magento/module-swatches-graph-ql: 100.4.6
magento/module-swatches-layered-navigation: 100.4.4
magento/module-tax: 100.4.8
magento/module-tax-graph-ql: 100.4.4
magento/module-tax-import-export: 100.4.7
magento/module-theme: 101.1.8
magento/module-theme-graph-ql: 100.4.5
magento/module-translation: 100.4.8
magento/module-ui: 101.2.8
magento/module-ups: 100.4.8
magento/module-url-rewrite: 102.0.7
magento/module-url-rewrite-graph-ql: 100.4.7
magento/module-user: 101.2.8
magento/module-usps: 100.4.7
magento/module-variable: 100.4.6
magento/module-vault: 101.2.8
magento/module-vault-graph-ql: 100.4.4
magento/module-version: 100.4.5
magento/module-webapi: 100.4.7
magento/module-webapi-async: 100.4.6
magento/module-webapi-security: 100.4.5
magento/module-weee: 100.4.8
magento/module-weee-graph-ql: 100.4.5
magento/module-widget: 101.2.8
magento/module-wishlist: 101.2.8
magento/module-wishlist-analytics: 100.4.6
magento/module-wishlist-graph-ql: 100.4.8
magento/page-builder: 1.7.5
magento/security-package: 1.1.7
magento/theme-adminhtml-backend: 100.4.8
magento/theme-frontend-blank: 100.4.8
magento/theme-frontend-luma: 100.4.8
magento/zend-cache: ^1.16
magento/zend-db: ^1.16
magento/zend-pdf: ^1.16
monolog/monolog: ^3.6
opensearch-project/opensearch-php: ^2.3
pelago/emogrifier: ^7.0
php: ~8.2.0||~8.3.0||~8.4.0
php-amqplib/php-amqplib: ^3.2
phpseclib/mcrypt_compat: ^2.0
phpseclib/phpseclib: ^3.0
psr/log: ^2 || ^3
ramsey/uuid: ^4.2
symfony/console: ^6.4
symfony/intl: ^6.4
symfony/mailer: ^6.4
symfony/mime: ^6.4
symfony/process: ^6.4
symfony/string: ^6.4
tedivm/jshrink: ^1.4
tubalmartin/cssmin: ^4.1
web-token/jwt-framework: ^3.4
webonyx/graphql-php: ^15.0
wikimedia/less.php: ^5.0
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
    <td>AWS SDK for PHP - Amazon Web Services gebruiken in je PHP project</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api.git"> open-telemetry/api </a>
    </td>
    <td>bibliotheek</td>
    <td>API voor OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context.git"> open-telemetrie/context </a>
    </td>
    <td>bibliotheek</td>
    <td>Context-implementatie voor OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      paypal/module-breintree
    </td>
    <td>pakket</td>
    <td>Braintree Magento</td>
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
      <a href="https://github.com/duosecurity/duo_universal_php.git"> duosecurity/duo_Universal_php </a>
    </td>
    <td>bibliotheek</td>
    <td>Een PHP-implementatie van de Duo Universal SDK.</td>
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
      <a href="https://github.com/laminas/laminas-di.git"> laminas/laminas-di </a>
    </td>
    <td>bibliotheek</td>
    <td>Geautomatiseerde afhankelijkheidsinjectie voor PSR-11 containers</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper.git">Laminas/Laminas-Escaper</a>
    </td>
    <td>bibliotheek</td>
    <td>Veilig en veilig ontsnappen aan HTML, HTML-attributen, JavaScript, CSS en URL's</td>
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
    <td>Biedt een eenvoudige interface voor het uitvoeren van HTTP-verzoeken (Hyper-Text Transfer Protocol)</td>
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
      <a href="https://github.com/laminas/laminas-server.git">laminas/laminas-server</a>
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
      <a href="https://github.com/laminas/laminas-session.git">Laminas/Laminas-sessie</a>
    </td>
    <td>bibliotheek</td>
    <td>Objectgeoriënteerde interface voor PHP-sessies en -opslag</td>
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
    <td>SPL-extensies, array-hulpprogramma's, fouthandlers en meer</td>
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
      <a href="https://github.com/laminas/laminas-translator.git">Laminas/Laminas-vertaler</a>
    </td>
    <td>bibliotheek</td>
    <td>Interfaces voor de Translator-component van laminas-i18n</td>
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
      <a href="https://github.com/marc-mabe/php-enum.git"> marc-mabe/php-enum </a>
    </td>
    <td>bibliotheek</td>
    <td>Eenvoudige en snelle implementatie van opsommingen met native PHP</td>
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
      <a href="https://github.com/phpfui/recaptcha.git"> phpfui/recaptcha </a>
    </td>
    <td>bibliotheek</td>
    <td>Clientbibliotheek voor Google reCAPTCHA voor PHP 8.4 en hoger</td>
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

### BSD-3-clausule-wijziging

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
    <td>Magento-module</td>
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
    <td>Voorheen videlalvaro/php-amqplib.  Deze library is een pure PHP implementatie van het AMQP protocol. Het is getest tegen RabbitMQ.</td>
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
    <td>Braintree PHP Client Bibliotheek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math.git"> steen/math </a>
    </td>
    <td>bibliotheek</td>
    <td>Rekenbibliotheek met willekeurige precisie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter.git">Baksteen/Varexporter</a>
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
      <a href="https://github.com/composer/pcre.git">Componist/PCRE</a>
    </td>
    <td>bibliotheek</td>
    <td>PCRE-wrappingbibliotheek die typeveilige preg_*-vervangingen biedt.</td>
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
      <a href="https://github.com/doctrine/lexer.git">Leer/Lexer</a>
    </td>
    <td>bibliotheek</td>
    <td>PHP Doctrine Lexer parser bibliotheek die kan worden gebruikt in Top-Down, Recursive Descent Parsers.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator.git"> egulias/e-mail-validator </a>
    </td>
    <td>bibliotheek</td>
    <td>Een bibliotheek voor het valideren van e-mailberichten op verschillende RFC's</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php.git"> elastic/vervoer </a>
    </td>
    <td>bibliotheek</td>
    <td>HTTP transport PHP bibliotheek voor Elastic producten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php.git"> elasticsearch/elasticsearch </a>
    </td>
    <td>bibliotheek</td>
    <td>PHP Client voor Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code.git">Endroid/QR-code</a>
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
      <a href="https://github.com/thephpleague/flysystem.git">competitie/flysystem</a>
    </td>
    <td>bibliotheek</td>
    <td>Abstractie van bestandsopslag voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3.git">competitie/flysystem-aws-s3-v3</a>
    </td>
    <td>bibliotheek</td>
    <td>AWS S3-bestandssysteemadapter voor Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local.git"> liga/flysystem-local </a>
    </td>
    <td>bibliotheek</td>
    <td>Lokale bestandssysteemadapter voor Flysystem.</td>
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
    <td>PHP 5.x polyfill voor random_bytes() en random_int() vanaf PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier.git">Pelago/Emogrifier</a>
    </td>
    <td>bibliotheek</td>
    <td>Hiermee zet u CSS-stijlen om in inline stijlkenmerken in uw HTML-code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery.git"> php-http/discovery </a>
    </td>
    <td>composer-plug-in</td>
    <td>Vindt en installeert PSR-7, PSR-17, PSR-18 en HTTPlug implementaties</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug.git"> php-http/httplug </a>
    </td>
    <td>bibliotheek</td>
    <td>HTTPlug, de HTTP client abstractie voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise.git"> php-http/promise </a>
    </td>
    <td>bibliotheek</td>
    <td>Promise die voor asynchrone HTTP- verzoeken wordt gebruikt</td>
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
      <a href="https://github.com/PhpGt/Dom.git">phpgt/dom</a>
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
    <td>PHP Secure Communications Library - Pure-PHP implementaties van RSA, AES, SSH2, SFTP, X.509 etc.</td>
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
    <td>Gemeenschappelijke containerinterface (PHP FIG PSR-11)</td>
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
    <td>PSR-17: Gemeenschappelijke interfaces voor PSR-7 HTTP-berichtenfabrieken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message.git">psr/http-bericht</a>
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
    <td>PHAR bestandsformaat hulpprogramma's, voor wanneer PHP je opvoert</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler.git">seld/sein-handler</a>
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
    <td>Vereenvoudigt het maken van mooie en testbare opdrachtregelinterfaces</td>
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
    <td>Biedt een gestructureerd proces voor het omzetten van een verzoek in een antwoord</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl.git">Symfony/INTL</a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt toegang tot de lokalisatiegegevens van de ICU-bibliotheek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer.git">symfonie/mailer</a>
    </td>
    <td>bibliotheek</td>
    <td>Helpt bij het verzenden van e-mails</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime.git"> symfony/mime </a>
    </td>
    <td>bibliotheek</td>
    <td>MIME-berichten kunnen worden bewerkt</td>
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
      <a href="https://github.com/symfony/polyfill-php82.git"> symfony/polyfill-php82 </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.2+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83.git"> symfony/polyfill-php83 </a>
    </td>
    <td>bibliotheek</td>
    <td>Symfony polyfill backportt enkele PHP 8.3+ functies naar lagere PHP-versies</td>
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
      <a href="https://github.com/symfony/string.git">symfonie/snaar</a>
    </td>
    <td>bibliotheek</td>
    <td>Biedt een objectgeoriënteerde API voor strings en gaat op een uniforme manier om met bytes, UTF-8-codepunten en grafeemclusters</td>
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
      <a href="https://github.com/symfony/yaml.git"> symfony/yaml </a>
    </td>
    <td>bibliotheek</td>
    <td>YAML-bestanden laden en dumpen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework.git"> web-token/jwt-framework </a>
    </td>
    <td>symfony-bundel</td>
    <td>JSON Object Signing en Encryption bibliotheek voor PHP en Symfony Bundle.</td>
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
      PayPal/module-braintree-cadeaubon
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
      PayPal/module-braintree-cadeauverpakking
    </td>
    <td>Magento2-module</td>
    <td>NVT</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>magento2-module</td>
    <td>NVT</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-promise
    </td>
    <td>Magento2-module</td>
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
      PayPal/module-braintree-core
    </td>
    <td>Magento2-module</td>
    <td>Vork uit de Magento Braintree 2.2.0 module door Gene Commerce for PayPal.</td>
  </tr>
  </tbody>
</table>
