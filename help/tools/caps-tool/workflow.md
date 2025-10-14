---
title: Hoe  [!DNL Cloud Automation Patching Service (CAPS)]  werkschema werkt
description: Leer over het  [!DNL Cloud Automation Patching Service (CAPS)]  werkschemaproces, met inbegrip van terminologie, werkschemafasen, en verrichtingen voor geautomatiseerd flardbeheer.
hide: true
hidefromtoc: true
source-git-commit: eff8c0ae9e1d9db6b46ba7cfbb915685ab5b194d
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 0%

---

# De werking van de [!DNL Cloud Automation Patching Service (CAPS)] -workflow

Dit onderwerp biedt een overzicht op hoog niveau van de werking van patchbewerkingen met [!DNL CAPS (Cloud Automation Patching Service)].

## Terminologie

* **Verrichtingen** - de belangrijkste acties die door [!DNL CAPS] worden uitgevoerd:
   * Toepassen
   * Vorige versie
* **Fases** - de drie fasen van het werkschema:
   * Voorafgaande controle
   * Reparatie
   * Validatie
* **Milieu** - het milieu van de Wolk van de Handel van Adobe waar de flarden worden toegepast.

## Bewerkingen

[!DNL CAPS] steunt twee belangrijkste *verrichtingen* voor het beheren van flarden in uw milieu van de Wolk van de Handel van Adobe:

* **pas verrichting** toe - voegt flardveranderingen in uw codebase door een veilig, bevestigd proces toe. Patches worden toegepast door patchbestanden in de map &#39;m2-hotfixes&#39; te plaatsen.

* **keert verrichting** terug - verwijdert eerder toegepaste flarden uit uw codebase door flarddossiers uit de &quot;m2-hotfixes&quot;omslag te verwijderen.

>[!IMPORTANT]
>
>Herstelbewerkingen zijn alleen beschikbaar voor patches die oorspronkelijk zijn toegepast via [!DNL CAPS] . Patches die handmatig of via andere methoden zijn toegepast, kunnen niet worden teruggedraaid met deze service.

## Fasen

Het [!DNL CAPS] werkschema gebruikt drie *fasen* die altijd in deze orde worden uitgevoerd om ervoor te zorgen dat de flarden veilig en betrouwbaar worden toegepast:

* **Voorlopige controle** - bevestigt flardverenigbaarheid en omgevingsbereidheid.
* **het Patching** - past of keert het flard in een integratiemilieu terug.
* **Bevestiging** - bevestigt de flardtoepassing en voert gezondheidscontroles uit.

## Fasdetails

### Fase 1: Voorafgaande controle

De voorbereidingscontrolefase controleert of de patch veilig op uw omgeving kan worden toegepast.

**wat gebeurt:**

