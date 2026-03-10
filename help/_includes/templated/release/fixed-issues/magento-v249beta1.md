---
source-git-commit: 0a22d08d6965c6abc288a1a171d25f4ff8bbd7ce
workflow-type: tm+mt
source-wordcount: '24356'
ht-degree: 0%

---
# Opgeloste problemen in Magento Open Source (v2.4.9-bèta1)

## Opgeloste problemen in v2.4.9-bèta1

We hebben 501 problemen opgelost in de Magento Open Source 2.4.9-bèta1-kerncode. Hieronder wordt een subset van de opgeloste problemen in deze release beschreven.

### API&#39;s

#### Speciale prijs tot op heden wordt ten onrechte gevalideerd voor applySpecialPrice

Het systeem werkt prima met betrekking tot de speciale prijs en de speciale prijs van het product zal verlopen op de datum die door de beheerder of het derdepartijsysteem door REST API wordt bepaald

_AC-13130 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39169) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39690)_

#### [ WebAPI ] klant e-mailbevestiging via paradox WebAPI

Het probleem waarbij klanten hun accounts niet via WebAPI konden activeren, is verholpen door een paradox van een machtiging waarbij een token was vereist vóór de bevestiging. Met de update kunnen niet-bevestigde klanten hun accounts activeren via de API, waardoor een consistente en functionele bevestigingsstroom wordt gegarandeerd.

_AC-13281 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39255) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Fout met factuuradres in beheerdashboard bij maken van bestelling via REST API met alleen betalingsgegevens

Oplossing voor een probleem waarbij via de API orders konden worden gemaakt zonder factuuradres, waardoor het dashboard van de beheerder vastliep.
Nu zijn bestellingen zonder factuuradres beperkt en worden deze niet meer gemaakt.

_AC-14049 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39651) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Product toevoegen aan winkelwagentprobleem in de Rest-API

Producten die niet aan een specifieke website waren toegewezen, konden nog steeds aan de wagen worden toegevoegd en aangeschaft. Dit probleem is nu opgelost.
Er wordt nu een foutbericht weergegeven: &quot;Het product dat u wilt toevoegen, is niet beschikbaar.&quot;

_AC-15054 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40029) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/f5cc09fc)_

#### Label voor kenmerkoptie wordt overschreven wanneer winkellabels worden bijgewerkt

Door het bijwerken van een multiselect productkenmerk via REST API werden alle store_labels overschreven en werden bestaande winkelspecifieke labels verwijderd. Dit probleem is nu opgelost.
Wanneer Magento nu het standaardweergavelabel van de winkel bijwerkt, worden de aangeboden labels samengevoegd met bestaande labels in plaats van ze volledig te overschrijven.
Dit zorgt ervoor dat de store-specific etiketten voor andere opslagmeningen na updates intact blijven.

_AC-15208 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40093) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [ Verduidelijkte Optie van Attributen van 0&rbrace; Uitgave bestaat reeds reactie]

Het systeem heeft nu de lastige zin &quot;Nieuwe bestandsnaam ophalen als hetzelfde al bestaat&quot; vervangen door een duidelijkere en grammaticale versie: &quot;Een nieuwe bestandsnaam ophalen als dit al bestaat.&quot; Hierdoor wordt de leesbaarheid en het begrip van de gebruiker verbeterd.
Hetzelfde voor de reactie van de kenmerkoptie.

_AC-15473 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39943) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39941)_

#### Interne serverfout in /V1/products/special-price API Endpoint

De misvormde verzoeken aan /V1/products/special-price en verwante het tarief APIs van de Server gaven een Fout van de Interne Server van 500 wegens een ongeldige TypeError terug.
De API&#39;s valideren nu de invoer en retourneren een fout van 400 voor ongeldige ladingen, waardoor de foutafhandeling en de betrouwbaarheid van de API&#39;s worden verbeterd.

_AC-6419 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35934) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a7ef6300)_

#### Interne serverfout in `/V1/order/&lbrace;orderId&rbrace;/ship` API-eindpunt

Het systeem lost nu de Interne Fout van de Server in `/V1/order/{orderId}/ship` API Eindpunt op en keert een 400 fout terug aangezien het verzoek misvormd is.

_AC-6420 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35931) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38282)_

#### Interne serverfout in /V1/creditmemo API-eindpunt

Onjuist geformuleerde verzoeken aan de /V1/creditmemo-API hebben een fout van 500 interne server geretourneerd. Dit probleem is nu opgelost.
Nu valideert de API de aanvraag correct en wordt een fout van 400 geretourneerd voor ongeldige ladingen, waardoor de foutafhandeling en de stabiliteit worden verbeterd.

_AC-6422 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35924) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a7ef6300)_

#### Rest API en Magento backend gebruiken verschillende bevestigingsmethodes voor attribute_code wanneer het creëren van nieuwe attributen

Correctie van inconsistentie waarbij de Magento Admin hoofdletters in attribute_code toestond, maar de REST API deze weigerde tijdens het maken van productkenmerken.
Zowel Admin als REST API voeren nu dezelfde validatie uit, zodat kenmerken met hoofdletters kunnen worden gemaakt.

_AC-6660 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/33138) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### Verschillende validatie tussen aanmaken en bijwerken van kenmerken via REST API

Niet-consistente validatie tijdens het maken van kenmerken via REST API leidde tot een onjuiste backend_type toegewezen. Dit probleem is nu opgelost.
Nu, plaatst het systeem het correcte achtergrondtype wanneer geldig, werpt een uitzondering voor ongeldige waarden, of daalt geschikt terug als niet verstrekt, die verenigbaar attributengedrag verzekeren.

_AC-6885 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/36327) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### Onjuiste aanvraaginstantie of parameters veroorzaken &quot;Interne serverfout&quot;

Onjuiste aanvraaginstanties of parameters retourneren nu een duidelijk &quot;400 Onjuist verzoek&quot;-antwoord.
Eerder, resulterend het verzenden van misvormde verzoekinstanties of parameters naar diverse REST API eindpunten (zoals /V1/carts/search, /V1/orders, /V1/products, enz.) in een generische &quot;Interne Fout van de Server&quot; (500), die het moeilijk maakt om inputkwesties te diagnostiseren.
Adobe Commerce geeft nu een &quot;400 Onjuiste aanvraag&quot;-reactie, die duidelijker feedback geeft wanneer aanvragen ongeldig zijn.

_AC-746 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/32784) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/f1adb44e)_

#### `/orders` (of `/orders/:id` ) het eindpunt ontbreekt &quot;status&quot;- en &quot;status&quot;-velden

De API-reacties `/orders` en `/orders/{id}` lieten de status en statusvelden weg als de databasewaarden null waren. Dit probleem is nu opgelost.
Nu worden beide velden consistent geretourneerd in de reactie, zodat wordt voldaan aan de API-documentatie en de betrouwbaarheid van de gegevens wordt verbeterd.

_AC-9244 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37807) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### Async Bulk Operation blijft open voor async.magento.configurableproduct.api.optionrepositoryinterface.save.post

De bulk API eindpunten zullen nu een fout als het verzoeklichaam geen Serie is, zo vereist dat bulkpuntsleutels opeenvolgende aantallen zijn die van 0 beginnen. Eerder werd de status van bulkobjecten niet bijgewerkt vanwege de willekeurige objectsleutel die in het bulkverzoek werd ingediend.

_ACP2E-3544 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### [ CLOUD ] API REST insect op is_subscribed waarde die niet van de huidige opslag overweegt gebruikend searchCriteria

Met de API REST-query van de klant wordt de juiste &quot;is_subscribed&quot;-waarde opgehaald uit de correcte opslag met behulp van searchCriteria
Eerder heeft de query van de klant van de API REST geen opslag overwogen bij het ophalen van is_subscribed&quot;-waarde.

_ACP2E-3621 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all kan veelvoudige ingangen voor 1 SKU tot stand brengen

Gelijktijdige verzoeken om hetzelfde product op te slaan en bij te werken, worden nu geserialiseerd om rasvoorwaarden te voorkomen die kunnen leiden tot gegevensinconsistentie of dubbele producten

_ACP2E-3744 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### Volgorde &quot;base_row_total&quot; en &quot;row_total&quot; geven prijs van één item weer in REST API-reactie

De REST api-reactie voor orderdetails bevat nu correcte waarden voor de kenmerken &quot;base_row_total&quot; en &quot;row_total&quot; voor het geval meerdere items werden geordend

_ACP2E-3874 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/4ca73607)_

#### REST API-eindpunt export-stock-salable-quality retourneert onjuiste items total_count

Probleem opgelost met paginering in de voorraad exportbestand. Verhandelbare hoeveelheid-API waarbij total_count onjuist beperkt was tot paginaformaat. Eerder, wanneer het gebruiken van /rest/all/V1/voorraad/export-stock-salable-quality/website/base eindpunt met pagineringsparameters zoals page_size=5, zou het total_count gebied in de reactie 5 in plaats van het daadwerkelijke totale aantal producten terugkeren die aan de onderzoekscriteria voldoen. Na deze moeilijke situatie, wijst het total_count gebied nu correct op het totale aantal producten beschikbaar ongeacht de page_size parameter, die verenigbaar pagineringsgedrag over alle eindpunten van Magento REST API verzekeren.

_ACP2E-4086 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

#### Validatieprobleem met aangepaste optie-id&#39;s in REST-API&#39;s voor winkelwagentjes.

REST API&#39;s V1/gast-carts/&lt;cartId>/items/ en V1/carts/mine/items/ valideren nu &quot;product_options.extension_attributes.custom_options.*.option_id&quot; om ervoor te zorgen dat het naar een geldige option_id verwijst voor het winkelwagentje SKU. Eerder werd deze parameter verwerkt en opgeslagen in de database zonder validatie.

_ACP2E-4138 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Tijdens het ophalen van het product uit de winkelwagentje en het wijzigen van de kopteksttaal van de winkel verandert dit niet

GraphQL customerCart-query retourneert nu productkenmerkwaarden op basis van de koptekstwaarde van de winkel. Eerder was het wijzigen van de kopteksttaal van de winkel tijdens het ophalen van een product van het winkelwagentje via GraphQL niet in overeenstemming met de bijgewerkte taal, wat leidde tot inconsistente lokalisatie.

_ACP2E-4227 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6e134409)_

#### REST API/media-eindpunt mislukt voor Cadeauproducten - retourneert &quot;Het product kan niet worden opgeslagen&quot;

Vóór de correctie mocht u cadeaukaartproducten maken die geen bedrag in het algemene bereik bevatten. Met de correctie is een validatie toegevoegd die controleert op bedragen in het algemene bereik.

_ACP2E-4395 - [&#x200B; GitHub kwestie &#x200B;](https://mcstaging.panini.it/shp_ita_it/)_

### API&#39;s, winkelwagentje en kassa

#### Voor validatie aan de serverzijde van verzendgegevens werkt de functie niet met REST API

Probleem verholpen in de REST API waarbij validatie van verzendadresgegevens niet overeenkwam met de kenmerkconfiguratie die is gedefinieerd in de Admin-backend. De validatie volgt nu correct de geconfigureerde instellingen.

_ACP2E-4156 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

### API&#39;s, catalogus

#### Standaardeindpunt van website-/winkel-einden van laag-prijzen verwijderen

Eerder, resulteerde het schrappen van de standaardbasiswebsite en het gebruiken van de secundaire website als standaardwebsite in een fout toen het proberen om de laagprijs voor de secundaire website bij te werken. Nadat u deze correctie hebt toegepast, kan de laagprijs echter worden bijgewerkt, zelfs als de basiswebsite wordt verwijderd of gedeactiveerd.

_ACP2E-4334 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

### API&#39;s, Framework

#### RedisRequestLogger\RedisClient (snelheidsbegrenzer)-uitzondering op toepassingsserver

Na de correctie kan de functie voor snelheidsbeperking samen met de GraphQL Application-server worden gebruikt in gevallen waarin de PHP redis-extensie is geïnstalleerd.

_ACP2E-4237 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

### API&#39;s, importeren/exporteren

#### Met de Async Invoice Refund-API worden offlinerestituties gemaakt in plaats van online restituties

Probleem verholpen met asynchrone terugbetalingsbewerkingen waarbij terugbetalingsaanvragen met de parameter `is_online` niet correct werden verwerkt.

_ACP2E-4394 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### API&#39;s, Order

#### [ CLOUD ] de informatiekwestie van de Orde met rij totale verschijning voor orde 000075568

Hiermee wordt het probleem verholpen waarbij de waarde row_total_incl_tax in de bestelling-API-reactie werd geretourneerd als een restwaarde van bijna nul in plaats van 0,00 wanneer een item volledig werd gedisconteerd.

_ACP2E-3950 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

### Account

#### [ kwestie ] moeilijke typos in het malplaatjeopties van Widget van de Catalogus

Het systeem lost nu typos in de malplaatjeopties van Widget van de Catalogus op.

_AC-11576 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38185) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38178)_

#### [ Uitgave ] Verwijderde onnodige spatiëring op achterste-end raster

Het systeem verwijdert nu overbodige spatiëring in het achtergrondraster wanneer er geselecteerde items zijn

_AC-11579 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38502) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/32622)_

#### Opgeslagen code van de klantengroep komt niet overeen met de invoer bij gebruik van multibyte-tekens

Probleem verholpen waarbij codes voor klantgroepen met multibyte-tekens werden afgekapt en niet overeenkwamen met de ingevoerde waarde. De update zorgt ervoor dat de volledige invoer correct wordt opgeslagen, zodat klantgroepen met multibyte-namen correct kunnen worden gemaakt.

_AC-1335 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39342) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a06a4a57)_

#### Probleem bij het bijwerken van de e-mail van de klant in Admin Panel met ö en .swiss domain

Het deelvenster Beheer accepteert nu e-mails van klanten met speciale tekens en met speciale domeinen.
Eerder, ontbrak het bijwerken van een klantene-mail aan een adres zoals max@möstermann.swiss met fouten over ongeldige hostnames en TLDs.
AC-13409

_AC-13409 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39394) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/d3ea191d)_

#### Schakelaar voor abonneetoewijzing voor nieuwsbrief werkt niet per website/winkel

Het systeem handelt abonnement met nieuwsbrief correct af wanneer wij veelvoudige websites/verhalen hebben toen het op globaal niveau werd onbruikbaar gemaakt

_AC-14283 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39751) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39752)_

#### [ Uitgave ] Verwijderde e-mailonthulling

Het systeem geeft nu een foutbericht weer waarin een onjuiste e-mail wordt aangegeven als de ingevoerde e-mail niet nodig is om de account te bevestigen, ongeacht of de klant bestaat of niet.

_AC-14561 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39574) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39570)_

#### Kan commentaar voor wenslijstonderdelen niet wissen via `updateProductsInWishlist` GraphQL-mutatie

De wenslijstopmerkingen werden niet bijgewerkt via GraphQL-mutaties. Dit probleem is nu opgelost.
Opmerkingen worden nu op de juiste wijze bijgewerkt en in de API-reactie en in de winkel weergegeven.

_AC-14682 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39911) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Product dat op Mobiel is verwijderd, verschijnt nog steeds in de sectie Mini Compare van het Web tot opnieuw aanmelden

Het systeem verwijdert nu het product dat direct uit alle vergelijkingsweergaven op zowel mobiel als web verdwijnt, inclusief de mini-vergelijkingssectie.

_AC-14703 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39905) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40023)_

#### Voor-/achtervoegselinstelling tonen die is genegeerd wanneer deze is ingesteld op Nee

Het voorvoegsel/achtervoegsel voor de naam van de klant werd ook in bestellingen weergegeven, zelfs als dit in de configuratie was uitgeschakeld. Dit probleem is nu opgelost.
Nu, worden de prefix/achtervoegselwaarden gestript van ordedetails die op config het plaatsen worden gebaseerd.

_AC-15074 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40036) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Storefront-accountregister van klant: e-mailadresnotatie wordt geconverteerd met verschillende domeinnotaties

Deze bug verholpen een probleem waarbij e-mails van klanten met speciale tekens in het domein (bijvoorbeeld tec55241@adòbe.com) automatisch werden omgezet in de indeling voor punycode (tec55241@xn—adbe-mqa.com).
In Magento 2.4.9-alpha3 zorgt de correctie ervoor dat dergelijke e-mailid&#39;s ongewijzigd en geldig blijven, zodat leveringsfouten worden voorkomen.

_AC-15177 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### Ontbrekende validatieberichten (afbeeldingsfout) op registratieformulier

In de vereiste velden op de pagina voor het aanmaken van een klantenaccount werden geen validatieberichten weergegeven als deze leeg waren. Dit probleem is nu opgelost.
Nauwkeurige foutberichten worden nu weergegeven voor alle lege of onjuiste velden.

_AC-15185 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40076) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Titel van modemtitel voor annulering van bestelling ontbreekt

Het systeem lost nu een ontbrekende vertaling in de orde annuleringsmodaal op de storefront op. Wanneer een klant op de knop Annuleren klikt op de pagina Mijn account > Mijn bestellingen, wordt een modaal venster weergegeven waarin om een annuleringsreden wordt gevraagd. De modale titel was echter eerder gecodeerd en kan niet worden vertaald. Deze wijziging zorgt ervoor dat de modale titel een juiste vertaalmethode gebruikt.

_AC-15260 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40098) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40100)_

#### Uitgave na aanmelding in magento 2.4.8-p1

Het probleem met Magento 2.4.8-p1 waarbij de koppeling &quot;Account maken&quot; na de aanmelding nog steeds zichtbaar was op de startpagina, is opgelost.
De koppeling is nu correct verborgen na de aanmelding en consistent met andere pagina&#39;s.

_AC-15292 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40120)_

#### [ Uitgave ] Reeks isSecureArea alvorens klant te schrappen

Het systeem werkt nu prima en deze PR-sets isSecureArea voor het verwijderingsproces en de klant kan zich opnieuw met succes registreren.

_AC-15723 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40211) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38462)_

#### [ de verrichting van de Wolk ] van de Schrapping is verboden voor huidige gebiedsfout tijdens de verwezenlijking van de klantenrekening

Nadat de oplossing die een klant met een ongeldig adres opslaat een bericht terugkeert die de reden voor invaliditeit in plaats van irrelevant beschrijft &quot;de verrichting van de Schrapping is verboden voor huidig gebied&quot;.

_ACP2E-3791 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6ea61121)_

#### [ B2B ] Webapi- verzoeken gaan oneindige lijn voor geregistreerde klanten wanneer &quot;eav&quot;geheim voorgeheugen onbruikbaar maakte

Na de correctie leidt het uitschakelen van de ev-cache niet tot een oneindige lus tijdens bepaalde REST-aanvragen.

_ACP2E-4191 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Fout bij laden van landinstelling

Probleem verholpen waarbij het maken van een klantenaccount is mislukt bij gebruik van de landinstelling Arabisch en het kenmerk Geboortedatum is ingesteld op weergave op de winkel. Het account kan nu met succes worden gemaakt in deze configuratie.

_ACP2E-4311 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

#### Fout Ongeldige datum bij bijwerken van accountgegevens

Klanten kunnen hun account nu bijwerken met succes wanneer ze de landinstelling Arabisch gebruiken. Eerder werd geprobeerd de accountinformatie op te slaan. De geboortedatum is mislukt als gevolg van een ongeldige datumfout.

_ACP2E-4344 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

### Account, beheerinterface

#### [ Wolk ] Geen dergelijke entiteit met cartId

Oplossing voor een probleem waarbij het gebruik van Aanmelden als klant met twee bedrijfsbeheeraccounts in dezelfde sessie een fout als &quot;Geen dergelijke entiteit met cartId&quot; veroorzaakte.

_ACP2E-4137 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### Door de klant gemaakte foutberichten voor formulieren worden niet vertaald

Probleem verholpen waarbij berichten met validatiefouten van klanten niet correct werden vertaald en opgemaakt voor verschillende interfaces. Validatiefouten geven nu correct vertaalde berichten weer in alle gebieden van de toepassing: storefront, adminhtml, rest api en graphic.

_ACP2E-4354 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

### Gebruikersinterface van beheerder

#### Raster Categorie-producten > Status &amp; Visibility Kolommen zijn leeg wanneer u sorteren op naam

Probleem verholpen waarbij de kolommen Status en Zichtbaarheid leeg werden weergegeven in het raster Categorieproducten bij het sorteren op productnaam.
In het raster worden nu correct alle kolomgegevens weergegeven na het sorteren, zodat u over nauwkeurige productinformatie beschikt in het deelvenster Beheer.

_AC-10659 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38233) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3cf1a106)_

#### E-mailsjabloon store-switch

Probleem verholpen waarbij de winkelswitch in de voorbeeldweergave van de e-mailsjabloon voor nieuwsbrief niet werd geopend wanneer hierop werd geklikt vanwege vervangen jQuery-code. Het bijwerken van de laadgebeurtenis heeft de juiste functionaliteit hersteld, zodat gebruikers naar behoren toegang hebben tot de opslagschakeloptie.

_AC-12334 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38892) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### De FPT-waarde in de winkelwagentje en de productpagina zijn verschillend voor dezelfde configuraties voor eenvoudige producten

FPT-waarden zijn nu consistent tussen winkelwagentjes en productpagina&#39;s voor eenvoudige producten.
Eerder konden de waarden voor Vaste productbelasting (FPT) in decimalen verschillen tussen de winkelwagentje- en productpagina&#39;s, zelfs als dezelfde configuraties werden toegepast.
AC-13066

_AC-13066 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8953613e)_

#### Meerdere opties voor selecteren/selecteren van kenmerken kan niet worden opgeslagen wanneer de stalenmodules zijn uitgeschakeld

Meerkeuzeopties/kenmerkopties selecteren kunnen nu worden opgeslagen wanneer de modules Stalen zijn uitgeschakeld.
Eerder, veroorzaakte het onbruikbaar maken van de modules van Monsters uitzonderingen wanneer het creëren van nieuwe multiselect/uitgezochte attributenopties.
AC-13071

_AC-13071 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8953613e)_

#### De FPT-waarde in de winkelwagentje en de productpagina zijn verschillend voor dezelfde configuraties voor een dynamisch product

FPT-waarden zijn nu consistent tussen winkelwagentjes en productpagina&#39;s voor dynamische producten.
Eerder konden de FPT-waarden (Fixed Product Tax) verschillen in decimalen tussen de winkelwagentje- en productpagina&#39;s voor dezelfde configuraties.
AC-13075

_AC-13075 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8953613e)_

#### Datumnotatie niet gerespecteerd in dateUI-component

Oplossing voor een probleem waarbij de component Date UI de geconfigureerde indeling negeerde en onjuiste waarden weergaf. De correctie zorgt ervoor dat het datumveld nu de opgegeven indeling (bijvoorbeeld Y-m-d) voor zowel weergave als invoer in acht neemt.

_AC-13174 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39218) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### Geen optie beschikbaar om bronnen te verwijderen

Er is een verwijderoptie toegevoegd voor inventarisbronnen in de beheerinterface, zodat beheerders extra bronnen kunnen verwijderen in plaats van alleen bronnen in of uit te schakelen. Deze verbetering verbetert het voorraadbeheer door betere controle over ongebruikte bronnen te verstrekken.

_AC-13354 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/32362) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/1b6c8a3e)_

#### Categorieboomstructuur in admin wordt niet uitgebreid om alle geselecteerde geneste categorieën van niveau 3 weer te geven

Probleem verholpen waarbij de boomstructuur van de beheercategorie niet werd uitgebreid tot geselecteerde geneste categorieën van meer dan niveau 3. Na de correctie worden alle geselecteerde categorieën automatisch uitgebreid, waardoor de zichtbaarheid en bruikbaarheid in alle aan de categorie gerelateerde voorwaarden worden verbeterd.

_AC-13363 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### [ Uitgave ] verbetert gebruikerservaring met rolboom

Met deze pull-aanvraag voegt u knoppen toe om alle elementen samen te vouwen, alle elementen uit te vouwen en vertakkingen uit te vouwen met geselecteerde items. Deze functionaliteit is vergelijkbaar met de functionaliteit in de categoriestructuur (Catalogus -> Overzicht -> Categorieën)

_AC-14020 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39654) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/36511)_

#### Logbestanden voor importeren/exporteren worden niet gemaakt in Systeem > Handelingenlogboeken > Raster rapporteren

Geïmplementeerde logboekregistratie voor import/export-beheeracties, zodat deze nu worden weergegeven in Systeem > Handelingenlogboeken > Rapport. Dit zorgt voor een betere controle door importactiviteiten op te nemen die voorheen ontbraken.

_AC-14266 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/b5e99d20)_

#### Symfony\Component\Mime\Exception\LogicException: De header &quot;Sender&quot; moet een instantie zijn van &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (met &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)

