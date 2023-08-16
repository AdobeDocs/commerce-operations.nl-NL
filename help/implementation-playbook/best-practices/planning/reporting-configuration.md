---
title: Beste praktijken voor de Configuratie van het Rapport
description: Optimaliseer siteprestaties door de rapportmodule te verwijderen als u deze niet gebruikt.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Beste praktijken voor rapportconfiguratie

Als uw zaken geen rapportering of dynamische functionaliteit van de klantensegmenten vereisen, maak onbruikbaar [Functie voor rapporten](https://docs.magento.com/user-guide/configuration/general/reports.html) om de winkelprestaties te verbeteren.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Rapportage uitschakelen

Als u niet de Rapporten of dynamische klantensegmenten gebruikt, maak de functionaliteit van Rapporten onbruikbaar.

1. Navigeer vanuit Beheer naar **Winkels** > **Instellingen** > **Configuratie** > **Algemeen** > **Rapporten**.
1. Onder **Algemene opties**, set **Rapporten inschakelen** tot *Nee*.
1. Cache leegmaken door uit te voeren `php bin/magento cache:flush` of in de Admin onder **Systeem** > **Gereedschappen** > **Cachebeheer**.

## Aanvullende informatie

- [Rapporten genereren in Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Dynamische segmenten van de klant](https://docs.magento.com/user-guide/marketing/customer-segments.html)
