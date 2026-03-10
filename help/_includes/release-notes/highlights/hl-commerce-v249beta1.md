---
source-git-commit: fd421e8c2455a2b45d3f3cc93573d2a609e4936d
workflow-type: tm+mt
source-wordcount: '2408'
ht-degree: 0%

---
# Adobe Commerce-hooglichten (v2.4.9-bèta1)

## Hooglichten in v2.4.9-bèta1

De volgende markeringen zijn van toepassing op de Adobe Commerce 2.4.9-bèta1-release.

### API&#39;s

#### REST API-productgalerie, overervingscontrole op archiefweergaveniveau

Wanneer een product via REST API in een opslagbereik wordt bijgewerkt, kunnen productafbeeldingen en video&#39;s geen wijzigingen van het algemene bereik overnemen wanneer `media_gallery_entries` wordt weggelaten uit de payload of is ingesteld op `NULL` . Het is nu ook mogelijk om via REST API de bereikovererving voor productafbeeldingen en -video te herstellen door het corresponderende veld in te stellen op `NULL` .

_ACP2E-4358 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Gebruikersinterface van beheerder

#### Menu Handelingen voor raster met catalogusprijsregels

Het raster Catalog Price Rules in Commerce Admin bevat nu een menu Acties waarmee verkopers meerdere prijsregels voor catalogi tegelijk kunnen activeren, deactiveren of verwijderen. Dit brengt het beheer van catalogusprijsregels in overeenstemming met de bestaande bulkacties beschikbaar voor de Regels van de Prijs van de Kar, beduidend verminderend de tijd die wordt vereist om grote regelreeksen te beheren.

_AC-13916_

#### Voorvertoning in de mobiele weergave voor het stapelen van inhoud

Met de voorvertoningsfunctie voor trapsgewijze voorvertoningen van mobiele apparaten die in de browser worden gesimuleerd, kunnen voorvertoningen van mobiele apparaten nu op de juiste wijze worden weergegeven, zodat u kunt zien hoe een testupdate op een mobiel apparaat wordt weergegeven.

_ACP2E-3397 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/520f9e30)_

### Braintree

#### Uitdrukkelijke afhandeling

- **Bevorderingsaanbiedingen in Google Pay express loonblad**

  Het Google Pay Express Pay Sheet ondersteunt nu promotie- en aanbiedingscodes. Klanten kunnen aanbiedingen voor Commerce-winkelwagentjes rechtstreeks op het Google Pay-blad toepassen, bekijken en verwijderen, zodat klanten met een expresse-out dezelfde kortingen en stimulansen krijgen als standaard afhandelingsstromen.

  _BUNDLE-3476_

- **Bevorderingsaanbiedingen in Apple Pay express loonblad**

  Het Apple Pay Express Pay Sheet ondersteunt nu promotie- en aanbiedingscodes. Klanten kunnen een coupon rechtstreeks op het Apple Pay-blad toepassen. Gebruikers die expressies afhandelen, profiteren dus van dezelfde kortingen en campagnes als standaardafhandelingsstromen.

  _BUNDLE-3477_

- **Apple betaalt op Chrome en Firefox**

  Apple Pay kan nu worden gebruikt op Chrome en Firefox, niet alleen op Safari. Wanneer Apple Pay Express is ingeschakeld, zijn Apple Pay-knoppen beschikbaar op ondersteunde winkellocaties en kunnen klanten de betaling voltooien door een code te scannen met hun iPhone.

  _BUNDLE-3478_

- **server-kant het verschepen callback voor Uitdrukkelijke PayPal**

  De PayPal Express-callback voor verzending is verplaatst van client naar server. Dit biedt dynamische verzendmethoden, real-time kostenberekeningen en nauwkeurige details op cartniveau rechtstreeks in het PayPal-modaal. Hierdoor wordt de betrouwbaarheid verbeterd en wordt de basis gelegd voor toekomstige functies, zoals de ondersteuning voor contactmodules, app-switch-stromen en Venmo Express.

  _BUNDLE-3479_

