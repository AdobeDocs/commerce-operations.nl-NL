---
title: Geavanceerde instellingen
description: Bekijk best practices en aanbevelingen voor grote bedrijfssystemen die zijn ontworpen om grote hoeveelheden gegevens te verwerken.
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---

# Geavanceerde instellingen

[!DNL Commerce] is een hoogst flexibel en scalable product dat oplossingen voor verkopers van elke grootte bevat. Deze sectie behandelt beste praktijken en aanbevelingen bij het vormen [!DNL Commerce] om met grote hoeveelheden gegevens, extreme lading, en andere ondernemingsgevallen te werken.

## Indexprestaties kalibreren

Bij grote hoeveelheden gegevens kan het opnieuw indexeren een probleem worden. De [!DNL Commerce] het team selecteerde de meest geladen indexen en liet partij indexeren toe, die u toestaat om een gedeelte van gegevens te plaatsen die op elke herhaling moeten worden verwerkt. Op deze manier kan de gebruiker de grootte van de batch aanpassen op basis van het type en de grootte van de gegevens in de database.

Als u deze instelling wilt beheren, bewerkt u de `batchRowsCount` in de `di.xml` bestand van de overeenkomstige module. De volgende indexen ondersteunen deze functie:

* Categorieproductindex (catalogusmodule)
* Prijsindex (module Catalogus)
* EAV-index (catalogusmodule)
* Bestandsindex (module CatalogInventory)

U kunt de indexeerprestaties afstemmen door de variabelen voor de grootte van de indexbatchreeksen aan te passen. Hiermee bepaalt u hoeveel entiteiten per keer door de indexer worden verwerkt. In sommige situaties, hebben wij significante dalingen in het indexeren tijd gezien.

Als u bijvoorbeeld een profiel uitvoert dat lijkt op B2B Medium, kunt u de configuratiewaarde overschrijven `batchRowsCount` in `app/code/Magento/catalog/etc/di.xml` en overschrijf de standaardwaarde van `5000` tot `1000`. Dit vermindert de volledige indexerende tijd van 4 uren neer aan 2 uren met een gebrek [!DNL MySQL] configuratie.

>[!NOTE]
>
>Het in batches plaatsen is niet ingeschakeld voor de indexfunctie voor catalogusregels. Handelaars met een groot aantal catalogusregels moeten hun [!DNL MySQL] configuratie om de indexatietijd te optimaliseren. In dit geval kunt u uw [!DNL MySQL] Het configuratiedossier en het toewijzen van meer geheugen aan de TMP_TABLE_SIZE en MAX_HEAP_TABLE_SIZE configuratiewaarden (het gebrek is 16M voor allebei) zullen prestaties voor deze indexeerder verbeteren, maar zal in [!DNL MySQL] meer RAM-geheugen verbruiken.

### Beperk klantgroepen en gedeelde catalogi door websites

Een groot aantal product-SKU&#39;s, websites, klantgroepen of gedeelde catalogi is van invloed op de runtime van de indexeerders Product Price en Catalog Rule. Dit komt doordat standaard alle websites zijn toegewezen aan alle klantengroepen (gedeelde catalogi).

