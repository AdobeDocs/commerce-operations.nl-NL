---
title: Problemen met aanbevolen werkwijzen oplossen
description: Leer hoe u problemen met de Adobe Commerce-implementatie kunt oplossen.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---


# Problemen met aanbevolen werkwijzen oplossen

Volg deze best practices voor effectieve probleemoplossing voor Adobe Commerce bij problemen met cloudinfrastructuur.

## Betrokken producten en versies

Adobe Commerce over cloudinfrastructuur

## Aanbevolen procedures

| Type uitgave | Aanbevolen procedures | Resource |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Implementatieproblemen | **Volg de best practices voor implementatie.** 13% van de ondersteuningstickets heeft betrekking op implementatieproblemen. De beste praktijken zijn bijgewerkt om manieren te omvatten om vele van deze oorzaken te verhinderen. | [Aanbevolen werkwijzen voor builds en implementatie](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) in onze ontwikkelaarsdocumentatie. |
| Problemen met site-down | **Gebruik de Troubleshooter van de Plaats neer.** Crons kunnen lang lopen en elkaar overschrijden. Zij zijn de bron van vele stroomonderbrekingen en prestatieskwesties. | [Problemen met site-onderaan oplossen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) en [Uitsnijdtaken herstellen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) in onze kennisbasis voor ondersteuning. |
| Prestatieproblemen | **Schakel de banner uit als u geen Adobe Commerce-banner gebruikt.** Wanneer de banner wordt toegelaten maar niet gebruikt, worden de middelen gebruikt om raadplegingen aan het gegevensbestand te doen wanneer zij niet worden vereist, en het zal prestatieskwesties veroorzaken. | [Uitvoer van Adobe Commerce Banner uitschakelen om de prestaties te verbeteren](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html in onze kennisbasis voor ondersteuning. |
| Zoekproblemen | **De zoekfunctie voor MySQL-catalogi is verwijderd uit Adobe Commerce 2.4.0.** U moet Elasticsearch host-instellingen hebben en geconfigureerd voordat u versie 2.4.0 installeert. Raadpleeg Installeren en configureren van Elasticsearch in de documentatie voor ontwikkelaars. | [De service Elasticsearch instellen](https://devdocs.magento.com/cloud/project/services-elastic.html) in onze ontwikkelaarsdocumentatie. |
| Aangepaste fouten | **Implementeer niet tijdens piektijden.** Het toevoegen van en het verwijderen van gebruikers zullen een plaatsing teweegbrengen. | [Implementatie zonder downtime](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) in onze ontwikkelaarsdocumentatie. |
| Databasefouten en -problemen | **Databasekwesties veroorzaken implementatie (posthakproblemen), prestaties en site-downsituaties.** Velen impliceren fouten of ontoereikende toewijzing van gegevensbestandruimte. | [MariaDB-foutcodes](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Opslagruimte beheren](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (inclusief database) in de documentatie voor ontwikkelaars. |
| Configuratieproblemen | **Indexeren op schema in plaats van Index bij Opslaan.** Dit is de meest efficiënte indexeringsconfiguratie. Index bij Opslaan zorgt voor volledige re-indexering. | [Indexeerders configureren](../../../configuration/cli/manage-indexers.md#configure-indexers) in onze ontwikkelaarsdocumentatie. |
| Aangepaste codeproblemen | **Controleer uw langzame vraaglogboeken voor kansen om processen te identificeren en misschien te doden die teveel tijd nemen om te voltooien.** De langzame vragen kunnen gegevensbestandblokkeringen veroorzaken die in plaatsafnames en prestatieskwesties resulteren. | [Het controleren van langzame vragen en processen die te lang in MySQL nemen](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Problemen met extensies | **Gebruik alleen geverifieerde extensies die momenteel op de Commerce Marketplace staan.** | [Extensies voor Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Bronproblemen | **Bewaak het beschikbare geheugen en de beschikbare ruimte en optimaliseer de opslagruimte.** U hebt mogelijk beschikbare ruimte vóór een handeling die aanzienlijke bronnen verbruikt (bijvoorbeeld implementatie). Een slechte optimalisatie van de bestandsopslag (bijvoorbeeld te veel grote, rijke afbeeldingen) kan ook tot onvoldoende ruimte leiden. De lage middelen veroorzaken prestatieskwesties, plaats neer, vastgelopen plaatsingen, en plaatsingsmislukkingen. | [Schijfruimte beheren](https://devdocs.magento.com/cloud/project/manage-disk-space.html) in onze documentatie voor ontwikkelaars; [Bestandsopslag laag/uitgeput, het laden van specifieke pagina&#39;s gaat traag](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) in onze kennisbasis voor ondersteuning. |
