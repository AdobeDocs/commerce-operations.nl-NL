---
source-git-commit: b829cf3685457f9f9ad3dfca2d294b6167accb82
workflow-type: tm+mt
source-wordcount: '3479'
ht-degree: 0%

---
# Adobe Commerce-hooglichten (v2.4.9)

## Hooglichten in v2.4.9

De volgende markeringen zijn van toepassing op de Adobe Commerce 2.4.9-release.

### Wijzigingen REST API

#### REST API-productgalerie, overervingscontrole op archiefweergaveniveau

Wanneer een product via REST API in een opslagbereik wordt bijgewerkt, kunnen productafbeeldingen en video&#39;s geen wijzigingen van het algemene bereik overnemen wanneer `media_gallery_entries` wordt weggelaten uit de payload of is ingesteld op `NULL` . Het is nu ook mogelijk om via REST API de bereikovererving voor productafbeeldingen en -video te herstellen door het corresponderende veld in te stellen op `NULL` .

Wanneer u producten bijwerkt via REST API op het niveau van de winkelweergave:

- Als u `media_gallery_entries` weglaat of instelt op NULL, blijft de overerving van de standaard/algemene galerie behouden.
- Als u de overerving voor specifieke galeriekenmerken (zoals `label` , `position` , `disabled` , `video_title` , `video_description` ) wilt herstellen, stelt u die velden in op NULL in de array `media_gallery_entries` .

Deze wijziging zorgt ervoor dat de opslagweergaven de standaardgaleriewaarden eenvoudig kunnen behouden of herstellen, verwarring verminderen en het galeriebeheer consistenter maken.

_ACP2E-4358 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Wijzigingen in GraphQL API

#### `clearCart` GraphQL-mutatie is nu beschikbaar in Magento Open Source

De [&#x200B; clearCart &#x200B;](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/) mutatie van GraphQL is nu beschikbaar aan alle gebruikers van Magento Open Source. Voorheen was deze mutatie alleen toegankelijk in Adobe Commerce.

_AC-16683 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/4449d914)_

#### Fouten in de beschrijving van de GraphQL-mutatie van `applyGiftCardToCart`

Verbeterde foutafhandeling voor de mutatie `applyGiftCardToCart` . De mutatie retourneert nu specifieke foutberichten voor gevallen zoals verlopen of cadeaukaarten met een nulbalans, waardoor de winkelervaring wordt verbeterd. Bovendien voorkomt de backend het toepassen van extra cadeaukaarten op bestellingen die al gratis zijn.

_LYNX-787_

#### Nieuwe `clearWishlist` GraphQL-mutatie verwijdert alle wenslijstonderdelen tegelijk

Toegevoegd a `clearWishlist` mutatie die alle punten uit een wenslijst in één enkele vraag verwijdert.

_LYNX-790_

#### Nieuwe `exchangeExternalCustomerToken` GraphQL-mutatie voor verificatie op basis van integratie

Introduceerde een nieuwe `exchangeExternalCustomerToken` GraphQL-mutatie die gebruikers via een integratietoken verifieert en zowel het klanttoken als de bijbehorende klantgegevens retourneert.

_LYNX-815_


#### Nieuwe GraphQL-query&#39;s retourneren toegepaste klantgroep, segmenten en kaartregel-id&#39;s

Nieuwe GraphQL-query&#39;s retourneren de gecodeerde `uid` code van de toegepaste klantengroep, klantsegmenten en winkelregels.

_LYNX-867_

#### Cadeauopties worden automatisch gewist wanneer het winkelwagentje wordt leeggemaakt

Correctie van een probleem waarbij cadeauopties op een leeg winkelwagentje bleven nadat alle objecten waren verwijderd. Cadeauopties worden nu automatisch gewist wanneer het winkelwagentje wordt geleegd, overeenkomstig het bestaande gedrag voor coupons.

_LYNX-786_

#### Cadeauopties worden consistent samengevoegd wanneer gasten- en klantenkaarten worden gecombineerd

