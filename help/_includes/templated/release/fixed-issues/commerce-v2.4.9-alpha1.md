---
source-git-commit: 2f471a1bc1cbf31076aeb67ceaee289196841cd4
workflow-type: tm+mt
source-wordcount: '3326'
ht-degree: 0%

---
# Opgeloste problemen in Adobe Commerce (v2.4.9-alpha1)

## Opgeloste problemen in v2.4.9-alpha1

We hebben 84 problemen opgelost in de Adobe Commerce 2.4.9-alpha1-kerncode. Hieronder wordt een subset van de opgeloste problemen in deze release beschreven.

### API&#39;s

#### Async Bulk Operation blijft open voor async.magento.configurableproduct.api.optionrepositoryinterface.save.post

De bulk API eindpunten zullen nu een fout als het verzoeklichaam geen Serie is, zo vereist dat bulkpuntsleutels opeenvolgende aantallen zijn die van 0 beginnen. Eerder werd de status van bulkobjecten niet bijgewerkt vanwege de willekeurige objectsleutel die in het bulkverzoek werd ingediend.

_ACP2E-3544 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9608ca21)_

#### [ CLOUD ] API REST insect op is_subscribed waarde die niet van de huidige opslag overweegt gebruikend searchCriteria

Met de API REST-query van de klant wordt de juiste &quot;is_subscribed&quot;-waarde opgehaald uit de correcte opslag met behulp van searchCriteria
Eerder heeft de query van de klant van de API REST geen opslag overwogen bij het ophalen van is_subscribed&quot;-waarde.

_ACP2E-3621 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9608ca21)_

#### async.operations.all kan veelvoudige ingangen voor 1 SKU tot stand brengen

Gelijktijdige verzoeken om hetzelfde product op te slaan en bij te werken, worden nu geserialiseerd om rasvoorwaarden te voorkomen die kunnen leiden tot gegevensinconsistentie of dubbele producten

_ACP2E-3744 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/520f9e30)_

### Account

#### [ de verrichting van de Wolk ] van de Schrapping is verboden voor huidige gebiedsfout tijdens de verwezenlijking van de klantenrekening

Nadat de oplossing die een klant met een ongeldig adres opslaat een bericht terugkeert die de reden voor invaliditeit in plaats van irrelevant beschrijft &quot;de verrichting van de Schrapping is verboden voor huidig gebied&quot;.

_ACP2E-3791 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6ea61121)_

### Gebruikersinterface van beheerder

#### [ Uitgave ] verbetert gebruikerservaring met rolboom

Met deze pull-aanvraag voegt u knoppen toe om alle elementen samen te vouwen, alle elementen uit te vouwen en vertakkingen uit te vouwen met geselecteerde items. Deze functionaliteit is vergelijkbaar met de functionaliteit in de categoriestructuur (Catalogus -> Overzicht -> Categorieën)

_AC-14020 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39654) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36511)_

#### Symfony\Component\Mime\Exception\LogicException: De header &quot;Sender&quot; moet een instantie zijn van &quot;Symfony\Component\Mime\Header\MailboxHeader&quot; (met &quot;Symfony\Component\Mime\Header\MailboxListHeader&quot;)

_AC-14520 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39823) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1e14bd72)_

#### Een functie bieden voor het massaal verwijderen van belastingtarieven via het raster

Admin-gebruikers kunnen nu meerdere belastingtarieven tegelijk verwijderen uit het raster Admin Tax Rates.  [ GitHub-33399 ](https://github.com/magento/magento2/issues/33399)

_AC-2238 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/33399) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/33484) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/5cd64dd0)_

#### De prijsregel voor winkelwagentjes met voorwaarde dat SKU geen rekening houdt met de &quot;voorloopnullen&quot; in de SKU (sku: 01234 is hetzelfde als 1234)

Het systeem behandelt nu correct de prijsregel van de Kar met voorwaarde SKU rekening houdt met &quot;belangrijke nul&quot;in SKU

_AC-9428 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37919) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39525)_

#### Probleem met standaardgedrag voor kenmerkoptie-optiewaarde voor Multiselect

Voorafgaand aan de correctie werden de standaardwaarden voor veelvoudige optiekenattributen niet behoorlijk bewaard. Na de correctie worden de waarden nu op de juiste wijze opgeslagen in de database.

