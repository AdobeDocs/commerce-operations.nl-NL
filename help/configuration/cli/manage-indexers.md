---
title: De indexen beheren
description: Zie voorbeelden van Commerce-indexen weergeven en beheren.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 5e1684d4d910f2ea52e12eeccdc291a54372f8d6
workflow-type: tm+mt
source-wordcount: '951'
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

De parallellisering van de index beïnvloedt scoped slechts indexeerders, wat betekent Commerce de gegevens in veelvoudige lijsten splitst gebruikend indexer als zijn werkingsgebied in plaats van het houden van alle gegevens in één lijst.

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

### Indexeermodus instellen

>[!IMPORTANT]
>
>Zorg ervoor dat u de [!DNL Customer Grid] with `realtime` in plaats van `schedule`. De [!DNL Customer Grid] kan alleen opnieuw worden gedexeerd met de opdracht [!UICONTROL Update on Save] -optie. Deze index ondersteunt het `Update by Schedule` -optie. Gebruik de volgende opdrachtregel om deze indexeer in te stellen op bijwerken bij opslaan: `php bin/magento indexer:set-mode realtime customer_grid`
>
>Zie [Aanbevolen procedures voor indexeerconfiguratie](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html) in de _Afspeelmap voor implementatie_.

>[!INFO]
>
>Stel uw website in op [onderhoud](../../installation/tutorials/maintenance-mode.md) en [uitsnijdtaken uitschakelen](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Dit zorgt ervoor u geen gegevensbestandsloten lijdt.

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

### Indexeringsstatus instellen

De `bin/magento indexer:set-status` werd geïntroduceerd in Adobe Commerce 2.4.7. Hiermee kunnen beheerders de operationele status van een of meer indexen wijzigen en de systeemprestaties optimaliseren tijdens uitgebreide bewerkingen, zoals het importeren, bijwerken of onderhouden van gegevens.

Command syntaxis:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Waarbij:

- `invalid`—Tekent indexeerders als verouderd, waardoor opnieuw indexeren wordt gevraagd bij de volgende uitsnijdbewerking, tenzij ze worden opgeschort.
- `suspended`—Hiermee worden tijdelijk automatische updates voor door snijden geactiveerde indexen gestopt. Deze status is van toepassing op zowel realtime- als planningsmodi, zodat automatische updates worden gepauzeerd tijdens intensieve bewerkingen.
- `valid`—Geeft aan dat indexergegevens up-to-date zijn, zonder dat opnieuw indexeren nodig is.
- `indexer`—Is een door spaties gescheiden lijst van indexen. Weglaten `indexer` om alle indexen te vormen de zelfde manier.

Als u bijvoorbeeld bepaalde indexen wilt onderbreken, voert u het volgende in:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Monsterresultaat:

```terminal
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Status geschorste index beheren

Wanneer een indexeerteken op een `suspended` status, heeft dit voornamelijk invloed op automatische re-dexering en geconcretiseerde weergave-updates. Hier volgt een kort overzicht:

**Opnieuw indexeren overgeslagen**: Automatisch opnieuw indexeren wordt overgeslagen voor `suspended` indexen en indexen indexen die het zelfde delen `shared_index`. Dit zorgt ervoor dat de systeembronnen behouden blijven door gegevens met betrekking tot geschorste processen niet opnieuw te indexeren.

**Updates van gematerialiseerde weergave overgeslagen**: Gelijkaardig aan het opnieuw indexeren, updates aan geconcretiseerde meningen met betrekking tot `suspended` indexeerders of hun gedeelde indexen worden ook gepauzeerd. Deze actie vermindert de belasting van het systeem tijdens de ophanging.

>[!INFO]
>
>De `indexer:reindex` alle indexen opnieuw indexeert, inclusief de indexen die zijn gemarkeerd als `suspended`, waardoor het handig wordt voor handmatige updates wanneer automatische updates worden gepauzeerd.

>[!IMPORTANT]
>
>De status van een indexeerder wijzigen in `valid` van `suspended` of `invalid` is voorzichtigheid geboden. Deze actie kan tot prestatiesdegradatie leiden als er geaccumuleerde niet geïndexeerde gegevens zijn.
>
>Het is essentieel om ervoor te zorgen dat alle gegevens nauwkeurig worden geïndexeerd alvorens manueel de status aan bij te werken `valid` de systeemprestaties en gegevensintegriteit te handhaven.
