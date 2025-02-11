---
source-git-commit: cfaa71f84f7d27d41c9d991aceef0087ee3d8ec0
workflow-type: tm+mt
source-wordcount: '9092'
ht-degree: 0%

---
# Opgeloste problemen in Adobe Commerce (v2.4.8-bèta2)

## Opgeloste problemen in v2.4.8-bèta2

We hebben 206 problemen opgelost in de Adobe Commerce 2.4.8-kerncode. Hieronder wordt een subset van de opgeloste problemen in deze release beschreven.

### API&#39;s

* _ACP2E-3236_: De verrichting van Async ontbreekt wanneer SKU van de lading mist
   * _nota van de Reparatie_: Async en synchroniseer eerder ontbroken verrichtingen wegens product sparen fouten als de sku van nuttige lading mist. Na de correctie mislukken de async en synchronisatieproduct de verrichtingen van de steunAPI met relevant uitzonderingsbericht.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>
* _ACP2E-3376_: [ CLOUD ] Onbekwaam om de basis-prijzen bij te werken gebruikend REST API (de waarde van &quot;value_id&quot;in &quot;catalog_product_entity_decimal&quot;wordt niet correct verhoogd.)
   * _nota van de Reparatie_: Eerder aan deze moeilijke situatie, toen rustapi /rest/default/V1/products/base-pricing werd geroepen, verhogingsidentiteitskaart werd verkeerd verhoogd verlatend een hiaat tussen waarden. Na de correctie wordt de increment id verhoogd, incrementeel. Ook het value_id-veldbereik is vergroot.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>
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

### Account

* _AC-10886_: update van het Admin Wachtwoord.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38352>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/4bca5dfe>
* _AC-11718_: Richt lijn opnieuw wanneer URL in hoofdletters heeft
   * _nota van de Reparatie_: Het systeem zet nu automatisch karakters in hoofdletters in URLs in kleine letters om, die een herleidingslijn verhinderen wanneer het toegang tot van homepage. Eerder, zou het hebben van karakters in hoofdletters in Veilige Basis URL een ononderbroken omleidingslijn veroorzaken wanneer het proberen om tot de homepage toegang te hebben.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38538>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38539>
* _AC-13000_: Login als klant opt-in checkbox niet vertaalbaar
   * _Nota van de Oplossing_: Het systeem staat nu &quot;Login toe als checkbox van de Klant het kiezen-binnen&quot;en &quot;Login als tooltip van de controledoos van de Klant&quot;gebieden om bij het werkingsgebied van de &quot;mening van de Opslag&quot;worden geplaatst, toelatend vertalingen voor verschillende archiefmeningen. Eerder werden deze velden alleen ingesteld in het bereik &quot;Website&quot;, zodat vertalingen voor afzonderlijke winkelweergaven niet konden worden vertaald.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32329>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32359>
* _ACP2E-3329_: Na het programma openen, zijn de producten die aan de vergelijkingslijst als gastgebruiker worden toegevoegd niet zichtbaar.
   * _Bevestig nota_: De producten die aan product werden toegevoegd vergelijken lijst alvorens het programma te openen als klant worden nu bewaard na het programma openen.
Eerder waren de producten die als gastgebruiker aan de vergelijkingslijst werden toegevoegd, na het aanmelden niet zichtbaar.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3433_: Sta de configuratiekwesties van Landen in de configuraties van het klantenadres toe
   * _nota van de Reparatie_: Nu het selecteren staat de configuratie van Landen toe beïnvloedt geen landen die voor buiten het bepaalde werkingsgebied worden getoond. Eerder toestaan de configuratie van Landen beïnvloedde klantenadresattributen buiten bepaald werkingsgebied
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3445_: De gedeelde Registratie van het Cadeautje toont de gebeurtenisdatum zoals 1 dag vroeger
   * _nota van de Reparatie_: De datum van de Registratie van het Gift wordt correct nu getoond op Storefront

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
* _wisselstroom-13131_: [ de Waarschuwing van het Correct van de Uitgave ]: Onbepaalde seriesleutel &quot;filters&quot;
   * _nota van de Reparatie_: Het systeem behandelt nu scenario&#39;s waar een nieuwe gebruiker nog niet met referenties heeft gecommuniceerd, verhinderend een ongedefinieerde serie zeer belangrijke &quot;filters&quot;waarschuwing wordt geregistreerd. Deze waarschuwing zou eerder worden geregistreerd als een nieuwe gebruiker geen interactie had gehad met bladwijzers.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39013>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38996>
* _AC-13529_: Het invoer csv- dossier van het product met speciale karakters ontbreekt toe te schrijven aan codeveranderingen in Validate.php- dossier
   * _nota van de Reparatie_: Het systeem bevestigt nu correct en voert productCSV- dossiers in die speciale karakters bevatten, die voor succesvolle gegevensoverdracht toestaan. Als u voorheen een CSV-bestand met speciale tekens importeerde, treedt er een fout op, waardoor het importproces niet meer kan plaatsvinden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13767_: Wanneer het Max Aantal Verzoeken van het Terugstellen van het Wachtwoord&quot;groter dan 0 b.v. wordt geplaatst: 3, &quot;de overschrijdende berichten van de beperkingsfout worden verzonden alvorens de grens te bereiken i.e van tweede keer
* _AC-13768_: Alhoewel het Max Aantal Verzoeken van het Terugstellen van het Wachtwoord&quot;aan 0 wordt geplaatst (Gediabled), &quot;het overschrijden van de berichten van de beperkingsfout wordt verzonden van tweede tijd&quot;
* _AC-7962_: Geen verbinding aan het verschepen wanneer in betalingen in controle in mobiele telefoonmening
   * _Bevestig nota_: Het systeem zorgt nu ervoor dat de controletitels/de verbindingen &quot;Verzending&quot;en &quot;Overzicht &amp; Betalingen&quot;altijd vóór de pagina in mobiele mening zichtbaar zijn, toestaand gebruikers om tussen stappen gemakkelijk te navigeren en noodzakelijke correcties te maken. Eerder waren deze titels/koppelingen verborgen in de mobiele weergave, waardoor het voor gebruikers moeilijk was om hun huidige stap te kennen of terug te gaan naar vorige stappen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36856>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36982>
* _AC-8109_: de vraag van de klant geeft vraagverzendcommentaren aan gecreeerde_bij is teruggekeerd in +0 timezone niet in opslag gevormde timezone
   * _nota van de Reparatie_: Het systeem toont nu correct het &quot;created_at&quot;gebied van ladingscommentaren in gevormde tijdzone van de klant wanneer het gebruiken van de vraag van de Orden van de klant. Eerder, werd het &quot;created_at&quot;gebied getoond in +0 timezone, ongeacht de gevormde timezone van de klant.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36947>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37642>
* _ACP2E-3294_: De het verschepen adresstaat is niet auto het bijwerken
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie, was het verschepende adresgebied (of gebied identiteitskaart) niet synchroon met de adres het factureren informatie. Nu worden zowel het verzendadres als de regio-id correct bijgewerkt wanneer het factuuradres wordt gewijzigd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3364_: De knoop van het Terugstellen werkt niet op Add/geeft admin gebruiker uit
   * _nota van de Reparatie_: Eerder, werkte de knoop van het Terugstellen niet op Add/geef Admin pagina van de Gebruiker uit. Nu werkt de knop Herstellen in het deelvenster Beheer onder Systeem -> Machtigingen -> Alle gebruikers correct op de pagina Admin-gebruiker toevoegen/bewerken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
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
   * _nota van de Reparatie_: Eerder, toelatend JavaScript minificatie op productiemodus binnen het admin paneel veroorzaakte de fouten van JavaScript met betrekking tot TinyMCE 7 om in browser console te verschijnen, die de functionaliteit en gebruikerservaring beïnvloedt. Dit probleem is nu opgelost en zorgt ervoor dat TinyMCE 7 probleemloos werkt zonder fouten te genereren, zelfs als JS-minificatie is ingeschakeld.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3459_: Verzoek om extra veranderingen om ACS2E-3375 moeilijke situatie volledig te voltooien
   * _Bevestig nota_: &quot;-
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Admin UI, Payment/Payment Methods, Order

