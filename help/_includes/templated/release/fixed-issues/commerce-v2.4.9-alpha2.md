---
source-git-commit: bfad68a46b9b1a79a702f04efd39129decda1a1c
workflow-type: tm+mt
source-wordcount: '4413'
ht-degree: 0%

---
# Opgeloste problemen in Adobe Commerce (v2.4.9-alpha2)

## Opgeloste problemen in v2.4.9-alpha2

We hebben 118 problemen opgelost in de Adobe Commerce 2.4.9-alpha2-kerncode. Hieronder wordt een subset van de opgeloste problemen in deze release beschreven.

### API&#39;s

#### Speciale prijs tot op heden wordt ten onrechte gevalideerd voor applySpecialPrice

Het systeem werkt prima met betrekking tot de speciale prijs en de speciale prijs van het product zal verlopen op de datum die door de beheerder of het derdepartijsysteem door REST API wordt bepaald

_AC-13130 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39169) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39690)_

#### Onjuiste aanvraaginstantie of parameters veroorzaken &quot;Interne serverfout&quot;

_AC-746 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32784) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/f1adb44e)_

#### Volgorde &quot;base_row_total&quot; en &quot;row_total&quot; geven prijs van één item weer in REST API-reactie

De REST api-reactie voor orderdetails bevat nu correcte waarden voor de kenmerken &quot;base_row_total&quot; en &quot;row_total&quot; voor het geval meerdere items werden geordend

_ACP2E-3874 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/4ca73607)_

### API&#39;s, Order

#### [ CLOUD ] de informatiekwestie van de Orde met rij totale verschijning voor orde 000075568

Hiermee wordt het probleem verholpen waarbij de waarde row_total_incl_tax in de bestelling-API-reactie werd geretourneerd als een restwaarde van bijna nul in plaats van 0,00 wanneer een item volledig werd gedisconteerd.

_ACP2E-3950 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/462ede94)_

### Account

#### Probleem bij het bijwerken van de e-mail van de klant in Admin Panel met ö en .swiss domain

_AC-13409 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39394) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/d3ea191d)_

#### Schakelaar voor abonneetoewijzing voor nieuwsbrief werkt niet per website/winkel

Het systeem handelt abonnement met nieuwsbrief correct af wanneer wij veelvoudige websites/verhalen hebben toen het op globaal niveau werd onbruikbaar gemaakt

_AC-14283 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39751) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39752)_

#### Een voorwaarde voor het klantensegment &quot;Product bekeken&quot; vervangen

_AC-14542_

#### [ Uitgave ] Verwijderde e-mailonthulling

Het systeem geeft nu een foutbericht weer waarin een onjuiste e-mail wordt aangegeven als de ingevoerde e-mail niet nodig is om de account te bevestigen, ongeacht of de klant bestaat of niet.

_AC-14561 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39574) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39570)_

### Gebruikersinterface van beheerder

#### De FPT-waarde in de winkelwagentje en de productpagina zijn verschillend voor dezelfde configuraties voor eenvoudige producten

_AC-13066 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/8953613e)_

#### Meerdere opties voor selecteren/selecteren van kenmerken kan niet worden opgeslagen wanneer de stalenmodules zijn uitgeschakeld

_AC-13071 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/8953613e)_

#### De FPT-waarde in de winkelwagentje en de productpagina zijn verschillend voor dezelfde configuraties voor een dynamisch product

_AC-13075 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/8953613e)_

#### Aanwijskleur niet toegepast op statische rasters in beheer

De aanwijskleuren worden nu toegepast zoals u had verwacht op de rijen statische beheerrasters.[ GitHub-35358 ](https://github.com/magento/magento2/issues/35358)

_AC-2916 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35358) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/35384)_

#### Beperkte beheergebruikers kunnen de status van het updateproduct niet massaal bijwerken

De aangepaste beheerder kan de status van een updateproduct massa&#39;s geven omdat het een eigenschap op websiteniveau is. De status wordt alleen bijgewerkt op de websites waartoe de beperkte beheerder toegang heeft.

_ACP2E-3772_

#### [ Staging2 ] Opgeslagen kaarten zijn niet zichtbaar op Admin paneel