Verbeterde afhandeling van geschenkopties tijdens het samenvoegen van winkelwagentjes voor een consistentere gebruikerservaring. Cadeauopties volgen nu een geprioriteerde samenvoegingslogica, die ongewenste overschrijvingen voorkomt wanneer een gastgebruiker zich aanmeldt en zijn winkelwagentje wordt samengevoegd met een bestaande klantenkar.

_LYNX-788_

#### Nieuw veld `grand_total_excl_tax` in GraphQL `OrderTotal` -reactie

Er is een nieuw veld, `OrderTotal.grand_total_excl_tax` , toegevoegd aan het GraphQL-orderantwoord. In dit veld wordt het totale bedrag van de order exclusief belasting weergegeven, waardoor het gemakkelijker wordt om rechtstreeks via de API toegang te krijgen tot totalen die exclusief belasting zijn.

Voordelen:

- U kunt eenvoudig het totaal van de kleinste bedragen, exclusief belastingen, ophalen voor elke bestelling via GraphQL.
- Vereenvoudigt integratie met externe systemen die uitsluitend belastingtotalen vereisen.
- Hiermee vermindert u de behoefte aan aangepaste berekeningen op de client.

_LYNX-892_

#### Historische orders bevatten details voor producten die nu uit voorraad zijn

Historische orders geven nu volledige productdetails weer voor lijnitems, zelfs nadat het product uit voorraad is verdwenen, zodat klanten en handelaren een volledig overzicht behouden van wat is aangeschaft.

_LYNX-913_

#### reCAPTCHA-validatie toegevoegd aan GraphQL-mutaties `updateCustomer` , `updateCustomerV2` en `contactUs`

Wanneer reCAPTCHA is ingeschakeld voor de corresponderende storefront-formulieren, dwingen de GraphQL-mutaties `updateCustomer` , `updateCustomerV2` en `contactUs` nu dezelfde validatie af, zodat automatisch misbruik via de API wordt voorkomen.

_LYNX-941_

#### reCAPTCHA-validatie toegevoegd aan de `applyCouponsToCart` GraphQL-mutatie

Wanneer reCAPTCHA is ingeschakeld voor het couponformulier, dwingt de `applyCouponsToCart` GraphQL-mutatie nu dezelfde validatie af, waardoor wordt voorkomen dat de waardeboncode via de API wordt opgesomd.

_LYNX-942_

#### B2B GraphQL API `customer_id` -veld hersteld en volledig ondersteund

Het veld `customer_id` in de B2B GraphQL API wordt hersteld en retourneert nu de juiste waarde in bedrijfsbeheerquery&#39;s en -mutaties. Eerder werd het veld vervangen en geretourneerd `null` , waardoor het nut voor B2B-integratie werd beperkt.

_LYNX-955_

### Gebruikersinterface van beheerder

#### Menu Handelingen voor raster met catalogusprijsregels

Het **net van de Regels van de Prijs van de Catalogus** in Commerce Admin omvat nu een **3&rbrace; menu van Acties &lbrace;, toestaand verkopers om, veelvoudige regels te activeren te deactiveren of te schrappen meteen.** Dit brengt het beheer van de catalogusprijsregel in lijn met de bestaande bulkacties beschikbaar voor **Regels van de Prijs van de Kar**, beduidend verminderend de tijd die wordt vereist om grote regelreeksen te beheren.

_AC-13916_

#### Voorvertoning in de mobiele weergave voor het stapelen van inhoud

Met de voorvertoningsfunctie voor trapsgewijze voorvertoningen van mobiele apparaten die in de browser worden gesimuleerd, worden voorvertoningen van mobiele apparaten nu op de juiste wijze weergegeven, zodat verkopers kunnen zien hoe een gefaseerde update op een mobiel apparaat wordt weergegeven voordat het apparaat actief wordt.

