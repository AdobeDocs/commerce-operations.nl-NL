---
title: Best practices voor catalogusbeheer
description: Meer informatie over aanbevelingen voor het configureren van kartlimieten en productkenmerken, het aanbieden van paginering, opties, promoties en variaties.
role: Developer
feature: Best Practices, Catalog Management
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '1876'
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

Voor de beste prestaties gebruikt u de volgende richtlijnen voor het beheer van de kartellimieten voor Adobe Commerce en Magento Open Source:

- Voor versies 2.3.x - 2.4.2, sta een maximum van 100 producten in een kar toe.
- Voor versies 2.4.3 en later, verhoogde de verbetering aan verkoopregelmogelijkheden het kartmaximum tot 750.

Voor versies 2.3.x - 2.4.2, zijn de verwachte prestaties gebaseerd op de grenzen van het winkelwagentje:

- Tot maximaal **100** producten in een kar-het product werkt, die prestatiesdoelstellingen voor reactietijd bereiken.
- Tot maximaal **300** producten in een winkelwagentje - het product werkt, maar de reactietijd neemt toe boven de doelen.
- Boven **500** producten in een winkelwagentje - de winkelwagentjes en de kassa werken niet altijd

### Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal winkelwagentjes verkleinen

Gebruik de volgende strategieën om het aantal winkelwagentjes te beheren

- Hiermee splitst u ordes in verschillende kleinere bestellingen met een kleiner aantal rijen met behulp van de optie [!UICONTROL Add Item by SKU] gebruiken.
- Voeg alleen de aangepaste logica en aanpassing van het winkelwagentje toe die zijn vereist om een lijst met items te laden.

### Mogelijke gevolgen voor de prestaties

Als u meer dan het aanbevolen maximumaantal producten in de kar hebt, kan dit de prestaties van de site op de volgende manieren beïnvloeden:

- Verhoogde responstijd voor het opvragen van gegevens, validatie van winkelwagentjes, controles voor het toepassen van prijsregels, en belasting en totale berekeningen.
- Verhoogde responstijd voor minicart-rendering, inclusief rendering van cartweergaven, uitcheckflow en uitvoering.
- Verhoogde laadtijd voor alle sitepagina&#39;s waarin het minicart aanwezig is.

## Categoriebeperkingen

Configureer voor de beste prestaties niet meer dan het maximale aanbevolen aantal categorieën voor Adobe Commerce-sites.

- Voor Adobe Commerce versie 2.4.2 en hoger configureert u maximaal 6000 categorieën
- Voor Adobe Commerce versie 2.3.x en 2.4.0 tot 2.4.1-p1 configureert u maximaal 3000 categorieën

### Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal producten verminderen

Gebruik de volgende strategieën om het aantal categorieën te verminderen:

- Unieke productfuncties beheren via kenmerken en aangepaste opties
- Niet-actieve categorieën verwijderen
- Catalogusdiepte optimaliseren in de navigatie

### Mogelijke gevolgen voor de prestaties

Het hebben van meer dan het geadviseerde maximum aantal categorieën kan plaatsprestaties op de volgende manieren beïnvloeden:

- Toekenbare verlenging van de responstijd voor cataloguspagina&#39;s die niet in de cache zijn geplaatst
- Lange uitvoering en time-outs terwijl categorieën van de beheerder worden beheerd
- Grotere grootte van overeenkomstige gegevensbestandlijsten
- De grotere indexlijsten vergen tijd wordt vereist om indexeringsverrichtingen voor te voltooien `[category/product relation index\]`
- Verhoogde verwerkingstijd om de bouw van de categorieboom, menuherwinning, en het beheersverrichtingen van categorieregels te voltooien

## Productkenmerken

- Voor de beste prestaties, vorm niet meer dan het maximum geadviseerde aantal productattributen of opties van productattributen.

- **Productkenmerken**—
   - Voor Adobe Commerce versie 2.3.x en 2.4.0 tot 2.4.1-p1 configureert u maximaal 500 kenmerken
   - Voor Adobe Commerce versie 2.4.2 en hoger kunt u maximaal 1500 productkenmerken configureren
- **Opties voor productkenmerken**-Vorm tot 100 attributenopties voor elk attribuut
- **Productkenmerksets**-Vorm een maximum van 1000 attributenreeksen

>[!NOTE]
>
>Productkenmerken geven functies aan die wereldwijd op alle producten van toepassing zijn. De kenmerkopties van het product zijn aanpassingen om eigenschappen te specificeren die op specifieke producten van toepassing zijn.

### Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

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

