---
source-git-commit: 3a341190ff7ab69ad49721f78dfc90bc9ef24b20
workflow-type: tm+mt
source-wordcount: '2138'
ht-degree: 0%

---
# Magento Open Source-hooglichten (v2.4.9)

## Hooglichten in v2.4.9

De volgende markeringen zijn van toepassing op de Magento Open Source 2.4.9-release.

### API&#39;s

#### De mogelijkheid toevoegen om de overerving van productgalerie in de REST API te behouden bij het bijwerken van een product in de weergaveniveau van de winkel

Wanneer het product via REST API in een opslagbereik wordt bijgewerkt, kunnen productafbeeldingen en video&#39;s geen wijzigingen van het algemene bereik meer overnemen als de media_gallery_entries worden weggelaten uit de payload of op NULL zijn ingesteld om wijzigingen in de productgalerie in dat bereik te voorkomen. Bovendien is het nu mogelijk om bereikovererving voor productafbeeldingen en video te herstellen via REST API door het corresponderende veld in te stellen op NULL.

_ACP2E-4358 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Braintree

#### Google betalen via het accountgebied wordt automatisch berekend

In Adobe Commerce 2.4.9 kunnen klanten hun Google Pay-kaarten nu via het accountgebied bewaren wanneer Google Pay Vault in Braintree is ingeschakeld. Geëxtraheerde kaarten worden weergegeven onder opgeslagen betalingsmethoden, kunnen worden gebruikt voor toekomstige aankopen bij afhandeling en kunnen door de klant worden verwijderd. Dit breidt de factureringsondersteuning uit van kaarten en PayPal naar Google Pay.

_BUNDLE-3459_

#### Real Time Account Updater (RTAU)

De functie Real Time Account Updater (RTAU) in Adobe Commerce 2.4.9 voor Braintree zorgt ervoor dat gearchiveerde Visa, Mastercard en Discover card-gegevens automatisch worden bijgewerkt wanneer kaarten verlopen of worden vervangen. Hierdoor worden mislukte betalingen geminimaliseerd, blijft Magento Vault actueel en worden niet-ondersteunde typen (prepaid, Apple Pay, Google Pay) zonder fouten overgeslagen.

_BUNDLE-3462_

#### Ondersteuning voor ELO-kaarttypen voor Braintree Card Payments

In Adobe Commerce 2.4.9 is ondersteuning voor het type ELO-kaart toegevoegd aan Braintree Payments. Beheerders kunnen nu ELO inschakelen in de creditcardconfiguratie en klanten kunnen met succes bestellingen plaatsen met ELO-kaarten bij het afrekenen, zodat transacties probleemloos verlopen via Braintree.

_BUNDLE-3464_

#### Betalen op factuur

Voor Adobe Commerce 2.4.9 (extensie Braintree) is een nieuwe lokale betalingsmethode &quot;Betalen op factuur&quot; toegevoegd voor Duitse kopers. Betalen op factuur is een optie Nu kopen, Later betalen (BNPL) met PayPal + Ratepay (&quot;Rechnungskauf mit Ratepay&quot;) waarmee klanten goederen als eerste kunnen ontvangen en de factuur binnen 30 dagen kunnen betalen, zonder dat ze een PayPal-rekening nodig hebben. Omdat het geen directe betaling is, wordt de afhandeling van bestellingen gedreven door een webhaak aan de serverzijde van PayPal.

_BUNDLE-3475_

#### Aanbiedingen toevoegen aan de Google Pay Express PayPal-pagina

Voor de Braintree-extensie in Adobe Commerce 2.4.9 biedt de Google Pay Express Pay Sheet nu ondersteuning voor promo-/aanbiedingscodes. Klanten kunnen aanbiedingen voor Magento-winkelwagentjes rechtstreeks op het Google Pay-blad toepassen, bekijken en verwijderen, zodat klanten met een expresse-out dezelfde kortingen en stimulansen krijgen als standaard afhandelingsstromen.

_BUNDLE-3476_

#### Aanbiedingen toevoegen aan het Apple Pay Express-betalingsblad

Voor de Braintree-extensie in Adobe Commerce 2.4.9 biedt de Apple Pay Express Pay Sheet nu ondersteuning voor promo-/aanbiedingscodes. Klanten kunnen een coupon rechtstreeks op het Apple Pay-blad toepassen. Gebruikers die expressies afhandelen, profiteren dus van dezelfde kortingen en campagnes als standaardafhandelingsstromen.

_BUNDLE-3477_

#### Betalen met Apple Pay op Chrome en Firefox

