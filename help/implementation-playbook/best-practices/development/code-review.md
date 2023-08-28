---
title: Beste werkwijzen voor codebeoordeling
description: Leer over code overzicht beste praktijken voor de ontwikkelingsfase van projecten van Adobe Commerce.
feature: Best Practices
role: Developer
source-git-commit: 291c3f5ea3c58678c502d34c2baee71519a5c6dc
workflow-type: tm+mt
source-wordcount: '1168'
ht-degree: 0%

---


# Aanbevolen procedures voor het beoordelen van code voor Adobe Commerce

Het belangrijkste doel van codeoverzicht is te bevestigen dat de uitgevoerde functionaliteit aan de vereisten op een optimale manier van prestaties, architectuur, en veiligheidsperspectieven voldoet.

Daarnaast is het de bedoeling dat de coderevisie ervoor zorgt dat code aan de best practices voor Adobe Commerce-ontwikkeling voldoet, gemakkelijk te begrijpen en te onderhouden is en de coderingsstandaarden volgt. De meeste coderingsnormen moeten automatisch worden gecontroleerd met de juiste gereedschappen.

## Aanbevolen codecontroleproces

Op hoog niveau moet het proces voor de toetsing van de code uit de volgende stappen bestaan:

1. Aftakking van de afhandelingsfunctie in de lokale ontwikkelomgeving.
1. Als het terwijl is geweest sinds de code voor overzicht werd voorgelegd, voeg de recentste veranderingen van de doeltak (gewoonlijk tak QA) samen, en duw updates aan de verre eigenschaptak (als om het even welk).
1. Voer een controle op hoog niveau uit om te controleren of de code alle vereisten implementeert. Als er grote verschillen zijn, neem dan contact op met de ontwikkelaar voor opheldering.
1. Het uitvoeren van de code is optioneel, maar als u twijfelt of de code werkt zoals verwacht of als het de efficiëntie van het proces bevordert, test u of de geïmplementeerde functionaliteit werkt zoals u verwacht voor hoofdgebruiksscenario&#39;s. Als er grote problemen zijn, stopt u het revisieproces en opent u het ticket opnieuw met de juiste opmerkingen.
1. Voer een grondige revisie uit om te controleren of de code alle vereisten implementeert. Als er problemen zijn, voegt u de gewenste opmerkingen toe aan het intrekkingsverzoek en opent u het ticket opnieuw.
1. Als alles er goed uitziet, voegt u de pull-aanvraag samen (of geeft u deze door aan het volgende codecontrole-niveau als er een is ingesteld).

Houd ook rekening met de volgende punten wanneer u codecontroleprocessen implementeert:

- De controle van de code is een primair hulpmiddel voor mededeling en kennisoverdracht binnen een team. Zelfs als een trekkingsverzoek geen belangrijke kwesties bevat en de vereiste bedrijfslogica uitvoert, kunt u het als kans gebruiken om meer verbeteringen voor te stellen nadat het is samengevoegd.

- Gemiddeld zou de controle van code niet meer dan 10% tot 20% van ontwikkelingsinspanning moeten vergen. Dat veronderstelt dat het ontwikkelingsteam uit senior ingenieurs bestaat die goed samenwerken. Als de codecontrole langer duurt, kan het projectbegroting en chronologie beïnvloeden.

- Problemen met te veel moeite aanpakken die vereist zijn voor coderevisies door de oorzaak van de problemen vast te stellen. Meestal is dat omdat de vereisten slecht vertaald zijn in ontwikkelingstickets (vanwege communicatieproblemen, slechte gebruikersverhalen) of omdat het een coachingprobleem is. In het eerste geval, adviseert matiging moet ervoor zorgen dat de kaartjes genoeg informatie voor teamleden hebben om de vereisten efficiënt te leveren. In het tweede geval, zou u de teamstructuur kunnen moeten aanpassen om hogere ingenieurs te omvatten of goedkeuring buiten het begeleiden en het coaching krijgen.

## Betrokken producten en versies