_ACP2E-3397 - [&#x200B; de codebijdrage van GitHub &#x200B;](https://github.com/magento/magento2/commit/520f9e30)_

#### Nieuwe beheerdersconfiguratiecontroles gast en de fusiemontages van de klantenkar bij login

Handelaars kunnen nu kiezen hoe winkelwagentjes worden samengevoegd wanneer een gast zich aanmeldt en al een klantenkar heeft:

- **Prioriteit van de Gast** - gebruik het aantal van de gastkar.
- **Prioriteit van de Klant** — Gebruik het aantal van de klantenkar.
- **de Hoeveelheden van de Fusie** (gebrek) — som beide hoeveelheden.

Vorm dit gedrag in **Opslag** > **Configuratie** > **Verkoop** > **Controle**, onder **de Voorkeur van de Fusie van de Kunst**. Het plaatsen is op alle producttypes van toepassing, die handelaars volledige controle over geven hoe de gast en de klantenwortels bij login worden gecombineerd.

_LYNX-889_

### Braintree

#### Uitdrukkelijke afhandeling

- **Bevorderingsaanbiedingen in Google Pay express loonblad**

  De betalingsbalans van Google Pay biedt nu ondersteuning voor promotie- en aanbiedingscodes. Klanten kunnen Commerce-winkelaanbiedingen rechtstreeks op het Pay-blad van Google toepassen, bekijken en verwijderen, zodat klanten met een exprestransactie dezelfde kortingen en stimulansen krijgen als klanten met een standaardbetalingssysteem.

  _BUNDLE-3476_

- **Bevorderingsaanbiedingen in Apple Pay express loonblad**

  De betalingsbalans van Apple Pay biedt nu ondersteuning voor promotie- en aanbiedingscodes. Klanten kunnen een coupon rechtstreeks op het Apple Pay-blad toepassen. Gebruikers die expressies afhandelen, profiteren dus van dezelfde kortingen en campagnes als standaardafhandelingsstromen.

  _BUNDLE-3477_

- **Apple betaalt op Chrome en Firefox**

  Apple Pay kan nu worden gebruikt op Chrome en Firefox, niet alleen op Safari. Wanneer Apple Pay Express is ingeschakeld, zijn de Apple Pay-knoppen beschikbaar op de pagina&#39;s PDP, mini-cart, winkelwagentje en kassa en kunnen klanten de betaling voltooien door een code met hun iPhone te scannen.

  _BUNDLE-3478_

- **server-kant het verschepen callback voor Uitdrukkelijke PayPal**

  De PayPal Express-callback voor verzending is verplaatst van client naar server. Dit biedt dynamische verzendmethoden, real-time kostenberekeningen en nauwkeurige details op cartniveau rechtstreeks in het PayPal-modaal. Hierdoor wordt de betrouwbaarheid verbeterd en wordt de basis gelegd voor toekomstige functies, zoals de ondersteuning voor contactmodules, app-switch-stromen en Venmo Express.

  _BUNDLE-3479_

- **PayPal Module van het Contact voor de handel van de V.S. Uitdrukkelijke controle**

  Er is een nieuwe PayPal-contactmodule geïntroduceerd voor Amerikaanse handelaren. Als deze optie is ingeschakeld, kunnen kopers met PayPal Express het e-mailadres en het telefoonnummer dat door de handelaar wordt gedeeld, direct in het PayPal-modaal bekijken en bijwerken tijdens expressies (PDP, mini-cart, winkelwagentje, uitcheckexpress). De gekozen contactgegevens worden vervolgens opgeslagen op de Commerce-bestelling.

  _BUNDLE-3480_

#### Betalingsmethoden

- **ELO kaarttype steun voor Braintree betalingen**

  Extra ondersteuning voor het type ELO-kaart in Braintree Payments. Beheerders kunnen ELO inschakelen in de creditcardconfiguratie en klanten kunnen met ELO-kaarten betalen bij het afrekenen.

  _BUNDLE-3464_

- **BLIK lokale betalingsmethode voor Poolse kopers**

  BLIK toegevoegd als een nieuwe lokale betalingsmethode voor Poolse kopers. Dit maakt veilige, op banken gebaseerde betalingen van BLIK mogelijk binnen de bestaande stroom van Braintree Local Payment Methods (LPM), waardoor het betaalgemak en de conversie voor klanten in Polen worden verbeterd.

  _BUNDLE-3481_

- **Betalen op Factuur — nieuwe BNPL betalingsmethode voor Duitsland**

  [!DNL Pay Upon Invoice] toegevoegd als een nieuwe lokale betalingsmethode voor Duitse kopers. [!DNL Pay Upon Invoice] is een optie Nu kopen, Later betalen (BNPL), aangedreven door PayPal en Ratepay (&quot;Rechnungskauf mit Ratepay&quot;), waarmee klanten goederen als eerste kunnen ontvangen en de factuur binnen 30 dagen kunnen betalen zonder dat ze een PayPal-rekening nodig hebben. Omdat het geen directe betaling is, wordt de afhandeling van bestellingen gedreven door een webhaak aan de serverzijde van PayPal.

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

#### Snellere paginabelasting op multi-theme en multi-locale opslag na SRI hash opslagrefactor

SRI-hash-opslag genereert nu afzonderlijke bestanden per gebied, thema en landinstelling in plaats van één groot `sri-hashes.json` -bestand. Deze wijziging zorgt ervoor dat alleen het desbetreffende hash-bestand voor elke pagina wordt geladen, waardoor de laadtijden van de pagina worden verbeterd en het geheugengebruik in winkels met meerdere thema&#39;s of landinstellingen wordt verminderd.

_AC-16113 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/bc83cd2c)_

