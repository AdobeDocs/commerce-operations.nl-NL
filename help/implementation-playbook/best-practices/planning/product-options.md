---
title: Aanbevolen werkwijzen voor productopties
description: Optimaliseer de Adobe Commerce-prestaties door het aantal productopties te beperken.
role: Admin
feature: Best Practices, Catalogs
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor productopties

Voor de beste prestaties configureert u maximaal 100 productopties per product.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Productopties verlagen

Gebruik de volgende strategieën om het aantal productopties te verminderen voor de beste prestaties van de site:

- Complexe producten en aangepaste opties configureren als bron van productvariaties.
- In plaats van globale productmalplaatjes en optiecontainers te creëren die op alle producten van toepassing zijn, gebruik attributenreeksen om specifieke productmalplaatjes met gerichte attributen en opties te bouwen.
- Productinformatie beheren via een extern productbeheersysteem (PMS).

## Mogelijke gevolgen voor de prestaties

Als u veel productopties configureert, neemt de hoeveelheid gegevens die voor elk product wordt opgehaald bij alle lees- en schrijfbewerkingen toe. Dit resulteert in:

- Verhoogd SQL vraagverkeer en zwaarder `JOIN` De verrichtingen verhogen gegevensbestandproductie.
- Grotere grootte voor Adobe Commerce-indexen en de zoekindex met volledige tekst.

De hierboven vermelde verhogingen beïnvloeden mogelijk de prestaties van de site op de volgende manieren:

- Langere reactietijd voor de meeste storefrontscenario&#39;s met betrekking tot producten die vele opties in attributen bevatten.
- De tijd die nodig is om de productbeheerbewerkingen in Admin te voltooien neemt aanzienlijk toe, wat kan leiden tot time-outs, met name voor scenario&#39;s met betrekking tot de lijst van kenmerken en het opvragen van bomen, waaronder het beheer van promotieregels.
- Kan bulkacties blokkeren die asynchrone massabewerkingen zoals importeren en exporteren voltooien en aangepaste prijzen toewijzen aan meerdere producten in een gedeelde catalogus.

## Aanvullende informatie

- [Een product maken](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Aanbevolen procedures voor de configuratie van productkenmerken](product-attributes-and-options.md)
- [Logbestand voor bulkacties](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [Handelingen voor inventarismassa](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Training: Catalogi en producten beheren met Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
