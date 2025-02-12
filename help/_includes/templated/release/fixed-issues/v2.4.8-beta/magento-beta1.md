---
source-git-commit: b3059a262fe6144bca47fc9fb1b4d201b38af3ba
workflow-type: tm+mt
source-wordcount: '14735'
ht-degree: 0%

---
# Magento Open Source-releaseopmerkingen (v2.4.8-bèta1)

## Hooglichten in v2.4.8-bèta1

De volgende 49 markeringen zijn van toepassing op de Magento Open Source 2.4.8-release.

### Kader

* _AC-10721_: Bevorder de ligging/de gebiedsdelen van de Samensteller van het vliegsysteem die aan recentste versie worden bevorderd
   * _Bevestig nota_: Bevorder de 2.x liga/de gebiedsdelen van de Composer van het vluchtsysteem aan recentste versie 3.x
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11495_: 2.4.8-bèta1 de Verbetering van de Componenten van het Platform
* _AC-11673_: Onderzoek php-amqplib/php-amqplib recentste versies
   * _nota van de Reparatie_: Bijgewerkt de recentste versie php-amqplib/php-amqplib:^3.x
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11723_: Refactoring van het kader van de Test van de Integratie voor phpunit 10 verenigbaarheid - IntegrationTest.php niet gevonden
   * _Bevestig nota_: PHPUnit 9 wordt bevorderd aan PHPUnit 10 met de het kaderveranderingen van de Test van de Integratie en WebAPI van Adobe Commerce. PHPUnit 10-wijzigingen zijn compatibel met oudere versies.
   * _GitHub codebijdrage_: &lt;https://github.com/magento/magento2/ (Intern, Unmerge)>
* _AC-11813_: WebApi het kader van de Test voor phpunit 10 verenigbaarheid - Kwestie met de connectiviteit RabbitMQ met SOAP en B2B modules
   * _Bevestig nota_: PHPUnit 9 wordt bevorderd aan PHPUnit 10 met de het kaderveranderingen van de Test van de Integratie en WebAPI van Adobe Commerce. PHPUnit 10-wijzigingen zijn compatibel met oudere versies.
   * _GitHub codebijdrage_: &lt;https://github.com/magento/magento2/ (Intern, Unmerge)>
* _AC-11816_: Voeg verenigbaarheid met MySQL 8.4 LTS toe
* _AC-11911_: jQuery/fileuploader css schoonmaakbeurt na migratie aan uppy bibliotheek
   * _Nota van de Oplossing_: Verwijderd jQuery/fileUploader bibliotheek omdat het aan de bibliotheek van het Uppy is gemigreerd
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_: Voeg verenigbaarheid met MySQL 8.4 LTS voor Magento CE toe
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12014_: Markeer elasticsearch 8 module als afgekeurd
* _AC-12015_: De omslag ExtJs schoont na migratie aan de bibliotheek jsTree
   * _nota van de Reparatie_: Verwijderd omslag TextJs aangezien de verwante functionaliteit is gemigreerd aan jsTree
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-12022_: Van de verbetering monolog/monoloog systeemgebiedsdeel aan de recentste belangrijkste versie
   * _nota van de Reparatie_: Het systeem is bijgewerkt om de recentste belangrijkste versie van de &quot;monolog/monolog:^3.x&quot;bibliotheek te gebruiken, die verenigbaarheid en betere prestaties verzekeren. Eerder gebruikte het systeem een verouderde versie van de &quot;monolog/monolog&quot; bibliotheek die tot mogelijke problemen en beperkingen had kunnen leiden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12023_: Bevorder wikimedia/less.php gebiedsdeel aan de recentste belangrijkste versie
   * _nota van de Reparatie_: Het systeem is bijgewerkt om recentste belangrijke versie 5.x van de &quot;wikimedia/less.php&quot;bibliotheek te gebruiken, die verenigbaarheid en bijgewerkte functionaliteit verzekeren. Eerder gebruikte het systeem een verouderde versie van de bibliotheek die tot veiligheidskwesties kon hebben geleid.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12024_: Bevorder jquery/bevestig bibliotheekgebiedsdeel aan de recentste minder belangrijke versie
   * _Bevestig nota_: Bevorder jquery/bevestig bibliotheekgebiedsdeel aan recentste minder belangrijke versie 1.20.0
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12025_: Het systeemgebiedsdeel van de verbetering moment.js aan de recentste minder belangrijke versie
   * _Bevestig nota_: De systeemgebiedsdeel van de verbetering moment.js aan recentste minder belangrijke versie 2.30.1
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12032_: Voeg verenigbaarheid met MySQL 8.4 LTS voor EE toe
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12034_: Voeg verenigbaarheid met MySQL 8.4 LTS voor B2B toe
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12074_: Voeg verenigbaarheid met MySQL 8.4 LTS voor bundeluitbreidingen toe
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12085_: voeg verenigbaarheid met MariaDB 11.4 LTS voor Ce toe
   * _Bevestig nota_: Toegevoegde MariaDB 11.4 steun met Adobe Commerce en uitbreidingen
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12165_: De Optimalisering van de abonnees - PhpUnit10
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_: De verbindingspogingen van de steun voor Redis zitting en compatibel met colinmolenhour/php-redis-session-abstract v2.0.0
   * _nota van de Reparatie_: Bijgewerkte recentste versie van colinmolenhour/php-redis-session-abstract v2.0.0 compatibel met de handel van Adobe
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12268_: De gebiedsdelen van de Composer van de verbetering liga/van het vluchtsysteem aan recentste versie
   * _Bevestig nota_: Bevorder de 2.x liga/de gebiedsdelen van de Composer van het vluchtsysteem aan recentste versie 3.x
* _AC-12576_: Onderzoek de mislukkingen van de automatiseringstests met MySQL 8.4 LTS
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_: voeg verenigbaarheid met MariaDB 11.4 LTS voor EE toe
   * _Bevestig nota_: Toegevoegde MariaDB 11.4 steun met Adobe Commerce en uitbreidingen
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12693_: Onderzoek op het hulpmiddel van de Migratie van Gegevens (DMT) met MySQL 8.4 LTS
* _AC-12715_: De gebiedsdelen van de composer van de update laminas bevorderen aan recentste versie
   * _nota van de Reparatie_: Het systeem steunt nu de recentste versies van laminas composer gebiedsdelen:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
zorgen voor compatibiliteit en up-to-date functionaliteit. Eerder, kon het bijwerken aan de recentste versies van deze gebiedsdelen achterwaartse onverenigbaarheidskwesties en testmislukkingen veroorzaken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12752_: voeg verenigbaarheid met MariaDB 11.4 LTS voor het hulpmiddel van de Migratie van Gegevens toe
   * _Bevestig nota_: Toegevoegde MariaDB 11.4 steun met Adobe Commerce en uitbreidingen
* _AC-12823_: Onderzoek de mislukking van de eenheidstest toe te schrijven aan phpunit flardupdate tijdens componentenverbetering
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12897_: SVC en EAT hulpmiddelverenigbaarheid met MySQL 8.4
* _AC-12898_: Het hulpmiddelverenigbaarheid van UCT met MySQL 8.4
   * _nota van de Reparatie_: Het Hulpmiddel van de Verenigbaarheid van de Verbetering (UCT) is nu compatibel met MySQL 8.4, die vlotte verrichting en verenigbaarheidscontroles voor instanties verzekeren die op deze versie lopen. Eerder werd het UCT-gereedschap niet getest en gecontroleerd op compatibiliteit met MySQL 8.4.
* _AC-9749_: FPUnit 10 verbetering
   * _Bevestig nota_: Bijgewerkt de punit/punit componentengebiedsdelen aan compatibele versie - &quot;punit/phpunit&quot;:&quot;10.x&quot;

### Installeren en beheren

* _AC-6819_: Plaats indexen aan &quot;Update door Programma&quot;door gebrek

### Volgorde

* _ACP2E-2709_: [ De Klant van het Verzoek van de Eigenschap ] stelt voor dat de Knoop van de Commentaar op de pagina van de Details van de Orde voorleggen verwarrend is en zou in iets anders moeten worden veranderd
   * _nota van de Reparatie_: Om de verwarring te minimaliseren, veranderde het &quot;Submit Comment&quot;knoopetiket in &quot;Update&quot;in de orde detailpagina.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/488c1034>

### Overige

* _AC-11420_: De vastgestelde indexen verschijnen in Klaar statusgebrek wanneer de nieuwe versie van Adobe Commerce wordt geïnstalleerd
   * _nota van de Reparatie_: Na Installatie Magento, moet de Status van Indexer in *Klaar* staat door gebrek zijn.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-11421_: In bestaande installatie van Magento wanneer de module van de derdeindexeermodule installeert plaatste indexen in update door gebrek.
   * _nota van de Reparatie_: Alle nieuwe indexen zijn door gebrek in [ Update door de 3} wijze van het Programma. ] Eerder, was de standaardwijze [ Update op sparen ]. Hetzelfde geldt voor aangepaste indexen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/71432aeb>
* _AC-12480_: Elasticsearch 7 en 8 opties zouden met Afgekeurd in config Admin moeten komen.
   * _nota van de Reparatie_: De optie van Elasticsearch 8 in de optie van Configuratie Admin zal met Vervangen tekst tonen om gebruikers te informeren dat Elasticsearch 8 niet meer geadviseerde optie aan gebruik is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12481_: Voeg tekstnota toe wanneer de optie van Elasticsearch in Configuratie Admin wordt geselecteerd
   * _nota van de Reparatie_: Een tekstnota wordt toegevoegd om de admingebruikers van Adobe Commerce te laten weten dat elasticsearch niet meer door Adobe wordt gesteund en afgekeurd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12870_: SVC en EAT hulpmiddelverenigbaarheid met MariaDB 11.4
   * _Bevestig nota_: SVC en EAT hulpmiddelverenigbaarheid met MariaDB 11.4
* _AC-12876_: Het hulpmiddelverenigbaarheid van UCT met MariaDB 11.4
* _LYNX-374_: De Bevestiging van e-mail van het document via GraphQL
* _LYNX-376_: Document dat configuraties voor reCAPTCHA in GraphQL krijgt
* _LYNX-409_: De Optimalisaties van de Vraag van OB voor de Mutatie van de Punten van de Kaart van de Update

### Beveiliging

* _AC-11041_: De Verbeteringen van de veiligheid voor 2.4.8-bèta1 van de versie van juni 2024
* _AC-11864_: De Verbeteringen van de veiligheid voor 2.4.8-bèta1 van de versie van Augustus 2024
* _AC-12346_: De Verbeteringen van de veiligheid voor 2.4.8-bèta1 van de versie van Oktober 2024
* _AC-12691_: [ 2.4.8-bèta1 ] de update REST API van de Klant werkt niet
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4102373>, <https://github.com/magento/magento2/commit/a4102373>

### UI Framework

* _AC-12726_: [ 2.4.8-bèta1 ] TinyMCE 5 migratie aan TinyMCE 7
   * _Nota van de Reparatie_: Gegigreerde TinyMCE 5 aan TinyMCE 7.3.0 om een gesteunde versie voor Adobe Commerce te zijn, vroeger gebruikte het systeem 5.10.2 die verouderd was en veiligheidskwetsbaarheid rapporteerde
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_: [ 2.4.8-bèta1 ] TinyMCE 5 migratie aan TinyMCE 7 de Bouwer van de Pagina
   * _Nota van de Reparatie_: Gegigreerde TinyMCE 5 aan TinyMCE 7.3.0 om een gesteunde versie voor Adobe Commerce te zijn, vroeger gebruikte het systeem 5.10.2 die verouderd was en veiligheidskwetsbaarheid rapporteerde
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_: [ 2.4.8-bèta1 ] TinyMCE 5 migratie aan TinyMCE 7 - Magento2-infra - verboden woorden
   * _Nota van de Reparatie_: Gegigreerde TinyMCE 5 aan TinyMCE 7.3.0 om een gesteunde versie voor Adobe Commerce te zijn, vroeger gebruikte het systeem 5.10.2 die verouderd was en veiligheidskwetsbaarheid rapporteerde
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_: Vereis.js verbetering aan recentste versie 2.3.7 (veiligheidskwetsbaarheid CVE-2024-38999)
   * _Bevestig nota_: Bijgewerkt require.js aan recentste versie 2.3.7. In vorige versie werd een beveiligingskwetsbaarheid gemeld
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>

## Opgeloste problemen in v2.4.8-bèta1

We hebben 253 problemen opgelost in de Magento Open Source 2.4.8-kerncode. Hieronder wordt een subset van de opgeloste problemen in deze release beschreven.

### API&#39;s

* _AC-10042_: /V1/de transacties REST API keert fout terug wanneer parent_txn_id = txn_id
   * _nota van de Reparatie_: Het systeem behandelt nu correct de ouder en kindconcepttransacties waar identiteitskaart van de oudertransactie het zelfde als transactieidentiteitskaart is, verhinderend een oneindige lijn wanneer het vragen van het /V1/transacties REST API eindpunt. Eerder zou dit scenario resulteren in een fatale fout als de maximale uitvoeringstijd wordt overschreden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [ Grafiek ] de kwestie van het Type in 2.4.7
   * _nota van de Reparatie_: Het systeem behandelt nu correct geheelwaarden in de functie GetCustomSelectedOptionAttributes wanneer het uitvoeren van een vraag van GraphQL, die om het even welke op type betrekking hebbende fouten verhinderen. Eerder resulteerde het lanceren van een vraag van GraphQL die GetCustomSelectedOptionAttributes met een geheelargument gebruikte in een typefout.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38662>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38663>
* _ACP2E-2927_: [ REST API ]: De Standaardwaarde van het gebruik in archiefmening blijft niet gecontroleerd na het toevoegen van configuraties voor een configureerbaar product
   * _nota van de Reparatie_: De kwestie is opgelost door correcte gegevensbestandingangen voor de klantgerichte opties voor een non-default opslag te verzekeren. Het selectievakje voor de aangepaste opslag in de sectie &quot;Beheer > Catalogus > Product Bewerken > Aanpasbare opties&quot; is eerder uitgeschakeld omdat de database niet correct is, zelfs als de titel van de optie voor de aangepaste opslag gelijk bleef aan de standaardwinkel.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-2969_: REST API kan verzoeken met schuine streep (/) in SKU wanneer het gebruiken van Oauth1 niet indienen
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie, kon u geen succesvolle API vraag voor een product maken dat &quot;/&quot;in zijn SKU had. Nu, kunt u een succesvolle API uitgeven krijgt verzoek om productdetails alhoewel zijn SKU een voorwaartse schuine streep in het heeft.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3079_: Het adresupdate van de klant die ontbreekt wanneer het bijwerken door REST API als &quot;validateDefaultAddress&quot;toegelaten
   * _nota van de Reparatie_: Het API eindpunt functioneert nu zoals bedoeld nadat het probleem met de sleutel van identiteitskaart die van de API lading mist is opgelost.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3091_: [ Wolk ] Creërend de Duplicate de klantengroep van de websitegroep in de Prijzen Api van de Rij.
   * _Bevestig nota_: Nu de Rest Api van de Prijs van de Reeks staat niet toe om de Dubbele groep van de de prijsklant van de websitegroep tot stand te brengen.
