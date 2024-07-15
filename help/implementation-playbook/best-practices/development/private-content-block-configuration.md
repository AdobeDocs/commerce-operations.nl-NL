---
title: Tips en trucs voor blokken met persoonlijke inhoud
description: Leer beste praktijken voor het vormen van privé inhoudsblokken om winkelprestaties te optimaliseren.
role: Developer
feature: Best Practices
exl-id: a6d2f324-f9b9-4b2b-997f-36df02c37465
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Tips en trucs voor blokken met persoonlijke inhoud

Wanneer een blok met inhoud van het type private de variabele `_isScopePrivate` bevat, kan het blok niet in cache worden geplaatst. Omdat het privéblok niet in de cache is opgeslagen, moet Adobe Commerce dezelfde gegevens ophalen voor elke aanvraag van de klant die de serverlading verhoogt.

In plaats van de variabele `_isScopePrivate` te gebruiken voor persoonlijke inhoud, maakt u een blok en een sjabloon om gebruikersbewuste gegevens weer te geven. Deze gegevens worden vervangen door gebruikersspecifieke gegevens door de Adobe Commerce UI-component, die het renderen van gegevens efficiënter afhandelt. Voor instructies, zie [ Privé Inhoud ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/) in _[!DNL Commerce PHP Extensions Guide]_.

## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Mogelijke gevolgen voor de prestaties

Sites met persoonlijke inhoudsblokken die de `_isScopePrivate` -variabelen bevatten, AJAX aanvragen om dezelfde gegevens voor elke klantaanvraag op te halen. Dit verhoogt reactietijd en gebruikt extra middelen die zouden kunnen worden gebruikt om meer zaken-kritieke archiefverrichtingen zoals klantenregistratie, winkelwagentupdates, orderindiening, en betalingstransacties te behandelen.

## Aanvullende informatie

- [Persoonlijke inhoud](../../../performance/configuration.md#client-side-optimization-settings)
- [ Hoge productie AJAX verzoeken veroorzaken slechte prestaties ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/high-throughput-ajax-requests-cause-poor-performance.html)
