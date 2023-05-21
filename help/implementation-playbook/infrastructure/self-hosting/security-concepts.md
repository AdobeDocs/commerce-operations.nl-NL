---
title: Zelfhostingconcepten voor Adobe Commerce-beveiliging
description: Leer over zelf-ontvangende veiligheidsideeën en concepten en beste praktijken om te overwegen. Leer concepten zoals alleen-lezen bestandssysteem, malware scanning en vele andere onderwerpen die u in overweging kunt nemen bij het hosten van Adobe-handel.
landing-page-description: Leer enkele beveiligingsconcepten en -zaken die u in acht moet nemen wanneer u Adobe Commerce op uw eigen computer host.
short-description: Leer strategieën en beveiligingsconcepten voor het hosten van Adobe Commerce zelf.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: c4912f02-0411-466f-8c77-d610de9eb35d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1571'
ht-degree: 0%

---

# Beveiligingsconcepten

Veiligheid moet altijd een sterke overweging zijn voor alles wat verband houdt met een e-commerceproject. Zonder een sterke veiligheidshouding is het oppervlak dat aangevallen kan worden exponentieel groter. De voorgestelde concepten en ideeën bieden methoden waarvan is bewezen dat ze de algemene kwetsbaarheden verminderen die doorgaans worden benut.

De volgende concepten zijn niet in een bepaalde volgorde. Ze zijn bedoeld om ideeën en concepten te bieden die in overweging moeten worden genomen. Velen zijn vrij of zouden minimale opstelling en configuratie en verdere controle vereisen. Onderzoek deze onderwerpen buiten dit leerprogramma om ervoor te zorgen hebt u een diep genoeg inzicht in de concepten hier voorgesteld.

## Alleen-lezen bestandssysteem

Het concept van het alleen-lezen bestandssysteem is geleend van [Adobe Commerce over cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/cloud/1-overview.html){target="_blank"}. Hierdoor wordt één belangrijk gebied verwijderd dat door een slechte acteur wordt gebruikt. Vele exploits hebben voordeel gehaald uit het veranderen van een dossier dat naar verwachting in de toepassing van de Handel zal zijn om opsporing te vermijden. In plaats van er een te maken, wijzigt de slechte actor de inhoud van een bestaand bestand om een onverwachte actie uit te voeren. Als u het bestandssysteem alleen-lezen maakt, wordt deze aanvalsvector aanzienlijk kleiner.

## Gebruik TWO Factor Authentificatie en wachtwoordmanagers

U deelt nooit wachtwoorden. Elke admin gebruiker zou hun eigen rekening met juiste ACL moeten hebben. Zorg ervoor dat twee factor-identificatie nooit is uitgeschakeld of verwijderd. Als u admin toegang tot een derde verleent, zorg ervoor dat het wachtwoord door een wachtwoordmanager wordt geproduceerd en nooit opnieuw gebruikt.

## Malware scans

Malware-scans worden doorgaans gevonden bij een hostingprovider die probeert zich te specialiseren in Adobe Commerce. Deze bibliotheek van bekende malware en exploitaties is een steeds groeiende lijst aangezien de nieuwe bedreigingen worden ontdekt, verdrievoudigd, en gediagnosticeerd. Controleer of de hostingprovider over een dergelijke service beschikt en of deze automatisch of alleen op verzoek kan worden uitgevoerd. Er zijn ook diensten die u kunt intekenen op die hun eigen bibliotheek van bekende exploitaties kunnen gebruiken om uw handelstoepassing constant te controleren op exploitaties. Sommige hiervan zijn alleen extern, andere kunnen worden toegevoegd aan de infrastructuur voor een interne diepgaande scan van alle mappen, bestanden en zelfs de database. Er zijn een paar aanbieders met jarenlange ervaring op dit gebied, van Sansec.io tot Sucuri en natuurlijk van MageReport. Sommige zijn gratis, en sommige hebben een bijbehorende prijs. Het weten van dit is beschikbaar en het hebben van een doordacht gesprek met uw architect van Adobe Commerce en team DevOps zal u de juiste oplossing verzekeren.

## Site-brede analyse