- **PayPal Module van het Contact voor de handel van de V.S. Uitdrukkelijke controle**

  Er is een nieuwe PayPal-contactmodule geïntroduceerd voor Amerikaanse handelaren. Als deze optie is ingeschakeld, kunnen kopers met PayPal Express het e-mailadres en het telefoonnummer dat door de handelaar wordt gedeeld, direct in het PayPal-modaal bekijken en bijwerken tijdens expressies (PDP, mini-cart, winkelwagentje, uitcheckexpress). De gekozen contactgegevens worden vervolgens opgeslagen op de Commerce-bestelling.

  _BUNDLE-3480_

#### Betalingsmethoden

- **ELO kaarttype steun voor Braintree betalingen**

  Ondersteuning voor het type ELO-kaart toegevoegd aan Braintree Payments. Beheerders kunnen nu ELO inschakelen in de creditcardconfiguratie en klanten kunnen met succes bestellingen plaatsen met ELO-kaarten bij het afrekenen, zodat transacties probleemloos verlopen via Braintree.

  _BUNDLE-3464_

- **BLIK lokale betalingsmethode voor Poolse kopers**

  BLIK toegevoegd als een nieuwe lokale betalingsmethode voor Poolse kopers. Dit maakt veilige, op banken gebaseerde betalingen van BLIK mogelijk binnen de bestaande stroom van Braintree Local Payment Methods (LPM), waardoor het betaalgemak en de conversie voor klanten in Polen worden verbeterd.

  _BUNDLE-3481_

- **Betalen op Factuur — nieuwe BNPL betalingsmethode voor Duitsland**

  Er is een nieuwe lokale betalingsmethode toegevoegd, Betalen op factuur voor Duitse kopers. Betalen op factuur is een optie Nu kopen, Later betalen (BNPL) met PayPal en Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) waarmee klanten goederen als eerste kunnen ontvangen en de factuur binnen 30 dagen kunnen betalen, zonder dat ze een PayPal-rekening nodig hebben. Omdat het geen directe betaling is, wordt de afhandeling van bestellingen gedreven door een webhaak aan de serverzijde van PayPal.

  _BUNDLE-3475_

#### Kaart vauleren

- **het Wisselen Google Betalen via het rekeningsgebied**

  Klanten kunnen hun Google Pay-kaarten nu via het accountgebied bewaren wanneer Google Pay Vault in Braintree is ingeschakeld. Geëxtraheerde kaarten worden weergegeven onder opgeslagen betalingsmethoden, kunnen worden gebruikt voor toekomstige aankopen bij afhandeling en kunnen door de klant worden verwijderd. Dit breidt de factureringsondersteuning uit van kaarten en PayPal naar Google Pay.

  _BUNDLE-3459_

- **in real time rekeningsupdater (RTAU) voor Braintree in kluizen**

  De functie Real-Time Account Updater (RTAU) die aan Braintree is toegevoegd, zorgt ervoor dat gearchiveerde Visa, Mastercard en Discover Card-gegevens automatisch worden bijgewerkt wanneer kaarten verlopen of worden vervangen. Hierdoor worden mislukte betalingen geminimaliseerd, blijft de Commerce Vault actueel en worden niet-ondersteunde typen (prepaid, Apple Pay, Google Pay) zonder fouten overgeslagen.

  _BUNDLE-3462_

#### Beheerprogramma&#39;s

- **orde van Commerce van de Verbinding aan portaal van Braintree**

  Er wordt nu een Braintree Portal-koppeling toegevoegd aan de ordergegevens in Commerce Admin. Als u op de koppeling klikt, wordt de bijbehorende transactie geopend in de Braintree Portal (op een nieuw tabblad) met de Merchant ID en de Transactie ID van de Commerce-order. Dit staat directe kruisverwijzing toe zonder het registreren in beide systemen afzonderlijk.

  _BUNDLE-3461_

