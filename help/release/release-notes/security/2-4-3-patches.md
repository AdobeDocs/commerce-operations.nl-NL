---
title: Opmerkingen bij de release van Adobe Commerce 2.4.3 Beveiligingspatches
description: Leer meer over oplossingen voor beveiligingsproblemen, beveiligingsverbeteringen en andere beveiligingsupdates die zijn opgenomen in de beveiligingspatchreleases voor Adobe Commerce versie 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: d532402e2d65a1f34558fc3c283d4291be5b006b
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---


# Opmerkingen bij de release voor beveiligingspatches van Adobe Commerce 2.4.3

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.3-p3

Het beveiligingsrelease van Adobe Commerce 2.4.3-p3 biedt beveiligingsoplossingen voor kwetsbaarheden die zijn geïdentificeerd in eerdere versies van 2.4.3. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB22-38 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb22-38.html).

### Toepassen `AC-3022.patch` DHL blijft aanbieden als scheepvaartmaatschappij

DHL heeft schemaversie 6.2 geïntroduceerd en zal schemaversie 6.0 in de nabije toekomst verwerpen. Adobe Commerce 2.4.4 en eerdere versies die de integratie van DHL steunen slechts versie 6.0. Merchants die deze versies opstellen zouden moeten toepassen `AC-3022.patch` zo snel mogelijk DHL als scheepvaartmaatschappij aan te bieden. Zie de [Een patch toepassen om DHL als scheepvaartmaatschappij te blijven aanbieden](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Het artikel van de Kennisbank voor informatie over het downloaden en het installeren van de flard.

### Beveiligingsmarkeringen

* ACL de middelen zijn toegevoegd aan de Inventaris.
* De beveiliging van het voorraadsjabloon is verbeterd.

## Adobe Commerce 2.4.3-p2

De Adobe Commerce 2.4.3-p2 veiligheidsversie verstrekt veiligheidsinsectenmoeilijke situaties voor kwetsbaarheid die in vorige versies zijn geïdentificeerd. Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.

Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB22-13 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  De patchrelease verhelpt ook de kwetsbaarheid die is opgelost door `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`,`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch`, en `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`.


### Toepassen `AC-3022.patch` DHL blijft aanbieden als scheepvaartmaatschappij

DHL heeft schemaversie 6.2 geïntroduceerd en zal schemaversie 6.0 in de nabije toekomst verwerpen. Adobe Commerce 2.4.4 en eerdere versies die de integratie van DHL steunen slechts versie 6.0. Merchants die deze versies opstellen zouden moeten toepassen `AC-3022.patch` zo snel mogelijk DHL als scheepvaartmaatschappij aan te bieden. Zie de [Een patch toepassen om DHL als scheepvaartmaatschappij te blijven aanbieden](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Het artikel van de Kennisbank voor informatie over het downloaden en het installeren van de flard.

### Beveiligingsmarkeringen

* Het gebruik van e-mailvariabelen is in 2.3.4 afgekeurd als onderdeel van een beperking van het beveiligingsrisico ten gunste van een striktere variabele syntaxis. Dit verouderde gedrag is volledig verwijderd in deze versie als voortzetting van die beperking van het veiligheidsrisico.

  Sjablonen voor e-mail- of nieuwsbrieven die in eerdere versies hebben gewerkt, werken dus mogelijk niet correct na de upgrade naar Adobe Commerce 2.4.3-p2. Betrokken sjablonen zijn onder andere overschrijvingen van beheer, thema&#39;s, onderliggende thema&#39;s en sjablonen van aangepaste modules of uitbreidingen van derden. Uw implementatie kan ook na het gebruik van de [Upgrade van compatibiliteitsprogramma](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=en) om afgekeurd gebruik te herstellen. Zie [Aangepaste e-mailsjablonen migreren](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) voor informatie over mogelijke effecten en richtlijnen voor het migreren van betrokken sjablonen.

* De tokens van de de toegangstoegang en van het wachtwoord terugstellen worden nu gecodeerd wanneer opgeslagen in het gegevensbestand. <!-- AC-520 1323-->

* Validatie is versterkt om het uploaden van niet-alfanumerieke bestandsextensies te voorkomen. <!-- AC-479-->

* De wagen is nu standaard uitgeschakeld wanneer Adobe Commerce in de productiemodus staat. <!-- AC-1450-->

* De ontwikkelaars kunnen de groottegrens voor series nu vormen die door Adobe Commerce RESTful eindpunten op een per-eindpuntbasis worden goedgekeurd. Zie [API-beveiliging](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Toegevoegde mechanismen voor het beperken van de grootte en het aantal bronnen dat een gebruiker via een web-API op systeembrede basis kan aanvragen, en voor het overschrijven van de standaardinstellingen voor afzonderlijke modules. Deze verbetering verhelpt het probleem dat door `MC-43048__set_rate_limits__2.4.3.patch`. Zie [API-beveiliging](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

De Adobe Commerce 2.4.3-p1-beveiligingsrelease biedt oplossingen voor beveiligingsproblemen voor kwetsbaarheden die zijn geïdentificeerd in de vorige release (Adobe Commerce 2.4.3 en Magento Open Source 2.4.3). Deze release bevat ook beveiligingsverbeteringen die de naleving van de meest recente best practices op het gebied van beveiliging verbeteren.


Voor de recentste informatie over de veiligheidsinsectenmoeilijke situaties, zie [Beveiligingsbulletin APSB21-86 van de Adobe](https://helpx.adobe.com/security/products/magento/apsb21-86.html). De flardversie verstrekt ook insectenmoeilijke situaties voor [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html), en [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html) door de leverancier ontwikkelde extensies.

### Toepassen `AC-3022.patch` DHL blijft aanbieden als scheepvaartmaatschappij

DHL heeft schemaversie 6.2 geïntroduceerd en zal schemaversie 6.0 in de nabije toekomst verwerpen. Adobe Commerce 2.4.4 en eerdere versies die de integratie van DHL steunen slechts versie 6.0. Merchants die deze versies opstellen zouden moeten toepassen `AC-3022.patch` zo snel mogelijk DHL als scheepvaartmaatschappij aan te bieden. Zie de [Een patch toepassen om DHL als scheepvaartmaatschappij te blijven aanbieden](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Het artikel van de Kennisbank voor informatie over het downloaden en het installeren van de flard.

### Hotfixes

Deze release bevat de volgende hotfix en alle hotfixes die zijn vrijgegeven voor de vorige patchrelease.

* Reparatie `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Zie de [Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatale error Hotfix](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) Het artikel van de Kennisbank voor informatie over zowel flard als kwestie.

### Beveiligingsmarkeringen

**Sessie-id&#39;s zijn verwijderd uit de database**. Deze codeverandering kan in het breken van veranderingen resulteren als de verkopers aanpassingen of geïnstalleerde uitbreidingen hebben die onbewerkte zitting IDs gebruiken die in het gegevensbestand worden opgeslagen. <!-- MC-40976-->

**Beperkte beheerdertoegang tot medialalageriefamappen**. De standaardbevoegdheden van de Medialerie staan nu alleen directorybewerkingen toe (weergeven, uploaden, verwijderen en maken) die expliciet zijn toegestaan door de configuratie. Beheerdergebruikers hebben geen toegang meer tot media-elementen via de medialerie die buiten het dialoogvenster `catalog/category` of `wysiwyg` mappen. Beheerders die toegang willen krijgen tot media-elementen, moeten deze naar een expliciet toegestane map verplaatsen of hun configuratie-instellingen aanpassen. Zie [Media Library-mapmachtigingen wijzigen](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Beperkte limieten voor GraphQL-query**. De GraphQL maximum toegestane vraagingewikkeldheid is verminderd om ontkenning-van-Dienst (DOS) aanvallen te verhinderen. Zie [GraphQL-beveiligingsconfiguratie](https://devdocs.magento.com/guides/v2.4/graphql/security-configuration.html). <!-- PWA-1700-->

**Onlangs gebruikte kwetsbaarheden voor penetratietest** zijn in deze release opgelost. <!-- MC-42431-->

De niet-ondersteunde bronexpressie `unsafe-inline` is verwijderd uit het inhoudsbeveiligingsbeleid `frame-ancestors` richtlijn. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->