De [Analyse voor de hele site](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html){target="_blank"} is een proactief zelfbedieningshulpmiddel en een centrale gegevensopslagplaats die gedetailleerde systeeminzichten en aanbevelingen omvat om de veiligheid en de operabiliteit van uw installatie van Adobe Commerce te verzekeren. Het biedt 24/7 real-time prestatiescontrole, rapporten, en advies om potentiële kwesties en betere zichtbaarheid in plaatsgezondheid, veiligheid, en toepassingsconfiguraties te identificeren. Het helpt de resolutietijd te verminderen en de stabiliteit en prestaties van de site te verbeteren.

## Instellingen voor registratie van beheeracties inschakelen en controleren

U vindt deze informatie nadat u zich hebt aangemeld bij de Adobe Commerce-beheerder en u hebt genavigeerd naar Opslag > Configuratie > Geavanceerd > Beheer > Logboekregistratie voor beheeracties. Dit verstrekt een lijst van gebeurtenissen die worden gecontroleerd en worden geregistreerd. Het is nuttig wanneer het doen van forensische analyse op een geëxploiteerde plaats, als het vermoeden hen toegang tot de beheerder van de Handel wordt verkregen. Dit registreren en rapport kan nuttig zijn om te zien welke gebeurtenissen de slechte actor uitvoerde. Als om het even welk logboek van admin acties gehandicapt is dat een teken dat iemand hen voor dekking kan onbruikbaar gemaakt hebben verwijdert het registreren wanneer het uitvoeren van bepaalde acties.

## Basingsserver voor SSH-toegang

Dit is moeilijker om uit te leggen dat de meeste onderwerpen in het leerprogramma van de Concepten van de Veiligheid. Het basisidee voor dit is een server te verstrekken die als middleman voor ssh toegang dienst doet. Op deze manier staan uw productieservers geen externe ssh-verbindingen toe. U kunt deze bastieserver tot stand brengen en een lokaal IP masker gebruiken om ervoor te zorgen dat slechts de aangewezen servers aan SSH in hen worden toegestaan.

## ACL rollen en toestemmingen van het overzicht

Elke admingebruiker van Adobe Commerce wordt toegewezen een ACL rol. Deze rol zou moeten worden gecreeerd om slechts de functionaliteit te verstrekken moet de baan uitvoeren. ACL rollen zouden vaak moeten worden geëvalueerd, om ervoor te zorgen zij niet meer gezag dan noodzakelijk verstrekken. Indien nodig, creeer vele ACL rollen met verantwoordelijkheden. Indien om een of andere reden toegang wordt verleend aan een derde, moeten zij zo spoedig mogelijk worden gedeactiveerd. Vraag hen hoe lang zij absoluut toegang en het plaatsen van een auto vervaldatum wanneer het creëren van hun admin gebruiker nodig hebben.

## Beheer gebruikers en SSH-gebruikerstoegang regelmatig controleren

Om ongewenste of onbevoegde het creëren van admin gebruiker te ontdekken, zou de lijst van admin gebruikers regelmatig moeten worden gecontroleerd. Een goede regel is om te controleren wie SSH en admin toegang tot de Adobe Commerce-toepassing heeft. Als nieuwe gebruikers worden gedetecteerd, schakelt u hun account uit en volgt u het beleid en de procedure van het bedrijf voor een dergelijk incident. Het is gemakkelijker om een gebruikerstoegang te herstellen dan het van een uitbuiten moet terugkrijgen.

## Database opschonen

Toegang tot productiegegevens beperken. Deze aangewezen teamgenoten zouden de capaciteit moeten hebben om productiedatabanken terug te trekken, en hen van echte gegevens te zuiveren. Als het verwijderen van de gegevens een optie is, verkort u de desbetreffende tabellen, zoals bestellingen, aanhalingstekens en klanten. Soms wilt u echter wel de volledige set gegevens, maar de waarden kunnen anoniem worden gemaakt. Dit geldt doorgaans in een testomgeving. Het is ook handig vóór upgrades. Door het echte volume van gegevens te hebben, maar anonymized verzekert u het testen en het bevestigen van de tijd om een plaatsing voor verbetering behoorlijk uit te voeren. Als u een beperkte reeks gegevens hebt, kunt u het verbeteringsproces en de timing onderschatten.

