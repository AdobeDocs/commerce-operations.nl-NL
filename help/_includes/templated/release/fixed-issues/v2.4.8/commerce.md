---
source-git-commit: 3f6776e5dbbf167bbb7b4f831f9a7d4cfbfc0b74
workflow-type: tm+mt
source-wordcount: '28398'
ht-degree: 0%

---
# Opgeloste problemen in Adobe Commerce (v2.4.8)

## Opgeloste problemen in v2.4.8

We hebben 582 problemen opgelost in de Adobe Commerce 2.4.8-kerncode. Hieronder wordt een subset van de opgeloste problemen in deze release beschreven.

### API&#39;s

* _AC-10042_: /V1/de transacties REST API keert fout terug wanneer parent_txn_id = txn_id
   * _nota van de Reparatie_: Het systeem behandelt nu correct de ouder en kindconcepttransacties waar identiteitskaart van de oudertransactie het zelfde als transactieidentiteitskaart is, verhinderend een oneindige lijn wanneer het vragen van het /V1/transacties REST API eindpunt. Eerder zou dit scenario resulteren in een fatale fout als de maximale uitvoeringstijd wordt overschreden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-11878_: [Graphql] Type probleem in 2.4.7
   * _Fix-opmerking_: het systeem verwerkt nu correct gehele getallen in de functie GetCustomSelectedOptionAttributes bij het uitvoeren van een GraphQL-query, waardoor typegerelateerde fouten worden voorkomen. Voorheen resulteerde het starten van een GraphQL-query die gebruikmaakte van GetCustomSelectedOptionAttributes met een integer-argument in een typefout.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38662>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38663>
* _AC-3223_: Speciale karakters in categorie url_key (wanneer gecreeerd via REST API)
   * _nota van de Reparatie_: Eerder in category_url_key speciaal karakter is daar niet na de moeilijke situatie het speciale karakter in category_url_key toont
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/35577>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c699c206>
* _ACP2E-2703_: REST API die orden van een andere website tonen. 
   * _nota van de Reparatie_: Het systeem steunt nu werkingsgebied geoorloofde toegang voor REST API admin tokens en Magento_Sales endpoints, die ervoor zorgen dat REST API slechts orden toont die admin toegang heeft tot. Eerder gaf de REST API opdrachten van alle websites weer, ongeacht de toegewezen website van de beheerder.
* _ACP2E-2755_: Probleem met rest api na het inschakelen van 2FA Duo
   * _Fix note_: 2FA met Duo-beveiligingsoptie genereert nu de juiste handtekening voor Rest API
   * _Bijdrage GitHub-code_: <https://github.com/magento/security-package/commit/412fa642>
