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

CSP kan in fasen worden geïmplementeerd om te voorkomen dat de sitebewerkingen worden beïnvloed. CSP heeft twee basismodi: `report-only mode` en `restrict mode` .

**rapport-slechts wijze**: Browser wordt opgedragen om beleidsschendingen te melden, maar hen niet af te dwingen. Telkens als een gevraagde middel CSP schendt, registreert browser de resulterende fouten aan de console. Het consolelogboek kan dan worden gebruikt om de oorzaak van elke schending te onderzoeken.

Het is belangrijk om alle CSP fouten te herzien aangezien zij voorkomen en het beleid te verfijnen tot alle noodzakelijke middelen worden gewhitelisterd. U kunt veilig overschakelen op `restrict mode` als er geen fouten meer optreden. Anders, zou slecht gevormde CSP browser kunnen veroorzaken om een lege pagina met talrijke consolefouten te tonen. Met een correct geconfigureerde CSP kan inhoud met whitelisting worden geleverd zonder dat dit van invloed is op de prestaties.

**Beperk wijze**: Browser wordt opgedragen om al inhoudsbeleid af te dwingen en publicatie te beperken tot gewhitelisteerde middelen.

De eerste fase van de Adobe Commerce CSP-implementatie werd geïntroduceerd in Adobe Commerce 2.3.5 en standaard beschikbaar gesteld in `report-only mode` .  In Adobe Commerce 2.4.7 en hoger is CSP standaard geconfigureerd in `restrict-mode` voor betaalpagina&#39;s in de winkelruimte en in de beheergebieden en in de `report-only` -modus voor alle andere pagina&#39;s. De corresponderende CSP-header bevat niet het trefwoord `unsafe-inline` in de instructie `script-src` voor betalingspagina&#39;s. Bovendien zijn alleen gewhitelisteerde inlinescripts toegestaan.

Omdat CSP van de server, eerder dan van Admin wordt gevormd, hebben de meeste verkopers de hulp van een systeemintegrator of ontwikkelaar nodig om het behoorlijk te vormen. Zie [ Beleid van de Veiligheid van de Inhoud ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/) in de _Gids van de Ontwikkelaar van Commerce PHP_.


## Rapportage

Door gebrek, verzendt CSP fouten naar de browser console, maar kan worden gevormd om foutenlogboeken door HTTP- verzoek te verzamelen. Bovendien zijn er verscheidene derdediensten die u kunt gebruiken om, schendingen te controleren te verzamelen en te melden CSP. CSP de schendingen kunnen aan een eindpunt voor inzameling worden gemeld door URI van Admin, of van het `config.xml` dossier voor een douanemodule toe te voegen.  Zie [ configuratie van URI van het Rapport ](https://developer.adobe.com/commerce/php/development/security/content-security-policies/#report-uri-configuration) in de _Gids van de Ontwikkelaar van de Uitbreidingen van Commerce PHP_.

[ URI van het Rapport ](https://report-uri.io/) is de dienst die schendingen CSP controleert en de resultaten in een dashboard toont. Zowel kunnen de handelaren als de ontwikkelaars de dienst gebruiken om rapporten te ontvangen wanneer de schendingen CSP voorkomen.
