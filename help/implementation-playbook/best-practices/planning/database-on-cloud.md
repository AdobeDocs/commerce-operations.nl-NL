---
title: Best practices voor databaseconfiguratie voor cloudimplementatie
description: Leer hoe u database- en toepassingsinstellingen configureert om de prestaties te verbeteren bij de implementatie van Adobe Commerce op cloudinfrastructuur.
role: Developer, Admin
feature: Best Practices
exl-id: ca377dc8-c8bd-4f77-a24b-22a298e2bba4
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 0%

---

# Aanbevolen procedures voor databaseconfiguratie

Leer over beste praktijken om gegevensbestandprestaties te verbeteren en efficiënt met het gegevensbestand te werken wanneer het opstellen van Adobe Commerce op wolkeninfrastructuur.

## Betrokken producten

Adobe Commerce over cloudinfrastructuur

## Alle MyISAM-tabellen converteren naar InnoDB

Adobe raadt u aan de InnoDB-database-engine te gebruiken. In een standaard Adobe Commerce-installatie worden alle tabellen in de database opgeslagen met de InnoDB-engine. Nochtans, kunnen sommige derdemodules (uitbreidingen) lijsten in het formaat introduceren MyISAM. Nadat u een module van derden hebt geïnstalleerd, controleert u de database om eventuele tabellen in `myisam` formatteren en omzetten in `innodb` gebruiken.

### Bepaal als een module lijsten MyISAM omvat

U kunt de code van de derdemodules analyseren alvorens het te installeren, om te bepalen als het lijsten MyISAM gebruikt.

Als u reeds een uitbreiding hebt geïnstalleerd, stel de volgende vraag in werking om te bepalen of het gegevensbestand om het even welke lijsten MyISAM heeft:

```sql
SELECT table_schema, CONCAT(ROUND((index_length+data_length)/1024/1024),'MB')
    AS total_size FROM information_schema. TABLES WHERE engine='myisam' AND table_schema
    NOT IN ('mysql', 'information_schema', 'performance_schema', 'sys');
```

### De opslagengine wijzigen in InnoDB

In de `db_schema.xml` bestand waarin de tabel wordt gedeclareerd, stelt u de `engine` kenmerkwaarde voor de overeenkomende `table` knooppunt naar `innodb`. Zie ter referentie [declaratief schema configureren > tabelknooppunt](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) in onze ontwikkelaarsdocumentatie.

De declaratieve regeling werd ingevoerd in Adobe Commerce op cloudinfrastructuur versie 2.3.

## De aanbevolen zoekmachine configureren voor native MySQL-zoekopdracht

Adobe raadt u aan altijd Elasticsearch of OpenSearch voor uw Adobe Commerce in te stellen voor een infrastructuurproject in de cloud, zelfs als u een zoekprogramma van derden voor uw Adobe Commerce-toepassing wilt configureren. Deze configuratie biedt een fallback-optie voor het geval dat het zoekprogramma van een andere fabrikant mislukt.

Het zoekprogramma dat u gebruikt, is afhankelijk van de geïnstalleerde Adobe Commerce-versie van de cloud:

- Gebruik voor Adobe Commerce 2.4.4 en hoger de OpenSearch-service voor native MySQL-zoekopdrachten.

- Gebruik Elasticsearch voor eerdere Adobe Commerce-versies.

Voer de volgende opdracht uit om te bepalen welke zoekengine momenteel wordt gebruikt:

```bash
./bin/magento config:show catalog/search/engine
```

Zie voor configuratieinstructies de Developer Guide for Adobe Commerce on cloud:

- [De OpenSearch-service instellen](https://devdocs.magento.com/cloud/project/services-opensearch.html)

- [De service Elasticsearch instellen](https://devdocs.magento.com/cloud/project/services-elastic.html)

## Aangepaste triggers voorkomen

Gebruik indien mogelijk geen aangepaste triggers.

De trekkers worden gebruikt om veranderingen in controletabellen te registreren. De Adobe raadt u aan de toepassing te configureren om rechtstreeks naar de audittabellen te schrijven in plaats van de triggerfunctionaliteit te gebruiken, en wel om de volgende redenen:

- Triggers worden geïnterpreteerd als code en MySQL compileert ze niet vooraf. Hooking op de transactieruimte van uw vraag, voegen zij de overheadkosten aan een parser en een interpreter voor elke vraag toe die met de lijst wordt uitgevoerd.
- De trekkers delen de zelfde transactieruimte zoals de originele vragen, en terwijl die vragen voor sloten op de lijst concurreren, concurreren de trekkers onafhankelijk op sloten op een andere lijst.

Zie voor meer informatie over alternatieven voor het gebruik van aangepaste triggers [MySQL-triggers](mysql-configuration.md#triggers).

## Upgrade [!DNL ECE-Tools] naar versie 2002.0.21 of hoger {#ece-tools-version}

Om potentiële problemen met kroonsloten te vermijden, bevorder ECE-Hulpmiddelen aan versie 2002.0.21 of hoger. Zie voor instructies [Bijwerken `ece-tools` versie](https://devdocs.magento.com/cloud/project/ece-tools-update.html) in onze ontwikkelaarsdocumentatie.

## Veilig overschakelen op indexmodus

<!--This best practice might belong in the Maintenance phase. Database lock prevention might be consolidated under a single heading-->

De omschakeling indexeert produceert [!DNL data definition language] (DDL) verklaringen om trekkers tot stand te brengen die gegevensbestandsloten kunnen veroorzaken. U kunt dit probleem voorkomen door uw website in de onderhoudsmodus te plaatsen en de taken voor uitsnijden uit te schakelen voordat u de configuratie wijzigt.
Zie voor instructies [Indexeerders configureren](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html#configure-indexers-1) in de *Adobe Commerce-configuratiegids*.

## DDL-instructies niet uitvoeren in productie

Vermijd het uitvoeren van verklaringen DDL in het milieu van de Productie om conflicten (zoals lijstwijzigingen en creaties) te verhinderen. De `setup:upgrade` -proces is een uitzondering.

Als u een DDL-instructie moet uitvoeren, zet u de website in de onderhoudsmodus en schakelt u de uitsnede uit (zie de instructies voor het veilig omschakelen van indexen in de vorige sectie).

## Archivering van bestellingen inschakelen

Archivering van bestellingen via de beheerder inschakelen om de benodigde ruimte voor verkooptabellen te verkleinen naarmate de gegevens van uw bestelling toenemen. Met archivering bespaart u MySQL-schijfruimte en verbetert u de afrekenprestaties.

Zie [Archivering inschakelen](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-archive.html) in de documentatie van Adobe Commerce Merchant.

## Aanvullende informatie

- [MySQL-opslagengines](https://dev.mysql.com/doc/refman/8.0/en/storage-engines.html)
- [Adobe Commerce 2.3.5-upgradevoorwaarden voor MariaDB](../maintenance/commerce-235-upgrade-prerequisites-mariadb.md)
- [Aanbevolen procedures om prestatieproblemen met databases op te lossen](../maintenance/resolve-database-performance-issues.md)