+++Voorbeeld van klanteninformatie willekeurig hier is een voorbeeld voor hoe te om klantene-mailadres met een willekeurige koord en al voornaam en laatste mane gebieden in sommige standaardlijsten te veranderen die Adobe Commerce gegevens opslaat. **Herinner me om alle lijsten voor gevoelige gegevens te controleren, is deze lijst niet allen inclusief aan de lijsten die klantengegevens kunnen opslaan**

```SQL
SET FOREIGN_KEY_CHECKS=0;
UPDATE customer_entity SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE email_contact SET email = REPLACE(email, SUBSTRING(email, LOCATE('@', email) +1), CONCAT(UUID(), '.com'));
UPDATE sales_invoice_grid SET customer_email = 'customer@example.com', customer_name  = 'Jack Smith';
UPDATE sales_order SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Smith', remote_ip = '127.0.0.1';
UPDATE sales_order_address SET region = 'Ohio', postcode = '12345-1234', lastname = 'Smith', street = '123 Main street', region_id = 44, city = 'Phoenix', telephone = NULL, firstname = 'Jane', company = NULL;
UPDATE sales_order_grid SET customer_email = 'customer@example.com', shipping_name = 'Jack', billing_name = 'Jack Smith', billing_address = '123 Main Street', shipping_address = '321 Pine Street', customer_name = 'Jane Smith';
UPDATE sales_shipment_grid SET customer_email = 'customer@example.com', customer_name = 'Jane Smith', billing_address = '123 Main street', billing_name = 'Jack Doe', shipping_name = 'Susie Smith';
UPDATE quote SET customer_email = 'customer@example.com', customer_firstname = 'Sally', customer_lastname = 'Jones', customer_dob = NULL, remote_ip = '127.0.0.1';
UPDATE quote_address SET email = 'customer@example.com', firstname = 'Jack', lastname = 'Smith', company = NULL, street = '123 Main st', city = 'AnyCity', region = 'Some State', region_id = 44, postcode = '12345-1234', telephone = NULL;
UPDATE magento_rma SET customer_custom_email = 'customer@example.com' WHERE customer_custom_email IS NOT NULL;
UPDATE customer_address_entity SET firstname = 'Jack', lastname = 'Smith', telephone = '909-555-1212', postcode = NULL,  region = NULL, street = '123 Main street', city = 'Anycity', company = NULL;
UPDATE customer_grid_flat SET name = 'Jane Doe', email = 'customer@example.com', dob = NULL, gender = NULL, taxvat = NULL, shipping_full = '', billing_full = '', billing_firstname = 'Jack', billing_lastname = 'Smith', billing_telephone = NULL, billing_postcode = NULL, billing_country_id = NULL, billing_region = NULL, billing_street = '123 Main street', billing_city = 'Anycity', billing_fax = NULL, billing_vat_id = NULL, billing_company = NULL;
UPDATE sales_creditmemo_grid SET billing_name = 'Sally', billing_address = '123 Main Street', customer_name = 'Jack Smith', customer_email = 'customer@example.com';
    
UPDATE magento_rma_grid SET customer_name = 'Jack Smith';
SET FOREIGN_KEY_CHECKS=1;
```

+++


+++U kunt tabellen ook afkappen in plaats van te proberen anonimiseren

```SQL
SET FOREIGN_KEY_CHECKS=0;
TRUNCATE customer_log;  
TRUNCATE customer_visitor;  
TRUNCATE magento_logging_event;
TRUNCATE oauth_consumer;
TRUNCATE oauth_nonce;
TRUNCATE oauth_token;
TRUNCATE password_reset_request_event;
TRUNCATE acknowledgement;
TRUNCATE acknowledgement_report;
TRUNCATE avatax_log;
TRUNCATE avatax_queue;
TRUNCATE cron_schedule;
SET FOREIGN_KEY_CHECKS=1;
```

+++

++ + verwijder volledig voorbeeld Hier is een voorbeeld voor het verwijderen van alle orders, aanhalingstekens, creditmemo&#39;s, en meer voorafgaand aan lancering of voor een lagere ontwikkelomgeving

