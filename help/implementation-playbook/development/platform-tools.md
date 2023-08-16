---
title: Platform Tools
description: Kies de aanbevolen platformgereedschappen voor uw Adobe Commerce-implementatie.
exl-id: 3fc164f9-a0fc-46e7-a54e-08ce101ccae7
feature: Configuration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# Platformgereedschappen

Er is geen gebrek aan aspecten die goed doordacht en streng getest moeten zijn om een elektronische plaats te houden die zonder interferentie loopt. Niet alleen moet u de juiste oplossingen identificeren om elk aspect van de plaats-van gegevensopslag en programmering aan caching en veiligheid aan te pakken-maar u hebt het juiste proces nodig om de levering van een platform te verzekeren dat zowel regelmatig loopt en efficiënt kan worden gebouwd en worden geoptimaliseerd.

Deze sectie biedt niet alleen een overzicht van de hulpmiddelen, de oplossingen, de processen, en de methodologieën die over een aantal implementaties van Adobe Commerce zijn getest en geperfectioneerd, maar ook onze aanbevelingen waarvoor de oplossingen specifieke bedrijfsbehoeften en doelstellingen het best passen.

De volgende tabel bevat oplossingen die wij aanbevelen en die in Adobe Commerce kunnen worden gebruikt om de prestaties op het platform te verbeteren:

| Doel | Gereedschap |
|------------------------------------------|-------------------------|
| Database | MySQL, MariaDB, Percona |
| Programmeertaal | PHP, JS, HTML, LESS CSS |
| Geïntegreerde ontwikkelomgeving (IDE) | Eclipse, PHPStorm |
| Webserver | Nginx, Apache |
| Caching | Redis, Varnish |
| Zoeken in services | Elasticsearch |
| Berichtenrijservices | [!DNL RabbitMQ] |
| Beveiligingsscan | SonarQube, ZAP |

## Database

Er zijn drie verschillende instrumenten die we gebruiken afhankelijk van de behoeften van het merk. MySQL is een geweldige basislijnoplossing als de Adobe Commerce-database als u niet verwacht dat uw winkel extreme belastingen kan verwerken.

MariaDB is meer gericht op de gemeenschap en werkt beter voor gebruikers die meer om eigenschappen dan zuivere prestaties geven. MariaDB ondersteunt een groot aantal database-engines, schijfcodering, complexe horizontale interconnectiviteit en schaalfuncties, wat interessant kan zijn voor grote Adobe Commerce-winkels.

Percona is een vork in MySQL die zich richt op prestaties en piekbelasting behandeling. Kies MariaDB als u meer levenskwaliteit en DevOps-functies nodig hebt. Ga voor Percona als uw doel high-load prestaties in grote datasets moet bereiken.

## Programmeertaal

Adobe Commerce is een PHP-gebaseerde toepassing en de nieuwste releases zijn altijd compatibel met de nieuwste stabiele PHP versie (Adobe Commerce versie 2.4 raadt bijvoorbeeld aan om PHP 7.4 te gebruiken). Om meer veiligheid en prestaties te krijgen, zijn er verschillende factoren die bij het configureren van PHP voor maximale snelheid en efficiëntie bij de verwerking van aanvragen in aanmerking moeten worden genomen. De Adobe Commerce-webwinkel is gebouwd met HTML, JavaScript en de LESS CSS-voorprocessor.

## Webservers

Adobe Commerce biedt volledige ondersteuning voor de Nginx- en Apache-webservers. Adobe Commerce biedt voorbeelden van aanbevolen configuratiebestanden voor beide:

- **Nginx**—`<magento_home>/nginx.conf.sample`
- **Apache**—`<magento_home>.htaccess.sample`

Het Nginx-voorbeeld bevat instellingen voor betere prestaties en is zo ontworpen dat weinig herconfiguratie nodig is.

## Caching

Adobe Commerce biedt een groot aantal opties voor het opslaan van uw cache- en sessiegegevens, waaronder Redis, Memcache, bestandssysteem en database. Redis is de beste optie voor het instellen met meerdere webknooppunten.

Wij adviseren hoogst gebruikend Varnish als full-page geheim voorgeheugenserver voor uw opslag. Adobe Commerce verspreidt een voorbeeldconfiguratiebestand voor Varnish dat alle aanbevolen instellingen voor de prestaties bevat.

## Zoeken in services

Voor Adobe Commerce versie 2.4 en hoger moeten alle installaties zo zijn geconfigureerd dat Elasticsearch of OpenSearch als zoekoplossing voor catalogi wordt gebruikt. Elasticsearch biedt snelle en geavanceerde zoekopdrachten naar producten in de catalogus. Elasticsearch is optioneel voor releases vóór 2.4, maar wordt aangeraden.

## Berichtenrijservices

De rijen van het bericht verstrekken een asynchroon communicatie mechanisme waarin de afzender en de ontvanger van een bericht niet elkaar contacteren. [!DNL RabbitMQ] is een open-bron berichtbroker die een betrouwbaar, hoogst beschikbaar, scalable, en draagbaar overseinensysteem aanbiedt.

## Beveiligingsgereedschappen

De [Adobe Commerce Security Scan](https://docs.magento.com/user-guide/magento/security-scan.html) biedt u de mogelijkheid om uw websites van uw winkel regelmatig te controleren en updates te ontvangen voor bekende beveiligingsrisico&#39;s, malware en verouderde software. Doorgaans gebruikt u dit gereedschap wanneer u met het testen van gebruikersacceptatie (UAT) begint. Naast het Adobe Commerce Security Scan-hulpprogramma, dat gratis is en beschikbaar is voor alle implementaties en versies van Adobe Commerce, zijn er andere opties die kunnen worden gebruikt tijdens het CI/CD-proces en voor elke release.

SonarQube is een open-source platform voor kwaliteitsbeheer, ontworpen om de technische kwaliteit van uw code te analyseren en te meten. SonarQube biedt niet alleen een volledig rapport van codefouten, syntaxisfouten en kwetsbaarheden, maar ook suggesties en voorbeelden voor het corrigeren van de code. SonarQube is perfect voor gebruik in een CI/CD-omgeving als hulpmiddel om de code te analyseren voordat deze wordt geïmplementeerd.

Zed Attack Proxy (ZAP) is een gratis hulpprogramma voor het testen van de beveiliging dat door duizenden pentesters over de hele wereld wordt gebruikt. ZAP wordt ontwikkeld door OWASP en is een van de meest geschikte hulpmiddelen voor handmatige beveiligingstests.