Eerder was het mogelijk om de prijsgroep voor de websitegroep Dupliceren te maken in Tier Prices Api die de validatie in Admin tijdens het opslaan van het product niet zou doorstaan.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3130_: Kan orde geen commentaar met status via REST API toevoegen
   * _nota van de Reparatie_: De kwestie is opgelost door de verandering in ordestatus toe te staan als het van de huidige slechts staat is. Eerder voldeed het niet aan de ordestatus en voorkwam het wijzigingen in een orderstatus, zelfs niet als deze van dezelfde status afkomstig was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93d50f8d>

### Account

* _AC-10782_: Het adresvorm van de klant staat willekeurige code op de naamgebieden toe
   * _nota van de Reparatie_: Het systeem bevestigt nu de input in de gebieden Voornaam en Achternaam in de vorm van het klantenadres, die het gebruik van willekeurige code verhindert. Eerder stond het systeem het gebruik van willekeurige code in deze gebieden toe zonder een fout te werpen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38331>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38345>
* _AC-10990_: mijn rekening voegt adresneerstorting toe op sparen
   * _nota van de Reparatie_: Het systeem bewaart nu correct klantenadressen zelfs wanneer het gebiedgebied niet wordt getoond, verhinderend een neerstorting tijdens het sparen proces. Als u eerder een adres probeert toe te voegen of te bewerken zonder veld voor een weergegeven gebied, treedt er een uitzonderingsfout op.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38406>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38407>
