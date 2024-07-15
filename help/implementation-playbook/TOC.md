---
user-guide-title: Afspeelmap voor implementatie
user-guide-description: Leer meer over strategieën voor het plannen en implementeren van een geslaagde Adobe Commerce-site.
mini-toc-levels: 3
source-git-commit: 36a2a86cbafab1e4913573b1c8431524ba43dc6a
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Afspeelmap voor implementatie {#implementation-playbook}

- [Overzicht](overview.md)
- Commerce {#intro}
   - [Informatie over Adobe Commerce](intro/about-commerce.md)
   - [Beginselen van platformontwikkeling](intro/platform-development.md)
- Projectbereik {#project-scope}
   - [Kennis is macht](project-scope/knowledge.md)
   - [Belangrijkste betrokkenen](project-scope/key-stakeholders.md)
   - [Proces en tijdlijn](project-scope/process-timeline.md)
   - [Te leveren items](project-scope/deliverables.md)
   - [Vereiste controlelijsten](project-scope/requirement-checklists.md)
- Ontwikkeling {#development}
   - [Platformgereedschappen](development/platform-tools.md)
   - [Projectbeheertools](development/project-management-tools.md)
   - [Methode voor projectuitvoering](development/delivery.md)
   - [Kwaliteitscontrole](development/quality-control.md)
- Planning en beheer {#planning}
   - [Bezorgings- en planningsaanpak](planning/delivery.md)
   - [Verantwoordelijkheid en verantwoordelijkheid](planning/ownership.md)
   - [Projectbeheer](planning/governance.md)
- Architectuur en integratie {#architecture}
   - [Enterprise-referentie](architecture/enterprise-blueprint.md)
   - Algemene referentiearchitectuur {#global-reference-architecture}
      - [Overzicht](architecture/global-reference/overview.md)
      - [Voorbeelden](architecture/global-reference/examples.md)
      - Ontwikkeling van composers {#composer}
         - [Overzicht](architecture/global-reference/composer/overview.md)
         - [Projectstructuur](architecture/global-reference/composer/project-structure.md)
         - [Tips en trucs](architecture/global-reference/composer/tips-and-tricks.md)
- Infrastructuur en implementatie {#infrastructure}
   - [Overzicht](infrastructure/overview.md)
   - Zelf hosten {#self-hosting}
      - [Overzicht](infrastructure/self-hosting/overview.md)
      - [ op-gebouwinfrastructuur ](infrastructure/self-hosting/on-premises.md)
      - [Beveiligingsconcepten](infrastructure/self-hosting/security-concepts.md)
      - [Bewaking van telemetrie en tools](infrastructure/self-hosting/monitoring-tools.md)
      - [Ideeën voor noodherstel](infrastructure/self-hosting/disaster-recovery-ideas.md)
      - [Tips voor prestaties](infrastructure/self-hosting/performance-tips.md)
   - Cloudinfrastructuur {#cloud}
      - [Overzicht](infrastructure/cloud/overview.md)
      - [Regio&#39;s](infrastructure/cloud/regions.md)
      - [Technologieën](infrastructure/cloud/technology.md)
      - [Beveiliging en naleving](infrastructure/cloud/security.md)
   - Prestaties optimaliseren {#performance}
      - [Typische problemen](infrastructure/performance/optimization.md)
      - [Benchmarks](infrastructure/performance/benchmarks.md)
      - [Recommendations](infrastructure/performance/recommendations.md)
- Gereedheid starten {#launch}
   - [Overzicht](launch/overview.md)
   - [Stappen vóór de introductie](launch/pre-launch-steps.md)
   - [Stappen starten](launch/launch-steps.md)
   - [Stappen voor Post](launch/post-launch-steps.md)
- Onderhoud en ondersteuning {#maintenance}
   - [Overzicht](maintenance/overview.md)
   - [Adobe Managed Services](maintenance/adobe-managed-services.md)
- Tips en trucs {#best-practices}
   - [Overzicht](best-practices/phases.md)
   - Planning {#planning}
      - [Overzicht](best-practices/planning/overview.md)
      - [Catalogusbeheer](best-practices/planning/catalog-management.md)
      - [Configuratie van sites, winkels en winkelweergave](best-practices/planning/sites-stores-store-views.md)
      - [Rapportageconfiguratie](best-practices/planning/reporting-configuration.md)
      - [Databaseconfiguratie voor cloud-implementaties &#x200B;](best-practices/planning/database-on-cloud.md)
      - [MySQL-configuratie](best-practices/planning/mysql-configuration.md)
      - [Redis-serviceconfiguratie](best-practices/planning/redis-service-configuration.md)
      - [OPcache-geheugengrootte](best-practices/planning/opcache-memory-size.md)
      - [Realpath cache-grootte](best-practices/planning/realpath-cache-size.md)
      - [Extensies](best-practices/planning/extensions.md)
      - [Partnerescalaties](best-practices/planning/partner-escalation.md)
      - [Betalingsopslagverwerking](best-practices/planning/payment-processing-storage.md)
   - Ontwikkeling {#development}
      - [Overzicht](best-practices/development/overview.md)
      - [Algemene beste praktijken](best-practices/development/general.md)
      - [Codebeheer](best-practices/development/code-management.md)
      - [Codeherziening](best-practices/development/code-review.md)
      - [Foutopsporing](best-practices/development/debugging.md)
      - [Uitzonderingsafhandeling](best-practices/development/exception-handling.md)
      - [Vertakkingen opvangen](best-practices/development/git-branching.md)
      - [Grootte van catalogusafbeelding wijzigen](best-practices/development/catalog-image-resizing.md)
      - [Optimalisatie van afbeeldingen](best-practices/development/image-optimization.md)
      - [Problemen oplossen](best-practices/development/troubleshooting.md)
      - [CSS- en JS-bestanden optimaliseren](best-practices/development/optimize-css-js-files.md)
      - [Persoonlijke inhoudsblokken](best-practices/development/private-content-block-configuration.md)
      - [Statische implementatie van inhoud](best-practices/development/static-content-deployment.md)
      - [Databasetabellen wijzigen](best-practices/development/modifying-core-and-third-party-tables.md)
      - [ Wijzend kern en derdecode ](best-practices/development/modifying-core-and-third-party-code.md)
   - Starten {#launch}
      - [Overzicht](best-practices/launch/overview.md)
      - [Webcrawlers configureren](best-practices/launch/robots-txt.md)
      - [Uw site en infrastructuur beveiligen](best-practices/launch/security-best-practices.md)
   - Onderhoud {#maintenance}
      - [Overzicht](best-practices/maintenance/overview.md)
      - [Voorwaartse controle](best-practices/maintenance/frontend-performance.md)
      - [Optimaliseer de prestaties van de backend](best-practices/maintenance/backend-performance.md)
      - [Indexeerconfiguratie](best-practices/maintenance/indexer-configuration.md)
      - [Repareren op schaal](best-practices/maintenance/patching-at-scale.md)
      - [Bestelverwerking](best-practices/maintenance/order-processing-configuration.md)
      - [Problemen met databaseprestaties oplossen](best-practices/maintenance/resolve-database-performance-issues.md)
      - [Reageren op beveiligingsincidenten](best-practices/maintenance/respond-to-security-incident.md)
      - [Admin-updates plannen op productiesites](best-practices/maintenance/scheduling-admin-updates-in-production.md)
      - [Services bijwerken](best-practices/maintenance/update-services.md)
      - [Controlelijst voor upgraden](best-practices/maintenance/upgrade-checklist.md)
      - [Voorwaarden voor upgrades voor MariaDB](best-practices/maintenance/mariadb-upgrade.md)
- [ Terugkeer aan Operationele Gidsen ](https://experienceleague.adobe.com/docs/commerce-operations/operational-guides/home.html)
