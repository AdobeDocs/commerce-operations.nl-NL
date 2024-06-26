---
title: Opmerkingen bij de release
description: Meer informatie over de patches die beschikbaar zijn voor Adobe Commerce en de problemen die ze oplossen.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '20485'
ht-degree: 0%

---

# Opmerkingen bij de release

De [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) levert afzonderlijke patches die door de Adobe en de Magento Open Source gemeenschap zijn ontwikkeld. Hiermee kunt u algemene informatie over alle afzonderlijke patches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce, toepassen, herstellen en weergeven. U kunt patches toepassen op Adobe Commerce- en Magento Open Source-projecten, ongeacht wie de patch heeft ontwikkeld. U kunt bijvoorbeeld een patch toepassen die door de gemeenschap is ontwikkeld op Adobe Commerce-projecten.

>[!INFO]
>
>Zie [Patches toepassen](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) voor instructies over het toepassen van patches op uw Adobe Commerce-projecten. Zie [[!DNL Quality Patches Tool]: Zoeken naar patches](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de Software Update Guide om een volledige lijst met vrijgegeven patches te bekijken.

>[!INFO]
>
>Voor informatie over [!DNL quality patches] die door de Gemeenschap voor Magento Open Source zijn opgericht, [releaseopmerkingen](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de `mergeCart` mutatie mislukt met een &quot;*Interne serverfout*&quot; in de [!DNL GraphQL] reactie bij het samenvoegen van bron- en doelwinkelwagentjes die dezelfde bundelitems hebben.
* **ACSD-56546** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij configureerbare en bundelproducten worden weergegeven als **Uit voorraad** in de winkel **weergave buiten productconfiguratie** is *Uitgeschakeld*.
* **ACSD-56635** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de geïmporteerde klant met hetzelfde e-mailadres wordt gedupliceerd wanneer een importbewerking wordt gebruikt met **account delen** instellen op *Algemeen*.
* **ACSD-56741** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het foutbericht &quot;*Arrayverschuiving benaderen bij waarde van type null*&quot; die wordt weergegeven tijdens `setup:upgrade` wanneer de database een aangepaste [!DNL MySQL] trigger die geen verband houdt met het indexeringsmechanisme en [!DNL MView].
* **ACSD-57315** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt de kwestie opgelost wanneer een nieuwe transactie wordt aangemaakt in [!DNL PayPal Payflow Pro] telkens als [!UICONTROL Fetch] op de knop wordt geklikt op de knop **[!UICONTROL View transaction]** in het beheerprogramma.
* **ACSD-57337** (voor Adobe Commerce >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij een beheerder met toegangsbeperkingen voor specifieke websites bedrijven kan zien van alle websites in de **[!UICONTROL Companies]** raster.
* **ACSD-57394** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem van onjuiste productsortering door meerdere sorteervelden opgelost in [!DNL GraphQL].
* **ACSD-57565** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de **[!UICONTROL Order]** op het dashboard worden onjuiste volgordegegevens weergegeven totdat de tijdsperiode is bijgewerkt. Op het dashboard worden nu de juiste volgordestatistieken weergegeven bij de eerste keer laden.
* **ACSD-57854** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen wanneer het product [!DNL GraphQL] aanvragen hebben uitgeschakelde categorieën in de categorieconcentraties geretourneerd.
* **ACSD-58008** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij bij het bijwerken van een geplande update de vorige versie van een gefaseerd item werd verwijderd als er geen einddatum was opgegeven.
* Bijgewerkte patches: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij *[!UICONTROL Used]* en *[!UICONTROL Times Used]* attributen geven onjuiste waarden voor gegenereerde coupons weer wanneer deze worden gebruikt tijdens het afrekenen met meerdere adressen.
* **ACSD-56760** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een tot een specifieke website beperkte gebruiker geen nieuwe producten binnen een categorie kan sorteren of toevoegen als de webwinkel een eigen hoofdcategorie heeft.
* **ACSD-56858** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de B2B-machtigingen voor de rol van een bedrijf met beperkte bevoegdheden onjuist worden weergegeven voor een beheerder.
* **ACSD-57074** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de *Ja/Nee* aangepast kenmerk met `attrbute_code` beginnen met `price_` werkt niet correct met indexering, en de producten met dergelijke attributen zijn niet beschikbaar op het vooreind.
* Bijgewerkte patches: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij de categoriepagina ongeldig wordt als de voorraadhoeveelheid verandert, zelfs als het product nog in voorraad is.
* **ACSD-54656** (voor Adobe Commerce >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het onzichtbare Recaptcha tijdens het afrekenen mislukt, zodat een bestelling niet kan worden geplaatst.
* **ACSD-55100** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij GraphQL in de zoekresultaten niet meer dan 10 k producten retourneert.
* **ACSD-56621** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de bijgewerkte voornaam en achternaam niet worden weergegeven in de koptekstsectie voor begroetingen voor de gebruiker van het bedrijfsbeheer.
* **ACSD-56842** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de uitgestelde proxy&#39;s en de uitgestelde proxyfabrieken ontbreken na het uitvoeren `setup:di:compile`.
* **ACSD-57003** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de orderstatus wordt gewijzigd in *[!UICONTROL Complete]* in plaats van gewijzigd te worden in *[!UICONTROL Processing]* wanneer een bestelling gedeeltelijk wordt terugbetaald en gedeeltelijk wordt verzonden.
* Bijgewerkte patches: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een configureerbaar product uit voorraad raakt wanneer een van twee onderliggende producten wordt uitgeschakeld door een geplande update.
* **ACSD-56616** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij gebundelde producten worden weergegeven als in voorraad op de winkel wanneer hun eenvoudige producten uit voorraad zijn.
* **ACSD-56515** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij beheerders met bevoegdheden op websiteniveau geen dynamisch blok kunnen toevoegen of bewerken.
* **ACSD-56447** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem opgelost dat het toevoegen van hetzelfde product aan het winkelwagentje via parallelle REST web API-aanvragen resulteert in twee aparte items in het winkelwagentje.
* **ACSD-56415** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de prestaties van de gedeeltelijke indexering van de prijzen worden vertraagd als gevolg van een `DELETE` vraag wanneer het gegevensbestand veel gedeeltelijke prijsgegevens aan index heeft.
* **ACSD-54965** (voor Adobe Commerce >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het Visual Merchandising-raster niet de juiste voorraad weergeeft wanneer een product alleen aan aangepaste voorraad wordt toegewezen.
* **ACSD-52824** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de knoppen PayPal Express, Google Pay en Apple Pay voor zakelijke klanten worden weergegeven wanneer dergelijke betalingsmethoden in de bedrijfsinstellingen zijn uitgeschakeld.
* Bijgewerkte patches: ACSD-56193

## v1.1.4 {#v1-1-44}

* **ACSD-56790** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een gebruiker naar het beheerdersdashboard wordt omgeleid bij het sorteren van categorieproducten met behulp van het **Van voorraad naar beneden verplaatsen** en de `Invalid security or form key. Please refresh the page` wordt boven op het scherm weergegeven.
* **ACSD-56280** (voor Adobe Commerce >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het bestellen van items uit een cadeauregister tot een uitzondering leidt.
* **ACSD-56246** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij gegevens uit het aangepaste multiselect-kenmerk worden verwijderd wanneer een geplande update voor een product actief wordt.
* **ACSD-56193** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4) - Hiermee wordt het probleem verholpen waarbij de vernis/snelste cache niet wordt bijgewerkt wanneer een gepland blok wordt gebruikt in de categoriebeschrijving met behulp van Page Builder.
* **ACSD-56158** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de vraag &quot;winkelwagentje&quot; de totale belastingwaarde voor elke belastingregel retourneert.
* **ACSD-56023** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de widgetinhoud niet op de CMS-pagina wordt bijgewerkt wanneer de cache wordt ingeschakeld.
* **ACSD-55427** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de gebruiker van de beheerder de toewijzing van een product uit een gedeelde catalogus niet ongedaan kan maken via de productpagina in de beheerdersinterface.
* **ACSD-55352** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij na het maken van een gedeeltelijke creditnota met bonuspunten van de klant de status van de order verandert in Gesloten en de opties voor creditnota verdwijnen van de pagina Admin-order.
* **ACSD-55231** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - Hiermee kunt u het probleem verhelpen dat u geen producten aan een winkelwagentje kunt toevoegen met de functie voor snelle bestelling.
* **ACSD-54283** (voor Adobe Commerce >=2.4.3 &lt;2.4.4) - Hiermee wordt het probleem opgelost waarbij Producten/categorieën die niet zijn toegewezen aan de gedeelde catalogus voor de standaardcatalogus (algemene groep), nog steeds worden opgenomen in de XML-itemap.
* Bijgewerkte patches: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de URL van de canonieke categorie niet wordt bijgewerkt nadat de categorie-URL is gewijzigd.
* **ACSD-53636** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5) - Hiermee wordt het probleem opgelost waarbij de normale prijs niet wordt weergegeven op pagina&#39;s met productlijsten voor configureerbare producten die onderliggende producten met speciale prijzen hebben.
* **ACSD-54885** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen met het meervoudige adresafhandeling wanneer de beheerder de optie *Aanmelden als klant* functionaliteit.
* **ACSD-55610** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een gedeeltelijk geannuleerde order een onjuist kortingsbedrag heeft.
* **ACSD-55334** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee corrigeert u vertalingen voor labels via vertaalwoordenboeken in GraphQL-reactie.
* **ACSD-54739** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de status van de productvoorraad niet wordt toegepast voor gerelateerde productregels.
* **ACSD-53925** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de beheerder CMS-blok niet kan opslaan met productcarrousel als `catalog_product_price` afmetingen-mode is ingesteld op *website*.
* **ACSD-52714** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het datumfilter niet werkt in het beheerraster wanneer de datumnotatie is ingesteld op *Y-m-d*.
* **ACSD-55055** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Verbetert de prestaties van het laden van productkenmerken in de regels voor de winkelwagentje.
* **ACSD-53790** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij via de REST API meerdere RMA&#39;s voor één product kunnen worden gemaakt.
* **ACSD-56090** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5) - Hiermee wordt het probleem verholpen waarbij het GraphQL-verzoek reageert met de gegevens van alle winkels in plaats van met de specifiek gevraagde opslaggegevens.
* **ACSD-54983** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het niet mogelijk is om de bedrijfgebruiker UID met GraphQL-aanvraag te verkrijgen als de gebruikersstatus is ingesteld op *[!UICONTROL Inactive]*.
* **ACSD-53309** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt de kwestie opgelost waarbij de belasting niet volledig wordt toegepast in de *[!UICONTROL Regular Price]* als de aanpasbare optie is geselecteerd.
* **ACSD-55305** (voor Adobe Commerce >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de *[!UICONTROL Edit Company User]* popup **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** pagina loopt vast met een lader op het scherm.
* Bijgewerkte patches: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij *[!UICONTROL Recently Viewed]* De productgegevens worden niet correct bijgewerkt in de winkelweergave.
* **ACSD-54626** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - Hiermee kunt u het probleem verhelpen waarbij u geen nieuwe regel voor inkooporders kunt maken (`createPurchaseOrderApprovalRule`) met de `NUMBER_OF_SKUS` kenmerk via [!DNL GraphQL].
* **ACSD-53845** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het [!DNL MySQL] probleem met time-out van verbinding wanneer `consumer max_messages` = 0.
* **ACSD-54890** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij `aggregate_sales_report_bestsellers_data` oorzaken [!DNL MySQL] fouten als gevolg van `/tmp` schijf heeft onvoldoende ruimte.
* **ACSD-55112** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de *[!UICONTROL Submit review]* er kan meerdere keren op de knop worden geklikt zonder [!DNL Google reCAPTCHA v3] validatie.
* **ACSD-54264** (voor Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij het foutbericht verschijnt *&quot;U kunt het gewenste kenmerk niet bijwerken. Rij-id: store_id&quot;* verschijnt wanneer een klant probeert uit te checken met een verhandelbaar aanhalingsteken in een andere winkelweergave.
* **ACSD-54418** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt de kwestie opgelost waarbij een vaste korting onjuist wordt toegepast op elk onderliggend product van de dynamisch geprijsde bundel.
* **ACSD-55238** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Oplossingen waarmee het lege product wordt opgeslagen *[!UICONTROL Meta Description]*.
* **ACSD-54966** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt de emissie gecorrigeerd waarbij een couponcode met een beperkt gebruik per klant niet opnieuw kan worden gebruikt als de vorige bestelling is mislukt.
* **ACSD-54060** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een beperkte beheerder een product niet kan opslaan als het een onderliggend product is van een ander product dat is toegewezen aan een ander bereik.
* **ACSD-48910** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Probleem verholpen waarbij een aan meerdere bronnen toegewezen bundelproduct uit voorraad komt nadat een bestelling is gefactureerd en verzonden, zelfs als het nog steeds een hoeveelheid van niet-nul heeft.
* **ACSD-55381** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - Oplossing voor een interne serverfout bij het opvragen van gegevens `configurable_product_option_uid` en `configurable_product_option_value_uid` velden van een [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL].
* **ACSD-55628** (voor Adobe Commerce >=2.4.4-p2 &lt; 2.4.5) || >=2.4.5-p1 &lt; 2.4.6) - Hiermee wordt het uploaden van een bestand naar het bedrijfsregistratieformulier en het vervangen van een bestand voor een klantkenmerk in de winkel opgelost.
* Bijgewerkte patches: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen dat optreedt in het winkelwagentje wanneer een product uit de gedeelde catalogus wordt verwijderd nadat het al aan het winkelwagentje is toegevoegd.
* **ACSD-53722** (voor Adobe Commerce >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de prijs van de gebundelde productopties verandert in $0 wanneer geplande updates voor verschillende bereiken actief worden.
* **ACSD-53643** (voor Adobe Commerce >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het totaal van de bestelling onjuist is bij het plaatsen van een kooporder met een uitgeschakeld of een out-of-stock product. Het probleem is opgelost door het *[!UICONTROL Place Order]* voor dergelijke inkooporders.
* **ACSD-54067** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een productvideo niet op een mobiel apparaat wordt afgespeeld.
* **ACSD-55414** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - verbetert prestaties wanneer MariaDB probeert EAV entity_id van koord aan geheel te werpen.
* **ACSD-51819** (voor Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - Hiermee wordt het probleem opgelost waarbij meerdere bestellingen met dezelfde aanhalings-id kunnen worden geplaatst.
* **ACSD-53118** (voor Adobe Commerce >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de *[!UICONTROL Cart Price Rule]* wordt toegepast met behulp van couponcode terwijl het product een leeg kenmerk heeft.
* **ACSD-54324** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het GraphQL request_lists geen rekening houdt met pagineringsinstellingen en alle resultaten retourneert.
* Bijgewerkte patches: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (voor Adobe Commerce >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het niet mogelijk is een B2B-offerte te verwerken die is ingediend voor een product met Meerdere toegewezen bronnen.
* **ACSD-54040** (voor Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij de *[!UICONTROL Created]* veld is leeg in de volgorde waarin de B2B-modules zijn ingeschakeld.
* **ACSD-54319** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij de prijs van het product nul toont in het dialoogvenster *[!UICONTROL Product in Cart]* verslag.
* **ACSD-53378** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - verbetert de laadtijd van de afhandelingspagina voor klanten die grote adresboeken hebben.
* **ACSD-52657** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de minicart niet wordt bijgewerkt in de secundaire storeview, die een subdomein gebruikt.
* **ACSD-53414** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een gebruiker met beperkte beheerdersrechten CMS-pagina&#39;s buiten het bereik van machtigingen kan zien.
* **ACSD-54472** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij klanten van een afgewezen onderneming nog steeds kunnen verifiëren en klanten van een geblokkeerd bedrijf en een afgewezen bedrijf nog steeds orders kunnen plaatsen. De patch voegt extra validatie toe voor GraphQL-eindpunten.
* **ACSD-52801** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee voegt u de optie toe om een gedeeltelijke overeenkomst uit te voeren bij het zoeken naar producten in GraphQL.
* **ACSD-55004** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de validator vastloopt tijdens het uploaden van een importbestand dat groter is dan de waarde die is geconfigureerd in `php.ini`.
* **ACSD-54989** (voor Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij een bedrijfsbeheerder geen order kan plaatsen als *[!UICONTROL Enable Purchase Orders]* is ingesteld op *[!UICONTROL Yes]* en *[!UICONTROL Purchase Order]* is ingesteld op *[!UICONTROL No]*.
* **ACSD-54007** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt de fout gecorrigeerd *&quot;Niet-gedefinieerde arraysleutel &quot;_scope&quot;* bij het importeren van klantgegevens.
* **ACSD-55031** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Hiermee wordt het *Tekst &quot;gemengd&quot; kan niet ongeldig worden gemaakt* fout tijdens compilatie.
* **ACSD-54961** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een gebruiker met beperkte beheerdersrechten geen massa kan bijwerken *Productbeoordeling* status.
* **ACSD-55256** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij alleen de eerste afbeelding correct wordt weergegeven met de schuifregelaar voor de afbeelding.
* Bijgewerkte patches: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (voor Adobe Commerce >=2.4.0 &lt;2.4.7) - Hiermee wordt de kwestie opgelost waarbij de geschiedenis van de beloningspunten na het verlopen van de beloningspunten onjuist wordt berekend.
* **ACSD-53583** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Verbetert de gedeeltelijke herindexprestaties voor *Categorieproducten* en *Productcategorieën* indexeerders.
* **ACSD-54026** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - Hiermee wordt een onjuist foutbericht voor een `updateCompanyRole` GraphQL-verzoek voor een niet-gemachtigde gebruiker.
* **ACSD-54106** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5) - Hiermee wordt het probleem opgelost waarbij het sorteren op naam van categorieproducten voor tekens met accent in het Turks onjuist is.
* **ACSD-52219** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij opgeslagen filters in beheerrasters niet werken zoals u had verwacht wanneer vaak wordt geschakeld tussen bladwijzerweergaven.
* **ACSD-54342** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt een onjuist foutbericht gecorrigeerd *Fout in gegevensstructuur: waarden zijn gemengd* bij het importeren van een CSV-bestand zonder geldige gegevens.
* **ACSD-54660** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Een nieuw invoerkenmerk toegevoegd *sorteren* om klantbestellingen in GraphQL te sorteren op `sort_field` en `sort_direction`.
* **ACSD-54776** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen als dit niet is ingeschakeld *[!UICONTROL Use Default Value]* en niet-standaardwaarden voor productvelden worden niet opgeslagen voor de tweede website-, winkel- en winkelweergave.
* **ACSD-53998** (voor Adobe Commerce en Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij a **[!UICONTROL Dynamic Block]** op basis van een **[!UICONTROL Customer Segment]** werkt niet correct na het afmelden van een klantenrekening.
* **ACSD-53204** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Oplossingen *Het product kan niet worden opgeslagen.* fout bij het gelijktijdig indienen van aanvragen om afbeeldingen aan de productgalerie toe te voegen met de opdracht `rest/V1/products/<sku>/media` eindpunt.
* **ACSD-47657** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Een caching mechanisme toegevoegd voor de referenties van AWS. Een geloofsbrieven leverancier gebruikt nu het geheime voorgeheugen van het Magento aan geheim voorgeheugengeloofsbrieven die van AWS voor configuratie EC2 worden teruggewonnen.
* Bijgewerkte patches: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4) - Hiermee wordt het probleem verholpen waarbij producten die zijn toegewezen aan een gedeelde catalogus niet in de winkel worden weergegeven wanneer een gedeeltelijke index wordt uitgevoerd.
* **ACSD-54018** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - Hiermee worden de prestatieproblemen opgelost met de [!UICONTROL Product List] widget die een niet-globaal kenmerk in de widgetvoorwaarde gebruikt.
* **ACSD-54111** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij de miniatuurafbeeldingen van het product niet worden weergegeven op de winkel wanneer de hoogte-breedteverhouding van de watermerkafbeelding niet overeenkomt met de productafbeelding.
* **ACSD-47669** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - Oplossingen *Schending van integriteitsbeperking: 1452 Kan geen onderliggende rij toevoegen of bijwerken: een beperking in een externe sleutel mislukt* fout bij het importeren van CSV-producten.
* **ACSD-53347** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de prijsindexer te veel tijd nodig heeft om uit te voeren.
* **ACSD-52287** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen met een onjuiste orderstatus in het raster van de gearchiveerde volgorde als asynchrone rasterindexering is ingeschakeld.
* **ACSD-52929** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost het probleem met overtollige verzoeken op om standaardbronpunten opnieuw te indexeren wanneer de inventarisindexeerder op async wijze wordt gevormd.
* **ACSD-53824** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij `UpdateMultiselectAttributesBackendTypes` de flard van migratiegegevens overschrijdt de grens van de gegevensbestandtransactie tijdens `setup:upgrade`.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij caches en indexen worden vernieuwd, zelfs als er geen updates worden uitgevoerd naar `Inventory_source` items door REST API.
* **ACSD-51884** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het cachepad voor de productafbeelding onjuist wordt nadat de opdracht voor vergroten/verkleinen is uitgevoerd.
* **ACSD-53628** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij in het CSV-rapport onjuiste speciale tekens worden weergegeven.
* **ACSD-53148** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem opgelost dat twee parallelle verzoeken in GraphQL om hetzelfde configureerbare product aan het winkelwagentje toe te voegen, resulteerden in twee afzonderlijke artikelen op het winkelwagentje met hetzelfde product-SKU.
* **ACSD-52606** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij het foutbericht *Uw bestelling kan niet worden opgehaald* wordt weergegeven wanneer de gebruiker klikt **[!UICONTROL Notify Order is Ready for Pickup]**.
* **ACSD-51574** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de afbeelding niet op de voorzijde wordt bijgewerkt nadat deze is vervangen door een andere afbeelding met dezelfde naam.
* **ACSD-53728** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij het voltooien van de EAV-indexeerfunctie van het product langer duurt.
* **ACSD-53979** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het JS-probleem op de startpagina opgelost als het welkomstbericht één enkel aanhalingsteken bevat.
* **ACSD-52085** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij een configureerbaar product met een speciale prijs niet zichtbaar is in de carrousel van het product.
* **ACSD-53795** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen met een ongeldig gegevenstype in `indexer_update_all_views` snijtaak.
* **ACSD-52143** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij aangepaste opties worden verwijderd na het importeren van het product.
* **ACSD-53750** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het *Gebroken pijp of gesloten verbinding* fout tijdens multi-threaded `catalog_product_price` redex.
* **ACSD-49843** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de koppeling bij het downloaden van het product niet beschikbaar is nadat het geordende item automatisch is gefactureerd via een online betalingsmethode met de **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** instelling ingeschakeld.
* **ACSD-47054** (voor Adobe Commerce >=2.4.2 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij de voorvertoning van de herindex voor alle winkels opnieuw wordt gecompileerd, wat tot vertraging leidt.
* Nieuwe versies toegevoegd voor ACSD-46541, ACSD-47079.
* ACSD-49970-v3 vervangen door ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt; 2.4.6) - Hiermee wordt het probleem verholpen waarbij de index van de inventaris alle caches in de modus Update on Schedule wist.
* **ACSD-50887** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de eigenschap van het productkenmerk *[!UICONTROL Use in Search Results Layered Navigation]* kan worden ingesteld op *Ja* zonder *[!UICONTROL Use in search]* optie ingesteld op *Ja*.
* **ACSD-51846** (voor Adobe Commerce en Magento Open Source >=2.4.3-p2 &lt;2.4.6) - Hiermee wordt het *Interne fout* probleem dat zich voordoet omdat niet alle niveaus van REST API-payload zijn gevalideerd.
* **ACSD-52906** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het cookie X-Magento-Vary onjuist is ingesteld voor aangemelde klanten die tot hetzelfde klantensegment behoren, waardoor sommige pagina&#39;s in het cachegeheugen worden geplaatst.
* **ACSD-52736** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij een *Regel voor winkelprijs* die eisen voor configureerbare producthoeveelheid omvat, werkt niet zoals verwacht.
* **ACSD-47875** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij gebruikers van de beheerder geen product uit de beheerdersruimte aan een winkelwagentje kunnen toevoegen voor een bepaald weergavebereik met voorraadbeheer.
* **ACSD-53176** (voor Adobe Commerce >=2.3.7 &lt;2.4.5) - Hiermee wordt het probleem opgelost waarbij *Regel voor verwante producten* with *is een van* voorwaarde komt niet overeen met producten.
* **ACSD-51666** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt de fout gecorrigeerd *De sessie is verlopen. Meld u opnieuw aan.* dat gebeurt nadat een klant probeert aan login.
* Nieuwe versies toegevoegd voor MDVA-39305-v2.
* Bijgewerkte eisen voor ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het standaardverzendadres bij de stap voor afhandeling automatisch wordt ingevuld met een eerder geselecteerd ophaaladres in de winkel.
* **ACSD-52041** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij het foutbericht: *[FOUT] [!DNL Page Builder] renderde gedurende 5 seconden zonder vergrendelingen vrij te geven.* wordt weergegeven in de Chrome-browser wanneer inhoud wordt opgeslagen die is bewerkt met [!DNL Page Builder].
* **ACSD-52095** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij de `manage_stock` waarde is onjuist ingesteld op 0 in het CSV-bestand na exporteren van product.
* **ACSD-51358** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het verwijderen van een geplande update zonder einddatum ertoe leidt dat andere geplande updates voor dezelfde entiteit worden verwijderd.
* **ACSD-48070** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij het bewerken van een geplande update een uitzondering activeert.
* **ACSD-51890** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de [!UICONTROL Submit review] er kan meerdere keren op de knop worden geklikt zonder [!DNL Google reCAPTCHA] v3-validatie.
* **ACSD-51984** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen als dit niet is ingeschakeld *[!UICONTROL Use Default Value]* en *[!UICONTROL non-default product field]* De waarden worden niet opgeslagen voor de tweede website-, opslag- en opslagweergave.
* **ACSD-52398** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt de fout gecorrigeerd *De gevraagde hoeveelheid is niet beschikbaar* dit gebeurt wanneer wordt geprobeerd de hoeveelheid van een gebundeld product in het winkelwagentje bij te werken.
* **ACSD-52786** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij een catalogusregelvoorwaarde *SKU is* van toepassing op alle producten die beginnen met de gegeven SKU.
* **ACSD-52921** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een interne fout optreedt wanneer GraphQL om cartdetails vraagt wanneer er een product in het winkelwagentje zit dat kan worden geconfigureerd.
* **ACSD-51683** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een aanpasbare optie niet aan het winkelwagentje kan worden toegevoegd met GraphQL.
* **ACSD-52133** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een klantenaccount niet kan worden opgeslagen na een upgrade.
* **ACSD-52202** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de verkoopbare hoeveelheid van de standaardvoorraad ten onrechte verandert in 0 wanneer een niet-standaardvoorraad wordt gewijzigd in 0 qty als aan de order wordt voldaan.
* **ACSD-51265** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Het probleem verhelpen met `catalog_product_price` de prestaties te verbeteren wanneer het systeem te veel gebundelde producten bevat.
* **ACSD-52831** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij klanten geen verhandelbare prijsbestellingen kunnen plaatsen wanneer [!DNL Google reCAPTCHA v3 Invisible] is ingeschakeld.
* **ACSD-51845** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij volgende producten met prijzen op lagen en verschillende kenmerksets niet via asynchrone bulksgewijze REST API kunnen worden bijgewerkt.
* **ACSD-52815** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de invoer voor het veld voor de hoeveelheid van een niet-standaardbron slechts maximaal zes cijfers ondersteunt, in tegenstelling tot 8 voor een standaardvoorraad.
* **ACSD-51149** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij Scheduled ImportExport met ingeschakelde catalogusmachtigingen indexen ongeldig maakt en vervolgens in het cachegeheugen wordt gespoeld met een uitsnede.
* **ACSD-50815** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Hiermee wordt de kwestie gecorrigeerd waarbij decimale hoeveelheden voor een eenvoudig product niet kunnen worden gebruikt voor een nieuwe optie voor gebundeld product.
* Bijgewerkte versies voor ACSD-47803.
* Bijgewerkte titel voor ACSD-51892.
* ACSD-51379 bijgewerkt.
* ACSD-49970-v2 bijgewerkt.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een gebruiker met beheerdersrechten niet correct wordt omgeleid nadat een winkelweergave is geselecteerd bij het maken van een nieuwe bestelling in Admin.
* **ACSD-50813** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem opgelost dat Admin niet in staat was gebundelde producten met een schuine streep in de SKU toe te voegen met de [!UICONTROL Add Products by SKU] functionaliteit voor de beheervolgorde.
* **ACSD-51630** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het downloaden van beheerpagina&#39;s wordt vertraagd door een grote hoeveelheid systeemberichten.
* **ACSD-51853** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij geen gekopieerde tekststijlen worden toegepast bij gebruik van de optie [!UICONTROL Page Builder].
* **ACSD-52160** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij het resultaat van de productvalidatie aan de hand van de regel van de kartprijs niet correct is beoordeeld op basis van de regel &quot;Als een artikel in de winkelwagentje is GEVONDEN/NIET is GEVONDEN met Al/een van deze voorwaarden true&quot;.
* **ACSD-51636** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de bedrijfsbeheerder geen nieuwe gebruikers kan toevoegen uit de sectie voor de klantenaccount, ondanks dat hij over alle benodigde rollen en machtigingen beschikt.
* **ACSD-51739** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een fout wordt geretourneerd wanneer de fout `structure_id` wordt gevraagd in een CompanyTeam GraphQL- verzoek.
* **ACSD-51857** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de trage prestaties van het `aggregate_sales_report_bestsellers_data` cron report on large sales_order en `sales_order_item` databasetabellen zijn het gevolg van de manier waarop de hoofdgegevensquery is geschreven.
* **ACSD-48448** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij zich een probleem voordoet met betrekking tot een zeldzame omstandigheid tijdens annuleringen van bestellingen, wat leidt tot een dubbele vermelding in het dialoogvenster `inventory_reservation` tabel.
* **ACSD-52689** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij afbeeldingen niet kunnen worden geüpload naar Amazon S3-opslag met behulp van REST API.
* **B2B-2674** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - voeg caching vermogen aan de 1customAttributeMetadata1 GraphQL vraag toe.
* Nieuwe versies toegevoegd voor ACSD-44938.
* Toegevoegde eisen voor ACSD-46988.

## v1.1.3 {#v1-1-33}

* **ACSD-50478** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5) - bevestigt het gegevensbestand terugschroeven van prijzen bevel voor een geval wanneer de stortplaats van DB trekkers en een *scheidingsteken* SQL-opdracht.
* **ACSD-50512** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het *Fout: de downloadbare koppeling heeft geen betrekking op het product. Controleer de koppeling en probeer het opnieuw.* fout die optreedt bij het bijwerken van de begindatum voor een downloadbare update voor productplaatsing.
* **ACSD-50949** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het prijsfilter in Geavanceerd zoeken geen goede resultaten oplevert bij gebruik langs het SKU-filter.
* **ACSD-51645** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt de gegenereerde fout gecorrigeerd wanneer een nieuwe regel voor winkelprijzen wordt opgeslagen als de extensie `Magento_OfflineShipping` is uitgeschakeld.
* **ACSD-50895** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij [!DNL Google Analytics] 3 GTM-tags worden niet geactiveerd als [!DNL Google Analytics] 4 GTM is niet geconfigureerd.
* **ACSD-51102** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een catalogusregel die op een groot aantal producten wordt toegepast, niet correct wordt geïndexeerd wanneer de regel wordt ingeschakeld door een geplande update.
* **ACSD-50368** (voor Adobe Commerce en Magento Open Source >= 2.4.3 &lt;2.4.5) - Hiermee wordt het probleem opgelost waarbij de klant `group_id` wordt genegeerd wanneer een klant wordt gemaakt via de Async REST API of de Async Bulk REST API.
* **ACSD-51497** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een klant een cataloguspagina niet kan sorteren op Aangepast kenmerk van het vervolgkeuzetype.
* **ACSD-51408** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt; 2.4.7) - Hiermee wordt het probleem verholpen waarbij de status van het orderitem onjuist is ingesteld op *[!UICONTROL Backordered]*.
* **ACSD-51735** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - Hiermee wordt het probleem verholpen waarbij de status van het orderitem onjuist is ingesteld op *[!UICONTROL Ordered]* wanneer de productvoorraad *0*.
* **ACSD-51792** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij een pagina niet de immateriële gebeurtenis heeft wanneer [!DNL Google Tag Manager] 4 is ingeschakeld.
* **ACSD-51471** (voor Adobe Commerce >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een gebruiker met beheerdersrechten geen geplande update kan opslaan voor een gebundeld product dat gebruikmaakt van een eenvoudig product met een geplande update.
* **ACSD-51700** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt de fout gecorrigeerd die optreedt wanneer wordt geschakeld naar een andere winkelweergave op een downloadbare productbewerkingspagina in de beheerder.
* **ACSD-51120** (voor Adobe Commerce >=2.3.7 &lt;2.4.3) - Hiermee wordt het probleem verholpen waarbij de GraphQL-GET cache niet wordt gewist voor CMS-pagina&#39;s die CMS-blokken bevatten die via een testupdate worden bijgewerkt.
* **ACSD-51240** (voor Adobe Commerce >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij het geüploade bestand ontbreekt als de registratie wordt uitgevoerd via het bedrijfsregistratieformulier.
* **ACSD-51907** (voor Adobe Commerce >=2.4.2 &lt;2.4.3) - Hiermee wordt het probleem verholpen waarbij een gebruiker met beperkte beheerdersrechten geen creditnota met een offlinerestitutie kan maken.
* **ACSD-52148** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4) - Hiermee wordt het probleem opgelost waarbij de [!DNL Google V3 reCAPTCHA] Aanmelden bij Admin mislukt soms.
* **ACSD-51431** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de status van een indexeerder is *werken* zelfs als er geen nieuwe ingangen in de verandering zijn.
* **ACSD-51892** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het prestatieprobleem verholpen waarbij configuratiebestanden meerdere keren worden geladen.
* Vervangen ACSD-51114.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de [!UICONTROL Page Builder's] meerdere fouten verhinderen dat beheerders een product opslaan zonder inhoudsmachtigingen.
* **ACSD-51305** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij configureerbare onderliggende producten uit de voorraad niet beschikbaar zijn in de GraphQL-reactie.
* **ACSD-50621** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij [!UICONTROL Tier Prices] voor verschillende websites in de gedeelde catalogus zijn niet zichtbaar wanneer u probeert deze te bewerken in een omgeving met meerdere websites.
* **ACSD-51041** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - verbetert de prestaties van de prijsindexer.
* **ACSD-51379** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij wijzigingen worden aangebracht in de inhoud van paginatekst via [!UICONTROL Page Builder] niet worden opgeslagen.
* **ACSD-49480** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij slechts één regel van de winkelwagenprijs op de winkelwagen wordt toegepast.
* **ACSD-51230** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt de kwestie opgelost waarbij de rekening van de cadeaukaart wordt verwijderd wanneer een gedeeltelijke terugbetaling van een eenvoudig product wordt verwerkt uit een bestelling.
* **ACSD-51238** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de inventarisbron wordt verwijderd wanneer configureerbare producten worden bijgewerkt en de prijs wordt bewerkt.
* **ACSD-50794** (voor Adobe Commerce >=2.4.1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het cadeaubericht of de informatie over het inpakken van cadeaus niet in de database worden bijgewerkt wanneer het bericht of de cadeau via GraphQL wordt verwijderd.
* **ACSD-51528** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de *x_forward_for* de kolom heeft ongeldige waarden in *sales_order* tabel.
* **ACSD-50849** (voor Adobe Commerce >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem opgelost dat het toevoegen van een nieuw product aan de categorie na het wissen van de cache resulteert in een onjuiste weergave van posities en selecties van de bestaande producten.
* **ACSD-51294** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij GTM/GA-prijs, -hoeveelheid, -belasting, -verzending en -inkomsten als een tekenreeks worden verzonden naar [!DNL Google Analytics] en GTM.
* **ACSD-51204** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij een volledig verkocht product na het maken van een creditmemo niet opnieuw in voorraad terugkeert.
* **ACSD-51291** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Hiermee wordt het probleem opgelost waarbij beperkte beheerders met toegang tot één website afbeeldingen/video&#39;s kunnen toevoegen aan het product dat aan meerdere websites is toegewezen.
* Nieuwe versies toegevoegd voor ACSD-50336.
* Vervangen patches ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij Recaptcha v2 niet opnieuw laadt na het verzenden van een mislukte betaling.
* **ACSD-50817** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - De baan van het Gewas optimaliseert `sales_clean_quotes` om sneller te werken.
* **ACSD-49392** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de status van de order verandert in een gesloten order na een gedeeltelijke terugbetaling voor een gebundeld product.
* **ACSD-51036** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - Hiermee wordt het probleem verholpen waarbij de rassenvoorwaarden tijdens gelijktijdige REST API-aanroepen resulteren in een overschrijving van de verzendstatusinformatie in het gedeelte [!UICONTROL Items Ordered] tabel.
* **ACSD-50858** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Verbetert de prestaties voor het laden van de inhoud van banners.
* Nieuwe versies toegevoegd voor MDVA-39305-v2, ACSD-45169.
* Bijgewerkte patches ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (voor Adobe Commerce en Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - Hiermee wordt het probleem verholpen waarbij e-mails met productwaarschuwingen niet worden verzonden wanneer een product weer in voorraad is of de prijs wordt gewijzigd.
* **ACSD-50367** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het exporteren van het adres van de klant niet werkt wanneer een attribuut van het klantenadres zonder waarden wordt gecreeerd dat uit meerdere categorieën bestaat.
* **ACSD-4987** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij automatisch afspelen van video niet werkt op mobiele apparaten [!DNL Safari] wanneer de video rechtstreeks aan een extern videobestand is gekoppeld en niet aan een streaming service.
* **ACSD-50165** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt de fout gecorrigeerd *Het bestand kan niet worden verwijderd. Waarschuwing!ontkoppelen: bestand of map bestaat niet* bij het leegmaken van de JS/CSS-cache uit de Admin.
* **ACSD-49737** (voor Adobe Commerce en Magento Open Source >=2.4.1-p1 &lt;2.4.7) - Hiermee wordt de emissie gecorrigeerd wanneer een coupon onjuist is gemarkeerd als gebruikt na een mislukte kaartbetaling.
* **ACSD-50814** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een beheerder geen creditnota kan maken.
* **ACSD-50116** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een gebruiker met beheerdersrechten geen URL kan maken die herschrijft voor subcategorieën niveau 3 of lager.
* **ACSD-49513** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5) - Hiermee wordt het probleem verholpen waarbij de synchronisatie van externe opslag mislukt als gevolg van bestanden van 0 byte.
* **ACSD-46683** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de verzendprijs wordt weergegeven *Nog niet berekend*.
* **ACSD-49129** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij de *[!UICONTROL content]* attribute (base64 image code) is not returned in `rest/V1/products/sku/media` API-reacties voor productmedia.
* **ACSD-50276** (voor Adobe Commerce >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij het registratieformulier van de klant niet in de winkel werkt als een kenmerk van een klant met meerdere selecties wordt gemaakt.
* **ACSD-50527** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt de fout gecorrigeerd die optreedt bij het opslaan van een pagina met een leeg dynamisch blok.
* **ACSD-49973** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - verbetert de prestaties van het ophalen van gebundelde producten via GraphQL.
* **ACSD-51114** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een willekeurig product uit grote catalogi verdwijnt wanneer asynchrone indexering is ingeschakeld. Verbetert de prestaties van asynchrone herindexering voor grote catalogi.
* **B2B-2598** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - Voeg caching mogelijkheden aan toe [!UICONTROL availableStores], [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency], en [!UICONTROL storeConfig] GraphQL query&#39;s.
* Nieuwe versies toegevoegd voor MDVA-42806, ACSD-48627, ACSD-46815.
* Bijgewerkte patches, metagegevens voor ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een e-mailbericht met de mogelijkheid om op te halen wordt verzonden door de API wanneer de bestelling niet klaar is om te worden opgehaald.
* **ACSD-4982** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij updates in het dialoogvenster [!UICONTROL Requisition List] pagina&#39;s niet worden weergegeven op de [!UICONTROL Print Requisition List].
* **ACSD-48771** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee kunt u het probleem verhelpen door het inhoudstype voor kolomblokken te upgraden vanaf een lagere pagina [!DNL Page Builder] versies.
* **ACSD-49464** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt de kwestie opgelost waarbij facturen, verzendingen en creditnota&#39;s niet uit het archief worden verplaatst wanneer orderId anders is.
* **ACSD-49773** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij het exporteren van producten mislukt wanneer AWS S3 wordt gebruikt als externe opslag.
* **ACSD-49748** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij geen uitnodigingen kunnen worden verzonden.
* **ACSD-49502** (voor Adobe Commerce >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de downloadbare koppeling niet correct wordt bijgewerkt nadat een testupdate op het downloadbare product is toegepast.
* **ACSD-49527** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de paginering niet correct wordt weergegeven in GraphQL-bedrijfsrollen.
* **ACSD-49706** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de standaardwaarde wordt opgeslagen voor een visueel staalkenmerk wanneer geen waarde is geselecteerd.
* **ACSD-49835** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de standaardwaarde van het selectievakje Gebruik niet correct wordt opgeslagen op archiefniveau voor een kenmerk met meerdere selecties.
* **ACSD-49898** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het productraster een uitzondering genereert wanneer een gebundeld product een speciale prijs heeft die hoger is dan 1000.
* **ACSD-50234** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.5) - Hiermee kunt u het probleem oplossen met de verkeerde naam van de klant in het bevestigingsbericht als u een bestelling plaatst met [!DNL PayPal].
* **ACSD-49960** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij filtering op datum niet werkt voor het orderraster van de klant.
* **ACSD-49849** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - Hiermee kunt u het probleem verhelpen waarbij de e-mail van de klant is vervangen door [!DNL PayPal] e-mail wanneer u een bestelling plaatst met [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij Prijsbepaling en structuur van gedeelde catalogus een fout veroorzaakt in Admin wanneer producten enkele of dubbele aanhalingstekens in SKU hebben.
* **ACSD-49970** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt een onjuiste afhandeling van GraphQL-fouten gecorrigeerd wanneer [!DNL New Relic] rapportage is ingeschakeld.
* **ACSD-50260** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de zoekresultaten van GraphQL-producten beperkt blijven tot 10.000 resultaten.
* **ACSD-48813** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de zoekopdracht geen relevante resultaten oplevert op basis van het zoekgewicht van de kenmerken.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.3) - Hiermee wordt het probleem verholpen waarbij een op het kenmerk Ja/Nee gebaseerde prijsregel voor catalogi geen rekening houdt met het geselecteerde bereik.
* **ACSD-47704** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt de kwestie gecorrigeerd waarbij het gebundelde product alleen de prijs van in-voorraad producten weergeeft.
* **ACSD-49370** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de *Datum en tijd* productkenmerk heeft een *FilterMatchTypeInput* type in GraphQL-schema.
* **ACSD-48807** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de Revisies van producten van de klant niet via GraphQL worden gefilterd.
* **ACSD-4943** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij het standaardbedrag in het winkelwagentje voor cadeaukaarten met een open bedrag als subtotaal wordt weergegeven.
* **ACSD-48866** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een fout optreedt bij het aanvragen van RSS-feed voor categorieën.
* **ACSD-48784** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de prijzen van het klantensegment onjuist in de cache worden opgeslagen tussen klantengroepen.
* **ACSD-48857** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een gebruiker geen wijzigingen kan opslaan na bewerking met Page Builder.
* **ACSD-49065** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij prijsaanhalingstekens niet zichtbaar zijn in de beheerder als deze alleen aan de aangepaste voorraad worden toegewezen.
* **ACSD-49179** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt de emissie gecorrigeerd waarbij in het orderrapport onjuiste bedragen worden weergegeven in geval van verschillende valuta&#39;s voor verschillende winkels.
* **ACSD-49286** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een product tweemaal aan een winkelwagentje wordt toegevoegd wanneer meerdere productwidgets op de pagina aanwezig zijn.
* **ACSD-49574** (voor Adobe Commerce >=2.4.4 &lt;2.4.7) - Hiermee voegt u functionaliteit toe ter ondersteuning van productupdates voor Cadeautjes in een winkelwagentje via GraphQL.
* Bijgewerkte patch: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (voor Adobe Commerce >=2.4.1 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij het standaardverzendadres wordt gebruikt in plaats van een nieuw adres wanneer een bestelling wordt geplaatst met behulp van een verhandelbaar aanhalingsteken.
* **ACSD-48059** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij handelaren het bestand &quot;[!UICONTROL Match product by rule]&quot; in de categorie.
* **ACSD-48216** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij [!UICONTROL AUTO_INCREMENT] van de [!UICONTROL inventory_source_item] tabelverhogingen op de [!UICONTROL UPDATE] -bewerking.
* **ACSD-47908** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Hiermee wordt de fout &quot;Er wordt een waarde kleiner dan of gelijk aan 0 verwacht&quot; bij het selecteren van de bron en hoeveelheid in de verzendstap tijdens het uitchecken.
* **ACSD-49497** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - Hiermee wordt de kwestie opgelost waarbij een bestelling na verzending nog steeds in de verwerkingsstatus verkeert en een gedeeltelijke terugbetaling wordt toegepast.
* **ACSD-48694** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de fout &quot;Ongeldige statuswijziging aangevraagd&quot; een klant belet een order te plaatsen.
* **ACSD-49013** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij e-mailbevestiging niet naar de landinstelling van de website wordt vertaald wanneer klanten met de bulkAPI worden gemaakt.
* **ACSD-48164** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een beperkte beheerder geen waarde op websiteniveau kan opslaan.
* **ACSD-48404** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4) - Hiermee wordt het probleem verholpen waarbij &quot;Categoriepaginering onthouden = Ja&quot; een fout veroorzaakt wanneer op de knop Vorige van de browser wordt gedrukt.
* **ACSD-48634** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee worden JS-fouten op een testupdatepagina gecorrigeerd wanneer &quot;[!UICONTROL Google Analytics Content Experiments]&quot; is ingeschakeld.
* **ACSD-49042** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - Hiermee wordt het probleem verholpen waarbij een product met een oneindige backorder niet vanuit de Storefront kan worden besteld.
* Bijgewerkte patches: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (voor Adobe Commerce en Magento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij meldingen voor prijsdalingen niet altijd worden verzonden vanwege caching op toepassingsniveau.
* **ACSD-48661** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt de kwestie opgelost waarbij als de kredietlimiet van het bedrijf groter is dan 999, het komma-scheidingsteken het opslaan van het bedrijf verhindert vanwege een validatiefout.
* **ACSD-48773** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de sjabloon voor het plaatsen van bonuspunten in de verkeerde winkel wordt opgehaald.
* **ACSD-48587** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij speciale HTML-tekens in de widgetwidgetregels voorkomen dat overeenkomende producten worden weergegeven.
* **ACSD-48212** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het product door het importeren aan de verkeerde bron wordt toegewezen.
* **ACSD-4798** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij bij het exporteren van producten HTML-tags uit de productbeschrijving van de paginabuilder worden bijgesneden.
* **ACSD-4836** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij de productafbeelding niet wordt weergegeven op de e-mailsjabloon Terug naar voorraad.
* **ACSD-48417** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een SQL-fout optreedt nadat een programmawijziging voor een product is gemaakt en een ander product is opgeslagen.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij de productprijsherdex niet werkt als het bundelproduct niet aan een website wordt toegewezen.
* **ACSD-48262** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij producten niet op de voorzijde zichtbaar zijn wanneer de instelling &quot;Alle producten per pagina toestaan&quot; is ingesteld op Ja.
* **ACSD-48293** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4) - Hiermee wordt het probleem opgelost waarbij de samengestelde producten uit de voorraad verdwijnen wanneer de onderliggende producten die werden verkocht naar de voorraad worden teruggestuurd.
* **ACSD-47520** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij klanten beloningspunten verliezen wanneer een creditmemo wordt gemaakt.
* **ACSD-4804** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4) - Hiermee wordt het probleem opgelost dat het toepassen van meerdere cadeaukaarten op één bestelling met meerdere verzendingen ertoe leidt dat bestellingen niet kunnen worden geplaatst.
* **ACSD 48300** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij geen return kan worden gemaakt als het configureerbare product wordt verwijderd.
* **ACSD-47910** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Oplossingen voor de afgifte van ontbrekende orders, facturen, overbrengingen en creditnota&#39;s in de respectieve entiteitsnetwerken.
* **ACSD-47292** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij gebundelde producten uit de voorraad niet beschikbaar zijn in het GraphQL-antwoord als de &quot;producten uit de voorraad&quot; op Ja is ingesteld.
* **ACSD-48234** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij in het zoekresultaat van de catalogus een onjuist aantal items in de categorie wordt weergegeven wanneer de optie &quot;show out of stock&quot; is ingeschakeld.
* **ACSD-48313** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5) - Hiermee wordt het probleem verholpen waarbij de kolom &quot;configurable_variation&quot; niet wordt geparseerd als de kenmerkwaarde een komma bevat. Hetzelfde parseringsalgoritme wordt gebruikt voor &quot;additional_attributes.
* **ACSD-48627** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het configureerbare product uit de voorraad een fout veroorzaakt bij het verzenden van een GraphQL-verzoek om kaartgegevens.
* Bijgewerkte patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij geen SEO-vriendelijke URL&#39;s worden gegenereerd voor producten die *url_key* worden genegeerd op winkelweergaveniveau.
* **ACSD-46865** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het net Verzending en creditmemo niet wordt gevuld wanneer asynchrone indexering is ingeschakeld.
* **ACSD-47004** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - Hiermee wordt het probleem opgelost dat btw niet wordt geheven op een factuuradres zonder BTW-identificatienummer.
* **ACSD-47803** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij stalen van producten die uit de voorraad kunnen worden geconfigureerd, worden weergegeven als beschikbaar.
* **ACSD-47137** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee verbetert u de laadsnelheid van de afbeeldingsgalerie wanneer de map pub/media erg groot is.
* **ACSD-46770** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee kunt u het probleem verhelpen waarbij e-mails met bestellingen voor beheerders worden verzonden, zelfs als de *E-mailorderbevestiging* is uitgeschakeld.
* **ACSD-4795** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij GraphQL de kaartkorting niet correct weergeeft.
* **ACSD-46617** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij de *Doorgaan met afhandeling* de knoop wordt grijs uit zelfs als subtotaal groter is dan gevormd *Minimumbedrag bestelling*.
* **ACSD-47079** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - Hiermee wordt het probleem verholpen waarbij de voorraadstatus van samengestelde producten (bundel, gegroepeerd en configureerbaar) niet wordt bijgewerkt wanneer de voorraadstatus van subproducten verandert via REST API POST /rest/V1/voorraad/bron-items.
* **ACSD-47336** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Oplossingen *Er is iets misgegaan.* fout bij het negeren van meldingen in Commerce Admin.
* **ACSD-47559** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het gebied Voorvertoning e-mailsjabloon niet volledig zichtbaar is.
* **ACSD-47920** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij orders via de rest-API als gastgebruiker kunnen worden geplaatst, zelfs als de *Uitchecken door gasten toestaan* is uitgeschakeld.
* Vervangen patches: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij een beheerder met beperkte toegang tot een bepaald bereik productbeoordelingen niet kan verwijderen.
* **ACSD-47107** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5) - Hiermee wordt het probleem opgelost waarbij de korting op de regel Catalogusprijs wordt toegepast op aangepaste productopties.
* **ACSD-47232** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt de emissie gecorrigeerd waarbij coupons met totaal gewicht niet kunnen worden toegepast in de Admin.
* **ACSD-46519** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij de aanvraag voor de GraphQL-categorieList een onjuist product_count voor een ankercategorie retourneert.
* **ACSD-47027** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - lost een slow updateCompanyRole GraphQL-verzoek op.
* **ACSD-4766** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij de filterfunctie niet werkt in Beheer > Systeem > Machtigingen > Gebruikersrollen > een rol > Rolgebruikersraster.
* **ACSD-47497** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het tabblad Services niet zichtbaar is in de Configuratie onder Beheer.
* Bijgewerkte patch: ACSD-47743.
* Vervangen patches: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-4744** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.3) - Hiermee wordt het _Arrayverschuiving benaderen bij waarde van type bool_ fout bij het openen van bepaalde niet bestaande categoriepaden voor bekende producten op PHP 7.4.
* **ACSD-47332** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij een fout optreedt die alleen wordt gerapporteerd bij een bewerking tussen 00:00 en 00:59 UTC.
* **ACSD-47280** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het uitschakelen van de functie voor gedeelde catalogus in een bepaald bereik niet correct werkt.
* **ACSD-47106** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij een waarde niet kan worden opgeslagen in een nieuw aangepast kenmerk op een pagina voor het maken van een bedrijf.
* Bijgewerkte patch: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij een gebruiker een fout krijgt bij het toewijzen van een groot aantal productbronnen.
* **ACSD-46856** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Verbetert de prestaties die laagprijzen bijwerken via System > Configuration > Import > Advanced Pricing.
* **ACSD-46541** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4) - Hiermee wordt het probleem verholpen waarbij een beheerder geen creditnota kan maken als een orderitem wordt verwijderd.
* **ACSD-46581** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij het geraamde belastingtotaal niet wordt bijgewerkt na selectie van een land in het winkelwagentje.
* **ACSD-46618** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij de widget voor de productlijst onjuiste prijzen in de cache weergeeft voor een aangemelde klant.
* **ACSD-46674** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - Hiermee kunt u het probleem verhelpen waarbij aangepaste opties van een afbeeldingstype als HTML worden weergegeven in e-mails van de klant.
* **ACSD-4698** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij de GraphQL &#39;currency&#39;-API-aanvraag NULL-waarden retourneert voor een aangepaste valuta.
* **ACSD-47076** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5) - Hiermee wordt het probleem opgelost waarbij Vimeo-video&#39;s niet op de winkel kunnen worden afgespeeld.
* **ACSD-45071** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4) - Hiermee wordt het probleem opgelost waarbij de standaardbron tijdens het importeren aan het product wordt toegevoegd.
* **AC-3023** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - DHL-schema bijwerken naar nieuwste versie 10.0.
* Bijgewerkte patches: MDVA-42584.
* Vervangen patches: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een gebruiker een onjuiste orderstatus krijgt wanneer het bedrag wordt terugbetaald via het winkelkrediet.
* **ACSD-46703** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij het niet mogelijk is om aangepaste opties te slepen en neer te zetten op een productbewerkingspagina.
* **ACSD-44851** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij een categorie met subcategorieën niet kan worden geopend of uitgebreid.
* **ACSD-46815** (*voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij de aanvraag voor de boomcategorie beperkt is tot 20 categorieën.
* **ACSD-45675** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6*) - Hiermee wordt het probleem opgelost waarbij voor het exporteren van het product categorienamen uit de *Standaardwinkelweergave* bereik.
* **ACSD-46869** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6*) - Hiermee wordt het probleem opgelost dat een configureerbaar product in een winkelwagentje niet via een *PUT REST API* aanvragen zonder de producthoeveelheid te wijzigen.
* **MDVA-42768-V2** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Oplossing van het probleem waarbij Configureerbaar product een normale prijs weergeeft als *0* wanneer *Weergeven uit voorraad* is *Ja*.
* Bijgewerkte patches: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Vervangen pleister: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de aanvraag voor de boomcategorie beperkt is tot 20 categorieën.
* **ACSD-45781** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij het zoekveld voor de winkel niet wordt weergegeven op mobiele apparaten.
* **ACSD-46192** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;2.4.5*) - Hiermee kunt u het probleem verhelpen door de opdracht `async/bulk/V1/configurable-products/bySku/options` eindpunt.
* **ACSD-46404** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een beheerder zich niet kan aanmelden na een upgrade naar 2.4.4.
* Bijgewerkte patches: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een GraphQL-productmutatie voor een specifieke winkel alle configureerbare varianten retourneert, inclusief varianten die niet aan de gevraagde winkel zijn toegewezen.
* **ACSD-46146** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij twee e-mails ter bevestiging van de bestelling worden verzonden nadat een bestelling van de beheerder is geplaatst.
* **ACSD-4525** (*voor Adobe Commerce >=2.4.3 &lt;2.4.6*) - Hiermee wordt een uitzondering op de pagina Rapport over lage voorraad voor een beperkte beheerder gecorrigeerd.
* **ACSD-4548** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6*) - Hiermee wordt het probleem verholpen waarbij een configureerbaar product met meerdere bronnen niet automatisch wordt teruggestuurd naar In Stock.
* **ACSD-45754** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.6*) - Hiermee wordt de emissie gecorrigeerd waarbij geen punten naar achteren worden toegevoegd nadat een coupon op de winkelwagentje is toegepast.
* **ACSD-45849** (*voor Adobe Commerce >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij videometagegevens verloren gaan nadat een gefaseerde update is toegepast.
* **ACSD-45257** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij GraphQL geen winkelkorting correct weergeeft.
* **ACSD-44938** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij `VAT_ID` kan niet worden toegepast in een GraphQL-aanvraag voor een gastgebruiker.
* Bijgewerkte patches: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.4*) - Hiermee wordt de kwestie opgelost waarbij de voorraadhoeveelheid voor een virtueel product onjuist wordt berekend na het maken van een creditnota.
* **ACSD-43887** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij onjuiste gegevens worden weergegeven op de betalingspagina voor afbetalingen wanneer Aankooporders voor bedrijven zijn ingeschakeld.
* **ACSD-45143** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de `setShippingAddressesOnCart` mutatie staat het plaatsen van numerieke gebiedscode als niet toe *regio*.
* **ACSD-44591** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.6*) - Hiermee wordt de fout gecorrigeerd die optreedt wanneer een bestelling wordt geplaatst zonder CAPTCHA-bevestiging.
* **ACSD-45520** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.6*) - Hiermee wordt het probleem opgelost waarbij staalopties niet vooraf op de pagina met productdetails zijn geselecteerd wanneer een gebruiker configureerbare producten bewerkt in het winkelwagentje.
* **ACSD-45169** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.6*) - Hiermee wordt het probleem opgelost waarbij [!DNL Visual Merchandiser] geeft niet de correcte voorraad en de prijs voor een configureerbaar product na een het opvoeren update wordt toegepast.
* **ACSD-45424** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.6*) - Hiermee wordt de kwestie opgelost waarbij na een gedeeltelijke terugbetaling een onjuiste reserveringscompensatie wordt gecreëerd (creditnota).
* **42807** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.6*) - Hiermee wordt de uitgave verholpen waarbij het aangepaste valutateken niet op de winkelvoorzijde worden weergegeven.
* Bijgewerkte patches: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **44703** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij het totaal van de bestellingen in het orderrapport onjuist wordt berekend voor de gebruiker met beperkte beheerdersrechten.
* **MDVA-44940** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt de SQL-fout verholpen die optreedt wanneer de categorie wordt opgeslagen in de beheerfunctie.
* **44562** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - Hiermee wordt het probleem opgelost waarbij de niet-standaard winkel-id voor aanhalingstekens wordt overschreven door de standaard winkel-id, ondanks het GraphQL-verzoek dat afkomstig is uit de niet-standaard winkelweergave.
* **MDVA-43167** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij de handeling voor de massa van het raster van de beheervolgorde niet van toepassing is op meerdere pagina&#39;s wanneer de beheerder alle bestellingen selecteert.
* **MDVA-4404** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - Hiermee wordt het probleem verholpen waarbij een product niet op de categoriepagina wordt weergegeven nadat het aan een nieuwe website is toegewezen.
* **42509** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een CSV niet kan worden geüpload voor een snelle bestelling, wat resulteert in een *Kan het cookie niet verzenden* fout.
* Bijgewerkte patches: MDVA-41061, MDVA-42584.
* Het voorvoegsel voor de nieuwe [!DNL Quality Patches Tool] patches worden gewijzigd van *MDVA* tot *ACSD* vanwege interne proceswijzigingen.

