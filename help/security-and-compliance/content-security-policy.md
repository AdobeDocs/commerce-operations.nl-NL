---
title: Overzicht van het inhoudsbeveiligingsbeleid
description: Leer hoe u de beveiligingspositie van uw Adobe Commerce-winkel kunt verbeteren met behulp van een beleid voor inhoudsbeveiliging.
exl-id: 81070a09-5f8f-48b1-b542-1443dbd43f5f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 0%

---

# Overzicht van het inhoudsbeveiligingsbeleid

Een beleid van de Veiligheid van de Inhoud (CSP) kan extra lagen defensie voor de installaties van Adobe Commerce verstrekken door te helpen om de Overseinen Scripting van de Ruimte (XSS) en verwante aanvallen van de gegevensinjectie te ontdekken en te verlichten. Deze algemene aanvalsvector werkt door kwaadaardige inhoud in te voeren waarvan ten onrechte wordt beweerd dat deze van de website afkomstig is. Nadat de kwaadaardige inhoud is geladen en uitgevoerd, kan de overdracht van gegevens door onbevoegden worden gestart.

CSP verstrekt een gestandaardiseerde reeks richtlijnen die browser vertelt welke inhoudsmiddelen kunnen worden vertrouwd, en die zouden moeten worden geblokkeerd. Met zorgvuldig gedefinieerde beleidsregels kan CSP de browserinhoud beperken, zodat alleen gewhitelisteerde bronnen worden weergegeven.

## Configuratie

CSP kan in fasen worden geïmplementeerd om te voorkomen dat de sitebewerkingen worden beïnvloed. CSP heeft twee basismodi: `report-only mode` en `restrict mode`.

**Alleen-rapporteren, modus**: De browser wordt geïnstrueerd om beleidsovertredingen te melden, maar hen niet af te dwingen. Telkens als een gevraagde middel CSP schendt, registreert browser de resulterende fouten aan de console. Het consolelogboek kan dan worden gebruikt om de oorzaak van elke schending te onderzoeken.

Het is belangrijk om alle CSP fouten te herzien aangezien zij voorkomen en het beleid te verfijnen tot alle noodzakelijke middelen worden gewhitelisterd. Het is veilig om over te schakelen naar `restrict mode` wanneer er geen fouten meer optreden. Anders, zou slecht gevormde CSP browser kunnen veroorzaken om een lege pagina met talrijke consolefouten te tonen. Met een correct geconfigureerde CSP kan inhoud met whitelisting worden geleverd zonder dat dit van invloed is op de prestaties.

**Beperken, modus**: De browser krijgt de instructie om al het inhoudsbeleid af te dwingen en de publicatie te beperken tot bronnen met whitelisting.

De eerste fase van de Adobe Commerce CSP-implementatie werd geïntroduceerd in Adobe Commerce 2.3.5 en beschikbaar gesteld in `report-only mode` standaard.  In Adobe Commerce 2.4.7 en hoger is CSP geconfigureerd in `restrict-mode` standaard voor betalingspagina&#39;s in de opslagruimte en de beheergebieden, en in `report-only` voor alle andere pagina&#39;s. De corresponderende CSP-header bevat niet de `unsafe-inline` trefwoord in de `script-src` richtlijn voor betalingspagina&#39;s. Bovendien zijn alleen gewhitelisteerde inlinescripts toegestaan.

Omdat CSP van de server, eerder dan van Admin wordt gevormd, hebben de meeste verkopers de hulp van een systeemintegrator of ontwikkelaar nodig om het behoorlijk te vormen. Zie [Beveiligingsbeleid voor inhoud](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) in de _PHP-ontwikkelaarsgids voor handel_.


## Rapportage

Door gebrek, verzendt CSP fouten naar de browser console, maar kan worden gevormd om foutenlogboeken door HTTP- verzoek te verzamelen. Bovendien zijn er verscheidene derdediensten die u kunt gebruiken om, schendingen te controleren te verzamelen en te melden CSP. CSP de schendingen kunnen aan een eindpunt voor inzameling worden gemeld door URI van Admin toe te voegen, of van `config.xml` bestand voor een aangepaste module.  Zie [URI-configuratie rapporteren](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) in de _Handleiding voor PHP Extensions-ontwikkelaars_.

[URI rapporteren](https://report-uri.io/) is de dienst die schendingen CSP controleert en de resultaten in een dashboard toont. Zowel kunnen de handelaren als de ontwikkelaars de dienst gebruiken om rapporten te ontvangen wanneer de schendingen CSP voorkomen.
