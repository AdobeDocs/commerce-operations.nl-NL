---
source-git-commit: 62b6501fc2ba595146bf7f38a7d3352ef02be1a0
workflow-type: tm+mt
source-wordcount: '26051'
ht-degree: 0%

---
# Magento Open Source-releaseopmerkingen (v2.4.8)

## Hooglichten

De volgende 31 markeringen zijn van toepassing op de Magento Open Source 2.4.8-release.

### Kader

* _AC-10721_: Bevorder de ligging/de gebiedsdelen van de Samensteller van het vliegsysteem die aan recentste versie worden bevorderd
   * _Bevestig nota_: Bevorder de 2.x liga/de gebiedsdelen van de Composer van het vluchtsysteem aan recentste versie 3.x
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/91cb4d46>
* _AC-11673_: Onderzoek php-amqplib/php-amqplib recentste versies
   * _nota van de Reparatie_: Bijgewerkt de recentste versie php-amqplib/php-amqplib:^3.x
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-11911_: jQuery/fileuploader css schoonmaakbeurt na migratie aan uppy bibliotheek
   * _Nota van de Oplossing_: Verwijderd jQuery/fileUploader bibliotheek omdat het aan de bibliotheek van het Uppy is gemigreerd
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7cabfb46>
* _AC-11995_: Voeg verenigbaarheid met MySQL 8.4 LTS voor Magento CE toe
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/672a2e61>
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
* _AC-12165_: Abonnees Optimalisatie - PhpUnit10
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/90e25b6b>
* _AC-12267_: Ondersteuning voor het opnieuw proberen van verbindingen voor Redis-sessies en compatibel met colinmollenhour/php-redis-session-abstract v2.0.0
   * _Fix note_: Bijgewerkte nieuwste versie van colinmollenhour/php-redis-session-abstract v2.0.0 compatibel met Adobe Commerce
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12576_: Onderzoek de fouten in automatiseringstests met MySQL 8.4 LTS
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/672a2e61>
* _AC-12595_: voeg verenigbaarheid met MariaDB 11.4 LTS voor EE toe
   * _Bevestig nota_: Toegevoegde MariaDB 11.4 steun met Adobe Commerce en uitbreidingen
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12715_: De gebiedsdelen van de composer van de update laminas bevorderen aan recentste versie
   * _nota van de Reparatie_: Het systeem steunt nu de recentste versies van laminas composer gebiedsdelen:
laminas/laminas-servicemanager
laminas/laminas-server
laminas/laminas-stdlib
laminas/laminas-validator
zorgen voor compatibiliteit en up-to-date functionaliteit. Eerder, kon het bijwerken aan de recentste versies van deze gebiedsdelen achterwaartse onverenigbaarheidskwesties en testmislukkingen veroorzaken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-12823_: Onderzoek de mislukking van de eenheidstest toe te schrijven aan phpunit flardupdate tijdens componentenverbetering
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-13076_: [ Deel 1 ] - werk alle js bibliotheek en npm gebiedsdeel met recentste beschikbare versie bij
   * _nota van de Reparatie_: De steun van de componentenversie was tot composer slechts versie 2.2.x. De ondersteuning is nu ook uitgebreid naar versie 2.4.x.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/19844aa0>

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
* _AC-13448_: Lever de verbetering van de laag-prijs verrichtingenprestaties in 2.4.8
   * _Nota van de Oplossing_: Het systeem staat nu voor efficiëntere bulkupdates van rijprijzen toe zonder prestatieskwesties of plaats onontvankelijkheid te veroorzaken wanneer het gebruiken van het &quot;/V1/products/laag-prijzen&quot;REST API eindpunt. Eerder, kon het bijwerken van een groot aantal prijzen gebruikend dit eindpunt in prestatieskwesties en plaatsonontvankelijkheid resulteren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/082d981c>
* _AC-13550_: Verwijder alle vertrouwelijke de copyrightberichten van Adobe uit de bewaarplaatsen van Magento Open Source
   * _Fix-opmerking_: alle vertrouwelijke auteursrechtvermeldingen van Adobe zijn verwijderd uit de open source-repositories, zodat alleen de beperkte vorm van Adobe-auteursrecht wordt gebruikt. Voorheen bevatten sommige bestanden in de openbare opslagplaatsen vertrouwelijke auteursrechtvermeldingen van Adobe, wat leidde tot escalaties van de community.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39493>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/4bca5dfe>

### UI-kader

* _AC-12726_: [2.4.8-beta1] TinyMCE 5 migratie naar TinyMCE 7
   * _Nota van de Reparatie_: Gegigreerde TinyMCE 5 aan TinyMCE 7.3.0 om een gesteunde versie voor Adobe Commerce te zijn, vroeger gebruikte het systeem 5.10.2 die verouderd was en veiligheidskwetsbaarheid rapporteerde
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12825_: [ 2.4.8-bèta1 ] TinyMCE 5 migratie aan TinyMCE 7 de Bouwer van de Pagina
   * _Fix-opmerking_: TinyMCE 5 gemigreerd naar TinyMCE 7.3.0 als een ondersteunde versie voor Adobe Commerce, voorheen gebruikte het systeem 5.10.2 die verouderd was en een beveiligingslek meldde
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12844_: [2.4.8-beta1] TinyMCE 5 migratie naar TinyMCE 7 - Magento2-infra - verboden woorden
   * _Nota van de Reparatie_: Gegigreerde TinyMCE 5 aan TinyMCE 7.3.0 om een gesteunde versie voor Adobe Commerce te zijn, vroeger gebruikte het systeem 5.10.2 die verouderd was en veiligheidskwetsbaarheid rapporteerde
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/edcd0dcc>
* _AC-12901_: Require.js upgrade naar de nieuwste versie 2.3.7 (beveiligingslek CVE-2024-38999)
   * _Fix-opmerking_: require.js bijgewerkt naar de nieuwste versie 2.3.7. In vorige versie gemeld beveiligingslek
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/b34c0a75>

## Opgeloste problemen

We hebben 497 problemen opgelost in de Magento Open Source 2.4.8 kerncode. Een subset van de opgeloste problemen in deze release wordt hieronder beschreven.

### Apis

* _AC-10042_: /V1/de transacties REST API keert fout terug wanneer parent_txn_id = txn_id
   * _nota van de Reparatie_: Het systeem behandelt nu correct de ouder en kindconcepttransacties waar identiteitskaart van de oudertransactie het zelfde als transactieidentiteitskaart is, verhinderend een oneindige lijn wanneer het vragen van het /V1/transacties REST API eindpunt. Eerder zou dit scenario resulteren in een fatale fout als de maximale uitvoeringstijd wordt overschreden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [ Grafiek ] de kwestie van het Type in 2.4.7
   * _nota van de Reparatie_: Het systeem behandelt nu correct geheelwaarden in de functie GetCustomSelectedOptionAttributes wanneer het uitvoeren van een vraag van GraphQL, die om het even welke op type betrekking hebbende fouten verhinderen. Eerder resulteerde het lanceren van een vraag van GraphQL die GetCustomSelectedOptionAttributes met een geheelargument gebruikte in een typefout.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38662>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38663>
* _AC-3223_: Speciale karakters in categorie url_key (wanneer gecreeerd via REST API)
   * _nota van de Reparatie_: Eerder in category_url_key speciaal karakter is daar niet na de moeilijke situatie het speciale karakter in category_url_key toont
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/35577>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2755_: De kwestie met rest api na toelaat 2FA Duo
   * _Nota van de Reparatie_: 2FA met Duo veiligheidsoptie produceert nu correcte handtekening voor Rest API
   * _GitHub codebijdrage_: <https://github.com/magento/security-package/commit/412fa642>
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
* _ACP2E-3236_: De verrichting van Async ontbreekt wanneer SKU van de lading mist
   * _nota van de Reparatie_: Async en synchroniseer eerder ontbroken verrichtingen wegens product sparen fouten als de sku van nuttige lading mist. Na de correctie mislukken de async en synchronisatieproduct de verrichtingen van de steunAPI met relevant uitzonderingsbericht.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [ CLOUD ] Onbekwaam om de basis-prijzen bij te werken gebruikend REST API (de waarde van &quot;value_id&quot;in &quot;catalog_product_entity_decimal&quot;wordt niet correct verhoogd.)
   * _nota van de Reparatie_: Eerder aan deze moeilijke situatie, toen rustapi /rest/default/V1/products/base-pricing werd geroepen, verhogingsidentiteitskaart werd verkeerd verhoogd verlatend een hiaat tussen waarden. Na de correctie wordt de increment id verhoogd, incrementeel. Ook het value_id-veldbereik is vergroot.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_: De punten van de orde zijn niet zichtbaar in creditmemo e-mails voor de API POST V1/order/:orderId/restitutie
   * _nota van de Reparatie_: Eerder, vóór deze moeilijke situatie, wanneer een klant een creditnota van een API verzoek creeert die send_email op de hoogte brengt, bevat het niet het net van de productdetails. Na deze correctie stuurt de klant een API-aanvraag voor creditnota en zoekt hij naar de gegevens van het product die in de e-mail worden weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3486_: Standaardwaarden zijn niet ingesteld voor datum- en tijdkenmerken met producten RestAPI
   * _Fix-opmerking_: standaardwaarden zijn nu correct ingesteld voor datum-, datum- en tijdkenmerken via RestAPI
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1984c61c>

### API&#39;s, winkelwagen en afrekenen

* _ACP2E-3343_: Kritieke 500-fout: Magento\Framework\Webapi\Exception met betrekking tot HTTP-header accepteren
   * _Fix-opmerking_: Na de fix is er geen probleem met het opgeven van de &quot;Accept&quot;-header.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1366ae5e>

### Account

* _AC-10782_: Het adresvorm van de klant staat willekeurige code op de naamgebieden toe
   * _nota van de Reparatie_: Het systeem bevestigt nu de input in de gebieden Voornaam en Achternaam in de vorm van het klantenadres, die het gebruik van willekeurige code verhindert. Eerder stond het systeem het gebruik van willekeurige code in deze gebieden toe zonder een fout te werpen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38331>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38345>
* _AC-10886_: admin Wachtwoord update.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38352>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_: mijn account adres toevoegen crash bij opslaan
   * _nota van de Reparatie_: Het systeem bewaart nu correct klantenadressen zelfs wanneer het gebiedgebied niet wordt getoond, verhinderend een neerstorting tijdens het sparen proces. Als u eerder een adres probeert toe te voegen of te bewerken zonder veld voor een weergegeven gebied, treedt er een uitzonderingsfout op.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38406>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38407>
* _AC-11718_: Richt lijn opnieuw wanneer URL in hoofdletters heeft
   * _nota van de Reparatie_: Het systeem zet nu automatisch karakters in hoofdletters in URLs in kleine letters om, die een herleidingslijn verhinderen wanneer het toegang tot van homepage. Voorheen veroorzaakte het hebben van hoofdletters in de Secure Base-URL een continue omleidingslus wanneer u probeerde toegang te krijgen tot de startpagina.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38538>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38539>