1. [Verbinding maken met de sitedatabase](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Het aantal kenmerksets zoeken met MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Verwijder ongebruikte kenmerksets.

### Mogelijke gevolgen voor de prestaties

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

- Langdurige verzoek- en renderingtijden voor productdetails (PDP) en categoriepagina&#39;s die complexe producten bevatten.
- Bewerkingen voor het opslaan van beheerproducten reactietijd neemt toe boven optimale prestatiedoelen.
- Verhoging van de rendertijd in Product Edit.
- Langzaam uitchecken.

## Productopties

Voor de beste prestaties configureert u maximaal 100 productopties per product.

### Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal opties verminderen

Gebruik de volgende strategieën om het aantal productopties te verminderen voor de beste prestaties van de site:

- Complexe producten en aangepaste opties configureren als bron van productvariaties.
- In plaats van globale productmalplaatjes en optiecontainers te creëren die op alle producten van toepassing zijn, gebruik attributenreeksen om specifieke productmalplaatjes met gerichte attributen en opties te bouwen.
- Productinformatie beheren via een extern productbeheersysteem (PMS).

### Mogelijke gevolgen voor de prestaties

Als u veel productopties configureert, neemt de hoeveelheid gegevens die voor elk product wordt opgehaald bij alle lees- en schrijfbewerkingen toe. Dit resulteert in:

- Verhoogd SQL vraagverkeer en zwaarder `JOIN` De verrichtingen verhogen gegevensbestandproductie.
- Grotere grootte voor Adobe Commerce-indexen en de zoekindex met volledige tekst.

De hierboven vermelde verhogingen beïnvloeden mogelijk de prestaties van de site op de volgende manieren:

- Langere reactietijd voor de meeste storefrontscenario&#39;s met betrekking tot producten die vele opties in attributen bevatten.
- De tijd die nodig is om de productbeheerbewerkingen in Admin te voltooien neemt aanzienlijk toe, wat kan leiden tot time-outs, met name voor scenario&#39;s met betrekking tot de lijst van kenmerken en het opvragen van bomen, waaronder het beheer van promotieregels.
- Kan bulkacties blokkeren die asynchrone massabewerkingen zoals importeren en exporteren voltooien en aangepaste prijzen toewijzen aan meerdere producten in een gedeelde catalogus.

## Paginering van productaanbiedingen

Geef voor de beste prestaties maximaal 48 producten per pagina weer.

U kunt Adobe Commerce zodanig configureren dat kopers alle producten van de categorie op één pagina kunnen bekijken. Als het aantal categorieproducten beduidend meer dan 48 producten is, werk de configuratie van de Catalogus voor de controles van de paginering van de opslagruimte bij.

### Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Configuratie van productlijsten bijwerken

Als u meer dan 48 producten in om het even welke categorie hebt, werk de configuratie van de archiefcatalogus bij om de optie onbruikbaar te maken om **Alle producten per pagina toestaan**.

Nadat u deze optie hebt uitgeschakeld, gebruikt Adobe Commerce de besturingselementen voor de paginering van de winkelpagina van het product om het aantal producten te beheren dat in winkelcomponenten wordt weergegeven. Zie voor instructies [Pagineringsbesturingselementen configureren](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-product-listings.html#configure-the-pagination-controls).

## SKU-limieten voor producten

Om de prestaties te maximaliseren, is het geadviseerde maximum voor efficiënte product het Houting Units (SKUs) 242 miljoen. Dit effectieve SKU-maximum wordt berekend als:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Waarbij:

- N staat als het aantal artikelen voor die categorie
- De groepen van de klant omvatten gedeelde catalogi, aangezien het een extra klantengroep creeert.

Als u meer dan het maximale aantal effectieve SKU&#39;s hebt, vertraagt u het ophalen van productgegevens en neemt de tijd voor het voltooien van bewerkingen of indexaties in het deelvenster Beheer toe.

### Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Het aantal producten verminderen

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
- Deactiveer of verwijder ongebruikte systeemcomponenten zoals modules. Zie  [Modules verwijderen](../../../installation/tutorials/uninstall-modules.md).
- Beheer producten in een extern Platform Management System (PMS).

## Productvariaties

Voor de beste prestaties configureert u maximaal 50 variaties per product.

### Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

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

Voor de beste prestaties, volg deze beste praktijken om verkoop en promoties voor punten in een winkelwagentje te vormen:

- **Verkoopregels (regels betreffende de kartprijs)**-Configureer niet meer dan 1000 regels voor winkelwagenprijzen voor alle websites
   - Ongebruikte regels beheren en verwijderen.
   - Voeg strikte regelvoorwaarden (zoals kenmerk- of categoriefilter) toe voor de meest efficiënte overeenkomst.
- **Coupons**—
   - Controleer of het totale aantal coupons in de database kleiner is dan 250.000.
   - Ongebruikte en verlopen coupons verwijderen.
   - Alleen het aantal coupons genereren dat nodig is om te voldoen aan de vereisten voor campagnes.

### Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

### Mogelijke gevolgen voor de prestaties

Als u meer dan het aanbevolen maximumaantal regels of coupons voor de kartonprijs hebt, kan dit de prestaties van de site op de volgende manieren beïnvloeden:

- Hogere responstijd wanneer producten aan het winkelwagentje worden toegevoegd.
- Meer tijd om de miniaturen te laden en weer te geven.
- Meer tijd om de winkelwagenpagina weer te geven.
- Verhoogde tijd om de **Totalen** op de pagina Afhandeling.
- Het toepassen van coupons kan meer dan 2 seconden duren.
