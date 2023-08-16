---
title: Zelfhostingprogramma's voor Adobe Commerce-bewaking
description: Leer over zelf-ontvangende controlehulpmiddelen ideeën en concepten en beste praktijken om te overwegen.
landing-page-description: Leer een aantal concepten en zaken van controlehulpmiddelen om te overwegen wanneer het ontvangen van Adobe Commerce op uw te houden.
short-description: Leer strategieën en concepten van controlehulpmiddelen voor het hosten van Adobe Commerce zelf.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 728e9439-63d0-4481-b014-7ba2ce97b9d0
feature: Install, Logs, Observability
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---

# Zelfhostende Adobe Commerce Monitoring-telemetrie en -tools

Het gebruiken van controlehulpmiddelen staat voor kansen toe om veranderingen te ontdekken zonder het moeten iemand betalen om alles de hele tijd te letten. Met de meeste gereedschappen kunt u waarschuwingen en meldingen toevoegen als aan een drempelwaarde wordt voldaan, zoals een harde schijf zonder voldoende ruimte. Sommige hulpmiddelen verstrekken output die zou moeten worden gevolgd en worden berekend, zoals de resultaten van de ladingstest. Elk gereedschap heeft ongeacht het doel en wanneer het op consistente wijze wordt gebruikt, kunt u het programma beter beheren. Er zijn vrije opties aan elk hulpmiddel, maar herinner dat het betalen voor de dienst vaak een snellere betrouwbaardere steun verzekert en de investering waard kan zijn. New Relic is een voorbeeld van een tool die een gratis versie en een betaalde versie biedt die veel meer kracht en mogelijkheden ontsluit. Er zijn andere zoals DataDog of Dynatrace. Zoek een goede optie voor u en gebruik deze consistent.

## Infrastructuurbewaking

De term infrastructuur wordt in deze context vrij losjes gebruikt. Voor dit onderwerp, betekent dit om het even welke server, proces, of apparaat dat wordt gebruikt om de plaats in werking te stellen. Bijvoorbeeld:

* Harde schijven
* CPU-gebruik
* RAM-gebruik
* Redis
* Gemiddelde belasting per server
* netwerkverkeer

Onderzoeksdrempels om efficiënte alarm te bouwen. Wijs er geen toe voor belangrijke zaken zoals de capaciteit van de harde schijf. Stel een paar in om verschillende groepen op de hoogte te stellen als de zaken verslechteren. Hier volgt bijvoorbeeld een set regels wanneer een vaste schijf vol raakt.

* 70% Slack melding aan het DevOps-kanaal
* 80% Melden de ruimte DevOps van de Slack en een lijst van de e-maildistributie van teamgenoten DevOps
* 90% meldt Slack DevOps kanaal en de Slack van de productiesupport, de distributiegroep van DevOps van e-mail en de techniekmanager
* 95% meldt Slack DevOps en de kanalen van de Slack van de productiesteun, de lijst van de e-maildistributie van alle ingenieurs en Director van techniek
* 98% waarschuwt om het even welke kanalen van de P1 Slack en DevOps en de kanalen van de Slack van de productiesteun, e-maildistributielijst van ingenieurs en Director van techniek en VP van technologie

Er zijn vele manieren om een team op de hoogte te brengen, zodat zorg ervoor u kiest die betrouwbaar is en niet met teveel alarm zal overstroomd worden. Het is belangrijk om waarschuwingen te reserveren voor wanneer het belangrijk is, anders loopt u het risico overweldigd te worden en waarschuwingen te negeren.

Er zijn vaak goede sjablonen die u kunt volgen voor de meeste gereedschappen, zoals New Relic, DataDog en Dynatrace. Neem de tijd om goede ideeën te vinden die het meest zinvol zijn voor uw toepassing. Met Adobe Commerce op cloudinfrastructuur zijn er waarschuwingen en triggers beschikbaar wanneer het project wordt ingericht. Dit machtigt het de productiesupteam van de Adobe om hun hulpmiddelen voor uptime en hoge beschikbaarheidscontrole toe te passen.