* _AC-11755_: middlename (&#39;s) niet bewaard voor gastrekeningen
   * _nota van de Reparatie_: Het systeem bewaart nu correct de middennaam voor gastrekeningen tijdens controle, die het in het e-mailmalplaatje toegankelijk maken. Voorheen werd de middelste naam niet opgeslagen in de offertetabel en was deze niet toegankelijk in de e-mailsjabloon voor gastaccounts.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38593>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/39067>
* _AC-11919_: Admin: Pagina-acties Knoppen zweven naar links in plaats van naar rechts
   * _Fix-opmerking_: het systeem lijnt nu de pagina-actieknoppen correct uit aan de rechterkant van de sticky header in het beheerderspaneel, waardoor de professionele look en feel wordt verbeterd. Voorheen zweefden deze knoppen ten onrechte naar de linkerkant van de sticky header.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38701>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: dev :di: infofout in magento 2.4.7
   * _nota van de Reparatie_: Het systeem toont nu correct constructorparameters wanneer het uitvoeren van het dev :di: info bevel, verhinderend om het even welke fouten voor te komen. Eerder resulteerde het uitvoeren van deze opdracht in een fout als gevolg van een niet-overeenkomend type in het argument.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38740>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_: Login als klant opt-in checkbox niet vertaalbaar
   * _Fix-opmerking_: het systeem staat nu toe dat de velden &quot;Inloggen als klant opt-in checkbox&quot; en &quot;Inloggen als klant&quot; tooltip worden ingesteld op het bereik &quot;Winkelweergave&quot;, waardoor vertalingen voor verschillende winkelweergaven mogelijk zijn. Voorheen werden deze velden alleen ingesteld in het bereik &quot;Website&quot;, waardoor vertalingen voor individuele winkelweergaven werden voorkomen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/32329>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32359>
* _AC-6071_: De klant wordt het programma geopend maar het tonen van 404 fout in front-end.
   * _nota van de Reparatie_: De storefront klantendashboardpagina laadt nu zoals verwacht wanneer een klant het programma opent. Eerder konden klanten zich aanmelden, maar op deze pagina werd een fout van 404 weergegeven. [ GitHub-35838 ](https://github.com/magento/magento2/issues/35838)
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/35838>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: Kan de attributeninformatie van de Klant niet opslaan in Admin geeft klantensectie uit;
   * _nota van de Oplossing_: De opslag identiteitskaart van de klant wordt nu behoorlijk uitgevoerd per websitewerkingsgebied voor de beheerder klant geeft vorm uit.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3329_: Na het programma openen, zijn de producten die aan de vergelijkingslijst als gastgebruiker worden toegevoegd niet zichtbaar.
   * _Bevestig nota_: De producten die aan product werden toegevoegd vergelijken lijst alvorens het programma te openen als klant worden nu bewaard na het programma openen.
Eerder waren de producten die als gastgebruiker aan de vergelijkingslijst werden toegevoegd, na het aanmelden niet zichtbaar.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: Sta de configuratiekwesties van Landen in de configuraties van het klantenadres toe
   * _nota van de Reparatie_: Nu het selecteren staat de configuratie van Landen toe beïnvloedt geen landen die voor buiten het bepaalde werkingsgebied worden getoond. Eerder toestaan de configuratie van Landen beïnvloedde klantenadresattributen buiten bepaald werkingsgebied
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3501_: VAPT: De Fout van de BedrijfsLogica - de datum van de toekomst als klantengeboortedatum
   * _Nota van de Moeilijke situatie_: De geboortedatum van de klant kan niet later dan vandaag worden geplaatst
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d4de4726>

### Account, API&#39;s, GraphQL

* _ACP2E-3246_: Klant API - Login Aantal mislukte aanmeldingen kan niet aan 0 terugstellen na succesvolle aanmelding
   * _nota van de Reparatie_: Nu wordt het mislukkingsaantal teruggesteld aan nul in de lijst van de klantenentiteit na succesvolle login door API eindpunten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Account, beheerinterface, B2B

* _ACP2E-3038_: De beperkte admin gebruikers kunnen niet altijd douane gedeelde catalogi zien
   * _nota van de Reparatie_: De beperkte admin gebruikers kunnen klanten en alle gedeelde catalogi nu consequent bekijken en beheren waaraan de producten worden toegewezen, op voorwaarde dat zij toegang tot de specifieke opslag hebben. Eerder, kon een beperkte admin gebruiker met toegang tot een bepaalde opslag niet altijd alle gedeelde catalogi zien waaraan de producten werden toegewezen of konden klanten zien die niet konden sparen, leidend tot inconsistenties in het systeem.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>

### Account, winkelwagentje en Afhandeling

* _AC-2341_: &quot;uitgezocht&quot;attribuut van het douaneadres van de klant geeft niet voor nieuw klantenadres terug
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/34950>

### Gebruikersinterface van beheerder

* _AC-10705_: [ Uitgave ] voegt toestemmingscontrole voor &quot;herladengegevens&quot;gegevensknoop toe
   * _nota van de Reparatie_: Het systeem omvat nu een toestemmingscontrole voor de &quot;knoop van Gegevens&quot;opnieuw laden, die ervoor zorgt dat het slechts voor gebruikers met de aangewezen toestemmingen wordt getoond en toegankelijk. Eerder was de knop &quot;Gegevens opnieuw laden&quot; zichtbaar en klikbaar voor alle gebruikers. Dit leidde tot een pagina &quot;niet toegestaan&quot; wanneer gebruikers zonder de vereiste machtigingen op deze pagina hadden geklikt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38283>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38279>
* _AC-11427_: [Inconsistente labels uitgeven] voor kenmerken in marketingregels
   * _Fix-opmerking_: het systeem vult de labels nu correct in voor categorie- en kenmerkopties in de prijsregel voor winkelwagentjes
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/31232>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/31231>
* _AC-11588_: De bevestiging van gegevens is succes en de knoop van de Invoer is aanwezig tijdens de producten van de Invoer met het gedrag van de Vervangen
   * _nota van de Reparatie_: Het systeem bevestigt nu correct gegevens en verbergt &quot;de knoop van de Invoer&quot;tijdens het proces van de productinvoer met &quot;vervangt&quot;gedrag, dat om het even welke onbedoelde gegevensvervanging verhindert. Eerder heeft het systeem de gegevens onjuist gevalideerd en de knop Importeren weergegeven. Dit leidt tot mogelijke inconsistenties in de gegevens.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [ Bug ] Magento 2.4.7 staat geen productfoto&#39;s met de uitbreiding van het hoofdletterdossier toe.
   * _nota van de Reparatie_: Het systeem keurt nu productbeeld toe uploadt met de uitbreidingen van het hoofdletterdossier, die een vlot proces verzekeren van de productverwezenlijking. Eerder werd het uploaden van afbeeldingen met bestandsextensies voor hoofdletters geweigerd, waardoor gebruikers gedwongen werden de bestandsextensie te wijzigen in kleine letters.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38831>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_: Verborgen dropdown in netten met uitgezochte actie (b.v. Inhoud > Elementen > Pagina&#39;s)
   * _nota van de Reparatie_: Nu is het systeem al gelijkaardige dropdown voor alle netten hersteld.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38891>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39371>
* _wisselstroom-13131_: [ de Waarschuwing van het Correct van de Uitgave ]: Onbepaalde seriesleutel &quot;filters&quot;
   * _nota van de Reparatie_: Het systeem behandelt nu scenario&#39;s waar een nieuwe gebruiker nog niet met referenties heeft gecommuniceerd, verhinderend een ongedefinieerde serie zeer belangrijke &quot;filters&quot;waarschuwing wordt geregistreerd. Deze waarschuwing zou eerder worden geregistreerd als een nieuwe gebruiker geen interactie had gehad met bladwijzers.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39013>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: Het invoer csv- dossier van het product met speciale karakters ontbreekt toe te schrijven aan codeveranderingen in Validate.php- dossier
   * _nota van de Reparatie_: Het systeem bevestigt nu correct en voert productCSV- dossiers in die speciale karakters bevatten, die voor succesvolle gegevensoverdracht toestaan. Als u voorheen een CSV-bestand met speciale tekens importeerde, treedt er een fout op, waardoor het importproces niet meer kan plaatsvinden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13850_: Er is geen rode asterisk voor verplicht gebied van het telefoonaantal
   * _nota van de Reparatie_: De vroegere rode asterisk toonde niet voor telefoonaantal maar  Telefoonnummer was verplicht. Dit is nu een vast rood sterretje dat op telefoonnummer als een verplicht veld kan worden weergegeven.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/c699c206>
* _AC-6975_: [Probleem] Stel de standaardindexeermodus in op &#39;schema&#39;
   * _Fix-opmerking_: alle nieuwe indexeerfuncties staan standaard in **[!UICONTROL Update by Schedule]** de modus.  Eerder was de standaardmodus **[!UICONTROL Update on Save]** . Dit heeft geen invloed op bestaande indexen. [ GitHub-36419 ](https://github.com/magento/magento2/issues/36419)
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36419>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0b410856>
* _wisselstroom-7700_: [ ] het veranderingslijsten van de Daling van de indexator op mening unsubscribe
   * _nota van de Reparatie_: Het systeem verwijdert nu automatisch ongebruikte veranderingslijsten wanneer een index van &quot;update op programma&quot;aan &quot;update op sparen&quot;wordt geschakeld, die de index als ongeldig markeren om ervoor te zorgen geen ingangen worden gemist. Als een index eerder werd overgeschakeld op &#39;bijwerken bij opslaan&#39;, blijven wijzigingstabellen die niet worden gebruikt in het systeem behouden en worden alle gewijzigde indexen &#39;geldig&#39; gemarkeerd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/29789>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/25859>
* _AC-7962_: Geen verbinding aan het verschepen wanneer in betalingen in controle in mobiele telefoonmening
   * _Bevestig nota_: Het systeem zorgt nu ervoor dat de controletitels/de verbindingen &quot;Verzending&quot;en &quot;Overzicht &amp; Betalingen&quot;altijd vóór de pagina in mobiele mening zichtbaar zijn, toestaand gebruikers om tussen stappen gemakkelijk te navigeren en noodzakelijke correcties te maken. Eerder waren deze titels/koppelingen verborgen in de mobiele weergave, waardoor het voor gebruikers moeilijk was om hun huidige stap te kennen of terug te gaan naar vorige stappen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36856>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: de vraag van de klant geeft vraagverzendcommentaren aan gecreeerde_bij is teruggekeerd in +0 timezone niet in opslag gevormde timezone
   * _nota van de Reparatie_: Het systeem toont nu correct het &quot;created_at&quot;gebied van ladingscommentaren in gevormde tijdzone van de klant wanneer het gebruiken van de vraag van de Orden van de klant. Eerder, werd het &quot;created_at&quot;gebied getoond in +0 timezone, ongeacht de gevormde timezone van de klant.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36947>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37642>
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
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2-page-builder/commit/60140cd2>, <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_: Product opslaan door een admin-gebruiker met een ander rolbereik overschrijft/verwijdert bestaande gerelateerde productinformatie in het product
   * _nota van de Reparatie_: Eerder, vóór de moeilijke situatie, werden de verwante producten teruggesteld en leeg geworden wanneer de secundaire admin gebruiker op sparen knoop klikte zonder in verwant product te veranderen. Na deze oplossing klikt de secundaire beheerder op de knop Opslaan en wordt het product niet gereset en wordt het opgeslagen
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
* _ACP2E-3294_: De het verschepen adresstaat is niet auto het bijwerken
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie, was het verschepende adresgebied (of gebied identiteitskaart) niet synchroon met de adres het factureren informatie. Nu worden zowel het verzendadres als de regio-id correct bijgewerkt wanneer het factuuradres wordt gewijzigd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: De knoop van het Terugstellen werkt niet op Add/geeft admin gebruiker uit
   * _nota van de Reparatie_: Eerder, werkte de knoop van het Terugstellen niet op Add/geef Admin pagina van de Gebruiker uit. Nu werkt de knop Herstellen in het deelvenster Beheer onder Systeem -> Machtigingen -> Alle gebruikers correct op de pagina Admin-gebruiker toevoegen/bewerken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_: Magento admin URL die onjuiste opsporing en fouten CORS verplettert
   * _nota van de Reparatie_: Na de moeilijke situatie, als het douane admin domein een subdomein van het belangrijkste domein is, is admin toegankelijk slechts van gevormde subdomain.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37663>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3392_: Gebroken bevestiging voor &quot;Maximale Aantal Toegestaan in het Schepen Kar&quot;
   * _nota van de Reparatie_: Eerder, wanneer wij `Maximum Qty Allowed in Shopping Cart` leeg zetten, veroorzaakte het geen uitzondering, hoewel een lege waarde hier niet wordt goedgekeurd. Nadat deze correctie is toegepast, genereert het plaatsen van een lege tekenreeks uitzonderingen en wordt het opslaan van het product niet meer toegestaan.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [Probleem met] de gebruikersinterface van Pagebuilder Preview De knoppen in de kolom Page Builder worden niet correct uitgelijnd
   * _Fix-opmerking_: de knoppen in de kolommen van Page Builder zijn nu correct uitgelijnd. Eerder waren ze verkeerd uitgelijnd in de kolommen van de Page Builder.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/1a52ef4c>
* _ACP2E-3431_: Het geordende rapport van producten voert niet uit. 404 fout.
   * _nota van de Reparatie_: De producten geordende rapportuitvoer naar CSV en XML werken nu zoals verwacht
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3457_: De Fout van TinyMCE JS in console na Js minification laat met productiemodus toe
   * _nota van de Reparatie_: Eerder, toelatend JavaScript minificatie op productiemodus binnen het admin paneel veroorzaakte de fouten van JavaScript met betrekking tot TinyMCE 6 om in browser console te verschijnen, die de functionaliteit en gebruikerservaring beïnvloedt. Dit probleem is nu opgelost en zorgt ervoor dat TinyMCE 6 probleemloos werkt zonder fouten te genereren, zelfs als JS-minificatie is ingeschakeld.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Verzoek om extra veranderingen om ACS2E-3375 moeilijke situatie volledig te voltooien
   * _Bevestig nota_: &quot;-
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3503_: Automatisch toelatend van nieuwe ACL toestemmingen
   * _de nota van de Reparatie_: De nieuwe toestemmingen die aan douanemodules worden toegevoegd zullen automatisch geen toegang tot alle bestaande gebruikersrollen verlenen tenzij uitdrukkelijk gevormd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3509_: Het Rapport van de Gebruiker van het Logboek van Acties Admin toont geen details voor adminhtml_user_delete
   * _Fix-opmerking_: de adminhtml_user_delete registreert nu correct belangrijke details. Voorheen werden er geen logboeken gegenereerd voor het verwijderen van gebruikers.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_: Winkelwagenregel met verzendvoorwaarde die niet van toepassing is bij het plaatsen van een bestelling door de beheerder
   * _nota van de Reparatie_: Eerder, als de regel van de kartprijs een het verschepen methodekorting met de coupon heeft, kan het niet door Admin UI worden toegepast. Nadat deze correctie is toegepast, wordt de korting op de winkelprijregel met een coupon voor een specifieke verzendmethode toegepast vanuit de interface van Admin.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a52ff98f>, <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_: [ FRESH ] de code van de HEX van de HEX werkt niet correct in STAAL bij
   * _nota van de Reparatie_: De code van de HEX die manueel door gebruiker in de Visuele de kleurenplukker van het Monster wordt ingegaan wordt niet meer veranderd door het systeem. Voorheen werden bepaalde HEX-codes enigszins aangepast als gevolg van omzettingsfouten tussen kleurmodellen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/344fce23>, <https://github.com/magento/inventory/commit/1ef984c0>

### Admin UI, B2B

* _AC-13628_: B2B Login als kopbal van de Klant heeft nog het brandmerken van Magento
   * _nota van de Reparatie_: Eerder toont de storefront kopbal &quot;u nu als &lt;customer name> op &lt;store name>&quot;met branding van Magento wordt verbonden. Deze is nu gefixeerd en de header wordt weergegeven met ADOBE-branding.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/96dec499>

### Admin UI, Payment/Payment Methods, Order

* _AC-13520_: De Vergunning van de transactie niet die in het Lusje van de Transactie na de Slimme Orde van de Knoop PayPal wordt getoond
   * _nota van de Reparatie_: Het systeem toont nu correct de transactievergunning in het lusje van de Transactie nadat een orde gebruikend de Slimme Knoop van PayPal wordt geplaatst. Voorheen verscheen de autorisatietransactie niet op het tabblad Transactie nadat u op de knop &quot;Autoriseren&quot; had geklikt en werd er geen nieuwe transactie van het type &quot;Autorisatie&quot; gemaakt.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Beheerdersinterface, prestaties

* _ACP2E-3169_: Na de update naar 2.4.5-p8 treden 500 fouten op bij het maken van een bestelling van de beheerder
   * _Fix-opmerking_: Voorheen kon bij het inschakelen van HTML-minificatie geen bestelling van de beheerder worden geplaatst. Nu, met HTML-minificatie ingeschakeld, kan de bestelling van de beheerder met succes worden geplaatst.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>

### Admin-gebruikersinterface, verzenden

* _ACP2E-2519_: De telling van de couponcode werkt niet in bij   De kolom &quot;Gebruikte tijd&quot; in het tabblad Codes voor coupons beheren als een bestelling wordt geplaatst met meerdere verzendingen.
   * _nota van de Reparatie_: Eerder, toen een orde met multi-verschepen werd geplaatst, werkte de telling van de waardeboncode niet in de &quot;Gebruikte Tijd&quot;kolom op het Manage lusje van de Codes van de Coupon bij. Nu wordt het juiste aantal weergegeven in zowel de &quot;Gebruikte tijd&quot; die de gewenste waarden weerspiegelt bij verzending via meerdere kanalen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/4745100c>

### Beheerdersinterface, Staging en Voorvertoning

* _ACP2E-3424_: [ Wolk ] het Verwijderen van malplaatje met ontbrekende beelden veroorzaakt pub/media om worden geschrapt
   * _nota van de Reparatie_: Eerder aan deze moeilijke situatie, als de naam van het voorproefbeeld voor een WebBuilder malplaatje mist, werd pub/media omslag geschrapt. Na de correctie wordt alleen de sjabloon verwijderd en de voorvertoning indien gevonden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analyse / Rapportage

* _AC-9922_: CSP-fout in Google Analytics https://region1.analytics.google.com
   * _Fix-opmerking_: het systeem staat nu correct verbindingen toe om &#39;https://region1.analytics.google.com&#39; te maken wanneer Google Analytics is ingeschakeld, waardoor fouten in het Content Security Policy (CSP) worden voorkomen. Voorheen zou het inschakelen van Google Analytics en het bekijken van de website vanuit de EU resulteren in CSP-consolefouten als gevolg van een weigering om verbinding te maken met &#39;https://region1.analytics.google.com&#39;.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/37750>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_: Het Rapport van de vooruitgang werkt niet
   * _nota van de Reparatie_: Het systeem steunt nu de generatie van de Geavanceerde Gegevensdossiers van de Rapportering voor extra grote datasets door rapporten in partijen van 10.000 te laden en te schrijven. Eerder, kon de Geavanceerde module van de Rapportering gegevensdossiers voor extra grote datasets niet produceren, veroorzakend &quot;MySQL server is weggegaan&quot;fouten tijdens de uitvoering van de analytics_collect_data bouwbaan.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Admin bestelde de kwestie van het de datumbereik van het Rapport van Producten.
   * _Fix-opmerking_: de gebruiker kan elke datum selecteren in het rapport met bestelde producten. Voorheen werd de datum na het vernieuwen van de tabel door &#39;VAN&#39;-datum te selecteren, de &#39;NAAR&#39;-datum gereset.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Onjuiste curl kopballen die nieuwe relic :create: opstellen-teller maken die niet werkt
   * _nota van de Reparatie_: Het systeem formatteert nu correct curl kopballen, toestaand het nieuwe betrouwbare :create: op:stellen-teller bevel om een plaatsingsteller in New Relic met succes tot stand te brengen. Eerder, verhinderden de onjuiste curl kopballen de verwezenlijking van een plaatsingsteller in New Relic.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37641>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3183_: NewRelic-browsermonitoring inlineJS-script veroorzaakt CSP-fouten
   * _Fix-opmerking_: NewRelic Browser Monitoring-scripts worden nu geïnjecteerd door de applicatie in plaats van door de APM-agent om te voldoen aan CSP (Content Security Policy). Voorheen waren NewRelic Browser Monitoring-scripts die door de APM-agent werden geïnjecteerd, niet compatibel met CSP en zorgden ze ervoor dat de scripts niet werden uitgevoerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: De vragen van het TUSSENVOEGSEL aan de lijst sales_bestsellers_compiled_daily worden langzaam op project met groot volume van de verkooporde
   * _nota van de Reparatie_: Eerder de bestsellers geaggregeerde dagelijks rapport zouden veel tijd vergen om voor groot volume van geplaatste orden te produceren. Nu wordt het verslag tijdig opgesteld.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: De rapporten van de orde die het verkeerde muntsymbool tonen
   * _nota van de Reparatie_: Het muntsymbool voor ordebedragen in het Rapport van de Orde werd verkeerd genomen van munt/opties/basis. Het is nu gecorrigeerd om valuta/opties/gebrek voor nauwkeurige rapportering te gebruiken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [ de Onjuiste Berekeningen van de Wolk ] in het Rapport van het Gebruik van de Coupon
   * _Bevestiging nota_: Het verkooptotaal in het netwerk van het couponrapport wordt nu nauwkeurig berekend door zowel het &quot;Bedrag van de Belastingcompensatie van de Korting&quot;als het &quot;Scheepskortingsbedrag van de Belastingcompensatie van de Schrapping te omvatten.&quot; Voorheen ontbraken deze bedragen in de berekening, wat leidde tot verschillen tussen het totaal van de verkopen en de gegevens van de verkooporder.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: De kwesties met gedeelde &quot;&lt;project_id>/var/tmp&quot;
   * _nota van de Reparatie_: De tijdelijke dossiers van DataExport van de Analyse zullen de folder van sys tmp gebruiken, die geschikter voor frequente toegang en veranderingen is. Om botsingen te vermijden in het geval dat de veelvoudige instanties op de zelfde server lopen, werd de weg tmp bijgewerkt om unieke identiteitskaart van een instantie te gebruiken
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analytics / Rapportage, B2B

* _ACP2E-2300_: B2B - sitemap bevat producten/categorieën die niet zijn toegewezen aan Shared Catalog
   * _Fix-opmerking_: Beperk de door het siteoverzicht gegenereerde categorieën en producten tot de categorieën en producten die alleen zijn toegewezen aan de openbare gedeelde catalogus en/of de machtigingsinstellingen voor cataloguscategorieën.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analyse / rapportage, cloud

* _ACP2E-3067_: Magento gooit de meeste New Relic cron transacties weg #34108
   * _nota van de Reparatie_: AC rapporteert correct gezamenlijke baan verwante transacties aan NewRelic. Voorheen zouden sommige aan een uitsnijdtaak gerelateerde transacties als &quot;OtherTransaction/Action/unknown&quot; in Northern Rock worden weergegeven
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_: Metrisch in NR zou voor achtergrondtransacties misleidend kunnen zijn - Follow-up van ACP2E-3067
   * _Fix-opmerking_: achtergrondtransacties (cron) gebruiken de naam van de New Relic-app die is gedefinieerd in de configuratie-instellingen
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _ACP2E-2139_: De producten die aan gedeelde catalogus worden toegewezen wijzen niet op het vooreind terug wanneer de gedeeltelijke index wordt uitgevoerd
   * _nota van de Reparatie_: De producten die aan gedeelde catalogus via REST API worden toegewezen zijn nu onmiddellijk zichtbaar op storefront nadat het gedeeltelijke indexeren volledig is. Eerder waren de producten pas zichtbaar na een volledige herindexering.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3044_: De onnodige grenzen op de Mijn sectie van Orden
   * _nota van de Reparatie_: Eerder werd een extra container (ordeverwijzingen) gecreeerd die extra CSS klassen toepaste, die onnodige grenslijnen veroorzaakte die onder het ordeaantal binnen de Mijn sectie van Orden verschijnen, die nu niet zichtbaar is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_: sales_clean_quotes cron schrapt citaten van aan nog goedgekeurde kooporden
   * _Nota van de Moeilijke situatie_: De citaten die in kooporden worden gebruikt zullen nu niet door sales_clean_quotes cron baan worden geschrapt
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>

### B2B, Kader

* _AC-9607_: Het filtreren van het Net van het Bedrijf &amp; toen het Poging van de Uitvoer van het Net CSV zal de Uitzondering van de Kwijting &amp; van de Borg ontbreken
   * _nota van de Reparatie_: Het systeem staat nu succesvolle uitvoer CSV van de het netgegevens van Bedrijven in het admin paneel toe, zelfs wanneer de filters zoals &quot;Uitstaand Saldo&quot;en &quot;Type van Bedrijf&quot;worden toegepast. Eerder, zou het toepassen van bepaalde filters en het proberen om de netgegevens uit te voeren in een mislukking resulteren en een uitzondering die wordt geworpen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/44cef3a9>

### Bundel

* _AC-10826_: Het berichtaantal van de Fout van de Bevestiging van de Bundel van de Bundel van de Storefront meer dan 1
   * _nota van de Reparatie_: Het systeem toont nu slechts één bericht van de bevestigingsfout wanneer &quot;toevoegt aan Kart&quot;wordt geklikt zonder enige checkbox opties voor een gebundeld product te selecteren. Eerder gaf het systeem meerdere foutmeldingen weer voor validatie voor elk niet-geselecteerd selectievakje.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3ea26621>

### Winkelwagentje en Afhandeling

* _AC-10660_: De uitzondering wordt niet behoorlijk behandeld terwijl het toevoegen van een product aan kar in de vergelijkingsproductpagina
   * _nota van de Reparatie_: Het systeem behandelt nu behoorlijk uitzonderingen wanneer het toevoegen van een product aan de kar van de vergelijkingsproductpagina, tonend een bericht van de berichtmanager in het controlemechanisme. Eerder zou een uitzondering ertoe leiden dat een JSON-gecodeerde pagina wordt geretourneerd in plaats van correct te worden afgevangen en afgehandeld.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38200>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag verzendt geen transactieprijzen en totalen.
   * _nota van de Reparatie_: Het systeem verzendt nu correct transactieprijzen en totalen naar de Markering van Google wanneer GTag wordt toegelaten, die nauwkeurige het volgen van elektronische handelgegevens verzekeren. Eerder werd de valuta onjuist verzonden als onderdeel van de &quot;alle&quot; bestellingen, in plaats van te worden gekoppeld aan de afzonderlijke bestelling.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37348>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Issue] [Checkout Depend-richtlijnen] bijgewerkt in e-mailsjabloon voor mislukte betaling
   * _Fix-opmerking_: Het systeem laat nu het verzendadres en de verzendmethode correct weg uit de e-mailsjabloon voor mislukte betalingen voor virtuele producten, zodat alleen relevante informatie in de e-mail wordt opgenomen. Voorheen bevatte de e-mail met mislukte betalingen voor virtuele producten ten onrechte het verzendadres en de verzendmethode.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/32781>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/32511>
* _AC-11717_: Magento 2 login binnen de controle met bestaande klant geeft consolefout in browser Firefox
   * _Bevestig nota_: Het systeem staat nu gebruikers toe om tijdens het controleproces aan te melden zonder enige consolefouten in browser Firefox te ontmoeten. Eerder, zou het proberen om zich aan te melden als bestaande klant tijdens controle in een consolefout in Firefox resulteren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38557>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39509>
* _AC-11876_: [Regressie van verkoopregels uitgeven] in 2.4.7
   * _Fix-opmerking_: het systeem valideert nu correct verkoopregels, waardoor de toepassing van een couponcode op een winkelwagentje wordt voorkomen wanneer de productstaat niet overeenkomt met een productnaam. Voorheen kon een verkoopregel worden toegepast en een korting op het verzendbedrag worden gegeven, zelfs als de productstaat niet overeenkwam met een productnaam.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38671>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_: [Uitgifte] Verkoopregel WinkelwagenVaste berekening : onjuist kortingsbedrag
   * _Fix-opmerking_: Het systeem berekent nu correct het kortingsbedrag voor verkoopregels met vaste bedragen in de winkelwagen, zodat nauwkeurige kortingen worden toegepast, ongeacht wijzigingen in winkelwagenartikelen. Voorheen kon het kortingsbedrag onjuist variëren wanneer winkelwagenartikelen werden gewijzigd, wat soms resulteerde in aanzienlijk grotere kortingen dan verwacht.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38694>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/581b7ef1>
* _AC-11993_: [Probleem] De lader blokkeert de verzendmethoden nadat de postcode is gewijzigd, validatieregels voor verzendtarieven
   * _nota van de Reparatie_: Het systeem behandelt nu correct douaneverschepende methodes zonder de bevestigingsregels van het verschepen tarief, die ervoor zorgen dat de lader niet de verschepende methodes blokkeert nadat postcode in het verschepende adres tijdens controle wordt veranderd. Als de postcode in het verzendadres tijdens de afhandeling werd gewijzigd, zou de lader eerder de verzendmethoden blokkeren en niet verdwijnen als er aangepaste verzendmethoden werden gebruikt zonder de validatieregels voor de verzendkosten.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38742>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: De eigenschap van de code van de coupon werkt niet behoorlijk in de controlepagina op Magento 2.4.7
   * _Nota van de Reparatie_: Het systeem laat nu het de inputgebied van de disconteringscode/coupon op de controlepagina voor virtuele en downloadbare producten toe, toestaand gebruikers om kortingscodes toe te passen zoals verwacht. Voorheen was de invoer van de kortingscode/kortingsbon uitgeschakeld en werd de titeltekst van de knop weergegeven als &quot;Kortingsbon annuleren&quot;, waardoor gebruikers geen kortingscodes konden toepassen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38826>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12479_: Het selectievakje Algemene voorwaarden staat geen HTML toe op de etalage
   * _nota van de Reparatie_: Het systeem steunt nu het formatteren van HTML in de checkbox van de &quot;Voorwaarden en van de Voorwaarden&quot;tekst op de storefront, die voor verbeterde aanpassing en leesbaarheid toestaat. Voorheen werd de tekst van het selectievakje weergegeven in tekst zonder opmaak, waarbij de gebruikte HTML-codes werden genegeerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _wisselstroom-12541_: De prijsregel van de kunst die voor het programma geopende gebruiker wordt gecreeerd wordt verkeerd toegepast niet het programma geopende gebruiker
   * _nota van de Reparatie_: Het systeem verwijdert nu correct de regel van de kartprijs voor het programma geopende gebruikers wanneer zij automatisch uit wegens koekjesafloop worden geregistreerd, die ervoor zorgen dat de korting niet op niet-het programma geopende gebruikers wordt toegepast. Eerder, werd de regel van de kartprijs nog toegepast zelfs toen de gebruiker uit het programma werd geopend, resulterend in een onjuiste korting die op niet-geregistreerde gebruikers wordt toegepast.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38944>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [ geef ] [ de optimalisering van de Eigenschappen ] grote winkelwagentjes van Prestaties door te verhinderen... uit.
   * _nota van de Reparatie_: Het systeem optimaliseert nu prestaties voor grote winkelwagentjes door dubbele vraag te verhinderen getActions, die de snelheid en de efficiency van het winkelwagentverrichtingen verbetert. Eerder werd voor een winkelwagentje met meerdere items de functie getActions meerdere keren aangeroepen, waardoor de prestaties van het systeem werden vertraagd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39292>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39290>
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
   * _Fix-opmerking_: na de fix wordt de korting correct weergegeven voor elke bestelling van dezelfde offerte voor meerdere verzendkosten.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [Parallelle verzoeken voor cloudproductie] om hetzelfde product aan de winkelwagen toe te voegen, resulteren in twee afzonderlijke items in de API voor de winkelwagensteun
   * _Fix-opmerking_: het systeem verwerkt nu correct meerdere parallelle verzoeken om hetzelfde product aan de winkelwagen toe te voegen aan een enkel regelitem, waardoor het maken van afzonderlijke regelitems voor dezelfde SKU wordt voorkomen. Voorheen resulteerde het indienen van parallelle aanvragen om hetzelfde product aan de winkelwagen toe te voegen via de REST API in meerdere regelitems voor dezelfde SKU.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2704_: Kan de cookie niet verzenden. Grootte van &#39;afbeeldingsberichten&#39; tijdens het opnieuw ordenen
   * _nota van de Reparatie_: Het opnieuw rangschikkende proces zal niet zijn eigen fouten nu produceren. Het object is afhankelijk van ingebouwde controles van winkelwagentjes.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: Het standaard verschepende adres wordt niet geselecteerd bij controle
   * _nota van de Reparatie_: Het standaard verschepende adres wordt nu geselecteerd gebeurtenis in context van toegelaten adresonderzoek.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [ CLOUD ] grafische addProductsToCart API kwestie met douaneoptie
   * _Fix-opmerking_: GraphQL voegt correct hetzelfde product toe aan de winkelwagen met verschillende aangepaste opties
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2923_: Meerdere adressen toegevoegd aan het account bij het afrekenen als nieuwe klant
   * _Fix-opmerking_: het systeem slaat nu slechts één keer een nieuw klantadres op als de bestelling niet is aangemaakt, waardoor wordt voorkomen dat er meerdere identieke adressen worden aangemaakt in het geval van fouten bij het plaatsen van bestellingen. Voorheen sloeg het systeem elke keer dat een bestelling werd geplaatst een nieuw adres op, ongeacht of de bestelling met succes was aangemaakt of niet.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Het opnieuw ordenen van klantenorde via de vorm van de gastorde resulteert een leeg karretje
   * _nota van de Reparatie_: Eerder, toen het plaatsen van een herschikking door de Orden en de pagina van Keert terug, werd de klant opnieuw gericht aan de login pagina. Nadat deze correctie is toegepast, wordt de geregistreerde klant correct omgeleid naar de pagina Winkelwagentje weergeven wanneer een nieuwe order wordt geplaatst. De stroom werkt het zelfde als gastklanten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: De Gebruiker van Admin met de beperkte Middelen van de Rol kan het Schepen van Kasten niet bekijken
   * _nota van de Reparatie_: Eerder, beperkte admin kon niet het verlaten het winkelwagentje van het admin paneel voor een bijbehorende website zien. Nadat deze correctie is toegepast, kan de beperkte beheerder het verlaten winkelwagentje van het admin paneel zien.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3176_: [ de Snelle orde van de Wolk ] grote hoeveelheid SKU prestaties
   * _nota van de Reparatie_: De prestaties van de kassa zijn verbeterd wanneer de attributen die in de voorwaarden van de kartprijs worden gebruikt niet voor alle producten aanwezig zijn en wanneer de eigenschap van de KAART (Minimale geadverteerde prijs) wordt toegelaten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: Dubbele punten in kar
   * _nota van de Reparatie_: Het systeem verwerkt nu correct veelvoudige parallelle verzoeken om het zelfde product aan de kar in één enkel lijnpunt toe te voegen, verhinderend de verwezenlijking van afzonderlijke lijnpunten voor zelfde SKU. Eerder, zou het doen van parallelle verzoeken om het zelfde product aan het karretje op Storefront toe te voegen in veelvoudige lijnpunten voor zelfde SKU resulteren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: De bevestiging van de betalingsorde wordt verzonden naar e-mail ingegaan in Voornaam/Achternaam
   * _nota van de Reparatie_: De bevestiging van de controleorde e-mail, die eerder werd verzonden toen een e-mailachtig patroon in de Voornaam en de gebieden van de Achternaam werd ingegaan, wordt niet meer verzonden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: De vorm van het het verschepende adres van de Afhandeling krijgt update met verkeerd adres
   * _Bevestig nota_: ShippingAddressFromData wordt nu bewaard in de lokale opslag per website. Eerder kon een adres van de verkeerde website automatisch worden ingevuld in het verzendadresformulier tijdens het uitchecken als een winkelcode in de URL werd gebruikt en het uitchecken tijdens dezelfde gastsessie werd gestart van meerdere websites.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3407_: Het Product van de Kaart van de Gift | Winkelsamenvoegen is een kaartje samenvoegen
   * _nota van de Reparatie_: De producten van Giftcard worden nu correct samengevoegd in het karretje
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3415_: De persistentie van de kunst wordt niet gerespecteerd op logout
   * _nota van de Reparatie_: Toegevoegde ontbrekende functionaliteit herinner me van klantenlogin aan authentificatie popup en checkout teken ins.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_: De bestaande citaatgegevens zijn niet bijgewerkt/niet zichtbaar, in plaats daarvan creeer een nieuw citaatverslag wanneer trigger_recollect = 1
   * _Bevestig nota_: De winkelwagentjes van de klant verdwijnen niet meer als resultaat van een product dat wordt geschrapt nadat het aan het winkelwagentje werd toegevoegd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3618_: [ CLOUD ] herordenen knoopfunctionaliteit
   * _nota van de Reparatie_: Bevel een orde van het beheerdergebied zal nu producten met voorraad aan het citaat toevoegen alhoewel er sommige producten in de originele orde zijn die geen voorraad meer hebben. Vóór de correctie werden geen producten aan het nieuwe prijsopgave toegevoegd als het product zonder voorraad zich in de oorspronkelijke volgorde bevond.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3622_: De opslag van het onderzoek werkt niet door postcode
   * _nota van de Reparatie_: Het zoeken naar ophaalplaatsen door ZIP code werkte niet behoorlijk voor Nederlandse localisaties. Na de correctie geeft het zoeken naar de locatie van het oppikken resultaten op basis van de postcode.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/344fce23>

### Afhandeling van winkelwagentje en afhandeling, Afhandeling/Afhandeling van één pagina

* _AC-9386_: [ het Willekeurige gebied van de BUG ] E-mail wordt niet teruggegeven of neemt veel tijd omhoog in de Verzending van de Controle of de pagina van de Betaling verschijnt
   * _Bevestig nota_: Commerce geeft nu het **[!UICONTROL Email]** gebied op de controle verschepen en betalingspagina&#39;s terug zoals verwacht. Eerder was dit veld afwezig of traag gerenderd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/e1babcfd>

### Winkelwagentje en afhandeling, bestelling

* _ACP2E-3097_: Datepicker voor product met veelvoudige Aanpasbare Opties met datumgebieden die niet werken wanneer het plaatsen van orde van admin
   * _nota van de Reparatie_: Het systeem toont nu correct de datumkiezer voor alle datumgebieden wanneer het vormen van een product met veelvoudige klantgerichte datumopties in het proces van de admin ordeverwezenlijking. Eerder werd de datumkiezer alleen weergegeven voor het veld voor de eerste datum, zodat de overige velden geen datumkiezer hadden.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/b21e5d91>

### Winkelwagen &amp; Afrekenen, Verzending

* _AC-12119_: Onmiddellijke aankoop &quot;goedkoopste verschepende&quot;gebroken voor configureerbare producten
   * _nota van de Reparatie_: De Onmiddellijke eigenschap van de Aankoop selecteerde verkeerd de duurdere optie van de Opslag van de Aankoop voor configureerbare producten in plaats van de goedkoopste Vlakke methode van het Tarief. Deze correctie zorgt ervoor dat de juiste verzendmethode wordt gekozen op basis van de werkelijke prijs.&quot;
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38811>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catalogus

* _AC-10910_: Bij het opschonen van cron_schedule databasetabel worden niet-bestaande taken niet opgeschoond
   * _nota van de Reparatie_: Het systeem ontruimt nu automatisch de cron_planning gegevensbestandlijst, verwijderend ingangen voor banen die niet meer in het systeem bestaan. Dit zorgt voor optimale prestaties door een minimaal aantal rijen in de tabel aan te houden. Eerder, werden de ingangen voor banen van inactieve of verwijderde modules niet schoongemaakt, die tot onnodige gegevensaccumulatie in de cron_planninglijst leidden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38217>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: De Prijs van de rij wordt niet geschrapt van Configurable Product
   * _nota van de Reparatie_: Het systeem verwijdert nu correct de rijprijs van een product wanneer het van een eenvoudig product aan een configureerbaar product wordt omgezet, die nauwkeurige prijsvertoning op het front verzekeren. Voorheen werd de staffelprijs van een configureerbaar product niet verwijderd wanneer een product werd geconverteerd van een eenvoudig product naar een configureerbaar product, wat leidde tot een mismatch in de weergegeven prijs.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38390>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: De beschrijving van de categorie WYSIWYG is leeg op niet standaard storeview
   * _nota van de Reparatie_: Het systeem bewaart nu correct en toont de categoriebeschrijving in de redacteur van WYSIWYG wanneer het uitgeven van een categorie op het niveau van de archiefmening. Voorheen leek de WYSIWYG-editor leeg na het opslaan van een categoriebeschrijving op het niveau van de winkelweergave.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38622>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38623>
* _wisselstroom-11970_: Onmogelijk om configureerbare producten met één checkbox geselecteerde douaneoptie opnieuw in orde te brengen
   * _nota van de Reparatie_: Het systeem verwerkt nu correct het opnieuw ordenen van configureerbare producten met één enkele geselecteerde checkbox douaneoptie, die voor succesvolle korteverwezenlijking toestaat. Voorheen leidde het opnieuw ordenen van dergelijke producten tot een fout en werd voorkomen dat artikelen aan het winkelwagentje werden toegevoegd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38736>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1d144bce>
* _wisselstroom-12076_: [ Eis ] Reparatie van filterpunt op gelaagde navigatie
   * _Fix-opmerking_: Het systeem gebruikt nu correct de woorden &quot;item&quot; en &quot;items&quot; in het gelaagde navigatiefilteritem, waardoor de duidelijkheid en nauwkeurigheid van de filterbeschrijvingen wordt verbeterd. Voorheen werden deze woorden onjuist gebruikt, wat leidde tot mogelijke verwarring bij gebruikers die door de filteropties navigeren.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38789>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: Datum- en tijdnotatie voor aangepaste optie werkt niet
   * _nota van de Reparatie_: Het systeem past nu correct het gevormde datumformaat op de opties van de productdouane van typeDatum toe, die ervoor zorgen dat het datumformaat correct op het front-end wordt getoond. Eerder waren wijzigingen in de configuratie van de datumnotatie niet van toepassing op de front-end voor aangepaste productopties van het type Date.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32990>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38925>
* _AC-13068_: Ontbrekende opties van de Dropdown
   * _nota van de Reparatie_: Het systeem toont nu correct alle waarden in dropdown wanneer het creëren van een nieuw attribuut met meer dan 20 waarden. Eerder werden alleen de eerste 20 waarden of een andere geselecteerde paginawaarden weergegeven, waardoor de resterende waarden ontbraken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [Probleem] Gebruik de huidige pijnlijke ID voor de runtime-cache van de categorie
   * _Fix-opmerking_: het systeem gebruikt nu correct de huidige winkel-ID voor de runtime-cache van de categorie, waardoor wordt voorkomen dat gegevens worden overschreven wanneer emulatie wordt gebruikt of aangepaste code de categorie in verschillende winkels opslaat. Voorheen kwam het object dat in runtime was opgeslagen mogelijk uit de verkeerde winkel, wat leidde tot gegevensoverschrijving.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39310>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: Bak/magento sampledata:opstellen - geen-update werpt een uitzondering
   * _nota van de Reparatie_: Het systeem keurt nu correct een booleaanse waarde goed wanneer het gebruiken van —geen-updateoptie in sampledata:stel bevel op, dat om het even welke fouten tijdens de plaatsing van steekproefgegevens verhindert. Er is eerder een fout opgetreden bij het gebruik van deze opdracht omdat het systeem een geheel getal verkeerd had verwacht.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39344>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [ het gebruik van de Uitgave ] van de Oplossing van EAV geheim voorgeheugentype
   * _nota van de Reparatie_: Het systeem gebruikt nu correct het EAV geheim voorgeheugentype in alle relevante plaatsen, die verenigbare en efficiënte gegevens caching verzekeren. Eerder werd het EAV-cachetype niet consistent gebruikt, wat tot mogelijke inefficiënties en inconsistenties in het in cache plaatsen van gegevens leidde.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32322>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: Het Geavanceerde Onderzoek van de catalogus met lege gegevens gaat naar de pagina van het onderzoeksresultaat [ 2.4.dev tak ]
   * _nota van de Reparatie_: Het systeem behoudt nu correct gebruikers op de Geavanceerde pagina van het Onderzoek en toont een foutenmelding wanneer zij proberen om een onderzoek uit te voeren zonder om het even welke gegevens in te gaan. Als u voorheen een lege zoekopdracht zou uitvoeren, zou u gebruikers omleiden naar de pagina Geavanceerd zoeken in catalogus met een bericht waarin ze worden gevraagd hun zoekopdracht te wijzigen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13622_: [ geef ] de lay-out van het Product uit die op attribute_set wordt gebaseerd
   * _nota van de Reparatie_: Het systeem staat nu de aanpassing van productlay-out toe die op de kenmerkenreeks wordt gebaseerd, die een praktischere en efficiëntere manier verstrekt om productvertoning in de vooruitgangsopslag te beheren. Voorheen kon de lay-out alleen worden aangepast door SKU of per productsoort, wat niet altijd praktisch was voor veel producten of specifieke artikelen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38790>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36244>
* _AC-6738_: Ontbrekende unieke sleutel op eav_attribute_option_value lijst
   * _nota van de Reparatie_: Het systeem omvat nu een unieke sleutel op de &quot;option_id&quot;en &quot;store_id&quot;kolommen in de &quot;eav_attribute_option_value&quot;lijst, die de mogelijkheid van een optie verhinderen die veelvoudige waarden voor de zelfde opslagmening hebben. Eerder, kon de gebrekkige code in een optie resulteren die veelvoudige waarden voor de zelfde opslagmening heeft, die kwesties veroorzaakt wanneer het uitgeven van producten of attributen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/24718>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [ de zichtbaarheidsklasse van het Gebruik van de kwestie ] voor de indexeerder van het categorieproduct, in plaats van geharde waarden
   * _nota van de Reparatie_: Het systeem gebruikt nu de zichtbaarheidsklasse voor de indexator van het categorieproduct in plaats van geharde waarden, verbeterend modulariteit. Eerder werden in de productindex van de categorie hardgecodeerde waarden gebruikt, waardoor de flexibiliteit en het aanpassingsvermogen werden beperkt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37200>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: Valutacode verandert niet in widget voor nieuwe producten
   * _Fix-opmerking_: het systeem werkt nu de valutacode in de widget Nieuw product correct bij wanneer de valuta in de frontend wordt gewijzigd, waardoor consistentie in de valutaweergave op de site wordt gegarandeerd. Voorheen had het wijzigen van de valuta in de front-end geen invloed op de valutacode die werd weergegeven in de widget Nieuw product.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37898>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: De regelmatige Prijs toont niet op PLP voor Configureerbaar Product
   * _nota van de Reparatie_: De regelmatige prijs wordt nu getoond op de pagina&#39;s van de productlijst voor configureerbare producten die kindproducten met speciale prijs hebben.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: De informatie van de voorraad die niet recht op het Visuele Net van de Verkoop toont
   * _Fix-opmerking_: de voorraad wordt nu weergegeven op basis van de geselecteerde winkel.
   * _Bijdrage GitHub-code_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: De inhoud van de widget wordt niet bijgewerkt op de cms-pagina
   * _Fix-opmerking_: het systeem werkt nu de widgetinhoud op een CMS-pagina bij wanneer een product als nieuw is ingesteld en is opgeslagen, zodat de bijgewerkte productcollectie op de pagina wordt weergegeven. Voorheen werd de pagina niet bijgewerkt om het nieuwe product weer te geven vanwege de onjuiste cache-identiteiten die werden gebruikt voor de widget in de cache.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/f89a447e>
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
   * _Fix-opmerking_: er is geen javascript-fout in de browserconsole tijdens het verwijderen van de optie uit het bundelproduct.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38505>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [Cloud] Bundle Product verkeerde prijzen in orderbevestiging
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
* _ACP2E-3103_: Het nieuwe voer van Producten RSS wordt niet bijgewerkt met nieuwe producten toe te schrijven aan geheim voorgeheugen
   * _nota van de Reparatie_: Het voer van Rss voor Nieuwe Producten wordt nu bijgewerkt wanneer een product als nieuw en bewaard wordt geplaatst
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3126_: [ de reactie van GQL van de Galerij van de Media van het Product van de Wolk ] wordt niet gesorteerd door beeldpositie
   * _nota van de Reparatie_: Het systeem sorteert nu correct punten in de media galerij door positie in de reactie van GraphQL, die nauwkeurige vertoningsorde verzekeren. Eerder zijn de items in de mediagalerie niet op positie gesorteerd, wat tot een onjuiste weergavevolgorde heeft geleid.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37671>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>
* _ACP2E-3136_: [ de punten van de 3} Subcategorie van de Wolk {worden niet getoond op widgets uitgeven op admin achtereind]
   * _nota van de Reparatie_: De categorieboom op de nieuwe widgetpagina zou geen kwesties meer moeten hebben ladend Niveau 5+ categorieën. Eerder ontbraken enkele categorieën bij het laden van de structuur voorbij de categorieën van niveau 5.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3198_: [ wolk ] tweemaal-vinger gezoem en bewegingskwestie op het echte mobiele apparaat
   * _Bevestig nota_: Het systeem verzekert nu verenigbare beeldgezoemfunctionaliteit op mobiele apparaten, die een vlotte en voorspelbare gebruikerservaring verstrekken. Eerder was de functie voor zoomen op afbeeldingen inconsistent en zoomde dan plotseling uit na een bepaald punt bij weergave op een mobiel apparaat.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3282_: Wanneer wij producten van de gedeelde catalogus unassign, worden de wenslijstproducten niet ontruimd
   * _nota van de Reparatie_: Nu, zijn geen punten zichtbaar in de wenslijst als een product niet beschikbaar in de gedeelde catalogus is. Eerder werd op de pagina Vraaglijsten een telling van 1 item onjuist weergegeven, zelfs als er geen items in de verlanglijst stonden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3286_: De verwante producten selecteren allen/Deselecteren Alle Uitgave
   * _nota van de Reparatie_: Eerder, &quot;Uitgezocht allen&quot;/ &quot;Unselect allen&quot;knopen voor verwante producten niet correct werkte als een product manueel werd geselecteerd. Na de correctie werken deze knoppen nu consistent, zelfs na handmatige selectie, zodat alle producten correct zijn geselecteerd of uitgeschakeld.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3336_: [ de waakzame e-mailvertaling van de Beeld van de Wolk ] aan de verkeerde taal
   * _Nota van de Oplossing_: Wanneer het verzenden van de Alarm van de Beeld/van de Prijs voor een website met veelvoudige opslagmeningen gebruikend verschillende talen, zal de taal voor de archiefmening waar het alarm werd gecreeerd op e-mail worden gebruikt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4cf5e62>, <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3350_: Uitgeschakelde categorieën hebben hun namen niet langer grijs weergegeven in de categorieboom
   * _Vaste opmerking_: Voorheen werden uitgeschakelde categorieën niet grijs weergegeven in de categoriestructuur. Nu worden ze weergegeven met een grijs-outeffect.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: Configureerbaar product bewerken formulier laden veroorzaakt time-out en geheugenuitputting
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke configureerbare productvariaties werden geconstrueerd gebaseerd op alle mogelijke combinaties van attributenopties. In gevallen waarin kenmerken veel opties hadden, resulteerde dit in een langdurige en hulpbronnenintensieve bewerking. Configureerbare productvariaties worden nu samengesteld op basis van bestaande onderliggende productkenmerken. Dit leidt tot veel minder berekeningen, dus tot een beter gebruik van middelen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: Fotorama laadt correct geen video wanneer het gebruiken van Monsters en de optie wordt pre-geselecteerd via URL
   * _nota van de Reparatie_: De video&#39;s van het product zullen nu behoorlijk op configureerbare pagina van productdetails teruggeven, als URL geselecteerde opties bevat.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: De Breedte van Carousel PageBuilder toont producten die voorwaarden niet aanpassen
   * _Nota van de Reparatie_: De lijst van het product die in widgets wordt gebruikt respecteert nu categorieconfiguratie
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: De fout van de bevestiging teweeggebracht voor Alle Producten in Groep wanneer men ongeldige hoeveelheid heeft
   * _Fix-opmerking_: Nu wordt de validatiefout correct geactiveerd voor alle producten in de groep wanneer een product een ongeldige hoeveelheid heeft, wat voorheen niet gebeurde.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3513_: [ CLOUD ] Speciale prijs die niet in Configurable product toont
   * _nota van de Reparatie_: Na de moeilijke situatie, die de &quot;Gebruikt in de Lijst van het Product&quot;waarde voor het speciale prijsattribuut verandert zal niet het tonen van de speciale prijs voor configureerbare producten beïnvloeden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_: De Tijdelijke lijsten van indexen worden niet schoongemaakt als het proces wordt geëindigd
   * _nota van de Reparatie_: De tijdelijke lijsten van de indexeerder CatalogRule worden nu schoongemaakt als het indexeerproces wordt geëindigd
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [ de mislukkingen van de de eenheidstest van de KANDIS ] van de Kern in 2.4.7-p3
   * _nota van de Reparatie_: De nota&#39;s van de Versie voor deze test zijn niet nodig aangezien het een eenheid-test verbetering is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3533_: De kwestie van prestaties in de Inkomsten van het Aantal van de Voorraad voor Gegroepeerde Producten met Veelvoudige Bronnen
   * _nota van de Reparatie_: De gegroepeerde product en de pagina van de bundelproduct uitgeven wordt nu geoptimaliseerd wanneer de toegewezen producten groot aantal inventarisbronnen hebben.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/0208e433>
* _ACP2E-3641_: Achtervoegsel https://jira.corp.adobe.com/browse/ACP2E-3389
   * _Nota van de Reparatie_: Verbeterde prestaties van admin categoriepagina in het geval van groot aantal ankercategorieën
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/982b1c42>

### Catalogus, inhoud

* _ACP2E-3063_: [ het geheime voorgeheugen van de Wolk ] wordt niet ongeldig gemaakt.
   * _nota van de Reparatie_: Eerder, toen het bewaren van een pagina van CMS met een bijgewerkte ontwerplay-out, bezat het niet geschikt op het vooreind. Nadat deze correctie is toegepast, is de juiste ontwerplay-out zichtbaar aan de voorkant wanneer we de ontwerplay-out wijzigen en de CMS-pagina opslaan.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [Categorieën voor cloudankers] /niet-ankers omgekeerd in inhoudswidget
   * _Fix-opmerking_: Eerder, toen we Display On -> Anchor Categories selecteerden, werden alle categorieën weergegeven die niet de ouder-kindrelatie tussen het anker en het niet-anker weerspiegelden. Nadat deze correctie is toegepast, worden in de Categorieën Weergeven op -> Anker alleen de ankercategorieën weergegeven (selecteerbaar) en in de Categorieën Weergeven op -> Niet-anker worden de niet-ankercategorieën weergegeven (selecteerbaar)
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: Categorieën die niet met widgets werken
   * _nota van de Reparatie_: Eerder, als wij het blok van CMS voor verschillende anker/niet ankercategorieën bewaarde, het niet voor de kindcategorieën werkte toen het op het vooreind toonde. Nadat deze correctie is toegepast, wordt het blok aan de voorzijde weergegeven voor verschillende categorieën.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d01ee51e>

### Catalogus, framework

* _AC-9111_: Bestelling krijgen (Verzendingen|Creditmemo&#39;s |Factuur)Incasso - Incasso mag niet worden geladen
   * _Fix-opmerking_: Het systeem zorgt er nu voor dat de incasso&#39;s voor zendingen en creditnota&#39;s niet vooraf worden geladen wanneer ze uit een order worden opgehaald, waardoor extra filters of bestellingen op deze incasso&#39;s kunnen worden toegepast. Eerder werden deze verzamelingen automatisch geladen, zodat er geen verdere wijzigingen konden worden aangebracht.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37561>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_: [ Cloud ] follow-up: Verkeerde gelijke in Gegevens Vergelijking wanneer het controleren als het gegeven veranderingen heeft
   * _nota van de Reparatie_: Eerder, werd het sparen voorwerp geroepen telkens zonder enige gegevensveranderingen (voor om het even welk numeriek gegevensgebied - zoals int/float/dubbel). Het activeert de vlag _hasDataChanges waar is en roept de opslagfunctie aan. Het controleert ook niet de zwevende getallen die zijn ingekapseld door een string. Nadat deze oplossing is toegepast, wordt de opslagfunctie alleen aangeroepen als de gegevens zijn gewijzigd. De gegevenswaarde voor int/float/dubbelcheck met de waarde die wordt doorgegeven aan de functie en doet strikte type-matching
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/c8931218>

### Catalogus, GraphQL

* _ACP2E-3090_: Het behandelen van de Filters van de Categorie in GraphQL: includeDirectChildrenOnly en category_uid
   * _Bevestig nota_: Slechts worden de directe kindcategorieën gehaald terwijl het filtreren door category_uid.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [ Cloud ] Grafiek het sorteren van het Product werkt niet
   * _Bevestig nota_: Het sorteren van het Product GraphQl door veelvoudige gebieden wanneer de gebieden in variabelen nu worden overgegaan werkt zoals verwacht.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_: Staffelprijzen retourneren de verkeerde waarde in producten GraphQL (vergeleken met Storefront)
   * _Fix-opmerking_: Na de fix hebben de staffelprijzen van het product die worden geretourneerd voor graphql-verzoeken een prijs per item.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1366ae5e>

### Catalogus, prijzen, enscenering en preview

* _ACP2E-2672_: [ het eindpunt van de PrijsAPI van de Wolk ] keert fout terug wanneer het bijwerken van grote aantallen producten gelijktijdig
   * _de nota van de Reparatie_: Nu zal de speciale Prijs update API één enkele campagne voor elke datumwaaier in plaats van veelvoudige geplande updates voor elk product en datumwaaier tot stand brengen. Bovendien worden gelijktijdige API-aanvragen voor snellere verwerking van een groot aantal SKU&#39;s ondersteund.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>

### Catalogus, product

* _AC-7050_: Categorieselectieboom in product bewerken staat niet in dezelfde volgorde als ingesteld in Catalogus->Categorieën
   * _nota van de Reparatie_: Het systeem toont nu correct de boomstructuur van de categorieselectie in product uitgeeft sectie in de zelfde orde zoals die in Catalogus ->Categorieën wordt geplaatst, makend productbeleid in grote catalogi gemakkelijker. Eerder werd de categoriestructuur in de productbewerkingssectie weergegeven in de volgorde van het maken van de categorie, ongeacht de weergavevolgorde ingesteld in Catalog->Categorieën.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36101>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36104>

### Catalogus, SEO

* _ACP2E-3653_: Onjuiste canonieke URL voor categorie wanneer pagina > 1
   * _Fix-opmerking_: Voorheen werkte de canonieke URL voor inhoud met meerdere pagina&#39;s niet correct, waardoor de basis-URL consequent werd weergegeven. Nadat de oplossing is geïmplementeerd, wordt de URL met de pagina-ID nu correct weergegeven in de canonieke URL voor inhoud met meerdere pagina&#39;s.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/982b1c42>

### Catalogus, Zoeken

* _ACP2E-2757_: De producten tonen niet op categorie en onderzoek maar de directe verbindingen werken
   * _Bevestig nota_: Eerder, werkt het ja/Geen douaneattribuut met price_* attribute_code niet met het indexeren. Na deze correctie werkt het kenmerk Yes/No naar behoren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [ Cloud ] Elastische onderzoeksfout op bepaalde categoriepagina&#39;s
   * _nota van de Reparatie_: Eerder, met het vermelde configuratiekaartje, wanneer wij prijs 0 voor veelvoudige producten zetten, zal het een uitzondering bij de voorste categoriepagina werpen. Nadat deze correctie is toegepast wanneer meerdere productprijzen 0 en we de pagina met categorieën vooraf laden, wordt er geen uitzondering gegenereerd en wordt de pagina met categorieën correct geladen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_: De Fout van het type kwam voor wanneer het creëren van voorwerp: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Uitzondering
   * _nota van de Reparatie_: Na de moeilijke situatie, kan een geval van klasse Magento\CatalogSearch\Model\Indexer\Fulltext worden gecreeerd zonder $data te specificeren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [ CLOUD ] Kwestie met Producten is niet Zichtbaar op Voorzijde na het Opslaan in Admin van Magento
   * _nota van de Reparatie_: Na de moeilijke configureerbare producten die kindproducten met lange namen hebben zullen niet in de storefront worden gemist.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>

### Wolk

* _ACP2E-3010_: [ de Wolk ] PHPSESSID verandert elk POST- Verzoek
   * _Nota van de Reparatie_: PHPSESSID regenereert niet meer op POST- verzoeken op frontend gebied voor een het programma geopende klant als L2 Redis geheime voorgeheugen wordt toegelaten en de klant werd bijgewerkt van het achterste eind
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3532_: De Waarschuwingen van de Generatie van de Sitemap
   * _nota van de Reparatie_: Na de moeilijke situatie, wordt de sitemap geproduceerd in de systeemfolder tmp en gekopieerd aan de definitieve bestemming.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d4de4726>

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
* _AC-12692_: De categorieboom van widget wordt niet correct teruggegeven
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39008>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: Onbekwaam om &quot;Gebruikend Standaardwaarde&quot;bericht te zien wanneer het veranderen van het thema in de pagina van de ontwerpconfiguratie
   * _nota van de Reparatie_: Het systeem omvat nu een afzonderlijke kolom om het &quot;Gebruikende Standaard waarde&quot;bericht afhankelijk van het geselecteerde thema in de pagina van de ontwerpconfiguratie te tonen. Dit zorgt voor helderheid en zichtbaarheid van de status van de standaardwaarde. Eerder werd het bericht &#39;Standaardwaarde gebruiken&#39; niet weergegeven, wat leidde tot verwarring over de status van het geselecteerde thema.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/47b448e2>
* _wisselstroom-13569_: [ geef uit ] herstelt achterwaartse verenigbaarheid met stop TinyMCE opnieuw (na het..
   * _Fix-opmerking_: het systeem herstelt nu achterwaartse compatibiliteit met TinyMCE-plug-ins, waardoor functies die in de plug-in zijn gedefinieerd, kunnen worden aangeroepen wanneer de widget vanaf een andere locatie wordt gebruikt. Eerder, als gevolg van een wijziging in de TinyMCE-versie, retourneerden de plug-ins de widgets niet als een object, wat resulteerde in een fout bij het aanroepen van bepaalde functies op de widget-instantie.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39262>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/39258>
* _AC-9638_: [Probleem met het uploaden van] bestanden in de WYSIWYG-editor op de productpagina
   * _nota van de Reparatie_: Het systeem toont nu correct de omslagboom en staat beeld toe uploadt in de redacteur van WYSIWYG op de productpagina, zelfs na het uitbreiden van het &quot;Beeld en Video&#39;s&quot;lusje eerst. Eerder werd door het uitvouwen van het tabblad &#39;Afbeelding en video&#39;s&#39; de mappenstructuur niet weergegeven en werd een foutbericht weergegeven wanneer werd geprobeerd een afbeelding te uploaden in de WYSIWYG-editor.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38026>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [ On-PREM ] Dynamische blokkwestie
   * _Fix note_: Wdigets worden nu correct gerenderd binnen dynamische blokken.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2693_: [Cloud] Frontend laadt niet vanwege probleem in nieuwsbriefsjabloon
   * _Fix note_: Het toevoegen van blokken via CMS Page content section leidt niet meer tot uitzonderingen
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [ Cloud ] onderzoekt uitzondering die in het logboek wordt gevonden: InvalidArgumentException: De klasse bestaat niet in vendor/magento/module-rule/Model/ConditionFactory.php
   * _nota van de Reparatie_: Het verwijderen van een voorwaarde op de montages van de de productinhoud PageBuilder veroorzaakt niet meer een uitzondering om in de logboekdossiers worden geregistreerd. Eerder, zou het verwijderen van een voorwaarde op de montages van de de productinhoud PageBuilder een kritieke uitzondering veroorzaken om in de logboeken worden geregistreerd, ondanks het veroorzaken van geen kwesties op het front-end.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: Het schakelen naar enige opslagwijze - de globale inhoud verschijnt niet meer
   * _nota van de Reparatie_: Het systeem synchroniseert nu de configuraties van het opslagmeningsontwerp met de configuraties van het websiteontwerp wanneer het toelaten van enige opslagwijze, die ervoor zorgen dat de inhoudsupdates op het frontend zichtbaar zijn. Voorheen zou het overschakelen naar de modus voor één winkel voorkomen dat inhoudsupdates werden weergegeven in de etalage.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: De Bouwer van de pagina vervangt beeld wanneer het proberen om verbinding en andere bruikbaarheidsglitches toe te voegen.
   * _nota van de Reparatie_: Nu het klikken op een beeld, zullen de verbindingen in beeldredacteur in het de tekstelement van de Bouwer van de Pagina juiste gegevens in het beeld, de dialoog van de verbindingsconfiguratie laden. Het toevoegen van een koppeling naar een afbeelding in de editor werkt nu goed. Eerder werd de afbeelding vervangen door een koppeling.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: De oude media galerij ontbreekt om beelden terug te geven wanneer een 0 byte beeld in de folder wordt geplaatst
   * _nota van de Reparatie_: Het systeem behandelt nu 0 byte beelden in de media galerij zonder functionaliteit te verstoren, toestaand andere beelden in de folder om worden getoond en worden geselecteerd zoals verwacht. Eerder was het zo dat door de aanwezigheid van een afbeelding van 0 byte in de mediagalerie niet alle afbeeldingen in de directory konden worden weergegeven of geselecteerd.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: Fout Page Builder bij het bewerken van CMS-blok
   * _nota van de Reparatie_: Het systeem bewaart nu correct veranderingen die in het admin gebied worden aangebracht gebruikend de Bouwer van de Pagina, zonder de fout &quot;Bouwer van de Pagina terug te werpen voor 5 seconden zonder sloten vrij te geven.&quot; in de browserconsole. Deze fout is eerder opgetreden tijdens een poging om wijzigingen op te slaan, zodat de inhoud niet met succes kan worden bijgewerkt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [ CLOUD ] Geen knopen van controle of geeft kart op de wortelsectie uit
   * _nota van de Reparatie_: Het product van de bundel wordt nu toegevoegd aan het karretje via widgets zonder fouten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3122_: [ CLOUD ] uploadt beeldknoop werkt niet
   * _Bevestig nota_: Vóór de Upload knoop van het Beeld voor Banner en Schuif van PageBuilder niet zoals verwacht werkte, en nu wanneer het drukken van het opent de lokale dossiermanager om het gezochte beeld te selecteren om te uploaden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3127_: imagecreatetruecolor (): Argument #2 ($height) moet groter zijn dan 0. Kan specifieke afbeelding niet uploaden
   * _nota van de Reparatie_: Los de kwestie op die fouten in admin veroorzaakt wanneer het uploaden van beelden met een hoogte van 0 via de media galerij, en succesvol de activa synchronisatie gebruikend het synchronisatiebevel. Eerder kan de afbeelding niet worden geüpload via de mediagalerie en de synchronisatieopdracht mislukt ook als een bepaalde afbeelding zich in de galerie bevindt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3154_: Prototype.js Array.from in conflict met Google Maps API
   * _nota van de Reparatie_: De Kaarten van Google geven nu behoorlijk in de redacteur PageBuilder terug. Een JavaScript-fout voorkomt eerder dat Google Maps correct wordt weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3275_: [ Wolk ] - de Schuif van CMS die de recentste veranderingen niet weerspiegelt
   * _nota van de Reparatie_: De kwestie is opgelost door de sliderlijst te verzekeren wordt verfrist terwijl sparen gebeurtenis op het uitgeeft diascherm wordt teweeggebracht. Eerder was het aanleiding tot het probleem.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Een fout komt in CSM pagina voor wanneer de blokken van CMS gebruikend paginabouwer in bepaalde orde worden opgenomen
   * _nota van de Reparatie_: Eerder op sommige versies van PHP en OS (Linux), zou het teruggeven van blokken die andere cms blokken door PageBuilder van verwijzingen voorzien met een &quot;Onbekende fout voorgekomen zijn ontbroken. Probeer het opnieuw.&quot;. Nu wordt de inhoud van de cms-blokken correct gerenderd in inhoud die door PageBuilder wordt gecontroleerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3428_: De mislukking van de malplaatjevoorproef van de Bouwer voor grote inhoud
   * _nota van de Reparatie_: De grote inhoud leidde tot canvaselement dat de browser grenzen overdrijft, en het terugkeren van onjuiste waarde, die achterste code (kan niet behoorlijk het beeld decoderen) brak. Opgelost met het beperken van de canvasgrootte tot de limiet van de universele browser.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_: De recentste veiligheidsupdates met TinyMCE 7 ontbrekende doopvontgrootte
   * _nota van de Reparatie_: De grootte van de doopvont en de selecteurs van de doopvontfamilie zijn nu beschikbaar in de redacteur van WYSIWYG. Voorafgaand aan deze moeilijke situatie, met TinyMCE 7 waren deze niet beschikbaar in de redacteursinterface.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>
* _ACP2E-3483_: De grootte van de redacteursdoopvont TinyMCE 7 in admin in PT en niet PX gelieve te verduidelijken
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie kon u doopvontgrootte in px in de gebieden van WYSIWYG niet specificeren. Nu kunt u de tekengrootte instellen in px in plaats van pt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3490_: Het Type van de Inhoud van het product in de Bouwer van de Pagina wordt samengevouwen zonder Correcte Berichten
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie werd voorproef HTML niet behoorlijk geproduceerd wanneer er geen producten in widget waren. De lege reactie wordt nu op de juiste wijze gegenereerd en de widget producten wordt in de voorvertoning op de juiste wijze weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3f12d152>, <https://github.com/magento/magento2-page-builder/commit/20aa5d7a>
* _ACP2E-3534_: [ pagina bouwer ] het Toevoegen van de Lijst van het Product om resultaten in fouten te blokkeren
   * _Bevestig nota_: Nu het toevoegen van de Lijst van het Product van de Bundel aan blok via paginabouwer resulteert niet in fouten
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/344fce23>

### Klanten/klanten

* _AC-12162_: Voorste eind - de bevestiging van de geboorte ontbreekt in de aanmaakpagina van de Klant
   * _nota van de Reparatie_: Verzeker al bevestiging zou na verbeteringsmoment.js systeemgebiedsdeel aan de recentste minder belangrijke versie moeten werken
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-8499_: Het de tekstgebied van het gebied wordt niet teruggesteld wanneer landdropdown wordt veranderd
   * _nota van de Reparatie_: Het systeem stelt nu het gebied van de gebiedstekst opnieuw in wanneer het land in het dropdown menu wordt veranderd, die ervoor zorgen dat de vorige waarden niet blijven bestaan. Als u voorheen het land uit de vervolgkeuzelijst wijzigde, werd het veld Regio niet opnieuw ingesteld, waardoor de laatst opgeslagen waarde behouden bleef.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: Het schrappen van Klant schoon niet Alle Browser Gegevens van de Zitting over Storefront voor binnen het programma gezette &amp; Geschrapte Klant
   * _Bevestig nota_: Het schrappen van een klant ontruimt nu alle gegevens van de browser zitting van de storefront voor het programma geopende en geschrapte klanten zoals verwacht. De winkelier kan blijven winkelen en hun browser behandelt hun sessie als een gastsessie. Eerder, toen de klantenrekening voor een het programma geopende verkoopster werd geschrapt van Admin, dan browser van de verkoopster de fouten van JavaScript verwierp.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7d5e3906>

### Kader

* _AC-10037_: [ vraag ] Ongebruikte configuratie van het Type in `app/code/Magento/Translation/etc/di.xml`
   * _Bevestig nota_: Het systeem verwijdert nu ongebruikte gebiedsdelen in de configuratie, die de algemene codeschoonheid en efficiency verbeteren. Eerder waren er ongebruikte afhankelijkheden in de configuratie die niet tot enige functionaliteit bijdroegen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38030>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38064>
* _AC-10654_: V1/klanten/wachtwoord eindvraag/kwestie
   * _nota van de Reparatie_: Het systeem houdt nu aan de beperkingen binnen beheer GUI worden geplaatst wanneer de verzoeken van de het wachtwoordverandering via API verwerken, die potentieel misbruik van de wachtwoordterugstellingfunctie verhinderen. Voorheen kon de API verzoeken om wachtwoordwijziging verwerken buiten de regels die zijn gedefinieerd in de GUI voor beheer, waardoor mogelijk een constante stroom e-mailberichten zou worden gemaakt als geldige e-mails bekend waren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38238>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10738_: De configuratie van de Varnish sluit niet alle marketing parameters uit
   * _nota van de Reparatie_: Het systeem sluit nu correct alle gemeenschappelijke marketing parameters in de configuratie van Varnish uit, die nauwkeurige het volgen en analyse verzekeren. Eerder waren bepaalde marketingparameters zoals gad_source, srsltid en msclchild niet uitgesloten, wat tot mogelijke onnauwkeurigheden in de gegevensverzameling leidde.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38298>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39188>
* _AC-10838_: Het proces van de het het procesfout van de het onderzoeksindex van de catalogus indexeren
   * _nota van de Reparatie_: Het systeem voltooit nu met succes het re-indexbevel zonder om het even welke fouten te ontmoeten, ongeacht de libxml versie die met PHP wordt gecompileerd. Eerder, resulteerde het runnen van het re-indexbevel in een &quot;fout van het proces van het het indexproces van het Onderzoek van de Catalogus tijdens indexeringsproces&quot;fout wanneer PHP met bepaalde versies van libxml werd gecompileerd.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38254>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _wisselstroom-10941_: Toegevoegde created_at, status en de filters Grand_total aan de vraag van de Orden van de klant en bevonden veelvoudige filtermislukking
   * _nota van de Reparatie_: Het systeem steunt nu het gebruik van created_at, status, en de filters Grand_total in de vragen van de Orden van de klant, en heeft een kwestie opgelost waar de veelvoudige filters niet correct werden toegepast. Eerder, steunde het systeem deze filters niet en zou er niet in slagen om alle filters toe te passen wanneer meer dan één in een vraag werd gebruikt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38392>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36949>
* _AC-10991_: Willekeurig overstroomd krijgen met vragen van verwant/upsell/crosssell blokken en prijs het indexeren
   * _nota van de Reparatie_: Het systeem optimaliseert nu vragen van verwant, upselt, en dwars-verkoopt blokken, verbeterend de prestaties en verhinderend de plaats om te gaan toe te schrijven aan bovenmatige vragen. Eerder, kon het systeem met vragen van deze blokken overbelast worden, veroorzakend significante vertragingen en potentieel verlamend de plaats.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36667>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Uitzondering: Waarschuwing: Het proberen om tot seriecompensatie binnen toegang te hebben.. -> Calendar.php sinds verbetering aan ICU 74.1 (PHP Intl)
   * _Opgeloste opmerking_: Commerce registreert de volgende uitzondering niet langer in de exception.log wanneer een shopper of verkoper de etalage of Admin bezoekt: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [ GitHub-38214 ](https://github.com/magento/magento2/issues/38214)
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38214>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [Probleem] Problemen met klantgegevens oplossen wanneer het formulier een element met een naam bevat `method`
   * _nota van de Reparatie_: Het systeem identificeert nu correct de &quot;methode&quot;attributen in vormvoorlegging, zelfs wanneer een element genoemd &quot;methode&quot;in de vorm aanwezig is. Dit zorgt voor een nauwkeurige verwerking van klantgegevens. Als een formulierelement voorheen de naam &#39;method&#39; had, zou dit problemen opleveren met de identificatie van het kenmerk &#39;method&#39; in formulierverzendingen, wat tot mogelijke problemen met de verwerking van klantgegevens zou leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38484>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [Issue] fix PHPDocs voor \Magento\Framework\Data\Collection::getItemById
   * _Fix-opmerking_: De PHPDocs voor de \Magento\Framework\Data\Collection::getItemById-methode zijn bijgewerkt om null op te nemen als een mogelijk retourtype, waardoor problemen met statische analysetools worden opgelost. Eerder, specificeerde PHPDocs van de methode ongeldig als mogelijk terugkeertype niet, dat tot waarschuwingen of fouten in statische analyse leidde toen de methode in voorwaardelijke verklaringen werd gebruikt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38485>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38439>
* _AC-11592_: [Probleem] Alleen geldige voorkeuren toestaan tijdens het instellen:di:van het compileren
   * _Fix-opmerking_: Het systeem genereert nu een foutmelding tijdens de setup-compilatieopdracht:di:als er een voorkeur wordt gemaakt voor een klasse die niet bestaat of specifiek is uitgesloten, zodat alleen geldige voorkeuren zijn toegestaan. Voorheen zouden deze scenario&#39;s geruisloos mislukken, waardoor alle plug-ins die aan de oorspronkelijke klassen waren gekoppeld, mogelijk onbruikbaar werden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38517>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/33161>
* _AC-11651_: Magento die probeert om read-only bezit in __wakeup methode van LoggerProxy te wijzigen
   * _nota van de Reparatie_: Het systeem staat nu de wijziging van eerder read-only eigenschappen in de methode __wakeup van LoggerProxy toe, die vlotte verrichting verzekert zonder gebruikers te dwingen om een alternerende actie aan te wenden. Eerder, zou een poging om de waarde van een read-only bezit in de methode __wakeup van LoggerProxy opnieuw toe te wijzen kwesties veroorzaken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38526>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_: [Uitgave] AC-2039 AC-1667 upgrade TinyMCE referenties
   * _Fix-opmerking_: Bijgewerkte tinymce nieuwste versie in composer.json
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38533>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker werkt niet in meerdere threads
   * _Fix-opmerking_: Het systeem ondersteunt nu procesvork voor MView-indexering, waardoor fouten tijdens de uitvoering van de indexeerfunctie worden voorkomen bij het werken op meerdere threads. Voorheen leidde het uitvoeren van de ChangelogBatchWalker op meerdere threads tot het verwijderen van tabellen die door andere threads werden gebruikt, waardoor een fout ontstond tijdens de uitvoering van de indexeerfunctie.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38246>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [Probleem] hernoemen verkeerd benoemde variabele
   * _Fix-opmerking_: Het systeem geeft nu de juiste naam van de variabele die het bedrag bevat dat nog kan worden terugbetaald, waardoor verwarring tijdens het debuggen wordt voorkomen. Eerder werd deze variabele onjuist benoemd als totalResund, wat tot misverstanden voor ontwikkelaars zou kunnen leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38609>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36205>
* _AC-11809_: [ geef ] douaneattributen van de Uitgave aan huidige verbinding via XML over
   * _nota van de Reparatie_: Het systeem staat nu douanekenmerken toe om tot de huidige verbinding via XML worden overgegaan, die ervoor zorgen dat deze attributen correct worden getoond zelfs wanneer de verbinding de huidige pagina is. Eerder werden er geen aangepaste kenmerken weergegeven voor de huidige paginakoppeling omdat de methode getAttributesHtml() niet werd gebruikt voor de huidige koppeling.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38500>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/30070>
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
* _AC-11874_: De achterwaartse verenigbaarheid is verloren op Magento\Catalog\Model\ProductRepository klasse
   * _nota van de Reparatie_: De klasse ProductRepository handhaaft nu achterwaartse verenigbaarheid door de klasse van de Helper van de Initialisatie als tweede parameter te herstellen, die ervoor zorgt dat de modules zich van deze klassenfunctie uitbreiden zoals verwacht. Eerder, resulteerde de schrapping van de Helper van de Initialisatie van de aannemer in de klasse ProductRepository in een verlies van achterwaartse verenigbaarheid, die gebruikers dwingt om een oplossing aan te wenden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38669>
* _AC-11905_: [ geef ] Statische inhoud uit - de fout van het Type
   * _nota van de Reparatie_: Het systeem behandelt nu correct lege dossiers LESS tijdens statische inhoudsplaatsing, tonend een &quot;LESS dossier is leeg&quot;foutenmelding. Eerder werd een fout met een onjuist type gegenereerd bij het optreden van een leeg LESS-bestand tijdens de implementatie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38682>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38683>
* _AC-12002_: [ Uitgave ] [ Mening ] Verwijderde extra ruimte in verbinding en manuscriptmarkering
   * _nota van de Reparatie_: Het systeem zorgt nu ervoor dat er geen extra ruimten in de verbinding en manuscriptmarkeringen zijn, die helderdere en efficiëntere code verstrekken. Eerder konden dubbele ruimten tussen attributen in de verbinding en manuscriptmarkeringen worden gevonden.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/32920>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/32919>
* _wisselstroom-12127_: [ Uitgave ] vermijdt een misconfiguration oneindige lijn
   * _Bevestig nota_: Het systeem vermijdt nu een oneindige lijn door zelfreferentiële afbeelding in virtuele typeconfiguraties te verhinderen. Dit zorgt ervoor dat de toepassing niet vastzit in een eindeloze lus wanneer wordt geprobeerd om een zelf-verwijzende knoop te dereference. Eerder, als een virtuele typeconfiguratie zelf-verwijzing was, zou het de toepassing veroorzaken om voor onbepaalde tijd te draaien.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38822>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: De Manager van objecten wordt niet gebruikt voor Magento\Csp\Model\Mode\Data\ModeConfigured
   * _nota van de Moeilijke situatie_: Het systeem gebruikt nu correct de Manager van Objecten wanneer het creëren van het voorwerp ModeConfigured, toestaand plugins om op dit voorwerp worden gebruikt. Eerder werd Objectbeheer niet gebruikt, waardoor plugins niet konden worden toegepast op het ModeConfigured-object.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38875>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38886>
* _AC-12540_: Onnauwkeurige doc-blokopmerking in productvoorraad- en prijswaarschuwingen
   * _Nota van de Oplossing_: De nota van het documentblok voor de deleteCustomer methode in de Aandelen van het Product en de Alarm van de Prijs is verbeterd om nauwkeurig te wijzen op dat de methode alle voorraadproduct of prijsalarm verbonden aan een bepaalde klant en een website, niet de klant van de website schrapt. Eerder werd in de opmerking onjuist aangegeven dat de methode bestond in het verwijderen van een klant van de website.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38939>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39001>
* _AC-12594_: [ Gecompileerde config van het Gebruik van de kwestie ] voor geproduceerde gegevens in plaats van algemene config
   * _nota van de Reparatie_: Het systeem gebruikt nu de gecompileerde configuratie voor geproduceerde gegevens in plaats van de algemene configuratie, die netwerkoverdracht en overheadkosten van gegevens vermindert die van een bepaalde versie van code afhangt. Door deze wijziging wordt voorkomen dat cache wordt overschreven in gedeelde instanties tijdens het wisselen van containers. Dit leidt tot betere stabiliteit en minder downtime. Eerder, gebruikten bepaalde kernklassen het gedeelde configuratietype, dat tot geheim voorgeheugen het met voeten treden of toepassingsonderbreking wegens verschillen in codeversies over veelvoudige servers kon leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38785>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [ Uitgave ] verwijdert verwijzingen naar dossiers uit extjs die in e1cdb werden verwijderd..
   * _nota van de Reparatie_: Het systeem verwijdert nu verwijzingen naar dossiers uit uitbreidingen die eerder werden verwijderd, eliminerend fouten in de browser console en het dossier van het systeemlogboek. Voorheen veroorzaakten deze verwijzingen fouten vanwege het ontbreken van de bestanden waarnaar wordt verwezen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38960>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38951>
* _AC-12778_: [ geef ] Kleine schoonmaak uit: het vaste verkeerde gebruik van sprintf, het neemt slechts 2 placeholders hier en w...
   * _nota van de Reparatie_: Het systeem gebruikt nu correct de functie sprintf met het aangewezen aantal placeholders, die codeschoonheid en consistentie verbeteren. Eerder werd de functie sprintf onjuist gebruikt met een extra argument, dat geen belangrijke kwesties veroorzaakte maar niet het correcte gebruik was.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39062>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38628>
* _AC-12857_: PHP 8.2.15 verwijderde de uitbreiding van FTP
   * _nota van de Reparatie_: Het systeem omvat nu de uitbreiding van FTP als gebiedsdeel in het composer.json- dossier, die de succesvolle configuratie van de invoer CSV via FTP verzekeren. Eerder werd een fout gegenereerd bij het configureren van CSV-import via FTP omdat de FTP-extensie ontbreekt in het PHP-pakket.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39083>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/47b448e2>
* _wisselstroom-12869_: [ de 3} Correcties van de Uitgave {onjuiste klassen die in de modules van Magento worden van verwijzingen voorzien.]
   * _nota van de Reparatie_: Het systeem verwijzingen nu correct klassen in modules, die vlottere verrichting verzekeren en neerstortingen wegens niet-bestaande klassen verhinderen. Dit omvat een bugfix in de modules Indexer en Creditmemo, en de implementatie van HttpGetActionInterface in de klasse PrintAction. Eerder, leidden de onjuiste klassenverwijzingen tot fouten en potentiële systeemneerstortingen, en bepaalde functionaliteiten, zoals filename voor creditmemo PDF dossiers en het opnieuw indexeren van voorraden, werkten niet zoals verwacht.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39126>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37784>
* _AC-12964_: Mogelijkheid om Gebied voor dev :di: info CLI bevel te bepalen
   * _nota van de Reparatie_: Het systeem staat nu ontwikkelaars toe om een gebied voor het dev :di: info CLI bevel te bepalen, dat de ontwikkeling en het het zuiveren proces verbetert. Eerder kon deze opdracht alleen informatie weergeven voor het GLOBAL-gebied.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38758>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38759>
* _AC-13149_: [ geef ] toe voeg isMultipleFiles bezit aan het malplaatje van het beeldvormelement toe
   * _nota van de Reparatie_: Deze moeilijke situatie, verhindert &quot;doorbladeren om beeld hier te vinden of te slepen&quot;knoop om te verdwijnen wanneer een beeld in een veelvoudige het vormelement van het dossierbeeld wordt toegevoegd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39219>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36325>
* _AC-13279_: [ Uitgave ] verwijdert alle marketing parameters krijgen om het geheime voorgeheugen te minimaliseren
   * _nota van de Reparatie_: Het systeem verwijdert nu alle marketing krijgen parameters om geheim voorgeheugengebruik te optimaliseren, die de logica weerspiegelen die wordt gebruikt wanneer Varnish in gebruik is. Eerder, konden deze parameters tot geheim voorgeheugenopblazing en verminderde prestaties leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39266>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [ Uitgave ] [ PHPDOC ] verbeter slechte phpdoc Magento\Directory\Model\AllowedCountries::getAllowedCountries ()
   * _nota van de Reparatie_: De PHPDoc voor AllowedCountries::getAllowedCountries () methode is verbeterd om nauwkeurige informatie te verstrekken, die de duidelijkheid en het nut van de documentatie verbetert. Eerder bevatte de PHPDoc voor deze methode onjuiste informatie, die tot verwarring of misbruik van de methode kon leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39246>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39241>
* _wisselstroom-13348_: [ Uitgave ] verwijdert één of andere code voor PHP versies die wij niet meer steunen.
   * _Bevestig nota_: Verwijdering van code voor PHP versies die niet meer in Magento worden gesteund
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39361>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [ geef ] van de Kwestie tot Adapter ImageMagick compatibel met php8 (Impliciete omzetting van vlotter aan int)
   * _nota van de Reparatie_: Het systeem verzekert nu verenigbaarheid met PHP8 door vlotteraantallen correct te behandelen wanneer het berekenen van beelddimensies, die om het even welke fouten te voorkomen toe te schrijven aan impliciete omzetting van vlotter aan int. Eerder kon de berekening van de afmetingen van de afbeelding leiden tot zwevende getallen, die bij impliciet afronden een fout zouden veroorzaken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39402>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [ Uitgave ] [ PHPDOC ] verbeter slechte phpdoc Magento\Framework\App\Config\ScopeConfigInterface
   * _nota van de Reparatie_: Deze update verbetert de annotaties PHPDoc in Magento\Framework\App\Config\ScopeConfigInterface om het type van het argument $scopeCode voor getValue en isSetFlag nauwkeurig te wijzen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39492>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/39199>
* _AC-13725_: Magento\Framework\Filesystem\Driver\Http is afhankelijk van de reden zin OK
   * _Fix-opmerking_: &quot;OK&quot;-zinscontrole verwijderd uit Magento\Framework\Filesystem\Driver\Http::isExists
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39546>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/39558>
* _AC-13810_: Customer Grid-indexer werkt niet goed in de modus Bijwerken volgens schema
   * _Fix-opmerking_: Eerder Klantenraster werd onmiddellijk bijgewerkt, maar na de oplossing Klantraster wordt bijgewerkt nadat cron is uitgevoerd, maar niet onmiddellijk wordt weergegeven.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_: typefout in een js-bestand.
   * _Fix-opmerking_: Het systeem gebruikt nu correct de term &quot;abonnees&quot; in het JavaScript-bestand, waardoor de juiste functionaliteit van de gerelateerde functies wordt gegarandeerd. Voorheen zorgde een typografische fout in het JavaScript-bestand voor het onjuist gebruik van de term &quot;subsctibers&quot;.
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
* _AC-8662_: [ Uitgave ] verbetert het registreren van de cron fout
   * _nota van de Reparatie_: Het systeem vangt en registreert nu zowel STDERR als STDOUT voor kroonprocessen, die waardevolle kenmerkende informatie in scenario&#39;s verstrekken waar de kroonprocessen ontbreken. Eerder, werden om het even welke foutenmeldingen binnen kroonprocessen niet geregistreerd, en STDERR en STDOUT voor kroongroepen die in afzonderlijke processen lopen werden verloren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37453>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32690>
* _wisselstroom-8984_: [ Uitgave ] voegt sommige meer kleuren aan de output van bepaalde opstellingskli bevelen toe
   * _nota van de Reparatie_: Het systeem voegt nu meer kleuren aan de output van bepaalde (CLI) bevelen van de opstellingsbevellijn toe, die leesbaarheid en gebruikerservaring verbeteren. Eerder was de uitvoer van deze opdrachten moeilijker te lezen vanwege een gebrek aan kleurdifferentiatie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/29335>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/29298>
* _AC-9630_: Bevorderend Magento stelt algemeen/gebied/state_required terug wanneer het nieuwe land met vereiste staat/gebied wordt toegevoegd.
   * _nota van de Reparatie_: Het systeem voegt nu slechts het gewijzigde land aan de &quot;algemene/regio/state_required&quot;configuratie toe wanneer een nieuw land met vereiste staten wordt toegevoegd, verhinderend om het even welke verstoring aan douanecode die veronderstelt het gebied gehandicapt is. Eerder, zou het toevoegen van een nieuw land met vereiste staten de &quot;algemene/regio/staat_required&quot;configuratie terugstellen om landen met een vereiste staat in gebreke te stellen, potentieel brekend de winkel.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37796>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38076>
* _AC-9712_: Verschil in minder compilatie tussen php &amp; nodejs library (grunt) met ingewikkelde `calc` expressies
   * _nota van de Reparatie_: Recht het verschil in minder compilatie tussen php &amp; nodejs bibliotheek (grot) na update wikimedia/less.php:^5.x
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/37841>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: Fout &quot;Basistabel of weergave niet gevonden&quot; treedt op wanneer gedeeltelijke indexering wordt uitgevoerd
   * _Fix note_: Gedeeltelijke herindexering werkt nu correct met grote changelog in het geval van secundaire db-verbinding
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: De kwesties na bevordering MariaDB aan 10.5.1 of hoger
   * _Bevestig nota_: Vaste de kwestie toen datetime waarden in een OB in 000-00-00 00 :00: 00 na verbetering Mysql zouden worden omgezet
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Typ Mismatch in Gegevensvergelijking bij het controleren of gegevens zijn gewijzigd
   * _nota van de Reparatie_: Eerder, werd het sparen voorwerp geroepen telkens zonder enige gegevensveranderingen (voor om het even welk numeriek gegevensgebied - zoals int/float/dubbel). Het activeert de markering _hasDataChanges om waar te zijn en roept de opslagfunctie aan. Nadat deze correctie is toegepast, wordt de functie Save alleen aangeroepen als de gegevens zijn gewijzigd. De gegevenswaarde voor int/float/double-check met de waarde die aan de functie wordt doorgegeven en strikte overeenkomende typen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [Cloudimport] kan niet worden gebruikt met directory var
   * _Fix-opmerking_: het product kan worden geïmporteerd, ongeacht de bestandsnaam.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: In ipad mini worden het menu en de header geladen als mobiel, in plaats daarvan moeten ze laden als desktop.
   * _Fix-opmerking_: het systeem behandelt apparaten met een breedte van 768px nu als desktop, zodat het menu en de header correct worden geladen. Voorheen werden apparaten met een breedte van 768px behandeld als mobiel, waardoor het menu en de header in een mobiele weergave werden geladen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3230_: Het wijzigen van kolomlengte via db_schema.xml werkt niet in het geval van buitenlandse sleutels
   * _nota van de Reparatie_: het wijzigen van kolom met buitenlandse sleutel via verklarend schema stijgt nu geen fouten met MariaDB
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: Enkele verbindingsverslagen worden bewaard aan OB wanneer het orderverslag wordt bewaard
   * _nota van de Reparatie_: Vóór de moeilijke moeilijke onnodige vragen van de UPDATE werden teweeggebracht die een effect prestaties kunnen hebben wijze. Na de moeilijke situatie, werden de onnodige vragen van de UPDATE geëlimineerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [ CLOUD ] In admin zijn er vele fout javascript in console
   * _nota van de Reparatie_: Eerder, in admin paneel zijn er vele fout javascript in console. In het deelvenster Beheer zijn er geen JavaScript-fouten in de console en worden alle standaard JavaScript-functies zonder problemen uitgevoerd.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [Cloud] Magento: wachtrij bericht is verwijderd
   * _nota van de Reparatie_: De berichten van de rij worden nu behoorlijk ontruimd. Voorafgaand aan de moeilijke situatie, aangezien SQL het rijsysteem werd gebruikt, konden de nieuwe berichten worden geschrapt als het bericht van de schoonmaakrij tezelfdertijd liep.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3537_: De overeenkomstige geheim voorgeheugenzeer belangrijke ingangen zijn niet beschikbaar in geheim voorgeheugenmarkeringen, vandaar geheim voorgeheugenreiniging niet correct werkt
   * _nota van de Reparatie_: De wijze van de LUA wordt nu toegelaten door gebrek voor de inzamelaar van het geheime voorgeheugen Redis om rassenvoorwaarden te verhinderen
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a52ff98f>
* _ACP2E-3681_: De waarde MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK wordt genegeerd
   * _nota van de Reparatie_: Na de moeilijke situatie, zal een variabele ENV die aan &quot;vals&quot;wordt geplaatst als bool vals, niet als koord &quot;vals&quot; worden behandeld.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/982b1c42>

### Framework, GraphQL

* _AC-7976_: [ Uitgave ] Ingevoerde steun van douane scalaire types voor het schema van GraphQL
   * _nota van de Reparatie_: Het systeem steunt nu douane scalaire types voor het schema van GraphQL, toestaand ontwikkelaars om douane scalaire types en implementaties te bepalen. Deze functie kan vooral handig zijn voor het uitdrukken van waarden die moeten worden gevalideerd, zoals HTML, e-mails, URL&#39;s, datums, enzovoort, en voor meer geavanceerde gevallen zoals EAV-kenmerken. Eerder, steunde het systeem niet de verwerking van douane scalaire types in GraphQL.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36877>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/34651>, <https://github.com/magento/magento2/commit/0574ac23>

### Framework, UI Framework

* _ACP2E-3324_: Mogelijkheid om configuratiewaarde te beschrijven zelfs als het gesloten is
   * _nota van de Reparatie_: Eerder aan deze moeilijke situatie, kon de ontwerpconfiguratie niet door bak/magento config worden geplaatst:vastgestelde bevel en gesloten waarden konden door manipulatie van de vorm worden veranderd die hen toont. Nadat de fix vergrendelde waarden zijn ingesteld vanuit cli met —lock-env of —lock-conf, kunnen deze niet meer worden bijgewerkt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>

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
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Gelaagde navetion uitschakelen - Verwijdert geen aggregatie uit Graphql
   * _nota van de Reparatie_: De kwestie is opgelost na het toepassen van de controle terwijl het verzoeken van een productonderzoek met categoriesamenvoegingen door een vraag van GraphQL wanneer admin configuratie die &quot;Catalogus > Gelaagde Navigatie > de Filter van de Categorie van de Vertoning&quot;plaatst.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: De vraag van de Producten van GraphQL die de prijsfilter {van bevat:&quot;0&quot;} keert geen resultaat terug
   * _nota van de Reparatie_: Eerder grafisch productonderzoek met filter voor nulprijzen retourneerde geen resultaten bij allen toe te schrijven aan een geworpen uitzondering. De zoekopdracht geeft nu resultaten zoals verwacht.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_: Vertalingen voor de attributen van de klantenterugkeer die niet in GraphQL API voor respectievelijke StoreView worden weerspiegeld
   * _nota van de Oplossing_: De vertalingen voor de attributen van de klantenterugkeer worden weerspiegeld in GraphQL API voor respectieve StoreView.
Eerder werden de teruggavekenmerken van de klant voor de respectievelijke StoreView niet weerspiegeld in de GraphQL API.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_: [ de Verbroken vraag van GraphQL van de Wolk ] voor getPurchaseOrder met knoopcitaat
   * _Fix-opmerking_: De Purchase Order GraphQL-aanroep kan de taak uitvoeren zonder interne serverfouten tegen te komen.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [In de cloud] configureerbare producten worden niet weergegeven op de productiesite als het product niet is ingeschakeld in &quot;Alle winkelweergaven&quot;
   * _Fix-opmerking_: het systeem geeft nu configureerbare producten correct weer op de site, zelfs als het product niet is ingeschakeld in &quot;Alle winkelweergaven&quot;, maar wel is ingeschakeld in specifieke winkelweergavebereiken.
Als een product voorheen was uitgeschakeld in &#39;Alle winkelweergaven&#39; en alleen was ingeschakeld in specifieke winkelweergavebereiken, werden de productkenmerken niet correct weergegeven in de GraphQL-reactie, waardoor het product niet correct werd weergegeven.
   * _Bijdrage GitHub-code_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: [ de Grafiek van de Producten van de Wolk ] die fout hebben wanneer het zelfde eenvoudige product aan veelvoudige configureerbare producten heeft toegewezen
   * _nota van de Reparatie_: Eerder, met afzonderlijke configureerbare producten met het zelfde eenvoudige product, keert grapQL een fout terug. Nadat deze moeilijke situatie van toepassing is, verschillende configureerbare producten met het zelfde eenvoudige product, geeft grapQL resultaat zonder geen fout.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_: [ Cloud ] Kwestie met de Authentificatie van de Gebruiker en de Symbolische Toegang van de Intersite in de Opstelling van de Multi-Plaats
   * _Bevestig nota_: Info van de Klant GraphQl en de vragen van de Kaart in de opstellingscontroles van de MultiSite als de klant op niet-standaard website bestaat.
Eerder uitgevoerde query werkte zonder ervoor te zorgen dat de klant op een niet-standaard website in de installatie van meerdere sites aanwezig was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_: De paginering van GraphQL karretjesV2 werkt niet correct
   * _Fix-opmerking_: het probleem is opgelost door de juiste waarde voor het huidige pagina-argument door te geven in de verzamelingsquery. Voorheen werd de verkeerde waarde doorgegeven om de huidige pagina in te stellen, wat het probleem veroorzaakte.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3255_: [GRAPHQL-modelwaarde] moet worden gespecificeerd bij het ophalen van customerCart
   * _Fix-opmerking_: De GraphQL &#39;customerCart&#39;-query kan nu een lege winkelwagen maken, zelfs als de offerte niet beschikbaar is in de database. Voorheen mislukte deze bewerking vanwege problemen met de landvalidatie tijdens het maken van de lege winkelwagen.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [ GraphQl ] de punten van de Schitlijst zijn zichtbaar via GraphQl maar niet zichtbaar op opslag
   * _nota van de Reparatie_: De producten van het Wislist waar niet behoorlijk worden vermeld wanneer gevraagd via GraphQL. Welnu, de producten van vorklijsten worden gefiltreerd gebaseerd op verstrekte archiefcontext.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [ GraphQL ] het wachtwoord e-mailinconsistentie van het Terugstellen tussen inhoud en onderwerp/verbinding
   * _nota van de Reparatie_: De kwestie is opgelost door de correcte opslag te simuleren waar de rekening van de klant wanneer het verzenden van het verzoek van het wachtwoordterugstellen, ongeacht de websiteopslag wordt geregistreerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: [Cloud] products GraphQL query retourneert gerelateerde producten die niet zijn toegewezen aan de huidige website
   * _Fix-opmerking_: Voorheen werden voor graphQL-query&#39;s multi-store-gerelateerde producten niet correct weergegeven voor productquery&#39;s. Nadat deze correctie is toegepast, voert graphQL voor producten een query uit op producten die verband houden met meerdere winkels en dienovereenkomstig worden weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: Het gebruik van de verkeerde Store-ID in de GraphQL-header veroorzaakt een fatale geheugenfout
   * _nota van de Reparatie_: Het verzenden van verkeerde opslagcode in GraphQL verzoek resulteert niet meer in bovenmatig geheugengebruik.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_: [ Cloud ] 500 reactie op lege Grahql op 2.4.7
   * _nota van de Reparatie_: Na de moeilijke situatie, zullen de ongeldige grafische verzoeken niet in het exception.log dossier worden geregistreerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3492_: [ Cloud ] Problemen met Grahql API
   * _nota van de Reparatie_: Vóór de moeilijke situatie door de toepassingsserver van Grafiek te gebruiken, kwam het verzoek van het klantenadres niet de meest recente gegevens terug.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3505_: Het gehandicapte product verschijnt nog in verwant, upsell, dwarselt punten in vraag grpahQL
   * _Nota van de Moeilijke situatie_: Grahql verstrekt nu correcte reactie voor gehandicapte verwante, upsell en dwars-verkoopt producten
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3647_: [ CLOUD ]: De fout van GraphQl Interne de mutatie van de serverfout placeOrder
   * _nota van de Reparatie_: De &quot;placeOrder&quot;mutatie met couponcodeinformatie in het verzoek produceert niet meer een interne foutenuitzondering, werd de orde met succes geplaatst. Eerder is dit mislukt met &quot;Interne serverfout&quot;.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/982b1c42>
* _LYNX-426_: Het disconto_percentage wordt niet berekend voor bundelproducten met dynamische prijs
   * _Nota van de Moeilijke situatie_: Bevel toegevoegd voor disconto_percentage van product.price_details die de correcte waarde voor bundelproducten tonen met dynamische toegelaten prijs en toegepaste kortingscoupon.
* _LYNX-485_: De producten van de bundel tonen nog &quot;IN_STOCK&quot;wanneer één van zijn gebundeld product uit voorraad
   * _Bevestiging nota_: Los de kwestie op waar de bundelproducten nog &quot;IN_STOCK&quot;tonen zelfs wanneer één van hun gebundelde producten uit voorraad was.
* _LYNX-486_: not_available_message en only_x_left_in_stock toont niet de zelfde beschikbare voorraad
   * _nota van de Reparatie_: Los de kwestie op waar not_available_message en only_x_left_in_stock inconsistente voorraadbeschikbaarheid tonen
* _LYNX-488_: original_row_total gebied die onjuiste waarde terugkeren
   * _Bevestig nota_: Los de kwestie met het original_row_total gebied op, dat onjuiste waarden teruggaf toen de douaneopties werden geselecteerd
* _LYNX-503_: De gegroepeerde productduimnagel zou volgens de configuratie moeten worden getoond     .
   * _nota van de Reparatie_: Los de kwestie op om de gegroepeerde productduimnagel volgens de configuratiemontages te verzekeren wordt getoond
* _LYNX-512_: original_item_price is exclusief kortingen
   * _Bevestig nota_: Bijgewerkt original_item_price om kortingen te omvatten.
* _LYNX-530_: Het niet beschikbare bericht toont niet de beschikbare inventarishoeveelheid
   * _nota van de Reparatie_: Los het foutenmelding en de foutencode voor de mutatie AddProductsToCart op om met de &quot;niet beschikbare&quot;berichtconfiguratie te richten
* _LYNX-532_: &quot;OUT_OF_STOCK&quot;statuswinst op Eenvoudig met de producten van douaneopties met multi-uitgezochte opties
   * _nota van de Reparatie_: Bijgewerkt StockStatusProvider resolver in het inventarispakket om stock_status voor eenvoudige producten met douaneopties te bevestigen.
* _LYNX-533_: Fout (GQL): cart.itemsV2.items.product.custom_attributesV2 keert een serverfout terug
   * _nota van de Reparatie_: Los de serverfout op die voorkwam wanneer een kartvraag de douaneattributen van een product door een product zonder enige douanekenmerken toe te voegen omvatte.
* _LYNX-536_: orden/date_of_first_order altijd terugkerend ongeldig
   * _Bevestig nota_: Los de kwestie op waar de orden > date_of_first_order altijd ongeldig terugkwamen.
* _LYNX-544_: De klant mag een gedeeltelijk verzonden bestelling niet kunnen annuleren
   * _Fix-opmerking_: validatie is toegevoegd om te voorkomen dat klanten een gedeeltelijk verzonden bestelling kunnen annuleren.
* _LYNX-548_: Foutcodes voor het annuleren van bestellingen op basis van de foutmelding
   * _Fix-opmerking_: De foutcodes voor het annuleren van bestellingen zijn nu gebaseerd op het specifieke foutbericht.
* _LYNX-581_: Beweeg terug koekjesgerelateerde eigenschappen van privé aan beschermde
   * _Nota van de Reparatie_: Keert de eigenschappen van de Magento\Framework\App\PageCache\Version klassenaannemer van privé aan beschermde
* _LYNX-600_: De maximum standaardGraphQL vraagingewikkeldheid van de verhoging aan 1000
   * _nota van de Reparatie_: Verhoogde standaard maximumingewikkeldheid van de vraag van GraphQL van 300 tot 1000.
* _LYNX-620_: GQL - itemsV2 > Origineel rijtotaal, de prijzen van de prijswaaier zijn teruggekeerd als $0.00 voor downloadbaar product met dossieropties die afzonderlijke prijzen hebben.
   * _nota van de Reparatie_: Los een kwestie op waar de downloadbare producten met afzonderlijke toegelaten verbindingsaankoopopties $0 voor itemsV2 > Oorspronkelijk rijtotaal teruggaven, als $0.00 voor producten met dossieropties die afzonderlijke prijzen hebben teruggekeerd.
* _LYNX-772_: Verenigbaarheid GraphQl voor PHP-8.4 Versie
   * _nota van de Oplossing_: Vaste de compatibiliteitskwesties van GraphQL met PHP 8.4 over veelvoudige resolvers, die vlotte functionaliteit verzekeren. Gewijzigde bestanden in de modules CatalogRule, Klant, Cadeaubericht, Cadeaukaart en Cadeauverpakking.

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
* _ACP2E-948_: De lijst van het product GraphQL vraag beperkt tot total_count 10.000 slechts producten
   * _nota van de Reparatie_: Na de moeilijke situatie, is het onderzoeksresultaat niet beperkt tot 10000 producten, wordt het mogelijk om alle producten te krijgen die aan de onderzoekscriteria voldoen zelfs als de telling meer dan 10000 is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, testkader

* _ACP2E-3363_: Magento\GraphQl\App\GraphQlCustomerMutationsTest.php de mislukking van de Test van de Integratie
   * _Bevestig nota_: &quot;-
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4cf5e62>

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
* _ACP2E-3172_: Ontbrekende knoop van de Invoer
   * _Bevestig nota_: Los de knoop van de Invoer ontbrekende kwestie na gegevenscontroles met correcte en onjuiste verslagen in CSV op. Eerder wordt de knop Importeren niet weergegeven na gegevenscontroles met juiste en onjuiste records in de CSV.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: Geëxporteerd klantadres kan niet worden geïmporteerd
   * _nota van de Reparatie_: De het adresinvoer van de klant zal zoals verwacht te werk gaan. Voorheen zou een bestand met het importeren van klantadressen geen validatie doorstaan als Share Customer Accounts = Global, en er zijn twee websites waar de standaardwebsite een lijst met landen met beperkingen heeft en het adres dat wordt geïmporteerd, geldt voor een andere website waar toegestane landen verschillend zijn
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [ de Verkeerde hoeveelheid van de Wolk ] in Csv- dossier gaf geen fout
   * _nota van de Reparatie_: Nu zal de invoer van voorraadbronnen bevestigingsfout voor niet numerieke waarden in de kwantitatieve kolom werpen. Eerder werd bij het importeren van voorraadbronnen met een niet-numerieke waarde in de kolom Hoeveelheid de hoeveelheid ingesteld op 0.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3455_: Het gedupliceerde zeer belangrijke die foutenmelding URL wanneer het invoeren van een product wordt geproduceerd is niet correct wanneer Sleutel URL reeds tot een categorie behoort
   * _nota van de Reparatie_: Het tonen van het correcte foutenbericht tijdens de controle van de productinvoer, wanneer de klant probeerde om product in te voeren wanneer de url van het product reeds tot een categorie behoort.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3475_: De uitvoer van het product veroorzaakt OOM zelfs met 4G geheugengrens
   * _nota van de Reparatie_: Vorig aan deze moeilijke situatie, ontbrak de productuitvoer als de productattributen duizenden optiewaarden zelfs met 4G beschikbaar geheugen hadden. Na deze correctie moet het exportbestand van het product het CSV-bestand hebben geëxporteerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3527_: [ de processen van de Invoer van de Wolk ] Interfering met elkaar
   * _nota van de Reparatie_: De correcte berichten worden getoond als de zelfde admin gebruiker twee of meer invoerverrichtingen gebruikend de zelfde gebruikerszitting uitvoert.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d4de4726>

### Importeren/exporteren, prestaties

* _ACP2E-3476_: [ de invoertijd van het Product van de Wolk ] is beduidend gestegen
   * _nota van de Reparatie_: Vorig aan de moeilijke situatie, de invoer van het catalogusproduct met meer dan 10K ingangen had een significante tijddegradatie. Na de correctie wordt het importeren van het catalogusproduct tijdig uitgevoerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/87d012e5>

### Installeren en beheren

* _AC-13242_: De verbetering van Magento ontbreekt op MariaDB 11.4 + 2.4.8-bèta1
   * _Bevestig nota_: De verbetering zou zonder enige fout moeten gebeuren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7b336d0a>
* _ACP2E-2102_: Geen VCL van de Uitvoer voor Varnish 7 knoop in admin paneel
   * _nota van de Reparatie_: &quot;De knoop van de Uitvoer VCL voor Varnish 7&quot;werd toegevoegd aan het Admin paneel.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventaris/MSI

* _AC-10750_: De update van de inventaris van het Configurable Product ontbreekt wanneer het gegevensbestand prefixen gebruikt
   * _nota van de Reparatie_: Het systeem werkt nu correct de inventaris van configureerbare producten bij wanneer het gegevensbestand prefixen gebruikt, die om het even welke foutenmeldingen verhinderen en ervoor zorgen dat het correcte aantal wordt bewaard. Eerder, zou een fout voorkomen wanneer het proberen om de inventarishoeveelheid voor eenvoudige producten binnen een configureerbaar product te bewaren als het gegevensbestand prefixen gebruikte.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38045>
* _AC-11593_: De sleutel van Google google API werkt niet terwijl het toevoegen van Kaart met attributen
   * _nota van de Reparatie_: Het systeem steunt nu de recentste versie 3.56 van de Kaarten API van Google, toestaand gebruikers om een de inhoudsblok van de Kaart van het menu PageBuilder aan het stadium met succes toe te voegen zonder om het even welke fouten te ontmoeten. Eerder konden gebruikers geen Map-inhoudsblok toevoegen vanwege compatibiliteitsproblemen met de Google Maps API-versie. Dit leidde tot een foutbericht dat er iets fout was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_: Onbekwaam om verzending voor ordepunt met veelvoudige bronnen en bedorven SKU tot stand te brengen
   * _nota van de Reparatie_: Eerder toen de ruimten door gegevensbestand verkeerd werden toegevoegd tot fout in ladingspagina leidt die nu vast is en de automatische bijsnijding wordt beschouwd als menselijke vriendschappelijke fout en geen effect werd gevonden.Daarom werd de lading met succes gecreeerd.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_: [ de producten van de Bundel van de Test ] met 0 voorraad die op opslagvoorzijde tonen
   * _Fix:_ Het bundelproduct wordt niet weergegeven op de extra websites die extra voorraad gebruiken.
* _ACP2E-2794_: [ de Kritieke Kwestie van de Wolk ] met Product dat met Lege Plaatsen van een lijst maakt
   * _nota van de Reparatie_: Het systeem toont nu correct productlijsten zonder lege ruimten wanneer de producten aan &quot;uit voorraad&quot;worden geplaatst, die een verenigbare en nauwkeurige vertoning van beschikbare producten verzekeren. Als u een product eerder instelt op &#39;Uit voorraad&#39;, wordt er een lege ruimte weergegeven in de productlijst, waardoor de layout wordt verstoord en klanten mogelijk in verwarring raken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_: Onbekwaam om de orde te verschepen wanneer MSI ophaalopslag wordt toegelaten
   * _Nota van de Reparatie_: Verbeterde inventarisprestaties van creeer het verschepen in het geval van vele bronnen met in-store bestelwagen
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: De Cron herdex ontbreekt om productbeschikbaarheid op frontend bij te werken
   * _nota van de Reparatie_: Eerder, bleven de Producten uit voorraad op het front na het bijwerken van de backorderstatus door REST API. Nadat u de status van de backorder hebt bijgewerkt via de REST API, worden de producten weergegeven als in voorraad.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: Het toevoegen van beelden aan configureerbaar niet werkend wanneer MSI wordt toegelaten.
   * _nota van de Reparatie_: Het beeld uploadt voor configureerbaar product zal nu zoals verwacht werken wanneer de inventarismodule wordt gebruikt. Eerder werkte het uploaden van de afbeelding niet
   * _Bijdrage GitHub-code_: <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_: Uitgave met Bundel Product + MSI in Schone M2.4.7-p3
   * _Fix-opmerking_: Voorheen kon het eenvoudige product niet worden opgeslagen voor voorraadbundelproducten na duplicatie met hetzelfde eenvoudige product. Nadat deze oplossing is toegepast, kan het eenvoudige product zonder uitzonderingen met succes worden opgeslagen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39358>
   * _Bijdrage GitHub-code_: <https://github.com/magento/inventory/commit/0208e433>

### Inventaris/MSI, zoeken

* _ACP2E-3413_: Alle producten worden geïndexeerd met [ is_out_of_stock ] = 1 wanneer SKU niet als onderzoekbaar attribuut wordt geplaatst
   * _nota van de Reparatie_: Na de moeilijke situatie, is &quot;is_out_of_stock&quot;in de index van het catalogusonderzoek correct, zelfs wanneer de huid niet doorzoekbaar is.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/5b21b7af>

### Volgorde

* _wisselstroom-10828_: Het scherm van het het overzicht van de orde van de achtergrond: Achtergeordende hoeveelheid niet zichtbaar op het niveau van het orde punt
   * _nota van de Reparatie_: Het systeem toont nu het aantal backordered punten in de kwantitatieve kolom op het scherm van het overzicht van de achterste orde. Dit zorgt ervoor dat de gebruikers de status van alle punten in een orde nauwkeurig kunnen volgen. Eerder gaf de kolom Aantal alleen het aantal objecten weer dat was besteld, gefactureerd en verzonden, maar niet het aantal objecten met een backorder.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38252>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38320>
* _AC-10994_: [Uitgifte] Verkeerde winkel-ID gebruikt in Order Address Renderer
   * _nota van de Reparatie_: Het systeem gebruikt nu correct opslagidentiteitskaart verbonden aan een orde wanneer het teruggeven van het ordeadres, die ervoor zorgen dat de adressen correct volgens hun respectieve opslagidentiteitskaart worden geformatteerd. Eerder gebruikte het systeem onjuist de huidige winkel-id, wat tot een onjuiste adresnotatie kan leiden wanneer meerdere bestelling-e-mails van verschillende winkels moeten worden verzonden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38412>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37932>
* _AC-11690_: Probleem met JoinProcessor caching
   * _Fix-opmerking_: het systeem past nu de JoinProcessor correct toe voor elke iteratie, zelfs met opeenvolgende aanroepen, waardoor nauwkeurige gegevensverzameling wordt gegarandeerd. Voorheen werd de JoinProcessor ten onrechte gemarkeerd als reeds toegepast in opeenvolgende iteraties, wat leidde tot fouten bij het ophalen van gegevens.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/27504>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/37550>
* _AC-11798_: [Uitgifte] Verzendprijs toont anders in gedrukte pdf
   * _nota van de Reparatie_: Het systeem toont nu correct de verschepende prijzen in gedrukte PDFs volgens de montages van de belastingconfiguratie, die consistentie tussen de de meningspagina van de verkooporde van de factuur en de gedrukte factuur verzekeren. Eerder was de verzendprijs die in de afgedrukte PDF werd weergegeven exclusief belasting, ongeacht de instellingen voor de belastingconfiguratie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38608>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _wisselstroom-13839_: Opnieuw orde met een geschrapt ouder configureerbaar product
   * _nota van de Reparatie_: Nu terwijl het opnieuw rangschikken met het geschrapte product zal het systeem niet de reorder knoop tonen om opnieuw te rangschikken
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39568>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39601>
* _AC-13924_: [ Kwestie ] verbeter slecht \Magento\Sales\Model\Order\Email\Container\Template:$id bezit
   * _Bevestig nota_: Dit moeilijke phpdoc voor \Magento\Sales\Model\Order\Email\Container\Template::$id, eigenlijk is $id type int maar in werkelijkheid is koord.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39151>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_: Kan wijzigingen in het telefoonnummer niet opslaan in bestaande bestelgegevens
   * _Fix-opmerking_: nu kan de gebruiker het internationale voorvoegsel 00 toevoegen in het telefoonveld van het besteladres
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38201>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: De e-mail ontbreekt om te verzenden
   * _nota van de Reparatie_: Het systeem omvat nu een configuratieoptie async_sending_probeerde om het aantal pogingen te specificeren om een e-mail te verzenden alvorens te stoppen, verbeterend de behandeling van ontbroken e-mail verzendt wanneer &quot;Asynchroon verzenden&quot;wordt toegelaten. Als het verzenden van een e-mail mislukt, probeert het systeem het bericht voortdurend opnieuw te verzenden, wat resulteert in een eindeloze lus met foutberichten in het systeemlogboek.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [ de Status van de Orde van de Wolk ] veranderde om te voltooien wanneer gedeeltelijk terugbetaling van een gedeeltelijk verscheepte orde
   * _Fix-opmerking_: bij het uitgeven van een creditnota wordt de bestelstatus niet langer gewijzigd in &quot;voltooid&quot; als er artikelen zijn die nog niet zijn verzonden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [ CLOUD ] kan verzenden geen E-mail van Admin UI onbruikbaar maken aangezien Dev Docs toont
   * _nota van de Reparatie_: Het systeem verhindert nu correct verkoope-mails worden verzonden wanneer de e-mailmededeling wordt onbruikbaar gemaakt. Deze e-mailberichten worden niet meer verzonden wanneer de e-mailcommunicatie opnieuw wordt ingeschakeld. Eerder werden e-mailberichten over verkopen die waren gestart terwijl e-mailcommunicatie was uitgeschakeld, nog steeds verzonden zodra de e-mailcommunicatie opnieuw was ingeschakeld.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Bestelling gesloten zonder volledige terugbetaling
   * _Fix-opmerking_: het systeem handhaaft nu correct de orderstatus als &#39;Verwerken&#39; en de factuurstatus als &#39;In behandeling&#39; wanneer een bestelling met een niet-gevangen betaling een zending heeft gemaakt. Dit zorgt ervoor dat bestellingen pas als &#39;Gesloten&#39; worden gemarkeerd nadat ze volledig zijn terugbetaald. Voorheen werd bij het maken van een zending voor een bestelling met een factuur in behandeling de orderstatus ten onrechte gewijzigd in &#39;Gesloten&#39;.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_: [ de Wolk ] kan orde in admin op één opslag tot stand brengen als slechts het Standaard het Factureren Adres niet opstelling was
   * _Bevestig nota_: Nu relevant foutenmelding &quot;een klant met het zelfde e-mailadres bestaat reeds in een bijbehorende website.&quot; wordt getoond als een klant geen Standaard het Factureren Adres heeft en probeert om een orde op een andere opslag tot stand te brengen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Admin gedupliceerde verzonden verzoeken van de plaatsorde
   * _nota van de Reparatie_: Eerder, kon de &quot;Submit knoop van de Orde&quot;in het admin paneel veelvoudige tijden worden geklikt of door herhaaldelijk te drukken &quot;binnengaan&quot;sleutel, veroorzakend dubbel of ordebijdragen met fout. Nu, het voorkomen van extra acties totdat de bestelling volledig is verwerkt, ervoor zorgen dat er slechts één bestelling wordt ingediend.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: Beheerder kan nog steeds een bestelling plaatsen, zelfs zonder betaalmethode
   * _Fix-opmerking_: Eerder geselecteerde betaalmethode wordt nu behouden wanneer de betaalmethode opnieuw verschijnt in de lijst met beschikbare betalingen.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Bestelling, Betalingen

* _ACP2E-3233_: Admin kan orde zelfs zonder betalingsmethode nog plaatsen
   * _nota van de Reparatie_: Eerder, kon de handelaar orden van het admin paneel plaatsen zonder een betalingsmethode te selecteren. Nu is de handelaar verplicht een betalingsmethode te gebruiken om een bestelling te plaatsen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Bestellen, Retourneren

* _ACP2E-2982_: Terugbetaling van bestelling resulteert in dubbele creditnota
   * _nota van de Oplossing_: Het uitgeven van de teruggave over REST API wanneer twee identieke verzoeken gelijktijdig werden uitgevoerd zal niet meer dubbele Kredietmemo&#39;s creëren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>

### Bestelling, belasting

* _ACP2E-3003_: [ CLOUD ] Onjuiste base_row_total in RESTFUL orde API wanneer het toelaten van grensoverschrijdende transacties en het toepassen van couponkortingen
   * _Bevestig nota_: Nu correct base_row_total is teruggekeerd van orde RESTFUL API wanneer de grensoverschrijdende transactie wordt toegelaten en de couponkorting wordt toegepast.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/9af794a4>

### Overige

* _LYNX-339_: privé_content_version koekje dat in vragen GQL is teruggekeerd
   * _Bevestig nota_: Vaste een kwestie waar het privé_content_version koekje in de vragen van GraphQL werd teruggekeerd, zelfs toen het zittingskoekje werd onbruikbaar gemaakt. Het cookie wordt niet meer opgenomen in GraphQL-reacties wanneer de sessie is uitgeschakeld, zoals u had verwacht.
* _LYNX-380_: is_available attributen in CartItemInterface keert altijd vals voor configureerbare producten terug
   * _Opgeloste opmerking_: Er is een probleem opgelost waarbij het is_available-kenmerk in CartItemInterface altijd onwaar retourneerde voor configureerbare producten die op voorraad waren. Nu wordt beschikbaarheid correct weergegeven als waar, indien van toepassing.
* _LYNX-382_: is_available attribuut in CartItemInterface retourneert waar, zelfs wanneer de verkoopbare voorraad lager is dan de hoeveelheid van het product
   * _Fix-opmerking: Opgeloste het_ probleem waarbij het is_available-attribuut in de CartItemInterface ten onrechte true retourneerde, zelfs wanneer de hoeveelheid winkelwagenartikelen de verkoopbare voorraad overschreed.
* _LYNX-399_: De placeholder duimnagel keert terug wanneer een eenvoudig product aan kar binnen een gegroepeerd product wordt toegevoegd
   * _nota van de Reparatie_: Vaste een kwestie waar het toevoegen van een eenvoudig product (deel van een gegroepeerd product) aan de kar een placeholder duimnagelbeeld teruggaf, zelfs wanneer het product een toegewezen beeld had.
Details herstellen:
・ De miniatuur van het product geeft nu correct de toegewezen afbeelding weer, indien beschikbaar.
・ De miniatuurselectie respecteert de onderstaande beheerdersconfiguratie:
Winkels > Configuratie > Verkoop > Afhandeling > Winkelwagentje > Gegroepeerde productafbeelding.
Dit zorgt voor consistent miniatuurgedrag voor gegroepeerde producten op basis van opslaginstellingen.
* _LYNX-400_: De attributen van de douaneoptie van de klant die niet met geheelwaarden werken
   * _Bevestig nota_: Vaste een kwestie waar de attributen van de douaneoptie van de klant niet werkten wanneer de teruggekeerde waarde een geheel was. De aangepaste opties verwerken nu correct de waarden van gehele getallen en retourneren deze zoals verwacht.
* _LYNX-402_: Interne serverfout wanneer het proberen om priceDetails voor de producten van de Bundel met dynamische prijs te krijgen
   * _Bevestig nota_: Los een kwestie op waar het vragen van price_details voor bundelproducten met dynamische tarifering via GraphQL in een interne serverfout resulteerde. Deze verbetering verzekert stabiele wortelvragen wanneer het werken met bundelproducten die met dynamische tarifering worden gevormd.
* _LYNX-403_: only_x_left_in_stock keert altijd 0 voor configureerbare producten terug
   * _nota van de Reparatie_: Los een kwestie op waar het only_x_left_in_stock attribuut altijd 0 voor configureerbare producten terugkeerde wanneer toegevoegd gebruikend ouderSKU met opties.
Details herstellen:
・ De waarde only_x_left_in_stock geeft nu nauwkeurig de voorraad van de geselecteerde kindvariant in plaats van bovenliggende SKU weer.
・ Dit zorgt ervoor dat de voorraadniveaus correct worden getoond voor configureerbare productvariaties in de kar en productpagina&#39;s.
* _LYNX-411_: De vraag van GraphQL keert geen correcte berekende regelmatige prijs voor klantgerichte producten terug
   * _Bevestig nota_: Vaste een kwestie waar GraphQL niet de correcte berekende regelmatige prijs voor klantgerichte producten terugbracht. De vraag omvat nu correct de berekende regelmatige prijs met aanpasbare toegepaste waarden (b.v., $125) in het prijsbezit, dat zowel de basisprijs als om het even welke extra aanpassingskosten weerspiegelt.
* _LYNX-412_: AppliedTaxes via EstimatedTotals blijven met bijgewerkte mutaties
   * _Bevestig nota_: Vaste een kwestie met de Mutatie EstimatedTotals waar de toegepaste belastingen op een kar zelfs na het bijwerken van het gebied of postcode voortvloeiden. De mutatie werkt nu correct de toegepaste belastingen bij wanneer het veranderen tussen regio en postcode waarden, die ervoor zorgen dat slechts de correcte belastingregel op de huidige kartgegevens wordt toegepast.
* _LYNX-420_: is_available attributen in CartItemInterface keert waar terug zelfs wanneer de verkoopbare voorraad lager is dan de hoeveelheid van het product
   * _nota van de Reparatie_: Vaste een kwestie waar is_available attribuut in CartItemInterface verkeerd waar terugkeerde zelfs wanneer de verkoopbare voorraad lager was dan de gevraagde producthoeveelheid. Het veld is_available retourneert nu correct false wanneer de hoeveelheid van het product groter is dan de beschikbare voorraad.
* _LYNX-425_: De regelmatige prijs van het product met 12 decimalen en verkeerde waarde
   * _Bevestiging nota_: Vaste een kwestie waar de regelmatige_prijswaarde in product.price_range.maximum_price en minimum_price de wegen van GraphQL niet de catalogusprijs overeenkwamen toen de veelvoudige belastingtarieven werden toegepast. Reguliere_price weerspiegelt nu consistent de catalogusprijs over alle belastingconfiguraties, die nauwkeurige eenheidsprijzen, totale rijkostenberekeningen, en kortingscontroles in de Samenvatting van de Objecten verzekeren verzekeren.
* _LYNX-430_: De serverfout van GraphQL op karretje met uit voorraad gebundeld product
   * _Bevestig nota_: Vaste een kwestie waar GraphQL een interne serverfout terugkeerde toen het halen van een kar die een gebundeld product met een uit-van-voorraadpunt bevat, specifiek wanneer de vraag het item ItemsV2 bezit omvatte. GraphQL retourneert nu correct een lijst met items met relevante foutberichten die zijn gekoppeld aan het item voor het gebundelde product-item, zoals wordt verwacht.
* _LYNX-441_: Het is niet mogelijk om een adres met douanekenmerken tot stand te brengen
   * _nota van de Reparatie_: Vaste een kwestie met de createCustomerAddress mutatie die de verwezenlijking van adressen met vereiste douaneattributen verhinderde. De mutatie behandelt nu correct de attributen van het douaneadres wanneer de aangewezen lading wordt verstrekt.
* _LYNX-447_: De serverfout van GraphQL op wagentje met only_x_left_in_stock op gebundeld product
   * _Bevestig nota_: Vaste een kwestie waar het halen van een kar die een gebundeld product met het only_x_left_in_stock gebied in de vraag van GraphQL in een interne serverfout resulteerde. GraphQL retourneert nu correct een float of null voor het veld only_x_left_in_stock zonder fouten.
* _LYNX-464_: De fout van GraphQL wanneer het verwijderen van andere producten met ontoereikende configureerbare product in kar
   * _nota van de Reparatie_: Vaste een kwestie waar het proberen om producten in-voorraad uit het karretje te verwijderen in een &quot;Gevraagde hoeveelheid is niet beschikbaar&quot;fout van GraphQL als het karretje ook configureerbare producten met ontoereikende voorraad bevatte. Het verwijderen werkt nu zoals verwacht zonder fouten te veroorzaken.
* _LYNX-469_: Kan producten toe te voegen toe te schrijven aan SKU in mutatie die gevoelig geval is
   * _nota van de Reparatie_: Los een kwestie op waar de mutatie addProductsToCart een fout &quot;PRODUCT_NOT_FOUND&quot;terugkeerde wanneer het gebruiken van SKUs met verschillend casing. De mutatie behandelt nu case-insensitive SKUs, die consistentie met de vragen van de Dienst van de Catalogus en gedrag PDP verzekeren.
* _LYNX-603_: Het attribuut van het product > handelsmerk korte vorm ™ is teruggekeerd als ™
   * _nota van de Reparatie_: Opgeloste karakter het coderen kwestie met de productnaam voor GraphQL API
* _LYNX-619_: updateCustomerEmail mutation kwestie
   * _Bevestig nota_: Los een kwestie met updateCustomerEmail mutatie op waar de klanten zonder vereiste douaneattributen (toegevoegd na rekeningsverwezenlijking) hun e-mail niet konden bijwerken.
* _LYNX-626_: De mutatie setShippingAddressOnCart veroorzaakt fout wanneer het gebruiken van pickup_location_code
   * _Bevestig nota_: Vaste een kwestie waar de mutatie setShippingAddressOnCart een fout terugkeerde toen het gebruiken van pickup_location_code zonder customer_address_id of adres te specificeren. De mutatie staat nu correct het plaatsen van een verschepend adres met enkel pickup_location_code toe.
* _LYNX-637_: Storefront-compatibiliteit - Logica bijwerken om de tabelnaam met voorvoegsel en andere kleine verbeteringen te krijgen
   * _Fix-opmerking_: Logica bijgewerkt om de tabelnaam met het voorvoegsel op te halen (gerelateerd aan SCP-wijzigingen).
* _LYNX-643_: opslaan in adresboek werkt niet bij gebruik van het veld same_as_shipping van setBillingAddressOnCart GQL
   * _Opgeloste opmerking_: Er is een probleem opgelost waarbij het verzendadres niet werd opgeslagen in het adresboek van de klant bij gebruik van de setBillingAddressOnCart GraphQL-mutatie met het veld same_as_shipping ingesteld op true. Nu wordt het verzendadres correct opgeslagen zoals verwacht.
* _LYNX-650_: Standaardiseer de order_id in mutaties
   * _Fix-opmerking_: de order_id-invoer in mutaties gestandaardiseerd en de e-mailsjabloon voor het annuleren van de bestelling bijgewerkt om de increment-ID weer te geven in plaats van de order-ID.
* _LYNX-651_: CustomerOrder geeft de opmerkingen bij de bestelling niet weer
   * _Fix-opmerking_: Er is een probleem opgelost met CustomerOrder om orderopmerkingen op te nemen in GraphQL-query&#39;s voor gasten en klantorders.
* _LYNX-652_: original_item_price mag geen korting bevatten
   * _Fix-opmerking_: de logica voor original_item_price in GraphQL Cart Item-prijzen is bijgewerkt om kortingen uit te sluiten.
* _LYNX-681_: Bundelproducten tonen nog steeds &quot;IN_STOCK&quot; wanneer een van de gebundelde producten niet op voorraad is
   * _nota van de Reparatie_: Los een kwestie op waar product.stock_status voor bundelproducten nog &quot;IN_STOCK&quot;toonde zelfs wanneer één van de gebundelde punten uit voorraad was.
* _LYNX-686_: de klantenvraag keert Interne Fout van de Server terug als de waarde voor geschrapt douanekenmerk voor een klant bestaat
   * _nota van de Reparatie_: Vaste de kwestie waar de klantenvraag een interne serverfout terugkeerde toen een geschrapt douanekenmerk nog een opgeslagen waarde had. Er wordt nu een correct foutbericht geretourneerd als een niet-bestaand kenmerk wordt aangevraagd. De vereiste cache wordt ongeldig gemaakt wanneer het aangepaste attribuut van de klant wordt verwijderd.
* _LYNX-687_: De parameter van de actie voor terugkeer en annuleert bevestigingsverbindingen
   * _Fix-opmerking_: actieparameter toegevoegd voor retour- en annuleringsbevestigings-e-mail gerelateerde links
* _LYNX-689_: De bevestigings-url van de gastgebruiker wordt doorgestuurd naar de statuspagina van de bestelling omdat er orderRef ontbreekt
   * _Nota van de Reparatie_: Toegevoegde parameter orderRef aan de verbinding in de bevestigingsmail van de bezoekersorde
* _LYNX-699_: Kan null niet retourneren voor het niet-nulleerbare veld &quot;TaxItem.title&quot; op placeOrder GQL
   * _Bevestig nota_: Vaste een kwestie waar de placeOrder mutatie met een interne serverfout wegens een ongeldige waarde voor het niet-nullable gebied TaxItem.title ontbrak. Het veld retourneert nu altijd een geldige waarde, zodat de bestelling correct wordt geplaatst.
* _LYNX-702_: EstimateTotals: Kortingen zijn ongeldig voor virtuele producttypes
   * _nota van de Reparatie_: Los de kwestie met de verbetering estimals op terugkerende nul voor kortingen op wanneer een kortingscode op een kar wordt toegepast die virtuele producten bevat.
* _LYNX-703_: Het product van de bundel keert niet het correcte disconteringspercentage en het bedrag terug
   * _de nota van de Reparatie_: De nieuwe eigenschappen &quot;catalog_disconto&quot;en &quot;row_catalog_disconting&quot;zijn geïntroduceerd voor de prijzen van het cataloguspunt om de correcte kortingsbedragen en percentages op zowel de rij als enige puntniveaus te tonen.
* _LYNX-714_: De berichtconfiguratie van het Gift op productniveau
   * _nota van de Reparatie_: Vaste een kwestie waar de gifteberichten niet op het productniveau werden toegepast wanneer globaal gehandicapt. Als cadeauberichten nu zijn ingeschakeld voor een specifiek product, kunnen ze worden toegevoegd met de updateCartItems-mutatie. Ze worden nu op de juiste wijze opgeslagen en gereflecteerd.
* _LYNX-757_: de fout van de de vraagterugkeer van cart.rules in plaats van lege serie voor het geval dat geen actieve kartregels worden toegepast
   * _nota van de Reparatie_: Vaste de vraag cart.rules om een lege serie in plaats van een fout terug te keren wanneer geen actieve wortelregels worden toegepast.
* _LYNX-778_: De vraag van GraphQL met de methode van OPTIONS keert 500 reactiecode terug wanneer adobe-commerce/opslag-verenigbaarheidspakket geïnstalleerd
   * _de nota van de Reparatie_: Vaste een kwestie waar de vraag van GraphQL die de methode van OPTIONS gebruiken een Fout van de Server van 500 terugkeerde toen adobe-commerce/storefront-verenigbaarheid pakket werd geïnstalleerd. Het eindpunt keert nu correct een 200/204 reactie terug zoals verwacht.

### Andere hulpprogramma&#39;s voor ontwikkelaars

* _AC-10658_: [Probleem] opgelost HTML-syntaxisfout in visual.phtml
   * _Fix-opmerking_: Het systeem sluit nu de start-tag in het bestand visual.phtml correct, waardoor de juiste HTML-syntaxis wordt gegarandeerd. Voorheen werd de start-tag niet goed gesloten, waardoor er een HTML-syntaxisfout ontstond.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38247>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [ Uitgave ] Gewijzigd &quot;actief&quot;aan &quot;toegelaten&quot;in bin/magento onderhoud:statusbevel
   * _nota van de Reparatie_: Het systeem verstrekt nu nauwkeurigere statusberichten voor het bevel van de onderhoudswijze, veranderend de status van &quot;actief&quot;in &quot;toegelaten&quot;en van &quot;niet actief&quot;aan &quot;gehandicapt&quot;. Voorheen werd het statusbericht voor de opdracht onderhoudsmodus weergegeven als &quot;actief&quot; of &quot;niet actief&quot;, wat tot verwarring kon leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38486>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: Navigeren in de categorieënboom leidt tot fouten in Redis: &quot;Redis session exceeded concurrent connections&quot;
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38851>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12731_: CSP-problemen in combinatie met dev/css/use_css_critical_path
   * _nota van de Reparatie_: Het systeem laadt nu correct CSS dossiers asynchroon op controlepagina&#39;s, zelfs wanneer &quot;dev/css/use_css_critical_path&quot;wordt toegelaten, die ervoor zorgen dat deze pagina&#39;s met de juiste CSS stijlen worden teruggegeven. Eerder werd met een beperkt inhoudsbeveiligingsbeleid (CSP) voorkomen dat inline JavaScript werd uitgevoerd, waardoor CSS-bestanden niet naar behoren werden geladen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39020>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: Met behulp van een virtueel type om de plug-in te configureren, kan de interceptormethode niet correct worden gegenereerd in de opdracht voor het opzetten:di:van de compilatie
   * _nota van de Reparatie_: Het systeem produceert nu correct interceptormethodes wanneer het gebruiken van een virtueel type om een stop te vormen, die verenigbare resultaten verzekeren of precompiled of runtime. Voorheen zou het systeem onjuiste resultaten genereren wanneer vooraf werd gecompileerd in vergelijking met de compilatie bij uitvoering.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/33980>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3631_: Adobe Commerce 2.4.7-p3 eenheidstests mislukken
   * _Fix-opmerking_: er zijn geen release-opmerkingen vereist.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/982b1c42>

### Betaling/ Betaalmethoden, Bestellen

* _AC-13699_: Pauselijke betaalstroom Creditcardgegevens die zijn opgeslagen voor later gebruik, worden niet weergegeven op de pagina met opgeslagen betaalmethoden
   * _Fix-opmerking_: eerdere pauselijke payflow-creditcardgegevens die waren opgeslagen voor later gebruik, werden niet weergegeven op de pagina met de opgeslagen betaalmethode, die nu vast is, creditcardgegevens worden weergegeven op de pagina met de opgeslagen betaalmethode.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/96dec499>

### Betalingen

* _AC-13414_: De betaling van de Kredietkaart (van de Payflow Link) werkt niet
   * _Bevestig nota_: Eerder het krijgen van fout (Betaling werd Ontworpen) terwijl het plaatsen van orde met Kaart na de met succes geplaatste moeilijke opdracht.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_: De uitstroom leidt tot nieuwe transactie telkens als wij op het terughaalknoop op het scherm van de meningstransactie klikken
   * _nota van de Reparatie_: Het systeem haalt nu correct transactieinformatie zonder een nieuwe betalingstransactie tot stand te brengen telkens als de haalknoop op het scherm van de meningstransactie wordt geklikt. Als u eerder op de knop Ophalen klikt, wordt een nieuwe betalingstransactie voor een bestelling die al is betaald, onjuist gemaakt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3028_: Het uitbetalende bericht toont niet in PDP voor Canadese paypal handelaarrekening
   * _Nota van de Moeilijke situatie_: Het systeem toont nu correct het PayLater bericht voor de Canadese handelsPAL rekeningen op de Pagina van het Detail van het Product (PDP) wanneer het land van de koper van het rekeningsfactuuradres of de verzending kan worden bepaald. Eerder werd het PayLater-bericht niet weergegeven vanwege een ontbrekende parameter, wat resulteerde in een fout in de browserconsole.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3143_: Restitutie van PayPal-bestellingen resulteert in dubbele creditnota
   * _Bevestig nota_: Vaste gelijktijdige kwestie van IPN-Gecreeerde creditmemo&#39;s voor de betalingsdienst van PayPal.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3163_: De prijsregel van de kunst die niet voor PayPal werkt
   * _Nota van de Moeilijke situatie_: Het juiste bedrag wordt getoond aan de kant van PayPal wanneer de korting door betalingsmethode wordt toegepast
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3208_: [ de Gebruikers van de Wolk ] met een specifieke rol kunnen niet login
   * _nota van de Reparatie_: admin gebruiker met rol die slechts de toegang van de Sectie van PayPal nu bevat kan login zonder fouten
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>

### Prestaties

* _AC-11932_: De StandaardKwestie van de Montages van de Attributen van het Product
   * _nota van de Reparatie_: Het systeem staat nu gebruikers toe om een standaardoptie voor een productattribuut te schrappen, die ervoor zorgen dat de attributen niet altijd een standaardreeks hebben. Eerder, toen een gebrek voor een productattribuut werd geplaatst, was er geen manier om het te schrappen, resulterend in de attributen altijd een standaardreeks.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38703>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-12000_: [ geef ] de schoonmaakbeurt van de Code uit en voeg nieuw kritiek hoofdblok toe en beweeg kritieke css vóór activa
   * _nota van de Reparatie_: Het systeem omvat nu een nieuw kritiek hoofdblok en beweegt kritieke CSS vóór activa, die voor meer aanpassing en prestatiesoptimalisering in het frontend toestaan. Eerder werd de kritieke CSS niet geplaatst vóór de activa, die aanpassing en optimaliseringsmogelijkheden beperken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38748>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: De onderbrekingen van de themacompilatie wanneer mysql gastheer haveninformatie bevat
   * _nota van de Reparatie_: Het systeem behandelt nu correct MySQL gastheerconfiguratie die haveninformatie omvat, die succesvolle themacompilatie verzekeren. Eerder, zou de themacompilatie ontbreken als de MySQL gastheerconfiguratie in de gegevensbestandverbinding haveninformatie omvatte.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38799>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38842>
* _AC-13471_: Steun voor CommandLoaderInterface van Symfony in Magento CLI
   * _Bevestig nota_: Deze verandering vermindert initialisatietijd van Magento CLI app door uitgestelde initialisering van bevelen toe te staan tot zij nodig zijn.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/29266>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_: De kwestie van prestaties wanneer het laden van productattributen in kartregels
   * _de nota van de Reparatie_: Verbeterde vraagprestaties voor verkoopregels - van rond 150ms aan enig cijfer ms.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: De gedeeltelijke indexerende prestaties van de prijs
   * _Fix-opmerking_: De prestaties van de gedeeltelijke prijsindexering zijn verbeterd door enkele van de verwijderquery&#39;s die in het indexeringsproces worden gebruikt, te optimaliseren.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: De orde wordt verworpen op multi-store opstelling wanneer het gebruiken van Async-orde verwerking + Voorwaarden en
   * _nota van de Reparatie_: De orden die van niet standaardwebsites met toegelaten termijnen en voorwaarden worden geplaatst worden nu verwerkt.
Voordat ze automatisch werden afgewezen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: De vraag van de Rest API van de orde neemt een lange tijd om uit te voeren
   * _Fix-opmerking_: Het systeem voert nu de Order Rest API-aanroep uit binnen een redelijk tijdsbestek, waardoor de prestaties bij het ophalen van een groot aantal bestellingen worden verbeterd. Eerder duurde de aanroep van de Order Rest API veel tijd om te worden uitgevoerd, wat vertragingen optrad bij het ophalen van een groot aantal bestellingen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/001e5188>

### Prijsstelling

* _AC-11810_: Magento2.4.6-p4 Order API Simple Item ontbrekende prijs
   * _nota van de Reparatie_: Het systeem toont nu correct de prijs van eenvoudige producten wanneer gevraagd door de Orde API, die nauwkeurige gegevensvertegenwoordiging verzekeren. Eerder werd de prijs van eenvoudige producten onjuist weergegeven als nul in de API-reactie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38603>
* _AC-13855_: De fout die van de Penny in catalogusregel afrondt
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/276e0acd>

### Product

* _wisselstroom-10535_: De speciale karakters in configureerbare associatieve productnaam worden omgezet in de Entiteiten van HTML.
   * _nota van de Reparatie_: Het systeem behoudt nu correct speciale karakters in de namen van bijbehorende producten wanneer het uitgeven van een configureerbaar product, verhinderend hen in de entiteiten van HTML worden omgezet. Eerder werden speciale tekens in gekoppelde productnamen geconverteerd naar HTML-entiteiten toen het configureerbare product werd bewerkt.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38146>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: ProductRepository functie GetById maakt niet de juiste cachesleutel
   * _nota van de Moeilijke situatie_: Het systeem leidt nu correct tot een geheim voorgeheugensleutel in de functie GetById van ProductRepository, ongeacht of opslag ID als koord of een geheel wordt overgegaan. Dit zorgt ervoor dat het product van geheugen op verdere vraag wordt teruggewonnen, verbeterend prestaties. Eerder, zou het systeem het product van het gegevensbestand terugwinnen telkens als de functie werd geroepen, zelfs met de zelfde parameters, wegens onjuist geheim voorgeheugenzeer belangrijke verwezenlijking.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38384>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [ Uitgave ] [ MFTF ] Toegevoegde AdminClickAddOptionForBundleItemsActionGroup
   * _nota van de Reparatie_: Het systeem omvat nu AdminClickAddOptionForBundleItemsActionGroup, die de functionaliteit van het admin paneel verbetert. Voorheen was deze actiegroep niet beschikbaar.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/30857>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/30838>
* _AC-13173_: [Probleem] Fix typfout in PHPDoc blok
   * _Fix-opmerking_: het systeem verwijdert nu correct een onbekende gerefereerde variabele in PHPDoc voor de declaratie van $helper variabelen, waardoor de code duidelijker en nauwkeuriger wordt. Voorheen veroorzaakte deze onbekende variabele in PHPDoc verwarring en mogelijke onnauwkeurigheden in de code.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38961>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [Probleem] opgelost kapotte bundel en lay-out van downloadbare productpagina&#39;s in Magento >= 2.4.7
   * _Fix-opmerking_: de lay-out voor bundel- en downloadbare productpagina&#39;s is gerepareerd, waardoor een consistente en correcte weergave op alle apparaten wordt gegarandeerd. Voorheen ondervonden deze pagina&#39;s lay-outproblemen als gevolg van een herschikking van het mediablok voor productinformatie.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39403>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_: AlertProcessor - Argument #2 ($storeId) moet van het type int zijn, string gegeven
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
* _ACP2E-3139_: De Regel van de verkoop met het attribuut van de Stap van de Korting van het Aantal (koop X) veroorzaakt dat andere regels niet worden toegepast
   * _Bevestig nota_: De prijsregel van de Kar annuleert eerder toegepaste regels niet als de hoeveelheid van het product in de kar niet genoeg voor toe te passen regel is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3332_: De verkoopregels van de uitgave met Vaste korting van het bedrag en &quot;De Maximale Korting van de Aantal wordt toegepast op&quot;
   * _nota van de Reparatie_: Vaste kwestie met de korting van de kartregels, wanneer de vaste waardekorting wordt gevormd om op een beperkte hoeveelheid producten worden toegepast is het karretje. Eerder werd de waarde &quot;Maximale korting op de hoeveelheid toegepast op&quot; gebruikt voor de berekening van de prijs van het lopende item in het winkelwagentje, niet alleen voor de berekening van de korting op de regel.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3349_: De regels van de wagen &quot;Vaste korting van het bedrag voor het volledige karretje&quot;  Met Actie worden kortingen onjuist toegepast
   * _nota van de Reparatie_: De codes van de coupon zullen behoorlijk ongeacht hogere geval of kleine letters, wanneer gebruikt in ordeverwezenlijking van het admin gebied worden bevestigd. De waardeboncode werd eerder niet gevalideerd als deze niet precies overeenkomt met het hoofdlettergebruik van de code van de geconfigureerde tekenregel.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_: In Achterkant, standaard opslagwaarden voor productattributen (in plaats van verwachte adminwaarden)
   * _Fix-opmerking_: In de back-end worden nu beheerderswaarden gebruikt in plaats van de standaard winkelwaarden voor productkenmerken.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_: De regels van de winkelwagen &quot;Vaste korting van het bedrag voor het volledige winkelwagentje&quot;actie passen onjuiste kortingen toe wanneer het toevoegen van bundelproducten
   * _Nota van de Reparatie_: De vaste regels van het aantalkarretje werden niet behoorlijk toegepast op bundelproducten. Bij de berekening van het totale kortingsbedrag worden nu onderliggende bundelproducten in aanmerking genomen, wat resulteert in een correcte disconteringsberekening.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_: De Regels van de Kar van de Prijs berekenen Verkeerde Korting
   * _nota van de Reparatie_: De vaste kortingen van het bedrag worden nu behoorlijk berekend. Voorafgaand aan de correctie werden kortingen voor vaste bedragen niet correct toegepast op bundelproducten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_: Geneste categorieën in regelvoorwaarden die niet tonen
   * _Opgeloste opmerking_: probleem opgelost wanneer geneste categorieën onder categorie 3 niet werden weergegeven in marketingregels voor categorievoorwaarde
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit en uses_per_customer wordt niet bijgewerkt in salesrule_coupon tabel
   * _Bevestig nota_: Het bijwerken van Gebruik per Coupon en Gebruik per Klant in de regel van de kartprijs zal nu bestaande autogeproduceerde coupons beïnvloeden. Eerder beïnvloedden de nieuwe waarden alleen nieuwe coupons
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3456_: De prijsregel van de wagen overweegt geen oudercategorie wanneer het &quot;evenaart of groter dan&quot;voorwaarde gebruikt.
   * _Nota van de Reparatie_: De Regels van de Prijs van de kunst overwegen nu correct oudercategorie wanneer het in geavanceerde voorwaarden wordt gebruikt
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93359343>
* _ACP2E-3463_: Ongeldige disconteringsberekening met prioriteit
   * _Bevestiging nota_: In het geval van vast die bedrag voor het volledige type van kartkorting wordt toegepast, werd het bedrag niet behoorlijk berekend voor kartpunten die reeds door een vorige bevordering werden verdisconteerd. Kortingen worden nu goed samengevat.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3472_: [ CLOUD ] de Verzendberekening overweegt niet de het winkelwagentregel
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie, werd een wortelregel met gebiedsvoorwaarde niet consequent toegepast. Na de correctie worden de regels voor het winkelwagentje met de omstandigheden van het gebied correct toegepast.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3491_: De voorwaarde van de de regelsku van de kunst ontbreekt voor factuur.
   * _nota van de Reparatie_: De Korting op het product van de Bundel met dynamische prijs wordt nu correct weerspiegeld in de factuur. Voorheen werd de korting niet in de factuur weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3498_: Onjuiste disconteringswaarde wanneer de veelvoudige regels van de kartprijs gelijktijdig met gedisconteerde/speciale geprijsde producten worden toegepast
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie, werd het vaste bedrag voor de volledige kartregels niet behoorlijk toegepast als meer dan één werd toegepast. Nu worden de regels voor kortingen op vaste bedragen correct toegepast.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>

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
* _ACP2E-3383_: Onjuiste url_rewrite ingangen creatie met veelvoudige opslag in één opslaggroep
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie, kon u URL slechts rewrites op een websiteniveau produceren wanneer het uitgeven van een product. Met de correctie is een nieuwe instelling geïntroduceerd (Winkels > Configuratie > Catalogus > Catalogus > Optimalisatie van zoekprogramma&#39;s, &quot;Product URL herschrijven bereik&quot; met opties &quot;Winkelweergave&quot;, &quot;Website&quot;) waarmee u URL-herschrijvingen kunt genereren in de winkelweergave of op websiteniveau.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/2d627301>

### Zoeken

* _AC-13053_: Het krijgen &quot;ga een onderzoekstermijn in en probeer opnieuw.&quot; fout bij geavanceerd zoeken van pagina in winkel 2.4.8-bèta1
   * _nota van de Reparatie_: Het systeem toont nu correct onderzoeksresultaten op de Geavanceerde pagina van het Onderzoek wanneer een productattribuut aan &quot;Nr&quot;wordt geplaatst. Als u eerder een productkenmerk instelt op &quot;Nee&quot; en een zoekopdracht uitvoert, verschijnt het foutbericht &quot;Voer een zoekterm in en probeer het opnieuw.&quot;
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/module-open-onderzoek hangt van nonexistent op openssearch-php tak af
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: search_query lijst wanneer van enorme grootte, heeft grote invloed op de frontend van de ladingstijd
   * _nota van de Reparatie_: De verbeterde tijd van de de paginalading van de onderzoekslijst. Vóór de correctie werd de pagina met zoeklijsten vertraagd vanwege een niet-geoptimaliseerde query.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>

### Beveiliging

* _AC-11855_: [ Uitgave ] Ontbrekende CSP van de Dooppop-up van het Font
   * _nota van de Reparatie_: Het systeem staat nu het laden van doopvont &quot;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; toe zonder de richtlijn van het Beleid van de Veiligheid van de Inhoud te overtreden, die de correcte vertoning van de Pop van de Paylater verzekert. Eerder werd het lettertype niet geladen vanwege een schending van de Content Security Policy-richtlijn, wat weergaveproblemen met de Paylater Popup veroorzaakte.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38624>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37401>
* _AC-12035_: [ geef ] Update js.js DOM- tekst uit die als HTML wordt hergeïnterpreteerd
   * _Bevestig nota_: Door innerText te gebruiken, zal het het risico van injectie van HTML vermijden, aangezien deze eigenschappen automatisch om het even welke speciale karakters van HTML in de verstrekte tekst ontsnappen. Met deze correctie voorkomt u XSS-kwetsbaarheden (cross-site scripting) door de invoer te behandelen als onbewerkte tekst in plaats van als geïnterpreteerde HTML.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38767>
* _ACP2E-3273_: ReCaptcha V2 toont verkeerd bij kassa voor het Duits
   * _Fix-opmerking_: Voorheen leek de recaptcha van onder het e-mailadres van de kassa niet gestileerd voor talen met lange woorden, zoals Duits. Hierna ziet de recaptcha er hetzelfde uit als alle recaptcha elementen uit de rest van de gebieden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Captcha op admin login vereist geen interactie voor sommige gebruikers
   * _nota van de Reparatie_: ReCaptcha voor admin login wordt bevestigd zoals verwacht
   * _GitHub codebijdrage_: <https://github.com/magento/security-package/commit/8f64ab3c>

### Verzending

* _AC-10757_: [ Vaste typefout van de kwestie ] in tracking.phtml - anders genoemd JS-functies &quot;currier&quot;aan &quot;drager&quot;
   * _nota van de Reparatie_: Het systeem gebruikt nu correct de term &quot;drager&quot;in plaats van de verkeerd gespelde &quot;currier&quot;in de de handlerfuncties van JavaScript die in het orde volgende malplaatje worden gebruikt, die correcte functienaam en codeduidelijkheid verzekeren. Voorheen werd de verkeerd gespelde term &quot;currier&quot; gebruikt, wat tot verwarring en inconsistentie in de codebase kan leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/34523>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/33414>
* _AC-11938_: UPS REST &quot;Een verzending kan geen KGS/IN of LBS/CM of OZS/CM als zijn eenheid van metingen hebben&quot;
   * _nota van de Reparatie_: Zorg aan de tarieven van UPS in controle en kart zichtbaar zouden moeten zijn.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38618>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/493e01f5>
* _AC-13172_: [ geef ] Correcte spelling van variabelen voor klantenadres uit
   * _nota van de Reparatie_: Het systeem spelt nu correct variabelen voor klantenadressen, die nauwkeurige vertoning op het rekeningsgebied van het vooreind verzekeren. Eerder kon een onjuiste spelling van deze variabelen leiden tot fouten tijdens lokale coderevisies.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32817>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_: Het volgen Venster die onjuiste Verwachte Datum van de Levering tonen
   * _nota van de Reparatie_: De correcte Datum van de Levering van de vertoning voor de Drager van de Verkoop van de Verkoop van de Verkoop.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: De Tarieven van de lijst die nog tonen hoewel de Vrije verscheping wordt toegepast
   * _Nota van de Reparatie_: De het verschepen methode van het Tarief van de lijst wordt nu getoond zelfs als de Vrije Verzending na coupon het toepassen beschikbaar wordt
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF test AdminCreatingShippingLabelTest die als gevolg van geloofsbrieven niet in milieu Jenkins wordt toegevoegd
   * _nota van de Reparatie_: mftf testmoeilijke situatie
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_: Het Spoor FedEx API van FedEx werkt niet met de geloofsbrieven van REST
   * _nota van de Reparatie_: Eerder integratie FedEx vereiste geen extra API sleutels voor het Volgen API. Er is nu een nieuwe configuratie toegevoegd ter ondersteuning van het bijhouden van API-sleutels.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [ de Wolk ] FedEx onderhandelde Tarieven niet op REST teruggekeerd
   * _nota van de Reparatie_: Vorig aan de moeilijke situatie, FedEx rekeningsspecifieke tarieven waar niet verzonden op de reactie, zelfs door volgens documentatie FedEx zij zouden moeten worden verzonden. Na de correctie worden de specifieke tarieven van de rekening verzonden op de reactie door het verzoek van onze kant te veranderen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>

### Staging en voorvertoning

* _ACP2E-3453_: Onbekwaam om Geplande Update bij te werken wanneer het Gebruiken van Uniek Attribuut van de Categorie van de Douane
   * _nota van de Reparatie_: Vaste een kwestie waar het bijwerken van een geplande update voor een categorie niet mogelijk was als de categorie een uniek attribuut had
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>

### Targeting

* _AC-9432_: [Probleem] Gebruik van CIDR-bereiken in de lijst met toegestane onderhoudsprogramma&#39;s toestaan
   * _Fix-opmerking_: het systeem ondersteunt nu het gebruik van CIDR-bereiken in de IP-lijst voor het toestaan van de onderhoudsmodus, waardoor een reeks IP-adressen de onderhoudsmodus kan omzeilen. Voorheen stond de onderhoudsmodus IP-lijst toe die alleen individuele IP-adressen toestond om de onderhoudsmodus te omzeilen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/37943>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/30699>

### Belasting

* _AC-13295_: [ de 3} Eigenschap van de kwestie/php8.1 de bevordering van het aannemersbezit toen grafiek ql]
   * _nota van de Reparatie_: Vervang bijna alle eigenschappen met de bevordering van het aannemersbezit in module waar grafiek ql:
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39309>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_: De Vaste Belasting van het Product (FPT) werkt niet met configureerbare producten
   * _nota van de Reparatie_: FPT voor configureerbare productvariaties die behoorlijk werken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Testkader

* _AC-11654_: De test van de integratie faalt testDbSchemaUpToDate toe te schrijven aan JSON kolomtype
   * _nota van de Reparatie_: Het systeem erkent nu correct JSON kolomtypes in het gegevensbestandschema tijdens integratietests, die testmislukkingen wegens een wanverhouding tussen het gegevensbestandschema en het verklarende schema verhinderen. Eerder, identificeerde het systeem verkeerd JSON kolomtypes als LONGTEXT in MariaDB, veroorzakend integratietests om te ontbreken.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_: [Probleem] PHPDoc correctie spelling
   * _Fix-opmerking_: het systeem herkent verouderde methoden nu correct in IDE&#39;s als gevolg van een spellingcorrectie in de PHPDoc. Voorheen zorgde een spelfout in de PHPDoc ervoor dat IDE&#39;s bepaalde methoden niet als verouderd herkenden.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/31399>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Het controleren van gedrag met het blijvende het winkelwagentje nadat de zitting is verlopen
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13848_: Verbeter statische tests om gebruik door 3d partijuitbreidingen toe te laten
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/9e383b4d>
* _ACP2E-3334_: [ de Interne ] Fixture past mislukking toe is niet getoond tijdens uitvoering of in logboeken
   * _Bevestig nota_: &quot;-
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3458_: [ MFTF ] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Vaste opmerking_: Vaste mftfs
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>

### UI-kader

* _AC-12128_: De veiligheidskwetsbaarheid van Prototype.js moeilijke situatie CVE-2020-27511
   * _nota van de Reparatie_: Het systeem is bijgewerkt om de veiligheidskwetsbaarheid CVE-2020-27511 in Prototype.js 1.7.3 te richten, die de algemene veiligheid van het systeem verbetert. Voorafgaand aan deze update was het systeem gevoelig voor een Regular Expression Denial of Service (ReDOS) via gestripte HTML-tags.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-12189_: Grunt minder gebruikspubs/prefix voor broncemaps
   * _nota van de Reparatie_: Het systeem produceert nu minder/css broncemaps zonder de /pub prefix voor wegen wanneer het gebruiken van steen, die de behoefte aan een tijdelijke oplossing in de configuratie van de webserver elimineren. Eerder, vereiste het gebruik van het prefix /pub in broncemaps wegen een specifieke configuratie in de webserver om correct te functioneren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38837>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38840>
* _AC-12432_: Het Gebied van het Dossier van de Component van UI
   * _nota van de Reparatie_: Het systeem bevestigt nu correct het dossiergebied in een UI componentenvorm, die de vorm toestaat om zonder fout worden voorgelegd wanneer een dossier wordt geselecteerd. De validatie zou eerder mislukken, zelfs als een bestand was geselecteerd, zodat het formulier niet kon worden verzonden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38908>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [ geef ] Verbeterde datumformaat in js console uit: schakelaar van 12 uur aan 24 uur van..
   * _Nota van de Reparatie_: Verbeterde datumformaat in js console: schakelaar van 12 uur aan 24 uur
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38983>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [ geef ] toe voeg bronMap generatie voor minder dossiers op ontwikkelaarwijze toe
   * _nota van de Reparatie_: Het systeem produceert nu bronkaarten voor minder dossiers wanneer op ontwikkelaarwijze, makend het gemakkelijker om de bron van een stijl te identificeren. Eerder, was het identificeren van de bron van een stijl uitdagend toen het runnen van het systeem op ontwikkelaarwijze met server-kant minder compilatie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38982>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38977>
* _AC-1306_: De statische inhoud stelt voor gehandicapte modules op
   * _nota van de Reparatie_: Het systeem sluit nu CSS met betrekking tot gehandicapte modules van de definitieve CSS outputdossiers uit, die ervoor zorgen dat de onnodige stijlen niet worden geladen. Eerder werden CSS met betrekking tot uitgeschakelde modules opgenomen in de uiteindelijke CSS-uitvoerbestanden, wat leidde tot het laden van extra, onnodige stijlen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/24666>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32922>
* _AC-13459_: Het inconsistente Gedrag in &quot;Voorraad&quot;Sorterend met Minimumdrempel van de Voorraad
   * _nota van de Reparatie_: Het systeem sorteert nu correct producten in de catalogus die op voorraadniveaus wordt gebaseerd, die de vastgestelde Minimum Drempel van de Beeld volgen en zich uit-van-voorraadpunten aan de bodem van de lijst constant bewegen. Eerder was het sorteergedrag inconsistent, waarbij items niet altijd in de juiste volgorde werden weergegeven op basis van hun voorraadniveau, en wijzigingen in sorteren kunnen onvoorspelbaar optreden na het opslaan, vernieuwen of wijzigen van de categoriehiërarchie.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Suggestie voor betere fout die voor require.js ladingsproblemen meldt
   * _nota van de Reparatie_: Deze PR verbetert het foutenbericht wanneer de vereisten er niet in slagen om een component te laden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36761>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38971>
* _AC-14004_: PHP 8.4 Deprecation Fouten die Build Failures veroorzaken in 2.4-develop
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_: [Probleem] Laad de context van het backend-blok niet op de front-end
   * _Fix-opmerking_: Het systeem zorgt er nu voor dat de context van het back-endblok niet op de frontend wordt geladen, waardoor het maken van onnodige backend-sessies en mogelijke sessievergrendelingen wordt voorkomen. Voorheen laadde het systeem de context van het backendblok op de frontend ten onrechte, wat leidde tot het maken van backend-sessies en mogelijke sessievergrendelingen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37617>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36368>
* _AC-9168_: [ Uitgave ] verwijdert onnodige samenvatting van manuscriptoverzicht
   * _nota van de Reparatie_: Het systeem optimaliseert nu de tijd van de paginalading door onnodige manuscripten van JavaScript uit de classificatiesectie te verwijderen, in plaats daarvan het gebruiken van gealigneerde CSS stijlen voor een efficiëntere en leesbare code. Eerder kon het gebruik van JavaScript-scripts voor de classificatiesectie de laadtijd van de pagina mogelijk vertragen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37776>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_: Uitzondering bij het controleren van het saldo van een cadeaubon wanneer Recaptcha is ingeschakeld
   * _Fix-opmerking_: gebruikers kunnen het saldo van de cadeaubon ophalen in het scherm voor het bekijken en bewerken van de winkelwagen. Voorheen werden deze details niet weergegeven terwijl reCAPTCHA was ingeschakeld.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [VERDUIDELIJKING] Functie Verzoek om ADA-conformiteit
   * _nota van de Reparatie_: Het systeem verzekert nu naleving ADA door niet gesteunde CSS eigenschappen te verwijderen en hen te vervangen met gesteunde degenen in het print.css- dossier. Eerder leidde het gebruik van niet-ondersteunde CSS-eigenschappen tot browsercompatibiliteitsproblemen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [ de bibliotheekcode van de Wolk ] van de Verzekering in effect-drop.js van AC 2.4.4-p8
   * _Fix-opmerking_: Het systeem implementeert nu de effect-drop.js-bibliotheek correct, waardoor de goede werking van jQuery UI-effecten wordt gegarandeerd. Eerder werd de bibliotheek effect-drop.js per ongeluk overschreven met de bibliotheek effect-clip.js, wat potentiële problemen met de gevolgen van jQuery UI veroorzaakte.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_: De Kopbal van de Plaats | Speciale tekens die het welkomstgedeelte van de klant doorbreken
   * _nota van de Reparatie_: Na de moeilijke situatie, worden de speciale karakters correct getoond in de klant welkome sectie.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_: Editie klantsegment mislukt met datumbereik
   * _Vaste opmerking_: Het is mogelijk om een klantsegment op te slaan met de voorwaarde van het datumbereik, wanneer slechts één van de datums is bewerkt.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/a52ff98f>