## v1.1.15 {#v1-1-15}

* **40961** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een extra item niet aan het winkelwagentje kan worden toegevoegd als de minimumhoeveelheid van het item al in het winkelwagentje staat.
* **MDVA-4487** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5*) - Hiermee worden de *Uncaught SyntaxError: Unexpected token &#39;const&#39;* in het deelvenster Beheer.
* **MDVA-43718** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Oplossingen *De consument heeft geen toegang tot %resources.* fout die wordt weergegeven wanneer u een gedeelde catalogus benadert via een aangepaste integratie.
* **MDVA-44660** (*voor Adobe Commerce en Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij het accent van het graf ligt ``` ` ``` kan niet worden gebruikt voor de voor- en achternaam van een klant.
* **40896** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee worden de *Fout: TypeError: Argument 3 passed to Magento* fout in async product bulkAPI.
* **MDVA-38559** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.3*) - Hiermee worden de */V1/customer/search-API* fout voor klanten met meer dan één abonnement.
* **MDVA-4453** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.4*) - Hiermee wordt de kwestie opgelost waarbij de korting ten onrechte wordt toegepast op een onderliggend product van een bundel.
* Bijgewerkte patches: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **43983** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waar producten *Niet afzonderlijk zichtbaar* worden nog steeds weergegeven in de geavanceerde zoekresultaten van de catalogus.
* **MDVA-4410** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij alle FPT&#39;s worden toegewezen aan het laatste product in het winkelwagentje en opnieuw worden ingesteld voor andere producten.
* **43605** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij met behulp van de Rest API negatieve waarden worden geretourneerd voor rijtotalen.
* **43102** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij het verkoopbare aantal niet correct wordt bijgewerkt wanneer een restitutie via REST API wordt uitgevoerd.
* **43178** (*voor Adobe Commerce en Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een klanttoken voor een aangepaste store niet kan worden opgehaald in GraphQL.
* **43859 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de fout optreedt *Geen dergelijke entiteit met customerId =* wordt geregistreerd wanneer een verwijderde klant probeert zich aan te melden.
* **MDVA-44147** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een GraphQL-aanvraag geen aanvraaglijsten retourneert.
* **44505** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.3*) - Hiermee worden de problemen opgelost waarbij GraphQL die Punten achteruit toepast het Eindtotaal niet bijwerkt en waarbij winkelkrediet meerdere keren wordt toegepast tijdens de plaatsing van de bestelling.
* Bijgewerkte patches: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-3993-V2.

## v1.1.13 {#v1-1-13}

* **42969** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij de regel Verwante producten alleen werkt als het klantsegment is ingesteld op *Alles*.
* **39605** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij Redis cache TTL (vervaldatum) een onjuiste waarde heeft.
* **MDVA-4386** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.5*) - Het probleem waarbij de klant geen winkelwagentjes kan bijwerken vanwege een GraphQL *UpdateCartItems-mutatie* fout.
* **MDVA-43824** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt bij het annuleren van bestellingen met een korting.
* **MDVA-43451** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de fout optreedt *De aangevraagde winkel is niet gevonden. Controleer de winkel en probeer het opnieuw.* verschijnt tijdens het configureren van een gedeelde catalogus voor een specifieke website.
* **MDVA-43491** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij het basisafbeeldingslabel niet wordt bijgewerkt wanneer u producten importeert voor een website met meerdere winkels.
* **MDVA-43601** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Het probleem met ontbrekende triggers wordt opgelost na volledige herindex.
* **42046** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een onjuiste waarde wordt toegewezen aan een productkenmerk met een datuminvoerveld tijdens het bijwerken van een product.
* **MDVA-43935** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij het Upsell-product tweemaal wordt weergegeven.
* **MDVA-4418** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Het probleem waarbij door het systeem verzonden e-mails met `.-` in adressen worden niet verzonden.
* **MDVA-42283** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de datum-tijdnotatie in het beheerorderraster voor de Franse landinstelling ongeldig is.
* Bijgewerkte patches: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Metagegevens van patches toegevoegd voor de [!DNL Site-Wide Analysis Tool].

## v1.1.12 {#v1-1-12}

* **39713** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij de gebruiker de begintijd voor een actieve geplande update kan bewerken.
* **MDVA-42410** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt de emissie gecorrigeerd waarbij in couponrapporten alleen de standaardbasisvaluta wordt weergegeven.
* **MDVA-41136** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de vervaldatum van de `mage-cache-sessid` niet wordt uitgebreid, wat leidt tot het opschonen van klantgegevens.
* **MDVA-3993** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij inventariswijzigingen die via de API worden doorgevoerd, niet op de productpagina op de voorzijde worden weergegeven.
* **MDVA-4285** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een nieuw klantadres niet in het adresboek wordt opgeslagen tijdens het afrekenen.
* **MDVA-42645** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de beheerder geen bonuspunten kan terugbetalen als de functionaliteit voor winkelkrediet is uitgeschakeld.
* **MDVA-43414** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - Hiermee wordt de fatale fout in PHP gecorrigeerd die optreedt wanneer de `inventory.reservations.updateSalabilityStatus` rij consument op numerieke SKUs.
* **MDVA-41628** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij bestaande beperkte beheergebruikers toegang krijgen tot de nieuwe bronnen wanneer nieuwe modules worden toegevoegd.
* **MDVA-43348** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een GraphQL-aanvraag voor een cadeaukaart een fout laat zien als `gift_card_options` bevatten *uid*.
* **39546** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de begindatum voor de gefaseerde update tijdens het bewerken kan worden ingesteld op een eerdere datum dan de huidige datum.
* **MDVA-42950** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Het probleem waarbij video&#39;s niet op de productpagina worden afgespeeld, is opgelost.
* **42689** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Het probleem waarbij Adobe Commerce een *Intensiteitsbeperking schending* fout tijdens het bijwerken van productcategorieën tijdens het importeren.
* **MDVA-41229** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij afbeeldingen die op de achtergrond beschikbaar zijn, niet op de voorzijde worden weergegeven nadat configureerbare producten zijn geïmporteerd.
* **MDVA-43731** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij *Synoniemen zoeken* werkt niet meer wanneer waarde wordt toegevoegd in *Minimale voorwaarden*.
* **MDVA-4323** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij sorteerproducten in [!DNL Visual Merchandiser] Door Speciale prijs voor Onder/Boven veroorzaakt u een fout bij het opslaan van de rubriek.
* **43726 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de catalogusprijsregel op basis van kenmerk op archiefniveau niet wordt toegepast na gedeeltelijke herindex.
* Bijgewerkte patches: MDVA-36464, MDVA-37478, MDVA-38608.
* Metagegevens van patches toegevoegd voor de [!DNL Site-Wide Analysis Tool].

## v1.1.11 {#v1-1-11}

* **MDVA-42790** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij productprijskenmerken niet kunnen worden bijgewerkt voor een specifieke website via REST API.
* **MDVA-41350** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een uitzondering wordt gegenereerd wanneer een beheerder met beperkte toegang een product buiten het rolbereik in een volgorde door SKU toevoegt.
* **MDVA-42269** (*voor Adobe Commerce en Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een beheerder zich niet kan aanmelden bij de beheerder vanwege de *TypeError: strtotime() verwacht dat parameter 1 een tekenreeks is, null gegeven* fout.
* **MDVA-40830** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij het winkelkrediet meerdere keren wordt toegepast tijdens het plaatsen van de bestelling.
* **MDVA-42237** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij een configureerbare speciale prijs van het product niet wordt bijgewerkt na wijzigingen in de prijs van het subproduct.
* **MDVA-42520** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt de kwestie opgelost waarbij het belastingtarief tweemaal wordt toegepast als *Grensoverschrijdende handel inschakelen* wordt gebruikt.
* Bijgewerkte patches: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Vervangen pleister: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **38728** (*voor Adobe Commerce en Magento Open Source >=2.3.2 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij bij het bijwerken van het massakenmerk alleen na het wijzigen een URL wordt gemaakt die wordt herschreven voor de standaardwinkel *Zichtbaarheid product*.
* **43091** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij de fout optreedt wanneer op de achtergrond een bundelproduct van de beheerder wordt besteld *U kunt geen decimale hoeveelheid gebruiken voor dit product*.
* **40816** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij producten uit categorieën die niet in de algemene voorwaarden zijn gedefinieerd, in de desbetreffende productregels worden vermeld.
* **41305** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij GraphQL-mutatie geen configureerbare productopties retourneert nadat deze aan de wenslijst is toegevoegd.
* **39181** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij producten uit categorieën die niet in de algemene voorwaarden zijn gedefinieerd, in de desbetreffende productregels worden vermeld.
* **42584** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de configureerbare voorraadstatus op de achtergrond niet wordt bijgewerkt nadat de status van de hoeveelheid en de voorraad via Importeren of API is gewijzigd.
* **MDVA-40175** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij *Klik om de verzendmethode te wijzigen* Keuzerondjes worden niet weergegeven om verzendmethoden in de beheerdersgroep te selecteren tijdens het opnieuw ordenen.
* **42768 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een standaardprijs van het product wordt ingesteld op 0 wanneer *Weergeven uit voorraad* Ja.
* **MDVA-43201** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt bij het aanmelden bij de klant bij het gebruik van het DOB-kenmerk voor bepaalde landinstellingen.
* Bijgewerkte patches: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **38346** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij datumfilters niet goed werken wanneer de Adobe Commerce-tijdzone afwijkt van de tijdzone van de lokale omgeving.
* **MDVA-42657** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de gebruiker van de beheerder geen categorieën kan selecteren onder de voorwaarden van het klantensegment.
* **42806** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij een *Nieuwe bedrijfsregistratie* Elke keer dat een bestaand bedrijf via de REST API wordt bijgewerkt, wordt een e-mail verzonden.
* **37984** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij de [!DNL Visual Merchandiser] *Product op regel afstemmen* de functionaliteit filtert producten met het opvoeren van updates correct niet.
* **MDVA-4048** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem opgelost dat configureerbare producten met kinderproducten uit de voorraad niet in hun juiste prijsbereik worden weergegeven.
* **42507** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de cache van de volledige pagina wordt opgeschoond nadat een faseupdate voor de kartelregel is toegepast.
* **39163** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij geen verzendmethoden beschikbaar zijn wanneer een nieuwe gebruiker wordt geregistreerd en producten in de winkelwagen afkomstig zijn van de gastsessie.
* **38626 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij de beheerder geen volgorde op de achtergrond kan plaatsen met de opdracht [!DNL PayPal Payflow Pro] betaling.
* **MDVA-3866** (*voor Adobe Commerce en Magento Open Source >=2.3.2 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij de gebruiker van de beheerder de configureerbare productopties in de winkelwagentje van de klant niet kan wijzigen.
* **38526 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij de beheerder geen toegang heeft tot de [!DNL Site-Wide Analysis tool].
* Bijgewerkte patches: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **41215 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij gebruikers de 500-fout krijgen nadat ze de instelling *afbeeldingsberichten* cookie, als deze al bestaat, maar er zijn geen nieuwe berichten.
* **MDVA-41139** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij configureerbare producten uit voorraad raken na het importeren van producten wanneer een eenvoudige producthoeveelheid voor een van de bronnen gelijk is aan 0.
* **42326 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij klanten na een sessietime-out een fout krijgen bij het uitchecken, zelfs als het permanente winkelwagentje is ingeschakeld.
* **MDVA-42341** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij de `categoryList` De resultaten van GraphQL-query worden niet gefilterd als een aanvraag de winkelkoptekst bevat.
* **38393** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij de catalogusregels niet meer werken voor een configureerbaar product als de naam van het eenvoudige product wordt gewijzigd.
* **39153** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij een kortingsbedrag onjuist wordt berekend tijdens het opnieuw ordenen in de beheerder.
* Bijgewerkte patches: MDVA-2893, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-3971** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij beheergebruikers geen toegang hebben tot het raster van de klant nadat ze de website hebben verwijderd.
* **MDVA-4031** (*voor Adobe Commerce en Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij beheergebruikers het foutbericht krijgen *Ongeldige beveiliging of formuliersleutel. Vernieuw de pagina* na aanmelding bij de beheerder als het aangepaste beheerpad is geconfigureerd en de geheime sleutel is ingeschakeld.
* **MDVA-41631** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij gebruikers een fout ondervinden bij het ophalen van ordergegevens zonder een optionele *telefoon* waarde via GraphQL.
* **27239 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij geen producten voor kruisverkoop worden weergegeven.
* Bijgewerkte patches: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-3451, MDVA-3179 1.

## v1.1.6 {#v1-1-6}

* **MDVA-40550** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij ontbrekende producten aan de voorzijde worden aangetroffen tijdens het opnieuw uitsnijden.
* **MDVA-40120** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost dat GraphQL-sortering via DESC/ASC niet werkt met producten met dezelfde relevantie of prijs.
* **MDVA-4139** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij beheergebruikers geen toegang hebben tot de *Winkelwagentje beheren* pagina als een klant een product aan de verlanglijst toevoegt.
* **MDVA-40609** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij gegevens over uitgeschakelde producten ontbreken in de `cataloginventory_stock_status` indextabel met onjuiste hoeveelheden van uitgeschakelde producten.
* **39031** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost dat het mogelijk is een product via GraphQL aan het winkelwagentje toe te voegen, zelfs als het niet aan de doelwebsite is toegewezen.
* **41597** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij gebruikers een fout krijgen wanneer ze meer dan één configureerbaar product met GraphQL aan de winkelwagen toevoegen.
* **27456** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.3.7*) - Hiermee wordt het probleem verholpen waarbij gebruikers een fout ondervinden bij het laden van een toepassing [!DNL Swagger].
* **32776** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de voorraadstatus niet wordt bijgewerkt wanneer een bestelling wordt geplaatst, maar niet wordt verzonden.
* **30862** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.0*) - Hiermee wordt het probleem verholpen met de onjuiste besteldatum op de gedrukte PDF-factuur.
* De indexpagina voor de [!DNL Quality Patch Tool]. Toegevoegde handige zoekfunctie en filterfunctie voor [!DNL quality patches] in de meest recente versie van het gereedschap.
* Bijgewerkte patches: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **41236 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is een nieuwe geplande update voor een product te maken of te bewerken als de einddatum eerder is verwijderd.
* **MDVA-41046** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Het probleem waarbij eenvoudige producten met aangepaste opties beschikbaar zijn voor het toewijzen aan configureerbare/gegroepeerde producten, is opgelost.
* **40545 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij alleen het eerste knooppunt voor een pagina is opgehaald, zelfs als er meer dan één knooppunt voor dezelfde pagina was.
* **MDVA-41164** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - Hiermee wordt het probleem verholpen waarbij een beheerder een bedrijf met een aangepast klantkenmerk voor het bestands- of afbeeldingstype niet kan opslaan of bewerken.
* **MDVA-3929** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waardoor de volgende fout optreedt na het bijwerken van de begintijd van update van catalogusregel bijhouden: *Cron Job staging_synchronize_entities_period heeft een fout: de actieve update kan niet worden verwijderd.*
* **MDVA-40619** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij wijzigingen in de hiërarchie van CMS-pagina een fout van 500 veroorzaken bij pogingen om inline te bewerken op een CMS-pagina.
* **MDVA-41061** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de voorraadstatus wordt hersteld naar de verkoopwaarde wanneer een product wordt opgeslagen bij de beheerder.
* **31763** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij de prijsregels voor catalogi worden teruggedraaid (of niet worden toegepast) totdat ze handmatig opnieuw worden berekend.
* **37748** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij een GraphQL-query producten retourneert die niet zijn toegewezen aan een gedeelde catalogus.

## v1.1.4 {#v1-1-4}

* **MDVA-4039** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij gedeeltelijke facturen voor dezelfde volgorde niet gelijktijdig via REST API kunnen worden gemaakt.
* **MDVA-40101** (*voor Adobe Commerce en Magento Open Source >=2.3.2 &lt;2.4.0*) - Hiermee wordt het probleem verholpen waarbij items niet uit de miniwinkelwagen worden verwijderd nadat de bestelling is geplaatst met [!DNL PayPal Express] Afhandeling.
* **MDVA-40401** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Hiermee wordt de emissie gecorrigeerd waarbij de waarde van het coupongebruik verandert, zelfs als het plaatsen van een bestelling mislukt.
* **40537 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - Hiermee wordt het probleem verholpen waarbij gebruikers een fout krijgen bij het maken van een winkelweergave als er meerdere CMS-pagina&#39;s met dezelfde URL-sleutel bestaan.
* **MDVA-37725** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - Hiermee wordt het probleem verholpen waarbij asynchrone bestellings-e-mails die van niet-standaard websites worden verzonden logo-URL&#39;s van de standaardwebsite bevatten.
* **39482** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij een product uit voorraad komt als het wordt geïmporteerd met de hoeveelheid &quot;0&quot; als backorders zijn ingeschakeld.
* **40435 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.4*) - Het probleem wordt verholpen met een onjuiste korting op bundelproducten met dynamische prijzen die via GraphQL worden toegepast.
* **MC-42528** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - Hiermee wordt het probleem opgelost waarbij de `categoryList` GraphQL-query retourneert zowel toegewezen als niet-toegewezen categorieën.
* **MDVA-2940** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Het probleem wordt verholpen met dubbele bestellingen die worden geplaatst met [!DNL PayPal Express Checkout].
* **26005** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is om een categorie in een categoriestructuur te selecteren voor de regelvoorwaarden voor winkelwagentjes.
* **25631** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - Verbetert de prestaties voor het bewerken en opslaan van klantsegmenten met een groot aantal klanten.

## v1.1.3 {#v1-1-3}

* **MDVA-4026** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij zoekopdrachten in GraphQL niet worden weergegeven in populaire zoektermen in de beheerdersaccount.
* **MDVA-40601** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - Hiermee wordt het probleem verholpen waarbij gebruikers een fout krijgen wanneer ze proberen informatie over de categorie te wijzigen via een geplande update via GraphQL.
* **37234** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Hiermee wordt het probleem verholpen waarbij een item meerdere keren (parallel verzoek) voor dezelfde SKU aan het winkelwagentje wordt toegevoegd, waardoor een dubbel regelitem voor dezelfde winkelwagentje-id wordt gemaakt.
* **33606** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - Hiermee wordt het probleem opgelost waarbij gebruikers een *Unieke schending van beperking* fout bij het opslaan van een CMS-pagina die is toegewezen aan een hiërarchie.
* **MDVA-31590** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - Hiermee wordt het probleem verholpen waarbij gebruikers geen kenmerken in bulk kunnen bijwerken met MySQL async-wachtrijen.
* **36309** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Het probleem waarbij het zoeken naar kenmerken van producten traag verloopt in de beheerrasters wordt opgelost.

## v1.1.2 {#v1-1-2}

* **38929 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Hiermee wordt de kwestie opgelost waarbij op de factuur met het FPT een verkeerde Grand Total wordt getoond wanneer de bestelling uit het winkelkrediet wordt betaald.
* **37364** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;=2.4.3*) - Hiermee wordt het probleem verholpen waarbij het aangepaste kenmerk voor klanten van het datumtype de interface van het raster van de klant verbreekt.
* **39195** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Hiermee wordt het probleem opgelost waarbij *Toevoegen aan winkelwagentje* button was inactief op de categoriepagina wanneer omleiding naar winkelwagentje ingeschakeld was.
* **MDVA-3715** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - Hiermee wordt het probleem opgelost waar een onnodige *Slechts 0 links* op de configureerbare productpagina wordt een waarschuwing weergegeven.
* **39521** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij de gebruiker geen verzendadressen op de winkelwagentje kan instellen met een leeg telefoonnummer via GraphQL.
* **39384** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Hiermee wordt het probleem verholpen waarbij het aangepaste klantkenmerk voor een bedrijfsgebruiker niet wordt opgeslagen.
* **39043** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.4.3*) - Hiermee wordt het probleem verholpen waarbij de beheerder met beperkte toegang een fout krijgt bij het toevoegen van de *Producten* aan de CMS-pagina.
* **MDVA-3996** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - Het probleem is opgelost door onjuiste landinstellingen te gebruiken.
* **38852** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij de catalogusvoorraad door het ontwerp tabellen vergrendelt voor updates die de prestaties aanzienlijk verminderen in gevallen met meerdere parallelle bestellingen.
* **39986** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de gebruiker via de Safari-browser geen bestelling kan plaatsen in de Admin op MacOS.
* **MDVA-3847** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - Hiermee worden twee kwesties opgelost: waar *Niet afzonderlijk zichtbaar* configureerbare onderliggende producten worden geretourneerd in GraphQL-reactie en optimaliseren MySQL-query voor GraphQL-productquery met categoriefilter.
* **MDVA-40134** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij GraphQL geen verwante producten retourneert wanneer de gedeelde catalogus is ingeschakeld.
* **39935** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - Het probleem waarbij de GraphQL configureerbare onderliggende producten retourneert die op websiteniveau zijn uitgeschakeld.

## v1.1.1 {#v1-1-1}

* **36021 MDVA** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij de *Aanroep van een lidfunctie getId()* Er wordt een fout weergegeven op de pagina met orderdetails in Admin.
* **34948** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Het probleem wordt opgelost met langdurige query&#39;s, zoals `GET_LOCK`.
* **39305** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij geregistreerde klanten zich niet kunnen aanmelden met Google ReCaptcha.
* **37897** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - Het probleem wordt verholpen met een onjuiste omleiding wanneer een klant producten probeert toe te voegen met opties van de onlangs bekeken widget.

## v1.1.0 {#v1-1-0}

* Patchcategorieën zijn geïntroduceerd om de gebruikerservaring te verbeteren en het zoeken naar vereiste patches voor klanten eenvoudiger te maken.
* De `patches.json` bestand is hernoemd naar `support-patches.json`.
* **MDVA-3879** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij downloadbare producten niet zijn opgeslagen na het maken van een testupdate.
* **37592** (*voor Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Het probleem wordt verholpen wanneer sorteren op prijs niet correct werkt voor producten met een nulprijs die aan de gedeelde catalogus is toegewezen.
* **MDVA-38827** (*voor Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij klanten een e-mail met een bestelbericht ontvangen dat een foutbericht bevat.

## v1.0.26 {#v1-0-26}

* **38468** (*voor Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - Hiermee wordt de fout bij het opslaan van CMS-pagina&#39;s gecorrigeerd: *Item met dezelfde id PAGE_ID bestaat al*.
* **MDVA-34680** (*voor Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de tijd die voor de Customer Account is gemaakt, niet correct is gefilterd in het klantenraster.
* **37068** (*voor Adobe Commerce >=2.3.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij het onjuiste belastingtarief wordt weergegeven wanneer het winkelwagentje alleen virtuele producten bevat.
* **38608** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij tijdelijke tabellen niet worden verwijderd als de redex niet met succes is voltooid.
* **38308** (*voor Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - Hiermee worden de problemen opgelost die te maken hebben met de toevoeging [!DNL Vimeo] video&#39;s naar producten.

## v1.0.25 {#v1-0-25}

* **37916** (*voor Adobe Commerce >=2.3.6 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de klant niet naar de pagina Betalingsbevestiging wordt geleid wanneer de gebruiker de [!DNL Paypal Payment Advanced] methode.
* **37082** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Het probleem wordt verholpen wanneer de aangepaste voorraad gegroepeerde producten wordt opgeslagen, waardoor het product op de voorgrond uit voorraad komt te staan.
* **36572** (*voor Adobe Commerce >=2.3.5 &lt;2.4.3*) - Hiermee wordt het probleem verholpen wanneer updates van creditnota niet langer leiden tot dubbele updates van productreserveringen in de database.
* **38132** (*voor Adobe Commerce >=2.3.3 &lt;2.4.3*) - Het probleem wordt opgelost wanneer het deelvenster Beheer niet bereikbaar is vanwege een *te veel omleidingen* fout.
* **MDVA-38270** (*voor Adobe Commerce >=2.4.1 &lt;2.4.3*) - Het probleem met ontbrekende Gift-kaartgegevens in het ordertotaal in GraphQL wordt opgelost.

## v1.0.24 {#v1-0-24}

* **MDVA-3779** (*voor Adobe Commerce >=2.4.2 &lt;=2.4.4*) - Het probleem met het toevoegen van een configureerbaar product aan het winkelwagentje via GraphQL wanneer de website-id niet overeenkomt met de winkel-id, is opgelost.
* **36832** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij afbeeldingen worden gedupliceerd op pagina&#39;s met een weergavebreedte van 768 px.
* **37874** (*voor Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - Hiermee wordt het probleem opgelost waarbij *Vaste korting voor hele winkelwagen* wordt verkeerd toegepast op een bundelproduct dat meer dan één optie bevat.
* **37913** (*voor Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - Hiermee wordt het probleem verholpen waarbij downloadbare koppelingen verdwijnen als het downloadbare product via de API wordt bijgewerkt.
* **MDVA-34330** (*voor Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij orders in het raster Bestellingen niet worden gefilterd volgens de tijdzone van Admin.

## v1.0.23 {#v1-0-23}

* **37478** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.7*) - Het probleem waarbij Adobe Commerce een fout genereert bij het maken van een gedeeltelijke factuur voor bestellingen die bij de *Betaling op rekening* betalingsmethode via REST API.
* **37362** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - Het probleem waarbij configureerbare waarden voor productopties en variantkenmerken in GraphQL-reactie leeg waren.
* **MDVA-3728** (*voor Adobe Commerce 2.4.2*) - Hiermee wordt het probleem opgelost waarbij na een GraphQL-aanvraag onjuiste prijzen werden geretourneerd.
* **MDVA-37225** (*voor Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij het uploadproces vastloopt tijdens het maken van snelle bestellingen wanneer geïmporteerde SKU&#39;s een geheel-getalwaarde hebben.
* **MDVA-3724** (*voor Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - Oplossing van het probleem waarbij klanten niet kunnen betalen voor een verhandelbare prijsopgave [!DNL PayFlow Pro] met een ander product in de kar.
* **36286** (*voor Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij de voorvertoning van de widget voor pagina Builder-producten wordt afgebroken als dezelfde SKU een andere positie in subcategorieën heeft.
* **30186** (*voor Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - Hiermee wordt het probleem verholpen waarbij kenmerkopties worden gesorteerd op optiewaarde in plaats van het aantal kenmerkitems in GraphQL-reactie.

## v1.0.22 {#v1-0-22}

* **36718 MDVA** (*voor Adobe Commerce >=2.3.0 &lt;=2.4.2*) - Hiermee wordt het probleem verholpen waarbij de oude aangepaste opties blijven bestaan nadat deze via API zijn gewijzigd.
* **MDVA-3573** (*voor Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Hiermee wordt de kwestie opgelost waarbij het Eindtotaal niet als nul op de factuur wordt weergegeven voor bestellingen met een korting van 100%.
* **MDVA-3683** (*voor Adobe Commerce 2.4.2*) - Het probleem wordt verholpen met zoekresultaten die een willekeurig aantal producten per pagina laten zien nadat bepaalde producten van de gedeelde catalogus zijn uitgesloten.
* **37182** (*voor Adobe Commerce >=2.4.1 &lt;=2.4.2*) - Het probleem wordt verholpen door onjuiste zoekresultaten op te halen in beide [!DNL Elasticsearch] versie 6 en versie 7.
* **36253** (*voor Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - Hiermee wordt het probleem opgelost waarbij het onjuiste subtotaal in het minikaart wordt weergegeven na verwijdering van het item.
* **36853** (*voor Adobe Commerce 2.4.2*) - Het probleem is opgelost zonder afbeeldingen die worden weergegeven wanneer grote mediagalerieën worden geladen.

## v1.0.21 {#v1-0-21}

* **MDVA-3465** (*voor Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - Het probleem met ontbrekende gebundelde producten op categoriepagina&#39;s wordt opgelost.
* **36615 MDVA** (*voor Adobe Commerce 2.4.2*) - Het probleem wordt verholpen met een onjuist aantal producten in het productraster van Admin.
* **36464** (*voor Adobe Commerce >=2.4.0 &lt;=2.4.2*) - Hiermee wordt het probleem verholpen waarbij de configuratie van de e-mailmelding niet werkt in de winkelweergave.
* **MDVA-36138** (*voor Adobe Commerce ^2.3.2*) - Hiermee wordt het probleem opgelost waarbij de verzendprijs niet wordt aangepast en de volledige verzendprijs aan klanten wordt getoond als niet alle objecten in de winkelwagentje in aanmerking komen voor de regel voor het gratis verzenden van winkelwagentjes.
* **36424 MDVA** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Hiermee wordt het probleem verholpen waarbij mediaafbeeldingen die zijn gekoppeld aan elementen van de paginaontwikkelaar verdwijnen als de inhoud herhaaldelijk wordt bewerkt als de URL van de achterste basis afwijkt van de URL van de opslagbasis.
* **35984** (*voor Adobe Commerce ^2.4.0*) - Hiermee wordt het probleem verholpen met een onjuiste producthoeveelheid en een verkoopbare hoeveelheid nadat meerdere gelijktijdige verzendingen voor hetzelfde product zijn gemaakt.

## v1.0.20 {#v1-0-20}

* **MDVA-36170** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermee verhelpt u het probleem waarbij de GraphQL-query niet in cache wordt geplaatst door de cachetag voor de categorie te gebruiken.
* **33168 MDVA** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Het probleem wordt verholpen wanneer een productkenmerk via API wordt bijgewerkt. Alle andere kenmerken worden gewijzigd in een lege waarde.
* **MDVA-19640** (*voor Adobe Commerce >=2.3.0*) - Hiermee wordt het probleem opgelost waarbij [!DNL Advanced Reporting] geeft geen gegevens weer.
* **MDVA-1189** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - Het probleem wordt verholpen wanneer een CSV-bestand is geïmporteerd om de productvoorraad bij te werken, rijen van de `cataloginventory_stock` de tabel wordt verwijderd.
* **26639 MDVA** (*voor Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij de orderonderdelen ontbreken in de e-mail met bevestiging van de bestelling als er een nieuwe sjabloon voor bevestiging van de bestelling wordt gemaakt.
* **MDVA-15546** (*voor Adobe Commerce >=2.3.0*) - Hiermee wordt het probleem opgelost waarbij na het maken van een bestelling een *Kolomentiteit_id waarbij de component dubbelzinnig is* de foutenvertoningen in het uitzonderingslogboek.
* **MDVA-2095** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - Het probleem bij een query wordt opgelost `INSERT INTO search_tmp` eindigt niet na de update van de waarde van het kenmerk mass.
* **23845** (*voor Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Hiermee wordt het probleem verholpen waarbij geen voorbeeld kan worden weergegeven van e-mailsjablonen nadat JavaScript-miniaturen zijn ingeschakeld.
* **MDVA-2026** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - Het probleem waarbij het importeren van producten uit CSV-bestand, inclusief afbeeldingen van externe URL&#39;s, mislukt.
* **22383** (*voor Adobe Commerce >=2.3.0 &lt;2.3.4*) - Het probleem waarbij het opslaan van een product veel tijd in beslag neemt en de pagina-einden.
* **MC-41359** (*voor Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - Hiermee wordt het probleem met de onjuiste instellingen van de SameSite-cookie-parameters opgelost.

## v1.0.19 {#v1-0-19}

* **33614** (*voor Adobe Commerce 2.4.1*) - Hiermee wordt het probleem verholpen waarbij de Page Builder de volgende fout veroorzaakt: *Er is een fout opgetreden bij het starten van de Page Builder. Neem contact op met uw contactpersoon voor technische ondersteuning.*
* **35356** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen met een onjuist rendement op winkelkredieten nadat de bestelling gedeeltelijk is geannuleerd.
* **33289** (*voor Adobe Commerce >=2.4.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij onbewerkte JavaScript-code wordt weergegeven in de gebruikersinterface van het factureringsadres tijdens het uitchecken als [!DNL Google Tag Manager] is ingeschakeld.
* **35982** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij beheerders die zich tot een bepaalde website beperken, geen verzending kunnen maken voor de bestelling die op dezelfde website is geplaatst.
* **MDVA-3515** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is om een bundelproduct te kopen als de optietitel is gewijzigd.
* **MDVA-35910** (*voor Adobe Commerce >=2.4.1 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is om een nieuwe klantenaccount te maken nadat de aanmelding als functionaliteit van de klant is uitgeschakeld.
* **34474** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Het probleem wordt verholpen door een product met de API toe te voegen aan de aanvraaglijst.
* **34591** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem opgelost met een onjuiste berekening van de winkelregelkorting voor *Maximale korting op de hoeveelheid wordt toegepast op* en *Kortingsstap (X kopen)*.
* **33704** (*voor Adobe Commerce >=2.4.0 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij de *Ophalen in winkel* De verschepende optie verschijnt niet, hoewel wordt gevormd om beschikbaar te zijn.
* **34928** (*voor Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij de paginalader oneindig wordt weergegeven nadat het winkelkrediet uit de betaling is verwijderd.
* **35254** (*voor Adobe Commerce >=2.3.1 &lt;2.4.3*) - Hiermee verhelpt u de problemen met CAPTCHA tijdens het afrekenen.
* **35569** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de *vaste productbelastingen* wordt niet ingevuld in GraphQL-reactie als de status is opgegeven.
* **35847 MDVA** (*voor Adobe Commerce >=2.4.1 &lt;2.4.3*) - Oplossing van het B2B-probleem waarbij het formulier Bedrijfs-gebruikers wordt afgebroken als een aangepast kenmerk van de klant wordt gebruikt.
* **31307** (*voor Adobe Commerce >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waar *Onvoldoende geheugen* fouten op bepaalde categorieën als gevolg van problemen met de dynamische whitelisting van CSP voor in cache geplaatste blokken.

## v1.0.18 {#v1-0-18}

* **MDVA-3265** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Corrigeert het onjuiste *in uitvoering* berichtstatus voor de juiste *complete* boodschap voor de consument `quoteItemCleaner` na het verwijderen van meerdere producten.
* **34102** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee stelt u de hoeveelheid standaardvoorraad in op nul voor uitgeschakelde producten op het productraster en op Productpagina&#39;s bewerken in het beheergebied.
* **35286** (*voor Adobe Commerce >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt wanneer een klant producten in de winkelwagen heeft gebundeld en overschakelt van het uitchecken van meerdere adressen naar het uitchecken op één pagina.
* **35312** (*voor Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - Hiermee wordt antwoordcode 500 gecorrigeerd wanneer een leeg GraphQL-verzoek wordt ingediend.
* **34189** (*voor Adobe Commerce >=2.3.4 &lt;2.4.3*) - Oplossingen voor 503 eerste byte-time-out op [!DNL Visual Merchandiser] vragen bij het laden van de pagina Admin-categorie.
* **34695** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1*) - Oplossingen negatief `children_count` na het verwijderen van categorieën.

## v1.0.17 {#v1-0-17}

* **34012** (*voor Adobe Commerce >=2.3.1 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij de *Standaardwaarde gebruiken* Schakel het selectievakje uit nadat de geplande wijzigingen zijn toegepast. De uitgave wordt weergegeven zodra de geplande wijzigingen niet meer van kracht zijn.
* **35064** (*voor Adobe Commerce >=2.3.3 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij URL-herschrijvingen niet worden gegenereerd voor configureerbare producten die via API zijn gemaakt.
* **34943** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de eerder ingevoerde SKU&#39;s in een cache worden opgeslagen met een snelle volgorde.
* **35197** (*voor Adobe Commerce >=2.3.5 &lt;2.4.0*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt bij het toevoegen aan winkelwagentje met GraphQL als eerder toegevoegde producten uit voorraad raken.
* **MDVA-34850** (*voor Adobe Commerce >=2.3.1 &lt;2.4.0*) - Hiermee wordt het probleem verholpen waarbij de opties voor een configureerbaar product die buiten de voorraad vallen, niet worden weergegeven in plaats van als doorgehaalde afbeelding.
* **34867** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij waarden voor een voorwaardenveld dat is ingesteld voor een geplande update, niet worden opgeslagen.
* **35092** (*voor Adobe Commerce >=2.3.5 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij gebruikers geen gegevens kunnen toevoegen [!DNL Vimeo] video&#39;s vanwege vervangen [!DNL Vimeo] API.

## v1.0.16 {#v1-0-16}

* **33453** (*voor Adobe Commerce >=2.3.6 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de voorvertoning van het inhoudstype Pagina Builder-producten wordt onderbroken als overeenkomende producten verschillende prijzen voor elke website hebben.
* **32634 MDVA** (*voor Adobe Commerce ^2.3.1*) - Hiermee wordt het probleem opgelost waarbij de `url_path` van de categorie die aan alle opslagruimten is toegewezen, blijft ongewijzigd nadat de categorie in de hiërarchie is verplaatst.
* **MDVA-3344** (*voor Adobe Commerce ^2.3.0*) - Het probleem met harde codering wordt opgelost `rma_item` id van standaard entiteitskenmerkset wordt gebruikt in plaats van de waarde uit de database.
* **34192** (*voor Adobe Commerce >=2.3.4 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij het onmogelijk is de geboortedatum van de klant te wijzigen of op te geven in de indeling dd/mm/jjjj.
* **34847** (*voor Adobe Commerce ^2.3.0*) - Oplossingen opslaan IDs type omzetting in geheel voor SQL voorwaarde in inzamelingen Admin voor Gebruiker Admin met douanerechten.
* **MDVA-3486** (*voor Adobe Commerce ^2.3.2*) - Hiermee wordt het probleem opgelost waarbij de zoekopdracht geen resultaten oplevert als *gewicht* productkenmerk is geconfigureerd als doorzoekbaar.

## v1.0.15 {#v1-0-15}

* **MDVA-33559** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Oplossingen voor het probleem van [!DNL PayPal Payflow Pro] betaling mislukt vanwege fout in indeling parameterlijst omleiden.
* **34023** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - Hiermee wordt het probleem opgelost waarbij de fout optreedt *Entiteit met adresId bestaat niet* wordt willekeurig weergegeven in browsers van bezoekers.
* **32759 MDVA** (*voor Adobe Commerce >=2.3.1 &lt;2.4.3 met B2B-extensie*) - Hiermee wordt het probleem verholpen waarbij gedeelde catalogi de bestaande laagprijzen verwijderen.
* **33482** (*voor Adobe Commerce ^2.3.5*) - Oplossing van de kwestie waar het genereren van een creditmemo tegen een gedeeltelijke factuur leidt tot belasting voor de totale bestelling in plaats van belasting voor die gedeeltelijke factuur.
* **MDVA-33393** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt de fout gecorrigeerd *Opgegeven landId bestaat niet*.
* **33632** (*voor Adobe Commerce >=2.3.0 &lt;2.3.7*) - Verstrekt een moeilijke situatie waar het uitzonderingsbericht *Dit product is uit voorraad* wordt nu weergegeven aan een beheerder die een product uit de voorraad opnieuw probeert te bestellen.
* **34469** (*voor Adobe Commerce >=2.4.1 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij GraphQL-mutaties in de winkelwagentje van een klant mislukken wanneer meerdere winkelweergaven worden gebruikt.
* **33976** (*voor Adobe Commerce >=2.3.0 &lt;2.3.7*) - Hiermee wordt het probleem opgelost waarbij het bundelproduct uit voorraad op de winkel wordt weergegeven nadat de tweede optie uit het bundelproduct is verwijderd.
* **33894** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1 met B2B-extensie*) - Hiermee worden meerdere problemen opgelost voor de functie Snel bestellen, zoals het toevoegen en verwijderen van meerdere producten en de gevoeligheid van SKU-hoofdletters.
* **MDVA-2764** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6*) - Oplossing van het probleem in het registratieformulier voor klanten dat een weergavefout veroorzaakt: *FOUT - De geboortedatum mag niet groter zijn dan vandaag.*
* **33970 MDVA** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Oplossing van de kwestie waar in het creditmemo het verkeerde valutateken staan wanneer het bereik van het prijselement op de website is ingesteld.
* **33992** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen van de speciale B2B-prijzen die tijdens het afrekenen onjuist worden weergegeven.
* **MDVA-34100** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2 met B2B-extensie*) - Hiermee wordt de kwestie opgelost waarbij een bedrijfsaccount niet op de pagina met bedrijfsstructuren kan worden gemaakt.

## v1.0.14 {#v1-0-14}

* **31969** (*voor Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - Het probleem is opgelost met gedupliceerde afbeeldingen nadat het product uit een CSV-bestand is geïmporteerd.
* **MDVA-33382** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee worden de problemen opgelost met de validatie van indexen nadat producten uit een categorie zijn verwijderd.
* **MDVA-2851** (*voor Adobe Commerce >=2.3.5 &lt;2.3.6*) - Hiermee wordt het probleem opgelost dat niet kan worden opgelost [!DNL PayPal] uitchecken als het veld Naam bepaalde tekens bevat (zoals hoofdletters met accent).
* **MDVA-31519** (*voor Adobe Commerce >=2.3.5 &lt;2.3.6*) - Het probleem wordt opgelost door wachttijden op te geven bij uitchecken door gasten wanneer een verkoopregel voor de hele site wordt gebruikt.
* **33281** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij een fatale fout optreedt in `inventory:reservation:list-inconsistencies` vanwege onjuist SKU-parametertype.
* **24201** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - Hiermee wordt de kwestie opgelost waarbij de prijzen pas na handmatig opnieuw indexeren de regel van de geplande winkelwagenprijs weerspiegelen.
* **32694** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een beheerder een product niet kan toevoegen aan een verhandelbaar aanhalingsteken als het betrekking heeft op een niet-standaardwinkel.
* **33516** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij het bewerken van een bundelproduct in een aanvraaglijst tot een fout leidt.
* **33975** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Oplossingen voor meerdere problemen met betrekking tot prijsberekening in GraphQL-verzoeken.

## v1.0.13 {#v1-0-13}

* **30858** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Het probleem verholpen met [!DNL PayPal] Afwikkelingsrapporten niet beschikbaar onder **Rapporten** > **Verkoop** > **[!DNL PayPal]** Afwikkeling zoals verwacht.
* **MCP-87** (*voor Adobe Commerce >=2.3.1 &lt;2.4.2*) - Verbeterde indexatietijd voor producten- en voorraadindexeerders voor grote profielen voor categorieën.
* **33106** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij de opnieuw geplande productwijzigingen worden gewist na de kroon `run` wordt uitgevoerd.
* **MDVA-19391** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - Hiermee wordt het probleem opgelost waarbij `analytics_collect_data` genereert een fout vanwege NULL-beschrijvingsrecords in het dialoogvenster `catalog_category_entity_text` tabel.
* **MDVA-2036** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - Het probleem is opgelost met de *Geen dergelijke entiteit met customerId = 1* fout in de `exception.log` voor aangemelde klanten na plaatsing van de bestelling.
* **23764** (*voor Adobe Commerce >=2.3.2 &lt;2.3.5*) - Hiermee wordt de fout opgelost in `JsFooterPlugin.php` die de weergave van dynamische blokken beïnvloedt.
* **13203** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de *Integriteitsbeperking schending search_tmp_ table* Er wordt een fout weergegeven na een volledige redex.
* **23426** (*voor Adobe Commerce >=2.3.3 &lt;2.3.5*) - Hiermee wordt het probleem verholpen waarbij e-mailberichten die door Adobe Commerce zijn verzonden een lege tekst bevatten met inhoud die als bijlage wordt toegevoegd.
* **MDVA-22150** (*voor Adobe Commerce >=2.3.1 &lt;2.3.4*) - Hiermee wordt het probleem verholpen waarbij klanten met een configureerbaar product in de winkelwagen en een coupon niet kunnen inloggen als dat configureerbare product is uitgeschakeld in de beheerder.
* **32545** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij facturen niet automatisch worden verzonden bij het maken van bestellingen van de beheerder.
* **32714** (*voor Adobe Commerce >=2.3.4 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij de prijs van de klantengroep niet werkt in de productquery van GraphQL.

## v1.0.12 {#v1-0-12}

* **MDVA-3139** (*voor Adobe Commerce >=2.3.2 &lt;2.4.2*) - Hiermee voegt u de *Subtotaal Belasting)* de mogelijkheid om prijsregels toe te passen.
* **MDVA-31236** (*voor Adobe Commerce >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij beheerders met aangepaste resourcetoegang 2FA niet kunnen instellen of zich aanmelden.
* **30845** (*voor Adobe Commerce >=2.3.5 &lt;2.3.7*) - Hiermee wordt het probleem opgelost waarbij de *Er zijn momenteel geen aanhalingstekens beschikbaar voor deze bestelling* Er wordt een fout weergegeven wanneer u geen verbinding maakt met UPS XML/USPS/DHL en er geen andere verzendmethode beschikbaar is.
* **MDVA-3213** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij mediagalerie in bepaalde gevallen niet vanaf Page Builder wordt geladen.
* **12304** (*voor Adobe Commerce >=2.3.0*) - Het maximumaantal cookies wordt verhoogd van 50 naar 200.
* **32632** (*voor Adobe Commerce >=2.3.2 &lt;2.3.5*) - Oplossing van het probleem waarbij in het betalingssysteem, maar niet in Adobe Commerce, bestellingen worden weergegeven.
* **MDVA-32449** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0. || >=2.4.1 &lt;2.4.2 met B2B-extensie*) - Hiermee wordt het probleem verholpen waarbij de geschiedenis van de bestelling zeer langzaam wordt geladen of helemaal niet wordt geladen.
* **MDVA-32739** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij oude e-mails worden verzonden wanneer asynchrone e-mailberichten worden ingeschakeld.

## v1.0.11 {#v1-0-11}

* **MC-38509** (*voor Adobe Commerce 2.3.6, 2.4.1*) - Hiermee wordt het probleem opgelost waarbij de *Een account maken* de knop blijft uitgeschakeld na correctie van ongeldige gegevens in het dialoogvenster *Nieuwe klantaccount maken* formulier.
* **31006** (*voor Adobe Commerce 2.3.0, 2.3.1*) - Hiermee wordt het probleem verholpen waarbij dubbele bestellingen worden weergegeven nadat een bestelling is geplaatst met [!DNL Paypal Express] betaling.
* **25602** (*voor Adobe Commerce 2.3.0*) - Probleem opgelost met [!DNL PayPal Payflow Pro] betalingsmethode en cookies behandelen als `SameSite=Lax` door gebrek in Chrome 80 browser en API reactie richt zich aan de klantenlogin pagina opnieuw.

## v1.0.10 {#v1-0-10}

Kleine correcties voor patchversies

## v1.0.9 {#v1-0-9}

* **31363** (*voor Adobe Commerce >=2.3.2 &lt;2.4.2*) - Hiermee wordt de kwestie opgelost waarbij de regel van de winkelwagenprijs met coupon niet van toepassing is via GraphQL wanneer *Korting op een vast bedrag voor een hele winkelwagen* actie wordt gebruikt.
* **MDVA-3089** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt nadat een bundel met virtuele en eenvoudige producten als opties is aangeroepen.
* **31791** (*voor Adobe Commerce >=2.3.4 &lt;2.3.5*) - Verbetert de prestaties van de productpagina in gevallen waarin doelregels of gekoppelde producten worden gebruikt.
* **MDVA-31168** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij het CSV-bestand voor het exporteren van het product niet wordt weergegeven en er een fout in de geheugentoewijzing optreedt.
* **32313** (*voor Adobe Commerce >=2.3.0 &lt;2.3.4*) - Hiermee wordt het probleem opgelost waarbij configureerbare producten aan de verlanglijst kunnen worden toegevoegd met de verkeerde configuratieopties.
* **MDVA-31759** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij producten niet worden bijgewerkt met *druppel* en *textarea* kenmerkwaarden tijdens het importeren van CSV.
* **32012** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost dat postcodes in Korea en Argentinië niet kunnen worden gevalideerd.
* **MDVA-31640** (*voor Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij een speciale prijs niet kan worden bijgewerkt via REST API.
* **28651** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 met B2B-extensie*) - Het probleem met prestatieproblemen bij het laden van verhandelbare aanhalingstekens via REST API wordt opgelost.

## v1.0.8 {#v1-0-8}

* **MDVA-31242** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1 met B2B-extensie*) - Hiermee wordt de kwestie opgelost waarbij een onjuist valutateken wordt weergegeven in het credit memo-raster.
* **31295** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt de kwestie opgelost waarbij beloningspunten niet worden berekend wanneer een gedeeltelijke bestelling wordt voltooid en items worden belast.
* **MDVA-3012** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermee wordt de kwestie opgelost waarbij het aantal bestellingen groter is dan *troebelgrootte* waarde, Adobe Commerce beschouwt de orders als *hangend* status als inconsistenties.
* **MDVA-31150** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Oplossing van het probleem waarbij de tegoeden van de creditcard van de winkel en van de cadeaukaart niet worden geretourneerd door de aanroep van de API voor facturering van de GET, wanneer de factuur werd gepost door de Rest API-aanroep en de bestelling gedeeltelijk werd betaald door creditcardrekeningen van de winkel.
* **30963** (*voor Adobe Commerce >=2.3.2 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij filterresultaten die zijn ingesteld op alleen waarden bevatten die zijn opgegeven voor *Alle winkelweergaven* bereik in de beheerdersinterface: omvat producten met waarden die op het weergaveniveau van de winkel zijn overschreven.
* **MDVA-29954** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0. || 2.4.2 met B2B-extensie*) - Hiermee wordt het probleem opgelost waarbij de *Nieuwe aanvraag voor registratie van bedrijf* en *U bent verbonden met een bedrijf* e-mails worden verzonden vanaf het verkeerde adres.
* **28357** (*voor Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Hiermee vervangt u de standaardanalysator door een aangepaste analysator met een trefwoordtokenizer voor het SKU-veld in het dialoogvenster [!DNL ElasticSearch] index om zoekopdrachten met jokertekens te laten werken met SKU&#39;s die een afbreekstreepje (&quot;-&quot;) bevatten.

## v1.0.7 {#v1-0-7}

* **30972** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij de aangepaste orderstatus is gewijzigd in *Verwerking* na gedeeltelijke verzending met WebApi.
* **30428** (*voor Adobe Commerce >=2.3.4 &lt;2.3.5*) - Hiermee wordt het probleem verholpen waarbij klanten een product niet aan de verlanglijst kunnen toevoegen als dit product aan een aangepaste inventarisbron is toegewezen.
* **30594** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een bestelling met meerdere adressen niet kon worden opgeslagen tijdens het uitchecken wanneer FPT is geconfigureerd.
* **MDVA-29148** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Het probleem wordt verholpen wanneer een product wordt gemaakt via een API-aanroep, het aangepaste productkenmerk van `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (zoals Multiselect) gebruikt de standaardwaarde niet als er geen waarde in de lading is opgegeven.
* **30837 MDVA** (*voor Adobe Commerce >=2.3.1 &lt;2.3.5*) - Een configuratie-instelling toegevoegd *Inclusief BTW op bedrag: Ja/Nee* in configuratie van de methode Free Shipping. Wanneer *Inclusief BTW op bedrag* is ingesteld op *Ja*, Minimumbedrag bestelling wordt berekend als Subtotaal + BTW. Wanneer *Inclusief BTW op bedrag* is ingesteld op *Nee*, Minimumbedrag bestelling wordt berekend als Subtotaal
* **25028** (*voor Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Het probleem wordt verholpen wanneer bestellingen worden geplaatst met [!DNL PayPal Payflow Pro] niet zijn ingesteld op de status Vermoedelijke fraude wanneer er fraudefilters worden geactiveerd.
* **MDVA-31224** (*voor Adobe Commerce >=2.3.3 &lt;2.3.5*) - Verbetert de prestaties van de `catalog_product_price` herindexering van de bundelproducten.
* **MDVA-31321** (*voor Adobe Commerce >=2.3.2 &lt;2.3.5*) - Hiermee wordt een lege pagina gecorrigeerd (fout) wanneer *Alles tonen* is geselecteerd. [!DNL Elasticsearch] retourneert een grote lijst met product-id&#39;s. In dit scenario wordt de volgorde door de component omgezet in een onjuiste SQL-indeling.
* **30815** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - Hiermee wordt het probleem verholpen waarbij Adobe Commerce een lege pagina weergeeft wanneer u wijzigt hoeveel zoekresultaten op de pagina met zoekresultaten moeten worden weergegeven. [!DNL Elasticsearch] geeft nu correct de resultaten van categoriepagina&#39;s weer wanneer u het aantal weergegeven zoekresultaten per pagina wijzigt.
* **30782** (*voor Adobe Commerce >=2.3.5 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij Dynamisch blok wordt weergegeven, ongeacht de regels voor winkelwagentjes.
* **31021 MDVA** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij prestatieproblemen optreden in `module-catalog-import-export/Model/Import/Product/Option.php`. Als er meer dan ~100k records zijn in `catalog_product_option` een nieuwe CSV met één product duurt minder dan 10 seconden om te valideren.
* **31007** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij aangepaste adreskenmerken niet correct worden weergegeven op de pagina met orderdetails in het gebied Mijn account en op de achtergrond.
* **29389** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Het probleem wordt verholpen met Geavanceerde rapportage waarbij de `analytics_collect_data` cronjob zegt : *De haven moet binnen gastheerparameter (als localhost:3306) worden gevormd*.
* **31343** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6*) - Het probleem wordt verholpen met de verwijderde body-klasse `page-layout-category-full-width` wanneer een categorie gepland is.
* **30945** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij een onherstelbaar foutbericht wordt weergegeven wanneer winkelwagentjes worden bijgewerkt `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php`.

## v1.0.6 {#v1-0-6}

* **MDVA-2893** (*voor Adobe Commerce >=2.3.4 &lt;2.4.0*) - Hiermee wordt het *Minimum moet overeenkomen* functionaliteit en gedeeltelijk zoeken naar [!DNL Elasticsearch] motor. Hiermee lost u problemen op met afbreekstreepjes in zoekopdrachten.
* **30102** (*voor Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Hiermee wordt het probleem verholpen waarbij de cache van Redis snel toeneemt omdat de lay-outcaches geen TTL hebben.
* **30599** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.0*) - Hiermee wordt het probleem verholpen waarbij gastcitaten die met API zijn gemaakt, onjuist zijn gemarkeerd als aanhalingstekens voor aangemelde klanten.
* **MDVA-2946** (*voor Adobe Commerce >=2.3.3 &lt;=2.4.0*) - Hiermee wordt het probleem opgelost waarbij de prijs van de niet-toepasselijke verzendmethode tijdens het afrekenen als nul wordt weergegeven.
* **MDVA-30357** (*voor Adobe Commerce >=2.3.2 &lt;=2.4.0*) - Het probleem wordt verholpen met onjuiste afbeeldings-URL&#39;s die worden gemaakt bij het genereren van een sitemap door uitsnijden.
* **30565** (*voor Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - Hiermee wordt het probleem opgelost waarbij *Geen dergelijke entiteit met kartide = 0* de fout wordt getoond voor gastklant op winkelkassabon als het blijvende winkelwagentje wordt toegelaten.
* **MDVA-2978** (*voor Adobe Commerce >=2.3.0 &lt;=2.4.0*) - Hiermee wordt het probleem opgelost waarbij de doelregel voor verwante producten niet werkt wanneer *is een van* De voorwaarde wordt gebruikt om producten te bepalen die moeten worden getoond.
* **MDVA-3097** (*voor Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij willekeurige producten uit categorieën ontbreken na herindexering.
* **28202** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.2*) - Hiermee wordt het probleem verholpen waarbij Gelaagde navigatie configureerbare producten niet correct filtert wanneer MSI wordt gebruikt.
* **MDVA-2830** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem opgelost waarbij de GQL-aanvraag niet de prijswijzigingen uit de prijsregels voor catalogi weerspiegelt.
* **31006** (*voor Adobe Commerce >=2.3.2 &lt;=2.4.2*) - Hiermee wordt het probleem verholpen waarbij dubbele bestellingen worden weergegeven nadat een bestelling is geplaatst met [!DNL Paypal Express] betaling.

## v1.0.5 {#v1-0-5}

* **30841** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0.*) - Het probleem wordt verholpen met gelaagde navigatie, waarbij de *Nee* waarde voor productkenmerken van het booleaanse type is niet opgenomen in gelaagde navigatie als [!DNL Elasticsearch] is gebruikt als zoekprogramma.
* **MDVA-2819** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij geen betalingsmethoden worden geladen tijdens het maken van bestellingen via de beheerder.
* **MDVA-29959** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 met B2B-extensie*) - Het probleem waarbij een gebruiker met beperkte beheerdersrechten *Bedrijven* rechten mogen bedrijfsaccount niet verwijderen.
* **MDVA-30265** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij de link voor het volgen van verzending stopt met werken na het maken van de factuur.
* **28409** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0.*) - Hiermee wordt het probleem opgelost waarbij de `sales_clean_quotes` snijtaak mislukt met *onvoldoende geheugen* fout wanneer het aantal verlopen aanhalingstekens in de database enorm is.
* **30593** (*voor Adobe Commerce >=2.3.0 &lt;2.3.4*) - Hiermee wordt het probleem opgelost waarbij de prijsopgaven die zijn verlopen volgens de instelling voor de levensduur van het citaat, niet worden opgeschoond.
* **30107** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - Hiermee wordt het probleem verholpen waarbij de winkelswitch niet naar behoren functioneert als verschillende basis-URL&#39;s worden gebruikt voor de weergave van de winkel.
* **28763** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - Hiermee wordt het probleem verholpen waarbij de productafbeelding wordt gedupliceerd nadat de productinformatie met behulp van de REST API meermaals is bijgewerkt.
* **30284** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij de zoekindex voor catalogi mislukt als gevolg van het volgende: *[!DNL Elasticsearch]fout: limiet van totaal aantal velden in index is overschreden.*
* **MDVA-2904** (*voor Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 met B2B-extensie*) - Hiermee wordt het probleem verholpen waarbij catalogusmachtigingen zijn gewijzigd in *Toestaan* automatisch nadat een nieuw product aan de gedeelde catalogus is toegevoegd.
* **30428** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij klanten een product niet aan de verlanglijst kunnen toevoegen als dit product aan een aangepaste inventarisbron is toegewezen.
* **MDVA-2861** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2 met B2B-extensie*) - Hiermee wordt het probleem verholpen waarbij een fout wordt gegenereerd in de accountsectie voor bedrijfsgebruikers nadat bedrijfsbeheer is gewijzigd.

