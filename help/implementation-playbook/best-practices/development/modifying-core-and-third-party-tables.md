---
title: Aanbevolen procedures voor het wijzigen van databasetabellen
description: Leer hoe en wanneer u Adobe Commerce en databasetabellen van derden wijzigt.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# Aanbevolen procedures voor het wijzigen van databasetabellen

Dit artikel biedt tips en trucs voor het wijzigen van databasetabellen die worden gemaakt door [!DNL Adobe Commerce] of modules van derden. Begrijpen wanneer en hoe te om lijsten effectief te wijzigen helpt de levensvatbaarheid en stabiliteit op lange termijn van uw handelsplatform verzekeren.

Migreren van [!DNL Magento 1] en andere e-commerceplatforms, of het werken met modules van [!DNL Adobe Commerce] Marketplace kan extra gegevens toevoegen en opslaan. Uw eerste instinct zou kunnen zijn om een kolom aan een gegevensbestandlijst toe te voegen, of bestaande aan te passen. U moet echter alleen een kern wijzigen [!DNL Adobe Commerce] tabel (of tabel van een externe leverancier) in beperkte situaties.

## Waarom Adobe aanbeveelt wijzigingen te vermijden

De belangrijkste reden om het wijzigen van kernlijsten te vermijden is dat Adobe Commerce onderliggende logica omvat die ruwe SQL vragen bevat. Wijzigingen in de structuur van de tabel kunnen leiden tot onverwachte bijwerkingen die moeilijk zijn op te lossen. De wijziging kan ook invloed hebben op bewerkingen met DDL (Data Definition Language) die onverwachte en onvoorspelbare gevolgen voor de prestaties hebben.