De dashboards verlenen snelle toegang tot de frequente of belangrijke aspecten van uw plaats. De punten van het dashboard kunnen uit paginameningen, gebruik van cpu per gastheer, lijst van alle servers, de tijden van de paginading, transactieduur, en zelfs synthetische controletestresultaten voor de afgelopen dagen bestaan. Deze dashboards zouden moeten worden gebouwd om snelle triage toe te staan als iets verkeerd is, of verschillende dashboards opstelling voor verschillende gebruikerservaring. Hopelijk kunt u verschillende dashboards ontwerpen en genieten van het zien van uw toepassing controle in echt - tijd. Het is zeer bevredigend, vooral wanneer gevraagd door de eigenaar van het project of een manager hoe de plaats werkt, en u kunt het antwoord in seconden, niet uren vinden.

## Logboekaggregatie en -rotatie

Logbestanden worden gevonden op toepassingsservers die aanvragen verwerken of MySQL-logbestanden wanneer de uitvoering te lang duurt. Het lastige aan logboeken is dat zij van elkaar en het vinden van elk van hen gescheiden zijn, kan het ontleden van de informatie van elk logboek omslachtig zijn. Vele jaren geleden werd dit probleem opgelost met behulp van een techniek die _logboeksamenvoeging_. Dit neemt logboekdossiers van al uw logboekplaatsen duwen hen aan een gecentraliseerde plaats. Nadat de gegevens zijn verplaatst, kan een stuk software deze lezen en methoden bieden voor het zoeken, filteren en reviseren van de gegevens. Dit kan een lastig proces zijn om goed te worden. Er zijn veel opties, maar als u geluk hebt, kunnen uw controlehulpmiddelen uw logboekdossiers, zoals New Relic lezen en samenvoegen. Door een goed hulpmiddel te vinden, kunt u zich een onmetelijke hoeveelheid tijd in de toekomst besparen. Tenzij u slechts één enkele server hebt die alles doet om uw plaats in werking te stellen en in werking te stellen, is het hebben van logboeksamenvoeging essentieel. Dit is vooral nuttig wanneer het proberen om te weten te komen als u onder een aanval DDoS bent of een wettige verkeerspiek ervaren, of wanneer het onderzoeken van waarom een bepaald verzoek ontbreekt.

Een ander belangrijk onderdeel voor logbestanden is ervoor te zorgen dat rotatie plaatsvindt. Dit is historisch gezien `run-away logs` die uw vaste schijf per ongeluk kunnen vullen en de site naar beneden kunnen laten gaan. Een versie van logboekomwenteling kan voorkomen wanneer een logboekdossier een bepaalde grootte, zoals 1 GB bereikt. Er zijn gereedschappen op serverniveau, zoals `logrotate` die ze automatisch kunnen verwijderen. Zo kunnen uitzonderlijk grote logbestanden worden verwijderd als deze groter zijn dan 1 GB of als logbestanden ouder zijn dan 90 dagen. U bepaalt een logboekbeleid, zodat is het belangrijk om uw middelbeperkingen te begrijpen.

## Malware scans