#### Compatibiliteit toevoegen met PHPUnit 12

De Adobe Commerce Composer-afhankelijkheid wordt bijgewerkt naar `phpunit/phpunit` 12.x. Alle tests worden bijgewerkt met het oog op compatibiliteit, betere beveiliging en betere afstemming op de nieuwste PHPUnit-functies. Deze upgrade zorgt ervoor dat Adobe Commerce gereed is voor toekomstige PHP- en PHPUnit-releases.

_AC-14808_

#### Compatibiliteit toevoegen met RabbitMQ 4.2

RabbitMQ 4.2 is nu een ondersteunde berichtbroker. Deze update is een kortetermijncompatibiliteitspad waarmee handelaren die op het AMQP-protocol vertrouwen, in februari 2026 RabbitMQ kunnen blijven gebruiken vóór RabbitMQ 4.1 end-of-support, zonder dat er een directe migratie naar STOMP plaatsvindt. Voor langetermijnimplementaties gebruikt u Apache ActiveMQ Artemis als de langetermijnvervanging voor RabbitMQ.

_AC-16117_

#### Apache ActiveMQ Artemis is de langetermijnvervanging van RabbitMQ

Apache ActiveMQ Artemis is de aanbevolen lange-termijn berichtenmakelaar voor Adobe Commerce, aangedreven door end risico&#39;s aan het einde van de ondersteuning in verband met RabbitMQ 4.1. ActiveMQ Artemis wordt volledig ondersteund in Commerce releaselijnen 2.4.6 tot en met 2.4.9. Op Adobe Commerce Cloud wordt het geleverd als AWS ActiveMQ voor implementaties in de cloud. Zowel gebruikers in de wachtrij als uitgevers kunnen worden geconfigureerd voor gebruik van STOMP.


