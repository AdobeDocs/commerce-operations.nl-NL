---
source-git-commit: ae571a9e7ca1234644a3bc9beade447009c58a3d
workflow-type: tm+mt
source-wordcount: '6077'
ht-degree: 0%

---
# Opgeloste problemen in Adobe Commerce (v2.4.9-alpha3)

## Opgeloste problemen in v2.4.9-alpha3

We hebben 129 problemen opgelost in de Adobe Commerce 2.4.9-alpha3-kerncode. Hieronder wordt een subset van de opgeloste problemen in deze release beschreven.

### API&#39;s

#### Fout met factuuradres in beheerdashboard bij maken van bestelling via REST API met alleen betalingsgegevens

Oplossing voor een probleem waarbij via de API orders konden worden gemaakt zonder factuuradres, waardoor het dashboard van de beheerder vastliep.
Nu zijn bestellingen zonder factuuradres beperkt en worden deze niet meer gemaakt.

_AC-14049 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39651) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Product toevoegen aan winkelwagentprobleem in de Rest-API

Producten die niet aan een specifieke website waren toegewezen, konden nog steeds aan de wagen worden toegevoegd en aangeschaft. Dit probleem is nu opgelost.
Er wordt nu een foutbericht weergegeven: &quot;Het product dat u wilt toevoegen, is niet beschikbaar.&quot;

_AC-15054 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40029) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/f5cc09fc)_

#### Label voor kenmerkoptie wordt overschreven wanneer winkellabels worden bijgewerkt

Door het bijwerken van een multiselect productkenmerk via REST API werden alle store_labels overschreven en werden bestaande winkelspecifieke labels verwijderd. Dit probleem is nu opgelost.
Wanneer Magento nu het standaardweergavelabel van de winkel bijwerkt, worden de aangeboden labels samengevoegd met bestaande labels in plaats van ze volledig te overschrijven.
Dit zorgt ervoor dat de store-specific etiketten voor andere opslagmeningen na updates intact blijven.

_AC-15208 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40093) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/36d4d6fb)_

#### REST API-eindpunt export-stock-salable-quality retourneert onjuiste items total_count

Probleem opgelost met paginering in de voorraad exportbestand. Verhandelbare hoeveelheid-API waarbij total_count onjuist beperkt was tot paginaformaat. Eerder, wanneer het gebruiken van /rest/all/V1/voorraad/export-stock-salable-quality/website/base eindpunt met pagineringsparameters zoals page_size=5, zou het total_count gebied in de reactie 5 in plaats van het daadwerkelijke totale aantal producten terugkeren die aan de onderzoekscriteria voldoen. Na deze moeilijke situatie, wijst het total_count gebied nu correct op het totale aantal producten beschikbaar ongeacht de page_size parameter, die verenigbaar pagineringsgedrag over alle eindpunten van Magento REST API verzekeren.

_ACP2E-4086 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/5632fb5e)_

#### Probleem met validatie met aangepaste optie-id&#39;s in REST API&#39;s van cart-items

REST API&#39;s V1/gast-carts/&lt;cartId>/items/ en V1/carts/mine/items/ valideren nu &quot;product_options.extension_attributes.custom_options.*.option_id&quot; om ervoor te zorgen dat het naar een geldige option_id verwijst voor het winkelwagentje SKU. Eerder werd deze parameter verwerkt en opgeslagen in de database zonder validatie.

_ACP2E-4138 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a1c57b2e)_

### Account

#### [ Uitgave ] Verwijderde onnodige spatiëring op achterste-end raster

Het systeem verwijdert nu overbodige spatiëring in het achtergrondraster wanneer er geselecteerde items zijn

_AC-11579 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38502) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32622)_

#### Kan commentaar voor wenslijstonderdelen niet wissen via `updateProductsInWishlist` GraphQL-mutatie

De wenslijstopmerkingen werden niet bijgewerkt via GraphQL-mutaties. Dit probleem is nu opgelost.
Opmerkingen worden nu op de juiste wijze bijgewerkt en in de API-reactie en in de winkel weergegeven.

_AC-14682 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39911) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Voor-/achtervoegselinstelling tonen die is genegeerd wanneer deze is ingesteld op Nee

Het voorvoegsel/achtervoegsel voor de naam van de klant werd ook in bestellingen weergegeven, zelfs als dit in de configuratie was uitgeschakeld. Dit probleem is nu opgelost.
Nu, worden de prefix/achtervoegselwaarden gestript van ordedetails die op config het plaatsen worden gebaseerd.

_AC-15074 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40036) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Storefront-accountregister van klant: e-mailadresnotatie wordt geconverteerd met verschillende domeinnotaties

Deze bug verholpen een probleem waarbij e-mails van klanten met speciale tekens in het domein (bijvoorbeeld tec55241@adòbe.com) automatisch werden omgezet in de indeling voor punycode (tec55241@xn—adbe-mqa.com).
In Magento 2.4.9-alpha3 zorgt de correctie ervoor dat dergelijke e-mailid&#39;s ongewijzigd en geldig blijven, zodat leveringsfouten worden voorkomen.

_AC-15177 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/68a45d0a)_

#### Ontbrekende validatieberichten (afbeeldingsfout) op registratieformulier

In de vereiste velden op de pagina voor het aanmaken van een klantenaccount werden geen validatieberichten weergegeven als deze leeg waren. Dit probleem is nu opgelost.
Nauwkeurige foutberichten worden nu weergegeven voor alle lege of onjuiste velden.

_AC-15185 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40076) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Uitgave na aanmelding in magento 2.4.8-p1

Het probleem met Magento 2.4.8-p1 waarbij de koppeling &quot;Account maken&quot; na de aanmelding nog steeds zichtbaar was op de startpagina, is opgelost.
De koppeling is nu correct verborgen na de aanmelding en consistent met andere pagina&#39;s.

_AC-15292 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40120)_

### Gebruikersinterface van beheerder

#### [ Uitgave ] vervangt afgekeurde escaper

Deze PR verwijdert de vervangen getEscaper() en voegt deze toe via constructorinjectie

_AC-15132 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40062) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38135)_

#### Welkomstbericht dat de productcategorie overlapt in de mobiele weergave.

Probleem opgelost waarbij de welkomstnaam in de mobiele weergave overlapte met de productcategorieën en kliks werd geblokkeerd.
Categorieën zijn nu volledig zichtbaar en kunnen zonder overlappende problemen worden aangeklikt.

_AC-15166 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Items voor de parameter reCAPTCHA kunnen niet worden opgelost in exception.log voor het deelvenster Google reCAPTCHA Admin

