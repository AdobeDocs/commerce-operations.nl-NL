---
title: Opmerkingen bij de release
description: Meer informatie over de patches die beschikbaar zijn voor Adobe Commerce en de problemen die ze oplossen.
source-git-commit: ead062ac2f5dbf07293aef2a5a5d9f1f21255402
workflow-type: tm+mt
source-wordcount: '9233'
ht-degree: 0%

---

# Opmerkingen bij de release

De [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) levert afzonderlijke patches die door Adobe en de Magento Open Source-gemeenschap zijn ontwikkeld. Hiermee kunt u algemene informatie over alle afzonderlijke patches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce of Magento Open Source, toepassen, herstellen en weergeven. U kunt patches toepassen op Adobe Commerce- en Magento Open Source-projecten, ongeacht wie de patch heeft ontwikkeld. U kunt bijvoorbeeld een patch toepassen die door de gemeenschap is ontwikkeld op Adobe Commerce-projecten.

>[!INFO]
>
>Zie [Patches toepassen](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) voor instructies voor het toepassen van patches op uw Adobe Commerce- of Magento Open Source-projecten. Zie [Beschikbare patches](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in de Software Update Guide om een volledige lijst met vrijgegeven patches te bekijken.

>[!INFO]
>
>Voor informatie over [!DNL quality patches] die door de Gemeenschap voor Magento Open Source zijn opgericht, [releaseopmerkingen](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een gebruiker een onjuiste orderstatus krijgt wanneer het bedrag wordt terugbetaald via het winkelkrediet.
* **ACSD-46703** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij het niet mogelijk is om aangepaste opties te slepen en neer te zetten op een productbewerkingspagina.
* **ACSD-44851** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij een categorie met subcategorieën niet kan worden geopend of uitgebreid.
* **ACSD-46815** (*voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij de aanvraag voor de boomcategorie beperkt is tot 20 categorieën.
* **ACSD-45675** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6*) - Hiermee wordt het probleem opgelost waarbij voor het exporteren van het product categorienamen uit de *Standaardwinkelweergave* bereik.
* **ACSD-46869** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6*) - Hiermee wordt het probleem opgelost dat een configureerbaar product in een winkelwagentje niet via een *PUT REST API* aanvragen zonder de producthoeveelheid te wijzigen.
* **MDVA-42768-V2** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Oplossing van het probleem waarbij Configureerbaar product een normale prijs weergeeft als *0* wanneer *Weergeven uit voorraad* is *Ja*.
* Bijgewerkte patches: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Verouderde patch: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de aanvraag voor de boomcategorie beperkt is tot 20 categorieën.
* **ACSD-45781** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij het zoekveld voor de winkel niet wordt weergegeven op mobiele apparaten.
* **ACSD-46192** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;2.4.5*) - Hiermee kunt u het probleem verhelpen door de opdracht `async/bulk/V1/configurable-products/bySku/options` eindpunt.
* **ACSD-46404** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een beheerder zich niet kan aanmelden na een upgrade naar 2.4.4.
* Bijgewerkte patches: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een GraphQL-productmutatie voor een specifieke winkel alle configureerbare varianten retourneert, inclusief varianten die niet aan de gevraagde winkel zijn toegewezen.
* **ACSD-46146** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij twee e-mails ter bevestiging van de bestelling worden verzonden nadat een bestelling van de beheerder is geplaatst.
* **ACSD-45255** (*voor Adobe Commerce >=2.4.3 &lt;2.4.6*) - Hiermee wordt een uitzondering op de pagina Rapport over lage voorraad voor een beperkte beheerder gecorrigeerd.
* **ACSD-45488** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij een configureerbaar product met meerdere bronnen niet automatisch wordt teruggestuurd naar In Stock.
* **ACSD-45754** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.6*) - Hiermee wordt de emissie gecorrigeerd waarbij geen punten naar achteren worden toegevoegd nadat een coupon op de winkelwagentje is toegepast.
* **ACSD-45849** (*voor Adobe Commerce >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij videometagegevens verloren gaan nadat een testupdate is toegepast.
* **ACSD-45257** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij GraphQL geen kaartkorting correct weergeeft.
* **ACSD-44938** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij `VAT_ID` kan niet in een verzoek GraphQL voor een gastgebruiker worden toegepast.
* Bijgewerkte patches: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.4*) - Hiermee wordt de kwestie opgelost waarbij de voorraadhoeveelheid voor een virtueel product onjuist wordt berekend na het maken van een creditnota.
* **ACSD-43887** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij onjuiste gegevens worden weergegeven op de betalingspagina voor afbetalingen wanneer Aankooporders voor bedrijven zijn ingeschakeld.
* **ACSD-45143** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de `setShippingAddressesOnCart` mutatie staat het plaatsen van numerieke gebiedscode als niet toe *regio*.
* **ACSD-44591** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.6*) - Hiermee wordt de fout gecorrigeerd die optreedt wanneer een bestelling wordt geplaatst zonder CAPTCHA-bevestiging.
* **ACSD-45520** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.6*) - Hiermee wordt het probleem opgelost waarbij staalopties niet vooraf op de pagina met productdetails zijn geselecteerd wanneer een gebruiker configureerbare producten bewerkt in het winkelwagentje.
* **ACSD-45169** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.6*) - Hiermee wordt het probleem opgelost waarbij [!DNL Visual Merchandiser] geeft niet de correcte voorraad en de prijs voor een configureerbaar product na een het opvoeren update wordt toegepast.
* **ACSD-45424** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.6*) - Hiermee wordt de kwestie opgelost waarbij na een gedeeltelijke terugbetaling een onjuiste reserveringscompensatie wordt gecreëerd (creditnota).
* **MDVA-42807** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.6*) - Hiermee wordt de uitgave verholpen waarbij het aangepaste valutateken niet op de winkelvoorzijde worden weergegeven.
* Bijgewerkte patches: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **MDVA-44703** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij het totaal van de bestellingen in het orderrapport onjuist wordt berekend voor de gebruiker met beperkte beheerdersrechten.
* **MDVA-44940** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt de SQL-fout verholpen die optreedt wanneer de categorie wordt opgeslagen in de beheerfunctie.
* **MDVA-44562** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Hiermee wordt het probleem opgelost waarbij de niet-standaard opslagid voor aanhalingstekens wordt overschreven door de standaard opslagid, ondanks het GraphQL-verzoek dat afkomstig is uit de niet-standaard winkelweergave.
* **MDVA-43167** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij de handeling voor de massa van het raster van de beheervolgorde niet van toepassing is op meerdere pagina&#39;s wanneer de beheerder alle bestellingen selecteert.
* **MDVA-44044** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Hiermee wordt het probleem verholpen waarbij een product niet op de categoriepagina wordt weergegeven nadat het aan een nieuwe website is toegewezen.
* **MDVA-42509** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een CSV niet kan worden geüpload voor een snelle bestelling, wat resulteert in een *Kan het cookie niet verzenden* fout.
* Bijgewerkte patches: MDVA-41061, MDVA-42584.
* Het voorvoegsel voor de nieuwe [!DNL Quality Patches Tool] patches worden gewijzigd van *MDVA* tot *ACSD* vanwege interne proceswijzigingen.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een extra item niet aan het winkelwagentje kan worden toegevoegd als de minimumhoeveelheid van het item al in het winkelwagentje staat.
* **MDVA-44887** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5*) - Hiermee worden de *Niet-afgevangen syntaxisfout: Onverwacht token &#39;const&#39;* in het deelvenster Beheer.
* **MDVA-43718** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Oplossingen *De consument heeft geen toegang tot %resources.* fout die wordt weergegeven wanneer u een gedeelde catalogus benadert via een aangepaste integratie.
* **MDVA-44660** (*voor Adobe Commerce en Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij het accent van het graf ligt ``` ` ``` kan niet worden gebruikt voor de voor- en achternaam van een klant.
* **MDVA-40896** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee worden de *Fout: TypeError: Argument 3 doorgegeven aan Magento* fout in async product bulk API.
* **MDVA-38559** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.3*) - Hiermee worden de */V1/customer/search-API* fout voor klanten met meer dan één abonnement.
* **MDVA-44533** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.4*) - Hiermee wordt de kwestie opgelost waarbij de korting ten onrechte wordt toegepast op een onderliggend product van een bundel.
* Bijgewerkte patches: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **MDVA-43983** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waar producten *Niet afzonderlijk zichtbaar* worden nog steeds weergegeven in de geavanceerde zoekresultaten van de catalogus.
* **MDVA-44100** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij alle FPT&#39;s worden toegewezen aan het laatste product in het winkelwagentje en opnieuw worden ingesteld voor andere producten.
* **MDVA-43605** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij met behulp van de Rest API negatieve waarden worden geretourneerd voor rijtotalen.
* **MDVA-43102** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij het verkoopbare aantal niet correct wordt bijgewerkt wanneer een restitutie via REST API wordt uitgevoerd.
* **MDVA-43178** (*voor Adobe Commerce en Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een klanttoken voor een aangepaste store niet kan worden opgehaald in GraphQL.
* **MDVA-43859** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de fout optreedt *Geen dergelijke entiteit met customerId =* wordt geregistreerd wanneer een verwijderde klant probeert zich aan te melden.
* **MDVA-44147** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een GraphQL-aanvraag geen aanvraaglijsten retourneert.
* **MDVA-44505** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.3*) - Hiermee worden de problemen opgelost waarbij GraphQL die terugkerende punten toepast het Eindtotaal niet bijwerkt en waarbij winkelkrediet meerdere keren wordt toegepast tijdens de plaatsing van de order.
* Bijgewerkte patches: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-39993-V2.

## v1.1.13 {#v1-1-13}

* **MDVA-42969** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij de regel Verwante producten alleen werkt als het klantsegment is ingesteld op *Alles*.
* **MDVA-39605** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij Redis cache TTL (vervaldatum) een onjuiste waarde heeft.
* **MDVA-43862** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de klant geen winkelwagentjes kan bijwerken vanwege een GraphQL *UpdateCartItems-mutatie* fout.
* **MDVA-43824** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt bij het annuleren van bestellingen met een korting.
* **MDVA-43451** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de fout optreedt *De aangevraagde winkel is niet gevonden. Controleer de winkel en probeer het opnieuw.* verschijnt tijdens het configureren van een gedeelde catalogus voor een specifieke website.
* **MDVA-43491** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij het basisafbeeldingslabel niet wordt bijgewerkt wanneer u producten importeert voor een website met meerdere winkels.
* **MDVA-43601** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Het probleem met ontbrekende triggers wordt opgelost na volledige herindex.
* **MDVA-42046** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een onjuiste waarde wordt toegewezen aan een productkenmerk met een datuminvoerveld tijdens het bijwerken van een product.
* **MDVA-43935** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij het Upsell-product tweemaal wordt weergegeven.
* **MDVA-44188** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Het probleem waarbij door het systeem verzonden e-mails met `.-` in adressen worden niet verzonden.
* **MDVA-42283** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de datum-tijdnotatie in het beheerorderraster voor de Franse landinstelling ongeldig is.
* Bijgewerkte patches: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Metagegevens van patches toegevoegd voor de [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **MDVA-39713** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij de gebruiker de begintijd voor een actieve geplande update kan bewerken.
* **MDVA-42410** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt de emissie gecorrigeerd waarbij in couponrapporten alleen de standaardbasisvaluta wordt weergegeven.
* **MDVA-41136** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de vervaldatum van de `mage-cache-sessid` niet wordt uitgebreid, wat leidt tot het opschonen van klantgegevens.
* **MDVA-3993** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij inventariswijzigingen die via de API worden doorgevoerd, niet op de productpagina op de voorzijde worden weergegeven.
* **MDVA-42855** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een nieuw klantadres niet in het adresboek wordt opgeslagen tijdens het afrekenen.
* **MDVA-42645** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de beheerder geen bonuspunten kan terugbetalen als de functionaliteit voor winkelkrediet is uitgeschakeld.
* **MDVA-43414** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Hiermee wordt de fatale fout in PHP gecorrigeerd die optreedt bij het uitvoeren van de `inventory.reservations.updateSalabilityStatus` rij consument op numerieke SKUs.
* **MDVA-41628** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij bestaande beperkte beheergebruikers toegang krijgen tot de nieuwe bronnen wanneer nieuwe modules worden toegevoegd.
* **MDVA-43348** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een grafischeQL-aanvraag voor een cadeaukaart een fout laat zien als `gift_card_options` bevatten *uid*.
* **MDVA-39546** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de begindatum voor de gefaseerde update tijdens het bewerken kan worden ingesteld op een eerdere datum dan de huidige datum.
* **MDVA-42950** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Het probleem waarbij video&#39;s niet op de productpagina worden afgespeeld, is opgelost.
* **MDVA-42689** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Het probleem waarbij Adobe Commerce een *Intensiteitsbeperking schending* fout tijdens het bijwerken van productcategorieën tijdens het importeren.
* **MDVA-41229** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij afbeeldingen die op de achtergrond beschikbaar zijn, niet op de voorzijde worden weergegeven nadat configureerbare producten zijn geïmporteerd.
* **MDVA-43731** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij *Synoniemen zoeken* werkt niet meer wanneer waarde wordt toegevoegd in *Minimale voorwaarden*.
* **MDVA-43232** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij sorteerproducten in [!DNL Visual Merchandiser] Door Speciale prijs voor Onder/Boven veroorzaakt u een fout bij het opslaan van de rubriek.
* **MDVA-43726** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de catalogusprijsregel op basis van kenmerk op archiefniveau niet wordt toegepast na gedeeltelijke herindex.
* Bijgewerkte patches: MDVA-36464, MDVA-37478, MDVA-38608.
* Metagegevens van patches toegevoegd voor de [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij productprijskenmerken niet kunnen worden bijgewerkt voor een specifieke website via REST API.
* **MDVA-41350** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een uitzondering wordt gegenereerd wanneer een beheerder met beperkte toegang een product buiten het rolbereik in een volgorde door SKU toevoegt.
* **MDVA-42269** (*voor Adobe Commerce en Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een beheerder zich niet kan aanmelden bij de beheerder vanwege de *TypeError: strtotime() verwacht dat parameter 1 tekenreeks is, null gegeven* fout.
* **MDVA-40830** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij het winkelkrediet meerdere keren wordt toegepast tijdens het plaatsen van de bestelling.
* **MDVA-42237** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij een configureerbare speciale prijs van het product niet wordt bijgewerkt na wijzigingen in de prijs van het subproduct.
* **MDVA-42520** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt de kwestie opgelost waarbij het belastingtarief tweemaal wordt toegepast als *Grensoverschrijdende handel inschakelen* wordt gebruikt.
* Bijgewerkte patches: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Verouderde patch: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **MDVA-38728** (*voor Adobe Commerce en Magento Open Source >=2.3.2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij bij het bijwerken van het massakenmerk alleen na het wijzigen een URL wordt gemaakt die wordt herschreven voor de standaardwinkel *Zichtbaarheid van product*.
* **MDVA-43091** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij de fout optreedt wanneer op de achtergrond een bundelproduct van de beheerder wordt besteld *U kunt geen decimale hoeveelheid gebruiken voor dit product*.
* **MDVA-40816** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij producten uit categorieën die niet in de algemene voorwaarden zijn gedefinieerd, in de desbetreffende productregels worden vermeld.
* **MDVA-41305** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij GraphQL-mutatie geen configureerbare productopties retourneert nadat deze aan de wenslijst is toegevoegd.
* **MDVA-39181** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij producten uit categorieën die niet in de algemene voorwaarden zijn gedefinieerd, in de desbetreffende productregels worden vermeld.
* **MDVA-42584** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de configureerbare voorraadstatus op de achtergrond niet wordt bijgewerkt nadat de status van de hoeveelheid en de voorraad via Importeren of API is gewijzigd.
* **MDVA-40175** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij *Klik om de verzendmethode te wijzigen* Keuzerondjes worden niet weergegeven om verzendmethoden in de beheerdersgroep te selecteren tijdens het opnieuw ordenen.
* **MDVA-42768** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een standaardprijs van het product wordt ingesteld op 0 wanneer *Weergeven uit voorraad* Ja.
* **MDVA-43201** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt bij het aanmelden bij de klant bij het gebruik van het DOB-kenmerk voor bepaalde landinstellingen.
* Bijgewerkte patches: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **MDVA-38346** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij datumfilters niet goed werken wanneer de Adobe Commerce-tijdzone afwijkt van de tijdzone van de lokale omgeving.
* **MDVA-42657** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de gebruiker van de beheerder geen categorieën kan selecteren onder de voorwaarden van het klantensegment.
* **MDVA-42806** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij een *Nieuwe bedrijfsregistratie* Elke keer dat een bestaand bedrijf via de REST API wordt bijgewerkt, wordt een e-mail verzonden.
* **MDVA-37984** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de [!DNL Visual Merchandiser] *Product op regel afstemmen* de functionaliteit filtert producten met het opvoeren van updates correct niet.
* **MDVA-40488** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem opgelost dat configureerbare producten met kinderproducten uit de voorraad niet in hun juiste prijsbereik worden weergegeven.
* **MDVA-42507** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de cache van de volledige pagina wordt opgeschoond nadat een faseupdate voor de kartelregel is toegepast.
* **MDVA-39163** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij geen verzendmethoden beschikbaar zijn wanneer een nieuwe gebruiker wordt geregistreerd en producten in de winkelwagen afkomstig zijn van de gastsessie.
* **MDVA-38626** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de beheerder geen volgorde op de achtergrond kan plaatsen met de opdracht [!DNL PayPal Payflow Pro] betaling.
* **MDVA-38666** (*voor Adobe Commerce en Magento Open Source >=2.3.2 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij de gebruiker van de beheerder de configureerbare productopties in de winkelwagentje van de klant niet kan wijzigen.
* **MDVA-38526** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij de beheerder geen toegang heeft tot de [!DNL Site-Wide Analysis tool].
* Bijgewerkte patches: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **MDVA-41215** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij gebruikers de 500-fout krijgen nadat ze de instelling *afbeeldingsberichten* cookie, als deze al bestaat, maar er zijn geen nieuwe berichten.
* **MDVA-41139** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij configureerbare producten uit voorraad raken na het importeren van producten wanneer een eenvoudige producthoeveelheid voor een van de bronnen gelijk is aan 0.
* **MDVA-42326** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij klanten na een sessietime-out een fout krijgen bij het uitchecken, zelfs als het permanente winkelwagentje is ingeschakeld.
* **MDVA-42341** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij de `categoryList` De vraag GraphQL filtert geen resultaten als een verzoek de kopbal van de Opslag heeft.
* **MDVA-38393** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij de catalogusregels niet meer werken voor een configureerbaar product als de naam van het eenvoudige product wordt gewijzigd.
* **MDVA-39153** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een kortingsbedrag onjuist wordt berekend tijdens het opnieuw ordenen in de beheerder.
* Bijgewerkte patches: MDVA-28993, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij beheergebruikers geen toegang hebben tot het raster van de klant nadat ze de website hebben verwijderd.
* **MDVA-40311** (*voor Adobe Commerce en Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij beheergebruikers het foutbericht krijgen *Ongeldige beveiliging of formuliersleutel. Vernieuw de pagina* na aanmelding bij de beheerder als het aangepaste beheerpad is geconfigureerd en de geheime sleutel is ingeschakeld.
* **MDVA-41631** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij gebruikers een fout ondervinden bij het ophalen van ordergegevens zonder een optionele *telefoon* waarde via GraphQL.
* **MDVA-27239** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij geen producten voor kruisverkoop worden weergegeven.
* Bijgewerkte patches: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-34551, MDVA-31791.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij ontbrekende producten aan de voorzijde worden aangetroffen tijdens het opnieuw uitsnijden.
* **MDVA-40120** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij het sorteren met GraphQL op DESC/ASC niet werkt met producten met dezelfde relevantie of prijs.
* **MDVA-41399** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij beheergebruikers geen toegang hebben tot de *Winkelwagentje beheren* pagina als een klant een product aan de verlanglijst toevoegt.
* **MDVA-40609** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij gegevens over uitgeschakelde producten ontbreken in de `cataloginventory_stock_status` indextabel met onjuiste hoeveelheden van uitgeschakelde producten.
* **MDVA-39031** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost dat het toevoegen van een product aan het winkelwagentje via GraphQL mogelijk is, zelfs als het product niet aan de doelwebsite is toegewezen.
* **MDVA-41597** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij gebruikers een fout krijgen wanneer ze meer dan één configureerbaar product aan het winkelwagentje toevoegen met behulp van GraphQL.
* **MDVA-27456** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.3.7*) - Hiermee wordt het probleem verholpen waarbij gebruikers een fout ondervinden bij het laden van een toepassing [!DNL Swagger].
* **MDVA-32776** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de voorraadstatus niet wordt bijgewerkt wanneer een bestelling wordt geplaatst, maar niet wordt verzonden.
* **MDVA-30862** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.0*) - Hiermee wordt het probleem verholpen met de onjuiste besteldatum op de gedrukte PDF-factuur.
* De indexpagina voor de [!DNL Quality Patch Tool]. Toegevoegde handige zoekfunctie en filterfunctie voor [!DNL quality patches] in de meest recente versie van het gereedschap.
* Bijgewerkte patches: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is een nieuwe geplande update voor een product te maken of te bewerken als de einddatum eerder is verwijderd.
* **MDVA-41046** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Het probleem waarbij eenvoudige producten met aangepaste opties beschikbaar zijn voor het toewijzen aan configureerbare/gegroepeerde producten, is opgelost.
* **MDVA-40545** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij alleen het eerste knooppunt voor een pagina is opgehaald, zelfs als er meer dan één knooppunt voor dezelfde pagina was.
* **MDVA-41164** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Hiermee wordt het probleem verholpen waarbij een beheerder een bedrijf met een aangepast klantkenmerk voor het bestands- of afbeeldingstype niet kan opslaan of bewerken.
* **MDVA-39229** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waardoor de volgende fout optreedt na het bijwerken van de begintijd van update van catalogusregel bijhouden: *Cron Job staging_synchronize_entities_period heeft een fout: De actieve update kan niet worden verwijderd.*
* **MDVA-40619** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij wijzigingen in de hiërarchie van CMS-pagina een fout van 500 veroorzaken bij pogingen om inline te bewerken op een CMS-pagina.
* **MDVA-41061** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de voorraadstatus wordt hersteld naar de verkoopwaarde wanneer een product wordt opgeslagen bij de beheerder.
* **MDVA-31763** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij de prijsregels voor catalogi worden teruggedraaid (of niet worden toegepast) totdat ze handmatig opnieuw worden berekend.
* **MDVA-37748** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij een GraphQL-query producten retourneert die niet zijn toegewezen aan een gedeelde catalogus.

## v1.1.4 {#v1-1-4}

* **MDVA-40399** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij gedeeltelijke facturen voor dezelfde volgorde niet gelijktijdig via REST API kunnen worden gemaakt.
* **MDVA-40101** (*voor Adobe Commerce en Magento Open Source >=2.3.2 &lt;2.4.0*) - Hiermee wordt het probleem verholpen waarbij items niet uit de miniwinkelwagen worden verwijderd nadat de bestelling is geplaatst met [!DNL PayPal Express] Afhandeling.
* **MDVA-40401** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Hiermee wordt de emissie gecorrigeerd waarbij de waarde van het coupongebruik verandert, zelfs als het plaatsen van een bestelling mislukt.
* **MDVA-40537** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Hiermee wordt het probleem verholpen waarbij gebruikers een fout krijgen bij het maken van een winkelweergave als er meerdere CMS-pagina&#39;s met dezelfde URL-sleutel bestaan.
* **MDVA-37725** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Hiermee wordt het probleem verholpen waarbij asynchrone bestellings-e-mails die van niet-standaard websites worden verzonden logo-URL&#39;s van de standaardwebsite bevatten.
* **MDVA-39482** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij een product uit voorraad komt als het wordt geïmporteerd met de hoeveelheid &quot;0&quot; als backorders zijn ingeschakeld.
* **MDVA-40435** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.4*) - Het probleem wordt opgelost met een onjuiste korting op bundelproducten met dynamische prijzen wanneer deze via GraphQL worden toegepast.
* **MC-42528** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Hiermee wordt het probleem opgelost waarbij de `categoryList` De vraag GraphQL keert zowel toegewezen als niet toegewezen categorieën terug.
* **MDVA-29400** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Het probleem wordt verholpen met dubbele bestellingen die worden geplaatst met [!DNL PayPal Express Checkout].
* **MDVA-26005** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is om een categorie in een categoriestructuur te selecteren voor de regelvoorwaarden voor winkelwagentjes.
* **MDVA-25631** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Verbetert de prestaties voor het bewerken en opslaan van klantsegmenten met een groot aantal klanten.

## v1.1.3 {#v1-1-3}

* **MDVA-40262** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij GraphQL-zoekopdrachten niet worden weergegeven in populaire zoektermen in de Admin.
* **MDVA-40601** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Hiermee wordt het probleem verholpen waarbij gebruikers een fout krijgen wanneer ze proberen om informatie over de categorie te wijzigen via een geplande update via GraphQL.
* **MDVA-37234** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Hiermee wordt het probleem verholpen waarbij een item meerdere keren (parallel verzoek) voor dezelfde SKU aan het winkelwagentje wordt toegevoegd, waardoor een dubbel regelitem voor dezelfde winkelwagentje-id wordt gemaakt.
* **MDVA-33606** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Het probleem waarbij gebruikers een *Unieke schending van beperking* fout bij het opslaan van een CMS-pagina die is toegewezen aan een hiërarchie.
* **MDVA-31590** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Hiermee wordt het probleem verholpen waarbij gebruikers geen kenmerken in bulk kunnen bijwerken met MySQL async-wachtrijen.
* **MDVA-36309** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Het probleem waarbij het zoeken naar kenmerken van producten traag verloopt in de beheerrasters wordt opgelost.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt de kwestie opgelost waarbij op de factuur met het FPT een verkeerde Grand Total wordt getoond wanneer de bestelling uit het winkelkrediet wordt betaald.
* **MDVA-37364** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;=2.4.3*) - Hiermee wordt het probleem verholpen waarbij het aangepaste kenmerk voor klanten van het datumtype de interface van het raster van de klant verbreekt.
* **MDVA-39195** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Hiermee wordt het probleem opgelost waarbij *Toevoegen aan winkelwagentje* button was inactief op de categoriepagina wanneer omleiding naar winkelwagentje ingeschakeld was.
* **MDVA-37115** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Hiermee wordt het probleem opgelost dat een *Slechts 0 links* op de configureerbare productpagina wordt een waarschuwing weergegeven.
* **MDVA-39521** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij de gebruiker geen verzendadressen op de winkelwagentje kan instellen met een leeg telefoonnummer via GraphQL.
* **MDVA-39384** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Hiermee wordt het probleem verholpen waarbij het aangepaste klantkenmerk voor een bedrijfsgebruiker niet wordt opgeslagen.
* **MDVA-39043** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.4.3*) - Hiermee wordt het probleem verholpen waarbij de beheerder met beperkte toegang een fout krijgt bij het toevoegen van de *Producten* widget naar de CMS-pagina.
* **MDVA-39966** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Het probleem is opgelost door onjuiste landinstellingen te gebruiken.
* **MDVA-38852** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij de catalogusvoorraad door het ontwerp tabellen vergrendelt voor updates die de prestaties aanzienlijk verminderen in gevallen met meerdere parallelle bestellingen.
* **MDVA-39986** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de gebruiker via de Safari-browser geen bestelling kan plaatsen in de Admin op MacOS.
* **MDVA-38447** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee worden twee problemen opgelost: waarbij *Niet afzonderlijk zichtbaar* configureerbare kindproducten zijn teruggekeerd in reactie GraphQL en optimaliseer vraag MySQL voor de productvraag GraphQL met categoriefilter.
* **MDVA-40134** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij GraphQL geen verwante producten retourneert wanneer de gedeelde catalogus is ingeschakeld.
* **MDVA-39935** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij GraphQL configureerbare onderliggende producten retourneert die op websiteniveau zijn uitgeschakeld.

## v1.1.1 {#v1-1-1}

* **MDVA-36021** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij de *Aanroep van een lidfunctie getId()* Er wordt een fout weergegeven op de pagina met orderdetails in Admin.
* **MDVA-34948** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Het probleem wordt opgelost met langdurige query&#39;s, zoals `GET_LOCK`.
* **MDVA-39305** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij geregistreerde klanten zich niet kunnen aanmelden met de ingeschakelde Google ReCaptcha.
* **MDVA-37897** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Het probleem wordt verholpen met een onjuiste omleiding wanneer een klant producten probeert toe te voegen met opties van de onlangs bekeken widget.

## v1.1.0 {#v1-1-0}

* Patchcategorieën zijn geïntroduceerd om de gebruikerservaring te verbeteren en het zoeken naar vereiste patches voor klanten eenvoudiger te maken.
* De `patches.json` bestand is hernoemd naar `support-patches.json`.
* **MDVA-38799** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij downloadbare producten niet zijn opgeslagen na het maken van een testupdate.
* **MDVA-37592** (*voor Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Het probleem wordt verholpen wanneer sorteren op prijs niet correct werkt voor producten met een nulprijs die aan de gedeelde catalogus is toegewezen.
* **MDVA-38827** (*voor Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij klanten een e-mail met een bestelbericht ontvangen dat een foutbericht bevat.

## v1.0.26 {#v1-0-26}

* **MDVA-38468** (*voor Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Hiermee wordt de fout bij het opslaan van CMS-pagina&#39;s gecorrigeerd: *Item met dezelfde id PAGE_ID bestaat al*.
* **MDVA-34680** (*voor Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de tijd die voor de Customer Account is gemaakt, niet correct is gefilterd in het klantenraster.
* **MDVA-37068** (*voor Adobe Commerce >=2.3.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij het onjuiste belastingtarief wordt weergegeven wanneer het winkelwagentje alleen virtuele producten bevat.
* **MDVA-38608** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij tijdelijke tabellen niet worden verwijderd als de redex niet met succes is voltooid.
* **MDVA-38308** (*voor Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Hiermee worden de problemen opgelost die te maken hebben met de toevoeging [!DNL Vimeo] video&#39;s naar producten.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*voor Adobe Commerce >=2.3.6 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de klant niet naar de pagina Betalingsbevestiging wordt geleid wanneer de gebruiker de [!DNL Paypal Payment Advanced] methode.
* **MDVA-37082** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Het probleem wordt verholpen wanneer de aangepaste voorraad gegroepeerde producten wordt opgeslagen, waardoor het product op de voorgrond uit voorraad komt te staan.
* **MDVA-36572** (*voor Adobe Commerce >=2.3.5 &lt;2.4.3*) - Hiermee wordt het probleem verholpen wanneer updates van creditnota niet langer leiden tot dubbele updates van productreserveringen in de database.
* **MDVA-38132** (*voor Adobe Commerce >=2.3.3 &lt;2.4.3*) - Het probleem wordt opgelost wanneer het deelvenster Beheer niet bereikbaar is vanwege een *te veel omleidingen* fout.
* **MDVA-38270** (*voor Adobe Commerce >=2.4.1 &lt;2.4.3*) - Het probleem wordt opgelost met ontbrekende gegevens van een creditcard in de volgorde totaal in GraphQL.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*voor Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Het probleem is opgelost door een configureerbaar product aan het winkelwagentje toe te voegen via GraphQL wanneer de website-id niet overeenkomt met de winkel-id.
* **MDVA-36832** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij afbeeldingen worden gedupliceerd op pagina&#39;s met een weergavebreedte van 768 px.
* **MDVA-37874** (*voor Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Hiermee wordt het probleem opgelost waarbij *Vaste korting voor hele winkelwagen* wordt verkeerd toegepast op een bundelproduct dat meer dan één optie bevat.
* **MDVA-37913** (*voor Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Hiermee wordt het probleem verholpen waarbij downloadbare koppelingen verdwijnen als het downloadbare product via de API wordt bijgewerkt.
* **MDVA-34330** (*voor Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij orders in het raster Bestellingen niet worden gefilterd volgens de tijdzone van Admin.

## v1.0.23 {#v1-0-23}

* **MDVA-37478** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Het probleem waarbij Adobe Commerce een fout genereert bij het maken van een gedeeltelijke factuur voor bestellingen die bij de *Betaling op rekening* betalingsmethode via REST API.
* **MDVA-37362** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij configureerbare waarden voor productopties en variantkenmerken leeg waren in GraphQL-respons.
* **MDVA-37288** (*voor Adobe Commerce 2.4.2*) - Hiermee wordt het probleem opgelost waarbij onjuiste prijzen op de niveaus werden geretourneerd na een GraphQL-verzoek.
* **MDVA-37225** (*voor Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij het uploadproces vastloopt tijdens het maken van snelle bestellingen wanneer geïmporteerde SKU&#39;s een geheel-getalwaarde hebben.
* **MDVA-37224** (*voor Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Oplossing van het probleem waarbij klanten niet kunnen betalen voor een verhandelbare prijsopgave [!DNL PayFlow Pro] met een ander product in de kar.
* **MDVA-36286** (*voor Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij de voorvertoning van de widget voor pagina Builder-producten wordt afgebroken als dezelfde SKU een andere positie in subcategorieën heeft.
* **MDVA-30186** (*voor Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij kenmerkopties worden gesorteerd op optiewaarde in plaats van op het aantal kenmerkitems in de reactie GraphQL.

## v1.0.22 {#v1-0-22}

* **MDVA-36718** (*voor Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Hiermee wordt het probleem verholpen waarbij de oude aangepaste opties blijven bestaan nadat deze via API zijn gewijzigd.
* **MDVA-35773** (*voor Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Hiermee wordt de kwestie opgelost waarbij het Eindtotaal niet als nul op de factuur wordt weergegeven voor bestellingen met een korting van 100%.
* **MDVA-36833** (*voor Adobe Commerce 2.4.2*) - Het probleem wordt verholpen met zoekresultaten die een willekeurig aantal producten per pagina laten zien nadat bepaalde producten van de gedeelde catalogus zijn uitgesloten.
* **MDVA-37182** (*voor Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Het probleem wordt verholpen door onjuiste zoekresultaten op te halen in beide [!DNL Elasticsearch] versie 6 en versie 7.
* **MDVA-36253** (*voor Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Hiermee wordt het probleem opgelost waarbij het onjuiste subtotaal in het minikaart wordt weergegeven na verwijdering van het item.
* **MDVA-36853** (*voor Adobe Commerce 2.4.2*) - Het probleem is opgelost zonder afbeeldingen die worden weergegeven wanneer grote mediagalerieën worden geladen.

## v1.0.21 {#v1-0-21}

* **MDVA-34665** (*voor Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Het probleem met ontbrekende gebundelde producten op categoriepagina&#39;s wordt opgelost.
* **MDVA-36615** (*voor Adobe Commerce 2.4.2*) - Het probleem wordt verholpen met een onjuist aantal producten in het productraster van Admin.
* **MDVA-36464** (*voor Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Hiermee wordt het probleem verholpen waarbij de configuratie van de e-mailmelding niet werkt in de winkelweergave.
* **MDVA-36138** (*voor Adobe Commerce ^2.3.2*) - Hiermee wordt het probleem opgelost waarbij de verzendprijs niet wordt aangepast en de volledige verzendprijs aan klanten wordt getoond als niet alle objecten in de winkelwagentje in aanmerking komen voor de regel voor het gratis verzenden van winkelwagentjes.
* **MDVA-36424** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Hiermee wordt het probleem verholpen waarbij mediaafbeeldingen die zijn gekoppeld aan elementen van de paginaontwikkelaar verdwijnen als de inhoud herhaaldelijk wordt bewerkt als de URL van de achterste basis afwijkt van de URL van de opslagbasis.
* **MDVA-35984** (*voor Adobe Commerce ^2.4.0*) - Hiermee wordt het probleem verholpen met een onjuiste producthoeveelheid en een verkoopbare hoeveelheid nadat meerdere gelijktijdige verzendingen voor hetzelfde product zijn gemaakt.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Dit verhelpt de kwestie waar de vraag GraphQL niet in het voorgeheugen onderbrengend door de markering van het categoriegeheime voorgeheugen te gebruiken.
* **MDVA-33168** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Het probleem wordt verholpen wanneer een productkenmerk via API wordt bijgewerkt. Alle andere kenmerken worden gewijzigd in een lege waarde.
* **MDVA-19640** (*voor Adobe Commerce >=2.3.0*) - Hiermee wordt het probleem opgelost waarbij [!DNL Advanced Reporting] geeft geen gegevens weer.
* **MDVA-11189** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - Het probleem wordt verholpen wanneer een CSV-bestand is geïmporteerd om de productvoorraad bij te werken, rijen van de `cataloginventory_stock` tabel worden verwijderd.
* **MDVA-26639** (*voor Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij de orderonderdelen ontbreken in de e-mail met bevestiging van de bestelling als er een nieuwe sjabloon voor bevestiging van de bestelling wordt gemaakt.
* **MDVA-15546** (*voor Adobe Commerce >=2.3.0*) - Hiermee wordt het probleem opgelost waarbij na het maken van een bestelling een *Kolomentiteit_id waarbij de component dubbelzinnig is* de foutenvertoningen in het uitzonderingslogboek.
* **MDVA-21095** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - Hiermee wordt het probleem verholpen wanneer een query wordt uitgevoerd `INSERT INTO search_tmp` eindigt niet na de update van de waarde van het kenmerk mass.
* **MDVA-23845** (*voor Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Hiermee wordt het probleem verholpen waarbij geen voorbeeld kan worden weergegeven van e-mailsjablonen nadat JavaScript-miniatuur is ingeschakeld.
* **MDVA-2026** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - Het probleem waarbij het importeren van producten uit CSV-bestand, inclusief afbeeldingen van externe URL&#39;s, mislukt.
* **MDVA-22383** (*voor Adobe Commerce >=2.3.0 &lt;2.3.4*) - Het probleem waarbij het opslaan van een product veel tijd in beslag neemt en de pagina-einden.
* **MC-41359** (*voor Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem met de onjuiste instellingen van de SameSite-cookie-parameters opgelost.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*voor Adobe Commerce 2.4.1*) - Hiermee wordt het probleem verholpen waarbij de Page Builder de volgende fout veroorzaakt: *Er is een fout opgetreden bij het starten van de Page Builder. Neem contact op met uw contactpersoon voor technische ondersteuning.*
* **MDVA-35356** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen met een onjuist rendement op winkelkredieten nadat de bestelling gedeeltelijk is geannuleerd.
* **MDVA-33289** (*voor Adobe Commerce >=2.4.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij onbewerkte JavaScript-code wordt weergegeven in de gebruikersinterface van het factureringsadres tijdens het uitchecken als [!DNL Google Tag Manager] is ingeschakeld.
* **MDVA-35982** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij beheerders die zich tot een bepaalde website beperken, geen verzending kunnen maken voor de bestelling die op dezelfde website is geplaatst.
* **MDVA-35155** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is om een bundelproduct te kopen als de optietitel is gewijzigd.
* **MDVA-35910** (*voor Adobe Commerce >=2.4.1 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is een nieuwe klantenaccount te maken nadat de aanmelding als functionaliteit van de klant is uitgeschakeld.
* **MDVA-34474** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Het probleem wordt verholpen door een product met de API toe te voegen aan de aanvraaglijst.
* **MDVA-34591** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem opgelost met een onjuiste berekening van de winkelregelkorting voor *Maximale korting op aantal wordt toegepast op* en *Kortingsstap (X kopen)*.
* **MDVA-33704** (*voor Adobe Commerce >=2.4.0 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij de *Ophalen in winkel* De verschepende optie verschijnt niet, hoewel wordt gevormd om beschikbaar te zijn.
* **MDVA-34928** (*voor Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij de paginalader oneindig wordt weergegeven nadat het winkelkrediet uit de betaling is verwijderd.
* **MDVA-35254** (*voor Adobe Commerce >=2.3.1 &lt;2.4.3*) - Hiermee verhelpt u de problemen met CAPTCHA tijdens het afrekenen.
* **MDVA-35569** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de *vaste productbelastingen* wordt het veld niet gevuld in GraphQL-reactie als de status is opgegeven.
* **MDVA-35847** (*voor Adobe Commerce >=2.4.1 &lt;2.4.3*) - Hiermee wordt het B2B-probleem verholpen waarbij het formulier Bedrijfgebruikers wordt afgebroken als een aangepast kenmerk van de klant wordt gebruikt.
* **MDVA-31307** (*voor Adobe Commerce >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waar *Onvoldoende geheugen* fouten op bepaalde categorieën als gevolg van problemen met de dynamische whitelisting van CSP voor in cache geplaatste blokken.

## v1.0.18 {#v1-0-18}

* **MDVA-32655** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrigeert het onjuiste *in uitvoering* berichtstatus voor de juiste *complete* boodschap voor de consument `quoteItemCleaner` na het verwijderen van meerdere producten.
* **MDVA-34102** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee stelt u de hoeveelheid standaardvoorraad in op nul voor uitgeschakelde producten op het productraster en op Productpagina&#39;s bewerken in het beheergebied.
* **MDVA-35286** (*voor Adobe Commerce >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt wanneer een klant producten in de winkelwagen heeft gebundeld en overschakelt van het uitchecken van meerdere adressen naar het uitchecken op één pagina.
* **MDVA-35312** (*voor Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Hiermee wordt antwoordcode 500 gecorrigeerd wanneer een leeg GraphQL-verzoek wordt ingediend.
* **MDVA-34189** (*voor Adobe Commerce >=2.3.4 &lt;2.4.3*) - Oplossingen voor 503 eerste byte-time-out op [!DNL Visual Merchandiser] vragen bij het laden van de pagina Admin-categorie.
* **MDVA-34695** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1*) - Oplossingen negatief `children_count` na het verwijderen van categorieën.

## v1.0.17 {#v1-0-17}

* **MDVA-34012** (*voor Adobe Commerce >=2.3.1 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij de *Standaardwaarde gebruiken* Schakel het selectievakje uit nadat de geplande wijzigingen zijn toegepast. De uitgave wordt weergegeven zodra de geplande wijzigingen niet meer van kracht zijn.
* **MDVA-35064** (*voor Adobe Commerce >=2.3.3 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij URL-herschrijvingen niet worden gegenereerd voor configureerbare producten die via API zijn gemaakt.
* **MDVA-34943** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de eerder ingevoerde SKU&#39;s in een cache worden opgeslagen met een snelle volgorde.
* **MDVA-35197** (*voor Adobe Commerce >=2.3.5 &lt;2.4.0*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt bij het toevoegen aan winkelwagentje met behulp van GraphQL als eerder toegevoegde producten uit voorraad raken.
* **MDVA-34850** (*voor Adobe Commerce >=2.3.1 &lt;2.4.0*) - Hiermee wordt het probleem verholpen waarbij de opties voor een configureerbaar product die buiten de voorraad vallen, niet worden weergegeven in plaats van als doorgehaalde afbeelding.
* **MDVA-34867** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij waarden voor een voorwaardenveld dat is ingesteld voor een geplande update, niet worden opgeslagen.
* **MDVA-35092** (*voor Adobe Commerce >=2.3.5 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij gebruikers geen gegevens kunnen toevoegen [!DNL Vimeo] video&#39;s vanwege vervangen [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **MDVA-33453** (*voor Adobe Commerce >=2.3.6 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de voorvertoning van het inhoudstype Pagina Builder-producten wordt onderbroken als overeenkomende producten verschillende prijzen voor elke website hebben.
* **MDVA-32634** (*voor Adobe Commerce ^2.3.1*) - Hiermee wordt het probleem opgelost waarbij de `url_path` van de categorie die aan alle opslagruimten is toegewezen, blijft ongewijzigd nadat de categorie in de hiërarchie is verplaatst.
* **MDVA-33344** (*voor Adobe Commerce ^2.3.0*) - Het probleem met harde codering wordt opgelost `rma_item` id van standaard entiteitskenmerkset wordt gebruikt in plaats van de waarde uit de database.
* **MDVA-34192** (*voor Adobe Commerce >=2.3.4 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is de geboortedatum van de klant te wijzigen of op te geven in de indeling dd/mm/jjjj.
* **MDVA-34847** (*voor Adobe Commerce ^2.3.0*) - Oplossingen opslaan IDs type omzetting in geheel voor SQL voorwaarde in inzamelingen Admin voor Gebruiker Admin met douanetoestemmingen.
* **MDVA-34886** (*voor Adobe Commerce ^2.3.2*) - Hiermee wordt het probleem verholpen waarbij de zoekopdracht geen resultaten oplevert als *gewicht* productkenmerk is geconfigureerd als doorzoekbaar.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Oplossingen voor het probleem van [!DNL PayPal Payflow Pro] betaling mislukt vanwege fout in indeling parameterlijst omleiden.
* **MDVA-34023** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij de fout optreedt *Entiteit met adresId bestaat niet* wordt willekeurig weergegeven in browsers van bezoekers.
* **MDVA-32759** (*voor Adobe Commerce >=2.3.1 &lt;2.4.3 met B2B-extensie*) - Hiermee wordt het probleem verholpen waarbij gedeelde catalogi de bestaande laagprijzen verwijderen.
* **MDVA-33482** (*voor Adobe Commerce ^2.3.5*) - Oplossing van de kwestie waar het genereren van een creditmemo tegen een gedeeltelijke factuur leidt tot belasting voor de totale bestelling in plaats van belasting voor die gedeeltelijke factuur.
* **MDVA-33393** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt de fout gecorrigeerd *Opgegeven landId bestaat niet*.
* **MDVA-33632** (*voor Adobe Commerce >=2.3.0 &lt;2.3.7*) - Verstrekt een moeilijke situatie waar het uitzonderingsbericht *Dit product is uit voorraad* wordt nu weergegeven aan een beheerder die een product uit de voorraad opnieuw probeert te bestellen.
* **MDVA-34469** (*voor Adobe Commerce >=2.4.1 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij GraphQL-mutaties op de winkelwagentje van een klant mislukken wanneer meerdere winkelweergaven worden gebruikt.
* **MDVA-33976** (*voor Adobe Commerce >=2.3.0 &lt;2.3.7*) - Hiermee wordt het probleem opgelost waarbij het bundelproduct uit voorraad op de winkel wordt weergegeven nadat de tweede optie uit het bundelproduct is verwijderd.
* **MDVA-33894** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1 met B2B-extensie*) - Hiermee worden meerdere problemen opgelost voor de functie Snel bestellen, zoals het toevoegen en verwijderen van meerdere producten en de gevoeligheid van SKU-hoofdletters.
* **MDVA-27664** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6*) - Oplossing van het probleem in het registratieformulier voor klanten dat een weergavefout veroorzaakt: *FOUT - De geboortedatum mag niet groter zijn dan vandaag.*
* **MDVA-33970** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Oplossing van de kwestie waar in het creditmemo het verkeerde valutateken staan wanneer het bereik van het prijselement op de website is ingesteld.
* **MDVA-33992** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen van de speciale B2B-prijzen die tijdens het afrekenen onjuist worden weergegeven.
* **MDVA-34100** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2 met B2B-extensie*) - Hiermee wordt de kwestie opgelost waarbij een bedrijfsaccount niet op de pagina met bedrijfsstructuren kan worden gemaakt.

## v1.0.14 {#v1-0-14}

* **MDVA-31969** (*voor Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Het probleem is opgelost met gedupliceerde afbeeldingen nadat het product uit een CSV-bestand is geïmporteerd.
* **MDVA-33382** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee worden de problemen opgelost met de validatie van indexen nadat producten uit een categorie zijn verwijderd.
* **MDVA-28511** (*voor Adobe Commerce >=2.3.5 &lt;2.3.6*) - Hiermee wordt het probleem opgelost dat niet kan worden opgelost [!DNL PayPal] uitchecken als het veld Naam bepaalde tekens bevat (zoals hoofdletters met accent).
* **MDVA-31519** (*voor Adobe Commerce >=2.3.5 &lt;2.3.6*) - Het probleem wordt opgelost door wachttijden op te geven bij uitchecken door gasten wanneer een verkoopregel voor de hele site wordt gebruikt.
* **MDVA-33281** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij een fatale fout optreedt in `inventory:reservation:list-inconsistencies` vanwege onjuist SKU-parametertype.
* **MDVA-24201** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - Hiermee wordt de kwestie opgelost waarbij de prijzen pas na handmatig opnieuw indexeren de regel van de geplande winkelwagenprijs weerspiegelen.
* **MDVA-32694** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een beheerder een product niet kan toevoegen aan een verhandelbaar aanhalingsteken als het betrekking heeft op een niet-standaardwinkel.
* **MDVA-33516** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij het bewerken van een bundelproduct in een aanvraaglijst tot een fout leidt.
* **MDVA-33975** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Oplossingen voor meerdere problemen in verband met prijsberekening in GraphQL-verzoeken.

## v1.0.13 {#v1-0-13}

* **MDVA-30858** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Het probleem verholpen met [!DNL PayPal] Afwikkelingsrapporten niet beschikbaar onder **Rapporten** > **Verkoop** > **[!DNL PayPal]** Afwikkeling zoals verwacht.
* **MCP-87** (*voor Adobe Commerce >=2.3.1 &lt;2.4.2*) - Verbeterde indexatietijd voor producten- en voorraadindexeerders voor grote profielen voor categorieën.
* **MDVA-33106** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij de opnieuw geplande productwijzigingen worden gewist na de kroon `run` wordt uitgevoerd.
* **MDVA-19391** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - Hiermee wordt het probleem opgelost waarbij `analytics_collect_data` genereert een fout vanwege NULL-beschrijvingsrecords in het dialoogvenster `catalog_category_entity_text` tabel.
* **MDVA-20376** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - Het probleem is opgelost met de *Geen dergelijke entiteit met customerId = 1* fout in de `exception.log` voor aangemelde klanten na plaatsing van de bestelling.
* **MDVA-23764** (*voor Adobe Commerce >=2.3.2 &lt;2.3.5*) - Hiermee wordt de fout opgelost in `JsFooterPlugin.php` die de weergave van dynamische blokken beïnvloedt.
* **MDVA-13203** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de *Integriteitsbeperking schending search_tmp_ table* Er wordt een fout weergegeven na een volledige redex.
* **MDVA-23426** (*voor Adobe Commerce >=2.3.3 &lt;2.3.5*) - Hiermee wordt het probleem verholpen waarbij e-mailberichten die door Adobe Commerce zijn verzonden een lege tekst bevatten met inhoud die als bijlage wordt toegevoegd.
* **MDVA-22150** (*voor Adobe Commerce >=2.3.1 &lt;2.3.4*) - Hiermee wordt het probleem verholpen waarbij klanten met een configureerbaar product in de winkelwagen en een coupon niet kunnen inloggen als dat configureerbare product is uitgeschakeld in de beheerder.
* **MDVA-32545** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij facturen niet automatisch worden verzonden bij het maken van bestellingen van de beheerder.
* **MDVA-32714** (*voor Adobe Commerce >=2.3.4 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij de prijs van de klantengroep niet werkt in GraphQL-productquery.

## v1.0.12 {#v1-0-12}

* **MDVA-31399** (*voor Adobe Commerce >=2.3.2 &lt;2.4.2*) - Hiermee voegt u de *Subtotaal (incl. Belasting)* de mogelijkheid om prijsregels toe te passen.
* **MDVA-31236** (*voor Adobe Commerce >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij beheerders met aangepaste resourcetoegang 2FA niet kunnen instellen of zich aanmelden.
* **MDVA-30845** (*voor Adobe Commerce >=2.3.5 &lt;2.3.7*) - Hiermee wordt het probleem opgelost waarbij de *Er zijn momenteel geen aanhalingstekens beschikbaar voor deze bestelling* Er wordt een fout weergegeven wanneer u geen verbinding maakt met UPS XML/USPS/DHL en er geen andere verzendmethode beschikbaar is.
* **MDVA-32133** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij mediagalerie in bepaalde gevallen niet vanaf Page Builder wordt geladen.
* **MDVA-12304** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Het maximumaantal cookies wordt verhoogd van 50 naar 200.
* **MDVA-32632** (*voor Adobe Commerce >=2.3.2 &lt;2.3.5*) - Oplossing van het probleem waarbij in het betalingssysteem, maar niet in Adobe Commerce, bestellingen worden weergegeven.
* **MDVA-32449** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || >=2.4.1 &lt;2.4.2 met B2B-extensie*) - Hiermee wordt het probleem verholpen waarbij de geschiedenis van de bestelling zeer langzaam wordt geladen of helemaal niet wordt geladen.
* **MDVA-32739** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij oude e-mails worden verzonden wanneer asynchrone e-mailberichten worden ingeschakeld.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*voor Adobe Commerce 2.3.6, 2.4.1*) - Hiermee wordt het probleem opgelost waarbij de *Een account maken* de knop blijft uitgeschakeld na correctie van ongeldige gegevens in het dialoogvenster *Nieuwe klantaccount maken* formulier.
* **MDVA-31006** (*voor Adobe Commerce 2.3.0, 2.3.1*) - Hiermee wordt het probleem verholpen waarbij dubbele bestellingen worden weergegeven nadat een bestelling is geplaatst met [!DNL Paypal Express] betaling.
* **MDVA-25602** (*voor Adobe Commerce 2.3.0*) - Probleem opgelost met [!DNL PayPal Payflow Pro] betalingsmethode en cookies behandelen als `SameSite=Lax` standaard wordt in de Chrome 80-browser en API-respons omgeleid naar de aanmeldingspagina van de klant.

## v1.0.10 {#v1-0-10}

Kleine correcties voor patchversies

## v1.0.9 {#v1-0-9}

* **MDVA-31363** (*voor Adobe Commerce >=2.3.2 &lt;2.4.2*) - Hiermee wordt de emissie gecorrigeerd waarbij de regel van de winkelwagenprijs met coupon niet van toepassing is via GraphQL wanneer *Korting op een vast bedrag voor het hele winkelwagentje* actie wordt gebruikt.
* **MDVA-30889** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt nadat een bundel met virtuele en eenvoudige producten als opties is aangeroepen.
* **MDVA-31791** (*voor Adobe Commerce >=2.3.4 &lt;2.3.5*) - Verbetert de prestaties van de productpagina in gevallen waarin doelregels of gekoppelde producten worden gebruikt.
* **MDVA-31168** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij het CSV-bestand voor het exporteren van het product niet wordt weergegeven en er een fout in de geheugentoewijzing optreedt.
* **MDVA-32313** (*voor Adobe Commerce >=2.3.0 &lt;2.3.4*) - Hiermee wordt het probleem opgelost waarbij configureerbare producten aan de verlanglijst kunnen worden toegevoegd met de verkeerde configuratieopties.
* **MDVA-31759** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij producten niet worden bijgewerkt met *druppel* en *textarea* kenmerkwaarden tijdens het importeren van CSV.
* **MDVA-32012** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost dat postcodes in Korea en Argentinië niet kunnen worden gevalideerd.
* **MDVA-31640** (*voor Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij een speciale prijs niet kan worden bijgewerkt via REST API.
* **MDVA-28651** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 met B2B-extensie*) - Het probleem met prestatieproblemen bij het laden van verhandelbare aanhalingstekens via REST API wordt opgelost.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1 met B2B-extensie*) - Hiermee wordt de kwestie opgelost waarbij een onjuist valutateken wordt weergegeven in het credit memo-raster.
* **MDVA-31295** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt de kwestie opgelost waarbij beloningspunten niet worden berekend wanneer een gedeeltelijke bestelling wordt voltooid en items worden belast.
* **MDVA-30112** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermee wordt de kwestie opgelost waarbij het aantal bestellingen groter is dan *troebelgrootte* waarde, Adobe Commerce beschouwt de orders als *hangend* status als inconsistenties.
* **MDVA-31150** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Oplossing van het probleem waarbij de tegoeden van de creditcard van de winkel en van de cadeaukaart niet worden geretourneerd door de aanroep van de API voor facturering van de GET, wanneer de factuur werd gepost door de Rest API-aanroep en de bestelling gedeeltelijk werd betaald door creditcardrekeningen van de winkel.
* **MDVA-30963** (*voor Adobe Commerce >=2.3.2 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij filterresultaten die zijn ingesteld op alleen waarden bevatten die zijn opgegeven voor *Alle winkelweergaven* bereik in de beheerdersinterface: omvat producten met waarden die op het weergaveniveau van de winkel zijn overschreven.
* **MDVA-29954** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0 || 2.4.2 met B2B-uitbreiding*) - Hiermee wordt het probleem opgelost waarbij de *Nieuwe aanvraag voor registratie van bedrijf* en *U bent verbonden met een bedrijf* e-mails worden verzonden vanaf het verkeerde adres.
* **MDVA-28357** (*voor Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Hiermee vervangt u de standaardanalysator door een aangepaste analysator met een trefwoordtokenizer voor het SKU-veld in het dialoogvenster [!DNL ElasticSearch] index om zoekopdrachten met jokertekens te laten werken met SKU&#39;s die een afbreekstreepje (&quot;-&quot;) bevatten.

## v1.0.7 {#v1-0-7}

* **MDVA-30972** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de aangepaste orderstatus is gewijzigd in *Verwerking* na gedeeltelijke verzending met gebruik van WebApi.
* **MDVA-30428** (*voor Adobe Commerce >=2.3.4 &lt;2.3.5*) - Hiermee wordt het probleem verholpen waarbij klanten een product niet aan de verlanglijst kunnen toevoegen als dit product aan een aangepaste inventarisbron is toegewezen.
* **MDVA-30594** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een bestelling met meerdere adressen niet kon worden opgeslagen tijdens het uitchecken wanneer FPT is geconfigureerd.
* **MDVA-29148** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Het probleem wordt verholpen wanneer een product wordt gemaakt via een API-aanroep, het aangepaste productkenmerk van `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (zoals Multiselect) gebruikt de standaardwaarde niet als er geen waarde in de lading is opgegeven.
* **MDVA-30837** (*voor Adobe Commerce >=2.3.1 &lt;2.3.5*) - Een configuratie-instelling toegevoegd *Inclusief BTW op bedrag: Ja/Nee* in configuratie van de methode Free Shipping. Wanneer *Inclusief BTW op bedrag* is ingesteld op *Ja*, Minimumbedrag bestelling wordt berekend als Subtotaal + BTW. Wanneer *Inclusief BTW op bedrag* is ingesteld op *Nee*, Minimumbedrag bestelling wordt berekend als Subtotaal
* **MDVA-25028** (*voor Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Het probleem wordt verholpen wanneer bestellingen worden geplaatst met [!DNL PayPal Payflow Pro] niet zijn ingesteld op de status Vermoedelijke fraude wanneer er fraudefilters worden geactiveerd.
* **MDVA-31224** (*voor Adobe Commerce >=2.3.3 &lt;2.3.5*) - Verbetert de prestaties van de `catalog_product_price` herindexering van de bundelproducten.
* **MDVA-31321** (*voor Adobe Commerce >=2.3.2 &lt;2.3.5*) - Hiermee wordt een lege pagina gecorrigeerd (fout) wanneer *Alles tonen* is geselecteerd. [!DNL Elasticsearch] retourneert een grote lijst met product-id&#39;s. In dit scenario wordt de volgorde door de component omgezet in een onjuiste SQL-indeling.
* **MDVA-30815** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - Hiermee wordt het probleem verholpen waarbij Adobe Commerce een lege pagina weergeeft wanneer u wijzigt hoeveel zoekresultaten op de pagina met zoekresultaten moeten worden weergegeven. [!DNL Elasticsearch] geeft nu correct de resultaten van categoriepagina&#39;s weer wanneer u het aantal weergegeven zoekresultaten per pagina wijzigt.
* **MDVA-30782** (*voor Adobe Commerce >=2.3.5 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij Dynamisch blok wordt weergegeven, ongeacht de regels voor winkelwagentjes.
* **MDVA-31021** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij prestatieproblemen optreden in `module-catalog-import-export/Model/Import/Product/Option.php`. Als er meer dan ~100k records zijn in `catalog_product_option` een nieuwe CSV met één product duurt minder dan 10 seconden om te valideren.
* **MDVA-31007** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij aangepaste adreskenmerken niet correct worden weergegeven op de pagina met orderdetails in het gebied Mijn account en op de achtergrond.
* **MDVA-29389** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Het probleem wordt verholpen met Geavanceerde rapportage waarbij de `analytics_collect_data` cronjob zegt : *De haven moet binnen gastheerparameter (als localhost:3306) worden gevormd*.
* **MDVA-31343** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6*) - Het probleem wordt verholpen met de verwijderde body-klasse `page-layout-category-full-width` wanneer een categorie gepland is.
* **MDVA-30945** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een onherstelbaar foutbericht wordt weergegeven wanneer winkelwagentjes worden bijgewerkt `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-28993** (*voor Adobe Commerce >=2.3.4 &lt;2.4.0*) - Hiermee wordt het *Minimum moet overeenkomen* functionaliteit en gedeeltelijk zoeken naar [!DNL Elasticsearch] motor. Hiermee lost u problemen op met afbreekstreepjes in zoekopdrachten.
* **MDVA-30102** (*voor Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Hiermee wordt het probleem verholpen waarbij de cache van Redis snel toeneemt omdat de lay-outcaches geen TTL hebben.
* **MDVA-30599** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Hiermee wordt het probleem verholpen waarbij gastcitaten die met API zijn gemaakt, onjuist zijn gemarkeerd als aanhalingstekens voor aangemelde klanten.
* **MDVA-29446** (*voor Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Hiermee wordt het probleem opgelost waarbij de prijs van de niet-toepasselijke verzendmethode tijdens het afrekenen als nul wordt weergegeven.
* **MDVA-30357** (*voor Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Het probleem wordt verholpen met onjuiste afbeeldings-URL&#39;s die worden gemaakt bij het genereren van een sitemap door uitsnijden.
* **MDVA-30565** (*voor Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Hiermee wordt het probleem opgelost waarbij *Geen dergelijke entiteit met kartide = 0* de fout wordt getoond voor gastklant op winkelkassabon als het blijvende winkelwagentje wordt toegelaten.
* **MDVA-29787** (*voor Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Hiermee wordt het probleem opgelost waarbij de doelregel voor verwante producten niet werkt wanneer *is een van* De voorwaarde wordt gebruikt om producten te bepalen die moeten worden getoond.
* **MDVA-30977** (*voor Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij willekeurige producten uit categorieën ontbreken na herindexering.
* **MDVA-28202** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Hiermee wordt het probleem verholpen waarbij Gelaagde navigatie configureerbare producten niet correct filtert wanneer MSI wordt gebruikt.
* **MDVA-28300** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem opgelost waarbij de GQL-aanvraag niet de prijswijzigingen uit de prijsregels voor catalogi weerspiegelt.
* **MDVA-31006** (*voor Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Hiermee wordt het probleem verholpen waarbij dubbele bestellingen worden weergegeven nadat een bestelling is geplaatst met [!DNL Paypal Express] betaling.

## v1.0.5 {#v1-0-5}

* **MDVA-30841** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Het probleem wordt verholpen met gelaagde navigatie, waarbij de *Nee* waarde voor productkenmerken van het booleaanse type is niet opgenomen in gelaagde navigatie als [!DNL Elasticsearch] is gebruikt als zoekprogramma.
* **MDVA-28191** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij geen betalingsmethoden worden geladen tijdens het maken van bestellingen via de beheerder.
* **MDVA-29959** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 met B2B-extensie*) - Het probleem waarbij een gebruiker met beperkte beheerdersrechten *Bedrijven* rechten mogen bedrijfsaccount niet verwijderen.
* **MDVA-30265** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij de link voor het volgen van verzending stopt met werken na het maken van de factuur.
* **MDVA-28409** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Hiermee wordt het probleem opgelost waarbij de `sales_clean_quotes` snijtaak mislukt met *onvoldoende geheugen* fout wanneer het aantal verlopen aanhalingstekens in de database enorm is.
* **MDVA-30593** (*voor Adobe Commerce >=2.3.0 &lt;2.3.4*) - Hiermee wordt het probleem opgelost waarbij de prijsopgaven die zijn verlopen volgens de instelling voor de levensduur van het citaat, niet worden opgeschoond.
* **MDVA-30107** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij de winkelswitch niet naar behoren functioneert als verschillende basis-URL&#39;s worden gebruikt voor de weergave van de winkel.
* **MDVA-28763** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - Hiermee wordt het probleem verholpen waarbij de productafbeelding wordt gedupliceerd nadat de productinformatie met behulp van de REST API meermaals is bijgewerkt.
* **MDVA-30284** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij de zoekindex voor catalogi mislukt als gevolg van het volgende: *[!DNL Elasticsearch]fout: de limiet van het totale aantal velden in de index is overschreden.*
* **MDVA-29042** (*voor Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 met B2B-extensie*) - Hiermee wordt het probleem verholpen waarbij catalogusmachtigingen zijn gewijzigd in *Toestaan* automatisch nadat een nieuw product aan de gedeelde catalogus is toegevoegd.
* **MDVA-30428** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij klanten een product niet aan de verlanglijst kunnen toevoegen als dit product aan een aangepaste inventarisbron is toegewezen.
* **MDVA-28661** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2 met B2B-extensie*) - Hiermee wordt het probleem verholpen waarbij een fout wordt gegenereerd in de accountsectie voor bedrijfsgebruikers nadat bedrijfsbeheer is gewijzigd.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*voor Adobe Commerce 2.3.1 - 2.3.4-p2*) - Hiermee wordt het probleem verholpen waarbij snijtaken mislukken als de databasenaam te lang is, waardoor de categorieën niet op de voorgrond worden bijgewerkt.
* **MDVA-30106** (*voor Adobe Commerce ^2.3.0*) - Hiermee wordt een probleem verholpen waarbij tijdens het afrekenen geen betalingen worden geladen *Kan eigenschap &#39;length&#39; van null niet lezen* fout in JS console.
* **MDVA-28656** (*voor Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost dat als een bestelling zonder vereiste betalingsinformatie is geplaatst (bijvoorbeeld met korting van 100%) en er een factuur voor de bestelling is gemaakt, de status van de bestelling verandert in *Gesloten* in plaats van Voltooid.
* **MDVA-30209** (*voor Adobe Commerce 2.3.0 - 2.3.3-p1*) - Hiermee wordt het probleem opgelost waarbij de klantengroep is gewijzigd in een standaardgroep als de klant zijn accountgegevens heeft bijgewerkt.
* **MDVA-30123** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij labels voor kenmerkopties niet correct worden vertaald voor GraphQL-query&#39;s.
* **MDVA-2996** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij de categoriepagina na het inschakelen van de categorietoestemming niet in de cache van volledige pagina wordt geplaatst.
* **MDVA-30164** (*voor Adobe Commerce >=2.3.1 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij klantenrecords niet uit het raster Klanten kunnen worden geëxporteerd als er aangepaste klantkenmerken zijn.
* **MDVA-30444** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij geen bevestigingsbericht wordt verzonden voor bestellingen die zijn geplaatst met GraphQL.
* **MDVA-30490** (*voor Adobe Commerce 2.3.4 - 2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij een productvergelijking de pagina met 500 fouten genereert als een van de producten een lege korte beschrijving heeft.
* **MDVA-30232** (*voor Adobe Commerce >=2.3.1 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij het niet mogelijk is de bestelling opnieuw te bestellen als de oorspronkelijke bestelling een cadeaukaart bevat.
* **MDVA-29965** (*voor Adobe Commerce >=2.3.3 &lt;2.4.0*) - Hiermee wordt het probleem opgelost waarbij klanten een fout met betrekking tot Ongeldige formuliersleutel krijgen wanneer ze een product aan het winkelwagentje toevoegen.
* **MDVA-30008** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Het B2B-probleem is verholpen waarbij het niet mogelijk is via de Admin API orders te plaatsen voor een product dat zich in een openbare catalogus bevindt.
* **MDVA-22469** (*voor Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Hiermee wordt het probleem verholpen waarbij Page Builder na de upgrade naar Adobe Commerce 2.3.3 niet werkt in het deelvenster Beheer en sommige JS- en CSS-bestanden niet worden geladen.
* **MC-35984** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - Oplossing van de kwestie waar de handelaren niet met om het even welke paginaelementen op de pagina van Terugkeren konden interactie aangaan nadat het creëren van een verschepend etiket voor een Vergunning van de Terugkeer Merchandise (RMA).

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*voor Adobe Commerce 2.3.0 - 2.3.4*) - Het probleem verholpen met [!DNL PayPal Payflow Pro] betalingsmethode en cookies behandelen als `SameSite=Lax` standaard wordt in de Chrome 80-browser en API-respons omgeleid naar de aanmeldingspagina van de klant.
* **MDVA-26694** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - Het probleem wordt verholpen met product- en cataloguscaches die dagelijks verlopen, maar volgens planning anders verlopen.
* **MDVA-27825** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1*) - Het probleem waarbij het exporteren van grote hoeveelheden gegevens is mislukt als gevolg van een geheugenlek.
* **MDVA-29085** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Hiermee wordt het B2B-probleem verholpen waarbij geen vereiste e-mailberichten van nieuwe bedrijven worden verzonden als een bedrijf door de API wordt gemaakt.
* **MDVA-29344** (*voor Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Hiermee wordt het probleem verholpen waarbij de Page Builder vastloopt nadat tekst van een koptekstelement naar een tekstelement is gekopieerd.
* **MDVA-29835** (*voor Adobe Commerce >2.3.1 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij in plaats van één kaartopdracht twee codes bevatte.
* **MDVA-30052** (*voor Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Het probleem is verholpen waarbij particuliere inhoud (lokale opslag) niet correct is ingevuld, wat tot prestatieproblemen heeft geleid.
* **MDVA-30131** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - Het probleem wordt verholpen met gelaagde navigatie, waarbij de *Nee* waarde voor productkenmerken van het booleaanse type is niet opgenomen in gelaagde navigatie als [!DNL Elasticsearch] is gebruikt als zoekprogramma.
* **MDVA-35514** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - Het probleem is opgelost door een verzendlabel te maken en geordende producten toe te voegen aan een pakket in het modale venster Pakketten maken.

