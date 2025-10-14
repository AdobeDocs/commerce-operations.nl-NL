---
title: Best practices voor databaseconfiguratie voor cloudimplementatie
description: Leer hoe u database- en toepassingsinstellingen configureert om de prestaties te verbeteren bij de implementatie van Adobe Commerce op cloudinfrastructuur.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Aanbevolen procedures voor databaseconfiguratie

Leer over beste praktijken om gegevensbestandprestaties te verbeteren en efficiënt met het gegevensbestand te werken wanneer het opstellen van Adobe Commerce op wolkeninfrastructuur.

## Betrokken producten

Adobe Commerce over cloudinfrastructuur

## Alle MyISAM-tabellen converteren naar InnoDB

Adobe raadt u aan de InnoDB-database-engine te gebruiken. In een standaard Adobe Commerce-installatie worden alle tabellen in de database opgeslagen met de InnoDB-engine. Nochtans, kunnen sommige derdemodules (uitbreidingen) lijsten in het formaat introduceren MyISAM. Nadat u een externe module hebt geïnstalleerd, controleert u de database om eventuele tabellen in `myisam` -indeling te identificeren en converteert u deze naar `innodb` -indeling.

### Bepaal als een module lijsten MyISAM omvat

U kunt de code van de derdemodules analyseren alvorens het te installeren, om te bepalen als het lijsten MyISAM gebruikt.

Als u reeds een uitbreiding hebt geïnstalleerd, stel de volgende vraag in werking om te bepalen of het gegevensbestand om het even welke lijsten MyISAM heeft:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### De opslagengine wijzigen in InnoDB

In het `db_schema.xml` -bestand dat de tabel declareert, stelt u de `engine` kenmerkwaarde voor het corresponderende `table` -knooppunt in op `innodb` . Voor verwijzing, zie [&#x200B; declaratief schema > lijstknoop &#x200B;](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) in onze ontwikkelaarsdocumentatie vormen.

De declaratieve regeling werd ingevoerd in Adobe Commerce op cloudinfrastructuur versie 2.3.

## De aanbevolen zoekmachine configureren voor native MySQL-zoekopdracht

Adobe raadt u aan Elasticsearch of OpenSearch altijd in te stellen voor uw Adobe Commerce-infrastructuurproject in de cloud, zelfs als u een zoekprogramma van derden voor uw Adobe Commerce-toepassing wilt configureren. Deze configuratie biedt een fallback-optie voor het geval dat het zoekprogramma van een andere fabrikant mislukt.

Het zoekprogramma dat u gebruikt, is afhankelijk van de geïnstalleerde Adobe Commerce-versie van de cloud:

- Gebruik voor Adobe Commerce 2.4.4 en hoger de OpenSearch-service voor native MySQL-zoekopdrachten.

- Gebruik Elasticsearch voor eerdere Adobe Commerce-versies.

Voer de volgende opdracht uit om te bepalen welke zoekengine momenteel wordt gebruikt:

```bash
./bin/magento config:show catalog/search/engine
```

Zie voor configuratieinstructies de Developer Guide for Adobe Commerce on cloud:

- [&#x200B; Opstelling de dienst OpenSearch &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/service/opensearch)

- [&#x200B; opstelling de dienst van Elasticsearch &#x200B;](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch)

## Aangepaste triggers voorkomen

Gebruik indien mogelijk geen aangepaste triggers.

De trekkers worden gebruikt om veranderingen in controletabellen te registreren. Adobe raadt u aan de toepassing te configureren om rechtstreeks naar de audittabellen te schrijven in plaats van de triggerfunctionaliteit te gebruiken, en wel om de volgende redenen:

- Triggers worden geïnterpreteerd als code en MySQL compileert ze niet vooraf. Hooking op de transactieruimte van uw vraag, voegen zij de overheadkosten aan een parser en een interpreter voor elke vraag toe die met de lijst wordt uitgevoerd.
- De trekkers delen de zelfde transactieruimte zoals de originele vragen, en terwijl die vragen voor sloten op de lijst concurreren, concurreren de trekkers onafhankelijk op sloten op een andere lijst.

Om over alternatieven te leren om douanetriggers te gebruiken, zie [&#x200B; trekkers MySQL &#x200B;](mysql-configuration.md#triggers).

## Upgrade [!DNL ECE-Tools] naar versie 2002.0.21 of hoger {#ece-tools-version}

Om potentiële problemen met kroonsloten te vermijden, bevorder ECE-Hulpmiddelen aan versie 2002.0.21 of hoger. Voor instructies, zie [&#x200B; versie `ece-tools` van de Update 0&rbrace; &lbrace;in onze ontwikkelaarsdocumentatie.](https://experienceleague.adobe.com/nl/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package)

## Veilig overschakelen op indexmodus

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

Als u overschakelt op indexen, worden [!DNL data definition language] (DDL)-instructies gegenereerd om triggers te maken die databaseslokken kunnen veroorzaken. U kunt dit probleem voorkomen door uw website in de onderhoudsmodus te plaatsen en de taken voor uitsnijden uit te schakelen voordat u de configuratie wijzigt.
Voor instructies, zie [&#x200B; indexeerders &#x200B;](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=nl-NL#configure-indexers-1) in de *Gids van de Configuratie van Adobe Commerce* vormen.

## DDL-instructies niet uitvoeren in productie

Vermijd het uitvoeren van verklaringen DDL in het milieu van de Productie om conflicten (zoals lijstwijzigingen en creaties) te verhinderen. Het `setup:upgrade` -proces is een uitzondering.

Als u een DDL-instructie moet uitvoeren, zet u de website in de onderhoudsmodus en schakelt u de uitsnede uit (zie de instructies voor het veilig omschakelen van indexen in de vorige sectie).

## Archivering van bestellingen inschakelen

Archivering van bestellingen via de beheerder inschakelen om de benodigde ruimte voor verkooptabellen te verkleinen naarmate de gegevens van uw bestelling toenemen. Met archivering bespaart u MySQL-schijfruimte en verbetert u de afrekenprestaties.

Zie [&#x200B; archivering &#x200B;](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html?lang=nl-NL) in de documentatie van de Merchant van Adobe Commerce toelaten.

## Aanvullende informatie

- [&#x200B; MySQL de Motoren van de Opslag &#x200B;](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Adobe Commerce 2.3.5-upgradevoorwaarden voor MariaDB](../maintenance/mariadb-upgrade.md)
- [Aanbevolen procedures om prestatieproblemen met databases op te lossen](../maintenance/resolve-database-performance-issues.md)