Adobe Commerce verzendt nu registratiee-mails wanneer een aangepast return-path-adres voor SMTP is geconfigureerd. Eerder werd in vanilla Adobe Commerce 2.4.8 met system/smtp/set_return_path ingesteld op 2 en system/smtp/return_path_email ingesteld op een aangepast adres, de klantregistratie voltooid maar de registratie-e-mail is niet verzonden en Adobe Commerce heeft deze fout geregistreerd: Symfony\Component\Mime\Exception\LogicException: De header &quot;Sender&quot; moet een instantie zijn van &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (kreeg &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;).

_AC-14520 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39823) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/1e14bd72) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/1514117f)_

#### De vernieuwingsvolgorde krijgt geen laatste aangepaste kenmerkgegevens

Probleem verholpen waarbij bij het vernieuwen van de orderpagina de meest recente aangepaste klantgegevens voor kenmerken niet werden weergegeven. Na de correctie worden bijgewerkte kenmerkwaarden nu weerspiegeld zonder dat de volgorde hoeft te worden geannuleerd en opnieuw hoeft te worden gemaakt.

_AC-14690 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/30301)_

#### [ Uitgave ] vervangt afgekeurde escaper

Verwijderd getEscaper() en toegevoegd via constructorinjectie.

_AC-15132 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40062) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38135)_

#### Welkomstbericht dat de productcategorie overlapt in de mobiele weergave

Probleem opgelost waarbij de welkomstnaam in de mobiele weergave overlapte met de productcategorieën en kliks werd geblokkeerd.
Categorieën zijn nu volledig zichtbaar en kunnen zonder overlappende problemen worden aangeklikt.

_AC-15166 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/1b1baf1d)_

#### De knop Formulier opnieuw instellen werkt niet zoals verwacht

Het systeem werkt nu prima wanneer u op de knop Herstellen klikt zonder de hele pagina opnieuw te laden, worden de formuliergegevens opnieuw ingesteld.

_AC-15204 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40092) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40094)_

#### [ Uitgave ] PageCache/AccessList: voeg CIDR steun toe

Het systeem keurt nu purge verzoeken binnen een netwerk goed, is het gemakkelijker om een waaier te leveren CIDR.

_AC-15804 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39953) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37809)_

#### [ Uitgave ] voegt verklarende titels aan geheim voorgeheugenbeheerknopen toe

Het systeem voegt nu verklarende titels aan geheim voorgeheugenbeheerknopen toe wanneer u de curseur beweegt

_AC-16212 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38607) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38598)_

#### Een functie bieden voor het massaal verwijderen van belastingtarieven via het raster

Admin-gebruikers kunnen nu meerdere belastingtarieven tegelijk verwijderen uit het raster Admin Tax Rates.  [&#x200B; GitHub-33399 &#x200B;](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/33399) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/33484) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/5cd64dd0)_

#### Aanwijskleur niet toegepast op statische rasters in beheer

De aanwijskleuren worden nu toegepast zoals u had verwacht op de rijen statische beheerrasters.[&#x200B; GitHub-35358 &#x200B;](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35358) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/35384)_

#### Items voor de parameter reCAPTCHA kunnen niet worden opgelost in exception.log voor het deelvenster Google reCAPTCHA Admin

Er is een reCaptcha-fout opgelost in het `var/log/exception.log` -bestand voor de aanmelding voor Google V3 reCAPTCHA Admin en er worden geen foutberichten geregistreerd. Eerder, werd de volgende fout geworpen om de paar seconden toen een admin gebruiker hun **Configuratie** > **Veiligheid** > **Google reCAPTCHA Admin Comité** montages vormde: `main.ERROR: Can not resolve reCAPTCHA parameter. {"exception":"[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)"} []`.  [&#x200B; GitHub-34975 &#x200B;](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/34975) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/4f7e5983) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/security-package/commit/804dbc2a)_

#### De prijsregel voor winkelwagentjes met voorwaarde-SKU houdt geen rekening met de &#39;voorloopnullen&#39; in de SKU (sku: 01234 is hetzelfde als 1234)

Het systeem behandelt nu correct de prijsregel van de Kar met voorwaarde SKU rekening houdt met &quot;belangrijke nul&quot;in SKU

_AC-9428 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37919) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39525)_

#### Probleem met standaardgedrag voor kenmerkoptie-optiewaarde voor Multiselect

Voorafgaand aan de correctie werden de standaardwaarden voor veelvoudige optiekenattributen niet behoorlijk bewaard. Na de correctie worden de waarden nu op de juiste wijze opgeslagen in de database.

_ACP2E-3523 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### Probleem tijdens het verplaatsen van de producthoeveelheid naar het winkelwagentje van de beheerder

Wanneer u een bestelling maakt van de beheerder, verdwijnen de producten in de klantenkar op de zijbalk niet wanneer ze aan de bestelling worden toegevoegd.

_ACP2E-3563 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### [ Staging2 ] Opgeslagen kaarten zijn niet zichtbaar op Admin paneel

Hiermee wordt het probleem verholpen waarbij de betalingsoptie &quot;Opgeslagen kaart&quot; niet meer wordt weergegeven in het formulier voor plaatsing van de achterste bestelling na een upgrade.

_ACP2E-3830 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### Beperkte admin-gebruikers kunnen standaardconfiguraties opslaan/bijwerken ondanks Store-Specific Machtigingen

Hiermee wordt het probleem verholpen waarbij gebruikers met beperkte beheerdersrechten het bereik Standaardconfiguratie konden zien en proberen bij te werken, hoewel ze alleen aan specifieke websitebereiken waren toegewezen. Dit kan tot verwarring leiden.

_ACP2E-4011 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Configureerbare productprijs die is opgeslagen in de DB voor elk weergavebereik van de winkel. Dit leidt tot problemen in de sorteerfunctie Producten in categorie waarvoor de opgeslagen prijs geen relevantie heeft in de frontend

Het selectievakje Standaardwaarde gebruiken voor een configureerbaar product is verwijderd wanneer de prijs per website wordt geconfigureerd en een winkelweergave is geselecteerd op de voor beheerders in de gebruikersinterface configureerbare productbewerkingspagina.

_ACP2E-4036 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/fab20b00)_

#### [ Admin het Beleid van het Wachtwoord van KANTOREN ] komt niet naleving PCI DSS 4.0 (minimum 12 Karakters) na

Beheerders kunnen nu de minimale lengte van wachtwoorden voor gebruikers met beheerdersrechten configureren via Opslag > Configuratie > Geavanceerd > Beheer > Beveiliging. Deze verbetering verstrekt grotere veiligheidsflexibiliteit terwijl het handhaven van bestaand wachtwoordbeleid. De validatie wordt afgedwongen tijdens het maken/wijzigen van gebruikers en het opslaan van de configuratie, met frontend-validatie in real time voor een betere gebruikerservaring.

_ACP2E-4044 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### Datumfilterprobleem wanneer de interfacetaal van het beheerder Japans is

Het filter en de kolom van de Verjaardag zullen het verenigde formaat M/d/y, zelfde als &quot;Klant sinds&quot;filter/kolom gebruiken

_ACP2E-4052 - [&#x200B; GitHub kwestie &#x200B;](https://stg1.navi-online.kakuyasu.co.jp/adminCgWN7zCh/admin/system_account/index/key/d6fdbee50ff25178d1fef981ec823c5e82e8cee6959717790031bb900c4d6633/) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### Witte blokken worden aan beide zijden van de koptekst van het beheerraster weergegeven

Probleem met visuele uitlijning in beheerrasters is opgelost. Als u eerder horizontaal door productrasters schuift in het deelvenster Beheer, worden witte blokken verkeerd uitgelijnd aan de linker- en rechterkant van de rasterkop. De elementen van de rasterkoptekst behouden nu de juiste verticale uitlijning tijdens het schuiven, zodat beheerders grote productcatalogi beter kunnen beheren.

_ACP2E-4104 - [&#x200B; GitHub kwestie &#x200B;](https://mcprod.pap-store.acer.com/index.html)_

#### UI-componentbestandUploader werkt niet correct op 2.4.8-p1/ 2.4-develop

Verbeterde bestandsupload voor aangepaste ui-component met meerdere selecties om uploaden toe te staan bij klikken in uploadgebied.

_ACP2E-4162 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/ee918f0d)_

#### [ op Prem ] nieuw creeerde Orders/Bedrijven/Klanten automatisch inbegrepen in &quot;Uitgezocht Al&quot;Reikwijdte tijdens uitgezocht Proces

Probleem verholpen waarbij bij het uitvoeren van massaacties onbedoeld alle records op een stramienpagina voor vaste beheerdersrechten werden verwijderd. Eerder, zou het net automatisch op &quot;selecteren allen&quot;wijze intern schakelen wanneer het aantal geselecteerde punten het totale aantal aanpast, die massaacties veroorzaken om alle verslagen in plaats van enkel uitdrukkelijk geselecteerde degenen te beïnvloeden.

_ACP2E-4202 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6e134409)_

#### Oplossing uit ACP2E-3362 werkt langzaam op MariaDB 10.6

Verbeterde prestaties van de voorste zoekpagina bij grote aantallen historische zoekverzoeken.

_ACP2E-4225 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/ab891304)_

#### Datumfilter werkt niet volgens de tijdzone van de opslag op het raster voor creditmemo&#39;s

Voorafgaand aan de moeilijke filtrerende lijsten door datumattributen veroorzaakte ontbrekende punten wegens tijdzoneverschillen tussen geselecteerde datum en opgeslagen data nu, nadat de filters van de fixdatum behoorlijk worden toegepast.

_ACP2E-4239 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Het dialoogvenster voor het uploaden van bestanden wordt twee keer geopend wanneer de pagebuilder wordt geïnstalleerd

Voordat de knop Aangepaste component uploaden corrigeren tweemaal zou worden geactiveerd. Nadat u de correctie hebt uitgevoerd, werkt de knop Uploaden naar behoren.

_ACP2E-4241 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2-page-builder/commit/5c4ae802)_

#### Validatiefouten bij verwijderde klantkenmerken bij het wijzigen van klantgegevens.

Vóór de moeilijke situatie, ontbrak het opslaan van de klant en klantenadres als zij veelvoudige attributenopties omvatten die waren geschrapt. Na de correctie kunnen beide worden opgeslagen, zelfs als er nog meerdere kenmerkopties aanwezig zijn.

_ACP2E-4281 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### JS-waarschuwing in het dashboard voor beheer: &quot;Start de lader naar verwachting, maar vond er geen in het bewegingsgebied&quot;

Probleem verholpen met de JavaScript-waarschuwing die in de browserconsole werd weergegeven toen grafieken waren ingeschakeld voor het dashboard voor beheer. Eerder, wanneer het toegang tot van het admin dashboard met toegelaten grafieken, zou een verouderde zuivert controle verkeerd &quot;Verwacht om loader te beginnen maar vond geen in het dom&quot;worden gewaarschuwd alhoewel de functionaliteit correct werkte.

_ACP2E-4336 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

#### [ CLOUD ] Configuratie met Bewerkbare Config van de Afhankelijkheid wanneer het Gebrek dat in de Configuratie van de Opslag wordt gecontroleerd

Probleem verholpen waarbij velden voor systeemconfiguratie na het laden van de pagina konden worden weergegeven, ondanks dat Standaard/Website gebruiken werd gecontroleerd.

_ACP2E-4337 - [&#x200B; GitHub kwestie &#x200B;](https://mcstaging.pap-store.acer.com) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

#### Beheersgrafiek van dashboardvolgorde leidt tot uiteindelijke grootte

De dashboardordegrafiek voor beheerders wordt nu direct weergegeven zonder dat de animatie onnodig moet worden aangepast.

_ACP2E-4398 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38860) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Page Builder kan inhoud niet opslaan in mobiele weergave vanwege JS-fout (TypeError: Cannot read properties of undefined)

Probleem verholpen waarbij het opslaan van pagina&#39;s in de Page Builder tijdens het toevoegen van banners in de mobiele weergave werd voorkomen.

_ACP2E-4399 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38565) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2-page-builder/commit/bdac5bca)_

### Admin UI, B2B

#### B2B-aanmelding als koptekst van klant heeft nog steeds Magento-branding

Eerder staat in de koptekst van de winkel &quot;U bent nu verbonden als &lt;naam klant> op &lt;naam winkel>&quot; met Magento-branding. Deze is nu gefixeerd en de header wordt weergegeven met ADOBE-branding.

_AC-14361 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/fadcfa8b)_

### Beheerdersinterface, catalogus

#### Het opslaan van het product mislukt als Catalogusregel actief is en de modus Realtime ingeschakeld is

Probleem verholpen waarbij indexering van catalogusregels zou kunnen mislukken met een foutmelding in een DDL-transactie tijdens het opslaan van producten door indexering van catalogusregels los te koppelen van de producttransactie.

_ACP2E-4378 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Admin UI, Content

#### Uitzondering &quot;Kan uitvoering voor paden met media-elementen niet maken&quot; tijdens het invoegen van de afbeelding

Nadat u de waarden voor Maximumbreedte en Maximumhoogte van de configuratie voor optimalisatie van de medialagalerie hebt verwijderd, treedt de fout niet meer op tijdens het optimalisatieproces voor de afbeelding.

_ACP2E-3781 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

### Admin UI, Order

#### Maken van beheervolgorde: sessiegrootte overloop bij het toevoegen van 20+ producten (sessiegrootte overschrijdt de limiet van 256 kB)

Oplossing voor een overloop van de sessiegrootte tijdens het maken van de beheervolgorde door te voorkomen dat grote HTML-reacties worden opgeslagen in de sessie voor JSON-verzoeken, zodat bulkproducttoevoegingen probleemloos werken zonder de beheerder uit te loggen.

_AC-15893_

### Admin-gebruikersinterface, beveiliging

#### Zwak wachtwoordbeheer

De admin-gebruiker kan niet worden opgeslagen wanneer u hetzelfde wachtwoord gebruikt. Eerder is het bestand opgeslagen zonder de juiste validatie.

_ACP2E-3657 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

### Admin-gebruikersinterface, BTW

#### Fiscaal tarief admin ui-fout

Met dit ticket werd een probleem opgelost in de gebruikersinterface van de beheerder van het belastingtarief, waarbij het veranderen van land (bijvoorbeeld vanuit de VS → VK) nog steeds de eerder geselecteerde Amerikaanse staat weergaf, misleidende gebruikers.
In 2.4.9-alpha3 wordt het statusveld nu teruggezet naar * als het geselecteerde land geen frames heeft.

_AC-8440 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

### Analyse/rapportage

#### [ Uitgave ] voegde de lijst van gewenste personen van SCP voor Analytics toe als u slechts Google Analytics gebruikt

Deze PR voegt een CSP whitelist aan de module van Google Analytics toe, toelatend het om onafhankelijk zonder een afhankelijkheid van Google Adwords te functioneren. Google Analytics werkt nu correct, zelfs als de Google Adwords-module is uitgeschakeld.

_AC-16311 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40051) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40032)_

#### Dubbele bestandsheaders in CSV-bestanden met geavanceerd rapport die lege rapporten veroorzaken

Na de moeilijke situatie, bevatten de rapporten voor de geavanceerde rapporteringseigenschap worden geproduceerd niet meer gedupliceerde kopbalrijen in gevallen wanneer het rijaantal de partijgrootte overschrijdt.

_ACP2E-4187 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Verlaten karretrapport bevat ongeldige tekens

Rapport Afgewezen winkelwagentje dat is geëxporteerd als CSV-bestand bevat nu correct weergegeven tekens voor valutasymbolen zoals Indiase roepie bij openen in MS Excel.

_ACP2E-4288 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### Update voor MDVA-19640 voor compatibiliteit met 2.4.8

Met de correctie worden de taken voor de snijtaak van de analysemodus verplaatst van de standaardgroep naar de analytische groep

_ACP2E-4309 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

#### Ontvangsten worden niet weergegeven in bestellingen/factuurrapporten in Admin voor de website/valuta van Canada

In sommige aan bestellingen gerelateerde rapporten werden geen wisselkoersen voor winkels toegepast. Na de moeilijke situatie, passen de rapporten behoorlijk gevormde opslagtarieven toe.

_ACP2E-4361 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

### B2B

#### validatie van bedrijfsvelden mislukt voor uitchecken door gast

Het uitchecken door de gast valideert nu het veld Bedrijf.
Eerder, toen het bedrijfattribuut werd vereist, ontbrak de gastcontrole met de fout: &quot;Bedrijf is een vereiste waarde,&quot;zelfs toen het gebied werd gevuld.
AC-14987

_AC-14987 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40011) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/f1adb44e)_

#### Rest API producten-render-info de verkeerde definitieve prijs voor het programma geopende klant

Het kaartje heeft een moeilijke situatie voor Rest API producten-teruggeven-info de verkeerde definitieve prijs voor het programma geopende klant

_AC-5979 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35757)_

### B2B, winkelwagentje en kassa

#### Geen dergelijke entiteit met cartId = X fout wordt getoond in Storefront wanneer login B2B bedrijfgebruiker van admin eigenschap &quot;Login als Klant&quot;

Nu is de fout &#39;&#39;Geen dergelijke entiteit met cartId = X&#39;&#39; niet meer zichtbaar nadat u zich met succes hebt aangemeld bij de back-end van de beheerder wanneer u de functie &#39;&#39;Aanmelden als klant&#39;&#39; gebruikt.

_ACP2E-3994 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Het ontbrekende factuuradres voorkomt dat bestellingen worden geplaatst met de verzendmethode &quot;In store Delivery&quot;

Probleem opgelost waarbij het factuuradres niet automatisch werd ingevuld tijdens het uitchecken toen Ophalen in de winkel als de leveringsmethode was geselecteerd. Zonder factuuradres kan het afrekenen niet worden voltooid.

_ACP2E-4030 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/42d23211)_

### Winkelwagentje en Afhandeling

#### Magento 2.4.7-update (mini)kart zonder decimale hoeveelheid toegestaan

Magento handelt nu correct als we de hoeveelheid bijwerken met decimalen van mini cart als de landinstelling NL (Nederlands) was

_AC-13238 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39236) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39669)_

#### [ Uitgave ] voegt EventPrefix en EventObject toe aan het model van de controleovereenkomst

Het systeem bevat nu EventPrefix en EventObject voor het model van de uitcheckovereenkomst, waardoor gebeurtenissen met een gebeurtenisvoorvoegsel kunnen worden geactiveerd. Deze verbetering biedt ontwikkelaars meer flexibiliteit bij het werken met gebeurtenissen voor afrekenovereenkomsten. Eerder, steunde het model van de controleovereenkomst geen EventPrefix en EventObject, die de capaciteit beperken om gebeurtenis behandeling aan te passen.

_AC-13252 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/32510) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/32451)_

#### [ Ervaring van de Ontwikkelaar van 0&rbrace; kwestie: De codestijl van AbstractItem van het citaat (SOP-348 van SwiftOtter)]

In deze aanvraag voor aftrekken worden misleidende methodedeclaraties voor methoden voor abstract item gecorrigeerd.

_AC-13334 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39340)_

#### Validaties voor Gegroepeerde productvoorkeuren ontbreken

Het systeem werkt nu goed en geeft een validatiefout weer wanneer we een negatieve hoeveelheid en maximale hoeveelheid proberen toe te voegen

_AC-13524 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39479) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39480)_

#### [ Uitgave ] Update subtotal.phtml

Het systeem werkt subtotal.phtml met de correcte spatiëring bij

_AC-13907 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39619) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39612)_

#### Kan de bestelling niet bij de gast plaatsen

Adobe Commerce staat gastgebruikers nu toe met succes orden te plaatsen wanneer het middelste naamgebied zoals vereist in Admin wordt gevormd. Eerder, in Adobe Commerce 2.4.8-bèta1 (PHP 8.3/8.4), vormend middennaam zoals vereist en het controleren als gast verhinderde orderplaatsing zelfs toen een middennaam werd verstrekt, die voltooiing van de controle blokkeerde. AC-14241

_AC-14241 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/27217d0e)_

#### [ Graphql ] kan ongeldig voor niet-nullable gebied &quot;SelectedCustomizableOption.label&quot; terugkeren

Het systeem genereert nu geen interne serverfout met een bericht als de geselecteerde optie niet langer bestaat

_AC-14256 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39729) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39888)_

#### GraphQL addWishlistItemsToCart kan de hoeveelheid bestaande winkelwagentitems niet bijwerken als één item voor de lijst met winkelwagentjes ongeldig is (Magento 2.4.7-p3)

Probleem verholpen waarbij de GraphQL addWishlistItemsToCart-mutatie de verwerking stopzette wanneer een ongeldig configureerbaar product werd aangetroffen. Na de correctie worden geldige wenslijstonderdelen aan het winkelwagentje toegevoegd en worden de hoeveelheden bijgewerkt, terwijl ongeldige items worden overgeslagen met de juiste geretourneerde fouten.

_AC-14464 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39820) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3cf1a106)_

#### [ 2.4.8 ] kan geen orden plaatsen waar de Stad cijfers 0-9, Ampersand, volledige eind of haakje in de Naam van de Stad heeft

Afhandeling is mislukt voor namen van steden met speciale tekens zoals. Dit probleem is nu opgelost. , en, of ronde haakjes.
Orden met dergelijke plaatsnamen worden nu zonder validatiefouten geplaatst.

_AC-14495 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39854) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Voorvoegsel van de gast niet Opgeslagen aan Adres 2.4.8 van het Citaat

Het voorvoegsel van de klant van de gast (Mr/Mevrouw) wordt nu bewaard tijdens het afrekenen.
Eerder, werden de aanhef die door gastklanten werd geselecteerd verloren alvorens de definitieve orde te bereiken, terwijl alle andere adresgebieden correct werden overgebracht.
AC-14705

_AC-14705 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39915) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/f1adb44e)_

#### Salesrule Subselect with Quantity condition Fail to apply

Probleem opgelost waarbij de regels voor de kartprijs met de voorwaarden voor productsubselectie niet van toepassing waren bij het afrekenen.
Nu, worden de kortingen met succes toegepast volgens de gevormde regels.

_AC-14884 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39965) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/fe72c407)_

#### [ Uitgave ] verwijdert ruimte in klassenattributen

Het systeem verwijdert nu een extra ruimte in het klassenattribuut

_AC-14939 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39977) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39970)_

#### Grafiek - De karretje van de Fusie werkt niet correct wanneer de Achterorde wordt toegelaten

Gastwinkelwagentjes zijn niet samengevoegd met winkelwagentje tijdens het samenvoegen van winkelwagentjes via GraphQL. Dit probleem is nu opgelost.
Klantwinkelwagentje geeft nu de gecombineerde hoeveelheid van zowel gasten- als klantenkaarten correct weer.

_AC-15148 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40064) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [ Integratie ] [ Afhandeling ] Depend richtlijnen die in ontbroken betalings e-mailmalplaatje worden bijgewerkt

Slaagde betalings e-mailmalplaatje bijgewerkt om correcte afhankelende richtlijnen te behandelen.
Correctie zorgt ervoor dat het verzendadres en de verzendmethode correct worden weergegeven, indien van toepassing.
Eerder ontbrak deze velden in mislukte e-mails over betalingen.

_AC-15363 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [ Kar ] het Winkelen kart pagina laadt niet wanneer de Vaste productBelasting wordt toegelaten

Probleem verholpen waarbij de winkelwagenpagina oneindig werd geladen toen de optie Vaste productbelasting (FPT) werd ingeschakeld. Het probleem werd veroorzaakt door onjuiste subtotale berekeningen omdat de belasting in hetzelfde HTML-element als de objectprijs werd opgenomen, wat leidde tot een verschil tussen de centrale en de samenvattende subtotalen. Na de correctie wordt het winkelwagentje correct geladen en worden de juiste totalen weergegeven.

_AC-16096 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### Voorwaarde voor prijs van winkelwagentje Handeling &#39;Prijs in winkelwagentje&#39;, van toepassing wanneer dit niet moet.

De regels voor de kartonprijs met de voorwaarde &quot;Prijs voor winkelwagentje lager dan&quot; werden onjuist toegepast op niet-subsidiabele producten. Dit probleem is nu opgelost.
Nu worden coupons correct gevalideerd en afgewezen wanneer de prijzen van winkelobjecten niet voldoen aan de geconfigureerde regelvoorwaarden.

_AC-6997 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/36433) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### [ Uitgave ] Vastgestelde prijs op citaatpunt in plaats van base_price

Het systeem verwerkt de prijs van het aanhalingsteken correct ingesteld op base_price in plaats van de prijs als er meerdere valuta&#39;s op één website op de frontend staan

_AC-9985 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38094) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/36878)_

#### Verlopen permanente aanhalingstekens worden niet opgeschoond door een uitsnijdvak sales_clean_quotes