Veel hostingbedrijven voor websites die gewijd zijn aan Adobe Commerce, beschikken over een bibliotheek met bekende misbruiken en malware. Ze moeten automatisch of op verzoek een scan aanbieden. Waar deze doeltreffend zijn, zijn ze reactionair en werken ze alleen als er nieuwe malware wordt gedetecteerd. Het kan een goed idee zijn om een pro-actief hulpmiddel te hebben dat de code en het gegevensbestand voor bekende malware kan bekijken. Er zijn enkele opties beschikbaar, zoals [MageReport](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"}, or [Magento Malware Scanner](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Ze kunnen een externe scan vanaf de buitenkant uitvoeren of proactief worden geïnstalleerd en bijgewerkt, scannen en controleren nadat ze zijn ingesteld op de servers. Dit kan een grote optie zijn, aangezien de bibliotheek constant wordt bijgewerkt omdat zij geïnstalleerd en duizenden plaatsen controleren als u een verstrekte oplossing zoals Sansec kiest. Aangezien een nieuwe malware wordt ontdekt, elk project dat zij controleren voordelen van de informatie en nu zal worden gealarmeerd als het wordt ontdekt.

Er zijn een paar vrije versies om te overwegen maar voor malware, zou u echt een betaalde oplossing moeten overwegen. Dit kan een verschil zijn tussen enkele minuten en enkele maanden wanneer uw site geïnfecteerd is. Omdat een uitbuiten op uw plaats enorme hoofdpijnen veroorzaakt, is dit één gebied u zou moeten overwegen voor de dienst te betalen.

## Analyse voor de hele site Adoben

Het hulpprogramma voor analyse van de hele site is een proactief zelfbedieningshulpmiddel en een centrale opslagplaats dat gedetailleerde systeeminzichten en aanbevelingen bevat om de veiligheid en de operabiliteit van uw Adobe Commerce-installatie te garanderen. Het biedt 24/7 real-time prestatiescontrole, rapporten, en advies om potentiële kwesties en betere zichtbaarheid in plaatsgezondheid, veiligheid, en toepassingsconfiguraties te identificeren. Het helpt de resolutietijd te verminderen en de stabiliteit en prestaties van de site te verbeteren.

De Recommendations-pagina van het hulpprogramma voor analyse voor de hele site bevat aanbevelingen op basis van aanbevolen procedures voor het oplossen van problemen die op uw site zijn aangetroffen. De aanbevelingen worden gesorteerd door prioritaire PO aan P4, waar PO kritiek is en P4 laag is. De bevindingen omvatten een beschrijving, een aanbeveling, een impact op de site, de hoofdoorzaak, scenario&#39;s/voorwaarden, het verwachte resultaat en de gebruikte gereedschappen.

Leer meer over de beste werkwijzen om de prestaties van uw site te verbeteren. Houd de aanbevelingen bij en implementeer ze als prioriteit.

Ga voor meer informatie over het installeren van deze installatie op uw project naar [Installatiehandleiding voor analysefuncties voor de hele site](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## SSL-bewaking

Een van de meer vergeten items voor een project is het SSL-certificaat. Ze hebben maar één keer per jaar aandacht nodig, dus het is heel eenvoudig om ze te vergeten. Het verlopen van uw beveiligingscertificaat kan leiden tot een waarschuwing in moderne browsers of een weigering om de pagina&#39;s op uw site weer te geven. Klanten kunnen e-mails of ondersteuning beginnen te verzenden als ze een dergelijk probleem ervaren en u kunt mogelijk pas werken als dit probleem is opgelost. Elke minuut telt, dus het erkennen van de vervaldatum komt voor tijd en het ervoor zorgen dat de dingen worden vernieuwd is van het grootste belang om de site draaiend te houden. Er zijn vele manieren om SSL controle te verwezenlijken. Overweeg synthetische controlehulpmiddelen voor uw plaats te gebruiken, gebruikend vrije of goedkope hulpmiddelen zoals het VK, Keyborst of Sucuri en zelfs aan de dienst in te schrijven die SSL certificaatvervalalarm aanbiedt. Met deze eenvoudige gereedschappen kunt u ervoor zorgen dat uw sitecertificaten geldig zijn en het risico op downtime voor uw klanten verminderen.

## Automatisch testen

Het uitvoeren van geautomatiseerde tests zoals functionele tests of eenheidstests helpt vaak om kwesties van onlangs geïntroduceerde code te ontdekken. Deze tests kunnen niet alles vangen, aangezien Adobe Commerce en eenheidstests typisch minder dan 50% dekking zijn. Dit betekent niet dat u ze niet hoeft te schrijven en te testen. Deze hulpmiddelen zijn hier om een andere laag van veiligheid en veiligheid toe te voegen die alles wordt begaan niet nadelig beïnvloedt uit de doos en om het even welke douanetests uw ontwikkelingsteam creeert. Door deze tests bij elke implementatie uit te voeren, worden belangrijke problemen vroegtijdig opgepakt en wordt vermeden dat het mogelijk wordt om de producten te produceren.

De tests van de lading kunnen uitdagend zijn om het goed te krijgen. Veel van de complexiteit is het gevolg van de manier waarop de frontend wordt gebruikt en geïmplementeerd. Als uw site een frontend zonder kop heeft, kunt u de API&#39;s voor GraphQL en REST laden. Hoe u uiteindelijk het testen van de belasting aan u en het team DevOps toeëigent. Weet dat elke laadtest, die zo snel mogelijk wordt uitgevoerd, inzicht geeft in de status van het project. Het biedt ook benchmarks voor toekomstige tests om na te gaan of er zich drastische veranderingen voordoen in de resultaten van de belastingstest. Als dat het geval is, en zij negatief zijn, is dit een goede gelegenheid om de recentste codeveranderingen te herzien en te zoeken prestaties beïnvloedende secties om te verbeteren.

Adobe Commerce heeft goede richtlijnen voor het uitvoeren van eenheidstests, zie [PHP-eenheidstests](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} in de _Testhandleiding voor toepassingen_ op de documentatiesite van Adobe Developer.

Ga voor meer informatie over functionele tests naar [Inleiding tot het kader voor functionele tests](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