* _AC-13520_: De Vergunning van de transactie niet die in het Lusje van de Transactie na de Slimme Orde van de Knoop PayPal wordt getoond
   * _nota van de Reparatie_: Het systeem toont nu correct de transactievergunning in het lusje van de Transactie nadat een orde gebruikend de Slimme Knoop van PayPal wordt geplaatst. Eerder werd de transactie voor autorisatie niet weergegeven op het tabblad Transactie nadat werd geklikt op de knop &quot;Autoriseren&quot; en werd geen nieuwe transactie van het type &quot;Autorisatie&quot; gemaakt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>

### Beheerdersinterface, Staging en Voorvertoning

* _ACP2E-3424_: [ Wolk ] het Verwijderen van malplaatje met ontbrekende beelden veroorzaakt pub/media om worden geschrapt
   * _nota van de Reparatie_: Eerder aan deze moeilijke situatie, als de naam van het voorproefbeeld voor een WebBuilder malplaatje mist, werd pub/media omslag geschrapt. Na de correctie wordt alleen de sjabloon verwijderd en de voorvertoning indien gevonden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/0986853b>

### Analyse/rapportage

* _AC-9922_: De Fout van Google Analytics CSP https://region1.analytics.google.com
   * _nota van de Reparatie_: Het systeem staat nu correct verbindingen aan &quot;https://region1.analytics.google.com&#39; toe wanneer Google Analytics wordt toegelaten, verhinderend de fouten van het Beleid van de Veiligheid van de Inhoud (CSP). Voorheen zou het inschakelen van Google Analytics en het bekijken van de website vanuit de EU leiden tot fouten in de CSP-console als gevolg van een weigering om verbinding te maken met &#39;https://region1.analytics.google.com&#39;.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37750>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38991>
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
* _ACP2E-3302_: [ de Onjuiste Berekeningen van de Wolk ] in het Rapport van het Gebruik van de Coupon
   * _Bevestiging nota_: Het verkooptotaal in het netwerk van het couponrapport wordt nu nauwkeurig berekend door zowel het &quot;Bedrag van de Belastingcompensatie van de Korting&quot;als het &quot;Scheepskortingsbedrag van de Belastingcompensatie van de Schrapping te omvatten.&quot; Voorheen ontbraken deze bedragen in de berekening, wat leidde tot verschillen tussen het totaal van de verkopen en de gegevens van de verkooporder.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3339_: De kwesties met gedeelde &quot;&lt;project_id>/var/tmp&quot;
   * _nota van de Reparatie_: De tijdelijke dossiers van DataExport van de Analyse zullen de folder van sys tmp gebruiken, die geschikter voor frequente toegang en veranderingen is. Om botsingen te vermijden in het geval dat de veelvoudige instanties op de zelfde server lopen, werd de weg tmp bijgewerkt om unieke identiteitskaart van een instantie te gebruiken
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Analyse/rapportage, cloud

* _ACP2E-3187_: Metrisch in NR zou voor achtergrondtransacties misleidend kunnen zijn - Follow-up van ACP2E-3067
   * _Nota van de Moeilijke situatie_: De transacties van de achtergrond (kruin) zullen New Relic gebruiken toepassingsnaam die in de config montages wordt bepaald
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>

### B2B

* _AC-13501_: 2.4.8-bèta102 de uitgave van de pakketonderneming ontbreekt met toepassingsuitzonderingen
* _AC-13816_: Onbekwaam om b2b eigenschap in achterste admin voor het eerst toe te laten
* _ACP2E-2139_: De producten die aan gedeelde catalogus worden toegewezen wijzen niet op het vooreind terug wanneer de gedeeltelijke index wordt uitgevoerd
   * _nota van de Reparatie_: De producten die aan gedeelde catalogus via REST API worden toegewezen zijn nu onmiddellijk zichtbaar op storefront nadat het gedeeltelijke indexeren volledig is. Eerder waren de producten pas zichtbaar na een volledige herindexering.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3247_: sales_clean_quotes cron schrapt citaten van aan nog goedgekeurde kooporden
   * _Nota van de Moeilijke situatie_: De citaten die in kooporden worden gebruikt zullen nu niet door sales_clean_quotes cron baan worden geschrapt
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3465_: De knoop van de Orde van de plaats verdwijnt in de details van de Orde van de Aankoop
   * _Nota van de Reparatie_: Vaste een kwestie waar de knoop van de Orde van de Plaats voor goedgekeurde inkooporden werd verborgen wanneer een productvariatie minimumaantal in gespecificeerde kaart had
* _ACP2E-3474_: [ CLOUD ] Geen dergelijke entiteit met id = 0 met b2b module
   * _Bevestig nota_: De geregistreerde gebruiker kan product aan wagentje toevoegen wanneer de Gedeelde eigenschappen van de Catalogus worden toegelaten.
Eerder toegevoegd product aan winkelwagentje resulteerde in Fout &#39;geen dergelijke entiteit met id = 0&#39;

### B2B, winkelwagentje en kassa

* _AC-13817_: kan producten op kar niet zien wanneer b2b alle eigenschappen worden toegelaten

### B2B, GraphQL

* _ACP2E-3391_: [ Wolk ] Onbekwaam om custom_attributes te plaatsen terwijl de bedrijfverwezenlijking over de grafische vraag
   * _nota van de Reparatie_: Na de moeilijke situatie, is het mogelijk om het &quot;custom_attributes&quot;attribuut voor bedrijfadmin tijdens bedrijfverwezenlijking te plaatsen gebruikend grafisch verzoek.

### Bundel

* _AC-10826_: Het berichtaantal van de Fout van de Bevestiging van de Bundel van de Bundel van de Storefront meer dan 1
   * _nota van de Reparatie_: Het systeem toont nu slechts één bericht van de bevestigingsfout wanneer &quot;toevoegt aan Kart&quot;wordt geklikt zonder enige checkbox opties voor een gebundeld product te selecteren. Eerder gaf het systeem meerdere foutmeldingen weer voor validatie voor elk niet-geselecteerd selectievakje.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13321_: De Uitzondering van Magento die in sommige orde verwante testgevallen wordt geworpen
   * _nota van de Reparatie_: Het systeem behandelt nu correct de stap &quot;sendGuestPaymentInformation&quot;in diverse testgevallen, die de uitzonderingen van Magento verhinderen worden geworpen. Voorheen deden deze uitzonderingen zich voor als gevolg van een null-betalingsmethode, wat in verschillende testgevallen tot mislukkingen leidde.

### Winkelwagentje en Afhandeling

* _AC-11914_: [ geef ] CartFixed berekening van de Regel van de Verkoop uit: onjuist disconteringsbedrag
   * _nota van de Reparatie_: Het systeem berekent nu correct het kortingsbedrag voor verkoopregels met winkelwagentvaste bedragen, die nauwkeurige kortingen verzekeren wordt toegepast ongeacht veranderingen in kartelpunten. Eerder kon het kortingsbedrag verkeerd variëren wanneer winkelwagentjes werden gewijzigd, wat soms tot aanzienlijk grotere kortingen leidde dan verwacht.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38694>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
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
* _AC-13797_: De verbinding van de registratiekenteken werkt niet behoorlijk
* _ACP2E-3176_: [ de Snelle orde van de Wolk ] grote hoeveelheid SKU prestaties
   * _nota van de Reparatie_: De prestaties van de kassa zijn verbeterd wanneer de attributen die in de voorwaarden van de kartprijs worden gebruikt niet voor alle producten aanwezig zijn en wanneer de eigenschap van de KAART (Minimale geadverteerde prijs) wordt toegelaten.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/66dea0de>
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
* _ACP2E-3488_: De bestaande citaatgegevens zijn niet bijgewerkt/niet zichtbaar, in plaats daarvan creeer een nieuw citaatverslag wanneer trigger_recollect = 1
   * _Bevestig nota_: De winkelwagentjes van de klant verdwijnen niet meer als resultaat van een product dat wordt geschrapt nadat het aan het winkelwagentje werd toegevoegd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>