De verlopen permanente aanhalingstekens worden nu gewist wanneer de &#39;persistent_clear_expired&#39; snijtaak wordt uitgevoerd. Eerder, verliepen blijvende citaten waar niet ontruimd door een andere kroonbaan.

_ACP2E-3493 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/11be3dff)_

#### &quot;Er is iets fout gegaan&quot; bij het afrekenen voor inactief bedrijf

Voorafgaand aan de correctie werd de logout-actie niet correct uitgevoerd op de pagina met winkelwagentjes als de oudere versie van het gebruikersbedrijf niet meer was ingeschakeld. Nu, als het bedrijf niet meer beschikbaar is, wordt de logout behoorlijk uitgevoerd.

_ACP2E-3541 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### De selectie van adressen wordt niet opgeslagen wanneer wij &quot;Controle uit met Meerdere Adressen&quot;

Voorafgaand aan de correctie bij het annuleren van de optie voor meerdere verzendingen, was het adres niet vooraf geselecteerd bij het terugkeren naar meerdere verzendingen. Het standaardadres wordt nu vervangen door een van de selecties die in het scherm met meerdere verzendingen zijn gemaakt.

_ACP2E-3646 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6ea61121)_

#### [ Recente Orden van de Wolk 1&rbrace; verschijnen niet in andere opslagmening als de orden op één archiefmening worden gecreeerd]

Het probleem waarbij op de pagina Mijn account geen recente bestellingen van andere winkelweergaven in dezelfde winkel werden weergegeven, is opgelost. De logica voor het ophalen van bestellingen is bijgewerkt om ervoor te zorgen dat de volgorde in alle weergaven van winkels consistent wordt weergegeven. Deze logica sluit aan op het gedrag van de pagina Mijn bestellingen.

_ACP2E-3807 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a20a6ff2)_

#### hoeveelheid weergegeven als  0 in het gedeelte Winkelwagentje voor klanten van de beheerder terwijl BUNDLE-producten worden toegevoegd  

In de sectie Winkelwagentje in Klantactiviteiten wordt nu het juiste aantal weergegeven. Eerder werd de hoeveelheid weergegeven als 0.

_ACP2E-3872 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/3ad96f6a)_

#### [ de Gratis Verzendkorting van de Wolk ] wordt niet correct verwijderd wanneer het winkelwagentje niet meer aan vereisten voldoet

Het subtotaal (behalve Belasting) in de regel van de kartprijs zal nu kortingen van vorige regels omvatten.

_ACP2E-3973 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Dubbele bestelling gevonden voor dezelfde klant in MultiShipping

Gelijktijdige aanvragen om bestelling met meerdere verzendadressen te plaatsen, resulteren niet langer in dubbele bestellingen voor dezelfde klant

_ACP2E-4117 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [ de grens van de Wolk ] voorraad overschrijdt berichtbericht tweemaal wordt getoond wanneer de Drempel van de Voorraad van buiten wordt geraakt

Probleem verholpen waarbij tijdens winkelwagentupdates dubbele foutbanners werden weergegeven. Eerder, na een AJAX-validatiefout, heeft de backend hetzelfde bericht toegevoegd tijdens het verzenden van het formulier, zodat kopers twee identieke waarschuwingen kunnen zien. Nu slaan we het toevoegen van het extra backend-bericht over, waardoor de winkelwagenpagina op één duidelijke foutbanner blijft staan.

_ACP2E-4192 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### Voor validatie van de Server met factureringsgegevens werkt de Server niet met de REST-API voor verzendinformatie

De gegevensvalidatie van de adresgegevens van de klant is verbeterd om consistenter te zijn tussen REST en GraphQl voor afhandeling.

_ACP2E-4223 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [ Cloud ] Bundel productprijskwestie op kartpagina

Probleem verholpen met de productprijs van de bundel op de winkelpagina met meerdere valuta&#39;s

_ACP2E-4245 - [&#x200B; GitHub kwestie &#x200B;](https://www.techbuyer.com/) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/cbca0396)_

#### Probleem met bereik van winkelwinkelobjecten beheren

Nu worden winkelwagenfouten weergegeven aan de beheerder die het winkelwagentje beheert voor een klant die is toegewezen aan een niet-standaard website. Eerder werden fouten niet weergegeven.

_ACP2E-4348 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

#### Coupon times_gebruikte voorinstellingen na gedeeltelijke annulering van factuur

Coupon times_used count wordt nu correct bijgewerkt wanneer een order gedeeltelijk wordt geannuleerd.

_ACP2E-4365 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### Winkelwagentje en afhandeling, GraphQL

#### Fout bij het toewijzen van foutcode aan een foutcode bij het plaatsen van een order via GraphQL

GraphQL roept om een orde voor een nonexistent of inactief karretje nu correct terug te keren CART_NOT_ACTIVE of CART_NOT_FOUND foutencodes in alle archiefmeningen, die een kwestie bevestigen waar de vertaalde foutenmeldingen eerder in een UNDEFINED code resulteerden.

_ACP2E-3942 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### [ GraphQl ] de kwestie van de de puntkorting van de kartvraag van het karretje op virtuele citaten

Oplossing voor een probleem waarbij de GraphQL-winkelwagenquery een onjuist kortingsbedrag voor virtuele aanhalingstekens heeft geretourneerd. Eerder werden kortingen onjuist toegepast op bepaalde virtuele producten die niet in aanmerking kwamen.

_ACP2E-4248 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/cbca0396)_

#### [ ACSD-68499_2.4.8-p2 van de Wolk ] leidt tot een andere kwestie

Wanneer een graphQL-verzoek voor een item met onvoldoende hoeveelheid is ingediend, is een correct foutbericht met een foutcode geretourneerd en als de gevraagde hoeveelheid beschikbaar is, is de cart-update geslaagd.

_ACP2E-4404 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/1c547060)_

### Winkelwagentje en afhandeling, GraphQL, Inventaris/MSI

#### is_available, kenmerk in CartItemInterface retourneert false, zelfs als de verkoopbare voorraad hoog is

Het is_available attribuut keert waar terug wanneer de verkoopbare voorraad hoog is. Eerder geeft het altijd false.

_ACP2E-3885 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/3ad96f6a)_

### Winkelwagentje en afhandeling, voorraad/MSI

#### 414 Fout bij Eindpunt &#39;Ophaallocatie zoeken&#39; met grote winkelgrootten

Het selecteren van een winkel tijdens het afrekenen met &quot;Winkel selecteren&quot; mislukt niet langer vanwege de lange URL&#39;s wanneer veel producten in de winkelwagentje staan.
Eerder, leidde dit tot een fout 414 die door bovenmatig lange URLs wordt veroorzaakt tijdens archiefselectie wordt geproduceerd, die klanten verhindert het afrekenen te voltooien.

_ACP2E-4266 - [&#x200B; GitHub kwestie &#x200B;](https://mcstaging.casamyers.com.mx/) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/ae1f272f)_

### Winkelwagentje en Afhandeling, Aanbieding

#### De weergave van het saldo op de creditcard wordt niet beperkt door het bereik van de website

Beperkte de de saldocontrole van de Kaart van het Cadeautje met het toegewezen Toepassingsgebied van de Website.

_ACP2E-4379 - [&#x200B; GitHub kwestie &#x200B;](https://www.panini.it)_

### Winkelwagentje en afhandeling, beveiliging

#### [ CLOUD ] die 404 voor JS- dossier op checkout pagina op eerste poging na het uitvoeren van sri flard krijgt

Vóór de fixmixins zouden niet geladen zijn in karretje en uitchecken wanneer minify en bundling ingeschakeld was. Na de correctie moeten alle mengsels op de verwachte wijze worden geladen.

_ACP2E-4128 - [&#x200B; GitHub kwestie &#x200B;](https://ansg.integration-5ojmyuq-f46gejjrfa7be.ap-3.magentosite.cloud/) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

### Winkelwagentje en afhandeling, verzending

#### [ Belangrijkste ] de regel van de Prijs van de Kar respecteert MultiShipping

Voorafgaand aan de toepassing van deze correctie was de regel van de cartprijs voor producten voor meerdere verzendingen niet correct van toepassing toen de voorwaarden voor onderselectie werden toegepast en de mogelijkheid tot gratis verzending werd ingeschakeld. Sinds de correctie is toegepast, functioneert de regel van de winkelwagenprijs voor meerscheepskaarten nu echter naar behoren.

_ACP2E-3666 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogus

#### Cache fpc dupliceren voor dezelfde pagina met dezelfde query

Het systeem identificeert en gebruikt nu correct het zelfde Volledige Geheime voorgeheugen van de Pagina (FPC) voor pagina&#39;s met de zelfde vraagparameters, ongeacht hun orde of navolgende karakters. Hierdoor wordt voorkomen dat de cachemap van de pagina onnodig wordt vergroot. Eerder, zou het systeem een verschillende herkenningsteken FPC voor de zelfde pagina tot stand brengen als de orde van de vraagparameters verschillend was of als er navolgende karakters waren, die tot een toename van de de omslaggrootte van het paginacachegeheugen leiden.

_AC-10722 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38269) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38270)_

#### Ontbrekende indexering van vereiste kolommen in de tabel catalog_product_entity_int

De ontbrekende indexering van vereiste kolommen in de tabel catalog_product_entity_int is toegevoegd

_AC-10844 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38315) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38316)_

#### Fout in bereik in URL-bron van catalogus (_getCategories)

Deze PR voegt een fallback aan standaardwerkingsgebied toe als er geen waarde op het archiefwerkingsgebied in categorie URL middel wordt bepaald.

_AC-11011 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38393) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38394)_

#### [ Uitgave ] Controle als OpenGraph prijs kan tonen

Het systeem werkt prima als we een plug-in gebruiken die de prijs verbergt en deze wijzigingsprijs niet zichtbaar is in de OG-tag.

_AC-11635 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38512) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38510)_

#### Afrondingsprobleem van de prijzen bij het toevoegen van belasting aan weergaveprijzen

Het systeem verhelpt nu het rondom de prijzen bestaande probleem bij het toevoegen van belasting aan weergaveprijzen

_AC-11725 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/18025) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/35730)_

#### [ Uitgave ] staat de regelvoorwaarden van de douanecatalogus toe

Oplossing voor een probleem dat ervoor zorgde dat de regelvoorwaarden voor aangepaste catalogi niet konden worden gebruikt vanwege strikte typecontrole. De correctie vervangt de controle van de klassengelijkheid door instantie van, die de klassen van de douanetoestand toestaat om correct te functioneren en succesvolle regelbevestiging en indexering toe te laten.

_AC-13338 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39339) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### Configureerbaar product verliest opties wanneer toegevoegd aan wenslijst

Probleem verholpen waarbij configureerbare productopties verloren gingen nadat het product aan de verlanglijst was toegevoegd. De geselecteerde opties blijven nu behouden, zodat het product probleemloos aan het winkelwagentje kan worden toegevoegd zonder dat gebruikers worden gevraagd opties opnieuw te selecteren.

_AC-13373 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39363) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/cc0ec250)_

#### Speciale prijs wordt niet correct weergegeven voor het configureerbare onderliggende product van het product (eenvoudig product)

Probleem verholpen waarbij de speciale prijs voor het onderliggende (eenvoudige) product van een configureerbaar product niet correct werd weergegeven op de pagina met productaanbiedingen wanneer &#39;Gebruikt in productaanbieding&#39; was ingesteld op Nee. Nu wordt de speciale prijs correct weergegeven samen met de normale prijs, zodat een consistente prijsweergave voor alle productsoorten wordt gewaarborgd.

_AC-13594 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3cf1a106)_

#### [ Bug ] REST API: De speciale prijzen van de update plaatsen geen waarden voor alle opslagmeningen

REST API werkt nu speciale prijzen bij voor alle winkelweergaven in een website.
Eerder beïnvloedde het bijwerken van speciale prijzen via REST API slechts de gespecificeerde opslagmening, niet alle opslagmeningen in de website.
AC-13671

_AC-13671 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39521) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Problemen met prijsbereik en config.php

In Magento 2.4.2 wordt bij het wijzigen van het prijsbereik via config.php de waarde is_global in catalog_eav_attribute voor het prijskenmerk niet correct bijgewerkt.
Als gevolg hiervan blijven productprijzen wereldwijd en kunnen deze niet per website worden opgeslagen, zelfs niet wanneer het prijsbereik op de website is ingesteld.
De oplossing vereist manueel het bijwerken van de is_global kolom in het gegevensbestand, dat niet ideaal voor productiemilieu&#39;s is.
Dit gedrag is consistent met het standaardontwerp van Magento, waar het prijsbereik Global of Website is, maar niet per winkelweergave.

_AC-13857 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/33559)_

#### [ \Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP fout niet vermeld

Veranderde de naam van een lusvariabele om de &quot;_cache_instance_product_ids&quot;gegevens over het bepaalde product correct toe te voegen dat op verdere vraag moet worden gebruikt.

_AC-14159 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39641) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39642)_

#### Elastic Search mengt zich in de standaardsorteervolgorde van producten (nieuwste eerst wijzigen in oudste eerst)

Het systeem sorteert nu de nieuwste producten in het gegevensbestand (met hoogste entiteit_id) eerst worden getoond

_AC-14411 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/31043) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/36900)_

#### Na de pagina van de archiefschakelaar komt uit geheim voorgeheugen (de schakelaars van de opslag werken niet) in 2.4.8

Het schakelen tussen de archiefweergaven van de winkelkoptekst werkte pas nadat de cache handmatig was gewist. Dit probleem is nu opgelost.
Nu, de omschakeling van de archiefmening werkt correct zonder een geheim voorgeheugen schoon te vereisen.

_AC-14426 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39806)_

#### Genegeerde .less-stijlen met min-breedte: (@screen__l)

Er werden slechts drie producten per rij weergegeven op rubriekpagina&#39;s. Dit probleem is nu opgelost.
Er worden nu vier producten per rij weergegeven zoals u had verwacht.

_AC-14463 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39817) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Het aantal van de lijst van het Wislijst wordt niet getoond op homepage/andere pagina&#39;s behalve wishlist pagina in het klantenmenu

Het aantal wenslijsten werd weergegeven als lege haakjes op pagina&#39;s zonder verlanglijstje. Dit probleem is nu opgelost.
Nu wordt het juiste aantal wenslijstonderdelen weergegeven naast Mijn lijst van wensen op alle pagina&#39;s.

_AC-14607 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39892) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/b3774fbe)_

#### catalog_product_save_before observer genereert een fout met betrekking tot de datum wanneer REST API wordt gebruikt zonder waarden op archiefniveau (getFinalPrice()-probleem)

Deze PR past de verwerking van SpecialFromDate aan om juiste het formatteren te verzekeren wanneer de datum als instantie DateTimeInterface wordt verstrekt. Dit voorkomt fouten die optreden tijdens uitvoering van getFinalPrice() in bepaalde scenario&#39;s.

_AC-14847 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39959) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40003)_

#### URGENT - Kan product niet aan bundel toevoegen wanneer het toe te voegen product aanpasbare opties heeft

Producten met aanpasbare opties konden niet aan bundelproducten worden toegevoegd. Dit probleem is nu opgelost.
Eerder werden dergelijke producten uitgesloten van de lijst &quot;Producten toevoegen aan optie&quot; in het maken van pakketten.
Producten met aanpasbare opties kunnen nu aan bundels worden toegevoegd zonder hun aangepaste opties op te nemen, zodat een goed voorraadbeheer mogelijk is.
Hierdoor kunt u pakketten maken zonder producten te dupliceren of het voorraadniveau te beïnvloeden.

_AC-14958 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39993)_

#### Negatieve `?p=` queryreeks veroorzaakt Elasticsearch-uitzondering

Het Systeem richt nu negatieve ?p= waarde in de paginering van de Categorie, die momenteel in uitzondering resulteert en als geldig verzoek wordt beschouwd

_AC-15191 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40079) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40080)_

#### Het prijsetiket &#39;Zo laag als&#39; wordt weergegeven voor configureerbare producten met één optie

In configureerbare producten werd de prijs weergegeven met een onjuist label &quot;Zo laag als&quot; op PDP/PLP. Dit probleem is nu opgelost.
Het product heeft nu de juiste prijs ($ 500) zonder misleidende labels.

_AC-15237 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40104) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Verkeerde methode die wordt aangeroepen voor knop Toevoegen aan vergelijking

Correctie van de methode gebruikt in \Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect().
Eerder werd getAddToCartButton() onjuist aangeroepen in plaats van getAddToCompareButton().
Deze wijziging zorgt voor het juiste gedrag bij het weergeven van de knop &quot;Toevoegen aan vergelijking&quot; in productaanbiedingen.
Er zijn geen wijzigingen in functioneel gedrag geïntroduceerd. De update verbetert de ervaring van de ontwikkelaar en de juistheid van de code.

_AC-15323 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39754) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### De verkeerde productprijs wordt in verschillende winkelweergaven weergegeven op het winkelwagentje met verschillende valuta&#39;s

Probleem verholpen waarbij in het winkelwagentje onjuiste productprijzen werden weergegeven wanneer verschillende valuta&#39;s werden gebruikt voor verschillende winkelweergaven. Na de correctie wordt nu de juiste omgezette prijs weergegeven op basis van de geconfigureerde valuta, zodat de productpagina en de winkelwagentje consistent blijven.

_AC-15385 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### Verkeerde prijsweergave &quot;Zo laag als&quot; voor configureerbare producten wanneer FPT is ingeschakeld

Bevestigd dat de onjuiste &quot;zo laag als&quot;prijs voor configureerbare producten wanneer FPT werd toegelaten door tweemaal toegepaste belasting werd veroorzaakt; de moeilijke situatie verzekert de definitieve prijsberekening respecteert de belastingconfiguratie en toont nu de correcte prijs.

_AC-15718 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40171) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a06a4a57)_

#### De tijdcomplexiteit van _loadAttributes in Eav\Model\Entity\Collection\AbstractCollection neemt toe met het aantal producten in winkelwagentjes en kenmerken

Deze PR optimaliseerde _loadAttributes in Eav\Model\Entity\Collection\AbstractCollection door genestelde lijnen met serie unie (+) te vervangen en vraag aan _setItemAttributeValue te verminderen, verbeterend prestaties voor grote productkaarten.

_AC-15833 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40216) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40217)_

#### Gecodeerde interactie tussen de Cache van de Inzameling en de Configureerbare Galerie van Producten

Oplossing voor een caching probleem met configureerbare productgalerieën door een defensieve typecontrole toe te voegen om ervoor te zorgen dat media_gallery_images altijd als een verzameling wordt behandeld, die fatale fouten verhinderen die door bedorven geheim voorgeheugengegevens worden veroorzaakt.

_AC-16066 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/33965) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

#### De productpagina bevat een fout vanwege herschrijvingen van URL&#39;s

De productpagina wordt nu geladen wanneer de URL wordt herschreven

_AC-2950 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35371) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39670)_

#### indexer_update_all_views fout met MAGE_INDEXER_THREADS_COUNT

Correctie van probleem met MAGE_INDEXER_THREADS_COUNT > 2 met index voor klantsegment.

_ACP2E-3538 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### Uitzondering tijdens het toevoegen van &quot;Combinatie van voorwaarden&quot; in de widgevoorwaarde voor producten van de Bouwer van de Pagina

Het probleem is opgelost door een controle toe te voegen om ontbrekende of onvolledige voorwaarden over te slaan. Eerder werden foutlogbestanden gegenereerd vanwege de verwerking van onvolledige voorwaarden in het systeem.

_ACP2E-3545 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/11be3dff)_

#### Browser crasht tijdens laden van kenmerkset

Browser loopt niet meer vast op de bewerkingspagina voor kenmerksets als er meer dan 4k-productkenmerken zijn

_ACP2E-3633 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38810) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

#### [ CLOUD ] Product URL herschrijft niet gecreeerd voor Nieuwe Opslag: Go Live Blocker

URL van product herschrijft voor nieuwe winkel is gemaakt.
Eerdere bewerking eindigde met geheugenlek of met time-out.

_ACP2E-3669 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### Standaardwaarde kenmerk voor opties werkt niet

Eerder, toen wij de standaardwaarde van een product veranderden selecteerde attributen, verscheen het als serieelement met de vorige waarden. Nadat deze moeilijke situatie wordt toegepast, wanneer wij een waarde van het productattribuut bijwerken zal het als één enkel element bij eav_attribute lijst bewaren.

_ACP2E-3688 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### [ Belangrijkste 1&rbrace; ] CLOUD [ Beeld die meer dan 400GB van schijfruimte resizing]

Nadat de correctie is uitgevoerd, genereert de opdracht `catalog:images:resize` die met de markering `--skip_hidden_images` wordt gebruikt geen afbeeldingscache voor websites waarop geen afbeeldingen aanwezig zijn.

_ACP2E-3869 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9ad7d277)_

#### Dynamische afbeelding genereren genereert een groot aantal afbeeldingen

Na de correctie worden afbeeldingen alleen gegenereerd voor de websites waaraan het product is toegewezen.

_ACP2E-3927 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/fab20b00)_

#### Opgegeven landID bestaat niet - Ierland (IE)

Na de correctie zijn Ierse postcodes beschikbaar om te zoeken naar ophaallocaties.

_ACP2E-3932 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/4ca73607) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/d2f1d6c6)_

#### Er treden 500 fouten op de voorgrond als gevolg van een onjuiste layoutstructuur in de layout in de cache wordt opgeslagen

Probleem verholpen waarbij een pagina een foutcode van 500 zou retourneren omdat een onjuiste layoutstructuur in de layout in de cache werd opgeslagen. Dit probleem is nu opgelost.

_ACP2E-4040 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### Rapport over productweergaven onjuist - Minder aantal vergeleken met GA

Oplossing voor een bug waarbij report_view_product_index table niet het correcte aantal meningen van de productpagina toonde.

_ACP2E-4045 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6e134409)_

#### Validatiefout voor het veld kortingsbedrag voor regel catalogusprijs in Geplande update

Eerder, alvorens deze kwestie te bevestigen, voor de planningsupdate voor de regel van de catalogusprijs, als het kortingsbedrag door_fixed is dan werd het niet behoorlijk bevestigd wegens de bevestiging-aantal-waaier regel. Nadat deze correctie is toegepast, werkt de validatie correct voor de regel van de catalogusprijs voor vaste prijzen.

_ACP2E-4054 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Btw-validatie mislukt vanwege limiet voor BTW-API-tarief - leidt tot fout-positieve wijziging in klantgroep

Geoptimaliseerd voor de aanvragen voor Europa Vat-validatiefunctie, wat resulteert in minder &quot;snelheidslimiter&quot;-fout

_ACP2E-4072 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/ee918f0d)_

#### Bulkverwijdering in Core Index waardoor fout bij maximale schrijfgrootte tijdens productie optreedt

Hiermee optimaliseert u de opschoonfunctie van de catalogusregelproductindex door twee verwijderingsstrategieën te implementeren op basis van gegevensvolume.

_ACP2E-4085 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

#### Producten worden weergegeven als out-of-stock na het uitschakelen

Na de correctie zijn uitgeschakelde producten niet aanwezig in de widget producten.

_ACP2E-4136 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [ Fouten van de Wolk ] met dubbele ingangen (temp_category_descendants_%)

Tijdens het maken van geplande updates voor omgevingen met een groot aantal geneste categorieën was er een probleem met dubbele vermeldingen. Dit probleem is nu opgelost.

_ACP2E-4159 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [ CLOUD ] vergelijk de kwestie van de Telling van Producten voor verschillende opslag

De productlijst vergelijken werkt nu correct na het schakelen naar een andere storeview

_ACP2E-4249 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/98f028ab)_

#### Geen optie om de standaardinstelling voor &#39;Afbeeldingen en video&#39;s&#39; te gebruiken bij de toewijzing van de afbeeldingsrol

De opties Standaardwaarde gebruiken zijn toegevoegd aan de sectie Afbeeldingen en video&#39;s van het product, waardoor de overerving van instellingen van het standaardbereik mogelijk is.

_ACP2E-4280 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

#### Beperkte categorieproducten die nog steeds in Wishlist worden geteld na update van de klantengroep

Voorafgaand aan de correctie werden categorietoestemmingen niet correct toegepast op wenslijstonderdelen van klanten. Na de correctie worden de items in de wenslijst nu correct weergegeven en gepagineerd op het web en in GraphQL.

_ACP2E-4294 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

#### [ de Prijskwestie van de Wolk ] van de Bundel op PDP en PLP

Prijs voor bundelproduct met normale prijs wordt correct weergegeven op PDP/PLP voor niet-standaardvaluta

_ACP2E-4298 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

#### De klant kan orde voor ontoegankelijk product na de verandering van de klantengroep plaatsen

