---
title: De indexen beheren
description: Zie voorbeelden van Commerce-indexen weergeven en beheren.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# De indexen beheren

{{file-system-owner}}

Een lijst met alle indexen weergeven:

```bash
bin/magento indexer:info
```

De lijst wordt als volgt weergegeven:

```
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

>[!NOTE]
> De handelaars van Adobe Commerce die Live Onderzoek, de Dienst van de Catalogus, of de Aanbevelingen van het Product gebruiken hebben de optie om [ op SaaS-Gebaseerde prijs te gebruiken indexeert ](https://experienceleague.adobe.com/docs/commerce/price-indexer/index.html).

## Indexstatus weergeven

Gebruik deze opdracht om de status van alle indexen of specifieke indexen weer te geven. Kijk bijvoorbeeld of een indexeerprogramma opnieuw moet worden gedexeerd.

Opdrachtopties:

```bash
bin/magento indexer:status [indexer]
```

Waar `[indexer]` een lijst met indexen is die door spaties worden gescheiden. Laat `[indexer]` weg om de status van alle indexen te bekijken.

Monsterresultaat:

```
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## Opnieuw indexeren

Gebruik deze opdracht om alle of geselecteerde indexen slechts één keer opnieuw te indexeren.

>[!INFO]
>
>Deze opdracht wordt slechts één keer opnieuw samengesteld. Om indexeerders bijgewerkt te houden, moet u opstelling a [ cron baan ](../cli/configure-cron-jobs.md).

Opdrachtopties:

```bash
bin/magento indexer:reindex [indexer]
```

Waar `[indexer]` een lijst met indexen is die door spaties worden gescheiden. Laat na `[indexer]` om alle indexeerfuncties opnieuw te indexeren.

Voorbeeld resultaat:

```
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>Het opnieuw indexeren van alle indexeerfuncties kan lang duren voor winkels met een groot aantal producten, klanten, categorieën en promotieregels.

### Opnieuw indexeren in parallelle modus

{{php-process-control}}

Indexeerfuncties hebben een bereik en zijn voorzien van meerdere threads om herindexering in parallelle modus te ondersteunen. Het parallelliseert op basis van de dimensie van de indexeerfunctie en wordt uitgevoerd over meerdere threads, waardoor de verwerkingstijd wordt verkort.

In deze context is de reikwijdte van de herindexering, `dimension` bijvoorbeeld een `website` of gewoon een specifieke `customer_group`.

Indexparallellisatie is alleen van invloed op indexeerfuncties met bereik, wat betekent dat Commerce de gegevens opsplitst in meerdere tabellen met de indexeerfunctie als bereik in plaats van alle gegevens in één tabel te bewaren.

U kunt de volgende indexen in de parallelle modus uitvoeren:

- `Catalog Search Fulltext` Kan worden parallel lopen met winkelweergaven.
- `Category Product` Kan worden parallel lopen met winkelweergaven.
- `Catalog Price` Kan worden parallel geschakeld door website en klantgroepen.
- `Catalog Permissions` kan worden parallel geschakeld door klantgroepen.

>[!INFO]
>
>Parallellisatie voor Catalog Search Fulltext en Category Product is standaard ingeschakeld.

Als u parallellisatie wilt gebruiken, stelt u een van de beschikbare dimensiemodi in voor de prijsindexeerder voor producten:

- `none` (standaard)
- `website`
- `customer_group`
- `website_and_customer_group`

Ga bijvoorbeeld als volgt te werk om de modus per website in te stellen:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Als u parallellisatie wilt gebruiken voor catalogusmachtigingen, stelt u een van de beschikbare dimensiemodi in voor de indexeerfunctie voor catalogusmachtigingen:

- `none` (standaard)
- `customer_group`

Of om de huidige modus te controleren:

```bash
bin/magento indexer:show-dimensions-mode
```

Als u in parallelle modus opnieuw wilt indexeren, voert u de opdracht opnieuw indexeren uit met behulp van de omgevingsvariabele `MAGE_INDEXER_THREADS_COUNT`of voegt u een omgevingsvariabele toe aan het `env.php` bestand. Deze variabele stelt het aantal threads in voor de herindexverwerking.

Met de volgende opdracht wordt de `Catalog Search Fulltext` indexeerfunctie bijvoorbeeld uitgevoerd op drie threads:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Index opnieuw instellen

Gebruik deze opdracht om de status van alle indexen of specifieke indexen ongeldig te maken.

Opdrachtopties:

```bash
bin/magento indexer:reset [indexer]
```

Waar ```[indexer]``` een lijst met indexen is die door spaties worden gescheiden. Laat `[indexer]` weg om alle indexen ongeldig te maken.

Monsterresultaat:

```
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## Indexeerders configureren

Gebruik deze opdracht om de volgende indexeeropties in te stellen:

- **Update bij opslaan (`realtime`)**: Geïndexeerde gegevens worden bijgewerkt wanneer er een wijziging wordt aangebracht in de beheerder. (De index van categorieproducten wordt bijvoorbeeld opnieuw geïndexeerd nadat producten zijn toegevoegd aan een categorie in de beheerder.)
- **Bijwerken volgens schema (`schedule`)**: Gegevens worden geïndexeerd volgens het schema dat is ingesteld door uw cron-taak.