Hiermee wordt het probleem verholpen waarbij de betalingsoptie &quot;Opgeslagen kaart&quot; niet meer wordt weergegeven in het formulier voor plaatsing van de achterste bestelling na een upgrade.

_ACP2E-3830 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7accebfa)_

### B2B

#### validatie van bedrijfsvelden mislukt voor uitchecken door gast

_AC-14987 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40011) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/f1adb44e)_

### Bundel

#### Uitsluiten van gekleurde JS-bestanden van Editor uit gebundelde uitvoer over thema&#39;s

_AC-15128 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/43648891) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/2bc584af)_

### Winkelwagentje en Afhandeling

#### Validaties voor Gegroepeerde productvoorkeuren ontbreken

Het systeem werkt nu goed en geeft een validatiefout weer wanneer we een negatieve hoeveelheid en maximale hoeveelheid proberen toe te voegen

_AC-13524 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39479) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39480)_

#### Voorvoegsel van de gast niet Opgeslagen aan Adres 2.4.8 van het Citaat

_AC-14705 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39915) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/f1adb44e)_

#### [ Uitgave ] Vastgestelde prijs op citaatpunt in plaats van base_price

Het systeem verwerkt de prijs van het aanhalingsteken correct ingesteld op base_price in plaats van de prijs als er meerdere valuta&#39;s op één website op de frontend staan

_AC-9985 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38094) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36878)_

#### [ Recente Orden van de Wolk 1} verschijnen niet in andere opslagmening als de orden op één archiefmening worden gecreeerd]

Het probleem waarbij op de pagina Mijn account geen recente bestellingen van andere winkelweergaven in dezelfde winkel werden weergegeven, is opgelost. De logica voor het ophalen van bestellingen is bijgewerkt om ervoor te zorgen dat de volgorde in alle weergaven van winkels consistent wordt weergegeven. Deze logica sluit aan op het gedrag van de pagina Mijn bestellingen.

_ACP2E-3807 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a20a6ff2)_

#### hoeveelheid weergegeven als  0 in het gedeelte Winkelwagentje voor klanten van de beheerder terwijl BUNDLE-producten worden toegevoegd  

In de sectie Winkelwagentje in Klantactiviteiten wordt nu het juiste aantal weergegeven. Eerder werd de hoeveelheid weergegeven als 0.

_ACP2E-3872 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3ad96f6a)_

### Winkelwagentje en afhandeling, GraphQL

#### Fout bij het toewijzen van foutcode aan een foutcode bij het plaatsen van een order via GraphQL

GraphQL roept om een orde voor een nonexistent of inactief karretje nu correct terug te keren CART_NOT_ACTIVE of CART_NOT_FOUND foutencodes in alle archiefmeningen, die een kwestie bevestigen waar de vertaalde foutenmeldingen eerder in een UNDEFINED code resulteerden.

_ACP2E-3942 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7accebfa)_

### Winkelwagentje en afhandeling, GraphQL, Inventaris/MSI

#### is_available, kenmerk in CartItemInterface retourneert false, zelfs als de verkoopbare voorraad hoog is

Het is_available attribuut keert waar terug wanneer de verkoopbare voorraad hoog is. Eerder geeft het altijd false.

_ACP2E-3885 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3ad96f6a)_

### Catalogus

#### Fout in bereik in URL-bron van catalogus (_getCategories)

Deze PR voegt een fallback aan standaardwerkingsgebied toe als er geen waarde op het archiefwerkingsgebied in categorie URL middel wordt bepaald.

_AC-11011 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38393) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38394)_

#### [ Uitgave ] Controle als OpenGraph prijs kan tonen

Het systeem werkt prima als we een plug-in gebruiken die de prijs verbergt en deze wijzigingsprijs niet zichtbaar is in de OG-tag.

_AC-11635 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38512) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38510)_

#### [ Bug ] REST API: De speciale prijzen van de update plaatsen geen waarden voor alle opslagmeningen

_AC-13671 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39521) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [ \Magento\ConfigurableProduct\Model\Product\Type\Configurable] PHP fout niet vermeld

Deze PR Verandert een lusvariabelenaam om de &quot;_cache_instance_product_ids&quot;gegevens over het bepaalde product correct toe te voegen dat op verdere vraag moet worden gebruikt.

