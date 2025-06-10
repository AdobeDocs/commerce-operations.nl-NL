---
source-git-commit: 21da8a0133c3c70c2c37851aca79e2d5d8f82905
workflow-type: tm+mt
source-wordcount: '27937'
ht-degree: 0%

---
# Opgeloste problemen in Adobe Commerce (v2.4.8)

## Opgeloste problemen in v2.4.8

We hebben 581 problemen opgelost in de Adobe Commerce 2.4.8-kerncode. Hieronder wordt een subset van de opgeloste problemen in deze release beschreven.

### API&#39;s

* __/V1/transactions REST API retourneert een fout wanneer parent_txn_id = txn_id__
Het systeem behandelt nu correct de ouder en kindconcepttransacties waar identiteitskaart van de oudertransactie het zelfde als transactieID is, die een oneindige lijn verhinderen wanneer het vragen van het /V1/transacties REST API eindpunt. Eerder zou dit scenario resulteren in een fatale fout als de maximale uitvoeringstijd wordt overschreden.
  _AC-10042 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1bafc571)_
* __[Grafiek ] Uitgave van het Type in 2.4.7__
Het systeem verwerkt nu correct gehele getallen in de functie GetCustomSelectedOptionAttributes wanneer een GraphQL-query wordt uitgevoerd, waardoor aan het type gerelateerde fouten worden voorkomen. Eerder resulteerde het lanceren van een vraag van GraphQL die GetCustomSelectedOptionAttributes met een geheelargument gebruikte in een typefout.
  _AC-11878 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38662) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38663)_
* __Speciale karakters in categorie url_key (wanneer gecreeerd via REST API)__
Eerder in categorie_url_key is er geen speciaal teken nadat de correctie een speciaal teken in categorie_url_key heeft getoond
  _AC-3223 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35577) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c699c206)_
* __REST API geeft orders van een andere website weer. __
Het systeem ondersteunt nu bereik geoorloofde toegang voor REST API-beheertokens en Magento_Sales-eindpunten, zodat de REST-API alleen orders weergeeft waartoe beheerders toegang hebben. Eerder gaf de REST API opdrachten van alle websites weer, ongeacht de toegewezen website van de beheerder.
  _ACP2E-2703_
* __Uitgave met rest api na toelaat 2FA Duo__
2FA met Duo-beveiligingsoptie genereert nu de juiste handtekening voor de Rest API
  _ACP2E-2755 - [ de codebijdrage van GitHub ](https://github.com/magento/security-package/commit/412fa642)_
* __[REST API ]: De Standaardwaarde van het gebruik in opslagmening blijft niet gecontroleerd na het toevoegen van configuraties voor een configureerbaar product__
De kwestie is opgelost door correcte gegevensbestandingangen voor de klantgerichte opties voor een non-default opslag te verzekeren. Het selectievakje voor de aangepaste opslag in de sectie &quot;Beheer > Catalogus > Product Bewerken > Aanpasbare opties&quot; is eerder uitgeschakeld omdat de database niet correct is, zelfs als de titel van de optie voor de aangepaste opslag gelijk bleef aan de standaardwinkel.
  _ACP2E-2927 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3056e9cb)_
* __REST API kan verzoeken met schuine streep (/) in SKU wanneer het gebruiken van Oauth1__
Voorafgaand aan de correctie kon u geen succesvolle API vraag voor een product maken dat &quot;/&quot; in zijn SKU had. Nu, kunt u een succesvolle API uitgeven krijgt verzoek om productdetails alhoewel zijn SKU een voorwaartse schuine streep in het heeft.
  _ACP2E-2969 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b21e5d91)_
* __het adresupdate die van de Klant ontbreekt wanneer het bijwerken door REST API als &quot;validateDefaultAddress&quot;toegelaten__
Het API-eindpunt functioneert nu naar behoren nadat het probleem met de id-sleutel die ontbreekt in de API-payload is opgelost.
  _ACP2E-3079 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9af794a4)_
* __[Wolk ] Creërend de Dubbele groep van de de prijsklant van de websitegroep in Prijzen Api van de Rij.__
Nu staat de Rest Api van de Prijs van de Reeks niet toe om de Dubbele prijsgroep van de websitegroep van de klant te creëren.
Eerder was het mogelijk om de prijsgroep voor de websitegroep Dupliceren te maken in Tier Prices Api die de validatie in Admin tijdens het opslaan van het product niet zou doorstaan.
  _ACP2E-3091 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/148c3ead)_
* __kan orde geen commentaar met status via REST API toevoegen__
Het probleem is opgelost door de wijziging in de status van de volgorde toe te staan als deze alleen uit het huidige frame afkomstig is. Eerder voldeed het niet aan de ordestatus en voorkwam het wijzigingen in een orderstatus, zelfs niet als deze van dezelfde status afkomstig was.
  _ACP2E-3130 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/93d50f8d)_
* __verrichting Async ontbreekt wanneer SKU van de nuttige lading__ mist
Async- en synchronisatiebewerkingen zijn eerder mislukt als gevolg van fouten bij het opslaan van het product. Na de correctie mislukken de async en synchronisatieproduct de verrichtingen van de steunAPI met relevant uitzonderingsbericht.
  _ACP2E-3236 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/66dea0de)_
* __[CLOUD ] Onbekwaam om de basis-prijzen bij te werken gebruikend REST API (de waarde van &quot;value_id&quot;in &quot;catalog_product_entity_decimal&quot;wordt niet correct verhoogd.)__
Eerder bij deze vaststelling, toen rustapi /rest/default/V1/products/base-pricing werd aangeroepen, werd de verhogingsid ten onrechte verhoogd, waardoor er een kloof tussen de waarden overbleef. Na de correctie wordt de increment id verhoogd, incrementeel. Ook het value_id-veldbereik is vergroot.
  _ACP2E-3376 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d50f6b5d)_
* __de punten van de Orde zijn niet zichtbaar in creditmemo e-mails voor API POST V1/order/:orderId/teruggave__
Eerder, vóór deze correctie, wanneer een klant een creditnota van een API verzoek creeert die send_email op de hoogte brengt, bevat het niet het net van de productdetails. Na deze correctie stuurt de klant een API-aanvraag voor creditnota en zoekt hij naar de gegevens van het product die in de e-mail worden weergegeven.
  _ACP2E-3460 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3f12d152)_
* __De Standaardwaarden worden niet geplaatst voor datum en tijdattributen met producten RestAPI__
Standaardwaarden worden nu correct ingesteld voor datum- en datum- en tijdkenmerken via RestAPI
  _ACP2E-3486 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1984c61c)_

### API&#39;s, winkelwagentje en kassa

* __Kritieke 500 Fout: Magento\Framework\Webapi\Exception Verwant aan Accepteer de Kopbal van HTTP__
Na de correctie doet het er niet toe om de header Accepteren op te geven.
  _ACP2E-3343 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1366ae5e)_

### API&#39;s, GraphQL

* __geen graphQl beschikbaar voor het intekenen van de Punten van de Terugkeer voor klant__
Eerder aan de moeilijke situatie, kon het attribuut van de klant beloning_warning_notification niet door de mutatie van GraphQL en de vraag van de Rest API worden bijgewerkt. Nu kan het zelfde als klantenattribuut worden bijgewerkt beloning_update_notification.
  _ACP2E-3348_

### API&#39;s, GraphQL, Tax

* __zowel Luma (Rest API) als Grahql berekent geen belastingen wanneer slechts de code van het ZIP wordt verstrekt.__
Het systeem berekent nu de belastingen correct wanneer alleen een postcode wordt geleverd, zodat er nauwkeurige belastingramingen zijn voor zowel Luma (Rest API) als GraphQL. Voorheen werden alleen verzendramingen berekend en werden geen belastingen opgenomen wanneer alleen een postcode werd verstrekt.
  _AC-12060_

### Account

* __het adresvorm van de Klant staat willekeurige code op de naamgebieden__ toe
Het systeem valideert nu de invoer in de velden Voornaam en Achternaam in het adresformulier van de klant, waardoor het gebruik van willekeurige code wordt voorkomen. Eerder stond het systeem het gebruik van willekeurige code in deze gebieden toe zonder een fout te werpen.
  _AC-10782 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38331) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38345)_
* __update van het Wachtwoord van admin.__
  _AC-10886 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38352) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/4bca5dfe)_
* __mijn rekening voegt adresneerstorting toe sparen__
Het systeem bewaart nu correct klantenadressen zelfs wanneer het gebiedgebied niet wordt getoond, verhinderend een neerstorting tijdens het sparen proces. Als u eerder een adres probeert toe te voegen of te bewerken zonder veld voor een weergegeven gebied, treedt er een uitzonderingsfout op.
  _AC-10990 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38406) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38407)_
* __Redirect lijn wanneer URL hoofdletters heeft__
Het systeem zet nu automatisch hoofdletters in URLs in kleine letters om, die een herleidingslijn verhinderen wanneer het toegang tot van de homepage. Eerder, zou het hebben van karakters in hoofdletters in Veilige Basis URL een ononderbroken omleidingslijn veroorzaken wanneer het proberen om tot de homepage toegang te hebben.
  _AC-11718 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38538) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38539)_
* __middlename (&#39;s) niet bewaard voor gastrekeningen__
Het systeem bewaart nu correct de middelste naam voor gastrekeningen tijdens controle, die het in het e-mailmalplaatje toegankelijk maken. Eerder werd de middelste naam niet opgeslagen in de prijsopgave en was deze niet toegankelijk in de e-mailsjabloon voor gastaccounts.
  _AC-11755 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38593) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39067)_
* __Admin: De Knopen van de Acties van de pagina drijven links in plaats van recht__
Het systeem richt nu correct de Knopen van de Acties van de Pagina aan de rechterkant van de kleverige kopbal in het admin paneel, die de professionele blik en het gevoel verbeteren. Eerder zweven deze knoppen onjuist naar de linkerkant van de kleverige koptekst.
  _AC-11919 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38701) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/44cef3a9)_
* __`dev:di:info`error in magento 2.4.7__
Het systeem geeft nu correct constructorparameters weer wanneer de opdracht `dev:di:info` wordt uitgevoerd, zodat geen fouten meer optreden. Eerder resulteerde het uitvoeren van deze opdracht in een fout als gevolg van een niet-overeenkomend type in het argument.
  _AC-11999 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38740) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Login als klant opt-in checkbox niet vertaalbaar__
Op het systeem kunnen nu de velden &quot;Aanmelden als klant aanmelden&quot; en &quot;Aanmelden als klant&quot; worden ingesteld in het bereik van de &quot;Winkelweergave&quot;, zodat vertalingen voor verschillende winkelweergaven mogelijk zijn. Eerder werden deze velden alleen ingesteld in het bereik &quot;Website&quot;, zodat vertalingen voor afzonderlijke winkelweergaven niet konden worden vertaald.
  _AC-13000 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32329) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32359)_
* __Voorste eind UI Homepage in mijn profiel Dropdown is knoop niet daar.(af en toe)__
  _AC-14299_
* __Klant wordt het programma geopend maar het tonen van 404 fout in front-end.__
De storefront klantendashboardpagina laadt nu zoals verwacht wanneer een klant zich aanmeldt. Eerder konden klanten zich aanmelden, maar op deze pagina werd een fout van 404 weergegeven. [ GitHub-35838 ](https://github.com/magento/magento2/issues/35838)
  _AC-6071 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35838) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36263)_
* __niet in staat om de attributeninformatie van de Klant in Admin te bewaren geeft klantensectie uit;__
De opslag-id van de klant wordt nu correct geïmplementeerd per websitebereik voor het bewerkingsformulier voor de beheerder.
  _ACP2E-2791 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/488c1034)_
* __[de Wolk ] kan geen klant via API tot stand brengen wanneer de Privé Verkoop wordt toegelaten__
Klanten kunnen nu worden gemaakt door geverifieerde gebruikers van beheerders en met geverifieerde integratietoken via REST api wanneer websitebeperking is ingeschakeld.
  _ACP2E-3115_
* __na het programma openen, zijn de producten die aan de vergelijkingslijst als gastgebruiker worden toegevoegd niet zichtbaar.__
Producten die aan product werden toegevoegd vergelijken lijst alvorens het programma te openen als klant nu worden bewaard na het programma openen.
Eerder waren de producten die als gastgebruiker aan de vergelijkingslijst werden toegevoegd, na het aanmelden niet zichtbaar.
  _ACP2E-3329 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_
* __staat de configuratieoorzaken van Landen in de configuraties van het klantenadres toe__
Nu het selecteren van toestaat de configuratie van Landen beïnvloedt geen landen die voor buiten het bepaalde werkingsgebied worden getoond. Eerder toestaan de configuratie van Landen beïnvloedde klantenadresattributen buiten bepaald werkingsgebied
  _ACP2E-3433 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_
* __Gedeelde Registratie van het Cadeautje toont de gebeurtenisdatum zoals 1 dag vroeger__
Cadeauregisterdatum wordt nu correct weergegeven in de winkel
  _ACP2E-3445_
* __VAPT: De Fout van de Bedrijfs logica - toekomstige datum als klantengeboortedatum__
De geboortedatum van de klant kan niet later worden ingesteld dan vandaag
  _ACP2E-3501 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d4de4726)_

### Account, API&#39;s, GraphQL

* __Klant API - Login ontbreekt Aantal niet om aan 0 na succesvolle Login te herstellen__
Nu wordt het mislukkingsaantal teruggesteld aan nul in de lijst van de klantenentiteit na succesvolle login door API eindpunten.
  _ACP2E-3246 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ec7e32a9)_

### Account, beheerinterface, B2B

* __Beperkte admin gebruikers kunnen niet altijd douane gedeelde catalogi__ zien
Beperkte beheergebruikers kunnen nu consistent klanten en alle gedeelde catalogi waaraan de producten zijn toegewezen, weergeven en beheren, op voorwaarde dat zij toegang hebben tot de specifieke opslag. Eerder, kon een beperkte admin gebruiker met toegang tot een bepaalde opslag niet altijd alle gedeelde catalogi zien waaraan de producten werden toegewezen of konden klanten zien die niet konden sparen, leidend tot inconsistenties in het systeem.
  _ACP2E-3038 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7377de59)_

### Account, winkelwagentje en Afhandeling

* __&quot;uitgezocht&quot;attribuut van het douaneadres van de klant geeft niet voor nieuw klantenadres terug__
  _AC-2341 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/34950)_

### Gebruikersinterface van beheerder

* __[Uitgave ] voegt toestemmingscontrole voor &quot;herlaad gegevens&quot;gegevensknoop__ toe
Het systeem bevat nu een machtigingencontrole voor de knop &quot;Gegevens opnieuw laden&quot;, zodat deze alleen wordt weergegeven en toegankelijk is voor gebruikers met de juiste machtigingen. Eerder was de knop &quot;Gegevens opnieuw laden&quot; zichtbaar en klikbaar voor alle gebruikers. Dit leidde tot een pagina &quot;niet toegestaan&quot; wanneer gebruikers zonder de vereiste machtigingen op deze pagina hadden geklikt.
  _AC-10705 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38283) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38279)_
* &rbrack; Inconsistente etiketten van 0&rbrace; kwestie &lbrace;voor attributen in marketing regels __Het systeem vult nu correct de labels consistent in voor categorie- en kenmerkopties in de regel van de winkelwagenprijs__&lbrack;
  _AC-11427 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/31232) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/31231)_
* __de bevestiging van Gegevens is succes en de knoop van de Invoer is aanwezig tijdens de producten van de Invoer met het gedrag van de Vervangen__
Het systeem valideert nu correct gegevens en verbergt de knop &quot;Importeren&quot; tijdens het importeren van het product met het gedrag &quot;Vervangen&quot;, waardoor onbedoelde gegevensvervanging wordt voorkomen. Eerder heeft het systeem de gegevens onjuist gevalideerd en de knop Importeren weergegeven. Dit leidt tot mogelijke inconsistenties in de gegevens.
  _AC-11588 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0574ac23)_
* __[Bug ] Magento 2.4.7 staat geen productfoto met de uitbreiding van het hoofdletterdossier toe.__
Het systeem accepteert nu het uploaden van productafbeeldingen met bestandsextensies met hoofdletters, zodat het product probleemloos kan worden gemaakt. Eerder werd het uploaden van afbeeldingen met bestandsextensies voor hoofdletters geweigerd, waardoor gebruikers gedwongen werden de bestandsextensie te wijzigen in kleine letters.
  _AC-12167 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38831) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c8f87c25)_
* __Verborgen dropdown in netten met uitgezochte actie (b.v. Inhoud > Elementen > Pagina&#39;s)__
Het systeem is nu allemaal gelijkaardige dropdown voor alle rasters hersteld.
  _AC-12319 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38891) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39371)_
* &rbrack; Waarschuwing van de Reparatie van 0&rbrace; Uitgave __&lbrack;: Onbepaalde seriesleutel &quot;filters&quot;__
Het systeem behandelt nu scenario&#39;s waar een nieuwe gebruiker nog niet met referenties heeft gecommuniceerd, verhinderend een ongedefinieerde &quot;filters&quot;waarschuwing van de seriesleutel wordt geregistreerd. Deze waarschuwing zou eerder worden geregistreerd als een nieuwe gebruiker geen interactie had gehad met bladwijzers.
  _AC-13131 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39013) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38996)_
* __de invoer van het Product csv- dossier met speciale karakters ontbreekt toe te schrijven aan codeveranderingen in Validate.php- dossier__
Het systeem valideert en importeert nu CSV-bestanden van producten die speciale tekens bevatten, zodat de gegevensoverdracht kan worden voltooid. Als u voorheen een CSV-bestand met speciale tekens importeerde, treedt er een fout op, waardoor het importproces niet meer kan plaatsvinden.
  _AC-13529 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __wanneer het Max Aantal Verzoeken van het Terugstellen van het Wachtwoord&quot;groter dan 0 b.v. wordt geplaatst: 3, &quot;worden de overschrijdende berichten van de beperkingsfout verzonden alvorens de grens te bereiken i.e van tweede tijd__
  _AC-13767_
* __Alhoewel het Max Aantal Verzoeken van het Terugstellen van het Wachtwoord&quot;aan 0 wordt geplaatst (getelegrafeerd), &quot;worden de overschrijdende berichten van de beperkingsfout verzonden van 2de keer&quot;__
  _AC-13768_
* __Er is geen rode asterisk voor verplicht gebied van het telefoonaantal__
Eerdere rode asterisk wordt niet weergegeven voor telefoonnummer, maar voor telefoonnummer  Telefoonnummer was verplicht. Dit is nu een vast rood sterretje dat op telefoonnummer als een verplicht veld kan worden weergegeven.
  _AC-13850 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c699c206)_
* __in Admin wanneer wij proberen om te herschikken verzend ordeknoop is niet klikbaar. (af en toe)__
  _AC-14300_
* __[Uitgave ] plaats standaardindexeerderwijze aan &quot;programma&quot;__
Alle nieuwe indexen worden standaard weergegeven in de modus **[!UICONTROL Update by Schedule]** .  Eerder was de standaardmodus **[!UICONTROL Update on Save]** . Dit heeft geen invloed op bestaande indexen. [ GitHub-36419 ](https://github.com/magento/magento2/issues/36419)
  _AC-6975 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36419) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0b410856)_
* &rbrack; het veranderingslijsten van de indexeermachine van de 1&rbrace; uitgave __&lbrack;op mening unsubscribe__
Het systeem verwijdert nu automatisch ongebruikte wijzigingstabellen wanneer een index wordt overgeschakeld van &#39;update op schema&#39; naar &#39;bijwerken bij opslaan&#39;, waarbij de index als ongeldig wordt gemarkeerd zodat geen items worden overgeslagen. Als een index eerder werd overgeschakeld op &#39;bijwerken bij opslaan&#39;, blijven wijzigingstabellen die niet worden gebruikt in het systeem behouden en worden alle gewijzigde indexen &#39;geldig&#39; gemarkeerd.
  _AC-7700 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/29789) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/25859)_
* __Geen verbinding aan het verschepen wanneer in betalingen in controle in mobiele telefoonmening__
Het systeem zorgt er nu voor dat de titels/koppelingen &quot;Verzending&quot; en &quot;Controleren en betalen&quot; altijd boven op de pagina in de weergave voor mobiele apparaten worden weergegeven, zodat gebruikers eenvoudig tussen de stappen kunnen navigeren en de benodigde correcties kunnen aanbrengen. Eerder waren deze titels/koppelingen verborgen in de mobiele weergave, waardoor het voor gebruikers moeilijk was om hun huidige stap te kennen of terug te gaan naar vorige stappen.
  _AC-7962 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36856) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36982)_
* __klant geeft de vraagverzendcommentaren van de Bestellingen opdracht created_at is teruggekeerd in +0 timezone niet in opslag gevormde timezone__
Het systeem toont nu correct het &quot;created_at&quot;gebied van ladingscommentaren in gevormde tijdzone van de klant wanneer het gebruiken van de vraag van de Orden van de klant. Eerder, werd het &quot;created_at&quot;gebied getoond in +0 timezone, ongeacht de gevormde timezone van de klant.
  _AC-8109 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36947) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37642)_
* __i18n:verzamelen-zinnen breken de integriteit van vertalingen__
De opdracht `bin/magento i18n:collect-phrases -o` verzamelt nu correct nieuwe zinnen uit JavaScript- en HTML-bestanden en voegt deze toe, zodat de vertalingen op de juiste wijze in het vertaalbestand worden weergegeven. Eerder was het systeem er niet in geslaagd om meerregelige vertaalzinnen uit JavaScript-bestanden en woordgroepen uit .phtml-bestanden op te nemen in het vertaalbestand, wat leidde tot onvolledige of onjuiste vertalingen.
  _AC-9843 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Uitgave van de Toestemming voor de toegang tot van Dynamisch Blok__
Eerder voor beperkte admin die een nieuw dynamisch blok toevoegde veroorzaakte een fout. Na het implementeren van deze fix kan beperkte admin het dynamische blok toevoegen en het blok zonder fout bewerken
  _ACP2E-2687_
* __apostrof in de naam van de opslagmening wordt vervangen door &#039;__
De filters van de de opslagmening van het net tonen nu behoorlijk apostroffen
  _ACP2E-2787 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38395) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/39d54c2d)_
* __Favicon uploadt ontbreekt om .ico- dossiers__ te bevestigen
De bestandsvalidatiefout is bijgewerkt naar &quot;Bestandsvalidatie mislukt. Controleer de instellingen voor afbeeldingsverwerking in de winkelconfiguratie.&quot; Eerder was dit gewoon &quot;Bestandsvalidatie mislukt.&quot;
  _ACP2E-2847 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/39d54c2d)_
* __Galerij in PageBuilder toont oude beeldduimnagel in plaats van onlangs geüploade beeld__
Regenereer voorvertoningen van afbeeldingen voor afbeeldingen die zijn verwijderd en opnieuw met dezelfde naam zijn geüpload via de mediagalerie in de inhoud van de paginaontwikkelaar.
  _ACP2E-2957 - [ GitHub codebijdrage ](https://github.com/magento/magento2-page-builder/commit/60140cd2) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/001e5188)_
* __Opgeslagen product door admin gebruiker met verschillende rolwerkingsgebied overschrijft/schrapt bestaande Verwante productinformatie in het product__
Eerder, vóór de moeilijke situatie, werden de verwante producten teruggesteld en werden leeg wanneer de secundaire admin gebruiker op sparen knoop klikte zonder in verwant product te veranderen. Na deze correctie klikt de secundaire gebruiker op de knop Opslaan en wordt het product niet opnieuw ingesteld en opgeslagen.
  _ACP2E-2978 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3056e9cb)_
* __Onbekwaam om meer dan 200 orden uit te voeren__
De servergrenzen voor de verzoekgrootte van eerder voorgelegde geselecteerde IDs zijn genegeerd door het HTTP- verzoek van GET in POST te veranderen om de kwestie te bevestigen. Eerder werd het probleem aangetroffen vanwege serverbeperkingen voor de grootte van GET-verzoeken.
  _ACP2E-3033 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/93d50f8d)_
* __het bericht van de de paginasevalidering van de controleverklaring onjuist.__
Als een vereist veld leeg blijft, zoals &quot;adres&quot;, wordt het bericht niet weergegeven bij de validatie aan de serverzijde. De clientvalidatie zorgt ervoor dat het vereiste foutbericht wordt weergegeven met de tekst &quot;Dit is een verplicht veld&quot;. Eerder werd het bericht &quot;adres is required&quot; weergegeven als een vereist veld leeg was, naast het validatiebericht aan de clientzijde.
  _ACP2E-3037 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9af794a4)_
* __het terugstellen van het Wachtwoord malplaatjekwestie met Admin gebruiker__
Het probleem is opgelost met de juiste sleutel, die nu de gebruikersnaam voor de beheerder in de e-mailsjabloon bevat en het onderwerp correct invult. Eerder was het probleem het gevolg van een verouderde sleutel die werd gebruikt.
  _ACP2E-3125 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/93d50f8d)_
* __Dubbele slashes in klantensegment URL__
Dubbele schuine strepen verschijnen niet in URL wanneer de &quot;Filter van het Terugstellen&quot;in het net wordt geklikt.
  _ACP2E-3149 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/8459b17d)_
* __COD is niet beschikbaar voor toegestane specifieke landen__
Nu is de levering onder rembours beschikbaar voor bepaalde landen wanneer dat nodig is en   AC-3216 werkt zoals verwacht.
  _ACP2E-3171 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6f4805f8)_
* __kan Aangepaste gecreeerde status van de Orde niet bijwerken__
&#39;We kunnen nu aangepaste orderstatussen bijwerken, terwijl eerder de status alleen gewijzigd kon worden als de huidige status &#39;verwerkings&#39; of &#39;fraude&#39; was.
  _ACP2E-3178 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38659) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/8459b17d)_
* __de het verschepen adresstaat is niet auto het bijwerken__
Voorafgaand aan de correctie was het gebied met het verzendadres (of regio-id) niet synchroon met de gegevens over de adresfacturering. Nu worden zowel het verzendadres als de regio-id correct bijgewerkt wanneer het factuuradres wordt gewijzigd.
  _ACP2E-3294 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/581b7ef1)_
* __de knoop van het Terugstellen werkt niet bij Add/geeft admin gebruiker__ uit
Eerder werkte de knoop van het Terugstellen niet op Add/uit Admin Gebruiker pagina. Nu werkt de knop Herstellen in het deelvenster Beheer onder Systeem -> Machtigingen -> Alle gebruikers correct op de pagina Admin-gebruiker toevoegen/bewerken.
  _ACP2E-3364 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/5184c067)_
* __Magento admin URL verpletterend verkeerde opsporing en fouten CORS__
Na de moeilijke situatie, als het douane admin domein een subdomein van het belangrijkste domein is, is admin toegankelijk slechts van gevormde subdomain.
  _ACP2E-3373 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37663) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/3f12d152)_
* __Gebroken bevestiging voor &quot;Maximale hoeveelheid die in het Winkelen van Kar wordt toegestaan&quot;__
Eerder, toen wij `Maximum Qty Allowed in Shopping Cart` leeg zetten, gaf het geen uitzondering, hoewel een lege waarde hier niet wordt goedgekeurd. Nadat deze correctie is toegepast, genereert het plaatsen van een lege tekenreeks uitzonderingen en wordt het opslaan van het product niet meer toegestaan.
  _ACP2E-3392 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d50f6b5d)_
* __[Uitgave UI van de Voorproef van de Bouwer van de Pagebuilder ] de knopen in de kolom van de Bouwer van de Pagina worden niet correct opgesteld__
De knoppen in de kolommen van de Page Builder zijn nu op de juiste wijze uitgelijnd. Eerder waren ze verkeerd uitgelijnd in de kolommen van de Page Builder.
  _ACP2E-3408 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/1a52ef4c)_
* __Geordende Producten rapport voert niet uit. 404 fout.__
Producten volgden rapportuitvoer naar CSV en XML werkt nu zoals verwacht
  _ACP2E-3431 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/88660e79)_
* __TinyMCE JS Fout in console na Js minification laat met productiemodus toe__
Als u in het beheerdeelvenster de miniatuur van JavaScript in de productiemodus inschakelde, werden JavaScript-fouten met betrekking tot TinyMCE 6 in de browserconsole weergegeven, wat van invloed was op de functionaliteit en gebruikerservaring. Dit probleem is nu opgelost en zorgt ervoor dat TinyMCE 6 probleemloos werkt zonder fouten te genereren, zelfs als JS-minificatie is ingeschakeld.
  _ACP2E-3457 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/56463d5e)_
* __Verzoek om extra veranderingen om ACS2E-3375 moeilijke situatie volledig te voltooien__
&#39;-
  _ACP2E-3459 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Automatisch toelatend van nieuwe ACL toestemmingen__
De nieuwe toestemmingen die aan douanemodules worden toegevoegd zullen niet meer automatisch toegang tot alle bestaande gebruikersrollen verlenen tenzij uitdrukkelijk gevormd.
  _ACP2E-3503 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3f12d152)_
* __het Rapport van de Gebruiker van het Logboek van Acties Admin toont geen details voor adminhtml_user_delete__
Met adminhtml_user_delete worden nu belangrijke details op de juiste manier geregistreerd. Eerder zijn geen logbestanden gegenereerd voor verwijderingen door gebruikers.
  _ACP2E-3509 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/4de008a9)_
* __Regel van het begin met het verschepen voorwaarde die niet wanneer het plaatsen van orde van admin van toepassing is__
Eerder, als de regel van de kartprijs een het verschepen methodekorting met de coupon heeft, kan het niet via Admin UI worden toegepast. Nadat deze correctie is toegepast, wordt de korting op de winkelprijregel met een coupon voor een specifieke verzendmethode toegepast vanuit de interface van Admin.
  _ACP2E-3536 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a52ff98f) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/11ce816b)_