Voor de Braintree-extensie in Adobe Commerce 2.4.9 kan Apple Pay nu worden gebruikt voor Chrome en Firefox, en niet alleen voor Safari. Wanneer Apple Pay Express is ingeschakeld, zijn Apple Pay-knoppen beschikbaar op ondersteunde winkellocaties en kunnen klanten de betaling voltooien door een code te scannen met hun iPhone.

_BUNDLE-3478_

#### Callback voor verzending op de server

Voor de Braintree-extensie in Adobe Commerce 2.4.9 is de PayPal Express-callback voor verzending verplaatst van client naar server. Dit biedt dynamische verzendmethoden, real-time kostenberekeningen en nauwkeurige details op cartniveau rechtstreeks in het PayPal-modaal. Hierdoor wordt de betrouwbaarheid verbeterd en wordt de basis gelegd voor toekomstige functies, zoals de ondersteuning voor contactmodules, app-switch-stromen en Venmo Express.

_BUNDLE-3479_

#### PayPal-contactmodule

Voor de Braintree-extensie in Adobe Commerce 2.4.9 wordt een nieuwe PayPal-contactmodule geïntroduceerd voor Amerikaanse handelaren. Als deze optie is ingeschakeld, kunnen kopers met PayPal Express het e-mailadres en het telefoonnummer dat door de handelaar wordt gedeeld, direct in het PayPal-modaal bekijken en bijwerken tijdens expressies (PDP, mini-cart, winkelwagentje, uitcheckexpress). De gekozen contactgegevens worden vervolgens opgeslagen op de Adobe Commerce-bestelling.

_BUNDLE-3480_

#### BLIK (lokale betalingsmethode)

Voor de uitbreiding van Braintree in Adobe Commerce 2.4.9 is BLIK toegevoegd als een nieuwe lokale betalingsmethode voor Poolse kopers. Dit maakt veilige, op banken gebaseerde betalingen van BLIK mogelijk binnen de bestaande stroom van Braintree Local Payment Methods (LPM), waardoor het betaalgemak en de conversie voor klanten in Polen worden verbeterd.

_BUNDLE-3481_

#### CSP-beleid voor updates van kardinale integratie

Voor de Braintree-extensie in Adobe Commerce 2.4.9 is het Content Security Policy (CSP) bijgewerkt ter ondersteuning van de nieuwste vereisten voor integratie in kardinaal (3-D Secure). Dit zorgt ervoor dat alle op kardinaal-ontvangen manuscripten, iframes, en verwante middelen die tijdens 3-D Veilige stromen worden gebruikt door browser CSP worden toegestaan, verhinderend geblokkeerde verzoeken en gebroken uitdaging/controleervaringen.

_BUNDLE-3485_

### Kader

#### De webtoken-/jwt-framebibliotheek is bijgewerkt naar de nieuwste hoofdversie

In het kader van het doorlopende veiligheidscontroleproces hebben we de meest recente grote release van het JWT-kader geëvalueerd om toekomstige compatibiliteit te waarborgen en sterke veiligheidsnormen te handhaven. Deze release heeft geen invloed op de bestaande functionaliteit.

_AC-13209 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/2bac8114) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/09b36ebb) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/33b81f28)_

#### [ Deel 2 ] - werk alle js bibliotheek en npm gebiedsdeel met recentste beschikbare versie bij

ondersteuning voor composer-versies was alleen beschikbaar voor versie 2.2.x van de composer. De ondersteuning is nu ook uitgebreid naar versie 2.4.x.

_AC-13792 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/19844aa0)_

#### Carlos-mg89/oauth vervangen door native functies van PHP

De carlos-mg89/oauth-bibliotheek van derden is vervangen door native PHP OAuth-functies om de beveiliging te verbeteren, externe afhankelijkheden te verminderen en de stabiliteit van het platform te verbeteren.

_AC-14075 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7b8064f7)_

#### Upgrade van jQuery/Uppy en upload bibliotheken met de nieuwste versie

De Uppy-bibliotheek voor het uploaden van bestanden is bijgewerkt naar versie 4.13.4 om de mogelijkheden voor het uploaden van bestanden te verbeteren, gebruikerservaring te verbeteren en beveiligingskwetsbaarheden in het verwerken van bestanden te verhelpen via de Adobe Commerce-beheerinterface en frontend-componenten.

_AC-14307 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/eb491c05)_

#### Upgrade de jQuery-validate-bibliotheek naar de nieuwste versie

De jQuery Validate-bibliotheek is bijgewerkt naar versie 1.21.0 om de validatiemogelijkheden van formulieren te verbeteren, gebruikerservaring te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-formulieren in zowel de beheerdersinterface als de frontendinterfaces.

_AC-14403 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

#### De jquery-ui-bibliotheek upgraden naar de nieuwste versie

