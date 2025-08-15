---
title: Reageren op een beveiligingsincident
description: Verwerk beveiligingsincidenten door de beste praktijken te volgen om te reageren op beveiligingsproblemen die de beschikbaarheid en prestaties van de site beïnvloeden en deze te verhelpen.
feature: Best Practices
exl-id: 77275d37-4f1d-462d-ba11-29432791da6a
source-git-commit: e63f68dd469564e70269154810cbfbd95d2b2e57
workflow-type: tm+mt
source-wordcount: '1172'
ht-degree: 0%

---

# Aanbevolen procedures om te reageren op een beveiligingsincident

In het volgende artikel worden de aanbevolen procedures beschreven om te reageren op een beveiligingsincident en om problemen op te lossen die gevolgen hebben voor de beschikbaarheid, betrouwbaarheid en prestaties van de Adobe Commerce-site.

Het volgen van deze beste praktijken kan helpen onbevoegde toegang en malware aanvallen verhinderen. Als een veiligheidsincident voorkomt, helpen deze beste praktijken u op een directe reactie voorbereiden, een analyse van de worteloorzaak uitvoeren, en het saneringsproces beheren om normale verrichtingen te herstellen.

>[!TIP]
>
>Adobe heeft ontdekt dat de meeste veiligheidsincidenten voorkomen wanneer de bedreigingsactoren voordeel halen uit bestaande, ongepatcheerde kwetsbaarheid, slechte wachtwoorden, en zwakke eigendom en toestemmingsmontages in de toepassing en de infrastructuurconfiguratie van Commerce. Minimaliseer het voorkomen van veiligheidsincidenten door best practices voor Adobe-beveiliging te evalueren en te volgen wanneer u Adobe Commerce-installaties instelt, configureert en bijwerkt. Zie [ uw plaats en infrastructuur van Commerce beveiligen ](../launch/security-best-practices.md).


## Betrokken producten en versies

