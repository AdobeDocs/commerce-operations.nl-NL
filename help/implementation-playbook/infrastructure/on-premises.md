---
title: On-premises Infrastructure
description: Meer informatie over de Adobe Commerce-infrastructuur op locatie en cloudservices van derden.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '631'
ht-degree: 0%

---


# Adobe Commerce on-premises infrastructure

The motivations for starting a new Adobe Commerce implementation or moving an existing on-premises Adobe Commerce implementation to the cloud are numerous, but the most common strategic drivers are reducing capital expenditure, decreasing ongoing cost, improving scalability and elasticity, improving time-to-market, and attaining improvements in security and compliance.

The following diagram shows the reference architecture for deploying Adobe Commerce on-premises on AWS infrastructure. Andere cloudproviders zoals Azure, Google Cloud en Alibaba Cloud delen een vergelijkbaar infrastructuurontwerp en homologe services.

![Diagram met de zelfgehoste Adobe Commerce-infrastructuur op cloudservices van derden](../../assets/playbooks/on-premises-infrastructure.svg)

Laten we dieper ingaan op de rollen en functies van elk aspect van de infrastructuur die hierboven wordt weergegeven:

1. Amazon Route 53 verstrekt DNS configuratie.

1. AWS WAF is een webtoepassingsfirewall die Adobe Commerce beschermt tegen veelvoorkomende webmisbruiken.

1. Amazon CloudFront is een snel netwerk voor het leveren van inhoud (CDN) dat de verspreiding van statische en dynamische webinhoud versnelt.

1. Het eerste Elastic Load Balancing Application Load balancer distribueert verkeer over verschillende instanties in een AWS Auto Scaling-groep in meerdere beschikbaarheidszones.

1. Varnish Cache is een HTTP reverse-proxy die in cache wordt geplaatst door een webtoepassing. De bedrijfsversie, die beschikbaar is via AWS Marketplace, wordt aanbevolen omdat deze over betere functies beschikt voor de ondersteuning van cloudback-ups en het leegmaken van cache op verschillende dynamische hosts.

1. Het tweede Elastic Load Balancing Application Load balancer verdeelt verkeer van Varnish Cache over de AWS Auto Scaling Group of Adobe Commerce instances in meerdere Beschikbaarheidszones.

1. Install the latest version of Magento Open Source or Adobe Commerce on Amazon EC2 instances. Installation consists of the Adobe Commerce application, Nginx webserver, and PHP. Bouw het Amazon Machine Image (AMI) om nieuwe exemplaren in een Auto Scaling-groep te lanceren.

1. Amazon Elasticsearch Service is een beheerde Elasticsearch-service voor het zoeken naar catalogi van Adobe Commerce.

1. Amazon ElastiCache voor Redis biedt een cachelaag voor de database.

1. Use Amazon Aurora or AmazonRDS to simplify database administration (including high availability and multi-master configuration).

1. EFSMount Target maakt het mogelijk om het Amazon Elastic File System (AmazonEFS) toe te wijzen aan instanties van Varnish en Adobe Commerce.

1. Amazon EFS van het gebruik om tot gedeelde configuratie over Varnish en gedeelde media activa over de instanties van de Handel van de Adobe toegang te hebben.

## Cloudservices

In addition to providing a supporting technology platform for the enablement of DevOps processes on AWS around your Adobe Commerce environment, AWS provides a collection of services that can provide (in the absence of) or augment your existing software configuration management (SCM) solutions. This includes AWSCodeCommit, AWSCodeBuild, AWSCodePipeline, and AWSCodeDeploy, which allows for a managed source control, build, continuous integration/continuous deployment (CI/CD), and deployment services.

## Cloud-migratie

The value proposition for migrating Adobe Commerce to AWS is further enhanced by the availability of several services that provide operational insight and agility. What we mean is operational insight into the platform from not only a technical perspective (for exmaple, requests per hour) but also a business operational perspective (for example, orders per hour), particularly when the two sets of data can be married. This provides a near-real-time look into campaign performance, platform operations costs, and a near infinite number of other indicators.

Adobe Commerce-instelling bij AWS kan specifieke toepassingsafhankelijkheden vervangen door volledig beheerde alternatieven die beschikbaar zijn in de cloud. In plaats van bijvoorbeeld rechtstreeks een relationele database op EC2-instanties te hosten, kan de database voor veel toepassingen eenvoudig worden vervangen door AmazonRDS (Amazon Relational Database Service). Het voordeel van deze strategie is dat de operationele verantwoordelijkheid van ongedifferentieerde componenten aan AWS kan worden overgeheveld zonder dat de kerntoepassing ingrijpend moet worden gewijzigd.

There are several deployment options available for running Adobe Commerce (both Magento Open Source and Adobe Commerce versions) on AWS. De meest geschikte keuze is afhankelijk van uw vereisten op het gebied van kosten, schaal, beschikbaarheid en flexibiliteit, en van de AWS- en Adobe Commerce-vaardigheden van uw organisatie.