_AC-14159 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39641) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39642)_

#### [ Belangrijkste 1} ] CLOUD [ Beeld die meer dan 400GB van schijfruimte resizing]

Na de correctie genereert de opdracht `catalog:images:resize` die wordt gebruikt met de markering —skip_hidden_images geen afbeeldingscache voor websites waarop geen afbeeldingen aanwezig zijn.

_ACP2E-3869 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9ad7d277)_

#### Opgegeven landID bestaat niet - Ierland (IE)

Na de correctie zijn Ierse postcodes beschikbaar om te zoeken naar ophaallocaties.

_ACP2E-3932 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/4ca73607) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/d2f1d6c6)_

### Catalogus, prestaties

#### Categorieën in admin laden erg langzaam

De prestaties bij het laden van categorieën zijn aanzienlijk verbeterd. Eerder duurde het zo lang om de categorie te laden die een time-outprobleem heeft veroorzaakt.

_ACP2E-3891 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/4ca73607)_

### Catalogus, prijzen

#### Onjuiste korting op catalogusprijsregel toegepast op het onderliggende product

Hiermee wordt het probleem verholpen waarbij de catalogusprijsregel voor de variatie wordt overschreven door het bovenliggende configureerbare product, in het geval dat beide regels dezelfde prioriteit hebben.

_ACP2E-3693 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a20a6ff2)_

### Catalogus, zoeken

#### Verzoek van RestApi &#39;/rest/default/V1/Categorieën?searchCriteria%5Bpage_size%5D=1&#39; mislukt vanwege een time-outfout

_AC-13358 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7bdafaa2)_

### Inhoud

#### Na de upgrade naar magento 2.4.7 p2 ziet u de geüploade bestanden niet meer in de mediagalerie

_AC-13262 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39275)_

#### Als u een galerie-afbeelding volledig verwijdert uit een afbeelding, worden de rollen/typen van het bereik ingesteld (basis/klein/miniatuur) en nadat u de &quot;oude&quot; rollen/typen opnieuw hebt toegevoegd, worden deze weergegeven

Het systeem werkt zoals verwacht in het opslagbereik de beelden erven de rollen/types van het nieuwe toegevoegde beeld zoals per het standaardwerkingsgebied

_AC-13556 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39481) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39680)_

#### [ Filter van 1} Kleine insect van het Comité Admin ] kan niet raken wanneer de gebiedswaarde `listing component` bevat`\`

Het systeem werkt prima als we paginatitel met slash filteren (bijvoorbeeld Magento\Store)

_AC-13661 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39513) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39535)_

#### Logoverstroming op de CMS-pagina met de id 0 bestaat niet

Het systeem werkt zoals verwacht na het creëren van admin gebruiker en wanneer wij een nieuwe pagina system.log creëren heeft geen foutenmeldingen

_AC-14254 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39743) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39746)_

#### Cataloguskoppelingswidgets gebruiken onjuiste URL

Het systeem verwerkt nu correct widgets nadat de koppeling naar het catalogusproduct en de cataloguscategorie is toegevoegd en bevat nu ook de juiste URL&#39;s in de HTML-bron

_AC-14437 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39464) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39710)_

#### De component Product van de Bouwer van de pagina werkt niet als de gebruiker geen toestemming Widget heeft

Vóór de correctie genereerde de pagina een algemene fout tijdens het openen van een widget zonder machtigingen en werd een GIF voor &quot;laden&quot; weergegeven. Na de correctie wordt nu een modaal venster weergegeven met &quot;Sorry, u hebt machtigingen nodig om deze inhoud weer te geven.&quot; bericht.

_ACP2E-3664 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Page Builder-productwidgetbestelling wordt niet toegepast in GraphQL

Hiermee wordt het probleem verholpen waarbij de GraphQL-query-reactie ‘route’ geen producten in de juiste sorteervolgorde heeft geretourneerd in een inhoudssoort van Page Builder-producten.

_ACP2E-3898 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/bd9181b6)_

#### Probleem met prijsstelling op niet-Engelse winkelvelden vanwege ICU-bibliotheekversie

Na de correctie wordt de productprijs correct weergegeven in de landinstelling Hebreeuws (Israël).

_ACP2E-3938 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7accebfa)_

