---
title: Opmerkingen bij de release
description: Meer informatie over de patches die beschikbaar zijn voor Adobe Commerce en de problemen die ze oplossen.
exl-id: 22262555-f5ea-49ad-98ad-ea8428ef66d5
source-git-commit: f10eb87efbda20899574486f1e9db01f2a66f855
workflow-type: tm+mt
source-wordcount: '22258'
ht-degree: 0%

---

# Opmerkingen bij de release

[[!DNL Quality Patches Tool] ](https://github.com/magento/quality-patches) levert individuele die flarden door Adobe en de gemeenschap van de Magento Open Source worden ontwikkeld. Hiermee kunt u algemene informatie over alle afzonderlijke patches die beschikbaar zijn voor de geïnstalleerde versie van Adobe Commerce, toepassen, herstellen en weergeven. U kunt patches toepassen op Adobe Commerce- en Magento Open Source-projecten, ongeacht wie de patch heeft ontwikkeld. U kunt bijvoorbeeld een patch toepassen die door de gemeenschap is ontwikkeld op Adobe Commerce-projecten.

>[!INFO]
>
>Zie [ flarden ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html#apply-individual-patches) voor instructies op het toepassen van flarden op uw projecten van Adobe Commerce toepassen. Zie [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de Gids van de Update van de Software om een volledige lijst van vrijgegeven flarden te herzien.

>[!INFO]
>
>Voor informatie over [!DNL quality patches] die door de Gemeenschap voor Magento Open Source wordt gecreeerd, zie de [ versienota&#39;s ](https://github.com/magento/quality-patches/blob/master/community-release-notes.md).

## v1.1.53 {#v1-1-53}

* **ACSD-48318** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost het probleem op waar het milieu het nesten van de wedijver niet wordt toegestaan. De emulatie begint tijdens de `send()` -aanroep zodra de emulatie stopt tijdens de `getInfoBlockHtml()` -aanroep.
* **ACSD-59930** (voor Adobe Commerce >=2.4.6 &lt;2.4.8) - verbetert prestaties van het bedrijf **[!UICONTROL Create]**, **[!UICONTROL Save]**, en **[!UICONTROL Delete]** stromen.
* **ACSD-60584** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar een toegangstoken die voor de gebruiker op één website wordt gecreeerd tot toegang heeft of klanteninformatie op andere websites verandert.
* **ACSD-60804** (voor Adobe Commerce >=2.4.4 &lt;2.4.8) - lost de kwestie op waar het uitgeven van een klant die met een geschrapt bedrijf wordt verbonden de fout *Vraag aan een lidfunctie `getSuperUserId()` op ongeldig* veroorzaakt.
* **ACSD-6113** (voor Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.8) - Hiermee wordt het probleem verholpen waarbij de `sales_clean_quotes` [!DNL cron] aanhalingstekens verwijdert van niet-goedgekeurde inkooporders.
* **ACSD-61528** (voor Adobe Commerce >=2.4.6 &lt;2.4.8) - lost de kwestie op waar het terugwinnen van rollen van [!UICONTROL Admin] gebruikend [!DNL GraphQL] geen resultaten terugkeert.
* **ACSD-61553** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost het probleem op waar **[!UICONTROL Cart Price Rule]** kortingen verkeerd worden berekend wanneer de veelvoudige kortingen met verschillende prioriteiten en **[!UICONTROL Maximum Qty Discount is Applied To]** worden toegepast op het product.
* **ACSD-61667** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.8) - verbetert inventarisprestaties voor het creëren van het verschepen in het geval van vele bronnen met in-store bestelwagen.
* **ACSD-61969** (voor Adobe Commerce >=2.4.7 &lt;2.4.8) - lost de kwestie op waar de gebruiker in een case-sensitive couponcode moet typen om precies te stemmen aangezien de couponcode werd gevormd.
* Bijgewerkte patches: ACSD-54989, ACSD-60632

## v1.1.52 {#v1-1-52}

* **BUNDLE-3375** (voor Adobe Commerce en Magento Open Source) - voegt alle noodzakelijke gebieden toe om de 3DS vereisten van het VISA mandaat te vervullen wanneer het gebruiken van [!DNL Braintree] als betalingsgateway.
* **ACSD-59366** (voor Adobe Commerce >=2.4.6 &lt;2.4.8) - lost de kwestie op waar een fout voorkomt wanneer het proberen om een team te schrappen dat gedeactiveerde gebruikers bevat die niet zichtbaar in de teamlijst zijn.
* **ACSD-59865** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar a [!UICONTROL Cart Price Rule] eerder toegepaste regels niet annuleert als de hoeveelheid van het product in het karretje niet genoeg voor de toe te passen regels is.
* **ACSD-59925** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.8) - lost de kwestie met sorterende punten in [!UICONTROL Media Gallery] door positie in GraphQL op.
* **ACSD-59952** (voor Adobe Commerce >=2.4.4 &lt;2.4.8) - lost de kwestie op waar een fout voorkomt wanneer het creëren van [!UICONTROL Shared Catalog] met een groepsidentiteitskaart die aan bestaand [!UICONTROL Shared Catalog] wordt toegewezen.
* **ACSD-60590** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - verbetert de prestaties van het produceren [!UICONTROL Bestsellers Aggregated Daily Reports] voor een groot volume van geplaatste orden.
* **ACSD-60673** (voor Adobe Commerce >=2.4.4 &lt;2.4.8) - lost de kwestie op waar [!UICONTROL Cart Price Rule] voor veelvoudige betalingsmethodes bij controle niet geschikt op de specifieke betalingsmethode van toepassing is.
* **ACSD-60684** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar het het productsorteren van GraphQL door veelvoudige gebieden niet zoals verwacht werkt.
* **ACSD-60788** (voor Adobe Commerce >=2.4.7 &lt;2.4.8) - lost de kwestie op waar de douanescripts voor [!DNL Google Tag Manager] niet wegens de fouten van het Veiligheidsbeleid van de Inhoud (CSP) worden uitgevoerd.
* **ACSD-61322** (voor Adobe Commerce >=2.4.6 &lt;2.4.8) - lost de kwestie op waar [!UICONTROL Products/Categories] niet toegewezen aan [!UICONTROL Shared Catalog] voor het Standaard (Algemene Groep) nog in de Sitemap van XML zijn.
* **ACSD-61366** (voor Adobe Commerce en Magento Open Source >=2.4.7 &lt;2.4.8) - lost de kwestie op waar het `setup:static-content:deploy --jobs 4` bevel met veelvoudige banen loopt die met de *Haven ontbreken moet binnen de fout van de gastheerparameter* worden gevormd wanneer de haven voor de verbinding van DB wordt gespecificeerd.
* Bijgewerkte patches: ACSD-51857, ACSD-57394

## v1.1.51 {#v1-1-51}

* **ACSD-59786** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.8) - lost de kwestie op waar GraphQL een interne serverfout wanneer het proberen om identiteitskaart van het Citaat voor een verlopen citaat te krijgen terugkeert.
* **ACSD-60234** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.8) - lost de kwestie op waar een onjuist bedrag op [!DNL PayPal] wordt getoond wanneer de korting door de betalingsmethode wordt toegepast.
* **ACSD-59967** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7-p2) - lost de kwestie op waar een fout van JavaScript [!DNL Google Maps] niet correct teruggeeft verhindert.
* **ACSD-60326** (voor Adobe Commerce >=2.4.4 &lt;2.4.8) - lost de kwestie op waar een fout op de vraag van GraphQL voor de status van de klantenterugkeer voorkomt.
* **ACSD-60538** (voor Adobe Commerce >=2.4.7 &lt;2.4.8) - lost de kwestie op waar als een product in *[!UICONTROL All Store Views]* gehandicapt is en slechts in specifieke werkingsgebied van de opslagmening wordt toegelaten, tonen de productattributen niet correct in de reactie van GraphQL, die tot het product leiden dat niet behoorlijk wordt getoond.
* **ACSD-60631** (voor Adobe Commerce en Magento Open Source >=2.4.7 &lt;2.4.8) - lost de kwestie op waar GraphQL een fout terugkeert wanneer het zelfde eenvoudige product aan veelvoudige configureerbare producten wordt toegewezen.
* **ACSD-60632** (voor Adobe Commerce en Magento Open Source >=2.4.5-p8 &lt;2.4.8) - lost de kwestie op waar een nieuw adres wordt bewaard telkens als een poging van de orderplaatsing wordt gemaakt, ongeacht of de orde met succes wordt gecreeerd of niet.
* **ACSD-60816** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar de [!DNL New Relic Browser Monitoring] manuscripten die door de agent APM worden ingespoten niet volgzaam met CSP (het Beleid van de Veiligheid van de Inhoud) zijn, verhinderend hun uitvoering.
* **ACSD-61195** (voor Adobe Commerce en Magento Open Source >=2.4.7 &lt;2.4.8) - lost de kwestie op waar geen wortelpunten op de laatste pagina voor het karretjeGraphQL verzoek zijn teruggekeerd.
* Bijgewerkte patches: ACSD-59378

## v1.1.50 {#v1-1-50}

* **ACSD-59280** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - lost de fout *Vraag aan undefined methode RefCollectionUnionType::getName ()* op die wanneer het installeren van 2.4.4-pX versies voorkomt.
* **ACSD-45049** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.4-p8 || >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij de kenmerkinstelling van een klant *[!UICONTROL Is required]* niet correct werkt volgens het bereik van de website in Admin.
* **ACSD-46938** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie met de prestaties van de trekkers van OB recreatie tijdens `setup:upgrade` op.
* **ACSD-48210** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar het bijwerken van een *[!UICONTROL Website Scope]* attribuut in een specifieke opslagmening de attributenwaarden in het globale werkingsgebied met voeten.
* **ACSD-5487** (voor Adobe Commerce en Magento Open Source >=2.4.4-p4 &lt;2.4.4-p9 || >=2.4.5-p3 &lt;2.4.5-p8 || >=2.4.6-p1 &lt;2.4.6-p6) - Hiermee wordt het probleem opgelost waarbij het winkelwagentje van de klant wordt gewist nadat de klantensessie is verlopen en [!UICONTROL Persistent Shopping Cart] ingeschakeld is.
* **ACSD-58141** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.8) - lost de kwestie op waar PHPSESSID op de verzoeken van de POST op het storefront gebied voor een het programma geopende klant regenereert als [!DNL L2 Redis cache] wordt toegelaten en de klant wordt bijgewerkt van Admin.
* **ACSD-58352** (voor Adobe Commerce >=2.4.4 &lt;2.4.7) - lost de kwestie op waar de etiketten van de terugkeerattributen voor de standaardarchiefmening via GraphQL API zijn teruggekeerd wanneer een niet-standaard opslagmening in de verzoekkopbal wordt gespecificeerd.
* **ACSD-58442** (voor Adobe Commerce >=2.4.4 &lt;2.4.7-p1) - lost de kwestie op waar de apparaten met een breedte van 768px als mobiel worden behandeld, veroorzakend het menu en de kopbal om in een mobiele mening in plaats van Desktop te laden.
* **ACSD-58790** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.8) - lost knijpfunctionaliteit aan gezoem op de beelden van de productdetailpagina in mobiele mening op [!DNL Chrome] op.
* **ACSD-59036** (voor Adobe Commerce en Magento Open Source >=2.4.7 &lt;2.4.8) - lost een uitzondering op die wanneer het laden van productprijzen met zowel lagere als hogere grenzen gelijk aan $0 gebeurt.
* **ACSD-59229** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar de op groep betrekking hebbende informatie van de klant in het verkeerde segment wegens de oude waarde van de x-Magento-variatie in verzoek wordt bewaard.
* **ACSD-59378** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost de kwestie op waar store-level URL tijdens de invoer verkeerd wordt bijgewerkt herschrijft.
* **ACSD-59514** (voor Adobe Commerce >=2.4.4 &lt;2.4.7-p2) - lost de kwestie op waar de vormen in het Admin gebied met [!DNL Page Builder] de fout *[!DNL Page Builder]teruggeven 5 seconden zonder lokken vrij te geven.* in de browserconsole na het verzenden van het formulier en wijzigingen kunnen niet worden opgeslagen.
* **ACSD-60303** (voor Adobe Commerce >=2.4.4-p9 &lt;2.4.5 || >=2.4.5-p8 &lt;2.4.6 || >=2.4.6-p6 &lt;2.4.8) - Hiermee wordt het probleem verholpen waarbij een bestelling van Admin niet kan worden geplaatst als HTML minificatie is ingeschakeld.
* **ACSD-60441** (voor Adobe Commerce en Magento Open Source 2.4.4-p9 || 2.4.5-p8 || 2.4.6-p6 || 2.4.7-p1) - Het probleem met het bijwerken van klanten via het `V1/customers` [!DNL REST API] -eindpunt wordt verholpen wanneer het token voor integratietoegang wordt gebruikt dat vanaf de achtergrond wordt gegenereerd.
* Bijgewerkte patches: ACSD-57003

## v1.1.49 {#v1-1-49}

* **ACSD-56979** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar de productbeelden na het schrappen van een het opvoeren update worden verwijderd.
* **ACSD-57086** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar de orden die van niet-standaard websites met toegelaten voorwaarden worden geplaatst niet correct worden verwerkt.
* **ACSD-57588** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar het verschepen van een orde aan veelvoudige adressen een fout tijdens de verwerking van gebiedsidentiteitskaart teweegbrengt.
* **ACSD-57643** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar de producten met douaneopties verkeerd aan het winkelwagentje via GraphQL worden toegevoegd.
* **ACSD-57846** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de producten van GraphQL met een filter voor nulprijzen zoeken geen resultaten toe te schrijven aan een uitzondering terugkeert.
* **ACSD-57941** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar de productopties verkeerd aan de admin opslag in plaats van hun respectieve opslag worden toegewezen.
* **ACSD-58375** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de verkeerde *[!DNL YouTube API Key]* configuratie een fout veroorzaakt wanneer het toevoegen van een [!DNL YouTube] video op het niveau van de archiefmening.
* **ACSD-58739** (voor Adobe Commerce en Magento Open Source >=2.4.7 &lt;2.4.8) - lost de kwestie op waar het gedeeltelijke opnieuw indexeren een fout veroorzaakt.
* **ACSD-58446** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost de kwestie op waar wanneer het schrappen van een team met kindgebruikers of teams ongeacht hun status (inactief), het systeem een uninformatief foutenmelding verstrekt niet verenigbaar met UI.
* **ACSD-58054** (voor Adobe Commerce >=2.4.4 &lt;2.4.6) - lost de kwestie op waar het mogelijk is om klantentekenen voor inactieve klanten via API te produceren.
* **ACSD-58163** (voor Adobe Commerce >=2.4.3 &lt;2.4.7) - lost de kwestie op waar a *[!UICONTROL Cart Price Rule]* geen korting voor een gastklant van de passende *[!UICONTROL Customer Segment]* kar zonder een couponcode toepast.
* **ACSD-57045** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost het probleem op waar URL herschrijft veroorzaken oneindige pagina het van een lus voorzien nadat *[!UICONTROL Website Root]* van *[!UICONTROL Hierarchy]* wordt ongecontroleerd.
* Bijgewerkte patches: ACSD-46815, ACSD-47027, ACSD-51683, ACSD-55031, ACSD-51819, ACSD-54965-v2

## v1.1.48 {#v1-1-48}

* **ACSD-55566** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar de `mergeCart` mutatie met &quot;*Interne Fout van de Server*&quot;in de [!DNL GraphQL] reactie wanneer het samenvoegen van bron en bestemmingshakken ontbreekt die de zelfde bundelpunten hebben.
* **ACSD-56546** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar configureerbare en bundelproducten als **uit Voorraad** op de opslagplaats tonen wanneer de **vertoning uit productconfiguratie** *Uitgeschakeld* is.
* **ACSD-56635** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost de kwestie op waar de ingevoerde klant met het zelfde e-mailadres wordt gedupliceerd, wanneer de invoer met **rekening wordt gebruikt delend** geplaatst aan *Globaal*.
* **ACSD-56741** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - bevestigt het foutenbericht &quot;*die probeert om tot seriecompensatie op waarde van type ongeldig*&quot;toegang te hebben die tijdens `setup:upgrade` toont wanneer het gegevensbestand een douane [!DNL MySQL] trekker niet verwant met het indexeringsmechanisme en [!DNL MView] bevat.
* **ACSD-57315** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op wanneer een nieuwe transactie in [!DNL PayPal Payflow Pro] wordt gecreeerd telkens als de [!UICONTROL Fetch] knoop op het **[!UICONTROL View transaction]** scherm in Admin wordt geklikt.
* **ACSD-57337** (voor Adobe Commerce >=2.4.4 &lt;2.4.6) - lost het probleem op waar een admin gebruiker met toegangsbeperkingen aan specifieke websites bedrijven van alle websites in het **[!UICONTROL Companies]** net kan zien.
* **ACSD-57394** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie van onjuiste productsortering door veelvoudige soortgebieden in [!DNL GraphQL] op.
* **ACSD-57565** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar het **[!UICONTROL Order]** dashboard onjuiste ordeinformatie toont tot de tijdspanne wordt bijgewerkt. Op het dashboard worden nu de juiste volgordestatistieken weergegeven bij de eerste keer laden.
* **ACSD-57854** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op wanneer de product [!DNL GraphQL] verzoeken gehandicapte categorieën in de categoriesamenvoegingen terugkwamen.
* **ACSD-58008** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de kwestie op waar het bijwerken van een geplande update de vorige versie van een gefaseerd punt verwijderde, als geen einddatum werd gespecificeerd.
* Bijgewerkte patches: MDVA-39305-V2, ACSD-48627, ACSD-54965

## v1.1.47 {#v1-1-47}

* **ACSD-55241** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar *[!UICONTROL Used]* en *[!UICONTROL Times Used]* attributen onjuiste waarden voor geproduceerde coupons tonen wanneer gebruikt tijdens controle met veelvoudige adressen.
* **ACSD-56760** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost de kwestie op waar een admin gebruiker die tot een specifieke website wordt beperkt geen nieuwe producten binnen een categorie kan sorteren of toevoegen voor het geval dat webstore zijn eigen wortelcategorie heeft.
* **ACSD-56858** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de B2B toestemmingen van de bedrijfrol verkeerd voor een beperkt bedrijf admin worden getoond.
* **ACSD-57074** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar *ja/Nr* douaneattribuut met `attrbute_code` die met `price_` beginnen niet behoorlijk met het indexeren werkt, en de producten met dergelijke attributen zijn niet beschikbaar op het vooreind.
* Bijgewerkte patches: ACSD-53378, ACSD-51819

## v1.1.46 {#v1-1-46}

