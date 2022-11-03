---
title: Productlimieten
description: Leer beste praktijken voor het vormen van de Eenheden van het Bewaren van het Product (SKUs) om plaatsprestaties te maximaliseren.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---


# Aanbevolen procedures voor SKU-configuratie van product

Om de prestaties te maximaliseren, is het geadviseerde maximum voor efficiënte het Houden Eenheden van het Product (SKUs) 10 miljoen. Dit effectieve productmaximum wordt berekend als:

`Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups`

Als u meer dan het maximale aantal effectieve SKU&#39;s hebt, vertraagt u het ophalen van productgegevens en neemt de tijd voor het voltooien van beheerbewerkingen toe.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Het aantal producten verminderen

Gebruik de volgende strategieën om het aantal producten (SKU&#39;s) te verminderen:

- Multipliers minimaliseren—
   - Als u winkels of websites verplaatst, vermindert u de vermenigvuldiger. Als u 50.000 SKUs, tien Websites, en tien Groepen van de Klant hebt, is het Effectieve Aantal SKUs 5 miljoen. Het verwijderen van vijf Klantengroepen vermindert Effectieve SKUs tot 2.5 miljoen.
   - Gebruik alternatieve productfuncties voor aangepaste prijzen om gedeelde catalogus en klantgroepvermenigvuldigers te vervangen.
- De catalogus herstructureren—
   - Verminder het aantal producten dat aan categorieën wordt toegewezen.
   - Verlaag het aantal SKU&#39;s door het aantal winkels, websites, klantengroepen of producten te verminderen.
- Verstrek meer productvariaties door douaneopties te gebruiken in plaats van het creëren van afzonderlijke producten.
- Deactiveer of verwijder ongebruikte systeemcomponenten zoals modules. (Zie  [Modules verwijderen](../../../installation/tutorials/uninstall-modules.md).)
- Producten beheren in een extern PMS (Platform Management System).

## Aanvullende informatie

- [Een product maken](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Producttoewijzingen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- Wolkeninfrastructuur: [Meerdere websites en winkels instellen](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Op het terrein: [Meerdere websites of winkels](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce op cloudinfrastructuur: Beste praktijken voor archiefconfiguratie](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
