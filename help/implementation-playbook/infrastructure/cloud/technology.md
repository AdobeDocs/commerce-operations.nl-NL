---
title: Cloud Infrastructure Technologies
description: Bekijk de verzameling van technologie die we voor Adobe Commerce gebruiken op cloudinfrastructuur nader.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Technologieën

Zoals we al hebben gezegd, gebruikt Adobe Commerce een aantal softwareoplossingen om het platform te ondersteunen. In het bijzonder hebben we, wat de productie betreft, een aantal technische oplossingen en functies in Adobe Commerce op cloudinfrastructuur opgesplitst die u helpen uw productieomgeving optimaal te benutten.

![Diagram van de Adobe Commerce over cloudinfrastructuurtechnologie](../../../assets/playbooks/infrastructure-technology.svg)

## Softwareoplossingen

- **Nginx**—Webserver met PHP-FPM. Er is één geval met veelvoudige arbeiders.

- **GlusterFS**—Bestandsserver voor het beheer van alle statische bestandsimplementaties en synchronisatie met vier directory-installaties:
   - `var`
   - `pub/media`
   - `pub/static`
   - `app/etc`

- **Redis**—Eén server per VM met slechts één actief en de andere twee als replica&#39;s.

- **Elasticsearch**—Zoeken naar Adobe Commerce versie 2.2.x en hoger.

- **OpenSearch**—Zoeken naar Adobe Commerce versie 2.4.6 en hoger.

- **Galera**—Databasecluster met één MariaDB MySQL-database per knooppunt met een instelling voor automatisch verhogen van drie voor unieke id&#39;s in elke database.

## Functies en voordelen

- Met drie specifieke instanties in een VPC, is er een elastische taakverdelingsmechanisme over drie afzonderlijke beschikbaarheidsstreken of gegevenscentra.

- Hogere veerkracht wordt verstrekt tegen gebeurtenissen die één enkele instantie kunnen veroorzaken om te ontbreken. Bijvoorbeeld, een stroomonderbreking van een volledige AWS beschikbaarheidsstreek of gegevenscentrum.

- Nul downtime schalen over de gehele stapel, inclusief web, caching, search en database, in minder dan 15 minuten.
