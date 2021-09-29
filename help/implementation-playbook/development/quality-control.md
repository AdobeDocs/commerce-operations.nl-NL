---
title: Kwaliteitscontrole
description: Leer over de kwaliteitscontroleprocessen van de Handel van de Adobe met betrekking tot implementatieprojecten.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---


# Quality control process and tools

![Diagram kwaliteitscontroleproces](../../assets/playbooks/quality-control-diagram.svg)

Het kwaliteitscontroleproces in het vorige diagram kan als volgt kort worden beschreven.

<table>
<thead>
  <tr>
    <th>Software-ontwikkelingsproces</th>
    <th>QC-workflow</th>
    <th>QC</th>
    <th>QC-leader</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Ontwikkeling</td>
    <td>Planning</td>
    <td></td>
    <td>Evalueren en bijdragen aan testplannen</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Testspecificaties opstellen (testgevallen/testscenario's)</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Testgegevens voorbereiden en verkrijgen</td>
  </tr>
  <tr>
    <td></td>
    <td>Analyse en ontwerp testen</td>
    <td>Review and contribute to test plans</td>
    <td>Start het preparaat, specificaties</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Testspecificaties opstellen (testgevallen/testscenario's)</td>
    <td>Schrijf of herzie een strategie van de Test voor het project</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Testgegevens voorbereiden en verkrijgen</td>
    <td> Regelafstand, begeleiding en controle van de analyse, het ontwerp</td>
  </tr>
  <tr>
    <td>Interne tests</td>
    <td>Implementatie en uitvoering testen</td>
    <td>Hiermee implementeert u tests, voert u deze uit en registreert u de tests</td>
    <td>Toezicht op de uitvoering en uitvoering van de tests</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Prestaties controleren en beveiliging scannen: evalueer de resultaten en de afwijkingen van de verwachte resultaten</td>
    <td>Zorg ervoor dat de tests tot op de testbasis traceerbaar zijn en controleer de fouten in het Bug-trackingssysteem</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Fouten posten voor het trackingsysteem voor fouten (Jira/Redmine/Trello)</td>
    <td>Prioriteit geven aan/plannen tests om zich aan te sluiten bij de projectplanning die door PM wordt bepaald</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Opnieuw testen (bevestigingstests) na het corrigeren van fouten</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td>Evaluatie en rapportage</td>
    <td>Voortgang van de test rapporteren naar lood voor QC en PM</td>
    <td>Evaluatie van testresultaten en voortgang</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td>Schrijf testsamenvattingsrapporten die op de tijdens de test verzamelde informatie worden gebaseerd</td>
  </tr>
  <tr>
    <td>UAT</td>
    <td>UAT</td>
    <td>Verify Customer Feedbacks or Change Requests (CRs)</td>
    <td>Follow-up</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Opnieuw testen en regressietests uitvoeren nadat de broncode is gewijzigd</td>
    <td>Controleren</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Testspecificaties bijwerken</td>
    <td></td>
  </tr>
  <tr>
    <td>Onderhoud</td>
    <td>Onderhoud</td>
    <td>Taken evalueren en hieraan een bijdrage leveren</td>
    <td>Tijdstip voor het beoordelen en ramen van taken</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Testspecificaties maken/bijwerken</td>
    <td>Voortgang van de follow-uptest</td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Test uitvoeren voor deze taken</td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td>Regressietests uitvoeren</td>
    <td></td>
  </tr>
</tbody>
</table>

Net als de [tools](project-management-tools.md) die we voor het ontwikkelingsproces hebben geïdentificeerd, hebben we een handvol gekozen oplossingen en platforms geselecteerd die we vaak gebruiken voor het testen van de kwaliteit.

| Doel | Gereedschap |
|---------------------------|---------------------------------------------------|
| Prestatie-index van website | Google PageSpeed, Webpagetest, JMeter |
| Beveiliging | Adobe Commerce Security Scan Tool, SonarQube, ZAP |
| Probleembeheersysteem | JIRA |
| UI-tests | Perfect pixel, BrowserStack |
| API-tests | Postman, SoapUI |
| Automatiseringstests | Selenium |


## Prestatie-index van website

GooglePageSpeed rapporteert over de prestaties van een pagina op zowel mobiele apparaten als desktopapparaten en geeft suggesties over de manier waarop die pagina kan worden verbeterd.

WebPageTest is een hulpmiddel van Webprestaties dat echte browsers gebruikt om tot Web-pagina&#39;s toegang te hebben en timingsmetriek te verzamelen.

JMeter is een Apache-project dat kan worden gebruikt als een tool voor het testen van de belasting voor het analyseren en meten van de prestaties van verschillende services, met de focus op webtoepassingen.

## Beveiliging

SonarQube en ZAP zijn in het ontwikkelingsproces geïntroduceerd, maar we nemen het hier ook op met meer informatie over hoe het betrokken is bij het kwaliteitscontroleproces.

SonarQube wordt ook gebruikt voor doorlopende inspectie van codekwaliteit om automatische revisies uit te voeren met statische analyse van code om insecten, codegeuren, en veiligheidskwetsbaarheid te ontdekken.

OWASPZAP (Zed Attack Proxy) is bedoeld om te worden gebruikt door zowel degenen die nieuw zijn aan toepassingsveiligheid, als professionele penetratietests. Enkele ingebouwde eigenschappen omvatten het onderscheppen van volmachtsserver, traditionele en AJAX kruipende Web, geautomatiseerde scanner, passieve scanner, gedwongen doorbladeren, Fuzzier, steun WebSocket, scripting talen, en stop-n-hack steun.

## UI-tests

Met Perfect Pixel kunnen ontwikkelaars en markeringsontwerpers een halftransparante afbeeldingsbedekking boven op de ontwikkelde HTML plaatsen en een pixelperfecte vergelijking maken.

BrowserStack is een testplatform voor cloud&#39;s en mobiele apparaten waarmee ontwikkelaars hun websites en mobiele toepassingen kunnen testen in browsers, besturingssystemen en mobiele apparaten op aanvraag.

## API testing

Postman is het samenwerkingsplatform voor API-ontwikkeling. Postman simplifies each step of building an API and streamlines collaboration so you can create better APIs.

SoapUI is een open-source webservice testtoepassing voor Simple Object Access Protocol (SOAP) en overdracht van representationele status (REST). Its functionality covers web-service inspection; invoking, development, simulation, and mocking; functional testing; load and compliance testing.

## Automatiseringstests

Selenium bestaat uit verschillende componenten (Selenium client-API, Selenium WebDriver), waarbij elk een specifieke rol speelt bij de ontwikkeling van testautomatisering voor webtoepassingen.
