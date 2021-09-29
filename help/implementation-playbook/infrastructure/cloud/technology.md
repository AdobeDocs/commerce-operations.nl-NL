---
title: Cloud Infrastructure Technologies
description: Bekijk de verzameling van technologie die we gebruiken voor Adobe Commerce op cloudinfrastructuur nader.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Technologieën

Zoals we al hebben aangegeven, gebruikt Adobe Commerce een aantal softwareoplossingen om het platform te ondersteunen. In het bijzonder hebben we, wat de productie betreft, een aantal van de technische oplossingen en functies van de Adobe Commerce op cloudinfrastructuur opgesplitst die u helpen uw productieomgeving optimaal te benutten.

![Diagram van de Adobe Commerce over de technologie van de wolkeninfrastructuur](../../../assets/playbooks/infrastructure-technology.svg)

## Softwareoplossingen

- **Nginx** - Webserver met PHP-FPM. Er is één geval met veelvoudige arbeiders.

- **GlusterFS**—Bestandsserver voor het beheer van alle statische bestandsimplementaties en synchronisatie met vier directory-installaties:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**—Eén server per VM met slechts één actief en de andere twee als replica&#39;s.

- **Elasticsearch**-Onderzoek naar versie 2.2.x van de Handel van de Adobe en later.

- **Galera**—Database-cluster met één MariaDB MySQL-database per knooppunt met een automatisch verhogende instelling van drie voor unieke id&#39;s in elke database.

## Functies en voordelen

- Met drie specifieke instanties in een VPC, is er een elastische taakverdelingsmechanisme over drie afzonderlijke beschikbaarheidsstreken of gegevenscentra.

- Hogere veerkracht wordt verstrekt tegen gebeurtenissen die één enkele instantie kunnen veroorzaken om te ontbreken. Bijvoorbeeld, een stroomonderbreking van een volledige AWS beschikbaarheidsstreek of gegevenscentrum.

- Nul downtime schalen over de gehele stapel, inclusief web, caching, search en database, in minder dan 15 minuten.
