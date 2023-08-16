---
title: Beveiliging van cloudinfrastructuur
description: Meer informatie over hoe we Adobe Commerce veilig houden op de cloudinfrastructuur.
exl-id: cd5d1106-c8db-4b70-b1c7-12378d7d77a7
feature: Cloud, Security
source-git-commit: d05629ef21608a017cfbbfcf05e9507375689fa2
workflow-type: tm+mt
source-wordcount: '1689'
ht-degree: 0%

---

# Beveiliging

De Adobe Commerce Pro-planarchitectuur is ontworpen om een zeer veilige omgeving te bieden. Elke klant wordt opgesteld in hun eigen geïsoleerde servermilieu, gescheiden van andere klanten. De beveiligingsdetails van de productieomgeving worden hieronder beschreven.

## Webbrowsers

Het grootste deel van het verkeer dat in en uit de wolkenomgeving gaat, komt van de webbrowsers van de consument. Consumentenverkeer kan worden beveiligd met HTTPS voor alle pagina&#39;s op de website (met behulp van een gedeelde SSL-certificering of het eigen SSL-certificaat van de klant voor een extra vergoeding). Afhandelings- en accountpagina&#39;s worden altijd via HTTPS verzonden. De beste manier is om alle pagina&#39;s onder HTTPS te bedienen.

## CDN (Content Delivery Network)

Verstrekt snel een CDN en verdeelde ontkenning van de dienst (DDoS) bescherming. De snelste CDN helpt directe toegang tot de oorspronkelijke servers te isoleren. Openbare DNS richt slechts aan het Fastly Netwerk. De snelste oplossing DDoS beschermt tegen hoogst ontwrichtende Laag 3 en Laag 4 aanvallen, evenals complexere Laag 7 aanvallen. Laag 7 de aanvallen kan worden geblokkeerd gebruikend douaneregels die op de volledige HTTP/HTTPS- verzoeken worden gebaseerd en op cliënt en verzoekcriteria, met inbegrip van kopballen, koekjes, verzoekweg, en cliëntIP, of indicatoren zoals geolocatie worden gebaseerd.

## Webtoepassingsfirewall (WAF)

De Snelle Firewall van de Toepassing van het Web (WAF) wordt gebruikt om extra bescherming te verstrekken. De op wolk gebaseerde WAF van Fastly gebruikt derderegels van commerciële en open-bronbronnen zoals de Ruleset van de Kern OWASP. Bovendien zijn er specifieke Adobe Commerce-regels. De klanten worden beschermd tegen zeer belangrijke toepassing-laag aanvallen, met inbegrip van injectieaanvallen en kwaadwillige input, dwars-plaats scripting, gegevensexfiltratie, het protocolschendingen van HTTP, en andere Hoogste 10 bedreigingen van OWASP.

De WAF-regels worden door Adobe Commerce bijgewerkt als er nieuwe kwetsbaarheden worden gedetecteerd waardoor Managed Services beveiligingsproblemen &quot;virtueel patcheert&quot; voordat softwarepatches worden uitgevoerd. De Fastly WAF biedt geen diensten voor tariefbeperking of botdetectie. Indien gewenst kunnen klanten een licentie voor een service voor botdetectie van derden verkrijgen die compatibel is met Fastly.

## Virtual Private Cloud (VPC)

De productieomgeving van het Adobe Commerce Pro-plan is geconfigureerd als een Virtual Private Cloud (VPC), zodat productieservers geïsoleerd zijn en slechts beperkt in staat zijn om verbinding te maken met en uit de cloud-omgeving. Alleen veilige verbindingen met de cloudservers zijn toegestaan. Beveiligde protocollen zoals SFTP of rsync kunnen worden gebruikt voor bestandsoverdracht.

De klanten kunnen de tunnels van SSH gebruiken om mededelingen met de toepassing te beveiligen. Voor toegang tot AWS Private Link kan een extra bedrag worden betaald. Alle verbindingen met deze servers worden gecontroleerd met behulp van AWS-beveiligingsgroepen, een virtuele firewall die verbindingen met de omgeving beperkt. De technische middelen van klanten kunnen tot deze servers toegang hebben gebruikend SSH.

## Versleuteling

Amazon Elastic Block Store (EBS) wordt gebruikt voor opslag. Alle EBS-volumes worden gecodeerd met het algoritme AES-265. Dit betekent dat de gegevens in rust worden gecodeerd. Het systeem codeert ook gegevens in doorvoer tussen CDN en de oorsprong, en tussen de oorspronkelijke servers. De wachtwoorden van de klant worden opgeslagen als knoeiboel. Gevoelige geloofsbrieven, met inbegrip van die voor de betaalgateway, worden gecodeerd gebruikend het algoritme SHA-256.