#### Beveiliging en compatibiliteit

- **de update van het het veiligheidsbeleid van de integratieinhoud van de Kardinaal voor Veilige 3-D**

  Het inhoudsbeveiligingsbeleid (CSP) is bijgewerkt ter ondersteuning van de nieuwste vereisten voor integratie in kardinaal (3-D Secure). Dit zorgt ervoor dat alle op kardinaal-ontvangen manuscripten, iframes, en verwante middelen die tijdens 3-D Veilige stromen worden gebruikt door browser CSP worden toegestaan, verhinderend geblokkeerde verzoeken en gebroken uitdaging of controleervaringen.

  _BUNDLE-3485_

- **Braintree betalings uitbreiding PHP 8.5 verenigbaarheid**

  De Braintree payment extension is bijgewerkt om de PHP 8.5 runtime te ondersteunen, terwijl de compatibiliteit met PHP 8.4 behouden blijft.

  _BUNDLE-3493_

### Platform en infrastructuur

#### Ondersteuning voor OpenSearch 3.x

Adobe Commerce 2.4.9-beta1 is volledig compatibel met OpenSearch 3.x. Deze update stelt handelaren in staat te profiteren van verbeterde prestaties, beveiliging en ondersteuning op lange termijn, terwijl de compatibiliteit met OpenSearch 2.x behouden blijft.

_AC-11846_

#### Volledige ondersteuning voor Valkey 8.x

Adobe Commerce 2.4.9-beta1 biedt uitgebreide ondersteuning voor Valkey 8.x als een Redis-compatibele cache-backend, inclusief volledige CLI-bevelpariteit met Redis. De configuratieopties voor beheer en cloud zijn bijgewerkt voor naadloze installatie van Valkey. Deze ondersteuning wordt aangestuurd door wijzigingen aan het einde van de ondersteuning en licenties van Redis 7.2, waardoor handelaren een betrouwbaar, volledig ondersteund alternatief krijgen voor Redis in Commerce-releaselijnen 2.4.5 tot en met 2.4.9-beta1.

_AC-14103, AC-14604_

#### Apache ActiveMQ Artemis-ondersteuning vervangt RabbitMQ

Toegevoegde ondersteuning voor Apache ActiveMQ Artemis als strategisch alternatief voor RabbitMQ, aangedreven door de risico&#39;s aan het einde van de ondersteuning in verband met RabbitMQ 4. ActiveMQ-artemis wordt nu volledig ondersteund in Commerce-releaselijnen 2.4.6 tot en met 2.4.9-bèta1, inclusief Adobe Commerce Cloud met AWS ActiveMQ voor cloudnative implementaties, en ondersteunt STOMP-configuratie voor gebruikers in de wachtrij en uitgevers. Bestaande RabbitMQ 4-installaties blijven compatibel voor verkopers die liever hun huidige service voor berichtwachtrij blijven gebruiken.

_AC-14558_

### PHP en Composer

#### Compatibiliteit met PHP 8.5

Vanaf Adobe Commerce 2.4.9 bèta1 is het platform volledig compatibel met PHP 8.5, terwijl het ondersteuning voor PHP 8.4 behoudt en PHP 8.3 toestaat voor upgrade-scenario&#39;s. Dit werk moderniseert de kerncode, afhankelijkheden en tools, zodat handelaren veilig kunnen overstappen naar nieuwere PHP versies voor het einde van de ondersteuning voor PHP 8.4, waardoor de PCI-compatibiliteit en de gezondheid van het platform op lange termijn behouden blijven.

_AC-15615_

#### Ondersteuning voor PHP 8.2 is verwijderd

Vanaf Adobe Commerce 2.4.9 bèta1 wordt PHP 8.2 niet meer ondersteund. Het platform is nu gericht op PHP 8.3 en hoger, met kerncode, afhankelijkheden en tools bijgewerkt om op een schone en betrouwbare manier te werken met PHP 8.4 en 8.5.