```SQL
DELETE FROM `gift_message`;
DELETE FROM `inventory_reservation`;
DELETE FROM `quote`;
DELETE FROM `quote_address`;
DELETE FROM `quote_address_item`;
DELETE FROM `quote_id_mask`;
DELETE FROM `quote_item`;
DELETE FROM `quote_item_option`;
DELETE FROM `quote_payment`;
DELETE FROM `quote_shipping_rate`;
DELETE FROM `reporting_orders`;
DELETE FROM `sales_bestsellers_aggregated_daily`;
DELETE FROM `sales_bestsellers_aggregated_monthly`;
DELETE FROM `sales_bestsellers_aggregated_yearly`;
DELETE FROM `sales_creditmemo`;
DELETE FROM `sales_creditmemo_comment`;
DELETE FROM `sales_creditmemo_grid`;
DELETE FROM `sales_creditmemo_item`;
DELETE FROM `sales_invoice`;
DELETE FROM `sales_invoiced_aggregated`;
DELETE FROM `sales_invoiced_aggregated_order`;
DELETE FROM `sales_invoice_comment`;
DELETE FROM `sales_invoice_grid`;
DELETE FROM `sales_invoice_item`;
DELETE FROM `sales_order`;
DELETE FROM `sales_order_address`;
DELETE FROM `sales_order_aggregated_created`;
DELETE FROM `sales_order_aggregated_updated`;
DELETE FROM `sales_order_grid`;
DELETE FROM `sales_order_item`;
DELETE FROM `sales_order_payment`;
DELETE FROM `sales_order_status_history`;
DELETE FROM `sales_order_tax`;
DELETE FROM `sales_order_tax_item`;
DELETE FROM `sales_payment_transaction`;
DELETE FROM `sales_refunded_aggregated`;
DELETE FROM `sales_refunded_aggregated_order`;
DELETE FROM `sales_shipment`;
DELETE FROM `sales_shipment_comment`;
DELETE FROM `sales_shipment_grid`;
DELETE FROM `sales_shipment_item`;
DELETE FROM `sales_shipment_track`;
DELETE FROM `sales_shipping_aggregated`;
DELETE FROM `sales_shipping_aggregated_order`;
DELETE FROM `tax_order_aggregated_created`;
DELETE FROM `tax_order_aggregated_updated`;
DELETE FROM `magento_rma`;
DELETE FROM `magento_rma_grid`;
DELETE FROM `magento_rma_item_entity`;
DELETE FROM `magento_rma_status_history`;
DELETE FROM `magento_sales_creditmemo_grid_archive`;
DELETE FROM `magento_sales_invoice_grid_archive`;
DELETE FROM `magento_sales_order_grid_archive`;
DELETE FROM `magento_sales_shipment_grid_archive`;
DELETE FROM `sequence_creditmemo_0`;
DELETE FROM `sequence_creditmemo_1`;
DELETE FROM `sequence_creditmemo_2`;
DELETE FROM `sequence_creditmemo_7`;
DELETE FROM `sequence_invoice_0`;
DELETE FROM `sequence_invoice_1`;
DELETE FROM `sequence_invoice_2`;
DELETE FROM `sequence_invoice_7`;
DELETE FROM `sequence_order_0`;
DELETE FROM `sequence_order_1`;
DELETE FROM `sequence_order_2`;
DELETE FROM `sequence_order_7`;
DELETE FROM `sequence_rma_item_0`;
DELETE FROM `sequence_rma_item_1`;
DELETE FROM `sequence_rma_item_2`;
DELETE FROM `sequence_rma_item_7`;
DELETE FROM `sequence_shipment_0`;
DELETE FROM `sequence_shipment_1`;
DELETE FROM `sequence_shipment_2`;
DELETE FROM `sequence_shipment_7`;

## USE THE FOLLOWING WITH CAUTION - CAN CAUSE ISSUES WITH TAX/PAYMENT PROCESSORS IF YOU REUSE ORDER NUMBERS, ETC.

ALTER TABLE sequence_creditmemo_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_creditmemo_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_invoice_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_order_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_rma_item_7 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_0 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_1 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_2 AUTO_INCREMENT=1;
ALTER TABLE sequence_shipment_7 AUTO_INCREMENT=1;
```

