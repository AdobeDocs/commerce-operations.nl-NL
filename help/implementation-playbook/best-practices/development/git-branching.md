---
title: Aanpassen aan vertakkende aanbevolen werkwijzen
description: Leer over verschillende vertakkende strategieën voor broncodebeheer.
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Aanpassen aan vertakkende aanbevolen werkwijzen

De Source-code doorloopt meerdere stabiliteitsfasen tijdens het ontwikkelingsproces:

- Actieve ontwikkeling
- Eerste codeintegratie
- Codeintegratie voor kwaliteitsborging (QA)
- Codeintegratie voor het testen van de eindgebruikeracceptatie (UAT)
- Definitieve code-integratie voor productieleveringen

## Betrokken producten en versies

[&#x200B; Alle gesteunde versies &#x200B;](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce in gebouwen

## Branchebeheer

Elke ontwikkelingsfase zou een overeenkomstige tak in Git moeten hebben om codeveranderingen te volgen en het plaatsingsproces te vergemakkelijken:

- **tak van de Taak** - waar de ontwikkelaars hun individuele codeveranderingen begaan terwijl het uitvoeren van specifieke taken, zoals eigenschappen en insectenmoeilijke situaties.
- **tak van de Ontwikkeling** - waar de veelvoudige ontwikkelaars veranderingen van hun individuele taaktakken in één enkele ontwikkelingstak voor geautomatiseerde integratie het testen samenvoegen. Deze vertakking wordt opgesteld aan een ontwikkelomgeving.
- **vertakking QA** - waar de ontwikkelaars veranderingen samenvoegen nadat de ontwikkeling volledig is en de code al geautomatiseerde integratie het testen en codeoverzicht heeft overgegaan. Deze tak wordt opgesteld aan het milieu QA voor het hand testen QA.
- **Stable/UAT tak** - waar de code wordt samengevoegd nadat het handtest QA overgaat. Deze tak wordt opgesteld aan een milieu van UAT voor het testen van de gebruikersaanvaarding.
- **de Vertakking van de Productie/van de versie** - waar de code wordt samengevoegd nadat het UAT overgaat. Deze tak wordt opgesteld aan productie voor een versie.

>[!TIP]
>
>Adobe Commerce op cloud-infrastructuurprojecten bevatten specifieke vertakkingen die overeenkomen met verschillende omgevingen. Zie het [&#x200B; Pro projectwerkschema &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=nl-NL) en [&#x200B; het projectwerkschema van de Aanzet &#x200B;](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html?lang=nl-NL) in de _Gids van de Wolk_.

## Branch-strategieën

Er zijn verschillende vertakkingsstrategieën die u kunt gebruiken. Kies een strategie die het beste werkt voor uw ontwikkelingsteam en de complexiteit van uw project.

Zie de volgende externe bronnen voor meer informatie:

- [&#x200B; Vertakkende werkschema&#39;s &#x200B;](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [&#x200B; Verdeelde werkschema&#39;s &#x200B;](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [&#x200B; Patronen voor het beheren van broncodetakken &#x200B;](https://martinfowler.com/articles/branching-patterns.html)
- [&#x200B; Een succesvolle het vertakken van het Git model &#x200B;](https://nvie.com/posts/a-successful-git-branching-model/)
- [&#x200B; GitHub stroom &#x200B;](https://docs.github.com/en/get-started/quickstart/github-flow)
- [&#x200B; GitLab stroom &#x200B;](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