* __[FRESH ] de code van de HEX werkt niet correct in STAAL__ bij
De HEX-code die handmatig door de gebruiker wordt ingevoerd in de kleurkiezer voor het visuele staal, wordt niet meer gewijzigd door het systeem. Voorheen werden bepaalde HEX-codes enigszins aangepast als gevolg van omzettingsfouten tussen kleurmodellen.
  _ACP2E-3559 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/344fce23) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/1ef984c0)_

### Admin UI, B2B

* __B2B Login als kopbal van de Klant heeft nog Magento branding__
Eerder staat in de koptekst van de winkel &quot;U bent nu verbonden als &lt;naam klant> op &lt;naam winkel>&quot; met Magento-branding. Deze is nu gefixeerd en de header wordt weergegeven met ADOBE-branding.
  _AC-13628 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/96dec499)_

### Beheerdersinterface, catalogus

* __kan geen posities voor de categorieproducten in de toegestane website als beperkte admin gebruiker veranderen__
Een beperkte beheerder toestaan om producten toe te voegen en te sorteren onder een categorie in de hoofdcategorie die is toegewezen onder een beperkte website.
  _ACP2E-2708_

### Admin UI, Payment/Payment Methods, Order

* __Vergunning van de transactie niet die in het Lusje van de Transactie na de Slimme Orde van de Knoop van PayPal__ wordt getoond
Het systeem geeft nu correct de transactievergunning weer op het tabblad Transactie nadat een bestelling is geplaatst met de Smart Button van PayPal. Eerder werd de transactie voor autorisatie niet weergegeven op het tabblad Transactie nadat werd geklikt op de knop &quot;Autoriseren&quot; en werd geen nieuwe transactie van het type &quot;Autorisatie&quot; gemaakt.
  _AC-13520 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/6cfb9b6b)_

### Beheerdersinterface, prestaties

* __na update aan 2.4.5-p8 komen 500 fouten voor wanneer het creëren van orde van admin__
Eerder kon bij het inschakelen van HTML-miniatuur geen bestelling van de beheerder worden geplaatst. Nu HTML is ingeschakeld, kan de bestelling van de beheerder met succes worden geplaatst.
  _ACP2E-3169 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b21e5d91)_

### Admin-gebruikersinterface, verzenden

* __Het aantal couponcodes wordt niet bijgewerkt in het dialoogvenster   De kolom &quot;Gebruikte tijd&quot; in het tabblad Codes voor coupons beheren als een bestelling wordt geplaatst met meerdere verzendingen.__
Eerder, toen een order met meerdere verzendingen werd geplaatst, werkte het aantal couponcodes niet bij in de kolom &quot;Gebruikte tijd&quot; op het tabblad Codes voor coupons beheren. Nu wordt het juiste aantal weergegeven in zowel de &quot;Gebruikte tijd&quot; die de gewenste waarden weerspiegelt bij verzending via meerdere kanalen.
  _ACP2E-2519 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/4745100c)_

### Beheerdersinterface, Staging en Voorvertoning

* __[de Wolk ] het Verwijderen van malplaatje met ontbrekende beelden veroorzaakt dat het Web/de media worden geschrapt__
Eerder bij deze correctie werd de map pub/media verwijderd als de naam van de voorvertoning van een pagebuildersjabloon ontbreekt. Na de correctie wordt alleen de sjabloon verwijderd en de voorvertoning indien gevonden.
  _ACP2E-3424 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/0986853b)_

### Analyse/rapportage

* __Google Analytics CSP Fout https://region1.analytics.google.com__
Het systeem staat nu correct verbindingen met &#39;https://region1.analytics.google.com&#39; toe wanneer Google Analytics is ingeschakeld, waardoor CSP-fouten (Content Security Policy) worden voorkomen. Voorheen zou het inschakelen van Google Analytics en het bekijken van de website vanuit de EU leiden tot fouten in de CSP-console als gevolg van een weigering om verbinding te maken met &#39;https://region1.analytics.google.com&#39;.
  _AC-9922 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37750) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38991)_
* __het Rapport van de Vooruitgang werkt niet__
Het systeem steunt nu de generatie van de Gegevensdossiers van de Vooruitgang van Rapportering voor extra grote datasets door rapporten in partijen van 10.000 te laden en te schrijven. Eerder, kon de Geavanceerde module van de Rapportering gegevensdossiers voor extra grote datasets niet produceren, veroorzakend &quot;MySQL server is weggegaan&quot;fouten tijdens de uitvoering van de analytics_collect_data bouwbaan.
  _ACP2E-2570 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a12063bd)_
* __Admin Bestelde de kwesties van het de datumbereik van het Rapport van Producten.__
De gebruiker zal om het even welke datum van het bevolen productrapport kunnen selecteren. Eerder, na een lijst verfrist zich, zal het selecteren van &quot;VAN&quot;datum &quot;aan&quot;datum terugstellen.
  _ACP2E-3080 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6f4805f8)_
* __Onjuiste curl kopballen die `newrelic:create:deploy-marker` maken het niet werken__
Het systeem maakt nu curl-koppen correct op, zodat de opdracht `newrelic:create:deploy-marker` een implementatiemarkering kan maken in New Relic. Eerder, verhinderden de onjuiste curl kopballen de verwezenlijking van een plaatsingsteller in New Relic.
  _ACP2E-3096 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37641) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/6a185204)_
* __GTM ontbrekende gebeurtenis addToCart in dataLayer voor configureerbaar product met douaneoptie__
Eerder werd de gebeurtenis addToCart niet geactiveerd voor configureerbare producten. Nu, wordt de gebeurtenis behoorlijk toegevoegd aan de GTM dataLayer variabele.
  _ACP2E-3146_
* __NewRelic browser die inlineJS manuscript controleert veroorzaakt CSP fouten__
De manuscripten van de Controle van de Browser NewRelic worden nu ingespoten door de toepassing in plaats van de agent APM voor naleving van CSP (het Beleid van de Veiligheid van de Inhoud). Eerder waren de scripts van NewRelic Browser Monitoring die door de APM-agent werden geïnjecteerd, niet compatibel met CSP en leidden deze ertoe dat de scripts niet werden uitgevoerd.
  _ACP2E-3183 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/66dea0de)_
* __de vragen van het TUSSENVOEGSEL aan de sales_bestsellers_aggregeerde_daily lijst worden langzaam op project met groot volume van de verkooporde__
Voorheen zouden de beste verkopers die dagelijks verslag hadden opgesteld, veel tijd nodig hebben om een groot aantal geplaatste orders te genereren. Nu wordt het verslag tijdig opgesteld.
  _ACP2E-3189 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7377de59)_
* __de rapporten van de Orde die het verkeerde muntsymbool tonen__
Het valutasymbool voor orderbedragen in het orderrapport is onjuist ontleend aan valuta/opties/basis. Het is nu gecorrigeerd om valuta/opties/gebrek voor nauwkeurige rapportering te gebruiken.
  _ACP2E-3276 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/fd5cf3af)_
* &rbrack; Onjuiste Berekeningen van de Wolk __&lbrack;&lbrace;in het Rapport van het Gebruik van de Coupon__
Het totale verkoopbedrag in het raster van het couponrapport wordt nu correct berekend door zowel het &quot;Discount Tax Compensation Amount&quot; als het &quot;Shipping Discount Tax Compensation Amount&quot; op te nemen. Voorheen ontbraken deze bedragen in de berekening, wat leidde tot verschillen tussen het totaal van de verkopen en de gegevens van de verkooporder.
  _ACP2E-3302 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d75cff27)_
* __Kwesties met gedeelde &quot;&lt;project_id>/var/tmp&quot;__
De tijdelijke dossiers van DataExport van de Analytics zullen de sys tmp folder gebruiken, die geschikter voor frequente toegang en veranderingen is. Om botsingen te vermijden in het geval dat de veelvoudige instanties op de zelfde server lopen, werd de weg tmp bijgewerkt om unieke identiteitskaart van een instantie te gebruiken
  _ACP2E-3339 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4cf5e62)_

### Analyse/rapportage, B2B

* __B2B - sitemap omvat producten/categorieën niet die aan Gedeelde Catalogus__ worden toegewezen
Beperk de sitemap gegenereerde categorieën en producten tot de categorieën en producten die alleen zijn toegewezen aan de openbare gedeelde catalogus en/of de machtigingsinstellingen voor de cataloguscategorie.
  _ACP2E-2300 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ea79f7dd)_

### Analyse/rapportage, cloud

* __Magento verwerpt de meeste New Relic kroontransacties #34108__
AC rapporteert correct de aan taken gerelateerde transacties aan NewRelic. Voorheen zouden sommige aan een uitsnijdtaak gerelateerde transacties als &quot;OtherTransaction/Action/unknown&quot; in Northern Rock worden weergegeven
  _ACP2E-3067 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/35b1b1da)_
* __Metrisch in NR zou voor achtergrondtransacties misleidend kunnen zijn - Follow-up van ACS2E-3067__
Voor achtergrondtransacties (uitsnijden) wordt de New Relic-toepassingsnaam gebruikt die is gedefinieerd in de configuratie-instellingen
  _ACP2E-3187 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ec7e32a9)_

### B2B

* __2.4.8-beta102 de uitgave van de pakketonderneming ontbreekt met toepassingsuitzonderingen__
  _AC-13501_
* __Producten die aan gedeelde catalogus worden toegewezen zijn niet op het vooreind wanneer de gedeeltelijke index wordt uitgevoerd__
Producten die via REST API aan een gedeelde catalogus zijn toegewezen, zijn nu direct zichtbaar in de winkel nadat de gedeeltelijke indexering is voltooid. Eerder waren de producten pas zichtbaar na een volledige herindexering.
  _ACP2E-2139 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7377de59)_
* __[de vertoning van de Wolk ] Prijs in mobiele en Desktopversie niet het zelfde in &quot;Mijn citaten&quot;__
Ongewenste Inclusief BTW-regel wordt niet meer weergegeven in Aanhalingstekens voor onderhandeling wanneer de totale catalogusprijs wordt uitgedeeld.
  _ACP2E-2873_
* __Onnoodzakelijke grenzen op de Mijn sectie van Orden__
Eerder werd een extra container (ordeverwijzingen) gecreeerd die extra CSS klassen toepaste, die onnodige grenslijnen veroorzaakte die onder het ordeaantal binnen de Mijn sectie van Orden verschijnen, die nu niet zichtbaar is.
  _ACP2E-3044 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9af794a4)_
* __sales_clean_quotes cron schrapt citaten van aan nog goedgekeurde kooporden__
Aanhalingstekens die nu in inkooporders worden gebruikt, worden niet verwijderd door salesschone_aanhalingstekens voor snijtaak
  _ACP2E-3247 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/581b7ef1)_
* __de knoop van de Orde van de Plaats verdwijnt in de details van de Orde van de Aankoop__
Probleem verholpen waarbij de knop Plaatsingsorder verborgen was voor goedgekeurde inkooporders terwijl een productvariant een minimumaantal creditcards had opgegeven. Dit probleem is nu opgelost.
  _ACP2E-3465_
* __[CLOUD ] Geen dergelijke entiteit met identiteitskaart = 0 met b2b module__
Aangemeld door gebruiker kan product aan winkelwagentje toevoegen wanneer de functie Gedeelde catalogus is ingeschakeld.
Eerder toegevoegd product aan winkelwagentje resulteerde in Fout &#39;geen dergelijke entiteit met id = 0&#39;
  _ACP2E-3474_
* __Geen foutenmelding die voor onze van voorraadproducten wordt getoond wanneer bulk het toevoegen van de lijst van de Vereiste__
Vóór de correctie werd een succesbericht weergegeven, ongeacht het aantal producten dat niet aan de wagen kon worden toegevoegd. Er worden nu afzonderlijke berichten weergegeven voor producten die zijn toegevoegd aan de winkelwagentje en voor producten die zijn mislukt.
  _ACP2E-3562_
* __kwestie met de Updates van SKU na Geplande Updates die Onjuiste Toestemmingen van het Product veroorzaken (-2 ontkennen)__
Als u de SKU van een product wijzigt met in het verleden geplande updates, is het product niet langer toegankelijk voor klanten met een gedeelde catalogus die het product mogen zien.
  _ACP2E-3628_

### B2B, catalogus

* __Producten/Categorieën zichtbaar tijdens re-dexatie wanneer het gebruiken van Toestemmingen NoDDL en van de Categorie__
Vermijd dat de categorieën en de inhoud van de categorieën waarvoor beperkingen gelden, worden weergegeven bij het indexeren van catalogusmachtigingen.
  _ACP2E-2860_

### B2B, Kader

* __Filtrerend het Net van het Bedrijf &amp; toen het Poging van de Uitvoer van het Net CSV zal ontbreken &amp; de Uitzondering van de Drijg__
Het systeem staat nu succesvolle uitvoer CSV van de gegevens van het net van Bedrijven in het admin paneel toe, zelfs wanneer de filters zoals &quot;Uitstaand Saldo&quot;en &quot;Bedrijfstype&quot;worden toegepast. Eerder, zou het toepassen van bepaalde filters en het proberen om de netgegevens uit te voeren in een mislukking resulteren en een uitzondering die wordt geworpen.
  _AC-9607 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/44cef3a9)_

### B2B, GraphQL

* __[Wolk ] Onbekwaam om custom_attributes te plaatsen terwijl de gemeenschappelijke verwezenlijking over de grafische vraag__
Na de moeilijke situatie, is het mogelijk om het &quot;custom_attributes&quot;attribuut voor bedrijfadmin tijdens bedrijfverwezenlijking te plaatsen gebruikend grafisch verzoek.
  _ACP2E-3391_

### Braintree

* __Admin uitdrukkelijk checkout knoop wordt onbruikbaar gemaakt.__
  _AC-14293_
* __Betaal via LPM__
Het systeem rendert nu correct de Methoden van de Lokale Betaling (LPM) bij aanvankelijke lading, zelfs wanneer de het verschepen en facturerings adressen van een aangemelde klant niet aanpassen, die een vlot afhandelingsproces verzekeren. Eerder, zou een wanverhouding tussen het verschepen en het facturerings adres van een klant LPM verhinderen teruggeven, veroorzakend potentiële verstoringen tijdens het afrekenen.
  _BUNDLE-3367_
* __configureerbaar met Virtueel als Product van het Kind__
Het systeem staat nu expresbetaalmethoden toe voor configureerbare producten met een virtueel onderliggende product, waardoor een soepel afrekeningsproces mogelijk is. Eerder waren expresbetalingsmethoden niet beschikbaar toen een configureerbaar product met een virtueel onderliggend product aan de winkelwagentje werd toegevoegd.
  _BUNDLE-3368_
* __De mislukte fout van de Verificatie CVV__
  _BUNDLE-3369_
* __het vaulteren via de Kwesties 247 van het rekeningsgebied__
Het systeem stelt klanten nu in staat om nieuwe creditcardgegevens of PayPal-accountgegevens op te slaan op meerdere websites zonder fouten in de autorisatie. Voorheen konden klanten geen nieuwe betalingsmethoden opslaan op verschillende websites en kregen ze een foutbericht over hun autorisatie te zien.
  _BUNDLE-3370_
* __verschepen aan een adres van een verschillend land__
Het systeem staat nu toe dat transacties zonder fouten worden verwerkt wanneer ze naar een adres uit een ander land worden verzonden, zodat een soepel afrekeningsproces mogelijk is. Eerder, zou het proberen om aan een adres van een verschillend land te verzenden in consolefouten, ondanks geen zichtbare fouten op de frontend resulteren.
  _BUNDLE-3371_
* __Kaart van de Krediet - de functie van de Onderbreking__
Het systeem handelt nu correct de afbraak van Braintree PayPal-componenten af wanneer een klant teruggaat van de betalingspagina naar de verzendpagina, om fouten te voorkomen en ervoor te zorgen dat PayPal Express-knoppen correct worden weergegeven. Eerder was het navigeren van de verzendpagina vanaf de betalingspagina soms een fout bij het afbreken van de Braintree PayPal-componenten.
  _BUNDLE-3372_
* __Verzendcallback voor Uitdrukkelijke PayPal__
Het systeem geeft nu correct de beschikbare verzendmethoden weer in het model PayPal Express, waarmee klanten hun voorkeursverzendmethode kunnen selecteren voordat ze naar de controlepagina gaan of hun transactie voltooien. Eerder waren er geen verzendmethoden beschikbaar om uit te kiezen in het PayPal Express-modaal, waardoor klanten een verzendmethode moesten selecteren op een aparte controlepagina voordat ze hun transactie konden voltooien.
  _BUNDLE-3373_

### Bundel

* {het berichtaantal van de Fout van de Bevestiging van de Bundel van 0} Storefront meer dan 1 __Het systeem geeft nu slechts één foutbericht weer wanneer op de knop Toevoegen aan winkelwagentje wordt geklikt zonder dat opties voor een gebundeld product worden geselecteerd.__ Eerder gaf het systeem meerdere foutmeldingen weer voor validatie voor elk niet-geselecteerd selectievakje.
  _AC-10826 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/3ea26621)_
* __de Uitzondering van Magento die in sommige orde verwante testgevallen wordt geworpen__
Het systeem verwerkt nu correct de stap &#39;sendGuestPaymentInformation&#39; in verschillende testgevallen, zodat Magento-uitzonderingen niet meer worden gegenereerd. Voorheen deden deze uitzonderingen zich voor als gevolg van een null-betalingsmethode, wat in verschillende testgevallen tot mislukkingen leidde.
  _AC-13321_

### Winkelwagentje en Afhandeling

* __Uitzondering wordt niet behoorlijk behandeld terwijl het toevoegen van een product aan kar in de vergelijkingsproductpagina__
Het systeem behandelt nu behoorlijk uitzonderingen wanneer het toevoegen van een product aan de kar van de vergelijkingsproductpagina, die een bericht van de berichtmanager in het controlemechanisme toont. Eerder zou een uitzondering ertoe leiden dat een JSON-gecodeerde pagina wordt geretourneerd in plaats van correct te worden afgevangen en afgehandeld.
  _AC-10660 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38200) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38257) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0c53bbf7)_
* __GTag verzendt geen transactieprijzen en totalen.__
Het systeem verzendt nu correct transactieprijzen en totalen naar Google Tag wanneer GTag wordt toegelaten, die nauwkeurige het volgen van e-commercegegevens verzekeren. Eerder werd de valuta onjuist verzonden als onderdeel van de &quot;alle&quot; bestellingen, in plaats van te worden gekoppeld aan de afzonderlijke bestelling.
  _AC-10698 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37348) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37504) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37349)_
* &rbrack; [ Uitchecken ] van het 0&rbrace; Uitgave richtlijnen die in ontbroken betalings e-mailmalplaatje worden bijgewerkt __Het systeem laat nu correct het verzendadres en de verzendmethode van de mislukte betalings-e-mailtemplate voor virtuele producten weg, zodat alleen relevante informatie in de e-mail wordt opgenomen.__&lbrack; Eerder bevatte het niet-betaalde e-mailbericht voor virtuele producten het verzendadres en de verzendmethode onjuist.
  _AC-11641 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32781) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32511)_
* __Magento 2 login binnen de controle met bestaande klant geeft consolefout in browser Firefox__
Het systeem staat nu gebruikers toe om zich tijdens het controleproces aan te melden zonder enige consolefouten in browser Firefox te ontmoeten. Eerder, zou het proberen om zich aan te melden als bestaande klant tijdens controle in een consolefout in Firefox resulteren.
  _AC-11717 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38557) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39509)_
* &rbrack; de regressie van de Regels van de Verkoop van 0&rbrace; kwestie &lbrace;in 2.4.7 __Het systeem valideert nu correct de verkoopregels, waardoor de toepassing van een couponcode op een winkelwagentje wordt voorkomen als de productvoorwaarde niet overeenkomt met een productnaam.__&lbrack; Voorheen kon een verkoopregel worden toegepast en een korting op het verzendbedrag worden gegeven, zelfs als de productvoorwaarde niet overeenkomt met een productnaam.
  _AC-11876 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38671) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0574ac23)_
* &rbrack; CartFixed berekening van de regel van de Verkoop 0&rbrace; Uitgave __: onjuiste disconteringsbedrag
Het systeem berekent nu correct het kortingsbedrag voor verkoopregels met vaste winkelbedragen, zodat nauwkeurige kortingen worden toegepast ongeacht wijzigingen in winkelartikelen.__&lbrack; Eerder kon het kortingsbedrag verkeerd variëren wanneer winkelwagentjes werden gewijzigd, wat soms tot aanzienlijk grotere kortingen leidde dan verwacht.
  _AC-11914 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38694) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/581b7ef1)_
* __[Uitgave ] de loader blokkeert de verschepende methodes nadat postcode wordt veranderd, de regels van de het bevestigen van rentetarieven__
Het systeem verwerkt aangepaste verzendmethoden nu correct zonder validatieregels voor verzendtarieven, zodat de lader de verzendmethoden niet blokkeert nadat de postcode in het verzendadres is gewijzigd tijdens het afrekenen. Als de postcode in het verzendadres tijdens de afhandeling werd gewijzigd, zou de lader eerder de verzendmethoden blokkeren en niet verdwijnen als er aangepaste verzendmethoden werden gebruikt zonder de validatieregels voor de verzendkosten.
  _AC-11993 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38742) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1bafc571)_
* __de codeeigenschap van de coupon werkt niet behoorlijk in de controlepagina op Magento 2.4.7__
Het systeem schakelt nu het veld voor de kortingscode/coupon-invoer op de uitcheckpagina voor virtuele en downloadbare producten in, zodat gebruikers de kortingscodes kunnen toepassen zoals verwacht. Eerder was de invoer van de kortingscode/coupon uitgeschakeld en werd de tekst van de knoptitel weergegeven als &quot;coupon annuleren&quot;, zodat gebruikers geen kortingscodes konden toepassen.
  _AC-12170 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38826) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1bafc571)_
* __de voorwaarden checkbox van voorwaarden staat HTML op storefront niet toe__
Het systeem biedt nu ondersteuning voor HTML-opmaak in het selectievakje Voorwaarden en bepalingen in de winkel, zodat u de instellingen beter kunt aanpassen en leesbaar kunt maken. Eerder werd de tekst van het selectievakje weergegeven als normale tekst, waarbij HTML-tags werden genegeerd.
  _AC-12479 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __de prijsregel van de Kar die voor het programma geopende gebruiker wordt gecreeerd krijgt verkeerd toegepast voor niet het programma geopende gebruiker__
Het systeem verwijdert nu correct de regel van de kartprijs voor aangemelde gebruikers wanneer zij automatisch uit wegens koekjesafloop worden geregistreerd, die ervoor zorgt dat de korting niet op niet-geregistreerde gebruikers wordt toegepast. Eerder, werd de regel van de kartprijs nog toegepast zelfs toen de gebruiker uit het programma werd geopend, resulterend in een onjuiste korting die op niet-geregistreerde gebruikers wordt toegepast.
  _AC-12541 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38944) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7d5e3906)_
* &rbrack; [ VAN DE VEREDELING ] De optimalisering van de Prestaties grote het winkelwagentjes door te verhinderen... __Het systeem optimaliseert nu de prestaties voor grote winkelwagentjes door dubbele getActions-aanroepen te voorkomen, waardoor de snelheid en efficiëntie van winkelwagentbewerkingen worden verbeterd.__&lbrack; Eerder werd voor een winkelwagentje met meerdere items de functie getActions meerdere keren aangeroepen, waardoor de prestaties van het systeem werden vertraagd.
  _AC-13302 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39292) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39290)_
* __Cadeauregistratieproduct toont niet behoorlijk__
  _AC-13797_
* __Cadeauregistratieproduct toont niet behoorlijk__
  _AC-13841_
* __Vertaling BTW in adresrenderer__
Het systeem staat nu voor de vertaling van de tekst &quot;BTW&quot;, &quot;T&quot;, &quot;F&quot;in adresrenderers toe, toelatend gebruikers om deze termijnen in de specifieke taal van de opslag te vertalen. Eerder waren deze termen niet vertaalbaar, waardoor gebruikers gedwongen werden een tijdelijke oplossing te kiezen.
  _AC-8103 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36942) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36943)_
* __dubbele orden met zelfde Identiteitskaart van het Citaat tezelfdertijd met weinig tijdverschil__
Het probleem waarbij Adobe Commerce-klanten dubbele orders tegenkwamen die met dezelfde QuoteID waren geplaatst, is opgelost.
  _ACP2E-2055 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f89a447e)_
* __Persistent die winkelwagentje tijdens checkout stap wordt ontruimd__
Als u na de correctie de betalingsmethode selecteert tijdens het afrekenen terwijl u zich niet hebt aangemeld, wordt de permanente sessie niet beëindigd.
  _ACP2E-2470 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4fbf702)_
* __opnieuw rangschikt voegt niet toegewezen product aan kar__ toe
Eerder, voor de verschillende opslagproducten kunnen van de andere opslag worden geordend. Nadat deze correctie is toegepast, kan alleen dezelfde store worden gebruikt, kan hetzelfde bereikproduct opnieuw worden geordend wanneer het delen van de klantenaccount is ingeschakeld
  _ACP2E-2518 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f89a447e)_
* __in admin, wordt het &quot;Shopping Kart&quot;op linkerkant niet bijgewerkt wanneer het selecteren van de punten en &quot;Beweging aan het Schepen Kar&quot;van de rechterkant__
De &quot;Winkelwagentje&quot; aan de linkerkant wordt bijgewerkt wanneer u de items selecteert en &quot;Verplaatsen naar winkelwagentje&quot; aan de rechterkant in de bestuurderszijde. Eerder werkte deze functionaliteit niet omdat de getransformeerde winkelwagentjes niet leeg werden tijdens de sessie.
  _ACP2E-2620 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/39d54c2d)_
* __[de Regel van de Verkoop van de Wolk ] wordt niet toegepast op eerste orde van Multi die__
Na de correctie wordt de korting correct weergegeven voor elke volgorde van hetzelfde meervoudige aanhalingsteken.
  _ACP2E-2646 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f89a447e)_
* &rbrack; De parallelle verzoeken van de productie van de wolk __&lbrack;om het zelfde product aan het resultaat van de kunst in twee afzonderlijke punten in de steunAPI van de Kunst toe te voegen__
Het systeem verwerkt nu correct veelvoudige parallelle verzoeken om het zelfde product aan de kar in één enkel lijnpunt toe te voegen, verhinderend de verwezenlijking van afzonderlijke lijnpunten voor zelfde SKU. Eerder zou het doen van parallelle verzoeken om hetzelfde product via de REST-API aan het winkelwagentje toe te voegen, resulteren in meerdere regelitems voor dezelfde SKU.
  _ACP2E-2664 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f89a447e)_
* __Uitgave met het Opdracht geven van de Registratie van het Cadeautje Magento 2.4.4 Onderneming/Commerce__
Het probleem waardoor de succesvolle aankoop van een product uit een cadeauregister onmogelijk werd, is opgelost, zodat bestellingen kunnen worden geplaatst en het cadeauregister op de juiste wijze kan worden bijgewerkt. Er is eerder een fout opgetreden bij het plaatsen van een bestelling in een register met cadeaus, waardoor de aankoop niet kon worden voltooid.
  _ACP2E-2676 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35432)_
* __het Krijgen Onbekwaam om het koekje te verzenden. Grootte van &#39;mage-messages&#39; tijdens het opnieuw ordenen__
Het opnieuw ordenen proces zal nu geen eigen fouten genereren. Het object is afhankelijk van ingebouwde controles van winkelwagentjes.
  _ACP2E-2704 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ba25af8a)_
* __Standaard verschepend adres wordt niet geselecteerd bij controle__
Het standaardverzendadres wordt nu geselecteerd voor een gebeurtenis in de context van een toegelaten adreszoekopdracht.
  _ACP2E-2798 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7e0e5582)_
* __[CLOUD ] grafisch addProductsToCart API kwestie met douaneoptie__
GraphQL voegt hetzelfde product met verschillende aangepaste opties toe aan de juiste poort
  _ACP2E-2897 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c971859e)_
* &rbrack; Verwante de Regels van de Producten van de Wolk __&lbrack;niet werkend wanneer het veranderen van de opslagmening__
Het probleem is opgelost door te bevestigen dat de aangepaste eigenschapswaarde is ontvangen op de pagina met winkelwagentjes. Eerder, werd het niet behoorlijk gehaald wanneer het schakelen tussen opslag op de winkelwagentje pagina.
  _ACP2E-2917_
* __Veelvoudige adressen die aan de rekening worden toegevoegd wanneer controle als nieuwe klant__
Het systeem slaat nu een nieuw klantenadres slechts eenmaal op als de orde om niet kon worden gecreeerd, verhinderend de verwezenlijking van veelvoudige identieke adressen in het geval van de fouten van de orderplaatsing. Eerder, zou het systeem een nieuw adres bewaren telkens als een bestelling plaatsingspoging werd gemaakt, ongeacht of de orde met succes werd gecreeerd of niet.
  _ACP2E-2923 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/001e5188) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/2ebcef39)_
* __het opnieuw ordenen van klantenorde via de vorm van de gastorde resulteert een leeg kart__
Eerder, toen het plaatsen van een herschikking door de Orders en Keert pagina terug, werd de klant opnieuw gericht aan de login pagina. Nadat deze correctie is toegepast, wordt de geregistreerde klant correct omgeleid naar de pagina Winkelwagentje weergeven wanneer een nieuwe order wordt geplaatst. De stroom werkt het zelfde als gastklanten.
  _ACP2E-3004 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6a185204)_
* __Admin Gebruiker met de beperkte Middelen van de Rol niet kunnen bekijken het Vormen Warten__
Voorheen kon de beperkte beheerder het verlaten winkelwagentje niet zien van het beheerpaneel voor een bijbehorende website. Nadat deze correctie is toegepast, kan de beperkte beheerder het verlaten winkelwagentje van het admin paneel zien.
  _ACP2E-3025 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d1f7dc95)_