Eerder, toen het veranderen van de klantengroep van admin, de frontend catalogus en het kart niet de veranderingen in catalogustoestemmingen weerspiegelden. Nadat u deze correctie hebt toegepast, wordt het aanhalingsteken voor de voorkant nu gewijzigd op basis van de bijgewerkte catalogusmachtigingen wanneer de klantengroep wordt gewijzigd van beheerder.

_ACP2E-4300 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

#### Opnieuw indexeren vastgelopen vanwege hoog geheugengebruik

Probleem verholpen waarbij de indexeerfunctie van de catalogusregel te veel geheugen verbruikte en niet kon worden voltooid, waardoor instabiliteit en fouten vanwege onvoldoende geheugen ontstonden.

_ACP2E-4303 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

#### [ CMS ] Geplande Verbinding van de Voorproef van de Update richt aan Onderhoudspagina opnieuw

De geplande Voorproef van de Update van de Verbinding van de Pagina van het Huis met Configurable Producten toont correct lijst van producten. Eerder werd de omleiding van gebruikers naar de onderhoudspagina gewijzigd

_ACP2E-4401 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/1c547060)_

### Catalogus, GraphQL

#### GraphQl ongeldige discontoberekening

GraphQL geeft nu correct kortingspercentages en basisprijzen weer wanneer catalogusprijzen zijn geconfigureerd om belasting op te nemen. Eerder traden ronding-fouten op, zoals het weergeven van 19,99% in plaats van 20%.

_ACP2E-3993 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

#### GetCart GraphQL Media Gallery Field Returns Empty Data after cache flush

Na de correctie wordt de media_gallery van het product geretourneerd zoals wordt verwacht in het GraphQL-antwoord voor het winkelwagentje.

_ACP2E-4185 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

### Catalogus, GraphQL, Zoeken

#### Grafische producten retourneren uitgeschakelde categorieën in de categoriecategorieën

Nadat de moeilijke moeilijke gehandicapte categorieën niet voor de productenverzoek GraphQl zijn teruggekeerd.

_ACP2E-2885 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogus, prestaties

#### Categorieën in admin laden erg langzaam

De prestaties bij het laden van categorieën zijn aanzienlijk verbeterd. Eerder duurde het zo lang om de categorie te laden die een time-outprobleem heeft veroorzaakt.

_ACP2E-3891 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/4ca73607)_

### Catalogus, prijzen

#### Onjuiste korting op catalogusprijsregel toegepast op het onderliggende product

Hiermee wordt het probleem verholpen waarbij de catalogusprijsregel voor de variatie wordt overschreven door het bovenliggende configureerbare product, in het geval dat beide regels dezelfde prioriteit hebben.

_ACP2E-3693 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a20a6ff2)_

#### [ Cloud ] Prijskwestie van de Bundel

Prijs voor Bundel Product met speciale prijs wordt correct weergegeven op PDP/PLP voor niet-standaardvaluta

_ACP2E-4110 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6e134409)_

### Catalogus, product

#### [ Willekeurige Bug ] de lib van Fotorama wordt niet geladen

Het systeem zorgt er nu voor dat de Fotorama-bibliotheek correct is geladen, zodat alle gekoppelde afbeeldingen naar behoren in de galerie met afbeeldingen kunnen worden weergegeven. Eerder was alleen de eerste afbeelding zichtbaar vanwege een probleem met de bibliotheek Fotorama dat niet correct werd geladen.

_AC-12124 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/45b51c9c) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/27217d0e)_

#### De koppeling Producten handmatig toevoegen moet altijd zichtbaar zijn

Probleem verholpen waarbij de koppeling &quot;Producten handmatig toevoegen&quot; niet zichtbaar was bij het maken van een configureerbaar product zonder bestaande configuraties. De koppeling wordt nu altijd weergegeven, zodat beheerders eenvoudige producten gemakkelijk kunnen koppelen zonder dummyconfiguraties te maken.

_AC-13866 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39595) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### Een product bewerken op de achtergrond Verwijdert extra decimalen uit de prijs van de productoptie

Probleem verholpen waarbij tijdens het bewerken van een product in de beheerder de prijzen van productopties tot twee decimalen werden verlaagd. Het systeem bewaart nu de prijzen met hogere decimale precisie, die ervoor zorgen dat de nauwkeurige waarden na sparen worden bewaard.

_AC-14050 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39655) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

### Catalogus, zoeken

#### Verzoek van RestApi &#39;/rest/default/V1/Categorieën?searchCriteria%5Bpage_size%5D=1&#39; mislukt vanwege een time-outfout

De REST API-aanvragen voor categorieën mislukken niet meer met time-outfouten.
Eerder, konden de verzoeken aan /rest/default/V1/categorieën?searchCriteria [ page_size ]=1 met een onderbreking na bepaalde codeveranderingen ontbreken.
AC-13358

_AC-13358 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

### Inhoud

#### graphql (magento 2.4.6-p4) - fout wanneer u probeert een cms-pagina zonder actieve status op te halen

GraphQL-query voor een uitgeschakelde CMS-pagina heeft een interne serverfout geretourneerd. Dit probleem is nu opgelost.
Nu, haalt de vraag een juiste reactie zonder fouten.

_AC-12302 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38877) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Met het formulier voor het delen van lijsten is willekeurige code toegestaan in naamvelden

Oplossing voor een kritieke SSTI (Server-Side Template Injection)-kwetsbaarheid in het formulier voor het delen van wenslijsten, waarbij kwaadaardige code in het berichtveld kon worden ingevoerd en via e-mail kon worden verzonden. De update voegt invoervalidatie toe om sjablooninstructies en onveilige patronen te blokkeren. Er wordt nu een foutbericht weergegeven wanneer ongeldige inhoud wordt gedetecteerd.

_AC-12730 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39024) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### Het plaatsen van csp_whitelist.xml in thema werkt niet en leidt tot intermitterende kwestie

Geïmplementeerde caching van CSP whitelist per websitegebied.

_AC-13069 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38933) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39672)_

#### Na de upgrade naar magento 2.4.7 p2 ziet u de geüploade bestanden niet meer in de mediagalerie

Nieuw geüploade bestanden worden nu na de upgrade weergegeven in de Medialerie.
Eerder, na upgrade naar Magento 2.4.7 p2, werden pas geüploade afbeeldingen pas weergegeven in de Medialerie nadat een handmatige synchronisatie was uitgevoerd.
AC-13262

_AC-13262 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39275)_

#### In de mediagalerie worden onjuiste afbeeldingen weergegeven uit mappen met identieke namen, maar verschillende hoofdletters en kleine letters

Het systeem verhelpt nu een probleem waarbij bestanden die naar een specifieke map in de medialerie zijn geüpload ook zichtbaar zijn in mappen met vergelijkbare namen, maar met verschillende hoofdletters en kleine letters.

_AC-13489 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39382) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39502)_

#### Als u een galerie-afbeelding volledig verwijdert uit een afbeelding, worden de rollen/typen van het bereik ingesteld (basis/klein/miniatuur) en nadat u de &quot;oude&quot; rollen/typen opnieuw hebt toegevoegd, worden deze weergegeven

Het systeem werkt zoals verwacht in het opslagbereik de beelden erven de rollen/types van het nieuwe toegevoegde beeld zoals per het standaardwerkingsgebied

_AC-13556 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39481) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39680)_

#### [ Filter van 1&rbrace; Kleine insect van het Comité Admin ] kan niet raken wanneer de gebiedswaarde `listing component` bevat`\`

Het systeem werkt prima als we paginatitel met slash filteren (bijvoorbeeld Magento\Store)

_AC-13661 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39513) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39535)_

#### Fout: scriptfout voor &quot;Magento_Catalog/js/validate-product&quot; voor pagebuilder voor inhoud voor beheerders met producten laden

Deze PR corrigeert de scriptfout voor catalogAddToCart tijdens het bewerken van de pagebuilder met de productvoorwaarde

_AC-13891 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39604) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39677)_

#### Script-fout catalogAddToCart bij het configureren van de productwidget.

Probleem verholpen met een scriptfout die optrad bij het configureren van de widget Producten met &quot;Combinatie van voorwaarden&quot; in Page Builder. Het probleem is veroorzaakt door ontbrekende JS-bestanden aan de voorzijde, wat leidt tot consolefouten. Na de correctie wordt de widget correct geladen zonder consolefouten.

_AC-13892 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/528af81a)_

#### Selectie blokkeren in widgets met dezelfde id

Het systeem verwerkt nu correct het selecteren van blokken tijdens het maken van widgets wanneer we dezelfde id-blokken hebben

_AC-14132 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39692) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39722)_

#### Logoverstroming op de CMS-pagina met de id 0 bestaat niet

Het systeem werkt zoals verwacht na het creëren van admin gebruiker en wanneer wij een nieuwe pagina system.log creëren heeft geen foutenmeldingen

_AC-14254 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39743) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39746)_

#### [ GraphQl ] de vraag van de Route oneindige lijn

Dit kaartje verholpen de kwestie waar een de routevraag van GraphQL met de identieke Weg van het Verzoek en de Weg van het Doel een oneindige lijn veroorzaakte en uiteindelijk uit tijdde.
In 2.4.9-alpha3, keert de vraag nu de correcte foutenreactie in plaats van het herhalen terug.

_AC-14269 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39707) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### Onbestaande sitemap reageert op productafbeelding

Het systeem wordt nu gerepareerd wanneer we toegang krijgen tot een bestaande sitemap die reageert op een productafbeelding met Response: 404 NOT FOUND

_AC-14295 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39756) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40135)_

#### Cataloguskoppelingswidgets gebruiken onjuiste URL

Het systeem verwerkt nu correct widgets nadat de koppeling naar het catalogusproduct en de cataloguscategorie is toegevoegd en bevat nu ook de juiste URL&#39;s in de HTML-bron

_AC-14437 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39464) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39710)_

#### Tabelvoorvoegsel wordt niet in aanmerking genomen

Adobe Commerce respecteert nu correct de voorvoegsels van de databasetabel wanneer het ontwerp > het themaraster Configuratie in de Admin wordt geladen. Eerder, in Adobe Commerce 2.4.8 met een lijstprefix gevormd in app/etc/env.php, leidde het navigeren aan Inhoud > Ontwerp > Configuratie tot een fout omdat het lijstprefix niet in aanmerking werd genomen, en het net van thema&#39;s niet teruggaf.

_AC-14556 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39847) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Wijzig de constante IMAGE_FILE_NAME_PATTERN in public visible, voor meer flexibiliteit

De constante IMAGE_FILE_NAME_PATTERN in GenerateRenditions.php is openbaar gemaakt, zodat ontwikkelaars flexibeler kunnen werken met afbeeldingsuitvoeringen. De oplossing is opgenomen in Magento 2.4.9-alpha3 met volledige eenheid en integratietestdekking.

_AC-15338 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39733) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### Onjuiste verzendmethode wordt weergegeven op de pagina met revisievolgorde voor meerdere verzendingen

Probleem verholpen bij afhandeling via meerdere verzendingen waarbij op de pagina met revisievolgorde onjuiste verzendkosten werden weergegeven (5 INR in plaats van 10 INR). De update zorgt ervoor dat het juiste verzendbedrag voor elk adres wordt weergegeven.

_AC-15664 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3cf1a106)_

#### bin/magento config :show (of reeks) ontwerp/theme/theme_id ontbreekt

De CLI bevelen bin/magento config :show en config :set ontbrak voor het ontwerp/theme/theme_id weg ondanks de configuratie die aanwezig is.
De opdrachten worden nu uitgevoerd en de thema-id kan zonder fouten worden weergegeven en ingesteld.

_AC-5915 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35751) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### Kan afbeelding met relatief kleine breedte niet uploaden

Het systeem kan de afbeelding niet meer vergroten of verkleinen met een relatief kleine breedte tot de hoogte.

_ACP2E-3558 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### De component Product van de Bouwer van de pagina werkt niet als de gebruiker geen toestemming Widget heeft

Vóór de correctie genereerde de pagina een algemene fout tijdens het openen van een widget zonder machtigingen en werd een GIF voor &quot;laden&quot; weergegeven. Na de correctie wordt nu een modaal venster weergegeven met &quot;Sorry, u hebt machtigingen nodig om deze inhoud weer te geven.&quot; bericht.

_ACP2E-3664 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Onjuist configuratiepad voor stijlconfiguratie van externe opslagpaden

Na de correctie heeft het instellen van de stijlconfiguratie voor het externe opslagpad invloed op de daadwerkelijke configuratie van de AWS S3-padstijl.

_ACP2E-3734 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### Page Builder-productwidgetbestelling wordt niet toegepast in GraphQL

Hiermee wordt het probleem verholpen waarbij de GraphQL-query-reactie ‘route’ geen producten in de juiste sorteervolgorde heeft geretourneerd in een inhoudssoort van Page Builder-producten.

_ACP2E-3898 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Probleem met prijsstelling op niet-Engelse winkelvelden vanwege ICU-bibliotheekversie

Na de correctie wordt de productprijs correct weergegeven in de landinstelling Hebreeuws (Israël).

_ACP2E-3938 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### Configuratie van gecastreerd ontwerp van winkelcode bijwerken

Oplossing van de kwestie waar het bijwerken van de code van de archiefmening de montages van de Configuratie van het Ontwerp wegens het configuratiecache niet behoorlijk verfrist ontruimde.

_ACP2E-3941 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### Page Builder - Product Condition Logic Issue (OF logica gedraagt zich verkeerd en toont minder producten)

Page Builder Products Widget retourneert nu het juiste resultaat wanneer een kenmerk met een algemeen bereik wordt gebruikt in de voorwaarde &quot;Match Any&quot;

_ACP2E-4096 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

#### Productcarrousel voegt onjuiste producten toe aan Page Builder

Vóór de correctie zou een configureerbaar product automatisch zijn opgenomen in de carrousellijsten van het PageBuilder-product als een van de onderliggende items aan de filtervoorwaarden zou hebben voldaan. Na de correctie wordt het bovenliggende product alleen opgenomen als het onderliggende product zelf niet zichtbaar is.

_ACP2E-4341 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

#### De widget Lijst met producten retourneert een onjuist resultaat als meerdere categorieën in de categorievoorwaarde worden vermeld

De widget Lijst met catalogusproducten geeft nu nauwkeurige resultaten weer wanneer meerdere categorieën in de voorwaarde &#39;Categorie is een van&#39; voorkomen. Eerder werd alleen de eerste categorie in de lijst verwerkt.

_ACP2E-4353 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/0a3b7032) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2-page-builder/commit/1c1b3419)_

#### [ de omslagverwezenlijking van de Galerij van de Media van de Wolk 1&rbrace; vereist schrapping_folder toestemming in Nieuwe Galerij van Media - de rollen met slechts create_folder kunnen geen omslagen tot stand brengen]

Eerder, voordat deze correctie werd geïmplementeerd, kon een gebruiker met alleen inhoud een map maken geen map maken in de CMS-mediagalerie. Na de correctie kunnen makers van inhoud in de mediagalerie nu echter alleen mappen maken met de machtiging Map maken.

_ACP2E-4376 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

#### [ KANTOREN ] Duplicerend een pagina van CMS

Vóór deze correctie zou het dupliceren van een cms-pagina met een aangepaste layout-update zijn mislukt. CMS-pagina&#39;s met aangepaste layout-updates kunnen nu zonder fouten worden gedupliceerd.

_ACP2E-4449 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Klanten/klanten

#### Uitzondering op Storefront wanneer Admin een CustomerCustomAttribute-blok toevoegt via CMS Page Content

Probleem verholpen waarbij het toevoegen van het blok CustomerCustomAttribute via CMS-pagina-inhoud een storefront-uitzondering veroorzaakte en ervoor zorgde dat de pagina niet kon worden geladen.
Storefront wordt nu normaal weergegeven en geeft een betekenisvol bericht weer wanneer de inhoud niet kan worden gerenderd, waarbij kritieke fouten worden voorkomen.

_AC-11004_

#### Klanten die zich nu online Admin-raster bevinden, tonen elke keer dat een gebruiker zich aanmeldt, vervolgens weer uit en vervolgens weer in rijen

Probleem verholpen waarbij in het beheerdersraster voor klanten nu online dubbele rijen werden weergegeven wanneer een klant zich afmelde en weer werd aangemeld.
Het net werkt nu het bestaande verslag met de recentste activiteit bij in plaats van het creëren van dubbele ingangen, die nauwkeurige klantenzitting het volgen verzekeren.

_AC-11511 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/528af81a)_

#### Validatie van minimum- en maximumwaarden werkt niet voor DOB-kenmerk in Storefront

Deze bug verholpen het probleem waarbij de minimale en maximale datumvalidatie voor het kenmerk Date of Birth (DOB) niet werkte op de storefront (hoewel deze werkte in Admin).
In 2.4.9-alpha3 blokkeert validatie nu correct het opslaan van klanten met DOB buiten het toegestane bereik, waarbij een foutbericht wordt weergegeven.

_AC-13535 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### Ajax 401 error load on Warning screen in admin panel while Login as Customer permission Introk

Deze bug verholpen een probleem waarbij een ingetrokken aanmelding als toestemming van de klant ertoe leidde dat een Ajax 401-fout met raw HTML in het pop-upvenster met waarschuwingen werd weergegeven.
Na de correctie geeft het systeem nu correct een normaal waarschuwingsbericht weer in plaats van de ruwe HTML.
De oplossing werd geleverd in Magento 2.4.9-alpha3

_AC-15336 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

### Kader

#### Combinatiecode van uitgeschakelde module.

Deze trekkingsverzoek ontsnapte aan gehandicapte modules vóór codecompilatie.

_AC-10933 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38241) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39723)_

#### Fout wanneer looppas bevelopstelling :upgrade met de trekker van douaneOB

De gegevensbestandtrekkers van de douane veroorzaken niet meer fouten tijdens opstelling :upgrade.
Eerder, zou het lopen bin/magento opstelling :upgrade met een trekker van het douanegegevensbestand (b.v., NA TUSSENVOEGSEL op de opslaglijst) in de fout kunnen resulteren:
&quot;Waarschuwing: Arrayverschuiving proberen te benaderen bij waarde van type null in vendor/magento/framework/Mview/View/Subscription.php op regel 357&quot;
AC-11487

_AC-11487 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38481)_

#### [ Uitgave ] maakt methodehandtekening verenigbaar met interface

De methodehandtekening voor getAttributes is nu verenigbaar met zijn interface, verhinderend om het even welke fouten wanneer het beschrijven van de methode. Eerder, veroorzaakte inconsistenties in de methodehandtekening fouten wanneer het proberen om de getAttributes methode te beschrijven.

_AC-11578 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38501) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/31955)_

#### Entiteitsformulier voor website/groep/winkel kan niet worden uitgebreid met meerdere waarden van formulierelementen voor extensiekenmerken

Met deze PR kunnen formulierelementen met meerdere waarden gegevens verzenden naar website/groep/winkel-formulier.

_AC-11657 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/24070) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/24094)_

#### [ Bevestig-e-mailregel voor ui-component van de kwestie ]

Het systeem valideert nu correct meerdere e-mailadressen die zijn ingevoerd in UI-componenten, zodat elke e-mail correct wordt bijgesneden en gevalideerd. Eerder gebruikte het systeem een onjuiste methode voor het bijsnijden van e-mailadressen, die tot validatiefouten kon leiden.

_AC-11719 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38528) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/33470)_

#### [ Uitgave ] verwijdert het gebruik van de werkingsgebiedoplosser

Deze PR verhelpt de URL-instellingen van Admin globaal in plaats van de huidige winkel

_AC-11736 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38566) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38554)_

#### [ Uitgave ] verwijdert overtollige methodes

Codekwaliteit: Verwijderde overtollige methodes in componenten AsynchronousOperations en Sales die slechts oudermethodes zonder functionaliteit riepen toe te voegen, verbeterend codehoudbaarheid.

_AC-11915 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/29748) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/29147)_

#### Magento_Theme title.phtml template is ongeldig voor PHP 8.2

Deze pull-aanvraag verhelpt een probleem wanneer CMS-pagina die is gemaakt met de null-kop zoals in PHP 8.x die null doorgeeft aan trim(), uitzondering genereert: Afgekeurde functionaliteit: trim(): null doorgeven aan parameter #1 ($string) van type string

_AC-12856 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39092) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39398)_

#### xsd-validatie mislukt voor etc/adminhtml/system.xml-bestanden die opmerkingen bevatten onder velditems.

In deze PR worden XML-schemadefinities in &#39;phpstorm&#39; gecorrigeerd voor het knooppunt Commentaar

_AC-12945 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39148) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39867)_

#### De blootstelling van de Versie van Magento via de route van de Opstelling met standaardConfiguratie Nginx

Het systeem werkt nu zoals verwacht en geeft de exacte versie van Magento waarop de site wordt uitgevoerd niet weer

_AC-13205 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39227) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39228)_

#### [ de objecten van de kwestie ] unpack objecten argumenten als genoemde parameters

Het systeem gebruikt nu de PHP 8.1 eigenschap van het decomprimeren serie met genoemde parameters, die de behoefte aan array_values vraag elimineert en potentieel algemene prestaties verbetert. Eerder, roept het systeem vereiste array_values voor het uitpakken van objecten argumenten.

_AC-13210 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39233) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37411)_

#### [ Uitgave ] citaat van refactor bevestigt methode

Deze PR bevat verbeteringen in de leesbaarheid van de doValidate-methode.

_AC-13214 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38230) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38219)_

#### Magento option —magento-init-params nooit gebruikt bij het uitvoeren van cli?

—magento-init-params optie wordt nu gebruikt wanneer het runnen van CLI bevelen.
Eerder, had het overgaan —magento-init-params aan CLI bevelen geen effect op parameters zoals MAGE_MODE.
AC-13231

_AC-13231 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39248) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue onjuiste typedeclaratie

Het systeem definieert nu correct de invoerparameter $value als een primitief type, niet als een array, in de functie getItemsByColumnValue, zodat de functie de verwachte verzameling retourneert. Eerder, als een serie met één enkele waarde als inputparameter werd gebruikt, zou de functie ongeldig terugkeren en IDEs zou het als fout merken.

_AC-13240 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/33070) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/33120)_

#### Wanneer het gebruiken van dossieropslag voor de slotleverancier, krijgen wij een steeds groeiende folder van dossiers zonder enige schoonmaakbeurt

Dit trekkingsverzoek introduceert een nieuwe baan die één keer per dag loopt en zoekt naar slotdossiers die niet in de laatste 24 uren zijn gewijzigd en kan zo veilig worden verwijderd. Hierdoor blijft de inhoud van de map met vergrendelingsbestanden onder controle.
Deze taak zal slechts iets uitvoeren wanneer de slotleverancier wordt gevormd om dossiers te gebruiken, niet wanneer één van anderen wordt gebruikt (gegevensbestand - het gebrek, zoökeeper of geheime voorgeheugen)

_AC-13367 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39369) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39372)_

#### [ Uitgave ] Schoonmaakbeurt: gebruik geen waarde van de ongeldige terugkeer van methodevraag.

Deze PR doet kleine schoonmaakbeurten. Soms noemden we methoden die niets retourden (void) en gebruikten we die resultaatwaarde. Dat is echt niet nodig.

_AC-13664 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39524) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39516)_

#### Cachetoetsen die zijn gekoppeld aan FPC op Magento 2.4.7 multi-store-implementaties

Probleem verholpen waarbij de FPC-cachemoetsen (Full Page Cache) in meerdere opslaginstellingen geen MAGE_RUN_CODE en MAGE_RUN_TYPE bevatten, wat leidt tot inconsistente werking van de cachemoets in vergelijking met eerdere versies. De sleutels van het geheime voorgeheugen omvatten nu correct opslagcontext, die correcte geheim voorgeheugenisolatie over opslag verzekert.

_AC-13719 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39456) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/ae6f305b)_

#### [ ] PHPDOC [ Correctie slechte phpdoc voor Magento\Framework\Message\ManagerInterface]

Deze PR corrigeert de ongeldige phpdoc voor \Magento\Framework\Message\ManagerInterface en verwijdert alle dubbele phpdoc in \Magento\Framework\Message\Manager (gebruik inheritdoc syntaxis).

_AC-14312 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39593) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39153)_

#### Onvolledige indexering werkt niet meer voor klanten met een groot aantal updates

De gedeeltelijke indexering werkt nu voor klanten met een groot aantal updates.
Eerder, leidden het bereiken van de maximumwaarde voor de version_id kolom in de veranderingstabel indexupdates om te stoppen.
AC-14424

_AC-14424 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Magento 2.4.8 gebruikt ontwikkelpakketten die semantische versioning niet volgen