[Meer informatie over indexeren](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Geef de huidige configuratie weer

De huidige configuratie van de indexeerfunctie weergeven:

```bash
bin/magento indexer:show-mode [indexer]
```

Waar `[indexer]` is een door spaties gescheiden lijst met indexeerfuncties. Laat weg `[indexer]` om de modi van alle indexeerders weer te geven. Ga bijvoorbeeld als volgt te werk om de modus van alle indexeerfuncties weer te geven:

Voorbeeld resultaat:

```
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### De indexeermodus instellen

>[!IMPORTANT]
>
>Zorg ervoor dat u de [!DNL Customer Grid] instelt met `realtime` in plaats van met `schedule` . De [!DNL Customer Grid] kan alleen opnieuw worden genummerd met de optie [!UICONTROL Update on Save] . Deze index ondersteunt de optie `Update by Schedule` niet. Gebruik de volgende opdrachtregel om deze indexeerfunctie in te stellen voor bijwerken bij opslaan: `php bin/magento indexer:set-mode realtime customer_grid`
>
>Zie [ Beste praktijken voor indexeerconfiguratie ](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html?lang=nl-NL) in _Playbook van de Implementatie_.

>[!INFO]
>
>Alvorens de wijzen van de omschakelingsindexeerder, plaats uw website aan [ onderhoud ](../../installation/tutorials/maintenance-mode.md) wijze en [ maak kanonbanen ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=nl-NL#disable-cron-jobs) onbruikbaar. Dit zorgt ervoor u geen gegevensbestandsloten lijdt.

De indexeerconfiguratie opgeven:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Waarbij:

- `realtime` - Hiermee stelt u de geselecteerde indexen in om bij te werken bij het opslaan.
- `schedule` - Stelt de opgegeven indexen in om op te slaan volgens het bijsnijdschema.
- `indexer` - Dit is een door spaties gescheiden lijst met indexen. Laat `indexer` weg om alle indexen de zelfde manier te vormen.

Als u bijvoorbeeld alleen de indexeerprogramma&#39;s voor de categorie en de productcategorieën wilt wijzigen, voert u het volgende in:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Monsterresultaat:

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

De indexeerdergerelateerde databasetriggers worden toegevoegd wanneer de indexeermodus is ingesteld op `schedule` en verwijderd wanneer de indexeermodus is ingesteld op `realtime` . Als de triggers ontbreken in uw database terwijl de indexen zijn ingesteld op `schedule` , wijzigt u de indexen in `realtime` en wijzigt u deze weer in `schedule` . Hierdoor worden de triggers opnieuw ingesteld.

### Indexeringsstatus instellen

De opdracht `bin/magento indexer:set-status` is geïntroduceerd in Adobe Commerce 2.4.7. Hiermee kunnen beheerders de operationele status van een of meer indexen wijzigen en de systeemprestaties optimaliseren tijdens uitgebreide bewerkingen, zoals het importeren, bijwerken of onderhouden van gegevens.

Command syntaxis:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Waarbij:

- `invalid` - Hiermee worden indexen als verouderd gemarkeerd en wordt opnieuw indexeren bij de volgende uitsnijdbewerking gevraagd, tenzij ze worden opgeschort.
- `suspended` - Hiermee worden tijdelijk automatische, door snijden geactiveerde updates voor indexen gestopt. Deze status is van toepassing op zowel realtime- als planningsmodi, zodat automatische updates worden gepauzeerd tijdens intensieve bewerkingen.
- `valid` - Geeft aan dat indexergegevens up-to-date zijn, zonder dat opnieuw indexeren nodig is.
- `indexer`—Is een door spaties gescheiden lijst van indexeerfuncties. Laat weg `indexer` om alle indexeerfuncties op dezelfde manier te configureren.

Als u bijvoorbeeld specifieke indexeerders wilt schorsen, voert u het volgende in:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Voorbeeld resultaat:

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### De status van opgeschorte indexeerfunctie beheren

Wanneer een indexeerfunctie is ingesteld op een `suspended` status, is dit voornamelijk van invloed op het automatisch opnieuw indexeren en gerealiseerde weergave-updates. Hier is een kort overzicht:

**Opnieuw indexeren Overgeslagen**: Automatisch opnieuw indexeren wordt overgeslagen voor `suspended` indexeerfuncties en indexeerfuncties die hetzelfde `shared_index`delen. Dit zorgt ervoor dat systeembronnen worden gespaard door gegevens met betrekking tot opgeschorte processen niet opnieuw te indexeren.

**Updates voor gerealiseerde weergaven overgeslagen**: Net als bij opnieuw indexeren, worden updates van gerealiseerde weergaven met betrekking tot `suspended` indexeerfuncties of hun gedeelde indexen ook onderbroken. Deze actie vermindert de systeembelasting tijdens ophangperioden nog verder.

>[!INFO]
>
>De `indexer:reindex` opdracht indexeert alle indexeerfuncties opnieuw, inclusief de indexeerfuncties die zijn gemarkeerd als `suspended`, waardoor het handig is voor handmatige updates wanneer automatische updates worden onderbroken.

>[!IMPORTANT]
>
>Het wijzigen van de status van een indexeerfunctie in `valid` van `suspended` of `invalid` vereist voorzichtigheid. Deze actie kan leiden tot prestatievermindering als er niet-geïndexeerde gegevens zijn verzameld.
>
>Het is van cruciaal belang om ervoor te zorgen dat alle gegevens nauwkeurig worden geïndexeerd voordat de status handmatig wordt bijgewerkt om `valid` de systeemprestaties en gegevensintegriteit te behouden.