* &rbrack; snelle orde van de wolk van 0&rbrace; de snelle orde grote hoeveelheid prestaties van SKU __De prestaties van de afhandeling zijn verbeterd wanneer kenmerken die worden gebruikt in de regels voor de kartprijs, niet voor alle producten aanwezig zijn en wanneer de functie voor het bepalen van de marktprijs (Minimale geadverteerde prijs) is ingeschakeld.__&lbrack;
  _ACP2E-3176 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/66dea0de)_
* __Gedupliceerde punten in kar__
Het systeem verwerkt nu correct veelvoudige parallelle verzoeken om het zelfde product aan de kar in één enkel lijnpunt toe te voegen, verhinderend de verwezenlijking van afzonderlijke lijnpunten voor zelfde SKU. Eerder, zou het doen van parallelle verzoeken om het zelfde product aan het karretje op Storefront toe te voegen in veelvoudige lijnpunten voor zelfde SKU resulteren.
  _ACP2E-3211 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/66dea0de)_
* __de bevestiging van de orde van de Afhandeling wordt verzonden naar e-mail ingegaan in Voornaam/Achternaam__
De e-mailbevestiging van de betalingsopdracht, die eerder is verzonden toen een e-mailpatroon werd ingevoerd in de velden Voornaam en Achternaam, wordt niet meer verzonden.
  _ACP2E-3296 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/5184c067)_
* __de vorm van het verschepende adres van de Afhandeling krijgt update met verkeerd adres__
ShippingAddressFromData wordt nu opgeslagen in de lokale opslag per website. Eerder kon een adres van de verkeerde website automatisch worden ingevuld in het verzendadresformulier tijdens het uitchecken als een winkelcode in de URL werd gebruikt en het uitchecken tijdens dezelfde gastsessie werd gestart van meerdere websites.
  _ACP2E-3402 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_
* __[CLOUD ] Controle behoudt niet het geselecteerde het factureren adres wanneer het Onderzoek van het Adres__ wordt toegelaten
De pagina voor afhandeling van betalingen behoudt nu het geselecteerde factuuradres wanneer het zoeken naar adressen is ingeschakeld. Eerder als &quot;Aantal Grens van de Adressen van de Klant&quot;aan 1 wordt gevormd, en de klant heeft meer dan één adres, zou het geselecteerde facturerings adres na het herladen van de pagina verdwijnen.
  _ACP2E-3405_
* __Cadeaukaartproduct | Bij het samenvoegen van winkelwagentjes worden kaartjes samengevoegd__
Creditcardproducten worden nu correct samengevoegd in het karretje
  _ACP2E-3407 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/88660e79)_
* __de persistentie van de Kar wordt niet gerespecteerd op logout__
Toegevoegde ontbrekende functionaliteit Onthoud mij mijn aanmeldingsgegevens voor de klant aan pop-up en uitchecken van verificatie.
  _ACP2E-3415 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/344fce23)_
* __Bestaande citaatgegevens zijn niet update/niet zichtbaar, in plaats daarvan creeer een nieuw citaatverslag wanneer trigger_recollect = 1__
De winkelwagentjes van de klant verdwijnen niet meer omdat een product wordt verwijderd nadat het aan het winkelwagentje is toegevoegd.
  _ACP2E-3488 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1984c61c)_
* __wanneer een punt van de cadeauregistratie wordt gekocht, ziet de klant punten niet op hun register__
Cadeauregister-update bevat niet langer items die niet bij het cadeauregister horen.
  _ACP2E-3495_
* __[Cloud ] Uitgave met &quot;verwijder Al&quot;Bevestigingspop het Verwijderen van de Punten van de Kunst zonder Bevestiging__
Als je nu op de knop Alles verwijderen klikt voor producten die onder de aandacht moeten worden gebracht, wordt een bevestigingspop-up weergegeven om te controleren of objecten alleen met je bevestiging worden verwijderd. Eerder werden objecten direct verwijderd zonder bevestiging
  _ACP2E-3510_
* __[CLOUD ] herordent knoopfunctionaliteit__
Als u een bestelling opnieuw ordent vanuit het beheerdersgebied, worden nu producten met voorraad aan het citaat toegevoegd, ook al zijn er bepaalde producten in de oorspronkelijke volgorde die geen voorraad meer hebben. Vóór de correctie werden geen producten aan het nieuwe prijsopgave toegevoegd als het product zonder voorraad zich in de oorspronkelijke volgorde bevond.
  _ACP2E-3618 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a52ff98f)_
* __de opslag van het Onderzoek werkt niet door postcode__
Het zoeken naar ophaallocaties op postcode werkte niet goed voor Nederlandse lokalisaties. Na de correctie geeft het zoeken naar de locatie van het oppikken resultaten op basis van de postcode.
  _ACP2E-3622 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/344fce23)_

### Afhandeling van winkelwagentje en afhandeling, Afhandeling/Afhandeling van één pagina

* __[Willekeurige BUG ] E-mailgebied wordt niet teruggegeven of neemt veel tijd verschijnt in de Verzending van de Controle of de pagina van de Betaling__
Commerce geeft nu het veld **[!UICONTROL Email]** weer op de pagina&#39;s voor verzending en betaling van de afhandeling zoals verwacht. Eerder was dit veld afwezig of traag gerenderd.
  _AC-9386 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/e1babcfd)_

### Winkelwagentje en afhandeling, bestelling

* __Datepicker voor product met veelvoudige Aanpasbare Opties met datumgebieden die niet werken wanneer het plaatsen van orde van admin__
Het systeem geeft nu correct de datumkiezer voor alle datumvelden weer wanneer u een product met meerdere aanpasbare datumopties configureert in het aanmaakproces van de beheervolgorde. Eerder werd de datumkiezer alleen weergegeven voor het veld voor de eerste datum, zodat de overige velden geen datumkiezer hadden.
  _ACP2E-3097 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b21e5d91)_

### Winkelwagentje en afhandeling, verzending

* __Onmiddellijke aankoop &quot;goedkoopste verschepen&quot;gebroken voor configureerbare producten__
Met de functie Direct aanschaffen hebt u de duurdere optie voor In-Store levering onjuist geselecteerd voor configureerbare producten in plaats van de goedkoopste methode met platte snelheid. Deze correctie zorgt ervoor dat de juiste verzendmethode wordt gekozen op basis van de werkelijke prijs.&quot;
  _AC-12119 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38811) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38819) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/29fe9097)_

### Catalogus

* __Schoonmaak van cron_planning gegevensbestandlijst schoont niet bestaande banen__
Het systeem ontruimt nu automatisch de cron_planning gegevensbestandlijst, verwijderend ingangen voor banen die niet meer in het systeem bestaan. Dit zorgt voor optimale prestaties door een minimaal aantal rijen in de tabel te handhaven. Eerder, werden de ingangen voor banen van inactieve of verwijderde modules niet schoongemaakt, die tot onnodige gegevensaccumulatie in de cron_planninglijst leidden.
  _AC-10910 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38217) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38693)_
* __de Prijs van de Rij wordt niet geschrapt van Configurable Product__
Het systeem verwijdert nu correct de laagprijs van een product wanneer het van een eenvoudig product in een configureerbaar product wordt omgezet, die nauwkeurige prijsvertoning op de frontend verzekert. Eerder werd de laagprijs van een configureerbaar product niet verwijderd wanneer een product werd omgezet van een eenvoudig product in een configureerbaar product, wat leidde tot een verschil in de weergegeven prijs.
  _AC-10953 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38390) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38427)_
* __beschrijving van de Categorie WYSIWYG is leeg op niet standaardstoreview__
Het systeem slaat nu op de juiste wijze de categoriebeschrijving op en geeft deze weer in de WYSIWYG-editor wanneer u een categorie bewerkt op het niveau van de winkelweergave. Eerder was de WYSIWYG-editor leeg nadat een categoriebeschrijving op het weergaveniveau van de winkel was opgeslagen.
  _AC-11804 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38622) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38623)_
* __Onmogelijk om configureerbare producten met één checkbox geselecteerde douaneoptie__ opnieuw in orde te brengen
Het systeem verwerkt nu correct het opnieuw ordenen van configureerbare producten met één enkele geselecteerde checkbox douaneoptie, die voor succesvolle korf verwezenlijking toestaat. Voorheen leidde het opnieuw ordenen van dergelijke producten tot een fout en werd voorkomen dat artikelen aan het winkelwagentje werden toegevoegd.
  _AC-11970 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38736) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1d144bce)_
* __[Uitgave ] Reparatie van filterpunt op gelaagde navigatie__
Het systeem gebruikt nu correct de woorden &quot;item&quot; en &quot;items&quot; in het gelaagde navigatiefilteritem, waardoor de helderheid en nauwkeurigheid van de filterbeschrijvingen worden verbeterd. Eerder werden deze woorden onjuist gebruikt, waardoor gebruikers door de filteropties konden navigeren.
  _AC-12076 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38789) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37852)_
* __het Formaat van de Datum en van de Tijd voor het Niet Werken van de Optie van de Douane__
Het systeem past nu correct het gevormde datumformaat op de opties van de productdouane van type Date toe, die ervoor zorgen dat het datumformaat correct op de front-end wordt getoond. Eerder waren wijzigingen in de configuratie van de datumnotatie niet van toepassing op de front-end voor aangepaste productopties van het type Date.
  _AC-12164 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32990) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38925)_
* __Ontbrekende opties Dropdown__
Het systeem geeft nu correct alle waarden in de vervolgkeuzelijst weer wanneer u een nieuw kenmerk met meer dan 20 waarden maakt. Eerder werden alleen de eerste 20 waarden of een andere geselecteerde paginawaarden weergegeven, waardoor de resterende waarden ontbraken.
  _AC-13068 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/47b448e2)_
* __[Uitgave ] Huidige opslag identiteitskaart van het Gebruik voor categorie runtime geheime voorgeheugen__
Het systeem gebruikt nu correct de huidige opslag-id voor de cache van de categorietuntime, zodat gegevens niet worden overschreven wanneer emulatie wordt gebruikt of de categorie door aangepaste code in verschillende winkels wordt opgeslagen. Eerder was het object dat in runtime was opgeslagen mogelijk afkomstig uit de verkeerde opslag, wat tot gegevensoverschrijving heeft geleid.
  _AC-13296 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39310) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36394)_
* __bin/magento sampledata:opstellen - geen-update werpt een uitzondering__
Het systeem keurt nu correct een booleaanse waarde goed wanneer het gebruiken van —geen-updateoptie in de steekproef gegevens:stel bevel op, die om het even welke fouten tijdens de plaatsing van steekproefgegevens verhinderen. Er is eerder een fout opgetreden bij het gebruik van deze opdracht omdat het systeem een geheel getal verkeerd had verwacht.
  _AC-13324 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39344) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39345)_
* __[Uitgave ] gebruik van het geheime voorgeheugentype van EAV herstellen__
Het systeem gebruikt nu correct het EAV-cachetype op alle relevante plaatsen, zodat consistente en efficiënte gegevens in cache worden geplaatst. Eerder werd het EAV-cachetype niet consistent gebruikt, wat tot mogelijke inefficiënties en inconsistenties in het in cache plaatsen van gegevens leidde.
  _AC-13355 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32322) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/31264)_
* __Catalogus Geavanceerd Onderzoek met lege gegevens gaat naar de pagina van het onderzoeksresultaat [ 2.4.dev tak]__
Het systeem behoudt gebruikers nu correct op de pagina Geavanceerd zoeken en geeft een foutbericht weer wanneer ze een zoekopdracht proberen uit te voeren zonder gegevens in te voeren. Als u voorheen een lege zoekopdracht zou uitvoeren, zou u gebruikers omleiden naar de pagina Geavanceerd zoeken in catalogus met een bericht waarin ze worden gevraagd hun zoekopdracht te wijzigen.
  _AC-13596 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __[Uitgave ] de lay-out van het Product die op attribute_set wordt gebaseerd__
Het systeem maakt het nu mogelijk de productlay-out aan te passen op basis van de kenmerkenset, waardoor een meer praktische en efficiënte manier wordt geboden om de productweergave in de frontend store te beheren. Voorheen kon de lay-out alleen worden aangepast door SKU of per productsoort, wat niet altijd praktisch was voor veel producten of specifieke artikelen.
  _AC-13622 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38790) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36244)_
* __Ontbrekende unieke sleutel op eav_attribute_option_value lijst__
Het systeem bevat nu een unieke sleutel voor de kolommen &#39;option_id&#39; en &#39;store_id&#39; in de tabel &#39;eav_attribute_option_value&#39;, waardoor het niet mogelijk is dat een optie meerdere waarden heeft voor dezelfde winkelweergave. Eerder, kon de gebrekkige code in een optie resulteren die veelvoudige waarden voor de zelfde opslagmening heeft, die kwesties veroorzaakt wanneer het uitgeven van producten of attributen.
  _AC-6738 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/24718) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/28796)_
* __[Uitgave ] de zichtbaarheidsklasse van het Gebruik voor de indexeer van het categorieproduct, in plaats van geharde waarden__
Het systeem gebruikt nu de zichtbaarheidsklasse voor de indexator van het categorieproduct in plaats van de geharde waarden, die modulariteit verbeteren. Eerder werden in de productindex van de categorie hardgecodeerde waarden gebruikt, waardoor de flexibiliteit en het aanpassingsvermogen werden beperkt.
  _AC-8297 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37200) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37199)_
* __de code van de Valuta verandert niet in Nieuwe product widget__
Het systeem werkt nu de valutacode in de widget Nieuw product correct bij wanneer de valuta op de voorgrond wordt gewijzigd, zodat de valutaweergave op de hele site consistent is. Eerder had het wijzigen van de valuta aan de voorzijde geen invloed op de valutacode die in de widget Nieuw product werd weergegeven.
  _AC-9375 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37898) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37899)_
* __Reguliere Prijs toont niet op PLP voor Configurable Product__
De standaardprijs wordt nu weergegeven op productpagina&#39;s voor configureerbare producten die kinderproducten met een speciale prijs hebben.
  _ACP2E-2224 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4fbf702)_
* __informatie van het Beeld die recht niet op het Visuele net van de Verkoop toont__
De voorraad wordt nu weergegeven volgens de geselecteerde winkel.
  _ACP2E-2478 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/bdbf97ea)_
* __inhoud Widget niet op cms pagina__ bijwerkt
Het systeem werkt nu de widgetinhoud op een CMS-pagina bij wanneer een product als nieuw en opgeslagen wordt ingesteld, zodat de bijgewerkte productverzameling op de pagina wordt weergegeven. Eerder werd de pagina niet bijgewerkt om het nieuwe product weer te geven vanwege een onjuiste cache-id voor de widget in de cache.
  _ACP2E-2621 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f89a447e)_
* __Kwesties die geavanceerde tarifering op bundelproducten besparen__
Bundle productbesparende prestatieverbetering.
  _ACP2E-2630 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b2286ecf)_
* __[] re-indexeert proces op locatie is inefficiënt wanneer het creëren van de Regels van de Prijs van de Catalogus__
Als u nu de regel voor catalogusprijzen opslaat, worden de indexen niet ongeldig, maar worden alleen de betrokken producten opnieuw geindexeerd
  _ACP2E-2652 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f89a447e)_
* __Bijwerkend tijd van Datum en het type van Tijd productattributen via de invoer CSV__
Datumtijdkenmerken worden nu opgenomen in de geëxporteerde gegevens. Het zal ook mogelijk zijn de tijd voor dergelijke kenmerken bij te werken met behulp van import. Ook als &quot;Fields Enclosure&quot; is ingeschakeld, worden kenmerkwaarden in de kolom &quot;additional_attributes&quot; tussen dubbele aanhalingstekens ingesloten.
  _ACP2E-2679 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38306) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Geen aangewezen foutenmelding wanneer website identiteitskaart in het verzoek__ verkeerd is
Het juiste foutbericht is nu toegevoegd om weer te geven wanneer de website-id in het verzoek onjuist is. Eerder was er geen validatie toen de website-id in het verzoek verkeerd was.
  _ACP2E-2689 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/39d54c2d)_
* {het beeld van het 0} Product wordt verloren na het schrappen van een bestaande Geplande Update die niet het beeld __beïnvloedt
Afbeeldingen van producten worden niet verwijderd als u de testupdate verwijdert.__
  _ACP2E-2785 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c8931218)_
* &rbrack; Verkeerde prijs van het bundelproduct van 0&rbrace; Cloud &lbrace;wanneer gebruikt met de prijzen van de rij __Bij de berekening van bepaalde percentages kortingen die tot op 2 decimalen zijn afgerond, worden voorheen verschillende definitieve prijzen voor de pagina met de winkelpagina&#39;s van de winkelwagentje en de productdetails gegenereerd.__&lbrack; Nadat deze correctie is toegepast, is de uiteindelijke prijs voor het bundelproduct gelijk aan die op de pagina met productdetails, de pagina met productaanbiedingen en de pagina met mini-winkelwagentjes.
  _ACP2E-2799 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38091) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/b2286ecf)_
* __Regel van de Bevorderingen van de Catalogus het werken niet met kwantiteit_and_stock_status attributen__
Het attribuut quantity_and_stock_status zal nu in aanmerking worden genomen door de regel van de catalogusbevordering, die niet eerder in aanmerking werd genomen toen het produceren van nieuw product van de admin kant.
  _ACP2E-2805 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35627) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/cf34971d)_
* __entiteit van het Product update_at kolomwaarden niet het bijwerken terwijl het bijwerken van prijs door REST API__
De kolom product &#39;last updated at&#39; van de beheerder wordt de juiste datum bijgewerkt terwijl de bestaande producten via de REST API worden bijgewerkt. Eerder is de kolom &#39;last updated at&#39; niet correct bijgewerkt.
  _ACP2E-2837 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/39d54c2d)_
* __het is mogelijk om niet-unieke waarden via productinvoer__ te plaatsen
Het systeem handhaaft nu correct de unieke waardebeperking voor unieke productkenmerken tijdens de invoer van het product, die dubbele waarden voor dat attribuut verhindert te hebben. Eerder was het mogelijk om niet-unieke waarden in te stellen voor productkenmerken die waren geconfigureerd om unieke waarden te hebben via het importeren van producten.
  _ACP2E-2840 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38445) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7e0e5582)_
* __Producten op de frontend opslag specifieke gegevens van de gebruiksopslag wanneer de Wijze van de enig-opslag wordt toegelaten__
Eerder, toen wij enige opslagwijze voor de standaard archiefmening toeliet, werden de veranderingen niet gemigreerd aan het website-vlakke werkingsgebied. Nadat deze correctie is toegepast, worden de weergavespecifieke standaardgegevens van de winkel gesynchroniseerd met gegevens op websiteniveau en worden de mogelijke conflicten voor producten en categorieën opgelost.
  _ACP2E-2843 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c8931218)_
* __kan niet &quot;StandaardSorteren door&quot;in een categorie plaatsen die rest API__ gebruikt
Correcte default_sort_by bijwerken op een categorie via REST / SOAP APi-verzoek
  _ACP2E-2857 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/57a32313)_
* __[Wolk ] de Merchant staat voor problemen met wishlist telling__
Als u een product aan de verlanglijst in één winkel toevoegt, wordt het aantal wenslijsten in andere winkels die in dezelfde browser zijn geopend, niet meer verhoogd. Als beide winkels in dezelfde browser werden geladen, zou het aantal wenslijsten ook in de andere winkel toenemen.
  _ACP2E-2871 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Pagina van de Categorie bij frontend toont lege groeven wanneer het gebruiken van bundelproduct__
Bundelproducten die niet in de huidige winkelcontext kunnen worden verkocht, worden niet meer geïndexeerd.
  _ACP2E-2874 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/bc37ec76)_
* __[CLARIFICATION ] de lijstkwesties van de de productopeenvolging van de bundel__
De records in de tabellen van de Bundle-productreeks (sequence_product_bundle_option, sequence_product_bundle_selection) worden nu verwijderd wanneer het Bundle-product wordt verwijderd of de Bundle-productopties worden verwijderd.
Eerder werden de records in de tabellen van de Bundle-productreeks niet verwijderd.
  _ACP2E-2888_
* __[Cloud ] Uitgave van Citaat in multi-website architectuur__
Eerder kon architectuur met meerdere websites met verschillende valuta&#39;s en klantgroepen geen kortingen op de winkel toepassen. Nadat deze oplossing is geïmplementeerd, wordt de architectuur met meerdere websites met verschillende kortingen voor de klantgroepprijs met succes toegepast op verschillende winkels.
  _ACP2E-2905 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38506) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a4fbf702)_
* __dynamic-rows.js:658 Uncaught TypeError: dataRecord.slice terwijl het uitgeven van bundelproducten__
Er is geen javascript-fout in de browserconsole wanneer de optie uit het bundelproduct wordt verwijderd.
  _ACP2E-2909 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38505) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/93d50f8d)_
* &rbrack; Het verkeerde tarief van het Product van de Bundel van de Wolk __&lbrack;in orde bevestiging__
Het juiste bedrag wordt weergegeven voor bundelopties, in volgorde op Storefront wanneer een andere valuta dan de eerste valuta werd gebruikt.
  _ACP2E-2950 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4fbf702)_
* __YouTube Video die Bug toevoegt__
Afbeeldingen en video&#39;s van producten worden geconfigureerd in het algemene bereik. Aangezien u geen productvideo in één werkingsgebied en niet in een andere kunt hebben, is de belangrijkste het plaatsen van de sleutel van Youtube API aan globaal werkingsgebied geplaatst.
  _ACP2E-2956 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4fbf702)_
* __[de update van de Wolk ] URL slechts voor store_id=0__
Het &quot;URL-pad&quot; wordt nu opgeslagen met de juiste opslag-id. Eerder was de opslag-id onjuist, waardoor er onjuiste URL-paden in de database achterbleven wanneer categorieën worden verplaatst.
  _ACP2E-2964 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9af794a4)_
* __async.operations.all uitvoerde en creeerde een fout.__
Onjuiste gegevens over productkoppelingen in REST API-aanroepen veroorzaken niet langer kritieke fouten.
  _ACP2E-3009 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4fbf702)_
* &rbrack; Mobiele Uitgave van de Wolk 1&rbrace; slechts kan niet op het beeld Pdp __knijpen
Het systeem ondersteunt nu zoomfuncties met knijpbeweging op afbeeldingen met productdetails in de mobiele weergave op Chrome, waardoor de mobiele gebruikerservaring wordt verbeterd.__&lbrack; Eerder werd niet op de afbeelding ingezoomd door te dubbeltikken op de afbeelding in de mobiele weergave op Chrome.
  _ACP2E-3029 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/148c3ead)_
* __Ontbrekend etiket in LayeredNavigation met optienaam 0__
Het probleem is opgelost door een lege waardecontrole voor kenmerkwaarde 0 over te slaan. Eerder werd het als leeg beschouwd en veroorzaakte het probleem.
  _ACP2E-3058 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3a7c4d17)_
* __de Klanten zien prijzen van andere klantengroepen__
Aan de klantengroep gerelateerde informatie werd in een onjuist segment opgeslagen vanwege de oude waarde van de X-Magento-Vary in aanvraag. Dit probleem is nu opgelost.
  _ACP2E-3069 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d1f7dc95)_
* __Fout wanneer het schrappen van bundelopties__
Het systeem verwijdert nu correct bundelopties zonder een fout te veroorzaken of ervoor te zorgen dat de pagina niet reageert. Als u voorheen bundelopties verwijdert, treedt de fout &quot;Pagina reageert niet&quot; op en wordt het product niet opgeslagen.
  _ACP2E-3076 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6a185204)_
* __Toestemmingen van de Categorie uit de kwestie van geheugenbrowser__
UI van de Toestemmingen van de categorie werd opnieuw ontworpen om het teruggeven van een grote hoeveelheid toestemmingen toe te staan die uit doos UI component en paginering gebruiken. Eerder categorietoestemmingen zouden ervoor zorgen dat de browser vastloopt met een grote hoeveelheid machtigingen die aan de categorie zijn toegewezen.
  _ACP2E-3094_
* __[het Dossier van het Beeld van de Wolk ] bestaat niet in het Logboek van de Fout van New Relic__
Het systeem synchroniseert nu aangepaste plaatsaanduidingsafbeeldingen naar lokale opslag, zodat deze op de juiste wijze worden weergegeven wanneer externe opslag zoals AWS S3 wordt gebruikt. Eerder konden aangepaste plaatsaanduidingsafbeeldingen niet worden gerenderd bij gebruik van externe opslag, wat resulteerde in een verbroken weergave van de afbeelding en foutlogboeken.
  _ACP2E-3100 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d1f7dc95)_
* __het Nieuwe voer van Producten RSS wordt niet bijgewerkt met nieuwe producten toe te schrijven aan geheim voorgeheugen__
De RSS-feed voor nieuwe producten wordt nu bijgewerkt wanneer een product als nieuw en opgeslagen wordt ingesteld
  _ACP2E-3103 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d01ee51e)_
* &rbrack; GQL van de Galerij van de Media van het Product van 0&rbrace; wolk &lbrace;wordt de reactie niet gesorteerd door beeldpositie __Het systeem sorteert items in de mediagalerie nu op de juiste positie in de GraphQL-reactie en zorgt voor een nauwkeurige weergavevolgorde.__&lbrack; Eerder zijn de items in de mediagalerie niet op positie gesorteerd, wat tot een onjuiste weergavevolgorde heeft geleid.
  _ACP2E-3126 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37671) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/b21e5d91)_
* &rbrack; De punten van de Subcategorie van 0&rbrace; Wolk &lbrace;worden niet getoond op widgets uitgeven op admin achterend __Voor de categoriestructuur op de nieuwe widgetpagina hoeven geen Level 5+-categorieën meer te worden geladen.__&lbrack; Eerder ontbraken enkele categorieën bij het laden van de structuur voorbij de categorieën van niveau 5.
  _ACP2E-3136 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/148c3ead)_
* __[wolk ] tweemaal-vinger gezoem en beweeg kwestie op het echte mobiele apparaat__
Het systeem zorgt nu voor een consistente zoomfunctionaliteit voor afbeeldingen op mobiele apparaten en zorgt voor een vloeiende en voorspelbare gebruikerservaring. Eerder was de functie voor zoomen op afbeeldingen inconsistent en zoomde dan plotseling uit na een bepaald punt bij weergave op een mobiel apparaat.
  _ACP2E-3198 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1366ae5e)_
* __wanneer wij producten van de gedeelde catalogus unassign, worden de producten van de wenslijst niet ontruimd__
Er zijn nu geen items zichtbaar in de verlanglijst als een product niet beschikbaar is in de gedeelde catalogus. Eerder werd op de pagina Vraaglijsten een telling van 1 item onjuist weergegeven, zelfs als er geen items in de verlanglijst stonden.
  _ACP2E-3282 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/5184c067)_
* __Verwante producten selecteren allen/Alle Uitgave deselecteren__
Eerder werkte de knop Alles selecteren/Alles deselecteren voor verwante producten niet correct als een product handmatig was geselecteerd. Na de correctie werken deze knoppen nu consistent, zelfs na handmatige selectie, zodat alle producten correct zijn geselecteerd of uitgeschakeld.
  _ACP2E-3286 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/fd5cf3af)_
* &rbrack; de waakzame e-mailvertaling van het Beeld van de Wolk 1&rbrace; aan de verkeerde taal __Wanneer u berichten over voorraden/prijzen verzendt voor een website met meerdere winkelweergaven die verschillende talen gebruiken, wordt in de e-mail de taal gebruikt van de winkelweergave waarin de waarschuwing is gemaakt.__&lbrack;
  _ACP2E-3336 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a4cf5e62) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/9f3e63d1)_
* __Uitgeschakelde Categorieën hebben niet meer hun namen grijs uit in de categorieboom__
Eerder werden uitgeschakelde categorieën niet grijs weergegeven in de categoriestructuur. Nu worden ze weergegeven met een grijs-uiteffect.
  _ACP2E-3350 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d75cff27)_
* __het configureerbare product geeft vormlading oorzaken onderbreking en geheugenuitputting uit__
Voorafgaand aan de moeilijke oplossing configureerbare productvariaties werden geconstrueerd gebaseerd op alle mogelijke combinaties van attributenopties. In gevallen waarin kenmerken veel opties hadden, resulteerde dit in een langdurige en hulpbronnenintensieve bewerking. Configureerbare productvariaties worden nu samengesteld op basis van bestaande onderliggende productkenmerken. Dit leidt tot veel minder berekeningen, dus tot een beter gebruik van middelen.
  _ACP2E-3410 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_
* __Fotorama laadt correct geen video wanneer het gebruiken van Monsters en de optie is vooraf geselecteerd via URL__
Productvideo&#39;s worden nu correct weergegeven op de pagina met configureerbare productdetails als de URL geselecteerde opties bevat.
  _ACP2E-3454 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_
* __Widget van Carrousel PageBuilder toont producten die voorwaarden niet aanpassen__
Productlijst die in widgets wordt gebruikt, voldoet nu aan de categorievoorwaarde
  _ACP2E-3461 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_
* __de Fout van de Bevestiging teweeggebracht voor Alle Producten in Groep wanneer men Ongeldige Hoeveelheid__ heeft
De validatiefout wordt nu correct geactiveerd voor alle producten in de groep wanneer een product een ongeldige hoeveelheid heeft, wat eerder niet is gebeurd.
  _ACP2E-3469 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/56463d5e)_
* __[CLOUD ] Speciale prijs die niet in Configurable product__ toont
Na de correctie heeft het wijzigen van de waarde &quot;Gebruikt in productaanbieding&quot; voor het speciale prijskenmerk geen invloed op het weergeven van de speciale prijs voor configureerbare producten.
  _ACP2E-3513 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d4de4726)_