[ Alle gesteunde versies ](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Reageren op een incident

Als u vermoedt dat een beveiligingsincident gevolgen heeft voor uw Adobe Commerce-infrastructuurproject voor de cloud, zijn de belangrijkste eerste stappen:

- Toegang tot alle beheerdersgebruikersaccounts controleren
- Geavanceerde MFA-besturingselementen (Multi-Factory Authentication) inschakelen
- Kritieke logbestanden behouden
- Controleer de beveiligingsupgrades voor uw versie van Adobe Commerce.

Hieronder vindt u meer aanbevelingen.

## Onmiddellijk actie ondernemen in geval van een aanval

In het ongelukkige geval van een plaatscompromis, zijn er enkele belangrijke aanbevelingen te volgen:

- Inschakeling van uw systeemintegrator en het juiste beveiligingspersoneel voor het uitvoeren van onderzoeks- en herstelwerkzaamheden.

- Bepaal het werkingsgebied van de aanval:
   - Werd toegang verkregen tot creditcardgegevens?
   - Welke informatie is gestolen?
   - Hoeveel tijd is er verstreken sinds het compromis?
   - Is de informatie versleuteld?

- Zoek de aanvalsvector om te bepalen wanneer en hoe de site is gecompromitteerd door de logbestanden van de server en de bestandswijzigingen te controleren.

   - In bepaalde omstandigheden kan het raadzaam zijn alles te wissen en opnieuw te installeren of, in het geval van virtuele hosting, een nieuwe instantie te maken. Malware kan op een onvermoede locatie worden verborgen, maar dan alleen maar wachten om zichzelf te herstellen.

   - Verwijder alle overbodige bestanden. Vervolgens installeert u de vereiste bestanden opnieuw vanuit een bekende, schone bron. U kunt de installatie bijvoorbeeld opnieuw uitvoeren met bestanden van uw versiebeheersysteem of de oorspronkelijke distributiebestanden van Adobe.

   - Alle referenties opnieuw instellen, inclusief de database, bestandstoegang, betalings- en verzendintegratie, webservices en de aanmeldingsgegevens voor Admin. Herstel ook alle integratie en API sleutels en rekeningen die zouden kunnen worden gebruikt om het systeem aan te vallen.

## Een incident analyseren

De eerste stap van de analyse van incidenten is om zoveel mogelijk feiten te verzamelen, zo snel mogelijk. Het verzamelen van informatie over het incident kan helpen de potentiële oorzaak van het incident te bepalen. Adobe Commerce biedt de onderstaande tools voor hulp bij uw analyse van incidenten.

- [ Logboeken van de Actie Admin van de Controle {](https://experienceleague.adobe.com/docs/commerce-admin/systems/action-logs/action-log-report.html).

  In het rapport Handelingenlogboeken wordt een gedetailleerd overzicht weergegeven van alle beheeracties die zijn ingeschakeld voor loggen. Elke record heeft een tijdstempel en registreert het IP-adres en de naam van de gebruiker. Het logboekgegeven omvat admin gebruikersgegevens en verwante veranderingen die tijdens de actie werden aangebracht.

- Analyseer gebeurtenissen met het [ Bevestiging voor het hulpmiddel van Adobe Commerce ](../../../tools/observation-for-adobe-commerce/intro.md).

  Met het gereedschap Waarnemen voor Adobe Commerce kunt u complexe problemen analyseren om de onderliggende oorzaken te achterhalen. In plaats van het bijhouden van ongelijke gegevens kunt u tijd besteden aan het correleren van gebeurtenissen en fouten om dieper inzicht te krijgen in de oorzaken van knelpunten in de prestaties.

  Gebruik het **lusje van de Veiligheid** in het hulpmiddel om een duidelijke mening van potentiële veiligheidskwesties te krijgen helpen worteloorzaken identificeren en plaatsen houden die optimaal presteren.

- Analyseer logboeken met [ Logboeken van New Relic ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/new-relic-service.html)

  Adobe Commerce op de Pro projecten van de wolkeninfrastructuur omvat de [ Logs van New Relic ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic/log-management.html) dienst. De dienst wordt pre-gevormd om alle logboekgegevens van uw het Opvoeren en milieu&#39;s van de Productie samen te voegen om het in een gecentraliseerd logboekbeheersdashboard te tonen waar u samengevoegde gegevens kunt zoeken en visualiseren.

  Voor andere projecten van Commerce, kunt u opstelling en de [ dienst van de Logboeken van New Relic gebruiken ](https://docs.newrelic.com/docs/logs/get-started/get-started-log-management/) om de volgende taken te voltooien:
   - Het gebruik [ vragen van New Relic ](https://docs.newrelic.com/docs/logs/new-relic-logs/ui-data/query-syntax-logs) aan onderzoek samengevoegde logboekgegevens.
   - Loggegevens visualiseren via New Relic Logs.

## Audit accounts, code en database

Controleer Commerce Admin- en gebruikersaccounts, toepassingscode en databaseconfiguratie en -logboeken om verdachte code te identificeren en op te ruimen en de beveiliging van account-, site- en databasetoegang te garanderen. Vervolgens kunt u desgewenst opnieuw implementeren.

Blijf de site nauwlettend volgen na het incident, aangezien veel sites binnen enkele uren weer gecompromitteerd raken. Zorg voor doorlopende logboekcontrole en controle van de bestandsintegriteit om snel tekenen van nieuwe compromissen te detecteren.

### Gebruikersaccounts van Admin controleren

- [ Admin van het Overzicht gebruikerstoegang ](https://experienceleague.adobe.com/docs/commerce-admin/systems/user-accounts/permissions-users-all.html) - verwijder oude, ongebruikte, of verdachte rekeningen en roteer wachtwoorden voor alle gebruikers Admin.

- [ de veiligheidsmontages van Admin van het Overzicht ](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-admin.html) - verifieer dat de veiligheidsmontages van Admin veiligheid best praktijken volgen.

- [ gebruikersrekeningen van het Overzicht voor Adobe Commerce op de projecten van de wolkeninfrastructuur ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html) - verwijder oude, ongebruikte, of verdachte rekeningen en roteer wachtwoorden voor alle gebruikers van Admin van het wolkenproject. Controleer of de beveiligingsinstellingen van de account correct zijn geconfigureerd.

- [ de sleutels van SSH van de Controle ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) voor Adobe Commerce op wolkeninfrastructuur-Overzicht, schrapt, en roteert de sleutels van SSH.

### Controlecode

- Van Admin, herzie de [ configuratie van de Kopbal en van de Voettekst van HTML ](https://experienceleague.adobe.com/docs/commerce-admin/content-design/design/page-setup.html) op alle werkingsgebiedniveaus, met inbegrip van `website` en `store view`. Verwijder alle onbekende JavaScript-code uit de scripts en stijlpagina&#39;s en andere HTML-instellingen. Alleen herkende code zoals tekstfragmenten bijhouden.

- Vergelijk de huidige basis van de productiecode met de codebasis die in het Systeem van de Controle van de Versie (VCS) wordt opgeslagen.

- Let op elke verdachte code.

- Zorg ervoor dat er geen restanten van verdachte code zijn door codebase aan het productiemilieu opnieuw op te stellen.

### Configuratie en logbestanden van databases controleren

- Controleer eventuele opgeslagen procedures voor wijzigingen.

- Controleer of de database alleen toegankelijk is voor de Commerce-instantie.

- Controleer of malware niet meer aanwezig is door de site te scannen met algemeen beschikbare hulpprogramma&#39;s voor malware-scannen.

- Beveilig het deelvenster Beheer door de naam ervan te wijzigen en te controleren of de site `app/etc/local.xml` en `var` URL&#39;s niet openbaar toegankelijk zijn.

- Blijf de site nauwlettend volgen na het incident, aangezien veel sites binnen enkele uren weer gecompromitteerd raken. Zorg voor doorlopende logboekcontrole en controle van de bestandsintegriteit om snel tekenen van nieuwe compromissen te detecteren.

## Google-waarschuwingen verwijderen

Als de site door Google is gemarkeerd als een locatie met kwaadaardige code, vraagt u om een revisie zodra de site is gereinigd. Het duurt een paar dagen voordat sites die met malware zijn besmet, zijn gecontroleerd. Nadat Google heeft vastgesteld dat de site schoon is, worden waarschuwingen uit zoekresultaten weergegeven en verdwijnen de browsers binnen 72 uur. Zie [ Verzoek om een overzicht ](https://web.dev/articles/request-a-review).

## Controlelijst voor malwaresultaten controleren

Als de openbaar beschikbare hulpmiddelen van het malwareaftasten een malware aanval bevestigen, onderzoek het incident. Werk met de oplossingenintegrator om de site schoon te maken en volg het aanbevolen herstelproces.

## Aanvullende beoordelingen uitvoeren

Wanneer het behandelen van verfijnde aanvallen, is de beste manier van actie met een ervaren ontwikkelaar, een derde deskundige, of oplossingenintegrator te werken om de plaats volledig te herstellen en veiligheidspraktijken te herzien. Het werken met ervaren veiligheidsberoeps zorgt ervoor dat de uitvoerige, geavanceerde maatregelen worden genomen om de veiligheid van uw zaken en zijn klanten te verzekeren.

## Aanvullende informatie

- [ Kader van de Analyse van de Oorzaak van de wortel ](https://sansec.io/kb/incident-response/magento-root-cause-analysis).