* **ACSD-46767** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie op waar de het geheime voorgeheugen van de categoriepagina ongeldig maakt wanneer de voorraadhoeveelheid verandert, zelfs als het product nog in voorraad is.
* **ACSD-54656** (voor Adobe Commerce >=2.4.5 &lt;2.4.6) - lost de kwestie op waar onzichtbare Recaptcha tijdens controle ontbreekt, verhinderend een orde wordt geplaatst.
* **ACSD-55100** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost de kwestie op waar GraphQL niet meer dan 10k producten in de onderzoeksresultaten terugkeert.
* **ACSD-56621** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de bijgewerkte voornaam en achternaam niet in de sectie van de begroetingskopbal voor het bedrijf admin gebruiker worden weerspiegeld.
* **ACSD-56842** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de uitgestelde volmachten en de uitgestelde volmachtsfabrieken na het lopen `setup:di:compile` ontbreken.
* **ACSD-57003** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar de ordestatus in *[!UICONTROL Complete]* in plaats van wordt veranderd in *[!UICONTROL Processing]* wordt veranderd wanneer een orde gedeeltelijk wordt terugbetaald en gedeeltelijk verscheept.
* Bijgewerkte patches: ACSD-50260-v2, ACSD-54966

## v1.1.45 {#v1-1-45}

* **ACSD-56886** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar een configureerbaar product uit voorraad wordt wanneer één van twee kindproducten door een geplande update wordt onbruikbaar gemaakt.
* **ACSD-56616** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost de kwestie op waar de gebundelde producten zoals in voorraad op de opslagplaats tonen wanneer hun eenvoudige producten uit voorraad zijn.
* **ACSD-56515** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de beheerder met de toestemmingen van het websiteniveau geen dynamisch blok kan toevoegen of uitgeven.
* **ACSD-56447** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar het toevoegen van het zelfde product aan het karretje via parallelle het Web API verzoeken in twee afzonderlijke punten in het karretje resulteert.
* **ACSD-56415** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar de prestaties van gedeeltelijke prijs het indexeren wegens a `DELETE` vraag worden vertraagd wanneer het gegevensbestand veel gedeeltelijke prijsgegevens aan index heeft.
* **ACSD-54965** (voor Adobe Commerce >=2.4.5 &lt;2.4.6) - lost de kwestie op waar het Visuele het Merchandising net niet de correcte voorraad toont wanneer een product aan douanevoorraad slechts wordt toegewezen.
* **ACSD-52824** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de kwestie op waar de Uitdrukkelijke PayPal, Google Pay, en de Pay knopen van Apple voor bedrijfklanten worden getoond wanneer dergelijke betalingsmethodes in bedrijfmontages gehandicapt zijn.
* Bijgewerkte patches: ACSD-56193

## v1.1.4 {#v1-1-44}

* **ACSD-56790** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar een gebruiker aan het dashboard Admin wordt opnieuw gericht wanneer het sorteren van categorieproducten gebruikend de **Beweging uit Beeld aan bodem** optie en de `Invalid security or form key. Please refresh the page` fout verschijnt op het scherm.
* **ACSD-56280** (voor Adobe Commerce >=2.4.4 &lt;2.4.7) - lost de kwestie op waar het opdracht geven tot punten van een geschenkregister tot een uitzondering leidt.
* **ACSD-56246** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar het gegeven uit de douane multi-uitgezochte attributen wordt verwijderd wanneer een geplande update voor een product actief wordt.
* **ACSD-56193** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4) - lost de kwestie op waar het Vierige/Fastly geheime voorgeheugen niet wordt bijgewerkt wanneer een gepland blok in de categoriebeschrijving gebruikend de Bouwer van de Pagina wordt gebruikt.
* **ACSD-56158** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar de &quot;wortel&quot;vraag de totale belastingwaarde voor elke belastingregel terugkeert.
* **ACSD-56023** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de widgetinhoud niet op de pagina van CMS bijwerkt wanneer het geheime voorgeheugen wordt toegelaten.
* **ACSD-55427** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de kwestie op waar de admingebruiker niet een product van een gedeelde catalogus van de productpagina in Admin kan unassign.
* **ACSD-55352** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar na het creëren van een gedeeltelijk creditmemo met de punten van de klantenbeloning, de veranderingen van de ordestatus in Gesloten en de opties van het creditmemo van de Admin ordepagina verdwijnen.
* **ACSD-55231** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - lost de kwestie op waar u geen producten aan een karretje kunt toevoegen gebruikend de snelle ordefunctionaliteit.
* **ACSD-54283** (voor Adobe Commerce >=2.4.3 &lt;2.4.4) - lost de kwestie op waar de Producten/de Categorieën niet die aan de Gedeelde Catalogus voor Standaard (Algemene Groep) worden toegewezen nog in de Sitemap van XML worden omvat.
* Bijgewerkte patches: ACSD-52041, ACSD-54040, ACSD-51819

## v1.1.43 {#v1-1-43}

* **ACSD-54972** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar canonieke categorie URL niet na het veranderen van categorie URL bijwerkt.
* **ACSD-53636** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5) - lost de kwestie op waar de regelmatige prijs niet op de pagina&#39;s van de productlijst voor configureerbare producten wordt getoond die kindproducten met speciale prijzen hebben.
* **ACSD-54885** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie met de veelvoudige adrescontrole op wanneer de admin gebruiker de *login als functionaliteit van de Klant* gebruikt.
* **ACSD-55610** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar een gedeeltelijk geannuleerde orde een onjuist kortingsbedrag heeft.
* **ACSD-55334** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost vertalingen voor etiketten door Vertaalwoordenboeken in de reactie van GraphQL op.
* **ACSD-54739** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de kwestie op waar de voorwaarde van de productvoorraad niet voor verwante productregels wordt toegepast.
* **ACSD-53925** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar admin het blok van CMS met productcarrousel niet kan bewaren wanneer `catalog_product_price` afmetingen-wijze aan *website* wordt geplaatst.
* **ACSD-52714** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de datumfilter niet in het admin net werkt wanneer het datumformaat als *y-m-d* wordt geplaatst.
* **ACSD-55055** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - verbetert prestaties van ladende productkenmerken in de regels van de kartprijs in het winkelwagentje.
* **ACSD-53790** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost de kwestie op waar Meerdere RMAs voor één enkel product via REST API kan worden gecreeerd.
* **ACSD-56090** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5) - lost de kwestie op waar het verzoek van GraphQL met alle gegevens van opslag eerder dan de specifiek gevraagde opslaggegevens antwoordt.
* **ACSD-54983** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - lost de kwestie op waar het krijgen van het verzoek van de bedrijfgebruiker UID met GraphQL niet mogelijk is wanneer de gebruikersstatus aan *[!UICONTROL Inactive]* wordt geplaatst.
* **ACSD-53309** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de belasting niet volledig in het *[!UICONTROL Regular Price]* etiket wordt toegepast wanneer de klantgerichte optie wordt geselecteerd.
* **ACSD-55305** (voor Adobe Commerce >=2.4.4 &lt;2.4.7) - lost de kwestie op waar *[!UICONTROL Edit Company User]* popup op **[!UICONTROL myAccount]** > **[!UICONTROL Company Structure]** pagina met een lader op het scherm bevriest.
* Bijgewerkte patches: ACSD-49013

## v1.1.42 {#v1-1-42}

* **ACSD-53658** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar *[!UICONTROL Recently Viewed]* productgegevens niet behoorlijk in de archiefmening worden bijgewerkt.
* **ACSD-54626** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost de kwestie op waar u geen nieuwe regel van de inkooporde (`createPurchaseOrderApprovalRule`) met het `NUMBER_OF_SKUS` attribuut via [!DNL GraphQL] kunt tot stand brengen.
* **ACSD-53845** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de [!DNL MySQL] kwestie van de verbindingsonderbreking op wanneer `consumer max_messages` = 0.
* **ACSD-54890** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost het probleem op waar `aggregate_sales_report_bestsellers_data` [!DNL MySQL] fouten veroorzaakt toe te schrijven aan `/tmp` schijf die uit ruimte is.
* **ACSD-55112** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar de *[!UICONTROL Submit review]* knoop veelvoudige tijden zonder [!DNL Google reCAPTCHA v3] bevestiging kan worden geklikt.
* **ACSD-54264** (voor Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Het probleem waarbij het foutbericht *&quot;U kunt het gevraagde kenmerk niet bijwerken. Identiteitskaart van de rij: store_id&quot;* verschijnt wanneer een klant probeert om met een verhandelbaar citaat van een andere archiefmening uit te checken.
* **ACSD-54418** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar een vaste hoeveelheid korting verkeerd wordt toegepast op elk kindproduct van de dynamisch geprijsde bundel.
* **ACSD-55238** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - moeilijke situaties die het lege product *[!UICONTROL Meta Description]* bewaren.
* **ACSD-54966** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar een couponcode met beperkt-gebruik per klant niet kan worden opnieuw gebruikt als de vorige orde ontbrak.
* **ACSD-54060** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar beperkt admin geen product kan opslaan als het een kind van een ander product is dat aan een verschillend werkingsgebied wordt toegewezen.
* **ACSD-48910** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - Vaste de kwestie waar een bundelproduct dat aan veelvoudige bronnen wordt toegewezen uit-van-voorraad gaat nadat een orde wordt gefactureerd en verscheept, zelfs als het nog een hoeveelheid niet-nul heeft.
* **ACSD-55381** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - lost een interne serverfout op wanneer het vragen `configurable_product_option_uid` en `configurable_product_option_value_uid` gebieden van a [!DNL B2B] *[!UICONTROL Requisition list]* via [!DNL GraphQL].
* **ACSD-55628** (voor Adobe Commerce >=2.4.4-p2 &lt; 2.4.5) || >=2.4.5-p1 &lt; 2.4.6) - Hiermee wordt het uploaden van een bestand naar het bedrijfsregistratieformulier en het vervangen van een bestand voor een klantkenmerk in de winkel opgelost.
* Bijgewerkte patches: ACSD-51240, ACSD-51890, ACSD-53098

## v1.1.41 {#v1-1-41}

* **ACSD-54376** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - lost de kwestie op die in het winkelwagentje voorkomt wanneer een product uit de gedeelde catalogus wordt verwijderd nadat het reeds aan het karretje is toegevoegd.
* **ACSD-53722** (voor Adobe Commerce >=2.4.4 &lt;2.4.7) - lost de kwestie op waar de gebundelde prijsveranderingen van productopties in $0 wanneer geplande updates voor verschillende werkingsgebieden actief worden.
* **ACSD-53643** (voor Adobe Commerce >=2.4.3 &lt;2.4.7) - lost de kwestie op waar de orde een onjuist totaal heeft wanneer het plaatsen van een kooporder met gehandicapte of uit-van-voorraad producten. Als dit gebeurt, wordt de knop *[!UICONTROL Place Order]* voor dergelijke inkooporders verborgen.
* **ACSD-54067** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar een productvideo niet op een mobiel apparaat speelt.
* **ACSD-55414** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - verbetert prestaties wanneer MariaDB probeert om EAV entity_id van koord aan geheel te gieten.
* **ACSD-51819** (voor Adobe Commerce >=2.4.4 &lt;2.4.4-p4) - lost de kwestie op waar de veelvoudige orden met zelfde citaatidentiteitskaart kunnen worden geplaatst.
* **ACSD-53118** (voor Adobe Commerce >=2.4.0 &lt;2.4.7) - lost de kwestie op waar *[!UICONTROL Cart Price Rule]* wordt toegepast gebruikend couponcode terwijl het product een leeg attribuut heeft.
* **ACSD-54324** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de kwestie op waar het verzoek GraphQL requisition_lists pagineringsmontages niet overweegt en alle resultaten terugkeert.
* Bijgewerkte patches: MDVA-42855-v2

## v1.1.40 {#v1-1-40}

* **ACSD-54680** (voor Adobe Commerce >=2.4.0 &lt;2.4.6) - lost de kwestie op waar het niet mogelijk is om een B2B Citaat te verwerken dat voor een product met Veelvoudige Toegewezen Bronnen wordt voorgelegd.
* **ACSD-54040** (voor Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij het veld *[!UICONTROL Created]* leeg is in de volgorde waarin de B2B-modules zijn ingeschakeld.
* **ACSD-54319** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - lost de kwestie op waar de productprijs nul in het *[!UICONTROL Product in Cart]* rapport toont.
* **ACSD-53378** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - verbetert de tijd van de controlepagina voor klanten die grote adresboeken hebben.
* **ACSD-52657** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar minicart niet op de secundaire storeview wordt bijgewerkt, die subdomain gebruikt.
* **ACSD-53414** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost de kwestie op waar een beperkte admin gebruiker CMS pagina&#39;s buiten hun toestemmingswerkingsgebied kan zien.
* **ACSD-54472** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost de kwestie op waar de klanten van een verworpen bedrijf nog kunnen voor authentiek verklaren, en de klanten van een geblokkeerd en verworpen bedrijf nog orden kunnen plaatsen. De patch voegt extra validatie toe voor GraphQL-eindpunten.
* **ACSD-52801** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - voegt de optie toe om een gedeeltelijke gelijke te doen wanneer het zoeken naar producten in GraphQL.
* **ACSD-55004** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar de validator tijdens het uploaden van een de invoerdossier groter dan de waarde die in `php.ini` wordt gevormd vastloopt.
* **ACSD-54989** (voor Adobe Commerce >=2.4.4-p5 &lt;2.4.5 || >=2.4.5-p4 &lt;2.4.6 || >=2.4.6-p2 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een bedrijfsbeheerder geen order kan plaatsen wanneer *[!UICONTROL Enable Purchase Orders]* is ingesteld op *[!UICONTROL Yes]* en *[!UICONTROL Purchase Order]* op *[!UICONTROL No]* .
* **ACSD-54007** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de fout *op &quot;Undefined seriesleutel &quot;_scope&quot;* bij het invoeren van klantengegevens.
* **ACSD-55031** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost het *&quot;gemengde Type&quot;niet* fout tijdens compilatie nullable op.
* **ACSD-54961** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar een beperkte admin gebruiker niet de *status van het Overzicht van het Product* kan massaal bijwerken.
* **ACSD-55256** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar slechts het eerste beeld met succes in de beeldschuif wordt getoond.
* Bijgewerkte patches: ACSD-52041, ACSD-54106

## v1.1.39 {#v1-1-39}

* **ACSD-53704** (voor Adobe Commerce >=2.4.0 &lt;2.4.7) - lost de kwestie op waar de geschiedenis van de beloningspunten na beloningspunten na afloop verkeerd wordt berekend.
* **ACSD-53583** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - verbetert gedeeltelijke herindexprestaties voor *Producten van de Categorie* en *de indexen van de Categorieën van het Product*.
* **ACSD-54026** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost een onjuist foutenmelding voor een `updateCompanyRole` verzoek van GraphQL voor een niet-geautoriseerde gebruiker op.
* **ACSD-54106** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5) - lost de kwestie op waar de sortering van het categorieproduct door naam voor Turkse geaccentueerde karakters onjuist is.
* **ACSD-52219** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar de Admin grids bewaarde filters niet zoals verwacht wanneer vaak het schakelen tussen referenties.
* **ACSD-54342** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost een onjuiste foutenmelding *Fout in gegevensstructuur op: de waarden zijn gemengd* wanneer het invoeren van een Csv- dossier zonder geldige gegevens.
* **ACSD-54660** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - voegde een nieuwe soort van inputattributen ** toe om klantenorden in GraphQL door `sort_field` en `sort_direction` te sorteren.
* **ACSD-54776** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de kwestie op waar niet gecontroleerd *[!UICONTROL Use Default Value]* en niet-standaard productgebiedwaarden niet voor de tweede website, opslag, en opslagmening worden bewaard.
* **ACSD-53998** (voor Adobe Commerce en Magento Open Source >=2.4.4-p2 &lt;2.4.5 || >=2.4.5-p1 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij een **[!UICONTROL Dynamic Block]** op basis van een **[!UICONTROL Customer Segment]** niet correct werkt nadat u zich hebt afgemeld bij een klantenaccount.
* **ACSD-53204** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - Vast *het product kan niet worden bewaard.* fout bij het gelijktijdig indienen van aanvragen om afbeeldingen toe te voegen aan de productgalerie met behulp van het `rest/V1/products/<sku>/media` -eindpunt.
* **ACSD-47657** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - voegde een caching mechanisme voor de geloofsbrieven van AWS toe. Een geloofsbrieven leverancier gebruikt nu het geheime voorgeheugen van het Magento aan geheim voorgeheugengeloofsbrieven die van AWS voor configuratie EC2 worden teruggewonnen.
* Bijgewerkte patches: ACSD-51984, ACSD-51574.

## v1.1.38 {#v1-1-38}

* **ACSD-53098** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4) - lost de kwestie op waar de producten die aan een gedeelde catalogus worden toegewezen niet op de storefront verschijnen wanneer een gedeeltelijke index wordt uitgevoerd.
* **ACSD-54018** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - lost de prestatieskwesties met [!UICONTROL Product List] widget op die een niet-globaal attribuut in de widgetvoorwaarde gebruikt.
* **ACSD-54111** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - lost de kwestie op waar de beelden van de productduimnagel niet op de opslagruimte worden getoond wanneer de aspectverhouding van het watermerkbeeld niet het productbeeld aanpast.
* **ACSD-47669** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - de schending van de de beperkingsbeperking van de Integriteit van Vormen *: 1452 kan een kindrij toevoegen of bijwerken: een buitenlandse zeer belangrijke beperking ontbreekt* fout wanneer het invoeren van producten CSV.
* **ACSD-53347** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de prijsindexeerder teveel tijd vergt uit te voeren.
* **ACSD-52287** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie met onjuiste ordestatus in het gearchiveerde orderaster op wanneer het asynchrone net indexeren wordt toegelaten.
* **ACSD-52929** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie met overtollige verzoeken op om bronpunten opnieuw in gebreke te stellen wanneer de inventarisindexeerder op async wijze wordt gevormd.
* **ACSD-53824** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar `UpdateMultiselectAttributesBackendTypes` het flard van migratiegegevens de grens van de grootte van de gegevensbestandtransactie tijdens `setup:upgrade` overschrijdt.

## v1.1.37 {#v1-1-37}

* **ACSD-52613** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar de geheime voorgeheugens en de indexen worden verfrist zelfs wanneer geen updates aan `Inventory_source` punten door REST API worden gemaakt.
* **ACSD-51884** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar het de geheim voorgeheugenweg van het productbeeld na het in werking stellen van resize bevel onjuist wordt.
* **ACSD-53628** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar het CSV rapport van de verkooporde onjuiste speciale karakters toont.
* **ACSD-53148** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar twee parallelle verzoeken in GraphQL om het zelfde configureerbare product aan het karretje toe te voegen in twee afzonderlijke punten op het karretje met zelfde product SKU resulteerde.
* **ACSD-52606** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar het foutenbericht *Uw orde niet klaar voor bestelwagen* wordt getoond wanneer de gebruiker **[!UICONTROL Notify Order is Ready for Pickup]** klikt.
* **ACSD-51574** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar het beeld niet op het vooreind na het vervangen van het met een ander beeld met de zelfde naam wordt bijgewerkt.
* **ACSD-53728** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de product EAV indexeer langer duurt om te voltooien.
* **ACSD-53979** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op JS die op de homepage voorkomt als het welkomstbericht één enkel citaat bevat.
* **ACSD-52085** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar een configureerbaar product met een speciale prijs niet in de carrousel van het product zichtbaar is.
* **ACSD-53795** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie met ongeldig gegevenstype in `indexer_update_all_views` kroonbaan op.
* **ACSD-52143** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar de douaneopties na productinvoer worden verwijderd.
* **ACSD-53750** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de *Verbroken pijp of gesloten verbindingsfout* tijdens multi-threaded `catalog_product_price` herdex op.
* **ACSD-49843** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de koppeling bij het downloaden van het product niet beschikbaar is nadat het geordende item automatisch via een online betalingsmethode is aangeroepen met de instelling **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]** ingeschakeld.
* **ACSD-47054** (voor Adobe Commerce >=2.4.2 &lt;2.4.6) - lost de kwestie op waar de voorproefherindexloopherindex voor alle opslag, veroorzakend vertraging in werking stelt.
* Nieuwe versies toegevoegd voor ACSD-46541, ACSD-47079.
* ACSD-49970-v3 vervangen door ACSD-54095.