* __de Tijdelijke lijsten van Indexers van Indexers worden niet schoongemaakt als het proces__ wordt geëindigd
Tijdelijke tabellen voor de indexering van de CatalogRule worden nu opgeschoond als het indexeerproces wordt beëindigd
  _ACP2E-3516 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1984c61c)_
* __[KANALEN ] de mislukkingen van de de eenheidstest van de Kern in 2.4.7-p3__
Opmerkingen bij de release voor deze test zijn niet nodig omdat het een verbetering van de eenheidstest betreft.
  _ACP2E-3520 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1984c61c)_
* __Uitgave van Prestaties in het Terugwinnen van de Hoeveelheid van de Voorraad voor Gegroepeerde Producten met Veelvoudige Bronnen__
De pagina voor het bewerken van gegroepeerde producten en bundelproducten is nu geoptimaliseerd wanneer toegewezen producten een groot aantal inventarisbronnen hebben.
  _ACP2E-3533 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/0208e433)_
* __Hervoegsel ACP2E-3389__
Verbeterde prestaties van de pagina met beheercategorieën bij een groot aantal ankercategorieën
  _ACP2E-3641 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/982b1c42)_

### Catalogus, inhoud

* __[het Geheime voorgeheugen van de Wolk ] wordt niet ongeldig gemaakt.__
Eerder was het niet passend om een CMS-pagina met een bijgewerkte ontwerplay-out op te slaan aan de voorzijde. Nadat deze correctie is toegepast, wordt de juiste ontwerplay-out aan de voorzijde weergegeven wanneer de ontwerplay-out wordt gewijzigd en de CMS-pagina wordt opgeslagen.
  _ACP2E-3063 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/66dea0de)_
* &rbrack; de Categorieën van het Anker/niet-Anker van de Wolk __&lbrack;die in Inhoud Widget worden omgekeerd__
Eerder werden bij de selectie van Weergeven op -> Ankercategorieën alle categorieën weergegeven die de relatie tussen het anker en het niet-anker niet weerspiegelden. Nadat deze correctie is toegepast, worden in de Categorieën Weergeven op -> Anker alleen de ankercategorieën weergegeven (selecteerbaar) en in de Categorieën Weergeven op -> Niet-anker worden de niet-ankercategorieën weergegeven (selecteerbaar)
  _ACP2E-3131 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7377de59)_
* __Categorieën die niet met widgets__ werken
Als we het CMS-blok eerder hadden opgeslagen voor verschillende ankercategorieën/niet-ankercategorieën, werkte het niet voor de onderliggende categorieën wanneer het op de voorkant werd weergegeven. Nadat deze correctie is toegepast, wordt het blok aan de voorzijde weergegeven voor verschillende categorieën.
  _ACP2E-3152 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d01ee51e)_

### Catalogus, framework

* __de Opdracht krijgt (Verzendingen|Creditmemos|Factuur)Inzameling - de Inzameling zou niet moeten worden geladen__
Het systeem zorgt er nu voor dat de inzamelingen voor overbrengingen en creditnota&#39;s niet vooraf worden geladen wanneer zij van een orde worden teruggewonnen, die extra filters of orden toestaan om op deze inzamelingen te worden toegepast. Eerder werden deze verzamelingen automatisch geladen, zodat er geen verdere wijzigingen konden worden aangebracht.
  _AC-9111 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37561) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37562)_
* &rbrack; Follow-up van de Wolk 1&rbrace;: Verkeerd in Gegevens Vergelijking wanneer het controleren als het gegeven veranderingen __heeft
Eerder werd het opslagobject aangeroepen telkens wanneer geen gegevenswijzigingen werden aangebracht (voor numerieke gegevensvelden, zoals int/float/double).__&lbrack; Het activeert de markering _hasDataChanges om waar te zijn en roept de opslagfunctie aan. Het controleert ook niet de drijvende aantallen die door koord worden ingekapseld. Nadat deze correctie is toegepast, wordt de functie Save alleen aangeroepen als de gegevens zijn gewijzigd. De gegevenswaarde voor int/float/double-check met de waarde die aan de functie wordt doorgegeven en het strikte type dat overeenkomt
  _ACP2E-2949 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c8931218)_

### Catalogus, GraphQL

* __Behandelend de Filters van de Categorie in GraphQL: includeDirectChildrenOnly en category_uid__
Alleen de directe onderliggende categorieën worden opgehaald tijdens het filteren op category_uid.
  _ACP2E-3090 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/93d50f8d)_
* &rbrack; Grafiek het sorteren van het Product van 0&rbrace; Cloud &lbrace;werkt niet __GraphQl-productsortering door meerdere velden wanneer de velden in variabelen worden doorgegeven, werkt nu zoals verwacht.__&lbrack;
  _ACP2E-3166 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/8459b17d)_
* __de terugkeer van de Prijzen van de Rij verkeerde waarde in producten GraphQL (in vergelijking met Storefront)__
Na de correctie hebben de laagprijzen van het product die voor grafische aanvragen worden geretourneerd, de prijs per één object.
  _ACP2E-3312 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD ] B2B: categoriekwestie via GraphQL__
Na de moeilijke situatie, keert de categorieën grafisch vragen categorieën met toestemming terug zelfs als de wortelcategorie geen toestemming heeft verleend.
  _ACP2E-3385_

### Catalogus, Prijzen, Staging en Voorvertoning

* &rbrack; het eindpunt van de prijsAPI van 0&rbrace; Cloud Speciale winst fout wanneer het bijwerken van grote aantallen producten gelijktijdig __Nu maakt de API voor bulkupdates voor speciale prijzen één campagne voor elk datumbereik in plaats van meerdere geplande updates voor elk product en datumbereik.__&lbrack; Bovendien worden gelijktijdige API-aanvragen voor snellere verwerking van een groot aantal SKU&#39;s ondersteund.
  _ACP2E-2672 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/f89a447e)_

### Catalogus, product

* __de selectieboom van de Categorie in geeft product uit is niet in de zelfde orde zoals die in Catalog ->Categorieën__ wordt geplaatst
Het systeem geeft nu correct de categorieselectiestructuur in de productbewerkingssectie weer in dezelfde volgorde als is ingesteld in Catalog->Categorieën, waardoor het beheer van producten in grote catalogi wordt vereenvoudigd. Eerder werd de categoriestructuur in de productbewerkingssectie weergegeven in de volgorde van het maken van de categorie, ongeacht de weergavevolgorde ingesteld in Catalog->Categorieën.
  _AC-7050 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36101) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36104)_

### Catalogus, SEO

* __Onjuiste canonieke URL voor categorie wanneer pagina > 1__
Eerder werkte de canonieke URL voor inhoud van meerdere pagina&#39;s niet correct, waarbij de basis-URL consistent werd weergegeven. Nadat de correctie is geïmplementeerd, wordt de URL voor inhoud van meerdere pagina&#39;s nu correct weergegeven met de pagina-id.
  _ACP2E-3653 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/982b1c42)_

### Catalogus, zoeken

* __Producten tonen niet op categorie en onderzoek maar de directe verbindingen werken__
Eerder werkte het kenmerk Yes/No custom met price_* attribute_code niet met indexeren. Na deze correctie werkt het kenmerk Yes/No naar behoren.
  _ACP2E-2757 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ba25af8a)_
* &rbrack; Elastische onderzoeksfout van 0&rbrace; wolk &lbrace;op bepaalde categoriepagina&#39;s __Eerder, met het vermelde configuratiekaart, wanneer wij prijs 0 voor veelvoudige producten zetten, zal het een uitzondering op de frontend categoriepagina werpen.__&lbrack; Nadat deze correctie is toegepast wanneer meerdere productprijzen 0 en we de pagina met categorieën vooraf laden, wordt er geen uitzondering gegenereerd en wordt de pagina met categorieën correct geladen.
  _ACP2E-3053 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c8931218)_
* __de Fout van het Type kwam voor toen het creëren van voorwerp: Magento\CatalogSearch\Model\Indexer\Fulltext\Interceptor Uitzondering__
Na de correctie kan een instantie van de klasse Magento\CatalogSearch\Model\Indexer\Fulltext worden gemaakt zonder $data op te geven.
  _ACP2E-3345 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD ] Uitgave met Producten is niet zichtbaar in Voorzijde na het Opslaan in Magento Admin__
Na de fix configureerbare producten die kindproducten met lange namen hebben zullen niet in de winkel worden gemist.
  _ACP2E-3521 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1984c61c)_

### Catalogus, verzenden

* __Verzendadres leeg terwijl het plaatsen van een orde voor een punt van de cadeauregistratie__
Eerder genereerde voor cadeau-registeritems van gastgebruikers, wanneer deze werden geretourneerd van de e-mailfunctie, een leeg leeg adres dat onjuist is voor het plaatsen van een bestelling. Nadat deze moeilijke situatie wordt toegepast, controleert het geschenkenregister het programma geopende gebruiker/gastgebruikers en toegewezen adressen als zij bestaan.
  _ACP2E-3195_

### Wolk

* __[de Wolk ] PHPSESSID verandert elk POST Verzoek__
PHPSESSID regenereert niet meer op POST- verzoeken op frontend gebied voor een het programma geopende klant als L2 Redis geheime voorgeheugen wordt toegelaten en de klant werd bijgewerkt van het achtereind
  _ACP2E-3010 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6a185204)_
* __de Waarschuwingen van de Generatie van de Sitemap__
Na de correctie wordt de sitemap gegenereerd in de tmp-systeemmap en gekopieerd naar de uiteindelijke bestemming.
  _ACP2E-3532 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d4de4726)_

### Inhoud

* __[Uitgave ] kwestie met de prijsvertoning in Recently Bekeken widget__
Het systeem geeft nu correct de prijs van eenvoudige producten uit de voorraad weer in de widget Onlangs bekeken product, zodat alle widgets en pagina&#39;s met productlijsten consistent zijn. Eerder werd de prijs van eenvoudige producten uit de voorraad niet weergegeven in de widget Onlangs bekeken product vanwege een voorwaarde in de sjablonen voor het laden van prijzen.
  _AC-10539 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38167) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38159)_
* &rbrack; Correct type en grammatica van 0&rbrace; kwestie &lbrace;in acl.xsd- dossier __Het systeem corrigeert nu een typefout en grammaticale fout in het bestand acl.xsd, waardoor de documentatie helderder en nauwkeuriger wordt.__&lbrack; Eerder bevatte het bestand acl.xsd een typefout en een onjuiste grammatica die tot verwarring kon leiden.
  _AC-10596 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38061) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38046)_
* __de bannerbeeld van de Pagebuilder niet zichtbaar in galerij__
Het systeem geeft nu correct bannerafbeeldingen weer die zijn geüpload in nieuwe mappen in de Pagebuilder-galerie, waardoor eerdere consolefouten worden voorkomen. Voorafgaand aan deze correctie waren de bannerafbeeldingen niet zichtbaar in de galerie als ze in een nieuwe map waren geüpload, waardoor een consolefout ontstond.
  _AC-10845 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c8f87c25)_
* __&quot;Gebiedscode niet ingesteld&quot; na update naar 2.4.5-p8__
Het systeem voltooit nu met succes het statische proces van de inhoudsplaatsing wanneer de module Magento_CSP wordt toegelaten en &quot;dev/js/translate_strategy&quot;wordt geplaatst aan &quot;ingebed&quot;zonder de &quot;Gebiedcode te veroorzaken niet plaatste&quot;fout. Eerder, onder deze voorwaarden, zou het statische proces van de inhoudsplaatsing met een &quot;niet vastgestelde geen&quot;fout van de Code van het Gebied ontbreken.
  _AC-12283 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38845) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38922)_
* __Widget categorieboom wordt niet correct teruggegeven__
  _AC-12692 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39008) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/58e40ceb)_
* __Onbekwaam om &quot;Gebruikend Standaardwaarde&quot;bericht te zien wanneer het veranderen van het thema in de pagina van de ontwerpconfiguratie__
Het systeem bevat nu een aparte kolom voor het weergeven van het bericht Standaardwaarde gebruiken, afhankelijk van het geselecteerde thema in de ontwerpconfiguratiepagina. Dit zorgt voor helderheid en zichtbaarheid van de status van de standaardwaarde. Eerder werd het bericht &#39;Standaardwaarde gebruiken&#39; niet weergegeven, wat leidde tot verwarring over de status van het geselecteerde thema.
  _AC-13054 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/47b448e2)_
* __[kwestie ] herstelt achterwaartse verenigbaarheid met TinyMCE stoppen opnieuw (na het...__
Het systeem herstelt nu achterwaartse compatibiliteit met TinyMCE-plug-ins, waardoor functies die in de plug-in zijn gedefinieerd, kunnen worden aangeroepen wanneer de widget vanaf een andere locatie wordt gebruikt. Als gevolg van een wijziging in de TinyMCE-versie gaven de plug-ins eerder de widgets niet als een object, wat resulteerde in een fout tijdens het aanroepen van bepaalde functies op de widgetinstantie.
  _AC-13569 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39262) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39258)_
* __[Uitgave ] dossier uploadt kwestie in de redacteur van WYSIWYG op productpagina__
Het systeem geeft nu correct de mapstructuur weer en staat het uploaden van afbeeldingen in de WYSIWYG-editor op de productpagina toe, zelfs nadat het tabblad Afbeelding en video&#39;s eerst is uitgevouwen. Eerder werd door het uitvouwen van het tabblad &#39;Afbeelding en video&#39;s&#39; de mappenstructuur niet weergegeven en werd een foutbericht weergegeven wanneer werd geprobeerd een afbeelding te uploaden in de WYSIWYG-editor.
  _AC-9638 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38026) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38025)_
* __[op-PREM ] Dynamische blokkwestie__
widgets worden nu op de juiste wijze gerenderd binnen dynamische blokken.
  _ACP2E-2392 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a12063bd)_
* __YouTube nocookie url die niet in de Bouwer van de Pagina werkt__
De pagebuilder staat nu de YouTube-URL zonder cookie toe in de formulierelementinstellingen van de validatieregels. Eerder werkte de YouTube no-cookie url niet in pagebuilder.
  _ACP2E-2606_
* __[Wolk ] Voorste niet ladend toe te schrijven aan kwestie in nieuwsbrief malplaatje__
Het toevoegen van blokken via de sectie CMS Pagina-inhoud leidt niet meer tot een uitzondering.
  _ACP2E-2693 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ea79f7dd)_
* __ACP2E-2836: [ Cloud ] onderzoekt uitzondering die in het logboek wordt gevonden: InvalidArgumentException: De klasse bestaat niet in vendor/magento/module-rule/Model/ConditionFactory.php__
Als u een voorwaarde verwijdert bij de inhoud-instellingen van een PageBuilder-product, wordt niet langer een uitzondering opgenomen in de logbestanden. Eerder, zou het verwijderen van een voorwaarde op de montages van de de productinhoud PageBuilder een kritieke uitzondering veroorzaken om in de logboeken worden geregistreerd, ondanks het veroorzaken van geen kwesties op het front-end.
  _ACP2E-2836 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/36c0f5df)_
* __Schakelen naar enige opslagwijze - de globale inhoud verschijnt niet meer__
Het systeem synchroniseert nu de configuraties van het ontwerp van de winkelweergave met de configuraties van het websiteontwerp wanneer de modus Eén winkel wordt ingeschakeld, zodat de updates van de inhoud zichtbaar zijn op de voorzijde. Eerder, zou het schakelen op enige opslagwijze inhoudsupdates worden weerspiegeld op de storefront verhinderen.
  _ACP2E-2842 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7e0e5582)_
* __de Bouwer van de Pagina vervangt beeld wanneer het proberen om verbinding en andere bruikbaarheidsglitches toe te voegen.__
Wanneer u nu op een afbeelding klikt, laden koppelingen in de bewerkingseditor in het tekstelement Page Builder de juiste gegevens in de afbeelding, het dialoogvenster voor de koppelingsconfiguratie. Het toevoegen van een koppeling naar een afbeelding in de editor werkt nu goed. Eerder werd de afbeelding vervangen door een koppeling.
  _ACP2E-2903 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __Oude media galerij ontbreekt om beelden terug te geven wanneer een 0 byte beeld in de folder__ wordt geplaatst
Het systeem verwerkt nu afbeeldingen van 0 byte in de mediagalerie zonder de functionaliteit te verstoren, zodat andere afbeeldingen in de directory naar behoren kunnen worden weergegeven en geselecteerd. Eerder was het zo dat door de aanwezigheid van een afbeelding van 0 byte in de mediagalerie niet alle afbeeldingen in de directory konden worden weergegeven of geselecteerd.
  _ACP2E-2970 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/35b1b1da)_
* __de Bouwer van de Pagina van de Fout wanneer het uitgeven van het Blok van CMS__
Het systeem slaat nu correct veranderingen op in het admin gebied gebruikend de Bouwer van de Pagina, zonder de fout te werpen &quot;de Bouwer van de Pagina gaf 5 seconden terug zonder sloten vrij te geven.&quot; in de browserconsole. Deze fout is eerder opgetreden tijdens een poging om wijzigingen op te slaan, zodat de inhoud niet met succes kan worden bijgewerkt.
  _ACP2E-3064 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/35b1b1da) - [ GitHub codebijdrage ](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __[CLOUD ] Geen knopen van controle of geef kart op de wortelsectie uit__
Het bundelproduct wordt nu zonder fouten toegevoegd aan het winkelwagentje via widgets.
  _ACP2E-3092 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/b21e5d91) - [ GitHub codebijdrage ](https://github.com/magento/magento2-page-builder/commit/4ebe3f1d)_
* __de Voorproef van het Staging van de inhoud op categoriepagina&#39;s toont product geen widgets__
De kwestie is opgelost door ervoor te zorgen dat de productgegevens voor de extra categorie die gekoppeld is aan het CMS-blok correct in de database zijn opgenomen. Eerder werd een lege resultatenset geretourneerd toen de pagina met voorvertoningen van rubrieken werd opgevraagd.
  _ACP2E-3113_
* __[CLOUD ] uploadt beeldknoop werkt niet__
Voordat de knop Afbeelding uploaden voor Banner en Slider van PageBuilder werkte niet zoals u had verwacht, en nu wanneer u erop drukt, wordt het lokale bestandsbeheer geopend en wordt het te uploaden afbeelding geselecteerd.
  _ACP2E-3122 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/476ef8ea)_
* __imagecreatetruecolor (): Argument #2 ($height) moet groter zijn dan 0. Kan specifieke afbeelding niet uploaden__
Oplossing voor het probleem dat fouten veroorzaakte in de beheerder bij het uploaden van afbeeldingen met een hoogte van 0 via de mediagalerie. Synchronisatie van de elementen is gelukt met de opdracht sync. Eerder kan de afbeelding niet worden geüpload via de mediagalerie en de synchronisatieopdracht mislukt ook als een bepaalde afbeelding zich in de galerie bevindt.
  _ACP2E-3127 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6f4805f8)_
* __Prototype.js Array.from in conflict met Google Maps API__
Google Maps wordt nu correct weergegeven in de PageBuilder-editor. Een JavaScript-fout voorkomt eerder dat Google Maps correct wordt weergegeven.
  _ACP2E-3154 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/148c3ead)_
* __[Wolk ] - de Schuifregelaar van CMS weerspiegelt niet de recentste veranderingen__
Het probleem is opgelost door ervoor te zorgen dat de lijst met schuifregelaars wordt vernieuwd terwijl de gebeurtenis Save wordt geactiveerd op het bewerkingsscherm. Eerder was het aanleiding tot het probleem.
  _ACP2E-3275 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __een fout komt in CSM pagina voor wanneer de blokken van CMS gebruikend paginabouwer in bepaalde orde worden opgenomen__
Eerder in sommige versies van PHP en OS (Linux), zou het renderen van blokken die naar andere cms-blokken verwijzen via PageBuilder zijn mislukt met een &quot;Onbekende fout opgetreden. Probeer het opnieuw.&quot;. Nu wordt de inhoud van de cms-blokken correct gerenderd in inhoud die door PageBuilder wordt gecontroleerd.
  _ACP2E-3326 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/ae2cdeb0)_
* __[de Dynamische blokken van de Wolk ] zullen niet behoorlijk functioneren__
De geregistreerde klantensegmenten worden nu ontruimd na logout die de gastzitting verhinderen eerder het programma geopende segmenten over te nemen
  _ACP2E-3388_
* {de mislukking van de malplaatjevoorproef van 0} Pagebuilder voor grote inhoud __Grote inhoud heeft ertoe geleid dat het canvaselement de browserlimieten overloopt en dat een onjuiste waarde wordt geretourneerd, waardoor de backendcode is beschadigd (de afbeelding kan niet correct worden gedecodeerd).__ Opgelost met het beperken van de canvasgrootte tot de limiet van de universele browser.
  _ACP2E-3428 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/adfb1747)_
* __Laatste veiligheidsupdates met TinyMCE 7 ontbrekende doopvontgrootte__
Lettergrootte en lettertypefamiliekiezers zijn nu beschikbaar in de WYSIWYG-editor. Voorafgaand aan deze moeilijke situatie, met TinyMCE 7 waren deze niet beschikbaar in de redacteursinterface.
  _ACP2E-3430 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/d50f6b5d) - [ GitHub codebijdrage ](https://github.com/magento/magento2-page-builder/commit/2c2f7a0e)_
* __TinyMCE 7 grootte van de redacteursdoopvont in admin in PT en niet PX gelieve te verduidelijken__
Voordat de correctie werd uitgevoerd, kon u in WYSIWYG-gebieden geen tekengrootte opgeven in px. Nu kunt u de tekengrootte instellen in px in plaats van pt.
  _ACP2E-3483 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/3f12d152) - [ GitHub codebijdrage ](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __Type van de Inhoud van het Product in de Bouwer van de Pagina wordt samengevouwen zonder Correcte Berichten__
Vóór de correctie werd de voorvertoning-HTML niet correct gegenereerd wanneer de widget geen producten bevatte. De lege reactie wordt nu op de juiste wijze gegenereerd en de widget producten wordt in de voorvertoning op de juiste wijze weergegeven.
  _ACP2E-3490 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/3f12d152) - [ GitHub codebijdrage ](https://github.com/magento/magento2-page-builder/commit/20aa5d7a)_
* __[pagina bouwer ] Toevoegend Product dat aan blokresultaten in fouten__ vermeldt
Als je nu een Bundle Product Listing toevoegt aan block via page builder, worden er geen fouten gegenereerd
  _ACP2E-3534 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/344fce23)_

### Inhoud, SEO

* __de hiërarchie van de Pagina van CMS kan URL veroorzaken herschrijft kwesties__
Eerder was het voor aangepaste permanente URL om de basispagina&#39;s van andere websites oneindig om te leiden en de pagina is nooit geladen. Nadat deze correctie is toegepast, werkt de aangepaste URL voor het herschrijven van de hoofdpagina van de niet-website naar behoren en vindt er geen omleidingslus plaats.
  _ACP2E-2870_

### Inhoud, Staging en Voorvertoning

* __de prijsregel van de Catalogus toont niet wanneer het aan programma met dynamische blokken__ wordt geplaatst
Het systeem geeft nu correct dynamische inhoud weer die is gekoppeld aan de regels voor catalogusprijzen op de pagina met productdetails. In het verleden kon dynamische inhoud niet worden geladen toen de prijsregels voor de catalogus waren gepland.
  _ACP2E-2979_

### Klanten/klanten

* __Voorste eind - de Datum van geboortebevestiging ontbreekt in de aanmaakpagina van de Klant__
Zorg ervoor dat alle validatie werkt na upgrade moment.js, afhankelijk van het systeem van de nieuwste secundaire versie
  _AC-12162 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/de4dfb8e)_
* __het Segment van de Klant > Voorwaarde > Geschiedenis van het Product* > &quot;het product werd bekeken&quot;werkt niet__
Het systeem geeft nu correct de overeenkomende geregistreerde klanten in de &quot;Product was Bekeken&quot;voorwaarde onder de Segmenten van de Klant weer, wanneer aan de voorwaarde wordt voldaan. Eerder was het aantal geregistreerde klanten dat bij een transactie was betrokken, zelfs toen aan de voorwaarde was voldaan, nul.
  _AC-13060_
* __het tekstgebied van het Gebied wordt niet teruggesteld wanneer landdropdown wordt veranderd__
Het systeem stelt nu het gebied tekstgebied opnieuw in wanneer het land in het drop-down menu wordt veranderd, die ervoor zorgen dat de vorige waarden niet blijven. Als u voorheen het land uit de vervolgkeuzelijst wijzigde, werd het veld Regio niet opnieuw ingesteld, waardoor de laatst opgeslagen waarde behouden bleef.
  _AC-8499 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/3ea26621)_
* __het Schrappen van Klant schoont niet Alle Browser Gegevens van de Zitting op Storefront voor Logged binnen &amp; Geschrapte Klant__
Als u een klant verwijdert, worden alle browsersessiegegevens nu gewist van de winkel voor aangemelde en verwijderde klanten, zoals verwacht. De winkelier kan blijven winkelen en hun browser behandelt hun sessie als een gastsessie. Eerder, toen de klantenrekening voor een het programma geopende verkoopster van Admin werd geschrapt, dan de browser van de verkoopster wierp de fouten van JavaScript.
  _AC-9240 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7d5e3906)_

### Kader

* &rbrack; Ongebruikte configuratie van het Type van 1&rbrace; Vraag `app/code/Magento/Translation/etc/di.xml`__Het systeem verwijdert nu ongebruikte gebiedsdelen in de configuratie, die de algemene codeschoonheid en efficiency verbeteren.__&lbrack; Eerder waren er ongebruikte afhankelijkheden in de configuratie die niet tot enige functionaliteit bijdroegen.
  _AC-10037 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38030) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38064)_
* __V1/klanten/wachtwoordeindpunt vraag/kwestie__
Het systeem houdt zich nu aan de beperkingen die zijn ingesteld in de beheer-GUI bij het verwerken van aanvragen voor wachtwoordwijzigingen via de API, om mogelijk misbruik van de functie voor het opnieuw instellen van wachtwoorden te voorkomen. Voorheen kon de API verzoeken om wachtwoordwijziging verwerken buiten de regels die zijn gedefinieerd in de GUI voor beheer, waardoor mogelijk een constante stroom e-mailberichten zou worden gemaakt als geldige e-mails bekend waren.
  _AC-10654 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38238) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0c53bbf7)_
* __Varnish de configuratie sluit niet alle marketing parameters__ uit
Het systeem sluit nu correct alle gemeenschappelijke marketing parameters in de configuratie van Varnish uit, die nauwkeurige het volgen en de analyse verzekeren. Eerder waren bepaalde marketingparameters zoals gad_source, srsltid en msclchild niet uitgesloten, wat tot mogelijke onnauwkeurigheden in de gegevensverzameling leidde.
  _AC-10738 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38298) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39188)_
* __het proces van de het procesfout van de het onderzoeksindex van de Catalogus indexeren__
Het systeem voltooit nu de opdracht voor opnieuw indexeren zonder fouten te ervaren, ongeacht de libxml-versie die met PHP is gecompileerd. Eerder, resulteerde het runnen van het re-indexbevel in een &quot;fout van het proces van het het indexproces van het Onderzoek van de Catalogus tijdens indexeringsproces&quot;fout wanneer PHP met bepaalde versies van libxml werd gecompileerd.
  _AC-10838 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38254) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38553) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0574ac23)_
* __Toegevoegde created_at, status en grand_total filters aan de vraag van de Orden van de klant en bevonden veelvoudige filtermislukking__
Het systeem steunt nu het gebruik van created_at, status, en grand_total filters in de vragen van de klantenorden, en heeft een kwestie opgelost waar de veelvoudige filters niet correct werden toegepast. Eerder, steunde het systeem deze filters niet en zou er niet in slagen om alle filters toe te passen wanneer meer dan één in een vraag werd gebruikt.
  _AC-10941 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38392) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36949)_
* __willekeurig overstroomd krijgen met vragen van verwant/upsell/crosssell blokken en prijs het indexeren__
Het systeem optimaliseert nu vragen van verwante, upsell, en dwars-verkoopblokken, verbetert de prestaties en verhindert de plaats te gaan door bovenmatige vragen. Eerder, kon het systeem met vragen van deze blokken overbelast worden, veroorzakend significante vertragingen en potentieel verlamend de plaats.
  _AC-10991 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36667) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38050)_
* __Uitzondering: Waarschuwing: Het proberen om tot matrixcompensatie binnen toegang te hebben.. -> Calendar.php sinds verbetering aan ICU 74.1 (PHP Intl)__
Commerce meldt niet langer de volgende uitzondering in het bestand exception.log wanneer een winkel of handelaar de winkel of Admin bezoekt: `main.CRITICAL: Exception: Warning: Trying to access array offset on value of type null in /vendor/magento/framework/View/Element/Html/Calendar.php on line 114 in /vendor/magento/framework/App/ErrorHandler.php:62` . [ GitHub-38214 ](https://github.com/magento/magento2/issues/38214)
  _AC-11423 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38214) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38364)_
* __[Uitgave ] Oplossen van problemen met de Gegevens van de Klant wanneer de vorm element met naam`method`__ bevat
Het systeem identificeert nu correct het kenmerk &#39;method&#39; in formulierverzendingen, zelfs als een element met de naam &#39;method&#39; aanwezig is in het formulier. Dit zorgt voor een nauwkeurige verwerking van klantgegevens. Als een formulierelement voorheen de naam &#39;method&#39; had, zou dit problemen opleveren met de identificatie van het kenmerk &#39;method&#39; in formulierverzendingen, wat tot mogelijke problemen met de verwerking van klantgegevens zou leiden.
  _AC-11476 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38484) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38449)_
