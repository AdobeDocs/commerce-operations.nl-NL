---
title: Platforms
description: Kies de aanbevolen platformgereedschappen voor uw Adobe Commerce-implementatie.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Platform tools

Er is geen gebrek aan aspecten die goed doordacht en streng getest moeten zijn om een elektronische plaats te houden die zonder interferentie loopt. Niet alleen moet u de juiste oplossingen identificeren om elk aspect van de plaats-van gegevensopslag en programmering aan caching en veiligheid aan te pakken—maar u hebt het juiste proces nodig om de levering van een platform te verzekeren dat zowel regelmatig loopt en efficiënt kan worden gebouwd en worden geoptimaliseerd.

Deze sectie biedt niet alleen een overzicht van de hulpmiddelen, de oplossingen, de processen, en de methodologieën die over een aantal implementaties van Adobe Commerce zijn getest en geperfectioneerd, maar ook onze aanbevelingen waarvoor de oplossingen specifieke bedrijfsbehoeften en doelstellingen het best passen.

De volgende tabel bevat oplossingen die wij aanbevelen en die in Adobe Commerce kunnen worden gebruikt om de prestaties op het platform te verbeteren:

| Doel | Gereedschap |
|------------------------------------------|-------------------------|
| Database | MySQL, MariaDB, Percona |
| Programming language | PHP, JS, HTML, LESS CSS |
| Geïntegreerde ontwikkelomgeving (IDE) | Eclipse, PHPStorm |
| Web server | Nginx, Apache |
| Caching | Redis, Varnish |
| Search services | Elasticsearch |
| Berichtenrijservices | KonijnMQ |
| Beveiligingsscan | SonarQube, ZAP |

## Database

There are three different tools that we use depending on the needs of the brand. MySQL is een fantastische basisoplossing als de Adobe Commerce-database als u niet verwacht dat uw winkel extreme belastingen kan verwerken.

MariaDB is more community-focused and works better for users who care more about features than pure performance. MariaDB ondersteunt een groot aantal database-engines, schijfcodering, complexe horizontale interconnectiviteit en schaalfuncties, wat interessant kan zijn voor grote Adobe Commerce-winkels.

Percona is een vork in MySQL die zich richt op prestaties en piekbelasting behandeling. Choose MariaDB if you need more quality of life and DevOps features. Go for Percona if your goal is to gain high-load performance in large-scale datasets.

## Programming language

Adobe Commerce is a PHP-based application and the newest releases are always compatible with the latest stable PHP version (for example, Adobe Commerce version 2.4 recommends using PHP 7.4). To get more security and performance, there are several factors to account for when configuring PHP to get maximum speed and efficiency on request processing. The Adobe Commerce web storefront is built with HTML, JavaScript, and the LESS CSS pre-processor.

## Webservers

Adobe Commerce biedt volledige ondersteuning voor de Nginx- en Apache-webservers. Adobe Commerce biedt voorbeelden van aanbevolen configuratiebestanden voor beide:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

The Nginx sample contains settings for better performance and is designed so that little reconfiguration is required.

## Caching

Adobe Commerce biedt een groot aantal opties voor het opslaan van uw cache- en sessiegegevens, waaronder Redis, Memcache, bestandssysteem en database. Redis is de beste optie voor het instellen met meerdere webknooppunten.

Wij adviseren hoogst gebruikend Varnish als full-page geheim voorgeheugenserver voor uw opslag. Adobe Commerce verspreidt een voorbeeldconfiguratiebestand voor Varnish dat alle aanbevolen instellingen voor de prestaties bevat.

## Search services

Voor Adobe Commerce versie 2.4 en hoger moeten alle installaties zo zijn geconfigureerd dat Elasticsearch als zoekoplossing voor catalogi wordt gebruikt. Elasticsearch biedt snelle en geavanceerde zoekopdrachten naar producten in de catalogus. Elasticsearch is optional for releases prior to 2.4, but it’s recommended.

## Message queue services

Message queues provide an asynchronous communication mechanism in which the sender and the receiver of a message do not contact each other. RabbitMQ is een open-source berichtbroker die een betrouwbaar, hoogst beschikbaar, scalable, en draagbaar overseinensysteem aanbiedt.

## Beveiligingsgereedschappen

The [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html) enables you to regularly monitor your store websites and receive updates for known security risks, malware, and out-of-date software. Doorgaans gebruikt u dit gereedschap wanneer u met het testen van gebruikersacceptatie (UAT) begint. Naast het Adobe Commerce Security Scan-hulpprogramma, dat gratis is en beschikbaar is voor alle implementaties en versies van Adobe Commerce, zijn er andere opties die kunnen worden gebruikt tijdens het CI/CD-proces en voor elke release.

SonarQube is an open-source quality management platform, designed to analyze and measure your code’s technical quality. SonarQube biedt niet alleen een volledig rapport van codefouten, syntaxisfouten en kwetsbaarheden, maar ook suggesties en voorbeelden voor het corrigeren van de code. SonarQube is perfect to use in a CI/CD environment as a tool capable of analyzing the code before it’s deployed.

Zed Attack Proxy (ZAP) is een gratis hulpprogramma voor het testen van de beveiliging dat door duizenden pentesters over de hele wereld wordt gebruikt. ZAP wordt ontwikkeld door OWASP en is een van de meest geschikte hulpmiddelen voor handmatige beveiligingstests.