#### Configuratie van gecastreerd ontwerp van winkelcode bijwerken

Oplossing van de kwestie waar het bijwerken van de code van de archiefmening de montages van de Configuratie van het Ontwerp wegens het configuratiecache niet behoorlijk verfrist ontruimde.

_ACP2E-3941 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/462ede94)_

### Kader

#### Fout wanneer looppas bevelopstelling :upgrade met de trekker van douaneOB

_AC-11487 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38481)_

#### Entiteitsformulier voor website/groep/winkel kan niet worden uitgebreid met meerdere waarden van formulierelementen voor extensiekenmerken

Met deze PR kunnen formulierelementen met meerdere waarden gegevens verzenden naar website/groep/winkel-formulier.

_AC-11657 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/24070) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/24094)_

#### [ Uitgave ] verwijdert het gebruik van de werkingsgebiedoplosser

Deze PR verhelpt de URL-instellingen van Admin globaal in plaats van de huidige winkel

_AC-11736 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38566) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38554)_

#### De blootstelling van de Versie van Magento via de route van de Opstelling met standaardConfiguratie Nginx

Het systeem werkt nu zoals verwacht en geeft de exacte versie van Magento waarop de site wordt uitgevoerd niet weer

_AC-13205 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39227) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39228)_

#### [ Uitgave ] citaat van refactor bevestigt methode

Deze PR bevat verbeteringen in de leesbaarheid van de doValidate-methode.

_AC-13214 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38230) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38219)_

#### Magento option —magento-init-params nooit gebruikt bij het uitvoeren van cli?

_AC-13231 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39248) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/132b9e68)_

#### getItemsByColumnValue onjuiste typedeclaratie

Het systeem definieert nu correct de invoerparameter $value als een primitief type, niet als een array, in de functie getItemsByColumnValue, zodat de functie de verwachte verzameling retourneert. Eerder, als een serie met één enkele waarde als inputparameter werd gebruikt, zou de functie ongeldig terugkeren en IDEs zou het als fout merken.

_AC-13240 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/33070) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/33120)_

#### Cachetoetsen die zijn gekoppeld aan FPC op Magento 2.4.7 multi-store-implementaties

_AC-13719 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39456) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/ae6f305b)_

#### Magento Rest API toont PII

_AC-13904 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39336)_

#### Onvolledige indexering werkt niet meer voor klanten met een groot aantal updates

_AC-14424 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7bdafaa2)_

#### Onderzoek &quot;gebruik strikt&quot;is onnodig binnen modules

_AC-14517 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/77c589a6)_

#### Na het downloaden van het verzendlabel zien we een bepaald bedrag aan verzendkosten dat niet overeenkomt met de verzendprijs.

_AC-14560_

#### MView-mechanisme negeert fouten bij het uitvoeren van de trigger op ongepaste wijze

_AC-14567 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/ae6f305b)_

#### [ Uitgave ] vermijd veel onnodige uitzonderingen tijdens de samenvoeging van lay-outXML laden

Deze PR introduceert een nieuwe functie (voor de compat van B/C beschrijven wij niet beschermde _loadXmlString) om te laden en geen uitzondering te werpen

_AC-14580 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39877) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37570)_

#### [ Uitgave ] Bevordering van constructoreigenschappen gebruiken in moduleVault grafiek Ql

Deze PR vervangt constructoreigenschappen door eigenschappenbevordering in de module VaultGraphQl

_AC-14616 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39900) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36996)_

#### [ Verwijderde de codeovertolligheid van de 0} Uitgave voor module frontend lay-outs.]

Deze PR verwijdert de redundantie van code voor themalay-outs voor Magento_MSRP-, Magento_LoginAsCustomerAssistance-, Magento_Newsletter- en Magento_Sitemap-modules voor frontend-layouts.

_AC-14625 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/30673) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/30644)_

#### [ Uitgave ] verwijdert code met betrekking tot Microsoft IIS

In deze PR wordt de code voor Microsoft IIS aangepast volgens de documentatie bij de systeemvereisten van Magento, waarin staat dat het Microsoft Windows-besturingssysteem niet wordt ondersteund

_AC-14702 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39910) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39894)_

#### Syntaxisfout Magnifier.js