_ACP2E-3523 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9608ca21)_

#### Ondertiteling in menu Backend-beheer wordt niet weergegeven

Alle titels van de hoofdmenugroepen worden nu correct weergegeven. Eerder werd de titel van de groep niet weergegeven als de tweede of derde kolom van het hoofdmenu slechts één groep koppelingen bevatte.

_ACP2E-3540_

#### Probleem tijdens het verplaatsen van de producthoeveelheid naar het winkelwagentje van de beheerder

Wanneer u een bestelling maakt van de beheerder, verdwijnen de producten in de klantenkar op de zijbalk niet wanneer ze aan de bestelling worden toegevoegd.

_ACP2E-3563 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c8ba4ab1)_

### Admin UI, B2B

#### B2B-aanmelding als koptekst van klant heeft nog steeds Magento-branding

Eerder staat in de koptekst van de winkel &quot;U bent nu verbonden als &lt;naam klant> op &lt;naam winkel>&quot; met Magento-branding. Deze is nu gefixeerd en de header wordt weergegeven met ADOBE-branding.

_AC-14361 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/fadcfa8b)_

### Admin UI, Content

#### Uitzondering &quot;Kan uitvoering voor paden met media-elementen niet maken&quot; tijdens het invoegen van de afbeelding

Nadat u de waarden voor Maximumbreedte en Maximumhoogte van de configuratie voor optimalisatie van de medialagalerie hebt verwijderd, treedt de fout niet meer op tijdens het optimalisatieproces voor de afbeelding.

_ACP2E-3781 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/520f9e30)_

### Admin-gebruikersinterface, beveiliging

#### Zwak wachtwoordbeheer

De admin-gebruiker kan niet worden opgeslagen wanneer u hetzelfde wachtwoord gebruikt. Eerder is het bestand opgeslagen zonder de juiste validatie.

_ACP2E-3657 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/df92debe)_

### Gebruikersinterface, beveiliging, opslaan en voorvertonen

#### Handelingenlogboeken voor het opvoeren van inhoud

In de Action Logs worden nu de activiteiten van de Staging Update weergegeven. Eerder werd het logbestand voor het bijwerken van de testupdate niet opgenomen in de logboeken voor beheeracties.

_ACP2E-3679_

### B2B

#### Plaatsingsorder werkt niet aan Doorgaan om af te rekenen via een verhandelbaar prijsopgave met de betalingsmethode PayFlow Pro-creditcard

_AC-11973_

#### Bericht met succes nadat naam van offerte is gewijzigd, verdwijnt af en toe

_AC-13447_

#### De totaalberekening is exclusief het belastingbedrag

De bestelling bevat correcte totalen wanneer plaatsen van bestaande inkooporder met grensoverschrijdende handel ingeschakeld zijn.

_ACP2E-3727_

#### De toewijzing van categorieën in een gedeelde B2B-catalogus via de REST-API verloopt traag

De prestaties zijn nu aanzienlijk verbeterd wanneer u categorieën in B2B verwijdert. Eerder duurde het lang voordat de toewijzing van categorieën in de gedeelde B2B-catalogus ongedaan werd gemaakt.

_ACP2E-3796_

#### Prestatieprobleem met nieuwe installatiepatroon in B2B

Oplossing van het prestatieprobleem waarbij het upgraden van de Magento_Company-module na het bijwerken naar B2B 1.5.2 veel te lang duurde bij het verwerken van een groot aantal records (~100.000+) in de company_structure-tabel.

_ACP2E-3850_

### Winkelwagentje en Afhandeling

#### Magento 2.4.7-update (mini)kart zonder decimale hoeveelheid toegestaan

Magento handelt nu correct als we de hoeveelheid bijwerken met decimalen van mini cart als de landinstelling NL (Nederlands) was

_AC-13238 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39236) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39669)_

#### [ Uitgave ] Update subtotal.phtml

Het systeem werkt subtotal.phtml met de correcte spatiëring bij

_AC-13907 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39619) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39612)_

#### Kan de bestelling niet bij de gast plaatsen

_AC-14241 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/27217d0e)_