De Adobe Commerce-toepassing biedt geen ondersteuning voor codering of codering op kolom- of rijniveau wanneer de gegevens niet in rust zijn of niet worden verzonden tussen servers. De klant kan coderingssleutels beheren vanuit de toepassing. Toetsen die door het systeem worden gebruikt, worden opgeslagen in het AWS Key Management System en moeten door Managed Services worden beheerd om onderdelen van de service te kunnen leveren.

## Detectie van eindpunten en respons

[!DNL CrowdStrike Falcon], een licht-gewicht, volgende-generatie eindpuntopsporing en reactie (EDR) agent die op alle eindpunten (met inbegrip van servers) binnen Adobe geïnstalleerd is, beschermt onze gegevens en onze systemen met ononderbroken controle en inzameling in real time die ons toelaat om aan bedreigingen snel te identificeren en te antwoorden.

## Penetentietests

Managed Services voert regelmatig penetratietests uit van het Adobe Commerce-wolkensysteem met behulp van de out-of-the-box-toepassing. Klanten zijn verantwoordelijk voor eventuele penetratietests van hun aangepaste toepassing.

## Betalingsgateway

Adobe Commerce vereist integratie van betaalgateway, waarbij creditcardgegevens rechtstreeks van de browser van de consument naar de betaalgateway worden doorgegeven. De kaartgegevens zijn nooit beschikbaar in een van de Adobe Commerce Pro Plan Managed Services-omgevingen. De acties op de transacties door de toepassing van de Handel worden voltooid gebruikend een verwijzing naar de transactie van de gateway.

## Adobe Commerce-toepassing

De Adobe test regelmatig de kerntoepassingscode op veiligheidskwetsbaarheid. Patches voor defecten en beveiligingsproblemen worden aan klanten geleverd. Het team van de Veiligheid van het Product valideert de producten van Adobe Commerce volgens de richtlijnen van de toepassingsveiligheid van OWASP. Verschillende hulpprogramma&#39;s voor beveiligingskwetsbaarheidsbeoordeling en externe leveranciers worden gebruikt om de naleving te testen en te controleren. Beveiligingsgereedschappen zijn onder meer:

- Statisch en dynamisch scannen van veracode
- Scannen naar RIPS-broncode
- Trustwave en Alert Logic&#39;s kwetsbaarheidsscanservices
- Burp Suite Pro
- OWASPZAP
- andSqlMap

