---
title: Beste praktijken voor de Configuratie van het Rapport
description: Optimaliseer siteprestaties door de rapportmodule te verwijderen als u deze niet gebruikt.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Beste praktijken voor rapportconfiguratie

Als uw zaken geen rapportering of dynamische functionaliteit van de klantensegmenten vereisen, maak onbruikbaar [Functie voor rapporten](https://docs.magento.com/user-guide/configuration/general/reports.html) om de prestaties van de winkel te verbeteren.

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