Voor compatibiliteit met PHP 8.4 is voor Magento 2.4.8 dev-versies van afhankelijk/afhankelijk en phpmd/phpmd (3.x-dev) vereist.
Deze dev-versies veroorzaken een conflict met hulpmiddelen van derden die SemVer-volgzame pakketten verwachten, die sommige verbeteringen verhinderen.
Een tijdelijke oplossing is het aliassen van de dev-versies in composer.json (bijvoorbeeld &quot;3.x-dev als 3.99.0&quot;), waardoor compatibiliteit mogelijk is en semantische versies voldoen.
Dit zorgt voor ondersteuning voor PHP 8.4 en vermijdt conflicten totdat stabiele releases beschikbaar komen.

_AC-14519 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39796)_

#### MView-mechanisme negeert fouten bij het uitvoeren van de trigger op ongepaste wijze

MView-mechanisme rapporteert nu correct fouten bij het uitvoeren van de trigger.
Eerder werden fouten tijdens de uitvoering van de trigger stilzwijgend genegeerd, waardoor indexupdates zouden kunnen ontbreken zonder dat hiervan melding wordt gemaakt.
AC-14567

_AC-14567 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/ae6f305b)_

#### [ Uitgave ] vermijd veel onnodige uitzonderingen tijdens de samenvoeging van lay-outXML laden

Deze PR introduceert een nieuwe functie (voor de compat van B/C beschrijven wij niet beschermde _loadXmlString) om te laden en geen uitzondering te werpen

_AC-14580 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39877) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37570)_

#### [ Uitgave ] Bevordering van constructoreigenschappen gebruiken in moduleVault grafiek Ql

Deze PR vervangt constructoreigenschappen door eigenschappenbevordering in de module VaultGraphQl

_AC-14616 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39900) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/36996)_

#### [ Verwijderde de codeovertolligheid van de 0&rbrace; Uitgave voor module frontend lay-outs.]

Deze PR verwijdert de redundantie van code voor themalay-outs voor Magento_MSRP-, Magento_LoginAsCustomerAssistance-, Magento_Newsletter- en Magento_Sitemap-modules voor frontend-layouts.

_AC-14625 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/30673) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/30644)_

#### [ Uitgave ] omvat Constructor om een deel van `CommandListInterface` API te zijn, breid gealigneerde documentatie uit

Deze PR update merkt Magento\Framework\Console\CommandList als API en introduceert de aannemer aan CommandListInterface voor betere rekbaarheid. Het verbetert ook gealigneerde documentatie om duidelijkheid en onderhoudbaarheid voor ontwikkelaars te verbeteren die consolebevelen uitbreiden.

_AC-14680 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/31102) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37901)_

#### [ Uitgave ] verwijdert code met betrekking tot Microsoft IIS

In deze PR wordt de code voor Microsoft IIS aangepast volgens de documentatie bij de systeemvereisten van Magento, waarin staat dat het Microsoft Windows-besturingssysteem niet wordt ondersteund

_AC-14702 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39910) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39894)_

#### Syntaxisfout Magnifier.js

De functie van de systeemvergroting zou moeten blijven werken zoals het vroeger werkte en magnifierOptions zou niet in globaal werkingsgebied beschikbaar moeten zijn

_AC-14722 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/36200) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39321)_

#### Modus Uitgebreide back-up in CLI-opdracht `setup:db:status`

De CLI-opdracht `setup:db:status` ondersteunt nu de uitgebreide modus.
Eerder was het moeilijk om de vereiste databasewijzigingen voor upgrades te begrijpen. Als u `bin/magento setup:db:status -v` nu uitvoert, krijgt u gedetailleerde informatie over schema- en gegevensverschillen.
AC-14807

_AC-14807 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

#### SMTP-mail wordt verzonden met TLS en 2.4.8

SMTP-verzending via e-mail met TLS werkt nu zoals verwacht.
Eerder, resulterend het verzenden van e-mails via SMTP met TLS in de fout: fout :1408F10B: SSL routines :ssl3_get_record: verkeerd versieaantal.
AC-14883

_AC-14883 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39947) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3717e6cb) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8b453942) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/d3ea191d)_

#### [ kwestie ] de kwestie van de Oplossing gelijktijdig in statische inhoud stelt op

Deze PR verhelpt een bug waarbij meerdere gelijktijdige processen hetzelfde themapakket afhandelen, afhankelijk van de manier waarop de thema&#39;s met hun ouders zijn gedefinieerd.

_AC-14944 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39990) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39954)_

#### [ Uitgave ] verwijdert erfenisverenigbaarheidscode voor PHP versies &lt; 8.1

Deze pull request verwijdert code die ontworpen was om uitgevoerd te worden op PHP &lt;8.1.
Ook, verwijder controles voor PHP_VERSION_ID contactbeschikbaarheid, aangezien het in alle PHP versies beschikbaar is

_AC-14971 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39891) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39882)_

#### FPC werkt niet bij aanmelding

FPC (Full Page Cache) werkt nu correct voor aangemelde klanten.
Eerder, na login, zou de homepage niet van geheim voorgeheugen laden en x-magento-cache-debug kopbal toonde MISS in plaats van HIT.
AC-14999

_AC-14999 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40007)_

#### Voeg generische types in bepaalde php klassen toe, voor betere statische analysesteun

Het systeem gebruikt nu generische typedefinitie om dit beduidend te verbeteren door het te hebben geïnterpreteerd als de nauwkeurige klasse een methodevraag terugkeert

_AC-15013 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40017) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40119)_

#### [ Uitgave ] verbetert fout behandelend SchemaBuilder

Deze PR verbetert de fout berichten behandeling van db schema. Het helpt ons om kwestie zonder zware zuivering te identificeren.

_AC-15020 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39816) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39799)_

#### Rest API: Call to a member function getVideoProvider() on null

Het aanroepen van de configureerbare API voor productonderliggende items heeft een fout van 500 interne server geretourneerd als een onderliggend product alleen een YouTube-video en geen andere afbeeldingen bevat. Dit probleem is nu opgelost.
De fout werd veroorzaakt door een ongeldige verwijzing in ExternalVideoEntryConverter.
De API retourneert nu op de juiste wijze onderliggende producten met mediagalerienummers, inclusief externe videogegevens, zonder fouten te genereren.
Hierdoor worden alle mediatypen voor onderliggende producten op de juiste wijze opgehaald via de REST API.

_AC-15046 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40021)_

#### [ W3C ] verwijdert tekst/javascript uit de verklaring van de de markeringsmarkering van het koekjesmanuscript

Deze PR heeft het overbodige type=&quot;text/javascript&quot;-kenmerk verwijderd uit de cookie script tag voor HTML5-compatibiliteit.

_AC-15061 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39982) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39983)_

#### [ Uitgave ] bevestig een paar typos in commentaren PHPDoc

In deze PR worden de paar typos in de phpdoc gecorrigeerd

_AC-15075 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40042) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38809)_

#### [ Uitgave ] verwijdert gebruik sprintf in uitdrukkingsvraag

Deze PR verwijdert het gebruik van sprintf in de woordfunctieaanroep in de Magento core.

_AC-15183 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40050) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40033)_

#### Kan niet alle ongeldige indexen opnieuw indexeren op indexeerapparaten met meerdere thread&#39;s met actieve toepassingsvergrendeling

Deze kwestie herstelde een multi-thread mislukking van de indexeerder wanneer use_application_lock werd toegelaten.
Eerder, werden de sloten van DB verloren tijdens parallelle verwerking, veroorzakend indexeerders om in &quot;werkende&quot;staat te blijven en SQL fouten (lijst niet gevonden) te werpen.
In Magento 2.4.9-alpha3 zorgt de correctie ervoor dat indexeerders correct opnieuw worden gecompileerd met toepassingsvergrendeling ingeschakeld.

_AC-15270 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40102) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### Onduidelijk/ongeldig retourneringstypen in Magento\Framework\Escaper

Het systeem zal types voor ontsnappingsmethodes goedkeuren wanneer het uitvoeren van statische analyse die phpstan op niveau 5 gebruikt

_AC-15272 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40012) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40114)_

#### [ Uitgave ] staat rij-specifieke configuratie toe om de standaard max-berichten waarde te overschrijden

Het systeem staat nu rij-specifieke configuratie toe om de standaard max-berichten waarde te overschrijden

_AC-15284 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40121) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40110)_

#### [ Uitgave ] Dupliceer geheim voorgeheugen voor de zelfde pagina met de zelfde vraag wanneer gebruikvernis

Deze PR verhelpt dubbele full-page geheim voorgeheugeningangen wanneer het gebruiken van Varnish door de orde van de vraagparameter te normaliseren, die verenigbare geheim voorgeheugensleutels voor identieke verzoeken verzekert.
Hiermee verbetert u de verhouding en prestaties van cachereacties voor URL&#39;s met dezelfde parameters in verschillende reeksen.

_AC-15325 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39706) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39704)_

#### Communautaire thema&#39;s bevatten middelen voor Commerce-editiemodule

Commerce-gebonden opmaakbronnen zijn verwijderd uit communautaire thema&#39;s door ze te verplaatsen naar hun respectievelijke moduledirectory&#39;s. Hierdoor wordt voorkomen dat ongebruikte CSS in de Community Edition wordt gebundeld, waardoor onnodige lading wordt voorkomen en regels met dode stijlen worden verwijderd en tegelijkertijd de juiste opmaak wordt gegarandeerd wanneer Commerce-modules worden ingeschakeld.

_AC-15347 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/21446) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/9bcd880a)_

#### [ Uitgave ] voegt de Code van de Opslag aan Urls toe zou Globaal moeten zijn

Deze PR verhelpt het probleem door ervoor te zorgen dat de instelling Winkelcode toevoegen aan URL&#39;s wordt opgehaald met het algemene bereik in de kerncode

_AC-15365 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40069) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40065)_

#### [ Logboek niet-gedeclareerde plug-in van 0&rbrace; Issue &lbrace;alleen als deze niet is uitgeschakeld]

Deze PR corrigeert en registreert de insteekmodule die niet is gedeclareerd en niet wordt gebruikt (ingeschakeld en ontbreekt).

_AC-15386 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40086) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40081)_

#### [ Kleine schoonmaakbeurt van 0&rbrace; kwestie, verwijderde dubbele sleutels van serie]

Het systeem is nu op kleine schaal opgeschoond en er is geen fout gevonden met betrekking tot Array met 2 dubbele toetsen met de waarde &#39;Weight (en hoger)&#39;

_AC-15414 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39851) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39844)_

#### Magento 2.4.8-p2, magento/framework versie 103.0.8-p2: EmailMessage-klasse die een niet-bestaande methode aanroept

De klasse EmailMessage handelt nu correct de herwinning van het e-maillichaam.
Eerder, in Magento 2.4.8-p2 met magento/framework versie 103.0.8-p2, probeerde de klasse Magento\Framework\Mail\EmailMessage een niet-bestaande methode (getTextBody) op het Symfony-berichtobject aan te roepen. Dit veroorzaakte fouten wanneer de modules of de aanpassingen van de derde op deze methode voor e-mailverwerking vertrouwden.
De klasse EmailMessage roept nu niet langer ongedefinieerde methoden aan, waardoor deze fouten worden voorkomen. AC-15446

_AC-15446 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40170) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/059fd469) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/e9412b24)_

#### [ Magento 2.3.x ] de Patches van Gegevens/van het Schema getAliases () veroorzaakt fouten tijdens `setup:upgrade`

getAliases() veroorzaakt fouten tijdens setup :upgrade, deze PR die het zelfde verhelpt

_AC-15559 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/31396) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38239)_

#### Ongeldige mix van collaties voor bewerking

_AC-15614 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40138) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/44329e9d)_

#### [ ] PHPDOC [ Correctie slechte phpdoc Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs ()]

Deze PR werkt PHPDoc voor \Magento\Framework\DB\Adapter\AdapterInterface::quoteColumnAs() bij om correct aan te geven dat de $alias-parameter naast string null kan zijn. Hiermee worden PHPStan-problemen op niveau 5+ opgelost en wordt de compatibiliteit met gereedschappen voor codekwaliteit verbeterd.

_AC-15626 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39598) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39581)_

#### Ongeldige mix van collaties in module urlrewrite

_AC-15647 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40189) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/44329e9d)_

#### Voorwaarde is nooit vervuld in `\Magento\Framework\Escaper::escapeScriptIdentifiers`

Correcteerde een onbereikbare voorwaarde in \Magento\Framework\Escaper::escapeScriptIdentifiers door de controle voor vals met ongeldig te vervangen, het te richten met preg_replace terugkeerwaarden en het verbeteren van codenauwkeurigheid zonder functionaliteit te beïnvloeden.

_AC-15667 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40195) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/cc0ec250)_

#### Varnish 7.3 (nieuwste versie) - Koppelingen naar subrubrieken / opties van de categorie Standaard worden niet weergegeven op de startpagina van de winkel

Bevestigd dat het ontbreken van subcategorieverbindingen op de storefront homepage toen het gebruiken van Veerling 7.3 door ESI verzoek behandeling en serverconfiguratie eerder dan een het codegebrek van Magento werd veroorzaakt; het probleem wordt opgelost door geadviseerde de configuratieaanpassingen van Varnish, zonder vereiste kerncodeveranderingen.

_AC-15674 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3cf1a106) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/9a62604c)_

#### [ Uitgave ] voegt extra zuivert gegevens aan `cache_invalidate` logboek toe

Deze PR verbeterde het cache_invalidate logboek om verzoekcontext en stapelspoor voor volledige geheim voorgeheugenzuivering te omvatten, verbeterend het zuiveren en het zicht.
Hierdoor kunt u de bron van onverwachte volledige cachevalidaties identificeren zonder de bestaande functionaliteit te wijzigen.

_AC-15719 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40204) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40196)_

#### [ Uitgave ] Verbeterde autoloader van de componist uitsluitingslijst een beetje.

Deze PR verfijnen de uitsluitingen van Composer-autoloader om testklassen over te slaan, onnodige klassingangen te reduceren en PSR-4-waarschuwingen te voorkomen.

_AC-15743 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40109) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40107)_

#### [ Uitgave ] verhindert `db_schema.xml` verklaringen met `comment=""` geen downtime plaatsingen te breken

Het systeem voorkomt nu dat db_schema.xml-declaraties met comment=&quot;&quot; geen downtime-implementaties kunnen onderbreken

_AC-15980 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40254) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40242)_

#### Kan de cache van `\Magento\Framework\Filesystem\Glob::glob(...)` niet wissen

Deze PR-update introduceert een manier om de interne statische cache te wissen die wordt gebruikt door \Magento\Framework\Filesystem\Glob. Hierdoor worden nieuwe en nauwkeurige resultaten verkregen wanneer de bestandsstructuren veranderen. Het verbetert betrouwbaarheid en ontwikkelaarservaring, vooral in testscenario&#39;s en langlopende processen waar de globale resultaten moeten bijgewerkt blijven.

_AC-15989 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35741) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/35742)_

#### URL van link ReadME Leaders heeft een permanente omleiding

De koppeling README-leiders is bijgewerkt door de permanent omgeleide en verlopen URL te vervangen door de juiste werkkoppelingen, zodat de pagina&#39;s met contribuanten en onderhoudspersoneel correct worden geopend.

_AC-16046 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40292) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### [ Uitgave ] [ PHPDOC ] Repareren slechte phpdoc Magento\Eav\Model\ResourceModel\Entity\Attribute\Collection

Correcte PHPDoc-annotaties voor joinLeft() in de kenmerkverzameling om juiste arraydefinities toe te staan, waardoor de correctheid van de code en de compatibiliteit met gereedschappen zoals PHPStan worden verbeterd.

_AC-16187 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40354) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39155)_

#### Zorg ervoor dat één enkele bevelmislukking de fout (dossier of stderr) registreert zonder de uitvoering van verdere bevelen CLI te stoppen.

Het systeem verzekert nu dat één enkele bevelmislukking de fout (dossier of stderr) registreert zonder de uitvoering van verdere bevelen CLI te stoppen

_AC-16244 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40006) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40063)_

#### [ Uitgave ] voegt int. type aan $maxAge in de Kernel PageCache toe

Deze PR zorgt ervoor dat de parameter $maxAge in de PageCache-kernel strikt wordt getypt als een geheel getal om de typeveiligheid te verbeteren en fouten in de PHPStan/statische analyse in de cacheverwerking te voorkomen.

_AC-16313 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40438) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/36600)_

#### Toevoegen aan winkelwagentje: lege prijzen

Productprijzen werden als null geretourneerd in de gebeurtenis checkout_cart_product_add_after als waarnemer tijdens het add-to-cart-proces. Dit probleem is nu opgelost.
Nu worden de basisprijs en de bijbehorende prijswaarden correct opgehaald, zodat er nauwkeurige gegevens beschikbaar zijn voor waarnemers en aangepaste uitvoeringen.

_AC-5966 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35638) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

#### Foutopsporing van het type PHP8.1

De bijbehorende producten worden nu geïnitialiseerd naar een lege array in plaats van naar false wanneer de strikte verwerkingsmodus niet actief is of wanneer productinformatie beschikbaar is. Deze verandering zorgt ervoor dat de daaropvolgende logica die daarmee verband houdt, zich consistent gedraagt, waardoor de stabiliteit en voorspelbaarheid van het productbereidingsproces worden verbeterd.

_AC-6017 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/35808) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/35842)_

#### Type &#39;Magento\Customer\Api\Data\GroupInterface&#39; verwacht. Gevonden &quot;Magento\Customer\Model\Group&quot;.

Het opslaan van een klantengroep via GroupRepositoryInterface met GroupFactory veroorzaakte een typefout. Dit probleem is nu opgelost.
Eerder verwachtte de dataopslag GroupInterface, maar groepsmodelinstanties werden overgegaan, resulterend in een fatale fout.
Klantgroepen kunnen nu met succes worden opgeslagen via de opslagplaats door te zorgen voor een correcte implementatie van de interface.
Dit verhelpt de waarschuwingen van winde en runtime fouten wanneer programmatically het creëren van of het bijwerken van klantengroepen.

_AC-6909 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/36269)_

#### Veldvalidatie voor creditnota&#39;s

Veldvalidatie op de pagina voor creditnota bood zelfs geen verzending nadat de vereiste aangepaste velden waren ingevuld. Dit probleem is nu opgelost.
Validatie werkt nu correct en de verzendknop wordt ingeschakeld zodra alle verplichte velden zijn voltooid.

_AC-8308 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37182) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### [ Uitgave ] verwijdert verboden `@author` markering uit kader (deel 3)

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8343 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37270) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37020)_

#### [ Uitgave ] Bevordering van het de aannemersbezit van het Gebruik in module verzendt vriendengrafiek ql

Het systeem gebruikt nu de bevordering van constructoreigenschappen in de module &#39;send vriend&#39; GraphQL, wat de leesbaarheid van de code verbetert en de complexiteit vermindert. Eerder, gebruikte de module eigenschappen die talrijke lijnen bezet, die de code complexer en minder leesbaar maken.

_AC-8346 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37235) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37197)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8349 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37266) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37016)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8350 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37265) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37015)_

#### [ Uitgave ] verwijdert verboden `@author` markering uit `Magento_Downloadable`

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8355 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37251) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37001)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de kwaliteit en consistentie van de code worden verbeterd. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8358 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37264) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37014)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8359 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37262) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37012)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8360 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37261) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37011)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, zodat u over een schonere en meer gestandaardiseerde code beschikt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8361 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37260) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37010)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8362 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37259) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37009)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8363 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37258) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37008)_

#### [ Uitgave ] verwijdert verboden `@author` markering van `Magento_Backup` en `Magento_Bundle`

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8367 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37244) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/36979)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8375 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37257) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37007)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8376 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37256) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37006)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8400 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37254) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37004)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8401 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37255) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37005)_

#### [ Uitgave ] verbetert Uitbreidbaarheid van de Generatie van Service URL

Het systeem staat nu voor aanpassing van de functie van de Generatie van de Dienst URL via plugins toe, die een meer houdbare benadering van wijzigingen bevorderen. Voorheen werd deze functie aangepast via voorkeuren, die mogelijk niet zo efficiënt of onderhoudsbaar waren.

_AC-8813 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37404) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37403)_

#### [ Repareer veranderlijke naam van 0&rbrace; Uitgave &lbrace;in catalogusonderzoek]

Het systeem noemt nu correct variabelen in de module van de onderzoeksmotor, die codehelderheid en onderhoudbaarheid verbeteren. Eerder werd een niet-relevante variabelenaam, $defaultCountry, gebruikt in de zoekmachine module, wat tot verwarring leidde.

_AC-9215 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37810) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/33533)_

#### allow_parallelle_generation moet worden ingesteld via de omgevingsvariabele

Na de correctie kan de omgevingsvariabele &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION&quot; worden gebruikt om de configuratie &quot;allow_parallelle_generation&quot; in te stellen.

_ACP2E-3673 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

#### [ Cloud ] Veranderend het type van lijstkolom van Int in Decimaal gebruikend db_schema.xml- dossier in Magento 2 resulteert in Fouten

Het wijzigen van het gegevenstype van de kolom werkt niet correct. Eerder werd een fout gegenereerd: het kenmerk &#39;identity&#39; is niet toegestaan.

_ACP2E-3709 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### Ondersteuning voor nieuwe valuta (XCG) in Adobe

Caraïbische Gulder (XCG) wordt toegevoegd aan de lijst met valuta&#39;s.

_ACP2E-3790 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### Probleem met upgrade 2.4.7-p5 vanwege nieuwe validatie

Probleem verholpen in de SchemaBuilder-klasse waarbij een niet-gedefinieerde arraysleutel &#39;kolom&#39; een crash veroorzaakte tijdens het maken of bijwerken van het schema. Dit gebeurde wanneer het verwerken van lijstgegevens die geen &quot;kolom&quot;sleutel omvatten.

_ACP2E-3871 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9ad7d277)_

#### [ KANS ] Uitgave van de Server die potentieel door Ongeldige S3 Sleutel van de Toegang wordt veroorzaakt

Onjuiste AWS S3-referenties zorgen er niet langer voor dat pagina&#39;s oneindig worden geladen in de winkel.

_ACP2E-3890 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [ KANSEN ] [ de Wolk ] Minify js die niet werkt

De volgende JS-bestanden worden nu volledig en correct geminiateerd wanneer JS-minificatie is ingeschakeld: mage/backend/tabs.min.j, jquery/jquery.validate.min.js en Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Als gevolg hiervan werkt de CSS-klassevalidering van Page Builder naar behoren.

_ACP2E-3925 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### PHP8.4 Deprection Error: E_USER_ERROR after Upgrade to Adobe Commerce 2.4.8

*DE GEEN NOTITIES VAN DE RELEASE WORDEN VEREIST*
De oplossing heeft geen invloed op klantgerichte scenario&#39;s.

_ACP2E-3963 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### Cron job not clearing the database table - cause outage due to Galera crash

Het opschonen van wijzigingstabellen wordt nu in batches uitgevoerd om zware verwijderingsbewerkingen te voorkomen.

_ACP2E-3995 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### Niet-geminieerde JS laadt soms &#39;js minifications inschakelen&#39;

Vóór de correctie, zelfs als u minificatie had toegelaten werden sommige JS dossiers gevraagd zonder het &quot;min&quot;prefix resulterend in 404 statuscode. Na de moeilijke situatie, wanneer de minificatie wordt toegelaten zijn er geen niet-geminificeerde JS gevraagde middelen.

_ACP2E-4058 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Datumkenmerk in aangepaste kenmerkgroep kan geen datumkiezer weergeven in Admin

Pop-up kalender voor datumkenmerken werd buiten het scherm weergegeven bij toewijzing aan aangepaste kenmerkgroepen. Dit probleem is nu opgelost.

_ACP2E-4060 - [&#x200B; GitHub kwestie &#x200B;](https://integration-5ojmyuq-3ssteurpe3xzy.us-5.magentosite.cloud/) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### De ACL Controle van de Toestemming van de productie veroorzaakte de Verslechtering van Prestaties - populateAcl Methode is het knelpunt

Geoptimaliseerde ACL regelverwerking

_ACP2E-4114 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/98f028ab)_

#### Afhandeling niet in de meest recente versie met AC-15867 + ACP2E-4296 en SCD compact

Voordat de correctie werd uitgevoerd, konden er problemen zijn opgetreden als er aangepaste javascripts door de hoofdsectie werden geladen. Na de introductie van de nieuwe instelling kunnen dergelijke scripts automatisch worden uitgesteld, zodat ze beter compatibel zijn met het Magento 2-framework.

_ACP2E-4319 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/1c547060)_

#### Waarschuwing bij afschrijving: gebruik moment.updateLocale(localeName, config) om een bestaande landinstelling te wijzigen. moment.defineLocale(localeName, config)

Voorafgaand aan de correctie werd een verouderde waarschuwing in browser console geworpen. Na de correctie wordt een dergelijke waarschuwing nu niet meer weergegeven.