#### Verlopen permanente aanhalingstekens worden niet opgeschoond door een uitsnijdvak sales_clean_quotes

De verlopen permanente aanhalingstekens worden nu gewist wanneer de &#39;persistent_clear_expired&#39; snijtaak wordt uitgevoerd. Eerder werden de verlopen permanente aanhalingstekens niet gewist door een andere uitsnijdtaak.

_ACP2E-3493 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/11be3dff)_

#### &quot;Er is iets fout gegaan&quot; bij het afrekenen voor inactief bedrijf

Voorafgaand aan de correctie werd de logout-actie niet correct uitgevoerd op de winkelwagenpagina als het aangemelde gebruikersbedrijf niet langer was ingeschakeld. Nu, als het bedrijf niet meer beschikbaar is, wordt de logout behoorlijk uitgevoerd.

_ACP2E-3541 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/df92debe)_

#### De selectie van adressen wordt niet opgeslagen wanneer wij &quot;Controle uit met Meerdere Adressen&quot;

Voorafgaand aan de correctie bij het annuleren van de optie voor meerdere verzendingen, was het adres niet vooraf geselecteerd bij het terugkeren naar meerdere verzendingen. Het standaardadres wordt nu vervangen door een van de selecties die in het scherm met meerdere verzendingen zijn gemaakt.

_ACP2E-3646 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6ea61121)_

### Winkelwagentje en afhandeling, SEO

#### Onjuiste URL voor kaartencode in e-mail bij aankoop op de secundaire website

Eerder richtte de multi-store opstelling en giftekaart voor niet gebrek altijd de gift kaarteis op de standaardwebsite. Nadat deze correctie is toegepast, leidt de e-mail de claimkoppeling van de creditcard om naar het juiste bereik of de juiste website.

_ACP2E-3699_

### Winkelwagentje en afhandeling, verzending

#### [ Belangrijkste ] de regel van de Prijs van de Kar respecteert MultiShipping

Voorafgaand aan de toepassing van deze correctie was de regel van de cartprijs voor producten voor meerdere verzendingen niet correct van toepassing toen de voorwaarden voor onderselectie werden toegepast en de mogelijkheid tot gratis verzending werd ingeschakeld. Sinds de correctie is toegepast, functioneert de regel van de winkelwagenprijs voor meerscheepskaarten nu echter naar behoren.

_ACP2E-3666 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogus

#### Cache fpc dupliceren voor dezelfde pagina met dezelfde query

Het systeem identificeert en gebruikt nu correct het zelfde Volledige Geheime voorgeheugen van de Pagina (FPC) voor pagina&#39;s met de zelfde vraagparameters, ongeacht hun orde of navolgende karakters. Zo voorkomt u een onnodige toename van de grootte van de paginacachemap. Eerder, zou het systeem een verschillende herkenningsteken FPC voor de zelfde pagina tot stand brengen als de orde van de vraagparameters verschillend was of als er navolgende karakters waren, die tot een toename van de de omslaggrootte van het paginacachegeheugen leiden.

_AC-10722 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38269) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38270)_

#### Ontbrekende indexering van vereiste kolommen in de tabel catalog_product_entity_int

De ontbrekende indexering van vereiste kolommen in de tabel catalog_product_entity_int is toegevoegd

_AC-10844 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38315) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38316)_

#### De productpagina bevat een fout vanwege herschrijvingen van URL&#39;s

De productpagina wordt nu geladen wanneer de URL wordt herschreven

_AC-2950 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35371) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39670)_

#### [ Bug van de Wolk ] toen het toevoegen van producten aan categorie

De paginering en het label voor het aantal records werken nu goed wanneer u producten aan een categorie toevoegt via het popup-raster. Eerder trad het laden van slechts één pagina met items die gelijk zijn aan het paginaformaat problemen op met het vervolgkeuzemenu voor het selecteren van items.

_ACP2E-3526_

#### indexer_update_all_views fout met MAGE_INDEXER_THREADS_COUNT

Correctie van probleem met MAGE_INDEXER_THREADS_COUNT > 2 met index voor klantsegment.

_ACP2E-3538 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9608ca21)_

#### Uitzondering tijdens het toevoegen van &quot;Combinatie van voorwaarden&quot; in de widgevoorwaarde voor producten van de Bouwer van de Pagina