Er is een reCaptcha-fout opgelost in het `var/log/exception.log` -bestand voor de aanmelding voor Google V3 reCAPTCHA Admin en er worden geen foutberichten geregistreerd. Eerder, werd de volgende fout geworpen om de paar seconden toen een admin gebruiker hun **Configuratie** > **Veiligheid** > **Google reCAPTCHA Admin Comité** montages vormde: `main.ERROR: Can not resolve reCAPTCHA parameter. {&quot;exception&quot;:&quot;[object] (Magento\Framework\Exception\InputException(code: 0): Can not resolve reCAPTCHA parameter. at /home/xxxxxxx/public_html/vendor/magento/module-re-captcha-ui/Model/CaptchaResponseResolver.php:25)&quot;} []`.  [ GitHub-34975 ](https://github.com/magento/magento2/issues/34975)

_AC-3179 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/34975) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/4f7e5983) - [ GitHub codebijdrage ](https://github.com/magento/security-package/commit/804dbc2a)_

#### Beperkte admin-gebruikers kunnen standaardconfiguraties opslaan/bijwerken ondanks Store-Specific Machtigingen

Hiermee wordt het probleem verholpen waarbij gebruikers met beperkte beheerdersrechten het bereik Standaardconfiguratie konden zien en proberen bij te werken, hoewel ze alleen aan specifieke websitebereiken waren toegewezen. Dit kan tot verwarring leiden.

_ACP2E-4011 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Configureerbare productprijs die is opgeslagen in de DB voor elk weergavebereik van de winkel. Dit leidt tot problemen in de sorteerfunctie Producten in categorie waarvoor de opgeslagen prijs geen relevantie heeft in de frontend

Het selectievakje Standaardwaarde gebruiken voor een configureerbaar product is verwijderd wanneer de prijs per website wordt geconfigureerd en een winkelweergave is geselecteerd op de voor beheerders in de gebruikersinterface configureerbare productbewerkingspagina.

_ACP2E-4036 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/fab20b00)_

#### [ Admin het Beleid van het Wachtwoord van KANTOREN ] komt niet naleving PCI DSS 4.0 (minimum 12 Karakters) na

Beheerders kunnen nu de minimale lengte van wachtwoorden voor gebruikers met beheerdersrechten configureren via Opslag > Configuratie > Geavanceerd > Beheer > Beveiliging. Deze verbetering verstrekt grotere veiligheidsflexibiliteit terwijl het handhaven van bestaand wachtwoordbeleid. De validatie wordt afgedwongen tijdens het maken/wijzigen van gebruikers en het opslaan van de configuratie, met frontend-validatie in real time voor een betere gebruikerservaring.

_ACP2E-4044 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/47721be6)_

#### Datumfilterprobleem wanneer de interfacetaal van het beheerder Japans is

Het filter en de kolom van de Verjaardag zullen het verenigde formaat M/d/y, zelfde als &quot;Klant sinds&quot;filter/kolom gebruiken

_ACP2E-4052 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/52f46328)_

### Admin-gebruikersinterface, BTW

#### Fiscaal tarief admin ui-fout

Met dit ticket werd een probleem opgelost in de gebruikersinterface van de beheerder van het belastingtarief, waarbij het veranderen van land (bijvoorbeeld vanuit de VS → VK) nog steeds de eerder geselecteerde Amerikaanse staat weergaf, misleidende gebruikers.
In 2.4.9-alpha3 wordt het statusveld nu teruggezet naar * als het geselecteerde land geen frames heeft.

_AC-8440 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a3b1abc2)_

### B2B

#### Rest API producten-render-info de verkeerde definitieve prijs voor het programma geopende klant

Het kaartje heeft een moeilijke situatie voor Rest API producten-teruggeven-info de verkeerde definitieve prijs voor het programma geopende klant

_AC-5979 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35757) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/)_

#### De knop Toevoegen aan lijst met aanvragen verdwijnt wanneer we deze proberen toe te voegen vanuit de pagina met categorieën

De knop Toevoegen aan lijst met aanvragen verdwijnt wanneer we deze proberen toe te voegen vanuit een vaste categoriepagina. De aanvraagknop wordt weergegeven op de categoriepagina

_AC-8575_

### B2B, winkelwagentje en kassa

#### Geen dergelijke entiteit met cartId = X fout wordt getoond in Storefront wanneer login B2B bedrijfgebruiker van admin eigenschap &quot;Login als Klant&quot;

Nu is de fout &#39;&#39;Geen dergelijke entiteit met cartId = X&#39;&#39; niet meer zichtbaar nadat u zich met succes hebt aangemeld bij de back-end van de beheerder wanneer u de functie &#39;&#39;Aanmelden als klant&#39;&#39; gebruikt.

_ACP2E-3994 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/2a1e1e55)_

### Winkelwagentje en Afhandeling

#### [ Uitgave ] voegt EventPrefix en EventObject toe aan het model van de controleovereenkomst

Het systeem bevat nu EventPrefix en EventObject voor het model van de uitcheckovereenkomst, waardoor gebeurtenissen met een gebeurtenisvoorvoegsel kunnen worden geactiveerd. Deze verbetering biedt ontwikkelaars meer flexibiliteit bij het werken met gebeurtenissen voor afrekenovereenkomsten. Eerder, steunde het model van de controleovereenkomst geen EventPrefix en EventObject, die de capaciteit beperken om gebeurtenis behandeling aan te passen.

_AC-13252 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32510) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32451)_

#### [ Graphql ] kan ongeldig voor niet-nullable gebied &quot;SelectedCustomizableOption.label&quot; terugkeren

Het systeem genereert nu geen interne serverfout met een bericht als de geselecteerde optie niet langer bestaat

_AC-14256 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39729) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39888)_

#### [ 2.4.8 ] kan geen orden plaatsen waar de Stad cijfers 0-9, Ampersand, volledige eind of haakje in de Naam van de Stad heeft

Afhandeling is mislukt voor namen van steden met speciale tekens zoals. Dit probleem is nu opgelost. , en, of ronde haakjes.
Orden met dergelijke plaatsnamen worden nu zonder validatiefouten geplaatst.

_AC-14495 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39854) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Salesrule Subselect with Quantity condition Fail to apply

Probleem opgelost waarbij de regels voor de kartprijs met de voorwaarden voor productsubselectie niet van toepassing waren bij het afrekenen.
Nu, worden de kortingen met succes toegepast volgens de gevormde regels.

_AC-14884 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39965) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/fe72c407)_

#### Grafiek - De karretje van de Fusie werkt niet correct wanneer de Achterorde wordt toegelaten

