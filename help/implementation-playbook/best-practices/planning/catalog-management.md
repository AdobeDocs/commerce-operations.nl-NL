---
title: Best practices voor catalogusbeheer
description: Meer informatie over aanbevelingen voor het configureren van kartlimieten en productkenmerken, het aanbieden van paginering, opties, promoties en variaties.
role: Developer
feature: Best Practices, Catalog Management
exl-id: 9a672017-9122-4841-a67b-a183224b67dc
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1403'
ht-degree: 0%

---

# Best practices voor catalogusbeheer

De best practices voor catalogusbeheer die hier worden beschreven, hebben betrekking op een aantal problemen, waaronder (maar niet beperkt tot):

- Grenswaarden voor winkelwagentjes
- Categoriebeperkingen
- Productkenmerken
- Paginering van productaanbiedingen
- Productopties
- Productvariaties
- Aanbiedingen

## Grenswaarden voor winkelwagentjes

Voor de beste prestaties gebruikt u de volgende richtlijnen voor het beheer van de kartellimieten voor Adobe Commerce.

### Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal winkelwagentjes verkleinen

Gebruik de volgende strategieën om het aantal winkelwagentjes te beheren

- U kunt met de functie [!UICONTROL Add Item by SKU] orders splitsen in verschillende kleinere bestellingen met een kleiner aantal rijen.
- Voeg alleen de aangepaste logica en aanpassing van het winkelwagentje toe die zijn vereist om een lijst met items te laden.

## Categoriebeperkingen

Het vormen van een groot aantal categorieën kan prestaties beïnvloeden.

### Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal producten verminderen

Gebruik de volgende strategieën om het aantal categorieën te verminderen:

- Unieke productfuncties beheren via kenmerken en aangepaste opties
- Niet-actieve categorieën verwijderen
- Catalogusdiepte optimaliseren in de navigatie

## Productkenmerken

Het configureren van te veel productkenmerken of productkenmerkopties kan de prestaties beïnvloeden.

>[!NOTE]
>
>Productkenmerken geven functies aan die wereldwijd op alle producten van toepassing zijn. De kenmerkopties van het product zijn aanpassingen om eigenschappen te specificeren die op specifieke producten van toepassing zijn.

### Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal kenmerken reduceren

Voor de beste prestaties bij het beheren van producten bij de beheerder en het ophalen van productgegevens in de winkel:

- Gebruik verschillende productsjablonen (kenmerksets) voor verschillende producten.
- Gebruik aangepaste opties en complexe producten voor variatiebeheer
- Minimaliseer het aantal doorzoekbare kenmerken.
- Producteigenschappen verwijderen die niet worden gebruikt.
- Niet-handelsgerelateerde kenmerken opslaan en beheren in externe productbeheersystemen (PMS).

### Het aantal kenmerkopties verminderen

Voor de beste prestaties bij het beheren van producten bij de beheerder en het ophalen van productgegevens in de winkel:

- Gebruik verschillende variatiemechanismen om producten te maken: complexe producten, aangepaste opties als bron van productvariaties.
- Stel specifieke productsjablonen samen met doelkenmerken en -opties om algemene productsjablonen en optiecontainers te voorkomen.
- Een lijst met werkelijke kenmerkopties bijhouden.
- Productinformatie beheren via een extern productbeheersysteem (PMS).

### Het aantal kenmerksets verminderen

Verwijder ongebruikte productkenmerksets met MySQL.

#### Configuratie kenmerkenset controleren