Het probleem is opgelost door een controle toe te voegen om ontbrekende of onvolledige voorwaarden over te slaan. Eerder werden foutlogbestanden gegenereerd vanwege de verwerking van onvolledige voorwaarden in het systeem.

_ACP2E-3545 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/11be3dff)_

#### Browser crasht tijdens laden van kenmerkset

Browser loopt niet meer vast op de bewerkingspagina voor kenmerksets als er meer dan 4k-productkenmerken zijn

_ACP2E-3633 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38810) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/b12ffe36)_

#### [ CLOUD ] Product URL herschrijft niet gecreeerd voor Nieuwe Opslag: Go Live Blocker

URL van product herschrijft voor nieuwe winkel is gemaakt.
Eerdere bewerking eindigde met geheugenlek of met time-out.

_ACP2E-3669 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/df92debe)_

#### Standaardwaarde kenmerk voor opties werkt niet

Eerder, toen wij de standaardwaarde van een product veranderden selecteerde attributen, verscheen het als serieelement met de vorige waarden. Nadat deze moeilijke situatie wordt toegepast, wanneer wij een waarde van het productattribuut bijwerken zal het als één enkel element bij eav_attribute lijst bewaren.

_ACP2E-3688 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/520f9e30)_

#### Validatie van kaartje mislukt bij bewerken vanwege duizend scheidingsteken

Correctie van uitgave met producttype van cadeau-kaart wanneer het bedrag van de cadeau-kaart 1000 of meer is.

_ACP2E-3704_

### Catalogus, GraphQL, Zoeken

#### Grafische producten retourneren uitgeschakelde categorieën in de categoriecategorieën

Nadat de moeilijke moeilijke gehandicapte categorieën niet voor de productenverzoek GraphQl zijn teruggekeerd.

_ACP2E-2885 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b12ffe36)_

### Catalogus, product

#### [ Willekeurige Bug ] de lib van Fotorama wordt niet geladen

Het systeem zorgt er nu voor dat de Fotorama-bibliotheek correct is geladen, zodat alle gekoppelde afbeeldingen naar behoren in de galerie met afbeeldingen kunnen worden weergegeven. Eerder was alleen de eerste afbeelding zichtbaar vanwege een probleem met de bibliotheek Fotorama dat niet correct werd geladen.

_AC-12124 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/45b51c9c) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/27217d0e)_

### Inhoud

#### Het plaatsen van csp_whitelist.xml in thema werkt niet en leidt tot intermitterende kwestie

Geïmplementeerde caching van CSP whitelist per websitegebied.

_AC-13069 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38933) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39672)_

#### Fout: scriptfout voor &quot;Magento_Catalog/js/validate-product&quot; voor pagebuilder voor inhoud voor beheerders met producten laden

Deze PR corrigeert de scriptfout voor catalogAddToCart tijdens het bewerken van de pagebuilder met de productvoorwaarde

_AC-13891 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39604) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39677)_

#### Selectie blokkeren in widgets met dezelfde id

Het systeem verwerkt nu correct het selecteren van blokken tijdens het maken van widgets wanneer we dezelfde id-blokken hebben

_AC-14132 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39692) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39722)_

#### Tabelvoorvoegsel wordt niet in aanmerking genomen

_AC-14556 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39847) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Kan afbeelding met relatief kleine breedte niet uploaden

Het systeem kan de afbeelding niet meer vergroten of verkleinen met een relatief kleine breedte tot de hoogte.

_ACP2E-3558 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9608ca21)_

#### Onjuist configuratiepad voor stijlconfiguratie van externe opslagpaden

Na de correctie heeft het instellen van de stijlconfiguratie voor het externe opslagpad invloed op de daadwerkelijke configuratie van de AWS S3-padstijl.

_ACP2E-3734 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/df92debe)_

### Kader

#### Compilerende code van uitgeschakelde module.

Deze trekkingsverzoek ontsnapt aan gehandicapte modules alvorens codecompilatie.

_AC-10933 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38241) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39723)_

#### Magento_Theme title.phtml template is ongeldig voor PHP 8.2

