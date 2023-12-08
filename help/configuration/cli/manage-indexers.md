---
title: De indexen beheren
description: Zie voorbeelden van hoe te om de indexen van de Handel te bekijken en te beheren.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# De indexen beheren

{{file-system-owner}}

Een lijst met alle indexen weergeven:

```bash
bin/magento indexer:info
```

De lijst wordt als volgt weergegeven:

```terminal
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
> Handelaren van Adobe Commerce die Live Search, Catalog Service of Product Recommendations gebruiken, hebben de mogelijkheid om [Prijsindexering op basis van SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## Indexstatus weergeven

Gebruik deze opdracht om de status van alle indexen of specifieke indexen weer te geven. Kijk bijvoorbeeld of een indexeerprogramma opnieuw moet worden gedexeerd.

Opdrachtopties:

```bash
bin/magento indexer:status [indexer]
```

Wanneer `[indexer]` is een door spaties gescheiden lijst met indexen. Weglaten `[indexer]` om de status van alle indexen weer te geven.

Monsterresultaat:

```terminal
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
>Deze opdracht wordt slechts één keer opnieuw samengesteld. Als u de indexen up-to-date wilt houden, moet u een [snijtaak](../cli/configure-cron-jobs.md).

Opdrachtopties:

```bash
bin/magento indexer:reindex [indexer]
```

Wanneer `[indexer]` is een door spaties gescheiden lijst met indexen. Weglaten `[indexer]` alle indexen opnieuw indexeren.

Monsterresultaat:

```terminal
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
>Het opnieuw indexeren van alle indexen kan lange tijd voor opslag met grote aantallen producten, klanten, categorieën, en promotieregels vergen.

### Opnieuw indexeren in parallelle modus

{{php-process-control}}

Indexers zijn bereikbaar en multithread om het opnieuw indexeren in parallelle modus te ondersteunen. Het parallelleert door de afmeting van de indexeerder en voert over veelvoudige draden uit, die verwerkingstijd verminderen.

In dit verband `dimension` de reikwijdte van de herindexering is, bijvoorbeeld `website` of slechts een specifieke `customer_group`.

De parallellisering van de index beïnvloedt scoped slechts indexeerders, wat betekent de Handel de gegevens in veelvoudige lijsten verdeelt gebruikend indexer als zijn werkingsgebied in plaats van het houden van alle gegevens in één lijst.

U kunt de volgende indexen in parallelle modus uitvoeren:

- `Catalog Search Fulltext` kan door archiefmeningen worden parallel gelopen.
- `Category Product` kan door archiefmeningen worden parallel gelopen.
- `Catalog Price` kan worden gekoppeld door website- en klantengroepen.
- `Catalog Permissions` kan door klantengroepen worden geëvenaard.

>[!INFO]
>
>Parallelization voor Catalog Search Fulltext en Categorie Product wordt toegelaten door gebrek.

Als u parallellisatie wilt gebruiken, stelt u een van de beschikbare afmetingen in voor de indexeer van de productprijs:

- `none` (standaard)
- `website`
- `customer_group`
- `website_and_customer_group`

Stel bijvoorbeeld de modus per website in:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Als u parallellisering wilt gebruiken voor catalogusmachtigingen, stelt u een van de beschikbare dimensiemodi in voor de indexer Catalogusmachtigingen:

- `none` (standaard)
- `customer_group`

Of om de huidige modus te controleren:

```bash
bin/magento indexer:show-dimensions-mode
```

Als u opnieuw wilt indexeren in parallelle modus, voert u de opdracht opnieuw uitvoeren met de omgevingsvariabele `MAGE_INDEXER_THREADS_COUNT`of voeg een omgevingsvariabele toe aan de `env.php` bestand. Met deze variabele wordt het aantal threads voor de herindexverwerking ingesteld.

Met de volgende opdracht voert u bijvoorbeeld de opdracht `Catalog Search Fulltext` indexeer over drie draden:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Index opnieuw instellen

Gebruik deze opdracht om de status van alle indexen of specifieke indexen ongeldig te maken.

Opdrachtopties:

```bash
bin/magento indexer:reset [indexer]
```

Wanneer ```[indexer]``` is een door spaties gescheiden lijst met indexen. Weglaten `[indexer]` om alle indexen ongeldig te maken.

Monsterresultaat:

```terminal
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

Gebruik deze opdracht om de volgende indexeropties in te stellen:

- **Bijwerken bij opslaan (`realtime`)**: De geïndexeerde gegevens worden bijgewerkt wanneer een verandering in Admin wordt aangebracht. (Zo wordt de index van de categorie producten opnieuw geindexeerd nadat de producten aan een categorie in Admin zijn toegevoegd.) Dit is de standaardinstelling.
- **Bijwerken volgens schema (`schedule`)**: Gegevens worden geïndexeerd volgens het schema dat is ingesteld door de snijtaak.

[Meer informatie over indexering](https://developer.adobe.com/commerce/php/development/components/indexing/).

### De huidige configuratie weergeven

De huidige indexeerconfiguratie weergeven:

```bash
bin/magento indexer:show-mode [indexer]
```

Wanneer `[indexer]` is een door spaties gescheiden lijst met indexen. Weglaten `[indexer]` om alle indexeerdermodi weer te geven. U kunt bijvoorbeeld als volgt de modus van alle indexen weergeven:

Monsterresultaat:

```terminal
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

### Indexeerders configureren

>[!INFO]
>
>Voordat u van indexeermodus overschakelt, raden we u aan uw website te plaatsen naar [onderhoud](../../installation/tutorials/maintenance-mode.md) en [uitsnijdtaken uitschakelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Dit zorgt ervoor u geen gegevensbestandsloten lijdt.

De indexeerconfiguratie opgeven:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Waarbij:

- `realtime`—Hiermee stelt u de geselecteerde indexen in om bij te werken bij het opslaan.
- `schedule`—Stelt de opgegeven indexen in om op te slaan volgens het bijsnijdschema.
- `indexer`—Is een door spaties gescheiden lijst van indexen. Weglaten `indexer` om alle indexen te vormen de zelfde manier.

Als u bijvoorbeeld alleen de indexeerprogramma&#39;s voor de categorie en de productcategorieën wilt wijzigen, voert u het volgende in:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Monsterresultaat:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

De indexeerdergerelateerde databasetriggers worden toegevoegd wanneer de indexeermodus is ingesteld op `schedule` en wordt verwijderd wanneer de indexeermodus is ingesteld op `realtime`. Als de triggers ontbreken in uw database terwijl de indexen zijn ingesteld op `schedule`wijzigt u de indexen in `realtime` en verander ze vervolgens naar `schedule`. Hierdoor worden de triggers opnieuw ingesteld.