## v1.1.36 {#v1-1-36}

* **ACSD-53239** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt; 2.4.6) - lost de kwestie op waar de inventarisindexeerder alle geheime voorgeheugens in Update op de wijze van het Programma ontruimt.
* **ACSD-50887** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar het bezit van het productattribuut *[!UICONTROL Use in Search Results Layered Navigation]* aan *ja* zonder de *[!UICONTROL Use in search]* optie kan worden geplaatst die aan *ja* wordt geplaatst.
* **ACSD-51846** (voor Adobe Commerce en Magento Open Source >=2.4.3-p2 &lt;2.4.6) - lost de *Interne fout* kwestie op die gebeurt omdat niet alle niveaus van REST API nuttige lading worden bevestigd.
* **ACSD-52906** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie op waar het x-Magento-Vary koekje verkeerd voor het programma geopende klanten wordt geplaatst die tot het zelfde klantensegment behoren die onjuiste caching voor sommige pagina&#39;s veroorzaken.
* **ACSD-52736** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - lost de kwestie op waar de Regel van de Prijs van de Kar van de a ** die vereisten voor configureerbare producthoeveelheid omvat niet zoals verwacht werkt.
* **ACSD-47875** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de admingebruikers geen product aan een klantenkar van Admin voor een bepaald werkingsgebied van de opslagmening met voorraadbeheer kunnen toevoegen.
* **ACSD-53176** (voor Adobe Commerce >=2.3.7 &lt;2.4.5) - lost de kwestie op waar *de Verwante Regel van het Product* met *één van* voorwaarde geen producten aanpast.
* **ACSD-51666** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de fout *op de zitting is verlopen, gelieve login opnieuw.* die plaatsvindt nadat een klant zich heeft aangemeld.
* Nieuwe versies toegevoegd voor MDVA-39305-v2.
* Bijgewerkte eisen voor ACSD-19640.

## v1.1.35 {#v1-1-35}

* **ACSD-51899** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar het standaardverzendadres op de controle verschepende stap auto-bevolkt met een eerder geselecteerd in-store besteladres is.
* **ACSD-52041** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar het foutenbericht: *[FOUT ] [!DNL Page Builder] het teruggeven voor 5 seconden zonder sloten vrij te geven.* wordt weergegeven in de Chrome-browser wanneer u inhoud opslaat die is bewerkt met [!DNL Page Builder] .
* **ACSD-52095** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - lost de kwestie op waar de `manage_stock` waarde verkeerd aan 0 in het Csv- dossier na productuitvoer werd geplaatst.
* **ACSD-51358** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de kwestie op waar het verwijderen van een geplande update zonder een einddatum tot het verwijderen van andere geplande updates voor de zelfde entiteit leidt.
* **ACSD-48070** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie op waar het uitgeven van een geplande update een uitzondering teweegbrengt.
* **ACSD-51890** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar de [!UICONTROL Submit review] knoop veelvoudige tijden zonder [!DNL Google reCAPTCHA] v3 bevestiging kan worden geklikt.
* **ACSD-51984** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de kwestie op waar niet gecontroleerde *[!UICONTROL Use Default Value]* en *[!UICONTROL non-default product field]* waarden niet voor de tweede website, opslag, en opslagmening worden bewaard.
* **ACSD-52398** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de fout *op de gevraagde hoeveelheid is niet beschikbaar* die wanneer het proberen om de hoeveelheid een gebundeld product in de kar op de storefront bij te werken voorkomt.
* **ACSD-52786** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost de kwestie op waar een voorwaarde van de catalogusregel *SKU* op alle producten van toepassing is die met bepaalde SKU beginnen.
* **ACSD-52921** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar een interne fout voorkomt als het verzoeken van worteldetails van GraphQL wanneer er een uit-van-voorraad configureerbaar product in de kar is.
* **ACSD-51683** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar een klantgerichte optie niet aan het karretje kan worden toegevoegd gebruikend GraphQL.
* **ACSD-52133** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar een klantenrekening niet na een verbetering kan worden bewaard.
* **ACSD-52202** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar de verkoopbare hoeveelheid standaardvoorraad verkeerd in 0 verandert wanneer een non-default voorraad in 0 qty op bestelling wordt veranderd.
* **ACSD-51265** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie met `catalog_product_price` opnieuw indexerende prestaties op wanneer er teveel gebundelde producten in het systeem zijn.
* **ACSD-52831** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de klanten geen verhandelbare citaatorden kunnen plaatsen wanneer [!DNL Google reCAPTCHA v3 Invisible] wordt toegelaten.
* **ACSD-51845** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar de verdere producten met laagprijzen en verschillende attributenreeksen niet via asynchrone bulkREST API kunnen worden bijgewerkt.
* **ACSD-52815** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de input voor het kwantitatieve gebied van een niet-standaardbron slechts tot 6 cijfers steunt, in tegenstelling tot 8 voor een standaardvoorraad.
* **ACSD-51149** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie op waar Gepland ImportExport met toegelaten de Toestemmingen van de Catalogus indexen ongeldig maakt en dan flushes door cron in het voorgeheugen opneemt.
* **ACSD-50815** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost de kwestie op waar de decimale hoeveelheid voor een eenvoudig product niet voor een nieuwe Gebundelde productoptie kan worden gebruikt.
* Bijgewerkte versies voor ACSD-47803.
* Bijgewerkte titel voor ACSD-51892.
* ACSD-51379 bijgewerkt.
* ACSD-49970-v2 bijgewerkt.

## v1.1.34 {#v1-1-34}

* **ACSD-52277** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar een admin gebruiker niet behoorlijk na het selecteren van een opslagmening wanneer het creëren van een nieuwe orde in Admin wordt opnieuw gericht.
* **ACSD-50813** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - verhelpt de kwestie waar Admin niet gebundelde producten kon toevoegen die een schuine streep in SKU met de [!UICONTROL Add Products by SKU] functionaliteit aan de adminorde bevatten.
* **ACSD-51630** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar een grote hoeveelheid systeemberichten het downloaden van admin pagina&#39;s vertraagt.
* **ACSD-51853** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.7) - lost de kwestie op waar de gekopieerde tekststijlen niet wanneer het gebruiken van [!UICONTROL Page Builder] worden toegepast.
* **ACSD-52160** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar het resultaat van de productbevestiging tegen de regel van de kartprijs niet behoorlijk werd geëvalueerd gebaseerd op de regelvoorwaarde &quot;als een punt in het karretje wordt GEVONDEN/NIET wordt GEVONDEN met Al/om het even welk van deze voorwaarden waar&quot;.
* **ACSD-51636** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de kwestie op waar het bedrijfbeheerder nieuwe gebruikers van de sectie van de klantenrekening ondanks het hebben van alle noodzakelijke rollen en toestemmingen niet kan toevoegen.
* **ACSD-51739** (voor Adobe Commerce >=2.4.6 &lt;2.4.7) - lost de kwestie op waar een fout is teruggekeerd wanneer `structure_id` in een verzoek van GraphQL CompanyTeam wordt gevraagd.
* **ACSD-51857** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar de langzame prestaties van het `aggregate_sales_report_bestsellers_data` bouwrapport over grote sales_order en `sales_order_item` gegevensbestandlijsten toe te schrijven waren aan de manier de belangrijkste gegevensvraag werd geschreven.
* **ACSD-48448** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar er een kwestie van de rasvoorwaarde die tijdens de orde annuleert gebeurt, die een gedupliceerde ingang in de `inventory_reservation` lijst veroorzaakt.
* **ACSD-52689** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.6) - lost de kwestie op waar de beelden niet aan de opslag van Amazon S3 gebruikend REST API kunnen worden geupload.
* **B2B-2674** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - voeg caching vermogen aan de 1customAttributeMetadata1 GraphQL vraag toe.
* Nieuwe versies toegevoegd voor ACSD-44938.
* Toegevoegde eisen voor ACSD-46988.

## v1.1.3 {#v1-1-33}

* **ACSD-50478** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5) - lost het gegevensbestand terugschroeven bevel voor een geval wanneer de stortplaats van DB trekkers en a *delimiter* SQL bevel bevat.
* **ACSD-50512** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - lost de *Fout op: De downloadbare verbinding is niet verwant met het product. Controleer de koppeling en probeer het opnieuw.* fout die optreedt bij het bijwerken van de begindatum voor een downloadbare update voor productplaatsing.
* **ACSD-50949** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar het prijsfilter in Geavanceerd onderzoek geen juiste resultaten wanneer gebruikt langs de filter van SKU terugkeert.
* **ACSD-51645** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de geworpen fout op wanneer het bewaren van een nieuwe Regel van de Prijs van het Kart als de uitbreiding `Magento_OfflineShipping` gehandicapt is.
* **ACSD-50895** (voor Adobe Commerce >=2.4.5 &lt;2.4.7) - verhelpt de kwestie waar [!DNL Google Analytics] 3 GTM markeringen niet in brand worden gestoken als [!DNL Google Analytics] 4 GTM niet wordt gevormd.
* **ACSD-51102** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - lost de kwestie op waar een catalogusregel die op een groot aantal producten wordt toegepast niet correct wordt geïndexeerd wanneer de regel door een geplande update wordt toegelaten.
* **ACSD-50368** (voor Adobe Commerce en Magento Open Source >= 2.4.3 &lt;2.4.5) - lost het probleem op waar de klant `group_id` wordt genegeerd wanneer een klant via Async REST API of Async Bulk REST API wordt gecreeerd.
* **ACSD-51497** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij een klant een cataloguspagina niet kan sorteren op Aangepast kenmerk van het vervolgkeuzetype.
* **ACSD-51408** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt; 2.4.7) - lost de kwestie op waar de status van het ordepunt verkeerd aan *[!UICONTROL Backordered]* wordt geplaatst.
* **ACSD-51735** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - lost de kwestie op waar de status van het ordepunt verkeerd aan *[!UICONTROL Ordered]* wordt geplaatst wanneer het productdossier *0* is.
* **ACSD-51792** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost de kwestie op waar een pagina niet de imperiagebeurtenis heeft wanneer [!DNL Google Tag Manager] 4 wordt toegelaten.
* **ACSD-51471** (voor Adobe Commerce >=2.4.3 &lt;2.4.7) - lost de kwestie op waar een admin gebruiker geen geplande update voor een gebundeld product kan bewaren dat een eenvoudig product gebruikt dat zelf een geplande update heeft.
* **ACSD-51700** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de fout op die wanneer het schakelen archiefmeningen over een downloadbaar product uitgeeft pagina in admin gebeurt.
* **ACSD-51120** (voor Adobe Commerce >=2.3.7 &lt;2.4.3) - lost de kwestie op waar de de verzoekgeheime voorgeheugen van de GET van GraphQL niet voor de pagina&#39;s van CMS wordt ontruimd die de blokken van CMS bevatten die via een het opvoeren update worden bijgewerkt.
* **ACSD-51240** (voor Adobe Commerce >=2.4.4 &lt;2.4.6) - lost de kwestie op waar het geüploade dossier mist als de registratie via de vorm van de bedrijfregistratie wordt gedaan.
* **ACSD-51907** (voor Adobe Commerce >=2.4.2 &lt;2.4.3) - lost de kwestie op waar een beperkte admin gebruiker geen creditnota met een off-line terugbetaling kan tot stand brengen.
* **ACSD-52148** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4) - lost de kwestie op waar [!DNL Google V3 reCAPTCHA] login Admin af en toe ontbreekt.
* **ACSD-51431** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar een indexeerstatus ** werkt zelfs als er geen nieuwe ingangen in het kanaal zijn.
* **ACSD-51892** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de prestatieskwestie op waar de configdossiers veelvoudige tijden laden.
* Vervangen ACSD-51114.

## v1.1.32 {#v1-1-32}

* **ACSD-49628** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de [!UICONTROL Page Builder's] veelvoudige fouten admin verhinderen een product zonder inhoudstoestemmingen op te slaan.
* **ACSD-51305** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar de uit-van-voorraad configureerbare kindproducten niet in de reactie van GraphQL beschikbaar zijn.
* **ACSD-50621** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost het probleem op waar [!UICONTROL Tier Prices] voor verschillende websites in de gedeelde catalogus niet zichtbaar zijn wanneer het proberen om hen in een multi-websitemilieu uit te geven.
* **ACSD-51041** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.0 || >=2.4.1 &lt;2.4.6) - verbetert de prestaties van de prijsindexer.
* **ACSD-51379** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de veranderingen die aan de inhoud van de paginatekst via [!UICONTROL Page Builder] worden aangebracht niet worden bewaard.
* **ACSD-49480** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie op waar slechts één de prijsregel van de karretje op het karretje wordt toegepast.
* **ACSD-51230** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de rekening van de cadeaukaart wordt geschrapt wanneer een gedeeltelijke teruggave van een eenvoudig product van een orde wordt verwerkt.
* **ACSD-51238** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - lost de kwestie op waar de inventarisbron wordt verwijderd wanneer het bijwerken van configureerbare producten en het uitgeven van de prijs.
* **ACSD-50794** (voor Adobe Commerce >=2.4.1 &lt;2.4.7) - lost de kwestie op waar het geschenkbericht of de geschenkompdetails niet in het gegevensbestand wanneer het verwijderen van het door GraphQL worden bijgewerkt.
* **ACSD-51528** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar de *x_door:sturen_for* kolom ongeldige waarden in de *sales_order* lijst heeft.
* **ACSD-50849** (voor Adobe Commerce >=2.4.4 &lt;2.4.6) - lost de kwestie op waar het toevoegen van een nieuw product aan de categorie na het ontruimen van het geheime voorgeheugen in een wanverhouding van posities en selecties van de bestaande producten resulteert.
* **ACSD-51294** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost het probleem op waar de prijs GTM/GA, hoeveelheid, belasting, verscheping, en opbrengst als koord aan [!DNL Google Analytics] en GTM worden verzonden.
* **ACSD-51204** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar een volledig verkocht product niet terug in voorraad na het creëren van een creditmemo terugkeert.
* **ACSD-51291** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.4-p4 || >=2.4.5 &lt;2.4.5-p3) - Hiermee wordt het probleem opgelost waarbij beperkte beheerders met toegang tot één website afbeeldingen/video&#39;s kunnen toevoegen aan het product dat aan meerdere websites is toegewezen.
* Nieuwe versies toegevoegd voor ACSD-50336.
* Vervangen patches ACSD-49970.

## v1.1.31 {#v1-1-31}

* **ACSD-50345** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4 || >=2.4.4-p1 &lt;2.4.6) - Hiermee wordt het probleem verholpen waarbij Recaptcha v2 niet opnieuw laadt na het verzenden van een mislukte betaling.
* **ACSD-50817** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - optimaliseert de baan van het Gewas `sales_clean_quotes` om sneller te lopen.
* **ACSD-49392** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.0 || >= 2.4.1 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij de status van de order verandert in een gesloten order na een gedeeltelijke terugbetaling voor een gebundeld product.
* **ACSD-51036** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - lost de kwestie op waar de rasvoorwaarden tijdens gezamenlijke vraag REST API in een overlapping van de informatie van de verzendstatus in de [!UICONTROL Items Ordered] lijst resulteren.
* **ACSD-50858** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - verbetert prestaties voor het laden van banners inhoud.
* Nieuwe versies toegevoegd voor MDVA-39305-v2, ACSD-45169.
* Bijgewerkte patches ACSD-50260-v2.

## v1.1.30 {#v1-1-30}

* **ACSD-50336** (voor Adobe Commerce en Magento Open Source >=2.4.4-p1 &lt;2.4.4-p3) - lost de kwestie op waar de e-mails van het productalarm niet worden verzonden wanneer een product terug in voorraad is of de prijs wordt veranderd.
* **ACSD-50367** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de de uitvoer van het klantenadres niet werkt wanneer een multi-uitgezochte attribuut van het klantenadres zonder waarden wordt gecreeerd.
* **ACSD-49877** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar video autoplay niet op mobiel [!DNL Safari] werkt wanneer de video direct met een ver videodossier en niet de het stromen dienst wordt verbonden.
* **ACSD-50165** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de fout *op het dossier kan niet worden geschrapt. Waarschuwing!unlink: Geen dergelijk bestand of deze map* wanneer JS/CSS-cache wordt leeggemaakt van de Admin.
* **ACSD-49737** (voor Adobe Commerce en Magento Open Source >=2.4.1-p1 &lt;2.4.7) - lost de kwestie op waar een coupon verkeerd zoals gebruikt na een ontbroken kaartbetaling wordt gemerkt.
* **ACSD-50814** (voor Adobe Commerce en Magento Open Source >=2.4.6 &lt;2.4.7) - lost de kwestie op waar een admin gebruiker geen creditnota kan tot stand brengen.
* **ACSD-50116** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar een admin gebruiker geen URL kan tot stand brengen herschrijft voor subcategorieniveau 3 of lager.
* **ACSD-49513** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5) - lost de kwestie op waar de verre opslagsynchronisatie wegens 0 bytedossiers ontbreekt.
* **ACSD-46683** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de het verschepen prijs *nog niet berekend* toont.
* **ACSD-49129** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - lost de kwestie op waar het *[!UICONTROL content]* attribuut (basis64 beeldcode) niet in `rest/V1/products/sku/media` de antwoorden van de productmedia API wordt teruggekeerd.
* **ACSD-50276** (voor Adobe Commerce >=2.4.0 &lt;2.4.7) - lost de kwestie op waar de vorm van de klantenregistratie niet aan de opslagront werkt als een multi-uitgezochte klantenattribuut wordt gecreeerd.
* **ACSD-50527** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de fout op die voorkomt wanneer het bewaren van een pagina met een leeg dynamisch blok.
* **ACSD-49973** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - verbetert prestaties van het halen van gebundelde producten door GraphQL.
* **ACSD-51114** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar een willekeurig product uit grote catalogi verdwijnt wanneer het asynchrone indexeren wordt toegelaten. Verbetert de prestaties van asynchrone herindexering voor grote catalogi.
* **B2B-2598** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.7) - voeg caching vermogen aan [!UICONTROL availableStores] toe, [!UICONTROL countries], [!UICONTROL country], [!UICONTROL currency], en [!UICONTROL storeConfig] vragen van GraphQL.
* Nieuwe versies toegevoegd voor MDVA-42806, ACSD-48627, ACSD-46815.
* Bijgewerkte patches, metagegevens voor ACSD-49773, ACSD-47179, ACSD-48300.