Gastwinkelwagentjes zijn niet samengevoegd met winkelwagentje tijdens het samenvoegen van winkelwagentjes via GraphQL. Dit probleem is nu opgelost.
Klantwinkelwagentje geeft nu de gecombineerde hoeveelheid van zowel gasten- als klantenkaarten correct weer.

_AC-15148 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40064) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a3b1abc2)_

#### [ Integratie ] [ Afhandeling ] Depend richtlijnen die in ontbroken betalings e-mailmalplaatje worden bijgewerkt

Slaagde betalings e-mailmalplaatje bijgewerkt om correcte afhankelende richtlijnen te behandelen.
Correctie zorgt ervoor dat het verzendadres en de verzendmethode correct worden weergegeven, indien van toepassing.
Eerder ontbrak deze velden in mislukte e-mails over betalingen.

_AC-15363 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/36d4d6fb)_

#### [ de Gratis Verzendkorting van de Wolk ] wordt niet correct verwijderd wanneer het winkelwagentje niet meer aan vereisten voldoet

Het subtotaal (behalve Belasting) in de regel van de kartprijs zal nu kortingen van vorige regels omvatten.

_ACP2E-3973 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Dubbele bestelling gevonden voor dezelfde klant in MultiShipping

Gelijktijdige aanvragen om bestelling met meerdere verzendadressen te plaatsen, resulteren niet langer in dubbele bestellingen voor dezelfde klant

_ACP2E-4117 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a1c57b2e)_

### Winkelwagentje en afhandeling, bestelling, product

#### E-mail met creditcard wordt verzonden, zelfs als de factuur voor de bestelling is mislukt

Voordat deze correctie werd geïmplementeerd, zijn e-mails met een cadeaukaart verzonden nadat de factuur was gemaakt. Nadat de correctie is toegepast, worden e-mails met een cadeaukaart verzonden nadat de facturen zijn opgeslagen en toegewezen.

_ACP2E-3905_

### Winkelwagentje en afhandeling, beveiliging

#### [ CLOUD ] die 404 voor JS- dossier op checkout pagina op eerste poging na het uitvoeren van sri flard krijgt

Vóór de fixmixins zouden niet geladen zijn in karretje en uitchecken wanneer minify en bundling ingeschakeld was. Na de correctie moeten alle mengsels op de verwachte wijze worden geladen.

_ACP2E-4128 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/e457c5e2)_

### Catalogus

#### Problemen met prijsbereik en config.php

In Magento 2.4.2 wordt bij het wijzigen van het prijsbereik via config.php de waarde is_global in catalog_eav_attribute voor het prijskenmerk niet correct bijgewerkt.
Als gevolg hiervan blijven productprijzen wereldwijd en kunnen deze niet per website worden opgeslagen, zelfs niet wanneer het prijsbereik op de website is ingesteld.
De oplossing vereist manueel het bijwerken van de is_global kolom in het gegevensbestand, dat niet ideaal voor productiemilieu&#39;s is.
Dit gedrag is consistent met het standaardontwerp van Magento, waar het prijsbereik Global of Website is, maar niet per winkelweergave.

_AC-13857 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/33559)_

#### Na de pagina van de archiefschakelaar komt uit geheim voorgeheugen (de schakelaars van de opslag werken niet) in 2.4.8

Het schakelen tussen de archiefweergaven van de winkelkoptekst werkte pas nadat de cache handmatig was gewist. Dit probleem is nu opgelost.
Nu, de omschakeling van de archiefmening werkt correct zonder een geheim voorgeheugen schoon te vereisen.

_AC-14426 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39806)_

#### Genegeerde .less-stijlen met min-breedte: (@screen__l)

Er werden slechts drie producten per rij weergegeven op rubriekpagina&#39;s. Dit probleem is nu opgelost.
Er worden nu vier producten per rij weergegeven zoals u had verwacht.

_AC-14463 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39817) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/b9f5d6f7)_

#### Het aantal van de lijst van het Wislijst wordt niet getoond op homepage/andere pagina&#39;s behalve wishlist pagina in het klantenmenu

Het aantal wenslijsten werd weergegeven als lege haakjes op pagina&#39;s zonder verlanglijstje. Dit probleem is nu opgelost.
Nu wordt het juiste aantal wenslijstonderdelen weergegeven naast Mijn lijst van wensen op alle pagina&#39;s.

_AC-14607 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39892) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a3b1abc2) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/b3774fbe)_

#### catalog_product_save_before observer genereert een fout met betrekking tot de datum wanneer REST API wordt gebruikt zonder waarden op archiefniveau (getFinalPrice()-probleem)

Deze PR past de verwerking van SpecialFromDate aan om juiste het formatteren te verzekeren wanneer de datum als instantie DateTimeInterface wordt verstrekt. Dit voorkomt fouten die optreden tijdens uitvoering van getFinalPrice() in bepaalde scenario&#39;s.

_AC-14847 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39959) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/40003)_

#### URGENT - Kan product niet aan bundel toevoegen wanneer het toe te voegen product aanpasbare opties heeft

Producten met aanpasbare opties konden niet aan bundelproducten worden toegevoegd. Dit probleem is nu opgelost.
Eerder werden dergelijke producten uitgesloten van de lijst &quot;Producten toevoegen aan optie&quot; in het maken van pakketten.
Producten met aanpasbare opties kunnen nu aan bundels worden toegevoegd zonder hun aangepaste opties op te nemen, zodat een goed voorraadbeheer mogelijk is.
Hierdoor kunt u pakketten maken zonder producten te dupliceren of het voorraadniveau te beïnvloeden.

_AC-14958 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39993)_

#### Het prijsetiket &#39;Zo laag als&#39; wordt weergegeven voor configureerbare producten met één optie

In configureerbare producten werd de prijs weergegeven met een onjuist label &quot;Zo laag als&quot; op PDP/PLP. Dit probleem is nu opgelost.
Het product heeft nu de juiste prijs ($ 500) zonder misleidende labels.

_AC-15237 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40104) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Verkeerde methode die wordt aangeroepen voor knop Toevoegen aan vergelijking

Correctie van de methode gebruikt in \Magento\Catalog\Ui\DataProvider\Product\Listing\Collector\Url::collect().
Eerder werd getAddToCartButton() onjuist aangeroepen in plaats van getAddToCompareButton().
Deze wijziging zorgt voor het juiste gedrag bij het weergeven van de knop &quot;Toevoegen aan vergelijking&quot; in productaanbiedingen.
Er zijn geen wijzigingen in functioneel gedrag geïntroduceerd. De update verbetert de ervaring van de ontwikkelaar en de juistheid van de code.

_AC-15323 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39754) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Dynamische afbeelding genereren genereert een groot aantal afbeeldingen