De functie van de systeemvergroting zou moeten blijven werken zoals het vroeger werkte en magnifierOptions zou niet in globaal werkingsgebied beschikbaar moeten zijn

_AC-14722 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36200) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39321)_

#### Modus Uitgebreide back-up in CLI-opdracht `setup:db:status`

_AC-14807 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7bdafaa2)_

#### SMTP-mail wordt verzonden met TLS en 2.4.8

_AC-14883 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39947) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/3717e6cb) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/8b453942) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/d3ea191d)_

#### [ kwestie ] de kwestie van de Oplossing gelijktijdig in statische inhoud stelt op

Deze PR verhelpt een bug waarbij meerdere gelijktijdige processen hetzelfde themapakket afhandelen, afhankelijk van de manier waarop de thema&#39;s met hun ouders zijn gedefinieerd.

_AC-14944 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39990) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39954)_

#### [ Uitgave ] verwijdert erfenisverenigbaarheidscode voor PHP versies &lt; 8.1

Deze pull request verwijdert code die ontworpen was om uitgevoerd te worden op PHP &lt;8.1.
Ook, verwijder controles voor PHP_VERSION_ID contactbeschikbaarheid, aangezien het in alle PHP versies beschikbaar is

_AC-14971 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39891) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39882)_

#### FPC werkt niet bij aanmelding

_AC-14999 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/40007) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/)_

#### [ Uitgave ] verbetert fout behandelend SchemaBuilder

Deze PR verbetert de fout berichten behandeling van db schema. Het helpt ons om kwestie zonder zware zuivering te identificeren.

_AC-15020 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39816) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39799)_

#### Integratietestfout bij SYNC PR voor 2.4.9-alpha2-ontwikkeling als gevolg van de aanpassing van CliStateTest

_AC-15136 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/2d0f8066)_

#### Foutopsporing van het type PHP8.1

De bijbehorende producten worden nu geïnitialiseerd naar een lege array in plaats van naar false wanneer de strikte verwerkingsmodus niet actief is of wanneer productinformatie beschikbaar is. Deze verandering zorgt ervoor dat de daaropvolgende logica die daarmee verband houdt, zich consistent gedraagt, waardoor de stabiliteit en voorspelbaarheid van het productbereidingsproces worden verbeterd.

_AC-6017 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35808) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/35842)_

#### [ Uitgave ] verwijdert verboden `@author` markering uit kader (deel 3)

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8343 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37270) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37020)_

#### [ Uitgave ] Bevordering van het de aannemersbezit van het Gebruik in module verzendt vriendengrafiek ql

Het systeem gebruikt nu de bevordering van constructoreigenschappen in de module &#39;send vriend&#39; GraphQL, wat de leesbaarheid van de code verbetert en de complexiteit vermindert. Eerder, gebruikte de module eigenschappen die talrijke lijnen bezet, die de code complexer en minder leesbaar maken.

_AC-8346 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37235) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37197)_

#### [ Uitgave ] verwijdert verboden `@author` markering uit `Magento_Downloadable`

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8355 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37251) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37001)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de kwaliteit en consistentie van de code worden verbeterd. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8358 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37264) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37014)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8360 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37261) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37011)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, zodat u over een schonere en meer gestandaardiseerde code beschikt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8361 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37260) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37010)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8363 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37258) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37008)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8375 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37257) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37007)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8376 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37256) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37006)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8400 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37254) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37004)_

#### [ Uitgave ] verwijdert verboden `@author` markering

Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, waardoor de algemene codekwaliteit toeneemt. Eerder was de aanwezigheid van dit label in bepaalde modules in strijd met de vastgestelde coderingsnormen.

_AC-8401 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37255) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37005)_

#### [ Uitgave ] verbetert Uitbreidbaarheid van de Generatie van Service URL

Het systeem staat nu voor aanpassing van de functie van de Generatie van de Dienst URL via plugins toe, die een meer houdbare benadering van wijzigingen bevorderen. Voorheen werd deze functie aangepast via voorkeuren, die mogelijk niet zo efficiënt of onderhoudsbaar waren.

_AC-8813 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37404) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37403)_

#### Probleem met upgrade 2.4.7-p5 vanwege nieuwe validatie

