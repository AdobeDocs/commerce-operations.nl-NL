---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '645'
ht-degree: 0%

---
# Adobe Commerce-releaseopmerkingen (v2.4.9-alpha2)

## Hooglichten in v2.4.9-alpha2

De volgende markeringen zijn van toepassing op de Adobe Commerce 2.4.9-alpha2-release.

### Kader

#### Ondersteuning toevoegen voor OpenSearch 3

Adobe Commerce 2.4.9 is nu volledig compatibel met OpenSearch 3.x. Deze update stelt handelaren in staat te profiteren van verbeterde prestaties, beveiliging en ondersteuning op lange termijn, terwijl de compatibiliteit met OpenSearch 2.x behouden blijft.

_AC-11846_

#### Nginx-versie bijwerken van 1.26 naar 1.28

De NGinx-versie die wordt gebruikt in ontwikkelings- en testomgevingen in alle momenteel ondersteunde versies van Adobe Commerce, wordt bijgewerkt van 1,26 tot 1,28, op één lijn met de nieuwste stabiele NGinx-versie die beschikbaar is.
Het testen op PR-niveau wordt nu uitgevoerd tegen Nginx 1.28, dat volledige compatibiliteit en ondersteuning voor alle Adobe Commerce-versies bevestigt.

_AC-14104_

#### De meest recente versie van jquery controleren en valideren

De jQuery Validate-bibliotheek is bijgewerkt naar versie 1.21.0 om de validatiemogelijkheden van formulieren te verbeteren, gebruikerservaring te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-formulieren in zowel de beheerdersinterface als de frontendinterfaces.

_AC-14403 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

#### De meest recente versie van jquery-ui onderzoeken

De jQuery-gebruikersinterfacebibliotheek is bijgewerkt naar versie 1.14.1 om de widgets van de gebruikersinterface te verbeteren, de toegankelijkheid te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-admin- en frontendinterfacecomponenten.

_AC-14417 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/77c589a6)_

#### De nieuwste versie van less.js bekijken

De CSS-preprocessor van Minder.js is bijgewerkt naar versie 4.2.2 om de prestaties van de CSS-compilatie te verbeteren, de syntaxisondersteuning te verbeteren en het proces voor het maken van thema&#39;s te moderniseren voor alle Adobe Commerce-thema&#39;s frontend en admin.

_AC-14418 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

#### Onderzoek de recentste versie moment-timezone-with-data.js

De tijdzonebibliotheek van het Moment aan versie 0.5.43 werd bijgewerkt om timezone behandelingsmogelijkheden te verbeteren, tijdzonegegevens met recentste veranderingen van het Gegevensbestand van de Tijdzone van IANA bij te werken, en datum/tijd verwerkingsnauwkeurigheid over alle internationale en multi-timezoneverrichtingen van Adobe Commerce te verbeteren.

_AC-14419 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

#### De meest recente versie van underscore.js bekijken

De Underscore.js-hulpprogrammabibliotheek is bijgewerkt naar versie 1.13.7 om de functionaliteit van JavaScript-programmering te verbeteren, de prestaties van gegevensmanipulatie te verbeteren en te zorgen voor moderne browsercompatibiliteit in alle Adobe Commerce-componenten voor frontend- en beheerinterface.

_AC-14420 - [&#x200B; GitHub codebijdrage &#x200B;](https://github.com/magento/magento2/commit/98b2848a)_

#### Migreren van TinyMCE naar Hugerte.org

Vanwege het einde van de ondersteuning voor TinyMCE 5 en 6 en vanwege onverenigbaarheden in licenties met TinyMCE 7, wordt de huidige implementatie van de Adobe Commerce WYSIWYG-editor gemigreerd van TinyMCE naar de open-source HugeRTE-editor (https://hugerte.org/).
Deze migratie zorgt ervoor dat Adobe Commerce compatibel blijft met open-sourcinglicenties, bekende TinyMCE 6-kwetsbaarheden voorkomt en een moderne, ondersteunde bewerkingservaring biedt voor handelaren en ontwikkelaars.

_AC-14568_

#### Volledige ondersteuning voor Valkey 8.x voor 2.4.9-alpha2 toevoegen

Adobe Commerce 2.4.9 heeft volledige CLI bevelensteun voor Valkey, die momenteel bestaande functionaliteit weerspiegelt Redis. Admin- en cloudconfiguratie bijgewerkt om naadloze installatie van Valkey mogelijk te maken.
Deze update zorgt ervoor dat Adobe Commerce ook in de toekomst bestendig en prestatiebestendig blijft door Valkey 8.x te ondersteunen, waardoor handelaren en ontwikkelaars een betrouwbaar alternatief voor Redis krijgen wanneer het afloopt.

_AC-14604_

### Overige

#### Werk de AWS Valkey 8.x Service voor CNS Build en Test bij

Werk de AWS Valkey 8.x-service voor CNS Build bij

_AC-14470_

#### 2.4.9-alpha2 - Kwaliteitsverbeteringen augustus

_AC-14700_

### Beveiliging

#### Beveiligingsverbeteringen voor 2.4.9-alpha2

_AC-14610_

### Verzending

#### USPS-integratie migreren van verouderde Web Tools API&#39;s naar nieuwe RESTful USPS API&#39;s

Om te voldoen aan de door USPS aangekondigde pensionering van de verouderde API&#39;s van de Webhulpmiddelen tegen 25 januari 2026, wordt de integratie van Adobe Commerce USPS gemigreerd naar de nieuwe RESTful USPS API&#39;s.
Belangrijkste verbeteringen:
- Ondersteuning voor dubbele API: Admin-gebruikers kunnen nu kiezen tussen de verouderde API voor webgereedschappen en de nieuwe RESTful-API voor USPS via configuratie-instellingen.
- Upgrade van verificatie: Geïmplementeerd OAuth 2.0 voor beveiligde API-toegang.
- Verbeterde gegevensindeling: overgang van XML naar JSON voor een schonere, efficiëntere communicatie.
- Nieuwe beheervelden:
URL van de REST van de gateway (die op wijze wordt gebaseerd: Ontwikkeling of Levend)
Client-id en -geheim
Accounttype, accountnummer
CRID, MID, identificatiecode van de legger
AES/ITN voor internationale overbrengingen
REST-specifieke toegestane verzendmethoden
Deze migratie zorgt ervoor dat Adobe Commerce blijft voldoen aan de USPS-standaarden, verbetert de betrouwbaarheid van het systeem en maakt het mogelijk om voortaan proefversies te maken van de verzendintegratie voor handelaren.

_AC-13257_