Een andere reden om te vermijden veranderend de structuur van de gegevensbestandlijst is dat uw veranderingen kwesties kunnen veroorzaken als het team van de kernontwikkeling of derdeontwikkelaars de structuur van hun gegevensbestandlijsten veranderen. Er zijn bijvoorbeeld een paar kerndatabasetabellen die een kolom hebben met de naam `additional_data`. Dit is altijd een `text` kolomtype. Nochtans, voor prestatiesredenen, zou het kernteam de kolom kunnen veranderen in `longtext`. Dit type kolom is een alias voor JSON. Door in dit kolomtype om te zetten, worden er prestatiewinst en zoekbaarheid toegevoegd aan die kolom, die niet als a bestaat `text` type. Meer informatie over dit onderwerp vindt u in [JSON-gegevenstype](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Weet wanneer gegevens moeten worden opgeslagen of verwijderd

Adobe raadt u aan eerst te bepalen of u deze gegevens moet opslaan. Als u gegevens verplaatst van een verouderd systeem, bespaart gegevens die u kunt verwijderen u tijd en moeite tijdens de migratie. (Er zijn manieren om gegevens te archiveren als het later moet worden betreden.) Om een goede beheerder van de toepassing en de prestaties te zijn, is het in orde om een verzoek uit te dagen om extra gegevens te bewaren. Uw doel is ervoor te zorgen dat het bewaren van de gegevens een vereiste is om een bedrijfsbehoefte te vervullen die niet een andere manier kan worden gevuld.

### Oudere gegevens

Als uw project erfenisgegevens, zoals oude orden of klantenverslagen bevat, overweeg een alternatieve raadplegingsmethode. Bijvoorbeeld, als de zaken toegang tot de gegevens slechts voor occasionele verwijzing vereisen, overweeg uitvoerend een extern onderzoek van het oude gegevensbestand buiten het handelsplatform wordt ontvangen in plaats van migrerend oude gegevens aan [!DNL Adobe Commerce].

Deze situatie zou vereisen dat de database naar een server wordt gemigreerd, waarbij een webinterface wordt aangeboden om de gegevens te lezen, of een training in het gebruik van MySQL Workbench of vergelijkbare tools. Als u deze gegevens niet in de nieuwe database opneemt, wordt de migratie versneld doordat het ontwikkelingsteam zich kan richten op de nieuwe site in plaats van problemen met de migratie van gegevens op te lossen.

Een andere verwante optie voor het houden van de gegevens extern aan handel maar het toestaan van u om het in echt te gebruiken - tijd zou andere hulpmiddelen, zoals het netwerk van GraphQL leveraging. Deze optie combineert verschillende gegevensbronnen en retourneert deze als één reactie.

U kunt bijvoorbeeld `stitch` oude bestellingen van een externe database samen te voegen, bijvoorbeeld de oude Magento 1-site die is ontmanteld. Dan gebruikend het net van GraphQL, toon hen als deel van de klantenorde geschiedenis. Deze oude bestellingen kunnen worden gecombineerd met de bestellingen van uw huidige [!DNL Adobe Commerce] milieu.

Ga voor meer informatie over het gebruik van API-netten met GraphQL naar [Wat is API-net](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) and [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Oudere gegevens migreren met extensiekenmerken

Als u vaststelt dat oudere gegevens moeten worden gemigreerd of dat nieuwe gegevens moeten worden opgeslagen [!DNL Adobe Commerce], raadt Adobe aan [extensiekenmerken](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. Het gebruik van extensiekenmerken voor het opslaan van aanvullende gegevens biedt de volgende voordelen:

- U kunt de gegevens controleren die en de gegevensbestandstructuur worden voortgeduurd, die ervoor zorgt dat het gegeven met het correcte kolomtype en juiste indexen wordt bewaard.
- Meeste entiteiten in [!DNL Adobe Commerce] en [!DNL Magento Open Source] het gebruik van extensiekenmerken ondersteunen.
- Extensiekenmerken zijn een agnostisch opslagmechanisme dat de flexibiliteit biedt om de gegevens op te slaan op de optimale locatie voor uw project.

Twee voorbeelden van opslagplaatsen zijn gegevensbestandlijsten en [!DNL Redis]. Bij het kiezen van een locatie moet u rekening houden met de vraag of een locatie een extra complexiteit veroorzaakt of van invloed is op de prestaties.

### Andere alternatieven overwegen

Als ontwikkelaar is het van essentieel belang om altijd te overwegen om hulpmiddelen buiten uw [!DNL Adobe Commerce] omgeving, zoals GraphQL mesh en Adobe App Builder. Deze hulpmiddelen kunnen u helpen toegang tot de gegevens behouden maar hebben geen invloed op de kernhandelstoepassing of zijn onderliggende gegevensbestandlijsten. Met deze aanpak maakt u uw gegevens beschikbaar via een API. Dan, voegt u een gegevensbron aan uw configuratie van de Bouwer van de App toe. Met GraphQL Mesh kunt u die gegevensbronnen combineren en één reactie produceren, zoals vermeld in [oudere gegevens](#legacy-data).

Zie voor meer informatie over GraphQL-netten [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. For information about the Adobe App Builder,  see [Introducing App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}.

## Een kerntabel of tabel van derden wijzigen

Als u besluit om gegevens op te slaan door een kern te wijzigen [!DNL Adobe Commerce] Voor een databasetabel met een externe module gebruikt u de volgende richtlijnen om de invloed op de stabiliteit en prestaties tot een minimum te beperken.

- Alleen nieuwe kolommen toevoegen.
- De _type_ waarde van een bestaande kolom. Wijzig een `integer` een `varchar` om aan uw unieke gebruiksscenario te voldoen.
- Voeg geen kolommen toe aan tabellen met EAV-kenmerken. Deze tabellen zijn al overbelast met logica en verantwoordelijkheid.
- Bepaal de grootte van een tabel voordat u deze aanpast. Het veranderen van grote lijsten beïnvloedt de plaatsing, die notulen of uren van vertraging kan veroorzaken wanneer de veranderingen worden toegepast.

## Aanbevolen procedures voor het wijzigen van een externe databasetabel

De Adobe raadt u aan deze stappen te volgen wanneer u een kolom toevoegt aan een kerndatabasetabel of een tabel van derden:

1. Maak een module met een naam in de naamruimte die aangeeft wat u wilt bijwerken.

   Bijvoorbeeld: `app/code/YourCompany/Customer`

1. Maak de juiste bestanden om de module in te schakelen (zie [Een module maken](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. Een bestand maken met de naam `db_schema.xml` in de `etc` en breng de gewenste wijzigingen aan.

   Indien van toepassing, een `db_schema_whitelist.json` bestand. Zie [Declarative Schema](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} voor meer informatie .

### Mogelijke effecten

Het toevoegen van een kolom aan een extern gegevensbestand kan uw Adobe Commerce project op de volgende manieren beïnvloeden:

- Upgrades kunnen complexer zijn.
- De plaatsingen worden beïnvloed als de lijst die groot is wordt gewijzigd.
- De migratie naar een nieuw platform zou ingewikkelder kunnen zijn.

## Manieren om het wijzigen van kerntabellen te vermijden

U kunt voorkomen dat u Adobe Commerce-databasetabellen wijzigt met [extensiekenmerken](#migrate-legacy-data-with-extension-attributes). Een ander alternatief is het gebruik van een speciale kolom (`additional_data`) vindt u in enkele kerntabellen om gegevens op te slaan en op te slaan in de indeling JSON-gecodeerd.

### Gegevens opslaan in een gegevenskolom die met JSON is gecodeerd

Sommige kerntabellen bevatten een `additional_data` kolom die JSON-gecodeerde gegevens bevat. Deze kolom biedt een native manier om extra gegevens in één veld toe te wijzen. Met deze methode vermijdt u het toevoegen van een tabel voor kleine, eenvoudige gegevenselementen die informatie voor gegevensherwinning zonder zoekopdracht opslaan. De `additional_data` de kolom is typisch beschikbaar slechts op het puntniveau, niet voor het volledige citaat of de orde.

- De voordelen van het gebruik van de `additional_data` field

   - Er zijn geen extra velden nodig, waardoor het aantal kolommen minimaal blijft. Dit is nuttig in de verkoopstroom, waar er vele lijsten reeds betrokken zijn. Het is beter om dit al ingewikkelde proces niet nog complexer te maken. Deze methode voldoet aan veel gebruikstoepassingen, maar niet aan alle.

- Nadelen

   - Deze methode is alleen ideaal voor het opslaan van alleen-lezen gegevens. Dit probleem doet zich voor omdat onze code niet-geserialiseerd moet zijn om het object te wijzigen en samen te stellen om afhankelijkheden of databaserelaties toe te voegen.

   - Het is moeilijk om databasebewerkingen te gebruiken om naar deze velden te zoeken. Het zoeken met deze methode gaat langzaam.

   - Bij de opslag van gegevens in de `additional_data` om te voorkomen dat serialisatie- of niet-serialisatiebewerkingen worden uitgevoerd die de code kunnen onderbreken door een ongeldige JSON te maken of tijdens runtime leesfouten te veroorzaken.

   - Deze velden moeten duidelijk in de code worden aangegeven, zodat een ontwikkelaar ze gemakkelijk kan vinden.

   - Andere problemen die kunnen optreden en die zeer moeilijk te diagnosticeren kunnen zijn. Bijvoorbeeld met sommige native PHP functies als je deze niet gebruikt [!DNL Adobe Commerce] omvattende methoden die door de kerntoepassing worden aangeboden, kan het eindresultaat van de getransformeerde gegevens afwijken van de verwachte indeling. Gebruik altijd de omvattende functies om consistentie en voorspelbaarheid van de gegevens te verzekeren die worden bewaard of teruggewonnen.

Hier zijn voorbeelden van tabellen die de kolom en structuur voor de `additional_data` kolom.

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

In versies 2.4.3, 2.4.4 en 2.4.5 zijn er tien tabellen die de kolom hebben `additional_data`.

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