_AC-15758_

#### Compatibiliteit van Composer 2.9 gecontroleerd

Adobe Commerce 2.4.9-beta1 is volledig compatibel met Composer 2.x, inclusief Composer 2.9. Deze groepering bewaart achterwaartse verenigbaarheid en verzekert een stabiele bouwstijl en plaatsingservaring voor handelaren en ontwikkelaars die de recentste versies Composer gebruiken.

_AC-14481_

### Kader

#### JWT-frameworkbeveiliging en compatibiliteitsupdate

Als onderdeel van ononderbroken platformveiligheidscontrole, is de web-token JWT kaderafhankelijkheid geëvalueerd en bijgewerkt naar de recentste belangrijke versie, die toekomstige verenigbaarheid en sterke veiligheidsnormen voor symbolisch-gebaseerde authentificatie over de integratie van Commerce verzekert. Bestaande functionaliteit blijft volledig behouden.

_AC-13209 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/2bac8114) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/09b36ebb) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/33b81f28)_

#### Adobe Commerce Functional Testing Framework bijgewerkt naar Symfony LTS-afhankelijkheden

Het Adobe Commerce Functional Testing Framework (MFTF) is bijgewerkt en gebruikt nu de nieuwste Symfony LTS-afhankelijkheden, waaronder symfony/config, zoals vereist door de web-token/jwt-framework-upgrade. Dit verhelpt eerdere afhankelijkheidsconflicten en zorgt voor een stabiele, ondersteunde stapel voor functionele tests.

_AC-13244_

#### Native PHP OAuth-functies vervangen bibliotheek van derden

De `carlos-mg89/oauth` -bibliotheek van derden is vervangen door native PHP OAuth-functies, die de beveiliging verbeteren, externe afhankelijkheden verminderen en de stabiliteit van het platform verbeteren.

_AC-14075 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7b8064f7)_

#### De component Symfony Cache vervangt Zend_Cache

Vanaf Adobe Commerce 2.4.9-beta1 is de afgekeurde component Zend_Cache vervangen door de component Symfony Cache. Deze update verbetert de prestaties en het onderhoud van de cache en zorgt voor compatibiliteit op lange termijn met PHP 8.x en toekomstige platform updates. Bestaande cache-backends en opdrachten voor cachebeheer blijven volledig ondersteund, zonder wijzigingen die vereist zijn voor de huidige integratie.

_AC-15823_

#### WYSIWYG-editor migreerde van TinyMCE naar HugeRTE

Wegens het eind van steun voor TinyMCE 5 en 6 en het verlenen van vergunningen onverenigbaarheden met TinyMCE 7, is de redacteur van Adobe Commerce WYSIWYG gemigreerd aan de open-bron [ ](https://hugerte.org/) redacteur HugeRTE. Deze migratie zorgt ervoor dat Adobe Commerce compatibel blijft met open-sourcinglicenties, bekende TinyMCE 6-kwetsbaarheden voorkomt en een moderne, ondersteunde bewerkingservaring biedt voor handelaren en ontwikkelaars.

_AC-14568_

#### Native MVC-implementatie vervangt Laminas MVC

Adobe Commerce heeft een native MVC-implementatie geïntroduceerd, die de verouderde Laminas MVC vervangt, om te zorgen voor compatibiliteit en stabiliteit op lange termijn boven PHP 8.5. Deze wijziging versterkt de prestaties, vermindert de externe afhankelijkheden en biedt een meer toekomstbestendige basis voor Commerce.

_AC-15160_

#### Officiële Symfony 7.4 LTS-ondersteuning

Als onderdeel van de Adobe Commerce 2.4.9-bèta1-platformupdates zijn alle Symfony-afhankelijkheden bijgewerkt naar de nieuwste Symfony LTS 7.4-versies. Alle aangepaste klassen die de kernklassen van Symfony uitbreiden, hebben typeverklaringen en methodehandtekeningen bijgewerkt die op de recentste vereisten van de Symfony worden gericht, verenigbaarheidskwesties verhinderen en een vlotte overgang aan de bijgewerkte kadercomponenten verzekeren.

_AC-15170 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c127d10b)_