Deze pull-aanvraag verhelpt een probleem wanneer CMS-pagina die is gemaakt met de null-kop zoals in PHP 8.x die null doorgeeft aan trim(), uitzondering genereert: Afgekeurde functionaliteit: trim(): null doorgeven aan parameter #1 ($string) van type string

_AC-12856 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39092) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39398)_

#### Wanneer het gebruiken van dossieropslag voor de slotleverancier, krijgen wij een steeds groeiende folder van dossiers zonder enige schoonmaakbeurt

Dit trekkingsverzoek introduceert een nieuwe uitsnijdtaak die één keer per dag wordt uitgevoerd en zoekt naar vergrendelingsbestanden die de laatste 24 uur niet zijn gewijzigd en die dus veilig kunnen worden verwijderd. Hierdoor blijft de inhoud van de map met vergrendelingsbestanden onder controle.
Deze cron baan zal slechts iets uitvoeren wanneer de slotleverancier wordt gevormd om dossiers te gebruiken, niet wanneer één van anderen wordt gebruikt (gegevensbestand - het gebrek, zoökeeper of geheime voorgeheugen)

_AC-13367 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39369) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39372)_

#### [ Uitgave ] Schoonmaakbeurt: gebruik geen waarde van de ongeldige terugkeer van methodevraag.

Deze PR doet kleine schoonmaakbeurten. Soms noemden we methoden die niets retourden (void) en gebruikten we die resultaatwaarde. Dat is echt niet nodig.

_AC-13664 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39524) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39516)_

#### [ ] PHPDOC [ Correctie slechte phpdoc voor Magento\Framework\Message\ManagerInterface]

Deze PR corrigeert de ongeldige phpdoc voor \Magento\Framework\Message\ManagerInterface en verwijdert alle dubbele phpdoc in \Magento\Framework\Message\Manager (gebruik inheritdoc syntaxis).

_AC-14312 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39593) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39153)_

#### Verwijderd bètaminimale stabiliteit uit composer.json

Verwijderd bètaminimale stabiliteit uit composer.json

_AC-14450 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1cbbf187)_

#### allow_parallelle_generation moet worden ingesteld via de omgevingsvariabele

Na de correctie kan de omgevingsvariabele &quot;MAGENTO_DC_CACHE__ALLOW_PARALLEL_GENERATION&quot; worden gebruikt om de configuratie &quot;allow_parallelle_generation&quot; in te stellen.

_ACP2E-3673 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b12ffe36)_

#### [ Cloud ] Veranderend het type van lijstkolom van Int in Decimaal gebruikend db_schema.xml- dossier in Magento 2 resulteert in Fouten

Het wijzigen van het gegevenstype van de kolom werkt niet correct. Eerder werd een fout gegenereerd: het kenmerk &#39;identity&#39; is niet toegestaan.

_ACP2E-3709 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/df92debe)_

#### Ondersteuning voor nieuwe valuta (XCG) in Adobe

Caraïbische Gulder (XCG) wordt toegevoegd aan de lijst met valuta&#39;s.

_ACP2E-3790 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/520f9e30)_

### GraphQL

#### GraphQL Response for Order placement bevat geen uitzonderingsbericht

Vorige wijziging die fouten in een andere indeling retourneert, is hersteld. Mogelijke fouten worden nu op een consistente manier geretourneerd, niet door het GraphQL-schema te verbreken. Dit moet worden toegevoegd als bekend BIC, goedgekeurd door PM in ACP2E-3399

_ACP2E-3399 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9608ca21)_

#### GraphQL Response for Order placement is gedeeltelijk gelokaliseerd

Fouten die door placeOrder GraphQl-mutatie zijn geretourneerd, zijn niet volledig gelokaliseerd. In een meertalige context worden fouten nu goed vertaald.

_ACP2E-3506 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9608ca21)_

#### Gelijktijdige aanroepen om GraphQL API opnieuw te ordenen - Dezelfde producten toegevoegd aan verschillende rijen

Hiermee wordt het probleem verholpen waarbij gelijktijdige aanroepen naar de GraphQL API opnieuw ordenen ertoe leiden dat dezelfde producten als verschillende rijen worden toegevoegd, wat leidt tot inconsistenties in de gegevens.