_ACP2E-4338 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

#### Incompatibiliteit met MariaDB 10.11

Eerder kon de nieuwste Magento 2-versie niet worden geïnstalleerd wanneer MariaDB 10.11 werd gebruikt, waardoor het installatieproces niet kon worden voltooid. Dit probleem is opgelost door databasecompatibiliteitsverwerking bij te werken ter ondersteuning van MariaDB 10.11.x tijdens de installatie.

_ACP2E-4367 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

### Framework, zoeken

#### Openssearch 2.19.1 illegal_argument_exception on one-price categorieën

Openssearch genereert niet langer een illegal_argument_exception op de categorieën die alle producten met dezelfde prijs bevatten. Eerder, heeft het deze uitzondering &quot;[ van ] parameter kan niet negatief zijn&quot;.

_ACP2E-3896 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### Het plaatsen van een bestelling in GraphQL lukt met een ongeldige verzendmethode

Probleem verholpen waarbij bestellingen via GraphQL konden worden geplaatst met een uitgeschakelde of ongeldige verzendmethode.
Het systeem valideert nu de geselecteerde verzendmethode en retourneert een fout als deze niet beschikbaar is, waardoor de bestelling niet meer kan worden gemaakt.

_AC-10472 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38268) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### Er wordt een uitzondering gegenereerd bij het uitvoeren van een GraphQl-query

Probleem verholpen waarbij een GraphQL-query een uitzondering genereerde vanwege een ongeldige sorteerparameter. Na de correctie wordt de query met succes uitgevoerd zonder fouten of uitzonderingslogbestanden te genereren.

_AC-14835 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### Interne serverfout bij het toevoegen van Cadeauproduct aan winkelwagentje via AddProductsToCart-mutatie inclusief custom_attributesV2

Oplossing van een Interne Fout die van de Server bij het toevoegen van cadeau kaart (en gelijkaardige douane-optie) producten aan de kar via GraphQL met custom_attributesV2 teweegbracht; de moeilijke situatie behandelt behoorlijk complexe attributenwaarden, toestaand producten om zonder fouten worden toegevoegd.

_AC-15856 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/7fa400a7)_

#### Null-velden in `Country` -query

Probleem verholpen waarbij bestellingen die virtuele, terugbetaalde en verzonden items bevatten, nog werden verwerkt door ervoor te zorgen dat virtuele items worden opgenomen in de berekeningen van de verzonden hoeveelheid, zodat de status van de bestelling correct kan worden voltooid.

_AC-7731 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### GraphQL-query &quot;customerOrders&quot; met kenmerk &quot;number&quot; veroorzaakt interne serverfout

De GraphQL-query voor CustomerOrders gaf een interne serverfout weer bij het aanvragen van het nummerveld. Dit probleem is nu opgelost.
Nu, zet resolver correct identiteitskaart van de ordingstoename terug, toestaand de vraag om met succes uit te voeren en het orderaantal terug te winnen.

_AC-8949 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

#### GraphQL Response for Order placement bevat geen uitzonderingsbericht

Vorige wijziging die fouten in een andere indeling retourneert, is hersteld. Mogelijke fouten worden nu op een consistente manier geretourneerd, niet door het GraphQL-schema te verbreken. Dit moet worden toegevoegd als gekende BIC, goedgekeurd door PM hier: https://jira.corp.adobe.com/browse/ACP2E-3399?focusedId=45248897&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel #comment-45248897

_ACP2E-3399 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### GraphQL Response for Order placement is gedeeltelijk gelokaliseerd

Fouten die door placeOrder GraphQl-mutatie zijn geretourneerd, zijn niet volledig gelokaliseerd. In een meertalige context worden fouten nu goed vertaald.

_ACP2E-3506 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9608ca21)_

#### Gelijktijdige aanroepen om GraphQL API opnieuw te ordenen - Dezelfde producten toegevoegd aan verschillende rijen

Hiermee wordt het probleem verholpen waarbij gelijktijdige aanroepen naar de GraphQL API opnieuw ordenen ertoe leiden dat dezelfde producten als verschillende rijen worden toegevoegd, wat leidt tot inconsistenties in de gegevens.

_ACP2E-3774 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL-mutatie (e-mailadres wijzigen) activeert de e-mailmelding niet

Eerder werd e-mail niet verzonden naar klanten nadat hun e-mailadressen op hun accounts waren bijgewerkt. Nadat de oplossing is toegepast, ontvangen klanten nu e-mailmeldingen nadat ze hun e-mailadressen hebben bijgewerkt.

_ACP2E-3785 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### Dynamisch kenmerk niet bijgewerkt in Cadeauregister via updateGiftRegistry Mutation

Eerder, vóór deze moeilijke situatie door de updateGiftRegistry mutatie, werd het douanekenmerk van het giftenregister niet gewijzigd of bijgewerkt door de mutaties van GraphQL. Nadat deze moeilijke situatie is toegepast, kan het dynamische attribuut van het giftenregister met succes door de updateGiftRegistry mutatie worden bijgewerkt.

_ACP2E-3805 - [&#x200B; GitHub kwestie &#x200B;](https://mcstaging.briscoes.co.nz/)_

#### GraphQL voor bestelling van klant: ophalen van productcategorieën voor het bijbehorende product is &quot;niet afzonderlijk zichtbaar

Als de bestelling een verborgen product bevatte, zouden de categorieën van de bestelling vóór de correctie een lege array weergeven in het antwoord GraphQl van de Bestelling van de Klant.
Nu, na de moeilijke situatie, zijn de productcategorieën inbegrepen in het antwoord van een GrafiekQl- verzoek van de Bestelling van de Klant zelfs als het product verborgen is.

_ACP2E-3945 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### De items in de lijst met identieke items worden niet gedeeld tussen de weergaven in één website in GraphQL-aanvraag

Vóór de correctie werden de items in de wenslijst gefilterd met de id van de winkel. Na de correctie worden de items in de wenslijst gefilterd op website.

_ACP2E-3987 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2a252ae6)_

#### [ de terugkeer van de Wolk ] getRemoteAddress 127.0.0.1 op Productie

Vóór deze correctie werd het externe adres niet correct bepaald wanneer de toepassingsserver wordt gebruikt. Na de moeilijke situatie wordt het verre adres behoorlijk bepaald gecombineerd met juiste kopbalopstelling in nginx en kopbalconfiguratie.

_ACP2E-3991 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

#### [ KANTOREN ] bevestigen GQL de uitzondering behandelende gedragsreversie van de orderplaatsing

Achterwaartse incompatibele wijziging voor placeOrder-mutatie is opgelost.

_ACP2E-4031 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### Probleemtoewijzing vertaald bericht naar foutcode bij plaatsen van bestelling via GraphQL

Probleem verholpen waarbij een vertaald uitzonderingsbericht werd gebruikt om de foutcode voor GraphQL-verzoeken toe te wijzen, waardoor een onbekende foutcode voor bekende fouten werd gegenereerd.

_ACP2E-4033 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/fab20b00)_

#### [ CLOUD ] de filter van de Orde van de Klant werkte niet voor Datums

Na de correctie wordt het juiste resultaat geretourneerd wanneer u via GraphQL orders ophaalt met een datumbereikfilter.

_ACP2E-4090 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### In ACS2E-4031 aan de orde gestelde kwesties

Vóór de correctie bood de positie van het foutknooppunt geen naadloze compatibiliteit met 2.4.7- en 2.4.9-versies. Na de correctie is het foutknooppunt nu op de juiste wijze geplaatst om beide versies samen te voegen.

_ACP2E-4115 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

#### Bovenliggend element van bundel dat uit voorraad weergeeft, zelfs als het onderliggende item een instantie in een grafische aanroep heeft

Na de correctie retourneert het aanvragen van een productlijst met GraphQL de juiste voorraadstatus voor bundelproducten.

_ACP2E-4168 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

#### GraphQL-uitzondering in SWAT

Na de correctie worden de antwoorden voor GraphQL-aanvragen uitgelijnd met de GraphQL over HTTP-specificaties. Een 4XX antwoordcode is teruggekeerd wanneer het onmogelijk is om het verzoek te ontleden, wordt het verzoek niet geautoriseerd, of er is een ander algemeen probleem met het verzoek. Als het verzoek wordt geparseerd en kan worden verwerkt, zal een 200 antwoordcode worden teruggekeerd.

_ACP2E-4194 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Product dat niet uit de vergelijkingslijst wordt verwijderd nadat de lijst aan de klant is toegewezen

Nadat de vergelijkingslijst van een gastgebruiker aan een klantenrekening wordt toegewezen, kunnen de producten die als gast worden toegevoegd nu door de klant worden verwijderd.
Eerder, ontbrak de verwijderingsverrichtingen omdat de gast-toegevoegde punten niet behoorlijk met de rekening van de klant na taak werden verbonden.

_ACP2E-4244 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

#### updateCartItems GraphQL onjuiste foutreactie

Eerder, toen een graphQL verzoek voor een punt met ontoereikende hoeveelheid werd ingediend, werd een correct foutenbericht met een foutencode teruggegeven, samen met de gevraagde hoeveelheid en prijsberekening, zelfs als het punt niet beschikbaar was. Nadat deze correctie is toegepast, wordt nu een correct foutbericht met een foutcode geretourneerd en wordt de hoeveelheid van het item ingesteld op de oude waarde als deze niet beschikbaar is in de reactie.

_ACP2E-4283 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/cbca0396)_

#### Fout bij toewijzing van gastvolgorde tussen verschillende websites in de insteekmodule MergeGuestOrder

Voorafgaand aan de oplossing overwogen een klant-toewijzing van de gastorder geen opties voor het delen van accounts. Nu, na de correctie, wordt een orde toegewezen aan een klant als klant en ordeopslagovereenkomst (gegeven dat de optie van het delen van de klantenrekening aan &quot;per website&quot;wordt geplaatst.

_ACP2E-4312 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/c135fc3a)_

### GraphQL, Inventaris/MSI

#### Probleem met only_x_left_in_stock in Magento 2 GraphQL - Onjuiste berekening bij gebruik van drempelwaarden

Probleem verholpen waarbij het veld only_x_left_in_stock GraphQL null retourneerde als gevolg van onjuiste dubbele aftrek van MinQty; de berekening werd gecorrigeerd zodat nu de juiste voorraadwaarde wordt geretourneerd op basis van drempels.

_AC-15832 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/35458c7f)_

#### GraphQL mergeCart-mutatieverschillen

Na de correctie wordt in het verzoek van GraphQL de hoeveelheid product correct gecontroleerd, rekening houdend met de voorraadconfiguratie.

_ACP2E-4184 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, product

#### Ontbrekende media_type in afbeelding van product in MediaGalleryInterface

Het GraphQL-verzoek voor MediaGallery bevat nu het veld &quot;types&quot; voor productafbeeldingstypen. Eerder bestond dit veld &quot;types&quot; niet in de aanvraag van MediaGallery GraphQL.

_ACP2E-3880 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL, beveiliging

#### Wachtwoord van klant opnieuw instellen via GraphQL houdt geen rekening met de beperkingen

Oplossing voor een probleem waarbij verzoeken om het opnieuw instellen van het wachtwoord van de klant die via GraphQL-mutaties zijn gedaan, niet voldeden aan de beperkingen voor het opnieuw instellen van het wachtwoord die zijn geconfigureerd onder Store > Configuration > Customers > Customer Configuration > Password Options. Deze instellingen worden nu correct toegepast.

_ACP2E-3992 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importeren/exporteren

#### [ Uitgave ] Reparatie parametertype

Oplossing voor een probleem met parametertypen in de module Importeren/exporteren, waarbij een waarde die eerder als een tekenreeks is gedefinieerd, nu correct is ingesteld als een array. Hiermee wordt uitgelijnd op de verwachte invoer van de exportcontroller en worden waarschuwingen voor statische analyse voorkomen.

_AC-11665 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38529) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### [ Uitgave ] Copyright: verandering &quot;het kopiëren&quot;aan &quot;het kopiëren&quot;

PR corrigeert de kleine kopie om de spelling van &quot;kopiëren&quot; te corrigeren

_AC-13300 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39311) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39307)_

#### REST-eindpunt Product Import Json valideert de verplichte velden niet

Het veld Naam is nu vereist wanneer u nieuwe producten maakt via het importproces (admin of API). Voorafgaand aan de moeilijke situatie, kon u nieuwe producten zonder naam tot stand hebben gebracht, zou dit de admin interface gebroken hebben en ongeldige producten gecreeerd.

_ACP2E-3660 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### Ontbrekende optie Websitefilter in exportproces

Het is nu mogelijk om producten via websites te filteren wanneer u producten maakt die u exporteert.

_ACP2E-3720 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### Duplicaat van AC-13913 - Statische kenmerkreiniging asynchroon.

Na de correctie is er geen &#39;Undefined array key &quot;apply_to&quot;&#39;-fout wanneer er meerdere instanties van de map \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType worden gemaakt.

_ACP2E-3752 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### CSV-product importeren: kan de instelling van een staalafbeelding niet ongedaan maken

Vóór de correctie kon u de staalafbeelding van een product niet bijwerken via het importeren van producten. Nu, na de moeilijke situatie, als u de kolom van het productmonster van het beeldbeeld met de gevormde lege teller markeert, zal het beeld aan verborgen worden geplaatst.

_ACP2E-3972 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Met Product importeren worden lege URL&#39;s gegenereerd voor het winkelbereik

De URL-sleutel van het product in de winkelweergave neemt nu de waarde over die is ingesteld in het standaardbereik als url_key een lege waarde heeft in de gegevensbron met importgegevens. Als u eerder url_key instelt op een lege waarde in de gegevensbron voor importweergave voor een record, wordt url_key overschreven door een lege waarde in dat bereik.

_ACP2E-4038 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### Bij het importeren van het product wordt een fout aangetroffen als een kenmerk met meerdere selecties naar wens is geconfigureerd

Probleem opgelost waarbij het importeren van producten mislukte als een vereist kenmerk van het type multi-select was opgenomen. De gegevensvalidatie wordt nu correct uitgevoerd, zodat het proces voor het importeren van producten met succes kan worden voltooid.

_ACP2E-4057 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [ CLOUD ] de Producten zonder die Achterorden op beheren voorraad nog klanten toestaan om over onze voorraadniveaus in orde te brengen wanneer ingevoerd

Na de correctie is het niet meer mogelijk om een onaanvaardbare waarde te importeren voor het kenmerk &quot;allow_backorders&quot; van het product.

_ACP2E-4116 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Productimport mislukt vanwege een beschrijvingslengte van meer dan 65.536 tekens Validatie

Na de correctie is het mogelijk om productkenmerken te importeren met tekst waarvan de waarden meer dan 65.536 tekens bevatten.

_ACP2E-4119 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Filters exporteren voor product Ja-geen kenmerken functioneren niet naar verwachting

Na de correctie bevatten geëxporteerde producten die zijn gefilterd door een kenmerk Ja/Nee, de verwachte producten die voldoen aan de toegepaste filters.

_ACP2E-4160 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/ee918f0d)_

#### Probleem met prijs van bundeloptie bijwerken per website via importeren

Het is nu mogelijk om prijzen voor bundelopties per website te exporteren en te importeren

_ACP2E-4243 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/98f028ab)_

#### Kan een klant niet importeren met een e-mailadres in hoofdletters

Correctie van een niet-gedefinieerde fout in de arraysleutel bij het importeren van klanten met e-mailberichten in hoofdletters wanneer Account Sharing is ingesteld op Global. E-mailnormalisatie is nu consistent tijdens het gehele importproces, zodat klanten ongeacht het geval van een e-mail kunnen worden geïmporteerd. Het gedrag voor het delen van accounts op websiteniveau blijft ongewijzigd.

_ACP2E-4373 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

### Importeren/exporteren, klant/klant

#### Beheerder kan een klant importeren waarvan de geboortedatum hoger is dan de huidige datum

Correctie van een probleem waarbij beheerders klanten met een geboortedatum in de toekomst konden importeren. Het systeem valideert nu de DOB tijdens het importeren, toont een fout voor ongeldige records en voorkomt dat klanten met toekomstige geboortedatums worden geïmporteerd, zodat accurate klantgegevens worden gegarandeerd.

_AC-13641 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

### Inventaris/MSI

#### Winkelafhandeling voldoet niet aan de maximale zoekstraal wanneer het adres bij afhandeling wordt gewijzigd

Nu vooraf geselecteerde winkel in Winkel kiezen wordt bijgewerkt als het verzendadres verandert. Eerder, toen een opslag vooraf werd geselecteerd, veranderde het niet zelfs als het nieuwe verzendadres niet binnen de straal van de geselecteerde opslag is

_ACP2E-3728 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/07620383)_

#### Geen winkel beschikbaar na omleiding naar homepage en uitchecken

Eerder geselecteerde winkel wordt nu vooraf geselecteerd bij Verzending in Winkel selecteren als de klant naar de betalingspagina navigeert, vervolgens terugkeert naar de homepage en ten slotte terugkeert naar de afhandelingspagina. Eerder werd de geselecteerde winkel in de &quot;Winkel kiezen&quot; gewist nadat u herhaaldelijk naar de uitcheckpagina was teruggekeerd.

_ACP2E-3793 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a20a6ff2) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/62c0d79b)_

#### De bewerking voor het verwijderen van bestanden is niet voltooid

Na de correctie leidt het verwijderen van een bronitem niet tot een volledige herindex en worden alleen de betrokken producten bijgewerkt, waardoor de prestaties toenemen.

_ACP2E-3917 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [ MSI ] Geen aanwijzing in admin als de klant asynchroon over Orde werd meegedeeld is Klaar voor Bestelwagen

Toegevoegd aan het bericht van de ordegeschiedenis over de klant werd asynchroon meegedeeld over Orde is Klaar voor Bestelwagen

_ACP2E-3968 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/29653b1d)_

#### Dubbele vragen over voorraadstatus bij het laden van aanhalingstekens

Oplossing voor dubbele uitvoering van query voor catalogvoorraad_stock_status bij het laden van een aanhalingsteken in de winkel, wat tot redundante DB-aanroepen heeft geleid.

_ACP2E-4102 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/fc15a9ae)_

#### Post-Patch ACP2E-4118: Bij wijziging van de voorraaddrempel in Admin worden negatieve verkoopbare hoeveelheden en een afwijkende voorraadstatus veroorzaakt

De voorraadstatus van de voorraad wordt nu automatisch aangepast wanneer de globale inventarisconfiguraties Hoeveelheid, Achterorders en Drempel voor voorraadverlies via import worden bijgewerkt.

_ACP2E-4142 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a1c57b2e) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/5632fb5e)_

#### [ CLOUD ] Admin- Rapport toont geen details wanneer de inventaris wordt bijgewerkt

De bronveranderingen van de productvoorraad worden nu geregistreerd door registrerenmodule. Voordat de correctie werd uitgevoerd, werden tijdens het opslaan van een product en het uitvoeren van inventarisgerelateerde wijzigingen geen gegevens geregistreerd.

_ACP2E-4167 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/cbca0396) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/76b88f7c)_

#### Bundel product dat niet aan de kar kan worden toegevoegd terwijl het als voorraad wordt gemerkt

De status van de bundelproductvoorraad weerspiegelt nu correct de reserveringen van onderliggende producten en de drempelwaarden voor producten buiten de voorraad.
Eerder werden bundelproducten gemarkeerd als &quot;in voorraad&quot;, zelfs als een of meer kinderproducten onvoldoende verkoopbare hoeveelheid hadden. Dit heeft geleid tot &#39;Onvoldoende items voor verkoop&#39;-fouten bij het toevoegen van de bundel aan de winkelwagen.

_ACP2E-4220 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/cbca0396) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/76b88f7c)_

#### Gegroepeerd product wordt na import uit CSV ten onrechte weergegeven als Uit voorraad op PDP wanneer kind wordt toegewezen aan aangepaste bron/voorraad (vast na handmatig opnieuw indexeren)

Na de correctie wordt bij het maken van een samengesteld product met import automatisch de voorraad opnieuw gedexeerd, zodat het product beschikbaar is zonder dat het handmatig opnieuw moet worden gecomprimeerd.

_ACP2E-4233 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/98f028ab) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/5704166a)_

#### [ MSI ] die tests MFTF met betrekking tot recentste belangrijkste veranderingen ontbreekt.

Voordat de oplossing werd gevonden voor klanten die in-Store ophaalservice zonder verzendadres kiezen, werd het factuuradres automatisch ingevuld met het adres van de winkel. Dit adres kon niet worden gewijzigd, wat tot onjuiste factuurgegevens leidde. Nadat het adres van het fixfacturerings nu editable in dit scenario is, toestaand gasten om hun eigen details in te gaan. Geregistreerde gebruikers zien hun opgeslagen factureringsadres in plaats van dat van de winkel.

_ACP2E-4260 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/ab891304) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/13e432a6)_

#### Onjuiste voorraadreservering gemaakt voor virtuele cadeaukaarten

Voordat deze oplossing werd geïmplementeerd, weerspiegelde de hoeveelheid van een virtuele cadeaukaart die meerdere items bevatte, niet nauwkeurig de voorraadreservering. Na toepassing van de correctie werden de hoeveelheid van de voorraadboeking en de voorraden echter gesynchroniseerd.

_ACP2E-4267 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/5704166a)_

#### Opdracht voor compensatie voor inventarisreservering mislukt vanwege onjuiste en niet-bestaande productreferenties

De CLI zou een uitzondering genereren als de verwerkte combinatie een ontbrekende bestelling-id had. Dit probleem is nu opgelost.

_ACP2E-4301 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/76b88f7c)_

#### Het product is uit voorraad nadat het SKU-geval is gewijzigd

Als de SKU-zaak wordt gewijzigd, is het product niet langer meer in de winkel.

_ACP2E-4375 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/0836c2ed)_

#### Bestellen op basis van prijs/prijsfactoren met ongeldige gegevens

Voorafgaand aan de vaststelling werden de prijzen van de bundels niet correct geïndexeerd wanneer de voorraden van kinderproducten onder aangepaste bronnen lagen. Nu, na de correctie, worden de bundelprijzen behoorlijk geïndexeerd ongeacht de toewijzing van kindproductvoorraad.

_ACP2E-4380 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/1c547060) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/1f83ed24)_

### Volgorde

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue []) breekt customAttributes

Aangepaste kenmerken op adressen worden nu correct verwerkt tijdens uitchecken en API-bewerkingen.
Als u voorheen $address->setCustomAttributes(&#39;custom_attributes&#39;, $attributes) gebruikte, kan dit de verwerking van aangepaste kenmerken onderbreken, waardoor kenmerkwaarden onjuist zijn gestructureerd.
AC-10568

_AC-10568 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/31644)_

#### Wanneer de klant voor citaatorde wordt geplaatst is nog een gastorde

_AC-11689 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38540)_

#### De bestelling is niet voltooid wanneer virtuele, terugbetaalde en verzonden items worden gemengd

Probleem verholpen waarbij bestellingen die virtuele, terugbetaalde en verzonden items bevatten, nog werden verwerkt door ervoor te zorgen dat virtuele items worden opgenomen in de berekeningen van de verzonden hoeveelheid, zodat de status van de bestelling correct kan worden voltooid.

_AC-11691 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38547)_

#### v2.4.7-p1 Magento reorder -1 volgordenummers

Het systeem werkt zoals verwacht en na herschikking vanaf de achtergrond zal het ordernummer uniek zijn 8 cijfers

_AC-12854 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39089) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39399)_

#### Uploaden van aangepaste optie voor product verliezen bij uitchecken met betalingsmethode voor Adobe-creditcard

Uploads naar aangepaste opties voor producten blijven nu behouden wanneer je uitcheckt met de betalingsmethode voor Adobe-creditcards.
Eerder ging het uploaden van bestanden verloren bij het gebruik van deze betalingsmethode, maar werkte het samen met anderen.
AC-14306

_AC-14306 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39647)_

#### Admin orders - kan niet zoeken naar Will

Probleem verholpen waarbij zoeken naar bestellingen op klantnaam (bijvoorbeeld &quot;Will&quot;) in het raster Admin-bestellingen geen resultaten opleverde. Na de moeilijke situatie, worden de relevante orden correct getoond wanneer gefiltreerd door klantennaam.

_AC-14360 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/36596) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### Magento 2.4.8 GraphQL - Order items order_date onjuiste opmaak

The order_date field in GraphQL response returned in yyyy-mm-dd format. Dit probleem is nu opgelost.
De order_date wordt nu correct weergegeven in dd-mm-jjjj formaat.

_AC-14431 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39805) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Kan null niet retourneren voor onverwacht probleem van veld \&quot;AppliedCoupon.code\&quot; dat niet kan worden null geretourneerd

