---
title: Aanbevolen werkwijzen voor configuratie van productkenmerken
description: Leer hoe u de Adobe Commerce-prestaties kunt optimaliseren door het aantal productkenmerken, kenmerkopties en kenmerksets te beperken
role: User, Admin
feature: Best Practices, Catalogs
exl-id: 81783a4c-bc82-4733-bee3-0154cf03079a
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Aanbevolen procedures voor de configuratie van productkenmerken

- Voor de beste prestaties, vorm niet meer dan het maximum geadviseerde aantal productattributen of opties van productattributen.

- **Productkenmerken**—
   - Voor Adobe Commerce versie 2.3.x en 2.4.0 tot 2.4.1-p1 configureert u maximaal 500 kenmerken
   - Voor Adobe Commerce versie 2.4.2 en hoger kunt u maximaal 1500 productkenmerken configureren
- **Opties voor productkenmerken**-Vorm tot 100 attributenopties voor elk attribuut
- **Productkenmerksets**-Vorm een maximum van 1000 attributenreeksen _
>[!NOTE]
>
>Productkenmerken geven functies aan die wereldwijd op alle producten van toepassing zijn. De kenmerkopties van het product zijn aanpassingen om eigenschappen te specificeren die op specifieke producten van toepassing zijn.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Aantal productkenmerken verminderen

Voor de beste prestaties bij het beheren van producten bij de beheerder en het ophalen van productgegevens in de winkel:

- Gebruik verschillende productsjablonen (kenmerksets) voor verschillende producten.
- Gebruik aangepaste opties en complexe producten voor variatiebeheer
- Minimaliseer het aantal doorzoekbare kenmerken.
- Producteigenschappen verwijderen die niet worden gebruikt.
- Niet-handelsgerelateerde kenmerken opslaan en beheren in externe productbeheersystemen (PMS).

## Opties voor kenmerken van numerieke producten reduceren

Voor de beste prestaties bij het beheren van producten bij de beheerder en het ophalen van productgegevens in de winkel:

- Verschillende variatiemechanismen gebruiken om producten te maken: complexe producten, aangepaste opties als bron van productvariaties.
- Stel specifieke productsjablonen samen met doelkenmerken en -opties om algemene productsjablonen en optiecontainers te voorkomen.
- Een lijst met werkelijke kenmerkopties bijhouden.
- Productinformatie beheren via een extern productbeheersysteem (PMS).

## Aantal sets productkenmerken verkleinen

Verwijder ongebruikte productkenmerksets met MySQL.

### Configuratie kenmerkenset controleren

1. [Verbinding maken met de sitedatabase](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Het aantal kenmerksets zoeken met MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Verwijder ongebruikte kenmerksets.

## Mogelijke gevolgen voor de prestaties

Veel configureren **productkenmerken** Hiermee wordt de productsjabloongrootte voor elk product (EAV-structuur) verhoogd en de hoeveelheid gegevens die moet worden opgehaald. Deze verhoging beïnvloedt verrichtingen op de volgende manieren:

- Verhoging van SQL vraagverkeer met betrekking tot EAV gegevensherwinning en de hoeveelheid verwerkte gegevens die in verminderde productie van DB resulteert
- Significante toename van de grootte van Adobe Commerce-indexen en de full-text zoekindex
- Harde MySQL-limieten bereiken bij het samenstellen van een FLAT-index voor grote productsjablonen en het niet gebruiken ervan

De verhogingen van productgegevens en indexgrootte kunnen plaatsprestaties op de volgende manieren beïnvloeden:

- De hogere reactietijd voor de meeste storefrontscenario&#39;s met betrekking tot catalogusdoorbladeren, (snel en geavanceerd) onderzoek, en gelaagde navigatie.
- Het beheer van producten in de beheerder vertraagt aanzienlijk, wat kan leiden tot time-outs.
- Functionaliteit voor productomassa kan worden geblokkeerd.
- De de herbouwingstijd van de index voor middelgrote en grote catalogi kan niet op een dagelijkse basis wegens lange uitvoeringstijden worden uitgevoerd.

Veel configureren **kenmerkopties** kan de prestaties van de site op de volgende manieren beïnvloeden:

- Langdurige verzoek- en weergavetijden voor productdetails (PDP) en categoriepagina&#39;s die complexe producten bevatten.
- Bewerkingen voor het opslaan van beheerproducten reactietijd neemt toe boven optimale prestatiedoelen.
- Verhoging van de rendertijd in Product Edit.
- Langzaam uitchecken.

## Aanvullende informatie

- [Overzicht van productkenmerken](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Kenmerksets](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Een product maken](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Aanpassingszelfstudies > Formulier voor het maken van producten aanpassen](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)
