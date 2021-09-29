---
title: Beveiliging van de cloud-infrastructuur
description: 'Meer informatie over hoe we Adobe Commerce op cloudinfrastructuur veilig houden. '
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1639'
ht-degree: 0%

---


# Beveiliging

De Adobe Commerce Pro planarchitectuur wordt ontworpen om een hoogst veilige omgeving te verstrekken. Elke klant wordt opgesteld in hun eigen geïsoleerde servermilieu, gescheiden van andere klanten. De beveiligingsdetails van de productieomgeving worden hieronder beschreven.

## Webbrowsers

The bulk of the traffic going in and out of the cloud environment comes from  consumers&#39; web browsers. Consumer traffic can be secured using HTTPS for all pages on the website (using either a shared SSL certification or the customer’s own SSL certificate for an additional fee). Checkout and account pages are always served using HTTPS. De beste manier is om alle pagina&#39;s onder HTTPS te bedienen.

## CDN (Content Delivery Network)

Verstrekt snel een CDN en verdeelde ontkenning van de dienst (DDoS) bescherming. De snelste CDN helpt directe toegang tot de oorspronkelijke servers te isoleren. Openbare DNS richt slechts aan het Fastly Netwerk. De snelste oplossing DDoS beschermt tegen hoogst ontwrichtende Laag 3 en Laag 4 aanvallen, evenals complexere Laag 7 aanvallen. Laag 7 de aanvallen kan worden geblokkeerd gebruikend douaneregels die op de volledige HTTP/HTTPS- verzoeken worden gebaseerd en op cliënt en verzoekcriteria, met inbegrip van kopballen, koekjes, verzoekweg, en cliëntIP, of indicatoren zoals geolocatie worden gebaseerd.

## Webtoepassingsfirewall (WAF)

De Snelle Firewall van de Toepassing van het Web (WAF) wordt gebruikt om extra bescherming te verstrekken. De op wolk gebaseerde WAF van Fastly gebruikt derderegels van commerciële en open-bronbronnen zoals de Ruleset van de Kern van OWASP. Bovendien zijn er specifieke regels voor de Adobe-handel. De klanten worden beschermd tegen zeer belangrijke toepassing-laag aanvallen, met inbegrip van injectieaanvallen en kwaadwillige input, dwars-plaats scripting, gegevensexfiltratie, het protocolschendingen van HTTP, en andere Hoogste 10 bedreigingen van OWASP.

De WAF-regels worden bijgewerkt door Adobe Commerce als er nieuwe kwetsbaarheden worden gedetecteerd, zodat Managed Services beveiligingsproblemen &quot;virtueel kan patchen&quot; voordat softwarepatches worden uitgevoerd. De Fastly WAF biedt geen diensten voor tariefbeperking of botdetectie. Indien gewenst kunnen klanten een licentie voor een service voor botdetectie van derden verkrijgen die compatibel is met Fastly.

## Virtual Private Cloud (VPC)

De productieomgeving van het Adobe Commerce Pro-plan is geconfigureerd als een Virtual Private Cloud (VPC) zodat productieservers geïsoleerd zijn en slechts beperkt in staat zijn om verbinding te maken met en uit de cloudomgeving. Alleen veilige verbindingen met de cloudservers zijn toegestaan. Beveiligde protocollen zoals SFTP of rsync kunnen worden gebruikt voor bestandsoverdracht.

Customers can use SSH tunnels to secure communications with the application. Toegang tot AWS PrivateLink kan tegen een extra vergoeding worden verleend. Alle verbindingen met deze servers worden gecontroleerd met behulp van AWS-beveiligingsgroepen, een virtuele firewall die verbindingen met de omgeving beperkt. De technische middelen van klanten kunnen tot deze servers toegang hebben gebruikend SSH.

## Versleuteling

Amazon Elastic Block Store (EBS) wordt gebruikt voor opslag. Alle EBS-volumes worden gecodeerd met het algoritme AES-265. Dit betekent dat de gegevens in rust worden gecodeerd. Het systeem codeert ook gegevens in doorvoer tussen CDN en de oorsprong, en tussen de oorspronkelijke servers. De wachtwoorden van de klant worden opgeslagen als knoeiboel. Sensitive credentials, including those for the payment gateway, are encrypted using the SHA-256 algorithm.