Probleem verholpen in de SchemaBuilder-klasse waarbij een niet-gedefinieerde arraysleutel &#39;kolom&#39; een crash veroorzaakte tijdens het maken of bijwerken van het schema. Dit gebeurde wanneer het verwerken van lijstgegevens die geen &quot;kolom&quot;sleutel omvatten.

_ACP2E-3871 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9ad7d277)_

#### PHP8.4 Deprection Error: E_USER_ERROR after Upgrade to Adobe Commerce 2.4.8

De oplossing heeft geen invloed op klantgerichte scenario&#39;s.

_ACP2E-3963 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7accebfa)_

### Framework, zoeken

#### Openssearch 2.19.1 illegal_argument_exception on one-price categorieën

Openssearch genereert niet langer een illegal_argument_exception op de categorieën die alle producten met dezelfde prijs bevatten. Eerder, heeft het deze uitzondering &quot;[ van ] parameter kan niet negatief zijn&quot;.

_ACP2E-3896 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3ad96f6a)_

### GraphQL

#### customerOrders grafisch retourneert een fout wanneer het product is verwijderd

De CustomerOrders grafisch verzoek werpt niet meer een fout zelfs het product in de orde werd geschrapt. Eerder werd de fout &quot;Interne serverfout&quot; gegenereerd.

_ACP2E-3936_

#### De items in de lijst met identieke items worden niet gedeeld tussen de weergaven in één website in GraphQL-aanvraag

Vóór de correctie werden de items in de wenslijst gefilterd met de id van de winkel. Na de correctie worden de items in de wenslijst gefilterd op website.

_ACP2E-3987 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/2a252ae6)_

### GraphQL, product

#### Ontbrekende media_type in afbeelding van product in MediaGalleryInterface

Het GraphQL-verzoek voor MediaGallery bevat nu het veld &quot;types&quot; voor productafbeeldingstypen. Eerder bestond dit veld &quot;types&quot; niet in de aanvraag van MediaGallery GraphQL.

_ACP2E-3880 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3ad96f6a)_

### Inventaris/MSI

#### Geen winkel beschikbaar na omleiding naar homepage en uitchecken

Eerder geselecteerde winkel wordt nu vooraf geselecteerd bij Verzending in Winkel selecteren als de klant naar de betalingspagina navigeert, vervolgens terugkeert naar de homepage en ten slotte terugkeert naar de afhandelingspagina. Eerder werd de geselecteerde winkel in de &quot;Winkel kiezen&quot; gewist nadat u herhaaldelijk naar de uitcheckpagina was teruggekeerd.

_ACP2E-3793 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a20a6ff2) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/62c0d79b)_

### Volgorde

#### AbstractAddress setData(&#39;custom_attributes&#39;, AttributeValue []) breekt customAttributes

_AC-10568 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/31644)_

#### v2.4.7-p1 Magento reorder -1 volgordenummers

Het systeem werkt zoals verwacht en na herschikking vanaf de achtergrond zal het ordernummer uniek zijn 8 cijfers

_AC-12854 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39089) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39399)_

#### Uploaden van aangepaste optie voor product verliezen bij uitchecken met betalingsmethode voor Adobe-creditcard

_AC-14306 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39647)_

#### Status van bestelling blijft bij verwerking behouden

Voordat de correctie werd uitgevoerd, werd bij het bestellen van een bundelproduct met de optie &quot;Samen verzenden&quot; ingeschakeld, niet automatisch overgeschakeld naar &quot;Voltooien&quot; na factuur en verzending. Na de correctie schakelt de orderstatus automatisch over naar &quot;complete&quot; nadat de bestelling is gefactureerd en verzonden.

_ACP2E-3947 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/2a252ae6)_

#### [ Magento OOTB-code van 1} Cloud - E-mail de kwestie van de Opstelling van het Malplaatje]

Voordat de oplossing werd gevonden, waren de e-mails bij het gebruik van asynchrone e-mailverzendingen niet in overeenstemming met de order van de winkel. Na deze correctie wordt nu de juiste e-mailbestelling voor verzending via e-mail naar de winkel verzonden.

_ACP2E-3998 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/462ede94)_

### Andere ontwikkelaarsgereedschappen

#### [ Verkeerde het typewenk van de kwestie ] voor het beschermde lid $_urlHelper

