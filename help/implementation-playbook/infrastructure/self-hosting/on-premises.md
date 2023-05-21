---
title: Infrastructuur op locatie
description: Meer informatie over Adobe Commerce-infrastructuur op locatie en cloudservices van derden.
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: de1467be-acec-4a0d-8229-e7e87614bc55
source-git-commit: a253da8cfe95083d1df76d3253aaa424b78a4865
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---

# Adobe Commerce-infrastructuur ter plaatse

De redenen voor het starten van een nieuwe Adobe Commerce-implementatie of het verplaatsen van een bestaande Adobe Commerce-implementatie op locatie naar de cloud zijn talrijk, maar de meest voorkomende strategische drijfveer is het verlagen van de kapitaaluitgaven, het verlagen van de lopende kosten, het verbeteren van de schaalbaarheid en de elasticiteit, het verbeteren van de tijd tot aan de markt en het bereiken van verbeteringen op het gebied van beveiliging en naleving.

Het volgende diagram toont de verwijzingsarchitectuur voor het opstellen van Adobe Commerce op-gebouw op de infrastructuur van AWS. Andere cloudproviders zoals Azure, Google Cloud en Alibaba Cloud delen een vergelijkbaar infrastructuurontwerp en homologe services.

![Diagram met zelfgehoorzame Adobe Commerce-infrastructuur op cloudservices van derden](/help/assets/playbooks/on-premises-infrastructure.svg)

Laten we dieper ingaan op de rollen en functies van elk aspect van de infrastructuur die hierboven wordt getoond:

1. Amazon Route 53 verstrekt DNS configuratie.

1. AWS WAF is een webtoepassingsfirewall die Adobe Commerce beschermt tegen veelvoorkomende webmisbruiken.

1. Amazon CloudFront is een snel netwerk voor het leveren van inhoud (CDN) dat de verspreiding van statische en dynamische webinhoud versnelt.

1. Het eerste Elastic Load Balancing Application Load balancer distribueert verkeer over verschillende instanties in een AWS Auto Scaling-groep in meerdere beschikbaarheidszones.

1. Varnish Cache is een HTTP reverse-proxy die in cache wordt geplaatst door een webtoepassing. De bedrijfsversie, die beschikbaar is via AWS Marketplace, wordt aanbevolen omdat deze betere functies biedt voor de ondersteuning van cloudback-ups en het leegmaken van cache op verschillende dynamische hosts.

1. Het tweede Elastic Load Balancing Application Load balancer distribueert verkeer van Varnish Cache over de AWS Auto Scaling Group van Adobe Commerce-instanties in meerdere Beschikbaarheidszones.

1. Installeer de nieuwste versie van Magento Open Source of Adobe Commerce op Amazon EC2-exemplaren. De installatie bestaat uit de Adobe Commerce-toepassing, Nginx-webserver en PHP. Bouw het Amazon Machine Image (AMI) om nieuwe exemplaren in een Auto Scaling-groep te lanceren.

1. Amazon Elasticsearch Service is een beheerde Elasticsearch-service voor het zoeken naar catalogi in Adobe Commerce.

1. Amazon ElastiCache voor Redis biedt een cachelaag voor de database.

1. Gebruik Amazon Aurora of AmazonRDS om databasebeheer te vereenvoudigen (inclusief hoge beschikbaarheid en multi-master configuratie).

1. EFSMount Target maakt het mogelijk om het Amazon Elastic File System (AmazonEFS) toe te wijzen aan instanties van Varnish en Adobe Commerce.

1. Gebruik Amazon EFS om toegang te krijgen tot gedeelde configuratie in verschillende versies en gedeelde media-elementen in Adobe Commerce-instanties.

## Cloudservices

Naast het verstrekken van een ondersteunend technologieplatform voor het inschakelen van processen DevOps op AWS rond uw milieu van Adobe Commerce, verstrekt AWS een inzameling van de diensten die (bij afwezigheid van) uw bestaande oplossingen van het het beheer van de softwareconfiguratie (SCM) kunnen verstrekken of verbeteren. Dit omvat AWSCodeCommit, AWSCodeBuild, AWSCodePipeline, en AWSCodeDeploy, die voor een beheerde broncontrole, bouwstijl, ononderbroken integratie/ononderbroken plaatsing (CI/CD), en plaatsingsdiensten toestaat.

## Cloud-migratie

Het waardevoorstel voor het migreren van Adobe Commerce naar AWS wordt verder verbeterd door de beschikbaarheid van verschillende diensten die operationeel inzicht en flexibiliteit bieden. Wat we bedoelen is operationeel inzicht in het platform vanuit niet alleen een technisch perspectief (bijvoorbeeld verzoeken per uur) maar ook vanuit een operationeel perspectief voor het bedrijfsleven (bijvoorbeeld orders per uur), vooral wanneer de twee gegevenssets kunnen worden gehuwd. Dit verstrekt bijna-real-time onderzoek naar campagneprestaties, de kosten van platformverrichtingen, en een bijna oneindig aantal andere indicatoren.

Adobe Commerce-configuratie voor AWS kan specifieke toepassingsafhankelijkheden vervangen door volledig beheerde alternatieven die beschikbaar zijn in de cloud. In plaats van bijvoorbeeld rechtstreeks een relationele database op EC2-instanties te hosten, kan de database voor veel toepassingen eenvoudig worden vervangen door AmazonRDS (Amazon Relational Database Service). Het voordeel van deze strategie is dat de operationele verantwoordelijkheid van ongedifferentieerde onderdelen naar AWS kan worden overgeheveld zonder dat de kerntoepassing ingrijpend moet worden gewijzigd.

Er zijn verschillende implementatieopties beschikbaar voor het uitvoeren van Adobe Commerce (zowel Magento Open Source- als Adobe Commerce-versies) op AWS. De meest geschikte keuze is afhankelijk van uw vereisten op het gebied van kosten, schaal, beschikbaarheid en flexibiliteit, en van de AWS- en Adobe Commerce-vaardigheden van uw organisatie.

{{$include /help/_includes/hosting-related-links.md}}
