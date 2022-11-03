---
title: Aanbevolen werkwijzen voor implementatie van statische inhoud
description: Leer hoe u problemen met statische inhoud kunt voorkomen die niet op uw Adobe Commerce- of Magento Open Source-winkel worden weergegeven.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---


# Aanbevolen werkwijzen voor implementatie van statische inhoud

In dit artikel wordt gesproken over de best practices voor het implementeren van statische inhoud (SCD) in Adobe Commerce om problemen te voorkomen waarbij de statische inhoud niet beschikbaar zou zijn op uw website.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

* Adobe Commerce over cloudinfrastructuur
* Adobe Commerce ter plaatse
* Magento Open Source

## Aanbevolen procedures

Als u wilt voorkomen dat er problemen optreden met statische inhoud die niet beschikbaar is op uw website, volgt u de volgende aanbevolen procedures om ervoor te zorgen dat uw statische inhoud zowel op de juiste wijze wordt geconfigureerd als geïmplementeerd:

1. Volg de richtlijnen voor implementatie:
   * Voor Adobe Commerce on-premiss en Magento Open Source (alle versies), zie [Implementatieoverzicht](../../../configuration/deployment/overview.md) in onze ontwikkelaarsdocumentatie.
   * Voor Adobe Commerce over cloudinfrastructuur (alle versies) raadpleegt u [Implementatieproces voor cloud](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) en [Statische strategieën voor implementatie van inhoud](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) in onze ontwikkelaarsdocumentatie.

1. Voor Adobe Commerce op cloudinfrastructuur (alle versies) dient u ervoor te zorgen dat de nieuwere release beschikbaar is. Zie: [Versie van gereedschappen bijwerken](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) in onze ontwikkelaarsdocumentatie.
1. Voor Adobe Commerce op wolkeninfrastructuur (alle versies), zorg ervoor dat de statische inhoud tijdens de bouwfase eerder dan de plaatsingsfase wordt opgesteld. Zie: [Configuratiebeheer voor opslaginstellingen - Statische prestaties voor de implementatie van inhoud](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) in onze ontwikkelaarsdocumentatie.
1. Zorg ervoor dat u geen lange-lopende kroonbanen hebt en doden om het even welke langlopende kroonprocessen. Langlopende bouwtaken kunnen CPU-bronnen in beslag nemen en de implementatietijd aanzienlijk vergroten.
1. Voor Adobe Commerce op locatie en Magento Open Source (alle versies) controleert u of de `php` proces in CLI heeft toegang tot `pub/static` directory. Anders zou u een probleem kunnen tegenkomen waarbij een statische inhoud niet kan worden geïmplementeerd om bestanden naar die map te schrijven. Voor meer informatie: [Toegangsrechten voor bestandssystemen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) in onze ontwikkelaarsdocumentatie.
1. Zorg ervoor dat de `generated` directory is geen gedeelde directory voor builds; anders zouden builds willekeurig kunnen mislukken . Voor meer informatie:
   * Adobe Commerce op locatie en Magento Open Source (alle versies): [Technische details](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) in onze ontwikkelaarsdocumentatie.
   * Adobe Commerce op cloudinfrastructuur (alle versies): [Implementatieproces - Fase 2: build](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) in onze ontwikkelaarsdocumentatie.

1. Controleer uw SCD-strategie. De *snel* strategie is de standaardinstelling. Voor meer informatie:
   * Adobe Commerce op locatie en Magento Open Source (alle versies): [Statische strategieën voor bestandsimplementatie](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) in onze ontwikkelaarsdocumentatie.
   * Adobe Commerce op cloudinfrastructuur (alle versies): [Variabelen implementeren - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) in onze ontwikkelaarsdocumentatie.

## Aanvullende informatie

In onze documentatie voor ontwikkelaars:

* [Container met statische inhoud](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Statische inhoud ondertekenen](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Variabelen implementeren - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Implementatiestroom](../../../performance/deployment-flow.md)
* [Implementatie zonder downtime](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [cloudimplementatie optimaliseren](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)

