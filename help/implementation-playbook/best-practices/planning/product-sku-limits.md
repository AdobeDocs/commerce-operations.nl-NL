---
title: Productlimieten
description: Leer beste praktijken voor het vormen van de Eenheden van het Bewaren van het Product (SKUs) om plaatsprestaties te maximaliseren.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e259f9b999566447469200c93db3bc4ba06434c0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Aanbevolen procedures voor SKU-configuratie van product

Om de prestaties te maximaliseren, is het geadviseerde maximum voor efficiënte product het Houting Units (SKUs) 242 miljoen. Dit effectieve SKU-maximum wordt berekend als:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Waar:

- N staat als het aantal artikelen voor die categorie
- De groepen van de klant omvatten gedeelde catalogi, aangezien het een extra klantengroep creeert.

Als u meer dan het maximale aantal effectieve SKU&#39;s hebt, vertraagt u het ophalen van productgegevens en neemt de tijd voor het voltooien van bewerkingen of indexaties in het deelvenster Beheer toe.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Het aantal producten verminderen

Gebruik de volgende strategieën om het aantal producten (SKU&#39;s) te verminderen:

- Multipliers minimaliseren—
   - Door websites te consolideren vermindert u de vermenigvuldiger. Als u 50.000 SKUs, tien Websites, en tien Groepen van de Klant hebt, is het Effectieve Aantal SKUs 5 miljoen. Het verwijderen van vijf Klantengroepen vermindert Effectieve SKUs tot 2.5 miljoen.
   - Gebruik alternatieve productfuncties voor aangepaste prijzen om gedeelde catalogus en klantgroepvermenigvuldigers te vervangen.
   - Zowel de klantengroepen als de gedeelde catalogusfunctie als vermenigvuldigers voor het aantal efficiënte SKUs in een opslag.
- De catalogus herstructureren—
   - Verminder het aantal producten dat aan categorieën wordt toegewezen.
   - Verlaag het aantal SKU&#39;s door het aantal websites, klantengroepen, gedeelde catalogi, het aantal producten of het aantal configureerbare productopties te verminderen
- Verstrek meer productvariaties door douaneopties te gebruiken in plaats van het creëren van afzonderlijke producten.
- Rekening houdend met het feit dat een effectieve SKU een aantal mogelijke prijsschommelingen kan omvatten, omdat de prijzen per winkel of klantengroep verschillend kunnen worden gespecificeerd.
- Deactiveer of verwijder ongebruikte systeemcomponenten zoals modules. (Zie  [Modules verwijderen](../../../installation/tutorials/uninstall-modules.md).)
- Producten beheren in een extern PMS (Platform Management System).

## Aanvullende informatie

- [Een product maken](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Producttoewijzingen](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Werken met gedeelde catalogi](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- Wolkeninfrastructuur: [Meerdere websites en winkels instellen](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Op het terrein: [Meerdere websites of winkels](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce op cloudinfrastructuur: Beste praktijken voor archiefconfiguratie](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
