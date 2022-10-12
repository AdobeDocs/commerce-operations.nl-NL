---
title: Overzicht van het inhoudsbeveiligingsbeleid
description: Leer hoe u de beveiligingspositie van uw Adobe Commerce- of Magento Open Source-winkel kunt verbeteren met behulp van een beleid voor inhoudsbeveiliging.
source-git-commit: 1a608e8a5986026d5a187dc8cbd358fed2db5d9e
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Overzicht van het inhoudsbeveiligingsbeleid

Een beleid van de Veiligheid van de Inhoud (CSP) kan extra lagen defensie voor de installaties van Adobe Commerce en van de Magento Open Source verstrekken door het helpen om de Scripting van de Intersite (XSS) en verwante aanvallen van de gegevensinjectie te ontdekken en te verlichten. Deze algemene aanvalsvector werkt door kwaadaardige inhoud in te voeren waarvan ten onrechte wordt beweerd dat deze van de website afkomstig is. Nadat de kwaadaardige inhoud is geladen en uitgevoerd, kan de overdracht van gegevens door onbevoegden worden gestart.

CSP verstrekt een gestandaardiseerde reeks richtlijnen die browser vertelt welke inhoudsmiddelen kunnen worden vertrouwd, en die zouden moeten worden geblokkeerd. Met zorgvuldig gedefinieerde beleidsregels kan CSP de browserinhoud beperken, zodat alleen gewhitelisteerde bronnen worden weergegeven.

## Configuratie

CSP kan in fasen worden geïmplementeerd om te voorkomen dat de sitebewerkingen worden beïnvloed. CSP heeft twee basismodi: `report-only mode` en `restrict mode`. De release van Adobe Commerce 2.3.5 markeert de eerste fase van onze implementatie en maakt CSP beschikbaar in `report-only mode` standaard. In een toekomstige release `restrict mode` is standaard ingeschakeld voor extra bescherming buiten de doos.

**Alleen-rapporteren, modus**: De browser wordt opgedragen om beleidsovertredingen te melden, maar niet om hen te dwingen. Telkens als een gevraagde middel CSP schendt, registreert browser de resulterende fouten aan de console. Het consolelogboek kan dan worden gebruikt om de oorzaak van elke schending te onderzoeken.

Het is belangrijk om alle CSP fouten te herzien aangezien zij voorkomen en het beleid te verfijnen tot alle noodzakelijke middelen worden gewhitelisterd. Het is veilig om te schakelen naar `restrict mode` wanneer er geen fouten meer optreden. Anders, zou slecht gevormde CSP browser kunnen veroorzaken om een lege pagina met talrijke consolefouten te tonen. Met een correct geconfigureerde CSP kan inhoud met whitelisting worden geleverd zonder dat dit van invloed is op de prestaties.

**Beperken, modus**: De browser krijgt de instructie om al het inhoudsbeleid af te dwingen en de publicatie te beperken tot bronnen met whitelisting. Omdat CSP van de server, eerder dan van Admin wordt gevormd, hebben de meeste verkopers de hulp van een systeemintegrator of ontwikkelaar nodig om het behoorlijk te vormen. Zie [Beveiligingsbeleid voor inhoud](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) in de _PHP-extensies voor handelsdoeleinden_ ontwikkelaarshandleiding.

## Rapportage

Door gebrek, verzendt CSP fouten naar de browser console, maar kan worden gevormd om foutenlogboeken door HTTP- verzoek te verzamelen. Bovendien zijn er verscheidene derdediensten die u kunt gebruiken om, schendingen te controleren te verzamelen en te melden CSP.

[URI rapporteren](https://report-uri.io/) is de dienst die schendingen CSP controleert en de resultaten in een dashboard toont. Zowel kunnen de handelaren als de ontwikkelaars de dienst gebruiken om rapporten te ontvangen wanneer de schendingen CSP voorkomen.