Na de correctie worden afbeeldingen alleen gegenereerd voor de websites waaraan het product is toegewezen.

_ACP2E-3927 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/fab20b00)_

#### Er treden 500 fouten op de voorgrond als gevolg van een onjuiste layoutstructuur in de layout in de cache wordt opgeslagen

Probleem verholpen waarbij een pagina een foutcode van 500 zou retourneren omdat een onjuiste layoutstructuur in de layout in de cache werd opgeslagen. Dit probleem is nu opgelost.

_ACP2E-4040 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/47721be6)_

#### Validatiefout voor het veld kortingsbedrag voor regel catalogusprijs in Geplande update

Eerder, alvorens deze kwestie te bevestigen, voor de planningsupdate voor de regel van de catalogusprijs, als het kortingsbedrag door_fixed is dan werd het niet behoorlijk bevestigd wegens de bevestiging-aantal-waaier regel. Nadat deze correctie is toegepast, werkt de validatie correct voor de regel van de catalogusprijs voor vaste prijzen.

_ACP2E-4054 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Producten worden weergegeven als out-of-stock na het uitschakelen

Na de correctie zijn uitgeschakelde producten niet aanwezig in de widget producten.

_ACP2E-4136 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [ Fouten van de Wolk ] met dubbele ingangen (temp_category_descendants_%)

Tijdens het maken van geplande updates voor omgevingen met een groot aantal geneste categorieën was er een probleem met dubbele vermeldingen. Dit probleem is nu opgelost.

_ACP2E-4159 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a1c57b2e)_

### Catalogus, GraphQL

#### GraphQl ongeldige discontoberekening

GraphQL geeft nu correct kortingspercentages en basisprijzen weer wanneer catalogusprijzen zijn geconfigureerd om belasting op te nemen. Eerder traden ronding-fouten op, zoals het weergeven van 19,99% in plaats van 20%.

_ACP2E-3993 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/e457c5e2)_

### Catalogus, product

#### Verwante producten via gerelateerde productregel worden niet weergegeven in PDP via GraphQL

Eerder, alvorens deze moeilijke situatie werd toegepast, keerde de relatieve productregel leeg/ongeldig voor een product terug dat de regel aanpaste. Nadat deze correctie is toegepast, retourneert de relatieve regel voor het product probleemloos voor overeenkomende producten.

_ACP2E-3949_

### Inhoud

#### graphql (magento 2.4.6-p4) - fout wanneer u probeert een cms-pagina zonder actieve status op te halen

GraphQL-query voor een uitgeschakelde CMS-pagina heeft een interne serverfout geretourneerd. Dit probleem is nu opgelost.
Nu, haalt de vraag een juiste reactie zonder fouten.

_AC-12302 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38877) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1b1baf1d)_

#### [ GraphQl ] de vraag van de Route oneindige lijn

Dit kaartje verholpen de kwestie waar een de routevraag van GraphQL met de identieke Weg van het Verzoek en de Weg van het Doel een oneindige lijn veroorzaakte en uiteindelijk uit tijdde.
In 2.4.9-alpha3, keert de vraag nu de correcte foutenreactie in plaats van het herhalen terug.

_AC-14269 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39707) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/68a45d0a)_

#### Wijzig de constante IMAGE_FILE_NAME_PATTERN in public visible, voor meer flexibiliteit

De constante IMAGE_FILE_NAME_PATTERN in GenerateRenditions.php is openbaar gemaakt om ontwikkelaars meer flexibiliteit te bieden bij het werken met afbeeldingsuitvoeringen.De correctie is opgenomen in Magento 2.4.9-alpha3 met volledige eenheid en integratietestdekking.

_AC-15338 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39733) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/68a45d0a)_

#### Voorvertoning van inhoudstaging werkt niet met zoekresultaten

Als u in Voorvertoning afspelen zoekt, worden nu producten geretourneerd in overeenstemming met het geselecteerde bereik. Eerder, resulteerde het onderzoek in het standaardwerkingsgebied, dat de geselecteerde opslag negeert.

_ACP2E-4095_

#### Page Builder - Product Condition Logic Issue (OF logica gedraagt zich verkeerd en toont minder producten)

Page Builder Products Widget retourneert nu het juiste resultaat wanneer een kenmerk met een algemeen bereik wordt gebruikt in de voorwaarde &quot;Match Any&quot;

_ACP2E-4096 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/e457c5e2)_

### Klanten/klanten

#### Validatie van minimum- en maximumwaarden werkt niet voor DOB-kenmerk in Storefront

Deze bug verholpen het probleem waarbij de minimale en maximale datumvalidatie voor het kenmerk Date of Birth (DOB) niet werkte op de storefront (hoewel deze werkte in Admin).
In 2.4.9-alpha3 blokkeert validatie nu correct het opslaan van klanten met DOB buiten het toegestane bereik, waarbij een foutbericht wordt weergegeven.

_AC-13535 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/68a45d0a)_

#### Ajax 401 error load on Warning screen in admin panel while Login as Customer permission Introk

Deze bug verholpen een probleem waarbij een ingetrokken aanmelding als toestemming van de klant ertoe leidde dat een Ajax 401-fout met raw HTML in het pop-upvenster met waarschuwingen werd weergegeven.
Na de correctie geeft het systeem nu correct een normaal waarschuwingsbericht weer in plaats van de ruwe HTML.
De oplossing werd geleverd in Magento 2.4.9-alpha3

_AC-15336 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/68a45d0a)_

### Kader

#### [ Uitgave ] maakt methodehandtekening verenigbaar met interface

De methodehandtekening voor getAttributes is nu verenigbaar met zijn interface, verhinderend om het even welke fouten wanneer het beschrijven van de methode. Eerder, veroorzaakte inconsistenties in de methodehandtekening fouten wanneer het proberen om de getAttributes methode te beschrijven.

_AC-11578 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38501) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/31955)_

#### [ Bevestig-e-mailregel voor ui-component van de kwestie ]

Het systeem valideert nu correct meerdere e-mailadressen die zijn ingevoerd in UI-componenten, zodat elke e-mail correct wordt bijgesneden en gevalideerd. Eerder gebruikte het systeem een onjuiste methode voor het bijsnijden van e-mailadressen, die tot validatiefouten kon leiden.

_AC-11719 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38528) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/33470)_

#### [ Uitgave ] verwijdert overtollige methodes

Codekwaliteit: Verwijderde overtollige methodes in componenten AsynchronousOperations en Sales die slechts oudermethodes zonder functionaliteit riepen toe te voegen, verbeterend codehoudbaarheid.

_AC-11915 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/29748) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/29147)_

#### xsd-validatie mislukt voor etc/adminhtml/system.xml-bestanden die opmerkingen bevatten onder velditems.