De jQuery-gebruikersinterfacebibliotheek is bijgewerkt naar versie 1.14.1 om de widgets van de gebruikersinterface te verbeteren, de toegankelijkheid te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-admin- en frontendinterfacecomponenten.

_AC-14417 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/77c589a6)_

#### Minder.js-bibliotheek upgraden naar de nieuwste versie

De CSS-preprocessor van Minder.js is bijgewerkt naar versie 4.2.2 om de prestaties van de CSS-compilatie te verbeteren, de syntaxisondersteuning te verbeteren en het proces voor het maken van thema&#39;s te moderniseren voor alle Adobe Commerce-thema&#39;s frontend en admin.

_AC-14418 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

#### Upgrade de tijdzone-met-data.js-bibliotheek naar de nieuwste versie

De tijdzonebibliotheek van het Moment aan versie 0.5.43 werd bijgewerkt om timezone behandelingsmogelijkheden te verbeteren, tijdzonegegevens met recentste veranderingen van het Gegevensbestand van de Tijdzone van IANA bij te werken, en datum/tijd verwerkingsnauwkeurigheid over alle internationale en multi-timezoneverrichtingen van Adobe Commerce te verbeteren.

_AC-14419 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

#### Upgrade de bibliotheek underscore.js naar de nieuwste versie

De Underscore.js-hulpprogrammabibliotheek is bijgewerkt naar versie 1.13.7 om de functionaliteit van JavaScript-programmering te verbeteren, de prestaties van gegevensmanipulatie te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-componenten voor frontend- en beheerinterface.

_AC-14420 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

#### Alure-framework/allure-phpunit versie bijwerken naar 3 en native afhankelijkheid verwijderen in 2.4.9-alpha1

In Adobe Commerce 2.4.9 is de afhankelijkheid van allure-framework/allure-phpunit geüpgraded naar versie 3, die ondersteuning biedt voor PHP 8.4, PHP 8.5 en onze rapportstack op basis van Alure moderniseert. De native afhankelijkheid die voorheen werd vereist door oudere versies van Alure PHPUnit is waar van toepassing verwijderd, waardoor installatie en onderhoud eenvoudiger werden.

_AC-14548 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/87b8b34e)_

#### De afhankelijkheid van Chart.js van de verbetering aan de recentste versie

De afhankelijkheid van chart.js wordt bevorderd tot de recentste versie 4.5.0.

_AC-15133 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/657f983e)_

#### Voeg overheidssteun toe voor Symfony 7.4 LTS en PHP 8.5 in Adobe Commerce 2.4.9

Als onderdeel van de Adobe Commerce 2.4.9-platformupdates zijn alle Symfony-afhankelijkheden die door het magento/composer-pakket worden gebruikt, bijgewerkt naar de nieuwste Symfony LTS 7.4-versies. Hiermee wordt de Commerce Composer-gereedschappen uitgelijnd op de huidige Symfony LTS-regel en worden eerdere afhankelijkheidsbeperkingen met betrekking tot oudere Symfony-versies verwijderd. Bovendien hebben alle aangepaste klassen die de kernklassen van Symfony uitbreiden, typedeclaraties en methodehandtekeningen bijgewerkt die zijn afgestemd op de meest recente Symfony-vereisten voordat de upgrade naar Adobe Commerce 2.4.9 wordt uitgevoerd. Dit voorkomt compatibiliteitsproblemen en zorgt voor een soepele overgang naar de bijgewerkte frameonderdelen.

_AC-15170 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c127d10b)_

### GraphQL

#### Zorg ervoor dat clearCart GraphQL-mutatie beschikbaar is in Open Source

Met Adobe Commerce 2.4.9 is de clearCart GraphQL-mutatie nu beschikbaar voor alle Open Source-gebruikers. Voorheen was deze mutatie alleen beschikbaar in Adobe Commerce, maar ze maakt nu ook deel uit van de standaard GraphQL-kaartfunctionaliteit voor Open Source.
De documentatie voor de mutatie is bijgewerkt om de beschikbaarheid ervan in Open Source voor versie 2.4.9 weer te geven.
Zie [ clearCart de mutatiedocumentatie van GraphQL ](https://developer.adobe.com/commerce/webapi/graphql/schema/cart/mutations/clear-cart/).

_AC-16683 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/4449d914)_

#### [ AC-2.4.9 ] het samenvoegen van gast en klantenkloklogica die de Configuratie Admin gebruiken

Er is een nieuwe beheerdersconfiguratieoptie geïntroduceerd om te bepalen hoe gasten- en klantenkaarten worden samengevoegd wanneer een klant zich aanmeldt. Deze verbetering geeft u flexibiliteit om het kartsamenvoeggedrag te bepalen dat het best aan uw bedrijfsbehoeften past.