Het systeem lost nu de verkeerde typewenk met correct op, die ook in aannemer wordt gebruikt

_AC-10716 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32503) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32496)_

### Prestaties

#### [ Uitgave ] Update Store.php

Deze PR verbetert de prestaties door de huidige winkelresolutie over te slaan.

_AC-14791 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39949) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38717)_

### Prijsstelling

#### Prijs is altijd 0 voor bundproduct-items zonder dynamische prijs voor rest-API voor bestelling

_AC-11925 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38687) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7da46f52)_

### Product

#### Procentuele korting op de tier-prijs en op de regel voor catalogusprijs berekend op de oorspronkelijke prijs zonder geselecteerde opties.

_AC-12004 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38750)_

#### Magento 2.4.7 minAllowed missing product order quality

Het systeem werkt prima en de paginabron geeft de minimale hoeveelheid van het product correct weer

_AC-12909 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39142) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39480)_

#### Magento-uitzondering tijdens uitvoeren van Magento Payflow Pro-test

_AC-13681_

#### Probleem met het raster Aanpasbare opties op de productpagina in het deelvenster Beheer

Het systeem werkt zoals verwacht wanneer we aanpasbare opties maken met vervolgkeuzelijst voor tekst

_AC-14003 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39640) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39694)_

#### De optie Pagina afdrukken van aanvraaglijst werkt niet

_AC-14711_

#### Alle punten van andere klanten vergelijken lijsten worden toegewezen aan de klant na het programma openen via admin

Eerder, toen een beheerder de &quot;Login als Klant&quot;eigenschap in het achterste eind gebruikte, werden de producten van de vergelijkingslijst van een eerder het programma geopende klant verkeerd toegewezen aan de momenteel nagemaakte klant.  Na de moeilijke situatie laadt de vergelijkingslijst correct voor de correcte het programma geopende klant.

_ACP2E-3818 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/462ede94)_

### SEO

#### Het bijwerken van product url_key via REST API genereert geen 301 URL herschrijven

Wanneer u de URL-sleutel van het product bijwerkt via de REST-API en de instelling &quot;Permanent omleiden voor URL&#39;s maken als URL-sleutel gewijzigd&quot; op Ja instelt, wordt bij het opnieuw schrijven van de product-URL een omleiding van de oude URL naar een nieuwe URL gemaakt.

_ACP2E-3900 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/462ede94)_

### Verkoop

#### De status Volgorde is verdwenen tijdens het selecteren van de waarde in het vervolgkeuzemenu Volgorde

_AC-15010_

### Beveiliging

#### Gebundelde/samengevoegde JS maakt geen deel uit van SRI-hashes

Voorafgaand aan de moeilijke situatie produceerde de bundel of de samengevoegde dossiers werden niet toegevoegd aan de lijst van haasjes SRI. Nu, worden de dossiers behoorlijk toegevoegd aan de hakken SRI.

_ACP2E-3854 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/4ca73607)_

### Verzending

#### [ KANSEN ] - controleert de de kernmodule Magento_Fedex voor een geldig-actief teken alvorens een verzoek te verzenden om nieuwe te krijgen?

Adobe Commerce doet niet langer veel aanvragen voor de FedEx API-service voor het toegangstoken. Eerder, alhoewel het toegangstoken nog geldig is, doet Adobe Commerce altijd nieuwe verzoeken aan FedEx API die een tarief beperkende kwestie veroorzaakten.

_ACP2E-3930 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/4ca73607)_

### Staging en voorvertoning

#### Kan de geplande productupdate niet voorvertonen met rubriekmachtigingen ingeschakeld

Vóór de correctie werd een product dat in de toekomst moet worden ingeschakeld, niet weergegeven in de voorvertoningsmodus. Nu wordt deze ook weergegeven als de huidige status is uitgeschakeld.

_ACP2E-3786 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7accebfa)_

#### Bereik toont verschillende winkelweergave tijdens de voorvertoning

Vóór de correctie kan een gefaseerde updatevoorvertoning van inhoud van cms-blokken en cms-pagina zijn geopend in een andere opslag dan de opslag die is toegewezen op het cms-blok of de pagina wanneer deze wordt benaderd vanuit het Dashboard voor het opslaan van inhoud. Als na de correctie voor het cms-blok of de pagina alleen een specifieke opslag is toegewezen in de testupdate, wordt de voorvertoning van het dashboard voor het opslaan van inhoud geopend met de juiste opslag geselecteerd.

