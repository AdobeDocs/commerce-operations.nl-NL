---
source-git-commit: 65a9bd667d434f1deae69798696f66998e6024a0
workflow-type: tm+mt
source-wordcount: '952'
ht-degree: 0%

---
# Magento Open Source-hooglichten (v2.4.9-bèta1)

## Hooglichten in v2.4.9-bèta1

De volgende markeringen zijn van toepassing op de Magento Open Source 2.4.9-bèta1-release.

### API&#39;s

#### De mogelijkheid toevoegen om de overerving van productgalerie in de REST API te behouden bij het bijwerken van een product in de weergaveniveau van de winkel

Wanneer het product via REST API in een opslagbereik wordt bijgewerkt, kunnen productafbeeldingen en video&#39;s geen wijzigingen van het algemene bereik meer overnemen als de media_gallery_entries worden weggelaten uit de payload of op NULL zijn ingesteld om wijzigingen in de productgalerie in dat bereik te voorkomen. Bovendien is het nu mogelijk om bereikovererving voor productbeelden en video via REST API te herstellen door het corresponderende veld in te stellen op NULL

_ACP2E-4358 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f7bbcb4e)_

### Kader

#### De nieuwste belangrijkste versie van webtoken/jwt-framework bekijken

In het kader van het doorlopende veiligheidscontroleproces hebben we de meest recente grote release van het JWT-kader geëvalueerd om toekomstige compatibiliteit te waarborgen en sterke veiligheidsnormen te handhaven. Deze release heeft geen invloed op de bestaande functionaliteit.

_AC-13209 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/2bac8114) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/09b36ebb) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/33b81f28)_

#### Carlos-mg89/oauth vervangen door native functies van PHP

De carlos-mg89/oauth-bibliotheek van derden is vervangen door native PHP OAuth-functies om de beveiliging te verbeteren, externe afhankelijkheden te verminderen en de stabiliteit van het platform te verbeteren.

_AC-14075 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7b8064f7)_

#### Onderzoek de recentste versie chart.js

De grafiekbibliotheek Chart.js JavaScript werd bijgewerkt naar de recentste versie 4.4.8 om grafiekteruggevende prestaties te verbeteren, visuele mogelijkheden te verbeteren, en veiligheidskwetsbaarheid in het admin dashboard en rapporteringsmodules te richten.

_AC-14304 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/768b4442)_

#### De meest recente versie van jQuery/uppy en uppy bekijken

De Uppy-bibliotheek voor het uploaden van bestanden is bijgewerkt naar versie 4.13.4 om de mogelijkheden voor het uploaden van bestanden te verbeteren, gebruikerservaring te verbeteren en beveiligingskwetsbaarheden in het verwerken van bestanden te verhelpen via de Adobe Commerce-beheerinterface en frontend-componenten.

_AC-14307 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/eb491c05)_

#### De meest recente versie van jquery controleren en valideren

De jQuery Validate-bibliotheek is bijgewerkt naar versie 1.21.0 om de validatiemogelijkheden van formulieren te verbeteren, gebruikerservaring te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-formulieren in zowel de beheerdersinterface als de frontendinterfaces.

_AC-14403 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

#### De meest recente versie van jquery-ui onderzoeken

De jQuery-gebruikersinterfacebibliotheek is bijgewerkt naar versie 1.14.1 om de widgets van de gebruikersinterface te verbeteren, de toegankelijkheid te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-admin- en frontendinterfacecomponenten.

_AC-14417 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/77c589a6)_

#### De nieuwste versie van less.js bekijken

De CSS-preprocessor van Minder.js is bijgewerkt naar versie 4.2.2 om de prestaties van de CSS-compilatie te verbeteren, de syntaxisondersteuning te verbeteren en het proces voor het maken van thema&#39;s te moderniseren voor alle Adobe Commerce-thema&#39;s frontend en admin.

_AC-14418 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

#### Onderzoek de recentste versie moment-timezone-with-data.js

De tijdzonebibliotheek van het Moment aan versie 0.5.43 werd bijgewerkt om timezone behandelingsmogelijkheden te verbeteren, tijdzonegegevens met recentste veranderingen van het Gegevensbestand van de Tijdzone van IANA bij te werken, en datum/tijd verwerkingsnauwkeurigheid over alle internationale en multi-timezoneverrichtingen van Adobe Commerce te verbeteren.

_AC-14419 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

#### De meest recente versie van underscore.js bekijken

