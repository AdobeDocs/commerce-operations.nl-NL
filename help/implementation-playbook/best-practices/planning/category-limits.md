---
title: Best practices voor categorieconfiguratie
description: Leer beste praktijken om plaatsprestaties te maximaliseren door het aantal categorieën in de catalogus te beperken.
role: Admin
feature: Best Practices
exl-id: c6834b32-9ee8-4a4a-932c-9726f3feee3f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Aanbevolen procedures voor categorieconfiguratie

Configureer voor de beste prestaties niet meer dan het maximale aanbevolen aantal categorieën voor Adobe Commerce-sites.

- Voor Adobe Commerce versie 2.4.2 en hoger configureert u maximaal 6000 categorieën
- Voor Adobe Commerce versie 2.3.x en 2.4.0 tot 2.4.1-p1 configureert u maximaal 3000 categorieën

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Het aantal producten verminderen

Gebruik de volgende strategieën om het aantal categorieën te verminderen:

- Unieke productfuncties beheren via kenmerken en aangepaste opties
- Niet-actieve categorieën verwijderen
- Catalogusdiepte optimaliseren in de navigatie

## Mogelijke gevolgen voor de prestaties

Het hebben van meer dan het geadviseerde maximum aantal categorieën kan plaatsprestaties op de volgende manieren beïnvloeden:

- Toekenbare verlenging van de responstijd voor cataloguspagina&#39;s die niet in de cache zijn geplaatst
- Lange uitvoering en time-outs terwijl categorieën van de beheerder worden beheerd
- Grotere grootte van corresponderende databasetabellen
- De grotere indexlijsten vergen tijd wordt vereist om indexeringsverrichtingen voor te voltooien `[category/product relation index\]`
- Verhoogde verwerkingstijd om de bouw van de categorieboom, menuherwinning, en het beheersverrichtingen van categorieregels te voltooien

## Aanvullende informatie

- [Overzicht van rubrieken](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Overzicht van navigatie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Producttoewijzingen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce op cloudinfrastructuur: Beste praktijken voor archiefconfiguratie](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