* &rbrack; Repareren PHPDocs van 0&rbrace; kwestie &lbrace;voor \Magento\Framework\Data\Collection::getItemById __PHPDocs voor de \Magento\Framework\Data\Collection::getItemById methode is bijgewerkt om ongeldig als mogelijk terugkeertype te omvatten, richtend kwesties met statische analysehulpmiddelen.__&lbrack; Eerder, specificeerde PHPDocs van de methode ongeldig als mogelijk terugkeertype niet, dat tot waarschuwingen of fouten in statische analyse leidde toen de methode in voorwaardelijke verklaringen werd gebruikt.
  _AC-11489 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38485) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38439)_
* __[Uitgave ] Alleen geldige voorkeuren toestaan tijdens`setup:di:compile`__
Het systeem genereert nu een fout tijdens de opdracht `setup:di:compile` als een voorkeur is gemaakt voor een klasse die niet bestaat of die specifiek is uitgesloten, zodat alleen geldige voorkeuren zijn toegestaan. Eerder, zouden deze scenario&#39;s ongemerkt ontbreken, potentieel die om het even welke stop-ins verbonden aan de originele klassen nutteloos teruggeven.
  _AC-11592 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38517) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/33161)_
* __Magento die probeert om read-only bezit in __ontwap methode van LoggerProxy__ te wijzigen
Het systeem staat nu de wijziging van eerder read-only eigenschappen in de methode __wakeup van LoggerProxy toe, die vlotte verrichting verzekert zonder gebruikers te dwingen om een alternerende actie aan te wenden. Eerder, zou een poging om de waarde van een read-only bezit in de methode __wakeup van LoggerProxy opnieuw toe te wijzen kwesties veroorzaken.
  _AC-11651 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38526) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c8f87c25)_
* &rbrack; AC-2039 wisselstroom-1667 van de 0&rbrace; Uitgave de verwijzingen van TinyMCE __Recentste versie met tinten bijgewerkt in composer.json__&lbrack;
  _AC-11681 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38533) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36543) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/b34c0a75)_
* __ChangelogBatchWalker werkt niet in veelvoudige draden__
Het systeem steunt nu procesvork voor indexatie MView, die fouten tijdens indexeruitvoering verhindert wanneer het werken op veelvoudige draden. Eerder, zou het runnen van ChangelogBatchWalker op veelvoudige draden tot de schrapping van lijsten leiden die door andere draden worden gebruikt, die een fout tijdens indexeruitvoering veroorzaken.
  _AC-11696 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38246) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38248)_
* __[Uitgave ] noemt verkeerd genoemde variabele__ anders
Het systeem noemt nu correct de variabele die de hoeveelheid geld bevat die nog kan worden teruggegeven, die verwarring tijdens het zuiveren verhinderen. Eerder werd deze variabele onjuist benoemd als totalResund, wat tot misverstanden voor ontwikkelaars zou kunnen leiden.
  _AC-11781 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38609) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36205)_
* __[Uitgave ] pas douaneattributen aan huidige verbinding via XML__ over
Het systeem staat nu toe dat douanekenmerken aan de huidige verbinding via XML worden overgegaan, die ervoor zorgen dat deze attributen correct worden getoond zelfs wanneer de verbinding de huidige pagina is. Eerder werden er geen aangepaste kenmerken weergegeven voor de huidige paginakoppeling omdat de methode getAttributesHtml() niet werd gebruikt voor de huidige koppeling.
  _AC-11809 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38500) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/30070)_
* __het ingebouwde geheime voorgeheugen FPC wordt gebroken in 2.4.7 voor sommige configuraties__
Het systeem slaat nu correct pagina&#39;s in het voorgeheugen op wanneer de parameter MAGE_RUN_CODE wordt geplaatst, die optimale prestaties verzekeren. Eerder werden pagina&#39;s niet in cache geplaatst onder deze omstandigheden, wat tot mogelijke prestatieproblemen leidde.
  _AC-11819 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38626) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38646) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0c53bbf7)_
* __[Uitgave ] de uitzondering behandelende inconsistentie van de moeilijke situatie tussen ontwikkelaar en productiemodi__
Het systeem behandelt nu consequent uitzonderingen tussen ontwikkelaar en productiemodi, die onverwachte omleiding aan de login pagina verhinderen wanneer een uitzondering wordt geworpen. Eerder, kon een inconsistentie in uitzonderingsbehandeling tot een omleiding aan de login pagina op productiemodus in plaats van het tonen van het uitzonderingsbericht leiden.
  _AC-11829 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38639) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37712)_
* __vervang &quot;PayPal Rekening&quot;vertaling in token_list.phtml__
Het systeem geeft de sectie voor betaalmethoden voor betaalrekeningen die als betaalbaar kunnen worden beschouwd nu het label &#39;&#39;Account&#39;&#39; in plaats van &#39;&#39;PayPal-account&#39;&#39; op de pagina Opgeslagen betalingsmethoden, waardoor deze representatiever is voor de functie ervan. Eerder werd deze sectie specifiek aangeduid als &quot;PayPal-rekening&quot;, wat misleidend was toen andere betaalmethoden voor betaalrekeningen werden toegevoegd die kenisbaar waren.
  _AC-11852 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35622) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37959)_
* __achterwaartse verenigbaarheid is verloren op Magento\Catalog\Model\ProductRepository klasse__
De klasse ProductRepository handhaaft nu achterwaartse verenigbaarheid door de klasse van de Helper van de Initialisatie als tweede parameter te herstellen, die ervoor zorgt dat de modules zich van deze klasse uitbreiden zoals verwacht. Eerder, resulteerde de schrapping van de Helper van de Initialisatie van de aannemer in de klasse ProductRepository in een verlies van achterwaartse verenigbaarheid, die gebruikers dwingt om een oplossing aan te wenden.
  _AC-11874 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38669)_
* __[Uitgave ] Statische inhoud opstellen - de fout van het Type__
Het systeem verwerkt lege LESS-bestanden nu correct tijdens de implementatie van statische inhoud, waarbij een foutbericht &quot;LESS-bestand is leeg&quot; wordt weergegeven. Eerder werd een fout met een onjuist type gegenereerd bij het optreden van een leeg LESS-bestand tijdens de implementatie.
  _AC-11905 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38682) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38683)_
* __[Uitgave ] [ Mening ] Verwijderde extra ruimte in verbinding en manuscriptmarkering__
Het systeem zorgt ervoor dat er geen extra ruimten in de verbinding en manuscriptmarkeringen zijn, die schonere en efficiëntere code verstrekken. Eerder konden dubbele ruimten tussen attributen in de verbinding en manuscriptmarkeringen worden gevonden.
  _AC-12002 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32920) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32919)_
* __[Uitgave ] vermijdt een misconfiguration oneindige lijn__
Het systeem vermijdt nu een oneindige lus door zelfreferentiële toewijzing in configuraties van virtuele typen te voorkomen. Dit zorgt ervoor dat de toepassing niet vastzit in een eindeloze lus wanneer wordt geprobeerd om een zelf-verwijzende knoop te dereference. Eerder, als een virtuele typeconfiguratie zelf-verwijzing was, zou het de toepassing veroorzaken om voor onbepaalde tijd te draaien.
  _AC-12127 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38822) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38794)_
* __Manager van Objecten niet gebruikt voor Magento\Csp\Model\Mode\Data\ModeConfigured__
Het systeem gebruikt nu op de juiste wijze Objectbeheer wanneer het ModeConfigured-object wordt gemaakt, zodat insteekmodules voor dit object kunnen worden gebruikt. Eerder werd Objectbeheer niet gebruikt, waardoor plugins niet konden worden toegepast op het ModeConfigured-object.
  _AC-12299 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38875) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38886)_
* __Onnauwkeurige documentblokopmerking in de Beeld van het Product en de Waarschuwingen van de Prijs__
De opmerking van het documentblok voor de deleteCustomer-methode in de productvoorraad- en prijswaarschuwingen is gecorrigeerd om correct weer te geven dat de methode alle waarschuwingen voor het voorraadproduct of de prijs van een bepaalde klant en website verwijdert, niet de klant van de website. Eerder werd in de opmerking onjuist aangegeven dat de methode bestond in het verwijderen van een klant van de website.
  _AC-12540 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38939) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39001)_
* __[Uitgave ] Gecompileerde config van het Gebruik voor geproduceerde gegevens in plaats van algemene config__
Het systeem gebruikt nu de gecompileerde configuratie voor geproduceerde gegevens in plaats van de algemene configuratie, die netwerkoverdracht en overhead van gegevens vermindert die van een bepaalde versie van code afhangt. Door deze wijziging wordt voorkomen dat cache wordt overschreven in gedeelde instanties tijdens het wisselen van containers. Dit leidt tot betere stabiliteit en minder downtime. Eerder, gebruikten bepaalde kernklassen het gedeelde configuratietype, dat tot geheim voorgeheugen het met voeten treden of toepassingsonderbreking wegens verschillen in codeversies over veelvoudige servers kon leiden.
  _AC-12594 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38785) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/29954)_
* __[Uitgave ] verwijdert verwijzingen naar dossiers uit uitbreidingen die in e1cdb werden verwijderd...__
Het systeem verwijdert nu verwijzingen naar dossiers uit gebieden die eerder werden verwijderd, die fouten in de browser console en het dossier van het systeemlogboek elimineren. Voorheen veroorzaakten deze verwijzingen fouten vanwege het ontbreken van de bestanden waarnaar wordt verwezen.
  _AC-12597 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38960) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38951)_
* &rbrack; Kleine schoonmaakbeurt van 0&rbrace; Uitgave __&lbrack;: het vaste verkeerde gebruik van sprintf, het neemt slechts 2 placeholders hier en w...__
Het systeem gebruikt nu correct de functie sprintf met het juiste aantal plaatsaanduidingen, waardoor de code schoner en consistenter wordt. Eerder werd de functie sprintf onjuist gebruikt met een extra argument, dat geen belangrijke kwesties veroorzaakte maar niet het correcte gebruik was.
  _AC-12778 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39062) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38628)_
* __PHP 8.2.15 verwijderde uitbreiding van FTP__
Het systeem bevat nu de FTP-extensie als een afhankelijkheid in het bestand composer.json, zodat de CSV-import correct kan worden geconfigureerd via FTP. Eerder werd een fout gegenereerd bij het configureren van CSV-import via FTP omdat de FTP-extensie ontbreekt in het PHP-pakket.
  _AC-12857 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39083) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/47b448e2)_
* &rbrack; Oplossingen van de kwestie __&lbrack;onjuiste klassen die in de modules van Magento worden van verwijzingen voorzien.__
Het systeem verwijst nu correct naar klassen in modules, waardoor de werking vloeiender wordt en vastlopen als gevolg van niet-bestaande klassen wordt voorkomen. Dit omvat een bugfix in de modules Indexer en Creditmemo, en de implementatie van HttpGetActionInterface in de klasse PrintAction. Eerder, leidden de onjuiste klassenverwijzingen tot fouten en potentiële systeemneerstortingen, en bepaalde functionaliteiten, zoals filename voor creditmemo PDF dossiers en het opnieuw indexeren van voorraden, werkten niet zoals verwacht.
  _AC-12869 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39126) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37784)_
* __Mogelijkheid om Gebied voor `dev:di:info` CLI bevel__ te bepalen
Het systeem staat ontwikkelaars nu toe om een gebied voor het `dev:di:info` CLI bevel te bepalen, dat het ontwikkeling en het zuiveren proces verbetert. Eerder kon deze opdracht alleen informatie weergeven voor het GLOBAL-gebied.
  _AC-12964 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38758) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38759)_
* __[Uitgave ] voegt isMultipleFiles bezit aan het malplaatje van het beeldvormelement toe__
Met deze correctie voorkomt u dat de knop &quot;Bladeren om hier een afbeelding te zoeken of te slepen&quot; verdwijnt wanneer een afbeelding wordt toegevoegd aan een formulierelement met meerdere bestanden.
  _AC-13149 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39219) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36325)_
* __opstelling:de verbetering ontbreekt met versie MariaDB 11.4 toe te schrijven aan charset &amp; sorteerveranderingen__
  _AC-13247_
* __[Uitgave ] verwijdert alle marketing krijgt parameters om het geheime voorgeheugen__ te minimaliseren
Het systeem verwijdert nu alle marketing parameters krijgen om geheim voorgeheugengebruik te optimaliseren, die de logica weerspiegelen die wordt gebruikt wanneer Varnish in gebruik is. Eerder, konden deze parameters tot geheim voorgeheugenopblazing en verminderde prestaties leiden.
  _AC-13279 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39266) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39099)_
* &rbrack; [ PHPDOC ] Correctie slechte phpdoc Magento\Directory\Model\AllowedCountries::getAllowedCountries () __De methode PHPDoc for the AllowedCountries::getAllowedCountries() is gecorrigeerd voor het verstrekken van nauwkeurige informatie, waardoor de documentatie helderder en nuttiger wordt.__&lbrack; Eerder bevatte de PHPDoc voor deze methode onjuiste informatie, die tot verwarring of misbruik van de methode kon leiden.
  _AC-13345 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39246) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39241)_
* __[Uitgave ] verwijdert één of andere code voor PHP versies wij niet meer steunen.__
Code verwijderen voor PHP-versies die niet meer worden ondersteund in Magento
  _AC-13348 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39361) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39202)_
* __[Uitgave ] maakt Adapter ImageMagick compatibel met php8 (Impliciete omzetting van vlotter aan int)__
Het systeem zorgt nu voor compatibiliteit met PHP8 door float getallen correct te verwerken bij het berekenen van de afmetingen van de afbeelding, zodat eventuele fouten door impliciete omzetting van float naar int worden voorkomen. Eerder kon de berekening van de afmetingen van de afbeelding leiden tot zwevende getallen, die bij impliciet afronden een fout zouden veroorzaken.
  _AC-13417 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39402) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37362)_
* __[Uitgave ] [ PHPDOC ] verbeter slechte phpdoc Magento\Framework\App\Config\ScopeConfigInterface__
Deze update verbetert de annotaties PHPDoc in Magento\Framework\App\Config\ScopeConfigInterface om nauwkeurig het type van het argument $scopeCode voor getValue en isSetFlag methodes te wijzen.
  _AC-13537 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39492) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39199)_
* __Magento\Framework\Filesystem\Driver\Http hangt van redenuitdrukking O.K. af__
Hiermee wordt de woordcontrole &quot;OK&quot; verwijderd uit Magento\Framework\Filesystem\Driver\Http::isExists
  _AC-13725 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39546) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39558)_
* __de indexeerder van het Net van de Klant werkt niet behoorlijk in Update door de wijze van het Programma__
Het eerdere raster van de Klant werd onmiddellijk bijgewerkt, maar nadat het raster van de Klant repareren is bijgewerkt na de uitloop, maar niet onmiddellijk wordt weerspiegeld.
  _AC-13810 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1da9ba6f)_
* __typefout op een JS dossier.__
Het systeem gebruikt nu correct de term &quot;abonnees&quot; in het JavaScript-bestand, zodat de verwante functies naar behoren kunnen functioneren. Eerder leidde een typografische fout in het JavaScript-bestand tot een onjuist gebruik van de term &quot;abonnees&quot;.
  _AC-6754 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36163) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36171)_
* __[Uitgave ] verwijdert verboden `@author` markering__
Het systeem voldoet nu aan de coderingsnormen door de verboden tag `@author` uit bepaalde modules te verwijderen, zodat u over een schonere en meer gestandaardiseerde code beschikt. Eerder was de tag `@author` in sommige modules aanwezig, wat in strijd was met de vastgestelde coderingsnormen.
  _AC-8353 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37253) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37003)_
* __[Uitgave ] verwijdert verboden `@author` markering uit `Magento_Customer` (deel 2)__
Het systeem voldoet nu aan de coderingsstandaard door de verboden tag `@author` uit bepaalde modules te verwijderen en zo een schonere en meer gestandaardiseerde code te garanderen. Eerder was de tag `@author` in sommige modules aanwezig, wat in strijd was met de vastgestelde coderingsnormen.
  _AC-8356 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37250) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37000)_
* __Ruimte in editorconfig syntaxisonderbrekingsregel voor [ {composer, auth}.json]__
Het systeem past nu correct een 4-spatie op de composer en auth.json dossiers toe, na een moeilijke situatie aan een syntaxisfout in editorconfig. Eerder waren deze bestanden vanwege een spatie in de bewerkingsconfig-syntaxis onjuist opgemaakt met een inspringing voor twee spaties.
  _AC-8659 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37394) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37395)_
* __[Uitgave ] verbetert het registreren van de cron fout__
Het systeem vangt en registreert nu zowel STDERR als STDOUT voor kroonprocessen, die waardevolle kenmerkende informatie in scenario&#39;s verstrekken waar de kantelprocessen ontbreken. Eerder, werden om het even welke foutenmeldingen binnen kroonprocessen niet geregistreerd, en STDERR en STDOUT voor kroongroepen die in afzonderlijke processen lopen werden verloren.
  _AC-8662 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37453) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32690)_
* __[Uitgave ] voegt wat meer kleuren aan de output van bepaalde opstellingskli bevelen toe__
Het systeem voegt nu meer kleuren toe aan de uitvoer van bepaalde CLI-opdrachten (setup Command Line Interface), waardoor de leesbaarheid en gebruikerservaring worden verbeterd. Eerder was de uitvoer van deze opdrachten moeilijker te lezen vanwege een gebrek aan kleurdifferentiatie.
  _AC-8984 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/29335) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/29298)_
* __Bevorderend Magento stelt algemeen/gebied/state_required terug wanneer het nieuwe land met vereiste staat/regio wordt toegevoegd.__
Het systeem voegt nu alleen het gewijzigde land toe aan de configuratie &#39;general/region/state_required&#39; wanneer een nieuw land met de vereiste staten wordt toegevoegd, zodat de aangepaste code niet wordt verstoord, ervan uitgaande dat de regio is uitgeschakeld. Eerder, zou het toevoegen van een nieuw land met vereiste staten de &quot;algemene/regio/staat_required&quot;configuratie terugstellen om landen met een vereiste staat in gebreke te stellen, potentieel brekend de winkel.
  _AC-9630 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37796) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38076)_
* __Verschil in minder compilatie tussen php &amp; nodejs bibliotheek (bot) met gecompliceerde `calc` uitdrukkingen__
Het verschil in minder compilatie tussen php- en nodejs-bibliotheek corrigeren (grijs) na update wikimedia/less.php:^5.x
  _AC-9712 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37841) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/b34c0a75)_
* __De fout van de &quot;Basis lijst of mening niet gevonden&quot;komt voor wanneer het gedeeltelijke indexeren wordt uitgevoerd__
De gedeeltelijke redex werkt nu correct met grote verandering in het geval van secundaire db verbinding
  _ACP2E-2692 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ba25af8a)_
* __Kwesties na bevordering MariaDB aan 10.5.1 of hoger__
Vaste de kwestie toen de datetime waarden in een OB in 0000-00-00 00 :00: 00 na verbetering Mysql zouden worden omgezet
  _ACP2E-2844 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a12063bd)_
* __het Type komt in Gegevens Vergelijking wanneer het controleren als het gegeven veranderingen heeft__ niet overeen
Eerder werd het opslagobject aangeroepen telkens wanneer geen gegevenswijzigingen werden aangebracht (voor numerieke gegevensvelden, zoals int/float/double). Het activeert de markering _hasDataChanges om waar te zijn en roept de opslagfunctie aan. Nadat deze correctie is toegepast, wordt de functie Save alleen aangeroepen als de gegevens zijn gewijzigd. De gegevenswaarde voor int/float/double-check met de waarde die aan de functie wordt doorgegeven en strikte overeenkomende typen.
  _ACP2E-2855 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/57a32313)_
* __[de invoer van de Wolk ] kan niet met folder var worden gebruikt__
Het product kan ongeacht de bestandsnaam worden geïmporteerd.
  _ACP2E-2959 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3a7c4d17)_
* __in iPad mini de menu en kopballadingen als mobiel, in plaats daarvan zouden zij als Desktop moeten laden.__
Het systeem behandelt apparaten met een breedte van 768 px als Desktop, die ervoor zorgen dat het menu en de kopbal correct laden. Eerder werden apparaten met een breedte van 768 px als mobiel beschouwd, waardoor het menu en de koptekst in een mobiele weergave werden geladen.
  _ACP2E-2966 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/35b1b1da) - [ GitHub codebijdrage ](https://github.com/magento/magento2-page-builder/commit/4d5db10a)_
* __de lijst of de mening van de Basis niet gevonden fout wanneer het runnen van mening krun terwijl het hebben van een verrichting DDL__
Het systeem behandelt nu correct de verrichtingen van de gegevensbestandupdate terwijl de meningsupdate op achtergrond loopt, die het voorkomen van &quot;de lijst van de Basis of mening niet gevonden&quot;fouten verhinderen. Eerder, konden sommige verrichtingen van de gegevensbestandupdate in de fout van de &quot;Basis tabel of mening niet gevonden&quot;resulteren, als de meningsupdate tezelfdertijd liep.
  _ACP2E-3046_
* __het Wijzigen van kolomlengte via db_schema.xml werkt niet in het geval van buitenlandse sleutels__
het wijzigen van kolom met buitenlandse sleutel via declaratief schema leidt nu niet tot fouten met MariaDB
  _ACP2E-3230 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/581b7ef1)_
* __sommige van de verbindingsverslagen worden bewaard aan OB wanneer het ordecord wordt bewaard__
Vóór de moeilijke situatie werden de onnodige vragen van de UPDATE teweeggebracht die een effect prestaties kunnen hebben wijze. Na de moeilijke situatie, werden de onnodige vragen van de UPDATE geëlimineerd.
  _ACP2E-3361 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1366ae5e)_
* __[CLOUD ] in admin zijn er vele fout javascript in console__
Eerder bevat het deelvenster Beheer veel JavaScript-fouten in de console. In het deelvenster Beheer zijn er geen JavaScript-fouten in de console en worden alle standaard JavaScript-functies zonder problemen uitgevoerd.
  _ACP2E-3375 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d75cff27)_
* __[Cloud ] Magento: het rijbericht is geschrapt__
De berichten van de rij worden nu behoorlijk ontruimd. Voorafgaand aan de moeilijke situatie, aangezien SQL het rijsysteem werd gebruikt, konden de nieuwe berichten worden geschrapt als het bericht van de schoonmaakrij tezelfdertijd liep.
  _ACP2E-3387 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d50f6b5d)_
* __de Overeenkomende geheim voorgeheugenzeer belangrijke ingangen zijn niet beschikbaar in geheim voorgeheugenmarkeringen, vandaar het geheime voorgeheugen schoonmaken werkt correct__
De LUA-modus is nu standaard ingeschakeld voor de opschoonfunctie voor cache van Redis om rasomstandigheden te voorkomen
  _ACP2E-3537 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a52ff98f)_
* __MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK waarde wordt genegeerd__
Na de correctie wordt een ENV-variabele die is ingesteld op &#39;false&#39;, behandeld als bool false, niet als tekenreeks &#39;false&#39;.
  _ACP2E-3681 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/982b1c42)_

### Framework, GraphQL

* __[Uitgave ] Introduceerde steun van douane scalaire types voor het schema van GraphQL__
Het systeem steunt nu douane scalar types voor het schema van GraphQL, toestaand ontwikkelaars om douane scalaire types en implementaties te bepalen. Deze functie kan vooral handig zijn voor het uitdrukken van waarden die moeten worden gevalideerd, zoals HTML, e-mails, URL&#39;s, datums, enzovoort, en voor meer geavanceerde gevallen zoals EAV-kenmerken. Eerder, steunde het systeem niet de verwerking van douane scalaire types in GraphQL.
  _AC-7976 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36877) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/34651) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0574ac23)_

### Kader, Product

* __2.4.8-beta1 EE Rapporten produceren niet toe te schrijven aan magento uitzondering__
  _AC-13011_

### Framework, UI Framework

* __Mogelijkheid om configuratiewaarde te beschrijven zelfs als het gesloten__ is
Eerder deze correctie kon de ontwerpconfiguratie niet worden ingesteld via bin/magento config:set-opdracht en vergrendelde waarden kunnen worden gewijzigd door het formulier met deze waarden te bewerken. Nadat de fix vergrendelde waarden zijn ingesteld vanuit cli met —lock-env of —lock-conf, kunnen deze niet meer worden bijgewerkt.
  _ACP2E-3324 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/55615e61)_

### GraphQL

* __Magento_GraphQl voert kopballen verwerking uit zelfs als de kopbalwaarde geen bevestiging__ overgaat
Het systeem zorgt er nu voor dat koptekstverwerking slechts eenmaal wordt uitgevoerd en alleen als de headerwaarde de validatie doorgeeft, de beveiliging verbetert en potentiële kwetsbaarheden voorkomt. Eerder werd koptekstverwerking uitgevoerd, zelfs als de headerwaarde niet was geslaagd voor validatie. Dit leidde tot potentiële kwetsbaarheden en onverwacht gedrag als gevolg van dubbele verwerking van headerwaarden.
  _AC-11729 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c8f87c25)_
* __de Fysieke opties van Giftcard hebben niet de juiste sorterende orde__
Het systeem sorteert nu correct de opties van fysieke cadeaukaartproducten wanneer deze via GraphQL worden aangevraagd, zodat een consistente rendering met het Luminantiemenu-thema wordt gegarandeerd. Eerder was de sorteervolgorde onjuist volgens luma-thema, wat leidde tot een onjuiste weergave en volgorde van opties zoals de naam van de afzender, de naam van de ontvanger en het bedrag.
  _AC-8951 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1bafc571)_
* __[het Geheime voorgeheugen van de Oplossing van GraphQL ] wordt ongeldig wanneer het Creëren/het uitgeven/het bewegen/het schrappen van een het Opslaan Update__
Het systeem zorgt er nu voor dat de resolver-cache niet ongeldig wordt gemaakt wanneer u een testupdate maakt, bewerkt, verplaatst of verwijdert, maar alleen wanneer de testupdate op de entiteit wordt toegepast. Eerder werd de oplossercache voortijdig ongeldig gemaakt, zelfs voordat de testupdate werd toegepast, wat tot onnodige cachevervalsingen leidde.
  _AC-9157 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0c53bbf7)_
* __het geheime voorgeheugen van de snelheid wordt niet ontruimd voor inhoud het opvoeren update__
GraphQL met de responscache voor de PageBuilder-inhoud wordt nu ongeldig wanneer de aan de PageBuilder-inhoud gerelateerde entiteiten worden bijgewerkt.
  _ACP2E-2642 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ba25af8a)_
* __het onbruikbaar maken Gelaagde Navigatie - verwijdert geen samenvoeging uit Grahql__
Het probleem is opgelost na het toepassen van de controle terwijl een productonderzoek met categoriesamenvoegingen door een vraag van GraphQL wordt gevraagd wanneer de admin configuratie die van &quot;Catalogus > Gelaagde Navigatie > de Filter van de Categorie van de Vertoning&quot;plaatst.
  _ACP2E-2653 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/12e071c3)_
* __de Vraag van de Producten van GraphQL die de prijsfilter {van:&quot;0&quot;} bevat keert geen resultaat__ terug
Eerder werd met het filter naar nulprijzen gezocht in grafische producten. Dit heeft helemaal geen resultaten opgeleverd vanwege een gegenereerde uitzondering. De zoekopdracht geeft nu resultaten zoals verwacht.
  _ACP2E-2928 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c971859e)_
* __Vertalingen voor de attributen van de klantenterugkeer die niet in GraphQL API voor respectievelijke StoreView__ worden weerspiegeld
Vertalingen voor de terugzendkenmerken van de klant worden weergegeven in de GraphQL API voor de betreffende StoreView.
Eerder werden de teruggavekenmerken van de klant voor de respectievelijke StoreView niet weerspiegeld in de GraphQL API.
  _ACP2E-2974 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ec7e32a9)_
* __[Cloud ] Gebroken vraag van GraphQL voor getPurchaseOrder met knoopcitaat__
De aanroep van de Purchase Order GraphQL kan de taak uitvoeren zonder dat er interne serverfouten optreden.
  _ACP2E-3128 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6f4805f8)_
* &rbrack; Configureerbare Producten van de Wolk __&lbrack;niet getoond in de Plaats van de Productie als het Product niet in &quot;Alle Mening van de Opslag&quot;__ wordt toegelaten
Het systeem geeft nu correct configureerbare producten op de site weer, zelfs als het product niet is ingeschakeld in &quot;Alle winkelweergaven&quot;, maar wel is ingeschakeld in specifieke weergavebereiken van de winkel.
Als een product eerder was uitgeschakeld in &quot;Alle winkelweergaven&quot; en alleen was ingeschakeld in specifieke weergavebereiken van de winkel, zouden de productkenmerken niet correct worden weergegeven in de GraphQL-reactie, waardoor het product niet correct wordt weergegeven.
  _ACP2E-3184 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/3f300077)_
* &rbrack; Grafiek van de Producten van de Wolk 1&rbrace; die fout hebben wanneer het zelfde eenvoudige product aan veelvoudige configureerbare producten __heeft toegewezen
Eerder, met afzonderlijke configureerbare producten met het zelfde eenvoudige product, keert grapQL een fout terug.__&lbrack; Nadat deze moeilijke situatie van toepassing is, verschillende configureerbare producten met het zelfde eenvoudige product, geeft grapQL resultaat zonder geen fout.
  _ACP2E-3190 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/148c3ead)_
* &rbrack; Uitgave van de Wolk __&lbrack;met de Authentificatie van de Gebruiker en de Symbolische Toegang van de Intersite in de Opstelling van de Multi-Plaats__
GraphQl-klantgegevens en vragen over winkelwagentjes bij de installatie van meerdere sites controleert of de klant op een niet-standaard website aanwezig is.
Eerder uitgevoerde query werkte zonder ervoor te zorgen dat de klant op een niet-standaard website in de installatie van meerdere sites aanwezig was.
  _ACP2E-3215 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/581b7ef1)_
