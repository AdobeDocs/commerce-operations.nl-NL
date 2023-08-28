---
title: Aanpassen aan vertakkende aanbevolen werkwijzen
description: Leer over verschillende vertakkende strategieën voor broncodebeheer.
feature: Best Practices
role: Developer
source-git-commit: 9b1c3f7ca56cb6baf262bbd4abc732a30a7eb0ed
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# Aanpassen aan vertakkende aanbevolen werkwijzen

De broncode gaat door veelvoudige stabiliteitsfasen tijdens het ontwikkelingsproces:

- Actieve ontwikkeling
- Eerste codeintegratie
- Codeintegratie voor kwaliteitsborging (QA)
- Codeintegratie voor het testen van de eindgebruikeracceptatie (UAT)
- Definitieve code-integratie voor productieleveringen

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce in gebouwen

## Branchebeheer

Elke ontwikkelingsfase zou een overeenkomstige tak in Git moeten hebben om codeveranderingen te volgen en het plaatsingsproces te vergemakkelijken:

- **Taaktak**—Waar ontwikkelaars hun individuele codeveranderingen begaan terwijl het uitvoeren van specifieke taken, zoals eigenschappen en insectenmoeilijke situaties.
- **Ontwikkelingstak**—Waar de veelvoudige ontwikkelaars veranderingen van hun individuele taaktakken in één enkele ontwikkelingstak voor geautomatiseerde integratietests samenvoegen. Deze vertakking wordt opgesteld aan een ontwikkelomgeving.
- **QA-vertakking**—Wanneer ontwikkelaars wijzigingen samenvoegen nadat de ontwikkeling is voltooid en de code alle automatische integratietests en coderevisie heeft doorstaan. Deze tak wordt opgesteld aan het milieu QA voor het hand testen QA.
- **Stabiel/UAT-vertakking**—Waar de code wordt samengevoegd nadat deze handmatige QA-tests heeft doorstaan. Deze tak wordt opgesteld aan een milieu van UAT voor het testen van de gebruikersaanvaarding.
- **Productie-/releaseafdeling**—Waar de code wordt samengevoegd nadat het UAT overgaat. Deze tak wordt opgesteld aan productie voor een versie.

>[!TIP]
>
>Adobe Commerce op cloud-infrastructuurprojecten bevatten specifieke vertakkingen die overeenkomen met verschillende omgevingen. Zie de [Workflow voor Pro-projecten](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html) en [Starter-projectworkflow](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html) in de _Cloud Guide_.

## Branch-strategieën

Er zijn verschillende vertakkingsstrategieën die u kunt gebruiken. Kies een strategie die het beste werkt voor uw ontwikkelingsteam en de complexiteit van uw project.

Zie de volgende externe bronnen voor meer informatie:

- [Workflows voor takken](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [Gedistribueerde workflows](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Patronen voor het beheren van broncodevertakkingen](https://martinfowler.com/articles/branching-patterns.html)
- [Een succesvol Git vertakkingsmodel](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub-stroom](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab-stroom](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