In deze PR worden XML-schemadefinities in &#39;phpstorm&#39; gecorrigeerd voor het knooppunt Commentaar

_AC-12945 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39148) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39867)_

#### Magento 2.4.8 gebruikt ontwikkelpakketten die semantische versioning niet volgen

Voor compatibiliteit met PHP 8.4 is voor Magento 2.4.8 dev-versies van afhankelijk/afhankelijk en phpmd/phpmd (3.x-dev) vereist.
Deze dev-versies veroorzaken een conflict met hulpmiddelen van derden die SemVer-volgzame pakketten verwachten, die sommige verbeteringen verhinderen.
Een tijdelijke oplossing is het aliassen van de dev-versies in composer.json (bijvoorbeeld &quot;3.x-dev als 3.99.0&quot;), waardoor compatibiliteit mogelijk is en semantische versies voldoen.
Dit zorgt voor ondersteuning voor PHP 8.4 en vermijdt conflicten totdat stabiele releases beschikbaar komen.

_AC-14519 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39796)_

#### Rest API: Call to a member function getVideoProvider() on null

Het aanroepen van de configureerbare API voor productonderliggende items heeft een fout van 500 interne server geretourneerd als een onderliggend product alleen een YouTube-video en geen andere afbeeldingen bevat. Dit probleem is nu opgelost.
De fout werd veroorzaakt door een ongeldige verwijzing in ExternalVideoEntryConverter.
De API retourneert nu op de juiste wijze onderliggende producten met mediagalerienummers, inclusief externe videogegevens, zonder fouten te genereren.
Hierdoor worden alle mediatypen voor onderliggende producten op de juiste wijze opgehaald via de REST API.

_AC-15046 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40021)_

#### [ Uitgave ] bevestig een paar typos in commentaren PHPDoc

In deze PR worden de paar typos in de phpdoc gecorrigeerd

_AC-15075 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40042) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38809)_

#### [ Uitgave ] verwijdert gebruik sprintf in uitdrukkingsvraag

Deze PR verwijdert het gebruik van sprintf in de woordfunctieaanroep in de Magento core.

_AC-15183 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40050) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/40033)_

#### Kan niet alle ongeldige indexen opnieuw indexeren op indexeerapparaten met meerdere thread&#39;s met actieve toepassingsvergrendeling

Deze kwestie herstelde een multi-thread mislukking van de indexeerder wanneer use_application_lock werd toegelaten.
Eerder, werden de sloten van DB verloren tijdens parallelle verwerking, veroorzakend indexeerders om in &quot;werkende&quot;staat te blijven en SQL fouten (lijst niet gevonden) te werpen.
In Magento 2.4.9-alpha3 zorgt de correctie ervoor dat indexeerders correct opnieuw worden gecompileerd met toepassingsvergrendeling ingeschakeld.

_AC-15270 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40102) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/68a45d0a)_

#### Lezen van de module bijwerken en koppelingen naar documenten herstellen

_AC-15340 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/ec9459d0)_

#### [ Logboek niet-gedeclareerde plug-in van 0} Issue {alleen als deze niet is uitgeschakeld]

Deze PR corrigeert en registreert de insteekmodule die niet is gedeclareerd en niet wordt gebruikt (ingeschakeld en ontbreekt).

_AC-15386 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40086) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/40081)_

#### Magento 2.4.8-p2, magento/framework versie 103.0.8-p2: EmailMessage-klasse die een niet-bestaande methode aanroept

_AC-15446 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40170) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/059fd469) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/e9412b24)_

#### [ Magento 2.3.x ] de Patches van Gegevens/van het Schema getAliases () veroorzaakt fouten tijdens `setup:upgrade`

getAliases() veroorzaakt fouten tijdens setup :upgrade, deze PR die het zelfde verhelpt

_AC-15559 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/31396) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38239)_

#### Type &#39;Magento\Customer\Api\Data\GroupInterface&#39; verwacht. Gevonden &quot;Magento\Customer\Model\Group&quot;.

Het opslaan van een klantengroep via GroupRepositoryInterface met GroupFactory veroorzaakte een typefout. Dit probleem is nu opgelost.
Eerder verwachtte de dataopslag GroupInterface, maar groepsmodelinstanties werden overgegaan, resulterend in een fatale fout.
Klantgroepen kunnen nu met succes worden opgeslagen via de opslagplaats door te zorgen voor een correcte implementatie van de interface.
Dit verhelpt de waarschuwingen van winde en runtime fouten wanneer programmatically het creëren van of het bijwerken van klantengroepen.

_AC-6909 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36269)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8349 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37266) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37016)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8350 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37265) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37015)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8359 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37262) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37012)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8362 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37259) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37009)_

#### [ Uitgave ] verwijdert verboden `@author` markering van `Magento_Backup` en `Magento_Bundle`

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8367 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37244) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36979)_

#### [ Repareer veranderlijke naam van 0} Uitgave {in catalogusonderzoek]

Het systeem noemt nu correct variabelen in de module van de onderzoeksmotor, die codehelderheid en onderhoudbaarheid verbeteren. Eerder werd een niet-relevante variabelenaam, $defaultCountry, gebruikt in de zoekmachine module, wat tot verwarring leidde.

_AC-9215 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37810) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/33533)_

#### [ KANS ] Uitgave van de Server die potentieel door Ongeldige S3 Sleutel van de Toegang wordt veroorzaakt

Onjuiste AWS S3-referenties zorgen er niet langer voor dat pagina&#39;s oneindig worden geladen in de winkel.

_ACP2E-3890 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [ KANSEN ] [ de Wolk ] Minify js die niet werkt

De volgende JS-bestanden worden nu volledig en correct geminiateerd wanneer JS-minificatie is ingeschakeld: mage/backend/tabs.min.j, jquery/jquery.validate.min.js en Magento_PageBuilder/js/form/element/validator-rules-mixin.min.js. Als gevolg hiervan werkt de CSS-klassevalidering van Page Builder naar behoren.

_ACP2E-3925 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/47721be6)_

#### Cron job not clearing the database table - cause outage due to Galera crash

Het opschonen van wijzigingstabellen wordt nu in batches uitgevoerd om zware verwijderingsbewerkingen te voorkomen.

_ACP2E-3995 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/52f46328)_

#### Niet-geminieerde JS laadt soms &#39;js minifications inschakelen&#39;

Vóór de correctie, zelfs als u minificatie had toegelaten werden sommige JS dossiers gevraagd zonder het &quot;min&quot;prefix resulterend in 404 statuscode. Na de moeilijke situatie, wanneer de minificatie wordt toegelaten zijn er geen niet-geminificeerde JS gevraagde middelen.