### Catalogus

* _wisselstroom-11970_: Onmogelijk om configureerbare producten met één checkbox geselecteerde douaneoptie opnieuw in orde te brengen
   * _nota van de Reparatie_: Het systeem verwerkt nu correct het opnieuw ordenen van configureerbare producten met één enkele geselecteerde checkbox douaneoptie, die voor succesvolle korteverwezenlijking toestaat. Voorheen leidde het opnieuw ordenen van dergelijke producten tot een fout en werd voorkomen dat artikelen aan het winkelwagentje werden toegevoegd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38736>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1d144bce>
* _AC-13068_: Ontbrekende opties van de Dropdown
   * _nota van de Reparatie_: Het systeem toont nu correct alle waarden in dropdown wanneer het creëren van een nieuw attribuut met meer dan 20 waarden. Eerder werden alleen de eerste 20 waarden of een andere geselecteerde paginawaarden weergegeven, waardoor de resterende waarden ontbraken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13296_: [ Uitgave ] Huidige opslag-id van het Gebruik voor categorie runtime geheime voorgeheugen
   * _nota van de Reparatie_: Het systeem gebruikt nu correct huidige opslagidentiteitskaart voor categoriemuntime geheim voorgeheugen, dat gegevensopheffing verhindert wanneer de wedijver wordt gebruikt of de douanecode bewaart de categorie in verschillende opslag. Eerder was het object dat in runtime was opgeslagen mogelijk afkomstig uit de verkeerde opslag, wat tot gegevensoverschrijving heeft geleid.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39310>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/36394>
* _AC-13324_: Bak/magento sampledata:opstellen - geen-update werpt een uitzondering
   * _nota van de Reparatie_: Het systeem keurt nu correct een booleaanse waarde goed wanneer het gebruiken van —geen-updateoptie in sampledata:stel bevel op, dat om het even welke fouten tijdens de plaatsing van steekproefgegevens verhindert. Er is eerder een fout opgetreden bij het gebruik van deze opdracht omdat het systeem een geheel getal verkeerd had verwacht.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39344>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39345>
* _AC-13355_: [ het gebruik van de Uitgave ] van de Oplossing van EAV geheim voorgeheugentype
   * _nota van de Reparatie_: Het systeem gebruikt nu correct het EAV geheim voorgeheugentype in alle relevante plaatsen, die verenigbare en efficiënte gegevens caching verzekeren. Eerder werd het EAV-cachetype niet consistent gebruikt, wat tot mogelijke inefficiënties en inconsistenties in het in cache plaatsen van gegevens leidde.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/32322>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/31264>
* _AC-13596_: Het Geavanceerde Onderzoek van de catalogus met lege gegevens gaat naar de pagina van het onderzoeksresultaat [ 2.4.dev tak ]
   * _nota van de Reparatie_: Het systeem behoudt nu correct gebruikers op de Geavanceerde pagina van het Onderzoek en toont een foutenmelding wanneer zij proberen om een onderzoek uit te voeren zonder om het even welke gegevens in te gaan. Als u voorheen een lege zoekopdracht zou uitvoeren, zou u gebruikers omleiden naar de pagina Geavanceerd zoeken in catalogus met een bericht waarin ze worden gevraagd hun zoekopdracht te wijzigen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _AC-13786_: De witte grens wordt niet remover na het onbruikbaar maken product_image_white_edges voor douanethema
* _ACP2E-3103_: Het nieuwe voer van Producten RSS wordt niet bijgewerkt met nieuwe producten toe te schrijven aan geheim voorgeheugen
   * _nota van de Reparatie_: Het voer van Rss voor Nieuwe Producten wordt nu bijgewerkt wanneer een product als nieuw en bewaard wordt geplaatst
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d01ee51e>
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
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3410_: De configureerbare product geeft vormlading oorzaken onderbreking en geheugenuitputting uit
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke configureerbare productvariaties werden geconstrueerd gebaseerd op alle mogelijke combinaties van attributenopties. In gevallen waarin kenmerken veel opties hadden, resulteerde dit in een langdurige en hulpbronnenintensieve bewerking. Configureerbare productvariaties worden nu samengesteld op basis van bestaande onderliggende productkenmerken. Dit leidt tot veel minder berekeningen, dus tot een beter gebruik van middelen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3454_: Fotorama laadt correct geen video wanneer het gebruiken van Monsters en de optie wordt pre-geselecteerd via URL
   * _nota van de Reparatie_: De video&#39;s van het product zullen nu behoorlijk op configureerbare pagina van productdetails teruggeven, als URL geselecteerde opties bevat.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3461_: De Breedte van Carousel PageBuilder toont producten die voorwaarden niet aanpassen
   * _Nota van de Reparatie_: De lijst van het product die in widgets wordt gebruikt respecteert nu categorieconfiguratie
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3469_: De fout van de bevestiging teweeggebracht voor Alle Producten in Groep wanneer men ongeldige hoeveelheid heeft
   * _nota van de Reparatie_: Nu, wordt de bevestigingsfout correct teweeggebracht voor alle producten in de groep wanneer één product een ongeldige hoeveelheid heeft, die niet eerder gebeurde.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/56463d5e>
* _ACP2E-3516_: De Tijdelijke lijsten van indexen worden niet schoongemaakt als het proces wordt geëindigd
   * _nota van de Reparatie_: De tijdelijke lijsten van de indexeerder CatalogRule worden nu schoongemaakt als het indexeerproces wordt geëindigd
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>
* _ACP2E-3520_: [ de mislukkingen van de de eenheidstest van de KANDIS ] van de Kern in 2.4.7-p3
   * _nota van de Reparatie_: De nota&#39;s van de Versie voor deze test zijn niet nodig aangezien het een eenheid-test verbetering is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>

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

### Catalogus, GraphQL

* _ACP2E-3312_: De terugkeer van de prijzen van de lijst verkeerde waarde in producten GraphQL (in vergelijking met Storefront)
   * _nota van de Reparatie_: Na de moeilijke situatie, hebben de de laagprijzen van het product voor grafische verzoeken zijn teruggekeerd prijs per één punt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3385_: [ CLOUD ] B2B: categoriekwestie via GraphQL
   * _nota van de Reparatie_: Na de moeilijke situatie, keert de categorieën grafisch vraagcategorieën categorieën met toestemming terug zelfs als de wortelcategorie geen toestemming heeft verleend.

### Catalogus, zoeken

* _ACP2E-3345_: De Fout van het type kwam voor wanneer het creëren van voorwerp: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Uitzondering
   * _nota van de Reparatie_: Na de moeilijke situatie, kan een geval van klasse Magento\CatalogSearch\Model\Indexer\Fulltext worden gecreeerd zonder $data te specificeren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
* _ACP2E-3521_: [ CLOUD ] Kwestie met Producten is niet Zichtbaar op Voorzijde na het Opslaan in Admin van Magento
   * _nota van de Reparatie_: Na de moeilijke configureerbare producten die kindproducten met lange namen hebben zullen niet in de storefront worden gemist.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>

### Catalogus, verzenden

* _ACP2E-3195_: Het verschepen adres leeg terwijl het plaatsen van een orde voor een punt van de cadeauregistratie
   * _nota van de Moeilijke situatie_: Eerder, voor gast-gebruiker gift-registratie punten, wanneer teruggekeerd van de e-mailfunctie, produceerde een leeg leeg adres, dat voor het plaatsen van een orde onjuist is. Nadat deze moeilijke situatie wordt toegepast, controleert het geschenkenregister het programma geopende gebruiker/gastgebruikers en toegewezen adressen als zij bestaan.