#### Alle PHPUnit-afhankelijkheid bijgewerkt naar versie 3

De `allure-framework/allure-phpunit` afhankelijkheid is bijgewerkt naar belangrijke versie 3, die ondersteuning biedt voor PHP 8.4 en PHP 8.5 en de Allure-based testrapportstack moderniseert. De native afhankelijkheid die eerder werd vereist door oudere versies van Alure PHPUnit is verwijderd, waardoor installatie en onderhoud eenvoudiger zijn geworden.

_AC-14548 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/87b8b34e)_

#### New Relic-rapportage bijgewerkt naar NerdGraph API

De New Relic-rapporteringsmodule is bijgewerkt ter ondersteuning van de NerdGraph (GraphQL)-API voor het bijhouden van wijzigingen in New Relic en met behoud van de bestaande integratie van de REST v2-implementatiemarkering. De verandering levert rijkere plaatsingsmeta-gegevens, regionale eindpuntsteun (V.S. en EU), en configureerbaarheid door montages Admin zonder bestaande montages te breken.

_AC-15461_

#### JavaScript-bibliotheekupdates

- **Chart.js die aan versie 4.5.0 wordt bijgewerkt**

  De grafiekbibliotheek Chart.js van JavaScript aan versie 4.5.0 werd bijgewerkt om grafiekteruggevende prestaties te verbeteren, visuele mogelijkheden te verbeteren, en veiligheidskwetsbaarheid in het admin dashboard en rapporteringsmodules te richten.

  _AC-14304, AC-15133 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/768b4442), [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/657f983e)_

- **van de gebruiks dossier uploadt bibliotheek die aan versie 4.13.4 wordt bijgewerkt**

  De Uppy-bibliotheek voor het uploaden van bestanden is bijgewerkt naar versie 4.13.4 om de mogelijkheden voor het uploaden van bestanden te verbeteren, gebruikerservaring te verbeteren en beveiligingskwetsbaarheden in het verwerken van bestanden te verhelpen via de Adobe Commerce-beheerinterface en frontend-componenten.

  _AC-14307 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/eb491c05)_

- **jQuery bevestigt bibliotheek bevorderd aan versie 1.21.0**

  De jQuery Validate-bibliotheek is bijgewerkt naar versie 1.21.0 om de validatiemogelijkheden van formulieren te verbeteren, gebruikerservaring te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-formulieren in zowel de beheerdersinterface als de frontendinterfaces.

  _AC-14403 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

- **jQuery UI bibliotheek bevorderd aan versie 1.14.1**

  De jQuery-gebruikersinterfacebibliotheek is bijgewerkt naar versie 1.14.1 om de widgets van de gebruikersinterface te verbeteren, de toegankelijkheid te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-admin- en frontendinterfacecomponenten.

  _AC-14417 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/77c589a6)_

- **Less.js CSS preprocessor die aan versie 4.2.2 wordt bevorderd**

  De CSS-preprocessor van Minder.js is bijgewerkt naar versie 4.2.2 om de prestaties van de CSS-compilatie te verbeteren, de syntaxisondersteuning te verbeteren en het proces voor het maken van thema&#39;s te moderniseren voor alle Adobe Commerce-thema&#39;s frontend en admin.

  _AC-14418 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

- **de bibliotheek van de Tijdzone van het Moment die aan versie 0.5.43 wordt bevorderd**

  De tijdzonebibliotheek van het Moment (`moment-timezone-with-data.js`) aan versie 0.5.43 werd bijgewerkt om timezone behandelingsmogelijkheden te verbeteren, tijdzonegegevens met de recentste veranderingen van het Gegevensbestand van de Tijdzone van IANA bij te werken het Gegevensbestand van de Tijdzone, en datum en tijdverwerkingsnauwkeurigheid over alle internationale en multi-timezoneverrichtingen van Adobe Commerce te verbeteren.

  _AC-14419 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

