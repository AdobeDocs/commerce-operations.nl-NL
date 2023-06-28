---
title: Tips en trucs voor blokken met persoonlijke inhoud
description: Leer beste praktijken voor het vormen van privé inhoudsblokken om winkelprestaties te optimaliseren.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Tips en trucs voor blokken met persoonlijke inhoud

Wanneer een blok met persoonlijke inhoud het `_isScopePrivate` variabele, is het blok niet cacheable. Omdat het privéblok niet in de cache is opgeslagen, moet Adobe Commerce dezelfde gegevens ophalen voor elke aanvraag van de klant die de serverlading verhoogt.

In plaats van de `_isScopePrivate` voor privé inhoud, creeer een blok en een malplaatje om user-agnostische gegevens te tonen. Deze gegevens worden vervangen door gebruikersspecifieke gegevens door de Adobe Commerce UI-component, die het renderen van gegevens efficiënter afhandelt. Zie voor instructies [Persoonlijke inhoud](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in de _[!DNL Commerce PHP Extensions Guide]_.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Mogelijke gevolgen voor de prestaties

Sites met persoonlijke inhoudsblokken die de `_isScopePrivate` variabelen brengen AJAX verzoeken teweeg om de zelfde gegevens voor elke klantenverzoek terug te winnen. Dit verhoogt reactietijd en gebruikt extra middelen die zouden kunnen worden gebruikt om meer zaken-kritieke archiefverrichtingen zoals klantenregistratie, winkelwagentupdates, orderindiening, en betalingstransacties te behandelen.

## Aanvullende informatie

- [Persoonlijke inhoud](../../../performance/configuration.md#client-side-optimization-settings)
- [De hoge productie AJAX verzoeken veroorzaken slechte prestaties](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