De bestaande installaties RabbitMQ 4 blijven compatibel voor handelaren die verkiezen om hun huidige dienst van de berichtrij op de korte termijn te blijven gebruiken — zie [&#x200B; verenigbaarheid met RabbitMQ 4.2 &#x200B;](#add-compatibility-with-rabbitmq-42) hierboven toevoegen. Plan een migratie naar de Artemis van ActiveMQ voor steun op lange termijn.

_AC-14558_

#### Ondersteuning toevoegen voor Valkey 9.x

Adobe Commerce 2.4.9 breidt de ondersteuning voor Valkey uit als een Redis-compatibele cache-backend:

- **Valkey 9.x** — Uitgebreide steun die in Adobe Commerce 2.4.9 wordt geïntroduceerd, met inbegrip van volledige CLI bevelpariteit met Redis en bijgewerkte Admin en de configuratieopties van de Wolk voor naadloze opstelling. Dit werk wordt aangestuurd door Redis 7.2 veranderingen aan het einde van de support en licenties, waardoor handelaren een betrouwbaar, volledig ondersteund alternatief voor Redis krijgen.

_AC-14103, AC-14604, AC-16122_

#### Ondersteuning toevoegen voor OpenSearch 3.x

Adobe Commerce 2.4.9 is volledig compatibel met OpenSearch 3.x, met de nieuwste release van het type minor nu de aanbevolen zoekfunctie. Merchants profiteren van verbeterde prestaties, beveiliging en ondersteuning op lange termijn, terwijl de compatibiliteit met OpenSearch 2.x behouden blijft.

_AC-11846, AC-16403_

#### Ondersteuning toevoegen voor MariaDB 11.8 en 12.x

MariaDB 11.8 en 12.x worden nu gesteund gegevensbestandversies, toelatend verkopers om de recentste versies voor betere SQL prestaties en de stabiliteit van het platform op lange termijn aan te nemen.

_AC-16533_

### PHP en Composer

#### Compatibiliteit met PHP 8.5

Adobe Commerce 2.4.9 biedt nu ondersteuning voor PHP 8.5 en PHP 8.4, waardoor je winkel kan draaien op de nieuwste veilige en compatibele PHP versies. Alle basisfuncties, gebundelde extensies (waaronder Page Builder, B2B, Braintree en meer) en Adobe SaaS-services zijn compatibel met PHP 8.5.

- PHP 8.5 en 8.4 worden volledig ondersteund.
- PHP 8.3 is alleen toegestaan voor upgradedoeleinden (niet aanbevolen voor productie).
- Zorgt voor compatibiliteit met PCI en toekomstbestendige proefdrukken van uw Adobe Commerce-installatie.

_AC-15615_

#### Ondersteuning voor PHP 8.2 is verwijderd

Vanaf Adobe Commerce 2.4.9 wordt PHP 8.2 niet meer ondersteund. Het platform is nu gericht op PHP 8.3 en hoger, met kerncode, afhankelijkheden en tools bijgewerkt om op een schone en betrouwbare manier te werken met PHP 8.4 en 8.5.

_AC-15758_

#### Compatibiliteit van Composer 2.9 gecontroleerd

Adobe Commerce 2.4.9 is volledig compatibel met Composer 2.x, inclusief Composer 2.9. De achterwaartse verenigbaarheid met vroegere versies Composer 2.x wordt bewaard, die een stabiele bouwstijl en plaatsingservaring voor verkopers en ontwikkelaars verzekeren gebruikend de recentste versies Composer.

_AC-14481_

### Kader

#### JWT-frameworkbeveiliging en compatibiliteitsupdate

Als onderdeel van ononderbroken platformveiligheidscontrole, is de web-token JWT kaderafhankelijkheid geëvalueerd en bijgewerkt naar de recentste belangrijke versie, die toekomstige verenigbaarheid en sterke veiligheidsnormen voor symbolisch-gebaseerde authentificatie over de integratie van Commerce verzekert. Bestaande functionaliteit blijft volledig behouden.

_AC-13209 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/2bac8114) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/09b36ebb) - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/33b81f28)_

#### Adobe Commerce Functional Testing Framework bijgewerkt naar Symfony LTS-afhankelijkheden

Het Adobe Commerce Functional Testing Framework (MFTF) is bijgewerkt en gebruikt nu de nieuwste Symfony LTS-afhankelijkheden, waaronder symfony/config, zoals vereist door de web-token/jwt-framework-upgrade. Dit verhelpt eerdere afhankelijkheidsconflicten en zorgt voor een stabiele, ondersteunde stapel voor functionele tests.

_AC-13244_

#### Native PHP OAuth-functies vervangen bibliotheek van derden

De `carlos-mg89/oauth` -bibliotheek van derden is vervangen door native PHP OAuth-functies, die de beveiliging verbeteren, externe afhankelijkheden verminderen en de stabiliteit van het platform verbeteren.

_AC-14075 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/7b8064f7)_

#### De component Symfony Cache vervangt Zend_Cache

Vanaf Adobe Commerce 2.4.9 is de vervangen Zend_Cache-component vervangen door de Symfony Cache-component. Deze update verbetert de prestaties en het onderhoud van de cache en zorgt voor compatibiliteit op lange termijn met PHP 8.x en toekomstige platform updates. Bestaande cache-backends en opdrachten voor cachebeheer blijven volledig ondersteund, zonder wijzigingen die vereist zijn voor de huidige integratie.

_AC-15823_

#### WYSIWYG-editor migreerde van TinyMCE naar HugeRTE