De toepassing van de Handel van de Adobe steunt kolom- of rij-vlakke encryptie of encryptie niet wanneer de gegevens in rust of niet in doorgang tussen servers zijn. De klant kan coderingssleutels beheren vanuit de toepassing. De sleutels die door het systeem worden gebruikt worden opgeslagen in het Zeer belangrijke Systeem van het Beheer AWS en moeten door Managed Services worden beheerd om delen van de dienst te verstrekken.

## Penetentietests

Managed Services voert regelmatig penetratietests uit van het Adobe Commerce-wolkensysteem met de out-of-the-box-toepassing. Klanten zijn verantwoordelijk voor eventuele penetratietests van hun aangepaste toepassing.

## Betalingsgateway

De Handel van de Adobe vereist de integratie van de betaalgateway waar de creditcardgegevens direct van browser van de consument aan de betaalgateway worden overgegaan. De kaartgegevens zijn nooit beschikbaar in de Adobe Commerce Pro-planomgevingen van Managed Services. Actions on the transactions by the ecommerce application are completed using a reference to the transaction from the gateway.

## Adobe Commerce-toepassing

Adobe test regelmatig de kerntoepassingscode op veiligheidskwetsbaarheid. Patches for defects and security issues are provided to customers. Het team van de Veiligheid van het Product bevestigt de producten van de Handel van de Adobe volgens de richtlijnen van de toepassingsveiligheid van OWASP. Verschillende hulpprogramma&#39;s voor beveiligingskwetsbaarheidsbeoordeling en externe leveranciers worden gebruikt om de naleving te testen en te controleren. Beveiligingsgereedschappen zijn:

- Statisch en dynamisch scannen van veracode
- Scannen naar RIPS-broncode
- De services voor het scannen van kwetsbaarheden van Trustwave en Alert Logic
- Burp Suite Pro
- OWASPZAP
- andSqlMap