[Alle ondersteunde versies](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Waar moet u naar zoeken in coderevisie

### Stijl

Stijl kan automatisch worden getest door de PHPStorm-inspectie uit te voeren (zie hieronder).

Zorg ervoor dat u [PHPMD en PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) en om de [Codeerstandaard](https://github.com/magento/magento-coding-standard) van de CLI (ook hieronder). Er is wat overlapping, maar beide hebben ook unieke tests.

### Conventie en structuur

Revisies voor conventie en structuur worden handmatig uitgevoerd.

- Is klassenfunctionaliteit beperkt tot één enkele verantwoordelijkheid?
- Heeft de mapstructuur zin?
- Is functionaliteit uitgevoerd op het juiste niveau (server, client, CSS, JS, database, framework, infrastructuur).
- Klopt de versie?
- Ziet de code er onconventioneel uit of probeert hij een probleem op de verkeerde manier te omzeilen?
- Is de naamgevingsconventie voor de naam van de module, de pakketnaam en de opslagplaats correct toegepast?
- Controleer of algemene CSS-stijlen zorgvuldig worden toegepast en niet worden overgebruikt.

### Volledigheid

De controles op volledigheid worden manueel gedaan.

- Kan de code door configuratie worden in- of uitgeschakeld en gedraagt alle vereiste code zich zoals verwacht?
- Is alle configuratie aanwezig die in het kaartje wordt vermeld? Controleer het bereik, het gegevenstype, de validatie, vertaling en standaardwaarden.
- Wordt de configuratie altijd opgehaald op het laagst mogelijke niveau (niveau van de archiefmening, website, of globaal niveau)? De herwinning van de configuratie moet de definitie van werkingsgebied in aanpassen `system.xml` bestand.
- Zijn alle paden in het stroomdiagram van de technische specificatie opgenomen? Zijn alle andere technische specificaties van toepassing?
- Worden ACLs bepaald voor de nieuwe functionaliteit?
- Zijn PhpDocs duidelijk? Wis het begaan van berichten duidelijk?
- Is om het even welke code commentarieert uit of ziet u zuivert code?

### Prestaties

De recensies voor prestaties worden gedaan manueel, die door code uitvoering kan worden gesteund wanneer in twijfel.

- Worden query&#39;s uitgevoerd in een lus? Deze lus kan zich buiten de bewerkte bestanden bevinden.
- Kan u elke `cachable="false"` kenmerken? Worden deze correct toegepast?

### Beveiliging

Beveiligingsbeoordelingen worden handmatig uitgevoerd, wat kan worden ondersteund door het zoeken naar tekst. Een deel van de veiligheidscontrole wordt verzorgd door geautomatiseerde tests.

- Worden de uitzonderingen geregistreerd wanneer nodig? Worden de juiste soorten uitzonderingen gebruikt?
- Kan `around` insteekmodules worden vermeden?
- Retourneert insteekmodules de juiste typen gegevens?
- Kunt u om het even welke ruwe SQL vragen vinden die zouden moeten worden gebouwd gebruikend de laag van de gegevensbestandabstractie?
- Is om het even welk nieuw type van gegevens blootgesteld aan om het even welk type van gebruiker, admin, of frontend? Is die blootstelling een veiligheidsrisico?
- Worden door de gebruiker gegenereerde gegevens gevalideerd? Alles wat uit de browser komt, wordt beschouwd als door de gebruiker gegenereerd, inclusief cookiewaarden en serverheaders.

### Privacy en GDPR

Revisies voor privacy en [GDPR](../../../security-and-compliance/privacy/gdpr.md) handmatig worden uitgevoerd.

- Verwerkt de code klantgegevens of e-mails? Let vooral op.
- Als deze code in een lijn kan worden uitgevoerd, kan het klantengegevens van één luscyclus aan een andere lekken?
- Indicatoren voor een risico zijn import, cron-taken, transactie-e-mails en batchrijhandlers.
- Zorg ervoor dat de gebruikersgegevens zijn gescheiden in lussen. Adobe raadt het gebruik van fabrieken of opslagruimten aan om modellen in de luscyclus te maken die niet toegankelijk zijn buiten de lus.

### Mentoring

Revisies voor mentoring worden handmatig uitgevoerd.

- Zoek naar plaatsen om kennis met het doel te delen om het team te onderwijzen.
- Als uw opmerking louter educatief is, maar niet essentieel voor het voldoen aan de normen, geeft u aan dat het niet verplicht is voor de auteur om deze op te lossen.
- Als je iets moois ziet, vertel het dan aan de ontwikkelaar, vooral wanneer ze een van je opmerkingen op een goede manier hebben behandeld. Codebeoordelingen zijn vaak gericht op fouten, maar moeten ook een aanmoediging en waardering voor goede praktijken bieden. Soms is het nog waardevoller om een ontwikkelaar te vertellen wat ze goed deden dan om hen te vertellen wat ze fout deden.

## Automatisering

De ontwikkelaars kunnen automatisering gebruiken om de compilatie van DI, gegevensbestandschema, componentenbevestiging, en naleving van de coderingsnormen te herzien:

- De compilatie-looppas van DI de volgende bevelen CLI om te zien of kan de code zonder enige kwesties worden gecompileerd.

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- Databaseschema `whitelist.json`—stel het volgende CLI bevel in werking en bevestig dat `db_schema_whitelist.json` wordt niet toegevoegd of gewijzigd.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer valideren—Valideer het `composer.json` dossier door het volgende CLI bevel in de folder in werking te stellen die het bevat `composer.json` bestand.

  ```bash
  composer validate
  ```

- Codering standaard—Installeer en voer het gereedschap Coderingsstandaard uit en voer dit uit op de module. In het volgende bestand ziet u hoe u het mogelijk maakt om het bestand overal te gebruiken `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Phpstan

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- PHPStorm-inspectie

- PHP-functie voor kopiëren/plakken in PHP
