---
source-git-commit: 6752688390a8bea98b49d235515f094386d88bd4
workflow-type: tm+mt
source-wordcount: '2906'
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

De volgende referentiedocumentatie wordt gegenereerd uit het `composer.lock` -bestand en omvat de vereiste pakketten die in Adobe Commerce 2.4.8 zijn opgenomen.

## Afhankelijkheden

`magento/product-enterprise-edition 2.4.8` heeft de volgende afhankelijkheden:

- adobe-commerce/extensions-metapakket: 2.0.1
- colinmolenhour/cache-back-end-file: ^1.4
- colinmolenhour/cache-backend-redis: ^1.16
- colinmolenuur/credits: ^1.15
- colinmolenhour/php-redis-session-abstract: ^2.0
- composer/composer: ^2.0, !=2.2.16
- duosecurity/duo_api_php: ^1.1
- duosecurity/duo_Universal_php: ^1.0
- elasticsearch/elasticsearch: ^8.15
- Text-bcmath: *
- text-type: *
- Tekstkrullen: *
- ext-dom: *
- Text-ftp: *
- ext-gd: *
- Teksthash: *
- ext-iconv: *
- Text-intl: *
- text-mbstring: *
- text-openssl: *
- ext-pdo_mysql: *
- ext-simplexml: *
- Volgende zeep: *
- Tekstnatrium: *
- Text-spl: *
- ext-xsl: *
- text-zip: *
- ezyang/htmlpurifier: ^4.17
- guzzlehttp: ^7.5
- laminas/laminas-captcha: ^2.18
- laminas/laminas-code: ^4.13
- laminas/laminas-di: ^3.15
- laminas/laminas-escaper: ^2.13
- laminas/laminas-eventmanager: ^3.11
- laminas/laminas-feed: ^2.2
- laminas/laminas-filter: ^2.33
- laminas/laminas-http: ^2.15
- laminas/laminas-i18n: ^2.17
- laminas/laminas-modulemanager: ^2.11
- laminas/laminas-mvc: ^3.6
- laminas/laminas-permissions-acl: ^2.10
- laminas/laminas-servicemanager: ^3.16
- laminas/laminas-soap: ^2.10
- laminas/laminas-stdlib: ^3.11
- laminas/laminas-uri: ^2.9
- laminas/laminas-validator: ^2.23
- liga/vliegsysteem: ^3.0
- liga/flysystem-aws-s3-v3: ^3.0
- lib-libxml: *
- magento/composer: ^1.10.1-bèta1
- magento/composer-dependency-version-audit-plugin: ^0.1
- magento/framework-foreign-key: 100.4.7
- magento/magento-composer-installer: >=0.4.0
- magento/magento-zf-db: ^3.21
- magento/magento2-ee base: 2.4.8
- [ magento/module-admin-gws ](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws/): 100.4.8
- [ magento/module-admin-gws-configureerbaar-product ](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-configurable-product/): 100.4.5
- [ magento/module-admin-gws-staging ](https://developer.adobe.com/commerce/php/module-reference/module-admin-gws-staging/): 100.4.5
- [ magento/module-geavanceerd-catalogus ](https://developer.adobe.com/commerce/php/module-reference/module-advanced-catalog/): 100.4.5
- [ magento/module-geavanceerd-controle ](https://developer.adobe.com/commerce/php/module-reference/module-advanced-checkout/): 100.4.8
- [ magento/module-geavanceerd-regel ](https://developer.adobe.com/commerce/php/module-reference/module-advanced-rule/): 100.4.5
- [ magento/module-geavanceerd-verkoop-regel ](https://developer.adobe.com/commerce/php/module-reference/module-advanced-sales-rule/): 100.4.5
- [ magento/module-toepassing-server ](https://developer.adobe.com/commerce/php/module-reference/module-application-server/): 100.4.1
- [ magento/module-application-server-new-relic ](https://developer.adobe.com/commerce/php/module-reference/module-application-server-new-relic/): 100.4.1
- [ magento/module-toepassing-server-prestaties-monitor ](https://developer.adobe.com/commerce/php/module-reference/module-application-server-performance-monitor/): 100.4.1
- [ magento/module-toepassing-server-staat-monitor ](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor/): 100.4.1
- [ magento/module-toepassing-server-staat-monitor-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-application-server-state-monitor-graph-ql/): 100.4.1
- [ magento/module-async-orde ](https://developer.adobe.com/commerce/php/module-reference/module-async-order/): 10.4.4
- [ magento/module-async-orde-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-async-order-graph-ql/): 100.4.3
- [ magento/module-ws-s3-klant-douane-attributen ](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-customer-custom-attributes/): 100.4.5
- [ magento/module-ws-s3-gift-kaart-invoer-uitvoer ](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-gift-card-import-export/): 100.4.5
- [ magento/module-ws-s3-geplande-invoer-uitvoer ](https://developer.adobe.com/commerce/php/module-reference/module-aws-s3-scheduled-import-export/): 100.4.5
- [ magento/module-banner ](https://developer.adobe.com/commerce/php/module-reference/module-banner/): 101.2.8
- [ magento/module-banner-klant-segment ](https://developer.adobe.com/commerce/php/module-reference/module-banner-customer-segment/): 100.4.6
- [ magento/module-banner-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-banner-graph-ql/): 100.4.4
- [ magento/module-banner-staging ](https://developer.adobe.com/commerce/php/module-reference/module-banner-staging/): 100.4.2
- [ magento/module-bundle-import-export-staging ](https://developer.adobe.com/commerce/php/module-reference/module-bundle-import-export-staging/): 100.4.5
- [ magento/module-bundle-staging ](https://developer.adobe.com/commerce/php/module-reference/module-bundle-staging/): 100.4.8
- [ magento/module-catalogus-gebeurtenis ](https://developer.adobe.com/commerce/php/module-reference/module-catalog-event/): 101.1.7
- [ magento/module-catalogus-import-export-staging ](https://developer.adobe.com/commerce/php/module-reference/module-catalog-import-export-staging/): 100.4.5
- [ magento/module-catalogus-inventaris-staging ](https://developer.adobe.com/commerce/php/module-reference/module-catalog-inventory-staging/): 100.4.6
- [ magento/module-catalogus-toestemmingen ](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions/): 100.4.8
- [ magento/module-catalogus-toestemmingen-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-catalog-permissions-graph-ql/): 100.4.6
- [ magento/module-catalogus-regel-staging ](https://developer.adobe.com/commerce/php/module-reference/module-catalog-rule-staging/): 100.4.8
- [ magento/module-catalogus-opvoeren ](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging/): 100.4.8
- [ magento/module-catalogus-staging-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-catalog-staging-graph-ql/): 100.4.7
- [ magento/module-catalogus-url-rewrite-staging ](https://developer.adobe.com/commerce/php/module-reference/module-catalog-url-rewrite-staging/): 100.4.7
- [ magento/module-checkout-adres-onderzoek ](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search/): 100.4.7
- [ magento/module-checkout-adres-gift-register ](https://developer.adobe.com/commerce/php/module-reference/module-checkout-address-search-gift-registry/): 100.4.4
- [ magento/module-checkout-staging ](https://developer.adobe.com/commerce/php/module-reference/module-checkout-staging/): 100.4.7
- [ magento/module-cms-staging ](https://developer.adobe.com/commerce/php/module-reference/module-cms-staging/): 100.4.8
- [ magento/module-configureerbaar-product-staging ](https://developer.adobe.com/commerce/php/module-reference/module-configurable-product-staging/): 100.4.7
- [ magento/module-douane-attribuut-beheer ](https://developer.adobe.com/commerce/php/module-reference/module-custom-attribute-management/): 100.4.7
- [ magento/module-klant-balans ](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance/): 100.4.8
- [ magento/module-klant-balans-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-customer-balance-graph-ql/): 100.4.5
- [ magento/module-klant-douane-attributen ](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes/): 100.4.8
- [ magento/module-klant-douane-attributen-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-customer-custom-attributes-graph-ql/): 100.4.1
- [ magento/module-klant-financiering ](https://developer.adobe.com/commerce/php/module-reference/module-customer-finance/): 100.4.5
- [ magento/module-klant-segment ](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment/): 102.1.8
- [ magento/module-klant-segment-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-customer-segment-graph-ql/): 100.4.1
- [ magento/module-uitgesteld-totaal-Berekend ](https://developer.adobe.com/commerce/php/module-reference/module-deferred-total-calculating/): 100.4.3
- [ magento/module-downloadbaar-opvoeren ](https://developer.adobe.com/commerce/php/module-reference/module-downloadable-staging/): 100.4.7
- [ magento/module-elasticsearch-catalog-toestemmingen ](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions/): 100.4.4
- [ magento/module-elasticsearch-catalog-permissions-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-elasticsearch-catalog-permissions-graph-ql/): 100.4.3
- [ magento/module-onderneming ](https://developer.adobe.com/commerce/php/module-reference/module-enterprise/): 100.4.6
- [ magento/module-gift-kaart ](https://developer.adobe.com/commerce/php/module-reference/module-gift-card/): 101.3.8
- [ magento/module-gift-kaart-rekening ](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account/): 101.2.8
- [ magento/module-gift-kaart-rekening-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-account-graph-ql/): 100.4.6
- [ magento/module-gift-kaart-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-graph-ql/): 100.4.8
- [ magento/module-gift-kaart-invoer-uitvoer ](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-import-export/): 100.4.5
- [ magento/module-gift-kaart-staging ](https://developer.adobe.com/commerce/php/module-reference/module-gift-card-staging/): 100.4.5
- [ magento/module-gift-bericht-staging ](https://developer.adobe.com/commerce/php/module-reference/module-gift-message-staging/): 100.4.5
- [ magento/module-gift-register ](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry/): 101.2.8
- [ magento/module-gift-register-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-gift-registry-graph-ql/): 100.4.4
- [ magento/module-gift-verpakken ](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping/): 101.2.7
- [ magento/module-gift-wrapping-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-graph-ql/): 100.4.5
- [ magento/module-gift-verpakken-staging ](https://developer.adobe.com/commerce/php/module-reference/module-gift-wrapping-staging/): 100.4.5
- [ magento/module-google-optimizer-staging ](https://developer.adobe.com/commerce/php/module-reference/module-google-optimizer-staging/): 100.4.5
- [ magento/module-google-markering-manager ](https://developer.adobe.com/commerce/php/module-reference/module-google-tag-manager/): 100.4.8
- [ magento/module-gegroepeerd-product-staging ](https://developer.adobe.com/commerce/php/module-reference/module-grouped-product-staging/): 100.4.6
- [ magento/module-invoer-csv ](https://developer.adobe.com/commerce/php/module-reference/module-import-csv/): 100.4.2
- [ magento/module-import-csv-api ](https://developer.adobe.com/commerce/php/module-reference/module-import-csv-api/): 100.4.2
- [ magento/module-import-json ](https://developer.adobe.com/commerce/php/module-reference/module-import-json/): 100.4.1
- [ magento/module-import-json-api ](https://developer.adobe.com/commerce/php/module-reference/module-import-json-api/): 100.4.1
- [ magento/module-uitnodiging ](https://developer.adobe.com/commerce/php/module-reference/module-invitation/): 100.4.7
- [ magento/module-gelaagd-navigatie-staging ](https://developer.adobe.com/commerce/php/module-reference/module-layered-navigation-staging/): 100.4.5
- [ magento/module-registreren ](https://developer.adobe.com/commerce/php/module-reference/module-logging/): 101.2.8
- [ magento/module-login-as-klant-registreren ](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-logging/): 100.4.8
- [ magento/module-login-as-klant-website-beperking ](https://developer.adobe.com/commerce/php/module-reference/module-login-as-customer-website-restriction/): 100.4.6
- [ magento/module-media-content-catalog-staging ](https://developer.adobe.com/commerce/php/module-reference/module-media-content-catalog-staging/): 100.4.5
- [ magento/module-msrp-staging ](https://developer.adobe.com/commerce/php/module-reference/module-msrp-staging/): 100.4.6
- [ magento/module-multicoupon ](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon/): 100.4.1
- [ magento/module-multicoupon-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-graph-ql/): 100.4.1
- [ magento/module-multicoupon-ui ](https://developer.adobe.com/commerce/php/module-reference/module-multicoupon-ui/): 100.4.1
- [ magento/module-veelvoudig-wenslijst ](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist/): 100.4.8
- [ magento/module-veelvoudig-verlanglist-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-multiple-wishlist-graph-ql/): 100.4.4
- [ magento/module-betaling-staging ](https://developer.adobe.com/commerce/php/module-reference/module-payment-staging/): 100.4.5
- [ magento/module-persistente-history ](https://developer.adobe.com/commerce/php/module-reference/module-persistent-history/): 100.4.5
- [ magento/module-prijs-toestemmingen ](https://developer.adobe.com/commerce/php/module-reference/module-price-permissions/): 100.4.4
- [ magento/module-product-video-opvoeren ](https://developer.adobe.com/commerce/php/module-reference/module-product-video-staging/): 100.4.5
- [ magento/module-bevordering-toestemmingen ](https://developer.adobe.com/commerce/php/module-reference/module-promotion-permissions/): 100.4.5
- [ magento/module-citaat-handel-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-quote-commerce-graph-ql/): 100.4.1
- [ magento/module-citaat-gift-kaart-opties ](https://developer.adobe.com/commerce/php/module-reference/module-quote-gift-card-options/): 100.4.5
- [ magento/module-citaat-staging ](https://developer.adobe.com/commerce/php/module-reference/module-quote-staging/): 100.4.5
- [ magento/module-herinnering ](https://developer.adobe.com/commerce/php/module-reference/module-reminder/): 101.2.7
- [ magento/module-ver-opslag-handel ](https://developer.adobe.com/commerce/php/module-reference/module-remote-storage-commerce/): 100.4.4
- [ magento/module-middel-verbindingen ](https://developer.adobe.com/commerce/php/module-reference/module-resource-connections/): 100.4.5
- [ magento/module-overzicht-staging ](https://developer.adobe.com/commerce/php/module-reference/module-review-staging/): 100.4.5
- [ magento/module-beloning ](https://developer.adobe.com/commerce/php/module-reference/module-reward/): 101.2.8
- [ magento/module-beloning-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-reward-graph-ql/): 100.4.7
- [ magento/module-beloning-staging ](https://developer.adobe.com/commerce/php/module-reference/module-reward-staging/): 100.4.5
- [ magento/module-rma ](https://developer.adobe.com/commerce/php/module-reference/module-rma/): 101.2.8
- [ magento/module-rma-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-rma-graph-ql/): 100.4.7
- [ magento/module-rma-staging ](https://developer.adobe.com/commerce/php/module-reference/module-rma-staging/): 100.4.5
- [ magento/module-verkoop-archief ](https://developer.adobe.com/commerce/php/module-reference/module-sales-archive/): 101.0.6
- [ magento/module-verkoop-regel-staging ](https://developer.adobe.com/commerce/php/module-reference/module-sales-rule-staging/): 100.4.7
- [ magento/module-scalable-checkout ](https://developer.adobe.com/commerce/php/module-reference/module-scalable-checkout/): 10.4.7
- [ magento/module-scalable-voorraad ](https://developer.adobe.com/commerce/php/module-reference/module-scalable-inventory/): 100.4.6
- [ magento/module-scalable-oms ](https://developer.adobe.com/commerce/php/module-reference/module-scalable-oms/): 100.4.6
- [ magento/module-gepland-invoer-uitvoer ](https://developer.adobe.com/commerce/php/module-reference/module-scheduled-import-export/): 101.2.8
- [ magento/module-onderzoek-staging ](https://developer.adobe.com/commerce/php/module-reference/module-search-staging/): 100.4.6
- [ magento/module-staging ](https://developer.adobe.com/commerce/php/module-reference/module-staging/): 101.2.8
- [ magento/module-staging-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-staging-graph-ql/): 100.4.5
- [ magento/module-steun ](https://developer.adobe.com/commerce/php/module-reference/module-support/): 101.2.7
- [ magento/module-swat ](https://developer.adobe.com/commerce/php/module-reference/module-swat/): 100.4.6
- [ magento/module-doel-regel ](https://developer.adobe.com/commerce/php/module-reference/module-target-rule/): 101.2.8
- [ magento/module-doel-regel-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-target-rule-graph-ql/): 100.4.5
- [ magento/module-versies-cms ](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms/): 101.2.8
- [ magento/module-versies-cms-pagina-geheime voorgeheugen ](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-page-cache/): 100.4.4
- [ magento/module-versies-cms-url-rewrite ](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite/): 100.4.6
- [ magento/module-versies-cms-url-rewrite-graph-ql ](https://developer.adobe.com/commerce/php/module-reference/module-versions-cms-url-rewrite-graph-ql/): 100.4.4
- [ magento/module-visual-merchandiser ](https://developer.adobe.com/commerce/php/module-reference/module-visual-merchandiser/): 100.4.8
- [ magento/module-webapi-rest-gws ](https://developer.adobe.com/commerce/php/module-reference/module-webapi-rest-gws/): 100.4.0
- [ magento/module-website-beperking ](https://developer.adobe.com/commerce/php/module-reference/module-website-restriction/): 10.4.7
- [ magento/module-weee-staging ](https://developer.adobe.com/commerce/php/module-reference/module-weee-staging/): 100.4.5
- [ magento/module-wishlist-gift-kaart ](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card/): 100.4.4
- [ magento/module-wishlist-gift-kaart-grafiek-ql ](https://developer.adobe.com/commerce/php/module-reference/module-wishlist-gift-card-graph-ql/): 100.4.4
- magento/page-builder-commerce: 1.7.5
- magento/product-community-edition: 2.4.8
- magento/security-package-ee: 1.0.3
- magento/theme-adminhtml-spectrum: 100.4.3
- magento/zend-cache: ^1.16
- magento/zend-db: ^1.16
- magento/zend-pdf: ^1.16
- monoloog/monoloog: ^3.6
- openssearch-project/openssearch-php: ^2.3
- pelago/emogrifier: ^7.0
- php: ~8.2.0||~8.3.0||~8.4.0
- php-amqplib/php-amqplib: ^3.2
- phpseclib/mcrypt_compat: ^2.0
- phpseclib/phpseclib: ^3.0
- psr/log: ^2 || ^3
- ramsey/uuid: ^4.2
- symfony/console: ^6.4
- symfony/intl: ^6.4
- symfony/mailer: ^6.4
- symfony/mime: ^6.4
- symfonie/proces: ^6.4
- symfony/tekenreeks: ^6.4
- tedivm/jshrink: ^1.4
- tubalmartin/cssmin: ^4.1
- web-token/jwt-framework: ^3.4
- webonyx/grafisch-php: ^15.0
- wikimedia/less.php: ^5.0

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
      <a href="https://github.com/opensearch-project/opensearch-php"> openssearch-project/openssearch-php </a>
    </td>
    <td>Bibliotheek</td>
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
      <a href="https://github.com/adobe/stock-api-libphp"> astock/stock-api-libphp </a>
    </td>
    <td>Bibliotheek</td>
    <td>Adobe Stock API-bibliotheek</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/awslabs/aws-crt-php"> aws/aws-crt-php </a>
    </td>
    <td>Bibliotheek</td>
    <td>AWS Common Runtime voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/aws/aws-sdk-php"> aws/aws-sdk-php </a>
    </td>
    <td>Bibliotheek</td>
    <td>AWS SDK for PHP - Amazon Web Services gebruiken in je PHP project</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/api"> open-telemetry/api </a>
    </td>
    <td>Bibliotheek</td>
    <td>API voor OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/opentelemetry-php/context"> open-telemetrie/context </a>
    </td>
    <td>Bibliotheek</td>
    <td>Context-implementatie voor OpenTelemetry PHP.</td>
  </tr>
  <tr>
    <td>
      paypal/module-breintree
    </td>
    <td>Metapakket</td>
    <td>Braintree Magento</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/wikimedia/less.php"> wikimedia/less.php</a>
    </td>
    <td>Bibliotheek</td>
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
      <a href="https://github.com/Bacon/BaconQrCode"> bacon/bacon-qr-code </a>
    </td>
    <td>Bibliotheek</td>
    <td>BaconQrCode is een QR code generator voor PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/DASPRiD/Enum"> dasprid/enum </a>
    </td>
    <td>Bibliotheek</td>
    <td>PHP 7.1 enum implementatie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webimpress/safe-writer"> webimpress/safe-writer </a>
    </td>
    <td>Bibliotheek</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_File"> colinmelenhour/cache-back-end-file </a>
    </td>
    <td>Magento-module</td>
    <td>De stock Zend_Cache_Backend_File achtergrond heeft uiterst slechte prestaties voor schoonmaken door markeringen die het onbruikbaar maken maken aangezien het aantal caching punten stijgt. Deze backend brengt vele veranderingen met zich mee die in een enorme prestatiesverhoging, vooral voor markeringszuivering resulteren.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/php-redis-session-abstract"> colinmolenhour/php-redis-session-abstract </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een op Redis gebaseerde sessiehandler met optimistische vergrendeling</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/duosecurity/duo_universal_php"> duosecurity/duo_Universal_php </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een PHP-implementatie van de Duo Universal SDK.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/firebase/php-jwt"> firebase/php-jwt </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een eenvoudige bibliotheek voor het coderen en decoderen van JSON Web Tokens (JWT) in PHP. Moet in overeenstemming zijn met de huidige specificatie.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-captcha"> laminas/laminas-captcha </a>
    </td>
    <td>Bibliotheek</td>
    <td>CAPTCHA's genereren en valideren met behulp van figuren, afbeeldingen, ReCaptcha en meer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-code"> laminas/laminas-code </a>
    </td>
    <td>Bibliotheek</td>
    <td>Extensies voor de PHP Reflectie-API, scannen van statische code en genereren van code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-config"> laminas/laminas-config </a>
    </td>
    <td>Bibliotheek</td>
    <td>biedt een geneste, op objecteigenschappen gebaseerde gebruikersinterface voor toegang tot deze configuratiegegevens binnen de toepassingscode</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-di"> laminas/laminas-di </a>
    </td>
    <td>Bibliotheek</td>
    <td>Geautomatiseerde afhankelijkheidsinjectie voor PSR-11 containers</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-escaper"> laminas/laminas-escaper </a>
    </td>
    <td>Bibliotheek</td>
    <td>Veilig en veilig ontsnappen aan HTML, HTML-kenmerken, JavaScript, CSS en URL's</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-eventmanager"> laminas/laminas-eventmanager </a>
    </td>
    <td>Bibliotheek</td>
    <td>Trigger en luister naar gebeurtenissen in een PHP-toepassing</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-feed"> laminas/laminas-voer </a>
    </td>
    <td>Bibliotheek</td>
    <td>biedt functionaliteit voor het maken en gebruiken van RSS- en Atom-feeds</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-filter"> laminas/laminas-filter </a>
    </td>
    <td>Bibliotheek</td>
    <td>Gegevens en bestanden programmatisch filteren en normaliseren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-http"> laminas/laminas-http </a>
    </td>
    <td>Bibliotheek</td>
    <td>Biedt een eenvoudige interface voor het uitvoeren van HTTP-aanvragen (Hyper-Text Transfer Protocol)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-i18n"> laminas/laminas-i18n </a>
    </td>
    <td>Bibliotheek</td>
    <td>Vertaal uw toepassing en filtert en valideert geïnternationaliseerde waarden</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-json"> laminas/laminas-json </a>
    </td>
    <td>Bibliotheek</td>
    <td>biedt gebruiksvriendelijke methoden voor het serialiseren van native PHP naar JSON en het decoderen van JSON naar native PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-loader"> laminas/laminas-loader </a>
    </td>
    <td>Bibliotheek</td>
    <td>Laden van autoloading en plug-in</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-modulemanager"> laminas/laminas-modulemanager </a>
    </td>
    <td>Bibliotheek</td>
    <td>Modulair toepassingssysteem voor laminas-mvc-toepassingen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-mvc"> laminas/laminas-mvc </a>
    </td>
    <td>Bibliotheek</td>
    <td>De gebeurtenis-gedreven laag MVC van Laminas, met inbegrip van Toepassingen MVC, Controllers, en Insteekmodules</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-permissions-acl"> laminas/laminas-permissions-acl </a>
    </td>
    <td>Bibliotheek</td>
    <td>Verstrekt een lichtgewichten flexibele implementatie van de toegangsbeheerlijst (ACL) voor toegangsbeheer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-recaptcha"> laminas/laminas-recaptcha </a>
    </td>
    <td>Bibliotheek</td>
    <td>OOP-wrapper voor de ReCaptcha-webservice</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-router"> laminas/laminas-router </a>
    </td>
    <td>Bibliotheek</td>
    <td>Flexibel verpletterend systeem voor HTTP en consoletoepassingen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-server"> laminas/laminas-server </a>
    </td>
    <td>Bibliotheek</td>
    <td>Op reflectie gebaseerde RPC-servers maken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-servicemanager"> laminas/laminas-servicemanager </a>
    </td>
    <td>Bibliotheek</td>
    <td>In de fabriek aangebrachte afhankelijkheidsinjectiecontainer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-session"> laminas/laminas-zitting </a>
    </td>
    <td>Bibliotheek</td>
    <td>Object-oriented interface aan PHP zittingen en opslag</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-soap"> laminas/laminas-soap </a>
    </td>
    <td>Bibliotheek</td>
    <td></td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-stdlib"> laminas/laminas-stdlib </a>
    </td>
    <td>Bibliotheek</td>
    <td>SPL-extensies, arrayhulpprogramma's, fouthandlers en meer</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-text"> laminas/laminas-text </a>
    </td>
    <td>Bibliotheek</td>
    <td>FIGlets en op tekst gebaseerde tabellen maken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-translator"> laminas/laminas-vertaler </a>
    </td>
    <td>Bibliotheek</td>
    <td>Interfaces voor de component Translator van laminas-i18n</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-uri"> laminas/laminas-uri </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een component die helpt bij het manipuleren en valideren van URI's (Uniform Resource Identifiers)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-validator"> laminas/laminas-validator </a>
    </td>
    <td>Bibliotheek</td>
    <td>Validatieklassen voor een groot aantal domeinen en de mogelijkheid om validators te ketenen om complexe validatiecriteria te maken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/laminas/laminas-view"> laminas/laminas-mening </a>
    </td>
    <td>Bibliotheek</td>
    <td>Flexibele weergavelaag die meerdere weergavelagen, hulplijnen en meer ondersteunt en biedt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/marc-mabe/php-enum"> marc-mabe/php-enum </a>
    </td>
    <td>Bibliotheek</td>
    <td>Eenvoudige en snelle implementatie van opsommingen met native PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/nikic/PHP-Parser"> nikic/php-parser </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een PHP parser geschreven in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpfui/recaptcha"> phpfui/recaptcha </a>
    </td>
    <td>Bibliotheek</td>
    <td>Clientbibliotheek voor Google reCAPTCHA voor PHP 8.4 en hoger</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tedious/JShrink"> tedivm/jshrink </a>
    </td>
    <td>Bibliotheek</td>
    <td>Javascript Minifier geïntegreerd in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/tubalmartin/YUI-CSS-compressor-PHP-port"> tubalmartin/cssmin </a>
    </td>
    <td>Bibliotheek</td>
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
      <a href="https://github.com/colinmollenhour/Cm_Cache_Backend_Redis"> colinmolenhour/cache-backend-redis </a>
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
      <a href="https://github.com/paragonie/sodium_compat"> paragonie/natrium_compat </a>
    </td>
    <td>Bibliotheek</td>
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
      <a href="https://github.com/ezyang/htmlpurifier"> ezyang/htmlpurifier </a>
    </td>
    <td>Bibliotheek</td>
    <td>HTML-filter voldoet aan standaarden geschreven in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-amqplib/php-amqplib"> php-amqplib/php-amqplib </a>
    </td>
    <td>Bibliotheek</td>
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
      <a href="https://github.com/braintree/braintree_php"> breintree/braintree_php </a>
    </td>
    <td>Bibliotheek</td>
    <td>Braintree PHP Client Library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/math"> steen/math </a>
    </td>
    <td>Bibliotheek</td>
    <td>Rekenkundige bibliotheek met willekeurige precisie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/brick/varexporter"> baksteen/varexporter </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een krachtig alternatief voor var_export(), dat sluitingen en objecten zonder __set_state() kan exporteren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ChristianRiesen/base32"> christian-riesen/base32 </a>
    </td>
    <td>Bibliotheek</td>
    <td>Base32 encoder/decoder volgens RFC 4648</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/colinmollenhour/credis"> colinmolenhour/credits </a>
    </td>
    <td>Bibliotheek</td>
    <td>Credis is een lichtgewicht interface naar de sleutelwaardewinkel van Redis, waar de phpredis-bibliotheek wordt geplaatst als deze beschikbaar is voor betere prestaties.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/ca-bundle"> composer/ca-bundle </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hier vindt u een pad naar de CA-bundel van het systeem en een fallback naar de Mozilla CA-bundel.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/class-map-generator"> composer/klasse-kaart-generator </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hulpprogramma's voor het scannen van PHP-code en het genereren van klassenkaarten.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/composer"> composer/composer </a>
    </td>
    <td>Bibliotheek</td>
    <td>Met Composer kunt u afhankelijkheden van PHP-projecten declareren, beheren en installeren. Zo weet u zeker dat u overal de juiste stapel hebt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/metadata-minifier"> composer/metadata-minifier </a>
    </td>
    <td>Bibliotheek</td>
    <td>Kleine nutsbibliotheek die meta-gegevensminificatie en uitbreiding behandelt.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/pcre"> composer/pcre </a>
    </td>
    <td>Bibliotheek</td>
    <td>PCRE-wrapping-bibliotheek met type-veilige preg_* vervangingen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/semver"> composer/semver </a>
    </td>
    <td>Bibliotheek</td>
    <td>Semverbibliotheek met hulpprogramma's, parsering en validatie van versiebeperkingen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/spdx-licenses"> composer/spdx-vergunningen </a>
    </td>
    <td>Bibliotheek</td>
    <td>Lijst met SPDX-licenties en validatiebibliotheek.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/composer/xdebug-handler"> composer/xdebug-manager </a>
    </td>
    <td>Bibliotheek</td>
    <td>Start een proces zonder Xdebug opnieuw.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/doctrine/lexer"> doctrine/lexer </a>
    </td>
    <td>Bibliotheek</td>
    <td>PHP Doctrine Lexer parser bibliotheek die gebruikt kan worden in top-down, Recursive Descent Parsers.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/egulias/EmailValidator"> egulias/e-mail-validator </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een bibliotheek voor het valideren van e-mailberichten op verschillende RFC's</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elastic-transport-php"> elastic/vervoer </a>
    </td>
    <td>Bibliotheek</td>
    <td>HTTP transport PHP bibliotheek voor Elastic producten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/elastic/elasticsearch-php"> elasticsearch/elasticsearch </a>
    </td>
    <td>Bibliotheek</td>
    <td>PHP-client voor Elasticsearch</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/endroid/qr-code"> endroid/qr-code </a>
    </td>
    <td>Bibliotheek</td>
    <td>QR-code van Endroid</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/guzzlestreams"> ezimuel/guzzlestreams </a>
    </td>
    <td>Bibliotheek</td>
    <td>Vork van guzzle/streams (verlaten) voor gebruik met elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ezimuel/ringphp"> ezimuel/ringphp </a>
    </td>
    <td>Bibliotheek</td>
    <td>Vork van guzzle/RingPHP (verlaten) voor gebruik met elasticsearch-php</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/guzzle"> guzzlehttp/guzzle </a>
    </td>
    <td>Bibliotheek</td>
    <td>Guzzle is een PHP HTTP client library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/promises"> guzzlehttp/promise </a>
    </td>
    <td>Bibliotheek</td>
    <td>Guzzle belooft library</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/guzzle/psr7"> guzzlehttp/psr7 </a>
    </td>
    <td>Bibliotheek</td>
    <td>PSR-7 berichtimplementatie die ook gemeenschappelijke nutsmethodes verstrekt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jsonrainbow/json-schema"> justinrainbow/json-schema </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een bibliotheek om een jseschema te valideren.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem"> liga/vliegsysteem </a>
    </td>
    <td>Bibliotheek</td>
    <td>Abstractie van bestandsopslag voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-aws-s3-v3"> liga/flysystem-ws-s3-v3 </a>
    </td>
    <td>Bibliotheek</td>
    <td>AWS S3-bestandssysteemadapter voor Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/flysystem-local"> liga/flysystem-local </a>
    </td>
    <td>Bibliotheek</td>
    <td>Lokale bestandssysteemadapter voor Flysystem.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/thephpleague/mime-type-detection"> liga/mime-type-opsporing </a>
    </td>
    <td>Bibliotheek</td>
    <td>MIME-typedetectie voor Flysystem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/monolog"> monolog/monolog </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hiermee verzendt u uw logbestanden naar bestanden, sockets, inboxen, databases en verschillende webservices</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/jmespath/jmespath.php"> mtdowling/jmespath.php</a>
    </td>
    <td>Bibliotheek</td>
    <td>Declaratief opgeven hoe elementen uit een JSON-document worden geëxtraheerd</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/constant_time_encoding"> paragonie/constant_time_encoding </a>
    </td>
    <td>Bibliotheek</td>
    <td>Constante-tijdImplementaties van Codering RFC 4648 (basis-64, basis-32, basis-16)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/paragonie/random_compat"> paragonie/random_compat </a>
    </td>
    <td>Bibliotheek</td>
    <td>PHP 5.x polyfill for random_bytes() en random_int() van PHP 7</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/emogrifier"> pelago/emogrifier </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hiermee zet u CSS-stijlen om in inline stijlkenmerken in uw HTML-code</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/discovery"> php-http/discovery </a>
    </td>
    <td>Composer-plug-in</td>
    <td>Vindt en installeert PSR-7, PSR-17, PSR-18 en HTTPlug implementaties</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/httplug"> php-http/httplug </a>
    </td>
    <td>Bibliotheek</td>
    <td>HTTPlug, de HTTP client abstractie voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-http/promise"> php-http/promise </a>
    </td>
    <td>Bibliotheek</td>
    <td>Promise die voor asynchrone HTTP- verzoeken wordt gebruikt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/CssXPath"> phpgt/cssxpath </a>
    </td>
    <td>Bibliotheek</td>
    <td>CSS-kiezers converteren naar XPath-query's.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/Dom"> phpgt/dom </a>
    </td>
    <td>Bibliotheek</td>
    <td>Moderne DOM API.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/PhpGt/PropFunc"> phpgt/propfunc </a>
    </td>
    <td>Bibliotheek</td>
    <td>Functies van accessoreigenschap en mutator.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/mcrypt_compat"> phpseclib/mcrypt_compat </a>
    </td>
    <td>Bibliotheek</td>
    <td>PHP 5.x-8.x polyfill for mcrypt extension</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/phpseclib/phpseclib"> phpseclib/phpseclib </a>
    </td>
    <td>Bibliotheek</td>
    <td>PHP Secure Communications Library - Pure-PHP implementaties van RSA, AES, SSH2, SFTP, X.509 enz.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/cache"> psr/cache </a>
    </td>
    <td>Bibliotheek</td>
    <td>Algemene interface voor het in cache plaatsen van bibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/clock"> psr/klok </a>
    </td>
    <td>Bibliotheek</td>
    <td>Gemeenschappelijke interface voor het lezen van de klok.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/container"> psr/container </a>
    </td>
    <td>Bibliotheek</td>
    <td>Common Container Interface (PHP FIG PSR-11)</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/event-dispatcher"> psr/event-dispatcher </a>
    </td>
    <td>Bibliotheek</td>
    <td>Standaardinterfaces voor gebeurtenisafhandeling.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-client"> psr/http-client </a>
    </td>
    <td>Bibliotheek</td>
    <td>Algemene interface voor HTTP-clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-factory"> psr/http-factory </a>
    </td>
    <td>Bibliotheek</td>
    <td>PSR-17: Gemeenschappelijke interfaces voor PSR-7 HTTP- berichtfabrieken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/http-message"> psr/http-message </a>
    </td>
    <td>Bibliotheek</td>
    <td>Algemene interface voor HTTP-berichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/php-fig/log"> psr/log </a>
    </td>
    <td>Bibliotheek</td>
    <td>Algemene interface voor logbibliotheken</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ralouphie/getallheaders"> ralouphie/getallheaders </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een polyfill voor getallheaders.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/collection"> ramsey/inzameling </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een PHP-bibliotheek voor het weergeven en manipuleren van verzamelingen.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/ramsey/uuid"> ramsey/uuid </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een PHP-bibliotheek voor het genereren en gebruiken van universeel unieke id's (UUID's).</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/reactphp/promise"> reactie/belofte </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een lichte implementatie van CommonJS Promises/A voor PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/MyIntervals/PHP-CSS-Parser"> sabberworm/php-css-parser </a>
    </td>
    <td>Bibliotheek</td>
    <td>Parser voor CSS-bestanden geschreven in PHP</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/jsonlint"> seld/jsonlint </a>
    </td>
    <td>Bibliotheek</td>
    <td>JSON Linter</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/phar-utils"> seld/phar-utils </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hulpprogramma's voor PHAR-bestandsindelingen, bijvoorbeeld wanneer PHP je opbelt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Seldaek/signal-handler"> geselecteerd/signaal-manager </a>
    </td>
    <td>Bibliotheek</td>
    <td>Eenvoudige unix signaalmanager die ongemerkt ontbreekt waar de signalen niet voor gemakkelijke dwars-platformontwikkeling worden gesteund</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/aes-key-wrap"> spomky-labs/aes-key-wrap </a>
    </td>
    <td>Bibliotheek</td>
    <td>AES Key Wrap voor PHP.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/otphp"> spomky-labs/otphp </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een PHP bibliotheek voor het produceren van één tijdwachtwoorden volgens RFC 4226 (het Algoritme van HOTP) en RFC 6238 (TOTP Algorithm) en compatibel met de Authenticator van Google</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/Spomky-Labs/pki-framework"> spomky-labs/pki-kader </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een PHP-framework voor het beheren van infrastructuur voor openbare sleutels. Het omvat X.509 openbare zeer belangrijke certificaten, attributencertificaten, certificatieverzoeken en certificatiewegbevestiging.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/config"> symfony/config </a>
    </td>
    <td>Bibliotheek</td>
    <td>Helpt u configuratiewaarden van om het even welke aard te vinden, te laden, te combineren, automatisch te vullen en te bevestigen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/console"> symfony/console </a>
    </td>
    <td>Bibliotheek</td>
    <td>Versnelt het creëren van mooie en testable bevellijninterfaces</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/css-selector"> symfony/css-selector </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hiermee converteert u CSS-kiezers naar XPath-expressies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/dependency-injection"> symfony/afhankelijkheid-injectie </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hiermee kunt u de manier waarop objecten in uw toepassing worden gemaakt standaardiseren en centraliseren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/deprecation-contracts"> symfony/deprecation-Contracten </a>
    </td>
    <td>Bibliotheek</td>
    <td>Een algemene functie en conventie voor het activeren van plaatsingsberichten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/error-handler"> symfony/fout-manager </a>
    </td>
    <td>Bibliotheek</td>
    <td>Biedt tools om fouten te beheren en foutopsporing in PHP-code te vereenvoudigen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher"> symfony/event-dispatcher </a>
    </td>
    <td>Bibliotheek</td>
    <td>Verstrekt hulpmiddelen die uw toepassingscomponenten toestaan om met elkaar te communiceren door gebeurtenissen te verzenden en aan hen te luisteren</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/event-dispatcher-contracts"> symfony/event-dispatcher-Contracts </a>
    </td>
    <td>Bibliotheek</td>
    <td>Algemene abstracties met betrekking tot verzendgebeurtenis</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/filesystem"> symfony/filesystem </a>
    </td>
    <td>Bibliotheek</td>
    <td>Biedt basisfuncties voor het bestandssysteem</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/finder"> symfony/vinder </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hiermee zoekt u bestanden en mappen via een intuïtieve fluent-interface</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client"> symfony/http-client </a>
    </td>
    <td>Bibliotheek</td>
    <td>Biedt krachtige methoden om HTTP-bronnen synchroon of asynchroon op te halen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-client-contracts"> symfony/http-client-Contracts </a>
    </td>
    <td>Bibliotheek</td>
    <td>Algemene abstracties met betrekking tot HTTP-clients</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-foundation"> symfony/http-foundation </a>
    </td>
    <td>Bibliotheek</td>
    <td>Definieert een objectgeoriënteerde laag voor de HTTP-specificatie</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/http-kernel"> symfony/http-kernel </a>
    </td>
    <td>Bibliotheek</td>
    <td>Verstrekt een gestructureerd proces om een Verzoek in een Reactie om te zetten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/intl"> symfony/intl </a>
    </td>
    <td>Bibliotheek</td>
    <td>Verleent toegang tot de localisatiegegevens van de bibliotheek ICU</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mailer"> symfony/mailer </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hulp bij het verzenden van e-mails</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/mime"> symfony/mime </a>
    </td>
    <td>Bibliotheek</td>
    <td>MIME-berichten kunnen worden bewerkt</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-ctype"> symfony/polyfill-type </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill voor tekstfuncties</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-grapheme"> symfony/polyfill-intl-grapheme </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill voor de functies grapheme_* van intl</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-idn"> symfony/polyfill-intl-idn </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill voor de functies idn_to_ascii en idn_to_utf8</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-intl-normalizer"> symfony/polyfill-intl-normalizer </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill voor de klasse Normalizer van intl en verwante functies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-mbstring"> symfony/polyfill-mbstring </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill voor de extensie Mbstring</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php73"> symfony/polyfill-php73 </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 7.3+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php80"> symfony/polyfill-php80 </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.0+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php81"> symfony/polyfill-php81 </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.1+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php82"> symfony/polyfill-php82 </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.2+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/polyfill-php83"> symfony/polyfill-php83 </a>
    </td>
    <td>Bibliotheek</td>
    <td>Symfony polyfill geeft een aantal functies van PHP 8.3+ terug naar lagere PHP versies</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/process"> symfony/proces </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hiermee voert u opdrachten uit in subprocessen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/service-contracts"> symfony/dienst-contracten </a>
    </td>
    <td>Bibliotheek</td>
    <td>Algemene abstracties met betrekking tot schrijfdiensten</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/string"> symfony/koord </a>
    </td>
    <td>Bibliotheek</td>
    <td>Biedt een objectgeoriënteerde API voor tekenreeksen en behandelt bytes, UTF-8-codepunten en grafeemclusters op een uniforme manier</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-dumper"> symfony/var-dumper </a>
    </td>
    <td>Bibliotheek</td>
    <td>Biedt mechanismen om willekeurige PHP variabelen te doorlopen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/var-exporter"> symfony/var-exporter </a>
    </td>
    <td>Bibliotheek</td>
    <td>Hiermee wordt het exporteren van eventuele serialiseerbare PHP-gegevensstructuur naar normale PHP-code toegestaan</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/symfony/yaml"> symfony/yaml </a>
    </td>
    <td>Bibliotheek</td>
    <td>YAML-bestanden laden en dumpen</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/web-token/jwt-framework"> web-token/jwt-framework </a>
    </td>
    <td>Symfony-bundle</td>
    <td>JSON Object Signing and Encryption library for PHP and Symfony Bundle.</td>
  </tr>
  <tr>
    <td>
      <a href="https://github.com/webonyx/graphql-php"> webonyx/graphql-php </a>
    </td>
    <td>Bibliotheek</td>
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
    <td>Magento2-module</td>
    <td>NVT</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card
    </td>
    <td>Magento2-module</td>
    <td>NVT</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-card-account
    </td>
    <td>Magento2-module</td>
    <td>NVT</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-gift-wrapping
    </td>
    <td>Magento2-module</td>
    <td>NVT</td>
  </tr>
  <tr>
    <td>
      paypal/module-braintree-graph-ql
    </td>
    <td>Magento2-module</td>
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
      <a href="https://github.com/2tvenom/CBOREncode"> 2tvenom/cancode </a>
    </td>
    <td>Bibliotheek</td>
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
    <td>Magento2-module</td>
    <td>Vork uit de Magento Braintree 2.2.0 module door Gene Commerce for PayPal.</td>
  </tr>
  </tbody>
</table>
