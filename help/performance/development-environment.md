---
title: Ontwikkelingsomgeving Recommendations
description: Meer informatie over prestatieaanbevelingen voor het instellen van uw lokale Adobe Commerce- of Magento Open Source-ontwikkelomgeving.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 0%

---


# Aanbevelingen voor de ontwikkelomgeving

Deze pagina verstrekt aanbevelingen voor de ontwikkelomgevingen van de Handel.

## De cache verwijderen in plaats van uitschakelen

Vele ontwikkelaars neigen om alle geheime voorgeheugens op hun ontwikkelaarinstanties onbruikbaar te maken. We raden u alleen aan caches te reinigen zonder alle caches uit te schakelen. [!DNL Commerce] efficiënter werkt wanneer u [schoonmaken] in plaats van ze volledig uit te schakelen. De meeste typen caches worden zelden ongeldig gemaakt tijdens de ontwikkeling.

Als u [caches uitschakelen], adviseren wij slechts het onbruikbaar maken van de geheime voorgeheugens van de Pagina en van het Blok in ontwikkelingsinstanties. Vergeet niet alle caches tijdens het testen in te schakelen.

## Opdrachten om te voorkomen in de ontwikkelingsmodus

In de ontwikkelingswijze, stel geen bevelen voor compilatie, codegeneratie en statische inhoudsplaatsing in werking. Deze bevelen werden gebouwd voor gebruik op productiemodus slechts.

**Niet uitvoeren** productieopdrachten in ontwikkelingsmodus:

* `setup:di:compile` genereert automatisch gegenereerde klassen en geoptimaliseerde configuratiekaarten.

   ```bash
   bin/magento setup:di:compile
   ```

   In de ontwikkelingsmodus voert Magento de productie op aanvraag uit; hoeft u het programma niet uit te voeren. Als u een handtekening van een klasse hebt gewijzigd en de automatisch gegenereerde klasse opnieuw moet genereren `factories/proxies/interceptors`, verwijdert u deze klassen of de _gegenereerd_ map.

* `setup:static-content:deploy` implementeert statische inhoud voor een winkel.

   ```bash
   bin/magento setup:static-content:deploy
   ```

   In de ontwikkelingsmodus voert Magento dit op verzoek uit; hoeft u het programma niet uit te voeren.

## Normale laadtijd van pagina&#39;s op een virtuele computer

Als u zich op een VM ontwikkelt en het langer dan 2 seconden duurt om een Magento-pagina te laden, herzie uw omgevingsinstellingen.

<!-- Link definitions -->

[schoonmaken]: ../configuration/cli/manage-cache.md#clean-and-flush-cache-types
[caches uitschakelen]: ../configuration/cli/manage-cache.md#enable-or-disable-cache-types
