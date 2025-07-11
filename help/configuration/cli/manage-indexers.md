---
title: De indexen beheren
description: Zie voorbeelden van Commerce-indexen weergeven en beheren.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: ceefb9371dd0a85046cc5bfc0ddc72144d649608
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# De indexen beheren

{{file-system-owner}}

Een lijst met alle indexen weergeven:

```bash
bin/magento indexer:info
```

De lijst wordt als volgt weergegeven:

```text
cataloginventory_stock                   Stock
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalog_product_price                    Product Price
catalogrule_product                      Catalog Product Rule
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
sales_order_data_exporter                Sales Order Feed
sales_order_status_data_exporter         Sales Order Statuses Feed
store_data_exporter                      Stores Feed
```

>[!NOTE]
>
> De handelaars van Adobe Commerce die Live Onderzoek, de Dienst van de Catalogus, of de Aanbevelingen van het Product gebruiken hebben de optie om [ op SaaS-Gebaseerde prijs te gebruiken indexeert ](https://experienceleague.adobe.com/nl/docs/commerce/price-indexer/price-indexing).

## Indexstatus weergeven

Gebruik deze opdracht om de status van alle indexen of specifieke indexen weer te geven. Kijk bijvoorbeeld of een indexeerprogramma opnieuw moet worden gedexeerd.

Opdrachtopties:

```bash
bin/magento indexer:status [indexer]
```

Waar `[indexer]` een lijst met indexen is die door spaties worden gescheiden. Laat `[indexer]` weg om de status van alle indexen te bekijken.

Monsterresultaat:

```text
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| ID                               | Title                     | Status | Update On | Schedule Status     | Schedule Updated    |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| catalogrule_product              | Catalog Product Rule      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogrule_rule                 | Catalog Rule Product      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogsearch_fulltext           | Catalog Search            | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:01:02 |
| catalog_category_product         | Category Products         | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| customer_grid                    | Customer Grid             | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| design_config_grid               | Design Config Grid        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| inventory                        | Inventory                 | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_category         | Product Categories        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| catalog_product_attribute        | Product EAV               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_price            | Product Price             | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:54 |
| targetrule_product_rule          | Product/Target Rule       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
| sales_order_data_exporter        | Sales Order Feed          | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| sales_order_status_data_exporter | Sales Order Statuses Feed | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| salesrule_rule                   | Sales Rule                | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| cataloginventory_stock           | Stock                     | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| store_data_exporter              | Stores Feed               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:11 |
| targetrule_rule_product          | Target Rule/Product       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
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

Waar `[indexer]` een lijst met indexen is die door spaties worden gescheiden. Laat `[indexer]` weg om alle indexen opnieuw te indexeren.

Monsterresultaat:

```text
Stock index has been rebuilt successfully in <time>
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Product/Target Rule index has been rebuilt successfully in <time>
Target Rule/Product index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
Sales Rule index has been rebuilt successfully in <time>
Sales Order Feed index has been rebuilt successfully in <time>
Sales Order Statuses Feed index has been rebuilt successfully in <time>
Stores Feed index has been rebuilt successfully in <time>
```

>[!INFO]
>
>Het opnieuw indexeren van alle indexen kan lange tijd voor opslag met grote aantallen producten, klanten, categorieën, en promotieregels vergen.

### Opnieuw indexeren in parallelle modus

{{php-process-control}}

Indexers zijn bereikbaar en multithread om het opnieuw indexeren in parallelle modus te ondersteunen. Het parallelleert door de afmeting van de indexeerder en voert over veelvoudige draden uit, die verwerkingstijd verminderen.

In deze context is `dimension` het bereik van het opnieuw indexeren, bijvoorbeeld een `website` of alleen een specifieke `customer_group` .

De parallellisering van de index beïnvloedt scoped slechts indexeerders, wat betekent Commerce de gegevens in veelvoudige lijsten splitst gebruikend indexer als zijn werkingsgebied in plaats van het houden van alle gegevens in één lijst.

U kunt de volgende indexen in parallelle modus uitvoeren:

- Aan `Catalog Search Fulltext` kan worden deelgenomen door de weergaven van de winkel.
- Aan `Category Product` kan worden deelgenomen door de weergaven van de winkel.
- `Catalog Price` kan worden gekoppeld aan website- en klantgroepen.
- `Catalog Permissions` kan parallel lopen met klantengroepen.

>[!INFO]
>
>Parallelization voor Catalog Search Fulltext en Categorie Product wordt toegelaten door gebrek.

Als u parallellisatie wilt gebruiken, stelt u een van de beschikbare afmetingen in voor de indexeer van de productprijs:

- `none` (standaardwaarde)
- `website`
- `customer_group`
- `website_and_customer_group`

Stel bijvoorbeeld de modus per website in:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Als u parallellisering wilt gebruiken voor catalogusmachtigingen, stelt u een van de beschikbare dimensiemodi in voor de indexer Catalogusmachtigingen:

- `none` (standaardwaarde)
- `customer_group`

Of om de huidige modus te controleren:

```bash
bin/magento indexer:show-dimensions-mode
```

Als u opnieuw wilt indexeren in de parallelle modus, voert u de opdracht opnieuw indexeren uit met behulp van de omgevingsvariabele `MAGE_INDEXER_THREADS_COUNT` of voegt u een omgevingsvariabele toe aan het `env.php` -bestand. Met deze variabele wordt het aantal threads voor de herindexverwerking ingesteld.

Met de volgende opdracht voert u bijvoorbeeld de `Catalog Search Fulltext` -index uit over drie threads:

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

```text
Stock indexer has been invalidated.
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Product/Target Rule indexer has been invalidated.
Target Rule/Product indexer has been invalidated.
Catalog Search indexer has been invalidated.
Sales Rule indexer has been invalidated.
Sales Order Feed indexer has been invalidated.
Sales Order Statuses Feed indexer has been invalidated.
Stores Feed indexer has been invalidated.
```

## Indexeerders configureren

Gebruik deze opdracht om de volgende indexeropties in te stellen:

- **Update op sparen (`realtime`)**: De geïndexeerde gegevens worden bijgewerkt wanneer een verandering in Admin wordt aangebracht. (Zo wordt de index van de categorie producten opnieuw geindexeerd nadat de producten aan een categorie in Admin zijn toegevoegd.)
- **Update door programma (`schedule`)**: Het gegeven wordt geïndexeerd volgens het programma dat door uw kroonbaan wordt geplaatst.

[ Leer meer over het indexeren ](https://developer.adobe.com/commerce/php/development/components/indexing/).

### De huidige configuratie weergeven

De huidige indexeerconfiguratie weergeven:

```bash
bin/magento indexer:show-mode [indexer]
```

Waar `[indexer]` een lijst met indexen is die door spaties worden gescheiden. Laat `[indexer]` weg om de modi van alle indexen te tonen. U kunt bijvoorbeeld als volgt de modus van alle indexen weergeven:

Monsterresultaat:

```text
Stock:                                             Update by Schedule
Design Config Grid:                                Update by Schedule
Customer Grid:                                     Update by Schedule
Category Products:                                 Update by Schedule
Product Categories:                                Update by Schedule
Catalog Rule Product:                              Update by Schedule
Product EAV:                                       Update by Schedule
Inventory:                                         Update by Schedule
Product Price:                                     Update by Schedule
Catalog Product Rule:                              Update by Schedule
Product/Target Rule:                               Update by Schedule
Target Rule/Product:                               Update by Schedule
Catalog Search:                                    Update by Schedule
Sales Rule:                                        Update by Schedule
Sales Order Feed:                                  Update by Schedule
Sales Order Statuses Feed:                         Update by Schedule
Stores Feed:                                       Update by Schedule
```

### Indexeermodus instellen

>[!IMPORTANT]
>
>Het gedrag van de [!DNL Customer Grid] -index is in 2.4.8 gewijzigd:
>
>- **Voorafgaand aan 2.4.8**: [!DNL Customer Grid] indexeer kan slechts opnieuw worden gefixeerd gebruikend de [!UICONTROL Update on Save] optie en steunt niet de [!UICONTROL Update by Schedule] optie.
>
>   Gebruik de volgende opdracht om deze indexeer in te stellen op bijwerken bij opslaan:
>
>   ```bash
>   bin/magento indexer:set-mode realtime customer_grid
>   ```
>
>- **2.4.8 en later**: [!DNL Customer Grid] de indexer steunt zowel [!UICONTROL Update on Save] als [!UICONTROL Update by Schedule] wijzen, en gebreken aan [!UICONTROL Update by Schedule].
>
>Zie [ Beste praktijken voor indexeerconfiguratie ](https://experienceleague.adobe.com/nl/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration) in _Playbook van de Implementatie_.

>[!INFO]
>
>Alvorens de wijzen van de omschakelingsindexeerder, plaats uw website aan [ onderhoud ](../../installation/tutorials/maintenance-mode.md) wijze en [ maak kanonbanen ](https://experienceleague.adobe.com/nl/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) onbruikbaar. Dit zorgt ervoor u geen gegevensbestandsloten ervaart.

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
- `indexer` - Dit is een door spaties gescheiden lijst met indexen. Laat `indexer` weg om alle indexen de zelfde manier te vormen.

Als u bijvoorbeeld bepaalde indexen wilt onderbreken, voert u het volgende in:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Monsterresultaat:

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Status geschorste index beheren

Wanneer een indexeerfunctie is ingesteld op een `suspended` -status, heeft dit vooral invloed op de automatische re-indexering en op gematerialiseerde weergave-updates. Hier volgt een kort overzicht:

**het Reindexeren Overgeslagen**: Het systeem slaat automatisch opnieuw indexeren voor `suspended` indexeerders en om het even welke indexen over die het zelfde `shared_index` delen. Met deze methode worden de systeembronnen behouden doordat gegevens met betrekking tot stilgezette processen niet opnieuw hoeven te worden gekoppeld.

**Gematerialiseerde Overgeslagen Updates van de Mening**: Gelijkaardig aan het opnieuw indexeren, pauzeert het systeem ook updates aan materialized meningen met betrekking tot `suspended` indexeerders of hun gedeelde indexen. Deze pauze vermindert de belasting van het systeem tijdens de ophanging.

>[!INFO]
>
>Met de opdracht `indexer:reindex` schakelt u alle indexen opnieuw in, inclusief de indexen die als `suspended` zijn gemarkeerd. Dit is handig voor handmatige updates wanneer de automatische indexen worden gepauzeerd.

>[!IMPORTANT]
>
>Als u de status van een indexeerprogramma wilt wijzigen in `valid` van `suspended` of `invalid` , moet u voorzichtig zijn. Deze actie kan tot prestatiesdegradatie leiden als er geaccumuleerde niet geïndexeerde gegevens zijn.
>
>Het is van cruciaal belang dat alle gegevens correct worden geïndexeerd voordat de status handmatig wordt bijgewerkt naar `valid` om de systeemprestaties en gegevensintegriteit te behouden.
