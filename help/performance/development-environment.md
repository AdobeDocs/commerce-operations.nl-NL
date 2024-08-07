---
title: Ontwikkelingsomgeving Recommendations
description: Meer informatie over prestatieaanbevelingen voor het instellen van uw lokale Adobe Commerce-ontwikkelomgeving.
exl-id: f57396c0-86be-4933-8066-eb51c42fb9e4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# Aanbevelingen voor de ontwikkelomgeving

Deze pagina bevat aanbevelingen voor Commerce-ontwikkelomgevingen.

## De cache verwijderen in plaats van uitschakelen

Vele ontwikkelaars neigen om alle geheime voorgeheugens op hun ontwikkelaarinstanties onbruikbaar te maken. We raden u alleen aan caches te reinigen zonder alle caches uit te schakelen. [!DNL Commerce] loopt efficiënter wanneer u [ de geheime voorgeheugens ](../configuration/cli/manage-cache.md#clean-and-flush-cache-types) zuivert in plaats van hen volledig onbruikbaar te maken. De meeste typen caches worden zelden ongeldig gemaakt tijdens de ontwikkeling.

Als u [ de geheime voorgeheugens ](../configuration/cli/manage-cache.md#enable-or-disable-cache-types) onbruikbaar maakt, adviseren wij slechts het onbruikbaar maken van de geheime voorgeheugens van de Pagina en van het Blok in ontwikkelingsinstanties. Vergeet niet alle caches tijdens het testen in te schakelen.

## Opdrachten om te voorkomen in de ontwikkelingsmodus

In de ontwikkelingswijze, stel geen bevelen voor compilatie, codegeneratie en statische inhoudsplaatsing in werking. Deze bevelen werden gebouwd voor gebruik op productiemodus slechts.

**stel** productiebevelen op ontwikkelingswijze niet in werking:

* `setup:di:compile` genereert automatisch gegenereerde klassen en geoptimaliseerde configuratiekaarten.

  ```bash
  bin/magento setup:di:compile
  ```

  In de ontwikkelingsmodus voert het Magento de generatie op aanvraag uit; u hoeft deze niet uit te voeren. Als u een handtekening van een klasse wijzigde en zijn auto-geproduceerde `factories/proxies/interceptors` opnieuw moet produceren, verwijder die klassen of de _geproduceerde_ omslag.

* `setup:static-content:deploy` implementeert statische inhoud voor een winkel.

  ```bash
  bin/magento setup:static-content:deploy
  ```

  In de ontwikkelingsmodus voert het Magento het op aanvraag uit; u hoeft het niet uit te voeren.

## Normale laadtijd van pagina&#39;s op een virtuele computer

Als u zich op een VM ontwikkelt en het langer dan 2 seconden duurt om een pagina van het Magento te laden, herzie uw milieu montages.