Wegens het eind van steun voor TinyMCE 5 en 6 en het verlenen van vergunningen onverenigbaarheden met TinyMCE 7, is de redacteur van Adobe Commerce WYSIWYG gemigreerd aan de open-bron [&#x200B; &#x200B;](https://hugerte.org/) redacteur HugeRTE. Deze migratie zorgt ervoor dat Adobe Commerce compatibel blijft met open-sourcinglicenties, bekende TinyMCE 6-kwetsbaarheden voorkomt en een moderne, ondersteunde bewerkingservaring biedt voor handelaren en ontwikkelaars.

_AC-14568_

#### Native MVC-implementatie vervangt Laminas MVC

Adobe Commerce heeft een native MVC-implementatie geïntroduceerd, die de verouderde Laminas MVC vervangt, om te zorgen voor compatibiliteit en stabiliteit op lange termijn boven PHP 8.5. Deze wijziging versterkt de prestaties, vermindert de externe afhankelijkheden en biedt een meer toekomstbestendige basis voor Commerce.

_AC-15160_

#### Officiële Symfony 7.4 LTS-ondersteuning

Als onderdeel van de Adobe Commerce 2.4.9-platformupdates zijn alle Symfony-afhankelijkheden bijgewerkt naar de nieuwste Symfony LTS 7.4-versies. Alle aangepaste klassen die de kernklassen van Symfony uitbreiden, hebben typeverklaringen en methodehandtekeningen bijgewerkt die op de recentste vereisten van de Symfony worden gericht, verenigbaarheidskwesties verhinderen en een vlotte overgang aan de bijgewerkte kadercomponenten verzekeren.

_AC-15170 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/c127d10b)_

#### Alle PHPUnit-afhankelijkheid bijgewerkt naar versie 3

De `allure-framework/allure-phpunit` afhankelijkheid is bijgewerkt naar belangrijke versie 3, die ondersteuning biedt voor PHP 8.4 en PHP 8.5 en de Allure-based testrapportstack moderniseert. De native afhankelijkheid die eerder werd vereist door oudere versies van Alure PHPUnit is verwijderd, waardoor installatie en onderhoud eenvoudiger zijn geworden.

_AC-14548 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/87b8b34e)_

#### New Relic-rapportage bijgewerkt naar NerdGraph API

De New Relic-rapporteringsmodule is bijgewerkt ter ondersteuning van de NerdGraph (GraphQL)-API voor het bijhouden van wijzigingen in New Relic en met behoud van de bestaande integratie van de REST v2-implementatiemarkering. De verandering levert rijkere plaatsingsmeta-gegevens, regionale eindpuntsteun (V.S. en EU), en configureerbaarheid door montages Admin zonder bestaande montages te breken.

_AC-15461_

#### JavaScript-bibliotheekupdates

- **Chart.js die aan versie 4.5.0 wordt bijgewerkt**

  De grafiekbibliotheek Chart.js van JavaScript aan versie 4.5.0 werd bijgewerkt om grafiekteruggevende prestaties te verbeteren, visuele mogelijkheden te verbeteren, en veiligheidskwetsbaarheid in het admin dashboard en rapporteringsmodules te richten.

  _AC-14304, AC-15133 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/768b4442), [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/657f983e)_

- **van de gebruiks dossier uploadt bibliotheek die aan versie 4.13.4 wordt bijgewerkt**

  De Uppy-bibliotheek voor het uploaden van bestanden is bijgewerkt naar versie 4.13.4 om de mogelijkheden voor het uploaden van bestanden te verbeteren, gebruikerservaring te verbeteren en beveiligingskwetsbaarheden in het verwerken van bestanden te verhelpen via de Adobe Commerce-beheerinterface en frontend-componenten.

  _AC-14307 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/eb491c05)_

- **jQuery bevestigt bibliotheek bevorderd aan versie 1.21.0**

  De jQuery Validate-bibliotheek is bijgewerkt naar versie 1.21.0 om de validatiemogelijkheden van formulieren te verbeteren, gebruikerservaring te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-formulieren in zowel de beheerdersinterface als de frontendinterfaces.

  _AC-14403 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