_LYNX-889_

#### [ AC-2.4.9 ] het krijgen van historische orden met uit voorraadproducten

Historische orders geven nu productdetails weer, zelfs als ze nu uit voorraad zijn.

_LYNX-913_

#### [ AC-2.4.9 ] [ Ce ] voert ReCaptcha voor ontbrekende mutaties van GraphQL uit

De validatie van ReCaptcha wordt toegevoegd aan updateCustomer, updateCustomerV2, en contactUs mutaties.

_LYNX-941_

### Overige

#### Captcha/reCAPTCHA werkt niet voor API/GraphQL

Wanneer CAPTCHA (of reCAPTCHA) in Adobe Commerce 2.4.9 is ingeschakeld voor het formulier Account maken, wordt nu dezelfde CAPTCHA-validatie afgedwongen voor het maken van een klantenaccount via REST- en GraphQL-API&#39;s.

_AC-16245 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/fd7f30ee)_

#### hersenboomvertakking moet worden bijgewerkt met PHP 8.5-ondersteuning

De Braintree payment extension is bijgewerkt ter ondersteuning van de nieuwste PHP 8.5 runtime, terwijl compatibiliteit met PHP 8.4 behouden blijft.

_BUNDLE-3493_

#### Wissen van wenslijst toevoegen

Er is een nieuwe clearWishlist-mutatie toegevoegd ter ondersteuning van bulkbewerkingen, zodat alle items in één actie uit een wenslijst kunnen worden verwijderd.

_LYNX-790_

#### Introduceer uitwisselingExternalCustomerToken-mutatie

Introductie van nieuwe GraphQL-mutatieuitwisselingExternalCustomerToken die gebruikers via een integratietoken verifieert en zowel het klanttoken als de bijbehorende klantgegevens retourneert

_LYNX-815_

#### [ AC ] introduceert de vragen van GraphQL die toegepaste groep terugkeren, segmenten en worstregelaars ids

GraphQL query&#39;s die beschikbaar zijn om gecodeerde gegevens op te halen uit de toegepaste klantengroep, klantsegmenten en winkelregels.

_LYNX-867_

#### [ AC-2.4.9 ] introduceert OrderTotal.Grand_total_excl_tax gebied

Er is een nieuw veld, OrderTotal.Eindtotaal_excl_tax, toegevoegd aan het GraphQL-orderantwoord. In dit veld wordt het totale bedrag van de order exclusief belasting weergegeven, waardoor het gemakkelijker wordt om rechtstreeks via de API toegang te krijgen tot totalen die exclusief belasting zijn.

Voordelen:

- U kunt eenvoudig het totaal van de kleinste bedragen, exclusief belastingen, ophalen voor elke bestelling via GraphQL.
- Vereenvoudigt integratie met externe systemen die uitsluitend belastingtotalen vereisen.
- Hiermee vermindert u de behoefte aan aangepaste berekeningen op de client.

_LYNX-892_

### PCI, beveiliging

#### SRI-opslag van Refactor om efficiënter te presteren

SRI-hashopslag genereert nu afzonderlijke bestanden per gebied, thema en landinstelling in plaats van één grote sri-hashes.json. Deze wijziging zorgt ervoor dat alleen het desbetreffende hash-bestand voor elke pagina wordt geladen, wat de prestaties verbetert en het geheugengebruik in winkels met meerdere thema&#39;s of landinstellingen vermindert.

_AC-16113 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/bc83cd2c)_

### Beveiliging

#### Verbeterde prestaties van async-/bulkverzoeken

Verbeter de prestatievermindering in bulksgewijs asynchrone Webeindpunten die na het beveiligingspatch APSB25-08 worden geïntroduceerd, resulterend in verhoogde uitvoeringstijden.

_AC-14078 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/9a7352b7)_

#### Slechts vereist één toegelaten 2FA leverancier om per gebruiker te vormen

Admin-gebruikers moeten nu slechts een van de door de handelaar ingeschakelde 2FA-providers (bijvoorbeeld Google Authenticator of U2F) configureren voor toegang tot het beheerpaneel. Extra toegelaten leveranciers kunnen later worden gevormd zoals nodig. Eerder, toen veelvoudige 2FA leveranciers (b.v., de Authenticator van Google en U2F) werden toegelaten, werd elke gebruiker Admin vereist om alle toegelaten leveranciers te vormen alvorens zij konden binnen ondertekenen. Dit leidde tot wrijving voor gebruikers die geen toegang tot alle factoren (zoals een hardwaresleutel voor U2F) hadden.

_AC-8253 - [ GitHub codebijdrage ](https://github.com/magento/security-package/commit/71e7936b)_