Als u de indexatietijd wilt verkorten, kunt u [bepaalde websites uitsluiten van klantengroepen (gedeelde catalogi)](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Redis instellen

Soms is één instantie Redis niet genoeg om binnenkomende verzoeken te dienen. Er zijn verschillende oplossingen die we kunnen aanbevelen om deze situatie aan te pakken.

Eerste, [!DNL Commerce] kunt u afzonderlijke cacheopslag configureren voor elk type cache. Op deze manier kunt u net zoveel afzonderlijke Redis-exemplaren installeren als het aantal cachetypen dat in Magento is geregistreerd. Realistisch gezien, zou u instanties Redis voor de actiefste gebruikte geheime voorgeheugens, zoals configuratie, lay-out, en blokken kunnen willen.

Een andere oplossing kan zijn om het configuratiecache op het dossiersysteem te plaatsen en de andere geheime voorgeheugens naar de Redis server te verplaatsen. Met deze oplossing hebt u een afzonderlijk hulpmiddel nodig voor gecentraliseerde ongeldigmaking van configuratiecache op al uw webknooppunten.

U kunt ook een Redis-cluster gebruiken die parallelle lees- en schrijfbewerkingen uitvoert met een automatisch toenemend aantal knooppunten. [!DNL Commerce] biedt geen configuratie voor dit geval, maar kan worden gestart met kleine aanpassingen.

## Instellen [!DNL RabbitMQ]

Magento Open Source en Adobe [!DNL Commerce] de rijen van het steunbericht die door worden uitgevoerd [!DNL RabbitMQ]. [!DNL Commerce] gebruikt deze service voor het uitvoeren van talloze asynchrone bewerkingen, waaronder B2B-catalogusbewerkingen en asynchrone voorraadupdates. Alle interfaces voor het toevoegen van meer banen aan de baanserver worden gedistribueerd met het product en zijn beschikbaar voor douane asynchrone logische implementatie in het werkingsgebied van derdeuitbreidingen. Zoals bij elke andere integratie [!DNL Commerce] verstrekt een dossier van de steekproefconfiguratie voor [!DNL RabbitMQ] die alle aanbevolen instellingen bevat en volledig klaar is voor productiegebruik.

## De database splitsen

>[!WARNING]
>
>De functie voor gesplitste databases was [verouderd](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) in versie 2.4.2 van Adobe Commerce. Zie [Herstel van een gesplitste database naar één database](../configuration/storage/revert-split-database.md).

Adobe Commerce staat u toe om scalable gegevensbestandopslag te vormen om aan de behoeften van groeiende zaken te voldoen. U kunt drie aparte master databases instellen die specifieke domeinen bedienen:

* Hoofddatabase (catalogus)
* Afhandelingsdatabase
* Database van het Order Management System (OMS)

Om extra gegevensbestanden te vormen, moet u een leeg gegevensbestand creëren en één van de volgende bevelen in werking stellen:

Voor Master database voor afhandeling

```bash
bin/magento setup:db-schema:split-quote
```

Voor OMS Master DB

```bash
bin/magento setup:db-schema:split-sales
```

Deze bevelen migreren specifieke domeinlijsten van het belangrijkste gegevensbestand aan een domeingegevensbestand. Zij veranderen ook [!DNL Commerce] configuratie om overeenkomstige connectiviteit en beperkingsverwerking toe te staan.

Door afzonderlijke databases voor uitchecken en Bestelbeheer te hebben, kunt u de belasting verdelen tussen uw databaseservers. U kunt meer kassa&#39;s gebruiken en meer bestellingen per seconde verwerken zonder dat dit van invloed is op de beschikbaarheid van uw catalogus en andere bewerkingen. Wij adviseren het splitsen van gegevensbestanden voor periodes flits of actieve verkoop, of het gebruiken van hen permanent voor natuurlijk high-load projecten. De migratie van huidige gegevens tussen gegevensbestanden zou onder toezicht van uw systeembeheerder moeten worden uitgevoerd.  Geen databases splitsen in productiemodus.

Naast master databases [!DNL Commerce] staat u toe om een aantal slave gegevensbestanden (voor elke die gegevensmiddel te vormen in het systeem wordt verklaard). Een slave-database fungeert als een volledige replica van uw hoofddatabase of een van uw master domeindatabases. Deze wordt uitgegeven voor leesbewerkingen op een specifieke bron.

U kunt een slave-database toevoegen door de volgende opdracht uit te voeren:

```bash
bin/magento setup:db-schema:add-slave
```

Dit bevel voert configuratieveranderingen uit maar vormt replicatie zelf niet. Dat moet handmatig gebeuren.

Nadat u de master database hebt gesplitst en slave-databases hebt ingesteld, [!DNL Commerce] regelt automatisch verbindingen met een specifieke database, waarbij beslissingen worden genomen op basis van het type verzoek (POST, PUT, GET, enz.) en de gegevensbron. Indien [!DNL Commerce] of de extensies ervan schrijven naar een GET-aanvraag, schakelt het systeem de verbinding automatisch van slave naar een master database. Het werkt de zelfde manier met master gegevensbestanden: zodra u met een op uitchecken betrekking hebbende lijst werkt, richt het systeem alle vragen aan een specifiek gegevensbestand opnieuw. Ondertussen, zullen alle op catalogus betrekking hebbende vragen naar het belangrijkste gegevensbestand gaan.

Voor meer details over de configuratie en de voordelen van veelvoudige master/slave configuratie, zie
[Oplossing voor gesplitste databaseprestaties](../configuration/storage/multi-master.md).

## Media-inhoud serveren

Magento biedt geen specifieke integratie voor het leveren en leveren van media-inhoud. Alle gangbare benaderingen kunnen samen worden gebruikt in Magento.

De eenvoudigste manier om media-inhoud te bedienen is deze op een [!DNL Varnish] server. Bij deze aanpak wordt uitgegaan van een gedeeld bestandssysteem voor het opslaan van media-inhoud of een toegewijde server die verwijst naar [!DNL Varnish].

Voor middelgrote en hoge ladingsmilieu&#39;s, adviseren wij het gebruiken van de diensten van het Netwerk van de Levering van de Inhoud (CDN) zoals Fastly, Akamai, en anderen. Wanneer u met deze services werkt, [!DNL Commerce] gebruikt de klassieke pull-benadering voor inhoudsupdates. U moet configureren [!DNL Commerce] URLs om met de overeenkomstige dienst te werken CDN. Door media-inhoud naar een CDN te verplaatsen, verlaagt u de belasting van de instanties aanzienlijk.

## Logopslag configureren

De opslag van logboeken en hun invloed op andere schijfverrichtingen beïnvloeden de beschikbaarheid van uw Webknopen, vooral in high-load situaties. Wij adviseren dat u registreren minimaliseert als u het niet nodig hebt. U kunt registreren ook vormen zodat het op een afzonderlijk opslagsysteem schrijft dat hoge toegangssnelheden heeft. Merk op dat om het even welk knelpunt bij de toegang tot van logboekopslag de verwerking van inkomende verzoeken kan direct beïnvloeden die logboek schrijft of verrichtingen als deel van hun stroom leest.