* **de milieuwaarborgen van de Productie** (de milieu&#39;s van de Productie slechts):
   * Controleert of de opslag zich in de onderhoudsmodus bevindt
   * Hiermee wordt gecontroleerd of snijtaken zijn uitgeschakeld
   * Blokken patchen als niet aan de voorwaarden wordt voldaan
   * Hiermee wordt het bevestigingsvenster weergegeven als aan de voorwaarden is voldaan
* **bevestiging van het Reparatie** - verifieert het flarddossier geldig en compatibel is
* **beoordeling van het Milieu** - controleert milieubereidheid en middelen
* **opsporing van het Conflict** - identificeert potentiële conflicten met bestaande code
* **Controle van de Afhankelijkheid** - bevestigt de versiecompatibiliteit van Adobe Commerce

### Fase 2: Repareren

De patchfase past de pleister toe of keert deze terug in een tijdelijke integratieomgeving voor het testen. Tijdens dit stadium, creeert [!DNL CAPS] een tijdelijke testmilieu om de flard veilig toe te passen en te testen alvorens veranderingen in uw daadwerkelijke milieu aan te brengen.

Deze aanpak voorziet in:

* **Veiligheid** - houdt uw doelmilieu onaangetast tot het flard wordt bevestigd
* **het Testen** - in een echt milieu alvorens productie te beïnvloeden
* **vermogen van het Terugschroeven van prijzen** - als de kwesties worden ontdekt
* **Isolatie** - voor elke flardverrichting

#### Fase 2a: Integratieomgeving creëren

**de verwezenlijking van de Tak** - [!DNL CAPS] leidt tot een tijdelijke genoemde tak van het integratiemilieu `{target-environment}-CAPS-{patch-id}`

**opstelling van het Milieu** - het integratiemilieu wordt gecreeerd als kind van uw doelmilieu

**synchronisatie van de Code** - het integratiemilieu erft de nauwkeurige staat van uw doelmilieu

**vereisten van het Middel** - [!DNL CAPS] leidt tot een tijdelijk milieu gebruikend codebase van uw doelmilieu. Volgens de documentatie van Adobe Commerce Cloud beschikt elke omgeving (inclusief integratieomgevingen) over een aparte opslagtoewijzing op basis van uw gecontracteerde opslagabonnement. De hoeveelheid opslagruimte die u hebt gecontracteerd, geeft de totale opslagruimte voor elke omgeving aan. In de meeste gevallen zult u geen problemen met bronbeperkingen ondervinden. Als er een fout optreedt met betrekking tot de bronbeperkingen, controleert u de grootte van uw toepassing en de gecontracteerde opslag in uw abonnement.

#### Fase 2b: Patch application in integration environment

**Veilig het testen** - het flard wordt toegepast op het integratiemilieu, niet direct op uw doelmilieu

**het beheer van het Dossier** - de dossiers van het Reparatie worden geplaatst in de `m2-hotfixes/` folder

**de verrichtingen van het Git** - de veranderingen worden toegewijd en aan de tak van het integratiemilieu geduwd

**activering van het Milieu** - het integratiemilieu wordt geactiveerd om de gepatcheerde code op te stellen

#### Stap 2c: Samenvoegen naar doelomgeving

**Controle van het Milieu** - [!DNL CAPS] controleert plaatselijk uw doelmilieu

**verrichting van de Fusie** - de tak van het integratiemilieu wordt samengevoegd in het doelmilieu

**Conflict resolutie** - als om het even welke conflicten voorkomen, worden zij automatisch opgelost wanneer mogelijk

**Plaatsing** - de samengevoegde veranderingen worden opgesteld aan uw doelmilieu

**Verificatie** - [!DNL CAPS] verifieert dat de fusie succesvol was en de milieu&#39;s in synchronisatie zijn

**Opschoonmaakbeurt van het Milieu** - het tijdelijke integratiemilieu wordt geschrapt om middelen vrij te maken

## Levenscyclus integratieomgeving

Integratieomgevingen hebben een specifieke levenscyclus tijdens de patchfase:

* **Verwezenlijking** - die bij het begin van het het patchen stadium wordt gecreeerd
* **Actieve periode** - blijf actief tijdens flardtoepassing en het testen
* **Schoonmaakbeurt** - automatisch geschrapt na succesvolle fusie of als de verrichting ontbreekt

### Fase 3: Validatie

De validatiefase zorgt ervoor dat de patchtoepassing correct werkt en voert gezondheidscontroles uit.

**wat gebeurt:**

* **de gezondheidscontrole van de Toepassing** - verifieert het toepassingsbegin en looppas behoorlijk
* **Schoonmaakbeurt** - verwijdert tijdelijk milieu, werkt logboeken bij, brengt voltooiing op de hoogte

## Succesindicatoren

**pas verrichting toe:**

* &quot;Taak is voltooid&quot; - Reparatie is toegepast zonder problemen
* &quot;Reparatie is toegepast&quot; - Reparatie was al aanwezig (geen actie vereist)
* Patch-bestand is in map &#39;m2-hotfixes&#39; geplaatst
* Alle validatiecontroles slagen
* Gezondheidscontroles van toepassingen succesvol

**keert verrichting terug:**

* &quot;Taak is voltooid&quot; - Reparatie is ongedaan gemaakt zonder problemen
* &quot;Reparatie is hersteld&quot; - Reparatie is al hersteld (geen actie vereist)
* Reparatiebestand is verwijderd uit map &#39;m2-hotfixes&#39;
* Alle validatiecontroles slagen
* Gezondheidscontroles van toepassingen succesvol

## Beschermingsmaatregelen voor de productieomgeving

[!DNL CAPS] bevat specifieke voorzorgsmaatregelen voor productieomgevingen om onbedoelde onderbrekingen te voorkomen en ervoor te zorgen dat patches vooraf veilig worden gevalideerd.

### Voorwaarden voor productiepatches

Voordat u patches toepast op productieomgevingen, controleert [!DNL CAPS] op twee kritieke omstandigheden:

* **wijze van het Onderhoud** - de opslag moet op onderhoudswijze zijn
* **Gewas banen gehandicapt** - de banen van de Kroon moeten worden onbruikbaar gemaakt

Als aan een van beide voorwaarden niet wordt voldaan, wordt de patchtoepassing geblokkeerd en wordt de gebruiker op de hoogte gesteld.

## Verwante onderwerpen

* [CAPS-introductie](intro.md)
* [Toegang krijgen](access.md)
* [Aanbevolen procedures](best-practices.md)
* [Problemen oplossen](troubleshooting.md)
