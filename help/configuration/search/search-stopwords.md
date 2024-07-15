---
title: Zoekstopwoorden configureren
description: Leer hoe u stopwords voor Adobe Commerce kunt beheren met gebruik van CSV-bestanden.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Zoekstopwoorden configureren

In het algemeen, _stopwords_ zijn gemeenschappelijke woorden die de onderzoeksmotoren uit na verwerkingstekst filtreren. Aanvankelijk, toen schijfruimte en geheugen uiterst beperkt waren, betekende elke bespaarde kilobyte een significante verbetering van prestaties. Zodoende hebben zoekprogramma&#39;s prestatiewinst behaald door bepaalde woorden te negeren en de index klein te houden.

Hoewel we vandaag nog meer opslagruimte hebben, zijn prestaties nog steeds belangrijk. Elasticsearch en OpenSearch gebruiken, net als andere zoekprogramma&#39;s, nog steeds stopwords om de prestaties te verbeteren.

U moet de stopwoorden beheren met gebruik van CSV-bestanden in de map `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` of `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` , afhankelijk van de manier waarop u de Commerce-software hebt geïnstalleerd.

Zie de volgende bronnen voor meer informatie over hoe Elasticsearch en OpenSearch gebruik maken van stopwords:

- [ stoppenWoorden: Prestaties versus Precisie ](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [ Pros en Kons van Stopwords ](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [ Gebruikend Stopwords ](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [ stopwords en Prestaties ](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Stopwoorden configureren

Stopwoorden staan in de map `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` . Adobe Commerce wordt geleverd met één CSV-bestand met stopwords voor de standaardlandinstellingen en een extra bestand, `stopwords.csv` , dat stopwoorden bevat voor elke landinstelling die niet wordt vertegenwoordigd door een ander CSV-bestand.

De standaardlevensduur voor de cache van stopwords-bestanden is 15 minuten.

### stopwoorden bewerken voor een bestaande landinstelling

**om stopwords uit te geven**:

1. Login aan uw server van Commerce, of schakelaar aan, de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).
1. Gebruik een teksteditor om een stopword-bestand te openen in de map `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` .

   CSV-bestanden gebruiken de naamgevingsconventie `stopwords_<locale_code>.csv` . Het Duitse stopword-bestand heeft bijvoorbeeld de naam `stopwords_de_DE.csv` .

1. Voeg woorden toe, verwijder woorden of wijzig woorden in het bestand.

   (Elk stopwoord in een bestand begint op een nieuwe regel.)

1. Sla de wijzigingen op en sluit de teksteditor af.
1. Reinig de configuratiecache.

   - Admin: **Systeem** > Hulpmiddelen > **Beheer van het Geheime voorgeheugen**. Selecteer **checkbox van de Configuratie** en, van de lijst boven het, klik **verfrissen**. Klik **voorleggen** om de actie te voltooien.

   - Opdrachtregel: Voer de volgende opdracht in als de eigenaar van het bestandssysteem:

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Controleer de resultaten door te zoeken naar termen in je winkel.

### stopwoorden maken voor een nieuwe landinstelling

**om stopwords voor een scène** toe te voegen:

1. Login aan uw server van Commerce, of schakelaar aan, de [ eigenaar van het dossiersysteem ](../../installation/prerequisites/file-system/overview.md).

1. Gebruik een teksteditor om een stopword-bestand met de naam `stopwords_<locale_code>.csv` in de map `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` te maken.

   Als u bijvoorbeeld stopwoorden wilt maken voor de landinstelling in Italië, geeft u het bestand de naam `stopwords_it_IT.csv` .

1. Zorg ervoor dat elk stopword in het stopword-bestand zich op een aparte regel bevindt.
1. Sla de wijzigingen op en sluit de teksteditor af.
1. Open `esconfig.xml` in dezelfde map in een teksteditor.
1. Voeg als volgt een regel toe aan `esconfig.xml` :

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Als u bijvoorbeeld een Italiaans stopword-bestand wilt toevoegen, voegt u de volgende regel toe:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Sla de wijzigingen in `esconfig.xml` op en sluit de teksteditor af.
1. Reinig de configuratiecache.

   - Admin: **Systeem** > Hulpmiddelen > **Beheer van het Geheime voorgeheugen**. Selecteer **checkbox van de Configuratie** en, van de lijst boven het, klik **verfrissen**. Klik **voorleggen** om de actie te voltooien.

   - Opdrachtregel: Voer de volgende opdracht in als de eigenaar van het bestandssysteem:

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Controleer de resultaten door te zoeken naar termen in je winkel.

## De map stopword wijzigen

In deze sectie wordt beschreven hoe u de standaardmap stopword optioneel kunt wijzigen op basis van een van de volgende opties:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

De locatie is afhankelijk van de manier waarop u de Commerce-software hebt geïnstalleerd. Als u Magento 2 GitHub bewaart, is de weg onder `app/code`. Als u een gecomprimeerd archief of een metapakket hebt geïnstalleerd, is het pad kleiner dan `vendor` .

**om de folder** te veranderen:

1. Open als eigenaar van het bestandssysteem de Elasticsearch `di.xml` in een teksteditor.

   Als u de repository hebt gekloond, bevindt deze zich op `app/code/Magento/Elasticsearch/etc/di.xml`

   Als u een archief of het metapakket hebt, bevindt het zich op `vendor/magento/module-elasticsearch/etc/di.xml`

1. Wijzig de waarde van `stopwordsDirectory` in de gewenste map:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Sla de wijzigingen in `di.xml` op en sluit de teksteditor af.

## Om de folder van uw module te veranderen

1. [ creeer een module ](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. Voeg instructies toe in de module `etc/di.xml` :

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Maak in uw module de map `etc/stopwords` met het bijbehorende CSV-bestand.

1. Sla de wijzigingen in `di.xml` op en sluit de teksteditor af.