### Inhoud

* _AC-12692_: De categorieboom van widget wordt niet correct teruggegeven
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39008>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/58e40ceb>
* _AC-13054_: Onbekwaam om &quot;Gebruikend Standaardwaarde&quot;bericht te zien wanneer het veranderen van het thema in de pagina van de ontwerpconfiguratie
   * _nota van de Reparatie_: Het systeem omvat nu een afzonderlijke kolom om het &quot;Gebruikende Standaard waarde&quot;bericht afhankelijk van het geselecteerde thema in de pagina van de ontwerpconfiguratie te tonen. Dit zorgt voor helderheid en zichtbaarheid van de status van de standaardwaarde. Eerder werd het bericht &#39;Standaardwaarde gebruiken&#39; niet weergegeven, wat leidde tot verwarring over de status van het geselecteerde thema.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/47b448e2>
* _wisselstroom-13569_: [ geef uit ] herstelt achterwaartse verenigbaarheid met stop TinyMCE opnieuw (na het..
   * _nota van de Reparatie_: Het systeem herstelt nu achterwaartse verenigbaarheid met stop TinyMCE, toestaand functies die binnen de stop worden bepaald om worden geroepen wanneer het gebruiken van widget van een andere plaats. Als gevolg van een wijziging in de TinyMCE-versie gaven de plug-ins eerder de widgets niet als een object, wat resulteerde in een fout tijdens het aanroepen van bepaalde functies op de widgetinstantie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39262>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39258>
* _ACP2E-3122_: [ CLOUD ] uploadt beeldknoop werkt niet
   * _Bevestig nota_: Vóór de Upload knoop van het Beeld voor Banner en Schuif van PageBuilder niet zoals verwacht werkte, en nu wanneer het drukken van het opent de lokale dossiermanager om het gezochte beeld te selecteren om te uploaden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/476ef8ea>
* _ACP2E-3275_: [ Wolk ] - de Schuif van CMS die de recentste veranderingen niet weerspiegelt
   * _nota van de Reparatie_: De kwestie is opgelost door de sliderlijst te verzekeren wordt verfrist terwijl sparen gebeurtenis op het uitgeeft diascherm wordt teweeggebracht. Eerder was het aanleiding tot het probleem.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3326_: Een fout komt in CSM pagina voor wanneer de blokken van CMS gebruikend paginabouwer in bepaalde orde worden opgenomen
   * _nota van de Reparatie_: Eerder op sommige versies van PHP en OS (Linux), zou het teruggeven van blokken die andere cms blokken door PageBuilder van verwijzingen voorzien met een &quot;Onbekende fout voorgekomen zijn ontbroken. Probeer het opnieuw.&quot;. Nu wordt de inhoud van de cms-blokken correct gerenderd in inhoud die door PageBuilder wordt gecontroleerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2-page-builder/commit/ae2cdeb0>
* _ACP2E-3388_: [ de Dynamische blokken van de Wolk ] zullen niet behoorlijk functioneren
   * _Bevestig nota_: Logged-in klantensegmenten worden nu ontruimd na logout verhinderend de gastzitting eerder het programma geopende segmenten erven
* _ACP2E-3430_: De recentste veiligheidsupdates met TinyMCE 7 ontbrekende doopvontgrootte
   * _nota van de Reparatie_: De grootte van de doopvont en de selecteurs van de doopvontfamilie zijn nu beschikbaar in de redacteur van WYSIWYG. Voorafgaand aan deze moeilijke situatie, met TinyMCE 7 waren deze niet beschikbaar in de redacteursinterface.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>, <https://github.com/magento/magento2-page-builder/commit/2c2f7a0e>

### Klanten/klanten

* _AC-13060_: Het Segment van de klant > Voorwaarde > Geschiedenis van het Product* > &quot;het product werd bekeken&quot;werkt niet
   * _nota van de Reparatie_: Het systeem toont nu correct gecompenseerde klanten in het &quot;Product werd bekeken&quot;voorwaarde onder de Segmenten van de Klant, wanneer aan de voorwaarde wordt voldaan. Eerder was het aantal geregistreerde klanten dat bij een transactie was betrokken, zelfs toen aan de voorwaarde was voldaan, nul.
* _AC-8499_: Het de tekstgebied van het gebied wordt niet teruggesteld wanneer landdropdown wordt veranderd
   * _nota van de Reparatie_: Het systeem stelt nu het gebied van de gebiedstekst opnieuw in wanneer het land in het dropdown menu wordt veranderd, die ervoor zorgen dat de vorige waarden niet blijven bestaan. Als u voorheen het land uit de vervolgkeuzelijst wijzigde, werd het veld Regio niet opnieuw ingesteld, waardoor de laatst opgeslagen waarde behouden bleef.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-9240_: Het schrappen van Klant schoon niet Alle Browser Gegevens van de Zitting over Storefront voor binnen het programma gezette &amp; Geschrapte Klant
   * _Bevestig nota_: Het schrappen van een klant ontruimt nu alle gegevens van de browser zitting van de storefront voor het programma geopende en geschrapte klanten zoals verwacht. De winkelier kan blijven winkelen en hun browser behandelt hun sessie als een gastsessie. Eerder, toen de klantenrekening voor een het programma geopende verkoopster werd geschrapt van Admin, dan browser van de verkoopster de fouten van JavaScript verwierp.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7d5e3906>

### Kader

* _AC-10738_: De configuratie van de Varnish sluit niet alle marketing parameters uit
   * _nota van de Reparatie_: Het systeem sluit nu correct alle gemeenschappelijke marketing parameters in de configuratie van Varnish uit, die nauwkeurige het volgen en analyse verzekeren. Eerder waren bepaalde marketingparameters zoals gad_source, srsltid en msclchild niet uitgesloten, wat tot mogelijke onnauwkeurigheden in de gegevensverzameling leidde.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38298>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39188>
* _AC-11592_: [ Uitgave ] staat slechts geldige voorkeur tijdens opstelling toe :di: compileert
   * _nota van de Reparatie_: Het systeem werpt nu een fout tijdens de opstelling :di: compileert bevel als een voorkeur voor een klasse wordt gecreeerd die niet bestaat of specifiek uitgesloten is, die ervoor zorgt dat slechts de geldige voorkeur wordt toegestaan. Eerder, zouden deze scenario&#39;s ongemerkt ontbreken, potentieel die om het even welke stop-ins verbonden aan de originele klassen nutteloos teruggeven.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38517>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/33161>
* _AC-11809_: [ geef ] douaneattributen van de Uitgave aan huidige verbinding via XML over
   * _nota van de Reparatie_: Het systeem staat nu douanekenmerken toe om tot de huidige verbinding via XML worden overgegaan, die ervoor zorgen dat deze attributen correct worden getoond zelfs wanneer de verbinding de huidige pagina is. Eerder werden er geen aangepaste kenmerken weergegeven voor de huidige paginakoppeling omdat de methode getAttributesHtml() niet werd gebruikt voor de huidige koppeling.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38500>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/30070>
* _wisselstroom-12127_: [ Uitgave ] vermijdt een misconfiguration oneindige lijn
   * _Bevestig nota_: Het systeem vermijdt nu een oneindige lijn door zelfreferentiële afbeelding in virtuele typeconfiguraties te verhinderen. Dit zorgt ervoor dat de toepassing niet vastzit in een eindeloze lus wanneer wordt geprobeerd om een zelf-verwijzende knoop te dereference. Eerder, als een virtuele typeconfiguratie zelf-verwijzing was, zou het de toepassing veroorzaken om voor onbepaalde tijd te draaien.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38822>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38794>
* _AC-12299_: De Manager van objecten wordt niet gebruikt voor Magento\Csp\Model\Mode\Data\ModeConfigured
   * _nota van de Moeilijke situatie_: Het systeem gebruikt nu correct de Manager van Objecten wanneer het creëren van het voorwerp ModeConfigured, toestaand plugins om op dit voorwerp worden gebruikt. Eerder werd Objectbeheer niet gebruikt, waardoor plugins niet konden worden toegepast op het ModeConfigured-object.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38875>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38886>
* _wisselstroom-12540_: De onjuiste mededeling van het documentblok in de Beeld van het Product en de Waarschuwingen van de Prijs
   * _Nota van de Oplossing_: De nota van het documentblok voor de deleteCustomer methode in de Aandelen van het Product en de Alarm van de Prijs is verbeterd om nauwkeurig te wijzen op dat de methode alle voorraadproduct of prijsalarm verbonden aan een bepaalde klant en een website, niet de klant van de website schrapt. Eerder werd in de opmerking onjuist aangegeven dat de methode bestond in het verwijderen van een klant van de website.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38939>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39001>
* _AC-12857_: PHP 8.2.15 verwijderde de uitbreiding van FTP
   * _nota van de Reparatie_: Het systeem omvat nu de uitbreiding van FTP als gebiedsdeel in het composer.json- dossier, die de succesvolle configuratie van de invoer CSV via FTP verzekeren. Eerder werd een fout gegenereerd bij het configureren van CSV-import via FTP omdat de FTP-extensie ontbreekt in het PHP-pakket.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39083>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-12964_: Mogelijkheid om Gebied voor dev :di: info CLI bevel te bepalen
   * _nota van de Reparatie_: Het systeem staat nu ontwikkelaars toe om een gebied voor het dev :di: info CLI bevel te bepalen, dat de ontwikkeling en het het zuiveren proces verbetert. Eerder kon deze opdracht alleen informatie weergeven voor het GLOBAL-gebied.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38758>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38759>
* _AC-13247_: opstelling:verbetering ontbreekt met MariaDB 11.4 versie toe te schrijven aan charset &amp; collationveranderingen
* _AC-13279_: [ Uitgave ] verwijdert alle marketing parameters krijgen om het geheime voorgeheugen te minimaliseren
   * _nota van de Reparatie_: Het systeem verwijdert nu alle marketing krijgen parameters om geheim voorgeheugengebruik te optimaliseren, die de logica weerspiegelen die wordt gebruikt wanneer Varnish in gebruik is. Eerder, konden deze parameters tot geheim voorgeheugenopblazing en verminderde prestaties leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39266>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39099>
* _AC-13345_: [ Uitgave ] [ PHPDOC ] verbeter slechte phpdoc Magento\Directory\Model\AllowedCountries::getAllowedCountries ()
   * _nota van de Reparatie_: De PHPDoc voor AllowedCountries::getAllowedCountries () methode is verbeterd om nauwkeurige informatie te verstrekken, die de duidelijkheid en het nut van de documentatie verbetert. Eerder bevatte de PHPDoc voor deze methode onjuiste informatie, die tot verwarring of misbruik van de methode kon leiden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39246>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39241>
* _wisselstroom-13348_: [ Uitgave ] verwijdert één of andere code voor PHP versies die wij niet meer steunen.
   * _Bevestig nota_: Verwijdering van code voor PHP versies die niet meer in Magento worden gesteund
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39361>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39202>
* _AC-13417_: [ geef ] van de Kwestie tot Adapter ImageMagick compatibel met php8 (Impliciete omzetting van vlotter aan int)
   * _nota van de Reparatie_: Het systeem verzekert nu verenigbaarheid met PHP8 door vlotteraantallen correct te behandelen wanneer het berekenen van beelddimensies, die om het even welke fouten te voorkomen toe te schrijven aan impliciete omzetting van vlotter aan int. Eerder kon de berekening van de afmetingen van de afbeelding leiden tot zwevende getallen, die bij impliciet afronden een fout zouden veroorzaken.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39402>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/37362>
* _AC-13537_: [ Uitgave ] [ PHPDOC ] verbeter slechte phpdoc Magento\Framework\App\Config\ScopeConfigInterface
   * _nota van de Reparatie_: Deze update verbetert de annotaties PHPDoc in Magento\Framework\App\Config\ScopeConfigInterface om het type van het argument $scopeCode voor getValue en isSetFlag nauwkeurig te wijzen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39492>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39199>
* _AC-8662_: [ Uitgave ] verbetert het registreren van de cron fout
   * _nota van de Reparatie_: Het systeem vangt en registreert nu zowel STDERR als STDOUT voor kroonprocessen, die waardevolle kenmerkende informatie in scenario&#39;s verstrekken waar de kroonprocessen ontbreken. Eerder, werden om het even welke foutenmeldingen binnen kroonprocessen niet geregistreerd, en STDERR en STDOUT voor kroongroepen die in afzonderlijke processen lopen werden verloren.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37453>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/32690>
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

### Framework, UI Framework

* _ACP2E-3324_: Mogelijkheid om configuratiewaarde te beschrijven zelfs als het gesloten is
   * _nota van de Reparatie_: Eerder aan deze moeilijke situatie, kon de ontwerpconfiguratie niet door bak/magento config worden geplaatst:vastgestelde bevel en gesloten waarden konden door manipulatie van de vorm worden veranderd die hen toont. Nadat de fix vergrendelde waarden zijn ingesteld vanuit cli met —lock-env of —lock-conf, kunnen deze niet meer worden bijgewerkt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>

### GraphQL

* _ACP2E-2974_: Vertalingen voor de attributen van de klantenterugkeer die niet in GraphQL API voor respectievelijke StoreView worden weerspiegeld
   * _nota van de Oplossing_: De vertalingen voor de attributen van de klantenterugkeer worden weerspiegeld in GraphQL API voor respectieve StoreView.
Eerder werden de teruggavekenmerken van de klant voor de respectievelijke StoreView niet weerspiegeld in de GraphQL API.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3215_: [ Cloud ] Kwestie met de Authentificatie van de Gebruiker en de Symbolische Toegang van de Intersite in de Opstelling van de Multi-Plaats
   * _Bevestig nota_: Info van de Klant GraphQl en de vragen van de Kaart in de opstellingscontroles van de MultiSite als de klant op niet-standaard website bestaat.
Eerder uitgevoerde query werkte zonder ervoor te zorgen dat de klant op een niet-standaard website in de installatie van meerdere sites aanwezig was.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3255_: [ GRAPHQL ] modelwaarde zou moeten worden gespecificeerd wanneer het krijgen van customerCart
   * _nota van de Reparatie_: De vraag van GraphQL &quot;customerCart&quot;kan nu een leeg karretje tot stand brengen zelfs wanneer het citaat niet beschikbaar in het gegevensbestand is. Eerder was deze bewerking mislukt vanwege problemen met landvalidatie tijdens het maken van de lege winkelwagen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/fd5cf3af>
* _ACP2E-3380_: [ GraphQl ] de punten van de Schitlijst zijn zichtbaar via GraphQl maar niet zichtbaar op opslag
   * _nota van de Reparatie_: De producten van het Wislist waar niet behoorlijk worden vermeld wanneer gevraagd via GraphQL. Welnu, de producten van vorklijsten worden gefiltreerd gebaseerd op verstrekte archiefcontext.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>
* _ACP2E-3404_: [ GraphQL ] het wachtwoord e-mailinconsistentie van het Terugstellen tussen inhoud en onderwerp/verbinding
   * _nota van de Reparatie_: De kwestie is opgelost door de correcte opslag te simuleren waar de rekening van de klant wanneer het verzenden van het verzoek van het wachtwoordterugstellen, ongeacht de websiteopslag wordt geregistreerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3419_: [ de producten van de Wolk ] GraphQL de vraagwinst verwante die producten niet aan huidige website worden toegewezen
   * _nota van de Reparatie_: Eerder, voor de vraag graphQL, multi-store verwante producten tonen niet behoorlijk voor productvraag. Nadat deze moeilijke situatie wordt toegepast, voor producten, vraag graphQL verwante producten die dienovereenkomstig worden getoond multi-store.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>
* _ACP2E-3447_: Het gebruiken van onjuiste identiteitskaart van de Opslag in de kopbal van GraphQL veroorzaakt fatale geheugenfout
   * _nota van de Reparatie_: Het verzenden van verkeerde opslagcode in GraphQL verzoek resulteert niet meer in bovenmatig geheugengebruik.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>
* _ACP2E-3467_: [ Cloud ] 500 reactie op lege Grahql op 2.4.7
   * _nota van de Reparatie_: Na de moeilijke situatie, zullen de ongeldige grafische verzoeken niet in het exception.log dossier worden geregistreerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>
* _LYNX-600_: De maximum standaardGraphQL vraagingewikkeldheid van de verhoging aan 1000

### GraphQL, zoeken

* _ACP2E-948_: De lijst van het product GraphQL vraag beperkt tot total_count 10.000 slechts producten
   * _nota van de Reparatie_: Na de moeilijke situatie, is het onderzoeksresultaat niet beperkt tot 10000 producten, wordt het mogelijk om alle producten te krijgen die aan de onderzoekscriteria voldoen zelfs als de telling meer dan 10000 is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4cf5e62>

### GraphQL, testkader

* _ACP2E-3363_: Magento\GraphQl\App\GraphQlCustomerMutationsTest.php de mislukking van de Test van de Integratie
   * _Bevestig nota_: &quot;-
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/a4cf5e62>

### Importeren/exporteren

* _ACP2E-3172_: Ontbrekende knoop van de Invoer
   * _Bevestig nota_: Los de knoop van de Invoer ontbrekende kwestie na gegevenscontroles met correcte en onjuiste verslagen in CSV op. Eerder wordt de knop Importeren niet weergegeven na gegevenscontroles met juiste en onjuiste records in de CSV.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1819fe73>
* _ACP2E-3382_: Het uitgevoerde klantenadres kan niet worden ingevoerd
   * _nota van de Reparatie_: De het adresinvoer van de klant zal zoals verwacht te werk gaan. Voorheen zou een bestand met het importeren van klantadressen geen validatie doorstaan als Share Customer Accounts = Global, en er zijn twee websites waar de standaardwebsite een lijst met landen met beperkingen heeft en het adres dat wordt geïmporteerd, geldt voor een andere website waar toegestane landen verschillend zijn
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3448_: [ de Verkeerde hoeveelheid van de Wolk ] in Csv- dossier gaf geen fout
   * _nota van de Reparatie_: Nu zal de invoer van voorraadbronnen bevestigingsfout voor niet numerieke waarden in de kwantitatieve kolom werpen. Eerder werd bij het importeren van voorraadbronnen met een niet-numerieke waarde in de kolom Hoeveelheid de hoeveelheid ingesteld op 0.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/5b21b7af>
* _ACP2E-3475_: De uitvoer van het product veroorzaakt OOM zelfs met 4G geheugengrens
   * _nota van de Reparatie_: Vorig aan deze moeilijke situatie, ontbrak de productuitvoer als de productattributen duizenden optiewaarden zelfs met 4G beschikbaar geheugen hadden. Na deze correctie moet het exportbestand van het product het CSV-bestand hebben geëxporteerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>

### Importeren/exporteren, prestaties

* _ACP2E-3476_: [ de invoertijd van het Product van de Wolk ] is beduidend gestegen
   * _nota van de Reparatie_: Vorig aan de moeilijke situatie, de invoer van het catalogusproduct met meer dan 10K ingangen had een significante tijddegradatie. Na de correctie wordt het importeren van het catalogusproduct tijdig uitgevoerd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/87d012e5>

### Installeren en beheren

* _AC-13242_: De verbetering van Magento ontbreekt op MariaDB 11.4 + 2.4.8-bèta1
   * _Bevestig nota_: De verbetering zou zonder enige fout moeten gebeuren.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7b336d0a>

### Inventaris/MSI

* _ACP2E-3335_: Onbekwaam om de orde te verschepen wanneer MSI ophaalopslag wordt toegelaten
   * _Nota van de Reparatie_: Verbeterde inventarisprestaties van creeer het verschepen in het geval van vele bronnen met in-store bestelwagen
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/9f3e63d1>
* _ACP2E-3355_: De Cron herdex ontbreekt om productbeschikbaarheid op frontend bij te werken
   * _nota van de Reparatie_: Eerder, bleven de Producten uit voorraad op het front na het bijwerken van de backorderstatus door REST API. Nadat u de status van de backorder hebt bijgewerkt via de REST API, worden de producten weergegeven als in voorraad.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/e6fe0aa7>
* _ACP2E-3357_: Het toevoegen van beelden aan configureerbaar niet werkend wanneer MSI wordt toegelaten.
   * _nota van de Reparatie_: Het beeld uploadt voor configureerbaar product zal nu zoals verwacht werken wanneer de inventarismodule wordt gebruikt. Eerder werkte het uploaden van de afbeelding niet
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/fdf409aa>

### Inventaris/MSI, zoeken

* _ACP2E-3413_: Alle producten worden geïndexeerd met [ is_out_of_stock ] = 1 wanneer SKU niet als onderzoekbaar attribuut wordt geplaatst
   * _nota van de Reparatie_: Na de moeilijke situatie, is &quot;is_out_of_stock&quot;in de index van het catalogusonderzoek correct, zelfs wanneer de huid niet doorzoekbaar is.
   * _GitHub codebijdrage_: <https://github.com/magento/inventory/commit/5b21b7af>

### Volgorde

* _ACP2E-3311_: [ de Wolk ] kan orde in admin op één opslag tot stand brengen als slechts het Standaard het Factureren Adres niet opstelling was
   * _Bevestig nota_: Nu relevant foutenmelding &quot;een klant met het zelfde e-mailadres bestaat reeds in een bijbehorende website.&quot; wordt getoond als een klant geen Standaard het Factureren Adres heeft en probeert om een orde op een andere opslag tot stand te brengen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d75cff27>
* _ACP2E-3416_: Admin gedupliceerde verzonden verzoeken van de plaatsorde
   * _nota van de Reparatie_: Eerder, kon de &quot;Submit knoop van de Orde&quot;in het admin paneel veelvoudige tijden worden geklikt of door herhaaldelijk te drukken &quot;binnengaan&quot;sleutel, veroorzakend dubbel of ordebijdragen met fout. Nu, verhinderend extra acties tot de orde volledig wordt verwerkt, die ervoor zorgen dat slechts één orde wordt voorgelegd.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/5184c067>
* _ACP2E-3425_: Admin kan orde zelfs zonder betalingsmethode nog plaatsen
   * _nota van de Reparatie_: Eerder geselecteerde betalingsmethode wordt nu behouden wanneer de betalingsmethode in de lijst van beschikbare betalingen opnieuw verschijnt.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d50f6b5d>

### Bestelling, betalingen

* _ACP2E-3233_: Admin kan orde zelfs zonder betalingsmethode nog plaatsen
   * _nota van de Reparatie_: Eerder, kon de handelaar orden van het admin paneel plaatsen zonder een betalingsmethode te selecteren. Nu is de handelaar verplicht een betalingsmethode te gebruiken om een bestelling te plaatsen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/fd5cf3af>

### Overige

* _LYNX-426_: Het disconto_percentage wordt niet berekend voor bundelproducten met dynamische prijs
* _LYNX-485_: De producten van de bundel tonen nog &quot;IN_STOCK&quot;wanneer één van zijn gebundeld product uit voorraad
* _LYNX-486_: not_available_message en only_x_left_in_stock toont niet de zelfde beschikbare voorraad
* _LYNX-488_: original_row_total gebied die onjuiste waarde terugkeren
* _LYNX-503_: De gegroepeerde productduimnagel zou volgens de configuratie moeten worden getoond     .
* _LYNX-510_: Fout wanneer het vragen selected_options in OrderAddress
* _LYNX-512_: original_item_price is exclusief kortingen
* _LYNX-530_: Het niet beschikbare bericht toont niet de beschikbare inventarishoeveelheid
* _LYNX-532_: &quot;OUT_OF_STOCK&quot;statuswinst op Eenvoudig met de producten van douaneopties met multi-uitgezochte opties
* _LYNX-533_: Fout (GQL): cart.itemsV2.items.product.custom_attributesV2 keert een serverfout terug
* _LYNX-536_: orden/date_of_first_order altijd terugkerend ongeldig
* _LYNX-544_: De klant moet niet een gedeeltelijk verscheepte orde kunnen annuleren
* _LYNX-548_: De codes van de fout voor orde annuleren die op het foutenbericht wordt gebaseerd
* _LYNX-581_: Beweeg terug koekjesgerelateerde eigenschappen van privé aan beschermde

### Andere ontwikkelaarsgereedschappen

* _AC-12731_: CSP kwesties die met dev/css/use_css_Critical_path worden gecombineerd
   * _nota van de Reparatie_: Het systeem laadt nu correct CSS dossiers asynchroon op controlepagina&#39;s, zelfs wanneer &quot;dev/css/use_css_critical_path&quot;wordt toegelaten, die ervoor zorgen dat deze pagina&#39;s met de juiste CSS stijlen worden teruggegeven. Eerder werd met een beperkt inhoudsbeveiligingsbeleid (CSP) voorkomen dat inline JavaScript werd uitgevoerd, waardoor CSS-bestanden niet naar behoren werden geladen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39020>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39040>
* _AC-13398_: Gebruikend virtueel type om stop te vormen, kan de interceptormethode niet correct in opstelling worden geproduceerd :di: compileert bevel
   * _nota van de Reparatie_: Het systeem produceert nu correct interceptormethodes wanneer het gebruiken van een virtueel type om een stop te vormen, die verenigbare resultaten verzekeren of precompiled of runtime. Voorheen zou het systeem onjuiste resultaten genereren wanneer vooraf werd gecompileerd in vergelijking met de compilatie bij uitvoering.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/33980>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38141>
* _ACP2E-3441_: Onbekwaam om dossiers van de Collector van Gegevens te downloaden
   * _nota van de Reparatie_: Het downloaden van steun toont niet meer lege pagina in plaats van het downloaden van het dossier.

### Betalingen

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

* _AC-11932_: De StandaardKwestie van de Montages van de Attributen van het Product
   * _nota van de Reparatie_: Het systeem staat nu gebruikers toe om een standaardoptie voor een productattribuut te schrappen, die ervoor zorgen dat de attributen niet altijd een standaardreeks hebben. Eerder, toen een gebrek voor een productattribuut werd geplaatst, was er geen manier om het te schrappen, resulterend in de attributen altijd een standaardreeks.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38703>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13471_: Steun voor CommandLoaderInterface van Symfony in Magento CLI
   * _Bevestig nota_: Deze verandering vermindert initialisatietijd van Magento CLI app door uitgestelde initialisering van bevelen toe te staan tot zij nodig zijn.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/29266>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/29355>

### Product

* _wisselstroom-13173_: [ 3} Het type van de Oplossing van de kwestie {in blok PHPDoc]
   * _nota van de Reparatie_: Het systeem verwijdert nu correct een onbekende referenced variabele in PHPDoc voor de veranderlijke verklaring $helper, die codeduidelijkheid en nauwkeurigheid verbetert. Voorheen veroorzaakte deze onbekende variabele waarnaar in PHPDoc wordt verwezen, verwarring en potentiële onnauwkeurigheden in de code.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38961>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38940>
* _AC-13423_: [ Uitgave ] Vaste gebroken Bundel en downloadbare productpagina&#39;s lay-out in Magento >= 2.4.7
   * _nota van de Reparatie_: De lay-out voor bundel en downloadbare productpagina&#39;s is bevestigd, die een verenigbare en correcte vertoning over alle apparaten verzekeren. Eerder traden op deze pagina&#39;s lay-outproblemen op als gevolg van een herschikking van het mediablok met productinformatie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/39403>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/6cfb9b6b>
* _ACP2E-3471_: [ de Producten van de Wolk ] in Categorie - voeg Producten toe - wijs - Uitgezocht allen toe
   * _nota van de Reparatie_: De gebruikers kunnen producten nu selecteren of schrappen gebruikend de knevel.

### Aanbieding

* _ACP2E-3139_: De Regel van de verkoop met het attribuut van de Stap van de Korting van het Aantal (koop X) veroorzaakt dat andere regels niet worden toegepast
   * _Bevestig nota_: De prijsregel van de Kar annuleert eerder toegepaste regels niet als de hoeveelheid van het product in de kar niet genoeg voor toe te passen regel is.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/d01ee51e>
* _ACP2E-3331_: De kwestie van prestaties op de prijsregel van de Kaart - de module van de Regel van de Verkoop van de Vooruitgang
   * _nota van de Reparatie_: Toegevoegde ontbrekende indexen van DB voor filters AdvancedSalesRule
* _ACP2E-3332_: De verkoopregels van de uitgave met Vaste korting van het bedrag en &quot;De Maximale Korting van de Aantal wordt toegepast op&quot;
   * _nota van de Reparatie_: Vaste kwestie met de korting van de kartregels, wanneer de vaste waardekorting wordt gevormd om op een beperkte hoeveelheid producten worden toegepast is het karretje. Eerder werd de waarde &quot;Maximale korting op de hoeveelheid toegepast op&quot; gebruikt voor de berekening van de prijs van het lopende item in het winkelwagentje, niet alleen voor de berekening van de korting op de regel.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
* _ACP2E-3342_: [ CLOUD ] de verbetering van Magento veroorzaakte coupons om case-sensitive te worden
   * _nota van de Reparatie_: Vóór de moeilijke situatie moest u in de couponcode precies typen aangezien het met inachtneming van hoofdletters of kleine letters werd gevormd. De coupon wordt nu gevalideerd op de achtergrond, ongeacht de configuratie van code in hoofdletters of kleine letters.
* _ACP2E-3349_: De regels van de wagen &quot;Vaste korting van het bedrag voor het volledige karretje&quot;  Met Actie worden kortingen onjuist toegepast
   * _nota van de Reparatie_: De codes van de coupon zullen behoorlijk ongeacht hogere geval of kleine letters, wanneer gebruikt in ordeverwezenlijking van het admin gebied worden bevestigd. De waardeboncode werd eerder niet gevalideerd als deze niet precies overeenkomt met het hoofdlettergebruik van de code van de geconfigureerde tekenregel.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/581b7ef1>
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
* _ACP2E-3498_: Onjuiste disconteringswaarde wanneer de veelvoudige regels van de kartprijs gelijktijdig met gedisconteerde/speciale geprijsde producten worden toegepast
   * _nota van de Reparatie_: Voorafgaand aan de moeilijke situatie, werd het vaste bedrag voor de volledige kartregels niet behoorlijk toegepast als meer dan één werd toegepast. Nu worden de regels voor kortingen op vaste bedragen correct toegepast.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1984c61c>

### Retourneert

* _ACP2E-3330_: [ CLOUD ] Beperkte admin gebruikers kunnen het terugkeermenu en de knopen zien
   * _nota van de Reparatie_: De beperkte gebruikers Admin hebben nu geen toegang tot RMA verwante controles (menu en knopen).
Eerder beperkte admin-gebruikers konden het retourmenu en de knoppen zien.
* _ACP2E-3443_: Het Scherm van de terugkeer wordt verduisterd wanneer verfrist het scherm
   * _Bevestig nota_: De gebruiker kan de pagina verfrissen zonder het schermvervorming te ervaren.

### Verkoop

* _AC-13750_: Het Grote Totaal en het totaal van de basis grote niet aanpassen met de stappen van het testresultaat
* _AC-13751_: De tweede Regel van de Prijs van de Kar wordt niet toegepast als de Eerste regel van de Kar reeds wordt toegepast

### Zoeken

* _AC-13053_: Het krijgen &quot;ga een onderzoekstermijn in en probeer opnieuw.&quot; fout bij geavanceerd zoeken van pagina in winkel 2.4.8-bèta1
   * _nota van de Reparatie_: Het systeem toont nu correct onderzoeksresultaten op de Geavanceerde pagina van het Onderzoek wanneer een productattribuut aan &quot;Nr&quot;wordt geplaatst. Als u eerder een productkenmerk instelt op &quot;Nee&quot; en een zoekopdracht uitvoert, verschijnt het foutbericht &quot;Voer een zoekterm in en probeer het opnieuw.&quot;
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/3ea26621>
* _AC-13721_: magento/module-open-onderzoek hangt van nonexistent op openssearch-php tak af
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/05dc0bbf>
* _ACP2E-3362_: search_query lijst wanneer van enorme grootte, heeft grote invloed op de frontend van de ladingstijd
   * _nota van de Reparatie_: De verbeterde tijd van de de paginalading van de onderzoekslijst. Vóór de correctie werd de pagina met zoeklijsten vertraagd vanwege een niet-geoptimaliseerde query.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>

### Beveiliging

* _ACP2E-3273_: ReCaptcha V2 toont verkeerd bij kassa voor het Duits
   * _nota van de Reparatie_: Eerder recaptcha van onder e-mailadres van checkout verschijnen unstyled voor talen met lange woorden, zoals duits. Hierna ziet de rechaptcha er hetzelfde uit als alle elementen van de rest van de gebieden.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7377de59>
* _ACP2E-3300_: Captcha op admin login vereist geen interactie voor sommige gebruikers
   * _nota van de Reparatie_: ReCaptcha voor admin login wordt bevestigd zoals verwacht

### Verzending

* _wisselstroom-12938_: De &quot;zandbak&quot;van UPS en &quot;prod&quot;opstellingsinstructieupdates in devdoc
* _ACP2E-3340_: Het Spoor FedEx API van FedEx werkt niet met de geloofsbrieven van REST
   * _nota van de Reparatie_: Eerder integratie FedEx vereiste geen extra API sleutels voor het Volgen API. Er is nu een nieuwe configuratie toegevoegd ter ondersteuning van het bijhouden van API-sleutels.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>
* _ACP2E-3354_: [ de Wolk ] FedEx onderhandelde Tarieven niet op REST teruggekeerd
   * _nota van de Reparatie_: Vorig aan de moeilijke situatie, FedEx rekeningsspecifieke tarieven waar niet verzonden op de reactie, zelfs door volgens documentatie FedEx zij zouden moeten worden verzonden. Na de correctie worden de specifieke tarieven van de rekening verzonden op de reactie door het verzoek van onze kant te veranderen.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/55615e61>

### Staging en voorvertoning

* _ACP2E-3453_: Onbekwaam om Geplande Update bij te werken wanneer het Gebruiken van Uniek Attribuut van de Categorie van de Douane
   * _nota van de Reparatie_: Vaste een kwestie waar het bijwerken van een geplande update voor een categorie niet mogelijk was als de categorie een uniek attribuut had
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>

### Belasting

* _ACP2E-3193_: De Vaste Belasting van het Product (FPT) werkt niet met configureerbare producten
   * _nota van de Reparatie_: FPT voor configureerbare productvariaties die behoorlijk werken.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/ec7e32a9>

### Testkader

* _AC-13362_: [ vraag ] de correctietelling van PHPDoc
   * _nota van de Reparatie_: Het systeem erkent nu correct vervangen methodes in IDEs toe te schrijven aan een spelcorrectie in PHPDoc. Eerder heeft een spelfout in de PHPDoc ertoe geleid dat IDE&#39;s bepaalde methoden niet herkennen als afgekeurd.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/31399>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/31398>
* _AC-13478_: MAGETWO-95118: Het controleren van gedrag met het blijvende het winkelwagentje nadat de zitting is verlopen
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/7d5e3906>
* _AC-13716_: De tests van de integratie zijn ontbroken Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission
* _ACP2E-3458_: [ MFTF ] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest
   * _Bevestig nota_: Vaste mftfs
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/078c387e>

### UI Framework

* _AC-12432_: Het Gebied van het Dossier van de Component van UI
   * _nota van de Reparatie_: Het systeem bevestigt nu correct het dossiergebied in een UI componentenvorm, die de vorm toestaat om zonder fout worden voorgelegd wanneer een dossier wordt geselecteerd. De validatie zou eerder mislukken, zelfs als een bestand was geselecteerd, zodat het formulier niet kon worden verzonden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38908>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/39004>
* _AC-12645_: [ geef ] Verbeterde datumformaat in js console uit: schakelaar van 12 uur aan 24 uur van..
   * _Nota van de Reparatie_: Verbeterde datumformaat in js console: schakelaar van 12 uur aan 24 uur
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38983>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38972>
* _AC-12650_: [ geef ] toe voeg bronMap generatie voor minder dossiers op ontwikkelaarwijze toe
   * _nota van de Reparatie_: Het systeem produceert nu bronkaarten voor minder dossiers wanneer op ontwikkelaarwijze, makend het gemakkelijker om de bron van een stijl te identificeren. Eerder, was het identificeren van de bron van een stijl uitdagend toen het runnen van het systeem op ontwikkelaarwijze met server-kant minder compilatie.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/38982>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38977>
* _AC-13459_: Het inconsistente Gedrag in &quot;Voorraad&quot;Sorterend met Minimumdrempel van de Voorraad
   * _nota van de Reparatie_: Het systeem sorteert nu correct producten in de catalogus die op voorraadniveaus wordt gebaseerd, die de vastgestelde Minimum Drempel van de Beeld volgen en zich uit-van-voorraadpunten aan de bodem van de lijst constant bewegen. Eerder was het sorteergedrag inconsistent, waarbij items niet altijd in de juiste volgorde werden weergegeven op basis van hun voorraadniveau, en wijzigingen in sorteren kunnen onvoorspelbaar optreden na het opslaan, vernieuwen of wijzigen van de categoriehiërarchie.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/47b448e2>
* _AC-13472_: Suggestie voor betere fout die voor require.js ladingsproblemen meldt
   * _nota van de Reparatie_: Deze PR verbetert het foutenbericht wanneer de vereisten er niet in slagen om een component te laden.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/36761>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/38971>
* _AC-9168_: [ Uitgave ] verwijdert onnodige samenvatting van manuscriptoverzicht
   * _nota van de Reparatie_: Het systeem optimaliseert nu de tijd van de paginalading door onnodige manuscripten van JavaScript uit de classificatiesectie te verwijderen, in plaats daarvan het gebruiken van gealigneerde CSS stijlen voor een efficiëntere en leesbare code. Eerder kon het gebruik van JavaScript-scripts voor de classificatiesectie de laadtijd van de pagina mogelijk vertragen.
   * _GitHub kwestie_: <https://github.com/magento/magento2/issues/37776>
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/pull/34643>
* _ACP2E-3367_: De Kopbal van de Plaats | Speciale tekens die het welkomstgedeelte van de klant doorbreken
   * _nota van de Reparatie_: Na de moeilijke situatie, worden de speciale karakters correct getoond in de klant welkome sectie.
   * _GitHub codebijdrage_: <https://github.com/magento/magento2/commit/1366ae5e>