* __GraphQL kart itemsV2 paginering werkt niet correct__
De kwestie is opgelost door de correcte waarde voor het huidige paginaargument in de inzamelingsvraag over te gaan. Eerder werd de verkeerde waarde doorgegeven om de huidige pagina in te stellen, waardoor de uitgave optrad.
  _ACP2E-3253 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/8459b17d)_
* __[GRAPHQL ] modelwaarde zou moeten worden gespecificeerd wanneer het krijgen van customerCart__
Met de GraphQL-query &#39;customerCart&#39; kan nu een leeg winkelwagentje worden gemaakt, zelfs als het aanhalingsteken niet beschikbaar is in de database. Eerder was deze bewerking mislukt vanwege problemen met landvalidatie tijdens het maken van de lege winkelwagen.
  _ACP2E-3255 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/fd5cf3af)_
* __[GraphQl ] De punten van de Uittreksel zijn zichtbaar via GraphQl maar niet zichtbaar op storefront__
Producten op de lijst weergeven die niet correct worden vermeld op verzoek van GraphQL. Welnu, de producten van vorklijsten worden gefiltreerd gebaseerd op verstrekte archiefcontext.
  _ACP2E-3380 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/55615e61)_
* __[GraphQL ] het wachtwoord e-mailinconsistentie van het Terugstellen tussen inhoud en onderwerp/verbinding__
Het probleem is opgelost door de correcte opslag te simuleren waar de rekening van de klant wanneer het verzenden van het verzoek van het wachtwoordterugstellen, ongeacht de websiteopslag wordt geregistreerd.
  _ACP2E-3404 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/5184c067)_
* &rbrack; de vraagwinst van GraphQL van de 0&rbrace; wolk &lbrace;verwante die producten niet aan huidige website __worden toegewezen
Eerder, voor graphQL vraag, multi-store verwante producten tonen niet behoorlijk voor productvraag.__&lbrack; Nadat deze moeilijke situatie wordt toegepast, voor producten, vraag graphQL verwante producten die dienovereenkomstig worden getoond multi-store.
  _ACP2E-3419 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_
* __Gebruikend onjuiste identiteitskaart van de Opslag in de kopbal van GraphQL veroorzaakt fatale geheugenfout__
Het verzenden van onjuiste winkelcode in een GraphQL-aanvraag leidt niet langer tot overmatig geheugengebruik.
  _ACP2E-3447 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d50f6b5d)_
* __[wolk ] 500 reactie op lege Grafiekreactie op 2.4.7__
Na de moeilijke situatie, zullen de ongeldige grafiekverzoeken niet in het exception.log dossier worden geregistreerd.
  _ACP2E-3467 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1984c61c)_
* __[Cloud ] Problemen met Grafiek API__
Vóór de moeilijke situatie door de toepassingsserver te gebruiken Graphql, het verzoek van het klantenadres kwam niet de meest recente gegevens terug.
  _ACP2E-3492 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3f12d152)_
* __Gehandicapte product verschijnt nog in verwant, upsell, dwarselt punten in vraag grpahQL__
Grahql biedt nu de juiste reactie voor gehandicapte gerelateerde, upsell- en cross-selproducten
  _ACP2E-3505 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d4de4726)_
* __[CLOUD ]: De fout van GraphQl Interne de mutatie van de serverfout placeOrder__
De &quot;placeOrder&quot;-mutatie met couponcode-informatie in de aanvraag genereert niet langer een interne foutuitzondering, omdat de volgorde correct is geplaatst. Eerder is dit mislukt met &quot;Interne serverfout&quot;.
  _ACP2E-3647 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/982b1c42)_
* __disconto_percentage wordt niet berekend voor bundelproducten met dynamische prijs__
Correctie toegevoegd voor korting_percentage van product.price_details die niet de correcte waarde voor bundelproducten tonen met dynamische prijs toegelaten en kortingscoupon toegepast.
  _LYNX-426_
* __de producten van de bundel tonen nog &quot;IN_STOCK&quot;wanneer één van zijn gebundeld product uit voorraad__
Het probleem waarbij bundelproducten nog steeds &quot;IN_STOCK&quot; vertoonden, is opgelost, zelfs als een van hun gebundelde producten uit voorraad was.
  _LYNX-485_
* __niet_available_message en only_x_left_in_stock toont niet de zelfde beschikbare voorraad__
Oplossing van de kwestie waar not_available_message en only_x_left_in_stock inconsistente voorraadbeschikbaarheid toonden
  _LYNX-486_
* __original_row_total gebied die onjuiste waarde terugkeren__
Het probleem is opgelost met het veld original_row_total, dat onjuiste waarden retourneerde toen er aangepaste opties waren geselecteerd
  _LYNX-488_
* __gegroepeerde productduimnagel zou volgens de configuratie moeten worden getoond     .__
Het probleem is opgelost zodat de miniatuur van het gegroepeerde product wordt weergegeven volgens de configuratie-instellingen
  _LYNX-503_
* __Fout wanneer het vragen selected_options in OrderAddress__
Bijgewerkte AttributeSelectedOptions aan custom_attributesV2 in de reactie van GraphQL van het ordeadres.
  _LYNX-510_
* __original_item_price omvat geen kortingen__
Originele_item_prijs is bijgewerkt om kortingen op te nemen.
  _LYNX-512_
* __niet beschikbaar bericht toont niet de beschikbare inventarishoeveelheid__
Oplossing van het foutenbericht en de foutencode voor de mutatie AddProductsToCart om zich met de &quot;niet beschikbare&quot;berichtconfiguratie te richten
  _LYNX-530_
* __&quot;OUT_OF_STOCK&quot; status retourneert op Eenvoudig met aangepaste optieproducten met opties voor meerdere selecties__
De StockStatusProvider resolver in het inventarispakket is bijgewerkt om stock_status voor eenvoudige producten met douaneopties te bevestigen.
  _LYNX-532_
* __Fout (GQL): cart.itemsV2.items.product.custom_attributesV2 keert een serverfout__ terug
Oplossing voor de serverfout die optrad toen een kartvraag de douanekenmerken van een product door een product zonder enige douanekenmerken toe te voegen omvatte.
  _LYNX-533_
* __orders/date_of_first_order altijd terugkerend ongeldig__
Oplossing voor het probleem waarbij orders > date_of_first_order altijd null retourneerden.
  _LYNX-536_
* __de Klant moet niet een gedeeltelijk verscheepte orde kunnen annuleren__
Validatie is toegevoegd om te voorkomen dat klanten een gedeeltelijk verzonden bestelling annuleren.
  _LYNX-544_
* __de codes van de Fout voor ordecorrectie die op het foutenbericht wordt gebaseerd__
De foutcodes voor annulering van een bestelling zijn nu gebaseerd op het specifieke foutbericht.
  _LYNX-548_
* __Beweeg terug koekjesgerelateerde eigenschappen van privé aan beschermde__
Hiermee wordt de zichtbaarheid van de eigenschappen van de klasseconstructor Magento\Framework\App\PageCache\Version hersteld van private naar protected
  _LYNX-581_
* __de maximum standaard de vraagingewikkeldheid van GraphQL van de verhoging aan 1000__
De standaard maximale complexiteit van GraphQL-query is verhoogd van 300 naar 1000.
  _LYNX-600_
* __GQL - itemsV2 > Origineel rijtotaal, de prijzen van de prijswaaier zijn teruggekeerd als $0.00 voor downloadbaar product met dossieropties die afzonderlijke prijzen hebben.__
Probleem opgelost waarbij downloadbare producten met afzonderlijke opties voor het aanschaffen van koppelingen $0 retourneerden voor objecten V2 > Totaal van originele rij, met een prijsbereik van $0,00 voor producten met bestandskeuzeopties met afzonderlijke prijzen.
  _LYNX-620_
* __Schema van een lijst wanneer wordt gecreeerd gloednieuw dan wanneer bevordering__
Oplossing voor een probleem waarbij het toevoegen van een nieuwe VARCHAR-kolom aan een bestaande tabel testfouten veroorzaakte als gevolg van schemaverschillen tussen nieuwe installaties en upgrades. Met de methode modifyColumn() worden VARCHAR-kolommen nu op de juiste wijze afgehandeld door de standaardtekenset en -sortering in te stellen.
  _LYNX-711_
* __Compatibiliteit GraphQl voor PHP-8.4 Versie__
Oplossing voor GraphQL compatibiliteitsproblemen met PHP 8.4 voor meerdere oplosmiddelen, waardoor een vloeiende functionaliteit werd gegarandeerd. Gewijzigde bestanden in de modules CatalogRule, Klant, Cadeaubericht, Cadeaukaart en Cadeauverpakking.
  _LYNX-772_

### GraphQL, Inventaris/MSI

* __de mutatie MergeCart werpt uitzondering wanneer de bron en de bestemmingshavens de zelfde bundelpunten__ hebben
&#39;-
  _ACP2E-2607 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/c971859e) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/db0620da)_

### GraphQL, Inventory / MSI, prestaties

* __Plaats neer na verbetering__
De prestaties van het halen van bundelproducten door GraphQl worden verbeterd.
  _ACP2E-1716 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/ba25af8a) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/bdbf97ea)_

### GraphQL, prestaties

* __[GraphQL Resolver ] De gegevens van de Oplossing van de Klant worden niet ongeldig gemaakt van de Invoer__
De GraphQL-cache voor klantoplossingers wordt nu ongeldig gemaakt, zoals u had verwacht, wanneer een klant door import wordt bewerkt of verwijderd. Eerder is de cache niet ongeldig gemaakt en konden de klantgegevens tijdens het importeren worden bewerkt of verwijderd.
  _AC-9569 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0574ac23)_

### GraphQL, zoeken

* __GraphQL het sorteren van de productlijst door veelvoudige parameters werkt niet__
Het sorteren van producten op meerdere velden in GraphQl werkt nu zoals beschreven in de documentatie
  _ACP2E-2809 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c971859e)_
* __de lijst van het Product GraphQL vraag beperkt tot total_count 10.000 slechts producten__
Na de correctie is het zoekresultaat niet beperkt tot 10000 producten, maar wordt het mogelijk om alle producten die aan de zoekcriteria voldoen, ook als het aantal meer dan 10000 is.
  _ACP2E-948 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4cf5e62)_

### GraphQL, testkader

* __Magento\GraphQl\App\GraphQlCustomerMutationsTest.php de mislukking van de Test van de Integratie__
&#39;-
  _ACP2E-3363 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4cf5e62)_

### Importeren/exporteren

* __Uitgave bij productinvoer wanneer voorzien van douane opties-type: het dossier (het Gemaakt Product bevat geen prijs voor douane-optie en toont slechts de eerste verstrekte dossiertype uitbreiding)__
Het systeem importeert nu op de juiste wijze productgegevens met aangepaste opties van het type &#39;file&#39;, zodat alle beschikbare bestandsextensies worden weergegeven en de prijs voor de aangepaste optie wordt opgenomen. Eerder werd tijdens het importeren van producten alleen de eerste extensie weergegeven en ontbrak de prijs voor de aangepaste optie als een aangepaste optie van het type &#39;file&#39; was voorzien van meerdere bestandsextensies.
  _AC-12172 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38805) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38926)_
* __Verkeerde uitvoeringstijd voor de invoerverrichting in het net van de Geschiedenis van de Invoer__
De uitvoeringstijd van het importrapport wordt correct onafhankelijk van de beheerlandinstelling weergegeven.
  _ACP2E-2710 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ea79f7dd)_
* __Dubbele klanten die met het zelfde e-mailadres worden gecreeerd gebruikend de invoer__
Importeren van de klant terwijl Account Sharing is ingesteld op Global, geïmporteerde klant die in het systeem aanwezig is, wordt bijgewerkt.
Eerder geïmporteerde klant is gedupliceerd.
  _ACP2E-2737 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c971859e)_
* __voeg/werk de Invoer op Producten toe die Aanpasbare Opties dupliceren__
Het probleem is opgelost door de juiste opslagruimte toe te wijzen aan productopties tijdens de CSV-import.
Eerder, toegewezen aan de admin store in plaats van hun respectieve opslag.
  _ACP2E-2902 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3a7c4d17)_
* __Klant &quot;created_at&quot;datum niet Omgezet om tijdzone op te slaan op de uitvoer__
Een kolom &quot;created_at&quot;datumwaarde wordt omgezet in het juiste datumformaat dat op de opslag timezone in de de uitvoerCSV van de klant wordt gebaseerd.
  _ACP2E-2990 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3056e9cb)_
* __[Wolk ] die fout terwijl het controleren van de gegevens in de invoergegevens gebruikend CSV__ krijgt
Er is geen fout opgetreden tijdens het controleren van de gegevens tijdens het importeren van CSV-bestanden. Eerder werd het volgende foutbericht weergegeven: &quot;We kunnen geen klant vinden die deze e-mail- en websitecode in rij(en): 1 aanpast wanneer de gegevens in de importsectie worden gecontroleerd met gebruik van CSV vanuit de beheerder.
  _ACP2E-3165 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/8459b17d)_
* __knoop van de Invoer mist__
Los het probleem met de ontbrekende knop Importeren op nadat de gegevens zijn gecontroleerd met de juiste en onjuiste records in de CSV. Eerder wordt de knop Importeren niet weergegeven na gegevenscontroles met juiste en onjuiste records in de CSV.
  _ACP2E-3172 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1819fe73)_
* __Uitgevoerd klantenadres kan niet worden ingevoerd__
Het adres van de klant wordt naar behoren geïmporteerd. Voorheen zou een bestand met het importeren van klantadressen geen validatie doorstaan als Share Customer Accounts = Global, en er zijn twee websites waar de standaardwebsite een lijst met landen met beperkingen heeft en het adres dat wordt geïmporteerd, geldt voor een andere website waar toegestane landen verschillend zijn
  _ACP2E-3382 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ec7e32a9)_
* &rbrack; Verkeerde hoeveelheid van de Wolk __&lbrack;in Csv- dossier gaf geen fout__
Importeren van aandelenbronnen genereert nu een validatiefout voor niet-numerieke waarden in de kolom Aantal. Eerder werd bij het importeren van voorraadbronnen met een niet-numerieke waarde in de kolom Hoeveelheid de hoeveelheid ingesteld op 0.
  _ACP2E-3448 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/5b21b7af)_
* __Gedupliceerde URL zeer belangrijke die foutenmelding wanneer het invoeren van een product wordt geproduceerd is niet correct wanneer Sleutel URL reeds tot een categorie__ behoort
De juiste foutmelding wordt weergegeven tijdens de controle van het importeren van producten, wanneer de klant heeft geprobeerd het product te importeren wanneer de URL-sleutel van het product al tot een categorie behoort.
  _ACP2E-3455 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d4de4726)_
* __de uitvoer van het Product veroorzaakt OOM zelfs met 4G geheugengrens__
Vóór deze correctie kon het product niet worden geëxporteerd als productkenmerken duizenden optiewaarden hadden, zelfs niet als er 4G geheugen beschikbaar was. Na deze correctie moet het exportbestand van het product het CSV-bestand hebben geëxporteerd.
  _ACP2E-3475 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1984c61c)_
* &rbrack; de Processen van de Invoer van 0&rbrace; Wolk die met elkaar __in wisselwerking staan
De correcte berichten worden getoond als de zelfde admin gebruiker twee of meer invoerverrichtingen gebruikend de zelfde gebruikerszitting uitvoert.__&lbrack;
  _ACP2E-3527 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d4de4726)_

### Importeren/exporteren, prestaties

* __&lbrack;de invoertijd van het 1&rbrace; Product van de Wolk &lbrace;is beduidend gestegen__
Vóór de correctie was er een aanzienlijke tijdsvermindering bij het importeren van catalogusproducten met meer dan 10 k items. &rbrack; Na de correctie wordt het importeren van het catalogusproduct tijdig uitgevoerd.
  _ACP2E-3476 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/87d012e5)_

### Installeren en beheren

* __de verbetering van Magento ontbreekt op MariaDB 11.4 + 2.4.8-bèta1__
De upgrade moet zonder fouten worden uitgevoerd.
  _AC-13242 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7b336d0a)_
* __Geen VCL van de Uitvoer voor Varnish 7 knoop in admin paneel__
De knop VCL exporteren voor VCL 7 is toegevoegd aan het deelvenster Beheer.
  _ACP2E-2102 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4fbf702)_

### Inventaris/MSI

* __update van de Inventaris van het Configurable Product ontbreekt wanneer het gegevensbestand prefixen__ gebruikt
Het systeem werkt nu correct de inventaris van configureerbare producten bij wanneer het gegevensbestand prefixen gebruikt, om het even welke foutenmeldingen te verhinderen en ervoor te zorgen dat het correcte aantal wordt bewaard. Eerder, zou een fout voorkomen wanneer het proberen om de inventarishoeveelheid voor eenvoudige producten binnen een configureerbaar product te bewaren als het gegevensbestand prefixen gebruikte.
  _AC-10750 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38045)_
* __Google API sleutel van Google werkt niet terwijl het toevoegen van Kaart met attributen__
Het systeem biedt nu ondersteuning voor de nieuwste versie 3.56 van de Google Maps API, waarmee gebruikers met succes een Kaart-inhoudsblok van het menu PageBuilder aan het werkgebied kunnen toevoegen zonder fouten te ondervinden. Eerder konden gebruikers geen Map-inhoudsblok toevoegen vanwege compatibiliteitsproblemen met de Google Maps API-versie. Dit leidde tot een foutbericht dat er iets fout was.
  _AC-11593 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0574ac23)_
* __Onbekwaam om verzending voor ordepunt met veelvoudige bronnen en bedorven SKU tot stand te brengen__
Eerder wanneer spaties per ongeluk via de database in de sku werden toegevoegd, treedt een fout op in de verzendpagina die nu vast is en automatische bijsnijden wordt beschouwd als een menselijke fout en er is geen effect gevonden. Daarom is de verzending voltooid.
  _AC-13922 - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/c18eb5fa)_
* &rbrack; De producten van de Bundel van de 0&rbrace; Test &lbrace;met 0 voorraad die op de voorzijde van de opslagplaats __toont
Het bundelproduct wordt niet weergegeven op de aanvullende websites die gebruikmaken van extra voorraad.__&lbrack;
  _ACP2E-1411_
* __[de Kritieke Uitgave van de Wolk ] met Product dat met Lege Plaatsen van een lijst maakt__
Het systeem geeft nu correct productlijsten weer zonder lege ruimten wanneer producten op &quot;Out of Stock&quot; zijn ingesteld, zodat de beschikbare producten op consistente en nauwkeurige wijze worden weergegeven. Als u een product eerder instelt op &#39;Uit voorraad&#39;, wordt er een lege ruimte weergegeven in de productlijst, waardoor de layout wordt verstoord en klanten mogelijk in verwarring raken.
  _ACP2E-2794 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/ea79f7dd) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/b59e48ca)_
* __Onbekwaam om de orde te verschepen wanneer MSI ophaalopslag wordt toegelaten__
Verbeterde voorraadprestaties van het creëren van verscheping in het geval van vele bronnen met in-store bestelwagen
  _ACP2E-3335 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/9f3e63d1)_
* __Cron herdex ontbreekt om productbeschikbaarheid op frontend bij te werken__
Eerder stonden de producten niet meer op de voorgrond nadat de status van de backorder via de REST API was bijgewerkt. Nadat u de status van de backorder hebt bijgewerkt via de REST API, worden de producten weergegeven als in voorraad.
  _ACP2E-3355 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/e6fe0aa7)_
* __Toevoegend beelden aan configureerbaar niet werkend wanneer MSI wordt toegelaten.__
Uploaden van images voor configureerbaar product werkt nu zoals u had verwacht wanneer de voorraadmodule wordt gebruikt. Eerder werkte het uploaden van de afbeelding niet
  _ACP2E-3357 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/fdf409aa)_
* __Uitgave met Bundel Product + MSI in Schone M2.4.7-p3__
Eerder, voor inventarisbundelproducten na duplicatie met hetzelfde eenvoudige product, kan het eenvoudige product niet worden opgeslagen. Nadat deze correctie is toegepast, kan het eenvoudige product zonder uitzonderingen worden opgeslagen.
  _ACP2E-3470 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39358) - [ GitHub codebijdrage ](https://github.com/magento/inventory/commit/0208e433)_

### Inventaris/MSI, zoeken

* __Alle producten worden geïndexeerd met [ is_out_of_stock ] = 1 wanneer SKU niet als onderzoekbare attributen__ wordt geplaatst
Na de correctie is &quot;is_out_of_stock&quot; in de zoekindex van de catalogus correct, zelfs als de sku niet doorzoekbaar is.
  _ACP2E-3413 - [ de codebijdrage van GitHub ](https://github.com/magento/inventory/commit/5b21b7af)_

### Volgorde

* __het overzichtsscherm van de orde van het achtereind: De achtergrond rangschikte hoeveelheid niet zichtbaar op het niveau van het orde punt__
Het systeem geeft nu het aantal achtergeordende items weer in de kolom Aantal op het scherm met het overzicht van de achterste volgorde. Dit zorgt ervoor dat de gebruikers de status van alle punten in een orde nauwkeurig kunnen volgen. Eerder gaf de kolom Aantal alleen het aantal objecten weer dat was besteld, gefactureerd en verzonden, maar niet het aantal objecten met een backorder.
  _AC-10828 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38252) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38320)_
* &rbrack; Verkeerde opslagidentiteitskaart van 0&rbrace; Uitgave &lbrace;die in Renderer van het Adres van de Orde wordt gebruikt __Het systeem gebruikt nu correct de opslag-id die aan een bestelling is gekoppeld bij het weergeven van het besteladres, zodat de adressen correct zijn opgemaakt op basis van hun respectievelijke winkel-id.__&lbrack; Eerder gebruikte het systeem onjuist de huidige winkel-id, wat tot een onjuiste adresnotatie kan leiden wanneer meerdere bestelling-e-mails van verschillende winkels moeten worden verzonden.
  _AC-10994 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38412) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37932)_
* __JoinProcessor caching kwestie__
Het systeem past nu correct JoinProcessor voor elke herhaling toe, zelfs met opeenvolgende vraag, die nauwkeurige gegevensterugwinning verzekeren. Eerder werd de JoinProcessor onjuist gemarkeerd, zoals al werd toegepast in opeenvolgende herhalingen, wat leidde tot fouten in het ophalen van gegevens.
  _AC-11690 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/27504) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37550)_
* __[Uitgave ] Verzendprijs die verschillend in gedrukte pdf__ toont
Het systeem geeft nu de verzendprijzen correct weer in afgedrukte PDF&#39;s volgens de instellingen voor de belastingconfiguratie, zodat de weergavepagina van de verkooporder en de afgedrukte factuur consistent zijn. Eerder was de verzendprijs die in de afgedrukte PDF werd weergegeven exclusief belasting, ongeacht de instellingen voor de belastingconfiguratie.
  _AC-11798 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38608) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38595) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1bafc571)_
* __opnieuw orde met een geschrapt ouder configureerbaar product__
Tijdens het opnieuw ordenen met het verwijderde product wordt de knop Opnieuw ordenen niet weergegeven
  _AC-13839 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39568) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39601)_
* &rbrack; Repareren slechte \Magento\Sales\Model\Order\Email\Container\Template: Het bezit van 0&rbrace; Uitgave __Dit corrigeert het slechte phpdoc voor \Magento\Sales\Model\Order\Email\Container\Template:$id, eigenlijk is $id type int, maar in werkelijkheid is het string.__&lbrack;
  _AC-13924 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39151) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39150)_
* __Onbekwaam om veranderingen in telefoonaantal in bestaande ordedetails te bewaren__
De gebruiker kan nu het internationale voorvoegsel 00 toevoegen in het telefoonveld van het orderadres
  _ACP2E-2622 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38201) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/12e071c3)_
* __E-mail ontbreekt te verzenden__
Het systeem omvat nu een configuratieoptie async_sending_probeerde om het aantal pogingen te specificeren om een e-mail te verzenden alvorens tegen te houden, verbeterend de behandeling van ontbroken e-mail verzendt wanneer &quot;Asynchroon verzenden&quot;wordt toegelaten. Als het verzenden van een e-mail mislukt, probeert het systeem het bericht voortdurend opnieuw te verzenden, wat resulteert in een eindeloze lus met foutberichten in het systeemlogboek.
  _ACP2E-2734 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b2286ecf)_
* __[de Status van de Orde van de Wolk ] veranderde om te voltooien wanneer gedeeltelijke terugbetaling van een gedeeltelijk verscheepte orde__
Bij het uitgeven van een creditnota, wordt de ordestatus niet meer veranderd in &quot;voltooid&quot;als er voorwerpen zijn die nog niet zijn verscheept.
  _ACP2E-2756 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7e0e5582)_
* __[CLOUD ] kan verzenden geen E-mail van Admin UI zoals Dev Docs toont__ onbruikbaar maken
Het systeem voorkomt nu op de juiste wijze dat e-mails worden verzonden wanneer e-mailcommunicatie is uitgeschakeld. Deze e-mailberichten worden niet meer verzonden wanneer de e-mailcommunicatie opnieuw wordt ingeschakeld. Eerder werden e-mailberichten over verkopen die waren gestart terwijl e-mailcommunicatie was uitgeschakeld, nog steeds verzonden zodra de e-mailcommunicatie opnieuw was ingeschakeld.
  _ACP2E-3002 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c8931218)_
* __orde gesloten zonder volledig teruggegeven__
Het systeem behoudt nu correct de status van de bestelling als &#39;Verwerking&#39; en de status van de factuur als &#39;In behandeling&#39; wanneer een bestelling met een niet-vastgelegde betaling een transport heeft gemaakt. Dit zorgt ervoor dat orders alleen als &#39;Gesloten&#39; worden gemarkeerd nadat ze volledig zijn terugbetaald. Als u eerder een verzending maakt voor een bestelling waarvoor een factuur in behandeling is, wordt de status van de bestelling onjuist gewijzigd in &#39;Gesloten&#39;.
  _ACP2E-3045 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6a185204)_
* __[de Wolk ] kan orde in admin op één opslag tot stand brengen als slechts het Standaard het Factureren Adres niet opstelling__ was
Relevant foutbericht &quot;Er bestaat al een klant met hetzelfde e-mailadres op een gekoppelde website.&quot; wordt getoond als een klant geen Standaard het Factureren Adres heeft en probeert om een orde op een andere opslag tot stand te brengen.
  _ACP2E-3311 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d75cff27)_
* __Admin gedupliceerde verzonden verzoeken van de plaatsorde__
Eerder kon op de knop &quot;Bestelling verzenden&quot; in het deelvenster Beheer meerdere keren worden geklikt of geactiveerd door herhaaldelijk op de toets &quot;Enter&quot; te drukken, waardoor dubbele verzendingen of bestellingen met een fout konden worden uitgevoerd. Nu, verhinderend extra acties tot de orde volledig wordt verwerkt, die ervoor zorgen dat slechts één orde wordt voorgelegd.
  _ACP2E-3416 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/5184c067)_
* __Admin kan orde zelfs zonder betalingsmethode nog plaatsen__
Eerder geselecteerde betalingsmethode blijft nu behouden wanneer de betalingsmethode opnieuw wordt weergegeven in de lijst met beschikbare betalingen.
  _ACP2E-3425 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d50f6b5d)_
* __Punten worden gedupliceerd nadat wij een orde van Admin op - browser Mozilla Firefox__ creëren
Producten die worden toegevoegd met &quot;Producten toevoegen door SKU&quot;, worden niet meer gedupliceerd in Firefox wanneer een bestelling wordt gemaakt in admin.
  _ACP2E-3518_

### Bestelling, betalingen

* __Admin kan orde zelfs zonder betalingsmethode nog plaatsen__
Eerder kon de handelaar orders van het admin paneel plaatsen zonder een betalingsmethode te selecteren. Nu is de handelaar verplicht een betalingsmethode te gebruiken om een bestelling te plaatsen.
  _ACP2E-3233 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/fd5cf3af)_

### Order, Returns

* __de teruggave van de Orde resulteert in dubbel creditnota__
Het afgeven van de restitutie via REST API wanneer twee identieke aanvragen tegelijkertijd werden uitgevoerd, leidt niet langer tot dubbele creditmemo&#39;s.
  _ACP2E-2982 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a4fbf702)_

### Bestelling, belasting

* __[CLOUD ] Onjuiste base_row_total in RESTFUL orde API wanneer het toelaten van grensoverschrijdende transacties en het toepassen van couponkortingen__
Correcte base_row_total wordt nu geretourneerd uit de RESTFUL order API wanneer grensoverschrijdende transacties zijn ingeschakeld en couponkorting wordt toegepast.
  _ACP2E-3003 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/9af794a4)_

### Overige

* __[Braintree ] online terugbetaalde opslagtransactie als transactie-id-terugbetaling__
  _BUNDLE-3394_
* __[Braintree ] + [ CLOUD ] Braintree (creditcard) bevelen niet om de lasten__ te verdelen
  _BUNDLE-3421_
* __[Braintree ] [ het SSL Certificaat van de Wolk ] van Braintree verloopt tegen 30 Juni__
  _BUNDLE-3422_
* __private_content_version koekje dat in vragen GQL is teruggekeerd__
Probleem verholpen waarbij het cookie private_content_version werd geretourneerd in GraphQL query&#39;s, zelfs als het sessiecookie was uitgeschakeld. Het cookie wordt niet meer opgenomen in GraphQL-reacties wanneer de sessie is uitgeschakeld, zoals u had verwacht.
  _LYNX-339_
* __fout van de Server op e-mailsteunen in fysieke vragen van de giftekaart__
Probleem verholpen waarbij query&#39;s voor zender_email en receiving_email op fysieke cadeaukaarten tot een serverfout leidden. Deze props worden nu correct geretourneerd voor virtuele cadeaukaarten en het querygedrag is consistent.
  _LYNX-366_
