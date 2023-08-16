---
title: Zoekstopwoorden configureren
description: Leer hoe u stopwords voor Adobe Commerce kunt beheren met gebruik van CSV-bestanden.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 789b7d9dc400b1f669de0067a59e2036c2977a19
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---

# Zoekstopwoorden configureren

In het algemeen: _stopwords_ Dit zijn veelvoorkomende woorden die zoekprogramma&#39;s uitfilteren na het verwerken van tekst. Aanvankelijk, toen schijfruimte en geheugen uiterst beperkt waren, betekende elke bespaarde kilobyte een significante verbetering van prestaties. Zodoende hebben zoekprogramma&#39;s prestatiewinst behaald door bepaalde woorden te negeren en de index klein te houden.

Hoewel we vandaag nog meer opslagruimte hebben, zijn prestaties nog steeds belangrijk. Elasticsearch en OpenSearch gebruiken, net als andere zoekprogramma&#39;s, nog steeds stopwords om de prestaties te verbeteren.

U moet de stopwoorden beheren met gebruik van CSV-bestanden in het dialoogvenster `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` of de `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` directory, afhankelijk van hoe u de software van de Handel installeerde.

Zie de volgende bronnen voor meer informatie over hoe Elasticsearch en OpenSearch gebruik maken van stopwords:

- [Stopwords: prestaties versus precisie](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Pros en klokken van stopwords](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Stopwoorden gebruiken](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Stopwoorden en prestaties](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Stopwoorden configureren

Stopwoorden bevinden zich in de `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` directory. Adobe Commerce en Magento Open Source worden geleverd met één CSV-bestand met stopwords voor de standaardlandinstellingen en een extra bestand. `stopwords.csv`, met stopwoorden voor elke landinstelling die niet wordt vertegenwoordigd door een ander CSV-bestand.

De standaardlevensduur voor de cache van stopwords-bestanden is 15 minuten.

### stopwoorden bewerken voor een bestaande landinstelling

**Stopwoorden bewerken**:

1. Meld u aan bij de Commerce-server of schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).
1. Een teksteditor gebruiken om een stopwoordbestand te openen in het dialoogvenster `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` directory.

   CSV-bestanden gebruiken de naamgevingsconventie `stopwords_<locale_code>.csv`. Het Duitse stopword-bestand krijgt bijvoorbeeld de naam `stopwords_de_DE.csv`.

1. Voeg woorden toe, verwijder woorden of wijzig woorden in het bestand.

   (Elk stopwoord in een bestand begint op een nieuwe regel.)

1. Sla de wijzigingen op en sluit de teksteditor af.
1. Reinig de configuratiecache.

   - Beheerder: **Systeem** > Gereedschappen > **Cachebeheer**. Selecteer de **Configuratie** en klikt u in de bovenstaande lijst op **Vernieuwen**. Klikken **Verzenden** om de actie te voltooien.

   - Opdrachtregel: Voer de volgende opdracht in als de eigenaar van het bestandssysteem:

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Controleer de resultaten door te zoeken naar termen in je winkel.

### stopwoorden maken voor een nieuwe landinstelling

**Stop-woorden toevoegen voor een landinstelling**:

1. Meld u aan bij de Commerce-server of schakel over naar de [eigenaar van bestandssysteem](../../installation/prerequisites/file-system/overview.md).

1. Een teksteditor gebruiken om een stopword-bestand met de naam `stopwords_<locale_code>.csv` in de `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` directory.

   Als u bijvoorbeeld stopwoorden voor de landinstelling in Italië wilt maken, geeft u het bestand een naam `stopwords_it_IT.csv`.

1. Zorg ervoor dat elk stopword in het stopword-bestand zich op een aparte regel bevindt.
1. Sla de wijzigingen op en sluit de teksteditor af.
1. In dezelfde map opent u `esconfig.xml` in een teksteditor.
1. Een regel toevoegen aan `esconfig.xml` als volgt:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Als u bijvoorbeeld een Italiaans stopword-bestand wilt toevoegen, voegt u de volgende regel toe:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. De wijzigingen opslaan in `esconfig.xml` en sluit de teksteditor af.
1. Reinig de configuratiecache.

   - Beheerder: **Systeem** > Gereedschappen > **Cachebeheer**. Selecteer de **Configuratie** en klikt u in de bovenstaande lijst op **Vernieuwen**. Klikken **Verzenden** om de actie te voltooien.

   - Opdrachtregel: Voer de volgende opdracht in als de eigenaar van het bestandssysteem:

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Controleer de resultaten door te zoeken naar termen in je winkel.

## De map stopword wijzigen

In deze sectie wordt beschreven hoe u de standaardmap stopword optioneel kunt wijzigen op basis van een van de volgende opties:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

De locatie is afhankelijk van de manier waarop u de software Commerce hebt geïnstalleerd. Als u Magento 2 de bewaarplaats van GitHub kloond, is de weg onder `app/code`. Als u een gecomprimeerd archief of een pakket hebt geïnstalleerd, is het pad lager dan `vendor`.

**De map wijzigen**:

1. Open als eigenaar van het bestandssysteem de Elasticsearch `di.xml` in een teksteditor.

   Als u de opslagplaats hebt gekloond, bevindt deze zich op `app/code/Magento/Elasticsearch/etc/di.xml`

   Als u een archief of het metapakket hebt, bevindt het zich op `vendor/magento/module-elasticsearch/etc/di.xml`

1. De waarde wijzigen van `stopwordsDirectory` naar de gewenste map:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Sla uw wijzigingen op in `di.xml` en sluit de teksteditor af.

## Om de folder van uw module te veranderen

1. [Een module maken](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. In uw module `etc/di.xml` instructies toevoegen:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Maak de map in uw module `etc/stopwords`, met het bijbehorende CSV-bestand.

1. Sla uw wijzigingen op in `di.xml` en sluit de teksteditor af.
