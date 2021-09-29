---
title: Platforms
description: Kies aanbevolen platformhulpmiddelen voor uw Adobe Commerce-implementatie.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Gereedschappen voor Platforms

Er is geen gebrek aan aspecten die goed doordacht en streng getest moeten zijn om een elektronische plaats te houden die zonder interferentie loopt. Niet alleen moet u de juiste oplossingen identificeren om elk aspect van de plaats-van gegevensopslag en programmering aan caching en veiligheid aan te pakken—maar u hebt het juiste proces nodig om de levering van een platform te verzekeren dat zowel regelmatig loopt en efficiënt kan worden gebouwd en worden geoptimaliseerd.

This section offers not only a look at the tools, solutions, processes, and methodologies that have been tested and perfected over a number of Adobe Commerce implementations, but also our recommendations for which solutions best fit specific business needs and objectives.

The following table includes solutions that we recommend and can be used within Adobe Commerce to drive performance on the platform:

| Doel | Tool |
|------------------------------------------|-------------------------|
| Database | MySQL, MariaDB, Percona |
| Programmeertaal | PHP, JS, HTML, LESS CSS |
| Geïntegreerde ontwikkelomgeving (IDE) | Eclipse, PHPStorm |
| Web server | Nginx, Apache |
| Caching services | Redis, Varnish |
| Search services | Elasticsearch |
| Berichtenrijservices | RabbitMQ |
| Beveiligingsscan | SonarQube, ZAP |

## Datbase

Er zijn drie verschillende instrumenten die we gebruiken afhankelijk van de behoeften van het merk. MySQL is a great baseline solution as the Adobe Commerce database if you don’t expect your store to handle extreme loads.

MariaDB is meer gericht op de gemeenschap en werkt beter voor gebruikers die meer om eigenschappen dan zuivere prestaties geven. MariaDB ondersteunt een groot aantal database-engines, schijfcodering, complexe horizontale interconnectiviteit en schaalfuncties, wat interessant kan zijn voor grote Adobe Commerce-winkels.

Percona is een vork in MySQL die zich richt op prestaties en piekbelasting behandeling. Kies MariaDB als u meer levenskwaliteit en DevOps-functies nodig hebt. Ga voor Percona als uw doel high-load prestaties in grote datasets moet bereiken.

## Programmeertaal

Adobe Commerce is een PHP-toepassing en de nieuwste releases zijn altijd compatibel met de nieuwste stabiele PHP versie (Adobe Commerce versie 2.4 raadt bijvoorbeeld aan PHP 7.4 te gebruiken). Om meer veiligheid en prestaties te krijgen, zijn er verschillende factoren die bij het configureren van PHP voor maximale snelheid en efficiëntie bij de verwerking van aanvragen in aanmerking moeten worden genomen. De Adobe Commerce-webwinkel is gebouwd met HTML, JavaScript en de LESS CSS-voorprocessor.

## Webservers

Adobe Commerce biedt volledige ondersteuning voor de Nginx- en Apache-webservers. De Handel van de Adobe verstrekt steekproef geadviseerde configuratiedossiers voor allebei:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

The Nginx sample contains settings for better performance and is designed so that little reconfiguration is required.

## Caching services

Adobe Commerce provides numerous options to store your cache and session data, including Redis, Memcache, filesystem, and database. For a setup with multiple web nodes, Redis is the best option.

Wij adviseren hoogst gebruikend Varnish als full-page geheim voorgeheugenserver voor uw opslag. De Handel van de Adobe verspreidt een dossier van de steekproefconfiguratie voor Varnish dat alle geadviseerde montages voor prestaties bevat.

## Search services

Voor Adobe Commerce versie 2.4 en recenter, moeten alle installaties worden gevormd om Elasticsearch als oplossing van de catalogusonderzoek te gebruiken. Elasticsearch provides quick and advanced searches on products in the catalog. Elasticsearch is optioneel voor versies ouder dan 2.4, maar wordt aangeraden.

## Message queue services

Message queues provide an asynchronous communication mechanism in which the sender and the receiver of a message do not contact each other. RabbitMQ is an open-source message broker that offers a reliable, highly available, scalable, and portable messaging system.

## Security tools

The [Adobe Commerce Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html) enables you to regularly monitor your store websites and receive updates for known security risks, malware, and out-of-date software. Doorgaans gebruikt u dit gereedschap wanneer u met het testen van gebruikersacceptatie (UAT) begint. Besides the Adobe Commerce Security Scan tool, which is free and available for all implementations and versions of Adobe Commerce, there are other choices that can be used during the CI/CD process and before each release.

SonarQube is an open-source quality management platform, designed to analyze and measure your code’s technical quality. SonarQube biedt niet alleen een volledig rapport van codefouten, syntaxisfouten en kwetsbaarheden, maar ook suggesties en voorbeelden voor het corrigeren van de code. SonarQube is perfect to use in a CI/CD environment as a tool capable of analyzing the code before it’s deployed.

Zed Attack Proxy (ZAP) is een gratis hulpprogramma voor het testen van de beveiliging dat door duizenden pentesters over de hele wereld wordt gebruikt. ZAP wordt ontwikkeld door OWASP en is een van de meest geschikte hulpmiddelen voor handmatige beveiligingstests.