_ACP2E-3774 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### updateCustomerEmail GraphQL-mutatie (e-mailadres wijzigen) activeert de e-mailmelding niet

Eerder werd e-mail niet verzonden naar klanten nadat hun e-mailadressen op hun accounts waren bijgewerkt. Nadat de oplossing is toegepast, ontvangen klanten nu e-mailmeldingen nadat ze hun e-mailadressen hebben bijgewerkt.

_ACP2E-3785 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c8ba4ab1)_

#### Dynamisch kenmerk niet bijgewerkt in Cadeauregister via updateGiftRegistry Mutation

Eerder, vóór deze moeilijke situatie door de updateGiftRegistry mutatie, werd het douanekenmerk van het giftenregister niet gewijzigd of bijgewerkt door de mutaties van GraphQL. Nadat deze moeilijke situatie is toegepast, kan het dynamische attribuut van het giftenregister met succes door de updateGiftRegistry mutatie worden bijgewerkt.

_ACP2E-3805 - [ GitHub kwestie ](https://mcstaging.briscoes.co.nz/)_

### Importeren/exporteren

#### [ Uitgave ] Copyright: verandering &quot;het kopiëren&quot;aan &quot;het kopiëren&quot;

PR corrigeert de kleine kopie om de spelling van &quot;kopiëren&quot; te corrigeren

_AC-13300 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39311) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39307)_

#### REST-eindpunt Product Import Json valideert de verplichte velden niet

Het veld Naam is nu vereist wanneer u nieuwe producten maakt via het importproces (admin of API). Voorafgaand aan de moeilijke situatie, kon u nieuwe producten zonder naam tot stand hebben gebracht, zou dit de admin interface gebroken hebben en ongeldige producten gecreeerd.

_ACP2E-3660 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/df92debe)_

#### Ontbrekende optie Websitefilter in exportproces

Het is nu mogelijk om producten via websites te filteren wanneer u producten maakt die u exporteert.

_ACP2E-3720 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/520f9e30)_

#### Duplicaat van AC-13913 - Statische kenmerkreiniging asynchroon.

Na de correctie is er geen &#39;Undefined array key &quot;apply_to&quot;&#39;-fout wanneer er meerdere instanties van de map \Magento\CatalogImportExport\Model\Import\Product\Type\AbstractType worden gemaakt.

_ACP2E-3752 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/520f9e30)_

### Inventaris/MSI

#### Winkelafhandeling voldoet niet aan de maximale zoekstraal wanneer het adres bij afhandeling wordt gewijzigd

Nu vooraf geselecteerde winkel in Winkel kiezen wordt bijgewerkt als het verzendadres verandert. Eerder, toen een opslag vooraf werd geselecteerd, veranderde het niet zelfs als het nieuwe verzendadres niet binnen de straal van de geselecteerde opslag is

_ACP2E-3728 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/07620383)_

### Volgorde

#### Kan null niet retourneren voor niet-nullable veld \&amp;quot;AppliedCoupon.code\&amp;quot; onverwachte uitgave

_AC-14484 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39841) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/97b2ea42)_

#### [ Wolk ] sommige Inline Javascript werkt niet na verbetering aan magento 2.4.6-p7

Als u in Beheer op de knop Verwijderen klikt in &quot;Toevoegen aan bestelling door SKU&quot;, wordt de SKU nu verwijderd. Als u in het verleden op de knop &quot;Verwijderen&quot; in &quot;Toevoegen aan bestelling door SKU&quot; klikte, werd de SKU niet verwijderd.

_ACP2E-3515_

#### gift_cards geserialiseerde gegevens zijn inconsistent in de sales_order lijst

gift_cards gegevens in sales_order lijst wordt nu correct geserialiseerd. Eerder, werd het geserialiseerd telkens als de orde werd bijgewerkt.

_ACP2E-3662_

### Volgorde, prijzen

#### Bij het maken van de return geeft Admin een onjuist valutasymbool weer

Bij een installatie van meerdere websites met verschillende valuta&#39;s (EUR/USD/GBP) wordt op de pagina met de productselectie voor retourzending in de administratie nu het juiste valutasymbool weergegeven. Eerder werd het standaardvalutasymbool weergegeven.

_ACP2E-3658 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/df92debe)_