_ACP2E-3815_

#### Ontbrekende validatie voor veld kortingswaarde regel catalogusprijs

Eerder, werd het disconto_amount gebied in de het opvoeren planningsupdate niet correct bevestigd met de huidige bevestigingsregels. Nochtans, na het toepassen van de moeilijke situatie, zal het disconto_amount gebied geschikt worden bevestigd.

_ACP2E-3867 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/462ede94)_

### Belasting

#### Onjuist totaal van de Volgorde, wordt de ronde niet toegepast op de prijsberekening.

Het systeem wordt nu correct verwerkt bij het berekenen van de prijs_after_reduction, korting_amount en de belastingen.
het werkelijke totaal van de bestelling

_AC-11389 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38455) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39687)_

### Testkader

#### [ Uitgave ] negeert lib/internal/Magento/Framework/App/Test/Unit/_files/app/etc/nl...

Het systeem negeert nu het bestand &#39;env.php&#39; dat wordt gegenereerd wanneer eenheidstests worden uitgevoerd, zodat de status van de it na het uitvoeren van tests schoon blijft. Eerder, zou het runnen van eenheidstests een nieuw dossier &quot;env.php&quot;produceren, die de status van de it veroorzaken om een nieuw gevonden dossier te tonen en het te maken vies lijken.

_AC-13293 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39304) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37631)_

#### [ Uitgave ] de kwestie van de de integratietest van de Oplossing met onderschepper

Het systeem herkent en behandelt nu correct \Magento\TestFramework\App\Config\Interceptor in de integratietest, die ervoor zorgt dat de test tot de noodzakelijke gegevens kan toegang hebben zelfs wanneer een stop op de klasse bestaat. Eerder was het systeem er niet in geslaagd om de mogelijkheid van \Magento\TestFramework\App\Config te verklaren \Magento\TestFramework\App\Config\Interceptor was, resulterend in een fout toen het proberen om tot het $data bezit toegang te hebben.

_AC-13305 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39324) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37187)_

#### [ Uitgave ] MFTF: Het voorleggen van E-mail aan de Vorm van de Vriend met toegelaten captcha

De testcase heeft betrekking op de functionaliteit van het formulier &quot;E-mail naar vriend&quot; wanneer CAPTCHA is ingeschakeld. Hierbij wordt ervoor gezorgd dat het proces voor het verzenden van formulieren correct werkt met onjuiste en correcte CAPTCHA-waarden.

_AC-13492 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39462) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32830)_

#### [ TestFramework ] Gebruik van TestCase::getTestResultObject is ongeldig aangezien punit v10

_AC-13502 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39463)_

#### Milieu-specifieke eenheidstests mislukkingen in AC 2.4.7-p3

Dit probleem verhelpt problemen met eenheidstests die niet in alle versies en omgevingen worden gereproduceerd. Eerder werden enkele eenheidstests niet hersteld omdat er verschillende bibliotheekversies waren of omdat er functionaliteit in een latere versie was toegevoegd.

_ACP2E-3712 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9ad7d277)_

### Tools/DataMigrationTool

#### [ ATLH ] Fatale fout wanneer er geen verschillen zijn

Fatale fout wordt niet meer weergegeven wanneer er geen verschil meer is om weer te geven

_ACP2E-3901_

### UI Framework

#### WYSIWYG is leeg in dynamische rijen

_AC-12336 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38893) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7bdafaa2)_

#### [ kwestie ] mime type van Reparatie

Het systeem handelt het mime-type en -type voor gif-afbeelding correct af en corrigeert deze

_AC-8001 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36899) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36669)_

#### [ Uitgave ] vermijd directe toegang tot de lijst van overzichten Ajax

Het systeem handelt correct en vermijdt directe toegang tot de revisielijst Ajax

_AC-9381 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37920) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/33876)_

### Upgrades - Upgrade Compatibility Tool

#### Vervangen functionaliteit: maken van dynamische eigenschap Magento\Framework\Acl:$_roleRegistry

_AC-12343 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37469)_
