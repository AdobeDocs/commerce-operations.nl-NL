---
title: Beste werkwijzen voor codebeoordeling
description: Leer over code overzicht beste praktijken voor de ontwikkelingsfase van projecten van Adobe Commerce.
feature: Best Practices
role: Developer
exl-id: 1ef78bce-2e69-4c95-a26e-1bf7196ce546
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1161'
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

[&#x200B; Alle gesteunde versies &#x200B;](../../../release/versions.md) van:

- Adobe Commerce over cloudinfrastructuur
- Adobe Commerce ter plaatse

## Waar moet u naar zoeken in coderevisie

### Stijl

Stijl kan automatisch worden getest door de PHPStorm-inspectie uit te voeren (zie hieronder).

Zorg ervoor om [&#x200B; PHPMD en PHPCS &#x200B;](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) te vormen en het [&#x200B; Norm van de Codering &#x200B;](https://github.com/magento/magento-coding-standard) hulpmiddel van CLI (ook hieronder) in werking te stellen. Er is wat overlapping, maar beide hebben ook unieke tests.

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
- Wordt de configuratie altijd opgehaald op het laagst mogelijke niveau (niveau van de archiefmening, website, of globaal niveau)? Ophalen van configuratie moet overeenkomen met de definitie van bereik in het `system.xml` -bestand.
- Zijn alle paden in het stroomdiagram van de technische specificatie opgenomen? Zijn alle andere technische specificaties van toepassing?
- Worden ACLs bepaald voor de nieuwe functionaliteit?
- Zijn PhpDocs duidelijk? Wis het begaan van berichten duidelijk?
- Is om het even welke code commentarieert uit of ziet u zuivert code?

### Prestaties

De recensies voor prestaties worden gedaan manueel, die door code uitvoering kan worden gesteund wanneer in twijfel.

- Worden query&#39;s uitgevoerd in een lus? Deze lus kan zich buiten de bewerkte bestanden bevinden.
- Kunt u `cachable="false"` kenmerken vinden? Worden deze correct toegepast?

### Beveiliging

Beveiligingsbeoordelingen worden handmatig uitgevoerd, wat kan worden ondersteund door het zoeken naar tekst. Een deel van de veiligheidscontrole wordt verzorgd door geautomatiseerde tests.

- Worden de uitzonderingen geregistreerd wanneer nodig? Worden de juiste soorten uitzonderingen gebruikt?
- Kan `around` plug-ins worden vermeden?
- Retourneert insteekmodules de juiste typen gegevens?
- Kunt u om het even welke ruwe SQL vragen vinden die zouden moeten worden gebouwd gebruikend de laag van de gegevensbestandabstractie?
- Is om het even welk nieuw type van gegevens blootgesteld aan om het even welk type van gebruiker, admin, of frontend? Is die blootstelling een veiligheidsrisico?
- Worden door de gebruiker gegenereerde gegevens gevalideerd? Alles wat uit de browser komt, wordt beschouwd als door de gebruiker gegenereerd, inclusief cookiewaarden en serverheaders.

### Privacy en GDPR

De recensies voor privacy en [&#x200B; GDPR &#x200B;](../../../security-and-compliance/privacy/gdpr.md) worden gedaan manueel.

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

- Databaseschema `whitelist.json` - Voer de volgende CLI-opdracht uit en controleer of het `db_schema_whitelist.json` -bestand niet is toegevoegd of gewijzigd.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer valideert - Valideer het `composer.json` dossier door het volgende CLI bevel in de folder in werking te stellen die het `composer.json` dossier bevat.

  ```bash
  composer validate
  ```

- Codering standaard—Installeer en voer het gereedschap Coderingsstandaard uit en voer dit uit op de module. In het volgende bestand ziet u hoe u kunt instellen dat het bestand overal kan worden uitgevoerd door `mcs ./app/code/Vendor/Module/` te typen.

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