## v1.1.29 {#v1-1-29}

* **ACSD-49389** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.7) - lost de kwestie op waar een klaar-aan-opnamee-mail door API wordt verzonden wanneer de orde niet klaar voor bestelwagen is.
* **ACSD-49822** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de updates in de [!UICONTROL Requisition List] pagina niet op [!UICONTROL Print Requisition List] worden weerspiegeld.
* **ACSD-48771** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie met de bevordering van het kolom-blok inhoudstype van oudere [!DNL Page Builder] versies op.
* **ACSD-49464** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de facturen, de verzendingen, en de creditmemo&#39;s niet van het archief worden verplaatst wanneer orderId verschillend is.
* **ACSD-49773** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - lost de kwestie op waar de productuitvoer ontbreekt wanneer AWS S3 als verre opslag wordt gebruikt.
* **ACSD-49748** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de uitnodigingen niet kunnen worden verzonden.
* **ACSD-49502** (voor Adobe Commerce >=2.4.3 &lt;2.4.7) - lost de kwestie op waar de downloadbare verbinding niet behoorlijk wordt bijgewerkt nadat een het opvoeren update op het downloadbare product wordt toegepast.
* **ACSD-49527** (voor Adobe Commerce >=2.4.2 &lt;2.4.7) - lost de kwestie op waar de het bedrijfrollen van GraphQL paginering niet correct tonen.
* **ACSD-49706** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de standaardwaarde voor een visueel staalattribuut wordt bewaard wanneer geen waarde wordt geselecteerd.
* **ACSD-49835** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar de waarde van de standaard controledoos van het Gebruik niet correct op een opslagniveau voor een multi-uitgezochte attribuut wordt bewaard.
* **ACSD-49898** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie op waar het productnet een uitzondering werpt wanneer een gebundeld product een speciale prijs heeft die 1000 overschrijdt.
* **ACSD-50234** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.5) - lost de kwestie met de verkeerde klantennaam in bevestigingse-mail op als het plaatsen van een orde met [!DNL PayPal].
* **ACSD-49960** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost het probleem op waar het filtreren door datum niet voor het net van de klantenorde werkt.
* **ACSD-49849** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - lost de kwestie op waar de klantene-mail door [!DNL PayPal] e-mail werd vervangen toen het plaatsen van een orde met [!DNL PayPal Express] via GraphQL.
* **ACSD-49839** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost het probleem op waar de Gedeelde Prijsbepaling en de structuur van de Catalogus een fout in Admin veroorzaakt wanneer de producten enige of dubbele citaten in SKU hebben.
* **ACSD-49970** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost onjuiste behandeling van de fouten van GraphQL op wanneer [!DNL New Relic] het melden wordt aangezet.
* **ACSD-50260** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost het probleem op waar de resultaten van het het productonderzoek van GraphQL tot 10.000 slechts resultaten beperkt zijn.
* **ACSD-48813** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar het onderzoek relevante resultaten niet toont die op het onderzoeksgewicht van de attributen worden gebaseerd.

## v1.1.28 {#v1-1-28}

* **ACSD-48204** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.3) - lost de kwestie op waar een regel van de catalogusprijs die op Ja/Geen attributen wordt gecreeerd niet het geselecteerde werkingsgebied overweegt.
* **ACSD-47704** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar het gebundelde product de prijs van in voorraadproducten slechts toont.
* **ACSD-49370** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar het *3} productattribuut van de Tijd van de Datum a* FilterMatchTypeInput *type in het schema van GraphQL heeft.*
* **ACSD-48807** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.7) - lost de kwestie op waar de Revisies van het Product van de klant niet door storeview via GraphQL worden gefiltreerd.
* **ACSD-49433** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar het standaardbedrag als subtotaal in het karretje voor geschenkkaart met een open bedrag wordt getoond.
* **ACSD-48866** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar een fout voorkomt wanneer het verzoeken van RSS voer voor categorieën.
* **ACSD-48784** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de prijzen van het klantensegment verkeerd caching tussen klantengroepen zijn.
* **ACSD-48857** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar een gebruiker veranderingen na het uitgeven met de Bouwer van de Pagina niet kan bewaren.
* **ACSD-49065** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de citaatpunten niet zichtbaar in Admin als slechts toegewezen aan het douanedossier zijn.
* **ACSD-49179** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar het Rapport van Orden onjuiste bedragen in het geval van verschillende valuta&#39;s voor verschillende opslag toont.
* **ACSD-49286** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar een product tweemaal aan een kar wordt toegevoegd wanneer de veelvoudige productwidgets op de pagina aanwezig zijn.
* **ACSD-49574** (voor Adobe Commerce >=2.4.4 &lt;2.4.7) - voegt functionaliteit toe om het productupdates van de Kaart van de Kaart in een kar via GraphQL te steunen.
* Bijgewerkte patch: ACSD-48694.

## v1.1.27 {#v1-1-27}

* **ACSD-48362** (voor Adobe Commerce >=2.4.1 &lt;2.4.7) - lost de kwestie op waar het standaard verschepende adres in plaats van nieuwe wordt gebruikt wanneer het plaatsen van een orde gebruikend een verhandelbaar citaat.
* **ACSD-48059** (voor Adobe Commerce >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de handelaren &quot;[!UICONTROL Match product by rule]&quot;in de categorie niet kunnen opslaan.
* **ACSD-48216** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Hiermee wordt het probleem opgelost waarbij [!UICONTROL AUTO_INCREMENT] van de [!UICONTROL inventory_source_item] -tabel groter wordt dan de [!UICONTROL UPDATE] -bewerking.
* **ACSD-47908** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.0 &lt;2.4.7) - Hiermee wordt de fout &quot;Er wordt een waarde kleiner dan of gelijk aan 0 verwacht&quot; bij het selecteren van de bron en hoeveelheid in de verzendstap tijdens het uitchecken.
* **ACSD-49497** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - lost de kwestie op waar een orde in de verwerkingsstaat na verzending blijft en een gedeeltelijke terugbetaling wordt toegepast.
* **ACSD-48694** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.3.8 || >=2.4.1 &lt;2.4.7) - Hiermee wordt het probleem verholpen waarbij de fout &quot;Ongeldige statuswijziging aangevraagd&quot; een klant belet een order te plaatsen.
* **ACSD-49013** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.7) - lost de kwestie op waar de e-mailbevestiging niet aan de Webscène wanneer het creëren van klanten gebruikend bulk API wordt vertaald.
* **ACSD-48164** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar beperkt admin geen website-vlakke waarde kan bewaren.
* **ACSD-48404** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4) - lost de kwestie op waar &quot;Herinner de Paginering van de Categorie = ja&quot;een fout veroorzaakt wanneer het drukken van de browser achterknoop.
* **ACSD-48634** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost JS fouten op een het opvoeren updatepagina op wanneer &quot;[!UICONTROL Google Analytics Content Experiments]&quot;wordt toegelaten.
* **ACSD-49042** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - lost de kwestie op waar een product met oneindige backorder niet van de Storefront kan worden bevolen.
* Bijgewerkte patches: ACSD-48366, ACSD-48661.

## v1.1.26 {#v1-1-26}

* **ACSD-47937** (voor Adobe Commerce en Magento Open Source 2.4.4 || >=2.4.5 &lt;2.4.6) - Hiermee wordt het probleem opgelost waarbij meldingen voor prijsdalingen niet altijd worden verzonden vanwege caching op toepassingsniveau.
* **ACSD-48661** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar als de de kredietgrens van het bedrijf groter is dan 999, het kommascheidingsteken het sparen van het bedrijf wegens een bevestigingsfout verhindert.
* **ACSD-48773** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.7) - lost de kwestie op waar het e-mailmalplaatje van bonuspunten van de verkeerde opslag wordt genomen.
* **ACSD-48587** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.7) - lost de kwestie op waar de speciale karakters van de HTML in de producten widget passende regels hen verhinderen passende producten te tonen.
* **ACSD-48212** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - lost de kwestie op waar de productinvoer het product aan de verkeerde bron toewijst.
* **ACSD-47988** (voor Adobe Commerce en Magento Open Source >=2.3.7 &lt;2.4.6) - lost de kwestie op waar de de uitvoer van het product HTML markeringen van de paginabouwer productbeschrijving bijsnijdt.
* **ACSD-48366** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie op waar het productbeeld niet op de Achter aan het malplaatje van de e-mail van de Beeld wordt getoond.
* **ACSD-48417** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.7) - lost de kwestie op waar een SQL fout na het creëren van een programmaverandering voor een product verschijnt en het opslaan van een ander product verschijnt.

## v1.1.25 {#v1-1-25}

* **ACSD-48058** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost de kwestie op waar de de prijsherdex van het product niet werkt als het bundelproduct niet aan om het even welke website wordt toegewezen.
* **ACSD-48262** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost de kwestie op waar de producten niet op het vooreind zichtbaar zijn wanneer &quot;Alle Producten per Pagina&quot;plaatsen ja toestaan wordt geplaatst.
* **ACSD-48293** (voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4) - lost de kwestie op waar de samengestelde producten uit voorraad gaan wanneer de kindproducten die uit werden verkocht aan voorraad worden teruggekeerd.
* **ACSD-47520** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar de klanten beloningspunten verliezen wanneer een creditnota wordt gecreeerd.
* **ACSD-48044** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4) - lost de kwestie op waar het toepassen van veelvoudige geschenkkaarten op één enkele orde met multi-verschepen orders verhindert worden geplaatst.
* **ACSD-48300** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar een terugkeer niet kan worden gecreeerd als het configureerbare product wordt verwijderd.
* **ACSD-47910** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie van ontbrekende orden, facturen, verzendingen, en creditnota&#39;s in respectieve entiteitennetten op.
* **ACSD-47292** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie op waar de uit-van-voorraad gebundelde producten niet in de reactie van GraphQL beschikbaar zijn als &quot;show uit-van-voorraad producten&quot;aan ja wordt geplaatst.
* **ACSD-48234** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost de kwestie op waar het resultaat van het catalogusonderzoek een onjuiste telling van het categoriepunt toont wanneer de &quot;show uit voorraad&quot;optie wordt toegelaten.
* **ACSD-48313** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5) - lost de kwestie op waar de kolom &quot;configurable_variation&quot;niet wordt ontleed als de attributenwaarde een komma bevat. Hetzelfde parseringsalgoritme wordt gebruikt voor &quot;additional_attributes.
* **ACSD-48627** (voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6) - lost de kwestie op waar het uit-van-voorraad configureerbare product een fout veroorzaakt wanneer het verzenden van een verzoek van GraphQL om worteldetails te krijgen.
* Bijgewerkte patch: MDVA-39384.

## v1.1.24 {#v1-1-24}

* **ACSD-45168** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - lost de kwestie op waar SEO-vriendelijke URLs niet voor producten worden geproduceerd die *url_key* attributen hebben die op store-view niveau worden met voeten getreden.
* **ACSD-46865** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie op waar het net van het Memo van de Verzending en van het Krediet niet bevolkt is wanneer het asynchrone indexeren wordt toegelaten.
* **ACSD-47004** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - lost de kwestie op waar de BTW niet op een factureringsadres zonder een identiteitskaart van de BTW wordt toegepast.
* **ACSD-47803** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar de uit-van-voorraad configureerbare productmonsters zoals beschikbaar worden getoond.
* **ACSD-47137** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - verbetert de ladingssnelheid van de beeldgalerij wanneer de pub/media omslag zeer groot is.
* **ACSD-46770** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar de admin orde e-mails worden verzonden zelfs wanneer de *bevestiging van de E-mailorde* wordt ongecontroleerd.
* **ACSD-47955** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie op waar GraphQL de wortelkorting niet correct toont.
* **ACSD-46617** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar *verdergaat aan Checkout* knoop uit grijs is zelfs als subtotal groter is dan het gevormde *Minimale Bedrag van de Orde*.
* **ACSD-47079** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5) - lost de kwestie op waar de samengestelde producten (bundel, gegroepeerd, en configureerbaar) voorraadstatus niet worden bijgewerkt wanneer de status van de voorraad van het subproduct via de POST /rest/V1/voorraad/bron-punten van REST API verandert.
* **ACSD-47336** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - de Oplossingen *ging het Iets fout.* fout bij het negeren van meldingen in Commerce Admin.
* **ACSD-47559** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar het gebied van het Malplaatje van de Voorproef E-mail niet volledig zichtbaar is.
* **ACSD-47920** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar de orden via Rest API als gastgebruiker kunnen worden geplaatst zelfs wanneer *GastControle* wordt uitgezet toestaat.
* Vervangen patches: MDVA-39305, MDVA-42855.

## v1.1.23 {#v1-1-23}

* **ACSD-47179** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar een beheerder met beperkte toegang tot een specifiek werkingsgebied productoverzichten niet kan schrappen.
* **ACSD-47107** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5) - lost de kwestie op waar de korting van de Regel van de Prijs van de Catalogus op de opties van het douaneproduct wordt toegepast.
* **ACSD-47232** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar de coupons met totaal gewicht niet in Admin kunnen worden toegepast.
* **ACSD-46519** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.6) - lost de kwestie op waar het GraphQL categoryList- verzoek een onjuiste product_count voor een ankercategorie terugkeert.
* **ACSD-47027** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - lost een langzaam updateCompanyRole GraphQL verzoek op.
* **ACSD-47666** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar de filterfunctie niet in Admin > Systeem > Toestemmingen > de rollen van de Gebruiker > een rol > het net van de Gebruikers van de Rol werkt.
* **ACSD-47497** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar het lusje van de Diensten niet zichtbaar in de Configuratie onder Admin is.
* Bijgewerkte patch: ACSD-47743.
* Vervangen patches: MDVA-42807.

## v1.1.22 {#v1-1-22}

* **ACSD-47444** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.3) - bevestigt _Poging om tot seriecompensatie op waarde van type bool_ fout toegang te hebben wanneer het toegang tot van bepaalde niet-bestaande categoriepaden voor bekende producten op PHP 7.4.
* **ACSD-47332** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar de mengeling met een fout ontbreekt die slechts wanneer het lopen tussen 00:00 en 00:59 UTC wordt gemeld.
* **ACSD-47280** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar het onbruikbaar maken van de gedeelde cataloguseigenschap op een specifiek werkingsgebied niet correct werkt.
* **ACSD-47106** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie op waar een waarde niet in een nieuw douaneattribuut op een pagina van de bedrijfverwezenlijking kan worden bewaard.
* Bijgewerkte patch: ACSD-45143.

## v1.1.21 {#v1-1-21}

* **ACSD-46809** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6) - lost de kwestie op waar een gebruiker een fout krijgt wanneer het toewijzen van een groot aantal productbronnen.
* **ACSD-46856** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - verbetert prestaties het bijwerken laagprijzen via Systeem > Configuratie > de Invoer > Geavanceerde Prijsbepaling.
* **ACSD-46541** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4) - lost de kwestie op waar een admin gebruiker geen creditnota kan tot stand brengen als een orderpunt wordt geschrapt.
* **ACSD-46581** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar het geschatte belastingtotaal niet na het selecteren van een land in het winkelwagentje wordt bijgewerkt.
* **ACSD-46618** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar de widget van de productlijst onjuiste caching prijzen voor een het programma geopende klant toont.
* **ACSD-46674** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - lost de kwestie op waar de douaneopties van een beeldtype als HTML in klantene-mails worden getoond.
* **ACSD-46988** (voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6) - lost de kwestie op waar het &quot;valuta&quot;API Verzoek van GraphQL ONGELDIGE waarden voor een douanemunt terugkeert.
* **ACSD-47076** (voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5) - lost de kwestie op waar de video&#39;s van Vimeo niet op de storefront kunnen worden gespeeld.
* **ACSD-45071** (voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4) - lost de kwestie op waar de standaardbron aan het product tijdens de invoer wordt toegevoegd.
* **AC-3023** (voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6) - de regeling van DHL van de Update aan recentste versie 10.0.
* Bijgewerkte patches: MDVA-42584.
* Vervangen patches: MDVA-36572, ACSD-45241.

## v1.1.20 {#v1-1-20}

* **ACSD-46520** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5*) - lost de kwestie op waar een gebruiker een onjuiste ordestatus wanneer teruggegeven gebruikend het opslagkrediet krijgt.
* **ACSD-46703** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6*) - lost de kwestie op waar het niet mogelijk is om douaneopties op een product te slepen en te laten vallen uitgeven pagina.
* **ACSD-44851** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6*) - lost de kwestie op waar een categorie met subcategorieën niet kan openen of uitbreiden.
* **ACSD-46815** (*voor Adobe Commerce en Magento Open Source >=2.4.5 &lt;2.4.6*) - lost de kwestie op waar het verzoek van de categorieboom tot 20 categorieën wordt beperkt.
* **ACSD-45675** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.6*) - lost de kwestie op waar de de uitvoer van het product categorienamen van de *StandaardMening van de Opslag* werkingsgebied gebruikt.
* **ACSD-46869** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.6*) - lost de kwestie op waar een configureerbaar product in een kar niet via a *PUT REST API* verzoek zonder de producthoeveelheid te veranderen wordt bijgewerkt.
* **mDVA-42768-v2** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - lost de kwestie op waar het Configurable product regelmatige prijs als *0* toont wanneer *de Vertoning uit-van-voorraad* ja ** is.
* Bijgewerkte patches: MDVA-44562, ACSD-46213, MDVA-41305, MDVA-38346, MDVA-13203.
* Vervangen pleister: MDVA-42768.

## v1.1.19 {#v1-1-19}

* **ACSD-46213** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - lost de kwestie op waar het verzoek van de categorieboom tot 20 categorieën wordt beperkt.
* **ACSD-45781** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.2*) - lost de kwestie op waar het gebied van de archiefvooronderzoek niet op mobiel wordt getoond.
* **ACSD-46192** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;2.4.5*) - lost de kwestie met het gebruiken van het `async/bulk/V1/configurable-products/bySku/options` eindpunt op.
* **ACSD-46404** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5*) - lost de kwestie op waar een admin gebruiker zich na bevordering aan 2.4.4 niet kan aanmelden.
* Bijgewerkte patches: MDVA-41305, MDVA-38626, MDVA-38728, MDVA-41061-V4, MDVA-42269, MDVA-39305.

## v1.1.18 {#v1-1-18}