_ACP2E-4058 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Datumkenmerk in aangepaste kenmerkgroep kan geen datumkiezer weergeven in Admin

Pop-up kalender voor datumkenmerken werd buiten het scherm weergegeven bij toewijzing aan aangepaste kenmerkgroepen. Dit probleem is nu opgelost.

_ACP2E-4060 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6dd3fa99)_

### GraphQL

#### GraphQL voor bestelling van klant: ophalen van productcategorieën voor het bijbehorende product is &quot;niet afzonderlijk zichtbaar

Als de bestelling een verborgen product bevatte, zouden de categorieën van de bestelling vóór de correctie een lege array weergeven in het antwoord GraphQl van de Bestelling van de Klant.
Nu, na de moeilijke situatie, zijn de productcategorieën inbegrepen in het antwoord van een GrafiekQl- verzoek van de Bestelling van de Klant zelfs als het product verborgen is.

_ACP2E-3945 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/2a1e1e55)_

#### [ de terugkeer van de Wolk ] getRemoteAddress 127.0.0.1 op Productie

Vóór deze correctie werd het externe adres niet correct bepaald wanneer de toepassingsserver wordt gebruikt. Na de moeilijke situatie wordt het verre adres behoorlijk bepaald gecombineerd met juiste kopbalopstelling in nginx en kopbalconfiguratie.

_ACP2E-3991 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/47721be6)_

#### [ KANTOREN ] bevestigen GQL de uitzondering behandelende gedragsreversie van de orderplaatsing

Achterwaartse incompatibele wijziging voor placeOrder-mutatie is opgelost.

_ACP2E-4031 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/52f46328)_

#### Probleemtoewijzing vertaald bericht naar foutcode bij plaatsen van bestelling via GraphQL

Probleem verholpen waarbij een vertaald uitzonderingsbericht werd gebruikt om de foutcode voor GraphQL-verzoeken toe te wijzen, waardoor een onbekende foutcode voor bekende fouten werd gegenereerd.

_ACP2E-4033 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/fab20b00)_

#### [ CLOUD ] de filter van de Orde van de Klant werkte niet voor Datums

Na de correctie wordt het juiste resultaat geretourneerd wanneer u via GraphQL orders ophaalt met een datumbereikfilter.

_ACP2E-4090 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a1c57b2e)_

#### In ACS2E-4031 aan de orde gestelde kwesties

Vóór de correctie bood de positie van het foutknooppunt geen naadloze compatibiliteit met 2.4.7- en 2.4.9-versies. Na de correctie is het foutknooppunt nu op de juiste wijze geplaatst om beide versies samen te voegen.

_ACP2E-4115 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/e457c5e2)_

#### Bovenliggend element van bundel dat uit voorraad weergeeft, zelfs als het onderliggende item een instantie in een grafische aanroep heeft

Na de correctie retourneert het aanvragen van een productlijst met GraphQL de juiste voorraadstatus voor bundelproducten.

_ACP2E-4168 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a1c57b2e) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, Inventaris/MSI

#### GraphQL mergeCart-mutatieverschillen

Na de correctie wordt in het verzoek van GraphQL de hoeveelheid product correct gecontroleerd, rekening houdend met de voorraadconfiguratie.

_ACP2E-4184 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/5632fb5e)_

### GraphQL, beveiliging

#### Wachtwoord van klant opnieuw instellen via GraphQL houdt geen rekening met de beperkingen

Oplossing voor een probleem waarbij verzoeken om het opnieuw instellen van het wachtwoord van de klant die via GraphQL-mutaties zijn gedaan, niet voldeden aan de beperkingen voor het opnieuw instellen van het wachtwoord die zijn geconfigureerd onder Store > Configuration > Customers > Customer Configuration > Password Options. Deze instellingen worden nu correct toegepast.

_ACP2E-3992 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6dd3fa99)_

### Importeren/exporteren

#### CSV-product importeren: kan de instelling van een staalafbeelding niet ongedaan maken

Vóór de correctie kon u de staalafbeelding van een product niet bijwerken via het importeren van producten. Nu, na de moeilijke situatie, als u de kolom van het productmonster van het beeldbeeld met de gevormde lege teller markeert, zal het beeld aan verborgen worden geplaatst.

_ACP2E-3972 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/2a1e1e55)_

#### Met Product importeren worden lege URL&#39;s gegenereerd voor het winkelbereik

De URL-sleutel van het product in de winkelweergave neemt nu de waarde over die is ingesteld in het standaardbereik als url_key een lege waarde heeft in de gegevensbron met importgegevens. Als u eerder url_key instelt op een lege waarde in de gegevensbron voor importweergave voor een record, wordt url_key overschreven door een lege waarde in dat bereik.

_ACP2E-4038 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/52f46328)_

#### Bij het importeren van het product wordt een fout aangetroffen als een kenmerk met meerdere selecties naar wens is geconfigureerd

Probleem opgelost waarbij het importeren van producten mislukte als een vereist kenmerk van het type multi-select was opgenomen. De gegevensvalidatie wordt nu correct uitgevoerd, zodat het proces voor het importeren van producten met succes kan worden voltooid.

_ACP2E-4057 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a1c57b2e)_

#### [ CLOUD ] de Producten zonder die Achterorden op beheren voorraad nog klanten toestaan om over onze voorraadniveaus in orde te brengen wanneer ingevoerd

Na de correctie is het niet meer mogelijk om een onaanvaardbare waarde te importeren voor het kenmerk &quot;allow_backorders&quot; van het product.

_ACP2E-4116 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a1c57b2e)_

#### Productimport mislukt vanwege een beschrijvingslengte van meer dan 65.536 tekens Validatie

Na de correctie is het mogelijk om productkenmerken te importeren met tekst waarvan de waarden meer dan 65.536 tekens bevatten.

_ACP2E-4119 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a1c57b2e)_

### Inventaris/MSI

#### De bewerking voor het verwijderen van bestanden is niet voltooid

Na de correctie leidt het verwijderen van een bronitem niet tot een volledige herindex en worden alleen de betrokken producten bijgewerkt, waardoor de prestaties toenemen.

_ACP2E-3917 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/ee0bf4ad)_

#### [ MSI ] Geen aanwijzing in admin als de klant asynchroon over Orde werd meegedeeld is Klaar voor Bestelwagen

Toegevoegd aan het bericht van de ordegeschiedenis over de klant werd asynchroon meegedeeld over Orde is Klaar voor Bestelwagen

_ACP2E-3968 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/29653b1d)_

#### Dubbele vragen over voorraadstatus bij het laden van aanhalingstekens

