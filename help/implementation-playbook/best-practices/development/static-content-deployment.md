---
title: Aanbevolen werkwijzen voor implementatie van statische inhoud
description: Leer hoe u problemen met statische inhoud kunt voorkomen die niet in uw Adobe Commerce-winkel worden weergegeven.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor implementatie van statische inhoud

In dit artikel wordt gesproken over de best practices voor het implementeren van statische inhoud (SCD) in Adobe Commerce om problemen te voorkomen waarbij de statische inhoud niet beschikbaar zou zijn op uw website.

## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

* Adobe Commerce over cloudinfrastructuur
* Adobe Commerce ter plaatse

## Aanbevolen procedures

Als u wilt voorkomen dat er problemen optreden met statische inhoud die niet beschikbaar is op uw website, volgt u de volgende aanbevolen procedures om ervoor te zorgen dat uw statische inhoud zowel op de juiste wijze wordt geconfigureerd als geïmplementeerd:

1. Volg de richtlijnen voor implementatie:
   * Voor Adobe Commerce op-gebouw (alle versies), zie [ Overzicht van de Plaatsing ](../../../configuration/deployment/overview.md) in onze ontwikkelaarsdocumentatie.
   * Voor Adobe Commerce op wolkeninfrastructuur (alle versies), zie [ het plaatsingsproces van de Wolk ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/process) en [ Statische strategieën van de inhoudsplaatsing ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/static-content) in onze ontwikkelaarsdocumentatie.

1. Voor Adobe Commerce op cloudinfrastructuur (alle versies) dient u ervoor te zorgen dat de nieuwere release beschikbaar is. Zie: [ update knoop-hulpmiddelen versie ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) in onze ontwikkelaarsdocumentatie.
1. Voor Adobe Commerce op wolkeninfrastructuur (alle versies), zorg ervoor dat de statische inhoud tijdens de bouwfase eerder dan de plaatsingsfase wordt opgesteld. Zie: [ beheer van de Configuratie voor opslagmontages - de Statische prestaties van de inhoudsplaatsing ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over) in onze ontwikkelaarsdocumentatie.
1. Zorg ervoor dat u geen lange-lopende kroonbanen hebt en doden om het even welke langlopende kroonprocessen. Langlopende bouwtaken kunnen CPU-bronnen in beslag nemen en de implementatietijd aanzienlijk vergroten.
1. Voor Adobe Commerce (alle versies) controleert u op locatie of het `php` -proces in CLI toegang heeft tot de map `pub/static` . Anders zou u een probleem kunnen tegenkomen waarbij een statische inhoud niet kan worden geïmplementeerd om bestanden naar die map te schrijven. Voor meer informatie: [ de toegangstoestemmingen van de systeemtoegang van het Dossier ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
1. Zorg ervoor dat de map `generated` geen gedeelde map is voor alle builds, anders kunnen builds willekeurig mislukken. Voor meer informatie:
   * Adobe Commerce op-gebouw (alle versies): [ Technische Details ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
   * Adobe Commerce op wolkeninfrastructuur (alle versies): [ het proces van de Plaatsing - Fase 2: bouw ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build) in onze ontwikkelaarsdocumentatie.

1. Controleer uw SCD-strategie. De *snelle* strategie is het gebrek. Voor meer informatie:
   * Adobe Commerce op-gebouw (alle versies): [ Statische strategieën van de dossierplaatsing ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html?lang=nl-NL) in onze ontwikkelaarsdocumentatie.
   * Adobe Commerce op wolkeninfrastructuur (alle versies): [ stel variabelen op - SCD \_STRATEGY ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy) in onze ontwikkelaarsdocumentatie.

## Aanvullende informatie

In onze documentatie voor ontwikkelaars:

* [ de Statische Container van de Inhoud ](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [ Statische Inhoud die ](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html?lang=nl-NL) ondertekenen
* [ stel variabelen op - STATIC\_CONTENT \_SYMLINK ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [Implementatiestroom](../../../performance/deployment-flow.md)
* [ Nul onderbreking plaatsing ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [ optimaliseer wolkenplaatsing ](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