Adobe Commerce retourneert nu correct toegepaste couponcodes via GraphQL bij het opvragen van orders van klanten. Eerder, in Adobe Commerce 2.4.8, kon het halen van een orde met het applied_coupons.code gebied (bijvoorbeeld via de customer.orders vraag) met een interne serverfout ontbreken en het bericht kan ongeldig voor niet-nullable gebied &quot;AppliedCoupon.code&quot;terugkeren, en applied_coupons werd teruggegeven als [ ongeldig ] in plaats van een lijst die de waardeboncode bevat. AC-14484

_AC-14484 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39841) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/97b2ea42)_

#### E-mailbericht voor verzending niet verzonden na verzending vanuit de weergave Admin Order, hoewel ingeschakeld in winkelconfiguratie

Het systeem verzendt nu een e-mail met de bevestiging van de verzending aangezien het in de archiefconfiguratie wordt toegelaten waar de orde werd geplaatst.

_AC-14563 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39861) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39897)_

#### Filteren op datum werkt niet vanwege dubbelzinnige veldnamen

In Magento 2.4.7-p6 zou het filteren van het orderraster op datum een fout veroorzaken vanwege verbindingen met Braintree-modules.
De kwestie betrof vragen die zich bij braintree_transaction_details en sales_order lijsten aansluiten wanneer het toepassen van datumfilters.
Adobe Commerce Engineering heeft de zaak onderzocht, maar kon de fout in de omgeving niet reproduceren.
Filteren op datum moet naar verwachting zonder fouten orders met het filter retourneren.

_AC-15037 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40024)_

#### Het creëren van de orde in backoffice met veelvoudige producten waarvan minstens één douaneopties bevat, leidt tot ongewenste extra producten om aan de orde te worden toegevoegd

Probleem verholpen waarbij het maken van een bestelling in de back-up met meerdere producten, waaronder een met aangepaste opties, onbedoeld extra producten toevoegde en fouten veroorzaakte. Het systeem voegt nu alleen de geselecteerde producten toe, zodat bestellingen zonder onverwachte items kunnen worden gemaakt.

_AC-15286 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40122) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/b5e99d20)_

#### Magento2: geen regel voor speciale acties kan worden gemaakt

Deze PR corrigeert, krijgen we
\Magento\Catalog\Model\ResourceModel\Eav\Attribute model in plaats van \Magento\Catalog\Model\ResourceModel\Eav\Attribute in de methode \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/12176) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/30479)_

#### Magento heeft het entiteitstype $order gewijzigd na aanroepen van $factuur = $this->_factuservice->prepareInvoice($order);

Probleem verholpen waarbij tijdens het bewerken van een bestaande geplande update voor een subcategorie het aantal children_count voor bovenliggende categorieën in de database onjuist werd verhoogd. Het probleem heeft geleid tot onjuiste hiërarchiegegevens van categorieën nadat updates waren opgeslagen. Na de moeilijke situatie, blijft de kindtelling correct en niet meer onverwacht toename.

_AC-15401 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40154)_

#### De bestelling blijft na verzending in de status &#39;processing&#39; (verwerking) staan als objecten gedeeltelijk worden terugbetaald

Probleem verholpen waarbij bestellingen de status Verwerken bleven nadat ze objecten gedeeltelijk hadden terugbetaald en de overige objecten werden verzonden. De status van de bestelling wordt nu correct bijgewerkt en voltooid wanneer de totale verzonden en terugbetaalde hoeveelheden overeenkomen met de gefactureerde hoeveelheid. Hierdoor wordt een accuraat levenscyclusbeheer van de bestelling gegarandeerd.

_AC-15419 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/cc0ec250)_

#### Het verzenden van een e-mailbericht van een backend geeft altijd succes - ook als dit is uitgeschakeld

Probleem verholpen met het e-mailbericht voor terugverkoop om nauwkeurige berichten weer te geven door het resultaat van de e-mailservice te valideren. Zo zorgt u ervoor dat gebruikers op de hoogte worden gesteld wanneer e-mails met bestellingen of facturen zijn uitgeschakeld en niet worden verzonden.

_AC-16059 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40309) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/c95ed7d7)_

#### De aangepaste prijs 0 wordt bij opnieuw ordenen teruggezet op de oorspronkelijke prijs.

Producten met een aangepaste prijs van 0 werden tijdens het opnieuw ordenen weer tegen de oorspronkelijke prijs geplaatst. Dit probleem is nu opgelost.
De aangepaste prijs blijft nu op de juiste wijze behouden en zorgt ervoor dat de prijs nauwkeurig is bij het opnieuw ordenen van items.

_AC-8147 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/36970) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/01cee3c3)_

#### Bestelling plaatsen met Uitgeschakelde betalingsmethode

Probleem verholpen waarbij orders via GraphQL konden worden geplaatst met een betalingsmethode voor niet-openbare betalingen.
Er wordt nu een fout geretourneerd wanneer wordt geprobeerd een niet-beschikbare betalingsmethode in te stellen of te gebruiken, waardoor de bestelling niet kan worden gemaakt.

_AC-9605 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37983) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### Status van bestelling blijft bij verwerking behouden

Voordat de correctie werd uitgevoerd, werd bij het bestellen van een bundelproduct met de optie &quot;Samen verzenden&quot; ingeschakeld, niet automatisch overgeschakeld naar &quot;Voltooien&quot; na factuur en verzending. Na de correctie schakelt de orderstatus automatisch over naar &quot;complete&quot; nadat de bestelling is gefactureerd en verzonden.

_ACP2E-3947 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2a252ae6)_

#### [ Magento OOTB-code van 1&rbrace; Cloud - E-mail de kwestie van de Opstelling van het Malplaatje]

Voordat de oplossing werd gevonden, waren de e-mails bij het gebruik van asynchrone e-mailverzendingen niet in overeenstemming met de order van de winkel. Na deze correctie wordt nu de juiste e-mailbestelling voor verzending via e-mail naar de winkel verzonden.

_ACP2E-3998 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### Omleiding van factuur naar 404 annuleren

Annulering van de factuur met het type Not Capture leidt niet langer tot pagina 404.

_ACP2E-4001 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Probleem met bijgewerkte bestellingen met configureerbare opties die REST API gebruiken

Bestaande productopties op verkooporderitems behouden wanneer een bestelling wordt bijgewerkt via eindpunten van de rest van de app.

_ACP2E-4061 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### De async van de verkoop door identiteitskaart- tussenvoegsel beperkt tot 100 ingangen per bouwstijllooppas

Verbeterde verwerking van het asynchrone tussenvoegsel van het verkoopnet. Bij één uitsnijdbewerking worden nu alle rijen die in behandeling zijn, in batches ingevoegd in plaats van een strikte 100 rijen per uitvoering.

_ACP2E-4360 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/31258bf6)_

#### Foutbericht &quot;Het product met id &quot;1&quot; bestaat niet.&quot; wordt herhaaldelijk het programma geopend in exception.log

Vóór de correctie, werden de kritieke fouten geregistreerd toen de geschrapte producten in de Laatste Bestelde sectie van Punten werden ontmoet. Na de correctie kunnen handelaren configureren of verwijderde producten moeten worden geregistreerd of overgeslagen via de parameter `skipDeletedProductLogging` in di.xml. Standaard blijft het gedrag ongewijzigd voor achterwaartse compatibiliteit, maar verkopers kunnen de parameter instellen op `true` om verwijderde producten stil over te slaan en logruis te voorkomen.

_ACP2E-4366 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

#### Dubbele belasting op terugbetaling tweede creditnota

Correctie van onjuiste belastingberekening in creditnota&#39;s toen het creëren van een gedeeltelijke terugbetaling van een factuur nadat een vorige creditmemo van de de meningspagina van de orde werd gecreeerd.

_ACP2E-4384 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### Volgorde, prijzen

#### Bij het maken van de return geeft Admin een onjuist valutasymbool weer

Bij een installatie van meerdere websites met verschillende valuta&#39;s (EUR/USD/GBP) wordt op de pagina met de productselectie voor retourzending in de administratie nu het juiste valutasymbool weergegeven. Eerder werd het standaardvalutasymbool weergegeven.

_ACP2E-3658 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

### Order, Returns

#### Fout bij maken van creditmemo voor offline restitutie

Probleem verholpen waarbij het maken van een creditmemo mislukte voor bundelproducten met de instelling Dynamische prijs = Nee. Creditmemo&#39;s kunnen nu zonder fouten worden gemaakt.

_ACP2E-4157 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

### Andere ontwikkelaarsgereedschappen

#### [ Verkeerde het typewenk van de kwestie ] voor het beschermde lid $_urlHelper

Het systeem lost nu de verkeerde typewenk met correct op, die ook in aannemer wordt gebruikt

_AC-10716 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/32503) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/32496)_

#### [ Uitgave ] schoonmaakbeurt ongebruikte code.

Het systeem verwijdert nu ongebruikte code voor de ongebruikte importbewerkingen.

_AC-10980 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38424) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/33499)_

#### Toegankelijkheid van vuurtoren is mislukt

Het systeem gaat nu over met toegankelijkheidsscore van 100

_AC-12783 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39054) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39164)_

#### Captcha storefont-configuratie uitschakelen en nog steeds captcha js-bestanden laden

Het systeem laadt nu geen captcha js-bestanden wanneer we captcha hebben uitgeschakeld
voor storefont

_AC-14267 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/32987) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39154)_

#### [ Toegankelijkheid van 0&rbrace; kwestie ]: WAI-ARIA rollen die verkeerd in menu nesten

Het systeem genereert nu een toegankelijkheid van een vuurtoren zonder dat de WAI-ARIA-rollen fout nesten in een menufout en het rapport moet groen zijn

_AC-15082 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40045) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38617)_

#### Console-fout in e-mailvoorvertoning in Magento-beheerder

Het systeem genereert geen consolefout wanneer we een voorbeeld van de e-mailsjabloon bekijken

_AC-9245 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37820) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37933)_

### Betalings-/betalingsmethoden

#### Paylater Message wordt niet weergegeven in storefront terwijl de configuratie is gelukt in Backend

Probleem verholpen waarbij het PayPal Pay Later bericht niet werd weergegeven op de pagina&#39;s Home en Winkelwagentje ondanks dat het in de achtergrond werd geconfigureerd. De banner kon niet worden weergegeven wanneer het land van de koper voor gasten of klanten zonder standaardadres null was. Na de correctie wordt het bericht Later betalen correct weergegeven in de winkel.

_AC-12335 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/528af81a)_

### Betalingen

#### [ Uitgave ] Correctie offline factuur vangst (404)

Hierbij wordt de fout van 404 pagina&#39;s gecorrigeerd terwijl facturen voor offline betalingsmethoden worden vastgelegd door Magento-beheerders

_AC-1336 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39298) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39297)_

#### Onbekende IPN&#39;s van PayPal misbruiken IPN-processor

De IPN-handler negeert nu niet-ondersteunde of onbekende IPN-typen. In plaats van een 500-fout te retourneren, wordt het probleem geregistreerd en wordt de verwerking zonder onderbreking voortgezet.

_ACP2E-4049 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Met PayflowPro opgeslagen kaarttoken is mislukt bij betaling

PayPal PayFlow Pro transactie-id&#39;s (PNREF&#39;s) zijn nu geldig voor gebruik in Reference Transactions voor een vaste periode van 12 maanden. Nadat de vervaldatum is bereikt, wordt de opgeslagen kaart niet meer weergegeven en moet deze opnieuw worden toegevoegd. Voorheen werd de geldigheid bepaald door de vervaldatum van de betaalkaart die in de oorspronkelijke transactie werd gebruikt.

_ACP2E-4064 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### Uitgave van een Vaulcard bij het plaatsen van een bestelling op Admin

Het plaatsen van een bestelling met een opgeslagen creditcard op een website met een andere configuratie voor een betalingsactie leidt niet langer tot een fout of een verkeerd transactietype

_ACP2E-4270 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a8c9a9a)_

#### [ Cloud ] PayflowPro bewaarde kaart (Vault) laatste 4 cijfer niet in de orde toont

De kaartgegevens worden nu correct voortgezet en weergegeven wanneer je opgeslagen kaarten gebruikt bij de actie Verkoop, overeenkomstig het gedrag wanneer je de betalingsactie Autorisatie voor PayflowPro gebruikt.

_ACP2E-4346 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

### Prestaties

#### [ Uitgave ] Update Store.php

Deze PR verbetert de prestaties door de huidige winkelresolutie over te slaan.

_AC-14791 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39949) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/38717)_

#### [ Uitgave ] de controle van het gebruiksgeheime voorgeheugen van de Update onveranderlijk voor statische plaats

Deze PR verbetert de prestaties door de statische inhoud op elke pagina pas te valideren wanneer en tenzij deze wordt gewijzigd.

_AC-15171 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39486) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39484)_

#### [ Geheime voorgeheugen van de kwestie ] de resultaten van vraag isCacheable om prestaties te verbeteren

Deze PR voegt caching voor de methode isCacheable() toe, wat resulteert in het renderingsproces van de layout om redundante controles te verminderen en de algehele weergaveprestaties van de pagina te verbeteren.

_AC-16054 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40156) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40112)_

#### [ kwestie ] de kleine prestatiesverbetering van de async verwerking van het ordenetwerk

Deze PR introduceert een prestatiesoptimalisering voor de asynchrone verwerking van het ordennet van Magento door de transient cache-based last_updated_at raadpleging te vervangen met een blijvende die vlag DB-gesteund in de vlaglijst wordt opgeslagen. Dit verzekert het systeem constant de laatste verwerkte timestamp zelfs na geheim voorgeheugenflushes of plaatsingen behoudt, die onnodige full-table scans op grote sales_order datasets verhinderen. Hierdoor worden asynchrone rasterupdates efficiënter en voorspelbaarder, met name in winkels met veel volumes met veelvuldige orderactiviteit.

_AC-16109 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40282) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40271)_

#### [ CLOUD ] Onbekwaam om producten aan categorieën toe te voegen

Verbeterde prestaties wanneer het toevoegen van product aan categorie door Visuele Merchandiser.

_ACP2E-3946 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/inventory/commit/29653b1d)_

#### Probleem met het opschonen van wijzigingen na ACP2E-3995

Na de correctie worden wijzigingen volledig gewist door de snijtaak van indexer_clean_all_changelogs, waarbij batchgewijs wordt gehouden.

_ACP2E-4211 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/ee918f0d)_

#### [ CLOUD ] het Fastly geheime voorgeheugen werkt niet nadat wij aan 2.4.8 bevorderen

Oplossing voor een probleem waarbij cacheable pagina&#39;s niet correct werden opgeslagen of via Fastly-cache werden aangeboden, wat leidde tot inconsequent cachegedrag en verminderde prestaties.

_ACP2E-4324 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

#### Onderzoek de redenen voor verhoogde opnieuw sleutels en geheim voorgeheugensleutels verwezenlijking

Voorafgaand aan de correctie waren de cacheknoppen die voor externe opslagmetagegevens werden gebruikt, niet verlopen. Nu, na de moeilijke situatie, kunt u TTL voor dergelijke geheim voorgeheugensleutels door gebiedsdeelinjectie plaatsen.

_ACP2E-4345 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

### Prijsstelling

#### Prijs is altijd 0 voor bundproduct-items zonder dynamische prijs voor rest-API voor bestelling

De REST API van de orde keert nu correcte prijzen voor bundelproductpunten zonder dynamische prijs terug.
Eerder, toen het uitvoeren van orden via REST API, de prijs voor bundelproducten zonder dynamische prijsstelling altijd als 0 werd teruggegeven, in plaats van de daadwerkelijke prijs die op de bundelpagina wordt getoond.
AC-1925

_AC-11925 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38687) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/7da46f52)_

#### Onjuist bereik toegewezen aan prijskenmerken bij maken

Probleem verholpen waarbij nieuw gemaakte prijskenmerken ten onrechte het bereik van de winkelweergave werden toegewezen, ongeacht de configuratie. Na de correctie wordt het kenmerkbereik nu standaard uitgelijnd op de instelling voor prijsbereik van catalogus (Algemeen of Website).

_AC-14945 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39986) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### Het product wordt opgeslagen, zelfs als de Speciale prijs van Datum later is dan Datum met behulp van een massale actie

Producten konden zonder validatie worden opgeslagen met een ongeldig speciaal prijsdatumbereik. Dit probleem is nu opgelost.
Er wordt nu een foutbericht weergegeven: &quot;Controleer of de datum Tot later is dan of gelijk is aan de datum bij Van.&quot;

_AC-15252 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40113) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/36d4d6fb)_

#### De normale prijs is niet zichtbaar, ook al wordt een speciale prijs toegepast.

Probleem opgelost waarbij de normale prijs niet werd weergegeven toen een speciale prijs werd toegepast. De normale prijs wordt nu correct weergegeven naast de speciale prijs zoals verwacht.

_ACP2E-4100 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/47721be6)_

### Product

#### Configureerbaar product met slecht gedrag aan de voorkant

Het probleem waarbij configureerbare producten een onjuist gedrag aan de voorzijde weergaven wanneer een kleurstaalkenmerk werd opgenomen, waardoor de prijzen, de lay-out voor vervolgkeuzelijsten en de vereiste veldindicatoren onjuist werden weergegeven. Dit probleem is nu opgelost.
Nu, vormen de configureerbare producten correct met juiste tarifering, gerichte dalingen, en verwacht gedrag UI terug.

_AC-1014 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/14296) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### De beweringskoord van de prijs wanverhouding wanneer het Configurable Product toegewezen aan de Voorraad van de Test en website van de Test met optie om uit-van-voorraad producten te tonen toegelaten

Bijgewerkt de falende test om zich aan werkelijk prijsgedrag voor configureerbare producten te richten wanneer alle kindproducten de zelfde prijs hebben.
De bewering bevestigt nu correct de getoonde prijs, die valse testmislukkingen verhindert zonder functionaliteit te beïnvloeden.

_AC-10843 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/inventory/commit/1ccc786b)_

#### Het label &#39;As low as&#39; wordt nog steeds weergegeven voor een configureerbaar product voor testcase AC-6158

Geïmplementeerde en geverifieerde configureerbare producten (P1-P7) met respectieve variaties en categorietoewijzingen. Zorgde voor een correcte weergave van de winkelprijs en een zo laag mogelijk labelgedrag voor producten van categorie C.

_AC-10847 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Procentuele korting op de tier-prijs en op de regel voor catalogusprijs berekend op de oorspronkelijke prijs zonder geselecteerde opties.

Procentuele kortingen op de prijsregels voor lagen en catalogusprijzen bevatten nu geselecteerde aangepaste opties.
Eerder werden procentuele kortingen berekend op de oorspronkelijke productprijs zonder rekening te houden met geselecteerde aangepaste opties, wat tot onjuiste eindprijzen leidde.
AC-12004

_AC-12004 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38750)_

#### [ Uitgave ] bevestigt-classificatie werkt niet, wordt de selecteur van revisieclassificatie veranderd

Probleem verholpen waarbij de validatie van de beoordeling niet werd geactiveerd vanwege een gewijzigde kiezer. Eerder konden revisies worden opgeslagen zonder een beoordeling te selecteren. Nadat de correctie is uitgevoerd, werkt de validatie correct en wordt een revisie niet opgeslagen, tenzij er een classificatie is geselecteerd.

_AC-12686 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/33424) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/528af81a)_

#### Magento 2.4.7 minAllowed missing product order quality

Het systeem werkt prima en de paginabron geeft de minimale hoeveelheid van het product correct weer

_AC-12909 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39142) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39480)_

#### De Inzameling van het product - addMediaGalleryData roept getSize wanneer de inzameling misschien of zal worden geladen (kan telling gebruiken om een extra vraag van DB te vermijden)

Deze PR vermindert de extra vraagvraag gebruikend count() als de productinzameling reeds wordt geladen wanneer het roepen van Grafiek van het Product met media_gallery gebied inbegrepen in het.

_AC-13055 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39111) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39681)_

#### Ongeldige SKU-verwerking voor gekoppelde producten in Magento

Probleem verholpen waarbij producten met SKU &quot;0&quot; niet konden worden gekoppeld als gerelateerde, up-sell of cross-sell items vanwege ongeldige SKU-validatie. De update zorgt ervoor dat dergelijke producten kunnen worden gekoppeld, zodat het product zonder fouten kan worden opgeslagen.

_AC-13311 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39329) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

#### Probleem met het raster Aanpasbare opties op de productpagina in het deelvenster Beheer

Het systeem werkt zoals verwacht wanneer we aanpasbare opties maken met vervolgkeuzelijst voor tekst

_AC-14003 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39640) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39694)_

#### Fout op de pagina met productpagina Admin wanneer alle productkenmerken zijn ingesteld op algemeen bereik

Probleem verholpen waarbij op de pagina voor productbewerking voor beheerders een fout werd weergegeven wanneer alle productkenmerken op een algemeen bereik waren ingesteld. De fout werd veroorzaakt door een lege gegevensbestandvraag, die tot de pagina onbruikbaar maakt. Na de correctie wordt de productpagina correct weergegeven en kunnen producten zonder problemen worden gemaakt.

_AC-14011 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39646)_

#### [ 2.4.8 ] Geen callbacks die voor cron job catalog_product_alert worden gevonden

Adobe Commerce voorkomt nu op de juiste wijze dat onjuiste catalog_product_alert-snijtaken worden gepland nadat de naam van de productwaarschuwing is gewijzigd in product_alert. Eerder, in Adobe Commerce 2.4.8, leidde het vormen van Opslag > Configuratie > Catalogus > Catalogus > de Montages van de Looppas van de Waarschuwingen van het Product ertoe dat een catalog_product_alert cron ingang in core_config_data wordt gecreeerd, en wanneer het bouwwerk het dossier opende de fout Magento_Cron.CRITICAL: Uitzondering: Geen callbacks die voor cron baancatalog_product_alert worden gevonden alt alhoewel de geldige product_alert correct was.

_AC-14494 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39800) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### [ Product vergelijk ] vergelijkingslijst zal onbruikbaar zijn

Probleem verholpen waarbij de vergelijkingslijst onbruikbaar werd toen het zelfde product van verschillende archiefmeningen werd toegevoegd; na de moeilijke situatie, laadt de vergelijkingslijst correct en toont punten die op de specifieke opslag worden gebaseerd.

_AC-14885 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### Extra registratie bij aanvragen van een product via een opslagplaats mislukt

Verbeterde foutberichten voor ProductRepository::get en getById wanneer geen SKU of ID wordt gevonden.
Eerder, verstrekte de uitzonderingen geen context over welke SKU of identiteitskaart de fout veroorzaakte.
Nu, omvat het uitzonderingsbericht ontbrekende SKU of identiteitskaart, die in het zuiveren en ontwikkelaarservaring helpt te verbeteren.
Deze wijziging heeft geen invloed op functies van de API.

_AC-15199 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40090) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Kenmerkset bestaat geen fouteinden op de pagina

Probleem verholpen waarbij het invoeren van een ongeldige kenmerkset-id in de URL een fatale fout veroorzaakte. Het systeem geeft nu een correct foutbericht weer met de mededeling dat de kenmerkset niet bestaat in plaats van de pagina te verbreken.

_AC-15753 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40213) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a06a4a57)_

#### Restitutie met negatieve restitutie van de hoeveelheid

Het maken van een creditmemo met een negatief aantal heeft het kortingsbedrag onjuist gerestitueerd. Dit probleem is nu opgelost.
Kortingen worden nu niet terugbetaald voor negatieve hoeveelheden en de restitutiehoeveelheid wordt correct op nul ingesteld.

_AC-9424 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37917) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### Langzame query wordt uitgevoerd wanneer productwidget wordt opgenomen via pagebuilder

De query voor het maken van productwidgets, inclusief product-SKU&#39;s, is geoptimaliseerd.

_ACP2E-3449 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### Afbeeldingen van producten waarvan de grootte niet wordt aangepast wanneer ze als configureerbaar product worden toegevoegd

Eerder waren de afbeeldingen die via Configuraties in het beheerpaneel werden toegevoegd, niet in overeenstemming met de maximale uploadgrootte, wat tot inconsistenties en beheerproblemen kan leiden. Er is nu een oplossing geïmplementeerd om ervoor te zorgen dat de grootte van de afbeeldingen tijdens het uploaden automatisch wordt aangepast om te voldoen aan de maximale groottebeperking, het proces te stroomlijnen en systeemstandaarden te handhaven.

_ACP2E-3504 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/df92debe)_

#### Alle punten van andere klanten vergelijken lijsten worden toegewezen aan de klant na het programma openen via admin

Eerder, toen een beheerder de &quot;Login als Klant&quot;eigenschap in het achterste eind gebruikte, werden de producten van de vergelijkingslijst van een eerder het programma geopende klant verkeerd toegewezen aan de momenteel nagemaakte klant.  Na de moeilijke situatie laadt de vergelijkingslijst correct voor de correcte het programma geopende klant.