Oplossing voor dubbele uitvoering van query voor catalogvoorraad_stock_status bij het laden van een aanhalingsteken in de winkel, wat tot redundante DB-aanroepen heeft geleid.

_ACP2E-4102 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/fc15a9ae)_

#### Post-Patch ACP2E-4118: Bij wijziging van de voorraaddrempel in Admin worden negatieve verkoopbare hoeveelheden en een afwijkende voorraadstatus veroorzaakt

De voorraadstatus van de voorraad wordt nu automatisch aangepast wanneer de globale inventarisconfiguraties Hoeveelheid, Achterorders en Drempel voor voorraadverlies via import worden bijgewerkt.

_ACP2E-4142 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a1c57b2e) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/5632fb5e)_

### Volgorde

#### Magento 2.4.8 GraphQL - Order items order_date onjuiste opmaak

The order_date field in GraphQL response returned in yyyy-mm-dd format. Dit probleem is nu opgelost.
De order_date wordt nu correct weergegeven in dd-mm-jjjj formaat.

_AC-14431 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39805) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a3b1abc2)_

#### E-mailbericht voor verzending niet verzonden na verzending vanuit de weergave Admin Order, hoewel ingeschakeld in winkelconfiguratie

Het systeem verzendt nu een e-mail met de bevestiging van de verzending aangezien het in de archiefconfiguratie wordt toegelaten waar de orde werd geplaatst.

_AC-14563 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39861) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39897)_

#### Filteren op datum werkt niet vanwege dubbelzinnige veldnamen

In Magento 2.4.7-p6 zou het filteren van het orderraster op datum een fout veroorzaken vanwege verbindingen met Braintree-modules.
De kwestie betrof vragen die zich bij braintree_transaction_details en sales_order lijsten aansluiten wanneer het toepassen van datumfilters.
Adobe Commerce Engineering heeft de zaak onderzocht, maar kon de fout in de omgeving niet reproduceren.
Filteren op datum moet naar verwachting zonder fouten orders met het filter retourneren.

_AC-15037 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40024)_

#### Magento2: geen regel voor speciale acties kan worden gemaakt

Deze PR corrigeert, krijgen we
\Magento\Catalog\Model\ResourceModel\Eav\Attribute model in plaats van \Magento\Catalog\Model\ResourceModel\Eav\Attribute in de methode \Magento\SalesRule\Model\Rule\Condition\Product::loadAttributeOptions

_AC-15358 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/12176) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/30479)_

#### Omleiding van factuur naar 404 annuleren

Annulering van de factuur met het type Not Capture leidt niet langer tot pagina 404.

_ACP2E-4001 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/2a1e1e55)_

#### VerkooparchiefCron-taken veroorzaken problemen met DB-vergrendeling

Vóór de correctie veroorzaakten niet-gebonden DELETE-query&#39;s in order archive cron problemen met Galera. Nu, na de update, worden de schrappingsvragen uitgevoerd met grenzen.

_ACP2E-4010_

#### Probleem met bijgewerkte bestellingen met configureerbare opties die REST API gebruiken

Bestaande productopties op verkooporderitems behouden wanneer een bestelling wordt bijgewerkt via eindpunten van de rest van de app.

_ACP2E-4061 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6dd3fa99)_

### Andere ontwikkelaarsgereedschappen

#### [ Uitgave ] schoonmaakbeurt ongebruikte code.

Het systeem verwijdert nu ongebruikte code voor de ongebruikte importbewerkingen.

_AC-10980 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38424) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/33499)_

#### [ Toegankelijkheid van 0} kwestie ]: WAI-ARIA rollen die verkeerd in menu nesten

Het systeem genereert nu een toegankelijkheid van een vuurtoren zonder dat de WAI-ARIA-rollen fout nesten in een menufout en het rapport moet groen zijn

_AC-15082 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40045) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38617)_

#### Console-fout in e-mailvoorvertoning in Magento-beheerder

Het systeem genereert geen consolefout wanneer we een voorbeeld van de e-mailsjabloon bekijken

_AC-9245 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37820) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37933)_

### Betalingen

#### Onbekende IPN&#39;s van PayPal misbruiken IPN-processor

De IPN-handler negeert nu niet-ondersteunde of onbekende IPN-typen. In plaats van een 500-fout te retourneren, wordt het probleem geregistreerd en wordt de verwerking zonder onderbreking voortgezet.

_ACP2E-4049 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6dd3fa99)_

#### Met PayflowPro opgeslagen kaarttoken is mislukt bij betaling

PayPal PayFlow Pro transactie-id&#39;s (PNREF&#39;s) zijn nu geldig voor gebruik in Reference Transactions voor een vaste periode van 12 maanden. Nadat de vervaldatum is bereikt, wordt de opgeslagen kaart niet meer weergegeven en moet deze opnieuw worden toegevoegd. Voorheen werd de geldigheid bepaald door de vervaldatum van de betaalkaart die in de oorspronkelijke transactie werd gebruikt.

_ACP2E-4064 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/52f46328)_

### Prestaties

#### [ Uitgave ] de controle van het gebruiksgeheime voorgeheugen van de Update onveranderlijk voor statische plaats

Deze PR verbetert de prestaties door de statische inhoud op elke pagina pas te valideren wanneer en tenzij deze wordt gewijzigd.

_AC-15171 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39486) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39484)_

#### [ CLOUD ] Onbekwaam om producten aan categorieën toe te voegen

Verbeterde prestaties wanneer het toevoegen van product aan categorie door Visuele Merchandiser.

_ACP2E-3946 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/29653b1d)_

#### [ Cloud ] cache_invalidate over 10K logboeken

Voorheen werd de cache gewist bij elk bezoek van de PLP of de Kart, wat onnodige prestatieoverhead veroorzaakte. De doelregelcache wordt niet langer ongeldig op deze pagina&#39;s, wat de bladerefficiëntie verbetert.

_ACP2E-4059_

### Prijsstelling

#### Het product wordt opgeslagen, zelfs als de Speciale prijs van Datum later is dan Datum met behulp van een massale actie

Producten konden zonder validatie worden opgeslagen met een ongeldig speciaal prijsdatumbereik. Dit probleem is nu opgelost.
Er wordt nu een foutbericht weergegeven: &quot;Controleer of de datum Tot later is dan of gelijk is aan de datum bij Van.&quot;

_AC-15252 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40113) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/36d4d6fb)_

#### Verzendgegevens komen niet overeen na het voltooien van de PayPal Express-afhandeling voor een verhandelbaar prijsopgave.

