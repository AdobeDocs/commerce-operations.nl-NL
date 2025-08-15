---
title: Admin-updates plannen op productiesites
description: Leer beste praktijken voor het plannen van kritieke updates aan Adobe Commerce om langzame prestaties en stroomonderbrekingen te verhinderen.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---

# Aanbevolen procedures voor het plannen van Admin-updates op productiesites

Plan kritieke updates en bewerkingen op uw Adobe Commerce-sites tijdens niet-piekuren om langzame prestaties en uitval op productiesites te voorkomen.

Voorbeelden van kritieke acties:

- Wijzigingen in de beheerdersconfiguratie, bijvoorbeeld het bijwerken van een productkenmerk of het verplaatsen van een productsubcategorie naar een andere categorie
- Invoer- of uitvoerbewerkingen van gegevens

Kritieke acties leiden tot invalidatie en herindexering van het cachegeheugen, waardoor de responstijd aanzienlijk toeneemt en er problemen kunnen ontstaan met de site.

## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Aanvullende informatie

- [ Beste praktijken voor caching ](https://experienceleague.adobe.com/nl/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [ Privé inhoud: Valideer privé inhoud ](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Hardware-aanbevelingen: Caches](../../../performance/hardware.md#caches)
- [Geavanceerde instellingen: Redis instellen](../../../performance/advanced-setup.md#set-up-redis)