De Underscore.js-hulpprogrammabibliotheek is bijgewerkt naar versie 1.13.7 om de functionaliteit van JavaScript-programmering te verbeteren, de prestaties van gegevensmanipulatie te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-componenten voor frontend- en beheerinterface.

_AC-14420 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/98b2848a)_

#### Alure-framework/allure-phpunit versie bijwerken naar 3 en native afhankelijkheid verwijderen in 2.4.9-alpha1

In Adobe Commerce 2.4.9 is de afhankelijkheid van allure-framework/allure-phpunit geüpgraded naar versie 3, die ondersteuning biedt voor PHP 8.4, PHP 8.5 en onze rapportstack op basis van Alure moderniseert. De native afhankelijkheid die voorheen werd vereist door oudere versies van Alure PHPUnit is waar van toepassing verwijderd, waardoor installatie en onderhoud eenvoudiger werden.

_AC-14548 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/87b8b34e)_

#### De afhankelijkheid van Chart.js van de verbetering aan de recentste versie

De afhankelijkheid van chart.js wordt bevorderd tot de recentste versie 4.5.0

_AC-15133 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/657f983e)_

#### Voeg overheidssteun toe voor Symfony 7.4 LTS en PHP 8.5 in Adobe Commerce 2.4.9

Als onderdeel van de Adobe Commerce 2.4.9-platformupdates zijn alle Symfony-afhankelijkheden die door het magento/composer-pakket worden gebruikt, bijgewerkt naar de nieuwste Symfony LTS 7.4-versies. Hiermee wordt het gereedschap Composer van Commerce uitgelijnd op de huidige LTS-regel van Symfony en worden eerdere afhankelijkheidsbeperkingen met betrekking tot oudere Symfony-versies verwijderd. Bovendien hebben alle aangepaste klassen die de kernklassen van Symfony uitbreiden, typedeclaraties en methodehandtekeningen bijgewerkt die zijn afgestemd op de meest recente Symfony-vereisten voordat de upgrade naar Adobe Commerce 2.4.9 wordt uitgevoerd. Dit voorkomt compatibiliteitsproblemen en zorgt voor een soepele overgang naar de bijgewerkte frameonderdelen.

_AC-15170 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c127d10b)_

### Overige

#### Captcha/reCaptha werkt niet voor API/GraphQl

Wanneer CAPTCHA (of reCAPTCHA) in Adobe Commerce 2.4.9 is ingeschakeld voor het formulier Account maken, wordt nu dezelfde CAPTCHA-validatie afgedwongen voor het maken van een klantenaccount via REST- en GraphQL-API&#39;s.

_AC-16245 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/fd7f30ee)_

### Beveiliging

#### Verbeterde prestaties van async-/bulkverzoeken

Verbeter de prestatievermindering in bulksgewijs asynchrone Webeindpunten die na het beveiligingspatch APSB25-08 worden geïntroduceerd, resulterend in verhoogde uitvoeringstijden.

_AC-14078 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/9a7352b7)_

#### Slechts vereist één toegelaten 2FA leverancier om per gebruiker te vormen

Admin-gebruikers moeten nu slechts een van de door de handelaar ingeschakelde 2FA-providers (bijvoorbeeld Google Authenticator of U2F) configureren voor toegang tot het beheerpaneel. Extra toegelaten leveranciers kunnen later worden gevormd zoals nodig. Eerder, toen veelvoudige 2FA leveranciers (b.v., de Authenticator van Google en U2F) werden toegelaten, werd elke gebruiker Admin vereist om alle toegelaten leveranciers te vormen alvorens zij konden binnen ondertekenen. Dit leidde tot wrijving voor gebruikers die geen toegang tot alle factoren (zoals een hardwaresleutel voor U2F) hadden.

_AC-8253 - [ GitHub codebijdrage ](https://github.com/magento/security-package/commit/71e7936b)_

### Staging en voorvertoning

#### [ Voorproef van de het opvoeren van de inhoud van het 10} Verzoek van de Eigenschap in mobiele mening]

Met de functie voor voorvertoningen van gefaseerde mobiele apparaten in het deelvenster Beheer kunnen voorvertoningen van door de browser gesimuleerde mobiele apparaten nu op de juiste wijze worden weergegeven. Zo kunt u zien hoe de gefaseerde update op een mobiel apparaat wordt weergegeven.

_ACP2E-3397 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/520f9e30)_