De volledige codebasis wordt gescand met deze hulpmiddelen op een tweewekelijkse basis. Klanten worden op de hoogte gesteld van beveiligingspatches via directe e-mails, meldingen in de toepassing en in het [Beveiligingscentrum](https://magento.com/security).

Klanten moeten ervoor zorgen dat deze patches binnen 30 dagen na de release op hun aangepaste toepassing worden toegepast, volgens de PCI-richtlijnen. Adobe biedt ook een [Security Scan Tool](https://docs.magento.com/user-guide/magento/security-scan.html) waarmee verkopers hun sites regelmatig kunnen controleren en updates kunnen ontvangen over bekende beveiligingsrisico&#39;s, malware en onbevoegde toegang. Het hulpmiddel van de Scannen van de Veiligheid is de vrije dienst en kan op om het even welke versie van de Handel van de Adobe worden in werking gesteld.

Om veiligheidsonderzoekers aan te moedigen om kwetsbaarheid te identificeren en te melden, heeft de Handel van Adobe een [bug-bounty programma](https://hackerone.com/magento) naast interne het testen. Further, the customer is provided the full source code of the application for their own review if desired.

## Read-only file system

Alle uitvoerbare code wordt opgesteld in een read-only beeld van het dossiersysteem, dat dramatisch de oppervlakken vermindert die voor aanval beschikbaar zijn. Tijdens het implementatieproces wordt een Squash-FS-afbeelding gemaakt. This approach dramatically reduces opportunities to inject PHP or JavaScript code into the system or modify the Adobe Commerce application files.

## Externe implementatie

De enige manier om uitvoerbare code in de de productieomgeving van Managed Services te krijgen is het door een leveringsproces in werking te stellen. Dit betekent dat de broncode van uw bronopslagplaats moet worden overgebracht naar een externe opslagplaats die een implementatieproces start. De toegang tot dat plaatsingsdoel wordt gecontroleerd, zodat hebt u volledige controle over wie tot het plaatsingsdoel kan toegang hebben. Alle plaatsingen van toepassingscode aan het niet productiemilieu worden gecontroleerd door de klant.

## Logboekregistratie

Alle AWS-activiteiten zijn aangemeld bij AWS CloudTrail. Linux-, toepassingsserver- en databaselogboeken worden opgeslagen op de productieservers en opgeslagen in back-ups. Alle wijzigingen in de broncode worden vastgelegd in een Git-opslagplaats. De geschiedenis van de plaatsing is beschikbaar in de Handel [Interface van het Web van het Project ](https://devdocs.magento.com/cloud/project/projects.html#login). Alle ondersteuningstoegang wordt geregistreerd en de steunzittingen worden geregistreerd.

## Gevoelige gegevens

Gevoelige gegevens kunnen betrekking hebben op persoonlijke informatie van consumenten of vertrouwelijke gegevens van Managed Services-klanten. De bescherming van gevoelige gegevens van klanten en consumenten is een essentiële verplichting voor Adobe Commerce Managed Services. Zowel Managed Services als onze klanten hebben wettelijke verplichtingen over persoonlijk identificeerbare informatie. Naast de veiligheidseigenschappen van de architectuur, zijn er andere controles om de distributie en de toegang tot gevoelige gegevens te beperken.

De klanten hebben hun gegevens en hebben controle over waar die gegevens zullen worden gevestigd. De klant geeft de locatie op waar de productie- en ontwikkelingsinstanties zich bevinden. Zij specificeren ook welke plaats voor de milieu van de Magento Business Intelligence (MBI) samen met Handel zal worden gebruikt, en als die toepassing MBI toegang tot persoonlijk identificeerbare informatie heeft of niet. Productie-instanties kunnen zich in de meeste AWS-regio&#39;s bevinden, terwijl ontwikkelings- en MBI-omgevingen momenteel in de Verenigde Staten of in de Europese Unie kunnen worden gevonden.

Gevoelige gegevens kunnen door het Fastly CDN servernetwerk overgaan maar worden niet opgeslagen in het Fastly netwerk. Alle partners die deel uitmaken van de Adobe Commerce Managed Services hebben contractuele verplichtingen om de bescherming van gevoelige gegevens te waarborgen. Managed Services will not move sensitive customer or consumer data from the locations specified by the customer.

As part of providing the services included in the Adobe Commerce Managed Services offering, Managed Services staff requires access to production systems that contain sensitive data. These employees are trained on their obligations to protect sensitive customer and consumer data. De toegang tot deze systemen is beperkt tot werknemers die toegang vereisen. Deze werknemers hebben slechts toegang voor de tijd nodig om deze diensten te leveren.

## Algemene verordening inzake gegevensbescherming (GDPR)

GDPR is a legal framework that sets guidelines for the collection and processing of personal information for individuals in the European Union (EU). Deze regels gelden ongeacht de vestigingsplaats van de site en EU-bezoekers hebben er toegang toe.

In wezen moeten bezoekers op de hoogte worden gesteld van de gegevens die de site bij hen verzamelt en moeten zij uitdrukkelijk instemmen met het verzamelen van informatie. De sites moeten bezoekers op de hoogte stellen als de persoonsgegevens van de site worden geschonden.

The merchant or company operating the site must also have a dedicated Data Protection Officer who oversees the site’s data security, and this individual (or website management team) should be available for contact should a visitor request that their data be erased.

De GDPR dringt er ook op aan dat alle persoonlijk identificeerbare informatie (zoals namen, ras en geboortedatum) die is verzameld, geanonimiseerd of pseudoniem wordt gemaakt.

>[!NOTE]
>
> Deze pagina is gewoon bedoeld als een algemeen overzicht van wat u in overweging moet nemen voor GDPR. Raadpleeg voor meer informatie uw juridische adviseur of raadpleeg de [officiële tekst](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Back-ups

De steun wordt uitgevoerd elk uur voor de laatste 24 uren van verrichting. Na de periode van 24 uur, worden de steunen behouden op het volgende programma, gebruikend de dienst van de Momentopname van AWS EBS:

| Tijdsperiode | Herstelbeleid |
|----------------|-------------------------|
| Dagen 1 t/m 3 | Elke back-up |
| dagen 4 tot 6 | Eén back-up per dag |
| Week 2 tot en met 6 | Eén back-up per week |
| Week 8 t/m 12 | Eén tweewekelijkse back-up |
| Week 12 t/m 22 | Eén back-up per maand |

This creates an independent backup on redundant storage. Omdat de EBS-volumes gecodeerd zijn, worden de back-ups ook gecodeerd. Bovendien voert Managed Services op verzoek back-ups uit.

Uw Adobe Commerce Managed Services-back-up- en herstelbenadering maakt gebruik van een architectuur met hoge beschikbaarheid in combinatie met back-ups op volledig systeem. Elk project wordt herhaald—alle gegevens, code, en activa-over drie afzonderlijke AWS beschikbaarheidsstreken; elke zone met een afzonderlijk datacenter.