1. [ verbind met het plaatsgegevensbestand ](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Het aantal kenmerksets zoeken met MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Verwijder ongebruikte kenmerksets.

### Mogelijke gevolgen voor de prestaties

Vormend vele **productattributen** verhoogt de grootte van het productmalplaatje voor elk product (structuur EAV) en de hoeveelheid gegevens die moeten worden teruggewonnen. Deze verhoging beïnvloedt verrichtingen op de volgende manieren:

- Verhoging van SQL vraagverkeer met betrekking tot EAV gegevensherwinning en de hoeveelheid verwerkte gegevens die in verminderde productie van DB resulteert
- Significante toename van de grootte van Adobe Commerce-indexen en de full-text zoekindex
- Harde MySQL-limieten bereiken bij het samenstellen van een FLAT-index voor grote productsjablonen en het niet gebruiken ervan

De verhogingen van productgegevens en indexgrootte kunnen plaatsprestaties op de volgende manieren beïnvloeden:

- De hogere reactietijd voor de meeste storefrontscenario&#39;s met betrekking tot catalogusdoorbladeren, (snel en geavanceerd) onderzoek, en gelaagde navigatie.
- Het beheer van producten in de beheerder vertraagt aanzienlijk, wat kan leiden tot time-outs.
- Functionaliteit voor productomassa kan worden geblokkeerd.
- De de herbouwingstijd van de index voor middelgrote en grote catalogi kan niet op een dagelijkse basis wegens lange uitvoeringstijden worden uitgevoerd.

Vormend vele **attributenopties** kan plaatsprestaties op de volgende manieren beïnvloeden:

- Langdurige verzoek- en renderingtijden voor productdetails (PDP) en categoriepagina&#39;s die complexe producten bevatten.
- Bewerkingen voor het opslaan van beheerproducten reactietijd neemt toe boven optimale prestatiedoelen.
- Verhoging van de rendertijd in Product Edit.
- Langzaam uitchecken.

## Productopties

Het configureren van te veel productopties per product kan de prestaties beïnvloeden.

### Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal opties verminderen

Gebruik de volgende strategieën om het aantal productopties per product te verminderen:

- Complexe producten en aangepaste opties configureren als bron van productvariaties.
- In plaats van globale productmalplaatjes en optiecontainers te creëren die op alle producten van toepassing zijn, gebruik attributenreeksen om specifieke productmalplaatjes met gerichte attributen en opties te bouwen.
- Productinformatie beheren via een extern productbeheersysteem (PMS).

### Mogelijke gevolgen voor de prestaties

Als u veel productopties configureert, neemt de hoeveelheid gegevens die voor elk product wordt opgehaald bij alle lees- en schrijfbewerkingen toe. Dit resulteert in:

- Verhoogd SQL vraagverkeer en zwaardere `JOIN` verrichtingen verhogen gegevensbestandproductie.
- Grotere grootte voor Adobe Commerce-indexen en de zoekindex met volledige tekst.

De hierboven vermelde verhogingen beïnvloeden mogelijk de prestaties van de site op de volgende manieren:

- Langere reactietijd voor de meeste storefrontscenario&#39;s met betrekking tot producten die vele opties in attributen bevatten.
- De tijd die nodig is om de productbeheerbewerkingen in Admin te voltooien neemt aanzienlijk toe, wat kan leiden tot time-outs, met name voor scenario&#39;s met betrekking tot de lijst van kenmerken en het opvragen van bomen, waaronder het beheer van promotieregels.
- Kan bulkacties blokkeren die asynchrone massabewerkingen zoals importeren en exporteren voltooien en aangepaste prijzen toewijzen aan meerdere producten in een gedeelde catalogus.

## Paginering van productaanbiedingen

Het weergeven van te veel producten per pagina kan de prestaties beïnvloeden.

### Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Configuratie van productlijsten bijwerken

Als u teveel producten in een categorie hebt, werk de configuratie van de storefrontcatalogus bij om de optie onbruikbaar te maken om **Alle Producten per pagina** toe te staan.

Nadat u deze optie hebt uitgeschakeld, gebruikt Adobe Commerce de besturingselementen voor de paginering van de winkelpagina van het product om het aantal producten te beheren dat in winkelcomponenten wordt weergegeven. Voor instructies, zie [ pagineringscontroles ](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls) vormen.

## SKU-limieten voor producten

Het vormen van teveel product SKUs kan prestaties beïnvloeden door de terugwinning van productgegevens te vertragen en de tijd te verhogen om verrichtingen Admin of indexaties te voltooien.

### Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal producten verminderen

Gebruik de volgende strategieën om het aantal producten (SKU&#39;s) te verminderen:

- Multipliers minimaliseren—
   - Door websites te consolideren vermindert u de vermenigvuldiger.
   - Gebruik alternatieve productfuncties voor aangepaste prijzen om gedeelde catalogus en klantgroepvermenigvuldigers te vervangen.
   - Zowel de klantengroepen als de gedeelde catalogusfunctie als vermenigvuldigers voor het aantal efficiënte SKUs in een opslag.
- De catalogus herstructureren—
   - Verminder het aantal producten dat aan categorieën wordt toegewezen.
   - Verlaag het aantal SKU&#39;s door het aantal websites, klantengroepen, gedeelde catalogi, het aantal producten of het aantal configureerbare productopties te verminderen
- Verstrek meer productvariaties door douaneopties te gebruiken in plaats van het creëren van afzonderlijke producten.
- Rekening houdend met het feit dat een effectieve SKU een aantal mogelijke prijsschommelingen kan omvatten, omdat de prijzen per winkel of klantengroep verschillend kunnen worden gespecificeerd.
- Deactiveer of verwijder ongebruikte systeemcomponenten zoals modules. Zie [ modules ](../../../installation/tutorials/uninstall-modules.md) desinstalleren.
- Beheer producten in een extern Platform Management System (PMS).

## Productvariaties

Het configureren van te veel variaties per product kan de prestaties beïnvloeden.

### Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal variaties verminderen

Gebruik de volgende strategieën om het aantal productvariaties te verminderen voor de beste prestaties van de site:

- Herstructureer de catalogus door het aantal variaties over verschillende producten te verdelen.
- Verwijder configureerbare kenmerkopties die niet in voorraad zijn.
- U kunt variaties beheren met alternatieve functies, zoals aangepaste opties, categorieën, verwante, gegroepeerde en bundelproducten.

### Mogelijke gevolgen voor de prestaties

Het overschrijden van het aanbevolen aantal productvariaties kan op de volgende manieren van invloed zijn op de prestaties van de site:

- Langdurige aanvraag- en weergavetijden voor productdetails en categoriepagina&#39;s met complexe producten.
- Toename van reactietijd om opslagbewerkingen in de beheerder uit te voeren.
- Meer tijd om het formulier Product bewerken weer te geven.
- Langzaam uitchecken.

## Aanbiedingen

Volg deze aanbevolen procedures om verkoop en promoties voor objecten in een winkelwagentje te configureren:

- **Regels van de Verkoop (de regels van de kartprijs)**
   - Ongebruikte regels beheren en verwijderen.
   - Voeg strikte regelvoorwaarden (zoals kenmerk- of categoriefilter) toe voor de meest efficiënte overeenkomst.
- **Coupons**
   - Ongebruikte en verlopen coupons verwijderen.
   - Alleen het aantal coupons genereren dat nodig is om te voldoen aan de vereisten voor campagnes.

### Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Mogelijke gevolgen voor de prestaties

Als u meer dan het aanbevolen maximumaantal regels of coupons voor de kartonprijs hebt, kan dit de prestaties van de site op de volgende manieren beïnvloeden:

- Hogere responstijd wanneer producten aan het winkelwagentje worden toegevoegd.
- Meer tijd om de miniaturen te laden en weer te geven.
- Meer tijd om de winkelwagenpagina weer te geven.
- Verhoogde tijd om het **1} blok van Totalen {op de pagina van de Controle terug te geven.**