- **Underscore.js nutsbibliotheek die aan versie 1.13.7 wordt bevorderd**

  De Underscore.js-hulpprogrammabibliotheek is bijgewerkt naar versie 1.13.7 om de functionaliteit van JavaScript-programmering te verbeteren, de prestaties van gegevensmanipulatie te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-componenten voor frontend- en beheerinterface.

  _AC-14420 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

### Beveiliging

#### CAPTCHA-validatie is nu verplicht voor REST- en GraphQL-API&#39;s

Wanneer CAPTCHA (of reCAPTCHA) is ingeschakeld voor het formulier Account maken, wordt dezelfde CAPTCHA-validatie nu afgedwongen voor het maken van een klantenaccount via REST- en GraphQL-API&#39;s.

_AC-16245_

#### Verbeterde prestaties van async-/bulkverzoeken

Deze correctie verhelpt prestatievermindering in bulksgewijs asynchrone web API-eindpunten die zijn geïntroduceerd na de beveiligingspatch van APSB25-08, waardoor de verwachte uitvoeringstijden worden hersteld.

_AC-14078 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/9a7352b7)_

#### Vereenvoudigde configuratie met twee verificatiefactoren

Admin-gebruikers moeten nu slechts een van de door de handelaar ingeschakelde 2FA-providers (bijvoorbeeld Google Authenticator of U2F) configureren voor toegang tot het beheerpaneel. Extra toegelaten leveranciers kunnen later worden gevormd zoals nodig. Eerder, toen veelvoudige 2FA leveranciers werden toegelaten, werd elke gebruiker Admin vereist om alle toegelaten leveranciers te vormen alvorens zij konden binnen ondertekenen, die tot wrijving voor gebruikers leiden die geen toegang tot alle factoren hadden.

_AC-8253 - [ GitHub codebijdrage ](https://github.com/magento/security-package/commit/71e7936b)_

### Verzending

#### USPS-integratie migreren naar RESTful USPS API&#39;s

Adobe Commerce heeft zijn USPS-integratie gemigreerd naar de nieuwe RESTful USPS-API&#39;s om te voldoen aan de aangekondigde pensionering van de oude Web Tools API&#39;s van USPS.

Belangrijke verbeteringen:

- Ondersteuning voor dubbele API: Admin-gebruikers kunnen nu kiezen tussen de verouderde API voor webgereedschappen en de nieuwe RESTful-API voor USPS via configuratie-instellingen.
- Upgrade van verificatie: gebruikt OAuth 2.0 voor beveiligde API-toegang.
- Verbeterde gegevensindeling: gebruikt JSON in plaats van XML voor betere, efficiëntere communicatie.
- Nieuwe beheervelden:
   - URL van de REST van de gateway (die op wijze wordt gebaseerd: Ontwikkeling of Levend)
   - Client-id en geheim
   - Accounttype, accountnummer
   - CRID, MID, identificatiecode van de legger
   - AES/ITN voor internationale overbrengingen
   - REST-specifieke toegestane verzendmethoden

Deze migratie zorgt ervoor dat Adobe Commerce blijft voldoen aan de USPS-standaarden, verbetert de betrouwbaarheid van het systeem en maakt het mogelijk om voortaan proefversies te maken van de verzendintegratie voor handelaren.

_AC-13257_

#### DHL-integratie migreren naar MyDHL RESTful-API&#39;s

De ingebouwde DHL-scheepvaartintegratie ondersteunt nu MyDHL RESTful API&#39;s, terwijl de compatibiliteit met de oudere DHL Express XML-API behouden blijft. Handelaars kunnen kiezen welke DHL API in Admin te gebruiken, die van de moderne mogelijkheden van de REST profiteren zonder bestaande op XML-Gebaseerde montages te breken.

_AC-13258_