### Andere ontwikkelaarsgereedschappen

#### Toegankelijkheid van vuurtoren is mislukt

Het systeem gaat nu over met toegankelijkheidsscore van 100

_AC-12783 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39054) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39164)_

#### Captcha storefront config uitschakelen laadt nog steeds captcha js-bestanden

Het systeem laadt nu geen captcha js-bestanden wanneer we captcha voor storefront hebben uitgeschakeld

_AC-14267 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32987) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39154)_

### Verpakken

#### [ Repareren magento/magento-coding-standard dependency+ page-builder]

_ACPLTSRV-6383_

### Betalingen

#### [ Uitgave ] Correctie offline factuur vangst (404)

Hierbij wordt de fout van 404 pagina&#39;s gecorrigeerd terwijl facturen voor offline betalingsmethoden worden vastgelegd door Magento-beheerders

_AC-1336 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39298) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39297)_

### Prestaties

#### De module van de Toestemmingen van de categorie kan caching verhinderen

Controllers van derden worden nu correct in cache geplaatst met klantsegmenten

_ACP2E-3721_

### Product

#### De Inzameling van het product - addMediaGalleryData roept getSize wanneer de inzameling misschien of zal worden geladen (kan telling gebruiken om een extra vraag van DB te vermijden)

Deze PR vermindert de extra vraagvraag gebruikend count() als de productinzameling reeds wordt geladen wanneer het roepen van Grafiek van het Product met media_gallery gebied inbegrepen in het.

_AC-13055 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39111) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39681)_

#### [ 2.4.8 ] Geen callbacks die voor cron job catalog_product_alert worden gevonden

_AC-14494 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39800) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1bc2d6d0)_

#### Langzame query wordt uitgevoerd wanneer productwidget wordt opgenomen via pagebuilder

De query voor het maken van productwidgets, inclusief product-SKU&#39;s, is geoptimaliseerd.

_ACP2E-3449 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/df92debe)_

#### Afbeeldingen van producten waarvan de grootte niet wordt aangepast wanneer ze als configureerbaar product worden toegevoegd

Eerder waren de afbeeldingen die via Configuraties in het beheerpaneel werden toegevoegd, niet in overeenstemming met de maximale uploadgrootte, wat tot inconsistenties en beheerproblemen kan leiden. Er is nu een oplossing geïmplementeerd om ervoor te zorgen dat de grootte van de afbeeldingen tijdens het uploaden automatisch wordt aangepast om te voldoen aan de maximale groottebeperking, het proces te stroomlijnen en systeemstandaarden te handhaven.

_ACP2E-3504 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/df92debe)_

### Verzending

#### Document moet worden bijgewerkt voor %-uitvoering die niet correct is in het officiële document

Het devdoc voor DHL Rest API-ondersteuning is bijgewerkt

_AC-14507_

#### [ DHL ] - handvat Facultatieve Afmetingen in de Reguliere Montages van de Grootte en de Variantie van de Prijs tussen de Integratie van REST en van XML API

_AC-14601 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1e3bde4c)_

#### Uitzondering tijdens maken van UPS-verzendlabel

Fixed Warning: Array to string conversion during UPS Shipping Label creation

_ACP2E-3676 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b12ffe36)_

### Staging en voorvertoning

#### Als u een voorvertoning van een geplande update weergeeft, wordt de eerste winkelweergave in alfabetische volgorde geopend in plaats van in de winkelweergave van interesse.

Vóór de correctie wordt de voorvertoning van een geplande update in alfabetische volgorde geopend in de eerste winkelweergave in plaats van de toegewezen winkelweergave.
Na de correctie wordt de voorvertoning nu correct geopend in de winkelweergave die is toegewezen aan de CMS-bloktestupdate.

_ACP2E-3671 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b12ffe36)_

#### Uitsnijdgedrag Staging_apply_version - special_price genegeerd

Na de correctie worden de totalen van de offertes opnieuw berekend nadat de speciale prijs is gewijzigd door de geplande productupdate.

_ACP2E-3674_

### Belasting

#### Het BTW-bedrag wordt niet bijgewerkt wanneer cadeauverpakking uit het winkelwagentje wordt verwijderd

_AC-14637_