* _AC-11919_: Admin: De Knopen van de Acties van de pagina drijvende linkerzijde in plaats van recht
   * _nota van de Reparatie_: Het systeem richt nu correct de Knopen van de Acties van de Pagina aan de rechterkant van de kleverige kopbal in het admin paneel, dat de professionele blik en het gevoel verbetert. Eerder zweven deze knoppen onjuist naar de linkerkant van de kleverige koptekst.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38701>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: dev :di: infofout in magento 2.4.7
   * _nota van de Reparatie_: Het systeem toont nu correct constructorparameters wanneer het uitvoeren van het dev :di: info bevel, verhinderend om het even welke fouten voor te komen. Eerder resulteerde het uitvoeren van deze opdracht in een fout als gevolg van een niet-overeenkomend type in het argument.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38740>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-6071_: De klant wordt het programma geopend maar het tonen van 404 fout in front-end.
   * _nota van de Reparatie_: De storefront klantendashboardpagina laadt nu zoals verwacht wanneer een klant het programma opent. Eerder konden klanten zich aanmelden, maar op deze pagina werd een fout van 404 weergegeven. [ GitHub-35838 ](https://github.com/magento/magento2/issues/35838)
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/35838>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: Kan de attributeninformatie van de Klant niet opslaan in Admin geeft klantensectie uit;
   * _nota van de Oplossing_: De opslag identiteitskaart van de klant wordt nu behoorlijk uitgevoerd per websitewerkingsgebied voor de beheerder klant geeft vorm uit.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/488c1034>

### Gebruikersinterface van beheerder

* _AC-11588_: De bevestiging van gegevens is succes en de knoop van de Invoer is aanwezig tijdens de producten van de Invoer met het gedrag van de Vervangen
   * _nota van de Reparatie_: Het systeem bevestigt nu correct gegevens en verbergt &quot;de knoop van de Invoer&quot;tijdens het proces van de productinvoer met &quot;vervangt&quot;gedrag, dat om het even welke onbedoelde gegevensvervanging verhindert. Eerder heeft het systeem de gegevens onjuist gevalideerd en de knop Importeren weergegeven. Dit leidt tot mogelijke inconsistenties in de gegevens.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [ Bug ] Magento 2.4.7 staat geen productfoto&#39;s met de uitbreiding van het hoofdletterdossier toe.
   * _nota van de Reparatie_: Het systeem keurt nu productbeeld toe uploadt met de uitbreidingen van het hoofdletterdossier, die een vlot proces verzekeren van de productverwezenlijking. Eerder werd het uploaden van afbeeldingen met bestandsextensies voor hoofdletters geweigerd, waardoor gebruikers gedwongen werden de bestandsextensie te wijzigen in kleine letters.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38831>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8f87c25>
* _wisselstroom-6975_: [ Uitgave ] plaats standaardindexeermodus aan &quot;programma&quot;
   * _nota van de Reparatie_: Alle nieuwe indexeerders zijn door gebrek op **[!UICONTROL Update by Schedule]** wijze.  Eerder was de standaardmodus **[!UICONTROL Update on Save]** . Dit heeft geen invloed op bestaande indexen. [ GitHub-36419 ](https://github.com/magento/magento2/issues/36419)
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36419>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0b410856>
* _wisselstroom-7700_: [ ] het veranderingslijsten van de Daling van de indexator op mening unsubscribe
   * _nota van de Reparatie_: Het systeem verwijdert nu automatisch ongebruikte veranderingslijsten wanneer een index van &quot;update op programma&quot;aan &quot;update op sparen&quot;wordt geschakeld, die de index als ongeldig markeren om ervoor te zorgen geen ingangen worden gemist. Als een index eerder werd overgeschakeld op &#39;bijwerken bij opslaan&#39;, blijven wijzigingstabellen die niet worden gebruikt in het systeem behouden en worden alle gewijzigde indexen &#39;geldig&#39; gemarkeerd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/29789>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/25859>
* _AC-9843_: i18n:verzamelen-zinnen breken de integriteit van vertalingen
   * _nota van de Reparatie_: Het `bin/magento i18n:collect-phrases -o` bevel verzamelt nu correct en voegt nieuwe uitdrukkingen van JavaScript en .phtml- dossiers toe, ervoor zorgend dat de vertalingen nauwkeurig in het vertaaldossier worden weerspiegeld. Eerder was het systeem er niet in geslaagd om meerregelige vertaalzinnen uit JavaScript-bestanden en woordgroepen uit .phtml-bestanden op te nemen in het vertaalbestand, wat leidde tot onvolledige of onjuiste vertalingen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2787_: Apostrof in de naam van de opslagmening wordt vervangen door &quot;
   * _Bevestig nota_: De filters van de de opslagmening van het net tonen nu behoorlijk apostroffen
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38395>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: Het uploaden van het favicon ontbreekt om .ico- dossiers te bevestigen
   * _nota van de Reparatie_: De fout van de dossierbevestiging is bijgewerkt aan &quot;Ontbroken Bevestiging van het Dossier. Controleer de instellingen voor afbeeldingsverwerking in de winkelconfiguratie.&quot; Eerder was dit gewoon &quot;Bestandsvalidatie mislukt.&quot;
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: De galerie in PageBuilder toont oude beeldduimnagel in plaats van onlangs geupload beeld
   * _nota van de Reparatie_: Regenereer beeldvoorproeven voor beelden die met de zelfde naam door media galerij in de inhoud van de paginabouwer worden geschrapt en opnieuw worden geupload.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/magento2-page-builder/commit/60140cd2>
* _ACP2E-2978_: Het bewaren van product door admin gebruiker met verschillende rolwerkingsgebied beschrijft/schrapt bestaande Verwante productinformatie in het product
   * _nota van de Reparatie_: Eerder, vóór de moeilijke situatie, werden de verwante producten teruggesteld en leeg geworden wanneer de secundaire admin gebruiker op sparen knoop klikte zonder in verwant product te veranderen. Na deze correctie klikt de secundaire gebruiker op de knop Opslaan en wordt het product niet opnieuw ingesteld en opgeslagen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: Onbekwaam om meer dan 200 orden uit te voeren
   * _nota van de Reparatie_: De servergrenzen voor de verzoekgrootte van eerder voorgelegde geselecteerde IDs zijn genegeerd door het verzoek van HTTP van GET in POST te veranderen om de kwestie te bevestigen. Eerder werd het probleem aangetroffen vanwege serverbeperkingen voor de grootte van GET-verzoeken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: Het bericht van de de paginasalidering van de uitcheckpagina onjuist.
   * _nota van de Reparatie_: Als om het even welk vereist gebied leeg, zoals &quot;adres wordt verlaten,&quot;zal de server-zijbevestiging niet het bericht tonen. De clientvalidatie zorgt ervoor dat het vereiste foutbericht wordt weergegeven met de tekst &quot;Dit is een verplicht veld&quot;. Eerder werd het bericht &quot;adres is required&quot; weergegeven als een vereist veld leeg was, naast het validatiebericht aan de clientzijde.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3125_: De kwestie van het het terugstellensjabloon van het wachtwoord met gebruiker Admin
   * _nota van de Reparatie_: De kwestie is opgelost door de correcte sleutel te gebruiken, die nu de admin gebruikersbenaming in het e-mailmalplaatje omvat en behoorlijk het onderwerp voltooit. Eerder was het probleem het gevolg van een verouderde sleutel die werd gebruikt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3149_: De dubbele slashes in klantensegment URL
   * _nota van de Reparatie_: De dubbele schuine strepen verschijnen niet in URL wanneer de &quot;Filter van het Terugstellen&quot;in het net wordt geklikt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3171_: CZV is niet beschikbaar voor toegestane specifieke landen
   * _Nota van de Moeilijke situatie_: Nu Geld op levering is beschikbaar voor toegestane specifieke landen wanneer het wordt vereist en   AC-3216 werkt zoals verwacht.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3178_: Kan de Status van de Orde van de Douane niet bijwerken Creeerde
   * _Bevestig nota_: &quot;
We kunnen nu aangepaste orderstatussen bijwerken, terwijl eerder de status alleen gewijzigd kon worden als de huidige status &#39;verwerkings&#39; of &#39;fraude&#39; was.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38659>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/8459b17d>

### Beheerdersinterface, prestaties

* _ACP2E-3169_: Na update aan 2.4.5-p8 komen 500 fouten voor wanneer het creëren van orde van admin
   * _nota van de Reparatie_: Eerder, toen het toelaten van de minificatie van HTML, kon een orde van admin niet worden geplaatst. Nu HTML is ingeschakeld, kan de bestelling van de beheerder met succes worden geplaatst.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>

### Admin-gebruikersinterface, verzenden

* _ACP2E-2519_: De telling van de couponcode werkt niet in bij   De kolom &quot;Gebruikte tijd&quot; in het tabblad Codes voor coupons beheren als een bestelling wordt geplaatst met meerdere verzendingen.
   * _nota van de Reparatie_: Eerder, toen een orde met multi-verschepen werd geplaatst, werkte de telling van de waardeboncode niet in de &quot;Gebruikte Tijd&quot;kolom op het Manage lusje van de Codes van de Coupon bij. Nu wordt het juiste aantal weergegeven in zowel de &quot;Gebruikte tijd&quot; die de gewenste waarden weerspiegelt bij verzending via meerdere kanalen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/4745100c>

### Analyse/rapportage

* _ACP2E-2570_: Het Rapport van de vooruitgang werkt niet
   * _nota van de Reparatie_: Het systeem steunt nu de generatie van de Geavanceerde Gegevensdossiers van de Rapportering voor extra grote datasets door rapporten in partijen van 10.000 te laden en te schrijven. Eerder, kon de Geavanceerde module van de Rapportering gegevensdossiers voor extra grote datasets niet produceren, veroorzakend &quot;MySQL server is weggegaan&quot;fouten tijdens de uitvoering van de analytics_collect_data bouwbaan.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Admin bestelde de kwestie van het de datumbereik van het Rapport van Producten.
   * _nota van de Reparatie_: De gebruiker zal om het even welke datum van het bevolen productrapport kunnen selecteren. Eerder, na een lijst verfrist zich, zal het selecteren van &quot;VAN&quot;datum &quot;aan&quot;datum terugstellen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Onjuiste curl kopballen die nieuwe relic :create: opstellen-teller maken die niet werkt
   * _nota van de Reparatie_: Het systeem formatteert nu correct curl kopballen, toestaand het nieuwe betrouwbare :create: op:stellen-teller bevel om een plaatsingsteller in New Relic met succes tot stand te brengen. Eerder, verhinderden de onjuiste curl kopballen de verwezenlijking van een plaatsingsteller in New Relic.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37641>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>

### Analyse/rapportage, B2B

* _ACP2E-2300_: B2B - sitemap omvat producten/categorieën niet die aan Gedeelde Catalogus worden toegewezen
   * _nota van de Reparatie_: Beperk de sitemap geproduceerde categorieën en producten tot de categorieën en het product die slechts aan de openbare gedeelde catalogus en/of de de toestemmingsopstelling van de cataloguscategorie worden toegewezen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analyse/rapportage, cloud

* _ACP2E-3067_: Magento gooit de meeste New Relic cron transacties weg #34108
   * _nota van de Reparatie_: AC rapporteert correct gezamenlijke baan verwante transacties aan NewRelic. Voorheen zouden sommige aan een uitsnijdtaak gerelateerde transacties als &quot;OtherTransaction/Action/unknown&quot; in Northern Rock worden weergegeven
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>

### B2B

* _ACP2E-3044_: De onnodige grenzen op de Mijn sectie van Orden
   * _nota van de Reparatie_: Eerder werd een extra container (ordeverwijzingen) gecreeerd die extra CSS klassen toepaste, die onnodige grenslijnen veroorzaakte die onder het ordeaantal binnen de Mijn sectie van Orden verschijnen, die nu niet zichtbaar is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/9af794a4>

### B2B, Kader

* _AC-9607_: Het filtreren van het Net van het Bedrijf &amp; toen het Poging van de Uitvoer van het Net CSV zal de Uitzondering van de Kwijting &amp; van de Borg ontbreken
   * _nota van de Reparatie_: Het systeem staat nu succesvolle uitvoer CSV van de het netgegevens van Bedrijven in het admin paneel toe, zelfs wanneer de filters zoals &quot;Uitstaand Saldo&quot;en &quot;Type van Bedrijf&quot;worden toegepast. Eerder, zou het toepassen van bepaalde filters en het proberen om de netgegevens uit te voeren in een mislukking resulteren en een uitzondering die wordt geworpen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/44cef3a9>

### Braintree

* _BUNDLE-3367_: Betaal via LPM
   * _nota van de Reparatie_: Het systeem geeft nu correct Lokale BetalingsMethoden (LPM) op aanvankelijke lading terug, zelfs wanneer de het verschepen en het factureren van een aangemelde klant adressen niet aanpassen, die een vlot controleproces verzekeren. Eerder, zou een wanverhouding tussen het verschepen en het facturerings adres van een klant LPM verhinderen teruggeven, veroorzakend potentiële verstoringen tijdens het afrekenen.
   * _GitHub codebijdrage_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3368_: Configureerbaar met Virtueel als Product van het Kind
   * _nota van de Reparatie_: Het systeem staat nu uitdrukkelijke betalingsmethodes voor configureerbare producten toe die een virtueel kindproduct hebben, die een vlot afrekenen proces verzekeren. Eerder waren expresbetalingsmethoden niet beschikbaar toen een configureerbaar product met een virtueel onderliggend product aan de winkelwagentje werd toegevoegd.
   * _GitHub codebijdrage_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3369_: De mislukte fout van de Verificatie CVV
   * _GitHub codebijdrage_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3370_: Het vaulting via de Kwesties 247 van het rekeningsgebied
   * _Bevestig nota_: Het systeem staat nu klanten toe om nieuwe kaart of Paypal rekeningsinformatie over veelvoudige websites op te slaan zonder vergunningsfouten te ontmoeten. Voorheen konden klanten geen nieuwe betalingsmethoden opslaan op verschillende websites en kregen ze een foutbericht over hun autorisatie te zien.
   * _GitHub codebijdrage_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3371_: Schip aan een adres van een verschillend land
   * _nota van de Reparatie_: Het systeem staat nu transacties toe om zonder fouten worden verwerkt wanneer het verschepen naar een adres van een verschillend land, die een vlot afhandelingsproces verzekeren. Eerder, zou het proberen om aan een adres van een verschillend land te verzenden in consolefouten, ondanks geen zichtbare fouten op de frontend resulteren.
   * _GitHub codebijdrage_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3372_: Kredietkaart - de functie van de Onderbreking
   * _Nota van de Oplossing_: Het systeem behandelt nu correct de opruiming van de componenten van Braintree PayPal wanneer een klant terug van de betalingspagina naar de het verschepen pagina navigeert, die om het even welke fouten verhinderen en ervoor zorgen dat de Uitdrukkelijke knopen van PayPal correct teruggeven. Eerder was het navigeren van de verzendpagina vanaf de betalingspagina soms een fout bij het afbreken van de Braintree PayPal-componenten.
   * _GitHub codebijdrage_: <https://github.com/magento/ext-braintree/pull/204>
* _BUNDLE-3373_: Verzendcallback voor Uitdrukkelijke PayPal
   * _nota van de Reparatie_: Het systeem toont nu correct beschikbare verschepende methodes in Uitdrukkelijke PayPal, toestaand klanten om hun aangewezen het verschepen methode te selecteren alvorens aan de overzichtspagina of hun transactie te werk te gaan. Eerder waren er geen verzendmethoden beschikbaar om uit te kiezen in het PayPal Express-modaal, waardoor klanten een verzendmethode moesten selecteren op een aparte controlepagina voordat ze hun transactie konden voltooien.
   * _GitHub codebijdrage_: <https://github.com/magento/ext-braintree/pull/204>

### Winkelwagentje en Afhandeling

* _AC-10660_: De uitzondering wordt niet behoorlijk behandeld terwijl het toevoegen van een product aan kar in de vergelijkingsproductpagina
   * _nota van de Reparatie_: Het systeem behandelt nu behoorlijk uitzonderingen wanneer het toevoegen van een product aan de kar van de vergelijkingsproductpagina, tonend een bericht van de berichtmanager in het controlemechanisme. Eerder zou een uitzondering ertoe leiden dat een JSON-gecodeerde pagina wordt geretourneerd in plaats van correct te worden afgevangen en afgehandeld.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38200>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag verzendt geen transactieprijzen en totalen.
   * _nota van de Reparatie_: Het systeem verzendt nu correct transactieprijzen en totalen naar de Markering van Google wanneer GTag wordt toegelaten, die nauwkeurige het volgen van elektronische handelgegevens verzekeren. Eerder werd de valuta onjuist verzonden als onderdeel van de &quot;alle&quot; bestellingen, in plaats van te worden gekoppeld aan de afzonderlijke bestelling.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37348>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [ Uitgave ] [ Afhandeling ] onderdrukt richtlijnen die in ontbroken betalings e-mailmalplaatje worden bijgewerkt
   * _nota van de Reparatie_: Het systeem weglaat nu correct het verschepen adres en het verschepen methode van het ontbroken betalings e-mailmalplaatje voor virtuele producten, die slechts relevante informatie verzekeren is inbegrepen in e-mail. Eerder bevatte het niet-betaalde e-mailbericht voor virtuele producten het verzendadres en de verzendmethode onjuist.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32781>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32511>
* _AC-11876_: [ de regressie van de Regels van de Verkoop van de Uitgave ] in 2.4.7
   * _nota van de Reparatie_: Het systeem bevestigt nu correct verkoopregels, die de toepassing van een couponcode aan een karretje verhinderen wanneer de productvoorwaarde geen productnaam aanpast. Voorheen kon een verkoopregel worden toegepast en een korting op het verzendbedrag worden gegeven, zelfs als de productvoorwaarde niet overeenkomt met een productnaam.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38671>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0574ac23>
* _wisselstroom-11993_: [ geef ] de ladingsblokken de verschepende methodes na postcode wordt veranderd, de regels van de de rentesubsidie bevestiging
   * _nota van de Reparatie_: Het systeem behandelt nu correct douaneverschepende methodes zonder de bevestigingsregels van het verschepen tarief, die ervoor zorgen dat de lader niet de verschepende methodes blokkeert nadat postcode in het verschepende adres tijdens controle wordt veranderd. Als de postcode in het verzendadres tijdens de afhandeling werd gewijzigd, zou de lader eerder de verzendmethoden blokkeren en niet verdwijnen als er aangepaste verzendmethoden werden gebruikt zonder de validatieregels voor de verzendkosten.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38742>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: De eigenschap van de code van de coupon werkt niet behoorlijk in de controlepagina op Magento 2.4.7
   * _Nota van de Reparatie_: Het systeem laat nu het de inputgebied van de disconteringscode/coupon op de controlepagina voor virtuele en downloadbare producten toe, toestaand gebruikers om kortingscodes toe te passen zoals verwacht. Eerder was de invoer van de kortingscode/coupon uitgeschakeld en werd de tekst van de knoptitel weergegeven als &quot;coupon annuleren&quot;, zodat gebruikers geen kortingscodes konden toepassen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38826>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-8103_: De Vertaling BTW in adresrenderer
   * _nota van de Reparatie_: Het systeem staat nu voor de vertaling van de tekst &quot;BTW&quot;toe, &quot;T&quot;, &quot;F&quot;in adresrenderers, toelatend gebruikers om deze termijnen aan de specifieke taal van de opslag te vertalen. Eerder waren deze termen niet vertaalbaar, waardoor gebruikers gedwongen werden een tijdelijke oplossing te kiezen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36942>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: De dubbele orden met zelfde Citaat ID tezelfdertijd met weinig tijdverschil
   * _Bevestig nota_: Vaste de kwestie toen de klanten van Adobe Commerce dubbele die orden tegenkwamen met zelfde QuoteID worden geplaatst
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: Persistent die winkelwagentje tijdens checkout wordt ontruimd
   * _nota van de Reparatie_: Na de moeilijke situatie, die de betalingsmethode tijdens controle selecteert terwijl het programma niet het programma wordt geopend beëindigt niet de blijvende zitting.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: De orde voegt niet toegewezen product aan wagentje opnieuw toe
   * _nota van de Reparatie_: Eerder, voor de verschillende opslagproducten kunnen van de andere opslag worden opnieuw in orde gebracht. Nadat deze correctie is toegepast, kan alleen dezelfde store worden gebruikt, kan hetzelfde bereikproduct opnieuw worden geordend wanneer het delen van de klantenaccount is ingeschakeld
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: In admin, wordt het &quot;Winkelende Kart&quot;op linkerkant niet bijgewerkt wanneer het selecteren van de punten en &quot;Beweging aan het Winkelende Kart&quot;van de rechterkant
   * _nota van de Reparatie_: De &quot;Winkelwagentje&quot;op de linkerkant wordt bijgewerkt wanneer het selecteren van de punten en &quot;Beweging aan het winkelwagentje&quot;van de rechterkant in admin kant. Eerder werkte deze functionaliteit niet omdat de getransformeerde winkelwagentjes niet leeg werden tijdens de sessie.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: [ de Regel van de Verkoop van de Wolk ] wordt niet toegepast op eerste orde van Multi die verscheept
   * _nota van de Reparatie_: Na de moeilijke situatie, wordt de korting correct getoond voor elke orde van het zelfde multi-verschepende citaat.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [ de parallelle verzoeken van de de productie van de Wolk ] om het zelfde product aan het resultaat van de Kar toe te voegen in Twee afzonderlijke punten in de steun API
   * _nota van de Reparatie_: Het systeem verwerkt nu correct veelvoudige parallelle verzoeken om het zelfde product aan de kar in één enkel lijnpunt toe te voegen, verhinderend de verwezenlijking van afzonderlijke lijnpunten voor zelfde SKU. Eerder zou het doen van parallelle verzoeken om hetzelfde product via de REST-API aan het winkelwagentje toe te voegen, resulteren in meerdere regelitems voor dezelfde SKU.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_: Het krijgen van Onbekwaam om het koekje te verzenden. Grootte van &#39;afbeeldingsberichten&#39; tijdens het opnieuw ordenen
   * _nota van de Reparatie_: Het opnieuw rangschikkende proces zal niet zijn eigen fouten nu produceren. Het object is afhankelijk van ingebouwde controles van winkelwagentjes.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: Het standaard verschepende adres wordt niet geselecteerd bij controle
   * _nota van de Reparatie_: Het standaard verschepende adres wordt nu geselecteerd gebeurtenis in context van toegelaten adresonderzoek.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [ CLOUD ] grafische addProductsToCart API kwestie met douaneoptie
   * _nota van de Reparatie_: GraphQL voegt toe om correct het zelfde product met verschillende douaneopties te kar
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: De veelvoudige adressen die aan de rekening worden toegevoegd wanneer controle als nieuwe klant
   * _nota van de Reparatie_: Het systeem bewaart nu een nieuw klantenadres slechts eenmaal als de orde om niet kon worden gecreeerd, verhinderend de verwezenlijking van veelvoudige identieke adressen in het geval van de fouten van de orderplaatsing. Eerder, zou het systeem een nieuw adres bewaren telkens als een bestelling plaatsingspoging werd gemaakt, ongeacht of de orde met succes werd gecreeerd of niet.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Het opnieuw ordenen van klantenorde via de vorm van de gastorde resulteert een leeg karretje
   * _nota van de Reparatie_: Eerder, toen het plaatsen van een herschikking door de Orden en de pagina van Keert terug, werd de klant opnieuw gericht aan de login pagina. Nadat deze correctie is toegepast, wordt de geregistreerde klant correct omgeleid naar de pagina Winkelwagentje weergeven wanneer een nieuwe order wordt geplaatst. De stroom werkt het zelfde als gastklanten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: De Gebruiker van Admin met de beperkte Middelen van de Rol kan het Schepen van Kasten niet bekijken
   * _nota van de Reparatie_: Eerder, beperkte admin kon niet het verlaten het winkelwagentje van het admin paneel voor een bijbehorende website zien. Nadat deze correctie is toegepast, kan de beperkte beheerder het verlaten winkelwagentje van het admin paneel zien.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d1f7dc95>

### Afhandeling van winkelwagentje en afhandeling, Afhandeling/Afhandeling van één pagina

* _AC-9386_: [ het Willekeurige gebied van de BUG ] E-mail wordt niet teruggegeven of neemt veel tijd omhoog in de Verzending van de Controle of de pagina van de Betaling verschijnt
   * _Bevestig nota_: Commerce geeft nu het **[!UICONTROL Email]** gebied op de controle verschepen en betalingspagina&#39;s terug zoals verwacht. Eerder was dit veld afwezig of traag gerenderd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/e1babcfd>

### Winkelwagentje en afhandeling, bestelling

* _ACP2E-3097_: Datepicker voor product met veelvoudige Aanpasbare Opties met datumgebieden die niet werken wanneer het plaatsen van orde van admin
   * _nota van de Reparatie_: Het systeem toont nu correct de datumkiezer voor alle datumgebieden wanneer het vormen van een product met veelvoudige klantgerichte datumopties in het proces van de admin ordeverwezenlijking. Eerder werd de datumkiezer alleen weergegeven voor het veld voor de eerste datum, zodat de overige velden geen datumkiezer hadden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>

### Winkelwagentje en afhandeling, verzending

* _AC-12119_: Onmiddellijke aankoop &quot;goedkoopste verschepende&quot;gebroken voor configureerbare producten
   * _nota van de Reparatie_: De Onmiddellijke eigenschap van de Aankoop selecteerde verkeerd de duurdere optie van de Opslag van de Aankoop voor configureerbare producten in plaats van de goedkoopste Vlakke methode van het Tarief. Deze correctie zorgt ervoor dat de juiste verzendmethode wordt gekozen op basis van de werkelijke prijs.&quot;
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38811>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catalogus

* _AC-10910_: De schoonmaakbeurt van cron_planningsgegevensbestandlijst schoont niet bestaande banen
   * _nota van de Reparatie_: Het systeem ontruimt nu automatisch de cron_planning gegevensbestandlijst, verwijderend ingangen voor banen die niet meer in het systeem bestaan. Dit zorgt voor optimale prestaties door een minimaal aantal rijen in de tabel te handhaven. Eerder, werden de ingangen voor banen van inactieve of verwijderde modules niet schoongemaakt, die tot onnodige gegevensaccumulatie in de cron_planninglijst leidden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38217>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: De Prijs van de rij wordt niet geschrapt van Configurable Product
   * _nota van de Reparatie_: Het systeem verwijdert nu correct de rijprijs van een product wanneer het van een eenvoudig product aan een configureerbaar product wordt omgezet, die nauwkeurige prijsvertoning op het front verzekeren. Eerder werd de laagprijs van een configureerbaar product niet verwijderd wanneer een product werd omgezet van een eenvoudig product in een configureerbaar product, wat leidde tot een verschil in de weergegeven prijs.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38390>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: De beschrijving van de categorie WYSIWYG is leeg op niet standaard storeview
   * _nota van de Reparatie_: Het systeem bewaart nu correct en toont de categoriebeschrijving in de redacteur van WYSIWYG wanneer het uitgeven van een categorie op het niveau van de archiefmening. Eerder was de WYSIWYG-editor leeg nadat een categoriebeschrijving op het weergaveniveau van de winkel was opgeslagen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38622>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38623>
* _wisselstroom-12076_: [ Eis ] Reparatie van filterpunt op gelaagde navigatie
   * _nota van de Reparatie_: Het systeem gebruikt nu correct de woorden &quot;punt&quot;en &quot;punten&quot;in het gelaagde punt van de navigatiefilter, die de duidelijkheid en de nauwkeurigheid van de filterbeschrijvingen verbeteren. Eerder werden deze woorden onjuist gebruikt, waardoor gebruikers door de filteropties konden navigeren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38789>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: Datum en het Formaat van de Tijd voor de Optie van de Douane het Werken van de Optie van de Douane niet
   * _nota van de Reparatie_: Het systeem past nu correct het gevormde datumformaat op de opties van de productdouane van typeDatum toe, die ervoor zorgen dat het datumformaat correct op het front-end wordt getoond. Eerder waren wijzigingen in de configuratie van de datumnotatie niet van toepassing op de front-end voor aangepaste productopties van het type Date.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32990>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38925>
* _AC-6738_: Ontbrekende unieke sleutel op eav_attribute_option_value lijst
   * _nota van de Reparatie_: Het systeem omvat nu een unieke sleutel op de &quot;option_id&quot;en &quot;store_id&quot;kolommen in de &quot;eav_attribute_option_value&quot;lijst, die de mogelijkheid van een optie verhinderen die veelvoudige waarden voor de zelfde opslagmening hebben. Eerder, kon de gebrekkige code in een optie resulteren die veelvoudige waarden voor de zelfde opslagmening heeft, die kwesties veroorzaakt wanneer het uitgeven van producten of attributen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/24718>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [ de zichtbaarheidsklasse van het Gebruik van de kwestie ] voor de indexeerder van het categorieproduct, in plaats van geharde waarden
   * _nota van de Reparatie_: Het systeem gebruikt nu de zichtbaarheidsklasse voor de indexator van het categorieproduct in plaats van geharde waarden, verbeterend modulariteit. Eerder werden in de productindex van de categorie hardgecodeerde waarden gebruikt, waardoor de flexibiliteit en het aanpassingsvermogen werden beperkt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37200>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: De code van de Valuta verandert niet in Nieuwe product widget
   * _nota van de Reparatie_: Het systeem werkt nu correct de muntcode in Nieuwe widget van het Product bij wanneer de munt in het front-end wordt veranderd, die consistentie in muntvertoning over de plaats verzekeren. Eerder had het wijzigen van de valuta aan de voorzijde geen invloed op de valutacode die in de widget Nieuw product werd weergegeven.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37898>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: De regelmatige Prijs toont niet op PLP voor Configureerbaar Product
   * _nota van de Reparatie_: De regelmatige prijs wordt nu getoond op de pagina&#39;s van de productlijst voor configureerbare producten die kindproducten met speciale prijs hebben.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: De informatie van de voorraad die niet recht op het Visuele Net van de Verkoop toont
   * _nota van de Reparatie_: De voorraad wordt nu getoond volgens geselecteerde opslag.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: De inhoud van widget werkt niet op cms pagina bij
   * _nota van de Reparatie_: Het systeem werkt nu de widgetinhoud op een pagina van CMS bij wanneer een product als nieuw en bewaard wordt geplaatst, ervoor zorgend dat de pagina de bijgewerkte productinzameling toont. Eerder werd de pagina niet bijgewerkt om het nieuwe product weer te geven vanwege een onjuiste cache-id voor de widget in de cache.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_: De kwesties die geavanceerde tarifering op bundelproducten besparen
   * _nota van de Reparatie_: Bundel productbesparende prestatiesverbetering.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [ het proces van de re-index van het op-Premise ] is inefficiënt wanneer het creëren van de Regels van de Prijs van de Catalogus
   * _nota van de Reparatie_: Nu het bewaren van de regel van de catalogusprijs zal geen indexen ongeldig maken, in plaats daarvan zal het beïnvloede slechts producten opnieuw indexeren
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_: Het bijwerken tijd van Datum en het type van Tijd productattributen via de invoer CSV
   * _nota van de Reparatie_: Nu datetime zullen de attributen tijd deel in uitgevoerde gegevens hebben. Het zal ook mogelijk zijn de tijd voor dergelijke kenmerken bij te werken met behulp van import. Ook als &quot;Fields Enclosure&quot; is ingeschakeld, worden kenmerkwaarden in de kolom &quot;additional_attributes&quot; tussen dubbele aanhalingstekens ingesloten.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38306>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_: Geen aangewezen foutenmelding wanneer website identiteitskaart in het verzoek verkeerd is
   * _nota van de Reparatie_: Nu werd het aangewezen foutenmelding toegevoegd aan vertoning wanneer website identiteitskaart in het verzoek verkeerd is. Eerder was er geen validatie toen de website-id in het verzoek verkeerd was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_: Het beeld van het product wordt verloren na het schrappen van een bestaande Geplande Update die niet het beeld beïnvloedt
   * _nota van de Reparatie_: De beelden van het product worden niet verwijderd terwijl het schrappen van het opvoeren update.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [ de Verkeerde prijs van het bundelproduct van de Wolk ] wanneer gebruikt met rijprijzen
   * _Nota van de Moeilijke situatie_: Eerder wanneer het berekenen van bepaalde percentagekortingen die omhoog tot 2 decimale punten worden afgerond zullen verschillende definitieve prijzen voor de kart en de pagina van de productlijst/productdetails pagina produceren. Nadat deze correctie is toegepast, is de uiteindelijke prijs voor het bundelproduct gelijk aan die op de pagina met productdetails, de pagina met productaanbiedingen en de pagina met mini-winkelwagentjes.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38091>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: De Regel van de Bevorderingen van de catalogus het werken niet met quantity_and_stock_status attributen
   * _nota van de Reparatie_: Het attribuut kwantiteit_and_stock_status zal nu door de regel van de catalogusbevordering worden in aanmerking genomen, die niet eerder in aanmerking werd genomen wanneer het produceren van nieuw product van admin kant.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/35627>
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/cf34971d>
* _ACP2E-2837_: De entiteit van het product die_bij kolomwaarden wordt bijgewerkt niet terwijl het bijwerken van prijs door REST API
   * _nota van de Reparatie_: Het product &quot;laatst bijgewerkt bij&quot;kolom van admin wordt bijgewerkt de juiste datumtijd terwijl het bijwerken van de bestaande producten door REST API. Eerder is de kolom &#39;last updated at&#39; niet correct bijgewerkt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2840_: Het is mogelijk om niet-unieke waarden via productinvoer te plaatsen
   * _nota van de Reparatie_: Het systeem dwingt nu correct de unieke waardebeperking voor unieke productattributen tijdens productinvoer af, verhinderend dubbele waarden voor dat dergelijke attribuut te hebben. Eerder was het mogelijk om niet-unieke waarden in te stellen voor productkenmerken die waren geconfigureerd om unieke waarden te hebben via het importeren van producten.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38445>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2843_: De producten op het voorste gebruiksopslag specifieke gegevens wanneer de Enige-Opslagwijze wordt toegelaten
   * _nota van de Reparatie_: Eerder, toen wij enige opslagwijze voor de standaard opslagmening toeliet, werden de veranderingen niet gemigreerd aan het website-vlakke werkingsgebied. Nadat deze correctie is toegepast, worden de weergavespecifieke standaardgegevens van de winkel gesynchroniseerd met gegevens op websiteniveau en worden de mogelijke conflicten voor producten en categorieën opgelost.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2857_: Kan &quot;StandaardSoort door&quot;in een categorie plaatsen die rest API gebruiken niet
   * _Bevestig nota_: Update correct default_sort_by op een categorie door REST/SOAP APi- verzoek
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [ Wolk ] De Merchant staat voor problemen met wishlist aantal
   * _Nota van de Reparatie_: Het toevoegen van een product aan de wenslijst in één opslag verhoogt niet meer de verlanglijsttelling in andere opslag open in zelfde browser. Als beide winkels in dezelfde browser werden geladen, zou het aantal wenslijsten ook in de andere winkel toenemen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: De Pagina van de categorie bij frontend toont lege groeven wanneer het gebruiken van bundelproduct
   * _nota van de Reparatie_: De producten van de bundel die niet verkoopbaar in huidige archiefcontext zijn worden niet meer geïndexeerd.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2905_: [ Cloud ] Uitgave van Citaat in multi-website architectuur
   * _nota van de Reparatie_: Eerder, multi-website architectuur met verschillende valuta en klantengroepen kon geen kortingen op de opslag correct toepassen. Nadat deze oplossing is geïmplementeerd, wordt de architectuur met meerdere websites met verschillende kortingen voor de klantgroepprijs met succes toegepast op verschillende winkels.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38506>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice while editing bundle products
   * _nota van de Reparatie_: Er is geen fout javascript in browser console terwijl het schrappen van optie van bundelproduct.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38505>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [ de verkeerde prijs van het Product van de Pakket van de Wolk ] in orde bevestiging
   * _nota van de Reparatie_: Het correcte bedrag wordt getoond voor bundelopties in orde op Storefront wanneer de munt buiten basale werd gebruikt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: Video die van YouTube Bug toevoegt
   * _nota van de Reparatie_: De beelden en de video&#39;s van het product worden gevormd in globaal werkingsgebied. Aangezien u geen productvideo in één werkingsgebied en niet in een andere kunt hebben, is de belangrijkste het plaatsen van de sleutel van Youtube API aan globaal werkingsgebied geplaatst.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [ de update van de Wolk ] URL slechts voor store_id=0
   * _nota van de Reparatie_: Het &quot;Weg URL&quot;wordt nu opgeslagen met correcte opslagidentiteitskaart Eerder was de opslag-id onjuist, waardoor er onjuiste URL-paden in de database achterbleven wanneer categorieën worden verplaatst.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all uitgevoerde en creeerde een fout.
   * _nota van de Reparatie_: De onjuiste gegevens van de productverbinding in vraag REST API veroorzaken niet meer kritieke fouten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [ de Mobiele Uitgave van de Wolk ] kan slechts niet op het beeld pinch PDP
   * _nota van de Reparatie_: Het systeem steunt nu knijpbeweging-aan-gezoemfunctionaliteit op de beelden van de productdetailpagina in mobiele mening op Chrome, die de mobiele gebruikerservaring verbeteren. Eerder werd niet op de afbeelding ingezoomd door te dubbeltikken op de afbeelding in de mobiele weergave op Chrome.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: Ontbrekend etiket in LayeredNavigation met optienaam 0
   * _nota van de Reparatie_: De kwestie is opgelost door een lege waardecontrole voor attributenwaarde 0 over te slaan. Eerder werd het als leeg beschouwd en veroorzaakte het probleem.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: De klanten zien prijzen van andere klantengroepen
   * _Nota van de Reparatie_: Vaste kwestie waar de klantengroep verwante informatie in een verkeerd segment wegens de oude waarde van X-Magento-Vary in verzoek werd bewaard
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: Fout wanneer het schrappen van bundelopties
   * _nota van de Reparatie_: Het systeem schrapt nu correct bundelopties zonder een fout teweeg te brengen of de pagina te veroorzaken om niet ontvankelijk te worden. Als u voorheen bundelopties verwijdert, treedt de fout &quot;Pagina reageert niet&quot; op en wordt het product niet opgeslagen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3100_: [ het Dossier van het Beeld van de Wolk ] bestaat niet in het Logboek van de Fout van New Relic
   * _nota van de Reparatie_: Het systeem synchroniseert nu douaneplaceholder beelden aan lokale opslag, die ervoor zorgen dat zij correct teruggeven wanneer het gebruiken van verre opslag zoals AWS S3. Eerder konden aangepaste plaatsaanduidingsafbeeldingen niet worden gerenderd bij gebruik van externe opslag, wat resulteerde in een verbroken weergave van de afbeelding en foutlogboeken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3126_: [ de reactie van GQL van de Galerij van de Media van het Product van de Wolk ] wordt niet gesorteerd door beeldpositie
   * _nota van de Reparatie_: Het systeem sorteert nu correct punten in de media galerij door positie in de reactie van GraphQL, die nauwkeurige vertoningsorde verzekeren. Eerder zijn de items in de mediagalerie niet op positie gesorteerd, wat tot een onjuiste weergavevolgorde heeft geleid.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37671>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [ de punten van de 3} Subcategorie van de Wolk {worden niet getoond op widgets uitgeven op admin achtereind]
   * _nota van de Reparatie_: De categorieboom op de nieuwe widgetpagina zou geen kwesties meer moeten hebben ladend Niveau 5+ categorieën. Eerder ontbraken enkele categorieën bij het laden van de structuur voorbij de categorieën van niveau 5.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/148c3ead>

### Catalogus, framework

* _ACP2E-2949_: [ Cloud ] follow-up: Verkeerde gelijke in Gegevens Vergelijking wanneer het controleren als het gegeven veranderingen heeft
   * _nota van de Reparatie_: Eerder, werd het sparen voorwerp geroepen telkens zonder enige gegevensveranderingen (voor om het even welk numeriek gegevensgebied - zoals int/float/dubbel). Het activeert de markering _hasDataChanges om waar te zijn en roept de opslagfunctie aan. Het controleert ook niet de drijvende aantallen die door koord worden ingekapseld. Nadat deze correctie is toegepast, wordt de functie Save alleen aangeroepen als de gegevens zijn gewijzigd. De gegevenswaarde voor int/float/double-check met de waarde die aan de functie wordt doorgegeven en het strikte type dat overeenkomt
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8931218>

### Catalogus, GraphQL

* _ACP2E-3090_: Het behandelen van de Filters van de Categorie in GraphQL: includeDirectChildrenOnly en category_uid
   * _Bevestig nota_: Slechts worden de directe kindcategorieën gehaald terwijl het filtreren door category_uid.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [ Cloud ] Grafiek het sorteren van het Product werkt niet
   * _Bevestig nota_: Het sorteren van het Product GraphQl door veelvoudige gebieden wanneer de gebieden in variabelen nu worden overgegaan werkt zoals verwacht.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/8459b17d>

### Catalogus, Prijzen, Staging en Voorvertoning

* _ACP2E-2672_: [ het eindpunt van de PrijsAPI van de Wolk ] keert fout terug wanneer het bijwerken van grote aantallen producten gelijktijdig
   * _de nota van de Reparatie_: Nu zal de speciale Prijs update API één enkele campagne voor elke datumwaaier in plaats van veelvoudige geplande updates voor elk product en datumwaaier tot stand brengen. Bovendien worden gelijktijdige API-aanvragen voor snellere verwerking van een groot aantal SKU&#39;s ondersteund.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>

### Catalogus, product

* _AC-7050_: De boomstructuur van de categorieselectie in geeft product uit is niet in de zelfde orde zoals die in Catalog ->Categorieën wordt geplaatst
   * _nota van de Reparatie_: Het systeem toont nu correct de boomstructuur van de categorieselectie in product uitgeeft sectie in de zelfde orde zoals die in Catalogus ->Categorieën wordt geplaatst, makend productbeleid in grote catalogi gemakkelijker. Eerder werd de categoriestructuur in de productbewerkingssectie weergegeven in de volgorde van het maken van de categorie, ongeacht de weergavevolgorde ingesteld in Catalog->Categorieën.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36101>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36104>

### Catalogus, zoeken

* _ACP2E-2757_: De producten tonen niet op categorie en onderzoek maar de directe verbindingen werken
   * _Bevestig nota_: Eerder, werkt het ja/Geen douaneattribuut met price_* attribute_code niet met het indexeren. Na deze correctie werkt het kenmerk Yes/No naar behoren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [ Cloud ] Elastische onderzoeksfout op bepaalde categoriepagina&#39;s
   * _nota van de Reparatie_: Eerder, met het vermelde configuratiekaartje, wanneer wij prijs 0 voor veelvoudige producten zetten, zal het een uitzondering bij de voorste categoriepagina werpen. Nadat deze correctie is toegepast wanneer meerdere productprijzen 0 en we de pagina met categorieën vooraf laden, wordt er geen uitzondering gegenereerd en wordt de pagina met categorieën correct geladen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8931218>

### Wolk

* _ACP2E-3010_: [ de Wolk ] PHPSESSID verandert elk POST- Verzoek
   * _Nota van de Reparatie_: PHPSESSID regenereert niet meer op POST- verzoeken op frontend gebied voor een het programma geopende klant als L2 Redis geheime voorgeheugen wordt toegelaten en de klant werd bijgewerkt van het achterste eind
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>

### Inhoud

* _AC-10539_: [ Uitgave ] kwestie met de prijsvertoning in Recently Bekeken widget
   * _nota van de Reparatie_: Het systeem toont nu correct de prijs van uit-van-voorraad eenvoudige producten in &quot;onlangs Bekeken Product&quot;widget, die consistentie over alle widgets en pagina&#39;s van de productlijst verzekeren. Eerder werd de prijs van eenvoudige producten uit de voorraad niet weergegeven in de widget Onlangs bekeken product vanwege een voorwaarde in de sjablonen voor het laden van prijzen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38167>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38159>
* _AC-10596_: [ Correct type en grammatica van de Kwestie ] in acl.xsd- dossier
   * _nota van de Reparatie_: Het systeem verbetert nu een typefout en grammaticacl.xsd- dossier, die de duidelijkheid en de nauwkeurigheid van de documentatie verbeteren. Eerder bevatte het bestand acl.xsd een typefout en een onjuiste grammatica die tot verwarring kon leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38061>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38046>
* _AC-10845_: Beeld van de banner van de Pagebuilder niet zichtbaar in galerij
   * _nota van de Reparatie_: Het systeem toont nu correct bannerbeelden die in pas gecreëerde omslagen in de galerij van de Pagebuilder worden geupload, die vorige consolefouten elimineren. Voorafgaand aan deze correctie waren de bannerafbeeldingen niet zichtbaar in de galerie als ze in een nieuwe map waren geüpload, waardoor een consolefout ontstond.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12283_: &quot;De code van het gebied niet plaatste&quot;na update aan 2.4.5-p8
   * _nota van de Reparatie_: Het systeem voltooit nu met succes het statische proces van de inhoudsplaatsing wanneer de module Magento_CSP wordt toegelaten en &quot;dev/js/translate_strategy&quot;wordt geplaatst aan &quot;ingebed&quot;, zonder de &quot;code van het Gebied te veroorzaken niet plaatste&quot;fout. Eerder, onder deze voorwaarden, zou het statische proces van de inhoudsplaatsing met een &quot;niet vastgestelde geen&quot;fout van de Code van het Gebied ontbreken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38845>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38922>
* _AC-9638_: [ het dossier van de kwestie ] uploadt kwestie in de redacteur van WYSIWYG op productpagina
   * _nota van de Reparatie_: Het systeem toont nu correct de omslagboom en staat beeld toe uploadt in de redacteur van WYSIWYG op de productpagina, zelfs na het uitbreiden van het &quot;Beeld en Video&#39;s&quot;lusje eerst. Eerder werd door het uitvouwen van het tabblad &#39;Afbeelding en video&#39;s&#39; de mappenstructuur niet weergegeven en werd een foutbericht weergegeven wanneer werd geprobeerd een afbeelding te uploaden in de WYSIWYG-editor.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38026>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [ On-PREM ] Dynamische blokkwestie
   * _Bevestig nota_: De widgets worden nu behoorlijk teruggegeven binnen dynamische blokken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_: [ Wolk ] Frontend niet ladend toe te schrijven aan kwestie in nieuwsbrief malplaatje
   * _Bevestig nota_: Het toevoegen van blokken via de de inhoudssectie van de Pagina van CMS leidt niet meer tot uitzondering
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [ Cloud ] onderzoekt uitzondering die in het logboek wordt gevonden: InvalidArgumentException: De klasse bestaat niet in vendor/magento/module-rule/Model/ConditionFactory.php
   * _nota van de Reparatie_: Het verwijderen van een voorwaarde op de montages van de de productinhoud PageBuilder veroorzaakt niet meer een uitzondering om in de logboekdossiers worden geregistreerd. Eerder, zou het verwijderen van een voorwaarde op de montages van de de productinhoud PageBuilder een kritieke uitzondering veroorzaken om in de logboeken worden geregistreerd, ondanks het veroorzaken van geen kwesties op het front-end.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: Het schakelen naar enige opslagwijze - de globale inhoud verschijnt niet meer
   * _nota van de Reparatie_: Het systeem synchroniseert nu de configuraties van het opslagmeningsontwerp met de configuraties van het websiteontwerp wanneer het toelaten van enige opslagwijze, die ervoor zorgen dat de inhoudsupdates op het frontend zichtbaar zijn. Eerder, zou het schakelen op enige opslagwijze inhoudsupdates worden weerspiegeld op de storefront verhinderen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: De Bouwer van de pagina vervangt beeld wanneer het proberen om verbinding en andere bruikbaarheidsglitches toe te voegen.
   * _nota van de Reparatie_: Nu het klikken op een beeld, zullen de verbindingen in beeldredacteur in het de tekstelement van de Bouwer van de Pagina juiste gegevens in het beeld, de dialoog van de verbindingsconfiguratie laden. Het toevoegen van een koppeling naar een afbeelding in de editor werkt nu goed. Eerder werd de afbeelding vervangen door een koppeling.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: De oude media galerij ontbreekt om beelden terug te geven wanneer een 0 byte beeld in de folder wordt geplaatst
   * _nota van de Reparatie_: Het systeem behandelt nu 0 byte beelden in de media galerij zonder functionaliteit te verstoren, toestaand andere beelden in de folder om worden getoond en worden geselecteerd zoals verwacht. Eerder was het zo dat door de aanwezigheid van een afbeelding van 0 byte in de mediagalerie niet alle afbeeldingen in de directory konden worden weergegeven of geselecteerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: De Bouwer van de Pagina van de fout wanneer het uitgeven van het Blok van CMS
   * _nota van de Reparatie_: Het systeem bewaart nu correct veranderingen die in het admin gebied worden aangebracht gebruikend de Bouwer van de Pagina, zonder de fout &quot;Bouwer van de Pagina terug te werpen voor 5 seconden zonder sloten vrij te geven.&quot; in de browserconsole. Deze fout is eerder opgetreden tijdens een poging om wijzigingen op te slaan, zodat de inhoud niet met succes kan worden bijgewerkt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [ CLOUD ] Geen knopen van controle of geeft kart op de wortelsectie uit
   * _nota van de Reparatie_: Het product van de bundel wordt nu toegevoegd aan het karretje via widgets zonder fouten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3127_: imagecreatetruecolor (): Argument #2 ($height) moet groter zijn dan 0. Kan specifieke afbeelding niet uploaden
   * _nota van de Reparatie_: Los de kwestie op die fouten in admin veroorzaakt wanneer het uploaden van beelden met een hoogte van 0 via de media galerij, en succesvol de activa synchronisatie gebruikend het synchronisatiebevel. Eerder kan de afbeelding niet worden geüpload via de mediagalerie en de synchronisatieopdracht mislukt ook als een bepaalde afbeelding zich in de galerie bevindt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from in conflict met Google Maps API
   * _nota van de Reparatie_: De Kaarten van Google geven nu behoorlijk in de redacteur PageBuilder terug. Een JavaScript-fout voorkomt eerder dat Google Maps correct wordt weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/148c3ead>

### Klanten/klanten

* _AC-12162_: Voorste eind - de bevestiging van de geboorte ontbreekt in de aanmaakpagina van de Klant
   * _nota van de Reparatie_: Verzeker al bevestiging zou na verbeteringsmoment.js systeemgebiedsdeel aan de recentste minder belangrijke versie moeten werken
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/de4dfb8e>

### Kader

* _AC-10654_: V1/klanten/wachtwoord eindvraag/kwestie
   * _nota van de Reparatie_: Het systeem houdt nu aan de beperkingen binnen beheer GUI worden geplaatst wanneer de verzoeken van de het wachtwoordverandering via API verwerken, die potentieel misbruik van de wachtwoordterugstellingfunctie verhinderen. Voorheen kon de API verzoeken om wachtwoordwijziging verwerken buiten de regels die zijn gedefinieerd in de GUI voor beheer, waardoor mogelijk een constante stroom e-mailberichten zou worden gemaakt als geldige e-mails bekend waren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38238>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10721_:
   * _Bevestig nota_: Bevorder de ligging/de gebiedsdelen van de Componist van het vluchtsysteem die aan recentste versie worden bevorderd
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/91cb4d46>>
   * _de codebijdrage van GitHub_: Bevorder de 2.x liga/de gebiedsdelen van de Composer van het vluchtsysteem aan recentste versie 3.x
* _AC-10838_: Het proces van de het het procesfout van de het onderzoeksindex van de catalogus indexeren
   * _nota van de Reparatie_: Het systeem voltooit nu met succes het re-indexbevel zonder om het even welke fouten te ontmoeten, ongeacht de libxml versie die met PHP wordt gecompileerd. Eerder, resulteerde het runnen van het re-indexbevel in een &quot;fout van het proces van het het indexproces van het Onderzoek van de Catalogus tijdens indexeringsproces&quot;fout wanneer PHP met bepaalde versies van libxml werd gecompileerd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38254>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _wisselstroom-10941_: Toegevoegde created_at, status en de filters Grand_total aan de vraag van de Orden van de klant en bevonden veelvoudige filtermislukking
   * _nota van de Reparatie_: Het systeem steunt nu het gebruik van created_at, status, en de filters Grand_total in de vragen van de Orden van de klant, en heeft een kwestie opgelost waar de veelvoudige filters niet correct werden toegepast. Eerder, steunde het systeem deze filters niet en zou er niet in slagen om alle filters toe te passen wanneer meer dan één in een vraag werd gebruikt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38392>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36949>
* _AC-10971_: https://github.com/magento/magento2/issues/38415
   * _Bevestig nota_: PHP 8.2/8.3, slechts één gebiedsdeel ontbreekt de php linter op het ogenblik: liga/vliegsysteem
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _GitHub codebijdrage_: Het systeem steunt nu PHP 8.2/8.3 door het liga/flysystem pakket aan versie 3.0.20 bij te werken, die ervoor zorgen geen PHP het verbinden fouten voorkomen. Eerder, resulteerde het lopen PHP dossiers door PHP linter met PHP 8.3 in het linken van fouten in het liga/flysystem pakket.
* _AC-10991_: Willekeurig overstroomd krijgen met vragen van verwant/upsell/crosssell blokken en prijs het indexeren
   * _nota van de Reparatie_: Het systeem optimaliseert nu vragen van verwant, upselt, en dwars-verkoopt blokken, verbeterend de prestaties en verhinderend de plaats om te gaan toe te schrijven aan bovenmatige vragen. Eerder, kon het systeem met vragen van deze blokken overbelast worden, veroorzakend significante vertragingen en potentieel verlamend de plaats.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36667>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Uitzondering: Waarschuwing: Het proberen om tot seriecompensatie binnen toegang te hebben.. -> Calendar.php sinds verbetering aan ICU 74.1 (PHP Intl)
   * _nota van de Moeilijke situatie_: Commerce registreert niet meer de volgende uitzondering in exception.log wanneer een verkoopster of handelaar of storefront of Admin bezoekt: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [ GitHub-38214 ](https://github.com/magento/magento2/issues/38214)
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38214>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [ de kwesties van de Uitgave ] verhelpen met de Gegevens van de Klant wanneer de vorm element met naam `method` bevat
   * _nota van de Reparatie_: Het systeem identificeert nu correct de &quot;methode&quot;attributen in vormvoorlegging, zelfs wanneer een element genoemd &quot;methode&quot;in de vorm aanwezig is. Dit zorgt voor een nauwkeurige verwerking van klantgegevens. Als een formulierelement voorheen de naam &#39;method&#39; had, zou dit problemen opleveren met de identificatie van het kenmerk &#39;method&#39; in formulierverzendingen, wat tot mogelijke problemen met de verwerking van klantgegevens zou leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38484>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [ Uitgave ] Repareer PHPDocs voor \Magento\Framework\Data\Collection::getItemById
   * _nota van de Reparatie_: PHPDocs voor de \Magento\Framework\Data\Collection::getItemById methode is bijgewerkt om ongeldig als mogelijk terugkeertype te omvatten, richtend kwesties met statische analysehulpmiddelen. Eerder, specificeerde PHPDocs van de methode ongeldig als mogelijk terugkeertype niet, dat tot waarschuwingen of fouten in statische analyse leidde toen de methode in voorwaardelijke verklaringen werd gebruikt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38485>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38439>
* _AC-11651_: Magento die probeert om read-only bezit in __wakeup methode van LoggerProxy te wijzigen
   * _nota van de Reparatie_: Het systeem staat nu de wijziging van eerder read-only eigenschappen in de methode __wakeup van LoggerProxy toe, die vlotte verrichting verzekert zonder gebruikers te dwingen om een alternerende actie aan te wenden. Eerder, zou een poging om de waarde van een read-only bezit in de methode __wakeup van LoggerProxy opnieuw toe te wijzen kwesties veroorzaken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38526>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11673_:
   * _Nota van de Reparatie_: Onderzoek php-amqplib/php-amqplib recentste versies
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub codebijdrage_: Bijgewerkt de recentste versie php-amqplib/php-amqplib:^3.x
* _AC-11681_: [ Uitgave ] AC-2039 wisselstroom-1667 verbetert verwijzingen TinyMCE
   * _Nota van de Moeilijke situatie_: Bijgewerkte versie van de tinentie in composer.json
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38533>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker werkt niet in veelvoudige draden
   * _nota van de Reparatie_: Het systeem steunt nu procesvork voor indexatie MView, die fouten tijdens indexeeruitvoering verhinderen wanneer het werken op veelvoudige draden. Eerder, zou het runnen van ChangelogBatchWalker op veelvoudige draden tot de schrapping van lijsten leiden die door andere draden worden gebruikt, die een fout tijdens indexeruitvoering veroorzaken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38246>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [ Uitgave ] noemt verkeerd genoemde variabele anders
   * _nota van de Reparatie_: Het systeem noemt nu correct de variabele die de hoeveelheid geld bevat die nog kan worden teruggegeven, verhinderend verwarring tijdens het zuiveren. Eerder werd deze variabele onjuist benoemd als totalResund, wat tot misverstanden voor ontwikkelaars zou kunnen leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38609>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36205>
* _AC-11808_:
   * _Bevestig nota_: De lijst van de gebiedsdelen van de Kern van Adobe Commerce van de investering en bevordert
   * _GitHub codebijdrage_: De behoefte verbetert de lijst van de Gedeelten van de Kern van Adobe Commerce 
* _AC-11819_: Het ingebouwde geheime voorgeheugen FPC wordt gebroken in 2.4.7 voor sommige configuraties
   * _nota van de Reparatie_: Het systeem bewaart nu correct pagina&#39;s wanneer de parameter MAGE_RUN_CODE wordt geplaatst, die optimale prestaties verzekeren. Eerder werden pagina&#39;s niet in cache geplaatst onder deze omstandigheden, wat tot mogelijke prestatieproblemen leidde.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38626>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38646>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-11829_: [ De uitzondering van de kwestie ] lost inconsistentie van de uitzonderingsbehandeling tussen ontwikkelaar en productiemodi op
   * _nota van de Reparatie_: Het systeem behandelt nu constant uitzonderingen tussen ontwikkelaar en productiemodi, verhinderend onverwachte redirection aan de login pagina wanneer een uitzondering wordt geworpen. Eerder, kon een inconsistentie in uitzonderingsbehandeling tot een omleiding aan de login pagina op productiemodus in plaats van het tonen van het uitzonderingsbericht leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38639>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37712>
* _AC-11852_: Vervang de vertaling &quot;van de Rekening van PayPal&quot;in token_list.phtml
   * _Bevestig nota_: Het systeem etiketteert nu de sectie voor kenizable methodes van de rekeningsbetaling als &quot;Rekening&quot;in plaats van &quot;Rekening van PayPal&quot;in de Opgeslagen pagina van de Methoden van de Betaling, die het representatiever van zijn functie maakt. Eerder werd deze sectie specifiek aangeduid als &quot;PayPal-rekening&quot;, wat misleidend was toen andere betaalmethoden voor betaalrekeningen werden toegevoegd die kenisbaar waren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/35622>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37959>
* _AC-11905_: [ geef ] Statische inhoud uit - de fout van het Type
   * _nota van de Reparatie_: Het systeem behandelt nu correct lege dossiers LESS tijdens statische inhoudsplaatsing, tonend een &quot;LESS dossier is leeg&quot;foutenmelding. Eerder werd een fout met een onjuist type gegenereerd bij het optreden van een leeg LESS-bestand tijdens de implementatie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38682>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38683>
* _AC-11911_:
   * _Bevestig nota_: jQuery/fileuploader css schoonmaakbeurt na migratie aan uppy bibliotheek
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub codebijdrage_: Verwijderd jQuery/fileUploader bibliotheek omdat het aan de bibliotheek van het Uppy is gemigreerd
* _AC-12002_: [ Uitgave ] [ Mening ] Verwijderde extra ruimte in verbinding en manuscriptmarkering
   * _nota van de Reparatie_: Het systeem zorgt nu ervoor dat er geen extra ruimten in de verbinding en manuscriptmarkeringen zijn, die helderdere en efficiëntere code verstrekken. Eerder konden dubbele ruimten tussen attributen in de verbinding en manuscriptmarkeringen worden gevonden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32920>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32919>
* _AC-12015_:
   * _Bevestig nota_: De omslagschoonmaakbeurt ExtJs na migratie aan jsTree bibliotheek
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/7cabfb46>>
   * _GitHub codebijdrage_: Verwijderd omslag TextJs aangezien de verwante functionaliteit aan jsTree is gemigreerd
* _AC-12022_:
   * _Bevestig nota_: De monoloog/monoloog systeemgebiedsdeel van de verbetering aan de recentste belangrijkste versie
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub codebijdrage_: Het systeem is bijgewerkt om de recentste belangrijkste versie van de &quot;monolog/monolog:^3.x&quot;bibliotheek te gebruiken, die verenigbaarheid en betere prestaties verzekeren. Eerder gebruikte het systeem een verouderde versie van de &quot;monolog/monolog&quot; bibliotheek die tot mogelijke problemen en beperkingen had kunnen leiden.
* _AC-12023_:
   * _Bevestig nota_: Bevorder wikimedia/less.php gebiedsdeel aan de recentste belangrijkste versie
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _GitHub codebijdrage_: Het systeem is bijgewerkt om de recentste belangrijkste versie 5.x van de &quot;wikimedia/less.php&quot;bibliotheek te gebruiken, die verenigbaarheid en bijgewerkte functionaliteit verzekeren. Eerder gebruikte het systeem een verouderde versie van de bibliotheek die tot veiligheidskwesties kon hebben geleid.
* _AC-12024_:
   * _Bevestig nota_: Bevorder jquery/bevestig bibliotheekgebiedsdeel aan de recentste minder belangrijke versie
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub codebijdrage_: Bevorder jquery/bevestig bibliotheekgebiedsdeel aan recentste minder belangrijke versie 1.20.0
* _AC-12025_:
   * _Bevestig nota_: Het systeemgebiedsdeel van de verbetering moment.js aan de recentste minder belangrijke versie
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/de4dfb8e>>
   * _GitHub codebijdrage_: Het systeemgebiedsdeel van de verbetering moment.js aan recentste minder belangrijke versie 2.30.1
* _AC-12267_:
   * _Bevestig nota_: De verbindingspogingen van de steun voor Redis zitting en compatibel met colinmolenhour/php-redis-session-abstract v2.0.0
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/672a2e61>>
   * _de codebijdrage van GitHub_: Bijgewerkte recentste versie van colinmolenhour/php-redis-session-abstract v2.0.0 compatibel met de handel van Adobe
* _AC-12268_:
   * _Bevestig nota_: De gebiedsdelen van de Samensteller van de verbetering liga/flysystem aan recentste versie
   * _de codebijdrage van GitHub_: Bevorder de 2.x liga/de gebiedsdelen van de Composer van het vluchtsysteem aan recentste versie 3.x
* _AC-12594_: [ Gecompileerde config van het Gebruik van de kwestie ] voor geproduceerde gegevens in plaats van algemene config
   * _nota van de Reparatie_: Het systeem gebruikt nu de gecompileerde configuratie voor geproduceerde gegevens in plaats van de algemene configuratie, die netwerkoverdracht en overheadkosten van gegevens vermindert die van een bepaalde versie van code afhangt. Door deze wijziging wordt voorkomen dat cache wordt overschreven in gedeelde instanties tijdens het wisselen van containers. Dit leidt tot betere stabiliteit en minder downtime. Eerder, gebruikten bepaalde kernklassen het gedeelde configuratietype, dat tot geheim voorgeheugen het met voeten treden of toepassingsonderbreking wegens verschillen in codeversies over veelvoudige servers kon leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38785>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [ Uitgave ] verwijdert verwijzingen naar dossiers uit extjs die in e1cdb werden verwijderd..
   * _nota van de Reparatie_: Het systeem verwijdert nu verwijzingen naar dossiers uit uitbreidingen die eerder werden verwijderd, eliminerend fouten in de browser console en het dossier van het systeemlogboek. Voorheen veroorzaakten deze verwijzingen fouten vanwege het ontbreken van de bestanden waarnaar wordt verwezen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38960>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38951>
* _AC-12715_:
   * _Bevestig nota_: De gebiedsdelen van de composer van de update laminas bevorderen aan recentste versie
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/b34c0a75>>
   * _GitHub codebijdrage_: Het systeem steunt nu de recentste versies van laminas composer gebiedsdelen:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
zorgen voor compatibiliteit en up-to-date functionaliteit. Eerder, kon het bijwerken aan de recentste versies van deze gebiedsdelen achterwaartse onverenigbaarheidskwesties en testmislukkingen veroorzaken.
* _AC-12778_: [ geef ] Kleine schoonmaak uit: het vaste verkeerde gebruik van sprintf, het neemt slechts 2 placeholders hier en w...
   * _nota van de Reparatie_: Het systeem gebruikt nu correct de functie sprintf met het aangewezen aantal placeholders, die codeschoonheid en consistentie verbeteren. Eerder werd de functie sprintf onjuist gebruikt met een extra argument, dat geen belangrijke kwesties veroorzaakte maar niet het correcte gebruik was.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39062>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38628>
* _AC-12866_:
   * _nota van de Reparatie_: Verwijder Afschrijvingen - Tests van de Integratie PhpUnit10
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _de codebijdrage van GitHub_: Los de Afschrijvingen PHPUnit op
* _AC-12868_:
   * _nota van de Reparatie_: Verwijder Afschrijvingen - Tests PhpUnit10 WebApi
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/edcd0dcc>>
   * _de codebijdrage van GitHub_: Los de Afschrijvingen PHPUnit op
* _wisselstroom-12869_: [ de 3} Correcties van de Uitgave {onjuiste klassen die in de modules van Magento worden van verwijzingen voorzien.]
   * _nota van de Reparatie_: Het systeem verwijzingen nu correct klassen in modules, die vlottere verrichting verzekeren en neerstortingen wegens niet-bestaande klassen verhinderen. Dit omvat een bugfix in de modules Indexer en Creditmemo, en de implementatie van HttpGetActionInterface in de klasse PrintAction. Eerder, leidden de onjuiste klassenverwijzingen tot fouten en potentiële systeemneerstortingen, en bepaalde functionaliteiten, zoals filename voor creditmemo PDF dossiers en het opnieuw indexeren van voorraden, werkten niet zoals verwacht.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39126>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37784>
* _AC-6754_: typefout op een JS- dossier.
   * _nota van de Reparatie_: Het systeem gebruikt nu correct de term &quot;abonnees&quot;in het dossier van JavaScript, die juiste functionaliteit van de verwante eigenschappen verzekeren. Eerder leidde een typografische fout in het JavaScript-bestand tot een onjuist gebruik van de term &quot;abonnees&quot;.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36163>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36171>
* _AC-8353_: [ Uitgave ] verwijdert verboden `@author` markering
   * _nota van de Reparatie_: Het systeem volgt nu aan coderingsnormen door de verboden `@author` markering van bepaalde modules te verwijderen, die schonere en meer gestandaardiseerde code verzekeren. Eerder was de tag `@author` in sommige modules aanwezig, wat in strijd was met de vastgestelde coderingsnormen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37253>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37003>
* _AC-8356_: [ Uitgave ] verwijdert verboden `@author` markering uit `Magento_Customer` (deel 2)
   * _nota van de Reparatie_: Het systeem houdt nu aan de coderingsnorm door de verboden `@author` markering van bepaalde modules te verwijderen, die schonere en meer gestandaardiseerde code verzekeren. Eerder was de tag `@author` in sommige modules aanwezig, wat in strijd was met de vastgestelde coderingsnormen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37250>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37000>
* _AC-8659_: Ruimte in redactorconfig de regel van de syntaxis voor [ {composer, auth}.json ]
   * _nota van de Reparatie_: Het systeem past nu correct een 4-ruimteparagraaf op de composer en auth.json- dossiers toe, na een moeilijke situatie op een syntaxisfout in editorconfig. Eerder waren deze bestanden vanwege een spatie in de bewerkingsconfig-syntaxis onjuist opgemaakt met een inspringing voor twee spaties.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37394>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37395>
* _wisselstroom-8984_: [ Uitgave ] voegt sommige meer kleuren aan de output van bepaalde opstellingskli bevelen toe
   * _nota van de Reparatie_: Het systeem voegt nu meer kleuren aan de output van bepaalde (CLI) bevelen van de opstellingsbevellijn toe, die leesbaarheid en gebruikerservaring verbeteren. Eerder was de uitvoer van deze opdrachten moeilijker te lezen vanwege een gebrek aan kleurdifferentiatie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/29335>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: Bevorderend Magento stelt algemeen/gebied/state_required terug wanneer het nieuwe land met vereiste staat/gebied wordt toegevoegd.
   * _nota van de Reparatie_: Het systeem voegt nu slechts het gewijzigde land aan de &quot;algemene/regio/state_required&quot;configuratie toe wanneer een nieuw land met vereiste staten wordt toegevoegd, verhinderend om het even welke verstoring aan douanecode die veronderstelt het gebied gehandicapt is. Eerder, zou het toevoegen van een nieuw land met vereiste staten de &quot;algemene/regio/staat_required&quot;configuratie terugstellen om landen met een vereiste staat in gebreke te stellen, potentieel brekend de winkel.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37796>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: Verschil in minder compilatie tussen php &amp; nodejs bibliotheek (grot) met gecompliceerde `calc` uitdrukkingen
   * _nota van de Reparatie_: Recht het verschil in minder compilatie tussen php &amp; nodejs bibliotheek (grot) na update wikimedia/less.php:^5.x
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37841>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: De fout &quot;van de lijst van de Basis of de mening niet gevonden&quot;komt voor wanneer het gedeeltelijke indexeren wordt uitgevoerd
   * _Nota van de Reparatie_: De gedeeltelijke herdex werkt nu correct met grote verandering in geval van secundaire db verbinding
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: De kwesties na bevordering MariaDB aan 10.5.1 of hoger
   * _Bevestig nota_: Vaste de kwestie toen datetime waarden in een OB in 000-00-00 00 :00: 00 na verbetering Mysql zouden worden omgezet
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Het type in Vergelijking van Gegevens wanneer het controleren als het gegeven veranderingen heeft
   * _nota van de Reparatie_: Eerder, werd het sparen voorwerp geroepen telkens zonder enige gegevensveranderingen (voor om het even welk numeriek gegevensgebied - zoals int/float/dubbel). Het activeert de markering _hasDataChanges om waar te zijn en roept de opslagfunctie aan. Nadat deze correctie is toegepast, wordt de functie Save alleen aangeroepen als de gegevens zijn gewijzigd. De gegevenswaarde voor int/float/double-check met de waarde die aan de functie wordt doorgegeven en strikte overeenkomende typen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [ de invoer van de Wolk ] kan niet met folder var worden gebruikt
   * _nota van de Reparatie_: Het product kan met succes ongeacht het dossier worden ingevoerd - naam.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: In iPad mini de menu en kopballadingen als mobiel, in plaats daarvan zouden zij als Desktop moeten laden.
   * _nota van de Reparatie_: Het systeem behandelt nu apparaten met een breedte van 768px als Desktop, die ervoor zorgen dat het menu en de kopbal correct laden. Eerder werden apparaten met een breedte van 768 px als mobiel beschouwd, waardoor het menu en de koptekst in een mobiele weergave werden geladen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>

### Framework, GraphQL

* _AC-7976_: [ Uitgave ] Ingevoerde steun van douane scalaire types voor het schema van GraphQL
   * _nota van de Reparatie_: Het systeem steunt nu douane scalaire types voor het schema van GraphQL, toestaand ontwikkelaars om douane scalaire types en implementaties te bepalen. Deze functie kan vooral handig zijn voor het uitdrukken van waarden die moeten worden gevalideerd, zoals HTML, e-mails, URL&#39;s, datums, enzovoort, en voor meer geavanceerde gevallen zoals EAV-kenmerken. Eerder, steunde het systeem niet de verwerking van douane scalaire types in GraphQL.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36877>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL

* _AC-11729_: Magento_GraphQl voert kopballen verwerking uit zelfs als de kopbalwaarde geen bevestiging overgaat
   * _nota van de Reparatie_: Het systeem zorgt nu ervoor dat de kopbalverwerking slechts eenmaal wordt uitgevoerd als de kopbalwaarde bevestiging overgaat, die veiligheid verbetert en potentiële kwetsbaarheid verhindert. Eerder werd koptekstverwerking uitgevoerd, zelfs als de headerwaarde niet was geslaagd voor validatie. Dit leidde tot potentiële kwetsbaarheden en onverwacht gedrag als gevolg van dubbele verwerking van headerwaarden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-8951_: De fysieke opties van Giftcard hebben niet de juiste sorteervolgorde
   * _nota van de Reparatie_: Het systeem sorteert nu correct de opties van fysieke geschenkkaartproducten wanneer gevraagd via GraphQL, die verenigbare teruggeven met het thema van de Luma verzekeren. Eerder was de sorteervolgorde onjuist volgens luma-thema, wat leidde tot een onjuiste weergave en volgorde van opties zoals de naam van de afzender, de naam van de ontvanger en het bedrag.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-9157_: [ het Geheime voorgeheugen van de Oplossing van GraphQL ] wordt ongeldig wanneer het Creëren/het Uitgeven/het Bewegend/het Schrappen van een het Opvoeren Update
   * _nota van de Reparatie_: Het systeem zorgt nu ervoor dat het resolver geheime voorgeheugen niet ongeldig wordt wanneer het creëren van, het uitgeven van, het bewegen van, of het schrappen van een het opvoeren update, maar slechts wanneer de het opvoeren update wordt toegepast op de entiteit. Eerder werd de oplossercache voortijdig ongeldig gemaakt, zelfs voordat de testupdate werd toegepast, wat tot onnodige cachevervalsingen leidde.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2642_: Fastly geheim voorgeheugen niet ontruimd voor de update van de inhoudstaging
   * _nota van de Reparatie_: Nu GraphQL met het geheime voorgeheugen van de de inhoudsreactie PageBuilder wordt ongeldig gemaakt, wanneer de tevreden PageBuilder verwante entiteiten worden bijgewerkt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Het onbruikbaar maken van Gelaagde Navigatie - verwijdert geen samenvoeging uit Grahql
   * _nota van de Reparatie_: De kwestie is opgelost na het toepassen van de controle terwijl het verzoeken van een productonderzoek met categoriesamenvoegingen door een vraag van GraphQL wanneer admin configuratie die &quot;Catalogus > Gelaagde Navigatie > de Filter van de Categorie van de Vertoning&quot;plaatst.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: De vraag van de Producten van GraphQL die de prijsfilter {van bevat:&quot;0&quot;} keert geen resultaat terug
   * _nota van de Reparatie_: Eerder grafisch productonderzoek met filter voor nulprijzen retourneerde geen resultaten bij allen toe te schrijven aan een geworpen uitzondering. De zoekopdracht geeft nu resultaten zoals verwacht.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-3128_: [ de Verbroken vraag van GraphQL van de Wolk ] voor getPurchaseOrder met knoopcitaat
   * _Bevestig nota_: De vraag van GraphQL van de Orde van de Aankoop zal de taak kunnen uitvoeren zonder enige interne serverfouten te ontmoeten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [ De Wolk ] Configureerbare Producten niet getoond in de Plaats van de Productie als het Product niet in &quot;Alle Mening van de Opslag&quot;wordt toegelaten
   * _nota van de Reparatie_: Het systeem toont nu correct configureerbare producten in de plaats zelfs als het product niet in &quot;Alle Kijken van de Opslag&quot;wordt toegelaten, maar in specifiek werkingsgebied van de opslagmening wordt toegelaten.
Als een product eerder was uitgeschakeld in &quot;Alle winkelweergaven&quot; en alleen was ingeschakeld in specifieke weergavebereiken van de winkel, zouden de productkenmerken niet correct worden weergegeven in de GraphQL-reactie, waardoor het product niet correct wordt weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: [ de Grafiek van de Producten van de Wolk ] die fout hebben wanneer het zelfde eenvoudige product aan veelvoudige configureerbare producten heeft toegewezen
   * _nota van de Reparatie_: Eerder, met afzonderlijke configureerbare producten met het zelfde eenvoudige product, keert grapQL een fout terug. Nadat deze moeilijke situatie van toepassing is, verschillende configureerbare producten met het zelfde eenvoudige product, geeft grapQL resultaat zonder geen fout.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3253_: De paginering van GraphQL karretjesV2 werkt niet correct
   * _nota van de Reparatie_: De kwestie is bevestigd door de correcte waarde voor het huidige paginaargument in de inzamelingsvraag over te gaan. Eerder werd de verkeerde waarde doorgegeven om de huidige pagina in te stellen, waardoor de uitgave optrad.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/8459b17d>

### GraphQL, Inventaris/MSI

* _ACP2E-2607_: De mutatie MergeCart werpt uitzondering wanneer de bron en de bestemmingshavens de zelfde bundelpunten hebben
   * _Bevestig nota_: &quot;-
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>, <https://github.com/magento/inventory/commit/db0620da>

### GraphQL, Inventory / MSI, prestaties

* _ACP2E-1716_: Plaats neer na verbetering
   * _nota van de Reparatie_: De prestaties van het halen van bundelproducten door GraphQl wordt verbeterd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>, <https://github.com/magento/inventory/commit/bdbf97ea>

### GraphQL, prestaties

* _wisselstroom-9569_: [ GraphQL Resolver ] de Gegevens van de Resolver van de Klant wordt niet ongeldig van de Invoer
   * _nota van de Oplossing_: Het geheime voorgeheugen van de klantenoplosser van GraphQL wordt nu ongeldig gemaakt zoals verwacht wanneer een klant door de invoer wordt uitgegeven of geschrapt. Eerder is de cache niet ongeldig gemaakt en konden de klantgegevens tijdens het importeren worden bewerkt of verwijderd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0574ac23>

### GraphQL, zoeken

* _ACP2E-2809_: Het sorteren van de het productlijst van GraphQL door veelvoudige parameters werkt niet
   * _Nota van de Reparatie_: Het sorteren van het product door veelvoudige gebieden in GraphQl werkt nu zoals die in de documentatie wordt beschreven
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>

### Importeren/exporteren

* _AC-12172_: Uitgave bij productinvoer wanneer voorzien van douane opties-type: dossier (het Gemaakt Product bevat geen prijs voor douane-optie en toont slechts de eerste verstrekte uitbreiding van het dossiertype)
   * _nota van de Reparatie_: Het systeem voert nu correct productgegevens met douaneopties van type &quot;dossier&quot;in, die ervoor zorgen dat alle verstrekte dossieruitbreidingen worden getoond en de prijs voor de douaneoptie is inbegrepen. Eerder werd tijdens het importeren van producten alleen de eerste extensie weergegeven en ontbrak de prijs voor de aangepaste optie als een aangepaste optie van het type &#39;file&#39; was voorzien van meerdere bestandsextensies.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38805>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: Onjuiste uitvoeringstijd voor de invoerverrichting in het net van de Geschiedenis van de Invoer
   * _nota van de Reparatie_: De uitvoeringstijd van het rapport van de invoer toont correct onafhankelijk van admin scène.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: De dubbele klanten die met het zelfde e-mailadres worden gecreeerd gebruikend de invoer
   * _nota van de Reparatie_: Het invoeren van de klant terwijl het Delen van de Rekening die aan Globale wordt geplaatst, wordt de ingevoerde klant die in het systeem bestaat bijgewerkt.
Eerder geïmporteerde klant is gedupliceerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2902_: Voeg/werk de Invoer op Producten toe die Aanpasbare Opties dupliceren
   * _nota van de Reparatie_: De kwestie is opgelost door de correcte opslag aan productopties tijdens de invoer CSV van productopties toe te wijzen.
Eerder, toegewezen aan de admin store in plaats van hun respectieve opslag.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2990_: De klant &quot;created_at&quot;datum niet Omgezet om tijdzone op de uitvoer op te slaan
   * _nota van de Reparatie_: Een kolom &quot;created_at&quot;datumwaarde wordt omgezet in het juiste datumformaat dat op de opslag wordt gebaseerd tijdzone in de de uitvoerCSV van de klant.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3165_: [ Cloud ] die fout terwijl het controleren van de gegevens in invoergegevens gebruikend CSV krijgt
   * _nota van de Reparatie_: Er is geen fout wanneer het controleren van de gegevens tijdens de invoer CSV. Eerder werd het volgende foutbericht weergegeven: &quot;We kunnen geen klant vinden die deze e-mail- en websitecode in rij(en): 1 aanpast wanneer de gegevens in de importsectie worden gecontroleerd met gebruik van CSV vanuit de beheerder.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/8459b17d>

### Installeren en beheren

* _ACP2E-2102_: Geen VCL van de Uitvoer voor Varnish 7 knoop in admin paneel
   * _nota van de Reparatie_: &quot;De knoop van de Uitvoer VCL voor Varnish 7&quot;werd toegevoegd aan het Admin paneel.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventaris/MSI

* _AC-11593_: De sleutel van Google google API werkt niet terwijl het toevoegen van Kaart met attributen
   * _nota van de Reparatie_: Het systeem steunt nu de recentste versie 3.56 van de Kaarten API van Google, toestaand gebruikers om een de inhoudsblok van de Kaart van het menu PageBuilder aan het stadium met succes toe te voegen zonder om het even welke fouten te ontmoeten. Eerder konden gebruikers geen Map-inhoudsblok toevoegen vanwege compatibiliteitsproblemen met de Google Maps API-versie. Dit leidde tot een foutbericht dat er iets fout was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2794_: [ de Kritieke Kwestie van de Wolk ] met Product dat met Lege Plaatsen van een lijst maakt
   * _nota van de Reparatie_: Het systeem toont nu correct productlijsten zonder lege ruimten wanneer de producten aan &quot;uit voorraad&quot;worden geplaatst, die een verenigbare en nauwkeurige vertoning van beschikbare producten verzekeren. Als u een product eerder instelt op &#39;Uit voorraad&#39;, wordt er een lege ruimte weergegeven in de productlijst, waardoor de layout wordt verstoord en klanten mogelijk in verwarring raken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>

### Volgorde

* _wisselstroom-10828_: Het scherm van het het overzicht van de orde van de achtergrond: Achtergeordende hoeveelheid niet zichtbaar op het niveau van het orde punt
   * _nota van de Reparatie_: Het systeem toont nu het aantal backordered punten in de kwantitatieve kolom op het scherm van het overzicht van de achterste orde. Dit zorgt ervoor dat de gebruikers de status van alle punten in een orde nauwkeurig kunnen volgen. Eerder gaf de kolom Aantal alleen het aantal objecten weer dat was besteld, gefactureerd en verzonden, maar niet het aantal objecten met een backorder.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38252>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38320>
* _wisselstroom-10994_: [ Verkeerde de opslagidentiteitskaart van de Uitgave ] die in Renderer van het Adres van de Orde wordt gebruikt
   * _nota van de Reparatie_: Het systeem gebruikt nu correct opslagidentiteitskaart verbonden aan een orde wanneer het teruggeven van het ordeadres, die ervoor zorgen dat de adressen correct volgens hun respectieve opslagidentiteitskaart worden geformatteerd. Eerder gebruikte het systeem onjuist de huidige winkel-id, wat tot een onjuiste adresnotatie kan leiden wanneer meerdere bestelling-e-mails van verschillende winkels moeten worden verzonden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38412>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37932>
* _AC-11798_: [ de Verzendprijs van de kwestie ] die verschillend in gedrukt pdf toont
   * _nota van de Reparatie_: Het systeem toont nu correct de verschepende prijzen in gedrukte PDFs volgens de montages van de belastingconfiguratie, die consistentie tussen de de meningspagina van de verkooporde van de factuur en de gedrukte factuur verzekeren. Eerder was de verzendprijs die in de afgedrukte PDF werd weergegeven exclusief belasting, ongeacht de instellingen voor de belastingconfiguratie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38608>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _ACP2E-2622_: Onbekwaam om veranderingen in telefoonaantal in bestaande ordedetails te bewaren
   * _nota van de Reparatie_: Nu kan de gebruiker internationale prefix 00 op het telefoongebied van ordeadres toevoegen
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38201>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: De e-mail ontbreekt om te verzenden
   * _nota van de Reparatie_: Het systeem omvat nu een configuratieoptie async_sending_probeerde om het aantal pogingen te specificeren om een e-mail te verzenden alvorens te stoppen, verbeterend de behandeling van ontbroken e-mail verzendt wanneer &quot;Asynchroon verzenden&quot;wordt toegelaten. Als het verzenden van een e-mail mislukt, probeert het systeem het bericht voortdurend opnieuw te verzenden, wat resulteert in een eindeloze lus met foutberichten in het systeemlogboek.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [ de Status van de Orde van de Wolk ] veranderde om te voltooien wanneer gedeeltelijk terugbetaling van een gedeeltelijk verscheepte orde
   * _nota van de Reparatie_: Wanneer het uitgeven van een creditnota, wordt de ordestatus niet meer veranderd in &quot;voltooid&quot;als er punten zijn die nog niet zijn verscheept.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [ CLOUD ] kan verzenden geen E-mail van Admin UI onbruikbaar maken aangezien Dev Docs toont
   * _nota van de Reparatie_: Het systeem verhindert nu correct verkoope-mails worden verzonden wanneer de e-mailmededeling wordt onbruikbaar gemaakt. Deze e-mailberichten worden niet meer verzonden wanneer de e-mailcommunicatie opnieuw wordt ingeschakeld. Eerder werden e-mailberichten over verkopen die waren gestart terwijl e-mailcommunicatie was uitgeschakeld, nog steeds verzonden zodra de e-mailcommunicatie opnieuw was ingeschakeld.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Bestelling gesloten zonder volledig terugbetaald
   * _Bevestig nota_: Het systeem handhaaft nu correct de ordestatus als &quot;Verwerking&quot;en de factuurstatus als &quot;In behandeling&quot;wanneer een orde met een niet gevangen betaling een lading heeft gecreeerd. Dit zorgt ervoor dat orders alleen als &#39;Gesloten&#39; worden gemarkeerd nadat ze volledig zijn terugbetaald. Als u eerder een verzending maakt voor een bestelling waarvoor een factuur in behandeling is, wordt de status van de bestelling onjuist gewijzigd in &#39;Gesloten&#39;.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>

### Order, Returns

* _ACP2E-2982_: De teruggaaf van de orde resulteert in dubbele creditnota
   * _nota van de Oplossing_: Het uitgeven van de teruggave over REST API wanneer twee identieke verzoeken gelijktijdig werden uitgevoerd zal niet meer dubbele Kredietmemo&#39;s creëren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>

### Bestelling, belasting

* _ACP2E-3003_: [ CLOUD ] Onjuiste base_row_total in RESTFUL orde API wanneer het toelaten van grensoverschrijdende transacties en het toepassen van couponkortingen
   * _Bevestig nota_: Nu correct base_row_total is teruggekeerd van orde RESTFUL API wanneer de grensoverschrijdende transactie wordt toegelaten en de couponkorting wordt toegepast.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/9af794a4>

### Andere ontwikkelaarsgereedschappen

* _AC-10658_: [ de syntaxisfout van HTML van de kwestie ] verhelpen in visual.phtml
   * _nota van de Reparatie_: Het systeem sluit nu correct de beginmarkering in het visual.phtml- dossier, die juiste syntaxis van HTML verzekeren. Eerder was de begintag niet correct gesloten, waardoor een HTML-syntaxisfout ontstond.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38247>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [ Uitgave ] Gewijzigd &quot;actief&quot;aan &quot;toegelaten&quot;in bin/magento onderhoud:statusbevel
   * _nota van de Reparatie_: Het systeem verstrekt nu nauwkeurigere statusberichten voor het bevel van de onderhoudswijze, veranderend de status van &quot;actief&quot;in &quot;toegelaten&quot;en van &quot;niet actief&quot;aan &quot;gehandicapt&quot;. Eerder werd het statusbericht voor de opdracht voor de onderhoudsmodus weergegeven als &quot;actief&quot; of &quot;niet actief&quot;, wat tot verwarring kan leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38486>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: Het navigeren in de categorienoom leidt tot fouten in Redis: &quot;Redis zitting overschrijdt gezamenlijke verbindingen&quot;
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38851>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0611e750>

### Betalingen

* _ACP2E-2841_: De uitstroom leidt tot nieuwe transactie telkens als wij op het terughaalknoop op het scherm van de meningstransactie klikken
   * _nota van de Reparatie_: Het systeem haalt nu correct transactieinformatie zonder een nieuwe betalingstransactie tot stand te brengen telkens als de haalknoop op het scherm van de meningstransactie wordt geklikt. Als u eerder op de knop Ophalen klikt, wordt een nieuwe betalingstransactie voor een bestelling die al is betaald, onjuist gemaakt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: Het uitbetalende bericht toont niet in PDP voor Canadese paypal handelaarrekening
   * _Nota van de Moeilijke situatie_: Het systeem toont nu correct het PayLater bericht voor de Canadese handelsPAL rekeningen op de Pagina van het Detail van het Product (PDP) wanneer het land van de koper van het rekeningsfactuuradres of de verzending kan worden bepaald. Eerder werd het PayLater-bericht niet weergegeven vanwege een ontbrekende parameter, wat resulteerde in een fout in de browserconsole.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>

### Prestaties

* _AC-12000_: [ geef ] de schoonmaakbeurt van de Code uit en voeg nieuw kritiek hoofdblok toe en beweeg kritieke css vóór activa
   * _nota van de Reparatie_: Het systeem omvat nu een nieuw kritiek hoofdblok en beweegt kritieke CSS vóór activa, die voor meer aanpassing en prestatiesoptimalisering in het frontend toestaan. Eerder werd de kritieke CSS niet geplaatst vóór de activa, die aanpassing en optimaliseringsmogelijkheden beperken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38748>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: De onderbrekingen van de themacompilatie wanneer mysql gastheer haveninformatie bevat
   * _nota van de Reparatie_: Het systeem behandelt nu correct MySQL gastheerconfiguratie die haveninformatie omvat, die succesvolle themacompilatie verzekeren. Eerder, zou de themacompilatie ontbreken als de MySQL gastheerconfiguratie in de gegevensbestandverbinding haveninformatie omvatte.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38799>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38842>
* _ACP2E-2494_: De kwestie van prestaties wanneer het laden van productattributen in kartregels
   * _de nota van de Reparatie_: Verbeterde vraagprestaties voor verkoopregels - van rond 150ms aan enig cijfer ms.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: De gedeeltelijke indexerende prestaties van de prijs
   * _nota van de Reparatie_: De prijs gedeeltelijke indexerende prestaties zijn verbeterd door sommige schrappingsvragen te optimaliseren die binnen het indexeren proces worden gebruikt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: De orde wordt verworpen op multi-store opstelling wanneer het gebruiken van Async-orde verwerking + Voorwaarden en
   * _nota van de Reparatie_: De orden die van niet standaardwebsites met toegelaten termijnen en voorwaarden worden geplaatst worden nu verwerkt.
Voordat ze automatisch werden afgewezen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: De vraag van de Rest API van de orde neemt een lange tijd om uit te voeren
   * _nota van de Reparatie_: Het systeem voert nu de Rest API van de Orde vraag binnen een redelijk tijdsbestek uit, verbeterend de prestaties wanneer het halen van een groot aantal orden. Eerder duurde de aanroep van de Order Rest API veel tijd om te worden uitgevoerd, wat vertragingen optrad bij het ophalen van een groot aantal bestellingen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/001e5188>

### Product

* _wisselstroom-10535_: De speciale karakters in configureerbare associatieve productnaam worden omgezet in de Entiteiten van HTML.
   * _nota van de Reparatie_: Het systeem behoudt nu correct speciale karakters in de namen van bijbehorende producten wanneer het uitgeven van een configureerbaar product, verhinderend hen in de entiteiten van HTML worden omgezet. Eerder werden speciale tekens in gekoppelde productnamen geconverteerd naar HTML-entiteiten toen het configureerbare product werd bewerkt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38146>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: De functie GetById van ProductRepository leidt niet tot de correcte geheim voorgeheugensleutel
   * _nota van de Moeilijke situatie_: Het systeem leidt nu correct tot een geheim voorgeheugensleutel in de functie GetById van ProductRepository, ongeacht of opslag ID als koord of een geheel wordt overgegaan. Dit zorgt ervoor dat het product van geheugen op verdere vraag wordt teruggewonnen, verbeterend prestaties. Eerder, zou het systeem het product van het gegevensbestand terugwinnen telkens als de functie werd geroepen, zelfs met de zelfde parameters, wegens onjuist geheim voorgeheugenzeer belangrijke verwezenlijking.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38384>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [ Uitgave ] [ MFTF ] Toegevoegde AdminClickAddOptionForBundleItemsActionGroup
   * _nota van de Reparatie_: Het systeem omvat nu AdminClickAddOptionForBundleItemsActionGroup, die de functionaliteit van het admin paneel verbetert. Eerder was deze actiegroep niet beschikbaar.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/30857>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/30838>
* _AC-5969_: AlertProcessor - Argument #2 ($storeId) moet van type int zijn, gegeven koord
   * _nota van de Reparatie_: Het systeem brengt nu correct productalarm e-mail door het opslagherkenningsteken van het correcte gegevenstype te verzekeren in werking. Eerder werden de e-mails met productwaarschuwingen niet verzonden omdat het type niet overeenkomt met de winkel-id.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/35602>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: [ de functie van de Wolk ] addFilterToMap werkt niet voor bepaalde kolommen
   * _nota van de Reparatie_: Nu, kan de douanemodule in het orderaster worden gebruikt. Eerdere fouten zijn opgetreden tijdens het gebruik van een aangepaste module.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3a7c4d17>

### Aanbieding

* _ACP2E-2602_: Kenmerk van de klant niet zichtbaar wanneer het creëren van rekening van uitnodiging
   * _nota van de Reparatie_: De attributen van de klant zijn beschikbaar terwijl het creëren van rekening van uitnodiging.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: De code van de coupon met Gebruik per grens van de Coupon wordt niet vrijgegeven voor betaling ontbrak met orde annuleren
   * _nota van de Reparatie_: Het systeem werkt nu onmiddellijk coupongebruik bij wanneer een orde wordt gecreeerd of geannuleerd, en voegt regelgebruikers aan een rij toe om potentiële implantaties te verhinderen. Dit zorgt ervoor dat een couponcode met de limiet &quot;Gebruik per coupon&quot; wordt vrijgegeven en opnieuw kan worden gebruikt als een order wordt geannuleerd vanwege een mislukte betaling. Eerder heeft het systeem de couponcode niet vrijgegeven voor hergebruik in dergelijke gevallen, wat resulteerde in een foutbericht waarin stond dat de couponcode niet geldig was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [ Cloud ] het Reindexeren van het Product van de Regel van de Catalogus meldt SQLSTATE [ HY000 ]: Algemene fout: De server van 2006 MySQL is weggegaan.
   * _nota van de Reparatie_: Het systeem behandelt nu correct douane &quot;batchCount&quot;waarde in di.xml voor &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, die SQL fouten zoals &quot;Algemene fout verhinderen: De server van 2006 MySQL is weggegaan&quot;tijdens het opnieuw indexeren van het Product van de Regel van de Catalogus wegens de onjuiste partijgrootte op grote catalogi
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>

### SEO

* _AC-11907_: Het toevoegen van URL herschrijft met een accent veroorzaakt oneindig laden
   * _nota van de Reparatie_: Het systeem leidt nu met succes tot en functioneert URL herschrijft met accenten, verhinderend oneindig ladend tijdens het besparingsproces. Eerder veroorzaakte het toevoegen van een URL voor herschrijven met een accent een oneindig ladingsprobleem.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38692>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/44cef3a9>
* _ACP2E-2641_: De multiVerkeerde categorie van de Opslag rl-herschrijft voor derde niveaucategorie
   * _Bevestig nota_: Produceer correcte url herschrijft voor kinderen met ouder met douane scoped url sleutel
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2770_: De karakters van dubbel-byte (speciale karakters) in de gebiedsblokken van de Naam van het Product productverwezenlijking in achterste eind
   * _nota van de Reparatie_: Een nieuwe het plaatsen is toegevoegd die u toestaat om vertaliteratie op productURL al dan niet toe te passen. Instelling is hier beschikbaar: Storingen > Configuratie > Catalogus > Catalogus > Optimalisatie van zoekprogramma&#39;s: &quot;Transliteratie toepassen voor product-URL&quot;
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>

### Beveiliging

* _AC-11762_:
   * _Nota van het Repareren_: Werk 2FA OTP venstergebied met correcte beschrijving en standaardwaarde na verandering BiC bij
   * _GitHub codebijdrage_: Bijgewerkt bevel voor de manier hoe de periode otp_window van nu bin/magento config zal zijn ingegaan:plaats twee factorauth/google/otp_window VALUE
naar bin/magento config:set two factorauth/google/leeway VALUE
* _AC-11855_: [ Uitgave ] Ontbrekende CSP van de Dooppop-up van het Font
   * _nota van de Reparatie_: Het systeem staat nu het laden van doopvont &quot;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; toe zonder de richtlijn van het Beleid van de Veiligheid van de Inhoud te overtreden, die de correcte vertoning van de Pop van de Paylater verzekert. Eerder werd het lettertype niet geladen vanwege een schending van de Content Security Policy-richtlijn, wat weergaveproblemen met de Paylater Popup veroorzaakte.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38624>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37401>
* _AC-11937_:
   * _Nota van het Repareren_: Werk 2FA OTP venstergebied met correcte beschrijving en standaardwaarde na verandering BiC bij
   * _GitHub codebijdrage_: Bijgewerkt bevel voor de manier hoe de periode otp_window van nu bin/magento config zal zijn ingegaan:plaats twee factorauth/google/otp_window VALUE
naar bin/magento config:set two factorauth/google/leeway VALUE
* _AC-12309_:
   * _Bevestig nota_: De documentatie van de gebruiker van de update voor twee-factor authentificatie (2FA) aan veranderings pop_window bevel
   * _de codebijdrage van GitHub_: De gebruikersdocumentatie van de update voor twee-factor authentificatie (2FA) om OTP_WINDOW montagesbevel te veranderen zoals per: https://jira.corp.adobe.com/browse/AC-11762

### Verzending

* _AC-10757_: [ Vaste typefout van de kwestie ] in tracking.phtml - anders genoemd JS-functies &quot;currier&quot;aan &quot;drager&quot;
   * _nota van de Reparatie_: Het systeem gebruikt nu correct de term &quot;drager&quot;in plaats van de verkeerd gespelde &quot;currier&quot;in de de handlerfuncties van JavaScript die in het orde volgende malplaatje worden gebruikt, die correcte functienaam en codeduidelijkheid verzekeren. Voorheen werd de verkeerd gespelde term &quot;currier&quot; gebruikt, wat tot verwarring en inconsistentie in de codebase kan leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/34523>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/33414>
* _AC-11811_:
   * _Nota van de Moeilijke situatie_: UPS REST &quot;een verzending kan geen KGS/IN of LBS/CM of OZS/CM als zijn eenheid van metingen hebben&quot;
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/9b1713d8>>
   * _GitHub codebijdrage_: De tarieven van UPS zijn zichtbaar in controle en kart.
* _AC-11916_:
   * _Bevestig nota_: [ QPT ] UPS REST &quot;Een verzending kan KGS/IN of LBS/CM of OZS/CM als zijn eenheid van metingen niet hebben&quot;
   * _GitHub codebijdrage_: De tarieven van UPS zijn zichtbaar in controle en kart.
* _AC-11938_: UPS REST &quot;Een verzending kan geen KGS/IN of LBS/CM of OZS/CM als zijn eenheid van metingen hebben&quot;
   * _nota van de Reparatie_: Zorg aan de tarieven van UPS in controle en kart zichtbaar zouden moeten zijn.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38618>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-11983_:
   * _Bevestig nota_: [ QPT ] UPS REST &quot;Een verzending kan KGS/IN of LBS/CM of OZS/CM als zijn eenheid van metingen niet hebben&quot;
   * _GitHub codebijdrage_: De tarieven van UPS zijn zichtbaar in controle en kart.
* _AC-11984_:
   * _Bevestig nota_: [ QPT ] UPS REST &quot;Een verzending kan KGS/IN of LBS/CM of OZS/CM als zijn eenheid van metingen niet hebben&quot;
   * _GitHub codebijdrage_: De tarieven van UPS zijn zichtbaar in controle en kart.
* _ACP2E-2738_: Het volgen Venster die onjuiste Verwachte Datum van de Levering tonen
   * _nota van de Reparatie_: De correcte Datum van de Levering van de vertoning voor de Drager van de Verkoop van de Verkoop van de Verkoop.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: De Tarieven van de lijst die nog tonen hoewel de Vrije verscheping wordt toegepast
   * _Nota van de Reparatie_: De het verschepen methode van het Tarief van de lijst wordt nu getoond zelfs als de Vrije Verzending na coupon het toepassen beschikbaar wordt
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF test AdminCreatingShippingLabelTest die als gevolg van geloofsbrieven niet in milieu Jenkins wordt toegevoegd
   * _nota van de Reparatie_: mftf testmoeilijke situatie
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Targeting

* _wisselstroom-9432_: [ Uitgave ] staat gebruik van CIDR waaiers in onderhoudscategorie toe in lijst van gewenste personen
   * _nota van de Reparatie_: Het systeem steunt nu het gebruik van CIDR waaiers op de onderhoudswijze staat IP lijst toe, toelatend een waaier van IP adressen om onderhoudswijze te mijden. Eerder, staat de onderhoudswijze IP lijst slechts toegelaten individuele IP adressen toe om onderhoudswijze te mijden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37943>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/30699>

### Testkader

* _AC-11491_:
   * _Bevestig nota_: [ Skip ] moet de test van de Integratie zijn niet-overslaan
   * _GitHub kwestie_: &lt;<https://github.com/magento/magento2/commit/493e01f5>>
   * _GitHub codebijdrage_: Un-overslaat alle integratietest die in dit PR - https://github.com/magento-commerce/magento2ce/pull/8811/ wordt overgeslagen
* _AC-11654_: De test van de integratie faalt testDbSchemaUpToDate toe te schrijven aan JSON kolomtype
   * _nota van de Reparatie_: Het systeem erkent nu correct JSON kolomtypes in het gegevensbestandschema tijdens integratietests, die testmislukkingen wegens een wanverhouding tussen het gegevensbestandschema en het verklarende schema verhinderen. Eerder, identificeerde het systeem verkeerd JSON kolomtypes als LONGTEXT in MariaDB, veroorzakend integratietests om te ontbreken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ef81f5a2>

### UI Framework

* _AC-12128_: De veiligheidskwetsbaarheid van Prototype.js moeilijke situatie CVE-2020-27511
   * _nota van de Reparatie_: Het systeem is bijgewerkt om de veiligheidskwetsbaarheid CVE-2020-27511 in Prototype.js 1.7.3 te richten, die de algemene veiligheid van het systeem verbetert. Voorafgaand aan deze update was het systeem gevoelig voor een Regular Expression Denial of Service (ReDOS) via gestripte HTML-tags.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt minder gebruikspubs/prefix voor broncemaps
   * _nota van de Reparatie_: Het systeem produceert nu minder/css broncemaps zonder de /pub prefix voor wegen wanneer het gebruiken van steen, die de behoefte aan een tijdelijke oplossing in de configuratie van de webserver elimineren. Eerder, vereiste het gebruik van het prefix /pub in broncemaps wegen een specifieke configuratie in de webserver om correct te functioneren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38837>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38840>
* _AC-1306_: De statische inhoud stelt voor gehandicapte modules op
   * _nota van de Reparatie_: Het systeem sluit nu CSS met betrekking tot gehandicapte modules van de definitieve CSS outputdossiers uit, die ervoor zorgen dat de onnodige stijlen niet worden geladen. Eerder werden CSS met betrekking tot uitgeschakelde modules opgenomen in de uiteindelijke CSS-uitvoerbestanden, wat leidde tot het laden van extra, onnodige stijlen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/24666>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32922>
* _AC-9007_: [ Uitgave ] laadt geen backend blokcontext op frontend
   * _nota van de Reparatie_: Het systeem zorgt nu ervoor dat de achtergrondblokcontext niet op het front wordt geladen, verhinderend de verwezenlijking van onnodige achterste zittingen en potentiële zittingssloten. Eerder, laadde het systeem verkeerd de achtergrondblokcontext op het front-end, die tot de verwezenlijking van achterste deelzittingen en potentiële zittingssloten leidde.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37617>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36368>
* _ACP2E-2529_: Uitzondering wanneer het controleren van een saldo van de giftekaart wanneer Recaptcha wordt toegelaten
   * _nota van de Reparatie_: De gebruikers zullen geschenkkaartsaldo in de mening kunnen halen en het kaartscherm uitgeven. Eerder werden deze details niet weergegeven terwijl reCAPTCHA ingeschakeld was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [ CLARIFICATION ] het Verzoek van de Eigenschap ADA Naleving
   * _nota van de Reparatie_: Het systeem verzekert nu naleving ADA door niet gesteunde CSS eigenschappen te verwijderen en hen te vervangen met gesteunde degenen in het print.css- dossier. Eerder leidde het gebruik van niet-ondersteunde CSS-eigenschappen tot browsercompatibiliteitsproblemen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [ de bibliotheekcode van de Wolk ] van de Verzekering in effect-drop.js van AC 2.4.4-p8
   * _nota van de Reparatie_: Het systeem voert nu correct de effect-drop.js bibliotheek uit, die het juiste functioneren van gevolgen jQuery UI verzekeren. Eerder werd de bibliotheek effect-drop.js per ongeluk overschreven met de bibliotheek effect-clip.js, wat potentiële problemen met de gevolgen van jQuery UI veroorzaakte.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>