+++

## Omgevingsvariabelen gebruiken

[!BADGE Alleen Adobe Commerce op cloud]{type=Informative}

Door omgevingsvariabelen te gebruiken, kunt u bepaalde waarden instellen die voor elke omgeving kunnen en moeten worden gewijzigd. U wilt bijvoorbeeld voor elke omgeving een andere URL voor de beheerder gebruiken. Door deze waarde in te stellen als een omgevingsvariabele kunt u deze configureren en zo nodig snel naar deze waarde verwijzen vanuit de interface van de cloud.

Meer informatie over dit onderwerp vindt u in het Experience League [Handel in omgevingsvariabelen van de cloudinfrastructuur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html){target="_blank"}

## Hulpprogramma&#39;s voor het scannen van kwetsbaarheden van software

De CI/CD pijpleiding kan een krachtig hulpmiddel zijn en helpen sommige taken automatiseren. Met name de mogelijkheid voor een ontwikkelaar om code toe te passen die exploiteerbaar kan zijn, is altijd een reële mogelijkheid. Peer coderevisies vangen dergelijke punten normaal, maar omdat het een mens is, gebeuren fouten. Geautomatiseerd scannen van code helpt de kans op onverwachte kwetsbaarheden in een nieuw geïntroduceerde functie te verminderen. Deze gereedschappen kunnen zelfs aanwezig zijn om het samenvoegen van code in de live codebase te blokkeren. Er zijn vele manieren en hulpmiddelen om geautomatiseerde codeveiligheid en kwaliteitsscans aan te bieden. Er kunnen robuuste, aangepaste gereedschappen zijn, maar deze vereisen constante updates en aanpassingen. U kunt ook proactief bijgewerkte gereedschappen toepassen, zoals synchroniseren.io en Amazon-codecontrole.

## Web Application Firewall

Een Firewall van de Toepassing van het Web of WAF zoals vaak wanneer het spreken aan DevOps of een ontvangende leverancier wordt gebruikt.

De Vuurmuren van de Toepassing van het Web (WAFs) verhinderen kwaadwillig verkeer plaatsen en netwerken in te gaan door verkeer tegen een reeks veiligheidsregels te filtreren. Het verkeer dat om het even welke regels teweegbrengt wordt geblokkeerd alvorens het uw plaatsen of netwerk kan beschadigen.

Adobe Commerce cloud WAF biedt een WAF-beleid met een regel die is ontworpen om uw Adobe Commerce-webtoepassingen te beschermen tegen een groot aantal aanvallen. Als u een optie voor zelfhosting kiest, is het vinden van een WAF-bestand en het configureren van de regels uw verantwoordelijkheid. Sommige hostingproviders en WAF-providers hebben een generieke set regels die een goed begin vormen, maar verwachten dat er wat werk wordt gedaan om uw project te laten functioneren.

WAF onderzoekt Web en admin verkeer om het even welke verdachte activiteit te identificeren. Het evalueert het verkeer van de GET en van de POST (de vraag van HTTP API) en past de regel toe die wordt geplaatst om te bepalen welk verkeer aan blok. WAF kan een grote verscheidenheid van aanvallen, met inbegrip van SQL injectieaanvallen, dwars-plaats scripting aanvallen, de aanvallen van de gegevensexfiltratie, en de protocolschendingen van HTTP blokkeren.

Als cloudgebaseerde service vereist de WAF geen hardware of software voor installatie of onderhoud. Ten slotte, een bestaande technologiepartner, verstrekt de software en de deskundigheid. Hun hoge prestaties, altijd-op WAF verblijven in elke geheim voorgeheugenknoop over het globale leveringsnetwerk van Fastly.

Lees voor meer informatie over de WAF op de Adobe Commerce over cloud die Fastly biedt de [Veelgestelde vragen over Adobe Commerce Knowledge Base](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/faq/web-application-firewall-waf-powered-by-fastly-the-faq.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