* **ACSD-45817** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar een het productmutatie van GraphQL voor een specifieke opslag alle configureerbare varianten, met inbegrip van die terugkeert die niet aan de gevraagde opslag worden toegewezen.
* **ACSD-46146** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.6*) - lost de kwestie op waar twee e-mails van de ordesbevestiging na het plaatsen van een orde van Admin worden verzonden.
* **ACSD-45255** (*voor Adobe Commerce >=2.4.3 &lt;2.4.6*) - lost een uitzondering op de Lage pagina van het Rapport van de Voorraad voor een beperkte admin gebruiker op.
* **ACSD-45488** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.6*) - lost de kwestie op waar een configureerbaar product met veelvoudige bronnen niet automatisch aan In Voorraad wordt teruggekeerd.
* **ACSD-45754** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.6*) - lost de kwestie op waar de Punten van de Terugkeer niet na het toepassen van een coupon op de kar worden toegevoegd.
* **ACSD-45849** (*voor Adobe Commerce >=2.4.3 &lt;2.4.4*) - lost de kwestie op waar de videometa-gegevens worden verloren nadat een het opvoeren update wordt toegepast.
* **ACSD-45257** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.4*) - lost de kwestie op waar GraphQL geen wortelkorting correct toont.
* **ACSD-44938** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4*) - lost de kwestie op waar `VAT_ID` niet in een verzoek van GraphQL voor een gastgebruiker kan worden toegepast.
* Bijgewerkte patches: MDVA-43417.

## v1.1.17 {#v1-1-17}

* **ACSD-45241** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.4*) - lost de kwestie op waar de voorraadhoeveelheid voor een virtueel product na het creëren van een creditnota verkeerd wordt berekend.
* **ACSD-43887** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - lost de kwestie op waar de onjuiste details op de pagina van de controlebetaling worden getoond wanneer de Orden van de Aankoop voor bedrijven worden toegelaten.
* **ACSD-45143** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5*) - lost de kwestie op waar de `setShippingAddressesOnCart` mutatie het plaatsen van numerieke gebiedcode als *gebied* niet toestaat.
* **ACSD-44591** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.6*) - lost de fout op die voorkomt wanneer een orde zonder bevestiging CAPTCHA wordt geplaatst.
* **ACSD-45520** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.6*) - lost de kwestie op waar de staalopties niet vooraf op de pagina van het productdetail worden geselecteerd wanneer een gebruiker configureerbare producten van het winkelwagentje uitgeeft.
* **ACSD-45169** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.6*) - lost de kwestie op waar [!DNL Visual Merchandiser] niet de correcte voorraad en de prijs voor een configureerbaar product toont nadat een het opvoeren update wordt toegepast.
* **ACSD-45424** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.6*) - lost de kwestie op waar een onjuiste reserveringscompensatie na een gedeeltelijke terugbetaling (creditmemo) wordt gecreeerd.
* **MDVA-42807** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.6*) - lost de kwestie op waar het teken van de douanemunt niet op de archiefvoorzijde wordt getoond.
* Bijgewerkte patches: MDVA-42689, AC-3022.

## v1.1.16 {#v1-1-16}

* **mDVA-44703** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - lost de kwestie op waar de ordertotalen in het rapport van Orden verkeerd voor de beperkte admin gebruiker worden berekend.
* **mDVA-44940** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - lost de SQL fout op die terwijl het bewaren van de categorie van Admin voorkomt.
* **mDVA-44562** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.2-p2*) - lost de kwestie op waar niet-standaard opslag identiteitskaart voor citaatpunten door standaard opslagidentiteitskaart wordt met voeten getreden, ondanks het verzoek van GraphQL voortkomend uit de niet-gebrek opslagmening.
* **mDVA-43167** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar de de massa van het admin ordaster geen actie voor multi-pagina van toepassing is wanneer de admin gebruiker alle orden selecteert.
* **MDVA-44044** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.2-p2*) - lost de kwestie op waar een product niet op de categoriepagina wordt getoond nadat het aan een nieuwe website wordt toegewezen.
* **MDVA-42509** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.4*) - lost de kwestie op waar CSV niet voor een snelle orde kon worden geupload die in *resulteert Onbekwaam om de koekjesfout* te verzenden.
* Bijgewerkte patches: MDVA-41061, MDVA-42584.
* Het voorvoegsel voor de nieuwe [!DNL Quality Patches Tool] flarden zal van *MDVA* in *ACSD* wegens interne procesveranderingen worden veranderd.

## v1.1.15 {#v1-1-15}