De volledige codebasis wordt gescand met deze hulpmiddelen op een tweewekelijkse basis. Klanten worden via directe e-mail op de hoogte gesteld van beveiligingspatches, via meldingen in de toepassing en in de [Beveiligingscentrum](https://magento.com/security).

Klanten moeten ervoor zorgen dat deze patches binnen 30 dagen na de release op hun aangepaste toepassing worden toegepast, volgens de PCI-richtlijnen. Adobe biedt ook een [Beveiligingsscan](https://docs.magento.com/user-guide/magento/security-scan.html) dat verkopers toelaat om hun plaatsen regelmatig te controleren en updates over bekende veiligheidsrisico&#39;s, malware, en onbevoegde toegang te ontvangen. Het hulpprogramma Beveiligingsscan is gratis en kan worden uitgevoerd op elke versie van Adobe Commerce.

Adobe Commerce heeft een [programma voor foutopsporing](https://hackerone.com/magento) naast interne tests. Bovendien wordt de klant de volledige broncode van de toepassing verstrekt voor hun eigen overzicht indien gewenst.

## Alleen-lezen bestandssysteem

Alle uitvoerbare code wordt opgesteld in een read-only beeld van het dossiersysteem, dat dramatisch de oppervlakken vermindert die voor aanval beschikbaar zijn. Tijdens het implementatieproces wordt een Squash-FS-afbeelding gemaakt. Deze aanpak beperkt de mogelijkheden om PHP- of JavaScript-code in het systeem te injecteren of om de Adobe Commerce-toepassingsbestanden te wijzigen aanzienlijk.

## Externe implementatie

De enige manier om uitvoerbare code in de de productieomgeving van Managed Services te krijgen is het door een leveringsproces in werking te stellen. Dit betekent dat de broncode van uw bronopslagplaats moet worden overgebracht naar een externe opslagplaats die een implementatieproces start. De toegang tot dat plaatsingsdoel wordt gecontroleerd, zodat hebt u volledige controle over wie tot het plaatsingsdoel kan toegang hebben. Alle plaatsingen van toepassingscode aan het niet productiemilieu worden gecontroleerd door de klant.

## Logboekregistratie

Alle AWS-activiteiten zijn aangemeld bij AWS CloudTrail. Linux-, toepassingsserver- en databaselogboeken worden opgeslagen op de productieservers en opgeslagen in back-ups. Alle wijzigingen in de broncode worden vastgelegd in een Git-opslagplaats. Implementatiegeschiedenis is beschikbaar in de Adobe Commerce [Projectwebinterface](https://devdocs.magento.com/cloud/project/projects.html#login). Alle ondersteuningstoegang wordt geregistreerd en de steunzittingen worden geregistreerd.

## Gevoelige gegevens

Gevoelige gegevens kunnen betrekking hebben op persoonlijke informatie van consumenten of vertrouwelijke gegevens van Managed Services-klanten. De bescherming van gevoelige gegevens van klanten en consumenten is een essentiële verplichting voor Adobe Commerce Managed Services. Zowel Managed Services als onze klanten hebben wettelijke verplichtingen met betrekking tot persoonlijk identificeerbare informatie. Naast de veiligheidseigenschappen van de architectuur, zijn er andere controles om de distributie en de toegang tot gevoelige gegevens te beperken.

De klanten hebben hun gegevens en hebben controle over waar die gegevens zullen worden gevestigd. De klant geeft de locatie op waar de productie- en ontwikkelingsinstanties zich bevinden. Zij geven ook aan welke locatie zal worden gebruikt voor de Adobe Commerce Reporting environment in combinatie met Commerce, en of die Adobe Commerce Reporting application al dan niet toegang heeft tot persoonlijk identificeerbare informatie. Productie-instanties kunnen zich in de meeste AWS-regio&#39;s bevinden, terwijl ontwikkelings- en Adobe Commerce-rapportageomgevingen op dit moment zowel in de Verenigde Staten als in de Europese Unie te vinden zijn.

Gevoelige gegevens kunnen door het Fastly CDN servernetwerk overgaan maar worden niet opgeslagen in het Fastly netwerk. Alle partners die deel uitmaken van het Adobe Commerce Managed Services-aanbod hebben contractuele verplichtingen om de bescherming van gevoelige gegevens te waarborgen. Managed Services verplaatst geen gevoelige klant- of consumentengegevens van de door de klant opgegeven locaties.

Als onderdeel van de dienstverlening in het aanbod van Adobe Commerce Managed Services, vereist het personeel van Managed Services toegang tot productiesystemen die gevoelige gegevens bevatten. Deze werknemers worden opgeleid over hun verplichtingen om gevoelige klant en consumentengegevens te beschermen. De toegang tot deze systemen is beperkt tot werknemers die toegang vereisen. Deze werknemers hebben slechts toegang voor de tijd nodig om deze diensten te leveren.

## Algemene verordening inzake gegevensbescherming (GDPR)

De GDPR is een juridisch kader dat richtsnoeren vaststelt voor het verzamelen en verwerken van persoonsgegevens voor personen in de Europese Unie (EU). Deze regels gelden ongeacht de vestigingsplaats van de site en EU-bezoekers hebben er toegang toe.

In wezen moeten bezoekers op de hoogte worden gesteld van de gegevens die de site bij hen verzamelt en moeten zij uitdrukkelijk instemmen met het verzamelen van informatie. De sites moeten bezoekers op de hoogte stellen als de persoonsgegevens van de site worden geschonden.

De handelaar of het bedrijf dat de site exploiteert, moet ook beschikken over een speciale functionaris voor gegevensbescherming die toezicht houdt op de gegevensbeveiliging van de site, en deze persoon (of het team van websitebeheer) moet beschikbaar zijn voor contact indien een bezoeker verzoekt zijn gegevens te wissen.

De GDPR dringt er ook op aan dat alle persoonlijk identificeerbare informatie (zoals namen, ras en geboortedatum) die is verzameld, geanonimiseerd of pseudoniem wordt gemaakt.

>[!NOTE]
>
> Deze pagina is gewoon bedoeld als een algemeen overzicht van wat u in overweging moet nemen voor GDPR. Voor meer informatie raadpleegt u uw juridisch adviseur of raadpleegt u de[officiële tekst](https://eur-lex.europa.eu/eli/reg/2016/679/oj).

## Back-ups

De steun wordt uitgevoerd elk uur voor de laatste 24 uren van verrichting. Na de periode van 24 uur worden back-ups volgens het volgende schema bewaard, waarbij de service AWS EBS Snapshot wordt gebruikt:

| Tijdsperiode | Herstelbeleid |
|----------------|-------------------------|
| Dagen 1 t/m 3 | Elke back-up |
| dagen 4 tot 6 | Eén back-up per dag |
| Week 2 tot 6 | Eén back-up per week |
| Week 8 t/m 12 | Eén tweewekelijkse back-up |
| Week 12 t/m 22 | Eén back-up per maand |

Hierdoor wordt een onafhankelijke back-up van redundante opslag gemaakt. Omdat de EBS-volumes gecodeerd zijn, worden de back-ups ook gecodeerd. Bovendien voert Managed Services op verzoek back-ups uit.

Voor uw Adobe Commerce Managed Services-back-up- en herstelaanpak wordt een architectuur met hoge beschikbaarheid gebruikt, gecombineerd met back-ups op volledig systeem. Elk project wordt herhaald—alle gegevens, code, en activa-over drie afzonderlijke de beschikbaarheidsstreken van AWS; elke streek met een afzonderlijk gegevenscentrum.
