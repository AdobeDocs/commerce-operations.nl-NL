---
title: Huidige zoekengine wordt niet ondersteund
description: Los uw Adobe Commerce of verbetering van de Magento Open Source na het ontmoeten van een fout over een niet gestaafde onderzoeksmotor problemen op.
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# Huidige zoekengine wordt niet ondersteund

Het volgende foutbericht geeft aan dat de Adobe Commerce- of Magento Open Source-versie waarvan u een upgrade uitvoert, is geconfigureerd voor het gebruik van een zoekprogramma voor catalogi dat niet wordt ondersteund in de versie waarnaar u de upgrade uitvoert:

```terminal
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Deze fout betekent dat een van de volgende voorwaarden geldt voor de versie op downniveau van Adobe Commerce of Magento Open Source:

- Het zoekprogramma is ingesteld op MySQL.
- Het zoekprogramma is ingesteld op een versie van Elasticsearch die niet meer wordt ondersteund.

Gebruik de volgende opdracht om de huidige zoekfunctie te controleren:

```bash
bin/magento config:show catalog/search/engine
```

De fout treedt op als de geretourneerde waarde `mysql`, `elasticsearch`, of `elasticsearch6`.

>[!WARNING]
>
>Als deze fout is opgetreden, verloopt de installatie niet correct en hebt u geen toegang tot de beheerder. We raden u aan terug te keren naar uw vorige versie terwijl u deze fout verhelpt. Voer hiertoe een van de volgende opdrachten uit:
>
>
```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>
```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Wanneer `<version>` is de versie van de Magento die u hebt uitgevoerd **voor** de upgrade. Bijvoorbeeld: `2.3.5`.

Volg de richtlijnen die in de volgende secties worden beschreven om van een inconsistente staat terug te krijgen.

## Als uw zoekmachine `mysql`

In eerdere versies dan 2.4 was MySQL de standaardzoekengine voor catalogi, maar MySQL wordt in deze hoedanigheid niet meer ondersteund. Nu moet u Elasticsearch of OpenSearch installeren en configureren als zoekprogramma voordat u de upgrade uitvoert naar 2.4.

Gebruik de volgende bronnen om u door dit proces te begeleiden:

- [De zoekengine installeren en configureren](../../configuration/search/overview-search.md)
- [Configuratie van zoekmachine](../../configuration/search/configure-search-engine.md)

Nadat u de zoekmachine en de herindex hebt geconfigureerd, kunt u een upgrade uitvoeren naar 2.4.

## Als uw zoekmachine `elasticsearch`

Elasticsearch 6 en eerder worden niet meer ondersteund.

Een waarde van `elasticsearch` Hiermee geeft u aan dat uw versie op downniveau van Adobe Commerce of Magento Open Source is geconfigureerd voor gebruik van Elasticsearch 2.x. Deze versie van Elasticsearch wordt niet meer ondersteund.

U moet de volgende taken uitvoeren alvorens aan 2.4 te bevorderen:

1. Update aan een versie van Elasticsearch die door de Handel wordt gesteund. Zie [Elasticsearch bijwerken](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) voor volledige instructies voor het maken van back-ups van uw gegevens, het opsporen van potentiële migratiekwesties en het testen van upgrades voordat u deze implementeert naar de productie. Afhankelijk van uw huidige versie van Elasticsearch, is het mogelijk dat een volledige clusterherstart al dan niet vereist is.

   >[!NOTE]
   >
   >Elasticsearch vereist JDK 1.8 of hoger. Zie [De JDK (Java Software Development Kit) installeren](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) om te controleren welke versie van JDK is geïnstalleerd.

1. [Elasticsearch configureren](../../configuration/search/configure-search-engine.md) en opnieuw indexeren.

Nadat u de zoekmachine en de herindex hebt geconfigureerd, kunt u een upgrade uitvoeren naar 2.4.