* __is_available attributen in CartItemInterface keert altijd vals voor configureerbare producten__ terug
Probleem verholpen waarbij het kenmerk is_available in CartItemInterface altijd false retourneerde voor configureerbare producten in de voorraad. Nu geeft het de beschikbaarheid correct weer, indien van toepassing.
  _LYNX-380_
* __is_available attributen in CartItemInterface keert waar terug zelfs wanneer de verkoopbare voorraad lager is dan de hoeveelheid van het product__
Probleem verholpen waarbij het kenmerk is_available in de CartItemInterface onjuist true retourneerde, zelfs wanneer de hoeveelheid van het winkelwagentje groter was dan de verkoopbare voorraad.
  _LYNX-382_
* __only_x_left_in_stock attribuut in ProductInterface is niet nauwkeurig op configureerbare producten__
Probleem verholpen waarbij het kenmerk only_x_left_in_stock in ProductInterface de beschikbare voorraad voor configureerbare productvarianten in het winkelwagentje niet nauwkeurig weerspiegelde. Nu, beantwoordt only_x_left_in_stock waarde correct aan de daadwerkelijke variantvoorraadniveaus, die nauwkeurige inventarisgegevens verzekeren in de vraag van GQL van de Kar wordt teruggekeerd.
  _LYNX-395_
* __placeholder duimnagel keert terug wanneer een eenvoudig product aan kar binnen een gegroepeerd product__ werd toegevoegd
Probleem verholpen waarbij het toevoegen van een eenvoudig product (onderdeel van een gegroepeerd product) aan het winkelwagentje een plaatsaanduidingsminiatuurafbeelding retourneerde, zelfs als het product een toegewezen afbeelding had.
Details herstellen:
* De miniatuur van het product geeft nu correct de toegewezen afbeelding weer, indien beschikbaar.
* De miniatuurselectie respecteert de onderstaande beheerdersconfiguratie:
Winkels > Configuratie > Verkoop > Afhandeling > Winkelwagentje > Gegroepeerde productafbeelding.
Dit zorgt voor consistent miniatuurgedrag voor gegroepeerde producten op basis van opslaginstellingen.
  _LYNX-399_
* {de attributen van de de douaneoptie van de klant van 0} het werken niet met geheelwaarden __Probleem verholpen waarbij de aangepaste optiekenmerken van de klant niet werkten wanneer de geretourneerde waarde een geheel getal was.__ De aangepaste opties verwerken nu correct de waarden van gehele getallen en retourneren deze zoals verwacht.
  _LYNX-400_
* __Interne serverfout wanneer het proberen om priceDetails voor de producten van de Bundel met dynamische prijs te krijgen__
Probleem opgelost waarbij het opvragen van price_details voor bundelproducten met dynamische prijsstelling via GraphQL tot een interne serverfout leidde. Deze verbetering verzekert stabiele wortelvragen wanneer het werken met bundelproducten die met dynamische tarifering worden gevormd.
  _LYNX-402_
* __only_x_left_in_stock keert altijd 0 voor configureerbare producten__ terug
Oplossing van een kwestie waar het only_x_left_in_stock attribuut altijd 0 voor configureerbare producten terugkeerde wanneer toegevoegd gebruikend ouderSKU met opties.
Details herstellen:
* De waarde only_x_left_in_stock geeft nu nauwkeurig de voorraad van de geselecteerde kindvariant in plaats van bovenliggende SKU weer.
* Dit zorgt ervoor dat voorraadniveaus correct worden getoond voor configureerbare productvariaties in de kar en productpagina&#39;s.
  _LYNX-403_
* __Fout van GraphQL: Niet gesteund &quot;dossier&quot;type in klantgerichte optiesvraag__
GraphQL heeft een fout geretourneerd voor aanpasbare opties van het type &#39;file&#39; in winkelwagentjes. Dit probleem is nu opgelost. De query retourneert nu op de juiste wijze details voor alle aanpasbare optietypen, inclusief op bestanden gebaseerde opties, zonder fouten te veroorzaken.
  _LYNX-405_
* __vraag van GraphQL die correcte berekende regelmatige prijs voor klantgerichte producten terugkeren__
Probleem verholpen waarbij GraphQL de correcte berekende normale prijs voor aanpasbare producten niet heeft geretourneerd. De vraag omvat nu correct de berekende regelmatige prijs met aanpasbare toegepaste waarden (b.v., $125) in het prijsbezit, dat zowel de basisprijs als om het even welke extra aanpassingskosten weerspiegelt.
  _LYNX-411_
* __AppliedTaxes via EstimatedTotals blijven met bijgewerkte mutaties__
Probleem verholpen met de Mutatie EstimatedTotals waarbij toegepaste belastingen op een winkelwagentje bleven bestaan, zelfs na het bijwerken van de regio of postcode. De mutatie werkt nu correct de toegepaste belastingen bij wanneer het veranderen tussen regio en postcode waarden, die ervoor zorgen dat slechts de correcte belastingregel op de huidige kartgegevens wordt toegepast.
  _LYNX-412_
* __is_available attributen in CartItemInterface keert waar terug zelfs wanneer de verkoopbare voorraad lager is dan de hoeveelheid van het product__
Probleem verholpen waarbij het kenmerk is_available in CartItemInterface onjuist true retourneerde, zelfs als de verkoopbare voorraad kleiner was dan de aangevraagde producthoeveelheid. Het veld is_available retourneert nu correct false wanneer de hoeveelheid van het product groter is dan de beschikbare voorraad.
  _LYNX-420_
* __kan geen coupon aan wagentje voor het verschepen slechts korting toevoegen__
Probleem verholpen waarbij een coupon niet kon worden toegepast op een winkelwagentje voor alleen verzendkortingen. De coupon wordt nu correct toegepast op het verzendbedrag wanneer een verkoopregel zonder productvoorwaarden wordt gebruikt, zodat de verwachte korting op de verzendkosten wordt toegepast.
  _LYNX-421_
* __regelmatige prijs van het Product met 12 decimalen en verkeerde waarde__
Probleem verholpen waarbij de reguliere_prijswaarde in de paden product.price_range.maximum_price en minimum_price GraphQL niet overeenkwam met de catalogusprijs wanneer meerdere belastingtarieven werden toegepast. Reguliere_price weerspiegelt nu consistent de catalogusprijs over alle belastingconfiguraties, die nauwkeurige eenheidsprijzen, totale rijkostenberekeningen, en kortingscontroles in de Samenvatting van de Objecten verzekeren verzekeren.
  _LYNX-425_
* __de serverfout van GraphQL op wortel met uit voorraad gebundeld product__
Probleem verholpen waarbij GraphQL een interne serverfout heeft geretourneerd bij het ophalen van een winkelwagentje dat een gebundeld product met een out-of-stock item bevat, met name wanneer de query de eigenschap itemsV2 bevatte. GraphQL retourneert nu correct een lijst met items met relevante foutberichten die zijn gekoppeld aan het item voor het gebundelde product-item, zoals wordt verwacht.
  _LYNX-430_
* __het is niet mogelijk om een adres met douanekenmerken tot stand te brengen__
Probleem verholpen met de createCustomerAddress-mutatie die het maken van adressen met vereiste aangepaste kenmerken verhinderde. De mutatie behandelt nu correct de attributen van het douaneadres wanneer de aangewezen lading wordt verstrekt.
  _LYNX-441_
* __de serverfout van GraphQL op wortel met only_x_left_in_stock op gebundeld product__
Probleem verholpen waarbij het ophalen van een winkelwagentje met een gebundeld product met het veld only_x_left_in_stock in de GraphQL-query resulteerde in een interne serverfout. GraphQL retourneert nu correct een float of null voor het veld only_x_left_in_stock zonder fouten.
  _LYNX-447_
* __fout van GraphQL wanneer het verwijderen van andere producten met ontoereikende configureerbare product in kar__
Probleem verholpen waarbij pogingen om producten in voorraad uit het winkelwagentje te verwijderen tot een GraphQL-fout &#39;De gevraagde hoeveelheid is niet beschikbaar&#39; hebben geleid als het winkelwagentje ook configureerbare producten met onvoldoende voorraad bevatte. Het verwijderen werkt nu zoals verwacht zonder fouten te veroorzaken.
  _LYNX-464_
* __kan geen producten toe te voegen toe te schrijven aan SKU in mutatie die gevoelig geval is__
Oplossing voor een probleem waarbij de addProductsToCart-mutatie een &#39;PRODUCT_NOT_FOUND&#39;-fout heeft geretourneerd bij het gebruik van SKU&#39;s met andere behuizing. De mutatie behandelt nu case-insensitive SKUs, die consistentie met de vragen van de Dienst van de Catalogus en gedrag PDP verzekeren.
  _LYNX-469_
* __attribuut van het Product > de korte vorm&amp;amp van het handelsmerk; is teruggekeerd als &handel;__
Probleem met tekencodering met productnaam voor de GraphQL API opgelost
  _LYNX-603_
* __updateCustomerEmail mutatiekwestie__
Probleem opgelost met de updateCustomerEmail mutatie waarbij klanten zonder de vereiste aangepaste kenmerken (toegevoegd na het maken van de account) hun e-mail niet konden bijwerken.
  _LYNX-619_
* __Mutation setShippingAddressOnCart werpt fout wanneer het gebruiken van pickup_location_code__
Probleem verholpen waarbij de mutatie setShippingAddressOnCart een fout retourneerde bij het gebruik van pickup_location_code zonder customer_address_id of adres op te geven. De mutatie staat nu correct het plaatsen van een verschepend adres met enkel pickup_location_code toe.
  _LYNX-626_
* __CustomerOrder.items_acceptable_for_return de lijst moet met orde punten__ verenigbaar zijn
Opgeloste inconsistenties met retournering in orders:
1. De lijst CustomerOrder.items_in aanmerking komend_for_return is nu consistent met de werkelijke orderitems.
2. Het veld OrderItemInterface.in_for_return retourneert correct false wanneer de volledige hoeveelheid al is geretourneerd.
3. CustomerOrder.items_in aanmerking komend_for_return bevat nu alleen items die nog niet worden geretourneerd.
   _LYNX-627_
* __voeg kwantiteit_return_requested gebied__ toe
Het veld Quantity_return_requested is toegevoegd aan de OrderItemInterface, zodat u de hoeveelheid items kunt identificeren waarvoor een return is verzonden. Hierdoor wordt het bijhouden van de geretourneerde waarde verbeterd naast het bestaande veld quantity_returned.
  _LYNX-628_
* __de beschikbare acties van de Orde moeten geen RETURN na terugkeer bevatten die voor alle punten in volledige hoeveelheid wordt gecreeerd__
Probleem verholpen waarbij het veld available_actions in de GraphQL customer.orders-query RETURN ten onrechte bevatte nadat een volledige return was gemaakt voor alle items. De actie RETURN wordt nu correct verwijderd als het retourproces is voltooid.
  _LYNX-634_
* __Compatibiliteit van de Storefront - logica van de Update om lijstnaam met prefix en andere minder belangrijke verbeteringen te krijgen__
Bijgewerkte logica om de lijstnaam met de prefix terug te winnen (verwant aan veranderingen SCP).
  _LYNX-637_
* __sparen in adresboek werkt niet wanneer het gebruiken van setBillingAddressOnCart GQL&#39;s same_as_Shipping gebied__
Probleem verholpen waarbij het verzendadres niet werd opgeslagen in het adresboek van de klant wanneer de setBillingAddressOnCart-GraphQL-mutatie werd gebruikt met het zelfde_as_Shipping-veld ingesteld op true. Het verzendadres is nu correct opgeslagen zoals u had verwacht.
  _LYNX-643_
* __normaliseer order_id in mutaties__
Gestandaardiseerd de orde_id input in mutaties en bijgewerkt de orde annuleert bevestigings e-mailmalplaatje om verhogingsidentiteitskaart in plaats van orde identiteitskaart bloot te stellen.
  _LYNX-650_
* __CustomerOrder toont niet de orde commentaren__
Probleem met CustomerOrder verholpen om orderopmerkingen op te nemen in GraphQL-vragen van gasten en klanten.
  _LYNX-651_
* __original_item_price moet geen korting__ omvatten
De logica voor original_item_price in GraphQL Cart-objectprijzen is bijgewerkt om kortingen uit te sluiten.
  _LYNX-652_
* __de producten van de bundel tonen nog &quot;IN_STOCK&quot;wanneer één van zijn gebundeld product uit voorraad__
Oplossing voor een probleem waarbij product.stock_status voor bundelproducten nog steeds &quot;IN_STOCK&quot; weergaven, zelfs als een van de gebundelde items uit voorraad was.
  _LYNX-681_
* __klantenvraag keert Interne Fout van de Server terug als de waarde voor geschrapt douanekenmerk voor een klant__ bestaat
Probleem verholpen waarbij de klantenquery een interne serverfout retourneerde wanneer een verwijderd aangepast kenmerk nog steeds een opgeslagen waarde had. Er wordt nu een correct foutbericht geretourneerd als een niet-bestaand kenmerk wordt aangevraagd. De vereiste cache wordt ongeldig gemaakt wanneer het aangepaste attribuut van de klant wordt verwijderd.
  _LYNX-686_
* __parameter van de Actie voor terugkeer en annuleert bevestigingsverbindingen__
Handelingsparameter toegevoegd voor retourneren en annuleren van e-mailkoppelingen voor bevestiging
  _LYNX-687_
* __de gebruikersbevestigingsURL van de Gast wordt opnieuw gericht aan de pagina van de ordestatus aangezien het orderRef (voor GuestRMA)__ mist
De parameter orderRef is toegevoegd aan de koppeling in de RMA-bevestigingsmail van de gast
  _LYNX-688_
* __de gebruikersbevestigingsURL van de Gast wordt opnieuw gericht aan de pagina van de ordestatus aangezien het order orderRef__ mist
De parameter orderRef is toegevoegd aan de koppeling in het bevestigingsbericht voor annulering van de gastvolgorde
  _LYNX-689_
* __Kwesties met klantenvraag wanneer RMA__ onbruikbaar maakte
De GraphQL-logica is bijgewerkt om ervoor te zorgen dat eerder gemaakte geretourneerde waarden toegankelijk blijven, zelfs als RMA wereldwijd is uitgeschakeld. Het foutbericht is verwijderd om de opslag-UX te verbeteren, zodat klanten hun eerdere retourneert nog steeds kunnen bekijken.
  _LYNX-690_
* __GraphQL die geen bijgewerkte wortelgegevens terugkeren wanneer het in conflict brengen van coupons van toepassing was__
Probleem verholpen waarbij het toepassen van een conflicterende coupon met een hogere prioriteit resulteerde in een foutbericht zonder de bijgewerkte kaartgegevens te retourneren. Wanneer een nieuwe coupon de bestaande ongeldig maakt, retourneert de mutatie nu de juiste kaart met de geldige coupon toegepast.
  _LYNX-696_
* __kan ongeldig voor niet-nullable gebied &quot;TaxItem.title&quot;op placeOrder GQL terugkeren__
Probleem verholpen waarbij de placeOrder-mutatie is mislukt vanwege een interne serverfout vanwege een null-waarde voor het niet-null veld TaxItem.title. Het veld retourneert nu altijd een geldige waarde, zodat de bestelling correct wordt geplaatst.
  _LYNX-699_
* __EstimateTotals: De Kortingen zijn ongeldig voor virtuele producttypes__
Het probleem is opgelost met de &#39;estimals&#39;-mutatie die null retourneert voor kortingen wanneer een kortingscode wordt toegepast op een winkelwagentje dat virtuele producten bevat.
  _LYNX-702_
* __het product van de Bundel keert niet het correcte disconteringspercentage en het bedrag terug__
De nieuwe eigenschappen &quot;catalog_disconto&quot;en &quot;row_catalog_disconto&quot;zijn geïntroduceerd voor cataloguspuntprijzen om de correcte kortingsbedragen en percentages op zowel de rij als enige puntniveaus te tonen.
  _LYNX-703_
* __Cadeauberichtconfiguratie op productniveau__
Probleem verholpen waarbij cadeauberichten niet werden toegepast op productniveau als ze globaal waren uitgeschakeld. Als cadeauberichten nu zijn ingeschakeld voor een specifiek product, kunnen ze worden toegevoegd met de updateCartItems-mutatie. Ze worden nu op de juiste wijze opgeslagen en gereflecteerd.
  _LYNX-714_
* __Kwestie met het verwijderen van gift het verpakken van wortelpunt__
Correctie van het probleem waarbij het verwijderen van cadeauverpakking uit een winkelwagentje met de updateCartItems-mutatie niet werkte zoals verwacht. Nu werkt het toepassen en verwijderen van een cadeauverpakking correct zonder fouten.
  _LYNX-717_
* __de aangepaste geregistreerde klanteneigenschap werkt niet in Boilerplate, en de trackViewedProduct mutatie moet voor gasten worden toegelaten.__
Blootgestelde trackViewedProduct-mutatie om de productweergavegebeurtenis voor klanten en gasten bij te houden
  _LYNX-751_
* __cart.rules vraagterugkeer fout in plaats van lege serie in het geval dat geen actieve kartregels worden toegepast__
Probleem verholpen met de query cart.rules om een lege array te retourneren in plaats van een fout wanneer geen actieve regels voor winkelwagentjes worden toegepast.
  _LYNX-757_
* __Uitgave die gift terugwint voor de punten van het karretje__
Bijgewerkte opvragingslogica om geschenkomsluitende opties voor kar punten terug te keren wanneer globaal gehandicapt maar toegelaten op het productniveau
  _LYNX-758_
* __de vraag van GraphQL met de methode van OPTIONS keert 500 reactiecode terug wanneer adobe-commerce/storefront-verenigbaarheid pakket wordt geïnstalleerd__
Probleem verholpen waarbij GraphQL-aanroepen met behulp van de OPTIONS-methode een fout van 500 interne server hebben geretourneerd bij de installatie van het pakket adobe-commerce/storefront-compatibility. Het eindpunt keert nu correct een 200/204 reactie terug zoals verwacht.
  _LYNX-778_

### Andere ontwikkelaarsgereedschappen

* &rbrack; Repareer de syntaxisfout van HTML van 0&rbrace; kwestie in visual.phtml __Het systeem sluit nu correct de begintag in het bestand visual.phtml, zodat de juiste HTML-syntaxis wordt gebruikt.__&lbrack; Eerder was de begintag niet correct gesloten, waardoor een HTML-syntaxisfout ontstond.
  _AC-10658 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38247) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37457)_
* __[Uitgave ] veranderde &quot;actief&quot;aan &quot;toegelaten&quot;in bin/magento onderhoud:statusbevel__
Het systeem biedt nu nauwkeurigere statusberichten voor de opdracht in de onderhoudsmodus, waarbij de status wordt gewijzigd van &quot;actief&quot; in &quot;ingeschakeld&quot; en van &quot;niet actief&quot; in &quot;uitgeschakeld&quot;. Eerder werd het statusbericht voor de opdracht voor de onderhoudsmodus weergegeven als &quot;actief&quot; of &quot;niet actief&quot;, wat tot verwarring kan leiden.
  _AC-11474 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38486) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38410)_
* __het navigeren in de categorieboom leidt tot fouten in Redis: &quot;Redis zitting overschrijdt gezamenlijke verbindingen&quot;__
  _AC-12571 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38851) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0611e750)_
* __CSP kwesties die met dev/css/use_css_critical_path worden gecombineerd__
Het systeem laadt CSS-bestanden nu correct asynchroon op afhandelingspagina&#39;s, zelfs als de instelling &#39;dev/css/use_css_critical_path&#39; is ingeschakeld, zodat deze pagina&#39;s met de juiste CSS-stijlen worden weergegeven. Eerder werd met een beperkt inhoudsbeveiligingsbeleid (CSP) voorkomen dat inline JavaScript werd uitgevoerd, waardoor CSS-bestanden niet naar behoren werden geladen.
  _AC-12731 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39020) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39040)_
* __Gebruikend virtueel type om stop te vormen, kan de interceptormethode niet correct in `setup:di:compile` bevel__ worden geproduceerd
Het systeem produceert nu correct interceptormethodes wanneer het gebruiken van een virtueel type om een stop te vormen, die verenigbare resultaten verzekeren of precompiled of runtime. Voorheen zou het systeem onjuiste resultaten genereren wanneer vooraf werd gecompileerd in vergelijking met de compilatie bij uitvoering.
  _AC-13398 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/33980) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38141)_
* __Adobe Commerce 2.4.7-p3 eenheidstests ontbreken__
Release-aantekeningen zijn niet vereist.
  _ACP2E-3631 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/982b1c42)_

### Betalings-/betalingsmethoden, bestelling

* __de details van de Krediet van de saldocreditcard van de Overeenkomst die voor later gebruik worden bewaard tonen niet op opgeslagen pagina van de betalingsmethode__
Eerder opgeslagen gegevens over de papieren creditcard werden niet weergegeven op de pagina met opgeslagen betalingsmethoden. Deze pagina bevat nu vaste creditcardgegevens die worden weergegeven op de pagina met opgeslagen betalingsmethoden.
  _AC-13699 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/96dec499)_

### Betalingen

* __de betaling van de Kredietkaart (van de Payflow Link) werkt niet__
Eerdere fout bij ophalen (betaling is afgewezen) bij het plaatsen van een bestelling met creditcard na het plaatsen van de herstelopdracht.
  _AC-13414 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/a68324bc)_
* __Payflow leidt tot nieuwe transactie telkens als wij op halen knoop op het scherm van de meningstransactie klikken__
Het systeem haalt nu correct transactieinformatie zonder een nieuwe betalingstransactie te creëren telkens als de vangknop op het scherm van de meningstransactie wordt geklikt. Als u eerder op de knop Ophalen klikt, wordt een nieuwe betalingstransactie voor een bestelling die al is betaald, onjuist gemaakt.
  _ACP2E-2841 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b2286ecf)_
* __Payrecentere bericht dat niet in PDP voor Canadese paypal handelaarrekening__ toont
Het systeem geeft nu correct het PayLater-bericht voor Canadese PayPal Merchant-accounts weer op de pagina met productdetails (PDP) wanneer het land van de koper kan worden bepaald aan de hand van het factuuradres of de verzending van de account. Eerder werd het PayLater-bericht niet weergegeven vanwege een ontbrekende parameter, wat resulteerde in een fout in de browserconsole.
  _ACP2E-3028 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/6a185204)_
* __PayPal de resultaten van de orderterugbetaling in dubbel creditnota__
Correctie van gelijktijdige afgifte van door IPN gemaakte creditmemo&#39;s voor PayPal-betalingsservice.
  _ACP2E-3143 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d01ee51e)_
* __de prijsregel van de Kar werkt niet voor PayPal__
Het juiste bedrag wordt weergegeven aan de kant van PayPal wanneer korting wordt toegepast op de betalingsmethode
  _ACP2E-3163 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7377de59)_
* &rbrack; De Gebruikers van de Wolk __&lbrack;met een specifieke rol kunnen niet login__
Admin-gebruiker met rol die nu alleen Paypal Section-toegang bevat, kan zich nu zonder fouten aanmelden
  _ACP2E-3208 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/66dea0de)_

### Prestaties

* __Uitgave van de Montages van het Attribuut van het Standaard van het Product__
Het systeem staat nu gebruikers toe om een standaardoptie voor een productattribuut te schrappen, ervoor zorgend dat het attribuut niet altijd een standaardreeks heeft. Eerder, toen een gebrek voor een productattribuut werd geplaatst, was er geen manier om het te schrappen, resulterend in de attributen altijd een standaardreeks.
  _AC-11932 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38703) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7d5e3906)_
* &rbrack; Opschonen van de Code van 0&rbrace; kwestie &lbrace;en voeg nieuw kritiek hoofdblok toe en beweeg kritieke css vóór activa __Het systeem bevat nu een nieuw kritiek kopblok en plaatst kritieke CSS voor elementen, waardoor u meer aanpassingen en optimalisatie van prestaties op de voorgrond kunt uitvoeren.__&lbrack; Eerder werd de kritieke CSS niet geplaatst vóór de activa, die aanpassing en optimaliseringsmogelijkheden beperken.
  _AC-12000 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38748) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/35580)_
* __de compilatieonderbrekingen van het thema wanneer mysql gastheer haveninformatie__ bevat
Het systeem behandelt nu correct MySQL gastheerconfiguratie die haveninformatie omvat, die succesvolle themacompilatie verzekert. Eerder, zou de themacompilatie ontbreken als de MySQL gastheerconfiguratie in de gegevensbestandverbinding haveninformatie omvatte.
  _AC-12176 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38799) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38842)_
* __Steun voor CommandLoaderInterface van Symfony in Magento CLI__
Deze wijziging verkort de initialisatietijd van de Magento CLI-toepassing door uitgestelde initialisatie van opdrachten toe te staan totdat deze nodig zijn.
  _AC-13471 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/29266) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/29355)_
* __Uitgave van Prestaties wanneer het laden van productattributen in kartregels__
Verbeterde queryprestaties voor verkoopregels - van ongeveer 150 ms tot ms van één cijfer.
  _ACP2E-2494 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ba25af8a)_
* __Prijs gedeeltelijke het indexeren prestaties__
De prestaties voor gedeeltelijke indexering van de prijs zijn verbeterd door sommige verwijderingsquery&#39;s te optimaliseren die in het indexeringsproces worden gebruikt.
  _ACP2E-2673 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ba25af8a)_
* __de Orde wordt verworpen op multi-store opstelling wanneer het gebruiken van Async-orde verwerking + Voorwaarden en Voorwaarden__
De bestellingen die van niet-standaard websites zijn geplaatst met de ingeschakelde voorwaarden, worden nu verwerkt.
Voordat ze automatisch werden afgewezen.
  _ACP2E-2850 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/57a32313)_
* __Rest API vraag van de Orde neemt een lange tijd om uit te voeren__
Het systeem voert nu de vraag van de Rest API van de Orde binnen een redelijke termijn uit, verbeterend de prestaties wanneer het halen van een groot aantal orden. Eerder duurde de aanroep van de Order Rest API veel tijd om te worden uitgevoerd, wat vertragingen optrad bij het ophalen van een groot aantal bestellingen.
  _ACP2E-2910 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/001e5188)_

### Prestaties, promotie

* __de regelindexeerder van de Verkoop stopte lopend__
Het systeem voltooit nu met succes de indexeerder van de verkoopregel zelfs met een groot aantal gecombineerde filtergroepen, die ervoor zorgen dat de kartregelvoorwaarden op het karretje zoals verwacht worden toegepast. Eerder, zou de indexeerder van de verkoopregel niet voltooien wanneer er een groot aantal gecombineerde filtergroepen waren, die tot een foutenmelding leiden en de toepassing van de voorwaarden van de kartregel verhinderen.
  _ACP2E-2617_

### Prijsstelling

* __Magento2.4.6-p4 het Eenvoudige Vermiste Prijs van de Orde API van de Orde__
Het systeem geeft nu correct de prijs van eenvoudige producten weer wanneer deze via de Order-API worden gevraagd, zodat de gegevens correct worden weergegeven. Eerder werd de prijs van eenvoudige producten onjuist weergegeven als nul in de API-reactie.
  _AC-11810 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38603)_
* __Penny die fout in catalogusregel afronden__
  _AC-13855 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/276e0acd)_

### Product

* __de Speciale karakters in configureerbare associatieve productnaam worden omgezet in de Entiteiten van HTML.__
Het systeem behoudt nu correct de speciale karakters in de namen van bijbehorende producten wanneer het uitgeven van een configureerbaar product, die hen verhinderen in de entiteiten van HTML worden omgezet. Eerder werden speciale tekens in gekoppelde productnamen geconverteerd naar HTML-entiteiten toen het configureerbare product werd bewerkt.
  _AC-10535 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38146) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38447)_
* __ProductRepository functie GetById leidt niet tot de correcte geheim voorgeheugensleutel__
Het systeem creeert nu correct een geheim voorgeheugensleutel in de functie GetById van ProductRepository, ongeacht of de opslag identiteitskaart als koord of een geheel wordt overgegaan. Dit zorgt ervoor dat het product van geheugen op verdere vraag wordt teruggewonnen, verbeterend prestaties. Eerder, zou het systeem het product van het gegevensbestand terugwinnen telkens als de functie werd geroepen, zelfs met de zelfde parameters, wegens onjuist geheim voorgeheugenzeer belangrijke verwezenlijking.
  _AC-10947 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38384) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38433)_
* __[Uitgave ] [ MFTF ] AdminClickAddOptionForBundleItemsActionGroup__
Het systeem bevat nu de AdminClickAddOptionForBundleItemsActionGroup, die de functionaliteit van het beheerpaneel verbetert. Eerder was deze actiegroep niet beschikbaar.
  _AC-11992 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/30857) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/30838)_
* __[Uitgave ] Fix typo in blok PHPDoc__
Het systeem verwijdert nu correct een onbekende referenced variabele in PHPDoc voor de $helper veranderlijke verklaring, die codeduidelijkheid en nauwkeurigheid verbetert. Voorheen veroorzaakte deze onbekende variabele waarnaar in PHPDoc wordt verwezen, verwarring en potentiële onnauwkeurigheden in de code.
  _AC-13173 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38961) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38940)_
* __[Uitgave ] Vaste gebroken Bundel en downloadbare productpagina&#39;s lay-out in Magento >= 2.4.7__
De lay-out voor bundel- en downloadbare productpagina&#39;s is hersteld, waardoor een consistente en correcte weergave op alle apparaten is gegarandeerd. Eerder traden op deze pagina&#39;s lay-outproblemen op als gevolg van een herschikking van het mediablok met productinformatie.
  _AC-13423 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39403) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/6cfb9b6b)_
