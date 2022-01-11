---
title: Huidige zoekengine wordt niet ondersteund
description: Los uw Adobe Commerce of verbetering van de Magento Open Source na het ontmoeten van een fout over een niet gestaafde onderzoeksmotor problemen op.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---


# Huidige zoekengine wordt niet ondersteund

Het volgende foutbericht geeft aan dat de Magento-versie waarvan u een upgrade uitvoert, is geconfigureerd voor het gebruik van een zoekfunctie voor catalogi die niet wordt ondersteund in de Magento-versie waarnaar u een upgrade uitvoert:

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

De fout treedt op als de geretourneerde waarde `mysql` of `elasticsearch`.

>[!WARNING]
>
>Als deze fout is opgetreden, is de status van Magento inconsistent en hebt u geen toegang tot de beheerder. We raden u aan terug te keren naar uw vorige versie terwijl u deze fout verhelpt. Voer hiertoe een van de volgende opdrachten uit:
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

In eerdere versies dan 2.4 was MySQL de standaardzoekengine voor catalogi, maar MySQL wordt in deze hoedanigheid niet meer ondersteund. Nu, moet u Elasticsearch als uw onderzoeksmotor installeren en vormen alvorens aan 2.4 te bevorderen.

Gebruik de volgende bronnen om u door dit proces te begeleiden:

- [Elasticsearch installeren en configureren](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-overview.html)
- [Elasticsearch installeren](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)
- Elasticsearch configureren om mee te werken [nginx](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-nginx.html) of [Apache](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/es-config-apache.html)
- [Magento configureren voor gebruik van Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html)

Nadat u Elasticsearch en herdex vormt, bent u bereid om aan 2.4 te bevorderen.

## Als uw zoekmachine `elasticsearch`

Een waarde van `elasticsearch` Hiermee geeft u aan dat uw versie op downniveau van Adobe Commerce of Magento Open Source is geconfigureerd voor gebruik van Elasticsearch 2.x. Deze versie van Elasticsearch wordt niet meer ondersteund.

U moet de volgende taken uitvoeren alvorens aan 2.4 te bevorderen:

1. Elasticsearch bijwerken. We raden u aan de update naar Elasticsearch 7.x uit te voeren. Zie [Elasticsearch bijwerken](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) voor volledige instructies voor het maken van back-ups van uw gegevens, het opsporen van potentiële migratiekwesties en het testen van upgrades voordat u deze implementeert naar de productie. Afhankelijk van uw huidige versie van Elasticsearch, is het mogelijk dat een volledige clusterherstart al dan niet vereist is.

   >[!NOTE]
   >
   >Elasticsearch vereist JDK 1.8 of hoger. Zie [De JDK (Java Software Development Kit) installeren](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#prereq-java) om te controleren welke versie van JDK is geïnstalleerd.

1. [Magento configureren voor gebruik van Elasticsearch](https://devdocs.magento.com/guides/v2.3/config-guide/elasticsearch/configure-magento.html) en opnieuw indexeren.

Nadat u Elasticsearch en herdex vormt, bent u bereid om aan 2.4 te bevorderen.