* **MDVA-40961** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - lost de kwestie op waar een extra punt niet aan het karretje kan worden toegevoegd wanneer de minimumhoeveelheid van het punt reeds in de kar is.
* **mDVA-44887** (*voor Adobe Commerce en Magento Open Source >=2.4.4 &lt;2.4.5*) - bevestigt *Uncaught SyntaxError: Onverwachte symbolische &quot;const&quot;* fout in het Admin paneel.
* **mDVA-43718** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - Vast *de consument wordt niet gemachtigd om tot %resources toegang te hebben.* -fout die wordt weergegeven wanneer u een gedeelde catalogus opent vanuit een aangepaste integratie.
* **mDVA-44660** (*voor Adobe Commerce en Magento Open Source >=2.4.2-p1 &lt;2.4.5*) - lost de kwestie op waar het graf accentkarakter ``` ` ``` niet voor de voornaam en achternaam van een klant kon worden gebruikt.
* **mvdr-40896** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - lost *Fout op: TypeError: Argument 3 die tot Magento* fout in async product bulkAPI wordt overgegaan.
* **MDVA-38559** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.3*) - lost */V1/klanten/onderzoek API* fout voor klanten met meer dan één abonnement op.
* **mDVA-44533** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.4*) - lost de kwestie op waar de korting verkeerd op een product van het bundelkind wordt toegepast.
* Bijgewerkte patches: MDVA-41061, MDVA-42269.

## v1.1.14 {#v1-1-14}

* **mDVA-43983** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - lost de kwestie op waar de producten *niet afzonderlijk* nog in de Resultaten van het Onderzoek van de Catalogus Geavanceerd verschijnen.
* **MDVA-44100** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - lost de kwestie op waar alle FPTs aan het laatste product in het winkelwagentje en teruggesteld voor andere producten worden toegewezen.
* **mDVA-43605** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.5*) - lost de kwestie op waar de ordegegevens negatieve waarden voor rijtotalen terugkeren wanneer het gebruiken van Rest API.
* **mDVA-43102** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;2.4.5*) - lost de kwestie op waar het verkoopbare aantal niet correct wordt bijgewerkt wanneer een restitutie via REST API wordt gedaan.
* **mDVA-43178** (*voor Adobe Commerce en Magento Open Source >=2.4.3-p2 &lt;2.4.5*) - lost de kwestie op waar een klantenteken voor een douaneopslag niet in GraphQL kan worden teruggewonnen.
* **mDVA-43859** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - lost de kwestie op waar de fout *Geen dergelijke entiteit met customerId =* wordt geregistreerd wanneer een geschrapte klant probeert om binnen te registreren.
* **mDVA-44147** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - lost de kwestie op waar een verzoek van GraphQL niet de Lijsten van de Verzoek terugkeert.
* **mDVA-44505** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.3*) - lost de kwesties op waar GraphQL die de Punten van de Terugkeer toepast het Grote Totaal niet bijwerkt en waar de opslagkredieten veelvoudige tijden tijdens de ordeplaatsing worden toegepast.
* Bijgewerkte patches: MDVA-29148, MDVA-36464-V5, MDVA-42584, MDVA-3993-V2.

## v1.1.13 {#v1-1-13}

* **mDVA-42969** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.3*) - lost de kwestie op waar de Verwante Regel van het Product slechts werkt wanneer het Segment van de Klant aan *allen* wordt geplaatst.
* **MDVA-39605** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.5*) - lost de kwestie op waar Redis geheim voorgeheugen TTL (vervaldatum) een verkeerde waarde heeft.
* **mvdr-43862** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.5*) - lost de kwestie op waar de klant geen wortelpunten wegens een GraphQL *UpdateCartItems mutatie* fout kan bijwerken.
* **mDVA-43824** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p3 || >=2.4.1 &lt;2.4.5*) - Hiermee wordt het probleem verholpen waarbij een fout optreedt bij het annuleren van bestellingen met een korting.
* **MDVA-43451** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - lost de kwestie op waar de fout *de opslag die werd gevraagd niet werd gevonden. Controleer de winkel en probeer het opnieuw.* wordt weergegeven tijdens het configureren van een gedeelde catalogus voor een specifieke website.
* **mDVA-43491** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.5*) - lost de kwestie op waar het etiket van het basisbeeld niet wanneer het invoeren van producten voor een multi-opslagwebsite bijwerkt.
* **mDVA-43601** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie met ontbrekende trekkers na volledige herdex op.
* **MDVA-42046** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.3.5-p2 || >=2.4.0 &lt;2.4.5*) - Hiermee wordt het probleem opgelost waarbij een onjuiste waarde wordt toegewezen aan een productkenmerk met een datuminvoerveld tijdens het bijwerken van een product.
* **MDVA-43935** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - lost de kwestie op waar het Upsell product tweemaal wordt getoond.
* **MDVA-44188** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - lost de kwestie op waar de systeem-uitgegeven e-mail met `.-` in adressen niet wordt verzonden.
* **MDVA-42283** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar het datum-tijdformaat in het netwerk van de adminorde voor de Franse scène ongeldig is.
* Bijgewerkte patches: MDVA-41061-V2, MDVA-36309, MDVA-30862, MDVA-39713.
* Metagegevens van patches zijn toegevoegd voor de [!DNL Site-Wide Analysis Tool] .

## v1.1.12 {#v1-1-12}

* **mDVA-39713** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.3.6*) - lost de kwestie op waar de gebruiker de begintijd voor een actieve geplande update kan uitgeven.
* **MDVA-42410** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar de couponrapporten slechts de standaardbasismunt tonen.
* **mDVA-41136** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar de vervaldatum van `mage-cache-sessid` niet wordt uitgebreid, resulterend in de schoonmaak van klantengegevens.
* **mDVA-39993** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;=2.3.7-p2 || >=2.4.0 &lt;2.4.4*) - Hiermee wordt het probleem verholpen waarbij inventariswijzigingen die via de API zijn doorgevoerd, niet op de productpagina aan de voorzijde worden doorgevoerd.
* **MDVA-42855** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - lost de kwestie op waar een nieuw klantenadres niet aan het adresboek tijdens controle wordt bewaard.
* **MDVA-42645** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - lost de kwestie op waar Admin geen beloningspunten kan terugbetalen als de functionaliteit van het opslagkrediet wordt onbruikbaar gemaakt.
* **mDVA-43414** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2*) - lost de PHP fatale fout op die wanneer het runnen van de `inventory.reservations.updateSalabilityStatus` rijconsument op numerieke SKUs voorkomt.
* **mDVA-41628** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.5*) - lost de kwestie op waar de bestaande beperkte admin gebruikers toegang tot de nieuwe middelen krijgen wanneer de nieuwe modules worden toegevoegd.
* **mDVA-43348** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - lost de kwestie op waar het verzoek van de kaartjeGraphQL een fout toont als `gift_card_options` *uid* bevat.
* **MDVA-39546** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar de begindatum voor het opvoeren van update aan een vroegere datum dan de huidige datum tijdens het uitgeven kon worden geplaatst.
* **MDVA-42950** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar de video&#39;s niet op de productpagina spelen.
* **mvdr-42689** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op waar Adobe Commerce een *fout van de Schending van de Intentiegrens van de Intensiteit* terwijl het bijwerken van productcategorieën tijdens de invoer werpt.
* **mvdr-41229** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar de beelden beschikbaar op het achtereind niet op het vooreind na configureerbare producten de invoer tonen.
* **mDVA-43731** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - lost de kwestie op waar *Synoniemen van het Onderzoek* niet meer werkt wanneer de waarde in *MinimumTermen wordt toegevoegd om* aan te passen.
* **mDVA-43232** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.5*) - lost de kwestie op waar het sorteren van producten in [!DNL Visual Merchandiser] door Speciale Prijs aan Onder/Bovenkant veroorzaakt een fout terwijl het bewaren van de categorie.
* **mDVA-43726** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.3*) - lost de kwestie op waar de de prijsregel van de Catalogus die op store-level kenmerkgelijke wordt gebaseerd niet na gedeeltelijke herdex van toepassing is.
* Bijgewerkte patches: MDVA-36464, MDVA-37478, MDVA-38608.
* Metagegevens van patches zijn toegevoegd voor de [!DNL Site-Wide Analysis Tool] .

## v1.1.11 {#v1-1-11}

* **mDVA-42790** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - lost de kwestie op waar de attributen van de productprijs niet voor een specifieke website via REST API kunnen worden bijgewerkt.
* **mDVA-41350** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar een uitzondering wordt geworpen wanneer een admin gebruiker met beperkte toegang een product buiten hun rolwerkingsgebied door SKU in een orde toevoegt.
* **mDVA-42269** (*voor Adobe Commerce en Magento Open Source >=2.4.3-p1 &lt;2.4.5*) - lost de kwestie op waar een admin gebruiker zich niet bij Admin wegens *TypeError kan aanmelden: strtotime () verwacht parameter 1 om koord te zijn, ongeldig gegeven* fout.
* **mDVA-40830** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar het opslagkrediet veelvoudige tijden tijdens ordeplaatsing wordt toegepast.
* **mDVA-42237** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - lost de kwestie op waar een configureerbare product speciale prijs niet na veranderingen in zijn subproductprijs wordt bijgewerkt.
* **mDVA-42520** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - lost de kwestie op waar het belastingtarief tweemaal wordt toegepast als *grensoverschrijdende handel* toelaat wordt gebruikt.
* Bijgewerkte patches: MDVA-27239, MDVA-39305, MDVA-41236, MDVA-36832.
* Vervangen pleister: MDVA-37725.

## v1.1.10 {#v1-1-10}

* **mDVA-38728** (*voor Adobe Commerce en Magento Open Source >=2.3.2 &lt;2.4.5*) - lost de kwestie op waar de update van het massakarakter URL creeert herschrijft voor StandaardOpslag slechts na het veranderen van *het zicht van het Product*.
* **mDVA-43091** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - lost de kwestie op waar het opdracht geven tot van een bundelproduct van Admin in het achtereind de fout *geeft u geen decimale hoeveelheid voor dit product* kunt gebruiken.
* **MDVA-40816** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar de verwante productregels producten van categorieën tonen die niet in de regelvoorwaarden worden bepaald.
* **mDVA-41305** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.5*) - lost de kwestie op waar de mutatie van GraphQL geen configureerbare productopties na het toevoegen van het aan de wenslijst terugkeert.
* **MDVA-39181** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - lost de kwestie op waar de verwante productregels producten van categorieën tonen die niet in de regelvoorwaarden worden bepaald.
* **MDVA-42584** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - lost de kwestie op waar configureerbare voorraadstatus in het achterste deel niet na veranderende hoeveelheid en voorraadstatus via de Invoer of API wordt bijgewerkt.
* **MDVA-40175** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.3*) - lost de kwestie op waar *klikken om het verschepen methode te veranderen* geen radioknopen toont om het verschepen methodes in Admin tijdens reorder te selecteren.
* **mDVA-42768** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.5*) - lost de kwestie op waar het Configurable product regelmatige prijs als 0 toont wanneer *de Vertoning uit-van-voorraad* ja is.
* **mDVA-43201** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar een fout in klantenlogin wanneer het gebruiken van DOB attributen met bepaalde scènes voorkomt.
* Bijgewerkte patches: MDVA-35092, MDVA-33970.

## v1.1.9 {#v1-1-9}

* **mDVA-38346** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.5*) - lost de kwestie op waar de datumfilters niet behoorlijk werken wanneer de tijdzone van Adobe Commerce van lokale milieu timezone verschillend is.
* **mDVA-42657** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - lost de kwestie op waar de admin gebruiker niet categorieën in de voorwaarden van het klantensegment kan selecteren.
* **MDVA-42806** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar a *Nieuwe bedrijfregistratie* e-mail wordt verzonden telkens als een bestaand bedrijf via REST API wordt bijgewerkt.
* **mDVA-37984** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.5*) - lost de kwestie op waar [!DNL Visual Merchandiser] *het product van de Gelijke door regel* functionaliteit niet correct producten met het opvoeren van updates filtert.
* **MDVA-40488** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar de configureerbare producten met uit-van-voorraad kindproducten niet in hun correcte prijswaaier worden getoond.
* **MDVA-42507** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.5*) - lost de kwestie op waar het full-page geheime voorgeheugen na het toepassen van opvoeringsupdate voor de kartregel wordt schoongemaakt.
* **MDVA-39163** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.5*) - lost de kwestie op waar de verschepende methodes niet beschikbaar zijn wanneer een nieuwe gebruiker wordt geregistreerd en de producten in de kar van de gastzitting zijn.
* **MDVA-38626** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.5*) - lost de kwestie op waar de admin gebruiker geen orde op het achterste eind kan plaatsen gebruikend de [!DNL PayPal Payflow Pro] betaling.
* **MDVA-38666** (*voor Adobe Commerce en Magento Open Source >=2.3.2 &lt;2.3.6*) - lost de kwestie op waar de admin gebruiker niet de configureerbare productopties in de kar van de klant kan veranderen.
* **mDVA-38526** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - lost de kwestie op waar de admingebruiker niet tot [!DNL Site-Wide Analysis tool] kan toegang hebben.
* Bijgewerkte patches: MDVA-40101.

## v1.1.8 {#v1-1-8}

* **mvdr-41215** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op waar de gebruikers de 500 fout na het plaatsen van het *beeld-berichten* koekje krijgen als het reeds bestaat, maar er zijn geen nieuwe berichten.
* **mDVA-41139** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;2.4.4*) - lost de kwestie op waar de configureerbare producten uit voorraad na de invoer van het product worden wanneer qty=0 van een eenvoudig product voor één van zijn bronnen.
* **mDVA-42326** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij klanten een fout krijgen bij het afrekenen na een sessietime-out, zelfs als het hardnekkige winkelwagentje is ingeschakeld.
* **mDVA-42341** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar de `categoryList` vraag van GraphQL geen resultaten filtert als een verzoek de kopbal van de Opslag heeft.
* **mDVA-38393** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op waar de regels van de Catalogus het werken voor een configureerbaar product ophouden als zijn eenvoudig product wordt hernoemd.
* **mDVA-39153** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar een kortingsbedrag verkeerd tijdens reorder in Admin wordt berekend.
* Bijgewerkte patches: MDVA-2893, MDVA-41061, MDVA-35984.

## v1.1.7 {#v1-1-7}

* **MDVA-39711** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.3*) - lost de kwestie op waar de admingebruikers tot het net van de klant na het schrappen van de website niet kunnen toegang hebben.
* **mDVA-40311** (*voor Adobe Commerce en Magento Open Source >=2.4.2-p2 &lt;2.4.4*) - lost de kwestie op waar de admin gebruikers het foutenbericht *Ongeldige veiligheid of vormsleutel krijgen. Vernieuw de pagina* na aanmelding bij de beheerder als het aangepaste beheerpad is geconfigureerd en de geheime sleutel is ingeschakeld.
* **mDVA-41631** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - lost de kwestie op waar de gebruikers een fout wanneer het proberen om ordeinformatie zonder een facultatieve *telefoon* waarde door GraphQL terug te winnen krijgen.
* **mDVA-27239** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.3.6*) - lost de kwestie op waar de dwars-verkoopproducten niet worden getoond.
* Bijgewerkte patches: MDVA-37068, MDVA-35254, MDVA-41164, MDVA-37916, MDVA-37478, MDVA-3451, MDVA-3179 1.

## v1.1.6 {#v1-1-6}

* **mDVA-40550** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.4*) - lost de kwestie met ontbrekende producten op het frontend tijdens het opnieuw indexeren op.
* **MDVA-40120** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - lost de kwestie op waar het sorteren van GraphQL door DESC/ASC niet met producten werkt die de zelfde relevantie of de prijs hebben.
* **mDVA-41399** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;2.4.2*) - lost de kwestie op waar de admingebruikers niet tot *kunnen toegang hebben het Vormen Kart* beheren als een klant een product aan de wenslijst toevoegt.
* **MDVA-40609** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - lost de kwestie op waar de gehandicapte productgegevens in de `cataloginventory_stock_status` indexlijst ontbreken, tonend onjuiste gehandicapte producthoeveelheden.
* **MDVA-39031** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - lost de kwestie op waar het toevoegen van een product aan de kar via GraphQL mogelijk is zelfs als het niet aan de doelwebsite wordt toegewezen.
* **mDVA-41597** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar de gebruikers een fout krijgen wanneer het toevoegen van meer dan één configureerbaar product aan de kar gebruikend GraphQL.
* **mDVA-27456** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.3.7*) - lost de kwestie op waar de gebruikers een fout wanneer het proberen om [!DNL Swagger] krijgen te laden.
* **MDVA-32776** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.2*) - lost de kwestie op waar de voorraadstatus niet wordt bijgewerkt wanneer een orde wordt geplaatst maar niet verscheept.
* **mDVA-30862** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.0*) - lost de kwestie met de onjuiste ordedatum op de gedrukte factuur van de PDF op.
* De indexpagina voor de [!DNL Quality Patch Tool] is verbeterd. Voor [!DNL quality patches] in de meest recente versie van het gereedschap is een handige zoekfunctie en filterfunctie toegevoegd.
* Bijgewerkte patches: MDVA-33382, MDVA-39482.

## v1.1.5 {#v1-1-5}

* **MDVA-41236** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op waar het onmogelijk is om een nieuwe tot stand te brengen of een bestaande geplande update voor een product uit te geven als de Datum van het Eind eerder is verwijderd.
* **mDVA-41046** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op waar de eenvoudige producten met douaneopties voor het toewijzen aan configureerbare/gegroepeerde producten beschikbaar zijn.
* **MDVA-40545** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op waar slechts de eerste knoop voor een pagina werd teruggewonnen zelfs als er meer dan één knoop voor de zelfde pagina was.
* **mDVA-41164** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3-p1*) - lost de kwestie op waar een admin gebruiker een Bedrijf met een dossier of beeldtype douaneattribuut niet kan opslaan of uitgeven.
* **mDVA-39229** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op die de volgende fout veroorzaakt om na het bijwerken van de regel van de Catalogus te verschijnen de tijd van de Update van de Update: *het Draaien van de Baan staging_synchronize_entities_period heeft een fout: De actieve update kan niet worden geschrapt.*.
* **MDVA-40619** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op waar de veranderingen in de paginahiërarchie van CMS een fout 500 veroorzaken wanneer het proberen om gealigneerde het uitgeven op een pagina van CMS te doen.
* **mDVA-41061** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - lost de kwestie op waar de voorraadstatus aan verkoopbaar terugstelt wanneer een product van Admin wordt bewaard.
* **mDVA-31763** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op waar de regels van de catalogusprijs (of niet toegepast) tot handherdex worden teruggedraaid.
* **mDVA-37748** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - lost de kwestie op waar een vraag van GraphQL producten terugkeert die niet aan een gedeelde catalogus worden toegewezen.

## v1.1.4 {#v1-1-4}

* **mDVA-40399** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar de gedeeltelijke facturen voor de zelfde orde niet gelijktijdig via REST API kunnen worden gecreeerd.
* **MDVA-40101** (*voor Adobe Commerce en Magento Open Source >=2.3.2 &lt;2.4.0*) - lost de kwestie op waar de punten niet uit de mini kar na een succesvolle ordeplaatsing worden verwijderd gebruikend [!DNL PayPal Express] Controle.
* **mDVA-40401** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Hiermee wordt de emissie gecorrigeerd waar de waarde van het coupongebruik verandert, zelfs als het plaatsen van een order mislukt.
* **mDVA-40537** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.4.0-p1*) - lost de kwestie op waar de gebruikers een fout wanneer het creëren van een opslagmening krijgen als verscheidene pagina&#39;s van CMS met de zelfde sleutel URL bestaan.
* **mDVA-37725** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.4.3-p1*) - lost de kwestie op waar de asynchrone orde e-mails die van niet-standaardwebsites worden verzonden embleem URLs van de standaardwebsite bevatten.
* **mDVA-39482** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.7-p2 || >=2.4.1 &lt;2.4.4*) - Hiermee wordt het probleem opgelost waarbij een product uit voorraad komt als het wordt geïmporteerd met de hoeveelheid &quot;0&quot; als backorders zijn ingeschakeld.
* **MDVA-40435** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;2.4.4*) - lost de kwestie met een onjuiste korting op bundelproducten met dynamische prijzen wanneer toegepast via GraphQL op.
* **MC-42528** (*voor Adobe Commerce en Magento Open Source >=2.4.3 &lt;=2.4.3-p1*) - lost de kwestie op waar de `categoryList` vraag van GraphQL zowel toegewezen als niet toegewezen categorieën terugkeert.
* **mDVA-29400** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.3.7-p1 || >=2.4.0 &lt;=2.4.0-p1*) - Hiermee wordt het probleem verholpen met dubbele orders die bij [!DNL PayPal Express Checkout] worden geplaatst.
* **mDVA-26005** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.3.5-p2*) - lost de kwestie op waar het onmogelijk is om een categorie in een categorieboom voor de regelvoorwaarden van de Prijs van de Kar te selecteren.
* **mDVA-25631** (*voor Adobe Commerce en Magento Open Source >=2.3.3 &lt;=2.3.5-p2*) - verbetert prestaties voor het uitgeven en het bewaren van klantensegmenten die een groot aantal klanten bevatten.

## v1.1.3 {#v1-1-3}

* **mDVA-40262** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost de kwestie op waar de het onderzoeksvragen van GraphQL niet in populaire onderzoekstermijnen in Admin worden getoond.
* **MDVA-40601** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;=2.4.2-p2*) - lost de kwestie op waar de gebruikers een fout wanneer het proberen om informatie over de categorie te krijgen die door geplande update door GraphQL wordt veranderd.
* **mDVA-37234** (*voor Adobe Commerce en Magento Open Source >=2.3.5 &lt;2.4.0 || >=2.4.1 &lt;=2.4.2-p2*) - Hiermee wordt het probleem opgelost waarbij het toevoegen van een item aan het winkelwagentje meerdere keren (parallel verzoek) voor dezelfde SKU een dubbel regelitem voor dezelfde winkelwagentje-id maakt.
* **mDVA-33606** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;=2.4.2-p2*) - lost de kwestie op waar de gebruikers a *Unieke fout van de beperkingsschending* wanneer het opslaan van een pagina van CMS die aan een hiërarchie wordt toegewezen krijgen.
* **mDVA-31590** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;=2.4.1-p1*) - lost de kwestie op waar de gebruikers attributen in massa niet kunnen bijwerken gebruikend asynchrone rijen MySQL.
* **mDVA-36309** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - lost de kwestie op waar het productonderzoek door attributen langzaam in de admingrids is.

## v1.1.2 {#v1-1-2}

* **MDVA-38929** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie op waar de factuur met FPT een verkeerde Groot Totaal toont wanneer de orde van het archiefkrediet wordt betaald.
* **mDVA-37364** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;=2.4.3*) - lost de kwestie op waar de attributen van de douaneklanten van datatype het net UI van de klant breekt.
* **mDVA-39195** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - lost de kwestie op waar *toevoegt aan de knoop van de Kar* inactief op de categoriepagina was wanneer opnieuw richt aan toegelaten kar.
* **mDVA-37115** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;=2.4.2-p2*) - lost de kwestie op waar een onnodige *slechts 0 linker* bericht op de configureerbare productpagina wordt getoond.
* **MDVA-39521** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4*) - lost de kwestie op waar de gebruiker geen verzendadressen op de kar met een leeg telefoonaantal via GraphQL kan plaatsen.
* **MDVA-39384** (*voor Adobe Commerce en Magento Open Source >=2.3.1 &lt;=2.3.6 || >=2.4.1 &lt;=2.4.3*) - Oplossingen de kwestie waar het attribuut van de douaneklant voor een bedrijfgebruiker niet wordt bewaard.
* **mDVA-39043** (*voor Adobe Commerce en Magento Open Source >=2.3.4 &lt;=2.4.3*) - lost de kwestie op waar de admin gebruiker met beperkte toegang een fout krijgt wanneer het proberen om *Producten* widget aan de pagina van CMS toe te voegen.
* **mDVA-39966** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.3.5-p2 || >=2.4.0 &lt;=2.4.0-p1*) - lost het probleem met het opstellen van onjuiste scènes op.
* **mDVA-38852** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;=2.3.5-p2*) - lost de kwestie op waar de catalogusinventaris door ontwerpsloten lijsten voor updates die prestaties beduidend verminderen in gevallen met verscheidene parallelle orden.
* **MDVA-39986** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.3*) - lost de kwestie op waar de gebruiker geen orde in Admin op MacOS kan plaatsen gebruikend Safari browser.
* **mvdr-38447** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.4*) - lost twee kwesties op: waar *niet zichtbaar individueel* configureerbare kindproducten in de reactie van GraphQL zijn teruggekeerd en optimaliseer vraag MySQL voor de productvraag van GraphQL met categoriefilter.
* **MDVA-40134** (*voor Adobe Commerce en Magento Open Source >=2.4.2 &lt;2.4.3*) - lost de kwestie op waar GraphQL geen verwante producten terugkeert wanneer de Gedeelde Catalogus wordt toegelaten.
* **MDVA-39935** (*voor Adobe Commerce en Magento Open Source >=2.4.1 &lt;2.4.4*) - lost de kwestie op waar GraphQL configureerbare kindproducten terugkeert die op het websiteniveau worden onbruikbaar gemaakt.

## v1.1.1 {#v1-1-1}

* **mDVA-36021** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;2.4.4*) - lost de kwestie op waar de *Vraag aan een lidfunctie getId ()* fout op de pagina van de ordedetails in Admin wordt getoond.
* **mDVA-34948** (*voor Adobe Commerce en Magento Open Source >=2.3.6 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.0-p1*) - lost het probleem met langdurige vragen, zoals `GET_LOCK` op.
* **mDVA-39305** (*voor Adobe Commerce en Magento Open Source >=2.4.0 &lt;=2.4.2-p1*) - lost de kwestie op waar de geregistreerde klanten niet met toegelaten Google kunnen login ReCaptcha kunnen.
* **mvdr-37897** (*voor Adobe Commerce en Magento Open Source >=2.3.0 &lt;2.4.4*) - lost de kwestie met een onjuiste omleiding op wanneer een klant probeert om producten met opties van onlangs Bekeken widget toe te voegen.

## v1.1.0 {#v1-1-0}

* Patchcategorieën zijn geïntroduceerd om de gebruikerservaring te verbeteren en het zoeken naar vereiste patches voor klanten eenvoudiger te maken.
* De naam van het `patches.json` -bestand is gewijzigd in `support-patches.json` .
* **MDVA-38799** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie op waar de downloadbare producten niet na het creëren van een het opvoeren update werden bewaard.
* **mDVA-37592** (*voor Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - lost de kwestie op wanneer het sorteren door prijs niet correct voor producten met een nulprijs werkt die aan de gedeelde catalogus wordt toegewezen.
* **mDVA-38827** (*voor Adobe Commerce >=2.3.3-p1 &lt;2.4.4*) - lost de kwestie op waar de klanten een bericht van de orde verzenden dat een foutenmelding bevat.

## v1.0.26 {#v1-0-26}

* **mDVA-38468** (*voor Adobe Commerce >=2.3.2 &lt;=2.3.5-p2*) - lost de fout op wanneer het bewaren van de pagina&#39;s van CMS: *Punt met zelfde identiteitskaart PAGE_ID bestaat reeds*.
* **mDVA-34680** (*voor Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;2.4.3*) - Hiermee wordt het probleem verholpen waarbij de tijd die door de Customer Account is gemaakt niet correct wordt gefilterd in het klantenraster.
* **MDVA-37068** (*voor Adobe Commerce >=2.3.1 &lt;2.4.4*) - lost de kwestie op waar het onjuiste belastingtarief toont wanneer het winkelwagentje slechts virtuele producten heeft.
* **MDVA-38608** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie op waar de tijdelijke lijsten niet worden geschrapt wanneer de herdex niet met succes wordt gebeëindigd.
* **mDVA-38308** (*voor Adobe Commerce >=2.3.5 &lt;=2.3.6-p1 || >=2.4.0 &lt;=2.4.1-p1 || >=2.4.2 &lt;2.4.4*) - lost de problemen op die betrekking hebben op het toevoegen van [!DNL Vimeo] video&#39;s aan producten.

## v1.0.25 {#v1-0-25}

* **MDVA-37916** (*voor Adobe Commerce >=2.3.6 &lt;2.4.3*) - lost de kwestie op waar de klant niet aan de pagina van de Bevestiging van de Betaling wanneer het gebruiken van de [!DNL Paypal Payment Advanced] methode wordt genomen.
* **mDVA-37082** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie op wanneer het bewaren van de douanevoorraad van gegroepeerde producten het product veroorzaakt om uit voorraad in het frontend te tonen.
* **mDVA-36572** (*voor Adobe Commerce >=2.3.5 &lt;2.4.3*) - lost de kwestie op wanneer de updates van het Memo van het Krediet niet meer dubbele updates van de productreserve in het gegevensbestand veroorzaken.
* **mDVA-38132** (*voor Adobe Commerce >=2.3.3 &lt;2.4.3*) - lost de kwestie op wanneer het Admin paneel wegens a *te veel redirects* fout onbereikbaar is.
* **mDVA-38270** (*voor Adobe Commerce >=2.4.1 &lt;2.4.3*) - lost de kwestie met ontbrekende kaartinformatie van het Cadeautje in het orde totaal in GraphQL op.

## v1.0.24 {#v1-0-24}

* **MDVA-37779** (*voor Adobe Commerce >=2.4.2 &lt;=2.4.4*) - lost de kwestie met het toevoegen van een configureerbaar product aan het karretje via GraphQL op wanneer website ID niet met opslag ID samenvalt.
* **mDVA-36832** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - lost de kwestie op waar de beelden op pagina&#39;s dupliceren wanneer de meningsbreedte 768px is.
* **mDVA-37874** (*voor Adobe Commerce >=2.3.6 &lt;=2.3.7 || >=2.4.1 &lt;=2.4.2-p1*) - lost de kwestie op waar *Vaste discontobedrag voor het volledige karretje* verkeerd wordt toegepast op een bundelproduct dat meer dan één optie bevat.
* **mDVA-37913** (*voor Adobe Commerce >=2.3.0 &lt;=2.4.0-p1*) - lost de kwestie waar downloadbare verbindingen verdwijnen als het downloadbare product via API wordt bijgewerkt.
* **mDVA-34330** (*voor Adobe Commerce >=2.3.1 &lt;=2.4.2-p1*) - lost de kwestie op waar de orden in het net van Orden niet volgens Admin timezone worden gefiltreerd.

## v1.0.23 {#v1-0-23}

* **mDVA-37478** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.7*) - lost de kwestie op waar Adobe Commerce een fout wanneer het creëren van een gedeeltelijke factuur voor orden veroorzaakt die met de *Betaling op Rekening* betalingsmethode door REST API worden geplaatst.
* **mDVA-37362** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.2-p1*) - lost de kwestie op waar de configureerbare waarden van de productoptie en de variantattributenwaarden in de reactie van GraphQL leeg waren.
* **MDVA-37288** (*voor Adobe Commerce 2.4.2*) - lost de kwestie op waar de verkeerde rijprijzen na GraphQL verzoek werden teruggekeerd.
* **mDVA-37225** (*voor Adobe Commerce >=2.4.1 &lt;=2.4.2-p1*) - lost de kwestie op waar het uploadproces tijdens snelle ordeverwezenlijking geplakt is wanneer er een geheelwaarde in ingevoerde SKUs is.
* **mDVA-37224** (*voor Adobe Commerce >=2.3.3 &lt;=2.4.2-p1*) - lost de kwestie op waar de klanten voor verhandelbaar citaat met [!DNL PayFlow Pro] met een ander product in de kar niet kunnen betalen.
* **mDVA-36286** (*voor Adobe Commerce >=2.3.6 &lt;=2.4.2-p1*) - lost de kwestie op waar de de producten widget van de Bouwer van de Pagina voorproef breken als zelfde SKU een verschillende positie in subcategorieën heeft.
* **mDVA-30186** (*voor Adobe Commerce >=2.3.4 &lt;=2.3.5-p2, >=2.4.0 &lt;=2.4.0-p1, >=2.4.2 &lt;=2.4.2-p1*) - lost de kwestie op waar de attributenopties door optiewaarde in plaats van worden gesorteerd aantal objecten in GraphQL-reactie.

## v1.0.22 {#v1-0-22}

* **mDVA-36718** (*voor Adobe Commerce >=2.3.0 &lt;=2.4.2*) - lost de kwestie op waar de oude douaneopties na wordt veranderd via API blijven.
* **mDVA-35773** (*voor Adobe Commerce >=2.3.6 &lt;=2.3.6-p1 || >=2.4.1 &lt;=2.4.2*) - Hiermee wordt de kwestie opgelost waarbij het Eindtotaal niet als nul op de factuur wordt weergegeven voor bestellingen met een korting van 100%.
* **MDVA-36833** (*voor Adobe Commerce 2.4.2*) - lost de kwestie met onderzoeksresultaten op die willekeurige aantallen producten per pagina tonen na het uitsluiten van sommige producten van gedeelde catalogus.
* **mDVA-37182** (*voor Adobe Commerce >=2.4.1 &lt;=2.4.2*) - lost de kwestie met het krijgen van onjuiste onderzoeksresultaten in zowel [!DNL Elasticsearch] versie 6 als versie 7 op.
* **mDVA-36253** (*voor Adobe Commerce >=2.4.0 &lt;=2.4.1-p1*) - lost de kwestie op waar het verkeerde subtotaal in de minikaart na puntschrapping toont.
* **MDVA-36853** (*voor Adobe Commerce 2.4.2*) - lost de kwestie zonder beelden op wanneer het laden van grote media galerieën.

## v1.0.21 {#v1-0-21}

* **mDVA-34665** (*voor Adobe Commerce >=2.3.4 &lt;=2.3.4-p2*) - lost de kwestie met ontbrekende gebundelde producten op categoriepagina&#39;s op.
* **MDVA-36615** (*voor Adobe Commerce 2.4.2*) - lost de kwestie met onjuiste producttelling in het Admin productnet op.
* **mDVA-36464** (*voor Adobe Commerce >=2.4.0 &lt;=2.4.2*) - lost de kwestie op waar de configuratie van het e-mailbericht niet op store-view niveau werkt.
* **MDVA-36138** (*voor Adobe Commerce ^2.3.2*) - lost de kwestie op waar de het verschepen prijs niet wordt aangepast en de volledige het verschepen prijs aan klanten wordt getoond als niet alle punten in de kar voor de vrije het verschepen kartelregel kwalificeren.
* **mDVA-36424** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 || >=2.0.0 &lt;2.2.0*) - Hiermee wordt het probleem verholpen waarbij mediaafbeeldingen die aan elementen van de paginaontwikkelaar zijn gekoppeld, verdwijnen als de inhoud herhaaldelijk wordt bewerkt als de URL van de achterste basis afwijkt van de basis-URL van de opslagront.
* **MDVA-35984** (*voor Adobe Commerce ^2.4.0*) - lost de kwestie met onjuiste producthoeveelheid en verkoopbare hoeveelheid na het creëren van veelvoudige gezamenlijke verzendingen voor het zelfde product op.

## v1.0.20 {#v1-0-20}

* **mDVA-36170** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - dit bevestigt de kwestie waar de vraag van GraphQL niet caching door de markering van het categoriecache te gebruiken.
* **mDVA-33168** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - lost de kwestie op wanneer het bijwerken van een productattribuut via API alle andere attributen veranderen in een lege waarde.
* **MDVA-19640** (*voor Adobe Commerce >=2.3.0*) - lost de kwestie op waar [!DNL Advanced Reporting] geen gegevens toont.
* **mDVA-11189** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - lost de kwestie op wanneer na het invoeren van een CSV- dossier om productvoorraad bij te werken, worden de rijen van de `cataloginventory_stock` lijst geschrapt.
* **mDVA-26639** (*voor Adobe Commerce >=2.3.3-p1 &lt;2.3.6*) - lost de kwestie op waar als een nieuw malplaatje van de orderbevestiging wordt gecreeerd, de orde punten in de orde post missen.
* **mDVA-15546** (*voor Adobe Commerce >=2.3.0*) - lost de kwestie op waar na het creëren van een orde a *Column entity_id waar de clausule dubbelzinnige* foutenvertoningen in het uitzonderingslogboek is.
* **mDVA-21095** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - lost de kwestie op wanneer een vraag `INSERT INTO search_tmp` niet na de update van de massafakenwaarde zal beëindigen.
* **mDVA-23845** (*voor Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - lost de kwestie op waar de e-mailmalplaatjes niet kunnen worden voorvertoond nadat de minificatie van JavaScript wordt toegelaten.
* **mDVA-22026** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - lost de kwestie op waar het invoeren van producten van Csv- dossier met inbegrip van beelden van externe URLs ontbreekt.
* **mDVA-22383** (*voor Adobe Commerce >=2.3.0 &lt;2.3.4*) - lost de kwestie op waar het bewaren van een product een lange tijd en de paginaugmenten vergt.
* **mc-41359** (*voor Adobe Commerce >=2.3.6-p1 &lt;2.3.7, >=2.4.2 &lt;2.4.3*) - lost de kwestie van de onjuiste montages van de parameters van het koekje SameSite op.

## v1.0.19 {#v1-0-19}

* **MDVA-33614** (*voor Adobe Commerce 2.4.1*) - lost de kwestie op waar de Bouwer van de Pagina de volgende fout werpt: *Een fout is voorgekomen terwijl het in werking stellen van de Bouwer van de Pagina. Raadpleeg uw contactpersoon voor technische ondersteuning.*
* **mDVA-35356** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie met onjuiste terugkeer van het opslagkrediet na gedeeltelijk gefactureerde orderannulering op.
* **mDVA-33289** (*voor Adobe Commerce >=2.4.0 &lt;2.4.3*) - lost de kwestie op waar de ruwe code van JavaScript in het facturerings adres UI tijdens controle wordt getoond als [!DNL Google Tag Manager] wordt toegelaten.
* **mDVA-35982** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie op waar de admingebruikers tot een specifieke website beperkt geen lading voor de orde tot stand kunnen brengen die op de zelfde website wordt geplaatst.
* **mDVA-35155** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - lost de kwestie op waar het onmogelijk is om een bundelproduct te kopen als de optietechtheek werd veranderd.
* **mDVA-35910** (*voor Adobe Commerce >=2.4.1 &lt;2.4.3*) - lost de kwestie op waar het onmogelijk is om een nieuwe klantenrekening tot stand te brengen na het onbruikbaar maken van Login als functionaliteit van de Klant.
* **mDVA-34474** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie met het toevoegen van een product aan de verzoeklijst gebruikend API op.
* **mDVA-34591** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie met een onjuiste berekening van de de kaartregelkorting voor *Maximale Korting van de Aantal wordt toegepast op* en *de Stap van de Korting van de Aantal (Koop X)*.
* **mvdr-33704** (*voor Adobe Commerce >=2.4.0 &lt;2.4.3*) - lost de kwestie op waar *In opslag bestelwagen* verschepende optie niet verschijnt, hoewel om beschikbaar wordt gevormd.
* **mDVA-34928** (*voor Adobe Commerce >=2.3.5 &lt;2.3.5-p2*) - lost de kwestie op waar de paginalader voor onbepaalde tijd wordt getoond nadat het opslagkrediet wordt verwijderd uit de betaling.
* **mDVA-35254** (*voor Adobe Commerce >=2.3.1 &lt;2.4.3*) - lost de kwesties met CAPTCHA tijdens controle op.
* **MDVA-35569** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - lost de kwestie op waar het *vaste productbelastingen* gebied niet in de reactie van GraphQL wordt bevolkt wanneer de staat wordt gespecificeerd.
* **mDVA-35847** (*voor Adobe Commerce >=2.4.1 &lt;2.4.3*) - lost de B2B kwestie op waar de Gebruikers van het Bedrijf onderbrekingen vormen als een attribuut van de douaneklant wordt gebruikt.
* **mDVA-31307** (*voor Adobe Commerce >=2.4.0 &lt;2.4.2*) - lost de kwestie op waar er *uit geheugen* fouten op bepaalde categorieën wegens problemen met dynamische CSP het fluiten voor caching blokken zijn.

## v1.0.18 {#v1-0-18}

* **mvdr-32655** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost het onjuiste *op lopende* berichtstatus aan het correcte *volledige* bericht voor consument `quoteItemCleaner` na het schrappen van verscheidene producten.
* **mDVA-34102** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - bevestigt de hoeveelheid StandaardVoorraad nul voor gehandicapte producten op het Net van het Product en geef de pagina&#39;s van het Product in het gebied Admin uit.
* **mDVA-35286** (*voor Adobe Commerce >=2.4.0 &lt;2.4.2*) - lost de kwestie op waar er een fout is als een klant producten in de kar heeft gebundeld en schakelt van de Veelvoudige controle van Adressen aan de controle van Onepage.
* **mDVA-35312** (*voor Adobe Commerce >=2.4.1-p1 &lt;2.4.2*) - lost reactiecode 500 op wanneer een leeg verzoek van GraphQL.
* **mDVA-34189** (*voor Adobe Commerce >=2.3.4 &lt;2.4.3*) - lost 503 eerste byteonderbreking op [!DNL Visual Merchandiser] vragen wanneer het laden van de Admin pagina van de Categorie.
* **mDVA-34695** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1*) - lost negatief `children_count` na het schrappen van categorieën op.

## v1.0.17 {#v1-0-17}

* **mDVA-34012** (*voor Adobe Commerce >=2.3.1 &lt;2.4.3*) - lost de kwestie op waar het *Gebruik standaardwaarde* checkbox wordt ontruimd nadat de geplande veranderingen worden toegepast. De uitgave wordt weergegeven zodra de geplande wijzigingen niet meer van kracht zijn.
* **mDVA-35064** (*voor Adobe Commerce >=2.3.3 &lt;2.4.3*) - lost de kwestie op waar URL herschrijft niet voor configureerbare producten die via API worden gecreeerd worden geproduceerd.
* **mDVA-34943** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de snelle orde eerder ingegaan SKUs in het voorgeheugen onderbrengt.
* **mDVA-35197** (*voor Adobe Commerce >=2.3.5 &lt;2.4.0*) - lost de kwestie op waar er een fout wanneer het toevoegen aan karretje gebruikend GraphQL is als de eerder toegevoegde producten uit voorraad worden.
* **mDVA-34850** (*voor Adobe Commerce >=2.3.1 &lt;2.4.0*) - lost de kwestie op waar de uit-van-voorraad opties van een configureerbaar product niet worden getoond in plaats van worden getoond zoals doorgeslagen-door.
* **mDVA-34867** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie op waar de waarden voor een voorwaardengebied dat voor een geplande update wordt geplaatst niet worden bewaard.
* **mDVA-35092** (*voor Adobe Commerce >=2.3.5 &lt;2.4.3*) - lost de kwestie op waar de gebruikers [!DNL Vimeo] video&#39;s wegens verouderde [!DNL Vimeo] API niet kunnen toevoegen.

## v1.0.16 {#v1-0-16}

* **mDVA-33453** (*voor Adobe Commerce >=2.3.6 &lt;2.4.3*) - lost de kwestie op waar de de inhoudstype van de Producten van de Bouwer van de Pagina als de passende producten verschillende prijzen voor elke website hebben.
* **MDVA-32634** (*voor Adobe Commerce ^2.3.1*) - lost de kwestie op waar `url_path` van de categorie die aan al opslag wordt toegewezen onveranderd blijft na het bewegen van de categorie in de hiërarchie.
* **mDVA-33344** (*voor Adobe Commerce ^2.3.0*) - lost de kwestie op waar hard - gecodeerde `rma_item` entiteit standaard geplaatste identiteitskaart in plaats van de waarde van het gegevensbestand wordt gebruikt.
* **mDVA-34192** (*voor Adobe Commerce >=2.3.4 &lt;2.4.3*) - lost de kwestie op waar het onmogelijk is om klantendatum van geboorte te wijzigen/te specificeren gebruikend dd/mm/jjjj formaat.
* **mDVA-34847** (*voor Adobe Commerce ^2.3.0*) - de typeomzetting van opslagIDs van Oplossingen aan geheel voor SQL voorwaarde in inzamelingen Admin voor Gebruiker Admin met douanetoestemmingen.
* **MDVA-34886** (*voor Adobe Commerce ^2.3.2*) - lost de kwestie op waar het onderzoek niet resultaten terugkeert als *gewicht* productattribuut als zoekbaar wordt gevormd.

## v1.0.15 {#v1-0-15}

* **mDVA-33559** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie van [!DNL PayPal Payflow Pro] betaling op die met de fout van het formaat van de parameterlijst opnieuw richt faalt.
* **mDVA-34023** (*voor Adobe Commerce >=2.3.0 &lt;2.4.3*) - lost de kwestie op waar de fout *geen dergelijke entiteit met addressId* vertoningen willekeurig op bezoekersbrowsers.
* **mDVA-32759** (*voor Adobe Commerce >=2.3.1 &lt;2.4.3 met B2B uitbreiding*) - lost de kwestie op waar de Gedeelde Catalogi bestaande rij het tarief schrappen.
* **MDVA-33482** (*voor Adobe Commerce ^2.3.5*) - lost de kwestie op waar het produceren van een Memo van het Krediet tegen een gedeeltelijke factuur in belasting voor de totale orde in plaats van belasting voor die gedeeltelijke factuur resulteert.
* **mDVA-33393** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de fout *op verstrekte countryId bestaat niet*.
* **mDVA-33632** (*voor Adobe Commerce >=2.3.0 &lt;2.3.7*) - verstrekt een moeilijke situatie waar het uitzonderingsbericht *Dit product uit voorraad* nu aan een admin gebruiker wordt getoond wanneer het proberen om een uit voorraadproduct opnieuw in orde te brengen.
* **mDVA-34469** (*voor Adobe Commerce >=2.4.1 &lt;2.4.2*) - lost de kwestie op waar de mutaties van GraphQL op het karretje van een klant ontbreken wanneer het gebruiken van veelvoudige opslagmeningen.
* **mDVA-33976** (*voor Adobe Commerce >=2.3.0 &lt;2.3.7*) - lost de kwestie op waar het bundelproduct uit Voorraad op de storefront na het verwijderen van de tweede optie uit het bundelproduct wordt getoond.
* **mDVA-33894** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1 met B2B uitbreiding*) - lost veelvoudige kwesties voor de Snelle functionaliteit van de Orde met inbegrip van het toevoegen van en het verwijderen van veelvoudige producten en de gevallengevoeligheid van SKU op.
* **mDVA-27664** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6*) - lost de kwestie in de vorm van de klantenregistratie op die een fout veroorzaakt om te tonen: *FOUT - de Datum van geboorte zou niet groter moeten zijn dan vandaag.*
* **mDVA-33970** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - lost de kwestie op waar er het verkeerde muntteken in het Memo van het Krediet is wanneer het werkingsgebied van de prijsattributen aan website wordt geplaatst.
* **mDVA-33992** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie van B2B speciale het tonen verkeerd tijdens controle op.
* **mDVA-34100** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2 met B2B uitbreiding*) - lost de kwestie op waar een ondernemingsrekening niet van de pagina van de bedrijfstructuur kan worden gecreeerd.

## v1.0.14 {#v1-0-14}

* **mDVA-31969** (*voor Adobe Commerce >=2.3.3 &lt;2.3.5, >=2.4.0 &lt;2.4.2*) - lost de kwestie met dubbele beelden na productinvoer uit een Csv- dossier op.
* **mDVA-33382** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwesties met indexeerderongeldigverklaring na productverwijdering uit een categorie op.
* **mDVA-28511** (*voor Adobe Commerce >=2.3.5 &lt;2.3.6*) - lost de kwestie op waar het niet mogelijk is om [!DNL PayPal] controle te voltooien als het gebied van de Naam bepaalde karakters (als geaccentueerde hoofdletters) bevat.
* **MDVA-31519** (*voor Adobe Commerce >=2.3.5 &lt;2.3.6*) - lost de kwestie met wachttijden in gastcontrole op wanneer een plaats-brede verkoopregel in gebruik is.
* **mDVA-33281** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6*) - lost de kwestie op waar er een fatale fout in `inventory:reservation:list-inconsistencies` wegens verkeerd de parametertype van SKU is.
* **mDVA-24201** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - lost de kwestie op waar de prijzen niet op de geplande de prijsregel van het karretje wijzen tot manueel opnieuw geïndexeerd.
* **mDVA-32694** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || >= 2.4.0 &lt;2.4.2*) - lost het probleem op waar een admin gebruiker geen product aan een verhandelbaar citaat kan toevoegen als het met een niet standaardopslag verwant is.
* **mDVA-33516** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - lost de kwestie op waar het uitgeven van een bundelproduct in een verzoeklijst tot een fout leidt.
* **mDVA-33975** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - lost veelvoudige kwesties met betrekking tot prijsberekening in de verzoeken van GraphQL op.

## v1.0.13 {#v1-0-13}

* **mDVA-30858** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie met [!DNL PayPal] rapporten van de Afwikkeling niet beschikbaar onder **Rapporten** > **Verkoop** > **[!DNL PayPal]** Afwikkeling zoals verwacht.
* **mcp-87** (*voor Adobe Commerce >=2.3.1 &lt;2.4.2*) - verbeterde indexatietijd voor categorieproduct en voorraadindexeerders voor grote profielen.
* **mDVA-33106** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de opnieuw geplande productveranderingen worden gewist nadat het bevel van de kruin `run` wordt uitgevoerd.
* **mDVA-19391** (*voor Adobe Commerce >=2.3.0 &lt;2.3.5*) - lost de kwestie op waar `analytics_collect_data` een fout toe te schrijven aan ONGELDIGE beschrijvingsverslagen in de `catalog_category_entity_text` lijst veroorzaakt.
* **mDVA-20376** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - lost de kwestie met *geen dergelijke entiteit met customerId = 1* fout in `exception.log` voor geregistreerde klanten na ordeplaatsing op.
* **mDVA-23764** (*voor Adobe Commerce >=2.3.2 &lt;2.3.5*) - lost de insect in `JsFooterPlugin.php` op die de vertoning van dynamische blokken beïnvloedt.
* **mDVA-13203** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de *schending van de Integriteitsbeperking search_tmp_ lijst* fout na een volledige herdex verschijnt.
* **MDVA-23426** (*voor Adobe Commerce >=2.3.3 &lt;2.3.5*) - lost de kwestie op waar de bericht e-mails die door Adobe Commerce worden verzonden een leeg lichaam met inhoud bevatten die als gehechtheid worden toegevoegd.
* **mDVA-22150** (*voor Adobe Commerce >=2.3.1 &lt;2.3.4*) - lost de kwestie op waar de klanten met een configureerbaar product in kart en een toegepaste coupon niet login kunnen als dat configureerbare product in Admin wordt onbruikbaar gemaakt.
* **mDVA-32545** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de facturen niet automatisch worden verzonden wanneer het creëren van orden van Admin.
* **mDVA-32714** (*voor Adobe Commerce >=2.3.4 &lt;2.4.1*) - lost de kwestie op waar de prijs van de klantengroep niet in het productvraag van GraphQL werkt.

## v1.0.12 {#v1-0-12}

* **mDVA-31399** (*voor Adobe Commerce >=2.3.2 &lt;2.4.2*) - voegt *Subtotal (incl. toe. Belasting)* optie aan de voorwaarden van de prijsregel.
* **mDVA-31236** (*voor Adobe Commerce >=2.4.0 &lt;2.4.2*) - lost de kwestie op waar Admins met de toegang van het douanemiddel niet aan opstelling 2FA of login kunnen.
* **MDVA-30845** (*voor Adobe Commerce >=2.3.5 &lt;2.3.7*) - lost de kwestie op waar *Sorry, geen citaten voor deze orde op dit ogenblik beschikbaar zijn* fout wordt getoond wanneer het nalaten om met UPS XML/USPS/DHL te verbinden, en geen andere het verschepen methode is beschikbaar.
* **mDVA-32133** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - lost de kwestie op waar de media galerij niet van de Bouwer van de Pagina in bepaalde gevallen laadt.
* **mDVA-12304** (*voor Adobe Commerce >=2.3.0*) - verhoogt het maximumaantal koekjes van 50 tot 200.
* **mDVA-32632** (*voor Adobe Commerce >=2.3.2 &lt;2.3.5*) - lost de kwestie op waar de orden in het betalingssysteem verschijnen, maar niet in Adobe Commerce.
* **mDVA-32449** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0. || >=2.4.1 &lt;2.4.2 met B2B uitbreiding*) - lost het probleem op waar de ordegeschiedenis zeer langzaam laadt of helemaal niet laadt.
* **MDVA-32739** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar het toelaten van Asynchrone E-mailberichten oude verkoope-mailberichten verzendt.

## v1.0.11 {#v1-0-11}

* **mc-38509** (*voor Adobe Commerce 2.3.6, 2.4.1*) - lost de kwestie op waar *creeert een knoop van de Rekening* gehandicapt na het verbeteren van ongeldige gegevens in *creeer Nieuwe Rekening van de Klant* vorm.
* **MDVA-31006** (*voor Adobe Commerce 2.3.0, 2.3.1*) - lost de kwestie op waar de dubbele orden na het plaatsen van een orde verschijnen gebruikend [!DNL Paypal Express] betaling.
* **MDVA-25602** (*voor Adobe Commerce 2.3.0*) - lost kwestie met [!DNL PayPal Payflow Pro] betalingsmethode op en behandelend koekjes als `SameSite=Lax` door gebrek in Chrome 80 browser en API reactie opnieuw richt aan klantenlogin pagina.

## v1.0.10 {#v1-0-10}

Kleine correcties voor patchversies

## v1.0.9 {#v1-0-9}

* **mDVA-31363** (*voor Adobe Commerce >=2.3.2 &lt;2.4.2*) - lost de kwestie op waar de Regel van de Prijs van het Kar met coupon niet via GraphQL van toepassing is wanneer *Vaste waardekorting voor volledige kar* actie wordt gebruikt.
* **mDVA-30889** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar een fout na het aanhalen van een bundel met virtuele en eenvoudige producten als opties voorkomt.
* **mDVA-31791** (*voor Adobe Commerce >=2.3.4 &lt;2.3.5*) - verbetert de prestaties van de productpagina in gevallen wanneer de doelregels of de verbonden producten worden gebruikt.
* **mDVA-31168** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar het product uitvoerCSV dossier niet verschijnt, en er is een fout van de geheugentoewijzing.
* **mDVA-32313** (*voor Adobe Commerce >=2.3.0 &lt;2.3.4*) - lost de kwestie op waar de configureerbare producten aan verlanglijst met de verkeerde configuratieopties konden worden toegevoegd.
* **mDVA-31759** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de producten niet met *dropdown* en *textarea* attributenwaarden tijdens de invoer CSV worden bijgewerkt.
* **mDVA-32012** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de postcodes in Korea en Argentinië niet kunnen worden bevestigd.
* **mDVA-31640** (*voor Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Hiermee wordt het probleem opgelost waarbij een speciale prijs niet kan worden bijgewerkt via de REST API.
* **mDVA-28651** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || >2.4.0 met B2B-extensie*) - Hiermee wordt het probleem verholpen waarbij zich prestatieproblemen voordoen bij het laden van verhandelbare aanhalingstekens via REST API.

## v1.0.8 {#v1-0-8}

* **mDVA-31242** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1 met B2B uitbreiding*) - lost de kwestie op waar een verkeerd muntteken in het net van het Memo van het Krediet wordt getoond.
* **mDVA-31295** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de beloningspunten niet worden berekend wanneer een gedeeltelijke orde wordt voltooid en de punten worden belast.
* **mDVA-30112** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - lost de kwestie op waar als het aantal orden de *troebele* waarde overschrijdt, beschouwt Adobe Commerce de orden met *hangende* status als inconsistenties.
* **mDVA-31150** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de tegoeden van de de opslagkrediet en giftekaarten niet door de vraag van de Rest API van de GET van de Factuur worden teruggegeven, toen de factuur door de vraag van Rest API werd gepost en de orde gedeeltelijk door de rekeningen van de opslagkrediet en van de cadeau werd betaald.
* **mDVA-30963** (*voor Adobe Commerce >=2.3.2 &lt;2.4.2*) - lost de kwestie op waar de producten die resultaten filtreren om waarden slechts te bevatten die voor *worden gespecificeerd Alle opslagmeningen* werkingsgebied in Admin, producten met waarden omvatten die op het niveau van de opslagmening worden met voeten getreden.
* **mDVA-29954** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0. || 2.4.2 met B2B uitbreiding*) - lost de kwestie op waar het *Nieuwe Verzoek van de Registratie van het Bedrijf* en *u met een bedrijf* e-mails werd verbonden van het verkeerde adres worden verzonden.
* **mDVA-28357** (*voor Adobe Commerce >=2.3.2 &lt;2.3.6 || >=2.4.0 &lt;2.4.1*) - Vervangt de standaardanalysator met een douanemonitor met sleutelwoordkenizer voor het gebied van SKU in de [!DNL ElasticSearch] index om de vragen van het vervangingsonderzoek met SKUs te laten werken die een koppelteken (&quot;-&quot;) bevatten.

## v1.0.7 {#v1-0-7}

* **mDVA-30972** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de status van de douaneorde in *Verwerking* na gedeeltelijke ladingsverwezenlijking gebruikend WebApi werd veranderd.
* **MDVA-30428** (*voor Adobe Commerce >=2.3.4 &lt;2.3.5*) - lost de kwestie op waar de klanten geen product aan verlanglijst kunnen toevoegen als dit product aan een bron van de douaneinventaris wordt toegewezen.
* **MDVA-30594** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar een orde met veelvoudige adressen niet tijdens controle kon worden bewaard wanneer FPT wordt gevormd.
* **mDVA-29148** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op wanneer het creëren van een product via een API vraag, gebruikt het productattribuut van `\Magento\Eav\Model\Entity\Attribute\Backend\ArrayBackend` (als Multiselect) type niet zijn standaardwaarde als geen waarde in de nuttige lading werd verstrekt.
* **mDVA-30837** (*voor Adobe Commerce >=2.3.1 &lt;2.3.5*) - voegde een configuratie toe plaatsend *omvat Belasting aan Bedrag: Ja/Nr* in de Vrije Verzendmethode configuratie. Wanneer *omvat Belasting aan Bedrag* aan *ja* wordt geplaatst, wordt het Minimale Bedrag van de Orde berekend als Subtotaal + Belasting. Wanneer *omvat Belasting aan Bedrag* aan *Nr* wordt geplaatst, wordt het Minimale Bedrag van de Orde berekend als Subtotaal
* **mDVA-25028** (*voor Adobe Commerce >=2.3.2 &lt;2.3.3 || >=2.3.5 &lt;2.3.6*) - Hiermee wordt het probleem verholpen wanneer orders die met [!DNL PayPal Payflow Pro] zijn geplaatst, niet zijn ingesteld op de status Vermoedelijke fraude wanneer er fraudefilters worden geactiveerd.
* **mDVA-31224** (*voor Adobe Commerce >=2.3.3 &lt;2.3.5*) - verbetert de prestaties van `catalog_product_price` re-indexverrichting voor bundelproducten.
* **mDVA-31321** (*voor Adobe Commerce >=2.3.2 &lt;2.3.5*) - lost een lege pagina (fout) op wanneer *allen tonen* wordt geselecteerd. [!DNL Elasticsearch] retourneert een grote lijst met product-id&#39;s. In dit scenario wordt de volgorde door de component omgezet in een onjuiste SQL-indeling.
* **MDVA-30815** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - lost de kwestie op waar wanneer u verandert hoeveel onderzoeksresultaten op de pagina van onderzoeksresultaten zouden moeten worden getoond, Adobe Commerce een lege pagina toont. [!DNL Elasticsearch] geeft nu correct de resultaten van categoriepagina&#39;s weer wanneer u het aantal weergegeven zoekresultaten per pagina wijzigt.
* **mDVA-30782** (*voor Adobe Commerce >=2.3.5 &lt;2.4.2*) - lost de kwestie op waar het Dynamische Blok ongeacht de wortelregel ongeacht wordt getoond.
* **mDVA-31021** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de prestatieskwesties in `module-catalog-import-export/Model/Import/Product/Option.php` bestaan. Als er meer dan ~100k verslagen in `catalog_product_option` lijst zijn, duurt een nieuw CSV met enig product minder dan 10 sec om te bevestigen.
* **mDVA-31007** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - lost de kwestie op waar de attributen van het douaneadres niet correct in de pagina van de ordedetails in het mijn rekeningsgebied en in het achtereind worden getoond.
* **mDVA-29389** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie met Geavanceerde Rapportering op waar de `analytics_collect_data` kronjob zegt: *Haven moet binnen gastheerparameter (zoals localhost worden gevormd:3306)*.
* **mDVA-31343** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6*) - lost de kwestie met de verwijderde lichaamscategorie `page-layout-category-full-width` op wanneer een categorie gepland is.
* **mDVA-30945** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar u een fatale foutenmelding wanneer het bijwerken van kaarten `Call to a member function getValue() on null in module-configurable-product CartItemProcessor.php` ontvangt.

## v1.0.6 {#v1-0-6}

* **mDVA-28993** (*voor Adobe Commerce >=2.3.4 &lt;2.4.0*) - voert het *Minimum* functionaliteit en gedeeltelijk onderzoek naar [!DNL Elasticsearch] motor aan. Hiermee lost u problemen op met afbreekstreepjes in zoekopdrachten.
* **mDVA-30102** (*voor Adobe Commerce >=2.3.2 &lt;=2.4.0*) - lost de kwestie op waar het geheime voorgeheugen van Redis snel stijgt aangezien de lay-outgeheime voorgeheugens TTL niet hebben.
* **mDVA-30599** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.0*) - lost de kwestie op waar de gastcitaten die gebruikend API worden gecreeerd verkeerd als citaten voor geregistreerde klanten worden gemerkt.
* **mDVA-29446** (*voor Adobe Commerce >=2.3.3 &lt;=2.4.0*) - lost de kwestie op waar de prijs van niet toepasselijke verschepende methode als nul tijdens controle wordt getoond.
* **MDVA-30357** (*voor Adobe Commerce >=2.3.2 &lt;=2.4.0*) - lost de kwestie met verkeerde beeld URLs op wanneer het produceren van een sitemap door kruin.
* **mDVA-30565** (*voor Adobe Commerce >=2.3.2 &lt;=2.3.3-p1*) - lost de kwestie op waar *Geen dergelijke entiteit met kartide = 0* fout voor gastklant op winkelrekenkamer wordt getoond als het blijvende winkelwagentje wordt toegelaten.
* **mDVA-29787** (*voor Adobe Commerce >=2.3.0 &lt;=2.4.0*) - lost de kwestie op waar de doelregel voor verwante producten niet werkt wanneer *één van* voorwaarde wordt gebruikt om te bepalen producten om worden getoond.
* **mDVA-30977** (*voor Adobe Commerce >=2.3.4 &lt;=2.3.5-p2*) - lost de kwestie met willekeurige producten die uit categorieën na herdex ontbreken op.
* **mDVA-28202** (*voor Adobe Commerce >=2.3.4 &lt;=2.4.2*) - lost de kwestie op waar de Gelaagde Navigatie niet configureerbare producten correct filtert wanneer MSI wordt gebruikt.
* **mDVA-28300** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - lost de kwestie op waar het GQL- verzoek niet op de prijsveranderingen van de regels van de catalogusprijs wijst.
* **MDVA-31006** (*voor Adobe Commerce >=2.3.2 &lt;=2.4.2*) - lost de kwestie op waar de dubbele orden na het plaatsen van een orde verschijnen gebruikend [!DNL Paypal Express] betaling.

## v1.0.5 {#v1-0-5}

* **mDVA-30841** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - lost de kwestie met gelaagde navigatie op, waar *geen* waarde voor booleaanse de attributen van het typeproduct niet inbegrepen in gelaagde navigatie was als [!DNL Elasticsearch] als onderzoeksmotor werd gebruikt.
* **mDVA-28191** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - lost de kwestie op waar geen betalingsmethodes tijdens ordeverwezenlijking via Admin worden geladen.
* **mDVA-29959** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.3-p1 met B2B uitbreiding*) - lost de kwestie op waar de beperkte admin gebruiker met *Bedrijven* toestemmingen niet wordt toegestaan om bedrijfrekening te schrappen.
* **mDVA-30265** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - lost de kwestie op waar de lading het volgen verbinding na de verwezenlijking van de Factuur ophoudt te werken.
* **mDVA-28409** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - lost de kwestie op waar de `sales_clean_quotes` kroonbaan met *uit-van-geheugen* fout ontbreekt wanneer het aantal verlopen citaten in het gegevensbestand reusachtig is.
* **mDVA-30593** (*voor Adobe Commerce >=2.3.0 &lt;2.3.4*) - lost de kwestie op waar de citaten die volgens het plaatsen van het Leven van het Citaat verliepen niet worden schoongemaakt.
* **mDVA-30107** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6*) - lost de kwestie op waar de opslagschakelaar niet zoals verwacht werkt als verschillende basis URLs voor opslagmeningen wordt gebruikt.
* **MDVA-28763** (*voor Adobe Commerce >=2.3.2 &lt;2.3.4*) - lost de kwestie op waar het productbeeld na het bijwerken van productinformatie wordt gedupliceerd meer dan eens gebruikend REST API.
* **mDVA-30284** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost de kwestie op waar de indexator van het Onderzoek van de Catalogus wegens de volgende *[!DNL Elasticsearch]fout ontbreekt: de grens van totale gebieden in index is overschreden.*
* **mDVA-29042** (*voor Adobe Commerce >=2.3.3 &lt;=2.3.4-p2 met B2B uitbreiding*) - lost de kwestie op waar de toestemmingen van de Catalogus in *werden veranderd sta* automatisch toe nadat het nieuwe product aan de gedeelde catalogus werd toegevoegd.
* **MDVA-30428** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - lost de kwestie op waar de klanten geen product aan verlanglijst kunnen toevoegen als dit product aan een bron van de douaneinventaris wordt toegewezen.
* **mDVA-28661** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2 met B2B uitbreiding*) - lost de kwestie op waar een fout in de sectie van de het bedrijfrekening van de Gebruikers van het Bedrijf wordt geworpen nadat bedrijfbeheerder wordt veranderd.

## v1.0.4 {#v1-0-4}

* **MDVA-30195** (*voor Adobe Commerce 2.3.1 - 2.3.4-p2*) - lost de kwestie op waar de kanonnen banen ontbreken als gegevensbestandnaam te lang is, resulterend in categorieën die niet op het front-end worden bijgewerkt.
* **MDVA-30106** (*voor Adobe Commerce ^2.3.0*) - lost een kwestie op waar tijdens controlebetalingen niet met *wordt geladen kan bezit &quot;lengte&quot;van ongeldige* fout in console lezen JS.
* **mDVA-28656** (*voor Adobe Commerce >=2.3.1 &lt;2.3.6 || >=2.4.0 &lt;2.4.2*) - lost de kwestie op waar als een orde zonder vereiste betalingsinformatie (bijvoorbeeld, met 100% korting) werd geplaatst en een factuur voor de orde werd gecreeerd, verandert de ordestatus in *Gesloten* in plaats van Voltooid.
* **MDVA-30209** (*voor Adobe Commerce 2.3.0 - 2.3.3-p1*) - lost de kwestie op waar de klantengroep in gebrek werd veranderd als klant hun rekeningsinformatie bijwerkte.
* **mDVA-30123** (*voor Adobe Commerce >=2.3.4 &lt;2.4.2*) - lost de kwestie op waar de etiketten van de attributenoptie niet correct voor de vragen van GraphQL worden vertaald.
* **mDVA-2996** (*voor Adobe Commerce >=2.3.3 &lt;2.4.2*) - lost de kwestie op waar na het toelaten van categorietoestemming, de categoriepagina niet in het voorgeheugen ondergebracht wordt door het Volledige Geheime voorgeheugen van de Pagina.
* **mDVA-30164** (*voor Adobe Commerce >=2.3.1 &lt;2.4.2*) - lost de kwestie op waar de klantenverslagen niet uit het net van Klanten kunnen worden uitgevoerd als de attributen van de douaneklanten bestaan.
* **mDVA-30444** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1*) - lost de kwestie op waar geen bevestigingse-mail wordt verzonden voor geplaatste orden gebruikend GraphQL.
* **MDVA-30490** (*voor Adobe Commerce 2.3.4 - 2.3.5-p2*) - lost de kwestie op waar de productvergelijking de 500 foutenpagina werpt als één van de producten een lege korte beschrijving heeft.
* **mDVA-30232** (*voor Adobe Commerce >=2.3.1 &lt;2.4.1*) - lost de kwestie op waar het niet mogelijk is om opnieuw in orde te brengen als de originele orde een geschenkkaart bevat.
* **mDVA-29965** (*voor Adobe Commerce >=2.3.3 &lt;2.4.0*) - lost de kwestie op waar de klanten de Ongeldige fout van de Vorm krijgen wanneer het toevoegen van een product aan de kar.
* **MDVA-30008** (*voor Adobe Commerce >=2.3.0 &lt;2.4.2*) - lost het B2B probleem op waar het niet mogelijk is om orden door Admin API voor een product te plaatsen dat in een openbare catalogus is.
* **MDVA-22469** (*voor Adobe Commerce 2.3.2-p2 - 2.3.3-p1*) - lost de kwestie op waar na bevordering aan Adobe Commerce 2.3.3, de Bouwer van de Pagina niet in het Admin paneel werkt en sommige JS en CSS dossiers niet laden.
* **MC-35984** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - lost de kwestie op waar de handelaren niet met om het even welke paginaelementen op de pagina van Keert na het creëren van een verschepend etiket voor een Vergunning van de Koophandel (RMA) konden in wisselwerking staan.

## v1.0.3 {#v1-0-3}

* **MDVA-25602** (*voor Adobe Commerce 2.3.0 - 2.3.4*) - lost de kwestie met [!DNL PayPal Payflow Pro] betalingsmethode en behandelende koekjes als `SameSite=Lax` door gebrek in Chrome 80 browser en API reactie opnieuw richt aan klantenlogin pagina.
* **mDVA-26694** (*voor Adobe Commerce >=2.3.0 &lt;2.3.6 || 2.4.0*) - lost de kwestie met product en catalogusgeheime voorgeheugens op die dagelijks verlopen, hoewel gepland om anders te verlopen.
* **mDVA-27825** (*voor Adobe Commerce >=2.3.0 &lt;2.4.1*) - lost de kwestie op waar het uitvoeren van grote hoeveelheden gegevens wegens geheugenlek ontbrak.
* **mDVA-29085** (*voor Adobe Commerce >=2.3.0 &lt;=2.3.5-p1*) - lost de B2B kwestie op waar geen vereiste nieuwe bedrijfe-mails worden verzonden als een bedrijf door API wordt gecreeerd.
* **mDVA-29344** (*voor Adobe Commerce >=2.3.5 &lt;=2.4.0-p1*) - lost de kwestie op waar de Bouwer van de Pagina na het kopiëren van tekst van een kopbalelement aan een tekstelement vastloopt.
* **mDVA-29835** (*voor Adobe Commerce >2.3.1 &lt;2.4.2*) - lost de kwestie op waar de orden van de giftekaart twee codes in plaats één bevatten.
* **mDVA-30052** (*voor Adobe Commerce >=2.3.2-p2 &lt;2.3.5*) - lost de kwestie met privé inhoud (lokale opslag) op die niet correct wordt bevolkt, die in prestatiesproblemen resulteerde.
* **mDVA-30131** (*voor Adobe Commerce >=2.3.4 &lt;2.3.6 || 2.4.0*) - lost de kwestie met gelaagde navigatie op, waar *geen* waarde voor booleaanse de attributen van het typeproduct niet inbegrepen in gelaagde navigatie was als [!DNL Elasticsearch] als onderzoeksmotor werd gebruikt.
* **mDVA-35514** (*voor Adobe Commerce >=2.4.0 &lt;2.4.1*) - lost de kwestie met het creëren van een het verschepen etiket op en het toevoegen van bevolen producten aan een pakket in het Create modale venster van Pakketten.
