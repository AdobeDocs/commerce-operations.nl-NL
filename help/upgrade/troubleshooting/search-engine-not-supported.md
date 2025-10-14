---
title: Huidige zoekengine wordt niet ondersteund
description: Los uw verbetering van Adobe Commerce na het ontmoeten van een fout over een niet gestaafd onderzoeksmotor problemen op.
feature: Upgrade, Search
exl-id: 11479d23-53a5-4086-9f9a-c3420ccad073
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Huidige zoekengine wordt niet ondersteund

Het volgende foutbericht geeft aan dat de Adobe Commerce-versie waarvan u een upgrade uitvoert, is geconfigureerd voor het gebruik van een zoekfunctie voor catalogi die niet wordt ondersteund in de versie waarnaar u de upgrade uitvoert:

```
Your current search engine, <Engine Name>, is not supported. You must install a supported search engine before upgrading. See the System Upgrade Guide for more information.
```

Deze fout betekent dat een van de volgende voorwaarden geldt voor de versie op downniveau van Adobe Commerce:

- Het zoekprogramma is ingesteld op MySQL.
- Het zoekprogramma is ingesteld op een versie van Elasticsearch die niet meer wordt ondersteund.

Gebruik de volgende opdracht om de huidige zoekfunctie te controleren:

```bash
bin/magento config:show catalog/search/engine
```

De fout treedt op als de geretourneerde waarde `mysql` , `elasticsearch` of `elasticsearch6` is.

>[!WARNING]
>
>Als deze fout is opgetreden, verloopt de installatie niet correct en hebt u geen toegang tot de beheerder. We raden u aan terug te keren naar uw vorige versie terwijl u deze fout verhelpt. Voer hiertoe een van de volgende opdrachten uit:
>
>```bash
>composer require-commerce magento/product-enterprise-edition=<version>
>```
>
>```bash
>composer require-commerce magento/product-community-edition=<version>
>```
>
>Waar `<version>` de versie van Magento is u **vóór** de verbetering in werking stelde. Bijvoorbeeld `2.3.5` .

Volg de richtlijnen die in de volgende secties worden beschreven om van een inconsistente staat terug te krijgen.

## Als uw zoekmachine `mysql` is

In eerdere versies dan 2.4 was MySQL de standaardzoekengine voor catalogi, maar MySQL wordt in deze hoedanigheid niet meer ondersteund. Nu moet u Elasticsearch of OpenSearch installeren en configureren als zoekprogramma voordat u de upgrade uitvoert naar versie 2.4.

Gebruik de volgende bronnen om u door dit proces te begeleiden:

- [De zoekengine installeren en configureren](../../configuration/search/overview-search.md)
- [Configuratie van zoekmachine](../../configuration/search/configure-search-engine.md)

Nadat u het onderzoeksmotor en de herindex vormt, bent u bereid aan verbetering 2.4.

## Als uw zoekmachine `elasticsearch` is

Elasticsearch 6 en eerder worden niet meer ondersteund.

De waarde `elasticsearch` geeft aan dat uw versie op downniveau van Adobe Commerce is geconfigureerd voor Elasticsearch 2.x. Deze versie van Elasticsearch wordt niet meer ondersteund.

U moet de volgende taken uitvoeren alvorens aan 2.4 te bevorderen:

1. Update uitvoeren naar een versie van Elasticsearch die wordt ondersteund door Commerce. Verwijs naar [&#x200B; Bevorderend Elasticsearch &#x200B;](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup-upgrade.html) voor volledige instructies bij het steunen van uw gegevens, het ontdekken van potentiële migratiekwesties, en het testen van verbeteringen alvorens aan productie op te stellen. Afhankelijk van uw huidige versie van Elasticsearch is het mogelijk dat een volledige cluster opnieuw moet worden opgestart.

   >[!NOTE]
   >
   >Elasticsearch vereist JDK 1.8 of hoger. Zie [&#x200B; de Uitrusting van de Ontwikkeling van de Software van Java installeren (JDK) &#x200B;](../../installation/prerequisites/search-engine/overview.md#install-the-java-software-development-kit-jdk) om te controleren welke versie van JDK geïnstalleerd is.

1. [&#x200B; vorm Elasticsearch &#x200B;](../../configuration/search/configure-search-engine.md) en herdex.

Nadat u het onderzoeksmotor en de herindex vormt, bent u bereid aan verbetering 2.4.