* _ACP2E-2927_: [REST API:] Gebruik de standaardwaarde in de winkelweergave en blijf niet aangevinkt na het toevoegen van configuraties voor een configureerbaar product
   * _Fix-opmerking_: Het probleem is opgelost door te zorgen voor correcte database-items voor de aanpasbare opties voor een niet-standaardwinkel. Het selectievakje voor de aangepaste opslag in de sectie &quot;Beheer > Catalogus > Product Bewerken > Aanpasbare opties&quot; is eerder uitgeschakeld omdat de database niet correct is, zelfs als de titel van de optie voor de aangepaste opslag gelijk bleef aan de standaardwinkel.
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
   * _Fix-opmerking_: Asynchrone en synchronisatiebewerkingen mislukten eerder vanwege fouten bij het opslaan van producten als sku ontbreekt in de payload. Na de oplossing mislukken de asynchrone en gesynchroniseerde API-bewerkingen van het product Save Rest met een relevant uitzonderingsbericht.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [CLOUD] Kan de basisprijzen niet bijwerken met behulp van REST API (de waarde van &#39;value_id&#39; in &#39;catalog_product_entity_decimal&#39; wordt niet correct verhoogd.)
   * _Opmerking oplossen_: Vóór deze oplossing, wanneer rest api /rest/default/V1/products/base-prices werd aangeroepen, werd de increment-id ten onrechte verhoogd, waardoor er een gat tussen de waarden ontstond. Na de oplossing wordt de increment-id verhoogd zoals verwacht, stapsgewijs. Ook het value_id veldbereik werd vergroot.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3460_: De punten van de orde zijn niet zichtbaar in creditmemo e-mails voor de API POST V1/order/:orderId/restitutie
   * _nota van de Reparatie_: Eerder, vóór deze moeilijke situatie, wanneer een klant een creditnota van een API verzoek creeert die send_email op de hoogte brengt, bevat het niet het net van de productdetails. Na deze correctie stuurt de klant een API-aanvraag voor creditnota en zoekt hij naar de gegevens van het product die in de e-mail worden weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3486_: De standaardwaarden worden niet geplaatst voor datum en tijdattributen met producten RestAPI
   * _Nota van de Reparatie_: De standaardwaarden plaatsen nu behoorlijk voor datum en datum en tijdattributen via RestAPI
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>

### API&#39;s, winkelwagentje en kassa

* _ACP2E-3343_: Kritieke 500 Fout: Magento\Framework\Webapi\Exception Verwant aan Accept de Kopbal van HTTP
   * _nota van de Reparatie_: Na de moeilijke situatie, is er geen kwestie met het specificeren van de &quot;Accepteer&quot;kopbal.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>

### API&#39;s, GraphQL

* _ACP2E-3348_: geen graphQl beschikbaar voor het intekenen van Punten van de Terugkeer voor klant
   * _nota van de Reparatie_: Eerder aan de moeilijke situatie, kon het attribuut van de klant beloning_warning_notification niet door de mutatie van GraphQL en de vraag van Rest API worden bijgewerkt. Nu kan het zelfde als klantenattribuut worden bijgewerkt beloning_update_notification.

### API&#39;s, GraphQL, Tax

* _AC-12060_: Zowel Luma (Rest API) als Grahql berekent geen belastingen wanneer slechts de code van het ZIP wordt verstrekt.
   * _nota van de Reparatie_: Het systeem berekent nu correct belastingen wanneer slechts een postcode wordt verstrekt, die nauwkeurige belastingramingen voor zowel Luma (Rest API) als GraphQL verzekeren. Voorheen werden alleen verzendramingen berekend en werden geen belastingen opgenomen wanneer alleen een postcode werd verstrekt.

### Account

* _AC-10782_: Het adresvorm van de klant staat willekeurige code op de naamgebieden toe
   * _nota van de Reparatie_: Het systeem bevestigt nu de input in de gebieden Voornaam en Achternaam in de vorm van het klantenadres, die het gebruik van willekeurige code verhindert. Eerder stond het systeem het gebruik van willekeurige code in deze gebieden toe zonder een fout te werpen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38331>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38345>
* _AC-10886_: update van het Admin Wachtwoord.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38352>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-10990_: mijn rekening voegt adresneerstorting toe op sparen
   * _nota van de Reparatie_: Het systeem bewaart nu correct klantenadressen zelfs wanneer het gebiedgebied niet wordt getoond, verhinderend een neerstorting tijdens het sparen proces. Als u eerder een adres probeert toe te voegen of te bewerken zonder veld voor een weergegeven gebied, treedt er een uitzonderingsfout op.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38406>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38407>
* _AC-11718_: Richt lijn opnieuw wanneer URL in hoofdletters heeft
   * _nota van de Reparatie_: Het systeem zet nu automatisch karakters in hoofdletters in URLs in kleine letters om, die een herleidingslijn verhinderen wanneer het toegang tot van homepage. Eerder, zou het hebben van karakters in hoofdletters in Veilige Basis URL een ononderbroken omleidingslijn veroorzaken wanneer het proberen om tot de homepage toegang te hebben.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38538>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38539>
* _AC-11755_: middlename (&#39;s) niet bewaard voor gastrekeningen
   * _nota van de Reparatie_: Het systeem bewaart nu correct de middennaam voor gastrekeningen tijdens controle, die het in het e-mailmalplaatje toegankelijk maken. Eerder werd de middelste naam niet opgeslagen in de prijsopgave en was deze niet toegankelijk in de e-mailsjabloon voor gastaccounts.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38593>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/39067>
* _AC-11919_: Admin: De Knopen van de Acties van de pagina drijvende linkerzijde in plaats van recht
   * _nota van de Reparatie_: Het systeem richt nu correct de Knopen van de Acties van de Pagina aan de rechterkant van de kleverige kopbal in het admin paneel, dat de professionele blik en het gevoel verbetert. Eerder zweven deze knoppen onjuist naar de linkerkant van de kleverige koptekst.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38701>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/44cef3a9>
* _AC-11999_: dev :di: infofout in magento 2.4.7
   * _nota van de Reparatie_: Het systeem toont nu correct constructorparameters wanneer het uitvoeren van het dev :di: info bevel, verhinderend om het even welke fouten voor te komen. Eerder resulteerde het uitvoeren van deze opdracht in een fout als gevolg van een niet-overeenkomend type in het argument.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38740>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-13000_: Login als klant opt-in checkbox niet vertaalbaar
   * _Fix-opmerking_: het systeem staat nu toe dat de velden &quot;Inloggen als klant opt-in checkbox&quot; en &quot;Inloggen als klant&quot; tooltip worden ingesteld op het bereik &quot;Winkelweergave&quot;, waardoor vertalingen voor verschillende winkelweergaven mogelijk zijn. Voorheen werden deze velden alleen ingesteld in het bereik &quot;Website&quot;, waardoor vertalingen voor individuele winkelweergaven werden voorkomen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/32329>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/32359>
* _AC-14299_: Front-end UI Homepage in mijn profiel Dropdown is knop is er niet.(met tussenpozen)
* _AC-6071_: De klant wordt het programma geopend maar het tonen van 404 fout in front-end.
   * _nota van de Reparatie_: De storefront klantendashboardpagina laadt nu zoals verwacht wanneer een klant het programma opent. Voorheen konden klanten inloggen, maar op deze pagina verscheen een 404-fout. [ GitHub-35838 ](https://github.com/magento/magento2/issues/35838)
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/35838>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/36263>
* _ACP2E-2791_: Kan de attributeninformatie van de Klant niet opslaan in Admin geeft klantensectie uit;
   * _nota van de Oplossing_: De opslag identiteitskaart van de klant wordt nu behoorlijk uitgevoerd per websitewerkingsgebied voor de beheerder klant geeft vorm uit.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/488c1034>
* _ACP2E-3115_: [ de Wolk ] kan geen klant via API tot stand brengen wanneer de Privé Verkoop wordt toegelaten
   * _nota van de Reparatie_: De klant kan nu door voor authentiek verklaarde admin gebruiker evenals met voor authentiek verklaard integratietoken via REST api worden gecreeerd wanneer de websitebeperking wordt toegelaten.
* _ACP2E-3329_: Na het programma openen, zijn de producten die aan de vergelijkingslijst als gastgebruiker worden toegevoegd niet zichtbaar.
   * _Bevestig nota_: De producten die aan product werden toegevoegd vergelijken lijst alvorens het programma te openen als klant worden nu bewaard na het programma openen.
Eerder waren de producten die als gastgebruiker aan de vergelijkingslijst werden toegevoegd, na het aanmelden niet zichtbaar.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: Sta de configuratiekwesties van Landen in de configuraties van het klantenadres toe
   * _nota van de Reparatie_: Nu het selecteren staat de configuratie van Landen toe beïnvloedt geen landen die voor buiten het bepaalde werkingsgebied worden getoond. Eerder toestaan de configuratie van Landen beïnvloedde klantenadresattributen buiten bepaald werkingsgebied
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_: De gedeelde Registratie van het Cadeautje toont de gebeurtenisdatum zoals 1 dag vroeger
   * _nota van de Reparatie_: De datum van de Registratie van het Gift wordt correct nu getoond op Storefront
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
* _AC-11427_: [ geef ] Inconsistente etiketten van de Uitgave voor attributen in marketing regels uit
   * _nota van de Reparatie_: Het systeem bevolkt nu correct de etiketten voor categorie en attributenopties in de regel van de kartprijs
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/31232>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/31231>
* _AC-11588_: De bevestiging van gegevens is succes en de knoop van de Invoer is aanwezig tijdens de producten van de Invoer met het gedrag van de Vervangen
   * _nota van de Reparatie_: Het systeem bevestigt nu correct gegevens en verbergt &quot;de knoop van de Invoer&quot;tijdens het proces van de productinvoer met &quot;vervangt&quot;gedrag, dat om het even welke onbedoelde gegevensvervanging verhindert. Eerder heeft het systeem de gegevens onjuist gevalideerd en de knop Importeren weergegeven. Dit leidt tot mogelijke inconsistenties in de gegevens.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-12167_: [Bug] Magento 2.4.7 staat geen productfoto&#39;s met de bestandsextensie van hoofdletters toe.
   * _Fix-opmerking_: het systeem accepteert nu uploads van productafbeeldingen met bestandsextensies in hoofdletters, wat zorgt voor een soepel productcreatieproces. Voorheen werden het uploaden van afbeeldingen met bestandsextensies met hoofdletters geweigerd, waardoor gebruikers gedwongen werden de bestandsextensie te wijzigen in kleine letters.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38831>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-12319_: Verborgen dropdown in netten met uitgezochte actie (b.v. Inhoud > Elementen > Pagina&#39;s)
   * _nota van de Reparatie_: Nu is het systeem al gelijkaardige dropdown voor alle netten hersteld.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38891>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39371>
* _wisselstroom-13131_: [ de Waarschuwing van het Correct van de Uitgave ]: Onbepaalde seriesleutel &quot;filters&quot;
   * _nota van de Reparatie_: Het systeem behandelt nu scenario&#39;s waar een nieuwe gebruiker nog niet met referenties heeft gecommuniceerd, verhinderend een ongedefinieerde serie zeer belangrijke &quot;filters&quot;waarschuwing wordt geregistreerd. Deze waarschuwing zou eerder worden geregistreerd als een nieuwe gebruiker geen interactie had gehad met bladwijzers.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39013>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: CSV-bestand voor het importeren van producten met speciale tekens mislukt vanwege codewijzigingen in Validate.php bestand
   * _nota van de Reparatie_: Het systeem bevestigt nu correct en voert productCSV- dossiers in die speciale karakters bevatten, die voor succesvolle gegevensoverdracht toestaan. Als u voorheen een CSV-bestand met speciale tekens importeerde, treedt er een fout op, waardoor het importproces niet meer kan plaatsvinden.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_: Wanneer het maximale aantal verzoeken om het opnieuw instellen van het wachtwoord is ingesteld groter dan 0, bijvoorbeeld: 3, &quot;Foutmeldingen over overschrijding van de limiet worden verzonden voordat de limiet wordt hersteld, dwz vanaf de tweede keer
* _AC-13768_: Hoewel het maximale aantal verzoeken om het opnieuw instellen van het wachtwoord is ingesteld op 0 (uitgeschakeld), &quot;Foutmeldingen over overschrijding van de limiet worden vanaf de 2e keer verzonden&quot;
* _AC-13850_: Er is geen rode asterisk voor verplicht gebied van het telefoonaantal
   * _nota van de Reparatie_: De vroegere rode asterisk toonde niet voor telefoonaantal maar  Telefoonnummer was verplicht. Dit is nu een vast rood sterretje dat op telefoonnummer als een verplicht veld kan worden weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c699c206>
* _AC-14300_: In Admin wanneer wij proberen om orde opnieuw te schikken verzend ordeknoop is niet klikbaar. (af en toe)
* _wisselstroom-6975_: [ Uitgave ] plaats standaardindexeermodus aan &quot;programma&quot;
   * _Fix-opmerking_: alle nieuwe indexeerfuncties staan standaard in **[!UICONTROL Update by Schedule]** de modus.  Voorheen was **[!UICONTROL Update on Save]** de standaardmodus . Dit heeft geen invloed op bestaande indexen. [ GitHub-36419 ](https://github.com/magento/magento2/issues/36419)
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36419>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0b410856>
* _wisselstroom-7700_: [ ] het veranderingslijsten van de Daling van de indexator op mening unsubscribe
   * _nota van de Reparatie_: Het systeem verwijdert nu automatisch ongebruikte veranderingslijsten wanneer een index van &quot;update op programma&quot;aan &quot;update op sparen&quot;wordt geschakeld, die de index als ongeldig markeren om ervoor te zorgen geen ingangen worden gemist. Als een index eerder werd overgeschakeld op &#39;bijwerken bij opslaan&#39;, blijven wijzigingstabellen die niet worden gebruikt in het systeem behouden en worden alle gewijzigde indexen &#39;geldig&#39; gemarkeerd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/29789>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/25859>
* _AC-7962_: Geen link naar verzending bij betalingen bij het afrekenen in de weergave van de mobiele telefoon
   * _Fix-opmerking_: het systeem zorgt er nu voor dat de titels/links van de kassa&#39;s &quot;Verzending&quot; en &quot;Beoordeling en betalingen&quot; altijd zichtbaar zijn bovenaan de pagina in de mobiele weergave, zodat gebruikers gemakkelijk tussen de stappen kunnen navigeren en de nodige correcties kunnen aanbrengen. Voorheen waren deze titels/links verborgen in de mobiele weergave, waardoor het voor gebruikers moeilijk was om hun huidige stap te kennen of terug te gaan naar eerdere stappen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/36856>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: opvragen van klanten Bestellingen verzenden opmerkingen created_at wordt geretourneerd in +0 tijdzone niet in de winkel geconfigureerde tijdzone
   * _nota van de Reparatie_: Het systeem toont nu correct het &quot;created_at&quot;gebied van ladingscommentaren in gevormde tijdzone van de klant wanneer het gebruiken van de vraag van de Orden van de klant. Eerder, werd het &quot;created_at&quot;gebied getoond in +0 timezone, ongeacht de gevormde timezone van de klant.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36947>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/37642>
* _AC-9843_: i18n:collect-phrases breekt de integriteit van de vertaling
   * _Fix-opmerking_: de `bin/magento i18n:collect-phrases -o` opdracht verzamelt en voegt nu correct nieuwe zinnen toe uit JavaScript- en .phtml-bestanden, zodat vertalingen correct worden weergegeven in het vertaalbestand. Voorheen nam het systeem geen meerregelige vertaalzinnen uit JavaScript-bestanden en zinnen uit .phtml-bestanden op in het vertaalbestand, wat leidde tot onvolledige of onjuiste vertalingen.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/0c53bbf7>
* _ACP2E-2687_: Machtigingsprobleem voor toegang tot Dynamic Block
   * _Fix-opmerking_: Voorheen voor beperkte beheerders leverde het toevoegen van een nieuw dynamisch blok een fout op. Na het implementeren van deze oplossing kan de beperkte beheerder met succes het dynamische blok toevoegen en het blok zonder enige fout bewerken
* _ACP2E-2787_: Apostrof in de naam van de opslagmening wordt vervangen door &quot;
   * _Bevestig nota_: De filters van de de opslagmening van het net tonen nu behoorlijk apostroffen
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38395>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2847_: Het uploaden van het favicon ontbreekt om .ico- dossiers te bevestigen
   * _nota van de Reparatie_: De fout van de dossierbevestiging is bijgewerkt aan &quot;Ontbroken Bevestiging van het Dossier. Controleer de instellingen voor afbeeldingsverwerking in de winkelconfiguratie.&quot; Eerder was dit gewoon &quot;Bestandsvalidatie mislukt.&quot;
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2957_: De galerie in PageBuilder toont oude beeldduimnagel in plaats van onlangs geupload beeld
   * _nota van de Reparatie_: Regenereer beeldvoorproeven voor beelden die met de zelfde naam door media galerij in de inhoud van de paginabouwer worden geschrapt en opnieuw worden geupload.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/60140cd2>, <https://github.com/magento/magento2/commit/001e5188>
* _ACP2E-2978_: Het bewaren van product door admin gebruiker met verschillende rolwerkingsgebied beschrijft/schrapt bestaande Verwante productinformatie in het product
   * _nota van de Reparatie_: Eerder, vóór de moeilijke situatie, werden de verwante producten teruggesteld en leeg geworden wanneer de secundaire admin gebruiker op sparen knoop klikte zonder in verwant product te veranderen. Na deze correctie klikt de secundaire gebruiker op de knop Opslaan en wordt het product niet opnieuw ingesteld en opgeslagen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3056e9cb>
* _ACP2E-3033_: Onbekwaam om meer dan 200 orden uit te voeren
   * _nota van de Reparatie_: De servergrenzen voor de verzoekgrootte van eerder voorgelegde geselecteerde IDs zijn genegeerd door het verzoek van HTTP van GET in POST te veranderen om de kwestie te bevestigen. Eerder werd het probleem aangetroffen vanwege serverbeperkingen voor de grootte van GET-verzoeken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3037_: Het bericht van de de paginasalidering van de uitcheckpagina onjuist.
   * _nota van de Reparatie_: Als om het even welk vereist gebied leeg, zoals &quot;adres wordt verlaten,&quot;zal de server-zijbevestiging niet het bericht tonen. De validatie aan de clientzijde zorgt ervoor dat de vereiste veldfoutmelding wordt weergegeven, met de vermelding &#39;Dit is een verplicht veld&#39;. Eerder werd het bericht &quot;adres is required&quot; weergegeven als een vereist veld leeg was, naast het validatiebericht aan de clientzijde.
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
* _ACP2E-3178_: Kan de status van de op maat gemaakte bestelling niet bijwerken
   * _Opmerking_ repareren: &#39;
We kunnen nu op maat gemaakte orderstatussen bijwerken, terwijl de status voorheen alleen kon worden gewijzigd als de huidige status &#39;verwerken&#39; of &#39;fraude&#39; was.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38659>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3294_: De het verschepen adresstaat is niet auto het bijwerken
   * _Oplossing_: Vóór de correctie was de regio van het verzendadres (of regio-ID) niet gesynchroniseerd met de factureringsgegevens van het adres. Nu worden zowel het verzendadres als de regio-id correct bijgewerkt wanneer het factuuradres wordt gewijzigd.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: De knoop van het Terugstellen werkt niet op Add/geeft admin gebruiker uit
   * _nota van de Reparatie_: Eerder, werkte de knoop van het Terugstellen niet op Add/geef Admin pagina van de Gebruiker uit. Nu werkt de knop Herstellen in het deelvenster Beheer onder Systeem -> Machtigingen -> Alle gebruikers correct op de pagina Admin-gebruiker toevoegen/bewerken.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3373_: Magento admin URL die onjuiste opsporing en fouten CORS verplettert
   * _nota van de Reparatie_: Na de moeilijke situatie, als het douane admin domein een subdomein van het belangrijkste domein is, is admin toegankelijk slechts van gevormde subdomain.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37663>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3f12d152>
* _ACP2E-3392_: Gebroken bevestiging voor &quot;Maximale Aantal Toegestaan in het Schepen Kar&quot;
   * _nota van de Reparatie_: Eerder, wanneer wij `Maximum Qty Allowed in Shopping Cart` leeg zetten, veroorzaakte het geen uitzondering, hoewel een lege waarde hier niet wordt goedgekeurd. Nadat deze correctie is toegepast, genereert het plaatsen van een lege tekenreeks uitzonderingen en wordt het opslaan van het product niet meer toegestaan.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3408_: [ Uitgave UI van de Voorproef van de Bouwer van de Pagebuilder ] De knopen in de kolom van de Bouwer van de Pagina worden niet correct opgesteld
   * _nota van de Reparatie_: De knopen in de kolommen van de Bouwer van de Pagina worden nu correct gericht. Eerder waren ze verkeerd uitgelijnd in de kolommen van de Page Builder.
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
   * _nota van de Reparatie_: Adminhtml_user_delete registreert nu correct belangrijke details. Eerder zijn geen logbestanden gegenereerd voor verwijderingen door gebruikers.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/4de008a9>
* _ACP2E-3536_: De Regel van de wagen met het verschepen voorwaarde die niet van toepassing is wanneer het plaatsen van orde van admin
   * _nota van de Reparatie_: Eerder, als de regel van de kartprijs een het verschepen methodekorting met de coupon heeft, kan het niet door Admin UI worden toegepast. Nadat deze correctie is toegepast, wordt de korting op de winkelwagenprijs met een kortingsbon voor een specifieke verzendmethode toegepast vanuit de beheerdersinterface.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/a52ff98f>, <https://github.com/magento/inventory/commit/11ce816b>
* _ACP2E-3559_: [FRESH] HEX-code wordt niet correct bijgewerkt in SWATCH
   * _nota van de Reparatie_: De code van de HEX die manueel door gebruiker in de Visuele de kleurenplukker van het Monster wordt ingegaan wordt niet meer veranderd door het systeem. Voorheen werden bepaalde HEX-codes enigszins aangepast als gevolg van omzettingsfouten tussen kleurmodellen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/344fce23>, <https://github.com/magento/inventory/commit/1ef984c0>

### Admin UI, B2B

* _AC-13628_: B2B Login als kopbal van de Klant heeft nog het brandmerken van Magento
   * _nota van de Reparatie_: Eerder toont de storefront kopbal &quot;u nu als &lt;customer name> op &lt;store name>&quot;met branding van Magento wordt verbonden. Deze is nu gefixeerd en de header wordt weergegeven met ADOBE-branding.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/96dec499>

### Admin UI, Catalogus

* _ACP2E-2708_: Kan geen posities wijzigen voor de categorie producten op de toegestane website als een beperkte beheerdersgebruiker
   * _nota van de Reparatie_: sta voor een beperkte admin gebruiker toe om producten onder een categorie toe te voegen en te sorteren bevat onder de wortelcategorie die onder beperkte website wordt toegewezen.

### Admin UI, Payment/Payment Methods, Order

* _AC-13520_: De Vergunning van de transactie niet die in het Lusje van de Transactie na de Slimme Orde van de Knoop PayPal wordt getoond
   * _nota van de Reparatie_: Het systeem toont nu correct de transactievergunning in het lusje van de Transactie nadat een orde gebruikend de Slimme Knoop van PayPal wordt geplaatst. Eerder werd de transactie voor autorisatie niet weergegeven op het tabblad Transactie nadat werd geklikt op de knop &quot;Autoriseren&quot; en werd geen nieuwe transactie van het type &quot;Autorisatie&quot; gemaakt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Beheerdersinterface, prestaties

* _ACP2E-3169_: Na de update naar 2.4.5-p8 treden 500 fouten op bij het maken van een bestelling van de beheerder
   * _Fix-opmerking_: Voorheen kon bij het inschakelen van HTML-minificatie geen bestelling van de beheerder worden geplaatst. Nu HTML is ingeschakeld, kan de bestelling van de beheerder met succes worden geplaatst.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>

### Admin-gebruikersinterface, verzenden

* _ACP2E-2519_: De telling van de couponcode werkt niet in bij   De kolom &quot;Gebruikte tijd&quot; in het tabblad Codes voor coupons beheren als een bestelling wordt geplaatst met meerdere verzendingen.
   * _nota van de Reparatie_: Eerder, toen een orde met multi-verschepen werd geplaatst, werkte de telling van de waardeboncode niet in de &quot;Gebruikte Tijd&quot;kolom op het Manage lusje van de Codes van de Coupon bij. Nu wordt het juiste aantal weergegeven in zowel de &quot;Gebruikte tijd&quot; die de gewenste waarden weerspiegelt bij verzending via meerdere kanalen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/4745100c>

### Beheerdersinterface, Staging en Voorvertoning

* _ACP2E-3424_: [ Wolk ] het Verwijderen van malplaatje met ontbrekende beelden veroorzaakt pub/media om worden geschrapt
   * _nota van de Reparatie_: Eerder aan deze moeilijke situatie, als de naam van het voorproefbeeld voor een WebBuilder malplaatje mist, werd pub/media omslag geschrapt. Na de correctie wordt alleen de sjabloon verwijderd en de voorvertoning indien gevonden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analyse/rapportage

* _AC-9922_: De Fout van Google Analytics CSP https://region1.analytics.google.com
   * _nota van de Reparatie_: Het systeem staat nu correct verbindingen aan &quot;https://region1.analytics.google.com&#39; toe wanneer Google Analytics wordt toegelaten, verhinderend de fouten van het Beleid van de Veiligheid van de Inhoud (CSP). Voorheen zou het inschakelen van Google Analytics en het bekijken van de website vanuit de EU leiden tot fouten in de CSP-console als gevolg van een weigering om verbinding te maken met &#39;https://region1.analytics.google.com&#39;.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37750>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38991>
* _ACP2E-2570_: Het Rapport van de vooruitgang werkt niet
   * _nota van de Reparatie_: Het systeem steunt nu de generatie van de Geavanceerde Gegevensdossiers van de Rapportering voor extra grote datasets door rapporten in partijen van 10.000 te laden en te schrijven. Eerder, kon de Geavanceerde module van de Rapportering gegevensdossiers voor extra grote datasets niet produceren, veroorzakend &quot;MySQL server is weggegaan&quot;fouten tijdens de uitvoering van de analytics_collect_data bouwbaan.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-3080_: Admin bestelde de kwestie van het de datumbereik van het Rapport van Producten.
   * _nota van de Reparatie_: De gebruiker zal om het even welke datum van het bevolen productrapport kunnen selecteren. Eerder, na een lijst verfrist zich, zal het selecteren van &quot;VAN&quot;datum &quot;aan&quot;datum terugstellen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3096_: Onjuiste curl kopballen die nieuwe relic :create: opstellen-teller maken die niet werkt
   * _nota van de Reparatie_: Het systeem formatteert nu correct curl kopballen, toestaand het nieuwe betrouwbare :create: op:stellen-teller bevel om een plaatsingsteller in New Relic met succes tot stand te brengen. Eerder, verhinderden de onjuiste curl kopballen de verwezenlijking van een plaatsingsteller in New Relic.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37641>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3146_: De ontbrekende gebeurtenis GTM addToCart in dataLayer voor configureerbaar product met douaneoptie
   * _nota van de Reparatie_: Eerder, werd de gebeurtenis addToCart niet teweeggebracht voor configureerbare producten. Nu, wordt de gebeurtenis behoorlijk toegevoegd aan de GTM dataLayer variabele.
* _ACP2E-3183_: NewRelic browser die inlineJS manuscript controleert veroorzaakt CSP fouten
   * _nota van de Reparatie_: De manuscripten van de Controle NewRelic Browser worden nu ingespoten door de toepassing in plaats van de agent APM voor naleving van CSP (het Beleid van de Veiligheid van de Inhoud). Eerder waren de scripts van NewRelic Browser Monitoring die door de APM-agent werden geïnjecteerd, niet compatibel met CSP en leidden deze ertoe dat de scripts niet werden uitgevoerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3189_: De vragen van het TUSSENVOEGSEL aan de lijst sales_bestsellers_compiled_daily worden langzaam op project met groot volume van de verkooporde
   * _nota van de Reparatie_: Eerder de bestsellers geaggregeerde dagelijks rapport zouden veel tijd vergen om voor groot volume van geplaatste orden te produceren. Nu wordt het verslag tijdig opgesteld.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3276_: De rapporten van de orde die het verkeerde muntsymbool tonen
   * _nota van de Reparatie_: Het muntsymbool voor ordebedragen in het Rapport van de Orde werd verkeerd genomen van munt/opties/basis. Het is nu gecorrigeerd om valuta/opties/gebrek voor nauwkeurige rapportering te gebruiken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3302_: [Onjuiste berekeningen in de cloud] in het rapport over het gebruik van coupons
   * _Fix-opmerking_: Het verkooptotaal in het raster van het couponrapport wordt nu nauwkeurig berekend door zowel het &quot;Compensatiebedrag voor kortingsbelasting&quot; als het &quot;Compensatiebedrag voor verzendkorting&quot; op te nemen. Voorheen ontbraken deze bedragen in de berekening, wat leidde tot discrepanties tussen het verkooptotaal en de verkoopordergegevens.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: De kwesties met gedeelde &quot;&lt;project_id>/var/tmp&quot;
   * _nota van de Reparatie_: De tijdelijke dossiers van DataExport van de Analyse zullen de folder van sys tmp gebruiken, die geschikter voor frequente toegang en veranderingen is. Om botsingen te vermijden in het geval dat de veelvoudige instanties op de zelfde server lopen, werd de weg tmp bijgewerkt om unieke identiteitskaart van een instantie te gebruiken
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analyse/rapportage, B2B

* _ACP2E-2300_: B2B - sitemap omvat producten/categorieën niet die aan Gedeelde Catalogus worden toegewezen
   * _Fix-opmerking_: Beperk de door het siteoverzicht gegenereerde categorieën en producten tot de categorieën en producten die alleen zijn toegewezen aan de openbare gedeelde catalogus en/of de machtigingsinstellingen voor cataloguscategorieën.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ea79f7dd>

### Analyse / rapportage, cloud

* _ACP2E-3067_: Magento gooit de meeste New Relic cron-transacties weg #34108
   * _nota van de Reparatie_: AC rapporteert correct gezamenlijke baan verwante transacties aan NewRelic. Voorheen zouden sommige aan een uitsnijdtaak gerelateerde transacties als &quot;OtherTransaction/Action/unknown&quot; in Northern Rock worden weergegeven
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3187_: Metrisch in NR zou voor achtergrondtransacties misleidend kunnen zijn - Follow-up van ACP2E-3067
   * _Nota van de Moeilijke situatie_: De transacties van de achtergrond (kruin) zullen New Relic gebruiken toepassingsnaam die in de config montages wordt bepaald
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_: 2.4.8-bèta102 de uitgave van de pakketonderneming ontbreekt met toepassingsuitzonderingen
* _ACP2E-2139_: De producten die aan gedeelde catalogus worden toegewezen wijzen niet op het vooreind terug wanneer de gedeeltelijke index wordt uitgevoerd
   * _nota van de Reparatie_: De producten die aan gedeelde catalogus via REST API worden toegewezen zijn nu onmiddellijk zichtbaar op storefront nadat het gedeeltelijke indexeren volledig is. Eerder waren de producten pas zichtbaar na een volledige herindexering.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-2873_: [ de vertoning van de Prijs van de Wolk ] in mobiele en Desktopversie niet het zelfde in &quot;Mijn citaten&quot;
   * _nota van de Reparatie_: Onnodig omvat de Lijn van de Belasting wordt niet meer getoond in Negotiable Citaat wanneer de sectie van de catalogustotale prijs wordt uitgebreid.
* _ACP2E-3044_: De onnodige grenzen op de Mijn sectie van Orden
   * _nota van de Reparatie_: Eerder werd een extra container (ordeverwijzingen) gecreeerd die extra CSS klassen toepaste, die onnodige grenslijnen veroorzaakte die onder het ordeaantal binnen de Mijn sectie van Orden verschijnen, die nu niet zichtbaar is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3247_: sales_clean_quotes cron schrapt citaten van aan nog goedgekeurde kooporden
   * _Nota van de Moeilijke situatie_: De citaten die in kooporden worden gebruikt zullen nu niet door sales_clean_quotes cron baan worden geschrapt
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_: De knoop van de Orde van de plaats verdwijnt in de details van de Orde van de Aankoop
   * _Nota van de Reparatie_: Vaste een kwestie waar de knoop van de Orde van de Plaats voor goedgekeurde inkooporden werd verborgen wanneer een productvariatie minimumaantal in gespecificeerde kaart had
* _ACP2E-3474_: [ CLOUD ] Geen dergelijke entiteit met id = 0 met b2b module
   * _Bevestig nota_: De geregistreerde gebruiker kan product aan wagentje toevoegen wanneer de Gedeelde eigenschappen van de Catalogus worden toegelaten.
Eerder toegevoegd product aan winkelwagentje resulteerde in Fout &#39;geen dergelijke entiteit met id = 0&#39;
* _ACP2E-3562_: Geen foutenmelding die voor onze van voorraadproducten wordt getoond wanneer bulk het toevoegen van aanvraaglijst
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie werd een succesbericht getoond ongeacht het aantal producten die om aan de kar ontbraken te worden toegevoegd. Er worden nu afzonderlijke berichten weergegeven voor producten die zijn toegevoegd aan de winkelwagentje en voor producten die zijn mislukt.
* _ACP2E-3628_: Uitgave met de Updates van SKU na Geplande Updates die Onjuiste Toestemmingen van het Product veroorzaken (-2 ontkennen)
   * _nota van de Reparatie_: Het wijzigen van SKU van een product met voorbije geplande updates veroorzaakt niet meer het product om aan de gedeelde catalogusklanten ontoegankelijk te zijn gerechtigd om het product te zien.

### B2B, catalogus

* _ACP2E-2860_: Producten/Categorieën zichtbaar tijdens herindexatie wanneer het gebruiken van Toestemmingen NoDDL en van de Categorie
   * _Bevestig nota_: Vermijd het tonen op opslag beperkte categorieën en hun inhoud terwijl de catalogustoestemmingen het indexeren wordt uitgevoerd.

### B2B, Kader

* _AC-9607_: Het filtreren van het Net van het Bedrijf &amp; toen het Poging van de Uitvoer van het Net CSV zal de Uitzondering van de Kwijting &amp; van de Borg ontbreken
   * _nota van de Reparatie_: Het systeem staat nu succesvolle uitvoer CSV van de het netgegevens van Bedrijven in het admin paneel toe, zelfs wanneer de filters zoals &quot;Uitstaand Saldo&quot;en &quot;Type van Bedrijf&quot;worden toegepast. Eerder, zou het toepassen van bepaalde filters en het proberen om de netgegevens uit te voeren in een mislukking resulteren en een uitzondering die wordt geworpen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/44cef3a9>

### B2B, GraphQL

* _ACP2E-3391_: [ Wolk ] Onbekwaam om custom_attributes te plaatsen terwijl de bedrijfverwezenlijking over de grafische vraag
   * _nota van de Reparatie_: Na de moeilijke situatie, is het mogelijk om het &quot;custom_attributes&quot;attribuut voor bedrijfadmin tijdens bedrijfverwezenlijking te plaatsen gebruikend grafisch verzoek.

### Braintree

* _wisselstroom-14293_: Admin express checkout knoop is gehandicapt.
* _BUNDLE-3367_: Betaal via LPM
   * _nota van de Reparatie_: Het systeem geeft nu correct Lokale BetalingsMethoden (LPM) op aanvankelijke lading terug, zelfs wanneer de het verschepen en het factureren van een aangemelde klant adressen niet aanpassen, die een vlot controleproces verzekeren. Eerder, zou een wanverhouding tussen het verschepen en het facturerings adres van een klant LPM verhinderen teruggeven, veroorzakend potentiële verstoringen tijdens het afrekenen.
* _BUNDLE-3368_: Configureerbaar met Virtueel als Product van het Kind
   * _nota van de Reparatie_: Het systeem staat nu uitdrukkelijke betalingsmethodes voor configureerbare producten toe die een virtueel kindproduct hebben, die een vlot afrekenen proces verzekeren. Eerder waren expresbetalingsmethoden niet beschikbaar toen een configureerbaar product met een virtueel onderliggend product aan de winkelwagentje werd toegevoegd.
* _BUNDEL-3369_: CVV-verificatie mislukte fout
* _BUNDEL-3370_: Kluis via het account Area Issues 247
   * _Fix-opmerking_: het systeem stelt klanten nu in staat om nieuwe kaart- of PayPal-accountgegevens op meerdere websites op te slaan zonder autorisatiefouten tegen te komen. Voorheen konden klanten geen nieuwe betaalmethoden op verschillende websites opslaan en kregen ze een autorisatiefoutmelding te zien.
* _BUNDEL-3371_: Verzenden naar een adres uit een ander land
   * _nota van de Reparatie_: Het systeem staat nu transacties toe om zonder fouten worden verwerkt wanneer het verschepen naar een adres van een verschillend land, die een vlot afhandelingsproces verzekeren. Eerder, zou het proberen om aan een adres van een verschillend land te verzenden in consolefouten, ondanks geen zichtbare fouten op de frontend resulteren.
* _BUNDLE-3372_: Kredietkaart - de functie van de Onderbreking
   * _Nota van de Oplossing_: Het systeem behandelt nu correct de opruiming van de componenten van Braintree PayPal wanneer een klant terug van de betalingspagina naar de het verschepen pagina navigeert, die om het even welke fouten verhinderen en ervoor zorgen dat de Uitdrukkelijke knopen van PayPal correct teruggeven. Eerder was het navigeren van de verzendpagina vanaf de betalingspagina soms een fout bij het afbreken van de Braintree PayPal-componenten.
* _BUNDLE-3373_: Verzendcallback voor Uitdrukkelijke PayPal
   * _Fix-opmerking_: het systeem geeft nu de beschikbare verzendmethoden correct weer in de PayPal Express-modal, zodat klanten de gewenste verzendmethode kunnen selecteren voordat ze doorgaan naar de beoordelingspagina of hun transactie voltooien. Voorheen waren er geen verzendmethoden beschikbaar om uit te kiezen in de PayPal Express-modal, waardoor klanten een verzendmethode moesten selecteren op een aparte beoordelingspagina voordat ze hun transactie konden voltooien.

### Bundel

* _AC-10826_: Storefront Bundle Checkbox Validatie Aantal foutmeldingen meer dan 1
   * _Fix-opmerking_: het systeem geeft nu slechts één validatiefoutmelding weer wanneer op de knop &#39;Toevoegen aan winkelwagentje&#39; wordt geklikt zonder dat er selectievakjes voor een gebundeld product zijn ingeschakeld. Voorheen gaf het systeem meerdere validatiefoutmeldingen weer voor elk niet-geselecteerd selectievakje.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_: Magento-uitzondering in een bepaalde volgorde gegooid gerelateerde testcases
   * _Fix note_: Het systeem verwerkt nu de stap &#39;sendGuestPaymentInformation&#39; correct in verschillende testgevallen, waardoor Magento-uitzonderingen niet worden gegenereerd. Voorheen deden deze uitzonderingen zich voor als gevolg van een ongeldige betaalmethode, waardoor in verschillende testgevallen fouten werden veroorzaakt.

### Winkelwagen &amp; Afrekenen

* _AC-10660_: Uitzondering is dat het niet goed wordt afgehandeld tijdens het toevoegen van een product aan de winkelwagen op de productpagina vergelijken
   * _Fix-opmerking_: het systeem gaat nu correct om met uitzonderingen bij het toevoegen van een product aan de winkelwagen vanaf de productpagina vergelijken, waarbij een bericht in de controller wordt weergegeven. Voorheen zou een uitzondering ertoe leiden dat een JSON-gecodeerde pagina werd geretourneerd in plaats van correct te worden opgevangen en behandeld.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38200>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38257>, <https://github.com/magento/magento2/commit/0c53bbf7>
* _AC-10698_: GTag verzendt geen transactieprijzen en totalen.
   * _Fix-opmerking_: het systeem verzendt nu correct transactieprijzen en totalen naar Google Tag wanneer GTag is ingeschakeld, waardoor een nauwkeurige tracking van e-commercegegevens wordt gegarandeerd. Voorheen werd de valuta ten onrechte verzonden als onderdeel van de &quot;alle&quot; bestellingen, in plaats van te worden gekoppeld aan de individuele bestelling.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/37348>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/37504>, <https://github.com/magento/magento2/pull/37349>
* _AC-11641_: [Issue] [Checkout Depend-richtlijnen] bijgewerkt in e-mailsjabloon voor mislukte betaling
   * _nota van de Reparatie_: Het systeem weglaat nu correct het verschepen adres en het verschepen methode van het ontbroken betalings e-mailmalplaatje voor virtuele producten, die slechts relevante informatie verzekeren is inbegrepen in e-mail. Eerder bevatte het niet-betaalde e-mailbericht voor virtuele producten het verzendadres en de verzendmethode onjuist.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32781>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32511>
* _AC-11717_: Magento 2 login binnen de controle met bestaande klant geeft consolefout in browser Firefox
   * _Bevestig nota_: Het systeem staat nu gebruikers toe om tijdens het controleproces aan te melden zonder enige consolefouten in browser Firefox te ontmoeten. Eerder, zou het proberen om zich aan te melden als bestaande klant tijdens controle in een consolefout in Firefox resulteren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38557>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39509>
* _AC-11876_: [ de regressie van de Regels van de Verkoop van de Uitgave ] in 2.4.7
   * _nota van de Reparatie_: Het systeem bevestigt nu correct verkoopregels, die de toepassing van een couponcode aan een karretje verhinderen wanneer de productvoorwaarde geen productnaam aanpast. Voorheen kon een verkoopregel worden toegepast en een korting op het verzendbedrag worden gegeven, zelfs als de productvoorwaarde niet overeenkomt met een productnaam.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38671>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-11914_: [ geef ] CartFixed berekening van de Regel van de Verkoop uit: onjuist disconteringsbedrag
   * _nota van de Reparatie_: Het systeem berekent nu correct het kortingsbedrag voor verkoopregels met winkelwagentvaste bedragen, die nauwkeurige kortingen verzekeren wordt toegepast ongeacht veranderingen in kartelpunten. Eerder kon het kortingsbedrag verkeerd variëren wanneer winkelwagentjes werden gewijzigd, wat soms tot aanzienlijk grotere kortingen leidde dan verwacht.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38694>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _wisselstroom-11993_: [ geef ] de ladingsblokken de verschepende methodes na postcode wordt veranderd, de regels van de de rentesubsidie bevestiging
   * _nota van de Reparatie_: Het systeem behandelt nu correct douaneverschepende methodes zonder de bevestigingsregels van het verschepen tarief, die ervoor zorgen dat de lader niet de verschepende methodes blokkeert nadat postcode in het verschepende adres tijdens controle wordt veranderd. Als de postcode in het verzendadres tijdens de afhandeling werd gewijzigd, zou de lader eerder de verzendmethoden blokkeren en niet verdwijnen als er aangepaste verzendmethoden werden gebruikt zonder de validatieregels voor de verzendkosten.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38742>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12170_: De eigenschap van de code van de coupon werkt niet behoorlijk in de controlepagina op Magento 2.4.7
   * _Nota van de Reparatie_: Het systeem laat nu het de inputgebied van de disconteringscode/coupon op de controlepagina voor virtuele en downloadbare producten toe, toestaand gebruikers om kortingscodes toe te passen zoals verwacht. Eerder was de invoer van de kortingscode/coupon uitgeschakeld en werd de tekst van de knoptitel weergegeven als &quot;coupon annuleren&quot;, zodat gebruikers geen kortingscodes konden toepassen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38826>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1bafc571>
* _AC-12479_: De voorwaarden checkbox van voorwaarden staat HTML op opslag niet toe
   * _nota van de Reparatie_: Het systeem steunt nu het formatteren van HTML in de checkbox van de &quot;Voorwaarden en van de Voorwaarden&quot;tekst op de storefront, die voor verbeterde aanpassing en leesbaarheid toestaat. Eerder werd de tekst van het selectievakje weergegeven als normale tekst, waarbij HTML-tags werden genegeerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _wisselstroom-12541_: De prijsregel van de kunst die voor het programma geopende gebruiker wordt gecreeerd wordt verkeerd toegepast niet het programma geopende gebruiker
   * _nota van de Reparatie_: Het systeem verwijdert nu correct de regel van de kartprijs voor het programma geopende gebruikers wanneer zij automatisch uit wegens koekjesafloop worden geregistreerd, die ervoor zorgen dat de korting niet op niet-het programma geopende gebruikers wordt toegepast. Eerder, werd de regel van de kartprijs nog toegepast zelfs toen de gebruiker uit het programma werd geopend, resulterend in een onjuiste korting die op niet-geregistreerde gebruikers wordt toegepast.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38944>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13302_: [ geef ] [ de optimalisering van de Eigenschappen ] grote winkelwagentjes van Prestaties door te verhinderen... uit.
   * _nota van de Reparatie_: Het systeem optimaliseert nu prestaties voor grote winkelwagentjes door dubbele vraag te verhinderen getActions, die de snelheid en de efficiency van het winkelwagentverrichtingen verbetert. Eerder werd voor een winkelwagentje met meerdere items de functie getActions meerdere keren aangeroepen, waardoor de prestaties van het systeem werden vertraagd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39292>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39290>
* _AC-13797_: Het product van de registratierapport van het Gift toont behoorlijk niet
* _AC-13841_: Het product van de registratierapport van het Gift toont niet behoorlijk
* _AC-8103_: Vertaling BTW in adresrenderer
   * _Fix-opmerking_: het systeem maakt het nu mogelijk om de tekst &quot;VAT&quot;, &quot;T&quot;, &quot;F&quot; in de adresrenderers te vertalen, waardoor gebruikers deze termen kunnen vertalen naar de specifieke taal van de winkel. Voorheen waren deze termen niet vertaalbaar, waardoor gebruikers gedwongen werden een tijdelijke oplossing te gebruiken.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/36942>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/36943>
* _ACP2E-2055_: De dubbele orden met zelfde Citaat ID tezelfdertijd met weinig tijdverschil
   * _Opmerking_ oplossen: het probleem opgelost wanneer Adobe Commerce-klanten dubbele bestellingen tegenkwamen die met dezelfde QuoteID waren geplaatst
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2470_: Persistent winkelwagentje gewist tijdens het afrekenen
   * _Fix-opmerking_: Als u na de oplossing de betaalmethode selecteert tijdens het afrekenen terwijl u niet bent ingelogd, wordt de permanente sessie niet beëindigd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2518_: De orde voegt niet toegewezen product aan wagentje opnieuw toe
   * _nota van de Reparatie_: Eerder, voor de verschillende opslagproducten kunnen van de andere opslag worden opnieuw in orde gebracht. Nadat deze correctie is toegepast, kan alleen dezelfde store worden gebruikt, kan hetzelfde bereikproduct opnieuw worden geordend wanneer het delen van de klantenaccount is ingeschakeld
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2620_: In admin, wordt het &quot;Winkelende Kart&quot;op linkerkant niet bijgewerkt wanneer het selecteren van de punten en &quot;Beweging aan het Winkelende Kart&quot;van de rechterkant
   * _Fix-opmerking_: de &quot;Winkelwagen&quot; aan de linkerkant wordt bijgewerkt bij het selecteren van de artikelen en &quot;Verplaatsen naar winkelwagen&quot; aan de rechterkant aan de beheerderskant. Eerder werkte deze functionaliteit niet omdat de getransformeerde winkelwagentjes niet leeg werden tijdens de sessie.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2646_: [ de Regel van de Verkoop van de Wolk ] wordt niet toegepast op eerste orde van Multi die verscheept
   * _nota van de Reparatie_: Na de moeilijke situatie, wordt de korting correct getoond voor elke orde van het zelfde multi-verschepende citaat.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2664_: [ de parallelle verzoeken van de de productie van de Wolk ] om het zelfde product aan het resultaat van de Kar toe te voegen in Twee afzonderlijke punten in de steun API
   * _nota van de Reparatie_: Het systeem verwerkt nu correct veelvoudige parallelle verzoeken om het zelfde product aan de kar in één enkel lijnpunt toe te voegen, verhinderend de verwezenlijking van afzonderlijke lijnpunten voor zelfde SKU. Eerder zou het doen van parallelle verzoeken om hetzelfde product via de REST-API aan het winkelwagentje toe te voegen, resulteren in meerdere regelitems voor dezelfde SKU.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2676_: Kwestie met het Opdracht geven van de Registratie van het Cadeautje Magento 2.4.4 Onderneming/Commerce
   * _nota van de Reparatie_: De kwestie die de succesvolle aankoop van een product van een geschenkregister verhindert is opgelost, toestaand orden om worden geplaatst en het geschenkregister om geschikt worden bijgewerkt. Er is eerder een fout opgetreden bij het plaatsen van een bestelling in een register met cadeaus, waardoor de aankoop niet kon worden voltooid.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/35432>
* _ACP2E-2704_: Het krijgen van Onbekwaam om het koekje te verzenden. Grootte van &#39;afbeeldingsberichten&#39; tijdens het opnieuw ordenen
   * _nota van de Reparatie_: Het opnieuw rangschikkende proces zal niet zijn eigen fouten nu produceren. Het object is afhankelijk van ingebouwde controles van winkelwagentjes.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2798_: Het standaard verschepende adres wordt niet geselecteerd bij controle
   * _nota van de Reparatie_: Het standaard verschepende adres wordt nu geselecteerd gebeurtenis in context van toegelaten adresonderzoek.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2897_: [ CLOUD ] grafische addProductsToCart API kwestie met douaneoptie
   * _nota van de Reparatie_: GraphQL voegt toe om correct het zelfde product met verschillende douaneopties te kar
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2917_: [ Cloud ] Verwante Regels van Producten die niet werken wanneer het veranderen van de archiefmening
   * _nota van de Reparatie_: De kwestie is opgelost door te bevestigen dat de waarde van het douanebezit met succes op de wortelpagina wordt ontvangen. Eerder, werd het niet behoorlijk gehaald wanneer het schakelen tussen opslag op de winkelwagentje pagina.
* _ACP2E-2923_: De veelvoudige adressen die aan de rekening worden toegevoegd wanneer controle als nieuwe klant
   * _nota van de Reparatie_: Het systeem bewaart nu een nieuw klantenadres slechts eenmaal als de orde om niet kon worden gecreeerd, verhinderend de verwezenlijking van veelvoudige identieke adressen in het geval van de fouten van de orderplaatsing. Eerder, zou het systeem een nieuw adres bewaren telkens als een bestelling plaatsingspoging werd gemaakt, ongeacht of de orde met succes werd gecreeerd of niet.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/001e5188>, <https://github.com/magento/inventory/commit/2ebcef39>
* _ACP2E-3004_: Het opnieuw ordenen van klantenorde via de vorm van de gastorde resulteert een leeg karretje
   * _nota van de Reparatie_: Eerder, toen het plaatsen van een herschikking door de Orden en de pagina van Keert terug, werd de klant opnieuw gericht aan de login pagina. Nadat deze correctie is toegepast, wordt de geregistreerde klant correct omgeleid naar de pagina Winkelwagentje weergeven wanneer een nieuwe order wordt geplaatst. De stroom werkt het zelfde als gastklanten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3025_: De Gebruiker van Admin met de beperkte Middelen van de Rol kan het Schepen van Kasten niet bekijken
   * _nota van de Reparatie_: Eerder, beperkte admin kon niet het verlaten het winkelwagentje van het admin paneel voor een bijbehorende website zien. Nadat deze correctie is toegepast, kan de beperkte beheerder het verlaten winkelwagentje van het admin paneel zien.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3176_: [ de Snelle orde van de Wolk ] grote hoeveelheid SKU prestaties
   * _Fix-opmerking_: de prestaties van het afrekenen zijn verbeterd wanneer kenmerken die worden gebruikt in de voorwaarden voor winkelwagenprijsregels niet voor alle producten aanwezig zijn en wanneer de MAP-functie (Minimum geadverteerde prijs) is ingeschakeld.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3211_: Dubbele punten in kar
   * _nota van de Reparatie_: Het systeem verwerkt nu correct veelvoudige parallelle verzoeken om het zelfde product aan de kar in één enkel lijnpunt toe te voegen, verhinderend de verwezenlijking van afzonderlijke lijnpunten voor zelfde SKU. Eerder, zou het doen van parallelle verzoeken om het zelfde product aan het karretje op Storefront toe te voegen in veelvoudige lijnpunten voor zelfde SKU resulteren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3296_: De bevestiging van de betalingsorde wordt verzonden naar e-mail ingegaan in Voornaam/Achternaam
   * _nota van de Reparatie_: De bevestiging van de controleorde e-mail, die eerder werd verzonden toen een e-mailachtig patroon in de Voornaam en de gebieden van de Achternaam werd ingegaan, wordt niet meer verzonden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3402_: De vorm van het het verschepende adres van de Afhandeling krijgt update met verkeerd adres
   * _Bevestig nota_: ShippingAddressFromData wordt nu bewaard in de lokale opslag per website. Eerder kon een adres van de verkeerde website automatisch worden ingevuld in het verzendadresformulier tijdens het uitchecken als een winkelcode in de URL werd gebruikt en het uitchecken tijdens dezelfde gastsessie werd gestart van meerdere websites.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3405_: [ CLOUD ] Controle behoudt niet het geselecteerde facturerings adres wanneer het Onderzoek van het Adres wordt toegelaten
   * _nota van de Reparatie_: De betalingspagina van de Betaling van de Betaling zal nu het geselecteerde het facturerings adres behouden wanneer het adresonderzoek wordt toegelaten. Eerder als &quot;Aantal Grens van de Adressen van de Klant&quot;aan 1 wordt gevormd, en de klant heeft meer dan één adres, zou het geselecteerde facturerings adres na het herladen van de pagina verdwijnen.
* _ACP2E-3407_: Het Product van de Kaart van de Gift | Winkelsamenvoegen is een kaartje samenvoegen
   * _nota van de Reparatie_: De producten van Giftcard worden nu correct samengevoegd in het karretje
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3415_: De persistentie van de kunst wordt niet gerespecteerd op logout
   * _nota van de Reparatie_: Toegevoegde ontbrekende functionaliteit herinner me van klantenlogin aan authentificatie popup en checkout teken ins.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/344fce23>
* _ACP2E-3488_: De bestaande citaatgegevens zijn niet bijgewerkt/niet zichtbaar, in plaats daarvan creeer een nieuw citaatverslag wanneer trigger_recollect = 1
   * _Bevestig nota_: De winkelwagentjes van de klant verdwijnen niet meer als resultaat van een product dat wordt geschrapt nadat het aan het winkelwagentje werd toegevoegd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3495_: Wanneer een punt van de cadeauregistratie wordt gekocht, ziet de klant punten niet op hun register
   * _nota van de Moeilijke situatie_: De update van de registratierapport omvat niet meer punten die niet tot de giftenregistratie behoren.
* _ACP2E-3510_: [ Cloud ] Kwestie met &quot;verwijder Al&quot;Bevestigingspop Verwijderend de Punten van de Kunst zonder Bevestiging
   * _nota van de Reparatie_: Nu, het klikken van &quot;verwijdert allen&quot;knoop voor de aandacht-vereiste producten zet een bevestigingspopup ertoe om punten te verzekeren slechts met uw bevestiging worden verwijderd. Eerder werden objecten direct verwijderd zonder bevestiging
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
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>

### Winkelwagentje en afhandeling, verzending

* _AC-12119_: Onmiddellijke aankoop &quot;goedkoopste verschepende&quot;gebroken voor configureerbare producten
   * _nota van de Reparatie_: De Onmiddellijke eigenschap van de Aankoop selecteerde verkeerd de duurdere optie van de Opslag van de Aankoop voor configureerbare producten in plaats van de goedkoopste Vlakke methode van het Tarief. Deze correctie zorgt ervoor dat de juiste verzendmethode wordt gekozen op basis van de werkelijke prijs.&quot;
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38811>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38819>, <https://github.com/magento/magento2/commit/29fe9097>

### Catalogus

* _AC-10910_: De schoonmaakbeurt van cron_planningsgegevensbestandlijst schoont niet bestaande banen
   * _nota van de Reparatie_: Het systeem ontruimt nu automatisch de cron_planning gegevensbestandlijst, verwijderend ingangen voor banen die niet meer in het systeem bestaan. Dit zorgt voor optimale prestaties door een minimaal aantal rijen in de tabel te handhaven. Eerder, werden de ingangen voor banen van inactieve of verwijderde modules niet schoongemaakt, die tot onnodige gegevensaccumulatie in de cron_planninglijst leidden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38217>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38693>
* _AC-10953_: De Prijs van de rij wordt niet geschrapt van Configurable Product
   * _nota van de Reparatie_: Het systeem verwijdert nu correct de rijprijs van een product wanneer het van een eenvoudig product aan een configureerbaar product wordt omgezet, die nauwkeurige prijsvertoning op het front verzekeren. Eerder werd de laagprijs van een configureerbaar product niet verwijderd wanneer een product werd omgezet van een eenvoudig product in een configureerbaar product, wat leidde tot een verschil in de weergegeven prijs.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38390>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38427>
* _AC-11804_: De beschrijving van de categorie WYSIWYG is leeg op niet standaard storeview
   * _nota van de Reparatie_: Het systeem bewaart nu correct en toont de categoriebeschrijving in de redacteur van WYSIWYG wanneer het uitgeven van een categorie op het niveau van de archiefmening. Eerder was de WYSIWYG-editor leeg nadat een categoriebeschrijving op het weergaveniveau van de winkel was opgeslagen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38622>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38623>
* _wisselstroom-11970_: Onmogelijk om configureerbare producten met één checkbox geselecteerde douaneoptie opnieuw in orde te brengen
   * _nota van de Reparatie_: Het systeem verwerkt nu correct het opnieuw ordenen van configureerbare producten met één enkele geselecteerde checkbox douaneoptie, die voor succesvolle korteverwezenlijking toestaat. Voorheen leidde het opnieuw ordenen van dergelijke producten tot een fout en werd voorkomen dat artikelen aan het winkelwagentje werden toegevoegd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38736>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1d144bce>
* _wisselstroom-12076_: [ Eis ] Reparatie van filterpunt op gelaagde navigatie
   * _nota van de Reparatie_: Het systeem gebruikt nu correct de woorden &quot;punt&quot;en &quot;punten&quot;in het gelaagde punt van de navigatiefilter, die de duidelijkheid en de nauwkeurigheid van de filterbeschrijvingen verbeteren. Eerder werden deze woorden onjuist gebruikt, waardoor gebruikers door de filteropties konden navigeren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38789>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37852>
* _AC-12164_: Datum en het Formaat van de Tijd voor de Optie van de Douane het Werken van de Optie van de Douane niet
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
   * _nota van de Reparatie_: Het systeem keurt nu correct een booleaanse waarde goed wanneer het gebruiken van —geen-updateoptie in sampledata:stel bevel op, dat om het even welke fouten tijdens de plaatsing van steekproefgegevens verhindert. Voorheen werd er een fout gegenereerd bij het gebruik van deze opdracht, omdat het systeem ten onrechte een gehele waarde verwachtte.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39344>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [ het gebruik van de Uitgave ] van de Oplossing van EAV geheim voorgeheugentype
   * _nota van de Reparatie_: Het systeem gebruikt nu correct het EAV geheim voorgeheugentype in alle relevante plaatsen, die verenigbare en efficiënte gegevens caching verzekeren. Eerder werd het EAV-cachetype niet consistent gebruikt, wat tot mogelijke inefficiënties en inconsistenties in het in cache plaatsen van gegevens leidde.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32322>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: Catalogus Geavanceerd zoeken met lege gegevens gaat naar de pagina[met zoekresultaten 2.4.dev filiaal]
   * _Fix-opmerking_: het systeem houdt gebruikers nu correct op de pagina Geavanceerd zoeken en geeft een foutmelding weer wanneer ze proberen een zoekopdracht uit te voeren zonder gegevens in te voeren. Voorheen werden gebruikers bij het uitvoeren van een lege zoekopdracht omgeleid naar de pagina Geavanceerd zoeken in de catalogus met een bericht waarin ze werden gevraagd hun zoekopdracht te wijzigen.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13622_: [Uitgave] Productlay-out op basis van attribute_set
   * _Fix-opmerking_: Het systeem maakt het nu mogelijk om de productlay-out aan te passen op basis van de attributenset, wat een praktischere en efficiëntere manier biedt om de productweergave in de frontend-winkel te beheren. Voorheen kon de lay-out alleen worden aangepast per SKU of per producttype, wat voor veel producten of specifieke artikelen niet altijd praktisch was.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38790>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36244>
* _AC-6738_: Ontbrekende unieke sleutel op eav_attribute_option_value lijst
   * _Fix-opmerking_: het systeem bevat nu een unieke sleutel in de kolommen &#39;option_id&#39; en &#39;store_id&#39; in de tabel &#39;eav_attribute_option_value&#39;, waardoor de mogelijkheid wordt voorkomen dat een optie meerdere waarden heeft voor dezelfde winkelweergave. Voorheen kon foutieve code ertoe leiden dat een optie meerdere waarden had voor dezelfde winkelweergave, wat problemen veroorzaakte bij het bewerken van producten of attributen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/24718>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/28796>
* _AC-8297_: [Probleem] Gebruik de zichtbaarheidsklasse voor de productindexeerder voor categorieën in plaats van hardgecodeerde waarden
   * _Fix-opmerking_: het systeem gebruikt nu de zichtbaarheidsklasse voor de categorieproductindexeerder in plaats van hardgecodeerde waarden, waardoor de modulariteit wordt verbeterd. Voorheen werden hardgecodeerde waarden gebruikt in de categorie productindexeerder, waardoor de flexibiliteit en het aanpassingsvermogen werden beperkt.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/37200>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/37199>
* _AC-9375_: Valutacode verandert niet in widget voor nieuwe producten
   * _Fix-opmerking_: het systeem werkt nu de valutacode in de widget Nieuw product correct bij wanneer de valuta in de frontend wordt gewijzigd, waardoor consistentie in de valutaweergave op de site wordt gegarandeerd. Voorheen had het wijzigen van de valuta in de front-end geen invloed op de valutacode die werd weergegeven in de widget Nieuw product.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37898>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37899>
* _ACP2E-2224_: De regelmatige Prijs toont niet op PLP voor Configureerbaar Product
   * _nota van de Reparatie_: De regelmatige prijs wordt nu getoond op de pagina&#39;s van de productlijst voor configureerbare producten die kindproducten met speciale prijs hebben.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2478_: De informatie van de voorraad die niet recht op het Visuele Net van de Verkoop toont
   * _nota van de Reparatie_: De voorraad wordt nu getoond volgens geselecteerde opslag.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/bdbf97ea>
* _ACP2E-2621_: De inhoud van widget werkt niet op cms pagina bij
   * _nota van de Reparatie_: Het systeem werkt nu de widgetinhoud op een pagina van CMS bij wanneer een product als nieuw en bewaard wordt geplaatst, ervoor zorgend dat de pagina de bijgewerkte productinzameling toont. Eerder werd de pagina niet bijgewerkt om het nieuwe product weer te geven vanwege een onjuiste cache-id voor de widget in de cache.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2630_: De kwesties die geavanceerde tarifering op bundelproducten besparen
   * _nota van de Reparatie_: Bundel productbesparende prestatiesverbetering.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2652_: [On-Premise] Re-indexproces is inefficiënt bij het maken van catalogusprijsregels
   * _Fix-opmerking_: Als u de catalogusprijsregel opslaat, worden de indexeerders niet ongeldig, maar worden alleen de getroffen producten opnieuw geïndexeerd
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>
* _ACP2E-2679_: Het bijwerken tijd van Datum en het type van Tijd productattributen via de invoer CSV
   * _nota van de Reparatie_: Nu datetime zullen de attributen tijd deel in uitgevoerde gegevens hebben. Het zal ook mogelijk zijn de tijd voor dergelijke kenmerken bij te werken met behulp van import. Ook als &quot;Fields Enclosure&quot; is ingeschakeld, worden kenmerkwaarden in de kolom &quot;additional_attributes&quot; tussen dubbele aanhalingstekens ingesloten.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38306>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2689_: Geen passende foutmelding wanneer de website-ID onjuist is in het verzoek
   * _nota van de Reparatie_: Nu werd het aangewezen foutenmelding toegevoegd aan vertoning wanneer website identiteitskaart in het verzoek verkeerd is. Eerder was er geen validatie toen de website-id in het verzoek verkeerd was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2785_: Het beeld van het product wordt verloren na het schrappen van een bestaande Geplande Update die niet het beeld beïnvloedt
   * _nota van de Reparatie_: De beelden van het product worden niet verwijderd terwijl het schrappen van het opvoeren update.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-2799_: [Cloud] Wrong bundel productprijs bij gebruik met staffelprijzen
   * _Vaste opmerking_: Voorheen genereerden kortingen die tot 2 cijfers achter de komma waren afgerond, bij het berekenen van bepaalde percentages, verschillende eindprijzen voor de winkelwagen en de pagina met productvermelding/productdetails. Nadat deze correctie is toegepast, is de uiteindelijke prijs voor het bundelproduct hetzelfde als op de pagina met productdetails, de productvermeldingspagina en de pagina met de miniwinkelwagen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38091>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2805_: Regel voor cataloguspromoties werkt niet met quantity_and_stock_status kenmerk
   * _Fix-opmerking_: het kenmerk quantity_and_stock_status wordt nu in aanmerking genomen door de cataloguspromotieregel, waarmee eerder geen rekening werd gehouden bij het genereren van een nieuw product aan de admin-kant.
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
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2871_: [Cloud] De handelaar heeft problemen met het aantal verlanglijstjes
   * _Fix-opmerking_: als u een product toevoegt aan de verlanglijst in de ene winkel, wordt het aantal verlanglijsten niet langer verhoogd in andere winkels die in dezelfde browser zijn geopend. Als beide winkels voorheen in dezelfde browser werden geladen, nam het aantal verlanglijstjes ook toe in de andere winkel.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2874_: De Pagina van de categorie bij frontend toont lege groeven wanneer het gebruiken van bundelproduct
   * _nota van de Reparatie_: De producten van de bundel die niet verkoopbaar in huidige archiefcontext zijn worden niet meer geïndexeerd.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/bc37ec76>
* _ACP2E-2888_: [ CLARIFICATION ] de lijstkwesties van de de opeenvolging van de Bundel
   * _nota van de Reparatie_: De verslagen in de lijsten van de het productopeenvolging van de Bundel (sequence_product_bundle_option, sequence_product_bundle_selection) worden nu verwijderd wanneer het product van de Bundel wordt geschrapt of de opties van het product van de Bundel worden geschrapt.
Eerder werden de records in de tabellen van de Bundle-productreeks niet verwijderd.
* _ACP2E-2905_: [ Cloud ] Uitgave van Citaat in multi-website architectuur
   * _nota van de Reparatie_: Eerder, multi-website architectuur met verschillende valuta en klantengroepen kon geen kortingen op de opslag correct toepassen. Nadat deze oplossing is geïmplementeerd, wordt een architectuur met meerdere websites met prijskortingen voor verschillende klantgroepen met succes toegepast op verschillende winkels.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38506>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2909_: dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice while editing bundle products
   * _nota van de Reparatie_: Er is geen fout javascript in browser console terwijl het schrappen van optie van bundelproduct.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38505>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-2950_: [ de verkeerde prijs van het Product van de Pakket van de Wolk ] in orde bevestiging
   * _nota van de Reparatie_: Het correcte bedrag wordt getoond voor bundelopties in orde op Storefront wanneer de munt buiten basale werd gebruikt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2956_: Video die van YouTube Bug toevoegt
   * _nota van de Reparatie_: De beelden en de video&#39;s van het product worden gevormd in globaal werkingsgebied. Aangezien u geen productvideo in één werkingsgebied en niet in een andere kunt hebben, is de belangrijkste het plaatsen van de sleutel van Youtube API aan globaal werkingsgebied geplaatst.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-2964_: [ de update van de Wolk ] URL slechts voor store_id=0
   * _nota van de Reparatie_: Het &quot;Weg URL&quot;wordt nu opgeslagen met correcte opslagidentiteitskaart Eerder was de opslag-id onjuist, waardoor er onjuiste URL-paden in de database achterbleven wanneer categorieën worden verplaatst.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/9af794a4>
* _ACP2E-3009_: async.operations.all uitgevoerd en er is een fout gemaakt.
   * _nota van de Reparatie_: De onjuiste gegevens van de productverbinding in vraag REST API veroorzaken niet meer kritieke fouten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>
* _ACP2E-3029_: [ de Mobiele Uitgave van de Wolk ] kan slechts niet op het beeld pinch PDP
   * _nota van de Reparatie_: Het systeem steunt nu knijpbeweging-aan-gezoemfunctionaliteit op de beelden van de productdetailpagina in mobiele mening op Chrome, die de mobiele gebruikerservaring verbeteren. Eerder werd niet op de afbeelding ingezoomd door te dubbeltikken op de afbeelding in de mobiele weergave op Chrome.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3058_: Ontbrekend label in LayeredNavigation met optienaam 0
   * _Fix-opmerking_: het probleem is opgelost door een lege waardecontrole voor kenmerkwaarde 0 over te slaan. Voorheen werd het als leeg beschouwd en veroorzaakte het het probleem.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3069_: De klanten zien prijzen van andere klantengroepen
   * _Nota van de Reparatie_: Vaste kwestie waar de klantengroep verwante informatie in een verkeerd segment wegens de oude waarde van X-Magento-Vary in verzoek werd bewaard
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d1f7dc95>
* _ACP2E-3076_: Fout wanneer het schrappen van bundelopties
   * _nota van de Reparatie_: Het systeem schrapt nu correct bundelopties zonder een fout teweeg te brengen of de pagina te veroorzaken om niet ontvankelijk te worden. Als u voorheen bundelopties verwijdert, treedt de fout &quot;Pagina reageert niet&quot; op en wordt het product niet opgeslagen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3094_: De Toestemmingen van de categorie uit de kwestie van geheugenbrowser
   * _nota van de Reparatie_: De Toestemmingen UI van de categorie werd opnieuw ontworpen om het teruggeven van een grote hoeveelheid toestemmingen toe te staan die uit doos UI component en paginering gebruiken. Eerder categorietoestemmingen zouden ervoor zorgen dat de browser vastloopt met een grote hoeveelheid machtigingen die aan de categorie zijn toegewezen.
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
* _ACP2E-3350_: De gehandicapte Categorieën hebben niet meer hun namen grijs uit in de categorieboom
   * _nota van de Reparatie_: Eerder, werden de gehandicapte categorieën niet grijs uit in de categorieboom. Nu worden ze weergegeven met een grijs-uiteffect.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: Configureerbaar product bewerken formulier laden veroorzaakt time-out en geheugenuitputting
   * _Opmerking voor_ de oplossing: Voorafgaand aan de oplossing werden configureerbare productvariaties geconstrueerd op basis van alle mogelijke combinaties van kenmerkopties. In gevallen waarin kenmerken veel opties hadden, resulteerde dit in een langdurige en hulpbronnenintensieve bewerking. Configureerbare productvariaties worden nu samengesteld op basis van bestaande onderliggende productkenmerken. Dit leidt tot veel minder berekeningen, dus tot een beter gebruik van middelen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: Fotorama laadt correct geen video wanneer het gebruiken van Monsters en de optie wordt pre-geselecteerd via URL
   * _nota van de Reparatie_: De video&#39;s van het product zullen nu behoorlijk op configureerbare pagina van productdetails teruggeven, als URL geselecteerde opties bevat.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: De Breedte van Carousel PageBuilder toont producten die voorwaarden niet aanpassen
   * _Fix-opmerking_: productlijst die in widgets wordt gebruikt, respecteert nu de categorievoorwaarde
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: validatiefout geactiveerd voor alle producten in de groep wanneer men een ongeldige hoeveelheid heeft
   * _Fix-opmerking_: Nu wordt de validatiefout correct geactiveerd voor alle producten in de groep wanneer een product een ongeldige hoeveelheid heeft, wat voorheen niet gebeurde.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3513_: [ CLOUD ] Speciale prijs die niet in Configurable product toont
   * _nota van de Reparatie_: Na de moeilijke situatie, die de &quot;Gebruikt in de Lijst van het Product&quot;waarde voor het speciale prijsattribuut verandert zal niet het tonen van de speciale prijs voor configureerbare producten beïnvloeden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d4de4726>
* _ACP2E-3516_: Indexeertafels Tijdelijke tabellen worden niet opgeschoond als het proces wordt beëindigd
   * _Fix-opmerking_: tijdelijke tabellen van de CatalogRule-indexeerfunctie worden nu opgeschoond als het indexeerproces wordt beëindigd
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
   * _nota van de Reparatie_: Eerder, toen het bewaren van een pagina van CMS met een bijgewerkte ontwerplay-out, bezat het niet geschikt op het vooreind. Nadat deze correctie is toegepast, wordt de juiste ontwerplay-out aan de voorzijde weergegeven wanneer de ontwerplay-out wordt gewijzigd en de CMS-pagina wordt opgeslagen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3131_: [ de Categorieën van het Anker van de Wolk ] Anker/niet-Anker die in Inhoud Widget wordt omgekeerd
   * _nota van de Reparatie_: Eerder, toen wij Vertoning op -> de Categorieën van het Anker selecteerden, toonde het alle categorieën die niet de ouder-kind verhouding tussen het anker en niet-anker weerspiegelden. Nadat deze correctie is toegepast, worden in de Categorieën Weergeven op -> Anker alleen de ankercategorieën weergegeven (selecteerbaar) en in de Categorieën Weergeven op -> Niet-anker worden de niet-ankercategorieën weergegeven (selecteerbaar)
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3152_: Categorieën die niet met widgets werken
   * _nota van de Reparatie_: Eerder, als wij het blok van CMS voor verschillende anker/niet ankercategorieën bewaarde, het niet voor de kindcategorieën werkte toen het op het vooreind toonde. Nadat deze correctie is toegepast, wordt het blok aan de voorzijde weergegeven voor verschillende categorieën.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d01ee51e>

### Catalogus, framework

* _AC-9111_: De orde krijgt (Verzendingen|Creditmemos|Factuur)Inzameling - de Inzameling zou niet moeten worden geladen
   * _nota van de Reparatie_: Het systeem zorgt nu ervoor dat de inzamelingen voor verzendingen en creditmemo&#39;s niet vooraf geladen wanneer teruggewonnen van een orde, die voor extra filters of orden toestaat om op deze inzamelingen worden toegepast. Eerder werden deze verzamelingen automatisch geladen, zodat er geen verdere wijzigingen konden worden aangebracht.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37561>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37562>
* _ACP2E-2949_: [ Cloud ] follow-up: Verkeerde gelijke in Gegevens Vergelijking wanneer het controleren als het gegeven veranderingen heeft
   * _nota van de Reparatie_: Eerder, werd het sparen voorwerp geroepen telkens zonder enige gegevensveranderingen (voor om het even welk numeriek gegevensgebied - zoals int/float/dubbel). Het activeert de markering _hasDataChanges om waar te zijn en roept de opslagfunctie aan. Het controleert ook niet de drijvende aantallen die door koord worden ingekapseld. Nadat deze correctie is toegepast, wordt de functie Save alleen aangeroepen als de gegevens zijn gewijzigd. De gegevenswaarde voor int/float/double-check met de waarde die aan de functie wordt doorgegeven en het strikte type dat overeenkomt
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8931218>

### Catalogus, GraphQL

* _ACP2E-3090_: Het behandelen van de Filters van de Categorie in GraphQL: includeDirectChildrenOnly en category_uid
   * _Bevestig nota_: Slechts worden de directe kindcategorieën gehaald terwijl het filtreren door category_uid.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/93d50f8d>
* _ACP2E-3166_: [ Cloud ] Grafiek het sorteren van het Product werkt niet
   * _Bevestig nota_: Het sorteren van het Product GraphQl door veelvoudige gebieden wanneer de gebieden in variabelen nu worden overgegaan werkt zoals verwacht.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3312_: De terugkeer van de prijzen van de lijst verkeerde waarde in producten GraphQL (in vergelijking met Storefront)
   * _Fix-opmerking_: Na de fix hebben de staffelprijzen van het product die worden geretourneerd voor graphql-verzoeken een prijs per item.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_: [CLOUD] B2B: categorie probleem via GraphQL
   * _Fix-opmerking_: Na de oplossing retourneert de categorieën graphql-query categorieën met toestaan, zelfs als de hoofdcategorie geen toelatingsmachtiging heeft.

### Catalogus, prijzen, enscenering en preview

* _ACP2E-2672_: [ het eindpunt van de PrijsAPI van de Wolk ] keert fout terug wanneer het bijwerken van grote aantallen producten gelijktijdig
   * _de nota van de Reparatie_: Nu zal de speciale Prijs update API één enkele campagne voor elke datumwaaier in plaats van veelvoudige geplande updates voor elk product en datumwaaier tot stand brengen. Bovendien worden gelijktijdige API-aanvragen voor snellere verwerking van een groot aantal SKU&#39;s ondersteund.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/f89a447e>

### Catalogus, product

* _AC-7050_: De boomstructuur van de categorieselectie in geeft product uit is niet in de zelfde orde zoals die in Catalog ->Categorieën wordt geplaatst
   * _nota van de Reparatie_: Het systeem toont nu correct de boomstructuur van de categorieselectie in product uitgeeft sectie in de zelfde orde zoals die in Catalogus ->Categorieën wordt geplaatst, makend productbeleid in grote catalogi gemakkelijker. Eerder werd de categoriestructuur in de productbewerkingssectie weergegeven in de volgorde van het maken van de categorie, ongeacht de weergavevolgorde ingesteld in Catalog->Categorieën.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36101>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36104>

### Catalogus, SEO

* _ACP2E-3653_: Onjuiste canonieke URL voor categorie wanneer pagina > 1
   * _nota van de Reparatie_: Eerder, werkte canonieke URL voor multi-page inhoud niet correct, constant tonend basis URL. Nadat de correctie is geïmplementeerd, wordt de URL voor inhoud van meerdere pagina&#39;s nu correct weergegeven met de pagina-id.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/982b1c42>

### Catalogus, Zoeken

* _ACP2E-2757_: De producten tonen niet op categorie en onderzoek maar de directe verbindingen werken
   * _Bevestig nota_: Eerder, werkt het ja/Geen douaneattribuut met price_* attribute_code niet met het indexeren. Na deze correctie werkt het kenmerk Yes/No naar behoren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-3053_: [ Cloud ] Elastische onderzoeksfout op bepaalde categoriepagina&#39;s
   * _nota van de Reparatie_: Eerder, met het vermelde configuratiekaartje, wanneer wij prijs 0 voor veelvoudige producten zetten, zal het een uitzondering bij de voorste categoriepagina werpen. Nadat deze correctie is toegepast wanneer meerdere productprijzen 0 en we de pagina met categorieën vooraf laden, wordt er geen uitzondering gegenereerd en wordt de pagina met categorieën correct geladen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3345_: Typefout opgetreden bij het maken van object: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Exception
   * _Opmerking over_ de oplossing: na de oplossing kan een exemplaar van de klasse Magento\CatalogSearch\Model\Indexer\Fulltext worden gemaakt zonder $data op te geven.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [ CLOUD ] Kwestie met Producten is niet Zichtbaar op Voorzijde na het Opslaan in Admin van Magento
   * _nota van de Reparatie_: Na de moeilijke configureerbare producten die kindproducten met lange namen hebben zullen niet in de storefront worden gemist.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>

### Catalogus, verzenden

* _ACP2E-3195_: Verzendadres leeg bij het plaatsen van een bestelling voor een cadeaulijstje
   * _nota van de Moeilijke situatie_: Eerder, voor gast-gebruiker gift-registratie punten, wanneer teruggekeerd van de e-mailfunctie, produceerde een leeg leeg adres, dat voor het plaatsen van een orde onjuist is. Nadat deze moeilijke situatie wordt toegepast, controleert het geschenkenregister het programma geopende gebruiker/gastgebruikers en toegewezen adressen als zij bestaan.

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
   * _nota van de Reparatie_: Het systeem herstelt nu achterwaartse verenigbaarheid met stop TinyMCE, toestaand functies die binnen de stop worden bepaald om worden geroepen wanneer het gebruiken van widget van een andere plaats. Eerder, als gevolg van een wijziging in de TinyMCE-versie, retourneerden de plug-ins de widgets niet als een object, wat resulteerde in een fout bij het aanroepen van bepaalde functies op de widget-instantie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39262>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39258>
* _AC-9638_: [ het dossier van de kwestie ] uploadt kwestie in de redacteur van WYSIWYG op productpagina
   * _nota van de Reparatie_: Het systeem toont nu correct de omslagboom en staat beeld toe uploadt in de redacteur van WYSIWYG op de productpagina, zelfs na het uitbreiden van het &quot;Beeld en Video&#39;s&quot;lusje eerst. Eerder werd door het uitvouwen van het tabblad &#39;Afbeelding en video&#39;s&#39; de mappenstructuur niet weergegeven en werd een foutbericht weergegeven wanneer werd geprobeerd een afbeelding te uploaden in de WYSIWYG-editor.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38026>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38025>
* _ACP2E-2392_: [ On-PREM ] Dynamische blokkwestie
   * _Bevestig nota_: De widgets worden nu behoorlijk teruggegeven binnen dynamische blokken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2606_: YouTube nocookie url die niet in de Bouwer van de Pagina werkt
   * _Fix-opmerking_: Nu staat de pagebuilder de youtube no-cookie-url toe in de instellingen van het formulierelement van de validatieregels. Voorheen werkte de youtube no-cookie url niet in pagebuilder.
* _ACP2E-2693_: [Cloud] Frontend laadt niet vanwege probleem in nieuwsbriefsjabloon
   * _Fix note_: Het toevoegen van blokken via CMS Page content section leidt niet meer tot uitzonderingen
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2836_: ACP2E-2836: [ Cloud ] onderzoekt uitzondering die in het logboek wordt gevonden: InvalidArgumentException: De klasse bestaat niet in vendor/magento/module-rule/Model/ConditionFactory.php
   * _nota van de Reparatie_: Het verwijderen van een voorwaarde op de montages van de de productinhoud PageBuilder veroorzaakt niet meer een uitzondering om in de logboekdossiers worden geregistreerd. Eerder, zou het verwijderen van een voorwaarde op de montages van de de productinhoud PageBuilder een kritieke uitzondering veroorzaken om in de logboeken worden geregistreerd, ondanks het veroorzaken van geen kwesties op het front-end.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/36c0f5df>
* _ACP2E-2842_: Het schakelen naar enige opslagwijze - de globale inhoud verschijnt niet meer
   * _nota van de Reparatie_: Het systeem synchroniseert nu de configuraties van het opslagmeningsontwerp met de configuraties van het websiteontwerp wanneer het toelaten van enige opslagwijze, die ervoor zorgen dat de inhoudsupdates op het frontend zichtbaar zijn. Eerder, zou het schakelen op enige opslagwijze inhoudsupdates worden weerspiegeld op de storefront verhinderen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-2903_: De Bouwer van de pagina vervangt beeld wanneer het proberen om verbinding en andere bruikbaarheidsglitches toe te voegen.
   * _nota van de Reparatie_: Nu het klikken op een beeld, zullen de verbindingen in beeldredacteur in het de tekstelement van de Bouwer van de Pagina juiste gegevens in het beeld, de dialoog van de verbindingsconfiguratie laden. Het toevoegen van een koppeling naar een afbeelding in de editor werkt nu goed. Eerder werd de afbeelding vervangen door een koppeling.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-2970_: De oude media galerij ontbreekt om beelden terug te geven wanneer een 0 byte beeld in de folder wordt geplaatst
   * _nota van de Reparatie_: Het systeem behandelt nu 0 byte beelden in de media galerij zonder functionaliteit te verstoren, toestaand andere beelden in de folder om worden getoond en worden geselecteerd zoals verwacht. Eerder was het zo dat door de aanwezigheid van een afbeelding van 0 byte in de mediagalerie niet alle afbeeldingen in de directory konden worden weergegeven of geselecteerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3064_: De Bouwer van de Pagina van de fout wanneer het uitgeven van het Blok van CMS
   * _nota van de Reparatie_: Het systeem bewaart nu correct veranderingen die in het admin gebied worden aangebracht gebruikend de Bouwer van de Pagina, zonder de fout &quot;Bouwer van de Pagina terug te werpen voor 5 seconden zonder sloten vrij te geven.&quot; in de browserconsole. Deze fout is eerder opgetreden tijdens een poging om wijzigingen op te slaan, zodat de inhoud niet met succes kan worden bijgewerkt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3092_: [ CLOUD ] Geen knopen van controle of geeft kart op de wortelsectie uit
   * _nota van de Reparatie_: Het product van de bundel wordt nu toegevoegd aan het karretje via widgets zonder fouten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b21e5d91>, <https://github.com/magento/magento2-page-builder/commit/4ebe3f1d>
* _ACP2E-3113_: De voorproef van het Staging van de inhoud op categoriepagina&#39;s toont product widgets niet
   * _nota van de Reparatie_: De kwestie is bevestigd door ervoor te zorgen dat de productingangen voor de extra categorie verbonden aan het blok van CMS correct in het gegevensbestand zijn geregistreerd. Eerder werd een lege resultatenset geretourneerd toen de pagina met voorvertoningen van rubrieken werd opgevraagd.
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
   * _Fix-opmerking_: het probleem is opgelost door ervoor te zorgen dat de lijst met schuifregelaars wordt vernieuwd terwijl de opslaggebeurtenis wordt geactiveerd op het scherm met de dia bewerken. Voorheen was het het triggeren en veroorzaken van het probleem.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Een fout komt in CSM pagina voor wanneer de blokken van CMS gebruikend paginabouwer in bepaalde orde worden opgenomen
   * _nota van de Reparatie_: Eerder op sommige versies van PHP en OS (Linux), zou het teruggeven van blokken die andere cms blokken door PageBuilder van verwijzingen voorzien met een &quot;Onbekende fout voorgekomen zijn ontbroken. Probeer het opnieuw.&quot;. Nu wordt de inhoud van de cms-blokken correct gerenderd in inhoud die door PageBuilder wordt gecontroleerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_: [ de Dynamische blokken van de Wolk ] zullen niet behoorlijk functioneren
   * _Bevestig nota_: Logged-in klantensegmenten worden nu ontruimd na logout verhinderend de gastzitting eerder het programma geopende segmenten erven
* _ACP2E-3428_: De mislukking van de malplaatjevoorproef van de Bouwer voor grote inhoud
   * _Fix-opmerking_: Grote inhoud leidde ertoe dat het canvaselement de limieten van de browser overschreed en een onjuiste waarde retourneerde, waardoor de backend-code werd verbroken (kan de afbeelding niet goed worden gedecodeerd). Opgelost met het beperken van de canvasgrootte tot de limiet van de universele browser.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2-page-builder/commit/adfb1747>
* _ACP2E-3430_: Laatste beveiligingsupdates met TinyMCE 7 ontbrekende lettergrootte
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

### Inhoud, SEO

* _ACP2E-2870_: De hiërarchie van de Pagina van CMS kan URL veroorzaken herschrijft kwesties
   * _Bevestig nota_: Eerder, voor douane permanent URL herschrijft voor niet-website wortelpagina&#39;s, eindeloos opnieuw richt en de pagina werd nooit geladen. Nadat deze correctie is toegepast, werkt de aangepaste URL voor het herschrijven van de hoofdpagina van de niet-website naar behoren en vindt er geen omleidingslus plaats.

### Inhoud, Staging en Voorvertoning

* _ACP2E-2979_: De de prijsregel van de catalogus toont niet wanneer het aan programma met dynamische blokken wordt geplaatst
   * _nota van de Reparatie_: Het systeem toont nu correct dynamische inhoud verbonden aan de geplande regels van de catalogusprijs op de pagina van het productdetail. In het verleden kon dynamische inhoud niet worden geladen toen de prijsregels voor de catalogus waren gepland.

### Klanten/klanten

* _AC-12162_: Voorste eind - de bevestiging van de geboorte ontbreekt in de aanmaakpagina van de Klant
   * _nota van de Reparatie_: Verzeker al bevestiging zou na verbeteringsmoment.js systeemgebiedsdeel aan de recentste minder belangrijke versie moeten werken
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/de4dfb8e>
* _AC-13060_: Het Segment van de klant > Voorwaarde > Geschiedenis van het Product* > &quot;het product werd bekeken&quot;werkt niet
   * _nota van de Reparatie_: Het systeem toont nu correct gecompenseerde klanten in het &quot;Product werd bekeken&quot;voorwaarde onder de Segmenten van de Klant, wanneer aan de voorwaarde wordt voldaan. Eerder was het aantal geregistreerde klanten dat bij een transactie was betrokken, zelfs toen aan de voorwaarde was voldaan, nul.
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
* _AC-10838_: Indexeringsproces voor cataloguszoekindexen
   * _Fix-opmerking_: Het systeem voltooit nu met succes het re-index-commando zonder fouten tegen te komen, ongeacht de libxml-versie die met PHP is gecompileerd. Voorheen resulteerde het uitvoeren van de opdracht opnieuw indexeren in een &quot;Catalog Search index process error during indexation process&quot; fout wanneer PHP werd gecompileerd met bepaalde versies van libxml.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38254>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38553>, <https://github.com/magento/magento2/commit/0574ac23>
* _wisselstroom-10941_: Toegevoegde created_at, status en de filters Grand_total aan de vraag van de Orden van de klant en bevonden veelvoudige filtermislukking
   * _nota van de Reparatie_: Het systeem steunt nu het gebruik van created_at, status, en de filters Grand_total in de vragen van de Orden van de klant, en heeft een kwestie opgelost waar de veelvoudige filters niet correct werden toegepast. Eerder, steunde het systeem deze filters niet en zou er niet in slagen om alle filters toe te passen wanneer meer dan één in een vraag werd gebruikt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38392>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36949>
* _AC-10991_: Willekeurig overstroomd krijgen met vragen van verwant/upsell/crosssell blokken en prijs het indexeren
   * _nota van de Reparatie_: Het systeem optimaliseert nu vragen van verwant, upselt, en dwars-verkoopt blokken, verbeterend de prestaties en verhinderend de plaats om te gaan toe te schrijven aan bovenmatige vragen. Eerder, kon het systeem met vragen van deze blokken overbelast worden, veroorzakend significante vertragingen en potentieel verlamend de plaats.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36667>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38050>
* _AC-11423_: Uitzondering: Waarschuwing: Het proberen om tot seriecompensatie binnen toegang te hebben.. -> Calendar.php sinds verbetering aan ICU 74.1 (PHP Intl)
   * _nota van de Moeilijke situatie_: Commerce registreert niet meer de volgende uitzondering in exception.log wanneer een verkoopster of handelaar of storefront of Admin bezoekt: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62`. [ GitHub-38214 ](https://github.com/magento/magento2/issues/38214)
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38214>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38364>
* _AC-11476_: [ de kwesties van de Uitgave ] verhelpen met de Gegevens van de Klant wanneer de vorm element met naam `method` bevat
   * _nota van de Reparatie_: Het systeem identificeert nu correct de &quot;methode&quot;attributen in vormvoorlegging, zelfs wanneer een element genoemd &quot;methode&quot;in de vorm aanwezig is. Dit zorgt voor een nauwkeurige verwerking van klantgegevens. Als een formulierelement voorheen de naam &#39;methode&#39; had, zou dit de identificatie van het kenmerk &#39;methode&#39; in formulierinzendingen verstoren, wat leidde tot mogelijke problemen met de verwerking van klantgegevens.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38484>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38449>
* _AC-11489_: [ Uitgave ] Repareer PHPDocs voor \Magento\Framework\Data\Collection::getItemById
   * _nota van de Reparatie_: PHPDocs voor de \Magento\Framework\Data\Collection::getItemById methode is bijgewerkt om ongeldig als mogelijk terugkeertype te omvatten, richtend kwesties met statische analysehulpmiddelen. Eerder, specificeerde PHPDocs van de methode ongeldig als mogelijk terugkeertype niet, dat tot waarschuwingen of fouten in statische analyse leidde toen de methode in voorwaardelijke verklaringen werd gebruikt.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38485>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38439>
* _AC-11592_: [ Uitgave ] staat slechts geldige voorkeur tijdens opstelling toe :di: compileert
   * _nota van de Reparatie_: Het systeem werpt nu een fout tijdens de opstelling :di: compileert bevel als een voorkeur voor een klasse wordt gecreeerd die niet bestaat of specifiek uitgesloten is, die ervoor zorgt dat slechts de geldige voorkeur wordt toegestaan. Eerder, zouden deze scenario&#39;s ongemerkt ontbreken, potentieel die om het even welke stop-ins verbonden aan de originele klassen nutteloos teruggeven.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38517>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/33161>
* _AC-11651_: Magento die probeert om read-only bezit in __wakeup methode van LoggerProxy te wijzigen
   * _nota van de Reparatie_: Het systeem staat nu de wijziging van eerder read-only eigenschappen in de methode __wakeup van LoggerProxy toe, die vlotte verrichting verzekert zonder gebruikers te dwingen om een alternerende actie aan te wenden. Eerder, zou een poging om de waarde van een read-only bezit in de methode __wakeup van LoggerProxy opnieuw toe te wijzen kwesties veroorzaken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38526>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c8f87c25>
* _AC-11681_: [Uitgave] AC-2039 AC-1667 upgrade TinyMCE referenties
   * _Fix-opmerking_: Bijgewerkte tinymce nieuwste versie in composer.json
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38533>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/36543>, <https://github.com/magento/magento2/commit/b34c0a75>
* _AC-11696_: ChangelogBatchWalker werkt niet in meerdere threads
   * _Fix-opmerking_: Het systeem ondersteunt nu procesvork voor MView-indexering, waardoor fouten tijdens de uitvoering van de indexeerfunctie worden voorkomen bij het werken op meerdere threads. Eerder, zou het runnen van ChangelogBatchWalker op veelvoudige draden tot de schrapping van lijsten leiden die door andere draden worden gebruikt, die een fout tijdens indexeruitvoering veroorzaken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38246>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38248>
* _AC-11781_: [ Uitgave ] noemt verkeerd genoemde variabele anders
   * _Fix-opmerking_: Het systeem geeft nu de juiste naam van de variabele die het bedrag bevat dat nog kan worden terugbetaald, waardoor verwarring tijdens het debuggen wordt voorkomen. Voorheen werd deze variabele ten onrechte genoemd als totalRefund, wat tot misverstanden voor ontwikkelaars kon leiden.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38609>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/36205>
* _AC-11809_: [Uitgifte] Geef aangepaste attributen door aan de huidige link via XML
   * _Fix-opmerking_: het systeem staat nu toe dat aangepaste attributen via XML worden doorgegeven aan de huidige link, zodat deze attributen correct worden weergegeven, zelfs als de link de huidige pagina is. Voorheen werden aangepaste kenmerken niet weergegeven voor de huidige paginakoppeling omdat de methode getAttributesHtml() niet werd gebruikt voor de huidige koppeling.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38500>
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
* _AC-11874_: Achterwaartse compatibiliteit is verloren gegaan in de klasse Magento\Catalog\Model\ProductRepository
   * _Opmerking oplossen_: De klasse ProductRepository behoudt nu achterwaartse compatibiliteit door de klasse Initialization Helper als de tweede parameter te herstellen, zodat modules die uit deze klasse voortvloeien, functioneren zoals verwacht. Voorheen resulteerde het verwijderen van de Initialization Helper uit de constructor in de klasse ProductRepository in een verlies van achterwaartse compatibiliteit, waardoor gebruikers gedwongen werden een tijdelijke oplossing te gebruiken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38669>
* _AC-11905_: [ geef ] Statische inhoud uit - de fout van het Type
   * _nota van de Reparatie_: Het systeem behandelt nu correct lege dossiers LESS tijdens statische inhoudsplaatsing, tonend een &quot;LESS dossier is leeg&quot;foutenmelding. Eerder werd een fout met een onjuist type gegenereerd bij het optreden van een leeg LESS-bestand tijdens de implementatie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38682>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38683>
* _AC-12002_: [Probleemweergave] [] Extra ruimte verwijderd in link en scripttag
   * _Fix-opmerking_: Het systeem zorgt er nu voor dat er geen extra spaties zijn in de link- en scripttags, wat zorgt voor schonere en efficiëntere code. Voorheen waren er dubbele spaties te vinden tussen attributen in de link- en scripttags.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/32920>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32919>
* _AC-12127_: [Probleem] vermijd een verkeerde configuratie oneindige lus
   * _Fix-opmerking_: het systeem vermijdt nu een oneindige lus door zelfreferentiële toewijzing in virtuele typeconfiguraties te voorkomen. Dit zorgt ervoor dat de applicatie niet vast komt te zitten in een eindeloze lus wanneer wordt geprobeerd een zelfreferentiële node te derefereren. Als een virtuele typeconfiguratie voorheen naar zichzelf verwees, zorgde dit ervoor dat de toepassing voor onbepaalde tijd draaide.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38822>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: Object Manager wordt niet gebruikt voor Magento\Csp\Model\Mode\Data\ModeConfigured
   * _nota van de Moeilijke situatie_: Het systeem gebruikt nu correct de Manager van Objecten wanneer het creëren van het voorwerp ModeConfigured, toestaand plugins om op dit voorwerp worden gebruikt. Eerder werd Objectbeheer niet gebruikt, waardoor plugins niet konden worden toegepast op het ModeConfigured-object.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38875>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38886>
* _wisselstroom-12540_: De onjuiste mededeling van het documentblok in de Beeld van het Product en de Waarschuwingen van de Prijs
   * _Nota van de Oplossing_: De nota van het documentblok voor de deleteCustomer methode in de Aandelen van het Product en de Alarm van de Prijs is verbeterd om nauwkeurig te wijzen op dat de methode alle voorraadproduct of prijsalarm verbonden aan een bepaalde klant en een website, niet de klant van de website schrapt. Eerder werd in de opmerking onjuist aangegeven dat de methode bestond in het verwijderen van een klant van de website.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38939>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39001>
* _AC-12594_: [ Gecompileerde config van het Gebruik van de kwestie ] voor geproduceerde gegevens in plaats van algemene config
   * _nota van de Reparatie_: Het systeem gebruikt nu de gecompileerde configuratie voor geproduceerde gegevens in plaats van de algemene configuratie, die netwerkoverdracht en overheadkosten van gegevens vermindert die van een bepaalde versie van code afhangt. Door deze wijziging wordt voorkomen dat cache wordt overschreven in gedeelde instanties tijdens het wisselen van containers. Dit leidt tot betere stabiliteit en minder downtime. Eerder, gebruikten bepaalde kernklassen het gedeelde configuratietype, dat tot geheim voorgeheugen het met voeten treden of toepassingsonderbreking wegens verschillen in codeversies over veelvoudige servers kon leiden.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38785>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/29954>
* _AC-12597_: [Probleem] Verwijder verwijzingen naar bestanden uit extjs die zijn verwijderd in e1ccdb...
   * _Fix-opmerking_: het systeem verwijdert nu verwijzingen naar bestanden uit extjs die eerder zijn verwijderd, waardoor fouten in de console van de browser en het systeemlogbestand worden geëlimineerd. Voorheen veroorzaakten deze verwijzingen fouten vanwege het ontbreken van de bestanden waarnaar wordt verwezen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38960>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38951>
* _AC-12778_: [ geef ] Kleine schoonmaak uit: het vaste verkeerde gebruik van sprintf, het neemt slechts 2 placeholders hier en w...
   * _Fix-opmerking_: het systeem gebruikt nu correct de sprintf-functie met het juiste aantal tijdelijke aanduidingen, waardoor de code netter en consistenter wordt. Voorheen werd de sprintf-functie verkeerd gebruikt met een extra argument, wat geen grote problemen opleverde, maar niet het juiste gebruik was.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39062>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38628>
* _AC-12857_: PHP 8.2.15 verwijderde de uitbreiding van FTP
   * _nota van de Reparatie_: Het systeem omvat nu de uitbreiding van FTP als gebiedsdeel in het composer.json- dossier, die de succesvolle configuratie van de invoer CSV via FTP verzekeren. Eerder werd een fout gegenereerd bij het configureren van CSV-import via FTP omdat de FTP-extensie ontbreekt in het PHP-pakket.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39083>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/47b448e2>
* _wisselstroom-12869_: [ de 3} Correcties van de Uitgave {onjuiste klassen die in de modules van Magento worden van verwijzingen voorzien.]
   * _nota van de Reparatie_: Het systeem verwijzingen nu correct klassen in modules, die vlottere verrichting verzekeren en neerstortingen wegens niet-bestaande klassen verhinderen. Dit omvat een bugfix in de modules Indexer en Creditmemo en de implementatie van de HttpGetActionInterface in de PrintAction-klasse. Eerder, leidden de onjuiste klassenverwijzingen tot fouten en potentiële systeemneerstortingen, en bepaalde functionaliteiten, zoals filename voor creditmemo PDF dossiers en het opnieuw indexeren van voorraden, werkten niet zoals verwacht.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39126>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/37784>
* _AC-12964_: Mogelijkheid om Gebied voor dev :di: info CLI bevel te bepalen
   * _Fix-opmerking_: het systeem stelt ontwikkelaars nu in staat om een gebied te definiëren voor de CLI-opdracht voor:di:ontwikkelaarsinformatie, waardoor het ontwikkelings- en foutopsporingsproces wordt verbeterd. Eerder kon deze opdracht alleen informatie weergeven voor het GLOBAL-gebied.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38758>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38759>
* _AC-13149_: [ geef ] toe voeg isMultipleFiles bezit aan het malplaatje van het beeldvormelement toe
   * _nota van de Reparatie_: Deze moeilijke situatie, verhindert &quot;doorbladeren om beeld hier te vinden of te slepen&quot;knoop om te verdwijnen wanneer een beeld in een veelvoudige het vormelement van het dossierbeeld wordt toegevoegd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39219>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36325>
* _AC-13247_: opstelling:verbetering ontbreekt met MariaDB 11.4 versie toe te schrijven aan charset &amp; collationveranderingen
* _AC-13279_: [ Uitgave ] verwijdert alle marketing parameters krijgen om het geheime voorgeheugen te minimaliseren
   * _nota van de Reparatie_: Het systeem verwijdert nu alle marketing krijgen parameters om geheim voorgeheugengebruik te optimaliseren, die de logica weerspiegelen die wordt gebruikt wanneer Varnish in gebruik is. Eerder, konden deze parameters tot geheim voorgeheugenopblazing en verminderde prestaties leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39266>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [ Uitgave ] [ PHPDOC ] verbeter slechte phpdoc Magento\Directory\Model\AllowedCountries::getAllowedCountries ()
   * _nota van de Reparatie_: De PHPDoc voor AllowedCountries::getAllowedCountries () methode is verbeterd om nauwkeurige informatie te verstrekken, die de duidelijkheid en het nut van de documentatie verbetert. Eerder bevatte de PHPDoc voor deze methode onjuiste informatie, die tot verwarring of misbruik van de methode kon leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39246>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39241>
* _AC-13348_: [Probleem] Verwijdert wat code voor PHP-versies die we niet langer ondersteunen.
   * _Fix note_: Verwijdering van code voor PHP-versies die niet langer worden ondersteund in Magento
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39361>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [Probleem] Maak de ImageMagick Adapter compatibel met php8 (Impliciete conversie van float naar int)
   * _nota van de Reparatie_: Het systeem verzekert nu verenigbaarheid met PHP8 door vlotteraantallen correct te behandelen wanneer het berekenen van beelddimensies, die om het even welke fouten te voorkomen toe te schrijven aan impliciete omzetting van vlotter aan int. Eerder kon de berekening van de afmetingen van de afbeelding leiden tot zwevende getallen, die bij impliciet afronden een fout zouden veroorzaken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39402>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [ Uitgave ] [ PHPDOC ] verbeter slechte phpdoc Magento\Framework\App\Config\ScopeConfigInterface
   * _nota van de Reparatie_: Deze update verbetert de annotaties PHPDoc in Magento\Framework\App\Config\ScopeConfigInterface om het type van het argument $scopeCode voor getValue en isSetFlag nauwkeurig te wijzen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39492>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39199>
* _AC-13725_: Magento\Framework\Filesystem\Driver\Http hangt van redenuitdrukking O.K. af
   * _nota van de Reparatie_: Verwijderd &quot;O.K.&quot;woordcontrole van Magento\Framework\Filesystem\Driver\Http::isExists
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39546>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39558>
* _AC-13810_: De indexeerder van het Net van de klant werkt niet behoorlijk in Update door de wijze van het Programma
   * _nota van de Oplossing_: Het vroegere net van de Klant werd onmiddellijk bijgewerkt maar nadat het net van de moeilijke Klant wordt bijgewerkt nadat de bouwlooppas maar niet onmiddellijk weerspiegelt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-6754_: typefout op een JS- dossier.
   * _nota van de Reparatie_: Het systeem gebruikt nu correct de term &quot;abonnees&quot;in het dossier van JavaScript, die juiste functionaliteit van de verwante eigenschappen verzekeren. Eerder leidde een typografische fout in het JavaScript-bestand tot een onjuist gebruik van de term &quot;abonnees&quot;.
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
* _AC-9712_: Verschil in minder compilatie tussen php &amp; nodejs bibliotheek (grot) met gecompliceerde `calc` uitdrukkingen
   * _nota van de Reparatie_: Recht het verschil in minder compilatie tussen php &amp; nodejs bibliotheek (grot) na update wikimedia/less.php:^5.x
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37841>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b34c0a75>
* _ACP2E-2692_: De fout &quot;van de lijst van de Basis of de mening niet gevonden&quot;komt voor wanneer het gedeeltelijke indexeren wordt uitgevoerd
   * _Nota van de Reparatie_: De gedeeltelijke herdex werkt nu correct met grote verandering in geval van secundaire db verbinding
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2844_: De kwesties na bevordering MariaDB aan 10.5.1 of hoger
   * _Bevestig nota_: Vaste de kwestie toen datetime waarden in een OB in 000-00-00 00 :00: 00 na verbetering Mysql zouden worden omgezet
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a12063bd>
* _ACP2E-2855_: Het type in Vergelijking van Gegevens wanneer het controleren als het gegeven veranderingen heeft
   * _nota van de Reparatie_: Eerder, werd het sparen voorwerp geroepen telkens zonder enige gegevensveranderingen (voor om het even welk numeriek gegevensgebied - zoals int/float/dubbel). Het activeert de markering _hasDataChanges om waar te zijn en roept de opslagfunctie aan. Nadat deze correctie is toegepast, wordt de functie Save alleen aangeroepen als de gegevens zijn gewijzigd. De gegevenswaarde voor int/float/double-check met de waarde die aan de functie wordt doorgegeven en strikte overeenkomende typen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2959_: [ de invoer van de Wolk ] kan niet met folder var worden gebruikt
   * _nota van de Reparatie_: Het product kan met succes ongeacht het dossier worden ingevoerd - naam.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-2966_: In iPad mini de menu en kopballadingen als mobiel, in plaats daarvan zouden zij als Desktop moeten laden.
   * _nota van de Reparatie_: Het systeem behandelt nu apparaten met een breedte van 768px als Desktop, die ervoor zorgen dat het menu en de kopbal correct laden. Eerder werden apparaten met een breedte van 768 px als mobiel beschouwd, waardoor het menu en de koptekst in een mobiele weergave werden geladen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>, <https://github.com/magento/magento2-page-builder/commit/4d5db10a>
* _ACP2E-3046_: De lijst van de basis of de mening niet gevonden fout wanneer het runnen van mview krun terwijl het hebben van een verrichting DDL
   * _nota van de Reparatie_: Het systeem behandelt nu correct de verrichtingen van de gegevensbestandupdate terwijl de meningsupdate op achtergrond loopt, verhinderend het voorkomen van &quot;de lijst van de Basis of mening niet gevonden&quot;fouten. Eerder, konden sommige verrichtingen van de gegevensbestandupdate in de fout van de &quot;Basis tabel of mening niet gevonden&quot;resulteren, als de meningsupdate tezelfdertijd liep.
* _ACP2E-3230_: Het wijzigen van kolomlengte via db_schema.xml werkt niet in het geval van buitenlandse sleutels
   * _nota van de Reparatie_: het wijzigen van kolom met buitenlandse sleutel via verklarend schema stijgt nu geen fouten met MariaDB
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3361_: Enkele verbindingsverslagen worden bewaard aan OB wanneer het orderverslag wordt bewaard
   * _nota van de Reparatie_: Vóór de moeilijke moeilijke onnodige vragen van de UPDATE werden teweeggebracht die een effect prestaties kunnen hebben wijze. Na de moeilijke situatie, werden de onnodige vragen van de UPDATE geëlimineerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3375_: [ CLOUD ] In admin zijn er vele fout javascript in console
   * _nota van de Reparatie_: Eerder, in admin paneel zijn er vele fout javascript in console. In het deelvenster Beheer zijn er geen JavaScript-fouten in de console en worden alle standaard JavaScript-functies zonder problemen uitgevoerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3387_: [ Cloud ] Magento: het rijbericht is geschrapt
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

### Kader, Product

* _AC-13011_: 2.4.8-beta1 EE Rapporten produceren niet toe te schrijven aan magento uitzondering

### Framework, UI Framework

* _ACP2E-3324_: Mogelijkheid om configuratiewaarde te beschrijven zelfs als het gesloten is
   * _nota van de Reparatie_: Eerder aan deze moeilijke situatie, kon de ontwerpconfiguratie niet door bak/magento config worden geplaatst:vastgestelde bevel en gesloten waarden konden door manipulatie van de vorm worden veranderd die hen toont. Nadat de fix vergrendelde waarden zijn ingesteld vanuit cli met —lock-env of —lock-conf, kunnen deze niet meer worden bijgewerkt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>

### GrafiekQL

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
   * _Fix-opmerking_: GraphQL met PageBuilder-inhoudsresponscache wordt nu ongeldig verklaard wanneer de PageBuilder-inhoudsgerelateerde entiteiten worden bijgewerkt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2653_: Gelaagde navetion uitschakelen - Verwijdert geen aggregatie uit Graphql
   * _nota van de Reparatie_: De kwestie is opgelost na het toepassen van de controle terwijl het verzoeken van een productonderzoek met categoriesamenvoegingen door een vraag van GraphQL wanneer admin configuratie die &quot;Catalogus > Gelaagde Navigatie > de Filter van de Categorie van de Vertoning&quot;plaatst.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2928_: GraphQL Products-aanroep met het prijsfilter {from:&quot;0&quot;} retourneert geen resultaat
   * _Fix note_: Voorheen zocht graphql producten met filter op nul prijzen leverde helemaal geen resultaten op vanwege een gegenereerd uitzondering. De zoekopdracht levert nu de verwachte resultaten op.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2974_: Vertalingen voor de attributen van de klantenterugkeer die niet in GraphQL API voor respectievelijke StoreView worden weerspiegeld
   * _nota van de Oplossing_: De vertalingen voor de attributen van de klantenterugkeer worden weerspiegeld in GraphQL API voor respectieve StoreView.
Eerder werden de teruggavekenmerken van de klant voor de respectievelijke StoreView niet weerspiegeld in de GraphQL API.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3128_: [ de Verbroken vraag van GraphQL van de Wolk ] voor getPurchaseOrder met knoopcitaat
   * _Bevestig nota_: De vraag van GraphQL van de Orde van de Aankoop zal de taak kunnen uitvoeren zonder enige interne serverfouten te ontmoeten.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/6f4805f8>
* _ACP2E-3184_: [ De Wolk ] Configureerbare Producten niet getoond in de Plaats van de Productie als het Product niet in &quot;Alle Mening van de Opslag&quot;wordt toegelaten
   * _nota van de Reparatie_: Het systeem toont nu correct configureerbare producten in de plaats zelfs als het product niet in &quot;Alle Kijken van de Opslag&quot;wordt toegelaten, maar in specifiek werkingsgebied van de opslagmening wordt toegelaten.
Als een product eerder was uitgeschakeld in &quot;Alle winkelweergaven&quot; en alleen was ingeschakeld in specifieke weergavebereiken van de winkel, zouden de productkenmerken niet correct worden weergegeven in de GraphQL-reactie, waardoor het product niet correct wordt weergegeven.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/3f300077>
* _ACP2E-3190_: [ de Grafiek van de Producten van de Wolk ] die fout hebben wanneer het zelfde eenvoudige product aan veelvoudige configureerbare producten heeft toegewezen
   * _nota van de Reparatie_: Eerder, met afzonderlijke configureerbare producten met het zelfde eenvoudige product, keert grapQL een fout terug. Nadat deze oplossing is toegepast, zijn verschillende configureerbare producten met hetzelfde eenvoudige product van toepassing, grapQL retourneert het resultaat zonder fouten.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/148c3ead>
* _ACP2E-3215_: [Cloudprobleem] met gebruikersverificatie en toegang tot cross-site tokens in multi-site setup
   * _Fix-opmerking_: GraphQl Customer Info en Cart queries in Multi-Site setup controleert of de klant op een niet-standaard website bestaat.
Voorheen werkte de query zonder ervoor te zorgen dat de klant zich op een niet-standaard website bevindt in de opstelling van Multi-Site.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3253_: GraphQL cart itemsV2 paginering werkt niet correct
   * _Fix-opmerking_: het probleem is opgelost door de juiste waarde voor het huidige pagina-argument door te geven in de verzamelingsquery. Voorheen werd de verkeerde waarde doorgegeven om de huidige pagina in te stellen, wat het probleem veroorzaakte.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/8459b17d>
* _ACP2E-3255_: [GRAPHQL-modelwaarde] moet worden gespecificeerd bij het ophalen van customerCart
   * _Fix-opmerking_: De GraphQL &#39;customerCart&#39;-query kan nu een lege winkelwagen maken, zelfs als de offerte niet beschikbaar is in de database. Voorheen mislukte deze bewerking vanwege problemen met de landvalidatie tijdens het maken van de lege winkelwagen.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [GraphQl] Wishlist-items zijn zichtbaar via GraphQl, maar niet zichtbaar op de etalage
   * _Let op_: Producten op de verlanglijst werden niet correct vermeld wanneer dit werd aangevraagd via GraphQL. Nu worden verlanglijstproducten gefilterd op basis van de opgegeven winkelcontext.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [GraphQL] Wachtwoord opnieuw instellen e-mail inconsistentie tussen inhoud en onderwerp/link
   * _Fix-opmerking_: Het probleem is opgelost door de juiste winkel te simuleren waar het account van de klant is geregistreerd bij het verzenden van het verzoek om het wachtwoord opnieuw in te stellen, ongeacht de websitewinkel.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: [Cloud] products GraphQL query retourneert gerelateerde producten die niet zijn toegewezen aan de huidige website
   * _nota van de Reparatie_: Eerder, voor de vraag graphQL, multi-store verwante producten tonen niet behoorlijk voor productvraag. Nadat deze moeilijke situatie wordt toegepast, voor producten, vraag graphQL verwante producten die dienovereenkomstig worden getoond multi-store.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: Het gebruiken van onjuiste identiteitskaart van de Opslag in de kopbal van GraphQL veroorzaakt fatale geheugenfout
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
   * _Fix-opmerking_: de &quot;placeOrder&quot;-mutatie met couponcode-informatie in het verzoek genereert niet langer een interne foutuitzondering, de bestelling is succesvol geplaatst. Eerder is dit mislukt met &quot;Interne serverfout&quot;.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/982b1c42>
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
* _LYNX-510_: Fout bij het opvragen van selected_options in OrderAddress
   * _Fix-opmerking_: AttributeSelectedOptions is bijgewerkt naar custom_attributesV2 in het orderadres GraphQL-antwoord.
* _LYNX-512_: original_item_price is exclusief kortingen
   * _Fix-opmerking_: original_item_price bijgewerkt met kortingen.
* _LYNX-530_: Het niet beschikbare bericht toont niet de beschikbare inventarishoeveelheid
   * _nota van de Reparatie_: Los het foutenmelding en de foutencode voor de mutatie AddProductsToCart op om met de &quot;niet beschikbare&quot;berichtconfiguratie te richten
* _LYNX-532_: de status &quot;OUT_OF_STOCK&quot; keert terug op Eenvoudig met aangepaste opties Producten met meerdere opties
   * _nota van de Reparatie_: Bijgewerkt StockStatusProvider resolver in het inventarispakket om stock_status voor eenvoudige producten met douaneopties te bevestigen.
* _LYNX-533_: Fout (GQL): cart.itemsV2.items.product.custom_attributesV2 keert een serverfout terug
   * _nota van de Reparatie_: Los de serverfout op die voorkwam wanneer een kartvraag de douaneattributen van een product door een product zonder enige douanekenmerken toe te voegen omvatte.
* _LYNX-536_: bestellingen/date_of_first_order altijd retournerend null
   * _Bevestig nota_: Los de kwestie op waar de orden > date_of_first_order altijd ongeldig terugkwamen.
* _LYNX-544_: De klant moet niet een gedeeltelijk verscheepte orde kunnen annuleren
   * _nota van de Reparatie_: De bevestiging is toegevoegd om klanten te beperken van het annuleren van een gedeeltelijk verscheepte orde.
* _LYNX-548_: De codes van de fout voor orde annuleren die op het foutenbericht wordt gebaseerd
   * _de nota van de Reparatie_: De foutencodes voor ordevernietiging zijn nu gebaseerd op het specifieke foutenbericht.
* _LYNX-581_: Beweeg terug koekjesgerelateerde eigenschappen van privé aan beschermde
   * _Nota van de Reparatie_: Keert de eigenschappen van de Magento\Framework\App\PageCache\Version klassenaannemer van privé aan beschermde
* _LYNX-600_: De maximum standaardGraphQL vraagingewikkeldheid van de verhoging aan 1000
   * _nota van de Reparatie_: Verhoogde standaard maximumingewikkeldheid van de vraag van GraphQL van 300 tot 1000.
* _LYNX-620_: GQL - itemsV2 > Origineel rijtotaal, de prijzen van de prijswaaier zijn teruggekeerd als $0.00 voor downloadbaar product met dossieropties die afzonderlijke prijzen hebben.
   * _nota van de Reparatie_: Los een kwestie op waar de downloadbare producten met afzonderlijke toegelaten verbindingsaankoopopties $0 voor itemsV2 > Oorspronkelijk rijtotaal teruggaven, als $0.00 voor producten met dossieropties die afzonderlijke prijzen hebben teruggekeerd.
* _LYNX-711_: Schema van een tabel wanneer deze gloednieuw wordt gemaakt, anders dan bij het upgraden
   * _nota van de Reparatie_: Los een kwestie op waar het toevoegen van een nieuwe kolom VARCHAR aan een bestaande lijst testmislukkingen wegens schemaverschillen tussen verse installaties en verbeteringen veroorzaakte. De methode modifyColumn() verwerkt VARCHAR-kolommen nu op de juiste manier door de standaardtekenset en sortering in te stellen.
* _LYNX-772_: GraphQl compatibiliteit voor PHP-8.4 versie
   * _Opgeloste opmerking_: Opgeloste GraphQL-compatibiliteitsproblemen met PHP 8.4 over meerdere resolvers, wat zorgt voor een soepele functionaliteit. Getroffen bestanden zijn bijgewerkt in de modules CatalogRule, Customer, GiftMessage, GiftCard en GiftWrapping.

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

* _ACP2E-2809_: GraphQL productlijst sorteren op meerdere parameters werkt niet
   * _Fix-opmerking_: het sorteren van producten op meerdere velden in GraphQl werkt nu zoals beschreven in de documentatie
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-948_: De lijst van het product GraphQL vraag beperkt tot total_count 10.000 slechts producten
   * _nota van de Reparatie_: Na de moeilijke situatie, is het onderzoeksresultaat niet beperkt tot 10000 producten, wordt het mogelijk om alle producten te krijgen die aan de onderzoekscriteria voldoen zelfs als de telling meer dan 10000 is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, testkader

* _ACP2E-3363_: Magento\GraphQl\App\GraphQlCustomerMutationsTest.php de mislukking van de Test van de Integratie
   * _Bevestig nota_: &quot;-
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importeren/exporteren

* _AC-12172_: Uitgave bij productinvoer wanneer voorzien van douane opties-type: dossier (het Gemaakt Product bevat geen prijs voor douane-optie en toont slechts de eerste verstrekte uitbreiding van het dossiertype)
   * _Fix-opmerking_: het systeem importeert nu correct productgegevens met aangepaste opties van het type &#39;bestand&#39;, zodat alle meegeleverde bestandsextensies worden weergegeven en de prijs voor de aangepaste optie is inbegrepen. Eerder werd tijdens het importeren van producten alleen de eerste extensie weergegeven en ontbrak de prijs voor de aangepaste optie als een aangepaste optie van het type &#39;file&#39; was voorzien van meerdere bestandsextensies.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38805>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38926>
* _ACP2E-2710_: Onjuiste uitvoeringstijd voor de invoerverrichting in het net van de Geschiedenis van de Invoer
   * _Fix-opmerking_: de uitvoeringstijd van het importrapport wordt correct weergegeven, onafhankelijk van de landinstelling van de beheerder.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-2737_: Dubbele klanten worden aangemaakt met hetzelfde e-mailadres met behulp van importeren
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
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: Het uitgevoerde klantenadres kan niet worden ingevoerd
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
* _ACP2E-2102_: Geen Export VCL voor Varnish 7 knop in admin paneel
   * _Fix note_: de knop &quot;Export VCL for Varnish 7&quot; is toegevoegd aan het beheerderspaneel.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4fbf702>

### Inventaris/MSI

* _AC-10750_: De update van de inventaris van het Configurable Product ontbreekt wanneer het gegevensbestand prefixen gebruikt
   * _nota van de Reparatie_: Het systeem werkt nu correct de inventaris van configureerbare producten bij wanneer het gegevensbestand prefixen gebruikt, die om het even welke foutenmeldingen verhinderen en ervoor zorgen dat het correcte aantal wordt bewaard. Eerder, zou een fout voorkomen wanneer het proberen om de inventarishoeveelheid voor eenvoudige producten binnen een configureerbaar product te bewaren als het gegevensbestand prefixen gebruikte.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38045>
* _AC-11593_: De sleutel van Google google API werkt niet terwijl het toevoegen van Kaart met attributen
   * _Fix-opmerking_: het systeem ondersteunt nu de nieuwste Google Maps API-versie 3.56, waardoor gebruikers met succes een kaartinhoudsblok vanuit het PageBuilder-menu aan het werkgebied kunnen toevoegen zonder fouten tegen te komen. Voorheen konden gebruikers geen Map-inhoudsblok toevoegen vanwege compatibiliteitsproblemen met de Google Maps API-versie, wat resulteerde in een foutmelding &#39;er is iets misgegaan&#39;.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/0574ac23>
* _AC-13922_: Kan geen verzending maken voor een orderitem met meerdere bronnen en een beschadigde SKU
   * _Fix-opmerking_: Eerder, wanneer spaties per ongeluk werden toegevoegd in sku via de database, leidde dit tot een fout in de verzendpagina die nu is opgelost en automatisch bijsnijden wordt beschouwd als een mensvriendelijke fout en er is geen impact gevonden. Daarom is de verzending met succes gemaakt.
   * _Bijdrage GitHub-code_: <https://github.com/magento/inventory/commit/c18eb5fa>
* _ACP2E-1411_: [ de producten van de Bundel van de Test ] met 0 voorraad die op opslagvoorzijde tonen
   * _nota van de Reparatie_: Het bundelproduct toont niet op de extra websites gebruikend extra voorraad.
* _ACP2E-2794_: [Cloudkritiek] probleem met productvermelding met lege ruimtes
   * _nota van de Reparatie_: Het systeem toont nu correct productlijsten zonder lege ruimten wanneer de producten aan &quot;uit voorraad&quot;worden geplaatst, die een verenigbare en nauwkeurige vertoning van beschikbare producten verzekeren. Als je een product voorheen instelde op &#39;Niet op voorraad&#39;, verscheen er een lege ruimte in de productvermelding, wat de lay-out verstoorde en klanten mogelijk in verwarring bracht.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ea79f7dd>, <https://github.com/magento/inventory/commit/b59e48ca>
* _ACP2E-3335_: Onbekwaam om de orde te verschepen wanneer MSI ophaalopslag wordt toegelaten
   * _Nota van de Reparatie_: Verbeterde inventarisprestaties van creeer het verschepen in het geval van vele bronnen met in-store bestelwagen
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: De Cron herdex ontbreekt om productbeschikbaarheid op frontend bij te werken
   * _nota van de Reparatie_: Eerder, bleven de Producten uit voorraad op het front na het bijwerken van de backorderstatus door REST API. Nadat u de status van de backorder hebt bijgewerkt via de REST API, worden de producten weergegeven als in voorraad.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: Het toevoegen van beelden aan configureerbaar niet werkend wanneer MSI wordt toegelaten.
   * _nota van de Reparatie_: Het beeld uploadt voor configureerbaar product zal nu zoals verwacht werken wanneer de inventarismodule wordt gebruikt. Eerder werkte het uploaden van de afbeelding niet
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/fdf409aa>
* _ACP2E-3470_: Uitgave met Bundel Product + MSI in Schone M2.4.7-p3
   * _nota van de Reparatie_: Eerder, voor de producten van de inventarisbundel na duplicatie met het zelfde eenvoudige product, kan het eenvoudige product niet worden bewaard. Nadat deze correctie is toegepast, kan het eenvoudige product zonder uitzonderingen worden opgeslagen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39358>
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/0208e433>

### Inventaris/MSI, zoeken

* _ACP2E-3413_: Alle producten worden geïndexeerd met [ is_out_of_stock ] = 1 wanneer SKU niet als onderzoekbaar attribuut wordt geplaatst
   * _nota van de Reparatie_: Na de moeilijke situatie, is &quot;is_out_of_stock&quot;in de index van het catalogusonderzoek correct, zelfs wanneer de huid niet doorzoekbaar is.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/5b21b7af>

### Volgorde

* _wisselstroom-10828_: Het scherm van het het overzicht van de orde van de achtergrond: Achtergeordende hoeveelheid niet zichtbaar op het niveau van het orde punt
   * _nota van de Reparatie_: Het systeem toont nu het aantal backordered punten in de kwantitatieve kolom op het scherm van het overzicht van de achterste orde. Dit zorgt ervoor dat de gebruikers de status van alle punten in een orde nauwkeurig kunnen volgen. Eerder gaf de kolom Aantal alleen het aantal objecten weer dat was besteld, gefactureerd en verzonden, maar niet het aantal objecten met een backorder.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38252>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38320>
* _wisselstroom-10994_: [ Verkeerde de opslagidentiteitskaart van de Uitgave ] die in Renderer van het Adres van de Orde wordt gebruikt
   * _nota van de Reparatie_: Het systeem gebruikt nu correct opslagidentiteitskaart verbonden aan een orde wanneer het teruggeven van het ordeadres, die ervoor zorgen dat de adressen correct volgens hun respectieve opslagidentiteitskaart worden geformatteerd. Eerder gebruikte het systeem onjuist de huidige winkel-id, wat tot een onjuiste adresnotatie kan leiden wanneer meerdere bestelling-e-mails van verschillende winkels moeten worden verzonden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38412>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37932>
* _AC-11690_: JoinProcessor caching kwestie
   * _nota van de Reparatie_: Het systeem past nu correct JoinProcessor voor elke herhaling, zelfs met opeenvolgende vraag toe, die nauwkeurige gegevensherwinning verzekeren. Eerder werd de JoinProcessor onjuist gemarkeerd, zoals al werd toegepast in opeenvolgende herhalingen, wat leidde tot fouten in het ophalen van gegevens.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/27504>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37550>
* _AC-11798_: [ de Verzendprijs van de kwestie ] die verschillend in gedrukt pdf toont
   * _nota van de Reparatie_: Het systeem toont nu correct de verschepende prijzen in gedrukte PDFs volgens de montages van de belastingconfiguratie, die consistentie tussen de de meningspagina van de verkooporde van de factuur en de gedrukte factuur verzekeren. Eerder was de verzendprijs die in de afgedrukte PDF werd weergegeven exclusief belasting, ongeacht de instellingen voor de belastingconfiguratie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38608>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38595>, <https://github.com/magento/magento2/commit/1bafc571>
* _wisselstroom-13839_: Opnieuw orde met een geschrapt ouder configureerbaar product
   * _Fix-opmerking_: tijdens het opnieuw bestellen met het verwijderde product toont het systeem nu niet de knop voor opnieuw bestellen om opnieuw te bestellen
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39568>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/39601>
* _AC-13924_: [Issue] Fix bad \Magento\Sales\Model\Order\Email\Container\Template::$id eigenschap
   * _Fix note_: Dit repareert de slechte phpdoc voor \Magento\Sales\Model\Order\Email\Container\Template::$id, eigenlijk is $id type int maar in werkelijkheid is het string.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39151>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39150>
* _ACP2E-2622_: Onbekwaam om veranderingen in telefoonaantal in bestaande ordedetails te bewaren
   * _nota van de Reparatie_: Nu kan de gebruiker internationale prefix 00 op het telefoongebied van ordeadres toevoegen
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38201>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/12e071c3>
* _ACP2E-2734_: De e-mail ontbreekt om te verzenden
   * _nota van de Reparatie_: Het systeem omvat nu een configuratieoptie async_sending_probeerde om het aantal pogingen te specificeren om een e-mail te verzenden alvorens te stoppen, verbeterend de behandeling van ontbroken e-mail verzendt wanneer &quot;Asynchroon verzenden&quot;wordt toegelaten. Als het verzenden van een e-mail mislukt, probeert het systeem het bericht voortdurend opnieuw te verzenden, wat resulteert in een eindeloze lus met foutberichten in het systeemlogboek.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2756_: [] Cloud Order Status gewijzigd in voltooid bij gedeeltelijke terugbetaling van een gedeeltelijk verzonden bestelling
   * _Fix-opmerking_: bij het uitgeven van een creditnota wordt de bestelstatus niet langer gewijzigd in &quot;voltooid&quot; als er artikelen zijn die nog niet zijn verzonden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7e0e5582>
* _ACP2E-3002_: [ CLOUD ] kan verzenden geen E-mail van Admin UI onbruikbaar maken aangezien Dev Docs toont
   * _Fix-opmerking_: het systeem voorkomt nu correct dat verkoop-e-mails worden verzonden wanneer e-mailcommunicatie is uitgeschakeld. Deze e-mailberichten worden niet meer verzonden wanneer de e-mailcommunicatie opnieuw wordt ingeschakeld. Voorheen werden verkoop-e-mails die werden geïnitieerd terwijl e-mailcommunicatie was uitgeschakeld, nog steeds verzonden zodra e-mailcommunicatie opnieuw was ingeschakeld.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/c8931218>
* _ACP2E-3045_: Bestelling gesloten zonder volledige terugbetaling
   * _Fix-opmerking_: het systeem handhaaft nu correct de orderstatus als &#39;Verwerken&#39; en de factuurstatus als &#39;In behandeling&#39; wanneer een bestelling met een niet-gevangen betaling een zending heeft gemaakt. Dit zorgt ervoor dat bestellingen pas als &#39;Gesloten&#39; worden gemarkeerd nadat ze volledig zijn terugbetaald. Voorheen werd bij het maken van een zending voor een bestelling met een factuur in behandeling de orderstatus ten onrechte gewijzigd in &#39;Gesloten&#39;.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/6a185204>
* _ACP2E-3311_: [Cloud] kan geen bestelling maken in de beheerder van één winkel als alleen het standaard factuuradres niet is ingesteld
   * _Fix-opmerking_: nu relevante foutmelding &quot;Een klant met hetzelfde e-mailadres bestaat al op een gekoppelde website.&quot; wordt getoond als een klant geen Standaard het Factureren Adres heeft en probeert om een orde op een andere opslag tot stand te brengen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Admin gedupliceerde verzonden verzoeken van de plaatsorde
   * _nota van de Reparatie_: Eerder, kon de &quot;Submit knoop van de Orde&quot;in het admin paneel veelvoudige tijden worden geklikt of door herhaaldelijk te drukken &quot;binnengaan&quot;sleutel, veroorzakend dubbel of ordebijdragen met fout. Nu, verhinderend extra acties tot de orde volledig wordt verwerkt, die ervoor zorgen dat slechts één orde wordt voorgelegd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: Admin kan orde zelfs zonder betalingsmethode nog plaatsen
   * _nota van de Reparatie_: Eerder geselecteerde betalingsmethode wordt nu behouden wanneer de betalingsmethode in de lijst van beschikbare betalingen opnieuw verschijnt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3518_: De punten worden gedupliceerd nadat wij een orde van Admin op - browser Mozilla Firefox creëren
   * _nota van de Reparatie_: De producten die worden toegevoegd gebruikend &quot;voeg Producten door SKU&quot;toe worden niet meer gedupliceerd in Firefox wanneer het creëren van een orde in admin.

### Bestelling, betalingen

* _ACP2E-3233_: Admin kan nog steeds een bestelling plaatsen, zelfs zonder betaalmethode
   * _Fix-opmerking_: voorheen kon de handelaar bestellingen plaatsen vanuit het beheerderspaneel zonder een betaalmethode te selecteren. Nu heeft de handelaar een betaalmethode nodig om door te gaan met het plaatsen van een bestelling.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Bestellen, Retourneren

* _ACP2E-2982_: Terugbetaling van bestelling resulteert in dubbele creditnota
   * _Fix-opmerking_: Als u de terugbetaling uitvoert via de REST API wanneer twee identieke aanvragen tegelijkertijd zijn uitgevoerd, worden er geen dubbele creditnota&#39;s meer gemaakt.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/a4fbf702>

### Bestelling, Belasting

* _ACP2E-3003_: [CLOUD] Onjuiste base_row_total in de RESTFUL-order-API bij het inschakelen van grensoverschrijdende transacties en het toepassen van couponkortingen
   * _Opmerking_ oplossen: de juiste base_row_total wordt nu geretourneerd vanuit de RESTFUL-order-API wanneer grensoverschrijdende transacties zijn ingeschakeld en couponkorting wordt toegepast.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/9af794a4>

### Ander

* _BUNDEL-3394_: [Braintree] Refund online opslagtransactie als transactionid-refund
* _BUNDEL-3421_: [Braintree] + [CLOUD] Braintree (creditcard) bestellingen kunnen de kosten niet splitsen
* _BUNDEL-3422_: [Braintree] [Cloud]Braintree SSL-certificaat verloopt op 30 juni
* _LYNX-339_: private_content_version cookie geretourneerd in GQL-query&#39;s
   * _Opmerking oplossen_: Er is een probleem opgelost waarbij de private_content_version-cookie werd geretourneerd in GraphQL-query&#39;s, zelfs als de sessiecookie was uitgeschakeld. De cookie wordt niet langer opgenomen in de antwoorden van GraphQL wanneer de sessie is uitgeschakeld, zoals verwacht.
* _LYNX-366_: Serverfout op e-mailrekwisieten in fysieke cadeaubonquery&#39;s
   * _Opgeloste opmerking_: er is een probleem opgelost waarbij query&#39;s voor sender_email en recipient_email op fysieke cadeaubonnen resulteerden in een serverfout. Deze rekwisieten worden nu correct geretourneerd voor virtuele cadeaubonnen en het zoekgedrag is consistent.
* _LYNX-380_: is_available attribuut in CartItemInterface retourneert altijd false voor configureerbare producten
   * _Opgeloste opmerking_: Er is een probleem opgelost waarbij het is_available-kenmerk in CartItemInterface altijd onwaar retourneerde voor configureerbare producten die op voorraad waren. Nu wordt beschikbaarheid correct weergegeven als waar, indien van toepassing.
* _LYNX-382_: is_available attribuut in CartItemInterface retourneert waar, zelfs wanneer de verkoopbare voorraad lager is dan de hoeveelheid van het product
   * _Fix-opmerking: Opgeloste het_ probleem waarbij het is_available-attribuut in de CartItemInterface ten onrechte true retourneerde, zelfs wanneer de hoeveelheid winkelwagenartikelen de verkoopbare voorraad overschreed.
* _LYNX-395_: only_x_left_in_stock kenmerk in ProductInterface is niet nauwkeurig voor configureerbare producten
   * _Opmerking_ opgelost: Er is een probleem opgelost waarbij het kenmerk only_x_left_in_stock in ProductInterface niet nauwkeurig de beschikbare voorraad weerspiegelde voor configureerbare productvarianten in de winkelwagen. Nu komt de only_x_left_in_stock waarde correct overeen met de werkelijke voorraadniveaus van de variant, zodat nauwkeurige voorraadgegevens worden geretourneerd in de Cart GQL-query.
* _LYNX-399_: Tijdelijke aanduiding voor de miniatuur keert terug wanneer een eenvoudig product wordt toegevoegd aan het winkelwagentje binnen een gegroepeerd product
   * _Opgeloste opmerking_: Er is een probleem opgelost waarbij het toevoegen van een eenvoudig product (onderdeel van een gegroepeerd product) aan de winkelwagen een tijdelijke miniatuurafbeelding opleverde, zelfs als aan het product een toegewezen afbeelding was toegewezen.
Details oplossen:
• De productminiatuur geeft nu de toegewezen afbeelding correct weer, indien beschikbaar.
• De thumbnail selectie respecteert de admin configuratie onder:
Winkels > configuratie > verkoop > afrekenen > winkelwagentje > gegroepeerde productafbeelding.
Dit zorgt voor consistent miniaturengedrag voor gegroepeerde producten op basis van winkelinstellingen.
* _LYNX-400_: Aangepaste optiekenmerken van de klant werken niet met gehele getallen
   * _Bevestig nota_: Vaste een kwestie waar de attributen van de douaneoptie van de klant niet werkten wanneer de teruggekeerde waarde een geheel was. De aangepaste opties verwerken nu correct de waarden van gehele getallen en retourneren deze zoals verwacht.
* _LYNX-402_: Interne serverfout wanneer het proberen om priceDetails voor de producten van de Bundel met dynamische prijs te krijgen
   * _Bevestig nota_: Los een kwestie op waar het vragen van price_details voor bundelproducten met dynamische tarifering via GraphQL in een interne serverfout resulteerde. Deze verbetering verzekert stabiele wortelvragen wanneer het werken met bundelproducten die met dynamische tarifering worden gevormd.
* _LYNX-403_: only_x_left_in_stock keert altijd 0 voor configureerbare producten terug
   * _nota van de Reparatie_: Los een kwestie op waar het only_x_left_in_stock attribuut altijd 0 voor configureerbare producten terugkeerde wanneer toegevoegd gebruikend ouderSKU met opties.
Details herstellen:
・ De waarde only_x_left_in_stock geeft nu nauwkeurig de voorraad van de geselecteerde kindvariant in plaats van bovenliggende SKU weer.
• Dit zorgt ervoor dat voorraadniveaus correct worden weergegeven voor configureerbare productvariaties in de winkelwagen en productpagina&#39;s.
* _LYNX-405_: GraphQL-fout: niet-ondersteund &#39;bestand&#39;-type in query voor aanpasbare opties
   * _Opmerking opgelost_: Er is een probleem opgelost waarbij GraphQL een fout retourneerde voor aanpasbare opties van het type &quot;bestand&quot; in winkelwagenitems. De query retourneert nu correct details voor alle aanpasbare optietypen, inclusief opties op basis van bestanden, zonder fouten te veroorzaken.
* _LYNX-411_: GraphQL-query retourneert niet de juiste berekende normale prijs voor aanpasbare producten
   * _Opgeloste opmerking_: Er is een probleem opgelost waarbij GraphQL niet de juiste berekende normale prijs retourneerde voor aanpasbare producten. De query bevat nu correct de berekende normale prijs met aanpasbare waarden die zijn toegepast (bijvoorbeeld $ 125) in de eigenschap prijzen, die zowel de basisprijs als eventuele extra aanpassingskosten weerspiegelen.
* _LYNX-412_: AppliedTaxes via EstimatedTotals blijven met bijgewerkte mutaties
   * _Bevestig nota_: Vaste een kwestie met de Mutatie EstimatedTotals waar de toegepaste belastingen op een kar zelfs na het bijwerken van het gebied of postcode voortvloeiden. De mutatie werkt nu correct de toegepaste belastingen bij wanneer het veranderen tussen regio en postcode waarden, die ervoor zorgen dat slechts de correcte belastingregel op de huidige kartgegevens wordt toegepast.
* _LYNX-420_: is_available attributen in CartItemInterface keert waar terug zelfs wanneer de verkoopbare voorraad lager is dan de hoeveelheid van het product
   * _nota van de Reparatie_: Vaste een kwestie waar is_available attribuut in CartItemInterface verkeerd waar terugkeerde zelfs wanneer de verkoopbare voorraad lager was dan de gevraagde producthoeveelheid. Het veld is_available retourneert nu correct false wanneer de hoeveelheid van het product groter is dan de beschikbare voorraad.
* _LYNX-421_: Kan coupon aan wagentje voor het verschepen slechts korting toevoegen
   * _Bevestig nota_: Oplossing een kwestie waar een coupon niet op een kar voor verschepende-slechts kortingen kon worden toegepast. De coupon wordt nu correct toegepast op het verzendbedrag wanneer een verkoopregel zonder productvoorwaarden wordt gebruikt, zodat de verwachte korting op de verzendkosten wordt toegepast.
* _LYNX-425_: De regelmatige prijs van het product met 12 decimalen en verkeerde waarde
   * _Bevestiging nota_: Vaste een kwestie waar de regelmatige_prijswaarde in product.price_range.maximum_price en minimum_price de wegen van GraphQL niet de catalogusprijs overeenkwamen toen de veelvoudige belastingtarieven werden toegepast. Reguliere_price weerspiegelt nu consistent de catalogusprijs over alle belastingconfiguraties, die nauwkeurige eenheidsprijzen, totale rijkostenberekeningen, en kortingscontroles in de Samenvatting van de Objecten verzekeren verzekeren.
* _LYNX-430_: De serverfout van GraphQL op karretje met uit voorraad gebundeld product
   * _Opmerking opgelost_: Er is een probleem opgelost waarbij GraphQL een interne serverfout retourneerde bij het ophalen van een winkelwagentje met een gebundeld product met een artikel dat niet op voorraad was, met name wanneer de query de eigenschap itemsV2 bevatte. GraphQL retourneert nu correct een lijst met artikelen met relevante foutmeldingen die zijn gekoppeld aan de gebundelde productartikelinvoer, zoals verwacht.
* _LYNX-441_: Het is niet mogelijk om een adres aan te maken met aangepaste attributen
   * _Fix-opmerking_: er is een probleem opgelost met de createCustomerAddress-mutatie waardoor er geen adressen met de vereiste aangepaste kenmerken konden worden gemaakt. De mutatie behandelt nu correct de attributen van het douaneadres wanneer de aangewezen lading wordt verstrekt.
* _LYNX-447_: GraphQL-serverfout op winkelwagen met only_x_left_in_stock op gebundeld product
   * _Opgeloste opmerking_: Er is een probleem opgelost waarbij het ophalen van een winkelwagentje met een gebundeld product met het veld only_x_left_in_stock in de GraphQL-query resulteerde in een interne serverfout. GraphQL retourneert nu correct een float of null voor het veld only_x_left_in_stock zonder fouten.
* _LYNX-464_: GraphQL-fout bij het verwijderen van andere producten met onvoldoende configureerbaar product in de winkelwagen
   * _Opgeloste opmerking_: Er is een probleem opgelost waarbij pogingen om producten die op voorraad zijn uit de winkelwagen te verwijderen, resulteerden in een GraphQL-fout &#39;De gevraagde hoeveelheid is niet beschikbaar&#39; als de winkelwagen ook configureerbare producten bevatte met onvoldoende voorraad. De verwijdering werkt nu zoals verwacht zonder fouten te activeren.
* _LYNX-469_: Kan producten toe te voegen toe te schrijven aan SKU in mutatie die gevoelig geval is
   * _Opmerking oplossen_: Er is een probleem opgelost waarbij de addProductsToCart-mutatie een &#39;PRODUCT_NOT_FOUND&#39;-fout retourneerde bij het gebruik van SKU&#39;s met een ander hoofdlettergebruik. De mutatie verwerkt SKU&#39;s nu niet-hoofdlettergevoelig, waardoor consistentie met Catalog Service-query&#39;s en PDP-gedrag wordt gegarandeerd.
* _LYNX-603_: Productkenmerk > verkorte handelsmerk ™ wordt geretourneerd als ™
   * _Fix-opmerking_: probleem met tekencodering met de productnaam voor de GraphQL API opgelost
* _LYNX-619_: updateCustomerEmail mutatie probleem
   * _Opmerking oplossen_: Er is een probleem opgelost met de updateCustomerEmail-mutatie waarbij klanten zonder de vereiste aangepaste kenmerken (toegevoegd na het maken van het account) hun e-mailadres niet konden bijwerken.
* _LYNX-626_: Mutatie setShippingAddressesOnCart genereert fout bij het gebruik van pickup_location_code
   * _Bevestig nota_: Vaste een kwestie waar de mutatie setShippingAddressOnCart een fout terugkeerde toen het gebruiken van pickup_location_code zonder customer_address_id of adres te specificeren. De mutatie staat nu correct het plaatsen van een verschepend adres met enkel pickup_location_code toe.
* _LYNX-627_: De lijst van CustomerOrder.items_Eli_for_return moet met orde punten verenigbaar zijn
   * _Bevestig nota_: Opgeloste inconsistenties met terugkeergeschiktheid in orden:
1. De lijst CustomerOrder.items_in aanmerking komend_for_return is nu consistent met de werkelijke orderitems.
2. Het veld OrderItemInterface.in_for_return retourneert correct false wanneer de volledige hoeveelheid al is geretourneerd.
3. CustomerOrder.items_in aanmerking komend_for_return bevat nu alleen items die nog niet worden geretourneerd.
* _LYNX-628_: voeg hoeveelheid_return_requested gebied toe
   * _nota van de Reparatie_: Voegt het kwantiteit_return_requested gebied aan OrderItemInterface toe, toestaand u om de hoeveelheid punten te identificeren waarvoor een terugkeer is voorgelegd. Hierdoor wordt het bijhouden van de geretourneerde waarde verbeterd naast het bestaande veld quantity_returned.
* _LYNX-634_: De orde beschikbare acties moet geen Terugkeer na terugkeer bevatten die voor alle punten in volledige hoeveelheid wordt gecreeerd
   * _nota van de Reparatie_: Vaste een kwestie waar het beschikbare_actieveld in de GraphQL customer.orders vraag verkeerd inbegrepen RETURN nadat een volledige terugkeer voor alle punten werd gecreeerd. De actie RETURN wordt nu correct verwijderd als het retourproces is voltooid.
* _LYNX-637_: De Verenigbaarheid van de Storefront - logica van de Update om lijstnaam met prefix en andere minder belangrijke verbeteringen te krijgen
   * _Bevestig nota_: Bijgewerkte logica om de lijstnaam met de prefix terug te winnen (met betrekking tot veranderingen SCP).
* _LYNX-643_: opslaan in adresboek werkt niet bij gebruik van het veld same_as_shipping van setBillingAddressOnCart GQL
   * _Bevestig nota_: Vaste een kwestie waar het verschepende adres niet aan het het adresboek van de klant werd bewaard toen het gebruiken van de GraphQL setBillingAddressOnCart met same_as_Shipping gebied dat aan waar wordt geplaatst. Het verzendadres is nu correct opgeslagen zoals u had verwacht.
* _LYNX-650_: normaliseer order_id in mutaties
   * _Bevestig nota_: Gestandaardiseerd de orde_id input in mutaties en bijgewerkt de orde annuleert bevestigingsemailmalplaatje om verhogingsidentiteitskaart in plaats van orde identiteitskaart bloot te stellen.
* _LYNX-651_: CustomerOrder toont niet de ordecommentaren
   * _nota van de Oplossing_: Los een kwestie met CustomerOrder op om ordercommentaren in gast en klantenorde GraphQL vragen te omvatten.
* _LYNX-652_: original_item_price moet geen korting omvatten
   * _Bevestig nota_: Bijgewerkt de logica voor original_item_price in de prijzen van het Punt van de Kaart van GraphQL om kortingen uit te sluiten.
* _LYNX-681_: De producten van de bundel tonen nog &quot;IN_STOCK&quot;wanneer één van zijn gebundeld product uit voorraad
   * _nota van de Reparatie_: Los een kwestie op waar product.stock_status voor bundelproducten nog &quot;IN_STOCK&quot;toonde zelfs wanneer één van de gebundelde punten uit voorraad was.
* _LYNX-686_: de klantenvraag keert Interne Fout van de Server terug als de waarde voor geschrapt douanekenmerk voor een klant bestaat
   * _nota van de Reparatie_: Vaste de kwestie waar de klantenvraag een interne serverfout terugkeerde toen een geschrapt douanekenmerk nog een opgeslagen waarde had. Er wordt nu een correct foutbericht geretourneerd als een niet-bestaand kenmerk wordt aangevraagd. De vereiste cache wordt ongeldig gemaakt wanneer het aangepaste attribuut van de klant wordt verwijderd.
* _LYNX-687_: De parameter van de actie voor terugkeer en annuleert bevestigingsverbindingen
   * _Bevestig nota_: De parameter van de actie die voor terugkeer wordt toegevoegd en annuleert bevestigingse-mail verwante verbindingen
* _LYNX-688_: De gebruiker van de gast bevestigingsurl wordt opnieuw gericht aan de pagina van de ordestatus aangezien het order orderRef (voor GuestRMA) mist
   * _Nota van de Reparatie_: Toegevoegde parameter orderRef aan de verbinding in de bevestigingsmail van gastRMA
* _LYNX-689_: De gebruiker van de gast bevestigingsurl wordt opnieuw gericht aan de pagina van de ordestatus aangezien het orderRef mist
   * _Nota van de Reparatie_: Toegevoegde parameter orderRef aan de verbinding in de bevestigingsmail van de bezoekersorde
* _LYNX-690_: Kwesties met klantenvraag wanneer RMA onbruikbaar maakte
   * _nota van de Reparatie_: Bijgewerkt de logica van GraphQL om ervoor te zorgen dat eerder gecreeerde terugkeer toegankelijk blijft zelfs wanneer RMA globaal gehandicapt is. Het foutbericht is verwijderd om de opslag-UX te verbeteren, zodat klanten hun eerdere retourneert nog steeds kunnen bekijken.
* _LYNX-696_: GraphQL keert geen bijgewerkte wortelgegevens terug wanneer het strijdig zijn coupons toepaste
   * _nota van de Reparatie_: Oplossing een kwestie waar het toepassen van een conflicterende coupon met een hogere prioriteit in een foutenmelding resulteerde zonder de bijgewerkte wortelgegevens terug te keren. Wanneer een nieuwe coupon de bestaande ongeldig maakt, retourneert de mutatie nu de juiste kaart met de geldige coupon toegepast.
* _LYNX-699_: Kan ongeldig voor niet-nullable gebied &quot;TaxItem.title&quot;op placeOrder GQL terugkeren
   * _Bevestig nota_: Vaste een kwestie waar de placeOrder mutatie met een interne serverfout wegens een ongeldige waarde voor het niet-nullable gebied TaxItem.title ontbrak. Het veld retourneert nu altijd een geldige waarde, zodat de bestelling correct wordt geplaatst.
* _LYNX-702_: EstimateTotals: Kortingen zijn ongeldig voor virtuele producttypes
   * _nota van de Reparatie_: Los de kwestie met de verbetering estimals op terugkerende nul voor kortingen op wanneer een kortingscode op een kar wordt toegepast die virtuele producten bevat.
* _LYNX-703_: Het product van de bundel keert niet het correcte disconteringspercentage en het bedrag terug
   * _de nota van de Reparatie_: De nieuwe eigenschappen &quot;catalog_disconto&quot;en &quot;row_catalog_disconting&quot;zijn geïntroduceerd voor de prijzen van het cataloguspunt om de correcte kortingsbedragen en percentages op zowel de rij als enige puntniveaus te tonen.
* _LYNX-714_: De berichtconfiguratie van het Gift op productniveau
   * _nota van de Reparatie_: Vaste een kwestie waar de gifteberichten niet op het productniveau werden toegepast wanneer globaal gehandicapt. Als cadeauberichten nu zijn ingeschakeld voor een specifiek product, kunnen ze worden toegevoegd met de updateCartItems-mutatie. Ze worden nu op de juiste wijze opgeslagen en gereflecteerd.
* _LYNX-717_: Kwestie met het verwijderen van gift het verpakken van het kartelpunt
   * _nota van de Reparatie_: Vaste de kwestie waar het verwijderen van gift het verpakken van een wortelpunt gebruikend de updateCartItems mutatie niet zoals verwacht werkte. Nu werkt het toepassen en verwijderen van een cadeauverpakking correct zonder fouten.
* _LYNX-751_: De aangepaste geregistreerde klanteneigenschap werkt niet in Boilerplate, en de trackViewedProduct mutatie moet voor gasten worden toegelaten.
   * _nota van de Reparatie_: De blootstelling trackViewedProduct mutatie om de gebeurtenis van de productmening voor klant en gasten te volgen
* _LYNX-757_: de fout van de de vraagterugkeer van cart.rules in plaats van lege serie voor het geval dat geen actieve kartregels worden toegepast
   * _nota van de Reparatie_: Vaste de vraag cart.rules om een lege serie in plaats van een fout terug te keren wanneer geen actieve wortelregels worden toegepast.
* _LYNX-758_: De kwestie die gift terugwint voor de punten van het karretje
   * _nota van de Reparatie_: Bijgewerkte herwinningslogica om gift terug te keren verpakt opties voor kartelpunten wanneer globaal gehandicapt maar toegelaten op het productniveau
* _LYNX-778_: De vraag van GraphQL met de methode van OPTIONS keert 500 reactiecode terug wanneer adobe-commerce/opslag-verenigbaarheidspakket geïnstalleerd
   * _de nota van de Reparatie_: Vaste een kwestie waar de vraag van GraphQL die de methode van OPTIONS gebruiken een Fout van de Server van 500 terugkeerde toen adobe-commerce/storefront-verenigbaarheid pakket werd geïnstalleerd. Het eindpunt keert nu correct een 200/204 reactie terug zoals verwacht.

### Andere ontwikkelaarsgereedschappen

* _AC-10658_: [ de syntaxisfout van HTML van de kwestie ] verhelpen in visual.phtml
   * _nota van de Reparatie_: Het systeem sluit nu correct de beginmarkering in het visual.phtml- dossier, die juiste syntaxis van HTML verzekeren. Eerder was de begintag niet correct gesloten, waardoor een HTML-syntaxisfout ontstond.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38247>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37457>
* _AC-11474_: [ Uitgave ] Gewijzigd &quot;actief&quot;aan &quot;toegelaten&quot;in bin/magento onderhoud:statusbevel
   * _nota van de Reparatie_: Het systeem verstrekt nu nauwkeurigere statusberichten voor het bevel van de onderhoudswijze, veranderend de status van &quot;actief&quot;in &quot;toegelaten&quot;en van &quot;niet actief&quot;aan &quot;gehandicapt&quot;. Eerder werd het statusbericht voor de opdracht voor de onderhoudsmodus weergegeven als &quot;actief&quot; of &quot;niet actief&quot;, wat tot verwarring kan leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38486>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38410>
* _AC-12571_: Het navigeren in de categorienoom leidt tot fouten in Redis: &quot;Redis zitting overschrijdt gezamenlijke verbindingen&quot;
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38851>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0611e750>
* _AC-12731_: CSP-problemen in combinatie met dev/css/use_css_critical_path
   * _nota van de Reparatie_: Het systeem laadt nu correct CSS dossiers asynchroon op controlepagina&#39;s, zelfs wanneer &quot;dev/css/use_css_critical_path&quot;wordt toegelaten, die ervoor zorgen dat deze pagina&#39;s met de juiste CSS stijlen worden teruggegeven. Eerder werd met een beperkt inhoudsbeveiligingsbeleid (CSP) voorkomen dat inline JavaScript werd uitgevoerd, waardoor CSS-bestanden niet naar behoren werden geladen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39020>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: Gebruikend virtueel type om stop te vormen, kan de interceptormethode niet correct in opstelling worden geproduceerd :di: compileert bevel
   * _nota van de Reparatie_: Het systeem produceert nu correct interceptormethodes wanneer het gebruiken van een virtueel type om een stop te vormen, die verenigbare resultaten verzekeren of precompiled of runtime. Voorheen zou het systeem onjuiste resultaten genereren wanneer vooraf werd gecompileerd in vergelijking met de compilatie bij uitvoering.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/33980>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3441_: Onbekwaam om dossiers van de Collector van Gegevens te downloaden
   * _nota van de Reparatie_: Het downloaden van steun toont niet meer lege pagina in plaats van het downloaden van het dossier.
* _ACP2E-3631_: De eenheidstests van Adobe Commerce 2.4.7-p3 ontbreken
   * _nota van de Reparatie_: Geen versienota&#39;s worden vereist.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/982b1c42>

### Betalings-/betalingsmethoden, bestelling

* _AC-13699_: De details van de de creditcard van de Papal die van de payflow voor later gebruik worden bewaard tonen niet op opgeslagen pagina van de betalingsmethode
   * _Nota van de Moeilijke situatie_: De vroegere details van de Kredietkaart van de Betalingskaart van de Papa voor later gebruik werden niet getoond op de opgeslagen pagina van de betalingsmethode die nu vaste creditcarddetails is tonen op opgeslagen pagina van de betalingsmethode.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/96dec499>

### Betalingen

* _AC-13414_: De betaling van de Kredietkaart (van de Payflow Link) werkt niet
   * _Bevestig nota_: Eerder het krijgen van fout (Betaling werd Ontworpen) terwijl het plaatsen van orde met Kaart na de met succes geplaatste moeilijke opdracht.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a68324bc>
* _ACP2E-2841_: Payflow maakt een nieuwe transactie elke keer dat we op de knop Ophalen klikken op het scherm Transactie weergeven
   * _Fix-opmerking_: het systeem haalt nu de transactie-informatie correct op zonder elke keer dat op de ophaalknop op het scherm voor het weergeven van de transactie wordt geklikt, een nieuwe betalingstransactie aan te maken. Voorheen werd er door op de knop Ophalen te klikken ten onrechte een nieuwe betalingstransactie gemaakt voor een bestelling die al was betaald.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/b2286ecf>
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

* _AC-11932_: Probleem met instellingen voor standaardproductkenmerken
   * _Opmerking oplossen_: het systeem staat gebruikers nu toe om een standaardoptie voor een productkenmerk te deselecteren, zodat het kenmerk niet altijd een standaardinstelling heeft. Eerder, toen een gebrek voor een productattribuut werd geplaatst, was er geen manier om het te schrappen, resulterend in de attributen altijd een standaardreeks.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38703>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-12000_: [ geef ] de schoonmaakbeurt van de Code uit en voeg nieuw kritiek hoofdblok toe en beweeg kritieke css vóór activa
   * _Fix note_: Het systeem bevat nu een nieuw kritiek hoofdblok en verplaatst kritieke CSS voor assets, waardoor meer maatwerk en prestatie-optimalisatie in de frontend mogelijk is. Voorheen werd de kritieke CSS niet vóór de activa geplaatst, waardoor de aanpassings- en optimalisatiemogelijkheden werden beperkt.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38748>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/35580>
* _AC-12176_: Themacompilatie wordt onderbroken wanneer mysql host poortinformatie bevat
   * _Fix-opmerking_: het systeem verwerkt nu correct de MySQL-hostconfiguratie die poortinformatie bevat, wat zorgt voor een succesvolle compilatie van thema&#39;s. Voorheen mislukte het compileren van thema&#39;s als de MySQL-hostconfiguratie in de databaseverbinding poortinformatie bevatte.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38799>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38842>
* _AC-13471_: Ondersteuning voor Symfony&#39;s CommandLoaderInterface in Magento CLI
   * _Fix-opmerking_: Deze wijziging verkort de initialisatietijd van de Magento CLI-app door uitgestelde initialisatie van opdrachten toe te staan totdat ze nodig zijn.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/29266>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/29355>
* _ACP2E-2494_: De kwestie van prestaties wanneer het laden van productattributen in kartregels
   * _de nota van de Reparatie_: Verbeterde vraagprestaties voor verkoopregels - van rond 150ms aan enig cijfer ms.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2673_: De gedeeltelijke indexerende prestaties van de prijs
   * _nota van de Reparatie_: De prijs gedeeltelijke indexerende prestaties zijn verbeterd door sommige schrappingsvragen te optimaliseren die binnen het indexeren proces worden gebruikt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ba25af8a>
* _ACP2E-2850_: De orde wordt verworpen op multi-store opstelling wanneer het gebruiken van Async-orde verwerking + Voorwaarden en
   * _nota van de Reparatie_: De orden die van niet standaardwebsites met toegelaten termijnen en voorwaarden worden geplaatst worden nu verwerkt.
Voordat ze automatisch werden afgewezen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2910_: De vraag van de Rest API van de orde neemt een lange tijd om uit te voeren
   * _nota van de Reparatie_: Het systeem voert nu de Rest API van de Orde vraag binnen een redelijk tijdsbestek uit, verbeterend de prestaties wanneer het halen van een groot aantal orden. Eerder duurde de aanroep van de Order Rest API veel tijd om te worden uitgevoerd, wat vertragingen optrad bij het ophalen van een groot aantal bestellingen.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/001e5188>

### Prestaties, Promotie

* _ACP2E-2617_: Indexeer verkoopregel werkt niet meer
   * _nota van de Reparatie_: Het systeem voltooit nu met succes de indexator van de verkoopregel zelfs met een groot aantal gecombineerde filtergroepen, die ervoor zorgen dat de voorwaarden van de wortelregel op het karretje zoals verwacht worden toegepast. Eerder, zou de indexeerder van de verkoopregel niet voltooien wanneer er een groot aantal gecombineerde filtergroepen waren, die tot een foutenmelding leiden en de toepassing van de voorwaarden van de kartregel verhinderen.

### Prijsstelling

* _wisselstroom-11810_: Magento2.4.6-p4 het Eenvoudige Punt van de Orde API van de Orde ontbrekende prijs
   * _nota van de Reparatie_: Het systeem toont nu correct de prijs van eenvoudige producten wanneer gevraagd door de Orde API, die nauwkeurige gegevensvertegenwoordiging verzekeren. Eerder werd de prijs van eenvoudige producten onjuist weergegeven als nul in de API-reactie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38603>
* _AC-13855_: Penny-afrondingsfout in catalogusregel
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/276e0acd>

### Product

* _AC-10535_: Speciale tekens in de configureerbare productnaam van de associëring worden geconverteerd naar HTML-entiteiten.
   * _Fix-opmerking_: het systeem behoudt nu correct speciale tekens in de namen van gekoppelde producten bij het bewerken van een configureerbaar product, waardoor wordt voorkomen dat ze worden geconverteerd naar HTML-entiteiten. Voorheen werden speciale tekens in gekoppelde productnamen geconverteerd naar HTML-entiteiten wanneer het configureerbare product werd bewerkt.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38146>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38447>
* _AC-10947_: ProductRepository functie GetById maakt niet de juiste cachesleutel
   * _Fix-opmerking_: Het systeem maakt nu correct een cachesleutel aan in de functie GetById van de ProductRepository, ongeacht of de winkel-ID wordt doorgegeven als een string of een geheel getal. Dit zorgt ervoor dat het product bij volgende oproepen uit het geheugen wordt opgehaald, waardoor de prestaties worden verbeterd. Voorheen haalde het systeem het product elke keer dat de functie werd aangeroepen uit de database, zelfs met dezelfde parameters, vanwege het onjuist maken van cachesleutels.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38384>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38433>
* _AC-11992_: [ Uitgave ] [ MFTF ] Toegevoegde AdminClickAddOptionForBundleItemsActionGroup
   * _nota van de Reparatie_: Het systeem omvat nu AdminClickAddOptionForBundleItemsActionGroup, die de functionaliteit van het admin paneel verbetert. Eerder was deze actiegroep niet beschikbaar.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/30857>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/30838>
* _wisselstroom-13173_: [ 3} Het type van de Oplossing van de kwestie {in blok PHPDoc]
   * _nota van de Reparatie_: Het systeem verwijdert nu correct een onbekende referenced variabele in PHPDoc voor de veranderlijke verklaring $helper, die codeduidelijkheid en nauwkeurigheid verbetert. Voorheen veroorzaakte deze onbekende variabele waarnaar in PHPDoc wordt verwezen, verwarring en potentiële onnauwkeurigheden in de code.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38961>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [ Uitgave ] Vaste gebroken Bundel en downloadbare productpagina&#39;s lay-out in Magento >= 2.4.7
   * _nota van de Reparatie_: De lay-out voor bundel en downloadbare productpagina&#39;s is bevestigd, die een verenigbare en correcte vertoning over alle apparaten verzekeren. Eerder traden op deze pagina&#39;s lay-outproblemen op als gevolg van een herschikking van het mediablok met productinformatie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39403>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-5969_: AlertProcessor - Argument #2 ($storeId) moet van type int zijn, gegeven koord
   * _Fix-opmerking_: het systeem activeert nu correct e-mails met productwaarschuwingen door ervoor te zorgen dat de winkel-ID van het juiste gegevenstype is. Voorheen werden e-mails met productwaarschuwingen niet verzonden vanwege een typeafwijking in de winkel-ID.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/35602>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/0574ac23>
* _ACP2E-2944_: [Cloud] addFilterToMap functie werkt niet voor bepaalde kolommen
   * _Fix-opmerking_: Nu kan de aangepaste module worden gebruikt in het bestelraster. Eerder traden er fouten op tijdens het gebruik van een aangepaste module.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3a7c4d17>
* _ACP2E-3471_: [ de Producten van de Wolk ] in Categorie - voeg Producten toe - wijs - Uitgezocht allen toe
   * _nota van de Reparatie_: De gebruikers kunnen producten nu selecteren of schrappen gebruikend de knevel.

### Aanbieding

* _ACP2E-2602_: Kenmerk van de klant niet zichtbaar wanneer het creëren van rekening van uitnodiging
   * _Vaste opmerking_: Klantkenmerken zijn beschikbaar tijdens het maken van een account op uitnodiging.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/39d54c2d>
* _ACP2E-2627_: Couponcode met limiet voor gebruik per coupon wordt niet vrijgegeven voor betaling mislukt bij annulering van bestelling
   * _Fix-opmerking_: het systeem werkt nu onmiddellijk het gebruik van coupons bij wanneer een bestelling wordt aangemaakt of geannuleerd, en voegt regelgebruik toe aan een wachtrij om mogelijke impasses te voorkomen. Dit zorgt ervoor dat een couponcode met de limiet &quot;Gebruik per coupon&quot; wordt vrijgegeven en opnieuw kan worden gebruikt als een order wordt geannuleerd vanwege een mislukte betaling. Eerder heeft het systeem de couponcode niet vrijgegeven voor hergebruik in dergelijke gevallen, wat resulteerde in een foutbericht waarin stond dat de couponcode niet geldig was.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/c971859e>
* _ACP2E-2811_: [ Cloud ] het Reindexeren van het Product van de Regel van de Catalogus meldt SQLSTATE [ HY000 ]: Algemene fout: De server van 2006 MySQL is weggegaan.
   * _nota van de Reparatie_: Het systeem behandelt nu correct douane &quot;batchCount&quot;waarde in di.xml voor &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, die SQL fouten zoals &quot;Algemene fout verhinderen: De server van 2006 MySQL is weggegaan&quot;tijdens het opnieuw indexeren van het Product van de Regel van de Catalogus wegens de onjuiste partijgrootte op grote catalogi
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2926_: [ CLOUD ] de Regel van de Prijs van de Kar voor het Segment van de Klant van Bezoekers die geen korting op kar toepassen
   * _nota van de Reparatie_: Het systeem past nu correct de Regels van de Prijs van de Kaart voor de Segmenten van de Klant van de Bezoeker toe, zelfs als de regel geen coupon gebruikt, die ervoor zorgt dat de aangewezen kortingen op het karretje worden toegepast. Voorheen werden geen kortingen toegepast op het winkelwagentje voor klantsegmenten van bezoekers, tenzij de prijsregel voor winkelwagentjes een coupon gebruikte.
* _ACP2E-3024_: Ontbrekend &quot;Type&quot;Attribuut in &quot;Producten aan Gelijke&quot;Lusje van Verwante Regels van het Product
   * _nota van de Reparatie_: Het &quot;Type&quot;attribuut is nu beschikbaar als filteroptie in het &quot;Producten aan Gelijke&quot;lusje van de &quot;Verwante module van de Regels van het Product&quot;, die voor nauwkeurigere regeldefinitie toestaat. Eerder ontbrak dit kenmerk op het tabblad &quot;Producten op maat&quot;, waardoor de mogelijkheid om nauwkeurige overeenkomende criteria te maken, werd beperkt.
* _ACP2E-3139_: De Regel van de verkoop met het attribuut van de Stap van de Korting van het Aantal (koop X) veroorzaakt dat andere regels niet worden toegepast
   * _Bevestig nota_: De prijsregel van de Kar annuleert eerder toegepaste regels niet als de hoeveelheid van het product in de kar niet genoeg voor toe te passen regel is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3331_: De kwestie van prestaties op de prijsregel van de Kaart - de module van de Regel van de Verkoop van de Vooruitgang
   * _nota van de Reparatie_: Toegevoegde ontbrekende indexen van DB voor filters AdvancedSalesRule
* _ACP2E-3332_: De verkoopregels van de uitgave met Vaste korting van het bedrag en &quot;De Maximale Korting van de Aantal wordt toegepast op&quot;
   * _nota van de Reparatie_: Vaste kwestie met de korting van de kartregels, wanneer de vaste waardekorting wordt gevormd om op een beperkte hoeveelheid producten worden toegepast is het karretje. Eerder werd de waarde &quot;Maximale korting op de hoeveelheid toegepast op&quot; gebruikt voor de berekening van de prijs van het lopende item in het winkelwagentje, niet alleen voor de berekening van de korting op de regel.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3342_: [CLOUD] Magento-upgrade zorgde ervoor dat coupons hoofdlettergevoelig werden
   * _nota van de Reparatie_: Vóór de moeilijke situatie moest u in de couponcode precies typen aangezien het met inachtneming van hoofdletters of kleine letters werd gevormd. Nu wordt de coupon gevalideerd in de backend, ongeacht de configuratie van hoofdletters of kleine letters.
* _ACP2E-3349_: De regels van de wagen &quot;Vaste korting van het bedrag voor het volledige karretje&quot;  Met Actie worden kortingen onjuist toegepast
   * _Fix-opmerking_: couponcodes worden correct gevalideerd, ongeacht hoofdletters of kleine letters, wanneer ze worden gebruikt bij het maken van bestellingen vanuit het beheerdersgebied. Voorheen werd de couponcode niet gevalideerd als deze niet exact overeenkwam met het hoofdlettergebruik van de geconfigureerde winkelwagenregelcode.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3374_: In Achterkant, standaard opslagwaarden voor productattributen (in plaats van verwachte adminwaarden)
   * _nota van de Reparatie_: Nu op Achtergrond, worden de adminwaarden gebruikt in plaats van standaardopslagwaarden voor productkenmerken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3377_: De regels van de winkelwagen &quot;Vaste korting van het bedrag voor het volledige winkelwagentje&quot;actie passen onjuiste kortingen toe wanneer het toevoegen van bundelproducten
   * _Nota van de Reparatie_: De vaste regels van het aantalkarretje werden niet behoorlijk toegepast op bundelproducten. Bij de berekening van het totale kortingsbedrag worden nu onderliggende bundelproducten in aanmerking genomen, wat resulteert in een correcte disconteringsberekening.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3403_: De Regels van de Kar van de Prijs berekenen Verkeerde Korting
   * _nota van de Reparatie_: De vaste kortingen van het bedrag worden nu behoorlijk berekend. Voorafgaand aan de correctie werden kortingen voor vaste bedragen niet correct toegepast op bundelproducten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/0b488dd1>
* _ACP2E-3406_: Geneste categorieën in regelvoorwaarden die niet tonen
   * _Nota van de Reparatie_: Vaste kwestie wanneer de genestelde categorieën onder niveau 3 categorie niet in marketing regels voor categorieconfiguratie worden getoond
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/88660e79>
* _ACP2E-3432_: usage_limit en uses_per_customer het bijwerken niet in salesrule_coupon Lijst
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

### Retourneert

* _ACP2E-3330_: [ CLOUD ] Beperkte admin gebruikers kunnen het terugkeermenu en de knopen zien
   * _nota van de Reparatie_: De beperkte gebruikers Admin hebben nu geen toegang tot RMA verwante controles (menu en knopen).
Eerder beperkte admin-gebruikers konden het retourmenu en de knoppen zien.
* _ACP2E-3443_: Het Scherm van de terugkeer wordt verduisterd wanneer verfrist het scherm
   * _Fix-opmerking_: de gebruiker kan de pagina vernieuwen zonder schermvervorming te ervaren.

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
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-3383_: Onjuiste aanmaak van url_rewrite vermeldingen met meerdere winkels in één winkelgroep
   * _Fix-opmerking_: Vóór de fix kon u alleen URL-herschrijvingen op websiteniveau genereren bij het bewerken van een product. Met de oplossing werd een nieuwe instelling geïntroduceerd (Winkels > Configuratie > Catalogus > Catalogus > Zoekmachineoptimalisatie, &quot;Product URL Rewrite Scope&quot; met opties &quot;Winkelweergave&quot;, &quot;Website&quot;) waarmee u URL-herschrijvingen kunt genereren op winkel- of websiteniveau.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/2d627301>

### Verkoop

* _AC-13751_: De tweede Regel van de Prijs van de Kar wordt niet toegepast als de Eerste regel van de Kar reeds wordt toegepast

### Zoeken

* _AC-13053_: &#39;Voer een zoekterm in en probeer het opnieuw&#39;. Fout op geavanceerde zoekpagina in storefront in 2.4.8-beta1
   * _Fix-opmerking_: het systeem geeft nu de zoekresultaten correct weer op de pagina Geavanceerd zoeken wanneer een productkenmerk is ingesteld op &quot;Nee&quot;. Voorheen resulteerde het instellen van een productkenmerk op &#39;Nee&#39; en het uitvoeren van een zoekopdracht in de foutmelding &#39;Voer een zoekterm in en probeer het opnieuw&#39;.
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
   * _nota van de Reparatie_: Eerder recaptcha van onder e-mailadres van checkout verschijnen unstyled voor talen met lange woorden, zoals duits. Hierna ziet de rechaptcha er hetzelfde uit als alle elementen van de rest van de gebieden.
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
* _wisselstroom-12938_: De &quot;zandbak&quot;van UPS en &quot;prod&quot;opstellingsinstructieupdates in devdoc
* _AC-13172_: [ geef ] Correcte spelling van variabelen voor klantenadres uit
   * _nota van de Reparatie_: Het systeem spelt nu correct variabelen voor klantenadressen, die nauwkeurige vertoning op het rekeningsgebied van het vooreind verzekeren. Eerder kon een onjuiste spelling van deze variabelen leiden tot fouten tijdens lokale coderevisies.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32817>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32815>
* _ACP2E-2738_: Het volgen Venster die onjuiste Verwachte Datum van de Levering tonen
   * _nota van de Reparatie_: De correcte Datum van de Levering van de vertoning voor de Drager van de Verkoop van de Verkoop van de Verkoop.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-2763_: Tabeltarieven worden nog steeds weergegeven, ook al wordt gratis verzending toegepast
   * _Vaste opmerking_: de verzendmethode met tabeltarief wordt nu weergegeven, zelfs als gratis verzending beschikbaar wordt nadat de coupon is toegepast
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/b2286ecf>
* _ACP2E-2765_: MFTF-test AdminCreatingShippingLabelTest mislukt omdat referenties niet zijn toegevoegd in de Jenkins-omgeving
   * _nota van de Reparatie_: mftf testmoeilijke situatie
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ea79f7dd>
* _ACP2E-3340_: Het Spoor FedEx API van FedEx werkt niet met de geloofsbrieven van REST
   * _nota van de Reparatie_: Eerder integratie FedEx vereiste geen extra API sleutels voor het Volgen API. Nu is er een nieuwe configuratie toegevoegd ter ondersteuning van Tracking API-sleutels.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [ de Wolk ] FedEx onderhandelde Tarieven niet op REST teruggekeerd
   * _nota van de Reparatie_: Vorig aan de moeilijke situatie, FedEx rekeningsspecifieke tarieven waar niet verzonden op de reactie, zelfs door volgens documentatie FedEx zij zouden moeten worden verzonden. Na de correctie worden de specifieke tarieven van de rekening verzonden op de reactie door het verzoek van onze kant te veranderen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>

### Enscenering &amp; Preview

* _ACP2E-2901_: Geplande update-instellingen worden niet opgeslagen als ze oorspronkelijk zijn toegevoegd door een update uit te voeren
   * _nota van de Reparatie_: Het systeem ontruimt nu correct de waarden van productattributen in verdere geplande updates wanneer dergelijke attributen in de momenteel lopende update worden gewijzigd. Eerder, toen een productattribuut door een lopende geplande update werd gewijzigd, was het onmogelijk om dergelijke attributen waarden te ontruimen wanneer het creëren van een nieuwe geplande update, die de gebruiker te vereisen om hen na verwezenlijking opnieuw uit te geven.
* _ACP2E-2999_: Winkelwagenprijsregel vanaf datum en tot op heden probleem niet gesynchroniseerd met faseringsupdate
   * _Fix-opmerking_: datums worden opgeslagen op basis van updates voor Cart Price Rule Staging.
* _ACP2E-3104_: De fout van JS in de Voorproef van het Staging
   * _Bevestig nota_: Nu laadt het form-mini-stub.js- dossier met succes zonder enige Js syntaxisfout in de hulpmiddelen van de Ontwikkelaar.
* _ACP2E-3162_: De Speciale PrijsGeleide Inhoud van het Product kan niet worden bijgewerkt
   * _nota van de Reparatie_: Het systeem staat nu voor het uitgeven van de einddatum van een campagne van de prijsupdate toe nadat het is begonnen, die ervoor zorgen dat de gebruikers noodzakelijke aanpassingen aan hun campagnes kunnen maken. Er is eerder een fout gegenereerd tijdens een poging de einddatum van een actieve campagne bij te werken, waardoor gebruikers niet meer wijzigingen kunnen aanbrengen.
* _ACP2E-3453_: Onbekwaam om Geplande Update bij te werken wanneer het Gebruiken van Uniek Attribuut van de Categorie van de Douane
   * _nota van de Reparatie_: Vaste een kwestie waar het bijwerken van een geplande update voor een categorie niet mogelijk was als de categorie een uniek attribuut had
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>

### Targeting

* _wisselstroom-9432_: [ Uitgave ] staat gebruik van CIDR waaiers in onderhoudscategorie toe in lijst van gewenste personen
   * _nota van de Reparatie_: Het systeem steunt nu het gebruik van CIDR waaiers op de onderhoudswijze staat IP lijst toe, toelatend een waaier van IP adressen om onderhoudswijze te mijden. Eerder, staat de onderhoudswijze IP lijst slechts toegelaten individuele IP adressen toe om onderhoudswijze te mijden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37943>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/30699>

### Belasting

* _AC-13295_: [Issue] Feature/php8.1 constructeur eigenschap promotie wee graph ql
   * _Fix note_: Vervang bijna alle eigenschappen door de promotie van de constructeurseigenschap in module wee graph ql:
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/39309>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/36975>
* _ACP2E-3193_: Fixed Product Tax (FPT) werkt niet met configureerbare producten
   * _Fix-opmerking_: FPT voor configureerbare productvariaties werkt naar behoren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Testkader

* _AC-11654_: De test van de integratie faalt testDbSchemaUpToDate toe te schrijven aan JSON kolomtype
   * _Fix-opmerking_: Het systeem herkent nu correct JSON-kolomtypen in het databaseschema tijdens integratietests, waardoor testfouten worden voorkomen als gevolg van een mismatch tussen het databaseschema en het declaratieve schema. Voorheen identificeerde het systeem JSON-kolomtypen ten onrechte als LONGTEXT in MariaDB, waardoor integratietests mislukten.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/ef81f5a2>
* _AC-13362_: [Probleem] PHPDoc correctie spelling
   * _nota van de Reparatie_: Het systeem erkent nu correct vervangen methodes in IDEs toe te schrijven aan een spelcorrectie in PHPDoc. Eerder heeft een spelfout in de PHPDoc ertoe geleid dat IDE&#39;s bepaalde methoden niet herkennen als afgekeurd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/31399>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Het controleren van gedrag met het blijvende het winkelwagentje nadat de zitting is verlopen
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_: De tests van de integratie zijn ontbroken Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _AC-13722_: [ Het Gegevensbestand vergelijkt ] Fatale fout als het gegevensbestand verslag over de Regel van het Doel zonder voorwaarden bevat
   * _nota van de Reparatie_: Eerder als het Gegevensbestand verslag over de doelregel zonder enige voorwaarde bevat kregen fatale fouten maar na het de vergelijkingshulpmiddel van het Gegevensbestand van de moeilijke situatie met succes zonder fatale fouten overgaat.
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
   * _Fix-opmerking_: het systeem genereert nu bronkaarten voor minder bestanden in de ontwikkelaarsmodus, waardoor het gemakkelijker wordt om de bron van een stijl te identificeren. Voorheen was het identificeren van de bron van een stijl een uitdaging bij het uitvoeren van het systeem in de ontwikkelaarsmodus met minder compilatie aan de serverzijde.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/38982>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/38977>
* _AC-1306_: Statische inhoud wordt geïmplementeerd voor uitgeschakelde modules
   * _nota van de Reparatie_: Het systeem sluit nu CSS met betrekking tot gehandicapte modules van de definitieve CSS outputdossiers uit, die ervoor zorgen dat de onnodige stijlen niet worden geladen. Eerder werden CSS met betrekking tot uitgeschakelde modules opgenomen in de uiteindelijke CSS-uitvoerbestanden, wat leidde tot het laden van extra, onnodige stijlen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/24666>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/32922>
* _AC-13459_: Het inconsistente Gedrag in &quot;Voorraad&quot;Sorterend met Minimumdrempel van de Voorraad
   * _nota van de Reparatie_: Het systeem sorteert nu correct producten in de catalogus die op voorraadniveaus wordt gebaseerd, die de vastgestelde Minimum Drempel van de Beeld volgen en zich uit-van-voorraadpunten aan de bodem van de lijst constant bewegen. Voorheen was het sorteergedrag inconsistent, waarbij artikelen niet altijd in de juiste volgorde werden weergegeven op basis van hun voorraadniveaus, en wijzigingen in de sortering konden onvoorspelbaar optreden na het opslaan, vernieuwen of wijzigen van de categoriehiërarchie.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Suggestie voor betere fout die voor require.js ladingsproblemen meldt
   * _nota van de Reparatie_: Deze PR verbetert het foutenbericht wanneer de vereisten er niet in slagen om een component te laden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36761>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38971>
* _AC-14004_: PHP 8.4 de Fouten die van de Verdringing veroorzaken bouwt Gebouwen Gebreken in 2.4-ontwikkelen
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1da9ba6f>
* _AC-9007_: [Probleem] Laad de context van het backend-blok niet op de front-end
   * _Fix-opmerking_: Het systeem zorgt er nu voor dat de context van het back-endblok niet op de frontend wordt geladen, waardoor het maken van onnodige backend-sessies en mogelijke sessievergrendelingen wordt voorkomen. Voorheen laadde het systeem de context van het backendblok op de frontend ten onrechte, wat leidde tot het maken van backend-sessies en mogelijke sessievergrendelingen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37617>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/36368>
* _AC-9168_: [Probleem] Onnodige scripts verwijderen Samenvatting van de beoordeling
   * _Fix-opmerking_: het systeem optimaliseert nu de laadtijd van pagina&#39;s door onnodige JavaScript-scripts uit de beoordelingssectie te verwijderen, in plaats daarvan inline CSS-stijlen te gebruiken voor een efficiëntere en leesbaardere code. Voorheen kon het gebruik van JavaScript-scripts voor het beoordelingsgedeelte de laadtijd van pagina&#39;s vertragen.
   * _GitHub-probleem_: <https://github.com/magento/magento2/issues/37776>
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-2529_: Uitzondering bij het controleren van het saldo van een cadeaubon wanneer Recaptcha is ingeschakeld
   * _nota van de Reparatie_: De gebruikers zullen geschenkkaartsaldo in de mening kunnen halen en het kaartscherm uitgeven. Eerder werden deze details niet weergegeven terwijl reCAPTCHA ingeschakeld was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/4a2795ea>
* _ACP2E-2729_: [ CLARIFICATION ] het Verzoek van de Eigenschap ADA Naleving
   * _nota van de Reparatie_: Het systeem verzekert nu naleving ADA door niet gesteunde CSS eigenschappen te verwijderen en hen te vervangen met gesteunde degenen in het print.css- dossier. Eerder leidde het gebruik van niet-ondersteunde CSS-eigenschappen tot browsercompatibiliteitsproblemen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/57a32313>
* _ACP2E-3061_: [ de bibliotheekcode van de Wolk ] van de Verzekering in effect-drop.js van AC 2.4.4-p8
   * _nota van de Reparatie_: Het systeem voert nu correct de effect-drop.js bibliotheek uit, die het juiste functioneren van gevolgen jQuery UI verzekeren. Eerder werd de bibliotheek effect-drop.js per ongeluk overschreven met de bibliotheek effect-clip.js, wat potentiële problemen met de gevolgen van jQuery UI veroorzaakte.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/35b1b1da>
* _ACP2E-3367_: De Kopbal van de Plaats | Speciale tekens die het welkomstgedeelte van de klant doorbreken
   * _nota van de Reparatie_: Na de moeilijke situatie, worden de speciale karakters correct getoond in de klant welkome sectie.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3561_: Editie klantsegment mislukt met datumbereik
   * _Vaste opmerking_: Het is mogelijk om een klantsegment op te slaan met de voorwaarde van het datumbereik, wanneer slechts één van de datums is bewerkt.
   * _Bijdrage GitHub-code_: <https://github.com/magento/magento2/commit/a52ff98f>