## v1.0.4 {#v1-0-4}

* **30195** (*voor Adobe Commerce 2.3.1 - 2.3.4-p2*) - Hiermee wordt het probleem verholpen waarbij snijtaken mislukken als de databasenaam te lang is, waardoor de categorieën niet op de voorgrond worden bijgewerkt.
* **30106** (*voor Adobe Commerce ^2.3.0*) - Hiermee wordt een probleem verholpen waarbij tijdens het afrekenen geen betalingen worden geladen *Kan eigenschap &#39;length&#39; van null niet lezen* fout in JS console.
* **28656** (*voor Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - Hiermee wordt het probleem opgelost dat als een bestelling zonder vereiste betalingsinformatie is geplaatst (bijvoorbeeld met korting van 100%) en er een factuur voor de bestelling is gemaakt, de status van de bestelling verandert in *Gesloten* in plaats van Voltooid.
* **30209** (*voor Adobe Commerce 2.3.0 - 2.3.3-p1*) - Hiermee wordt het probleem opgelost waarbij de klantengroep is gewijzigd in een standaardgroep als de klant zijn accountgegevens heeft bijgewerkt.
* **30123 MDVA** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij labels voor kenmerkopties niet correct worden vertaald voor GraphQL-query&#39;s.
* **MDVA-2996** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij de categoriepagina na het inschakelen van de categorietoestemming niet in de cache van volledige pagina wordt geplaatst.
* **30164 MDVA** (*voor Adobe Commerce >=2.3.1 &lt;2.4.2*) - Hiermee wordt het probleem verholpen waarbij klantenrecords niet uit het raster Klanten kunnen worden geëxporteerd als er aangepaste klantkenmerken zijn.
* **MDVA-3044** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij geen bevestigingsbericht wordt verzonden voor bestellingen die zijn geplaatst met GraphQL.
* **MDVA-30490** (*voor Adobe Commerce 2.3.4 - 2.3.5-p2*) - Hiermee wordt het probleem verholpen waarbij een productvergelijking de pagina met 500 fouten genereert als een van de producten een lege korte beschrijving heeft.
* **30232** (*voor Adobe Commerce >=2.3.1 &lt;2.4.1*) - Hiermee wordt het probleem verholpen waarbij het niet mogelijk is de bestelling opnieuw te bestellen als de oorspronkelijke bestelling een cadeaukaart bevat.
* **MDVA-2965** (*voor Adobe Commerce >=2.3.3 &lt;2.4.0*) - Hiermee wordt het probleem opgelost waarbij klanten een ongeldige fout krijgen bij het toevoegen van een product aan de winkelwagentje.
* **MDVA-3008** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - Het B2B-probleem is verholpen waarbij het niet mogelijk is via de Admin API orders te plaatsen voor een product dat zich in een openbare catalogus bevindt.
* **22469** (*voor Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - Hiermee wordt het probleem verholpen waarbij Page Builder na de upgrade naar Adobe Commerce 2.3.3 niet werkt in het deelvenster Beheer en sommige JS- en CSS-bestanden niet worden geladen.
* **MC-35984** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - Oplossing van de kwestie waar de handelaren niet met om het even welke paginaelementen op de pagina van Terugkeren konden interactie aangaan nadat het creëren van een verschepend etiket voor een Vergunning van de Terugkeer Merchandise (RMA).

## v1.0.3 {#v1-0-3}

* **25602** (*voor Adobe Commerce 2.3.0 - 2.3.4*) - Het probleem verholpen met [!DNL PayPal Payflow Pro] betalingsmethode en cookies behandelen als `SameSite=Lax` door gebrek in Chrome 80 browser en API reactie richt zich aan de klantenlogin pagina opnieuw.
* **MDVA-26694** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0.*) - Het probleem wordt verholpen met product- en cataloguscaches die dagelijks verlopen, maar volgens planning anders verlopen.
* **27825** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1*) - Het probleem waarbij het exporteren van grote hoeveelheden gegevens is mislukt als gevolg van een geheugenlek.
* **29085** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - Hiermee wordt het B2B-probleem verholpen waarbij geen vereiste e-mailberichten van nieuwe bedrijven worden verzonden als een bedrijf door de API wordt gemaakt.
* **MDVA-2934** (*voor Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - Hiermee wordt het probleem verholpen waarbij de Page Builder vastloopt nadat tekst van een koptekstelement naar een tekstelement is gekopieerd.
* **MDVA-2983** (*voor Adobe Commerce >2.3.1 &lt;2.4.2*) - Hiermee wordt het probleem opgelost waarbij in plaats van één kaartopdracht twee codes bevatte.
* **30052** (*voor Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - Het probleem is verholpen waarbij particuliere inhoud (lokale opslag) niet correct is ingevuld, wat tot prestatieproblemen heeft geleid.
* **30131** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0.*) - Het probleem wordt verholpen met gelaagde navigatie, waarbij de *Nee* waarde voor productkenmerken van het booleaanse type is niet opgenomen in gelaagde navigatie als [!DNL Elasticsearch] is gebruikt als zoekprogramma.
* **35514** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - Het probleem is opgelost door een verzendlabel te maken en geordende producten toe te voegen aan een pakket in het modale venster Pakketten maken.
