---
title: Beste praktijken voor de Configuratie van het Rapport
description: Optimaliseer siteprestaties door de rapportmodule te verwijderen als u deze niet gebruikt.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# Beste praktijken voor rapportconfiguratie

Als uw zaken niet rapporterend of dynamische functionaliteit van de klantensegmenten vereisen, maak de [ functionaliteit van Rapporten ](https://experienceleague.adobe.com/en/docs/commerce-admin/config/general/reports) onbruikbaar om opslagprestaties te verbeteren.

## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Rapportage uitschakelen

Als u niet de Rapporten of dynamische klantensegmenten gebruikt, maak de functionaliteit van Rapporten onbruikbaar.

1. Van Admin, navigeer aan **Opslag** > **Montages** > **Configuratie** > **Algemeen** > **Rapporten**.
1. Onder **Algemene Opties**, plaats **laat Rapporten** aan *Nr* toe.
1. Het geheime voorgeheugen van de flush door `php bin/magento cache:flush` of in Admin in werking te stellen onder **Systeem** > **Hulpmiddelen** > **het Beheer van het Geheime voorgeheugen**.

## Aanvullende informatie

- [ produceer rapporten in Adobe Commerce ](https://experienceleague.adobe.com/en/docs/commerce-admin/start/reporting/reports-menu)
- [ dynamische segmenten van de Klant ](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments)