_ACP2E-3818 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### [ B2B ] Gedeelde Catalogus sparen Keert Vervangen Fout van de Functionaliteit

Admin kan de toewijzing van producten uit de gedeelde catalogus ongedaan maken.
Eerder ontkende het toewijzen van producten met groot aantal lange product SKUs van Gedeelde Catalogus resulteerde in fout

_ACP2E-4097 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/ab891304)_

#### [ de generatieprestaties van de Sitemap van 0&rbrace; wolk &lbrace;zijn beduidend degraded]

Sitemap-generatie voor producten met afbeeldingen heeft niet langer een exponentiële vertraging. Eerder was het genereren van sitemaps voor winkels waarin het opnemen van afbeeldingen was ingeschakeld, een langdurig proces.

_ACP2E-4153 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e457c5e2)_

### Product, belasting

#### De vaste productbelasting (FPT) wordt niet afzonderlijk weergegeven met configureerbare producten

Probleem verholpen waarbij Vaste productbelasting (FPT) na het selecteren van een optie niet afzonderlijk werd weergegeven voor configureerbare producten. De FPT-indeling wordt nu op de juiste wijze weergegeven op de pagina&#39;s met productlijsten en details, in overeenstemming met de weergaveformaat van eenvoudige producten.

_AC-13171 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/b5e99d20)_

### Aanbieding

#### Met de regel voor kopen van X Winkelwagentje krijgt je onjuiste korting wanneer een andere regel al is toegepast

Probleem verholpen waarbij met de regel Winkelwagentje kopen X ophalen Y-winkelwagentje kortingen berekende op basis van de oorspronkelijke productprijs, zelfs nadat een andere regel deze al had verlaagd. De update zorgt ervoor dat de tweede regel nu de korting op de aangepaste prijs toepast. Dit resulteert in nauwkeurige totale kortingen wanneer meerdere aanbiedingen actief zijn.

_AC-12325 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### Fout bij het ophalen van kortingen voor orderitems toegepast_op voor klantenbestelling via GraphQl-klantverzoek

Eerder toen kortingen die_op voor klantenorde via GraphQl klantenverzoek werden toegepast interne serverfout werd waargenomen die nu vast is en de juiste gegevens van de klantenorde met toegepaste korting wordt gehaald

_AC-14888 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39963) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/fe72c407)_

#### Fout bij het ophalen van code voor het coupon van orderitems voor de klant via GraphQl-klantaanvraag

Ophaalopdrachten met coupongegevens via GraphQL hebben een interne serverfout geretourneerd. Dit probleem is nu opgelost.
De query wordt nu uitgevoerd en retourneert de juiste couponinformatie in de reactie.

_AC-14889 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39962) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/fe72c407)_

#### [ de Regel van de Catalogusprijs van de Wolk ][experienceleague] wordt niet toegepast

Vóór het instellen van de prijsregels voor de vaste catalogus werden de prijsregels niet toegepast wanneer `special_price` alleen op websiteniveau was ingesteld (niet bij Alle winkelweergaven). Nadat de prijsregels voor de herstelcatalogus correct zijn toegepast, wordt `special_price` nu op websiteniveau ingesteld door eerst de standaardwinkel van de website te controleren.

_ACP2E-4372 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### SEO

#### DynamicStorage.findProductRewriteByRequestPath() heeft geen filtermethode voor het type entity_type, waardoor CMS-pagina&#39;s worden behandeld als producten in categorie-URL&#39;s

Probleem verholpen waarbij DynamicStorage niet filterde op entiteit_type, waardoor CMS-pagina&#39;s onjuist werden behandeld als producten in categorie-URL&#39;s. Onjuist gevormde URL&#39;s retourneren nu correct een 404 in plaats van CMS-inhoud.

_AC-14991 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39996) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/64823f95)_

#### Uitschakelen van categoriepad in product-URL&#39;s resulteert in meerdere manieren van de opslagswitch

Probleem verholpen waarbij het inschakelen van categoriepaden in product-URL&#39;s ertoe leidde dat de store-switch mislukte. Door het schakelen naar een andere winkel worden product-URL&#39;s nu correct omgezet in de verschillende winkelweergaven zonder dat de gebruiker naar de homepage ging of fouten retourneerde.

_AC-15110 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40037) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a7ef6300)_

#### Ongedefinieerde arraysleutel in ProductRepository getById

De kwestie kwam voor toen ProductRepository::getById () met een ongeldige identiteitskaart zoals 123abc werd geroepen, die tot een &quot;Undefined seriesleutel&quot;fout leidde.
Na de moeilijke situatie in Magento 2.4.9-alpha3, keren dergelijke verzoeken nu correct een 404 pagina in plaats van het werpen van een uitzondering terug.
QA bevestigd met zowel geldige als misvormde id&#39;s, en er werden geen verdere problemen waargenomen.

_AC-15345 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40146) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/68a45d0a)_

#### Met het vergelijkingsproduct Storefront wordt een Google SEO-fout gemaakt - Koppelingen kunnen niet doorlopen

Oplossing voor een SEO-probleem waarbij de link &quot;Compare Products&quot; van de winkel niet door zoekmachines kon worden gevolgd omdat een ontbrekend of onjuist gebonden href-kenmerk ontbreekt. De update zorgt ervoor dat de koppeling nu een geldige, schuifbare URL bevat, waardoor de site beter kan worden ontdekt en Google SEO-audits beter kunnen worden doorgestuurd.

_AC-15547 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40185) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/c95ed7d7)_

#### Het bijwerken van product url_key via REST API genereert geen 301 URL herschrijven

Wanneer u de URL-sleutel van het product bijwerkt via de REST-API en de instelling &quot;Permanent omleiden voor URL&#39;s maken als URL-sleutel gewijzigd&quot; op Ja instelt, wordt bij het opnieuw schrijven van de product-URL een omleiding van de oude URL naar een nieuwe URL gemaakt.

_ACP2E-3900 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### [ Cloud ] Sitemap-generatie eindigt nooit

Vóór de correctie kon de sitemap-generatie niet worden voltooid als de catalogus meer dan een miljoen producten bevat. Na de oplossing eindigt de sitemapgeneratie met een lagere geheugentoewijzing en met maximaal één miljoen producten per winkel.

_ACP2E-3902 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/52f46328)_

#### [ de Schakelaar van de opslag van 0&rbrace; wolk &lbrace;het Werken van de Schakelaar van de Opslag niet van EN aan FR voor FAQ Pagina]

Probleem verholpen waarbij gebruikers door het schakelen tussen de winkelweergaven werden omgeleid naar de startpagina in plaats van naar de overeenkomstige vertaalde CMS-pagina. De opslagschakeloptie controleert nu of de URL opnieuw wordt opgeslagen in de doelwinkel om de juiste omleiding te garanderen (pagina met veelgestelde vragen in het Engels → pagina met veelgestelde vragen in het Frans).

_ACP2E-4112 - [&#x200B; GitHub kwestie &#x200B;](https://adobe-ent.crm.dynamics.com/main.aspx?appid=f2e74f34-7119-ea11-a811-000d3a5936c5&forceUCI=1&pagetype=entityrecord&etn=incident&id=3e1df344-8a69-f011-bec3-6045bd04f475)_

#### [ Cloud ] deactivate de oude generatie sitemap

Er is nu een nieuwe configuratieoptie beschikbaar waarmee kan worden geschakeld tussen het standaard sitemap-generatieproces en een nieuw geïmplementeerde batchmodus. Dankzij deze verbetering kunnen workflows voor het maken van sitemap flexibeler en schaalbaarder worden.

_ACP2E-4132 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/45cbf9b6)_

#### Vermoedelijke verzoeken werpen uitzonderingen in exception.log

Probleem verholpen waarbij kwaadaardige of misvormde URL-aanvragen tot sorteerfouten in de database leidden en uitzonderingslogbestanden vulden.
Eerder, toen verdachte verzoeken werden ontvangen die ongeldige karaktercoderingen of niet gestaafde karakters bevatten, zou het systeem proberen om hen te decoderen en te verwerken, die tot MySQL collatieconflicten leiden.

_ACP2E-4328 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/2687b487)_

### Verkoop

#### Wanneer het Cadeaubericht op het niveau van de Orde wordt toegelaten maar de gebruiker geen gegevens ingaat en orde plaatst, dan nog van Naam en aan Naam in Admin die klant eerste en familienaam tonen.

Probleem verholpen waarbij de velden voor het verzenden van cadeauberichten en de geadresseerde automatisch werden gevuld met klantnamen, zelfs als er geen cadeaubericht was ingevoerd. De velden blijven nu leeg, tenzij de gebruiker de gegevens opgeeft.

_AC-15140 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/a8cf637b)_

### Zoeken

#### &quot;Bevestig de Terugzending van het Formulier&quot;op Catalogusonderzoek met &quot;Herinner de Paginering van de Categorie&quot;

Wanneer u na het wijzigen van de werkbalkinstellingen teruggaat van een productpagina naar de pagina Zoekresultaten catalogus, wordt het dialoogvenster Formulierherverzending bevestigen niet meer geactiveerd wanneer de optie Categoriepaginering onthouden is ingeschakeld.
Eerder hebben gebruikers een browserfout of een waarschuwing over het opnieuw verzenden van formulieren aangetroffen tijdens het terugkeren naar de pagina met zoekresultaten nadat ze de werkbalkparameters zoals de sorteervolgorde hadden gewijzigd.

_ACP2E-4208 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### Geaggregeerd zoekveld &quot;_search&quot; wordt niet meer gebruikt in de zoekquery

Nu, keert het full-text onderzoek passende producten terug als het minimum zou moeten gelijke voorwaarde over alle doorzoekbare gebieden collectief wordt voldaan, eerder dan het vereisen van de voorwaarde om door één enkel gebied worden voldaan aan.

_ACP2E-4285 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/cbca0396)_

### Beveiliging

#### Interne serverfout

Magento voegt nu met succes producten aan de kar van een klant toe wanneer het gebruiken van het asynchrone eindpunt van REST POST /rest/default/async/V1/kratten/mijn/punten. Eerder, resulteerde dit async &quot;add to cart&quot;verzoek in een Interne Fout van de Server, en Magento registreerde de volgende fout: Fout: Vraag aan een lidfunctie setFinalPrice () op ongeldig in app/code/Magento/Quote/Model/Quote/Item/AbstractItem.php :162.

_AC-16344 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### Gebundelde/samengevoegde JS maakt geen deel uit van SRI-hashes

Voorafgaand aan de moeilijke situatie produceerde de bundel of de samengevoegde dossiers werden niet toegevoegd aan de lijst van haasjes SRI. Nu, worden de dossiers behoorlijk toegevoegd aan de hakken SRI.

_ACP2E-3854 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/4ca73607)_

#### [ CLOUD ] kreeg schrijfbare toestemmingskwestie in newrelic

Vóór de correctie werden de logboeken overlapt met uitzonderingen. Nadat u de correctie hebt toegepast, zijn de logboeken nu schoon en vrij van uitzonderingen.

_ACP2E-4296 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/61c96348)_

### Verzending

#### Onjuiste hoeveelheid om te verzenden na weinig creditmemo&#39;s

De waarde voor Aantal tegen verzendkosten werd onjuist berekend na meerdere creditmemo&#39;s, waardoor objecten konden worden verzonden die werden terugbetaald. Dit probleem is nu opgelost.
Nu werkt het systeem de resterende hoeveelheid die kan worden verzonden correct bij op basis van verzonden en terugbetaalde items, waardoor ongeldige verzendingen worden voorkomen.

_AC-1479 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/34289) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### Mogelijke prestatieproblemen bij het laden van verzendmethoden

Geoptimaliseerd het laadproces van de verzendmethoden door ervoor te zorgen dat alleen actieve vervoerders op verzoek worden geladen. Eerder werden fabrieken voor alle verzendmethoden geïnitialiseerd, wat onnodige prestatieoverhead veroorzaakte. De oplossing verbetert de efficiëntie door voorwaardelijk alleen actieve scheepvaartmaatschappijen te laden, waardoor de laadtijd en het gebruik van bronnen worden verminderd.

_AC-15415 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40153) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/cc0ec250)_

#### [ Commerciële bestemming van de kwestie ] &lbrace;zou niet als woon moeten worden behandeld

Probleem verholpen in de UPS REST Shipping Integration waarbij commerciële bestemmingen onjuist werden behandeld als residentieel. De ResidentialAddressIndicator is nu alleen opgenomen in het UPS-tariefverzoek voor woonadressen, waardoor onbedoelde woontoeslagen worden voorkomen en nauwkeurige commerciële verzendingen worden gegarandeerd.

_AC-16285 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/40314) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/40307)_

#### Uitzondering tijdens maken van UPS-verzendlabel

Fixed Warning: Array to string conversion during UPS Shipping Label creation

_ACP2E-3676 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

#### [ KANSEN ] - controleert de de kernmodule Magento_Fedex voor een geldig-actief teken alvorens een verzoek te verzenden om nieuwe te krijgen?

Adobe Commerce doet niet langer veel aanvragen voor de FedEx API-service voor het toegangstoken. Eerder, alhoewel het toegangstoken nog geldig is, doet Adobe Commerce altijd nieuwe verzoeken aan FedEx API die een tarief beperkende kwestie veroorzaakten.

_ACP2E-3930 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/4ca73607)_

### Staging en voorvertoning

#### De prijs van het product in winkelwagentje waarop de catalogusprijsregel van toepassing is, verandert niet wanneer de regel wordt aangepast door de testupdate

Probleem verholpen waarbij de productprijzen in het winkelwagentje niet volledig werden bijgewerkt na wijziging van een prijsregel voor catalogi via een gefaseerde update. Voorheen verscheen de bijgewerkte prijs alleen in het samenvattende gedeelte, terwijl de oude waarde in het centrale winkelwagentje werd weergegeven. Nu werkt de herziene regel correct de productprijs over het volledige karretje bij.

_AC-15304 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/913bf1a6)_

#### Wanneer de geplande update voor categorie wordt geschrapt, wordt de hoeveelheid kinderen niet verminderd voor de oudercategorie

Probleem verholpen waarbij het verwijderen van een geplande update voor een categorie het aantal onderliggende items van de bovenliggende categorie niet reduceerde, zodat de telling correct wordt bijgewerkt wanneer geplande updates of subcategorieën worden verwijderd.

_AC-15670 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/ef666cd9)_

#### Als u de geplande update voor categorieën bewerkt, worden onderliggende items toegevoegd aan de bovenliggende categorie

Probleem verholpen waarbij tijdens het bewerken van een bestaande geplande update voor een subcategorie het aantal children_count voor bovenliggende categorieën in de database onjuist werd verhoogd. Het probleem heeft geleid tot onjuiste hiërarchiegegevens van categorieën nadat updates waren opgeslagen. Na de moeilijke situatie, blijft de kindtelling correct en niet meer onverwacht toename.

_AC-16239 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/8670a2b4)_

#### Als u een voorvertoning van een geplande update weergeeft, wordt de eerste winkelweergave in alfabetische volgorde geopend in plaats van in de winkelweergave van interesse.

Vóór de correctie wordt de voorvertoning van een geplande update in alfabetische volgorde geopend in de eerste winkelweergave in plaats van de toegewezen winkelweergave.
Na de correctie wordt de voorvertoning nu correct geopend in de winkelweergave die is toegewezen aan de CMS-bloktestupdate.

_ACP2E-3671 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/b12ffe36)_

#### Kan de geplande productupdate niet voorvertonen met rubriekmachtigingen ingeschakeld

Vóór de correctie werd een product dat in de toekomst moet worden ingeschakeld, niet weergegeven in de voorvertoningsmodus. Nu wordt deze ook weergegeven als de huidige status is uitgeschakeld.

_ACP2E-3786 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/7accebfa)_

#### Ontbrekende validatie voor veld kortingswaarde regel catalogusprijs

Eerder, werd het disconto_amount gebied in de het opvoeren planningsupdate niet correct bevestigd met de huidige bevestigingsregels. Nochtans, na het toepassen van de moeilijke situatie, zal het disconto_amount gebied geschikt worden bevestigd.

_ACP2E-3867 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/462ede94)_

#### Het product van de bundel met geplande updates verwijdert de bundeloptie op productsparen actie

Het verwijderen van bundelproductopties of bijbehorende producten in geplande update heeft niet langer invloed op de oorspronkelijke bundelopties en bijbehorende producten en omgekeerd. Als u na het plannen van een update ook de productieopties van de bundel verwijdert in het oorspronkelijke product en deze vervangt door een andere optie, worden de nieuw toegevoegde opties niet meer verwijderd

_ACP2E-4212 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/ab891304)_

#### Kan niet navigeren tussen websites in voorvertoning voor update van schema

Vóór deze correctie wordt de voorvertoning van de geplande update afgebroken wanneer wordt geprobeerd een voorvertoning van inhoud weer te geven voor winkels met aangepaste domeinen. Na deze correctie kunnen aangepaste store-domeinen ongewijzigd worden voorvertoond en in de voorvertoning van iframe worden genavigeerd. De moeilijke situatie behandelt producten, categorieën, de pagina&#39;s van CMS, en de blokken van CMS, en steunt navigatiekoppelingen die `{{store url}}` prijsverhogingstags gebruiken zoals die in [&#x200B; de Variabelen van Adobe Commerce en de Markeringen van de Prijsverhoging &#x200B;](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/variables/markup-tags) worden gedocumenteerd.

_ACP2E-4308 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/0a3b7032)_

### Belasting

#### Onjuist totaal van de Volgorde, wordt de ronde niet toegepast op de prijsberekening.

Het systeem wordt nu correct verwerkt bij het berekenen van de prijs_after_reduction, korting_amount en de belastingen.
het werkelijke totaal van de bestelling

_AC-11389 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38455) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/39687)_

#### [ Uitgave ] Repareren: De waarde base_weee_tax_applied_row_amnt van de Punten van het Memo van het Krediet is Onjuist

Correcteerde de berekening van het creditnota door de juiste setter voor base_weee_tax_applied_row_amnt te gebruiken, ervoor te zorgen dat de fiscale waarde slechts op de teruggegeven hoeveelheid wijst. Eerder werd voor het rijbedrag onjuist de waarde van de volledige bestelling gebruikt in plaats van het gedeeltelijke bedrag van de creditnota.

_AC-12049 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38765) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/3b5ac075)_

#### Posten in de mini-cart geven valutaprijzen weer zonder conversie

Mini-cart zet nu correct valuta om en toont het nauwkeurige bedrag dat op gevormde omzettingspercentages wordt gebaseerd.

_ACP2E-4364 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/1c547060)_

### Testkader

#### [ Uitgave ] verwijdert een gedupliceerde &lt;severity> markering van MFTF test AdminSetUpWatermarkForSwatchImageTest

Het systeem bevat nu slechts één ernstcode in AdminSetUpWatermarkForSwatchImageTest, waardoor de code helderder en consistenter wordt. Voorheen bevatte deze test twee identieke ernstlabels, wat onnodig was en tot verwarring kon leiden.

_AC-11873 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38504) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/31862)_

#### [ Uitgave ] negeert lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/nl...

Het systeem negeert nu het bestand &#39;env.php&#39; dat wordt gegenereerd wanneer eenheidstests worden uitgevoerd, zodat de status van de it na het uitvoeren van tests schoon blijft. Eerder, zou het runnen van eenheidstests een nieuw dossier &quot;env.php&quot;produceren, die de status van de it veroorzaken om een nieuw gevonden dossier te tonen en het te maken vies lijken.

_AC-13293 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39304) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37631)_

#### [ Uitgave ] de kwestie van de de integratietest van de Oplossing met onderschepper

Het systeem herkent en behandelt nu correct \Magento\TestFramework\App\Config\Interceptor in de integratietest, die ervoor zorgt dat de test tot de noodzakelijke gegevens kan toegang hebben zelfs wanneer een stop op de klasse bestaat. Eerder was het systeem er niet in geslaagd om de mogelijkheid van \Magento\TestFramework\App\Config te verklaren \Magento\TestFramework\App\Config\Interceptor was, resulterend in een fout toen het proberen om tot het $data bezit toegang te hebben.

_AC-13305 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39324) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/37187)_

#### [ Uitgave ] MFTF: Het voorleggen van E-mail aan de Vorm van de Vriend met toegelaten captcha

De testcase heeft betrekking op de functionaliteit van het formulier &quot;E-mail naar vriend&quot; wanneer CAPTCHA is ingeschakeld. Hierbij wordt ervoor gezorgd dat het proces voor het verzenden van formulieren correct werkt met onjuiste en correcte CAPTCHA-waarden.

_AC-13492 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/39462) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/32830)_

#### Hardcoded Fixture Paths Fail in Composer Build

_AC-16488_

#### [ Uitgave ] magento/magento2#: GraphQl mutatie. Extra testdekking voor de montages storeConfig van de klant.

Het systeem voegt nu de extra testdekking voor de volgende klanten storeConfig opties toe:
required_character_classes_number
minimum_password_length

_AC-9370 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37915) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/28761)_

#### Milieu-specifieke eenheidstests mislukkingen in AC 2.4.7-p3

Dit probleem verhelpt problemen met eenheidstests die niet in alle versies en omgevingen worden gereproduceerd. Eerder werden enkele eenheidstests niet hersteld omdat er verschillende bibliotheekversies waren of omdat er functionaliteit in een latere versie was toegevoegd.

_ACP2E-3712 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/9ad7d277)_

### UI Framework

#### [ Uitgave ] verwijdert gedupliceerde variabelen uit één van minder dossiers

Het systeem verwijdert nu gedupliceerde variabelen uit minder bestanden en zorgt voor een schonere en efficiëntere code. Eerder waren deze gedupliceerde variabelen aanwezig in de minder bestanden, wat leidde tot onnodige redundantie in de code.

_AC-11743 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/31154) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/31150)_

#### WYSIWYG is leeg in dynamische rijen

WYSIWYG-velden in dynamische rijen worden nu correct geïnitialiseerd en gevuld.
Eerder konden WYSIWYG-velden in dynamische rijen (zoals in ontwerpconfiguratieformulieren) na bepaalde handelingen leeg lijken of hun inhoud verliezen, waardoor handmatig ingrijpen nodig was om gegevens te herstellen.
AC-12336

_AC-12336 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/38893) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [ kwestie ] mime type van Reparatie

Het systeem handelt het mime-type en -type voor gif-afbeelding correct af en corrigeert deze

_AC-8001 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/36899) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/36669)_

#### [ Uitgave ] verwijdert verboden `@author` markering uit `Magento_Backend`

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8814 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37522) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/36976)_

#### [ Uitgave ] vermijd directe toegang tot de lijst van overzichten Ajax

Het systeem handelt correct en vermijdt directe toegang tot de revisielijst Ajax

_AC-9381 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37920) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/pull/33876)_

#### Aanmelden/afmelden van koptekst niet bijwerken in installatie van meerdere winkels met gedeelde cookies

De header van de aanmelding wordt correct bijgewerkt bij het afmelden in overeenstemming met de configuratie-instellingen. Customer-data.js zal een koekje gebruiken om de &quot;beeld-klant-login&quot;waarde op te slaan als de klantenrekeningen globaal worden gedeeld. Lokale opslag wordt anders gebruikt.

_ACP2E-4149 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### [ Mobiel ] Fotorama kan MinKar op de dichte actie van de Kijker van het Beeld openen

Het probleem met Fotorama is opgelost. Eerder werd een Mini Cart geopend bij de sluitactie van de Image Viewer

_ACP2E-4231 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/e885088b)_

#### De samengevoegde JS dossiers worden niet behoorlijk geproduceerd op projecten met vele opslag.

Het samenvoegen van JavaScript-bestanden werkt nu correct wanneer meerdere opslagruimten zijn geconfigureerd.
Eerder konden bestanden soms niet correct worden samengevoegd in meerdere winkelinstellingen, wat tot onvolledige of inconsistente resultaten leidde.

_ACP2E-4246 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/ab891304)_

### Upgrades - Upgrade Compatibility Tool

#### Vervangen functionaliteit: maken van dynamische eigenschap Magento\Framework\Acl:$_roleRegistry

Verouderde functiefouten verhinderen niet langer de toegang van het beheerpaneel na een upgrade.
Na de upgrade naar Magento 2.4.6 kan het openen van het deelvenster Beheer resulteren in de fout:
&quot;Vervangen functionaliteit: maken van dynamische eigenschap Magento\Framework\Acl:$_roleRegistry is afgekeurd in vendor/magento/framework/Session/SessionManager.php op regel 186&quot;
Hierdoor konden beheerders zich niet aanmelden.
AC-12343

_AC-12343 - [&#x200B; GitHub kwestie &#x200B;](https://github.com/magento/magento2/issues/37469)_