- **jQuery UI bibliotheek bevorderd aan versie 1.14.1**

  De jQuery-gebruikersinterfacebibliotheek is bijgewerkt naar versie 1.14.1 om de widgets van de gebruikersinterface te verbeteren, de toegankelijkheid te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-admin- en frontendinterfacecomponenten.

  _AC-14417 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/77c589a6)_

- **Less.js CSS preprocessor die aan versie 4.2.2 wordt bevorderd**

  De CSS-preprocessor van Minder.js is bijgewerkt naar versie 4.2.2 om de prestaties van de CSS-compilatie te verbeteren, de syntaxisondersteuning te verbeteren en het proces voor het maken van thema&#39;s te moderniseren voor alle Adobe Commerce-thema&#39;s frontend en admin.

  _AC-14418 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

- **de bibliotheek van de Tijdzone van het Moment die aan versie 0.5.43 wordt bevorderd**

  De tijdzonebibliotheek van het Moment (`moment-timezone-with-data.js`) aan versie 0.5.43 werd bijgewerkt om timezone behandelingsmogelijkheden te verbeteren, tijdzonegegevens met de recentste veranderingen van het Gegevensbestand van de Tijdzone van IANA bij te werken het Gegevensbestand van de Tijdzone, en datum en tijdverwerkingsnauwkeurigheid over alle internationale en multi-timezoneverrichtingen van Adobe Commerce te verbeteren.

  _AC-14419 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

- **Underscore.js nutsbibliotheek die aan versie 1.13.7 wordt bevorderd**

  De Underscore.js-hulpprogrammabibliotheek is bijgewerkt naar versie 1.13.7 om de functionaliteit van JavaScript-programmering te verbeteren, de prestaties van gegevensmanipulatie te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-componenten voor frontend- en beheerinterface.

  _AC-14420 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

### Beveiliging

#### CAPTCHA-validatie is nu verplicht voor REST- en GraphQL-API&#39;s

Wanneer CAPTCHA (of reCAPTCHA) is ingeschakeld voor het formulier Account maken, wordt dezelfde CAPTCHA-validatie nu afgedwongen voor het maken van een klantenaccount via REST- en GraphQL-API&#39;s.

_AC-16245_

#### Verbeterde prestaties van async-/bulkverzoeken

Deze correctie verhelpt prestatievermindering in bulksgewijs asynchrone web API-eindpunten die zijn geïntroduceerd na de beveiligingspatch van APSB25-08, waardoor de verwachte uitvoeringstijden worden hersteld.

_AC-14078 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/9a7352b7)_

#### Vereenvoudigde configuratie met twee verificatiefactoren

Admin-gebruikers moeten nu slechts een van de door de handelaar ingeschakelde 2FA-providers (bijvoorbeeld Google Authenticator of U2F) configureren voor toegang tot het beheerpaneel. Extra toegelaten leveranciers kunnen later worden gevormd zoals nodig. Eerder, toen veelvoudige 2FA leveranciers werden toegelaten, werd elke gebruiker Admin vereist om alle hen te vormen alvorens zij konden binnen ondertekenen, die tot wrijving voor gebruikers leidde die geen toegang tot elke leverancier hadden.

_AC-8253 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento-commerce/security-package/commit/41e5a26bd36528cb6b1bdc27b249696a2c721779)_

### Verzending

#### USPS-integratie migreren naar RESTful USPS API&#39;s

Adobe Commerce heeft zijn USPS-integratie gemigreerd naar de nieuwe RESTful USPS-API&#39;s om te voldoen aan de aangekondigde pensionering van de oude Web Tools API&#39;s van USPS.

Belangrijke verbeteringen:

- Ondersteuning voor dubbele API: Admin-gebruikers kunnen nu via configuratie-instellingen kiezen tussen de verouderde Web Tools API en de nieuwe RESTful USPS API.
- Upgrade van verificatie: Gebruikt OAuth 2.0 voor veilige API toegang.
- Verbeterde gegevensindeling: Gebruikt JSON in plaats van XML voor schonere, efficiëntere communicatie.
- Nieuwe beheervelden:
   - URL van REST van de gateway (die op wijze wordt gebaseerd: Ontwikkeling of live)
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
