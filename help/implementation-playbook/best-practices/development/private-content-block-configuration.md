---
title: Tips en trucs voor blokken met persoonlijke inhoud
description: Leer beste praktijken voor het vormen van privé inhoudsblokken om winkelprestaties te optimaliseren.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Tips en trucs voor blokken met persoonlijke inhoud

Wanneer een blok met persoonlijke inhoud het `_isScopePrivate` variabele, is het blok niet cacheable. Omdat het privéblok niet in de cache is opgeslagen, moet Adobe Commerce dezelfde gegevens ophalen voor elke aanvraag van de klant die de serverlading verhoogt.

In plaats van de `_isScopePrivate` voor privé inhoud, creeer een blok en een malplaatje om user-agnostische gegevens te tonen. Deze gegevens worden vervangen door gebruikersspecifieke gegevens door de Adobe Commerce [UI-component](https://glossary.magento.com/ui-component/), waardoor gegevens vóór rendering efficiënter worden verwerkt. Zie voor instructies [Persoonlijke inhoud](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in de _[!DNL Commerce PHP Extensions Guide]_.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Mogelijke gevolgen voor de prestaties

Sites met persoonlijke inhoudsblokken die de `_isScopePrivate` variabelen brengen AJAX verzoeken teweeg om de zelfde gegevens voor elke klantenverzoek terug te winnen. Dit verhoogt reactietijd en gebruikt extra middelen die zouden kunnen worden gebruikt om meer zaken-kritieke archiefverrichtingen zoals klantenregistratie, winkelwagentupdates, orderindiening, en betalingstransacties te behandelen.

## Aanvullende informatie

- [Persoonlijke inhoud](../../../performance/configuration.md#client-side-optimization-settings)
- [De hoge productie AJAX verzoeken veroorzaken slechte prestaties](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)

