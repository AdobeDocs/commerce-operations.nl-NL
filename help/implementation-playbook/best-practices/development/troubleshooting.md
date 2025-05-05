---
title: Problemen met aanbevolen werkwijzen oplossen
description: Leer hoe u problemen met de Adobe Commerce-implementatie kunt oplossen.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Problemen met aanbevolen werkwijzen oplossen

Volg deze best practices voor effectieve probleemoplossing voor Adobe Commerce bij problemen met cloudinfrastructuur.

## Betrokken producten en versies

Adobe Commerce over cloudinfrastructuur

## Aanbevolen procedures

| Type uitgave | Aanbevolen procedures | Bron |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Implementatieproblemen | **volg plaatsing beste praktijken.** 13% van de ondersteuningstickets heeft betrekking op implementatieproblemen. De beste praktijken zijn bijgewerkt om manieren te omvatten om vele van deze oorzaken te verhinderen. | [ Beste praktijken voor bouwt en plaatsing ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) in onze ontwikkelaarsdocumentatie. |
| Problemen met site-down | **gebruik de Troubleshooter van de Plaats neer.** Crons kan lang lopen en elkaar overschrijden. Zij zijn de bron van vele stroomonderbrekingen en prestatieskwesties. | [ Plaats onderaan Troubleshooter ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=nl-NL) en [ hoe te breinbanen ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=nl-NL) in onze basis van de steunkennis terugstellen. |
| Prestatieproblemen | **als u geen banner van Adobe Commerce gebruikt, maak het onbruikbaar.** Wanneer de banner is ingeschakeld maar niet wordt gebruikt, worden bronnen gebruikt om zoekopdrachten uit te voeren naar de database wanneer deze niet vereist zijn. Hierdoor treden prestatieproblemen op. | [ maak de output van de Banner van Adobe Commerce onbruikbaar om prestaties ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html?lang=nl-NL) in onze basis van de steunkennis te verbeteren. |
| Zoekproblemen | **MySQL de motor van het catalogusonderzoek werd verwijderd in Adobe Commerce 2.4.0.** u moet de opstelling van de Elasticsearch gastheer hebben en voorafgaand aan het installeren van versie 2.4.0 worden gevormd. Raadpleeg Installeren en configureren van Elasticsearch in de documentatie voor ontwikkelaars. | [ de dienst van de Elasticsearch van de opstelling ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) in onze ontwikkelaarsdocumentatie. |
| Aangepaste fouten | **stelt niet tijdens piektijden op.** Door gebruikers toe te voegen en te verwijderen, wordt een implementatie geactiveerd. | [ Nul onderbreking plaatsing ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime) in onze ontwikkelaarsdocumentatie. |
| Databasefouten en -problemen | **de kwesties van het Gegevensbestand veroorzaken plaatsing (posthakkwesties), prestaties en plaats neer situaties.** Veel hiervan bevatten fouten of onvoldoende toewijzing van databaseruimte. | [ de Codes van de Fout MariaDB ](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [ leidt de Ruimte van de Opslag ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) (met inbegrip van gegevensbestand) in onze ontwikkelaarsdocumentatie. |
| Configuratieproblemen | **Index door Programma in plaats van Index bij sparen.** Dit is de meest efficiënte indexeringsconfiguratie. Index bij Opslaan zorgt voor volledige re-indexering. | [ vorm indexeerders ](../../../configuration/cli/manage-indexers.md#configure-indexers) in onze ontwikkelaarsdocumentatie. |
| Aangepaste codeproblemen | **controleer uw langzame vraaglogboeken voor kansen om processen te identificeren en misschien te doden die teveel tijd nemen om te voltooien.** Trage query&#39;s kunnen databasestandaarden veroorzaken, wat leidt tot een daling van de site en prestatieproblemen. | [ het controleren langzame vragen en processen die te lang in MySQL ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html?lang=nl-NL) nemen |
| Problemen met extensies | **slechts gebruik momenteel geverifieerde uitbreidingen op de Commerce Marketplace.** | [ Uitbreidingen voor Adobe Commerce ](https://marketplace.magento.com/extensions.html) |
| Bronproblemen | **Monitor beschikbaar geheugen en ruimte en optimaliseer opslag.** U hebt mogelijk ruimte beschikbaar vóór een handeling die aanzienlijke bronnen gebruikt (bijvoorbeeld implementatie). Een slechte optimalisatie van de bestandsopslag (bijvoorbeeld te veel grote, rijke afbeeldingen) kan ook tot onvoldoende ruimte leiden. De lage middelen veroorzaken prestatieskwesties, plaats neer, vastgelopen plaatsingen, en plaatsingsmislukkingen. | [ beheer schijfruimte ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) in onze ontwikkelaarsdocumentatie; [ de opslag van het Dossier laag/uitgeput, zijn de specifieke paginaladingen langzaam ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=nl-NL) in onze basis van steunkennis. |