* __AlertProcessor - Argument #2 ($storeId) moet van type int zijn, gegeven koord__
Het systeem activeert nu correct de e-mails met productwaarschuwingen door ervoor te zorgen dat de winkel-id van het juiste gegevenstype is. Eerder werden de e-mails met productwaarschuwingen niet verzonden omdat het type niet overeenkomt met de winkel-id.
  _AC-5969 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/35602) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/0574ac23)_
* &rbrack; addFilterToMap functie 0&rbrace; Cloud &lbrace;werkt niet voor bepaalde kolommen __De aangepaste module kan nu worden gebruikt in het raster van de volgorde.__&lbrack; Eerdere fouten zijn opgetreden tijdens het gebruik van een aangepaste module.
  _ACP2E-2944 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3a7c4d17)_
* &rbrack; Producten van de Wolk __&lbrack;in Categorie - voeg Producten toe - wijs toe - selecteer allen__
Gebruikers kunnen nu producten selecteren of deselecteren met de schakeloptie.
  _ACP2E-3471_

### Aanbieding

* __attributen van de Klant niet zichtbaar wanneer het creëren van rekening van uitnodiging__
Kenmerken van de klant zijn beschikbaar tijdens het maken van een account via een uitnodiging.
  _ACP2E-2602 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/39d54c2d)_
* __de code van de coupon met Gebruik per grens van de Coupon wordt niet vrijgegeven voor betaling ontbrak met orde annuleert__
Het systeem werkt nu onmiddellijk coupongebruik bij wanneer een order wordt gemaakt of geannuleerd, en voegt regelgebruikers toe aan een wachtrij om potentiële blokkeringen te voorkomen. Dit zorgt ervoor dat een couponcode met de limiet &quot;Gebruik per coupon&quot; wordt vrijgegeven en opnieuw kan worden gebruikt als een order wordt geannuleerd vanwege een mislukte betaling. Eerder heeft het systeem de couponcode niet vrijgegeven voor hergebruik in dergelijke gevallen, wat resulteerde in een foutbericht waarin stond dat de couponcode niet geldig was.
  _ACP2E-2627 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/c971859e)_
* &rbrack; het Opnieuw indexeren van het Product van de Regel van de Catalogus van de Wolk 1&rbrace; [ HY000 ] SQLSTATE &lbrace;teruggeeft: Algemene fout: De server van 2006 MySQL is weggegaan.__&lbrack;__
Het systeem behandelt nu correct douanewaarde &quot;batchCount&quot;in di.xml voor &quot;Magento\CatalogRule\Model\Indexer\IndexBuilder&quot;, die SQL fouten zoals &quot;Algemene fout verhinderen: de server van 2006 MySQL is weggegaan&quot;tijdens het opnieuw indexeren van het Product van de Regel van de Catalogus wegens de onjuiste partijgrootte op grote catalogi
  _ACP2E-2811 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b2286ecf)_
* __[CLOUD ] de Regel van de Prijs van de Kar voor het Segment van de Klant van Bezoekers die geen korting op kar toepassen__
Het systeem past nu correct de Regels van de Prijs van de Kaart voor de Segmenten van de Klant van de Bezoeker toe, zelfs als de regel geen coupon gebruikt, die ervoor zorgen dat de aangewezen kortingen op het karretje worden toegepast. Voorheen werden geen kortingen toegepast op het winkelwagentje voor klantsegmenten van bezoekers, tenzij de prijsregel voor winkelwagentjes een coupon gebruikte.
  _ACP2E-2926_
* __Ontbrekend &quot;Type&quot;Attribuut in &quot;Producten aan Gelijke&quot;Lusje van Verwante Regels van het Product__
Het kenmerk &quot;Type&quot; is nu beschikbaar als filteroptie op het tabblad &quot;Producten afstemmen&quot; van de module &quot;Verwante productregels&quot;, zodat een nauwkeurigere regeldefinitie mogelijk is. Eerder ontbrak dit kenmerk op het tabblad &quot;Producten op maat&quot;, waardoor de mogelijkheid om nauwkeurige overeenkomende criteria te maken, werd beperkt.
  _ACP2E-3024_
* __de Regel van de Verkoop met het attribuut van de Stap van de Aantal van de Korting (koop X) veroorzaakt andere regels om niet worden toegepast__
De prijsregel voor winkelwagentjes annuleert eerder toegepaste regels niet als de hoeveelheid van het product in het winkelwagentje niet voldoende is om de regel toe te passen.
  _ACP2E-3139 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d01ee51e)_
* __kwestie van Prestaties op de prijsregel van de Kar - de module van de Regel van de Verkoop van de Vooruitgang__
Ontbrekende DB-indexen toegevoegd voor AdvancedSalesRule-filters
  _ACP2E-3331_
* __de verkoopregels van de kwestie met Vaste waardekorting en de &quot;Maximale Korting van de Aantal wordt toegepast op&quot;__
Correctie van het probleem met de korting op de regels voor winkelwagentjes, wanneer korting op een vast bedrag is geconfigureerd om te worden toegepast op een beperkte hoeveelheid producten, is de winkelwagentje. Eerder werd de waarde &quot;Maximale korting op de hoeveelheid toegepast op&quot; gebruikt voor de berekening van de prijs van het lopende item in het winkelwagentje, niet alleen voor de berekening van de korting op de regel.
  _ACP2E-3332 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/581b7ef1)_
* __[CLOUD ] de verbetering van Magento veroorzaakte coupons om case-sensitive te worden__
Vóór de correctie moest u de waardeboncode precies typen zoals deze was geconfigureerd, rekening houdend met hoofdletters of kleine letters. De coupon wordt nu gevalideerd op de achtergrond, ongeacht de configuratie van code in hoofdletters of kleine letters.
  _ACP2E-3342_
* __de regels van de winkelwagentje &quot;Vaste korting van het bedrag voor het volledige karretje&quot;  Met Actie worden kortingen onjuist toegepast__
Couponcodes worden correct gevalideerd, ongeacht hoofdletters of kleine letters, wanneer deze worden gebruikt om via het beheergebied te worden gemaakt. De waardeboncode werd eerder niet gevalideerd als deze niet precies overeenkomt met het hoofdlettergebruik van de code van de geconfigureerde tekenregel.
  _ACP2E-3349 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/581b7ef1)_
* __op Achtergrond, standaard opslagwaarden voor productattributen (in plaats van verwachte adminwaarden)__
Op achtergrond worden nu beheerwaarden gebruikt in plaats van standaardwaarden voor de opslag van productkenmerken.
  _ACP2E-3374 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/5184c067)_
* __de regels van de Kar &quot;Vaste waardekorting voor Hele Kar&quot;actie past onjuiste kortingen toe wanneer het toevoegen van bundelproducten__
Voor bundelproducten werden de regels voor een vast bedrag aan winkelwagentjes niet correct toegepast. Bij de berekening van het totale kortingsbedrag worden nu onderliggende bundelproducten in aanmerking genomen, wat resulteert in een correcte disconteringsberekening.
  _ACP2E-3377 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1366ae5e)_
* __Verkeerde Korting van de Prijsregels van de Kar__
Korting op vaste bedragen wordt nu correct berekend. Voorafgaand aan de correctie werden kortingen voor vaste bedragen niet correct toegepast op bundelproducten.
  _ACP2E-3403 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/0b488dd1)_
* __Geneste categorieën in regelvoorwaarden die__ niet tonen
Geneste categorieën van categorie 3 werden niet vermeld in de marketingregels voor de categorie. Dit probleem is nu opgelost.
  _ACP2E-3406 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/88660e79)_
* __usage_limit en uses_per_customer het bijwerken niet in salesrule_coupon Lijst__
Het bijwerken van het gebruik per coupon en het gebruik per Klant in de regel van de kartprijs heeft nu invloed op bestaande automatisch gegenereerde coupons. Eerder beïnvloedden de nieuwe waarden alleen nieuwe coupons
  _ACP2E-3432 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/88660e79)_
* __de prijsregel van het Kart overweegt geen oudercategorie wanneer het &quot;evenaart of groter dan&quot;voorwaarde gebruikt.__
Bij regels voor winkelprijzen wordt een bovenliggende categorie nu correct beschouwd als deze in geavanceerde omstandigheden wordt gebruikt
  _ACP2E-3456 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/93359343)_
* __Ongeldige disconteringsberekening met prioriteit__
In het geval van een vast bedrag dat voor het hele type cartkorting werd aangevraagd, werd het bedrag niet correct berekend voor winkelwagentjes die al door een eerdere promotie waren gedisconteerd. Kortingen worden nu goed samengevat.
  _ACP2E-3463 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_
* __[CLOUD ] Verzendberekening overweegt niet de het winkelwagentregel__
Voorafgaand aan de correctie werd een kartelregel met gebiedsvoorwaarde niet consequent toegepast. Na de correctie worden de regels voor het winkelwagentje met de omstandigheden van het gebied correct toegepast.
  _ACP2E-3472 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d4de4726)_
* De __voorwaarde van de de regelsku van de Kar ontbreekt voor factuur.__
Korting op een bundelproduct met dynamische prijs wordt nu correct weergegeven in de factuur. Voorheen werd de korting niet in de factuur weergegeven.
  _ACP2E-3491 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/3f12d152)_
* __Onjuiste disconteringswaarde wanneer de veelvoudige regels van de kartprijs gelijktijdig met verdisconteerde/speciale geprijste producten worden toegepast__
Voorafgaand aan de vaststelling werd het vaste bedrag voor de regels voor het hele winkelwagentje niet correct toegepast als er meer dan één werd toegepast. Nu worden de regels voor kortingen op vaste bedragen correct toegepast.
  _ACP2E-3498 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1984c61c)_

### Retourneert

* __[CLOUD ] Beperkte admin gebruikers kunnen het terugkeermenu en de knopen zien__
Beperkte Admin-gebruikers hebben nu geen toegang tot aan RMA gerelateerde besturingselementen (menu en knoppen).
Eerder beperkte admin-gebruikers konden het retourmenu en de knoppen zien.
  _ACP2E-3330_
* __het Scherm van de Terugkeer wordt verduisterd wanneer het scherm__ verfrist
De gebruiker kan de pagina vernieuwen zonder schermvervorming te ervaren.
  _ACP2E-3443_

### SEO

* __toevoegend URL herschrijft met een accent oorzaken oneindig ladend__
Het systeem maakt en functioneert nu URL herschrijft met accenten, waardoor oneindig laden tijdens het opslagproces wordt voorkomen. Eerder veroorzaakte het toevoegen van een URL voor herschrijven met een accent een oneindig ladingsprobleem.
  _AC-11907 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38692) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/44cef3a9)_
* __Meerdere Verkeerde categorie van de Opslag rl-herschrijft voor derdeniveaucategorie__
Correcte url-herschrijvingen genereren voor kinderen met bovenliggende elementen met een aangepaste URL-sleutel met bereik
  _ACP2E-2641 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ea79f7dd)_
* __dubbel-byte karakters (speciale karakters) in het gebiedsblokcreatie van de Naam van het Product in achterste__
Er is een nieuwe instelling toegevoegd waarmee u transliteratie kunt toepassen op product-URL of niet. Instelling is hier beschikbaar: Storingen > Configuratie > Catalogus > Catalogus > Optimalisatie van zoekprogramma&#39;s: &quot;Transliteratie toepassen voor product-URL&quot;
  _ACP2E-2770 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b2286ecf)_
* __Onjuiste url_rewrite ingangen verwezenlijking met veelvoudige opslag in één opslaggroep__
Voordat de correctie werd uitgevoerd, kon u alleen URL-herschrijvingen op websiteniveau genereren wanneer u een product bewerkt. Met de correctie is een nieuwe instelling geïntroduceerd (Winkels > Configuratie > Catalogus > Catalogus > Optimalisatie van zoekprogramma&#39;s, &quot;Product URL herschrijven bereik&quot; met opties &quot;Winkelweergave&quot;, &quot;Website&quot;) waarmee u URL-herschrijvingen kunt genereren in de winkelweergave of op websiteniveau.
  _ACP2E-3383 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/2d627301)_

### Verkoop

* __de Tweede Regel van de Prijs van de Kar wordt niet toegepast als de Eerste regel van de Kar reeds wordt toegepast__
  _AC-13751_

### Zoeken

* __krijgen &quot;ga een onderzoekstermijn in en probeer opnieuw.&quot; fout op geavanceerde onderzoekspagina in storefront in 2.4.8-bèta1__
Het systeem geeft nu correct de zoekresultaten weer op de pagina Geavanceerd zoeken wanneer een productkenmerk op Nee is ingesteld. Als u eerder een productkenmerk instelt op &quot;Nee&quot; en een zoekopdracht uitvoert, verschijnt het foutbericht &quot;Voer een zoekterm in en probeer het opnieuw.&quot;
  _AC-13053 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/3ea26621)_
* __magento/module-open-onderzoek hangt van nonexistent op onderzoek-php tak__ af
  _AC-13721 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/05dc0bbf)_
* __search_query lijst wanneer van grote grootte, grote invloed op de voorkant van de ladingstijd heeft__
Verbeterde laadtijd voor pagina met zoekaanbiedingen. Vóór de correctie werd de pagina met zoeklijsten vertraagd vanwege een niet-geoptimaliseerde query.
  _ACP2E-3362 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/55615e61)_

### Beveiliging

* __[Uitgave ] Ontbrekende CSP van het Lettertype ontvangt pop-up__
Het systeem staat nu het laden van het lettertype &#39;https://www.paypalobjects.com/webstatic/mktg/2014design/font/PP-Sans/PayPalSansBig-Medium.woff&#39; toe zonder de Content Security Policy Directive te overtreden, waardoor de correcte weergave van de Paylater Popup wordt gegarandeerd. Eerder werd het lettertype niet geladen vanwege een schending van de Content Security Policy-richtlijn, wat weergaveproblemen met de Paylater Popup veroorzaakte.
  _AC-11855 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38624) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/37401)_
* &rbrack; Update js.js DOM tekst van 0&rbrace; Uitgave &lbrace;opnieuw geïnterpreteerd als HTML __Door innerText te gebruiken, voorkomt dit het risico van HTML-injectie, aangezien deze eigenschappen automatisch speciale HTML-tekens in de opgegeven tekst ontsnappen.__&lbrack; Met deze correctie voorkomt u XSS-kwetsbaarheden (cross-site scripting) door de invoer te behandelen als onbewerkte tekst in plaats van als geïnterpreteerde HTML.
  _AC-12035 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38767)_
* __ReCaptcha V2 toont verkeerd bij controle voor de Duitse taal__
Eerder werd de recaptcha van het uitchecken onder e-mailadres niet opgemaakt voor talen met lange woorden, zoals het duits. Hierna ziet de rechaptcha er hetzelfde uit als alle elementen van de rest van de gebieden.
  _ACP2E-3273 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/7377de59)_
* __Captcha op admin login vereist geen interactie voor sommige gebruikers__
ReCaptcha voor aanmelden bij beheerder is gevalideerd zoals verwacht
  _ACP2E-3300 - [ de codebijdrage van GitHub ](https://github.com/magento/security-package/commit/8f64ab3c)_

### Verzending

* &rbrack; Vaste typering van de kwestie van 0&rbrace; &lbrace;in tracking.phtml - anders genoemd JS-functies &quot;currier&quot;aan &quot;drager&quot;__Het systeem gebruikt nu correct de term &quot;drager&quot;in plaats van de verkeerd gespelde &quot;currier&quot;in de de handlerfuncties van JavaScript die in het orde volgende malplaatje worden gebruikt, die correcte functienaam en codeduidelijkheid verzekeren.__&lbrack; Voorheen werd de verkeerd gespelde term &quot;currier&quot; gebruikt, wat tot verwarring en inconsistentie in de codebase kan leiden.
  _AC-10757 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/34523) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/33414)_
* __UPS REST &quot;Een verzending kan geen KGS/IN of LBS/CM of OZS/CM als zijn eenheid van metingen hebben&quot;__
Zorg ervoor dat de UPS-snelheden zichtbaar zijn in het uitchecken en winkelwagentje.
  _AC-11938 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38618) - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/493e01f5)_
* __UPS REST &quot;zandbak&quot;en &quot;prod&quot;opstellingsinstructieupdates in devdoc__
  _AC-12938_
* &rbrack; Correcte spelling van variabelen voor klantenadres __&lbrack;uitgeven__
Het systeem spreidt nu correct variabelen voor klantenadressen, die nauwkeurige vertoning in het rekeningsgebied van het voorste eind verzekeren. Eerder kon een onjuiste spelling van deze variabelen leiden tot fouten tijdens lokale coderevisies.
  _AC-13172 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/32817) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32815)_
* __het Volgen Venster die onjuiste Verwachte Datum van de Levering tonen__
Geef de juiste leveringsdatum voor de Fedex Carrier weer.
  _ACP2E-2738 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/57a32313)_
* __de Tarieven van de Lijst die nog tonen alhoewel de Vrije verscheping wordt toegepast__
Verzendmethode voor tabelsnelheden wordt nu weergegeven, zelfs als de optie voor gratis verzending beschikbaar wordt nadat de coupon is toegepast
  _ACP2E-2763 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/b2286ecf)_
* __MFTF test AdminCreatingShippingLabelTest die wegens geloofsbrieven niet in milieu Jenkins wordt toegevoegd__ ontbreekt
mftf-testcorrectie
  _ACP2E-2765 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ea79f7dd)_
* __het Spoor FedEx API die niet met de geloofsbrieven van REST werkt__
Eerder voor FedEx-integratie waren geen extra API-sleutels vereist voor het bijhouden van de API. Er is nu een nieuwe configuratie toegevoegd ter ondersteuning van het bijhouden van API-sleutels.
  _ACP2E-3340 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ec7e32a9)_
* &rbrack; FedEx Onderhandelde Tarieven van de Wolk __&lbrack;&lbrace;die niet op REST__ zijn teruggekeerd
Vóór de correctie, rekening specifieke tarieven FedEx waar niet verzonden op de reactie, zelfs door volgens FedEx- documentatie zij zouden moeten worden verzonden. Na de correctie worden de specifieke tarieven van de rekening verzonden op de reactie door het verzoek van onze kant te veranderen.
  _ACP2E-3354 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/55615e61)_

### Staging en voorvertoning

* __Geplande updatemontages niet bewaard als oorspronkelijk toegevoegd door update in werking te stellen__
Het systeem wist nu correct waarden van productkenmerken in volgende geplande updates wanneer dergelijke kenmerken worden gewijzigd in de update die momenteel wordt uitgevoerd. Eerder, toen een productattribuut door een lopende geplande update werd gewijzigd, was het onmogelijk om dergelijke attributen waarden te ontruimen wanneer het creëren van een nieuwe geplande update, die de gebruiker te vereisen om hen na verwezenlijking opnieuw uit te geven.
  _ACP2E-2901_
* __de Regel van de Prijs van de winkelwagentje van datum en tot op heden kwestie niet die met het Opvoeren Update__ wordt gesynchroniseerd
Datums worden opgeslagen op basis van updates voor het opvoeren van regels voor winkelwagentprijzen.
  _ACP2E-2999_
* __fout JS in het Opvoeren van Voorproef__
Het bestand form-mini-stub.js wordt nu zonder Js-syntaxisfout geladen in de ontwikkelaarsgereedschappen.
  _ACP2E-3104_
* __de Speciale Prijs Geleide Inhoud van het Product kan niet worden bijgewerkt__
Het systeem maakt het nu mogelijk om de einddatum van een prijsupdate-campagne te bewerken nadat deze is gestart, zodat gebruikers de nodige aanpassingen in hun campagnes kunnen aanbrengen. Er is eerder een fout gegenereerd tijdens een poging de einddatum van een actieve campagne bij te werken, waardoor gebruikers niet meer wijzigingen kunnen aanbrengen.
  _ACP2E-3162_
* __Onbekwaam om Geplande Update bij te werken wanneer het Gebruiken van Uniek Attribuut van de Categorie van de Douane__
Probleem verholpen waarbij het bijwerken van een geplande update voor een categorie niet mogelijk was als de categorie een uniek kenmerk had
  _ACP2E-3453 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_

### Targeting

* __[Uitgave ] staat gebruik van CIDR waaiers in onderhoudscategorie__ toe
Het systeem steunt nu het gebruik van CIDR waaiers op de onderhoudswijze staat IP lijst toe, toelatend een waaier van IP adressen om onderhoudswijze te mijden. Eerder, staat de onderhoudswijze IP lijst slechts toegelaten individuele IP adressen toe om onderhoudswijze te mijden.
  _AC-9432 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37943) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/30699)_

### Belasting

* &rbrack; eigenschap/php8.1 de bevordering van het aannemersbezit van 0&rbrace; kwestie &lbrace;toen grafiek ql __Vervang bijna alle eigenschappen met de bevordering van het aannemersbezit in module wanneer grafiek ql:__&lbrack;
  _AC-13295 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/39309) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36975)_
* __Vaste Belasting van het Product (FPT) werkt niet met configureerbare producten__
FPT voor configureerbare productvariaties die correct werken.
  _ACP2E-3193 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/ec7e32a9)_

### Testkader

* __test van de Integratie het ontbreken test testDbSchemaUpToDate toe te schrijven aan JSON kolomtype__
Het systeem herkent nu correct JSON kolomtypes in het gegevensbestandschema tijdens integratietests, die testmislukkingen wegens een wanverhouding tussen het gegevensbestandschema en het verklarende schema verhinderen. Eerder, identificeerde het systeem verkeerd JSON kolomtypes als LONGTEXT in MariaDB, veroorzakend integratietests om te ontbreken.
  _AC-11654 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/ef81f5a2)_
* __[vraag ] de correctiepspelling van PHPDoc__
Het systeem herkent nu correct vervangen methodes in IDEs toe te schrijven aan een spelcorrectie in PHPDoc. Eerder heeft een spelfout in de PHPDoc ertoe geleid dat IDE&#39;s bepaalde methoden niet herkennen als afgekeurd.
  _AC-13362 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/31399) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/31398)_
* __MAGETWO-95118: Het controleren van gedrag met het blijvende het winkelwagentje nadat de zitting is verlopen__
  _AC-13478 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/7d5e3906)_
* __de tests van de Integratie zijn ontbroken Magento\NegotiableQuote\Controller\Quote\DownloadTest::testCompanyManagerDownloadWithNQSubPermission__
  _AC-13716_
* __[Gegevensbestand vergelijkt ] Onherstelbare fout als het gegevensbestand verslag over de Regel van het Doel zonder voorwaarden bevat__
Eerder als het Gegevensbestand verslag over de doelregel zonder enige voorwaarde bevat ontvingen fatale fouten maar na het de vergelijkingshulpmiddel van het Gegevensbestand van de moeilijke situatie met succes zonder fatale fouten.
  _AC-13722_
* __bevestig statische tests om gebruik door 3d partijuitbreidingen toe te laten__
  _AC-13848 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/9e383b4d)_
* __[de Interne ] Vast past mislukking toe is niet getoond tijdens uitvoering of in logboeken__
&#39;-
  _ACP2E-3334 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/d4de4726)_
* __[MFTF ] StorefrontCheckoutProcessForQuoteWithoutNegotiatedPricesTest__
Vaste mftfs
  _ACP2E-3458 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/078c387e)_

### UI Framework

* __de veiligheidskwetsbaarheid van Prototype.js moeilijke situatie CVE-2020-27511__
Het systeem is bijgewerkt om de beveiligingskwetsbaarheid CVE-2020-27511 in Prototype.js 1.7.3 te verhelpen, waardoor de algemene beveiliging van het systeem wordt verbeterd. Voorafgaand aan deze update was het systeem gevoelig voor een Regular Expression Denial of Service (ReDOS) via gestripte HTML-tags.
  _AC-12128 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/de4dfb8e)_
* __Grunt Minder gebruikspubs/prefix voor broncemaps__
Het systeem genereert nu minder /css broncemaps zonder het voorvoegsel /pub voor wegen wanneer het gebruiken van grot, die de behoefte aan een alternerende actie in de configuratie van de webserver elimineert. Eerder, vereiste het gebruik van het prefix /pub in broncemaps wegen een specifieke configuratie in de webserver om correct te functioneren.
  _AC-12189 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38837) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38840)_
* __het Gebied van het Dossier van de Component UI__
Het systeem valideert het bestandsveld nu correct in een UI-componentformulier, zodat het formulier zonder fout kan worden verzonden wanneer een bestand is geselecteerd. De validatie zou eerder mislukken, zelfs als een bestand was geselecteerd, zodat het formulier niet kon worden verzonden.
  _AC-12432 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38908) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/39004)_
* &rbrack; Verbeterd datumformaat van de kwestie __&lbrack;&lbrace;in js console: schakelaar van 12 uur aan 24 uur van...__
Verbeterde datumnotatie in JS-console: switch van 12 uur naar 24 uur
  _AC-12645 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38983) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38972)_
* __[Uitgave ] voegt bronMap generatie voor minder dossiers op ontwikkelaarwijze toe__
Het systeem genereert nu bronkaarten voor minder bestanden in de ontwikkelmodus, zodat de bron van een stijl gemakkelijker kan worden geïdentificeerd. Eerder, was het identificeren van de bron van een stijl uitdagend toen het runnen van het systeem op ontwikkelaarwijze met server-kant minder compilatie.
  _AC-12650 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/38982) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38977)_
* __de Statische inhoud stelt voor gehandicapte modules__ op
Het systeem sluit nu CSS met betrekking tot uitgeschakelde modules uit van de definitieve CSS outputdossiers, die ervoor zorgen dat de onnodige stijlen niet worden geladen. Eerder werden CSS met betrekking tot uitgeschakelde modules opgenomen in de uiteindelijke CSS-uitvoerbestanden, wat leidde tot het laden van extra, onnodige stijlen.
  _AC-1306 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/24666) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/32922)_
* __Inconsistent Gedrag in &quot;uit Voorraad&quot;Sorterend met de Minimale Drempel van het Beeld__
Het systeem sorteert producten in de catalogus nu correct op basis van voorraadniveaus, waarbij de vastgestelde minimumvoorraaddrempel wordt aangehouden en items uit de voorraad steeds naar de onderkant van de lijst worden verplaatst. Eerder was het sorteergedrag inconsistent, waarbij items niet altijd in de juiste volgorde werden weergegeven op basis van hun voorraadniveau, en wijzigingen in sorteren kunnen onvoorspelbaar optreden na het opslaan, vernieuwen of wijzigen van de categoriehiërarchie.
  _AC-13459 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/47b448e2)_
* __Suggestie voor betere fout die voor require.js ladingsproblemen meldt__
Deze PR verbetert het foutbericht wanneer vereisten er niet in slagen een component te laden.
  _AC-13472 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/36761) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/38971)_
* __PHP 8.4 de Fouten die van de Afwijking veroorzaken bouwfouten in 2.4-ontwikkelen__
  _AC-14004 - [ GitHub codebijdrage ](https://github.com/magento/magento2/commit/1da9ba6f)_
* __[Uitgave ] laadt geen backend blokcontext op frontend__
Het systeem zorgt er nu voor dat de achtergrondblokcontext niet op de frontend wordt geladen, waardoor onnodige back-endsessies en potentiële sessieslokken worden voorkomen. Eerder, laadde het systeem verkeerd de achtergrondblokcontext op het front-end, die tot de verwezenlijking van achterste deelzittingen en potentiële zittingssloten leidde.
  _AC-9007 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37617) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/36368)_
* __[Uitgave ] verwijdert onnodige samenvatting van het manuscriptoverzicht__
Het systeem optimaliseert nu de laadtijd van de pagina door overbodige JavaScript-scripts te verwijderen uit de classificatiesectie, in plaats van inline CSS-stijlen te gebruiken voor een efficiëntere en leesbare code. Eerder kon het gebruik van JavaScript-scripts voor de classificatiesectie de laadtijd van de pagina mogelijk vertragen.
  _AC-9168 - [ GitHub kwestie ](https://github.com/magento/magento2/issues/37776) - [ GitHub codebijdrage ](https://github.com/magento/magento2/pull/34643)_
* __Uitzondering wanneer het controleren van een evenwicht van de cadeaukaart wanneer Recaptcha wordt toegelaten__
Gebruikers kunnen de balans van de cadeaukaart ophalen in de weergave en het kaartscherm bewerken. Eerder werden deze details niet weergegeven terwijl reCAPTCHA ingeschakeld was.
  _ACP2E-2529 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2-page-builder/commit/4a2795ea)_
* __[CLARIFICATION ] Naleving ADA van het Verzoek van de Eigenschap &lbrace;__
Het systeem zorgt nu voor compatibiliteit met ADA door niet-ondersteunde CSS-eigenschappen te verwijderen en te vervangen door ondersteunde eigenschappen in het bestand print.css. Eerder leidde het gebruik van niet-ondersteunde CSS-eigenschappen tot browsercompatibiliteitsproblemen.
  _ACP2E-2729 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/57a32313)_
* __[de bibliotheekcode van de Wolk ] van de Fusie in effect-drop.js van AC 2.4.4-p8__
Het systeem implementeert nu correct de bibliotheek effect-drop.js, die de juiste werking van de gevolgen van jQuery UI verzekert. Eerder werd de bibliotheek effect-drop.js per ongeluk overschreven met de bibliotheek effect-clip.js, wat potentiële problemen met de gevolgen van jQuery UI veroorzaakte.
  _ACP2E-3061 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/35b1b1da)_
* __Sitekoptekst | Speciale tekens die het welkomstgedeelte van de klant doorbreken__
Na de moeilijke situatie, worden de speciale karakters correct getoond in de klant welkome sectie.
  _ACP2E-3367 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/1366ae5e)_
* __de uitgave van het Segment van de Klant ontbreekt met daterange__
Het is mogelijk om klantensegment met datumwaaiervoorwaarde te bewaren, toen slechts één van data werd uitgegeven.
  _ACP2E-3561 - [ de codebijdrage van GitHub ](https://github.com/magento/magento2/commit/a52ff98f)_