Deze kwestie heeft een fout in de verzendkosten opgelost bij het voltooien van een PayPal Express-afhandeling voor een goedgekeurd verhandelbaar prijsopgave.
Voor de correctie werd de verzending onjuist verdubbeld (met $10 in plaats van $5), wat leidde tot opgeblazen totalen.
De correctie in Magento 2.4.9-alpha3 zorgt ervoor dat de juiste verzendkosten worden toegepast

_AC-15280_

#### De speciale prijs wordt niet van kracht bij websites die met verschillende tijdzones zijn gemaakt

Voorafgaand aan de correctie werd de speciale prijsdatum gemaakt in het bereik van de huidige tijdstempel van de winkel. Nu, na de moeilijke situatie, wordt de standaardopslagtijdzone in overweging genomen.

_ACP2E-4002_

#### De normale prijs is niet zichtbaar, ook al wordt een speciale prijs toegepast.

Probleem opgelost waarbij de normale prijs niet werd weergegeven toen een speciale prijs werd toegepast. De normale prijs wordt nu correct weergegeven naast de speciale prijs zoals verwacht.

_ACP2E-4100 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/47721be6)_

### Product

#### Het label &#39;As low as&#39; wordt nog steeds weergegeven voor een configureerbaar product voor testcase AC-6158

Geïmplementeerde en geverifieerde configureerbare producten (P1-P7) met respectieve variaties en categorietoewijzingen. Zorgde voor een correcte weergave van de winkelprijs en een zo laag mogelijk labelgedrag voor producten van categorie C.

_AC-10847 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a3b1abc2)_

#### Extra registratie bij aanvragen van een product via een opslagplaats mislukt

Verbeterde foutberichten voor ProductRepository::get en getById wanneer geen SKU of ID wordt gevonden.
Eerder, verstrekte de uitzonderingen geen context over welke SKU of identiteitskaart de fout veroorzaakte.
Nu, omvat het uitzonderingsbericht ontbrekende SKU of identiteitskaart, die in het zuiveren en ontwikkelaarservaring helpt te verbeteren.
Deze wijziging heeft geen invloed op functies van de API.

_AC-15199 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40090) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1b1baf1d)_

#### Eenvoudige producten niet toegewezen wanneer configureerbaar product bewerkt door beperkte rol

Voorafgaand aan deze moeilijke situatie, als een beperkte admin gebruiker een configureerbaar product zou bewaren dat eenvoudige producten bevat die de admin gebruiker geen toegang tot had, werden verwijderd uit het configureerbare product bij sparen. Nadat het configureerbare product wordt hersteld zoals bewaard van volledig juiste admin.

_ACP2E-4081_

#### [ de generatieprestaties van de Sitemap van 0} wolk {zijn beduidend degraded]

Sitemap-generatie voor producten met afbeeldingen heeft niet langer een exponentiële vertraging. Eerder was het genereren van sitemaps voor winkels waarin het opnemen van afbeeldingen was ingeschakeld, een langdurig proces.

_ACP2E-4153 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/e457c5e2)_

### Aanbieding

#### Fout bij het ophalen van kortingen voor orderitems toegepast_op voor klantenbestelling via GraphQl-klantverzoek

Eerder toen kortingen die_op voor klantenorde via GraphQl klantenverzoek werden toegepast interne serverfout werd waargenomen die nu vast is en de juiste gegevens van de klantenorde met toegepaste korting wordt gehaald

_AC-14888 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39963) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/fe72c407)_

#### Fout bij het ophalen van code voor het coupon van orderitems voor de klant via GraphQl-klantaanvraag

Ophaalopdrachten met coupongegevens via GraphQL hebben een interne serverfout geretourneerd. Dit probleem is nu opgelost.
De query wordt nu uitgevoerd en retourneert de juiste couponinformatie in de reactie.

_AC-14889 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39962) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/fe72c407)_

### SEO

#### Ongedefinieerde arraysleutel in ProductRepository getById

De kwestie kwam voor toen ProductRepository::getById () met een ongeldige identiteitskaart zoals 123abc werd geroepen, die tot een &quot;Undefined seriesleutel&quot;fout leidde.
Na de moeilijke situatie in Magento 2.4.9-alpha3, keren dergelijke verzoeken nu correct een 404 pagina in plaats van het werpen van een uitzondering terug.
QA bevestigd met zowel geldige als misvormde id&#39;s, en er werden geen verdere problemen waargenomen.

_AC-15345 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40146) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/68a45d0a)_

#### [ Cloud ] Sitemap-generatie eindigt nooit

Vóór de correctie kon de sitemap-generatie niet worden voltooid als de catalogus meer dan een miljoen producten bevat. Na de oplossing eindigt de sitemapgeneratie met een lagere geheugentoewijzing en met maximaal één miljoen producten per winkel.

_ACP2E-3902 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/52f46328)_

#### [ de Schakelaar van de opslag van 0} wolk {het Werken van de Schakelaar van de Opslag niet van EN aan FR voor FAQ Pagina]

Probleem verholpen waarbij gebruikers door het schakelen tussen de winkelweergaven werden omgeleid naar de startpagina in plaats van naar de overeenkomstige vertaalde CMS-pagina. De opslagschakeloptie controleert nu of de URL opnieuw wordt opgeslagen in de doelwinkel om de juiste omleiding te garanderen (pagina met veelgestelde vragen in het Engels → pagina met veelgestelde vragen in het Frans).

_ACP2E-4112_

### Staging en voorvertoning

#### Voorvertoning van update bij afspelen wordt afgebroken bij het afrekenen wanneer een ander beheerdomein wordt gebruikt

Een klant kan zich aanmelden en zijn winkelwagentje bekijken in de voorvertoningsmodus van de winkel als de basis-URL van de winkel afwijkt van de URL van de beheerder.

_ACP2E-3906_

#### Dashboard voor inhoud stapelen Tijdstip onjuist

De datumfilters &quot;Begintijd&quot; en &quot;Eindtijd&quot; in het dashboard voor het opslaan van inhoud geven nu de juiste datum en tijd weer. Eerder werd een onjuiste datum en tijd weergegeven nadat de datum en tijd in de datepicker waren geselecteerd

_ACP2E-3969_

#### Bereik toont verschillende Winkelweergave tijdens Voorvertoning voor geplande updateproducten en rubriek

Vóór deze correctie is de voorbeeldkoppeling voor rubrieken en producten niet gegenereerd voor de juiste winkel. Na deze correctie selecteert de voorvertoningskoppeling automatisch de winkel waarop de voorvertoning is gemaakt.

_ACP2E-4053_

### UI Framework

#### [ Uitgave ] verwijdert verboden `@author` markering uit `Magento_Backend`

Deze PR verwijdert de tag `@author` uit de codebase

_AC-8814 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37522) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36976)_
